---
title: Notes de mise à jour de la version 2019.9.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.9.0
description: Consultez cette page pour obtenir des informations sur la version 2019.9.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.9.0 d’AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 26014cfabfee6226033ba2fc1167d8f5509e17c6

---

# Notes de mise à jour de la version 2019.9.0 {#release-notes-for}

The Cloud Manager 2019.9.0 Release updates the security test criteria, adds downloadable monitoring graphs, and fixes some customer-reported usability issues.

## Date de publication {#release-date}

La date de publication de la mise à jour 2019.9.0 de [!UICONTROL Cloud Manager] est le lundi 12 septembre 2019.

## Nouveautés {#whats-new}

* La classification de la vérification de l’intégrité du filtre de référents Sling a été changée de Critique à Important.
* La classification de la vérification de l’intégrité de la configuration du Gestionnaire de bibliothèques HTML a été changée de Critique à Important.
* Les graphiques de surveillance peuvent maintenant être téléchargés. Pour plus d’informations, consultez [Surveillance de vos environnements](monitor-your-environments.md).
* Si un programme ne dispose pas d’un environnement AEM de production, cliquer sur la carte du programme dans la page d’entrée permet d’accéder à la page d’aperçu de Cloud Manager et non de générer une boîte de dialogue d’erreur.
* La carte des paramètres **du** pipeline sur la page **Aperçu** a été remplacée par Paramètres **du pipeline de** production.
* Les boutons radio Comportement d’échec important ont été supprimés des tuyaux de qualité de code uniquement.
* La page **Activité** affiche désormais le nom du pipeline pour chaque exécution.
* La page d’exécution affiche désormais le nom du pipeline.
* La boîte de dialogue Résumé de la qualité du code affiche désormais une description de chaque évaluation.

## Correctifs {#bug-fixes}

* Certains utilisateurs n’ont pas pu afficher les détails d’une exécution en attente d’approbation.
* Sur la page **Aperçu** , la marge droite n’était pas cohérente.
* Le conteneur de génération peut manquer de mémoire dans les projets volumineux.
* Dans certaines circonstances, la règle OakPAL BanningPaths n'a pas identifié le contenu installé sous /libs.
* Lorsqu’une grille de qualité est rejetée, l’en-tête de la boîte de dialogue affiche toujours *Partiellement transmise*.

## Problèmes connus {#known-issues}

* Le téléchargement des graphiques de surveillance n’est pas disponible dans Safari.
