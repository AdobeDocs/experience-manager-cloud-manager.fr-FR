---
title: Ajout d’un pipeline hors production
description: Découvrez comment utiliser Cloud Manager pour créer et configurer des pipelines hors production afin de déployer votre code.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 1209faf71edbd74cd87acfe24ec438b98ddd4a3a
workflow-type: ht
source-wordcount: '688'
ht-degree: 100%

---

# Ajout d’un pipeline hors production {#configuring-non-production-pipelines}

Découvrez comment utiliser Cloud Manager pour créer et configurer des pipelines hors production afin de déployer votre code. Si vous souhaitez d’abord obtenir une vue d’ensemble plus conceptuelle du fonctionnement des pipelines dans Cloud Manager, reportez-vous au document [Pipelines CI/CD](/help/overview/ci-cd-pipelines.md).

## Vue d’ensemble {#overview}

En utilisant le volet **Pipelines** dans [!UICONTROL Cloud Manager], le **Responsable de déploiement** peut créer deux types de pipelines différents.

* **Pipelines de production** - un pipeline de production est un pipeline spécialement conçu, composé d’une série d’étapes coordonnées permettant de mener le code source jusqu’à la production.
* **Pipelines hors production** - un pipeline hors production sert principalement à exécuter des analyses de qualité du code ou à déployer le code source dans un environnement de développement.

Ce document se concentre sur les pipelines hors production. Pour plus de détails sur la configuration des pipelines de production, voir le document [Configurer des pipelines de production](/help/using/production-pipelines.md).

Il existe deux types de pipelines hors production :

* **Pipelines de qualité du code** : ceux-ci exécutent des analyses de qualité du code sur le code dans une branche Git et exécutent les étapes de création et de qualité du code.
* **Pipelines de déploiement** : outre l’exécution des étapes de création et de qualité du code, identiques à celles des pipelines de qualité du code, ces pipelines déploient le code dans un environnement hors production.

>[!NOTE]
>
>Un pipeline ne peut être configuré que si le référentiel Git qui lui est associé dispose d’au moins une branche et que la [configuration du programme](/help/getting-started/program-setup.md) est terminée. Consultez le document [Référentiels Cloud Manager](/help/managing-code/managing-repositories.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

## Ajout d’un nouveau pipeline hors production {#add-non-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez d’au moins un environnement utilisant l’interface utilisateur de Cloud Manager, vous êtes prêt à ajouter un pipeline hors production en suivant ces étapes.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la vignette Pipelines à partir de l’écran d’accueil de Cloud Manager. Cliquez sur **Ajouter** et sélectionnez **Ajouter un pipeline hors production**.

   ![Ajouter un pipeline hors production](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Sur l’onglet **Configuration** de la boîte de dialogue **Ajouter un pipeline hors production**, sélectionnez le type de pipeline que vous souhaitez créer, soit un **Pipeline de qualité du code** ou un **Pipeline de déploiement**.

   ![Choix du type de pipeline](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Fournissez une description de votre pipeline dans le champ **Nom du pipeline hors production**.

1. Si vous avez choisi d’ajouter un **Pipeline de déploiement**, sélectionnez l’environnement de déploiement cible dans le menu déroulant **Environnements de déploiement admissibles**.

1. Indiquez le référentiel dans lequel le pipeline doit récupérer le code.

   * **Référentiel** : définit à partir de quel référentiel Git le pipeline doit récupérer le code.
   * **Branche Git** : définit à partir de quelle branche le pipeline sélectionné doit récupérer le code.

1. Définissez vos options de déploiement.

   1. Sous **Déclencheur de déploiement**, définissez l’événement qui active le pipeline.

      * **Manuel** : vous permet de lancer le pipeline manuellement.
      * **Lors des modifications Git** : démarre le pipeline lorsque des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.

   1. Pour les pipelines de déploiement, sous **Comportement en cas d’échec de mesure grave**, définissez le comportement du pipeline en cas d’échec important à l’un des points de contrôle qualité.

      * **Demander à chaque fois** : paramètre par défaut, qui nécessite une intervention manuelle lors de n’importe quel échec important.
      * **Échouer immédiatement** : le pipeline sera interrompu dès qu’un échec important aura lieu. Il s’agit essentiellement de l’émulation d’un utilisateur ou d’une utilisatrice qui rejette manuellement chaque échec.
      * **Continuer immédiatement** : le pipeline se poursuivra automatiquement chaque fois qu’un échec important se produira. Il s’agit essentiellement de l’émulation d’un utilisateur ou d’une utilisatrice qui approuve manuellement chaque échec.

   1. **Configuration du Dispatcher** : le rôle de la personne **Responsable de déploiement** consiste à configurer un ensemble de chemins de contenu qui sont soit invalidés soit vidés du cache d’AEM Dispatcher lorsqu’un pipeline est exécuté. Ces actions de cache sont exécutées dans le cadre de l’étape du pipeline de déploiement, juste après le déploiement des modules de contenu. Ces paramètres utilisent le comportement standard d’AEM Dispatcher. Pour configurer :

      1. Sous **CHEMIN**, fournissez un chemin d’accès au contenu.
      1. Sous **TYPE**, sélectionnez l’action à effectuer sur ce chemin.

         * **Purge** - videz le cache.
         * **Invalider** - effectuez une invalidation du cache, comme lorsque le contenu est activé d’une instance de création vers une instance de publication.

      1. Cliquez sur **Ajouter un chemin** pour ajouter votre chemin spécifié. Vous pouvez ajouter jusqu’à 100 chemins par environnement.

1. Cliquez sur **Enregistrer**.

## Étapes suivantes {#the-next-steps}

Après avoir configuré le pipeline, vous pouvez déployer votre code. Voir la section [Déploiement du code](/help/using/code-deployment.md) pour plus d’informations.

## Tutoriel vidéo {#video-tutorial}

Cette vidéo présente une vue d’ensemble du processus de création de pipeline, détaillé dans ce document.

>[!VIDEO](https://video.tv.adobe.com/v/327614?captions=fre_fr)
