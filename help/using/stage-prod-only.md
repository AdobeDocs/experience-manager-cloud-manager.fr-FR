---
title: Pipelines dédiés à l’évaluation uniquement et à la production uniquement
description: Découvrez comment séparer les déploiements d’évaluation et de production à l’aide de pipelines dédiés.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: 03f7429fd2c4a6dd4c8ae3228eff9c8cdab1ded8
workflow-type: ht
source-wordcount: '932'
ht-degree: 100%

---

# Pipelines dédiés à l’évaluation uniquement et à la production uniquement {#stage-prod-only}

Découvrez comment séparer les déploiements d’évaluation et de production à l’aide de pipelines dédiés.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour le [programme d’adoption précoce](/help/release-notes/current.md#early-adoption).

## Vue d’ensemble {#overview}

Les environnements d’évaluation et de production sont étroitement liés. Par défaut, les déploiements qui leur sont associés sont liés à un pipeline unique. Il s’agit d’un pipeline de déploiement qui effectue le déploiement pour les environnements d’évaluation et de production de ce programme. Bien que cette liaison soit habituellement adaptée, certains cas d’utilisation présentent des inconvénients :

* Si vous souhaitez effectuer un déploiement vers l’environnement d’évaluation uniquement, vous rejetez l’étape **Promouvoir en production** dans le pipeline. Cependant, l’exécution est marquée comme annulée.
* Si vous souhaitez déployer le code le plus récent d’un environnement d’évaluation vers la production, vous devez redéployer l’ensemble du pipeline, y compris le déploiement de l’évaluation, même s’il n’y a eu aucune modification du code dans ce dernier.
* Les environnements ne peuvent pas être mis à jour pendant les déploiements. Si vous souhaitez mettre en pause pour effectuer des tests sur plusieurs jours dans l’environnement d’évaluation avant de procéder à la promotion en production, l’environnement de production reste bloqué et ne peut pas être mis à jour. Ce scénario rend les tâches non dépendantes, telles que la mise à jour des [variables d’environnement](/help/getting-started/build-environment.md#environment-variables), impossibles à effectuer.

Les pipelines dédiés à l’évaluation uniquement et à la production uniquement offrent des solutions à ces cas d’utilisation en fournissant des options de déploiement dédiées.

* Les **pipelines de déploiement en environnement d’évaluation uniquement** déploient uniquement vers un environnement d’évaluation, l’exécution se terminant une fois le déploiement et les tests terminés. Un pipeline dédié à l’évaluation uniquement se comporte de la même manière que le pipeline de pile pleine de production couplé standard, mais sans les étapes de déploiement de production (approbation, planification, déploiement).
* **Pipelines de déploiement en production uniquement :** pour un déploiement uniquement vers la production en sélectionnant la dernière exécution d’évaluation réussie. Ils déploient ensuite ses artefacts en production. Les pipelines dédiés à la production uniquement réutilisent les artefacts de déploiement en évaluation, en contournant la phase de création.

Les pipelines dédiés uniquement à l’évaluation et à la production ne sont pas exécutés lorsqu’un pipeline de production de pile pleine est en cours, et vice versa. Si le pipeline dédié uniquement à l’évaluation et à la production de pile complète dispose du déclencheur **Lors des modifications Git** configuré et pointent vers la même branche et le même référentiel, seul le pipeline dédié uniquement à l’évaluation est lancé automatiquement. Les pipelines dédiés à la production uniquement ne démarrent pas **`On Git Changes`**, car ils ne sont pas directement liés à un référentiel.

Les pipelines dédiés à la production uniquement sont déclenchés manuellement, car ils ne sont pas directement liés à un référentiel pour **Lors des modifications Git**.

Ces pipelines dédiés offrent plus de flexibilité, mais tenez compte des informations ci-après concernant leur fonctionnement et les recommandations associées.

>[!NOTE]
>
>Les pipelines dédiés à la production uniquement utilisent toujours des artefacts du pipeline d’évaluation uniquement. Ce processus reste vrai même si le pipeline dédié à la production couplé standard a déployé quelque chose d’autre sur l’environnement d’évaluation entre-temps.
>
>* Un tel scénario peut entraîner des restaurations de code indésirables.
>* Adobe vous recommande d’arrêter d’utiliser le pipeline de production couplé standard une fois que vous commencez à utiliser les pipelines dédiés à la production uniquement et à l’évaluation uniquement.
>* Si vous décidez malgré tout d’exécuter les pipelines couplés standard et les pipelines dédiés à l’évaluation/la production uniquement, tenez compte de la réutilisation des artefacts pour éviter les réécritures de code.

## Création de pipeline {#pipeline-creation}

Les pipelines dédiés à la production uniquement et à l’évaluation uniquement sont créés de la même manière que les [pipelines de production](/help/using/production-pipelines.md) et les [pipelines hors production](/help/using/non-production-pipelines.md) couplés standard. Consultez ces documents pour plus de détails.

1. Dans la fenêtre **Pipelines**, cliquez sur **Ajouter un pipeline**.

   * Sélectionnez **Ajouter un pipeline hors production** pour créer un pipeline dédié à l’évaluation uniquement.
   * Sélectionnez **Ajouter un pipeline de production uniquement** pour créer un pipeline dédié uniquement à la production.

   ![Création d’un pipeline dédié à la production/l’évaluation uniquement](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Certaines options peuvent être grisées si les pipelines correspondants existent déjà.
>
>* L’option **Ajouter un pipeline de production uniquement** n’est pas disponible si le pipeline dédié uniquement à l’évaluation n’existe pas encore.
>* L’option **Ajouter un pipeline de production** n’est pas disponible s’il n’existe pas encore de pipeline couplé standard.
>* Un seul pipeline dédié uniquement à la production et un seul pipeline dédié uniquement à l’évaluation sont autorisés par programme.

### Pipelines dédiés uniquement à l’évaluation {#stage-only}

1. Une fois que vous avez sélectionné l’option **Ajouter un pipeline hors production**, la boîte de dialogue **Ajouter un pipeline hors production** s’ouvre.
1. Pour créer un pipeline dédié uniquement à l’évaluation, sélectionnez l’environnement d’évaluation dans le champ **Environnements de déploiement éligibles** pour votre pipeline.
1. Renseignez les champs restants.
1. Cliquez sur **Continuer**.

   ![Création d’un pipeline dédié uniquement à l’évaluation](/help/assets/configure-pipelines/stage-only.png)

1. Dans l’onglet **Tests de l’environnement d’évaluation**, définissez les tests à effectuer dans l’environnement d’évaluation.
1. Cliquez sur **Enregistrer**.

   ![Paramètres de test d’un pipeline dédié uniquement à l’évaluation](/help/assets/configure-pipelines/stage-only-test.png)

### Pipelines dédiés uniquement à la production {#prod-only}

1. Une fois que vous avez sélectionné l’option **Ajouter un pipeline de production uniquement**, la boîte de dialogue **Ajouter un pipeline de production uniquement** s’ouvre.
1. Dans le champ **Nom du pipeline**, saisissez le nom de votre choix. Les options et les fonctionnalités restantes de la boîte de dialogue fonctionnent de la même manière que celles de la boîte de dialogue de création d’un pipeline couplé standard.
1. Dans l’angle inférieur droit de la boîte de dialogue, cliquez sur **Enregistrer**.

   ![Création d’un pipeline dédié uniquement à la production](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Exécuter des pipelines dédiés à la production uniquement et à l’évaluation uniquement {#running}

Les pipelines dédiés à la production uniquement et à l’évaluation uniquement sont exécutés en grande partie de la même manière que [tous les autres pipelines](/help/using/managing-pipelines.md#running-pipelines). Consultez cette documentation pour plus de détails. Toutefois, il existe deux nouvelles fonctionnalités pour ces pipelines.

* Les pipelines dédiés à l’évaluation uniquement et à la production uniquement offrent un nouveau [mode d’urgence](#emergency-mode) pour ignorer les tests.
* Une exécution de pipeline dédié uniquement à la production peut être déclenchée directement à partir des détails d’exécution d’un [pipeline dédié uniquement à l’évaluation](#stage-only-run).

### Mode d’urgence {#emergency-mode}

Lorsque vous démarrez des pipelines dédiés à la production uniquement et à l’évaluation uniquement, vous devez confirmer le démarrage et le mode de démarrage.

* Le **Mode normal** est une exécution standard qui comprend des étapes de test dans l’environnement d’évaluation.
* Le **Mode d’urgence** ignore les étapes de test dans l’environnement d’évaluation.

![Mode d’urgence](/help/assets/configure-pipelines/emergency-mode.png)

### Pipelines dédiés uniquement à l’évaluation {#stage-only-run}

Un pipeline dédié uniquement à l’évaluation s’exécute presque de la même manière que les pipelines couplés standard. Cependant, à la fin de l’exécution, après les étapes de test, un bouton **Promouvoir la version** s’affiche. Ce bouton permet de lancer une exécution de pipeline dédié à la production uniquement à l’aide des artefacts qui ont été déployés dans l’environnement d’évaluation lors de l’exécution et de les déployer en production.

![Exécution d’un pipeline dédié uniquement à l’évaluation](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Cliquer sur **Promouvoir la version** vous invite à confirmer l’exécution du pipeline associé dédié uniquement à l’évaluation, normalement ou en [mode d’urgence](#emergency-mode).

Si aucun pipeline dédié à la production uniquement n’existe, vous devez en créer un.

### Pipelines dédiés uniquement à la production {#prod-only-run}

Pour les pipelines dédiés uniquement à la production, veillez à identifier les artefacts source que vous souhaitez déployer en production. Ces informations se trouvent dans l’étape **Préparation des artefacts**. Vous pouvez accéder à ces exécutions pour plus de détails et pour accéder aux journaux.

![Détails d’un artefact](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
