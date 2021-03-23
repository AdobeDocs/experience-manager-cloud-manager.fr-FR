---
title: Notes de mise à jour de la version 2020.3.0
seo-title: Notes de mise à jour de la version 2020.3.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.3.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.3.0 d’AEM Cloud Manager
feature: Informations sur la version
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 100%

---

# Notes de mise à jour de la version 2020.3.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2020.3.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la mise à jour 2020.3.0 de [!UICONTROL Cloud Manager] est le 5 mars 2020.

## Nouveautés {#whats-new}

* Le journal de l’étape de création est désormais disponible pendant l’exécution de l’étape.
* Certains messages de la page des détails d’exécution de pipeline ont été modifiés pour plus de clarté.

## Correctifs {#bug-fixes}

* Certaines configurations de déploiement peuvent rendre indisponibles les journaux des étapes de déploiement en cas d’échec du déploiement.
* Des échecs spécifiques au cours des étapes de déploiement des programmes Managed Services peuvent entraîner l’échec des exécutions ultérieures au démarrage.
* Le démarrage de l’instance éphémère SonarQube utilisée lors de l’étape de création échouait parfois au cours du délai d’expiration configuré.
* Dans le cas de projets spécifiques, la règle *Les objets ResourceResolver doivent toujours être fermés* entraînait une exception de pointeur nul ; cela n’avait toutefois pas d’incidence sur l’exécution du pipeline.