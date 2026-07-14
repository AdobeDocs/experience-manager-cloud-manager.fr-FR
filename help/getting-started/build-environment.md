---
title: Environnement de création
description: Découvrez l’environnement de création spécialisé dans lequel les utilisateurs et utilisatrices de Cloud Manager peuvent créer et tester votre code.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
TQID: https://experienceleague.adobe.com/AdGVWjyF0DXEX7jH5S39JQ506oVnNYGtYqAWNHcQeP8
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552eid: cd2426f1-5719-4006-b8c2-738e5969754b
subfeature_v2: id: d9eb3b3e-9447-4ed4-bf4a-96c7b245cb27
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 1692390e24f8fa7d719bd8293a99586ec4ec36d4
workflow-type: tm+mt
source-wordcount: 1205
ht-degree: 50%

---

# Environnement de création {#build-environment}

Découvrez l’environnement de création spécialisé utilisé par Cloud Manager pour créer et tester votre code.

## Détails de l’environnement {#details}

Les environnements de création de Cloud Manager possèdent les attributs suivants.

* L’environnement de création est basé sur Linux, dérivé de Ubuntu 22.04.
* Apache Maven 3.9.4 est installé.
   * Adobe recommande aux utilisateurs et utilisatrices de [mettre à jour leurs référentiels Maven de sorte à utiliser HTTPS au lieu de HTTP](#https-maven).
* Les versions Java installées sont Oracle JDK 8u401 et Oracle JDK 11.0.22.
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* Par défaut, la variable d’environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk1.8.0_401` qui contient Oracle JDK 8u401. Consultez la section [ Autre version du JDK d’exécution de Maven ](#alternate-maven) pour plus d’informations.
* D’autres packages système nécessaires sont installés.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* D’autres packages sont installés au moment de la génération, comme décrit dans la section [Installation de packages système supplémentaires](#installing-additional-system-packages).
* Chaque génération est effectuée dans un nouvel environnement. Le conteneur de build ne conserve pas les données entre les exécutions.
* Maven est exécuté avec les trois commandes suivantes :
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven est configuré au niveau du système avec un fichier `settings.xml` qui inclut automatiquement le référentiel public d’artefacts Adobe à l’aide d’un profil appelé `adobe-public`. Pour plus d’informations, voir le [référentiel Maven public d’Adobe](https://repo1.maven.org/).
* Node.js 18 est disponible pour les [pipelines front-end](/help/overview/ci-cd-pipelines.md).

>[!IMPORTANT]
>La prise en charge des chaînes d’outils Maven a été supprimée à partir de la version Cloud Manager 2025.06.0. La sélection du JDK est désormais prise en charge uniquement via `.cloudmanager/java-version`. Pour plus d’informations, voir [ Utilisation d’une version Java spécifique ](#using-java-version).

>[!NOTE]
>
>Bien que Cloud Manager ne définisse pas de version spécifique du `jacoco-maven-plugin`, la version utilisée doit être au moins `0.7.5.201505241946`.

>[!TIP]
>
>Pour savoir comment utiliser les API Cloud Manager, consultez les ressources supplémentaires suivantes :
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Création d’une intégration d’API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration)
>* [Autorisations d’API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions)

## Référentiels Maven HTTPS {#https-maven}

Cloud Manager [2023.10.0](/help/release-notes/2023/2023-10-0.md) a commencé une mise à jour progressive de l’environnement de création (achevée avec la version 2023.12.0), qui incluait une mise à jour de Maven 3.8.8. Une modification introduite dans Maven 3.8.1 était une amélioration de la sécurité pour répondre aux vulnérabilités potentielles. Plus précisément, Maven désactive désormais par défaut tous les miroirs `http://*` non sécurisés, comme indiqué dans les [Notes de mise à jour de Maven](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291).

Certains utilisateurs rencontrent des problèmes lors de l’étape de création lors du téléchargement d’artefacts à partir de référentiels Maven qui utilisent des connexions HTTP non sécurisées.

Pour garantir une expérience fluide avec la version mise à jour, Adobe recommande aux utilisateurs et utilisatrices de mettre à jour leurs référentiels Maven de sorte à utiliser HTTPS au lieu de HTTP. Cet ajustement soutient la transition de l&#39;industrie vers des protocoles de communication sécurisés et maintient un processus de création sécurisé et fiable.

## Utiliser une version de Java spécifique {#using-java-version}

Par défaut, les projets créés par le processus de création Cloud Manager utilisent le JDK Oracle 8. Les clients qui souhaitent utiliser un autre JDK peuvent sélectionner une autre version de JDK pour l’ensemble du processus d’exécution Maven.

>[!IMPORTANT]
>
>Les chaînes d’outils Maven ne sont plus prises en charge dans Cloud Manager 2025.06.0. N’oubliez pas que les pipelines contenant une configuration maven-toolchains-plugin échouent avec `Cannot find matching toolchain definitions.` Utilisez le fichier `.cloudmanager/java-version` pour sélectionner JDK 11, 17 ou 21 à la place.
>
>**Conseils de migration :**
>
>1. Supprimez les chaînes d&#39;outils en supprimant toute entrée de `org.apache.maven.plugins:maven-toolchains-plugin` et tout `toolchains.xml` validé dans votre contrôle de code source.
>1. Sélectionnez un JDK avec des `.cloudmanager/java-version` (21, 17 ou 11), comme décrit dans la section [ Autre version du JDK d’exécution Maven ](#alternate-maven).
>1. Adobe recommande d’effacer le cache de build de Cloud Manager ou de déclencher une nouvelle exécution de pipeline.
>

<!--
DEPRECATED 
### Maven Toolchains {#maven-toolchains}

The [Maven Toolchains plug-in](https://maven.apache.org/plugins/maven-toolchains-plugin/) lets projects select a specific JDK (or toolchain) to use in the context of toolchains-aware Maven plug-ins. This process is done in the project's `pom.xml` file by specifying a vendor and version value. A sample section in the `pom.xml` file is the following:

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

This process causes all toolchains-aware Maven plug-ins to use the Oracle JDK, version 11.

When using this method, Maven itself still runs using the default JDK (Oracle 8) and the `JAVA_HOME` environment variable is not changed. Therefore, checking or enforcing the Java version through plug-ins like the [Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) does not work and such plug-ins must not be used.

The currently available vendor/version combinations are:

|Vendor|Version|
|---|---|
| Oracle |1.8|
| Oracle |1.11|
| Oracle |11|
| Sun |1.8|
| Sun |1.11|
| Sun |11|

>[!NOTE]
>
>Starting April 2022, Oracle JDK is going to be the default JDK for the development and operation of AEM applications. Cloud Manager's build process automatically switches to using Oracle JDK, even if an alternative option is explicitly selected in the Maven toolchain. See the [April release notes](/help/release-notes/2022/2022-4-0.md) for more details.
-->

### Autre version du JDK d’exécution Maven {#alternate-maven}

Il est possible de sélectionner Oracle 8 ou Oracle 11 en tant que JDK pour l’ensemble de l’exécution de Maven. Cette approche modifie le JDK utilisé pour tous les plug-ins. Par conséquent, la vérification et l’application de la version Java à l’aide du [module externe Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) sont prises en charge.

Pour effectuer ce processus, créez un fichier nommé `.cloudmanager/java-version` dans la branche de référentiel Git utilisée par le pipeline. Ce fichier peut avoir le contenu `11` ou `8`. Toute autre valeur est ignorée. Si `11` est spécifié, le système utilise Oracle 11 et définit la variable d’environnement `JAVA_HOME` sur `/usr/lib/jvm/jdk-11.0.22`. Si `8` est spécifié, le système utilise Oracle 8 et définit la variable d’environnement `JAVA_HOME` sur `/usr/lib/jvm/jdk1.8.0_401`.

## Variables d’environnement {#environment-variables}

### Variables d’environnement standard {#standard-environ-variables}

Dans certains cas, il est nécessaire de modifier le processus de création en fonction des informations sur le programme ou le pipeline.

Par exemple, lorsque vous utilisez un outil tel que gulp pour la minification de JavaScript, utilisez différents niveaux de minification pour les environnements de développement et d’évaluation et de production.

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

Seules les variables d’environnement normales peuvent être utilisées avec le [Dispatcher](https://experienceleague.adobe.com/fr/docs/experience-manager-dispatcher/using/dispatcher). Les secrets ne peuvent pas être utilisés.

Toutefois, les variables d’environnement ne peuvent pas être utilisées dans les directives `IfDefine`.

>[!TIP]
>
>Vous devez valider l’utilisation des variables d’environnement avec le [Dispatcher localement](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools) avant le déploiement.

#### Configurations OSGi {#osgi}

Les variables d’environnement normales et les secrets peuvent être utilisés dans les [configurations OSGi](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi).

### Variables de pipeline {#pipeline-variables}

Dans certains cas, le processus de création dépend de variables de configuration spécifiques. Ces variables ne sont pas appropriées pour le référentiel Git ou doivent varier entre les exécutions de pipeline utilisant la même branche.

Cloud Manager permet de configurer ces variables par le biais de l’API Cloud Manager ou de l’interface de ligne de commande de Cloud Manager pour chaque pipeline. Les variables sont stockées en tant que texte brut ou chiffrées au repos. Dans les deux cas, les variables sont disponibles dans l’environnement de création en tant que variable d’environnement qui peut ensuite être référencée depuis le fichier `pom.xml` ou d’autres scripts de création.

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
   * Par convention, les noms sont tous en majuscules.
* Il existe une limite de 200 variables par pipeline.
* Chaque nom doit comporter moins de 100 caractères.
* La valeur de chaque chaîne doit comporter moins de 2 048 caractères.
* Chaque valeur `secretString` doit comporter moins de 500 caractères.

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

## Installer des packages système supplémentaires {#installing-additional-system-packages}

Pour fonctionner correctement, certaines versions nécessitent l’installation de packages système supplémentaires. Par exemple, une version appelle un script Python ou Ruby et nécessite l’installation d’un interprète de langue approprié. Ce scénario peut être géré en appelant la [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) pour appeler APT. Cette exécution est encapsulée dans un profil Maven spécifique à Cloud Manager. Par exemple, pour installer Python, vous pouvez effectuer les opérations suivantes :

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

Cette méthode peut également être utilisée pour installer des packages spécifiques à la langue. En d’autres termes, utilisez `gem` pour les packages RubyGems ou `pip` pour les packages Python.

>[!NOTE]
>
>Installer un package système de cette manière ne l’installe pas dans l’environnement d’exécution utilisé pour Adobe Experience Manager. Si vous avez besoin d’installer un package système dans l’environnement AEM, contactez votre représentant Adobe.
