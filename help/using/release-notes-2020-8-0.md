---
title: Notes de mise à jour de la version 2020.8.0
seo-title: Notes de mise à jour de la version 2020.8.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.8.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.8.0 d’AEM Cloud Manager
translation-type: ht
source-git-commit: c1d07c95088a279376ef495001a5165c7e459642
workflow-type: ht
source-wordcount: '196'
ht-degree: 100%

---

# Notes de mise à jour de la version 2020.8.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2020.8.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la mise à jour 2020.8.0 de [!UICONTROL Cloud Manager] est le 06 août 2020.

## Nouveautés {#whats-new}

Les référentiels Maven privés liés à l’authentification sont désormais pris en charge.

## Correctifs {#bug-fixes}

* Certains plug-ins SonarQube inutiles et indésirables étaient exécutés dans le cadre de l’analyse de la qualité du code.

* Sur la page d’exécution du pipeline, le nom de la branche n’était pas correctement formaté.

* Lors d’un déploiement sur des topologies avec une seule publication, un Dispatcher unique et un auteur secondaire à froid, le Dispatcher était supprimé par erreur de l’équilibreur de charge.

* Dans certains cas, les exécutions de pipeline achevées n’étaient pas été enregistrées comme ayant été achevées, ce qui empêchait de nouvelles exécutions de pipeline.

* Les exécutions de pipelines étaient parfois *bloquées* en raison de problèmes de communication interne.

* Les info-bulles des cartes de programme n’étaient pas toujours correctes.

* Les couleurs n’étaient pas cohérentes sur la page **Aperçu**.

* Les tests de performances des sites prennent désormais en charge l’utilisation facultative de l’authentification.

* Les caches du Dispatcher des instances d’auteur sont automatiquement vidés lorsque les configurations du Dispatcher sont déployées via Cloud Manager.

