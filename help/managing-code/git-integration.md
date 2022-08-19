---
title: Intégration Git à Adobe Cloud Manager
description: Cette série de vidéos explique la configuration et l’intégration d’un référentiel Git géré par le client (On-Premise) avec Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 91e909273bf2b21d7f6413731923011915079e45
workflow-type: ht
source-wordcount: '347'
ht-degree: 100%

---


# Intégration Git à Adobe Cloud Manager

Adobe Cloud Manager est fourni avec un référentiel Git unique utilisé pour déployer le code à l’aide des pipelines CI/CD de Cloud Manager. Vous pouvez utiliser le référentiel Git de Cloud Manager prêt à l’emploi ou vous avez également la possibilité d’intégrer un référentiel Git On-Premise ou géré par le client avec Cloud Manager.

## Présentation de l’intégration Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

Cette série de vidéos explore plusieurs cas d’utilisation concernant l’intégration d’un référentiel Git géré par le client avec Cloud Manager.

* [Synchronisation initiale](#initial-sync)
* [Stratégie d’embranchement de base](#branching-strategy)
* [Développement des branches de fonctionnalités](#feature-development)
* [Déploiement dans l’environnement de production](#production-deployment)
* [Synchronisation des balises de publication](#sync-tags)

Cette série de vidéos part du principe que les spectateurs possèdent des connaissances de base de la gestion de Git et du contrôle de code source. Consultez les [ressources supplémentaires ci-dessous](#additional-resources) pour en savoir plus sur Git.

Les étapes et les conventions d’attribution de noms décrites dans cette série vidéo représentent quelques bonnes pratiques pour travailler avec un référentiel Git géré par le client et Cloud Manager. On s’attend à ce que les conventions et les workflows décrits soient adaptés aux équipes de développement individuelles.

Pour une présentation complète de Cloud Manager, consultez le document [Présentation de Cloud Manager](/help/introduction.md).

## Synchronisation initiale {#initial-sync}

Premières étapes de la synchronisation d’un référentiel Git géré par le client avec le référentiel Git de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Stratégie d’embranchement de base {#branching-strategy}

Configurez une stratégie d’embranchement de base afin de tirer parti des [pipelines de production](/help/using/production-pipelines.md) et [hors production](/help/using/non-production-pipelines.md) de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Développement des branches de fonctionnalités {#feature-development}

Utilisez une branche de fonctionnalités pour isoler les modifications de code dans un référentiel Git géré par le client et pour vous synchroniser avec le référentiel Git de Cloud Manager afin d’utiliser un pipeline hors production pour les tests de qualité du code et de validation.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Déploiement dans l’environnement de production {#production-deployment}

Préparez le code d’une mise à jour de production dans un référentiel Git géré par le client et synchronisez-le avec le référentiel Git de Cloud Manager afin de le déployer dans des environnements d’évaluation et de production.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Synchronisation des balises de mise à jour {#sync-tags}

Synchronisez les balises de mise à jour d’un référentiel Git Cloud Manager dans un référentiel Git géré par le client afin d’obtenir une visibilité sur le code déployé dans les environnements d’évaluation et de production.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Ressources supplémentaires {#additional-resources}

* [Présentation de Cloud Manager](/help/introduction.md)
* [Ressources GitHub](https://try.github.io)
* [Didacticiels Atlassian Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Antisèche Git](https://education.github.com/git-cheat-sheet-education.pdf)
