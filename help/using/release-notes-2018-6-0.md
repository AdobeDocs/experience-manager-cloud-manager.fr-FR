---
title: Notes de mise à jour de la version 2018.6.0
seo-title: AEM Cloud Manager Release Notes for 2018.6.0
description: Consultez cette page pour obtenir des informations sur la version 2018.6.0 de Cloud Manager.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2018.6.0.
uuid: 211b6e1b-10fb-46b0-b591-44d5e44abd77
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 8584f467-3e61-41ea-98e4-f79e68c86469
feature: Release Information
exl-id: 456f7892-c64c-4b3f-b845-15682d034aaa
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: ht
source-wordcount: '321'
ht-degree: 100%

---

# Notes de mise à jour de la version 2018.6.0 {#release-notes-for}

La section suivante présente les notes de mises à jour générales de la version 2018.6.0 de [!UICONTROL Cloud Manager]. Cette version prend en charge l’invalidation du Dispatcher lors des déploiements, des notifications supplémentaires et des améliorations de la convivialité.

## Date de publication {#release-date}

La date de publication de la version 2018.6.0 de [!UICONTROL Cloud Manager] est le 9 août 2018.

## Nouveautés {#what-s-new}

* **Pipeline CI/CD** : invalidation configurable du Dispatcher et purge du cache à la fois dans les environnements d’évaluation et de production lors de l’exécution du pipeline CI/CD. Reportez-vous au document [Configuration de pipelines de production](configuring-production-pipelines.md) pour en savoir plus.

* **Pipeline CI/CD** : lors de la configuration du pipeline, il est désormais possible de définir le comportement de celui-ci lorsqu’il rencontre un échec important à l’un des points de contrôle qualité. Reportez-vous au document [Configuration de pipelines de production](configuring-production-pipelines.md) pour en savoir plus.

* **Pipeline CI/CD** - lors de la configuration du pipeline, il est désormais possible de choisir si vous souhaitez que la supervision du CSE soit effectuée par votre CSE ou par tout CSE disponible. Reportez-vous au document [Configuration de pipelines de production](configuring-production-pipelines.md) pour en savoir plus.

* **Pipeline CI/CD** : lorsque le pipeline CI/CD atteint l’étape d’approbation, une notification est envoyée aux utilisateurs autorisés à approuver le déploiement. Pour en savoir plus, reportez-vous à la section [Notifications](notifications.md).

* **Pipeline CI/CD** : lorsque le pipeline CI/CD atteint l’étape de définition de la planification, une notification est envoyée aux utilisateurs autorisés à définir la planification. Pour en savoir plus, reportez-vous à la section [Notifications](notifications.md).

* **Analyse de la qualité du code** : nouvelles règles permettant d’identifier les requêtes HTTP/HTTPS sortantes incorrectement configurées. Pour en savoir plus, consultez la section [Règles de qualité du code personnalisé](custom-code-quality-rules.md).

## Correctifs {#bug-fixes}

* Dans certains cas, le test de performance n’était pas entièrement distribué entre plusieurs instances de dispatcher et de publication.
* La navigation d’en-tête disparaissait dans les fenêtres de navigateur étroites.
* Certains paramètres de pipeline n’étaient pas désactivés pendant l’exécution du pipeline.
* Les liens vers AEM et Surveillance dans l’écran Liste des programmes remplaçaient l’onglet du navigateur actuel et ouvraient un nouvel onglet.
* Dans certains cas, une longue période d’approbation pouvait entraîner un échec de déploiement.
