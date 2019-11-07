---
title: Notes de mise à jour de la version 2019.10.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.10.0
description: Consultez cette page pour obtenir des informations sur la version 2019.10.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.10.0 d’AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 52c54568d8ab7b5091c25b3b65b4baa126bf61f5

---

# Notes de mise à jour de la version 2019.10.0 {#release-notes-for}

La section suivante décrit les notes de mise à jour générales de la version 2019.10.0 de [!UICONTROL Cloud Manager] et ajoute des mises à jour aux étapes de déploiement et à la gestion des versions de projet Maven.
Pour plus d’informations, consultez les sections ci-après.

## Date de publication {#release-date}

[!UICONTROL Cloud Manager] version 2019.10.0 a été publié le 10 octobre 2019.

## Nouveautés {#whats-new}

* Une grande partie des étapes du déploiement a été rendue plus performante.
* Lorsque cela est pertinent, la version du projet Maven incorporera désormais la version du projet dans Git.
* Au moment de la génération, de nouvelles variables d’environnement sont disponibles.
* Il est possible de supprimer des pipelines hors production de la carte sur la page **Aperçu**, ainsi que de l’API.
* Il existe une nouvelle étape d’approbation facultative juste après l’étape de déploiement dans l’environnement intermédiaire, mais avant l’étape de test de sécurité.
* Lors de la configuration d’un pipeline CI/CD, le détachement et l’attachement des instances de dispatcher de l’équilibreur de charge peuvent être ignorés pour les environnements de développement et intermédiaires.
Pour en savoir plus, consultez le **[Processus de déploiement](deploying-code.md#deployment-process)**.
* Le CLI Cloud Manager a été augmenté afin de prendre en charge l’accès aux journaux des étapes d’exécution.
* L’API Cloud Manager prend désormais en charge la modification de la branche configurée d’un pipeline.
* Les requêtes exécutées au cours des tests de performances incluent désormais un jeton ***CloudManagerTest*** spécifique dans l’agent utilisateur.

## Correctifs {#bug-fixes}

* Certaines cartes de la page **Aperçu** n’étaient pas correctement alignées verticalement.
* Certaines conditions d’échec n’entraînaient pas le marquage correct des exécutions de pipeline et empêchaient les exécutions ultérieures.
