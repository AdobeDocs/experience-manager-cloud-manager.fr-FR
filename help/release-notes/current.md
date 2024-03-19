---
title: Notes de mise à jour de la version 2024.3.0
description: Voici les notes de mise à jour de la version 2024.3.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 22730ba281f7c1c4720158a3a813c56b815a0af1
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 93%

---


# Notes de mise à jour de la version 2024.3.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2024.3.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de la version 2024.3.0 de [!UICONTROL Cloud Manager] est le 14 mars 2024. La prochaine version est prévue pour le 11 avril 2024.

## Nouveautés {#what-is-new}

* Les détails, y compris les informations IP/DNS (FQDN) des serveurs verts, s’affichent désormais dans l’interface utilisateur de Cloud Manager.

## Programme d’adoption précoce {#early-adoption}

Prenez part à notre programme d’adoption précoce pour avoir la possibilité de tester certaines fonctionnalités à venir.

### Apporter votre propre GitHub {#byo-github}

Si vous utilisez GitHub pour gérer vos référentiels, [vous pouvez désormais valider le code directement dans vos référentiels GitHub via Cloud Manager.](/help/managing-code/byo-github.md) Cette intégration élimine la nécessité de constamment synchroniser le code avec le référentiel Adobe et vous permet de vérifier les requêtes d’extraction avant de les fusionner dans les branches principales. Cette fonctionnalité est réservée au GitHub public. La prise en charge du GitHub auto-hébergé n’est pas disponible.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à `Grp-CloudManager_BYOG@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID.

## Correctifs {#bug-fixes}

* Un bug a été corrigé qui faisait que les journaux appropriés n’étaient pas générés lors de l’étape de test des performances lorsque la mesure de taux d’erreur échouait.
* Une logique améliorée au sein du service de test des performances chargé de détecter l’absence d’une page sur le site (404) garantit désormais un déploiement plus fluide et ininterrompu.
