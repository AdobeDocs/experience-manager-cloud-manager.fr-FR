---
title: Intégration Git à Adobe Cloud Manager
description: Cette série de vidéos décrit la configuration et l’intégration d’un référentiel Git géré par le client (on-premise) avec Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 3671772a1369273d89fde101ba084a6e2f8ce8dc
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 21%

---


# Intégration Git avec Adobe Cloud Manager

Adobe Cloud Manager est fourni avec un seul référentiel Git utilisé pour déployer du code à l’aide des pipelines CI/CD Cloud Manager. Vous pouvez utiliser le référentiel Git Cloud Manager prêt à l’emploi ou vous avez également la possibilité d’intégrer un référentiel Git sur site ou géré par le client à Cloud Manager.

## Présentation de l’intégration Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/) (3 minutes, 11 secondes)

Cette série de vidéos explore plusieurs cas d’utilisation concernant l’intégration d’un référentiel Git géré par le client à Cloud Manager.

* [Synchronisation initiale](#initial-sync)
* [Stratégie d’embranchement de base](#branching-strategy)
* [Développement des branches de fonctionnalités](#feature-development)
* [Déploiement dans l’environnement de production](#production-deployment)
* [Synchronisation des balises de publication](#sync-tags)

Cette série vidéo suppose une connaissance de base de la gestion Git et du contrôle de code source. Pour plus d’informations sur Git, voir les [ressources supplémentaires ci-dessous](#additional-resources) .

Les étapes et les conventions de dénomination décrites dans cette série vidéo représentent quelques bonnes pratiques pour travailler avec un référentiel Git géré par le client et Cloud Manager. On s’attend à ce que les conventions et les workflows décrits soient adaptés aux équipes de développement individuelles.

Pour une vue d’ensemble complète de Cloud Manager, voir la section [Présentation de Cloud Manager](/help/introduction.md).

## Synchronisation initiale {#initial-sync}

Premières étapes de la synchronisation d’un référentiel Git géré par le client avec le référentiel Git de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12) (8 minutes)

## Stratégie d’embranchement de base {#branching-strategy}

Configurez une stratégie d’embranchement de base pour tirer parti des [pipelines de production](/help/using/production-pipelines.md) et [des pipelines hors production](/help/using/non-production-pipelines.md) de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12) (3 minutes, 48 secondes)

## Développement des branches de fonctionnalités {#feature-development}

Utilisez une branche de fonctionnalités pour isoler les modifications de code dans un référentiel Git géré par le client et synchroniser avec le référentiel Git de Cloud Manager pour utiliser un pipeline hors production pour les tests de qualité et de validation du code.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12) (9 minutes)

## Déploiement en production {#production-deployment}

Préparez le code d’une version de production dans un référentiel Git géré par le client et synchronisez-le avec le référentiel Git Cloud Manager pour le déploiement dans les environnements d’évaluation et de production.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12) (6 minutes, 6 secondes)

## Synchronisation des balises de publication {#sync-tags}

Vous pouvez synchroniser les balises de version d’un référentiel Git Cloud Manager dans un référentiel Git géré par le client. Cette fonctionnalité offre une visibilité sur le code qui a été déployé dans les environnements d’évaluation et de production.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12) (2 minutes, 57 secondes)

## Ressources supplémentaires {#additional-resources}

* [Présentation de Cloud Manager](/help/introduction.md)
* [Ressources GitHub](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [Didacticiels Atlassian Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Antisèche Git](https://education.github.com/git-cheat-sheet-education.pdf)
