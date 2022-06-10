---
title: Notes de mise à jour de la version 2022.6.0
description: Voici les notes de mise à jour de la version 2022.6.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 6dce1f48b66c6970c3ba025031f0adcbd01195dd
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 42%

---


# Notes de mise à jour de la version 2022.6.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2022.6.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] la version 2022.6.0 est le 9 juin 2022. La prochaine version est prévue pour le 30 juin 2022.

## Nouveautés {#what-is-new}

* Une nouvelle carte de bienvenue sur la page d’entrée de Cloud Manager permet aux utilisateurs d’accéder rapidement aux tutoriels d’intégration et aux mesures de progression liées au client.
   * Cette fonctionnalité sera déployée par étapes au cours de la semaine qui suivra la version 2022.06.0.
* [La création d’artefacts peut désormais être réutilisée.](/help/using/setting-up-project.md#build-artifact-reuse) lors de l’utilisation de la mise en miroir git.

## Modifications d’API {#api-changes}

* Le [`List Programs`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getPrograms) L’API a été abandonnée et [`List Programs for Tenant`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getProgramsForTenant) doit être utilisé à la place.
   * `List Programs` continue de fonctionner, mais son utilisation génère des messages d’avertissement dans les journaux.
   * Il ne sera plus pris en charge au bout de trois mois.
