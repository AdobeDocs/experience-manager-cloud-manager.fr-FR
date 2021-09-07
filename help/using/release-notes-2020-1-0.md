---
title: Notes de mise à jour de la version 2020.1.0
seo-title: AEM Cloud Manager Release Notes for 2020.1.0
description: Consultez cette page pour obtenir des informations sur la version 2020.1.0 de Cloud Manager
seo-description: Follow this page to get information for AEM Cloud Manager Release 2020.1.0
feature: Release Information
exl-id: 105e526f-b3c6-49d2-bb4d-d19a5afad6cc
source-git-commit: f4b0957ce2dda55ad9b0d7a736263bece54d2139
workflow-type: ht
source-wordcount: '138'
ht-degree: 100%

---

# Notes de mise à jour de la version 2020.1.0 {#release-notes-for}

La section suivante décrit les notes de mise à jour générales de la version 2020.1.0 de [!UICONTROL Cloud Manager], et ajoute des mises à jour relatives à l’accès aux informations d’identification Git et à l’expérience de connexion.

## Date de publication {#release-date}

La date de publication de la mise à jour 2020.1.0 de [!UICONTROL Cloud Manager] est le 16 janvier 2020.

## Nouveautés {#whats-new}

* Vous pouvez désormais obtenir des informations d’identification Git à partir de l’interface utilisateur de Cloud Manager. Pour plus d’informations, voir [Accès à Git](accessing-repos.md).
* La modification de l’expérience de connexion et de la structure des URL s’inscrit dans un programme global initié par Adobe. Les anciens signets redirigent les utilisateurs vers les nouvelles URL.


## Correctifs {#bug-fixes}

* Les déploiements vers des topologies de type Auteur uniquement ne déployaient pas les modifications de configuration du Dispatcher.
* Dans certaines configurations, la création d’un pipeline de type Qualité de code uniquement s’avérait impossible.
* La carte de résumé de l’environnement sur la page d’aperçu ne s’affichait pas toujours correctement.
* Les exécutions de pipeline pouvaient expirer sur les topologies de grande taille.
