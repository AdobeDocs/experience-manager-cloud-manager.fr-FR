---
title: Notes de mise à jour pour la version 2018.5.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2018.5.0
description: Consultez cette page pour plus d’informations sur la version 2018.5.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2018.5.0 d’AEM Cloud Manager.
uuid: 37f8b155-6984-454d-83a8-3f5fb081be97
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 6d1e7098-b56e-4172-8373-486f186f3d53
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 100%

---


# Notes de mise à jour pour la version 2018.5.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2018.5.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la mise à jour 2018.5.0 de [!UICONTROL Cloud Manager] est le 12 juillet 2018.

## Nouveautés {#what-s-new}

* **Notifications du pipeline CI/CD** : les utilisateurs afficheront désormais les notifications [!UICONTROL Experience Cloud] pour les événements de pipeline. Consultez la section [Notifications](notifications.md) pour en savoir plus.

* **Déploiements en production planifiés** : les utilisateurs peuvent maintenant planifier une date ou une heure pour les déploiements en production. Pour en savoir plus, consultez la section [Déploiement de votre code](deploying-code.md).

* La page **Etat** a été renommée **Activité**.

* Des informations plus spécifiques s’affichent sur la page d’accueil pour les problèmes rencontrés lors de l’exécution du pipeline.
* Améliorations de l’infrastructure des tests de performance.

## Correctifs {#bug-fixes}

* Dans certains cas, un profil SonarQube incorrect était utilisé, ce qui générait des mesures de qualité du code incorrectes.
* La vérification CQBP-75 de SonarQube de tenait pas compte de certaines annotations OSGI.
* Lorsque le pipeline CI/CD était annulé, l’état ne s’affichait pas de manière cohérente.

## Problèmes connus {#known-issues}

* Les liens vers **AEM** et **Surveillance** de l’écran Liste des programmes remplacent l’onglet actuel du navigateur et s’ouvrent dans un nouvel onglet.

