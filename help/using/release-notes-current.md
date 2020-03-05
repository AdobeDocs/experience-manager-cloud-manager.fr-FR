---
title: Notes de mise à jour de la version 2020.3.0
seo-title: Notes de mise à jour de la version 2020.3.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.3.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.3.0 d’AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 44671d89edad0ccb6ded998b62beb5fa012678e9

---

# Notes de mise à jour de la version 2020.3.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2020.3.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.3.0 is March 05, 2020.

## Nouveautés {#whats-new}

* Le journal de l’étape de création est désormais disponible pendant l’exécution de l’étape de création.
* Certains messages de la page des détails de l&#39;exécution du pipeline ont été modifiés pour plus de clarté.

## Correctifs {#bug-fixes}

* Certaines configurations de déploiement peuvent rendre indisponibles les journaux des étapes de déploiement en cas d’échec du déploiement.
* Des échecs spécifiques au sein des étapes de déploiement pour les programmes de services gérés peuvent entraîner l’échec des exécutions suivantes.
* L’instance éphémère SonarQube utilisée dans l’étape de création échouait parfois à démarrer dans le délai d’attente configuré.
* Dans le cas de projets spécifiques, les objets *ResourceResolver doivent toujours être fermés* pour générer une exception de pointeur nul ; cela n&#39; a toutefois pas eu d&#39; incidence sur l&#39; exécution du pipeline.


