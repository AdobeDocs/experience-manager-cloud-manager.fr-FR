---
title: Notes de mise à jour de la version 2020.4.0
seo-title: Notes de mise à jour de la version 2020.4.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.4.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.4.0 d’AEM Cloud Manager
translation-type: tm+mt
source-git-commit: ee7fc8a23dd0719eda84638c810842c2dc1772bb

---

# Notes de mise à jour de la version 2020.4.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2020.4.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.4.0 is April 09, 2020.

## Nouveautés {#whats-new}

* Modifications de la page d’aperçu de navigation Cloud Manager pour permettre à l’utilisateur de modifier ou de changer de  de.
* Modifications permettant à l’utilisateur de modifier des  à partir de la carte  sur la  de Cloud Manager.
* Nouvel état du pipeline **Pipeline En cours d’exécution** s’affichait par rapport au  auquel il est associé.
* Améliorations de la lisibilité de la page d&#39;exécution du pipeline. Ceci inclut l’affichage du nom du pipeline (canal non en production uniquement) et du type, ainsi qu’un badge pour indiquer si l’état du pipeline est En cours/Annulé/Échec.
* Le processus utilisé pour générer les mots de passe Git a été rendu plus résistant aux problèmes de la couche de service sous-jacente.

## Correctifs {#bug-fixes}

* Les données de surveillance peuvent parfois être affichées de manière incorrecte ou pas du tout en fonction de variations mineures des valeurs techniques.
* La configuration Maven utilisée dans le de génération a été mise à jour afin d’éviter les blocages lors du téléchargement des métadonnées d’artefact.
* Le processus de test des performances des ressources n’a pas pu déchiffrer le mot de passe AEM, ce qui a provoqué l’échec des tests.
* Certaines topologies avec des instances de secours peuvent avoir de faux négatifs dans les tests de sécurité.
* Si l’étape  contenait une instance arrêtée, l’étape de test de sécurité échouait parfois.
* Les notifications Experience Cloud n’ont pas été reçues de manière cohérente.

