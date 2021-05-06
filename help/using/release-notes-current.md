---
title: Notes de mise à jour de la version 2021.5.0
description: Consultez cette page pour obtenir des informations sur la version 2021.5.0 de Cloud Manager
feature: Informations sur la version
translation-type: tm+mt
source-git-commit: 849a2df2f272973740c1dd8580daaa518f2c9ec4
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 24%

---

# Notes de mise à jour de la version 2021.5.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.5.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la version 2021.5.0 de [!UICONTROL Cloud Manager] est le 06 mai 2021.
La prochaine version est prévue pour le 3 juin 2021.

## Nouveautés {#whats-new}

* La règle de qualité PackageOverlaps détecte désormais les cas où le même package a été déployé plusieurs fois, c’est-à-dire dans plusieurs emplacements incorporés, dans le même jeu de packages déployé.

* Le point de terminaison du référentiel dans l’API publique inclut désormais l’URL Git.

* Dans le processus Modifier le Programme, l’utilisateur n’est autorisé à définir que des valeurs d’indicateur de performance clé non décimales.

* Les échecs intermittents rencontrés lors de la publication du code à l&#39;Adobe Git ont maintenant été résolus.

* L’expérience Modifier le programme a été actualisée.

## Correctifs {#bug-fixes}

* Au lieu de supprimer les variables &quot;supprimées&quot;, l&#39;API des variables de pipeline les marquerait uniquement avec l&#39;état &quot;SUPPRIMÉ&quot;.

* Certains problèmes de qualité du type de code ont eu une incidence incorrecte sur la cote de fiabilité.

* Lorsqu’une exécution de pipeline a été démarrée entre minuit et 1h heure UTC, la version d’artefact générée par Cloud Manager n’était pas garantie supérieure à une version créée le jour précédent.
