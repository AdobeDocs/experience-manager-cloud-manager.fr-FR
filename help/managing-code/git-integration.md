---
title: Intégration Git à Adobe Cloud Manager
description: Cette série de vidéos explique la configuration et l’intégration d’un référentiel Git géré par le client ou la cliente (On-Premise) avec Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
TQID: https://experienceleague.adobe.com/fyGrLuc1bIBY9ZAgYiULxxJQy-ZZBLYtAAdYgqzSLAM
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 2011f63c513689f571d21772752348388c2f342a
workflow-type: tm+mt
source-wordcount: 356
ht-degree: 76%

---

# Intégration Git à Adobe Cloud Manager

Adobe Cloud Manager est fourni avec un référentiel Git unique utilisé pour déployer le code à l’aide des pipelines CI/CD de Cloud Manager. Vous pouvez utiliser le référentiel Git de Cloud Manager comme indiqué, ou vous avez la possibilité d’intégrer un référentiel Git local ou géré par le client avec Cloud Manager.

## Vue d’ensemble de l’intégration Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

Cette série de vidéos explore plusieurs cas d’utilisation concernant l’intégration d’un référentiel Git géré par le client ou la cliente avec Cloud Manager.

* [Synchronisation initiale](#initial-sync)
* [Stratégie d’embranchement de base](#branching-strategy)
* [Développement des branches de fonctionnalités](#feature-development)
* [Déploiement dans l’environnement de production](#production-deployment)
* [Synchronisation des balises de publication](#sync-tags)

Cette série vidéo nécessite des connaissances de base de Git et de la gestion de la commande source. Consultez les [ressources supplémentaires ci-dessous](#additional-resources) pour en savoir plus sur Git.

Les étapes et les conventions de nommage décrites dans cette série vidéo représentent quelques bonnes pratiques pour travailler avec un référentiel Git géré par le client et la cliente et Cloud Manager. Les conventions et les workflows présentés sont adaptés aux différentes équipes de développement.

Pour une vue d’ensemble complète de Cloud Manager, voir la section [Présentation de Cloud Manager](/help/introduction.md).

## Synchronisation initiale {#initial-sync}

Premières étapes de la synchronisation d’un référentiel Git géré par le client ou la cliente avec le référentiel Git de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Stratégie d’embranchement de base {#branching-strategy}

Configurez une stratégie d’embranchement de base pour utiliser les [pipelines de production](/help/using/production-pipelines.md) et [pipelines hors production](/help/using/non-production-pipelines.md) de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Développement des branches de fonctionnalités {#feature-development}

Utilisez une branche de fonctionnalités pour isoler les modifications de code dans un référentiel Git géré par le client ou la cliente et pour vous synchroniser avec le référentiel Git de Cloud Manager afin d’utiliser un pipeline hors production pour les tests de qualité du code et de validation.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Déploiement en production {#production-deployment}

Préparez le code d’une mise à jour de production dans un référentiel Git géré par le client ou la cliente et synchronisez-le avec le référentiel Git de Cloud Manager afin de le déployer dans des environnements d’évaluation et de production.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Synchroniser les balises de version {#sync-tags}

Vous pouvez synchroniser les balises de version d’un référentiel Git Cloud Manager dans un référentiel Git géré par le client ou la cliente. Cette fonctionnalité offre une visibilité sur le code qui a été déployé dans les environnements d’évaluation et de production.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Ressources supplémentaires {#additional-resources}

* [Présentation de Cloud Manager](/help/introduction.md)
* [Ressources GitHub](https://docs.github.com/en/get-started/git-basics/set-up-git)
* [Tutoriels Git pour Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Aide-mémoire Git](https://education.github.com/git-cheat-sheet-education.pdf)
