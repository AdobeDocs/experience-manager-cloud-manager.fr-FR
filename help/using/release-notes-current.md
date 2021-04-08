---
title: Notes de mise à jour de la version 2021.4.0
description: Consultez cette page pour obtenir des informations sur la version 2021.4.0 de Cloud Manager
feature: Informations sur la version
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
translation-type: tm+mt
source-git-commit: 1f7f87a4b944d1fadc708958a96a1bda7d41da5d
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 22%

---

# Notes de mise à jour de la version 2021.4.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.4.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la version 2021.4.0 de [!UICONTROL Cloud Manager] est le 08 avril 2021.
La prochaine version est prévue pour le 6 mai 2021.

## Nouveautés {#whats-new}

* Le délai d&#39;attente de la demande pour les utilisateurs virtuels du test de performances a été augmenté de 20 secondes à 60 secondes.

* Le bouton Gérer les tuyaux s’affiche sur la carte Pipelines même si aucun tuyau n’a été configuré.

* Au cours de l&#39;étape de déploiement de la page d&#39;exécution du pipeline, l&#39;utilisateur pourra voir les étapes de déploiement terminées et futures en plus de l&#39;étape actuelle de l&#39;interface utilisateur pour *l&#39;état En cours*.

* La version de l’archétype de projet AEM utilisée par Cloud Manager a été mise à jour vers la version 27.

* Le message d&#39;erreur lors du démarrage d&#39;un pipeline lorsqu&#39;un environnement a été supprimé a été clarifié.

* Les lots OSGi fournis par les projets Eclipse sont maintenant exclus de la règle `CQBP-84--dependencies`.

## Correctifs {#bug-fixes}

* Erreurs rares et transitoires pouvant survenir à l’étape *Test des ressources* du pipeline de production.

* Une barre oblique de fin dans le test de charge du pipeline de production provoquait une panne 404.

* La vérification `Runmode` produisait des faux positifs sur les noeuds non-dossiers.