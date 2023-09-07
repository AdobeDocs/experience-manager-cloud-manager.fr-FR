---
title: Notes de mise à jour de la version 2023.9.0
description: Voici les notes de mise à jour de la version 2023.9.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 74381d5d154f7c61135a990d2806fa9e39be7690
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 54%

---


# Notes de mise à jour de la version 2023.9.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2023.9.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de la version 2023.9.0 de [!UICONTROL Cloud Manager] est le 7 septembre 2023. La prochaine version est prévue pour le 5 octobre 2023.

## Nouveautés {#what-is-new}

Cette version contient des correctifs.

## Correctifs {#bug-fixes}

* Lorsqu’un programme est supprimé, tout pipeline associé en cours d’exécution est également supprimé, en s’assurant que le pipeline n’est pas incorrectement désigné comme état d’échec.
* Parfois, lorsque toutes les étapes d’exécution d’un pipeline sont &quot;terminées&quot;, l’état du pipeline est considéré comme &quot;en cours d’exécution&quot;, ce qui donne l’impression qu’il est en état de blocage. Il est maintenant considéré comme &quot;terminé&quot;.
* Pour les branches de référentiel générées à l’aide de l’archétype du générateur de code, le pipeline CI/CD échoue.
