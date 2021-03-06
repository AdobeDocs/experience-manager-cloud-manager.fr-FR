---
title: Environnement de création
description: Découvrez l’environnement de génération spécialisé dans lequel les utilisateurs de Cloud Manager peuvent créer et tester votre code.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: 4c051cd1696f8a00d0278131c9521ad4dcb956a3
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 52%

---


# Environnement de création {#build-environment}

Découvrez l’environnement de génération spécialisé dans lequel les utilisateurs de Cloud Manager peuvent créer et tester votre code.

## Détails de l’environnement {#details}

Les environnements de création de Cloud Manager possèdent les attributs suivants.

* L’environnement de génération est basé sur Linux, dérivé de Ubuntu 18.04.
* Apache Maven 3.6.0 est installé.
* Les versions Java installées sont Oracle JDK 8u202 et Oracle JDK 11.0.2.
* Par défaut, la variable d’environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk1.8.0_202` qui contient le JDK Oracle 8u202. Voir la section [Autre version du JDK d’exécution Maven](#alternate-maven) pour plus d’informations.
* D’autres packages système nécessaires sont installés.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* D’autres packages peuvent être installés au moment de la génération, comme décrit dans la section [Installation de packages système supplémentaires.](#installing-additional-system-packages)
* Chaque construction est faite dans un environnement vierge. Le conteneur de génération ne conserve aucun état entre les exécutions.
* Maven est toujours exécuté avec les trois commandes suivantes :
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven est configuré au niveau du système avec une `settings.xml` qui inclut automatiquement le référentiel d’artefacts d’Adobe public à l’aide d’un profil nommé `adobe-public`.
   * Reportez-vous à la section [Adobe du référentiel Maven public](https://repo1.maven.org/) pour plus d’informations.

>[!NOTE]
>
>Bien que Cloud Manager ne définisse pas de version spécifique du `jacoco-maven-plugin`, la version utilisée doit être au moins `0.7.5.201505241946`.

>[!TIP]
>
>Consultez les ressources supplémentaires suivantes pour savoir comment utiliser les API de Cloud Manager :
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Création d’une intégration d’API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [Autorisations d’API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)


## Utilisation d’une version de Java spécifique {#using-java-version}

Par défaut, les projets sont créés par le processus de génération Cloud Manager à l’aide du JDK Oracle 8. Les clients qui souhaitent utiliser un autre JDK disposent de deux options.

* [Maven Toolchains](#maven-toolchains)
* [Sélection d’une autre version du JDK pour l’ensemble du processus d’exécution Maven](#alternate-maven)

### Maven Toolchains {#maven-toolchains}

Le [Module externe Maven Toolchain](https://maven.apache.org/plugins/maven-toolchains-plugin/) permet aux projets de sélectionner un JDK spécifique (ou toolchain) à utiliser dans le contexte de modules externes Maven compatibles avec les chaînes d’outils. Cette opération est effectuée dans le fichier `pom.xml` du projet en spécifiant un fournisseur et une valeur de version. Voici un exemple de section dans le fichier `pom.xml` :

```xml
        <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-toolchains-plugin</artifactId>
    <version>1.1</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>11</version>
                <vendor>oracle</vendor>
            </jdk>
        </toolchains>
    </configuration>
</plugin>
```

Elle entraîne l’utilisation du JDK Oracle, version 11 dans tous les plug-ins Maven compatibles avec les chaînes d’outils.

Lors de l’utilisation de cette méthode, Maven s’exécute toujours en utilisant le JDK par défaut (Oracle 8) et la variable d’environnement `JAVA_HOME` n’est pas modifiée. Par conséquent, la vérification ou l’application de la version Java par le biais de plug-ins tels que le [plug-in Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) ne fonctionne pas et ces plug-ins ne doivent pas être utilisés.

Les combinaisons fournisseur/version actuellement disponibles sont les suivantes :

| Fournisseur | Version |
|---|---|
| oracle  | 1.8 |
| oracle  | 1,11 |
| oracle  | 11 |
| sun  | 1,8 |
| sun  | 1,11 |
| sun  | 11 |

>[!NOTE]
>
>À compter d’avril 2022, le JDK Oracle sera le JDK par défaut pour le développement et le fonctionnement des applications AEM. Le processus de création de Cloud Manager passe automatiquement à l’utilisation du JDK Oracle, même si une autre option est explicitement sélectionnée dans la chaîne d’outils Maven. Reportez-vous à la section [Notes de mise à jour d’avril](/help/release-notes/2022/2022-4-0.md) pour plus de détails.

### Autre version du JDK d’exécution Maven {#alternate-maven}

Il est également possible de sélectionner Oracle 8 ou Oracle 11 comme JDK pour l’ensemble de l’exécution Maven. Contrairement aux options de toolchains, un autre JDK sera utilisé pour tous les plug-ins, sauf si la configuration de toolchains est également définie, auquel cas la configuration de toolchains est toujours appliquée pour les plug-ins Maven compatibles avec les toolchains. Par conséquent, la vérification et l’application de la version Java à l’aide du [plug-in Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) fonctionneront.

Pour ce faire, créez un fichier nommé `.cloudmanager/java-version` dans la branche de référentiel git utilisée par le pipeline. Ce fichier peut avoir le contenu : `11` ou `8`. Toute autre valeur est ignorée. If `11` est spécifié, l’Oracle 11 est utilisé et la variable `JAVA_HOME` La variable d’environnement est définie sur `/usr/lib/jvm/jdk-11.0.2`. If `8` est spécifié, l’Oracle 8 est utilisé et la variable `JAVA_HOME` La variable d’environnement est définie sur `/usr/lib/jvm/jdk1.8.0_202`.

## Variables d’environnement {#environment-variables}

### Variables d’environnement standard {#standard-environ-variables}

Dans certains cas, il peut s’avérer nécessaire de modifier le processus de génération en fonction des informations sur le programme ou le pipeline.

Par exemple, si la minification JavaScript au moment de la génération est effectuée par le biais d’un outil comme gulp, il peut être nécessaire d’utiliser un niveau de minification différent lors de la création pour un environnement de développement plutôt que pour la création pour l’évaluation et la production.

Pour ce faire, Cloud Manager ajoute des variables d’environnement standard au conteneur de génération pour chaque exécution.

| Nom de variable | Description |
|---|---|
| `CM_BUILD` | Toujours définie sur `true` |
| `BRANCH` | Branche configurée pour l’exécution |
| `CM_PIPELINE_ID` | Identifiant numérique de pipeline |
| `CM_PIPELINE_NAME` | Nom du pipeline |
| `CM_PROGRAM_ID` | Identifiant numérique de programme |
| `CM_PROGRAM_NAME` | Nom du programme |
| `ARTIFACTS_VERSION` | Pour un pipeline d’évaluation ou de production, la version synthétique générée par Cloud Manager |

### Variables de pipeline {#pipeline-variables}

Dans certains cas, votre processus de création peut dépendre de variables de configuration spécifiques qui ne seraient pas appropriées pour le référentiel git ou qui doivent varier entre les exécutions de pipeline utilisant la même branche.

Cloud Manager permet de configurer ces variables par le biais de l’API Cloud Manager ou de l’interface de ligne de commande de Cloud Manager pour chaque pipeline. Les variables peuvent être stockées en texte brut ou chiffrées au repos. Dans les deux cas, les variables sont disponibles dans l’environnement de génération en tant que variable d’environnement qui peut ensuite être référencée à partir du fichier `pom.xml` ou d’autres scripts de génération.

Pour définir une variable à l’aide de l’interface en ligne de commande, exécutez une commande similaire à celle-ci.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Les variables actives peuvent être répertoriées à l’aide d’une commande similaire à celle-ci.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Les variables doivent respecter certaines limites.

* Les noms de variables ne peuvent contenir que des caractères alphanumériques et un trait de soulignement (`_`).
   * Par convention, les noms doivent être en majuscules.
* Il existe une limite de 200 variables par pipeline.
* Chaque nom doit comporter moins de 100 caractères.
* Chaque valeur de chaîne doit comporter moins de 2 048 caractères.
* Chaque valeur secretString doit comporter moins de et 500 caractères.

Lorsqu’il est utilisé dans un Maven `pom.xml` , il est généralement utile de mapper ces variables aux propriétés Maven à l’aide d’une syntaxe similaire à celle-ci.

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## Installation de packages système supplémentaires {#installing-additional-system-packages}

Pour fonctionner pleinement, certaines versions nécessitent l’installation de packages système supplémentaires. Par exemple, une version peut appeler un script Python ou Ruby et, par conséquent, doit avoir un interpréteur de langue approprié installé. Pour ce faire, appelez le plug-in [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) pour invoquer APT. Cette exécution doit généralement être encapsulée dans un profil Maven spécifique à Cloud Manager. Par exemple, pour installer Python :

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

Cette même technique peut être utilisée pour installer des packages spécifiques à la langue, c’est-à-dire utilisée `gem` pour les packages RubyGems ou `pip` pour les packages Python.

>[!NOTE]
>
>Installer un package système de cette manière ne l’installe pas dans l’environnement d’exécution utilisé pour Adobe Experience Manager. Si vous avez besoin d’installer un package système dans l’environnement AEM, contactez votre représentant Adobe.
