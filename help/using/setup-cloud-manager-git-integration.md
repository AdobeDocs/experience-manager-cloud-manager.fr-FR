---
title: Intégration Git à Adobe Cloud Manager
description: Série de vidéos qui décrit la configuration et l’intégration d’un référentiel Git géré par le client (sur site) avec Adobe Cloud Manager.
seo-title: Intégration Git à Adobe Cloud Manager
seo-description: Série de vidéos qui décrit la configuration et l’intégration d’un référentiel Git géré par le client (sur site) avec Adobe Cloud Manager.
feature: Référentiels Git
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Intégration Git à Adobe Cloud Manager

Adobe Cloud Manager est fourni avec un référentiel Git unique utilisé pour déployer le code à l’aide des pipelines CI/CD de Cloud Manager. Ce référentiel Git de Cloud Manager est prêt à l’emploi. Les clients ont également la possibilité d’intégrer un référentiel Git sur site ou **géré par le client** à Cloud Manager.

## Présentation de l’intégration Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

Cette série de vidéos explore plusieurs cas d’utilisation concernant l’intégration d’un référentiel Git géré par le client à Cloud Manager, notamment :

* [Synchronisation initiale](#initial-sync)
* [Stratégie d’embranchement de base](#branching-strategy)
* [Développement des branches de fonctionnalités](#feature-development)
* [Déploiement dans l’environnement de production](#production-deployment)
* [Synchronisation des balises de publication](#sync-tags)

Pour une présentation complète, consultez le [Guide de l’utilisateur de Cloud Manager](https://docs.adobe.com/content/help/fr/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html). La série vidéo suppose une connaissance de base de la gestion de Git et de la gestion de commande source. Consultez les [ressources supplémentaires ci-dessous](#additional-resources) pour en savoir plus sur Git.

>[!NOTE]
>
> Les étapes et les conventions d’attribution de noms décrites dans cette série vidéo représentent quelques bonnes pratiques pour travailler avec un référentiel Git géré par le client et Cloud Manager. On s’attend à ce que les conventions et les workflows décrits soient adaptés aux équipes de développement individuelles.

## Synchronisation initiale {#initial-sync}

Premières étapes de la synchronisation d’un référentiel Git géré par le client avec le référentiel Git de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Stratégie d’embranchement de base {#branching-strategy}

Configurez une stratégie d’embranchement de base afin de tirer parti des [pipelines de production et hors production](https://docs.adobe.com/content/help/fr/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html) de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Développement des branches de fonctionnalités {#feature-development}

Utilisez une branche de fonctionnalités pour isoler les modifications de code dans un référentiel Git géré par le client et pour vous synchroniser avec le référentiel Git de Cloud Manager afin d’utiliser un pipeline hors production pour les tests de qualité du code et de validation.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Déploiement dans l’environnement de production {#production-deployment}

Préparez le code d’une version de production dans un référentiel Git géré par le client et synchronisez-le avec le référentiel Git de Cloud Manager afin de le déployer dans des environnements intermédiaires et de production.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Synchronisation des balises de publication {#sync-tags}

Synchronisez les balises de publication d’un référentiel Git Cloud Manager dans un référentiel Git géré par le client afin de vous donner une idée du code déployé dans les environnements intermédiaires et de production.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Ressources supplémentaires {#additional-resources}

* [Documentation Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
* [Ressources GitHub](https://try.github.io)
* [Didacticiels Atlassian Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Antisèche Git](https://education.github.com/git-cheat-sheet-education.pdf)
