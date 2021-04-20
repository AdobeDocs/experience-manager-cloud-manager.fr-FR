---
title: Notes de mise à jour de la version 2019.9.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.9.0
description: Consultez cette page pour obtenir des informations sur la version 2019.9.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.9.0 d’AEM Cloud Manager.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 100%

---

# Notes de mise à jour de la version 2019.9.0 {#release-notes-for}

La version 2019.9.0 de [!UICONTROL Cloud Manager] met à jour les critères de test de sécurité, ajoute des graphiques de surveillance téléchargeables et corrige certains problèmes d’utilisation signalés par les clients.

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] Version 2019.9.0 est le 12 septembre 2019.

## Nouveautés {#whats-new}

* La classification de la vérification de l’intégrité du filtre de référents Sling a été changée de Critique à Important.
* La classification de la vérification de l’intégrité de la configuration du gestionnaire de bibliothèques HTML a été changée de Critique à Important.
* Les graphiques de surveillance peuvent maintenant être téléchargés. Pour plus d’informations, consultez [Surveillance de vos environnements](monitor-your-environments.md).
* Si le programme ne dispose pas d’un environnement AEM de production, cliquer sur la carte du programme sur la page d’entrée permet d’accéder à la page d’aperçu de Cloud Manager et ne produit pas de boîte de dialogue d’erreur.
* La carte **Paramètres du pipeline** de la page **Aperçu** a été remplacée par **Paramètres du pipeline de production**.
* Les cases d’option de comportement en cas d’échec important ont été supprimées des pipelines de qualité de code uniquement.
* La page **Activité** affiche désormais le nom du pipeline pour chaque exécution.
* La page d’exécution affiche désormais le nom du pipeline.
* La boîte de dialogue de résumé de la qualité du code affiche désormais une description de chaque évaluation.

## Correctifs {#bug-fixes}

* Certains utilisateurs ne pouvaient pas afficher les détails d’une exécution en attente d’approbation.
* Dans la page **Aperçu**, la marge de droite n’était pas cohérente.
* Le conteneur de génération pouvait manquer de mémoire dans les projets volumineux.
* Dans certaines circonstances, la règle OakPAL BannedPaths n’identifiait pas le contenu installé sous /libs.
* Lorsqu’un point de contrôle qualité était rejeté, l’en-tête de la boîte de dialogue affichait toujours *Réussite partielle*.

## Problèmes connus {#known-issues}

* Le téléchargement des graphiques de surveillance n’est pas disponible dans Safari.
