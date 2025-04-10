---
title: Notes de mise à jour de la version 2025.4.0 de Cloud Manager
description: En savoir plus sur la version 2025.4.0 de Cloud Manager dans Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 40d093ce7d6839fff4ba16f790c61b96cb88dda5
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 92%

---

# Notes de mise à jour de Cloud Manager 2025.4.0 dans Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Découvrez la version de [!UICONTROL Cloud Manager] 2025.4.0 dans Adobe Managed Services.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/home).

## Dates de publication {#release-date}

La date de publication de la version 2025.4.0 de [!UICONTROL Cloud Manager] est le vendredi 10 avril 2025.

La prochaine version est prévue le vendredi 8 mai 2025.

<!--
## What's new {#what-is-new}

* 
-->


## Programme d’adoption précoce {#early-adoption}

Participez au programme d’adoption précoce de Cloud Manager pour obtenir un accès exclusif aux fonctionnalités à venir avant leur publication générale.

Les possibilités d’adoption précoce suivantes sont actuellement disponibles :

### Apportez votre propre Git - avec prise en charge de GitLab et Bitbucket {#gitlab-bitbucket}

La fonctionnalité **Apportez votre propre Git** a été étendue pour inclure la prise en charge de référentiels externes tels que GitLab et Bitbucket. Cette nouvelle prise en charge s’ajoute à la prise en charge existante des référentiels GitHub privés et d’entreprise. Lorsque vous ajoutez ces nouveaux référentiels, vous pouvez également les lier directement à vos pipelines. Vous pouvez héberger ces référentiels sur des plateformes cloud publiques ou dans votre infrastructure ou cloud privés. Cette intégration élimine également la nécessité d’une synchronisation constante du code avec le référentiel d’Adobe et permet de valider les requêtes d’extraction avant de les fusionner dans une branche principale.

Les pipelines qui utilisent des référentiels externes (à l’exclusion de ceux hébergés par GitHub) et le **Déclencheur de déploiement** défini sur **Lors des modifications Git** démarrent désormais automatiquement.

Voir [Ajouter des référentiels externes dans Cloud Manager](/help/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Actuellement, les contrôles de qualité du code des requêtes d’extraction prêts à l’emploi sont exclusifs aux référentiels hébergés par GitHub, mais une mise à jour permettant d’étendre cette fonctionnalité à d’autres fournisseurs Git est en cours.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et indiquez si vous utilisez une structure de référentiel privée/publique ou d’entreprise.

### Pipelines dédiés uniquement à l’évaluation ou à la production {#staging-production-only-pipelines}

Adobe se réjouit d’annoncer l’introduction de la prise en charge des [pipelines dédiés uniquement à l’évaluation ou à la production](/help/using/stage-prod-only.md). Cette nouvelle fonctionnalité vous permet de diviser les pipelines de déploiement de production en pile pleine en déploiements plus petits et plus spécialisés.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID.



<!--
### Self-service Service Pack updates for AMS Cloud Manager customers 

As part of the early adopters program, Adobe Managed Services Cloud Manager customers can now perform self-service service pack updates through the **Cloud Manager** user interface. This feature is currently available *only for development environments* and includes limited error reporting for failures.  

Customers can check for service pack updates on the **Program Overview** page under the **Environments** section (**three-dot menu**).

![Check for updates menu option](/help/release-notes/assets/check-for-updates-1.png)

![Update Service Pack dialog box](/help/release-notes/assets/check-for-updates-2.png)

The installation and upgrade process can be tracked on the **Activity** page. 

Once the process is complete, customers must **approve the execution** for the service pack upgrade to finalize successfully.

![Approve service page update](/help/release-notes/assets/check-for-updates-3.png)

If you are interested in testing this new feature and sharing your feedback, contact your Adobe Customer Success Engineer.

See also [Service Pack Updates for Development Environments - Early Adopter](/help/using/service-packs-environments.md).
-->



## Correctifs {#bug-fixes}

* A

Problèmes connus {#known-issues}

* A —>
