---
title: Pipelines dédiés à l’évaluation uniquement et à la production uniquement
description: Découvrez comment séparer les déploiements d’évaluation et de production à l’aide de pipelines dédiés.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: 70b7994435f7f0f587c134fab1fb66c6576386d9
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 37%

---

# Pipelines d’évaluation uniquement et de production uniquement {#stage-prod-only}

Découvrez comment séparer les déploiements d’évaluation et de production à l’aide de pipelines dédiés.

>[!NOTE]
>
>Cette fonctionnalité est disponible uniquement pour [le programme d&#39;adoption précoce](/help/release-notes/current.md#early-adoption).

## Vue d’ensemble {#overview}

Les environnements d’évaluation et de production sont étroitement liés. Par défaut, les déploiements qui leur sont associés sont liés à un pipeline unique. En d’autres termes, un pipeline de déploiement est déployé dans les environnements d’évaluation et de production de ce programme. Bien que cette liaison soit habituellement adaptée, certains cas pratiques présentent des inconvénients :

* Si vous souhaitez effectuer un déploiement dans une version intermédiaire uniquement, vous rejetez l’étape **Convertir en production** du pipeline. Toutefois, l’exécution est marquée comme annulée.
* Si vous souhaitez déployer le code le plus récent dans un environnement d’évaluation en production, vous devez redéployer l’ensemble du pipeline, y compris le déploiement d’évaluation, même si aucun code n’y a été modifié.
* Les environnements ne peuvent pas être mis à jour pendant les déploiements. Si vous effectuez un test dans l’environnement d’évaluation pendant plusieurs jours avant de procéder à la promotion vers la production, l’environnement de production reste verrouillé et ne peut pas être mis à jour. Ce scénario rend impossible toute tâche non dépendante telle que la mise à jour des [variables d&#39;environnement](/help/getting-started/build-environment.md#environment-variables).

Les pipelines dédiés à l’évaluation uniquement et à la production uniquement offrent des solutions à ces cas d’utilisation en fournissant des options de déploiement dédiées.

* **Pipelines de déploiement en environnement intermédiaire uniquement :** déploie uniquement vers un environnement d’évaluation dont l’exécution se termine une fois le déploiement et les tests terminés. Un pipeline dédié à l’évaluation uniquement se comporte de la même manière que le pipeline de pile complète de production couplé standard, mais sans les étapes de déploiement de production (approbation, planification, déploiement).
* **Pipelines de déploiement prod uniquement :** déploie uniquement vers la production en sélectionnant une exécution intermédiaire réussie. Déploiement ensuite de ses artefacts en production. Les pipelines de production seule réutilisent les artefacts de déploiement d’étape, en contournant la phase de création.

Les pipelines d’évaluation seule et de production seule ne sont pas exécutés lorsqu’un pipeline de production de pile complète est en cours, et vice versa. Si le pipeline dédié uniquement à l’évaluation et à la production de pile complète dispose du déclencheur **Lors des modifications Git** configuré et pointent vers la même branche et le même référentiel, seul le pipeline dédié uniquement à l’évaluation est lancé automatiquement. Les pipelines de production seule ne démarrent pas **`On Git Changes`**, car ils ne sont pas directement liés à un référentiel.

Les pipelines de production seule sont déclenchés manuellement, car ils ne sont pas directement liés à un référentiel pour **Lors des modifications Git**.

Ces pipelines dédiés offrent plus de flexibilité, mais vous devez noter les détails suivants du fonctionnement et des recommandations.

>[!NOTE]
>
>Les pipelines de production uniquement utilisent toujours des artefacts du pipeline d’évaluation uniquement. Ce processus reste vrai même si le pipeline de production couplé standard a déployé quelque chose d’autre à mettre en scène entre-temps.
>
>* Un tel scénario peut entraîner des restaurations de code indésirables.
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

1. Dans l’onglet **Test dans l’environnement intermédiaire**, vous pouvez ensuite définir les tests qui doivent être effectués dans l’environnement d’évaluation. Cliquez sur **Enregistrer** pour enregistrer votre nouveau pipeline.

   ![Paramètres de test d’un pipeline dédié uniquement à l’évaluation](/help/assets/configure-pipelines/stage-only-test.png)

### Pipelines de production uniquement {#prod-only}

1. Une fois que vous avez sélectionné l’option **Ajouter un pipeline de production uniquement**, la boîte de dialogue **Ajouter un pipeline de production uniquement** s’ouvre.
1. Saisissez un **Nom de pipeline**. Les options et fonctionnalités restantes de la boîte de dialogue fonctionnent de la même manière que celles de la boîte de dialogue de création de pipeline couplé standard. Cliquez sur **Enregistrer** pour enregistrer le pipeline.

   ![Création d’un pipeline dédié uniquement à la production](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Exécution de pipelines en production seule et en production seule {#running}

Les pipelines de production seule et de production seule sont exécutés de la même manière que [ tous les autres pipelines sont exécutés](/help/using/managing-pipelines.md#running-pipelines). Consultez cette documentation pour plus de détails.

En outre, une exécution de pipeline dédié uniquement à la production peut être déclenchée directement à partir des détails d’exécution d’un pipeline dédié uniquement à l’évaluation.

### Pipelines d’évaluation uniquement {#stage-only-run}

Un pipeline dédié uniquement à l’évaluation s’exécute presque de la même manière que les pipelines couplés standard. Cependant, à la fin de l’exécution, après les étapes de test, un bouton **Convertir le build** s’affiche. Ce bouton permet de lancer une exécution de pipeline en production uniquement à l’aide des artefacts qui ont été déployés sur l’étape de l’exécution et de les déployer en production.

![Exécution d’un pipeline dédié uniquement à l’évaluation](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Le bouton **Promouvoir la version** n’apparaît que si vous vous trouvez dans la dernière exécution réussie d’un pipeline dédié uniquement à l’évaluation. Une fois que vous avez cliqué, il vous demande de confirmer l’exécution du pipeline prod uniquement ou de créer un pipeline prod uniquement s’il n’existe pas déjà.

### Pipelines de production uniquement {#prod-only-run}

Pour les pipelines prod uniquement, il est important d’identifier les artefacts source à déployer en production. Ces informations se trouvent dans l’étape **Préparation des artefacts**. Vous pouvez accéder à ces exécutions pour plus de détails et pour accéder aux journaux.

![Détails d’un artefact](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
