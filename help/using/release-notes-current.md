---
title: Notes de mise à jour de la version 2021.5.0
description: Consultez cette page pour obtenir des informations sur la version 2021.5.0 de Cloud Manager
feature: Informations sur la version
source-git-commit: 3f17f252d89a1753c9cb121461b048f619d28415
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 18%

---

# Notes de mise à jour de la version 2021.5.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.5.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>Reportez-vous à la section [Notes de mise à jour actuelles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) pour consulter les dernières notes de mise à jour de Cloud Manager dans AEM en tant que Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2021.5.0 de [!UICONTROL Cloud Manager] est le 06 mai 2021.
La prochaine version est prévue pour le 10 juin 2021.

## Nouveautés {#whats-new}

* La règle de qualité PackageOverlaps détecte désormais les cas où le même package a été déployé plusieurs fois, c’est-à-dire dans plusieurs emplacements incorporés, dans le même ensemble de packages déployé.

* Le point de terminaison du référentiel dans l’API publique inclut désormais l’URL Git.

* Dans le workflow Modifier le programme , l’utilisateur n’est autorisé à définir que des valeurs d’ICP non décimales.

* Les échecs intermittents rencontrés lors de la publication du code vers Adobe Git ont maintenant été résolus.

* L’expérience de modification du programme a été actualisée.

## Correctifs {#bug-fixes}

* Au lieu de supprimer des variables &quot;supprimées&quot;, l’API des variables de pipelines ne les marquerait que avec le statut &quot;SUPPRIMÉ&quot;.

* Certains problèmes de qualité du type d’odeur de code affectaient incorrectement l’évaluation de fiabilité.

* Lorsqu’une exécution de pipeline était lancée entre minuit et 1h du matin (UTC), il n’était pas garanti que la version d’artefact générée par Cloud Manager était supérieure à une version créée le jour précédent.

* Certains clients d’Adobe Managed Services (AMS) n’ont pas pu créer de projets dans Adobe I/O Developer Console à l’aide de l’API Cloud Manager.
