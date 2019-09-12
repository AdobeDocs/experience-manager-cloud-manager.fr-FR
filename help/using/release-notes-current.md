---
title: Notes de mise à jour de la version 2019.9.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.9.0
description: Consultez cette page pour obtenir des informations sur la version 2019.9.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.9.0 d’AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 862501f28f5104d0829a6d2d2ad5f5ce9f8ba341

---

# Notes de mise à jour de la version 2019.9.0 {#release-notes-for}

[!UICONTROL La version] 2019.9.0 de Cloud ajoute des mises à jour des graphiques de contrôle de l'intégrité et des graphiques de surveillance Sling Referrer.

## Date de publication {#release-date}

La date de publication de la mise à jour 2019.9.0 de [!UICONTROL Cloud Manager] est le lundi 11 septembre 2019.

## Nouveautés {#whats-new}

* La catégorisation de la vérification de l'intégrité du filtre de référents Sling a été changée de Critique en Important.
* La classification de la vérification de l'intégrité du gestionnaire de bibliothèque HTML a été changée de Critique en Important.
* Les graphiques de surveillance peuvent désormais être téléchargés. Pour plus d’informations, consultez [Surveillance de vos environnements](monitor-your-environments.md).
* Si un programme n'a pas d'environnement AEM Production, cliquez sur la carte de programme de la page d'entrée pour accéder à la page d'aperçu de Cloud Manager, sans produire de boîte de dialogue d'erreur.
* La Carte **Paramètres** du pipeline sur la **page Aperçu** a été renommée Paramètres du pipeline **de production**.
* Les boutons radio importants Comportement d'échec ont été supprimés des pipelines de qualité du code uniquement.
* La page **Activité** affiche désormais le nom du canal pour chaque exécution.
* La page d'exécution affiche désormais le nom du canal.
* La boîte de dialogue de résumé Qualité du code affiche désormais une description de chaque évaluation.

## Correctifs {#bug-fixes}

* Certains utilisateurs n'ont pas pu afficher les détails d'exécution lorsqu'ils attendaient l'approbation.
* Sur **la page Aperçu** , la marge droite n'était pas cohérente.
* Le conteneur de création peut manquer de mémoire dans les projets volumineux.
* Dans certains cas, la règle oakpal bannedpaths n'a pas identifié le contenu installé sous /libs.
* Lorsqu'une barrière de qualité a été rejetée, l'en-tête de dialogue affiche *toujours Partiellement transmis*.

## Problèmes connus {#known-issues}

Le téléchargement des graphiques de surveillance n'est pas disponible dans Safari.
