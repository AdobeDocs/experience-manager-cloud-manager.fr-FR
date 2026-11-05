---
title: Notes de mise à jour de la version 2026.11.0 de Cloud Manager
description: Découvrez la version 2026.11.0 de Cloud Manager dans Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: 'https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro'
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: b48085c8209c0802f6f2d321865bd1a1ee786139
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 10%
---

# Notes de mise à jour de Cloud Manager 2026.11.0 dans Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Découvrez la version  2026.11.0 dans Adobe Managed Services.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/home).

## Dates de publication {#release-date}

La date de publication de  2026.11.0 est le jeudi 5 novembre 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prochaine version prévue est le jeudi 3 décembre 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Nouvelles fonctionnalités {#new-features}

### Pipelines de niveau web pour AEM Managed Services {#web-tier-pipelines}

Cloud Manager prend désormais en charge les pipelines de niveau web dédiés pour les programmes AMS, ce qui permet aux équipes de déployer des configurations de niveau web et Dispatcher indépendamment des déploiements de pile complète. Cela permet une itération plus rapide sur les modifications de niveau web tout en réduisant les exécutions inutiles de pipelines complets.

Lorsqu’un pipeline de niveau web est configuré, les pipelines de pile complète ignorent automatiquement le déploiement de niveau web pour cet environnement afin d’éviter les conflits de déploiement. La suppression du pipeline de couche web restaure automatiquement le comportement de déploiement par défaut. <!-- CMGR-27553 -->

Voir [Pipelines de configuration de niveau web](/help/overview/ci-cd-pipelines.md#web-tier-config-pipelines).

## Programmes bêta {#beta-program}

Aucune opportunité de programme bêta n’est actuellement disponible.

<!--
To get exclusive access to upcoming features before their general release, participate in Cloud Manager's beta programs.

>[!IMPORTANT]
>
>Beta releases contain issues and are provided without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify or otherwise support (through Adobe Support Services or otherwise) the beta releases. Customers use beta releases at their own risk. Do not rely on the correct functioning or performance of beta releases, or on any accompanying documentation or materials. Features and APIs in beta are subject to change without notice. Any use of the beta releases is entirely at the customer's own risk.

The following beta program opportunity is currently available:
-->

## Correctifs {#bug-fixes}


* L’analyse de la qualité du code échoue sur les projets volumineux. L’analyse de la qualité du code (SonarQube) génère des journaux de débogage de plusieurs gigaoctets et est interrompue lors de l’analyse de certaines bibliothèques groupées, échouant ainsi à la création. L&#39;analyse a été corrigée afin qu&#39;elle se termine normalement sur les projets affectés. (CMGR-80025)

* L’exportation CSV d’utilisation des sites affichait des libellés de mois décalés d’un mois. Sur la page Licence > Détails d’utilisation des sites , l’exportation au format CSV affiche les libellés du mois qui ont été décalés d’un mois plus tôt pour les utilisateurs se trouvant dans les fuseaux horaires derrière UTC. L’exportation affiche désormais les libellés de mois corrects, quel que soit le fuseau horaire de l’utilisateur. (CMGR-80903)

* La réutilisation d’un nom de jeton d’accès ne remplace plus le jeton existant. La réutilisation d’un nom de jeton d’accès existant dans un programme remplace le jeton partagé et crée des secrets d’accès en double. Cloud Manager gère désormais correctement la réutilisation des noms de jeton, évitant les remplacements et les doublons accidentels. (CMGR-81236)


<!--
Known Issues {#known-issues}
-->
