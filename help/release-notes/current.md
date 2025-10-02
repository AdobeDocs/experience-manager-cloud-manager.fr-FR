---
title: Notes de mise à jour de la version 2025.10.0 de Cloud Manager
description: En savoir plus sur la version 2025.10.0 de Cloud Manager dans Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 03fc811a1a617263efd0f1d5667bba6975826a0e
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 59%

---

# Notes de mise à jour de Cloud Manager 2025.10.0 dans Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Découvrez la version de [!UICONTROL Cloud Manager] 2025.10.0 dans Adobe Managed Services.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/home).

## Dates de publication {#release-date}

La date de publication de la version 2025.10.0 de [!UICONTROL Cloud Manager] est le vendredi 2 octobre 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prochaine version est prévue le vendredi 6 novembre 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Nouveautés {#what-is-new}







## Programmes bêta {#beta-program}

Participez aux programmes Beta de Cloud Manager pour obtenir un accès exclusif aux fonctionnalités à venir avant leur publication générale.

Les opportunités suivantes sont actuellement disponibles :

### Extensibilité et personnalisation d’Experience Hub {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/experience-hub/experience-hub) sert de point d’entrée à AEM, personnalisé en fonction des besoins de votre entreprise. Informez Adobe de vos extensions d’interface utilisateur AEM existantes afin qu’elles puissent vous aider à les activer dans Experience Hub avec un effort minimal.

![Diagramme du workflow d’extensibilité et de personnalisation d’Experience Hub](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Intégrez des expériences personnalisées dans Experience Hub pour étendre et personnaliser le tableau de bord de votre organisation. Outre les widgets intégrés d’Adobe, ajoutez les vôtres à l’aide du framework [Extensibilité de l’interface utilisateur](https://developer.adobe.com/uix/docs/). Créez des applications d’interface utilisateur basées sur JavaScript et faites-les apparaître à vos utilisateurs pour répondre aux besoins et aux workflows spécifiques à l’entreprise.

Intéressé par la version bêta ? Envoyez un courrier électronique à l’adresse [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) avec votre ID d’organisation Adobe et une brève description de la personnalisation que vous avez l’intention de créer.

### Versions plus rapides avec mise en cache du module {#quick-build-cm-pipelines}

Un nouveau modèle de version compile uniquement les modules modifiés (plutôt que le référentiel entier) à l’aide de la mise en cache au niveau du module pour réduire les temps de création. Elle s’applique aux pipelines de qualité de code, full stack et intermédiaires uniquement.

Intéressé par la version bêta ? Envoyez [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) par e-mail avec votre ID d’organisation et votre ID de programme Adobe.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->


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

La version d’octobre de Cloud Manager ne contient aucun correctif significatif.

<!--
Known Issues {#known-issues}

* A -->
