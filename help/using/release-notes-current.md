---
title: Notes de mise à jour de la version 2020.8.0
seo-title: Notes de mise à jour de la version 2020.8.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.8.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.8.0 d’AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 3be958aa21d5423ddf371c286825d01afd554c4b
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 49%

---

# Notes de mise à jour de la version 2020.8.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2020.8.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la mise à jour 2020.8.0 de [!UICONTROL Cloud Manager] est le 06 août 2020.

## Nouveautés {#whats-new}

* Les tests de performances des sites prennent désormais en charge l’utilisation facultative de l’authentification.

   Pour plus de détails, reportez-vous à la section .

* Les référentiels Maven privés liés à l’authentification sont désormais pris en charge.

## Correctifs {#bug-fixes}

* Certains modules externes SonarQube inutiles et indésirables étaient exécutés dans le cadre de l’analyse de la qualité du code.

* Sur la page d&#39;exécution du pipeline, le nom de la branche n&#39;était pas correctement formaté.

* Lors d’un déploiement sur des topologies avec une seule publication, un répartiteur unique et un auteur Secondaire à froid, le répartiteur a été supprimé par erreur de l’équilibreur de charge.

* Dans certains cas, les exécutions de pipeline achevées n&#39;ont pas été enregistrées comme ayant été achevées, ce qui a empêché de nouvelles exécutions de pipeline.

* Les exécutions de pipelines se retrouveraient parfois *bloquées* en raison de problèmes de communication interne.

* L’info-bulle des cartes de programme n’était pas toujours correcte.

* Il y avait une incohérence de couleur sur la page d&#39;aperçu.

## Problèmes connus {#known-issues}

* Si un environnement AMS contient une instance de secours, le message consigné indique que l’instance est hors service, et non en mode de secours.

* En raison d’un changement au niveau du mode de calcul de la couverture du code, la version _minimale_ du plug-in Jacoco est désormais 0.7.5.201505241946 (publiée en mai 2015). Un message d’erreur sera généré dans le processus de qualité du code pour les clients qui référencent une version plus ancienne de manière explicite.
