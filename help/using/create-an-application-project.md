---
title: Création d’un projet d’application AEM
seo-title: Création d’un projet d’application AEM
description: 'null'
seo-description: Consultez cette page pour en savoir plus sur la configuration d’un projet AEM lors de la prise en main de Cloud Manager.
uuid: 7b976ebf-5358-49d8-a58d-0bae026303fa
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: Guide de démarrage
discoiquuid: 76c1a8e4-d66f-4a3b-8c0c-b80c9e17700e
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Création d’un projet d’application AEM {#create-an-aem-application-project}

## Utilisation de l’assistant pour créer un projet d’application AEM {#using-wizard-to-create-an-aem-application-project}

Lorsque les clients se connectent à Cloud Manager, ils reçoivent un référentiel git vide. Les clients Adobe Managed Services (AMS) actuels (ou clients AEM sur site qui migrent vers AMS) auront généralement déjà leur code de projet dans git (ou un autre système de contrôle de version) et importeront leur projet dans le référentiel git Cloud Manager. Toutefois, les nouveaux clients n’ont pas de projets existants.

Pour faciliter la prise en main des nouveaux clients, Cloud Manager peut désormais créer un projet AEM minimal comme point de départ. Ce processus repose sur l&#39;archétype du projet [**AEM**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T12:52:50.071-0400

2018.8.0: Added this new section

 -->

Suivez les étapes ci-dessous pour créer un projet d’application AEM dans Cloud Manager :

1. Une fois que vous vous êtes connecté à Cloud Manager et que la configuration du programme de base est terminée, une vignette d’appel à action spéciale s’affiche sur l’écran **Vue d’ensemble**, si le référentiel est vide.

   ![](assets/image2018-10-3_14-29-44.png)

1. Cliquez sur **Créer** pour accéder à l’écran **Configuration du pipeline**.

   ![](assets/image2018-10-3_14-30-22.png)

1. Cliquez sur **Créer** pour ouvrir une boîte de dialogue qui permet à l’utilisateur de fournir les paramètres requis par AEM Project Archetype. Dans le formulaire par défaut, la boîte de dialogue demande deux valeurs :

   * **Titre** : par défaut, cette valeur est définie sur le *nom du programme*.

   * **Nouveau nom de branche** : par défaut, il s’agit d’un *gabarit*.
   ![](assets/screen_shot_2018-10-08at55825am.png)

   La boîte de dialogue comporte un tiroir qui peut être ouvert en cliquant sur la poignée vers le bas de la boîte de dialogue. Dans le formulaire développé, la boîte de dialogue affiche tous les paramètres de configuration d’Archetype. La plupart de ces paramètres comportent des valeurs par défaut générées en fonction du **titre**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Par exemple, si le **titre** est ***We.Finance***, le paramètre d’identifiant de base de Maven Artifact est généré sous la forme de ***com.wefinance***. Si vous le souhaitez, vous pouvez modifier ces valeurs.
   >
   >
   >Par exemple, vous pouvez passer de la valeur générée ***com.wefinance*** à ***net.wefinance***.

1. Cliquez sur **Créer** à l’étape précédente pour créer le projet de démarrage en utilisant l’archétype et en validant la branche git nommée. Vous pouvez ensuite configurer le pipeline.

## Configuration du projet {#setting-up-your-project}

### Modification des détails de configuration du projet {#modifying-project-setup-details}

Pour créer et déployer dans Cloud Manager, les projets AEM existants doivent se conformer à certaines règles de base :

* Les projets doivent être créés à l’aide d’Apache Maven.
* Un fichier *pom.xml* doit se trouver à la racine du référentiel Git. Ce fichier *pom.xml* peut faire référence à autant de sous-modules (qui, à leur tour, peuvent comporter d’autres sous-modules, etc.) que nécessaire.

* Vous pouvez ajouter des références à d’autres référentiels d’artefact Maven dans vos fichiers *pom.xml*. Cependant, l’accès aux référentiels d’artefacts protégés par mot de passe ou par réseau n’est pas pris en charge.
* Les packages de contenu déployables sont découverts en analysant les fichiers *zip* de package de contenu contenus dans un répertoire appelé *target*. Un nombre illimité de sous-modules peuvent produire des packages de contenu.

* Les artefacts déployables de Dispatcher sont découverts en analysant les fichiers *zip* (contenus dans un répertoire appelé *target*) dont les répertoires sont appelés *conf* et *conf.d*.

* S’il existe plusieurs packages de contenu, l’ordre des déploiements des packages n’est pas garanti. Si un ordre spécifique est nécessaire, il est possible d’utiliser les dépendances de package pour le définir.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## Détails de l’environnement de génération {#build-environment-details}

Cloud Manager génère et teste votre code à l’aide d’un **environnement** d’exécution de génération spécialisé. Cet environnement comporte les attributs suivants :

* L’environnement de génération est basé sur Linux.
* Apache Maven 3.6.0 est installé.
* La version Java installée est Oracle JDK 8u181.
* D’autres packages système nécessaires sont installés :

   * bzip2
   * unzip
   * libpng
   * imagemagick
   * graphicsmagick
   * Si vous avez besoin d’autres packages, vous devez les demander auprès des ingénieurs du service client.

* Maven est toujours exécuté avec la commande : *mvn --batch-mode clean org.jacoco:jacoco-maven-plugin:prepare-agent package*.
* Maven est configuré au niveau du système avec un fichier settings.xml qui inclut automatiquement le référentiel public Adobe **Artifact**. (voir le référentiel [Adobe Public Maven](https://repo.adobe.com/) pour plus d&#39;informations).

## Activation des profils Maven dans Cloud Manager {#activating-maven-profiles-in-cloud-manager}

Dans certains cas, vous devrez peut-être légèrement modifier le processus de génération lors de l’exécution dans Cloud Manager, contrairement à celui qui s’exécute sur les postes de travail des développeurs. Dans ce cas, les [profils Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html)   peuvent être utilisés pour définir la manière dont la génération doit être différente dans différents environnements, notamment Cloud Manager.

L’activation d’un profil Maven dans l’environnement de génération Cloud Manager doit se faire en recherchant la présence d’une variable d’environnement appelée `CM_BUILD`. Cette variable sera toujours définie dans l’environnement de génération de Cloud Manager. Par contre, un profil destiné à être utilisé uniquement en dehors de l’environnement de génération Cloud Manager doit être créé en recherchant l’absence de cette variable.

Par exemple, si vous souhaitez générer un message de sortie simple uniquement lorsque la génération est exécutée dans Cloud Manager, procédez comme suit :

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
>Pour tester ce profil sur un poste de travail de développeur, vous pouvez l’activer sur la ligne de commande (avec `-PcmBuild`) ou dans l’environnement de développement intégré (IDE).

Si vous souhaitez générer un message de sortie simple uniquement lorsque la génération est exécutée en dehors de Cloud Manager, procédez comme suit :

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

## Variables d’environnement personnalisées

Dans certains cas, le processus de génération d’un client peut dépendre de variables de configuration spécifiques qu’il serait inadéquat de placer dans le référentiel git. Cloud Manager permet que ces variables soient configurées par un ingénieur du service client pour chaque client. Ces variables sont stockées à un emplacement de stockage sécurisé et ne sont visibles que dans le conteneur de génération pour le client spécifique. Les clients qui souhaitent utiliser cette fonctionnalité doivent contacter l’ingénieur du service client pour configurer leurs variables.

Une fois configurés, ces variables seront disponibles sous forme de variables d&#39;environnement. Pour les utiliser comme propriétés Maven, vous pouvez les référencer dans votre fichier pom.xml, potentiellement dans un profil, comme décrit ci-dessus :

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <properties>
                  <my.custom.property>${env.MY_CUSTOM_PROPERTY}</my.custom.property>  
            </properties>
        </profile>
```

>[!NOTE]
>
>Les noms des variables d&#39;environnement ne peuvent contenir que des caractères alphanumériques et des caractères de soulignement (_). Par convention, les noms doivent être tous les majuscules.

## Développement du code en fonction des bonnes pratiques {#develop-your-code-based-on-best-practices}

Les équipes Adobe Engineering et conseil ont développé [un ensemble complet de bonnes pratiques pour les développeurs AEM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html).
