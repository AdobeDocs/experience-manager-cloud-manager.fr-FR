---
title: Notes de mise à jour de la version 2023.9.0
description: Voici les notes de mise à jour de la version 2023.9.0 de Cloud Manager.
feature: Release Information
source-git-commit: f15a4b739150ee40b6dc48de0fbc20859093c79c
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 57%

---


# Notes de mise à jour de la version 2023.9.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2023.9.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de la version 2023.9.0 de [!UICONTROL Cloud Manager] est le 14 septembre 2023. La prochaine version est prévue pour le 5 octobre 2023.

## Correctifs {#bug-fixes}

* Lorsqu’un programme est supprimé, tout pipeline associé en cours d’exécution est désormais également supprimé.
* Une erreur occasionnelle a été corrigée lorsque toutes les étapes d’une exécution de pipeline étaient marquées comme étant terminées, mais que l’état du pipeline était toujours en cours d’exécution, ce qui donnait l’apparence d’un état bloqué.
* Une erreur a été corrigée lorsque les pipelines CI/CD échouaient pour les branches de référentiel qui généraient l’archétype.
