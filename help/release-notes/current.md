---
title: Notes de mise à jour de la version 2024.8.0 de Cloud Manager
description: Voici les notes de mise à jour de la version 2024.8.0 de Cloud Manager.
feature: Release Information
source-git-commit: 5ced643fabe0a670e456cbea72f9da8196ac774a
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 28%

---


# Notes de mise à jour de Cloud Manager 2024.8.0 {#release-notes}

Cette page présente les notes de mise à jour de la version 2024.8.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les dernières notes de mise à jour de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Cloud Manager dans AEM as a Cloud Service - Notes de mise à jour actuelles](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Date de publication {#release-date}

La date de publication de la version 2024.8.0 de [!UICONTROL Cloud Manager] est le jeudi 14 août 2024. La prochaine version est prévue pour le 14 septembre 2024.

## Nouveautés {#what-is-new}

* Pour les pipelines d’évaluation seule et de production seule (disponibles dans le cadre du [programme d’adoption précoce](#staging-production-only-pipelines)), vous pouvez désormais les exécuter en [mode d’urgence,](/help/using/stage-prod-only.md#emergency-mode) en ignorant les tests d’étape.

## Programme d’adoption précoce {#early-adoption}

Faites partie du programme Cloud Manager d’adoption anticipée et avez la possibilité de tester certaines fonctionnalités à venir.

### Pipelines d’évaluation et de production uniquement {#staging-production-only-pipelines}

Adobe est heureux d’annoncer l’introduction de la prise en charge des [pipelines d’évaluation uniquement et de production seule](/help/using/stage-prod-only.md). Cette nouvelle fonctionnalité vous permet de diviser les pipelines de déploiement de production en pile complète en déploiements plus petits et plus spécialisés.

Si vous souhaitez tester cette fonctionnalité et fournir des commentaires, envoyez un email `Grp-cloudmanager_splitpipelines@adobe.com` à l’aide de l’adresse électronique associée à votre Adobe ID.

## Correctifs

* Correction d’un problème rare en raison duquel les étapes de pipeline s’exécutaient après la suppression du pipeline.
* La réexécution du pipeline fonctionne désormais lors de la première tentative, corrigeant un problème rare où une réexécution devait être lancée plusieurs fois.
* Les étapes de déploiement planifiées pour les pipelines entièrement empilés respectent désormais la date planifiée sélectionnée et ne reviennent pas à **Maintenant**.
* Les états des tâches de contenu de copie ayant échoué sont désormais correctement reflétés et n’affichent plus incorrectement l’état `In Progress` dans de rares cas.

## Problèmes connus {#known-issues}

{{content-copy-known-issues}}
