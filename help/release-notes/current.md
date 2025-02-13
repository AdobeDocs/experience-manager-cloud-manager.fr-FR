---
title: Notes de mise à jour de la version 2025.2.0 de Cloud Manager
description: En savoir plus sur la version 2025.2.0 de Cloud Manager dans Adobe Managed Services.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 9d9bf7d689c0ace41bce3f31febe8ba78636c01f
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 93%

---

# Notes de mise à jour de Cloud Manager 2025.2.0 dans Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

Découvrez la version de [!UICONTROL Cloud Manager] 2025.2.0 dans Adobe Managed Services.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/home).

## Dates de publication {#release-date}

*Aucun bug notable ni aucune fonctionnalité pour la version de février de Cloud Manager.*

La date de publication de la version 2025.2.0 de [!UICONTROL Cloud Manager] est le vendredi 13 février 2025.

La prochaine version est prévue le vendredi 13 mars 2025.

## Nouveautés {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* À compter du jeudi 13 février 2025, l’étape de qualité du code Cloud Manager utilisera une version mise à niveau de SonarQube 9.9.5.90363.

  Les règles mises à jour, disponibles pour AMS via [ce lien](/help/using/code-quality-testing.md#code-quality-testing-step), déterminent les scores de sécurité et la qualité du code pour les pipelines Cloud Manager. Cette mise à jour peut avoir un impact sur vos points de contrôle qualité et bloquer potentiellement les déploiements.

## Programme d’adoption précoce {#early-adoption}

Prenez part à notre programme d’adoption précoce de Cloud Manager afin de pouvoir tester certaines fonctionnalités à venir.

### Apportez votre propre Git - avec prise en charge de GitLab et Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La fonctionnalité **Apportez votre propre Git** a été étendue pour inclure la prise en charge de référentiels externes tels que GitLab et Bitbucket. Cette nouvelle prise en charge s’ajoute à la prise en charge existante des référentiels GitHub privés et d’entreprise. Lorsque vous ajoutez ces nouveaux référentiels, vous pouvez également les lier directement à vos pipelines. Vous pouvez héberger ces référentiels sur des plateformes cloud publiques ou dans votre infrastructure ou cloud privés. Cette intégration élimine également la nécessité d’une synchronisation constante du code avec le référentiel d’Adobe et permet de valider les requêtes d’extraction avant de les fusionner dans une branche principale.

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
