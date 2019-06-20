---
title: Notes de mise à jour de la version 2019.6.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.6.0
description: Consultez cette page pour obtenir des informations sur la version 2019.6.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.6.0 d’AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 75563d3f4b2a27d943c052993c97d830338ead9c

---

# Notes de mise à jour de la version 2019.6.0 {#release-notes-for}

La version 2019.6.0 de [!UICONTROL Cloud Manager] ne contient pas de modifications fonctionnelles significatives. Pour plus d’informations, suivez les sections ci-après.

## Date de publication {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.6.0 is .

## Nouveautés {#whats-new}

* Nouvel assistant de mise à jour des produits pour aider les clients à exécuter une mise à jour AEM. (lien vers la page Assistant de mise à jour des produits)
* Règles de qualité du code qui examinent les structures de contenu. (lien vers la page Règles Qualité du code personnalisé)
* La taille maximale d&#39;une push git a été augmentée à 1 Go.

## Correctifs {#bug-fixes}

* Dans certains cas, les pipelines ne pouvaient pas être démarrés suite à un échec précédent.

## Problèmes connus {#known-issues}

* Le téléchargement CSV de qualité du code n&#39;est pas toujours trié en fonction de la gravité.
* Les faux positifs peuvent être signalés par la règle configandinstallaidonlycontainosginodes si les configurations osgi sont placées dans un dossier imbriqué sous un dossier de configuration.
