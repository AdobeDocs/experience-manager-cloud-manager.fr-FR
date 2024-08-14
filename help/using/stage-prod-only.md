---
title: Pipelines dédiés à l’évaluation uniquement et à la production uniquement
description: Découvrez comment séparer les déploiements d’évaluation et de production à l’aide de pipelines dédiés.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 72%

---

# Pipelines d’évaluation uniquement et de production uniquement {#stage-prod-only}

Découvrez comment séparer les déploiements d’évaluation et de production à l’aide de pipelines dédiés.

>[!NOTE]
>
>Cette fonctionnalité est disponible uniquement pour [le programme d&#39;adoption précoce](/help/release-notes/current.md#early-adoption).

## Vue d’ensemble {#overview}

Les environnements d’évaluation et de production sont étroitement liés. Par défaut, les déploiements qui leur sont associés sont liés à un pipeline unique. Il s’agit d’un pipeline de déploiement qui effectue le déploiement pour les environnements d’évaluation et de production de ce programme. Bien que cette liaison soit habituellement adaptée, certains cas pratiques présentent des inconvénients :

* Si vous souhaitez effectuer un déploiement sur l’environnement intermédiaire uniquement, vous ne pouvez le faire qu’en rejetant l’étape **Convertir en production** dans le pipeline. Cependant, l’exécution sera marquée comme annulée.
* Si vous souhaitez déployer le code le plus récent dans un environnement d’évaluation en production, vous devez redéployer l’ensemble du pipeline, y compris le déploiement d’évaluation, même si aucun code n’y a été modifié.
* Étant donné que les environnements ne peuvent pas être mis à jour pendant les déploiements, si vous souhaitez mettre en pause et effectuer des tests sur plusieurs jours dans l’environnement d’évaluation avant de procéder à la promotion en production, l’environnement de production ne peut pas être mis à jour. Cela rend les tâches non dépendantes, telles que la mise à jour des [variables d’environnement](/help/getting-started/build-environment.md#environment-variables), impossibles à effectuer.

Les pipelines dédiés à l’évaluation uniquement et à la production uniquement offrent des solutions à ces cas d’utilisation en fournissant des options de déploiement dédiées.

* Les **pipelines de déploiement en environnement d’évaluation uniquement** déploient uniquement vers un environnement d’évaluation, l’exécution se terminant une fois le déploiement et les tests terminés.
   * Un pipeline dédié à l’évaluation uniquement se comporte de la même manière que le pipeline de pile complète de production couplé standard, mais sans les étapes de déploiement de production (approbation, planification, déploiement).
* Les **pipelines de déploiement en production uniquement** déploient uniquement vers un environnement de production avec la possibilité de sélectionner une exécution terminée et validée avec succès pour l’évaluation et de déployer les artefacts de celle-ci en production.
   * Les pipelines dédiés à la production uniquement réutilisent les artefacts des déploiements en évaluation, ignorant ainsi la phase de création.

Ni les pipelines dédiés uniquement à l’évaluation, ni ceux dédiés uniquement à la production ne sont exécutés pendant l’exécution d’un pipeline de production de pile complète, et vice versa. Si le pipeline dédié uniquement à l’évaluation et à la production de pile complète dispose du déclencheur **Lors des modifications Git** configuré et pointent vers la même branche et le même référentiel, seul le pipeline dédié uniquement à l’évaluation est lancé automatiquement. Les pipelines dédiés uniquement à la production ne sont pas lancé **Lors des modifications Git**, car ils ne sont pas directement liés à un référentiel.

Ces pipelines dédiés offrent plus de flexibilité, mais vous devez noter les détails suivants du fonctionnement et des recommandations.

>[!NOTE]
>
>Les pipelines dédiés à la production uniquement utiliseront toujours les artefacts du pipeline dédié à l’évaluation uniquement, indépendamment de ce qui a pu être déployé en évaluation via le pipeline de production couplé standard entre-temps.
>
>* Cela peut entraîner des réécritures de code indésirables.
>* Adobe vous recommande d’arrêter d’utiliser le pipeline de production couplé standard une fois que vous commencez à utiliser les pipelines dédiés à la production uniquement et à l’évaluation uniquement.
>* Si vous décidez malgré tout d’exécuter les pipelines couplés standard et les pipelines dédiés à l’évaluation/la production uniquement, tenez compte de la réutilisation des artefacts pour éviter les réécritures de code.

## Création de pipeline {#pipeline-creation}

Les pipelines de production seule et de production seule sont créés de la même manière que les [pipelines de production](/help/using/production-pipelines.md) et les [pipelines hors production](/help/using/non-production-pipelines.md) couplés standard. Consultez ces documents pour plus de détails.

1. Dans la fenêtre **Pipelines** , cliquez sur **Ajouter un pipeline**.

   * Sélectionnez **Ajouter un pipeline hors production** pour créer un pipeline dédié à l’évaluation uniquement.
   * Sélectionnez **Ajouter un pipeline de production uniquement** pour créer un pipeline dédié uniquement à la production.

   ![Création d’un pipeline dédié à la production/l’évaluation uniquement](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Certaines options peuvent être grisées si les pipelines correspondants existent déjà.
>
>* **Ajouter un pipeline de production uniquement** n’est pas disponible si un pipeline d’évaluation uniquement n’existe pas encore.
>* **Ajouter un pipeline de production** n’est pas disponible si un pipeline de couplage standard existe déjà.
>* Un seul pipeline dédié uniquement à la production et un seul pipeline dédié uniquement à l’évaluation sont autorisés par programme.

### Pipelines d’évaluation uniquement {#stage-only}

1. Une fois que vous avez sélectionné l’option **Ajouter un pipeline hors production**, la boîte de dialogue **Ajouter un pipeline hors production** s’ouvre.
1. Pour créer un pipeline dédié uniquement à l’évaluation, sélectionnez l’environnement d’évaluation dans le champ **Environnements de déploiement éligibles** pour votre pipeline. Renseignez les champs restants et cliquez sur **Continuer**.

   ![Création d’un pipeline dédié uniquement à l’évaluation](/help/assets/configure-pipelines/stage-only.png)

1. Dans l’onglet **Tests de l’environnement d’évaluation** vous pouvez définir les tests qui doivent être effectués dans l’environnement d’évaluation. Cliquez sur **Enregistrer** pour enregistrer votre nouveau pipeline.

   ![Paramètres de test d’un pipeline dédié uniquement à l’évaluation](/help/assets/configure-pipelines/stage-only-test.png)

### Pipelines de production uniquement {#prod-only}

1. Une fois que vous avez sélectionné l’option **Ajouter un pipeline de production uniquement**, la boîte de dialogue **Ajouter un pipeline de production uniquement** s’ouvre.
1. Saisissez un **Nom de pipeline**. Les options et les fonctionnalités restantes de la boîte de dialogue fonctionnent de la même manière que celles de la boîte de dialogue de création d’un pipeline couplé standard. Cliquez sur **Enregistrer** pour enregistrer le pipeline.

   ![Création d’un pipeline dédié uniquement à la production](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Exécution de pipelines en production seule et en production seule {#running}

Les pipelines de production seule et de production seule sont exécutés de la même manière que [ tous les autres pipelines sont exécutés](/help/using/managing-pipelines.md#running-pipelines). Consultez cette documentation pour plus de détails.

En outre, une exécution de pipeline dédié uniquement à la production peut être déclenchée directement à partir des détails d’exécution d’un pipeline dédié uniquement à l’évaluation.

### Pipelines d’évaluation uniquement {#stage-only-run}

Un pipeline dédié uniquement à l’évaluation s’exécute presque de la même manière que les pipelines couplés standard. Toutefois, à la fin de l’exécution, après les étapes de test, un bouton **Promouvoir la version** vous permet de démarrer une exécution de pipeline dédié uniquement à la production qui utilise les artefacts déployés en évaluation par l’exécution et les déploie dans l’environnement de production.

![Exécution d’un pipeline dédié uniquement à l’évaluation](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Le bouton **Promouvoir la version** n’apparaît que si vous vous trouvez dans la dernière exécution réussie d’un pipeline dédié uniquement à l’évaluation. Une fois que vous avez cliqué, il vous demande de confirmer l’exécution du pipeline prod uniquement ou de créer un pipeline prod uniquement s’il n’existe pas déjà.

### Pipelines de production uniquement {#prod-only-run}

Pour les pipelines dédiés uniquement à la production, il est important d’identifier les artefacts source qui doivent être déployés en production. Ces informations se trouvent dans l’étape **Préparation des artefacts**. Vous pouvez accéder à ces exécutions pour plus de détails et pour accéder aux journaux.

![Détails d’un artefact](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
