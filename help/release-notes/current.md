---
title: Notes de mise à jour de la version 2026.7.0 de Cloud Manager
description: Découvrez la version 2026.7.0 de Cloud Manager dans Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 3b9ef92a96dab9c1f4b93466d8a2d15185b5864f
workflow-type: tm+mt
source-wordcount: 390
ht-degree: 10%

---


# Notes de mise à jour de Cloud Manager 2026.7.0 dans Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Découvrez la version  2026.6.0 dans Adobe Managed Services.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/home).

## Dates de publication {#release-date}

La date de publication de  2026.7.0 est le jeudi 9 juillet 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prochaine version prévue est le jeudi 6 août 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Nouveautés {#what-is-new}

<!-- There are no significant new features in the June 2026 Cloud Manager on AMS release. -->

* **Amélioration des performances de build avec la mise en cache du module**
Un nouveau modèle de version compile uniquement les modules modifiés (plutôt que le référentiel entier) à l’aide de la mise en cache au niveau du module pour améliorer les performances de la version. Elle s’applique aux pipelines de production. Vous contrôlez les pipelines de production qui utilisent **Smart Build**.

  Pour plus d’informations, consultez les sections suivantes :

  * [À propos de l’utilisation du Smart Build dans un pipeline de production](/help/using/production-pipelines.md#about-smart-build) et [À propos de l’utilisation du Smart Build dans un pipeline hors production](/help/using/non-production-pipelines.md#about-smart-build)
  * [Ajouter un pipeline de production](/help/using/production-pipelines.md#adding-production-pipeline) et [Ajouter un pipeline hors production](/help/using/non-production-pipelines.md#add-non-production-pipeline).

## Programmes bêta {#beta-program}

Pour obtenir un accès exclusif aux fonctionnalités à venir avant leur publication générale, participez aux programmes bêta de Cloud Manager.

>[!IMPORTANT]
>
>Les versions de Beta contiennent des défauts et sont fournies « EN L’ÉTAT » sans garantie d’aucune sorte. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge (par le biais des services d’assistance Adobe ou d’une autre manière) les versions bêta. Les clients utilisent les versions bêta à leurs risques et périls. Ne vous fiez pas au bon fonctionnement ou aux performances des versions bêta, ni à la documentation ou aux documents d’accompagnement. Les fonctionnalités et API de la version bêta peuvent être modifiées sans préavis. Toute utilisation des versions Beta s’effectue entièrement aux risques et périls du client.

Les opportunités de programme Beta suivantes sont actuellement disponibles :

### Pipelines de niveau web pour AEM Managed Services {#web-tier-pipelines}

Cloud Manager prend désormais en charge les pipelines de niveau web dédiés pour les programmes AMS, ce qui permet aux équipes de déployer des configurations de niveau web et Dispatcher indépendamment des déploiements de pile complète. Cela permet une itération plus rapide sur les modifications de niveau web tout en réduisant les exécutions inutiles de pipelines complets. Lorsqu’un pipeline de niveau web est configuré, les pipelines de pile complète ignorent automatiquement le déploiement de niveau web pour cet environnement afin d’éviter les conflits de déploiement. La suppression du pipeline de couche web restaure automatiquement le comportement de déploiement par défaut.

Pour rejoindre Beta, contactez votre ingénieur du succès client Adobe pour en savoir plus.




## Correctifs {#bug-fixes}

Il n’existe aucun correctif significatif dans la version de juillet 2026 de Cloud Manager on AMS.

<!--
Known Issues {#known-issues}

* A 
-->
