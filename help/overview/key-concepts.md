---
title: Concepts clés
description: Comme tous les outils puissants, Cloud Manager englobe plusieurs concepts et termes. Ce document résume les éléments les plus importants à connaître lorsque vous commencez à utiliser Cloud Manager.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: ht
source-wordcount: '414'
ht-degree: 100%

---


# Concepts clés {#key-concepts}

Comme tous les outils puissants, Cloud Manager englobe plusieurs concepts et termes. Ce document résume les éléments les plus importants à connaître lorsque vous commencez à utiliser Cloud Manager.

## Application {#application}

Une application est l’ensemble des personnalisations et des configurations créées par un client ou une cliente dans le but d’adapter la [solution](#solution) sous-jacente (par exemple, AEM Sites ou AEM Assets) à ses cas d’utilisation et ses besoins spécifiques. Une application est une unité logique pouvant être composée de plusieurs [artefacts](#artifact).

Exemple d’application : [WKND, une application fictive dédiée aux loisirs](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview).

## Artefact {#artifact}

Un artefact est une unité déployable et résulte d’un processus de création qui transforme le code source en une seule unité. Par exemple, un fichier Zip contenant le code source.

## Référentiel d’artefacts {#artifact-repository}

Un référentiel d’artefacts est un emplacement de stockage où sont enregistrés et sécurisés les [artefacts](#artifact) spécifiques des clients.

## Environnement {#environment}

Un environnement est un cluster unique de machines virtuelles au sein d’un [programme](#program). Pour AEM, cela comporte une instance de création (éventuellement avec une instance de création Cold Standby supplémentaire), zéro, une ou plusieurs instances de publication, une ou plusieurs instances du Dispatcher et un équilibreur de charge.

## Référentiel Git {#git-repository}

Un référentiel Git est un emplacement de stockage du code source spécifique au client ou à la cliente. Il est accessible [à l’aide de Git](https://git-scm.com).

## Instance {#instance}

Une instance est un serveur virtuel spécifique qui exécute la [solution](#solution) AEM. Les instances représentent une seule unité logique du point de vue du déploiement.

## Organisation {#organization}

Une organisation est un concept d’Adobe représentant un client d’entreprise. Une société peut être constituée de plusieurs organisations en fonction de la configuration initiale du système Identity Management (IMS) d’Adobe.

## Pipeline {#pipeline}

Un pipeline est un ensemble d’étapes de déploiement « exécutées » en séquence.

## Produit {#product}

Un produit est un ensemble spécifique de fonctionnalités au sein d’une [solution](#solution) autorisée par une organisation. Au sein d’une organisation, différents [programmes](#program) peuvent bénéficier de différents ensembles de produits, tels qu’AEM Sites, AEM Assets ou AEM Forms.

## Programme {#program}

Un programme est un ensemble d’environnements qui prennent en charge un regroupement logique d’initiatives client, correspondant en règle générale à un contrat de niveau de service (SLA) acheté. Chaque programme comprend un environnement de production précis et peut intégrer un grand nombre d’environnements hors production.

## Solution {#solution}

Une solution désigne l’une des solutions [!UICONTROL Experience Cloud] d’Adobe. Par exemple, Adobe Experience Manager, Adobe Target ou Adobe Analytics.

## Étape {#step}

Une étape est un ensemble d’instructions définies qui exécute une unité de travail à la manière d’un bloc de création d’un [pipeline](#pipeline).
