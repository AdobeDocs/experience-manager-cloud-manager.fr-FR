---
title: Configuration de pipelines hors production
description: Découvrez comment utiliser Cloud Manager pour créer et configurer des pipelines hors production afin de déployer votre code.
source-git-commit: 205113735cc743e11e140b1161413002844f5b79
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 12%

---


# Configuration de pipelines hors production {#configuring-non-production-pipelines}

Découvrez comment utiliser Cloud Manager pour créer et configurer des pipelines hors production afin de déployer votre code. si vous souhaitez d’abord une présentation plus conceptuelle du fonctionnement des pipelines dans Cloud Manager, reportez-vous à la section [Documentation de présentation du pipeline CI/CD.](ci-cd-pipeline.md)

>[!NOTE]
>
>Pour savoir comment configurer les pipelines CI/CD pour Cloud Manager dans AEM as a Cloud Service, voir [la documentation d’AEMaaCS ;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html#using-cloud-manager)

## Présentation {#understanding-the-flow}

Le **Responsable de déploiement** est chargé de configurer le pipeline à l’aide de la fonction **Pipelines** dans la [!UICONTROL Cloud Manager] Interface utilisateur.

Vous pouvez créer deux types de pipelines différents.

* **Pipelines de production** - Un pipeline de production est un pipeline personnalisé constitué d’une série d’étapes orchestrées permettant d’intégrer le code source jusqu’à la production.
* **Pipelines hors production** - Un pipeline hors production sert principalement à exécuter des analyses de qualité du code ou à déployer le code source dans un environnement de développement.

Ce document se concentre sur les pipelines hors production. Pour plus d’informations sur la configuration des pipelines hors production, voir le document [Configuration de pipelines hors production.](configuring-non-production-pipelines.md)

Il existe deux types de pipelines hors production :

* **Pipelines de qualité du code** - Ces étapes exécutent des analyses de qualité du code sur le code d’une branche Git et exécutent les étapes de création et de qualité du code.
* **Pipelines de déploiement** - Outre l’exécution des étapes de génération et de qualité de code, telles que les pipelines de qualité de code, ces pipelines déploient le code dans un environnement hors production.

>[!NOTE]
>
>Un pipeline ne peut pas être configuré tant que son référentiel git associé ne comporte pas au moins une branche et que [configuration du programme](setting-up-program.md) est terminée. Consultez [Ajout et gestion de référentiels](cloud-manager-repositories.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

## Tutoriel vidéo {#video-tutorial-two}

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

## Ajout d’un pipeline hors production {#add-non-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez d’au moins un environnement à l’aide de l’interface utilisateur de Cloud Manager, vous êtes prêt à ajouter un pipeline hors production en suivant ces étapes.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte Pipelines depuis l’écran d’accueil de Cloud Manager. Cliquez sur **Ajouter** et sélectionnez **Ajout d’un pipeline hors production**.

   ![Ajout d’un pipeline hors production](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Sur le **Configuration** de l’onglet **Ajout d’un pipeline hors production** , sélectionnez le type de pipeline que vous souhaitez créer, soit une **Pipeline de qualité du code** ou **Pipeline de déploiement**.


   ![Choix du type de pipeline](/help/using/assets/configure-pipelines/add-non-production-pipeline.png)

1. Fournissez une description de votre pipeline dans le **Nom du pipeline hors production** champ .

1. Si vous avez choisi d’ajouter une **Pipeline de déploiement**, sélectionnez l’environnement de déploiement cible dans le **Environnements de déploiement éligibles** menu déroulant.

1. Indiquez le référentiel dans lequel le pipeline doit récupérer le code.

   * **Référentiel** - Cette option définit à partir de quel référentiel git le pipeline doit récupérer le code.
   * **Branche Git** - Cette option définit à partir de quelle branche du pipeline sélectionné doit récupérer le code.

1. Définissez les options de déploiement.

   1. Sous **Déclencheur de déploiement**, définissez l’événement qui active le pipeline.

      * **Manuel** - Utilisez cette option pour démarrer manuellement le pipeline.
      * **Lors des modifications Git** - Cette option démarre le pipeline chaque fois que des validations sont ajoutées à la branche git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.
   1. Sous **Comportement des échecs de mesure importants**, définissez le comportement du pipeline en cas d’échec important dans l’un des points de contrôle qualité.

      * **Demander à chaque fois** - Il s’agit du paramètre par défaut qui nécessite une intervention manuelle en cas d’échec important.
      * **Échec immédiat** - Si cette option est sélectionnée, le pipeline est annulé chaque fois qu’un échec important se produit. Cette option émule essentiellement un utilisateur rejetant manuellement chaque échec.
      * **Continuer immédiatement** - Si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Cette option émule essentiellement la validation manuelle de l’utilisateur à chaque échec.


1. Cliquez sur **Enregistrer** pour enregistrer votre pipeline.

## Étapes suivantes {#the-next-steps}

Une fois que vous avez configuré le pipeline, vous devez déployer votre code.

Consultez le document [Déploiement de votre code](deploying-code.md) pour plus d’informations.
