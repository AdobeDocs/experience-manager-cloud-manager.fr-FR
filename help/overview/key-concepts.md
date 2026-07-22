---
title: Concepts clés
description: Comme tous les outils puissants, Cloud Manager englobe plusieurs concepts et termes. Ce document résume les éléments les plus importants à connaître lorsque vous commencez à utiliser Cloud Manager.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
TQID: https://experienceleague.adobe.com/usnXqDujeZ04U5hOtiI76aemlj-ceToAOtAYS9U0UuM
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 628eceafe63153d64151937df85937135bdc8e7b
workflow-type: tm+mt
source-wordcount: 421
ht-degree: 60%

---

# Concepts clés {#key-concepts}

Cloud Manager englobe de nombreux concepts et termes. Cet article résume certains des concepts les plus importants à connaître lorsque vous commencez à utiliser Cloud Manager.

## Application {#application}

Une application est l’ensemble des personnalisations et des configurations créées par un client ou une cliente dans le but d’adapter la [solution](#solution) sous-jacente (par exemple, AEM Sites ou AEM Assets) à ses cas d’utilisation et ses besoins spécifiques. Une application est une unité logique composée de plusieurs [artefacts](#artifact).

Exemple d’application : [WKND, une application fictive dédiée aux loisirs](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview).

## Artefact {#artifact}

Un artefact est une unité déployable et est le résultat d’un processus de création qui transforme le code source en une seule unité. Par exemple, un fichier Zip contenant le code source.

## Référentiel d’artefacts {#artifact-repository}

Un référentiel d’artefacts est un emplacement de stockage où sont enregistrés et sécurisés les [artefacts](#artifact) spécifiques des clients.

## Environnement {#environment}

Un environnement est un cluster unique de machines virtuelles au sein d’un [programme](#program). Pour AEM, cela comporte une instance de création (éventuellement avec une instance de création Cold Standby supplémentaire), zéro, une ou plusieurs instances de publication, une ou plusieurs instances du Dispatcher et un équilibreur de charge.

## Référentiel Git {#git-repository}

Un référentiel Git est un emplacement de stockage du code source spécifique au client ou à la cliente. Il est accessible [à l’aide de Git](https://git-scm.com).

## Instance {#instance}

Une instance est un serveur virtuel spécifique qui exécute la [solution](#solution) AEM. Les instances représentent une seule unité logique du point de vue du déploiement.

## Organisation {#organization}

Une organisation est un concept d’Adobe représentant un client d’entreprise. Une société peut avoir plusieurs organisations en fonction de la manière dont elles sont configurées dans Adobe Identity Management System (IMS).

## Pipeline {#pipeline}

Un pipeline est un ensemble d’étapes de déploiement exécutées en séquence.

## Produit {#product}

Un produit est un ensemble spécifique de fonctionnalités au sein d’une [solution](#solution) autorisée par une organisation. Au sein d’une organisation[&#128279;](#program) différents programmes ont droit à différents ensembles de produits, tels qu’AEM Sites, AEM Assets ou AEM Forms.

## Programme {#program}

Un programme est un ensemble d’environnements qui prennent en charge un regroupement logique d’initiatives client, correspondant en règle générale à un service level agreement acheté (SLA). Chaque programme comporte exactement un environnement de production et de nombreux environnements hors production.

## Solution {#solution}

Une solution désigne l’une des solutions [!UICONTROL Experience Cloud] d’Adobe. Par exemple, Adobe Experience Manager, Adobe Target ou Adobe Analytics.

## Étape {#step}

Une étape est un ensemble d’instructions configurées qui exécute une unité de travail en tant que composant d’un [pipeline](#pipeline).
