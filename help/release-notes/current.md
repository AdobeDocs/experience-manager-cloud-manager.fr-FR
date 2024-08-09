---
title: Notes de mise à jour de la version 2024.7.0
description: Découvrez les notes de mise à jour de Cloud Manager 2024.7.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 7%

---


# Notes de mise à jour de Cloud Manager 2024.7.0 {#release-notes}

Cette page documente les notes de mise à jour de [!UICONTROL Cloud Manager] 2024.7.0.

>[!NOTE]
>
>Pour obtenir les dernières notes de mise à jour de Cloud Manager dans AEM as a Cloud Service, voir [Cloud Manager dans AEM as a Cloud Service Notes de mise à jour actuelles](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] 2024.7.0 est le 18 juillet 2024. La prochaine version est prévue pour le mercredi 13 août 2024.

## Nouveautés {#what-is-new}

* Le [pipeline de production](/help/using/production-pipelines.md#adding-production-pipeline) et le [ pipeline hors production](/help/using/non-production-pipelines.md#adding-non-production-pipeline) déclenchent **Lors des modifications Git** pour démarrer le pipeline sur une validation est désormais disponible pour les [référentiels privés](/help/managing-code/private-repositories.md).
* Un pipeline de pré-production n’est déclenchable que manuellement et ne peut pas être configuré comme **Lors des modifications Git**.
* Pour les pipelines de production seule, la liste des exécutions promouvables inclut les exécutions avec une version d’artefact supérieure à la version d’artefact déployée sur l’environnement de production.
* [L’archétype de projet AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/developing/archetype/overview) a été mis à jour vers la [version 49](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49).

## Programme d&#39;adoption précoce {#early-adoption}

Faire partie du programme d’adoption anticipée de Cloud Manager et avoir la possibilité de tester certaines fonctionnalités à venir

### Pipelines d’évaluation uniquement et de production uniquement {#staging-production-only-pipelines}

La prise en charge des [pipelines d’évaluation seule et de production seule](/help/using/stage-prod-only.md) a été introduite, ce qui vous permet de diviser les pipelines de déploiement de production en pile complète en déploiements spécialisés plus petits.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un email à `Grp-cloudmanager_splitpipelines@adobe.com` à partir de votre adresse électronique associée à votre Adobe ID.
