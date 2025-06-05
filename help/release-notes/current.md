---
title: Notes de mise à jour de la version 2025.6.0 de Cloud Manager
description: En savoir plus sur la version 2025.5.0 de Cloud Manager dans Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: d0acd47ea6011dc5896d20d76ab0fcaa970df6ac
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 67%

---

# Notes de mise à jour de Cloud Manager 2025.6.0 dans Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Découvrez la version de [!UICONTROL Cloud Manager] 2025.6.0 dans Adobe Managed Services.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/home).

## Dates de publication {#release-date}

La date de publication de la version 2025.6.0 de [!UICONTROL Cloud Manager] est le vendredi 5 juin 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prochaine version est prévue le vendredi 10 juillet 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## Nouveautés {#what-is-new}

* **Pipelines d’évaluation uniquement et de production uniquement**

  Cloud Manager prend désormais en charge les pipelines d’évaluation uniquement et de production uniquement. Cette fonctionnalité vous permet de diviser les déploiements de production full stack en pipelines plus petits et spécifiques à un objectif. <!-- This feature went into GA from Early Adopter in the June 5, 2025 CM release -->

  ![Boîte de dialogue Ajouter un pipeline hors production avec le bouton radio Code de pile complète sélectionné et Environnement d’évaluation sélectionné](/help/release-notes/assets/add-non-production-pipeline.png)

  Voir [Pipelines d’évaluation uniquement et de production uniquement](/help/using/stage-prod-only.md).

* **Favoris de pipeline**

  Dans cette version, Cloud Manager offre la possibilité d’épingler les pipelines favoris, ce qui vous permet de marquer des pipelines spécifiques comme favoris afin qu’ils apparaissent en haut de la liste sur la page **Pipelines**. Cette amélioration facilite la recherche et l’exécution des pipelines fréquemment consultés. <!-- CMGR-68293 -->

  ![Pipelines marqués comme favoris](/help/release-notes/assets/pipeline-favorites.png) *deux pipelines marqués comme favoris.*

  Voir [Marquer les favoris du pipeline](/help/using/managing-pipelines.md#pipeline-favorites).


## Programme d’adoption précoce {#early-adoption}

Participez au programme d’adoption précoce de Cloud Manager pour obtenir un accès exclusif aux fonctionnalités à venir avant leur publication générale.

Les possibilités d’adoption précoce suivantes sont actuellement disponibles :


### Gérer les jetons d’accès{#access-tokens}

Utilisez la fonctionnalité **Gérer les jetons d’accès** de Cloud Manager pour afficher, renommer et supprimer les jetons d’accès associés aux référentiels Git externes Bring Your Own Git, tels que GitHub Enterprise, GitLab, Bitbucket et Azure DevOps.

Voir [ Gestion des jetons d’accès ](/help/managing-code/manage-access-tokens.md).

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et indiquez si vous utilisez une structure de référentiel privée/publique ou d’entreprise.


### Apportez votre propre Git - avec prise en charge de GitLab et Bitbucket {#gitlab-bitbucket}

La fonctionnalité **Apportez votre propre Git** a été étendue pour inclure la prise en charge de référentiels externes tels que GitLab et Bitbucket. Cette nouvelle prise en charge s’ajoute à la prise en charge existante des référentiels GitHub privés et d’entreprise. Lorsque vous ajoutez ces nouveaux référentiels, vous pouvez également les lier directement à vos pipelines. Vous pouvez héberger ces référentiels sur des plateformes cloud publiques ou dans votre infrastructure ou cloud privés. Cette intégration élimine également la nécessité d’une synchronisation constante du code avec le référentiel d’Adobe et permet de valider les requêtes d’extraction avant de les fusionner dans une branche principale.

Les pipelines qui utilisent des référentiels externes (à l’exclusion de ceux hébergés par GitHub) et le **Déclencheur de déploiement** défini sur **Lors des modifications Git** démarrent désormais automatiquement.

Voir [Ajouter des référentiels externes dans Cloud Manager](/help/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Actuellement, les contrôles de qualité du code des requêtes d’extraction prêts à l’emploi sont exclusifs aux référentiels hébergés par GitHub, mais une mise à jour permettant d’étendre cette fonctionnalité à d’autres fournisseurs Git est en cours.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et indiquez si vous utilisez une structure de référentiel privée/publique ou d’entreprise.


## Correctif des bugs {#bug-fixes}

* AEM Cloud Manager mappe désormais correctement les échecs de build Maven provoqués par des erreurs 409 (conflits) lors de la récupération des artefacts client vers un échec provoqué par le client. Cette modification améliore le message d’erreur en faisant la distinction entre les erreurs internes et les problèmes liés à la configuration de l’environnement client. <!-- CMGR-66673 -->

<!--
Known Issues {#known-issues}

* A -->
