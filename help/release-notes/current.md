---
title: Notes de mise à jour de la version 2025.8.0 de Cloud Manager
description: En savoir plus sur la version 2025.8.0 de Cloud Manager dans Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: b34fe26f8c9a2d59a7df3d03717f302fe4456352
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 63%

---

# Notes de mise à jour de Cloud Manager 2025.8.0 dans Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Découvrez la version de [!UICONTROL Cloud Manager] 2025.8.0 dans Adobe Managed Services.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/home).

## Dates de publication {#release-date}

La date de publication de la version 2025.8.0 de [!UICONTROL Cloud Manager] est le vendredi 7 août 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prochaine version est prévue le 4 septembre 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## Nouveautés {#what-is-new}

* **Adobe Experience Hub bientôt disponible**

  À partir du 19 août 2025, Adobe commence le déploiement échelonné de la nouvelle Experience Hub auprès de tous les utilisateurs de Adobe Experience Manager.

  Experience Hub est un point de départ unifié qui offre des expériences contextuelles personnalisées pour aider les utilisateurs à atteindre plus rapidement leurs objectifs. Le déploiement se termine le 26 août 2025, date à laquelle il sera disponible pour tous les utilisateurs. Le nouvel Experience Hub est accessible directement sur [experience.adobe.com](https://experience.adobe.com/). Pour en savoir plus, voir [Adobe Experience Hub](/help/experience-hub.md).

* **Pipelines d’évaluation uniquement et de production uniquement**

  Cloud Manager prend désormais en charge les pipelines d’évaluation uniquement et de production uniquement. Cette fonctionnalité vous permet de diviser les déploiements de production full stack en pipelines plus petits et spécifiques à un objectif. <!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![Boîte de dialogue Ajouter un pipeline hors production avec le bouton radio Code de pile complète sélectionné et Environnement d’évaluation sélectionné](/help/release-notes/assets/add-non-production-pipeline.png)

  Voir [Pipelines d’évaluation uniquement et de production uniquement](/help/using/stage-prod-only.md).

* **Pipelines favoris**

  Dans cette version, Cloud Manager offre la possibilité d’épingler les pipelines favoris, ce qui vous permet de marquer des pipelines spécifiques comme favoris afin qu’ils apparaissent en haut de la liste sur la page **Pipelines**. Cette amélioration facilite la recherche et l’exécution des pipelines fréquemment consultés. <!-- CMGR-68293 -->

  ![Pipelines marqués comme favoris](/help/release-notes/assets/pipeline-favorites.png) *Deux pipelines marqués comme favoris.*

  Voir la section [Marquer les pipelines favoris](/help/using/managing-pipelines.md#pipeline-favorites).


## Programmes bêta {#beta-program}

Participez aux programmes Beta de Cloud Manager pour obtenir un accès exclusif aux fonctionnalités à venir avant leur publication générale.

Les opportunités suivantes sont actuellement disponibles :


### Apporter votre propre Git (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Les clientes et clients peuvent désormais intégrer leurs référentiels Git Azure DevOps dans Cloud Manager, avec la prise en charge des référentiels Azure DevOps modernes et VSTS (Visual Studio Team Services) hérités.

* Pour les utilisateurs et utilisatrices d’Edge Delivery Services, le référentiel intégré peut être utilisé pour synchroniser et déployer le code du site.
* Pour les utilisateurs et utilisatrices d’AEM as a Cloud Service et d’Adobe Managed Services (AMS), le référentiel peut être lié aux pipelines full stack et front-end.

La prise en charge de types de pipeline supplémentaires et de la validation des demandes d’extraction par le biais de pipelines de qualité du code sera bientôt disponible.

Voir [Ajouter des référentiels externes dans Cloud Manager](/help/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/release-notes/assets/azure-repo.png)

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et indiquez si vous utilisez une structure de référentiel privée/publique ou d’entreprise.

#### Gérer les jetons d’accès{#manage-access-tokens}

Utilisez **Gérer les jetons d’accès** dans Cloud Manager pour afficher, renommer et supprimer les jetons d’accès associés aux référentiels BYOG externes, tels que GitHub Enterprise, GitLab, Bitbucket et Azure DevOps.

Voir la section [Gérer les jetons d’accès](/help/managing-code/manage-access-tokens.md).

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## Correctifs {#bug-fixes}

La version d’août de Cloud Manager ne contient aucun correctif significatif.

<!--
Known Issues {#known-issues}

* A -->
