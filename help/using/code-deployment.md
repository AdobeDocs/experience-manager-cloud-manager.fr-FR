---
title: Déploiement du code
description: Découvrez comment déployer votre code et ce qui se passe dans Cloud Manager lors du déploiement.
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: b85bd1bdf38360885bf2777d75bf7aa97c6da7ee
workflow-type: tm+mt
source-wordcount: '1655'
ht-degree: 84%

---


# Déploiement du code {#code-deployment}

Découvrez comment déployer votre code et ce qui se passe dans Cloud Manager lors du déploiement.

## Déploiement du code avec Cloud Manager {#deploying-code-with-cloud-manager}

Une fois que vous avez configuré votre pipeline de production, y compris le référentiel et les environnements nécessaires, vous êtes prêt à déployer votre code.

1. Cliquez sur **Déployer** dans Cloud Manager pour lancer le processus de déploiement.

   ![Bouton Déployer](/help/assets/Deploy1.png)

1. L’écran **Exécution du pipeline** s’affiche. Cliquez sur **Créer** pour lancer le processus.

   ![Bouton Créer](/help/assets/Deploy2.png)

Le processus de création lance le processus de déploiement du code, notamment les étapes suivantes :

* Déploiement dans l’environnement d’évaluation
* Test dans l’environnement d’évaluation
* Déploiement en production

En outre, vous pouvez examiner les étapes de divers processus de déploiement en affichant les journaux, ou en examinant les résultats, pour les critères de test.

## Étapes de déploiement {#deployment-steps}

Plusieurs actions se produisent au cours de chaque étape du déploiement, qui sont décrites dans cette section. Consultez la section [Détails du processus de déploiement](#deployment-process) pour obtenir des détails techniques sur la manière dont le code lui-même est déployé en arrière-plan.

### Étape de déploiement dans l’environnement d’évaluation {#stage-deployment}

Le **déploiement dans l’environnement d’évaluation** comprend les actions suivantes :

* **Validation** : cette étape garantit que le pipeline est configuré pour utiliser les ressources actuellement disponibles, par exemple l’existence de la branche configurée et la disponibilité des environnements.
* **Test de création et d’unité** : cette étape exécute un processus de création en conteneur. Consultez le document [Environnement de création](/help/getting-started/build-environment.md) pour plus de détails.
* **Analyse du code** : cette étape évalue la qualité du code de votre application. Consultez le document [Comprendre les résultats de test](/help/using/code-quality-testing.md) pour obtenir plus de détails sur le processus de test.
* **Déployer dans l’environnement d’évaluation**

![Déploiement dans l’environnement d’évaluation](/help/assets/Stage_Deployment1.png)

### Étape du test dans l’environnement d’évaluation {#stage-testing}

L’étape du **test dans l’environnement d’évaluation** comprend les actions suivantes :

* **Tests de sécurité** : cette étape évalue l’impact de votre code sur la sécurité de l’environnement AEM. Consultez le document [Comprendre les résultats de test](/help/using/code-quality-testing.md) pour obtenir plus de détails sur le processus de test.
   * **Tests de performance** : cette étape évalue les performances de votre code. Consultez le document [Comprendre les résultats de test](/help/using/code-quality-testing.md) pour obtenir plus de détails sur le processus de test.

  ![Test dans l’environnement d’évaluation](/help/assets/Stage_Testing1.png)

### Étape de déploiement en production {#production-deployment}

Le **déploiement en production** inclut les actions suivantes :

* **Application à approuver**
   * Cette option est activée lors de la configuration du pipeline.
   * Grâce à cette option, vous pouvez planifier le déploiement en production ou cliquer sur **Maintenant** pour exécuter immédiatement le déploiement en production.
* **Planifier le déploiement en production**
   * Cette option est activée lors de la configuration du pipeline.
   * La date et l’heure planifiées sont indiquées dans le fuseau horaire de l’utilisateur.
     ![Planifier le déploiement](/help/assets/Production_Deployment1.png)
* **Assistance de l’ingénieur du service client** (si activée).
* **Déploiement en environnement de production**

![Déploiement en production](/help/assets/Prod_Deployment1.png)

Une fois le déploiement terminé, votre code se trouve dans son environnement ciblé et vous pouvez afficher les journaux.

![Déploiement terminé](/help/assets/Production_Deployment2.png)

## Délais d’expiration {#timeouts}

Les étapes suivantes expirent s’ils sont en attente de commentaires de l’utilisateur :

| Étape | Délai dépassé |
|--- |--- |
| Test de qualité du code | 14 jours |
| Test de sécurité | 14 jours |
| Test de performance | 14 jours |
| Application à approuver | 14 jours |
| Planning du déploiement en production | 14 jours |
| Assistance de l’ingénieur du service client | 14 jours |

## Détails du processus de déploiement {#deployment-process}

Cloud Manager télécharge tous les fichiers target/*.zip générés par le processus de création vers un emplacement de stockage. Ces artefacts sont récupérés à partir de cet emplacement pendant les phases de déploiement du pipeline.

Lorsque Cloud Manager se déploie sur des topologies autres que de production, l’objectif est de réaliser le déploiement aussi rapidement que possible ; les artefacts sont donc déployés simultanément sur tous les nœuds, comme suit :

1. Cloud Manager détermine si chaque artefact est un package AEM ou dispatcher.
1. Cloud Manager supprime tous les Dispatchers de la répartition de charge pour isoler l’environnement pendant le déploiement.

   * Sauf configuration contraire, vous pouvez ignorer les modifications de la répartition de charge dans les déploiements de développement et d’évaluation, c’est-à-dire pour l’environnement de développement, les étapes d’attachement et de détachement dans les deux pipelines hors production, ainsi que pour l’environnement d’évaluation dans le pipeline de production.

   ![Ignorer la répartition de charge](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >Cette fonctionnalité devrait principalement être utilisée par les clients 1-1-1.

1. Chaque artefact AEM est déployé sur chacune des instances AEM par le biais des API de Package Manager, avec des dépendances de packages qui déterminent l’ordre de déploiement.

   * Pour en savoir plus sur l’utilisation de packages pour installer de nouvelles fonctionnalités, transférer du contenu entre des instances et sauvegarder le contenu du référentiel, reportez-vous au document [Gestionnaire de packages](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager.html?lang=fr).

   >[!NOTE]
   >
   >Tous les artefacts AEM sont déployés à la fois sur l’instance de création et les instances de publication. Les modes d’exécution doivent être utilisés lorsque des configurations spécifiques à un nœud sont requises. Pour en savoir plus sur la manière dont les modes d’exécution vous permettent d’ajuster votre instance AEM à des fins spécifiques, reportez-vous à la section [Modes d’exécution du document Déploiement sur AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=fr#runmodes)

1. L’artefact dispatcher est déployé sur chaque dispatcher comme suit :

   1. Les configurations actuelles sont sauvegardées et copiées vers un emplacement temporaire.
   1. Toutes les configurations sont supprimées, à l’exception des fichiers non-modifiables. Reportez-vous au document [Configurations du Dispatcher](/help/getting-started/dispatcher-configurations.md) pour plus de détails. Cela permet de vider les répertoires pour qu’aucun fichier orphelin ne soit abandonné.
   1. L’artefact est extrait dans le répertoire `httpd`. Les fichiers non modifiables ne sont pas remplacés. Toute modification apportée aux fichiers non modifiables dans votre référentiel git sera ignorée au moment du déploiement. Ces fichiers sont essentiels au framework Dispatcher AMS et ne peuvent pas être modifiés.
   1. Apache effectue un test de configuration. Si aucune erreur n’est trouvée, le service est rechargé. Si une erreur se produit, les configurations sont restaurées à partir de la sauvegarde, le service est rechargé et l’erreur est signalée à Cloud Manager.
   1. Chaque chemin spécifié dans la configuration de pipeline est invalidé ou purgé du cache du dispatcher.

   >[!NOTE]
   >
   >Cloud Manager exige que l’artefact du dispatcher contienne le jeu de fichiers complet. Tous les fichiers de configuration du dispatcher doivent être présents dans le référentiel git. Les fichiers ou dossiers manquants entraînent l’échec du déploiement.

1. Après le déploiement réussi de tous les packages AEM et de dispatcher sur tous les nœuds, les dispatchers sont ajoutés à l’équilibreur de charge et le déploiement est terminé.

   >[!NOTE]
   >
   >vous pouvez ignorer les modifications de la répartition de charge dans les déploiements de développement et d’évaluation, c’est-à-dire pour l’environnement de développement, les étapes d’attachement et de détachement dans les deux pipelines hors production, ainsi que pour l’environnement d’évaluation dans le pipeline de production.

### Phase de déploiement en production {#deployment-production-phase}

Le processus de déploiement des topologies de production diffère légèrement afin de minimiser l’impact sur les visiteurs du site AEM.

Les déploiements en production suivent généralement les mêmes étapes que ci-dessus, mais par roulements :

1. Déploiement des packages AEM sur l’instance de création.
1. Détachement de dispatcher1 de l’équilibreur de charge.
1. Déploiement en parallèle des packages AEM sur publish1 et du package dispatcher sur dispatcher1. Purge du cache du Dispatcher.
1. Replacement du dispatcher1 dans l’équilibreur de charge.
1. Lorsque dispatcher1 fonctionne à nouveau, détachement de dispatcher2 de l’équilibreur de charge.
1. Déploiement en parallèle des packages AEM sur publish2 et du package dispatcher sur dispatcher2. Purge du cache du Dispatcher.
1. Replacement du dispatcher2 dans la répartition de charge.

Ce processus se poursuit jusqu’à ce que le déploiement ait atteint toutes les instances de publication et tous les Dispatchers dans la topologie.

## Mode d’exécution d’urgence du pipeline {#emergency-pipeline}

Dans les situations critiques, les clients d’Adobe Managed Services peuvent devoir déployer les modifications de code dans leurs environnements intermédiaire et de production sans attendre l’exécution d’un cycle de test complet de Cloud Manager.

Pour résoudre ces problèmes, le pipeline de production de Cloud Manager peut être exécuté en mode d’urgence. Lorsque ce mode est utilisé, les étapes de test de sécurité et de performance ne sont pas exécutées. Toutes les autres étapes, y compris les étapes de validation configurées, sont exécutées comme dans le mode normal d’exécution du pipeline.

>[!NOTE]
>
>La fonctionnalité Mode d’exécution d’urgence du pipeline est activée programme par programme par les ingénieurs du succès client.

### Utiliser le mode d’exécution d’urgence de pipeline {#using-emergency-pipeline}

Lors du démarrage de l’exécution d’un pipeline de production, si la fonction de mode d’exécution d’urgence du pipeline a été activée pour le programme, vous pouvez démarrer l’exécution en mode normal ou d’urgence à partir d’une boîte de dialogue.

![Exécuter les options de pipeline](/help/assets/execution-emergency1.png)

Lors de l’affichage de la page des détails d’exécution du pipeline pour une exécution en mode d’urgence, le chemin de navigation en haut de l’écran affiche un indicateur signalant que le pipeline s’exécute en mode d’urgence.

![Chemins de navigation du mode d’urgence](/help/assets/execution-emergency2.png)

Vous pouvez également exécuter un pipeline en mode d’urgence à l’aide de l’API Cloud Manager ou de l’interface de ligne de commande. Pour démarrer une exécution en mode d’urgence, envoyez une requête `PUT` au point d’entrée d’exécution du pipeline avec le paramètre de requête `?pipelineExecutionMode=EMERGENCY` ou lors de l’utilisation de l’interface de ligne de commande :

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## Réexécution d’un déploiement en production {#reexecute-deployment}

Dans de rares cas, les étapes de déploiement en production peuvent échouer pour des raisons transitoires. Dans ce cas, la réexécution de l’étape de déploiement en production est prise en charge tant que l’étape de déploiement en production est terminée, quel que soit le type d’achèvement (par exemple, réussi, annulé ou non). La réexécution crée une nouvelle exécution à l’aide du même pipeline constitué de trois étapes.

1. **L’étape de validation** - Il s’agit essentiellement de la même validation qui se produit lors d’une exécution normale du pipeline.
1. **L’étape de création** - Dans le contexte d’une réexécution, l’étape de création copie les artefacts et n’exécute pas de nouveau processus de création.
1. **L’étape de déploiement en production** - Cette opération utilise la même configuration et les mêmes options que l’étape de déploiement en production dans une exécution normale de pipeline.

Dans ce cas, si une réexécution est possible, la page d’état du pipeline de production fournit la variable **Réexécuter** en regard de l’option habituelle **Journal de version de téléchargement** .

![Option Réexécuter dans la fenêtre d’aperçu du pipeline](/help/assets/re-execute.png)

>[!NOTE]
>
>Lors d’une nouvelle exécution, l’étape de création est étiquetée dans l’interface utilisateur afin de refléter qu’elle copie des artefacts, et non qu’elle recrée.

### Limites {#limitations}

* La réexécution de l’étape de déploiement en production n’est disponible que lors de la dernière exécution.
* La réexécution n’est pas disponible pour les exécutions de restauration ou les exécutions de mise à jour des notifications push.
* Si la dernière exécution a échoué à un moment donné avant l’étape de déploiement en production, la réexécution n’est pas possible.


### Réexécution de l’API {#reexecute-api}

En plus d’être disponible dans l’interface utilisateur, vous pouvez utiliser [API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Pipeline-Execution) pour déclencher de nouvelles exécutions et identifier les exécutions déclenchées comme réexécutions.

#### Déclencher une réexécution {#triggering}

Pour déclencher une réexécution, une requête `PUT` doit être envoyée au lien HAL `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute` à l’état d’étape de déploiement en production.

* Si ce lien est présent, l’exécution peut être redémarrée à partir de cette étape.
* En cas d’absence, l’exécution ne peut pas être redémarrée à partir de cette étape.

Ce lien n’est disponible que pour l’étape de déploiement en production.

```javascript
 {
  "_links": {
    "http://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```

Syntaxe du lien HAL `href` n’est qu’un exemple et la valeur réelle doit toujours être lue à partir du lien HAL et non générée.

L’envoi d’une requête `PUT` vers ce point d’entrée entraîne la génération d’une réponse `201` en cas de réussite, le corps de la réponse étant la représentation de la nouvelle exécution. Cela revient à lancer une exécution régulière via l’API.

#### Identifier une exécution de réexécution {#identifying}

Les exécutions réexécutées peuvent être identifiées par la valeur `RE_EXECUTE` dans le `trigger` champ .
