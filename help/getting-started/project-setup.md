---
title: Configurer votre projet
description: Découvrez comment configurer votre projet afin de pouvoir le gérer et le déployer avec Cloud Manager.
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
TQID: https://experienceleague.adobe.com/OhaZ2-x6p1b6aF0xHwr2G-RNTYPd15pqHVxKVwv-GDM
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: fa6be369b979682cebf68852603725d8754605ab
workflow-type: tm+mt
source-wordcount: 1411
ht-degree: 65%

---

# Configurer votre projet {#setting-up-your-project}

Découvrez comment configurer votre projet afin de pouvoir le gérer et le déployer avec Cloud Manager.

## Modifier des projets existants {#modifying-project-setup-details}

Les projets AEM existants doivent respecter certaines règles de base pour pouvoir être créés et déployés avec Cloud Manager.

* Les projets doivent être créés à l’aide d’Apache Maven.
* Un fichier `pom.xml` doit se trouver à la racine du référentiel Git.
   * Ce fichier `pom.xml` peut faire référence à autant de sous-modules (qui à leur tour comportent d’autres sous-modules) que nécessaire.
   * Vous pouvez ajouter des références à d’autres référentiels d’artefact Maven dans vos fichiers `pom.xml`.
   * L’accès aux [référentiels d’artefacts protégés par mot de passe](#password-protected-maven-repositories) est pris en charge s’il est configuré. Cependant, l’accès aux référentiels d’artefacts protégés par réseau n’est pas pris en charge.
* Cloud Manager détecte les packages de contenu déployables en analysant les fichiers ZIP de packages de contenu contenus dans un répertoire nommé `target`.
   * Un nombre illimité de sous-modules produit des packages de contenu.
* Cloud Manager détecte les artefacts Dispatcher déployables en recherchant les fichiers `zip` contenus dans des sous-répertoires de `target` nommés `conf` et `conf.d`.
* S’il existe plusieurs modules de contenu, l’ordre des déploiements des modules n’est pas garanti.
   * Si un ordre spécifique est nécessaire, il est possible d’utiliser les dépendances de module de contenu pour le définir.
* Les packages peuvent être [ignorés](#skipping-content-packages) du déploiement.

## Activer des profils Maven dans Cloud Manager {#activating-maven-profiles-in-cloud-manager}

Dans certains cas, modifiez légèrement le processus de génération lors de l’exécution dans Cloud Manager. Cela diffère de quand il s&#39;exécute sur les postes de travail des développeurs. Pour ces cas, les [Profils Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) définissent la manière dont la version diffère selon les environnements, y compris Cloud Manager.

L’activation d’un profil Maven dans l’environnement de création Cloud Manager doit se faire en recherchant la `CM_BUILD` [variable d’environnement](/help/getting-started/build-environment.md#environment-variables). À l’inverse, un profil destiné à être utilisé uniquement en dehors de l’environnement de création Cloud Manager doit être activé en vérifiant l’absence de cette variable.

Par exemple, si vous souhaitez générer un message simple uniquement lorsque la version s’exécute dans Cloud Manager, procédez comme suit :

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>Pour tester ce profil sur un poste de travail de développement, vous pouvez l’activer sur la ligne de commande (avec `-PcmBuild`) ou dans l’environnement de développement intégré (IDE).

Et si vous souhaitez générer un message simple uniquement lorsque la version s’exécute en dehors de Cloud Manager, procédez comme suit :

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

## Prise en charge d’un référentiel Maven protégé par mot de passe {#password-protected-maven-repositories}

Les artefacts d’un référentiel Maven protégé par mot de passe doivent être utilisés avec précaution, car le code déployé de cette manière n’est pas entièrement soumis aux contrôles de qualité appliqués par les normes de qualité de Cloud Manager. Adobe vous conseille également de déployer les sources Java et l’ensemble du code source du projet avec le binaire .

>[!TIP]
>
>Les artefacts des référentiels Maven protégés par mot de passe ne doivent être utilisés que dans de rares cas et pour le code qui n’est pas lié à AEM.

Pour utiliser un référentiel Maven protégé par mot de passe dans Cloud Manager, spécifiez le mot de passe (et éventuellement le nom d’utilisateur ou d’utilisatrice) en tant que [Variable de pipeline](/help/getting-started/build-environment.md#pipeline-variables) secrète, puis référencez ce secret dans un fichier nommé `.cloudmanager/maven/settings.xml` dans le référentiel Git. Ce fichier suit le schéma du [fichier de paramètres Maven](https://maven.apache.org/settings.html).

Au démarrage du processus de création de Cloud Manager, l’élément `<servers>` de ce fichier est fusionné dans le fichier `settings.xml` par défaut fourni par Cloud Manager. Les serveurs personnalisés utilisent des identifiants de serveur qui ne commencent pas par `adobe` ou `cloud-manager`. Ces identifiants sont considérés comme réservés. Cloud Manager ne reflète que les ID de serveur correspondant à l’un des préfixes spécifiés ou à l’ID par défaut `central`.

Une fois ce fichier en place, l’ID de serveur est référencé à l’intérieur d’un élément `<repository>` et/ou `<pluginRepository>` dans le fichier `pom.xml`. Ces éléments `<repository>` et/ou `<pluginRepository>` sont contenus dans un profil spécifique à [Cloud Manager](#activating-maven-profiles-in-cloud-manager), bien que cela ne soit pas strictement nécessaire.

Supposons, par exemple, que le référentiel se trouve à l’adresse `https://repository.myco.com/maven2`, que le nom d’utilisateur utilisé par Cloud Manager soit `cloudmanager` et que le mot de passe soit `secretword`.

Tout d’abord, définissez le mot de passe comme secret sur le pipeline :

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

Faites ensuite référence à l’élément suivant à partir du fichier `.cloudmanager/maven/settings.xml` :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

Enfin, faites référence à l’identifiant du serveur dans le fichier `pom.xml` :

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
        <build>
            <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
        </build>
    </profile>
</profiles>
```

### Déployer des sources {#deploying-sources}

Il est recommandé de déployer les sources Java avec le binaire dans un référentiel Maven.

Configurez le `maven-source-plugin` dans votre projet :

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-source-plugin</artifactId>
            <executions>
                <execution>
                    <id>attach-sources</id>
                    <goals>
                        <goal>jar-no-fork</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
```

### Déployer des sources de projet {#deploying-project-sources}

Il est recommandé de déployer l’ensemble du code source du projet avec le binaire dans un référentiel Maven. Ce procédé permet de reconstruire l’artefact exact.

Configurez le `maven-assembly-plugin` dans votre projet :

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <executions>
                <execution>
                    <id>project-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                    <configuration>
                        <descriptorRefs>
                            <descriptorRef>project</descriptorRef>
                        </descriptorRefs>
                    </configuration>
                </execution>
            </executions>
        </plugin>
```

## Ignorer les modules de contenu {#skipping-content-packages}

Dans Cloud Manager, les versions peuvent produire un nombre illimité de packages de contenu. Pour diverses raisons, il peut être préférable de produire un package de contenu, mais de ne pas le déployer. Par exemple, cette approche peut se révéler utile lorsque vous créez des modules de contenu uniquement à des fins de test ou lorsqu’une autre étape du processus de compilation les recompile. C’est-à-dire sous forme de sous-package d’un autre package.

Pour tenir compte de ces scénarios, Cloud Manager recherche une propriété nommée `cloudManagerTarget` dans les propriétés des modules de contenu créés. Si cette propriété est définie sur `none`, le package est ignoré et n’est pas déployé. Le mécanisme permettant de définir cette propriété dépend de la manière dont la création produit le module de contenu. Par exemple, avec le `filevault-maven-plugin` , configurez le plug-in comme suit :

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

La procédure est similaire avec le `content-package-maven-plugin` :

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

## Réutiliser l’artefact de création {#build-artifact-reuse}

Dans de nombreux cas, le même code est déployé dans plusieurs environnements AEM. Dans la mesure du possible, Cloud Manager évite de reconstruire la base du code lorsqu’il détecte que la même validation Git est utilisée dans plusieurs exécutions de pipelines de pile pleine.

Lorsqu’une exécution est lancée, la validation HEAD en cours pour le pipeline de branche est extraite. Le hachage de validation est visible dans l’IU et via l’API. Une fois l’étape de build terminée, les artefacts obtenus sont stockés en fonction de ce hachage de validation et peuvent être réutilisés dans les exécutions ultérieures du pipeline.

Les packages sont réutilisés sur plusieurs pipelines s’ils se trouvent dans le même programme. Lorsque vous recherchez des packages qui peuvent être réutilisés, AEM ignore les branches et réutilise les artefacts entre les branches.

En cas de réutilisation, les étapes de build et de qualité du code sont effectivement remplacées par les résultats de l’exécution initiale. Le fichier journal de l’étape de création répertorie les artefacts et les informations d’exécution qui ont été utilisées pour les créer à l’origine.

Voici un exemple dʼune telle sortie de journal.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

Le journal de l’étape de qualité du code contient des informations similaires.

### Exemples {#example-reuse}

#### Exemple 1 {#example-1}

Partez du principe que votre programme comporte deux pipelines de développement :

* Le pipeline 1 sur la branche `foo`
* Le pipeline 2 sur la branche `bar`

Les deux branches utilisent le même identifiant de validation.

1. L’exécution du pipeline 1 lance la construction normale des packages.
1. L’exécution du pipeline 2 entraîne ensuite la réutilisation des packages créés par le pipeline 1.

#### Exemple 2 {#example-2}

Supposons que votre programme comporte deux branches : Branche `foo` et Branche `bar`.

Les deux branches ont le même identifiant de validation.

1. Un pipeline de développement crée et exécute `foo`.
1. Par la suite, un pipeline de production crée et exécute `bar`.

Dans ce cas, l’artefact de `foo` est réutilisé pour le pipeline de production, car le même hachage de validation a été identifié.

### Opt-out {#opting-out}

Si vous le souhaitez, le comportement de réutilisation peut être désactivé pour des pipelines spécifiques en définissant la variable de pipeline `CM_DISABLE_BUILD_REUSE` sur `true`. Si cette variable est définie, le hachage de validation est toujours extrait. Les artefacts ainsi obtenus sont stockés pour une utilisation ultérieure, mais aucun artefact précédemment stocké n’est réutilisé. Pour comprendre ce comportement, considérez le scénario suivant :

1. Un pipeline est créé.
1. Le pipeline est exécuté (exécution #1) et la validation HEAD en cours est `becdddb`. L’exécution est réussie et les artefacts obtenus sont stockés.
1. La variable `CM_DISABLE_BUILD_REUSE` est définie.
1. Le pipeline est exécuté à nouveau sans modifier le code. Bien que des artefacts stockés soient associés à `becdddb`, ils ne sont pas réutilisés en raison de la variable `CM_DISABLE_BUILD_REUSE`.
1. Le code est modifié et le pipeline est exécuté. La validation HEAD est maintenant `f6ac5e6`. L’exécution est réussie et les artefacts obtenus sont stockés.
1. La variable `CM_DISABLE_BUILD_REUSE` est supprimée.
1. Le pipeline est exécuté à nouveau sans modifier le code. Puisque des artefacts stockés sont associés à `f6ac5e6`, ces artefacts sont réutilisés.

### Avertissements {#caveats}

* Les artefacts de build ne sont pas réutilisés dans différents programmes, que le hachage de validation soit identique ou non.
* Les artefacts de build sont réutilisés dans le même programme même si la branche et/ou le pipeline sont différents.
* [Gestion des versions Maven](/help/managing-code/maven-project-version.md) remplace la version du projet uniquement dans les pipelines de production. Si la même validation est utilisée pour les pipelines de développement et de production et que le pipeline de développement s’exécute en premier, les versions sont déployées dans les environnements d’évaluation et de production sans changer. Cependant, une balise sera toujours créée dans cette situation.
* Si la récupération des artefacts stockés échoue, l’étape de création est exécutée comme si aucun artefact n’avait été stocké.
* Les variables de pipeline autres que `CM_DISABLE_BUILD_REUSE` ne sont pas prises en compte lorsque Cloud Manager décide de réutiliser des artefacts de version créés précédemment.

## Développer du code en fonction des bonnes pratiques {#develop-your-code-based-on-best-practices}

Les équipes d’ingénierie et de conseil Adobe ont développé [un ensemble complet de bonnes pratiques pour les développeurs et développeuses AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/developing/bestpractices/best-practices).
