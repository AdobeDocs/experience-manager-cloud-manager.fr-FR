---
title: Notes de mise à jour de la version 2023.11.0
description: Voici les notes de mise à jour de la version 2023.11.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 264c7ffcbc9e10903880a511a4ca605be666f7e8
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 21%

---


# Notes de mise à jour de la version 2023.11.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2023.11.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de la version 2023.11.0 de [!UICONTROL Cloud Manager] est le 14 novembre 2023. La prochaine version est prévue pour le 7 décembre 2023.

## Nouveautés {#what-is-new}

* [Page des détails d’exécution du pipeline](/help/using/managing-pipelines.md#view-details) affiche désormais toutes les étapes d’une exécution de pipeline avec celles qui n’ont pas encore commencé en grisé.
* Sur les deux **[Activité](/help/using/managing-pipelines.md#activity)** et **[Pipelines](/help/using/managing-pipelines.md#pipelines)** , un résumé de l’exécution du pipeline est désormais disponible lorsque vous cliquez sur un pipeline avec l’état en cours d’exécution.
* Une nouvelle **Durée** a été ajoutée à la section [page des détails du pipeline](/help/using/managing-pipelines.md#view-details) qui inclut la durée moyenne de l’étape du pipeline en fonction de la tendance historique de ce programme.
* Sur le [page d’exécution du pipeline,](/help/using/managing-pipelines.md#activity-window) les étapes terminées affichent maintenant la durée
* Cloud Manager [outil de copie de contenu](/help/using/content-copy.md) permet aux utilisateurs de copier du contenu modifiable à la demande depuis leurs environnements de production hébergés par AMS AEM 6.x vers des environnements inférieurs à des fins de test.
* Exécution de [réutilisation d’artefacts de build](/help/getting-started/project-setup.md#build-artifact-reuse) affiche désormais le lien vers l’exécution qui a initialement créé ces artefacts.
* L’option à sélectionner **Échecs de mesures importants** peut maintenant être configuré pour [pipelines de qualité de code](/help/using/non-production-pipelines.md) ainsi que .

## Programme d&#39;adoption précoce {#early-adoption}

Faire partie de notre programme d’adoption précoce et avoir la possibilité de tester certaines fonctionnalités à venir

### Apportez votre propre GitHub {#byo-github}

Si vous utilisez GitHub pour gérer vos référentiels, [vous pouvez désormais valider le code directement dans vos référentiels GitHub via Cloud Manager.](/help/managing-code/byo-github.md) Cette intégration élimine la nécessité de synchroniser de manière cohérente le code avec le référentiel d’Adobe et vous permet de vérifier les requêtes d’extraction avant de les fusionner dans les branches principales.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `Grp-CloudManager_BYOG@adobe.com` de votre adresse électronique associée à votre Adobe ID.

### Autorisations personnalisées {#custom-permissions}

[Autorisations personnalisées de Cloud Manager](/help/using/custom-permissions.md) vous permet de créer des profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès aux programmes, aux pipelines et aux environnements pour les utilisateurs de Cloud Manager.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail. `Grp-CloudManager_ams_custompermissions@adobe.com` de votre adresse électronique associée à votre Adobe ID.
