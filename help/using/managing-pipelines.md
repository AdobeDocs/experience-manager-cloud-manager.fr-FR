---
title: Gestion des pipelines
description: Découvrez comment gérer vos pipelines existants, notamment en les modifiant, en les exécutant et en les supprimant.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 99325c28c379103db2ba4c19bb6d206849c6e126
workflow-type: ht
source-wordcount: '517'
ht-degree: 100%

---


# Gestion des pipelines {#managing-pipelines}

Découvrez comment gérer vos pipelines existants, notamment en les modifiant, en les exécutant et en les supprimant.

## Vignette de pipeline {#pipeline-card}

La vignette **Pipelines** de la page **Aperçu du programme** dans Cloud Manager vous donne un aperçu de tous vos pipelines et de leur statut actuel.

![Vignette de pipelines dans Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

En cliquant sur le bouton représentant des points de suspension à côté de chaque pipeline, vous pouvez effectuer les actions suivantes.

* [Exécuter le pipeline](#running-pipelines)
* [Modifier le pipeline](#editing-pipelines)
* [Supprimer le pipeline](#deleting-pipelines)
* [Afficher les détails](#view-details)

Au bas de la liste des pipelines, vous disposez d’options générales.

* **Ajouter** : permet d’[ajouter un nouveau pipeline de production](/help/using/production-pipelines.md) ou d’[ajouter un nouveau pipeline hors production](/help/using/non-production-pipelines.md).
* **Tout afficher** : dirige l’utilisateur vers l’écran **Pipelines** pour afficher tous les pipelines dans un tableau plus détaillé.
* **Accéder aux informations sur le référentiel** : affiche les informations nécessaires pour accéder au référentiel Git de Cloud Manager.
* **En savoir plus** : permet d’accéder aux ressources de documentation du pipeline CI/CD.

## Exécution des pipelines {#running-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la vignette **Pipelines** à partir de la page **Aperçu du programme** et cliquez sur le bouton représentant des points de suspension à côté du pipeline que vous exécutez, puis sélectionnez **Exécuter** dans le menu.

1. L’exécution du pipeline démarre et est indiquée par la colonne **Statut**.

Pour afficher les détails de l’exécution, cliquez de nouveau sur le bouton représentant des points de suspension et sélectionnez **[Afficher les détails](#view-details)**.

Selon le type de pipeline, vous pouvez être en mesure d’annuler l’exécution en cliquant de nouveau sur le bouton représentant des points de suspension et en sélectionnant **Annuler**.

## Modification de pipelines {#editing-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la vignette **Pipelines** à partir de la page **Aperçu du programme** et cliquez sur le bouton représentant des points de suspension à côté du pipeline que vous souhaitez modifier, puis sélectionnez **Modifier** dans le menu.

1. La boîte de dialogue **Modifier le pipeline de production** ou **Modifier le pipeline hors production** s’affiche, ce qui vous permet de modifier les mêmes détails que ceux saisis lors de la création du pipeline.

   * Consultez les pages suivantes pour plus d’informations sur tous les champs et options de configuration disponibles pour les pipelines.
      * [Configuration des pipelines de production](/help/using/production-pipelines.md)
      * [Configurer des pipelines hors production](/help/using/non-production-pipelines.md)

1. Cliquez sur **Mettre à jour** une fois que vous avez terminé de modifier le pipeline.

>[!NOTE]
>
>Vous ne pouvez pas modifier un pipeline en cours d’exécution.

## Suppression de pipelines {#deleting-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la vignette **Pipelines** à partir de la page **Aperçu du programme** et cliquez sur le bouton représentant des points de suspension à côté du pipeline que vous exécutez, puis sélectionnez **Supprimer** dans le menu.

>[!NOTE]
>
>Vous ne pouvez pas supprimer un pipeline en cours d’exécution.

## Afficher les détails {#view-details}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la vignette **Pipelines** à partir de la page **Aperçu du programme** et cliquez sur le bouton représentant des points de suspension à côté du pipeline que vous exécutez, puis sélectionnez **Afficher les détails** dans le menu.

1. Vous accédez à la page des détails du pipeline en cours d’exécution.

![Détails du pipeline](/help/assets/configure-pipelines/pipeline-running-details.png)

Vous pouvez y voir le statut des différentes étapes du pipeline et récupérer les journaux de génération à des fins de diagnostic. Reportez-vous au document [Déploiement du code](/help/using/code-deployment.md) pour plus d’informations.

>[!NOTE]
>
>Vous pouvez uniquement afficher les détails d’un pipeline en cours d’exécution ou qui a été exécuté au moins une fois.
