---
title: Notes de mise à jour de la version 2024.1.0
description: Voici les notes de mise à jour de la version 2024.1.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: b5907179d3de329e8b86546bb8aa99608a5b351a
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 84%

---


# Notes de mise à jour de la version 2024.1.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2024.1.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de la version 2024.1.0 de [!UICONTROL Cloud Manager] est le 17 janvier 2024. La prochaine version est prévue pour le 16 février 2024.

## Programme d’adoption précoce {#early-adoption}

Prenez part à notre programme d’adoption précoce pour avoir la possibilité de tester certaines fonctionnalités à venir.

### Apporter votre propre GitHub {#byo-github}

Si vous utilisez GitHub pour gérer vos référentiels, [vous pouvez désormais valider le code directement dans vos référentiels GitHub via Cloud Manager.](/help/managing-code/byo-github.md) Cette intégration élimine la nécessité de synchroniser de manière cohérente le code avec le référentiel d’Adobe et vous permet de vérifier les requêtes d’extraction avant de les fusionner dans les branches principales. Cette fonctionnalité est réservée au GitHub public. La prise en charge de GitHub auto-hébergé n’est pas disponible.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à `Grp-CloudManager_BYOG@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID.

## Correctifs {#bug-fixes}

* Une erreur a été corrigée dans certains cas particuliers où les téléchargements échouaient en raison de la manière dont l’application test interprète les données, provoquant l’échec du test pour le pourcentage d’erreur total.
* Lorsqu’une étape de création se termine avec le statut `FAILED` en raison d’une `BUILD_MAVEN_TRANSFER_ARTIFACT_ERROR`, elle est désormais décrite comme une erreur due à des conflits de fusion avec la branche de destination.
