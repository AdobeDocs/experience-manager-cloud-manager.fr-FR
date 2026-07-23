---
title: Partager des pipelines d’évaluation uniquement et de production uniquement
description: Découvrez comment séparer les déploiements d’évaluation et de production à l’aide de pipelines dédiés.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
TQID: https://experienceleague.adobe.com/whq-Hkwp3mjTr0iftoKZHKdsi0xaKtVXazXjUENoaLk
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 6b0075d2405e89dce1c883a2b5fc0bd952a3fddd
workflow-type: tm+mt
source-wordcount: 975
ht-degree: 53%

---

# Fractionner les pipelines d’évaluation uniquement et de production uniquement {#stage-prod-only}

Vous pouvez diviser les déploiements d’évaluation et de production à l’aide de pipelines dédiés.

## Vue d’ensemble {#overview}

Les environnements d’évaluation et de production sont étroitement liés. Par défaut, les déploiements qui leur sont associés sont liés à un pipeline unique. Un pipeline de déploiement se déploie à la fois dans les environnements d’évaluation et de production de ce programme. Bien que ce couplage soit normalement approprié, il existe certains cas d&#39;utilisation où des inconvénients se produisent :

* Si vous souhaitez effectuer un déploiement dans l’évaluation, vous pouvez ignorer l’étape **Convertir en production** dans le pipeline. Cependant, l’exécution est marquée comme annulée.
* Si vous souhaitez déployer le code le plus récent d’un environnement d’évaluation vers la production, vous devez redéployer l’ensemble du pipeline, y compris le déploiement d’évaluation, même si aucun code n’y a été modifié.
* Les environnements ne peuvent pas être mis à jour pendant les déploiements. Si vous retardez les tests dans l’environnement d’évaluation de plusieurs jours avant de passer en production, l’environnement de production reste verrouillé et ne peut pas être mis à jour. Ce scénario rend les tâches non dépendantes, telles que la mise à jour des [variables d’environnement](/help/getting-started/build-environment.md#environment-variables), impossibles à effectuer.

Les pipelines d’évaluation uniquement et de production uniquement offrent des solutions à ces cas d’utilisation en fournissant des options de déploiement dédiées.

* **Pipelines de déploiement d’évaluation uniquement :** effectuez un déploiement uniquement dans un environnement d’évaluation avec l’exécution se terminant une fois le déploiement et les tests terminés. Un pipeline dédié à l’évaluation uniquement se comporte de la même manière que le pipeline de pile pleine de production couplé standard, mais sans les étapes de déploiement de production (approbation, planification, déploiement).
* **Pipelines de déploiement en production uniquement :** déployez uniquement en production en sélectionnant la dernière exécution d’étape réussie. Déployez ensuite les artefacts en production. Les pipelines de production uniquement réutilisent les artefacts de déploiement d’étape, en ignorant la phase de création.

Les pipelines dédiés uniquement à l’évaluation et à la production ne sont pas exécutés lorsqu’un pipeline de production de pile pleine est en cours, et vice versa. Si le pipeline dédié uniquement à l’évaluation et à la production de pile complète dispose du déclencheur **Lors des modifications Git** configuré et pointent vers la même branche et le même référentiel, seul le pipeline dédié uniquement à l’évaluation est lancé automatiquement. Les pipelines de production uniquement ne déclenchent pas de **`On Git Changes`**, car ils ne sont pas directement liés à un référentiel.

Les pipelines dédiés à la production uniquement sont déclenchés manuellement, car ils ne sont pas directement liés à un référentiel pour **Lors des modifications Git**.

Ces pipelines dédiés offrent plus de flexibilité, mais notez les détails de fonctionnement et les recommandations suivants :

>[!NOTE]
>
>Les pipelines dédiés à la production uniquement utilisent toujours des artefacts du pipeline d’évaluation uniquement. Ce processus reste valide même si le pipeline de production couplée standard a déployé autre chose pour l’évaluation entre-temps.
>
>* Un tel scénario entraîne des restaurations de code indésirables.
>* Adobe recommande d’arrêter l’utilisation du pipeline de production couplé standard une fois que vous avez commencé à utiliser les pipelines de production uniquement prod et intermédiaire uniquement.
>* Si vous décidez malgré tout d’exécuter les pipelines couplés standard et les pipelines dédiés à l’évaluation/la production uniquement, tenez compte de la réutilisation des artefacts pour éviter les restaurations de code.

## Création de pipeline {#pipeline-creation}

Les pipelines de production uniquement et d’évaluation uniquement sont créés de la même manière que les pipelines couplés standard [pipelines de production](/help/using/production-pipelines.md) et [pipelines hors production](/help/using/non-production-pipelines.md). Consultez ces documents pour plus de détails.

1. Dans la fenêtre **Pipelines**, cliquez sur **Ajouter un pipeline**.

   * Sélectionnez **Ajouter un pipeline hors production** pour créer un pipeline dédié à l’évaluation uniquement.
   * Sélectionnez **Ajouter un pipeline de production uniquement** pour créer un pipeline de production uniquement.

   ![Création d’un pipeline dédié à la production/l’évaluation uniquement](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Certaines options sont grisées si les pipelines correspondants existent déjà.
>
>* **Ajouter un pipeline de production uniquement** n’est pas disponible si un pipeline d’évaluation uniquement n’existe pas encore.
>* L’option **Ajouter un pipeline de production** n’est pas disponible s’il n’existe pas encore de pipeline couplé standard.
>* Un seul pipeline en production seule et un seul pipeline intermédiaire sont autorisés par programme.

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

1. Après avoir cliqué sur **Ajouter un pipeline de production uniquement**, la boîte de dialogue associée s’ouvre.
1. Dans le champ **Nom du pipeline**, saisissez le nom de votre choix. Les options et les fonctionnalités restantes de la boîte de dialogue fonctionnent de la même manière que celles de la boîte de dialogue de création d’un pipeline couplé standard.
1. Dans l’angle inférieur droit de la boîte de dialogue, cliquez sur **Enregistrer**.

   ![Création d’un pipeline dédié uniquement à la production](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Exécuter des pipelines dédiés à la production uniquement et à l’évaluation uniquement {#running}

Les pipelines dédiés à la production uniquement et à l’évaluation uniquement sont exécutés en grande partie de la même manière que [tous les autres pipelines](/help/using/managing-pipelines.md#running-pipelines). Consultez cette documentation pour plus de détails. Toutefois, il existe deux nouvelles fonctionnalités pour ces pipelines.

* Les pipelines dédiés à l’évaluation uniquement et à la production uniquement offrent un nouveau [mode d’urgence](#emergency-mode) pour ignorer les tests.
* Une exécution de pipeline en production seule peut être déclenchée directement à partir des détails d’exécution d’un [pipeline d’évaluation seule](#stage-only-run).

### Mode d’urgence {#emergency-mode}

Lors du démarrage de pipelines de production uniquement et d’évaluation uniquement, vous êtes invité à confirmer le démarrage et la manière dont il se déroule.

* Le **Mode normal** est une exécution standard qui comprend des étapes de test dans l’environnement d’évaluation.
* Le **Mode d’urgence** ignore les étapes de test dans l’environnement d’évaluation.

![Mode d’urgence](/help/assets/configure-pipelines/emergency-mode.png)

### Pipelines dédiés uniquement à l’évaluation {#stage-only-run}

Un pipeline dédié uniquement à l’évaluation s’exécute presque de la même manière que les pipelines couplés standard. Cependant, à la fin de l’exécution, après les étapes de test, un bouton **Promouvoir la version** s’affiche. Ce bouton permet de lancer l&#39;exécution d&#39;un pipeline en production seule. Il utilise les artefacts déployés pour l’évaluation lors de l’exécution. Il les déploie ensuite en production.

![Exécution d’un pipeline dédié uniquement à l’évaluation](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Cliquez sur **Promouvoir la création** pour confirmer l&#39;exécution du pipeline en production seule associé, normalement ou en [mode d&#39;urgence](#emergency-mode).

Si aucun pipeline dédié à la production uniquement n’existe, vous devez en créer un.

### Pipelines dédiés uniquement à la production {#prod-only-run}

Pour les pipelines dédiés uniquement à la production, veillez à identifier les artefacts source que vous souhaitez déployer en production. Ces informations se trouvent dans l’étape **Préparation des artefacts**. Vous pouvez accéder à ces exécutions pour plus de détails et pour accéder aux journaux.

![Détails d’un artefact](/help/assets/configure-pipelines/prod-only-pipeline-run.png)

