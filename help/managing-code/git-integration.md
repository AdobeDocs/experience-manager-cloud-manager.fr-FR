---
title: Intégration Git à Adobe Cloud Manager
description: Cette série de vidéos explique la configuration et l’intégration d’un référentiel Git géré par le client ou la cliente (On-Premise) avec Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 51bd685a17eb9d68b1ec8245e6167cab02101fc1
workflow-type: ht
source-wordcount: '331'
ht-degree: 100%

---


# Intégration Git à Adobe Cloud Manager

Adobe Cloud Manager est fourni avec un référentiel Git unique utilisé pour déployer le code à l’aide des pipelines CI/CD de Cloud Manager. Vous pouvez utiliser le référentiel Git de Cloud Manager prêt à l’emploi ou vous avez également la possibilité d’intégrer un référentiel Git On-Premise ou géré par le client ou la cliente avec Cloud Manager.

## Vue d’ensemble de l’intégration Git

>[!VIDEO](https://video.tv.adobe.com/v/31135?captions=fre_fr)

Cette série de vidéos explore plusieurs cas d’utilisation concernant l’intégration d’un référentiel Git géré par le client ou la cliente avec Cloud Manager.

* [Synchronisation initiale](#initial-sync)
* [Stratégie d’embranchement de base](#branching-strategy)
* [Développement des branches de fonctionnalités](#feature-development)
* [Déploiement dans l’environnement de production](#production-deployment)
* [Synchronisation des balises de publication](#sync-tags)

Cette série de vidéos part du principe que les spectateurs et spectatrices possèdent des connaissances de base de la gestion de Git et du contrôle de code source. Consultez les [ressources supplémentaires ci-dessous](#additional-resources) pour en savoir plus sur Git.

Les étapes et les conventions de nommage décrites dans cette série vidéo représentent quelques bonnes pratiques pour travailler avec un référentiel Git géré par le client et la cliente et Cloud Manager. On s’attend à ce que les conventions et les workflows décrits soient adaptés aux équipes de développement individuelles.

Pour une vue d’ensemble complète de Cloud Manager, voir la section [Présentation de Cloud Manager](/help/introduction.md).

## Synchronisation initiale {#initial-sync}

Premières étapes de la synchronisation d’un référentiel Git géré par le client ou la cliente avec le référentiel Git de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/31134/?quality=12&captions=fre_fr)

## Stratégie d’embranchement de base {#branching-strategy}

Configurez une stratégie d’embranchement de base afin de tirer parti des [pipelines de production](/help/using/production-pipelines.md) et des [pipelines hors production](/help/using/non-production-pipelines.md) de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/31133/?quality=12&captions=fre_fr)

## Développement des branches de fonctionnalités {#feature-development}

Utilisez une branche de fonctionnalités pour isoler les modifications de code dans un référentiel Git géré par le client ou la cliente et pour vous synchroniser avec le référentiel Git de Cloud Manager afin d’utiliser un pipeline hors production pour les tests de qualité du code et de validation.

>[!VIDEO](https://video.tv.adobe.com/v/31132/?quality=12&captions=fre_fr)

## Déploiement en production {#production-deployment}

Préparez le code d’une mise à jour de production dans un référentiel Git géré par le client ou la cliente et synchronisez-le avec le référentiel Git de Cloud Manager afin de le déployer dans des environnements d’évaluation et de production.

>[!VIDEO](https://video.tv.adobe.com/v/31131/?quality=12&captions=fre_fr)

## Synchroniser les balises de version {#sync-tags}

Vous pouvez synchroniser les balises de version d’un référentiel Git Cloud Manager dans un référentiel Git géré par le client ou la cliente. Cette fonctionnalité offre une visibilité sur le code qui a été déployé dans les environnements d’évaluation et de production.

>[!VIDEO](https://video.tv.adobe.com/v/31130/?quality=12&captions=fre_fr)

## Ressources supplémentaires {#additional-resources}

* [Présentation de Cloud Manager](/help/introduction.md)
* [Ressources GitHub](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [Didacticiels Atlassian Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Antisèche Git](https://education.github.com/git-cheat-sheet-education.pdf)
