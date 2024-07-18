---
title: Notes de mise à jour de la version 2024.7.0
description: Voici les notes de mise à jour de la version 2024.7.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: d536cd96d135e48039f94fd01142a63305b6eeae
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 61%

---


# Notes de mise à jour de la version 2024.7.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2024.7.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de la version 2024.7.0 de [!UICONTROL Cloud Manager] est le 18 juillet 2024. La prochaine version est prévue pour le 8 août 2024.

## Nouveautés {#what-is-new}

* Le [pipeline de production](/help/using/production-pipelines.md#adding-production-pipeline) et le [pipeline hors production](/help/using/non-production-pipelines.md#adding-non-production-pipeline) déclenchent **Lors des modifications Git** pour démarrer le pipeline sur une validation est désormais disponible pour les [référentiels privés.](/help/managing-code/private-repositories.md)
* Un pipeline de pré-production ne peut être déclenché que manuellement et ne peut pas être configuré comme **lors des modifications Git**.
* Pour les pipelines de production seule, la liste des exécutions promouvables inclut celles dont la version d’artefact est supérieure à la version d’artefact déployée sur l’environnement de production.

## Programme d’adoption précoce {#early-adoption}

Prenez part à notre programme d’adoption précoce pour avoir la possibilité de tester certaines fonctionnalités à venir.

### Pipelines dédiés uniquement à l’évaluation ou la production {#staging-production-only-pipelines}

La prise en charge des [pipelines dédiés uniquement à l’évaluation ou la production](/help/using/stage-prod-only.md) a été mise en place, ce qui vous permet de diviser les pipelines de pile complète de déploiement de production en déploiements spécialisés et plus petits.

Si vous souhaitez tester cette nouvelle fonctionnalité et nous faire part de vos commentaires, envoyez un e-mail à l’adresse `Grp-cloudmanager_splitpipelines@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID.
