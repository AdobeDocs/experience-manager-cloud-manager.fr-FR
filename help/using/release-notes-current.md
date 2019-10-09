---
title: Notes de mise à jour de la version 2019.10.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.10.0
description: Consultez cette page pour obtenir des informations sur la version 2019.10.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.10.0 d’AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 1e927076e6bc84e8e1761e33a86cff61a3be0d2f

---

# Notes de mise à jour de la version 2019.10.0 {#release-notes-for}

La section suivante décrit les Notes de mise à jour générales de la version 2018.10.0 de [!UICONTROL Cloud Manager] et ajoute des mises à jour aux étapes de déploiement et à la gestion des versions de projet expert.
Suivez la page ci-dessous pour plus de détails.

## Date de publication {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.10.0 is October 12, 2019.

## Nouveautés {#whats-new}

* Une partie importante des étapes du déploiement a été rendue plus performante.
* Le cas échéant, la version du projet Maven incorporera désormais la version du projet dans git.
* Au moment de la création, de nouvelles variables d’environnement sont disponibles.
* Il est possible de supprimer des pipelines hors production de la carte sur la page Aperçu, ainsi que de l’API.
* Il existe une nouvelle étape d’approbation facultative juste après l’étape de déploiement de l’étape, mais avant l’étape de test de sécurité.
* Lors de la configuration d’un pipeline CI/CD, le détachement et l’association des instances de répartiteur de l’équilibreur de charge peuvent être ignorés pour les environnements de développement et d’évaluation.
Consultez Processus **[de](deploying-code.md#deployment-process)** déploiement pour plus d’informations.
* L’interface de ligne de commande de Cloud Manager a été augmentée pour prendre en charge l’accès aux journaux des étapes d’exécution.
* L’API Cloud Manager prend désormais en charge la modification de la branche configurée d’un pipeline.
* Les requêtes exécutées au cours des tests de performances incluent désormais un jeton ***CloudManagerTest*** spécifique dans l’agent utilisateur.

## Correctifs {#bug-fixes}

* Certaines cartes de la page **Aperçu** n’étaient pas correctement alignées verticalement.
* Certaines conditions d’échec n’entraînaient pas le marquage correct des exécutions de pipeline et empêchaient les exécutions ultérieures.
