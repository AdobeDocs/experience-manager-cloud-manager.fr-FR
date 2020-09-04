---
title: Présentation de l'Environnement de création
description: Suivez cette page pour en savoir plus sur les environnements
translation-type: tm+mt
source-git-commit: f73ea3db4bc50891518bebbe5da2d69dd2890a81
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 96%

---


# Présentation de l&#39;Environnement de création {#build-environment-details}

Cloud Manager crée et teste votre code à l&#39;aide d&#39;un environnement de création spécialisé. Cet environnement comporte les attributs suivants :

* L&#39;environnement de création est basé sur Linux, dérivé de Ubuntu 18.04.
* Apache Maven 3.6.0 est installé.
* Les versions Java installées sont Oracle JDK 8u202 et 11.0.2.
* D’autres packages système nécessaires sont installés :

   * bzip2
   * unzip
   * libpng
   * imagemagick
   * graphicsmagick

* D&#39;autres packages peuvent être installés au moment de la création, comme décrit [ci-dessous](#installing-additional-system-packages).
* Chaque génération a lieu dans un environnement vierge ; le conteneur de génération ne conserve aucun état entre les exécutions.
* Maven est toujours exécuté avec les trois commandes suivantes :

   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`

* Maven est configuré au niveau du système avec un fichier settings.xml qui inclut automatiquement le référentiel public Adobe **Artifact**. (Pour plus d’informations, consultez le [référentiel Maven public d’Adobe](https://repo.adobe.com/)).

>[!NOTE]
>Bien que Cloud Manager ne définisse pas de version spécifique du `jacoco-maven-plugin`, la version utilisée doit être au moins `0.7.5.201505241946`.

## Utilisation de Java 11 {#using-java-11}

Cloud Manager prend désormais en charge la création de projets clients avec Java 8 et Java 11. Par défaut, les projets sont créés à l’aide de Java 8. Les clients souhaitant utiliser Java 11 dans leurs projets peuvent le faire via le module [Apache Maven Toolchain](https://maven.apache.org/plugins/maven-toolchains-plugin/).

À cet effet, dans le fichier pom.xml, ajoutez une `<plugin>` entrée du type suivant :

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

>[!NOTE]
>Les `vendor` valeurs prises en charge sont `oracle` et `sun`, et les `version` valeurs prises en charge sont `1.8`, `1.11`et `11`.

## Variables d’environnement {#environment-variables}

### Variables d’environnement standard {#standard-environ-variables}

Dans certains cas, les clients jugent nécessaire de modifier le processus de génération en fonction des informations sur le programme ou le pipeline.

Par exemple, si la minification JavaScript au moment de la génération est effectuée via un outil comme gulp, il peut être nécessaire d’utiliser un autre niveau de minification lors de la génération pour un environnement de développement et pour des environnements intermédiaire et de production.

Pour la prise en charge, Cloud Manager ajoute ces variables d’environnement standard au conteneur de build pour chaque exécution.

| **Nom de variable** | **Définition** |
|---|---|
| CM_BUILD | Toujours définie sur &quot;true&quot; |
| BRANCHE | Branche configurée pour l’exécution |
| CM_PIPELINE_ID | Identifiant numérique de pipeline |
| CM_PIPELINE_NAME | Nom du pipeline |
| CM_PROGRAM_ID | Identifiant numérique de programme |
| CM_PROGRAM_NAME | Nom du programme |
| ARTIFACTS_VERSION | Pour un pipeline intermédiaire ou de production, version synthétique générée par Cloud Manager |

### Variables de pipeline {#pipeline-variables}

Dans certains cas, le processus de génération d’un client peut dépendre de variables de configuration spécifiques qui ne seraient pas appropriées pour le référentiel Git ou qui doivent varier entre les exécutions de pipeline utilisant la même branche.

Cloud Manager permet de configurer ces variables par le biais de l’API Cloud Manager ou de l’interface de ligne de commande de Cloud Manager pour chaque pipeline. Les variables peuvent être stockées en texte brut ou chiffrées au repos. Dans les deux cas, les variables sont disponibles dans l’environnement de génération en tant que variable d’environnement qui peut ensuite être référencée à partir du fichier `pom.xml` ou d’autres scripts de génération.

Pour définir une variable à l’aide de l’interface de ligne de commande, exécutez une commande du type :

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

Les variables actives peuvent être répertoriées :

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

Les noms des variables ne peuvent contenir que des caractères alphanumériques et des caractères de soulignement (_). Par convention, les noms doivent être entièrement en majuscules. Il existe une limite de 200 variables par pipeline, chaque nom doit comporter moins de 100 caractères et chaque valeur doit être inférieure à 2 048 caractères.

En cas d’utilisation dans un fichier `Maven pom.xml`, il est généralement utile de mapper ces variables aux propriétés Maven en suivant une syntaxe similaire à celle-ci :

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

Certaines versions nécessitent d&#39;autres packages système pour fonctionner entièrement. Par exemple, une version peut appeler un script Python ou ruby et, par conséquent, doit se voir installer un interprète de langue approprié. Pour ce faire, appelez le plug-in [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) pour invoquer APT. Cette exécution doit généralement être encapsulée dans un profil Maven spécifique à Cloud Manager. Par exemple, pour installer Python :

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
>Installer un package système de cette manière ne l&#39;installe **pas** dans l&#39;environnement d&#39;exécution utilisé pour exécuter Adobe Experience Manager. Si vous avez besoin d&#39;installer un package système dans l&#39;environnement AEM, contactez vos ingénieurs de la réussite client (CSE).