---
title: Notes de mise à jour de la version 2026.9.0 de Cloud Manager
description: Découvrez la version 2026.9.0 de Cloud Manager dans Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: e10c3c15c01c28f6bad0a9cf0464288937402cb7
workflow-type: tm+mt
source-wordcount: 403
ht-degree: 8%

---


# Notes de mise à jour de Cloud Manager 2026.9.0 dans Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Découvrez la version  2026.9.0 dans Adobe Managed Services.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/home).

## Dates de publication {#release-date}

La date de publication de  2026.9.0 est le jeudi 3 septembre 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prochaine version prévue est le jeudi 1er octobre 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Nouveautés {#what-is-new}

Il n’existe aucune nouvelle fonctionnalité significative dans la version de septembre 2026 de Cloud Manager on AMS.


## Programmes bêta {#beta-program}

Pour obtenir un accès exclusif aux fonctionnalités à venir avant leur publication générale, participez aux programmes bêta de Cloud Manager.

>[!IMPORTANT]
>
>Les versions de Beta contiennent des défauts et sont fournies sans garantie d’aucune sorte. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge d’une autre manière (par le biais des services d’assistance Adobe ou d’une autre manière) les versions bêta. Les clients utilisent les versions bêta à leurs risques et périls. Ne vous fiez pas au bon fonctionnement ou aux performances des versions bêta, ni à la documentation ou aux documents d’accompagnement. Les fonctionnalités et API de la version bêta peuvent être modifiées sans préavis. Toute utilisation des versions Beta s’effectue entièrement aux risques et périls du client.

L’opportunité de programme Beta suivante est actuellement disponible :

### Pipelines de niveau web pour AEM Managed Services {#web-tier-pipelines}

Cloud Manager prend désormais en charge les pipelines de niveau web dédiés pour les programmes AMS, ce qui permet aux équipes de déployer des configurations de niveau web et Dispatcher indépendamment des déploiements de pile complète. Cela permet une itération plus rapide sur les modifications de niveau web tout en réduisant les exécutions inutiles de pipelines complets. Lorsqu’un pipeline de niveau web est configuré, les pipelines de pile complète ignorent automatiquement le déploiement de niveau web pour cet environnement afin d’éviter les conflits de déploiement. La suppression du pipeline de couche web restaure automatiquement le comportement de déploiement par défaut.

Pour rejoindre Beta, contactez votre ingénieur du succès client Adobe pour en savoir plus.


## Correctifs {#bug-fixes}

* La régénération d’un mot de passe d’accès au référentiel invalide désormais l’ancien mot de passe. Auparavant, la régénération du mot de passe d’accès au référentiel Git n’invalidait pas immédiatement le mot de passe précédent, ce qui laissait les anciennes informations d’identification utilisables. La régénération du mot de passe invalide désormais immédiatement l’ancien, ce qui garantit que les informations d’identification précédentes ne peuvent plus être utilisées. (CMGR-41820)

* Vérifications des autorisations mises à jour pour appliquer la propriété des ressources. Correction d’un problème lié à l’évaluation des vérifications d’autorisations afin que l’accès à un programme soit toujours validé par rapport à l’organisation qui le possède. Cela renforce l’isolement entre les organisations pour les opérations soumises à autorisation. (CMGR-79156)

<!--
Known Issues {#known-issues}
-->
