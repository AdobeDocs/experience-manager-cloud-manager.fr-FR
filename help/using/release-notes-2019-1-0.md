---
title: Notes de mise à jour de la version 2019.1.0
seo-title: AEM Cloud Manager Release Notes for 2019.1.0
description: Consultez cette page pour obtenir des informations sur la version 2019.1.0 de Cloud Manager.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2019.1.0.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
feature: Release Information
exl-id: 383ca5a0-4b0b-48e9-aa48-1d1388875329
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: ht
source-wordcount: '319'
ht-degree: 100%

---

# Notes de mise à jour de la version 2019.1.0 {#release-notes-for}

La version 2018.9.0 de [!UICONTROL Cloud Manager] prend également en charge le test des programmes AEM Assets ainsi que d’autres types de pipelines qui exécutent les étapes de génération et de contrôle qualité de code, en se déployant éventuellement dans un environnement hors production.

## Date de publication {#release-date}

La date de publication de la version 2019.1.0 de [!UICONTROL Cloud Manager] est le 17 janvier 2019.

## Nouveautés {#whats-new}

* Ajout de la prise en charge des tests de performance d’AEM Assets. Reportez-vous au document [Configuration de pipelines de production](configuring-production-pipelines.md) pour en savoir plus.
* Ajout de la prise en charge des pipelines qui exécutent uniquement des étapes de génération et de contrôle qualité du code ainsi que des pipelines déployés dans des environnements hors production. Reportez-vous au document [Configuration de pipelines hors production](configuring-non-production-pipelines.md) pour en savoir plus.
* Ajout de la prise en charge des variables d’environnement personnalisées dans l’environnement de génération.
* Pour les clients disposant de plusieurs environnements d’évaluation ou de production, la sélection de l’environnement qui sera déployé dans le cadre du pipeline de production est disponible. Reportez-vous au document [Configuration de pipelines de production](configuring-production-pipelines.md) pour en savoir plus.
* Ajout de httxt2dbm au conteneur de génération.
* Tous les éléments de menu d’aide ouvrent un nouvel onglet.

## Correctifs {#bug-fixes}

* Lors de la modification d’un programme, il était possible de désélectionner tous les ensembles de pages.
* L’étape d’approbation portait un nom incorrect.
* Dans certains cas, le logo du programme était incorrectement mis en forme.
* Si seul le package de configuration du dispatcher était généré, l’étape de déploiement échouait.
* Les environnements qui contenaient des instances de secours à froid n’étaient pas gérés correctement.
* Certains programmes abandonnés s’affichaient sur le commutateur de programmes.
* Si une nouvelle branche avait été ajoutée au référentiel Git alors que le pipeline était en cours de modification, elle n’était peut-être pas immédiatement sélectionnable.
* Sur certains écrans, l’icône Developer Connection du menu Aide n’était pas visible.
* La touche de tabulation n’était pas correctement gérée dans la boîte de dialogue de configuration du vidage du Dispatcher.

## Problèmes connus {#known-issues}

* Lors de l’ouverture d’un programme pour lequel les IPC sont définis pour AEM Sites, mais pas pour AEM Assets, tous les utilisateurs voient une carte d’appel à l’action avec un bouton de **Configurer le programme**. Cependant, seuls les utilisateurs ayant le rôle Propriétaire de l’entreprise peuvent cliquer sur le bouton **Configurer le programme**.
