---
title: Configurer des pipelines hors production
description: Découvrez comment utiliser Cloud Manager pour créer et configurer des pipelines hors production afin de déployer votre code.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 567a16a032bf80451b5e8ba4e3d842cb617a615f
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 78%

---

# Configuration de pipelines hors production {#configuring-non-production-pipelines}

Découvrez comment utiliser Cloud Manager pour créer et configurer des pipelines hors production afin de déployer votre code. Si vous souhaitez d’abord une présentation plus conceptuelle du fonctionnement des pipelines dans Cloud Manager, consultez le document . [Pipelines CI/CD.](/help/overview/ci-cd-pipelines.md)

## Présentation {#overview}

En utilisant la variable **Pipelines** dans [!UICONTROL Cloud Manager], la variable **Responsable de déploiement** peut créer deux types de pipelines différents.

* **Pipelines de production** - un pipeline de production est un pipeline spécialement conçu, composé d’une série d’étapes coordonnées permettant de mener le code source jusqu’à la production.
* **Pipelines hors production** - un pipeline hors production sert principalement à exécuter des analyses de qualité du code ou à déployer le code source dans un environnement de développement.

Ce document se concentre sur les pipelines hors production. Pour plus d’informations sur la configuration des pipelines de production, voir le document . [Configuration des pipelines de production.](/help/using/production-pipelines.md)

Il existe deux types de pipelines hors production :

* **Pipelines de qualité du code** - ceux-ci exécutent des analyses de qualité du code sur le code dans une branche Git et exécutent les étapes de création et de qualité du code.
* **Pipelines de déploiement** - outre l’exécution des étapes de création et de qualité du code, telles que les pipelines de qualité du code, ces pipelines déploient le code dans un environnement hors production.

>[!NOTE]
>
>Un pipeline ne peut être configuré que si le référentiel Git associé dispose d’au moins une branche et que la [configuration du programme](/help/getting-started/program-setup.md) est terminée. Voir le document [Référentiels Cloud Manager](/help/managing-code/repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

## Tutoriel vidéo {#video-tutorial}

Cette vidéo présente un aperçu du processus de création de pipeline, détaillé dans ce document.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

## Ajouter un pipeline hors production {#add-non-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez d’au moins un environnement utilisant l’interface utilisateur de Cloud Manager, vous êtes prêt à ajouter un pipeline hors production en suivant ces étapes.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la vignette Pipelines à partir de l’écran d’accueil de Cloud Manager. Cliquez sur **Ajouter** et sélectionnez **Ajouter un pipeline hors production**.

   ![Ajouter un pipeline hors production](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Sur l’onglet **Configuration** de la boîte de dialogue **Ajouter un pipeline hors production**, sélectionnez le type de pipeline que vous souhaitez créer, soit un **Pipeline de qualité du code** ou un **Pipeline de déploiement**.

   ![Choix du type de pipeline](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Fournissez une description de votre pipeline dans le champ **Nom du pipeline hors production**.

1. Si vous avez choisi d’ajouter un **Pipeline de déploiement**, sélectionnez l’environnement de déploiement cible dans le menu déroulant **Environnements de déploiement admissibles**.

1. Indiquez le référentiel dans lequel le pipeline doit récupérer le code.

   * **Référentiel** - cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.
   * **Branche Git** - cette option définit à partir de quelle branche sélectionnée le pipeline doit récupérer le code.

1. Définissez vos options de déploiement.

   1. Sous **Déclencheur de déploiement**, définissez l’événement qui active le pipeline.

      * **Manuel** - utilisez cette option pour démarrer manuellement le pipeline.
      * **Lors des modifications Git** - cette option démarre le pipeline chaque fois que des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.
   1. Pour les pipelines de déploiement, sous **Comportement en cas d’échecs de mesures importants**, définissez le comportement du pipeline en cas d’échec important à l’un des points de contrôle qualité.

      * **Demander à chaque fois** - il s’agit du paramètre par défaut qui nécessite une intervention manuelle pour tout échec important.
      * **Défaillance immédiate** : si cette option est sélectionnée, le pipeline sera interrompu chaque fois qu’une défaillance importante aura lieu. Il s’agit essentiellement d’imiter un utilisateur qui rejetterait manuellement chaque échec.
      * **Continuer immédiatement** - si cette option est sélectionnée, le pipeline se poursuivra automatiquement chaque fois qu’une défaillance importante se produira. Il s’agit essentiellement d’émuler un utilisateur approuvant manuellement chaque échec.


1. Cliquez sur **Enregistrer** pour enregistrer votre pipeline.

## Les étapes suivantes {#the-next-steps}

Une fois que vous avez configuré le pipeline, vous devez déployer votre code. Consultez le document [Déploiement du code](/help/using/code-deployment.md) pour plus d’informations.
