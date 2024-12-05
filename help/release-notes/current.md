---
title: Notes de mise à jour de la version 2024.12.0 de Cloud Manager
description: Découvrez la version de Cloud Manager 2024.12.0 sur Adobe Managed Services.
feature: Release Information
source-git-commit: ee79124a012106e53ffaaf9462202712f7078809
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 65%

---

# Notes de mise à jour de Cloud Manager 2024.12.0 sur Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Découvrez la version de [!UICONTROL Cloud Manager] 2024.12.0 sur Adobe Managed Services.

>[!NOTE]
>
>Consultez les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/home).

## Dates de publication {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

La date de publication de [!UICONTROL Cloud Manager] 2024.12.0 est le 5 décembre 2024.

La prochaine version est prévue le vendredi 23 janvier 2025.

## Nouveautés {#what-is-new}

* L’étape AEM Qualité du code utilise désormais le serveur SonarQube 9.9, en remplacement de l’ancienne version 7.4. Cette mise à niveau apporte des contrôles de sécurité, de performance et de qualité du code supplémentaires, offrant ainsi une analyse et une couverture plus complètes de vos projets. <!-- CMGR-45683 -->

## Programme d’adoption précoce {#early-adoption}

Prenez part à notre programme d’adoption précoce de Cloud Manager afin de pouvoir tester certaines fonctionnalités à venir.

### Apportez votre propre Git - avec prise en charge de GitLab et Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La fonctionnalité **Bring Your Own Git** a été étendue pour inclure la prise en charge de référentiels externes, tels que GitLab et Bitbucket. Cette nouvelle prise en charge s’ajoute à la prise en charge existante des référentiels GitHub privés et d’entreprise. Lorsque vous ajoutez ces nouveaux référentiels, vous pouvez également les lier directement à vos pipelines. Vous pouvez héberger ces référentiels sur des plateformes cloud publiques ou dans votre infrastructure ou cloud privés. Cette intégration élimine également la nécessité d’une synchronisation constante du code avec le référentiel d’Adobe et permet de valider les requêtes d’extraction avant de les fusionner dans une branche principale.

Les pipelines qui utilisent des référentiels externes (à l’exclusion de ceux hébergés par GitHub) et le **Déclencheur de déploiement** défini sur **Lors des modifications Git** démarrent désormais automatiquement.

Voir [Ajouter des référentiels externes dans Cloud Manager](/help/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Actuellement, les contrôles de qualité du code des requêtes d’extraction prêts à l’emploi sont exclusifs aux référentiels hébergés par GitHub, mais une mise à jour permettant d’étendre cette fonctionnalité à d’autres fournisseurs Git est en cours.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et indiquez si vous utilisez une structure de référentiel privée/publique ou d’entreprise.


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
