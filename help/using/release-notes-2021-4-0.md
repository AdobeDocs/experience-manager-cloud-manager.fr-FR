---
title: Notes de mise à jour de la version 2021.4.0
description: Consultez cette page pour obtenir des informations sur la version 2021.4.0 de Cloud Manager
feature: Informations sur la version
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 5f81fdb86b1dfa6c748bb7784ef00dc062c9f8ef
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 23%

---

# Notes de mise à jour de la version 2021.4.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.4.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la version 2021.4.0 de [!UICONTROL Cloud Manager] est le 08 avril 2021.

## Nouveautés {#whats-new}

* Le délai d’attente de la requête pour les utilisateurs virtuels de test de performance a été augmenté de 20 secondes à 60 secondes.

* Le bouton Gérer Git s’affiche sur la carte Pipelines même lorsqu’aucun pipeline n’a été configuré.

* Au cours de l’étape de déploiement de la page d’exécution du pipeline, l’utilisateur pourra afficher les étapes de déploiement terminées et futures, en plus de l’étape actuelle de l’interface utilisateur pour l’état *En cours* .

* La version de l’archétype de projet AEM utilisé par Cloud Manager a été mise à jour vers la version 27.

* Le message d’erreur lors du démarrage d’un pipeline lorsqu’un environnement a été supprimé a été clarifié.

* Les lots OSGi fournis par les projets Eclipse sont désormais exclus de la règle `CQBP-84--dependencies`.

## Correctifs {#bug-fixes}

* Erreurs rares et transitoires pouvant se produire à l’étape *Test des ressources* dans le pipeline de production.

* Une barre oblique de fin dans le test de chargement du pipeline de production provoquait un échec 404.

* La vérification `Runmode` produisait des faux positifs sur les noeuds non-dossiers.