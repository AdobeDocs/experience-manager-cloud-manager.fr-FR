---
title: Gestion des pipelines
description: Découvrez comment gérer vos pipelines existants, notamment en les exécutant, en les modifiant et en les supprimant.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 9d910e1b1a4aad000a8389ddc22ce380bbccd4ef
workflow-type: ht
source-wordcount: '840'
ht-degree: 100%

---


# Gestion des pipelines {#managing-pipelines}

Découvrez comment gérer vos pipelines existants, notamment en les exécutant, en les modifiant et en les supprimant.

## Carte de pipeline {#pipeline-card}

La vignette **Pipelines** de la page **Aperçu du programme** dans Cloud Manager vous donne un aperçu de tous vos pipelines et de leur statut actuel.

![Vignette de pipelines dans Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

En cliquant sur le bouton représentant des points de suspension à côté de chaque pipeline, vous pouvez effectuer les actions suivantes :

* [Exécutez le pipeline](#running-pipelines).
* [Modifiez le pipeline](#editing-pipelines).
* [Supprimez le pipeline](#deleting-pipelines).
* [Affichez les détails](#view-details).

Au bas de la liste des pipelines, vous disposez des options générales suivantes :

* **Ajouter** : permet d’[ajouter un nouveau pipeline de production](/help/using/production-pipelines.md) ou d’[ajouter un nouveau pipeline hors production](/help/using/non-production-pipelines.md).
* **Tout afficher** : dirige l’utilisateur ou l’utilisatrice vers l’écran **Pipelines** pour afficher tous les pipelines dans un tableau plus détaillé.
* **Accéder aux informations sur le référentiel** : affiche les informations nécessaires pour accéder au référentiel Git de Cloud Manager.
* **En savoir plus** : permet d’accéder aux ressources de documentation du pipeline CI/CD.

## Page Pipelines {#pipelines}

La page **Pipelines** affiche la liste complète de tous les pipelines du programme sélectionné. Cette liste se révèle utile, car elle présente des informations plus complètes que celles disponibles dans la [Carte Pipelines](#pipeline-card).

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Pipelines** pour basculer vers la page **Pipelines**.

1. Vous y trouverez une liste de tous les pipelines du programme, ainsi que le début et l’arrêt de l’exécution du pipeline, comme dans la **Carte des pipelines**.

Le fait de cliquer sur l’icône `i` affiche des détails sur la dernière exécution ou l’exécution actuelle du pipeline.

![Détails de l’exécution du pipeline](/help/assets/configure-pipelines/pipeline-status.png)

Cliquez sur **Afficher les détails** pour accéder aux [détails de l’exécution du pipeline](#view-details).

## Page Activité {#activity}

La page **Activités** affiche la liste complète de toutes les exécutions de pipelines du programme sélectionné.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Activité** pour basculer vers la page **Activité**.

1. Vous y trouverez une liste de toutes les exécutions de pipeline du programme, y compris les exécutions actuelles et historiques.

Le fait de cliquer sur l’icône `i` affiche des détails sur l’exécution de pipeline sélectionnée.

![Détails de l’exécution du pipeline](/help/assets/configure-pipelines/pipeline-activity.png)

Cliquez sur **Afficher les détails** pour vérifier les [détails de l’exécution du pipeline](#view-details).

## Exécuter des pipelines {#running-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme**.
1. Cliquez sur le bouton représentant des points de suspension en regard du pipeline que vous exécutez, puis, dans le menu, sélectionnez **Exécuter**.

   La colonne Statut indique le début de l’exécution du pipeline.

   Pour afficher les détails de l’exécution, cliquez de nouveau sur le bouton représentant des points de suspension et sélectionnez **[Afficher les détails](#view-details)**.

   Selon le type de pipeline, vous pouvez être en mesure d’annuler l’exécution en cliquant de nouveau sur le bouton représentant des points de suspension et en sélectionnant **Annuler**.

## Modifier les pipelines {#editing-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme** et cliquez sur le bouton représentant des points de suspension à côté du pipeline que vous souhaitez modifier, puis sélectionnez **Modifier** dans le menu.

1. La boîte de dialogue **Modifier le pipeline de production** ou **Modifier le pipeline hors production** s’affiche. Vous pouvez modifier les mêmes informations que celles que vous avez saisies lors de la création du pipeline.

   Voir [Configuration des pipelines de production](/help/using/production-pipelines.md) et [Configuration des pipelines hors production](/help/using/non-production-pipelines.md) pour plus d’informations sur les champs et les options de configuration disponibles pour les pipelines.

1. Cliquez sur **Mettre à jour** lorsque vous avez terminé.

>[!NOTE]
>
>Vous ne pouvez pas modifier un pipeline en cours d’exécution.

## Supprimer des pipelines {#deleting-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme** et cliquez sur le bouton représentant des points de suspension à côté du pipeline que vous exécutez, puis sélectionnez **Supprimer** dans le menu.

>[!NOTE]
>
>Vous ne pouvez pas supprimer un pipeline en cours d’exécution.

## Afficher les détails {#view-details}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme** et cliquez sur le bouton représentant des points de suspension à côté du pipeline que vous exécutez, puis sélectionnez **Afficher les détails** dans le menu.

1. Vous accédez à la page des détails du pipeline en cours d’exécution.

![Détails du pipeline](/help/assets/configure-pipelines/pipeline-running-details.png)

Vous pouvez y voir le statut des différentes étapes du pipeline et récupérer les journaux de génération à des fins de diagnostic. Reportez-vous au document [Déploiement du code](/help/using/code-deployment.md) pour plus d’informations.

Toutes les étapes d’exécution d’un pipeline s’affichent, celles n’ayant pas encore commencé étant grisées. Les étapes terminées affichent leur durée.

Lorsqu’une étape de pipeline est terminée, un résumé est présenté.

![Résumé d’étape](/help/assets/configure-pipelines/pipeline-step.png)

Cliquez sur le lien **Afficher les détails** pour afficher la section **Durée**. Cette section inclut la durée moyenne du pipeline en fonction de la tendance historique de ce programme.

![Durée](/help/assets/configure-pipelines/duration.png)

Si votre pipeline contenait une étape **Analyse du code** qui a entraîné des problèmes, vous pouvez cliquer sur le bouton **Détails du téléchargement** pour afficher la liste des [tests de qualité du code](/help/using/code-quality-testing.md) qui ont échoué.

![Problèmes de qualité du code](assets/managing-pipelines-code-quality-issues.png)

Une colonne **Emplacement du fichier de projet** est présente dans le fichier CSV pour indiquer l’emplacement du code problématique. Cette colonne correspond au chemin d’accès relatif du projet, tandis que la colonne **Emplacement du fichier** est générée par Maven.

![Détails des problèmes de l’analyse du code du projet](assets/managing-pipelines-code-quality-details.png)


>[!NOTE]
>
>Vous pouvez uniquement afficher les détails d’un pipeline en cours d’exécution ou qui a été exécuté au moins une fois.
