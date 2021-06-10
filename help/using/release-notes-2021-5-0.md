---
title: Notes de mise à jour de la version 2021.5.0
description: Consultez cette page pour obtenir des informations sur la version 2021.5.0 de Cloud Manager
feature: Informations sur la version
source-git-commit: 5111a918b8063ab576ef587dc3c8d66ad976fc1a
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 97%

---

# Notes de mise à jour de la version 2021.5.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.5.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>Reportez-vous aux [Notes de mise à jour actuelles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr#getting-access) pour consulter les dernières notes de mise à jour de Cloud Manager dans AEM as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2021.5.0 de [!UICONTROL Cloud Manager] est le 06 mai 2021.
La prochaine version est prévue pour le 10 juin 2021.

## Nouveautés {#whats-new}

* La règle de qualité PackageOverlaps détecte désormais les cas dans lesquels le même package a été déployé plusieurs fois, c’est-à-dire dans de multiples emplacements incorporés, dans le même ensemble de packages déployé.

* Le point d’entrée du référentiel dans l’API publique inclut désormais l’URL Git.

* Dans le workflow Modifier le programme, l’utilisateur n’est autorisé à définir que des valeurs d’IPC non décimales.

* Les échecs intermittents rencontrés lors de la publication du code dans le Git Adobe ont maintenant été résolus.

* L’expérience de l’action Modifier le programme a été actualisée.

## Correctifs {#bug-fixes}

* Au lieu de supprimer les variables « deleted », l’API des variables de pipeline ne faisait que les marquer avec l’état « DELETED ».

* Certains problèmes de qualité de code de type smell avaient une incidence incorrecte sur la cote de fiabilité.

* Lorsqu’une exécution de pipeline était démarrée entre minuit et 1 h UTC, il n’était pas garanti que la version d’artefact générée par Cloud Manager soit supérieure à la version créée le jour précédent.

* Certains clients d’Adobe Managed Services (AMS) ne pouvaient pas créer de projets dans la Developer Console Adobe I/O à l’aide de l’API Cloud Manager.
