---
title: Notes de mise à jour de la version 2022.01.0
description: Consultez les notes de mise à jour de la version 2022.01.0 de Cloud Manager ci-dessous.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: ebbbbdca2bfd834bc3dc0ff06ffb318df42713ee
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 40%

---

# Notes de mise à jour de Cloud Manager version 2021.12.0 {#release-notes}

La section suivante présente les notes générales de mise à jour pour [!UICONTROL Cloud Manager] version 2022.01.0.

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr)

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] version 2022.01.0 du 20 janvier 2022. La prochaine version est prévue pour le 10 février 2022.

## Nouveautés {#whats-new}

* Cloud Manager [évitez de reconstruire la base de code lorsqu’il détecte que la même validation git est utilisée.](/help/using/setting-up-project.md#build-artifact-reuse) dans plusieurs exécutions complètes de pipeline de pile.
* Lors de la génération d’un mot de passe Git, la date d’expiration s’affiche.

## Correctifs {#bug-fixes}

* Les occurrences peu fréquentes de défaillances de pipeline fausses positives ont été corrigées.
* Pour les programmes ne comportant qu’un seul référentiel, l’écran d’exécution du pipeline affiche désormais le nom du référentiel.
