---
title: Concepts clés
description: Comme tous les outils puissants, Cloud Manager englobe plusieurs concepts et termes. Ce document résume les éléments les plus importants à connaître lorsque vous commencez à utiliser Cloud Manager.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 52%

---


# Principaux concepts {#key-concepts}

Comme tous les outils puissants, Cloud Manager englobe plusieurs concepts et termes. Ce document résume les éléments les plus importants à connaître lorsque vous commencez à utiliser Cloud Manager.

## Application {#application}

Une application est l’ensemble de personnalisations et de configurations créées par un client pour adapter la [solution](#solution) sous-jacente (telle qu’AEM Sites ou AEM Assets) à ses cas d’utilisation et besoins spécifiques. Une application est une unité logique qui peut être composée de plusieurs [artefacts](#artifact).

Un exemple d&#39;application est l&#39; [application de style de vie WKND](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview) fictive.

## Artefact {#artifact}

Un artefact est une unité déployable qui résulte d’un processus de génération qui transforme le code source en une seule unité. Par exemple, un fichier .zip contenant le code source.

## Référentiel d’artefacts {#artifact-repository}

Un référentiel d’artefacts est un emplacement de stockage où sont enregistrés et sécurisés les [artefacts](#artifact) spécifiques des clients.

## Environnement {#environment}

Un environnement est un cluster unique de machines virtuelles au sein d&#39;un [programme](#program). Pour AEM, cet environnement est composé d’une instance de création (éventuellement avec une instance de création Cold Standby supplémentaire), de zéro ou plusieurs instances de publication, d’une ou de plusieurs instances Dispatcher et d’un équilibreur de charge.

## Référentiel Git {#git-repository}

Un référentiel Git est un emplacement où le code source spécifique au client est stocké et est accessible [à l’aide de Git](https://git-scm.com).

## Instance {#instance}

Une instance est un serveur virtuel spécifique qui exécute la AEM [solution](#solution). Les instances représentent une seule unité logique du point de vue du déploiement.

## Organisation {#organization}

Une organisation est un concept d’Adobe représentant un client d’entreprise. Une société peut être constituée de plusieurs organisations en fonction de la configuration initiale du système Identity Management (IMS) d’Adobe.

## Pipeline {#pipeline}

Un pipeline est un ensemble d’étapes de déploiement exécutées ou &quot;exécutées&quot; en séquence.

## Produit {#product}

Un produit est un ensemble spécifique de fonctionnalités au sein d’une [solution](#solution) autorisée par une organisation. Au sein d’une organisation, différents [programmes](#program) peuvent bénéficier de différents ensembles de produits, tels qu’AEM Sites, AEM Assets ou AEM Forms.

## Programme {#program}

Un programme est un ensemble d’environnements qui prennent en charge un regroupement logique d’initiatives client, correspondant en règle générale à un contrat de niveau de service (SLA) acheté. Chaque programme comprend un environnement de production précis et peut intégrer un grand nombre d’environnements hors production.

## Solution {#solution}

Une solution désigne l’une des solutions [!UICONTROL Experience Cloud] d’Adobe. Par exemple, Adobe Experience Manager, Adobe Target ou Adobe Analytics.

## Étape {#step}

Une étape est un ensemble d’instructions configuré qui exécute une unité de travail en tant que bloc de création d’un [pipeline](#pipeline).
