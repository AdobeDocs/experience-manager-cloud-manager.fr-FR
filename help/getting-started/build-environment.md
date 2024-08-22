---
title: Environnement de création
description: Découvrez l’environnement de création spécialisé, dans lequel les utilisateurs Cloud Manager peuvent créer et tester votre code.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 53%

---


# Environnement de création {#build-environment}

Découvrez l’environnement de création spécialisé, dans lequel les utilisateurs Cloud Manager peuvent créer et tester votre code.

## Détails de l’environnement {#details}

Les environnements de création Cloud Manager possèdent les attributs suivants.

* L’environnement de création est basé sur Linux, dérivé de Ubuntu 22.04.
* Apache Maven 3.9.4 est installé.
   * Adobe recommande aux utilisateurs [de mettre à jour leurs référentiels Maven pour utiliser HTTPS au lieu de HTTP](#https-maven).
* Les versions Java installées sont Oracle JDK 8u401 et Oracle JDK 11.0.22.
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* Par défaut, la variable d’environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk1.8.0_401`, qui contient le JDK Oracle 8u401. Consultez la section [Autre version du JDK d’exécution de Maven](#alternate-maven) pour plus de détails.
* D’autres packages système nécessaires sont installés.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* D’autres packages peuvent être installés au moment de la création, comme décrit dans la section [Installation de packages système supplémentaires](#installing-additional-system-packages).
* Chaque construction est faite dans un environnement vierge. Le conteneur de génération ne conserve aucun état entre les exécutions.
* Maven est toujours exécuté avec les trois commandes suivantes :
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven est configuré au niveau du système avec un fichier `settings.xml` qui inclut automatiquement le référentiel public d’artefacts Adobe à l’aide d’un profil appelé `adobe-public`. Pour plus d’informations, voir le [référentiel Maven public Adobe](https://repo1.maven.org/) .
* Node.js 18 est disponible pour les [pipelines front-end](/help/overview/ci-cd-pipelines.md).

>[!NOTE]
>
>Bien que Cloud Manager ne définisse pas de version spécifique du `jacoco-maven-plugin`, la version utilisée doit être au moins `0.7.5.201505241946`.

>[!TIP]
>
>Consultez les ressources supplémentaires suivantes pour savoir comment utiliser les API Cloud Manager :
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Création d’une intégration d’API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [Autorisations d’API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)

## Référentiels HTTPS Maven {#https-maven}

Cloud Manager [2023.10.0](/help/release-notes/2023/2023-10-0.md) a commencé une mise à jour continue de l’environnement de création (avec la version 2023.12.0), qui incluait une mise à jour de Maven 3.8.8. Un changement significatif introduit dans Maven 3.8.1 a été une amélioration de la sécurité visant à atténuer les vulnérabilités potentielles. Plus précisément, Maven désactive désormais par défaut tous les miroirs `http://*` non sécurisés, comme indiqué dans les [ notes de mise à jour de Maven](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291).

Suite à cette amélioration de la sécurité, certaines personnes peuvent rencontrer des problèmes lors de l’étape de création, en particulier lors du téléchargement d’artefacts à partir de référentiels Maven qui utilisent des connexions HTTP non sécurisées.

Pour garantir une expérience fluide avec la version mise à jour, Adobe recommande aux utilisateurs et utilisatrices de mettre à jour leurs référentiels Maven de sorte à utiliser HTTPS au lieu de HTTP. Cet ajustement s’aligne sur la transition croissante du secteur vers des protocoles de communication sécurisés et contribue à maintenir un processus de création sécurisé et fiable.

## Utilisation d’une version Java spécifique {#using-java-version}

Par défaut, les projets créés par le processus de génération Cloud Manager utilisent le JDK Oracle 8. Les clients qui souhaitent utiliser un autre JDK disposent de deux options.

* [Maven Toolchains](#maven-toolchains)
* [Sélectionner une autre version du JDK pour l’ensemble du processus d’exécution de Maven](#alternate-maven)

### Maven Toolchains {#maven-toolchains}

Le [plug-in Maven Toolchain](https://maven.apache.org/plugins/maven-toolchains-plugin/) permet aux projets de sélectionner un JDK spécifique (ou toolchain) à utiliser dans le contexte des plug-ins Maven prenant en charge les chaînes d’outils. Ce processus est effectué dans le fichier `pom.xml` du projet en spécifiant un fournisseur et une valeur de version. Voici un exemple de section dans le fichier `pom.xml` :

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

Ce processus entraîne l’utilisation par tous les modules externes Maven prenant en charge les chaînes d’outils du JDK Oracle, version 11.

Lors de l’utilisation de cette méthode, Maven s’exécute toujours en utilisant le JDK par défaut (Oracle 8) et la variable d’environnement `JAVA_HOME` n’est pas modifiée. Par conséquent, la vérification ou l’application de la version Java par le biais de plug-ins tels que le [module externe Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) ne fonctionne pas et ces plug-ins ne doivent pas être utilisés.

Les combinaisons fournisseur/version actuellement disponibles sont les suivantes :

| Fournisseur | Version |
|---|---|
| Oracle | 1.8 |
| Oracle | 1.11 |
| Oracle | 11 |
| dim. | 1.8 |
| dim. | 1.11 |
| dim. | 11 |

>[!NOTE]
>
>À compter d’avril 2022, le JDK Oracle sera le JDK par défaut pour le développement et le fonctionnement des applications AEM. Le processus de génération de Cloud Manager passe automatiquement à l’utilisation du JDK Oracle, même si une autre option est explicitement sélectionnée dans la chaîne d’outils Maven. Pour plus d’informations, voir les [notes de mise à jour d’avril](/help/release-notes/2022/2022-4-0.md) .

### Autre version du JDK d’exécution Maven {#alternate-maven}

Il est également possible de sélectionner Oracle 8 ou Oracle 11 en tant que JDK pour l’ensemble de l’exécution de Maven. Contrairement aux options des chaînes d’outils, cela modifie le JDK utilisé pour tous les modules externes, sauf si la configuration des chaînes d’outils est également définie, auquel cas la configuration des chaînes d’outils est toujours appliquée aux modules externes Maven prenant en charge les chaînes d’outils. Par conséquent, la vérification et l’application de la version Java à l’aide du [module externe Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) fonctionnent.

Pour ce faire, créez un fichier nommé `.cloudmanager/java-version` dans la branche de référentiel Git utilisée par le pipeline. Ce fichier peut avoir le contenu `11` ou `8`. Toute autre valeur est ignorée. Si `11` est spécifié, Oracle 11 est utilisé et la variable d’environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk-11.0.22`. Si `8` est spécifié, Oracle 8 est utilisé et la variable d’environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk1.8.0_401`.

## Variables d’environnement {#environment-variables}

### Variables d’environnement standard {#standard-environ-variables}

Dans certains cas, les clients jugeront nécessaire de modifier le processus de création en fonction des informations sur le programme ou le pipeline.

Par exemple, lorsque vous utilisez un outil tel que gulp pour la minification JavaScript, vous pouvez préférer différents niveaux de minification pour les environnements de développement plutôt que d’évaluation et de production.

Pour la prise en charge, Cloud Manager ajoute des variables d’environnement standard au conteneur de création pour chaque exécution.

| Nom de variable | Description |
|---|---|
| `CM_BUILD` | Toujours définie sur `true` |
| `BRANCH` | Branche configurée pour l’exécution |
| `CM_PIPELINE_ID` | Identifiant numérique de pipeline |
| `CM_PIPELINE_NAME` | Nom du pipeline |
| `CM_PROGRAM_ID` | Identifiant numérique de programme |
| `CM_PROGRAM_NAME` | Nom du programme |
| `ARTIFACTS_VERSION` | Pour un pipeline d’évaluation ou de production, la version synthétique générée par Cloud Manager |

### Disponibilité des variables d’environnement standard {#availability}

Les variables d’environnement standard peuvent être utilisées à plusieurs endroits.

#### Environnements de création, de prévisualisation et de publication {#author-preview-publish}

Les variables d’environnement standard et les secrets peuvent être utilisés dans les environnements de création, de prévisualisation et de publication.

#### Dispatcher {#dispatcher}

Seules les variables d&#39;environnement standard peuvent être utilisées avec [le Dispatcher](https://experienceleague.adobe.com/fr/docs/experience-manager-dispatcher/using/dispatcher). Les secrets ne peuvent pas être utilisés.

Cependant, les variables d&#39;environnement ne peuvent pas être utilisées dans les directives `IfDefine`.

>[!TIP]
>
>Validez l’utilisation des variables d’environnement avec le [Dispatcher local](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools) avant le déploiement.

#### Configurations OSGi {#osgi}

Les variables d’environnement normales et les secrets peuvent être utilisés dans les [configurations OSGi](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi).

### Variables de pipeline {#pipeline-variables}

Dans certains cas, votre processus de création peut dépendre de variables de configuration spécifiques qui ne seraient pas appropriées pour le référentiel Git ou qui doivent varier entre les exécutions de pipeline utilisant la même branche.

Cloud Manager permet de configurer ces variables par le biais de l’API Cloud Manager ou de l’interface de ligne de commande de Cloud Manager pour chaque pipeline. Les variables peuvent être stockées en texte brut ou chiffrées au repos. Dans les deux cas, les variables sont disponibles dans l’environnement de génération en tant que variable d’environnement, qui peut ensuite être référencée à partir du fichier `pom.xml` ou d’autres scripts de génération.

Pour définir une variable à l’aide de l’interface de ligne de commande, exécutez une commande similaire à la suivante.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Les variables actuelles peuvent être répertoriées à l’aide d’une commande similaire à la suivante.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Les variables doivent respecter certaines limites.

* Les noms de variables ne peuvent contenir que des caractères alphanumériques et le trait de soulignement (`_`).
   * Par convention, les noms doivent être entièrement en majuscules.
* Il existe une limite de 200 variables par pipeline.
* Chaque nom doit comporter moins de 100 caractères.
* Chaque valeur de chaîne doit comporter moins de 2 048 caractères.
* Chaque valeur `secretString` doit comporter moins de 500 caractères.

En cas d’utilisation dans un fichier `pom.xml` Maven, il est généralement recommandé de mapper ces variables aux propriétés Maven en utilisant une syntaxe similaire à la suivante.

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

Pour fonctionner correctement, certaines versions nécessitent l’installation de packages système supplémentaires. Par exemple, une version peut appeler un script Python ou Ruby et, par conséquent, nécessiter l’installation d’un interprète de langue approprié. Ce scénario peut être réalisé en appelant [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) pour appeler APT. Cette exécution doit généralement être encapsulée dans un profil Maven spécifique à Cloud Manager. Par exemple, pour installer Python, vous pouvez effectuer les opérations suivantes :

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

Cette technique peut également être utilisée pour installer des packages spécifiques à la langue. Autrement dit, utilisez `gem` pour RubyGems ou `pip` pour les packages Python.

>[!NOTE]
>
>Installer un package système de cette manière ne l’installe pas dans l’environnement d’exécution utilisé pour Adobe Experience Manager. Si vous avez besoin d’installer un package système dans l’environnement AEM, contactez votre représentant Adobe.
