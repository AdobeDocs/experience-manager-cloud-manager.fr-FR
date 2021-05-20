---
title: Notes de mise à jour de la version 2019.7.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.7.0
description: Consultez cette page pour obtenir des informations sur la version 2019.7.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.7.0 d’AEM Cloud Manager.
feature: Informations sur la version
exl-id: 7e53bd97-5aa7-45bc-83c6-49e40266e1b1
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 100%

---

# Notes de mise à jour de la version 2019.7.0 {#release-notes-for}

La version 2019.7.0 de [!UICONTROL Cloud Manager] ajoute des mises à jour aux notifications et améliorations d’Experience Cloud sous forme de correctifs. Pour plus d’informations, consultez les sections ci-après.

## Date de publication {#release-date}

La date de publication de la mise à jour 2019.7.0 de [!UICONTROL Cloud Manager] est le 18 juillet 2019.

## Nouveautés {#whats-new}

Une notification Experience Cloud est maintenant envoyée au début d’un déploiement en production.

## Correctifs {#bug-fixes}

* Dans certains cas, Cloud Manager effectuait une analyse de code statique sur les fichiers Python et PHP.
* Les packages contenant des InstallHooks FileVault n’étaient pas systématiquement exécutés par l’étape de qualité du code.
* Dans certaines combinaisons, les problèmes de qualité du code n’étaient pas systématiquement triés.
* La page d’exécution du pipeline présentait certains problèmes visuels.
* L’étape de test des performances peut échouer parfois en raison de contraintes de ressources provenant de l’infrastructure de cloud sous-jacente.
* Certaines compilations de clients échouaient en raison de problèmes de réseau.
