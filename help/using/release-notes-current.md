---
title: Notes de mise à jour de la version 2019.6.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.6.0
description: Consultez cette page pour obtenir des informations sur la version 2019.6.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.6.0 d’AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: ef6a0a0bdc22e37357304823d6f0a70d84917fa4

---

# Notes de mise à jour de la version 2019.6.0 {#release-notes-for}

La version 2019.6.0 de [!UICONTROL Cloud Manager] ne contient pas de modifications fonctionnelles significatives. Pour plus d’informations, suivez les sections ci-après.

## Date de publication {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.6.0 is June 20, 2019 .

## Nouveautés {#whats-new}

* Assistant de mise à jour de nouveaux produits pour aider les clients à exécuter une mise à jour AEM. Refer to [Product Update Wizard](overview-productupdate-wizard.md) to learn more.
* Règles de qualité du code qui examinent les structures de contenu. Refer to [Custom Code Quality Rules](custom-code-quality-rules.md) for more information.
* La taille maximale d&#39;une push git a été augmentée à 1 Go.

## Correctifs {#bug-fixes}

* Dans certains cas, les pipelines ne pouvaient pas être démarrés suite à un échec précédent.

## Problèmes connus {#known-issues}

* Le téléchargement CSV de qualité du code n&#39;est pas toujours trié en fonction de la gravité.
* False positives may be reported by the *ConfigAndInstallShouldOnlyContainOsgiNodes* rule if OSGi configurations are placed in a nested folder under a *config* folder.
