---
title: Notes de mise à jour de la version 2024.5.0
description: Voici les notes de mise à jour de la version 2024.5.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 395fe2a42fc2d6413dff38c9e4620c62039f87e2
workflow-type: ht
source-wordcount: '287'
ht-degree: 100%

---


# Notes de mise à jour de la version 2024.5.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2024.5.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de la version 2024.5.0 de [!UICONTROL Cloud Manager] est le 9 mai 2024. La prochaine version est prévue pour le 6 juin 2024.

## Nouveautés {#what-is-new}

* L’étape d’audit du contenu est désormais ignorée lorsqu’un pipeline est en cours d’exécution [en mode d’urgence.](/help/using/code-deployment.md#emergency-pipeline)

## Programme d’adoption précoce {#early-adoption}

Prenez part à notre programme d’adoption précoce pour avoir la possibilité de tester certaines fonctionnalités à venir.

### Pipelines dédiés uniquement à l’évaluation ou la production {#staging-production-only-pipelines}

La prise en charge des [pipelines dédiés uniquement à l’évaluation ou la production](/help/using/stage-prod-only.md) a été mise en place, ce qui vous permet de diviser les pipelines de pile complète de déploiement de production en déploiements spécialisés et plus petits.

Si vous souhaitez tester cette nouvelle fonctionnalité et nous faire part de vos commentaires, envoyez un e-mail à l’adresse `Grp-cloudmanager_splitpipelines@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID.

### Apporter votre propre GitHub {#byo-github}

Si vous utilisez GitHub pour gérer vos référentiels, [vous pouvez désormais valider le code directement dans vos référentiels GitHub via Cloud Manager.](/help/managing-code/byo-github.md) Cette intégration élimine la nécessité de constamment synchroniser le code avec le référentiel Adobe et vous permet de vérifier les requêtes d’extraction avant de les fusionner dans les branches principales. Cette fonctionnalité est réservée au GitHub public. La prise en charge du GitHub auto-hébergé n’est pas disponible.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à `Grp-CloudManager_BYOG@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID.

## Correctifs {#bug-fixes}

* Correction d’un bug où Cloud Manager réutilisait des artefacts avec un hachage de validation incorrect.
