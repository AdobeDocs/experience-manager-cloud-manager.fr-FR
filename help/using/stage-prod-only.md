---
title: Pipelines d’évaluation uniquement et de production uniquement
description: Découvrez comment partager des déploiements d’évaluation et de production à l’aide de pipelines dédiés.
source-git-commit: c09fbf30270523018a36b128d43cbf10e65daf54
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 1%

---


# Pipelines d’évaluation uniquement et de production uniquement {#stage-prod-only}

Découvrez comment partager des déploiements d’évaluation et de production à l’aide de pipelines dédiés.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour le [programme d’adoption précoce.](/help/release-notes/current.md#early-adoption)

## Vue d’ensemble {#overview}

Les environnements d’évaluation et de production sont étroitement liés. Par défaut, les déploiements qui y sont associés sont liés à un pipeline unique. Il s’agit d’un déploiement de pipeline pour les environnements d’évaluation et de production de ce programme. Bien que ce couplage soit normalement adapté, certains cas pratiques présentent des inconvénients :

* Si vous souhaitez effectuer un déploiement sur l’environnement intermédiaire uniquement, vous ne pouvez le faire qu’en rejetant la variable **Promotion de la production** dans le pipeline. L&#39;exécution sera toutefois marquée comme annulée.
* Si vous souhaitez déployer le code le plus récent dans un environnement d’évaluation en production, vous devez redéployer l’ensemble du pipeline, y compris le déploiement d’évaluation, même si aucun code n’y a été modifié.
* Comme les environnements ne peuvent pas être mis à jour pendant les déploiements, si vous souhaitez mettre en pause et tester plusieurs jours dans l’environnement d’évaluation avant de procéder à la promotion en production, l’environnement de production ne peut pas être mis à jour. Cela rend les tâches non dépendantes, telles que la mise à jour [variables d&#39;environnement](/help/getting-started/build-environment.md#environment-variables) impossible.

Les pipelines d’évaluation seule et de production seule proposent des solutions à ces cas d’utilisation en fournissant des options de déploiement dédiées.

* **Pipelines de déploiement en environnement intermédiaire uniquement** déployer uniquement vers un environnement d’évaluation avec l’exécution terminée une fois le déploiement et les tests terminés.
   * Un pipeline d’évaluation uniquement se comporte de la même manière que le pipeline de production de pile complète couplée standard, mais sans les étapes de déploiement de production (approbation, planification, déploiement).
* **Pipelines de déploiement en production uniquement** déployer uniquement vers un environnement de production avec la possibilité de sélectionner une exécution terminée et validée avec succès sur l’étape et de déployer ses artefacts en production.
   * Les pipelines de production seule réutilisent les artefacts des déploiements dans les environnements intermédiaires, en ignorant la phase de création.

Ni les pipelines d’évaluation seule, ni les pipelines prod seule ne seront exécutés pendant l’exécution d’un pipeline de production pleine pile, et vice versa.

Ces pipelines dédiés offrent plus de flexibilité, mais veuillez noter les détails suivants du fonctionnement et des recommandations.

>[!NOTE]
>
>Les pipelines de production uniquement utiliseront toujours les artefacts du pipeline d’évaluation seule, indépendamment de ce qui a pu être déployé sur l’évaluation via le pipeline de production couplé standard entre-temps.
>
>* Cela peut entraîner des restaurations de code indésirables.
>* Adobe recommande d’arrêter l’utilisation du pipeline de production couplé standard une fois que vous commencez à utiliser les pipelines prod uniquement et stage uniquement.
>* Si vous décidez toujours d’exécuter les pipelines couplés standard et les pipelines d’évaluation/production uniquement, gardez à l’esprit la réutilisation des artefacts pour éviter les restaurations de code.

## Création de pipeline {#pipeline-creation}

Les pipelines de production uniquement et d’évaluation uniquement sont créés de la même manière que les pipelines couplés standard. [pipelines de production](/help/using/production-pipelines.md) et [pipelines hors production.](/help/using/non-production-pipelines.md) Veuillez consulter ces documents pour plus de détails.

1. Dans le **Pipelines** fenêtre, appuyez ou cliquez **Ajouter un pipeline**.

   * Sélectionner **Ajout d’un pipeline hors production** pour créer un pipeline intermédiaire uniquement.
   * Sélectionner **Ajout d’un pipeline Production uniquement** pour créer un pipeline prod-only.

   ![Création d’un pipeline prod/stage uniquement](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Certaines options peuvent être grisées si les pipelines correspondants existent déjà.
>
>* **Ajout d’un pipeline Production uniquement** ne sera pas disponible si un pipeline d’évaluation uniquement n’existe pas encore.
>* **Ajout d’un pipeline de production** ne sera pas disponible si un pipeline couplé standard existe déjà.
>* Un seul pipeline en production seule et un pipeline en évaluation seule sont autorisés par programme.

### Pipelines dans l’environnement intermédiaire uniquement {#stage-only}

1. Une fois que vous avez sélectionné le **Ajout d’un pipeline hors production** , l’option **Ajout d’un pipeline hors production** s’ouvre.
1. Pour créer un pipeline d’évaluation uniquement, sélectionnez l’environnement d’évaluation dans le **Environnements de déploiement éligibles** pour votre pipeline. Renseignez les champs restants et appuyez ou cliquez sur **Continuer**.

   ![Création d’un pipeline intermédiaire uniquement](/help/assets/configure-pipelines/stage-only.png)

1. Sur le **Test d’évaluation** vous pouvez ensuite définir les tests qui doivent être effectués sur l’environnement d’évaluation. Appuyez ou cliquez sur **Enregistrer** pour enregistrer votre nouveau pipeline.

   ![Paramètres de test d’un pipeline intermédiaire uniquement](/help/assets/configure-pipelines/stage-only-test.png)

### Pipelines Prod uniquement {#prod-only}

1. Une fois que vous avez sélectionné le **Ajout d’un pipeline Production uniquement** , l’option **Ajout d’un pipeline Production uniquement** s’ouvre.
1. Fournissez une **Nom du pipeline**. Les options et fonctionnalités restantes de la boîte de dialogue fonctionnent de la même manière que celles de la boîte de dialogue de création de pipeline couplé standard. Appuyez ou cliquez sur **Enregistrer** pour enregistrer le pipeline.

   ![Création d’un pipeline de production uniquement](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Exécution de pipelines de production uniquement et de test uniquement {#running}

Les pipelines de production seule et de production seule sont exécutés de la même manière que [tous les autres pipelines sont exécutés.](/help/using/managing-pipelines.md#running-pipelines) Consultez cette documentation pour plus de détails.

En outre, une exécution de pipeline prod uniquement peut être déclenchée directement à partir des détails d’exécution d’un pipeline intermédiaire uniquement.

### Pipelines dans l’environnement intermédiaire uniquement {#stage-only-run}

Un pipeline en phase seule s’exécute presque de la même manière que les pipelines couplés standard. Toutefois, à la fin de l’exécution, après les étapes de test, une **Convertir le build** vous permet de démarrer une exécution de pipeline en production seule qui utilise les artefacts déployés sur l’étape par cette exécution et les déploie sur l’environnement de production.

![Exécution du pipeline en mode d’évaluation uniquement](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

La variable **Convertir le build** n’apparaît que si vous utilisez la dernière exécution de pipeline en évaluation seule réussie. Lorsque vous appuyez ou cliquez dessus, vous devez confirmer l’exécution du pipeline prod uniquement ou créer un pipeline prod uniquement s’il n’existe pas déjà.

### Pipelines Prod uniquement {#prod-only-run}

Pour les pipelines prod uniquement, il est important d’identifier les artefacts source à déployer en production. Ces détails sont disponibles dans la section **Préparation des artefacts** étape . Vous pouvez accéder à ces exécutions pour plus de détails et de journaux.

![Détails de l’objet](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
