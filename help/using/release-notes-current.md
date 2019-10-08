---
title: Notes de mise à jour de la version 2019.10.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.10.0
description: Consultez cette page pour obtenir des informations sur la version 2019.10.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.10.0 d’AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: de9d2834ffa6c235e580227bd020fb8a0b94d22c

---

# Notes de mise à jour de la version 2019.10.0 {#release-notes-for}

La version 2019.10.0 de [!UICONTROL Cloud Manager] met à jour les critères de test de sécurité, ajoute des graphiques de surveillance téléchargeables et corrige certains problèmes d’utilisation signalés par les clients.

## Date de publication {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.10.0 is October 12, 2019.

## Nouveautés {#whats-new}

* Une partie importante des étapes du déploiement a été rendue plus performante.
* Le cas échéant, la version du projet Maven incorporera désormais la version du projet dans git.
* Au moment de la création, de nouvelles variables d’environnement sont disponibles.
* Il est possible de supprimer des pipelines hors production de la carte sur la page Aperçu, ainsi que de l’API.
* Il existe une nouvelle étape d’approbation facultative juste après l’étape de déploiement de l’étape, mais avant l’étape de test de sécurité.
* Lors de la configuration d’un pipeline CI/CD, le détachement et l’association des instances de répartiteur de l’équilibreur de charge peuvent être ignorés pour les environnements de développement et d’évaluation.
* L’interface de ligne de commande de Cloud Manager a été augmentée pour prendre en charge l’accès aux journaux des étapes d’exécution.
* L’API Cloud Manager prend désormais en charge la modification de la branche configurée d’un pipeline.
* Les requêtes exécutées lors des tests de performances incluent désormais un jeton spécifique ("CloudManagerTest") dans l’agent utilisateur.

## Correctifs {#bug-fixes}

* Certaines cartes de la page Aperçu n’étaient pas correctement alignées verticalement.
* Certaines conditions d’échec n’entraînaient pas le marquage correct des exécutions de pipeline et empêchaient les exécutions ultérieures.
