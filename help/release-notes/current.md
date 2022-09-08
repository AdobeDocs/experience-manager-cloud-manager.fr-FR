---
title: Notes de mise à jour de la version 2022.9.0
description: Voici les notes de mise à jour de la version 2022.9.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: e74d386d0b2d50a7e276bb7ead7594ef448742ae
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 35%

---


# Notes de mise à jour de la version 2022.9.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2022.9.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] la version 2022.9.0 est le 8 septembre 2022. La prochaine version est prévue pour le 6 octobre 2022.

## Nouveautés {#what-is-new}

* Prise en charge de la mise à l’échelle automatique horizontale multi-région par Cloud Manager.
* Nouvelle carte Page d’accueil personnalisée pour les utilisateurs disposant uniquement d’un rôle utilisateur Cloud Manager qui les guide sur la navigation vers les environnements AEM et l’accès restreint aux programmes.
* Les clients ne disposant d’aucun rôle Cloud Manager ne pourront pas accéder aux détails du programme. Ils peuvent toutefois accéder aux points de fin de création à partir de la page d’entrée CM.
* Éliminez les échecs de pipeline résultant d’échecs de reprise réalisés en renforçant la résilience.

## Correctifs {#bug-fixes}

* Amélioration des commentaires des clients concernant la création de l’application d’AEM client lorsque Maven est confronté à des problèmes de connectivité avec les référentiels privés.
* Dans de rares cas, lorsque le système de contrôle de l’intégrité n’est pas en mesure de récupérer un score d’intégrité valide, un événement de mise à l’échelle automatique ne sera pas déclenché.
