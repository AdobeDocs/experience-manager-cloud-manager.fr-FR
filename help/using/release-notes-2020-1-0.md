---
title: Notes de mise à jour de la version 2020.1.0
seo-title: Notes de mise à jour de la version 2020.1.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.1.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.1.0 d’AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 854c09878a633bd46e4d7e9d604a8335c225a1c4

---

# Notes de mise à jour de la version 2020.1.0 {#release-notes-for}

La section suivante décrit les notes de mise à jour générales de la version 2020.1.0 de [!UICONTROL Cloud Manager], et ajoute des mises à jour relatives à l’accès aux informations d’identification Git et à l’expérience de connexion.

## Date de publication {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.1.0 is January 16, 2020.

## Nouveautés {#whats-new}

* Vous pouvez désormais obtenir des informations d’identification Git à partir de l’interface utilisateur de Cloud Manager. Pour plus d’informations, voir [Accès à Git](/help/using/accessing-git.md).
* La modification de l’expérience de connexion et de la structure des URL s’inscrit dans un programme global initié par Adobe. Les anciens signets redirigent les utilisateurs vers les nouvelles URL.


## Correctifs {#bug-fixes}

* Les déploiements vers des topologies de type Auteur uniquement ne déployaient pas les modifications de configuration du Dispatcher.
* Dans certaines configurations, la création d’un pipeline de type Qualité de code uniquement s’avérait impossible.
* La carte de résumé de l’environnement sur la page d’aperçu ne s’affichait pas toujours correctement.
* Les exécutions de pipeline pouvaient expirer sur les topologies de grande taille.