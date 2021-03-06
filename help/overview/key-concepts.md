---
title: Concepts clés
description: Comme tous les outils puissants, Cloud Manager englobe de nombreux concepts et termes. Ce document résume les éléments les plus importants pour vous lorsque vous commencez à utiliser Cloud Manager.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: 73e322cf93dc7709b7581860974079c8d94034ba
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 10%

---


# Concepts clés {#key-concepts}

Comme tous les outils puissants, Cloud Manager englobe de nombreux concepts et termes. Ce document résume les éléments les plus importants pour vous lorsque vous commencez à utiliser Cloud Manager.

## Application {#application}

Et l’application est l’ensemble des personnalisations et des configurations créées par un client pour adapter la sous-jacente [solution](#solution) (AEM Sites ou AEM Assets, par exemple) en fonction de leurs cas d’utilisation et besoins spécifiques. Une application est une unité logique qui peut être composée de plusieurs [artefacts.](#artifact)

Exemple d’application : [application de style de vie WKND.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=fr)

## Artefact {#artifact}

Un artefact est une unité déployable et résulte d’un processus de génération qui transforme le code source en une seule unité. Par exemple, un fichier .zip contenant le code source.

## Référentiel d’artefacts {#artifact-repository}

Un référentiel d’artefacts est un emplacement de stockage spécifique au client. [artefacts](#artifact) sont enregistrées et sécurisées.

## Environnement {#environment}

Un environnement est un groupe unique de machines virtuelles au sein d’un même [programme.](#program) Pour AEM, il est composé d’une instance de création (éventuellement avec une instance de création Secondaire à froid supplémentaire), de zéro ou plusieurs instances de publication, d’une ou plusieurs instances de dispatcher et d’un équilibreur de charge.

## référentiel git {#git-repository}

Un référentiel git est un emplacement où le code source spécifique au client est stocké et est accessible. [utilisation de git.](https://git-scm.com)

## Instance {#instance}

Une instance est un serveur virtuel spécifique qui exécute l’AEM [solution.](#solution) Les instances représentent une seule unité logique du point de vue du déploiement.

## Organisation {#organization}

Une organisation est un concept d’Adobe représentant un client d’entreprise. Une société peut avoir plusieurs organisations en fonction de leur configuration dans le système Identity Management (IMS) d’Adobe.

## Pipeline {#pipeline}

Un pipeline est un ensemble d’étapes de déploiement exécutées en séquence.

## Produit {#product}

Un produit est un ensemble spécifique de fonctionnalités d’un [solution](#solution) sous licence par une organisation. Différent [programmes](#program) au sein d’une organisation peut avoir droit à différents ensembles de produits, par exemple AEM Sites, AEM Assets ou AEM Forms.

## Programme {#program}

Un programme est un ensemble d’environnements qui prennent en charge un regroupement logique d’initiatives clients, correspondant généralement à un contrat de niveau de service (SLA) acheté. Chaque programme comprend un environnement de production précis et peut intégrer un grand nombre d’environnements hors production.

## Solution {#solution}

Une solution est l’un des Adobes [!UICONTROL Experience Cloud] solutions. Par exemple, Adobe Experience Manager, Adobe Target ou Adobe Analytics.

## Étape {#step}

Une étape est un jeu d’instructions configuré qui exécute une unité de travail en tant que bloc de création d’une [pipeline.](#pipeline)
