---
title: Intégration Git à Adobe Cloud Manager
description: Série de vidéos qui décrit la configuration et l’intégration d’un référentiel de données géré par le client (sur site) avec Adobe Cloud Manager.
seo-title: Intégration Git à Adobe Cloud Manager
seo-description: Série de vidéos qui décrit la configuration et l’intégration d’un référentiel de données géré par le client (sur site) avec Adobe Cloud Manager.
translation-type: tm+mt
source-git-commit: 519f43ff16e0474951f97798a8e070141e5c124b

---


# Intégration Git à Adobe Cloud Manager

Adobe Cloud Manager est fourni avec un référentiel git unique utilisé pour déployer le code à l’aide des pipelines CI/CD de Cloud Manager. Les clients peuvent utiliser le référentiel Git de Cloud Manager de manière immédiate. Les clients ont également la possibilité d’intégrer un référentiel git sur site ou géré **par le** client à Cloud Manager.

## Présentation de l’intégration Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/?captions=fre_fr)

Cette série de vidéos explore plusieurs cas d’utilisation en ce qui concerne l’intégration d’un référentiel git géré par le client avec Cloud Manager, notamment :

* [Synchronisation initiale](#initial-sync)
* [Stratégie d'embranchement de base](#branching-strategy)
* [Développement des branches de fonctionnalités](#feature-development)
* [Déploiement dans l’environnement de production](#production-deployment)
* [Synchronisation des balises de publication](#sync-tags)

Pour une présentation complète, consultez le Guide [de l’utilisateur de](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)Cloud Manager. La série vidéo suppose une connaissance de base de la gestion du git et du contrôle de code source. Consultez les ressources [supplémentaires ci-dessous](#additional-resources) pour en savoir plus sur git.

>[!NOTE]
>
> Les étapes et les conventions d’attribution de noms décrites dans cette série vidéo représentent quelques bonnes pratiques pour travailler avec un référentiel git géré par le client et Cloud Manager. On s'attend à ce que les conventions et les processus décrits soient adaptés aux différentes équipes de développement.

## Synchronisation initiale {#initial-sync}

Première étape de la synchronisation d’un référentiel Git géré par le client avec le référentiel Git de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12&captions=fre_fr)

## Stratégie d'embranchement de base {#branching-strategy}

Configurez une stratégie d’embranchement de base afin de tirer parti des pipelines [de](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html)production et de non-production de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12&captions=fre_fr)

## Développement des branches de fonctionnalités {#feature-development}

Utilisez une branche de fonctionnalités pour isoler les modifications de code dans un référentiel git géré par le client et pour vous synchroniser avec le référentiel git de Cloud Manager afin d’utiliser un pipeline non productif pour les tests de qualité du code et de validation.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12&captions=fre_fr)

## Déploiement dans l’environnement de production {#production-deployment}

Préparez le code d’une version de production dans un référentiel git géré par le client et synchronisez-le avec le référentiel git de Cloud Manager afin de le déployer dans des environnements d’évaluation et de production.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12&captions=fre_fr)

## Synchronisation des balises de publication {#sync-tags}

Synchronisez les balises de version d’un référentiel Git Cloud Manager dans un référentiel Git géré par le client afin de vous donner une idée du code déployé dans les environnements de production et d’évaluation.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12&captions=fre_fr)

## Ressources supplémentaires {#additional-resources}

* [Documentation de Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
* [Ressources GitHub](https://try.github.io)
* [Didacticiels De Git Atlassien](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Obtenir la feuille de triche](https://education.github.com/git-cheat-sheet-education.pdf)