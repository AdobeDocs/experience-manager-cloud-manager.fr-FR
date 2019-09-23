---
title: Notes de mise à jour de la version 2019.9.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.9.0
description: Consultez cette page pour obtenir des informations sur la version 2019.9.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.9.0 d’AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 26014cfabfee6226033ba2fc1167d8f5509e17c6

---

# Notes de mise à jour de la version 2019.9.0 {#release-notes-for}

La version 2019.9.0 de [!UICONTROL Cloud Manager] 2019 met à jour les critères de test de sécurité, ajoute des graphiques de surveillance téléchargeables et corrige certains problèmes de convivialité signalés par les clients.

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
* The Code Quality summary dialog now shows a description for each rating.

## Correctifs {#bug-fixes}

* Some users could not view an execution details when it was waiting for approval.
* Sur la page **Aperçu** , la marge droite n’était pas cohérente.
* Le conteneur de génération peut manquer de mémoire dans les projets volumineux.
* Under certain circumstances, the BannedPaths OakPAL rule did not identify installed content under /libs.
* Lorsqu’une grille de qualité est rejetée, l’en-tête de la boîte de dialogue affiche toujours *Partiellement transmise*.

## Problèmes connus {#known-issues}

* Downloading of monitoring graphs is not available in Safari.
