---
title: Notes de mise à jour de la version 2019.12.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.12.0
description: Consultez cette page pour obtenir des informations sur la version 2019.12.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.12.0 d’AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 1f31e654272afa60cac3376ce4dc3bc76f0d9dda

---

# Notes de mise à jour de la version 2019.12.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2019.12.0 and adds updates to pipeline execution and enhancements to code quality scans.
Pour plus d’informations, consultez les sections ci-après.

## Date de publication {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.12.0 is December 12, 2019.

## Nouveautés {#whats-new}

* Les étapes de l’exécution du pipeline indiquent désormais l’horodatage de fin de chaque étape.
* Les analyses de qualité du code pour les projets qui ne contiennent pas de code Java signalent désormais un taux de couverture du code de 100 %.
* La vérification d’intégrité de la configuration du répartiteur CQ a été supprimée.


## Correctifs {#bug-fixes}

* Les dates ne s’affichaient pas correctement dans certains navigateurs.
* Dans de rares cas, le pipeline de production passerait à l’étape d’approbation alors que les tests de performances étaient toujours en cours d’exécution.
* Dans certains états, les boutons situés en haut de la page d’aperçu n’étaient pas correctement alignés.
* Dans certains cas, des utilisateurs non autorisés ont vu un bouton pour démarrer le pipeline, bien que le bouton lui-même ne puisse pas être cliqué.
* Les boutons d’action pour les pipelines hors production s’affichaient parfois au mauvais endroit.
* Les packages avec le type de noeud granite:Classement n’ont pas pu être analysés pour détecter certaines violations de règles de qualité.
* Certaines défaillances du processus de qualité du code étaient incorrectement comptées comme des bogues.
* Impossible de charger les données de surveillance pour certaines topologies.
