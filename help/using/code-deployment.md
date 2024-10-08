---
title: Déploiement du code
description: Découvrez comment déployer votre code et ce qui se passe dans Cloud Manager lors du déploiement.
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '1637'
ht-degree: 100%

---


# Déploiement du code {#code-deployment}

Découvrez comment déployer votre code et ce qui se passe dans Cloud Manager lors du déploiement.

## Déployer du code avec Cloud Manager {#deploying-code-with-cloud-manager}

Une fois que vous avez configuré votre pipeline de production, y compris le référentiel et les environnements nécessaires, vous pouvez déployer votre code.

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

Plusieurs actions se produisent au cours de chaque étape du déploiement, lesquelles sont décrites dans cette section. Voir la section [Détails du processus de déploiement](#deployment-process) pour obtenir des détails techniques sur la manière dont le code lui-même est déployé en arrière-plan.

### Étape de déploiement dans l’environnement d’évaluation {#stage-deployment}

Le **déploiement dans l’environnement d’évaluation** comprend les actions suivantes :

* **Validation** : cette étape permet de s’assurer que le pipeline est configuré pour utiliser les ressources actuellement disponibles, par exemple, en s’assurant de l’existence de la branche configurée et de la disponibilité des environnements.
* **Test de version et unitaire** : cette étape exécute un processus de création en conteneur. Voir la section [Environnement de création](/help/getting-started/build-environment.md) pour plus de détails.
* **Analyse du code** : cette étape évalue la qualité du code de votre application. Voir la section [Comprendre les résultats de test](/help/using/code-quality-testing.md) pour obtenir plus de détails sur le processus de test.
* **Déployer dans l’environnement d’évaluation**

![Déploiement dans l’environnement d’évaluation](/help/assets/Stage_Deployment1.png)

### Étape du test dans l’environnement d’évaluation {#stage-testing}

L’étape du **test dans l’environnement d’évaluation** comprend les actions suivantes :

* **Tests de sécurité** : cette étape évalue l’impact de votre code sur la sécurité de l’environnement AEM. Consultez le document [Comprendre les résultats de test](/help/using/code-quality-testing.md) pour obtenir plus de détails sur le processus de test.
   * **Tests de performance** : cette étape évalue les performances de votre code. Voir la section [Comprendre les résultats de test](/help/using/code-quality-testing.md) pour obtenir plus de détails sur le processus de test.

### Étape de déploiement en production {#production-deployment}

L’étape de **déploiement en production** inclut les actions suivantes :

* **Application à approuver**
   * Cette option est activée lors de la configuration du pipeline.
   * Grâce à cette option, vous pouvez planifier le déploiement en production ou cliquer sur **Maintenant** pour exécuter immédiatement le déploiement en production.
* **Planifier le déploiement en production**
   * Cette option est activée lors de la configuration du pipeline.
   * La date et l’heure planifiées sont indiquées dans le fuseau horaire de l’utilisateur ou de l’utilisatrice.
     ![Planifier le déploiement](/help/assets/Production_Deployment1.png)
* **Assistance de l’ingénieur du service client** (si activée).
* **Déploiement en environnement de production**

![Déploiement en production](/help/assets/Prod_Deployment1.png)

Une fois le déploiement terminé, votre code se trouve dans son environnement ciblé et vous pouvez afficher les journaux.

![Déploiement terminé](/help/assets/Production_Deployment2.png)

## Délais d’expiration {#timeouts}

Les étapes suivantes expirent si des commentaires de l’utilisateur ou de l’utilisatrice sont attendus :

| Étape | Délai dépassé |
|--- |--- |
| Test de qualité du code | 7 jours |
| Test de sécurité | 7 jours |
| Test de performance | 7 jours |
| Application à approuver (évaluation) | 7 jours |
| Application à approuver (production) | 14 jours |
| Planning du déploiement en production | 14 jours |
| Déploiement de production géré | 14 jours |

## Détails du processus de déploiement {#deployment-process}

Cloud Manager télécharge tous les fichiers target/*.zip générés par le processus de création vers un emplacement de stockage. Ces artefacts sont récupérés à partir de cet emplacement pendant les phases de déploiement du pipeline.

Lorsque Cloud Manager se déploie sur des topologies autres que de production, l’objectif est de réaliser le déploiement aussi rapidement que possible ; les artefacts sont donc déployés simultanément sur tous les nœuds, comme suit :

1. Cloud Manager détermine si chaque artefact est un package AEM ou Dispatcher.
1. Cloud Manager supprime tous les Dispatchers de la répartition de charge pour isoler l’environnement pendant le déploiement.

   * Sauf configuration contraire, vous pouvez ignorer les modifications de l’équilibreur de charge dans les déploiements de développement et d’évaluation. En d’autres termes, pour l’environnement de développement, désolidarisez et attachez des étapes dans les deux pipelines hors production, et pour l’environnement d’évaluation, dans le pipeline de production.

   ![Ignorer l’équilibreur de charge](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >Il est prévu que 1-1-1 clientes et clients utilisent cette fonctionnalité.

1. Chaque artefact AEM est déployé sur chacune des instances AEM par le biais des API du gestionnaire de packages, avec des dépendances de packages qui déterminent l’ordre de déploiement.

   * Pour en savoir plus sur l’utilisation des packages pour installer de nouvelles fonctionnalités, transférer du contenu entre des instances et sauvegarder le contenu du référentiel. Voir la section [Gestionnaire de packages](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).

   >[!NOTE]
   >
   >Tous les artefacts AEM sont déployés à la fois sur l’instance de création et les instances de publication. Les modes d’exécution doivent être utilisés lorsque des configurations spécifiques à un nœud sont requises. Pour en savoir plus sur la manière dont les modes d’exécution vous permettent d’ajuster votre instance AEM à des fins spécifiques, voir la section [Modes d’exécution du document Déploiement sur AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/deploying/overview#runmodes).

1. L’artefact Dispatcher est déployé sur chaque Dispatcher comme suit :

   1. Les configurations actuelles sont sauvegardées et copiées vers un emplacement temporaire.
   1. Toutes les configurations sont supprimées, à l’exception des fichiers non-modifiables. Voir la section [Configurations du Dispatcher](/help/getting-started/dispatcher-configurations.md) pour plus d’informations. Cela permet de vider les répertoires pour qu’aucun fichier orphelin ne soit abandonné.
   1. L’artefact est extrait dans le répertoire `httpd`. Les fichiers non modifiables ne sont pas remplacés. Toute modification apportée aux fichiers non modifiables dans votre référentiel Git sera ignorée au moment du déploiement. Ces fichiers sont essentiels à la structure du Dispatcher AMS et ne peuvent pas être modifiés.
   1. Apache effectue un test de configuration. Si aucune erreur n’est trouvée, le service est rechargé. Si une erreur se produit, les configurations sont restaurées à partir de la sauvegarde, le service est rechargé et l’erreur est signalée à Cloud Manager.
   1. Chaque chemin spécifié dans la configuration de pipeline est invalidé ou purgé du cache du Dispatcher.

   >[!NOTE]
   >
   >Cloud Manager exige que l’artefact du Dispatcher contienne le jeu de fichiers complet. Tous les fichiers de configuration du Dispatcher doivent être présents dans le référentiel Git. Les fichiers ou dossiers manquants entraînent l’échec du déploiement.

1. Après le déploiement réussi de tous les packages AEM et de Dispatcher sur tous les nœuds, les Dispatchers sont ajoutés à l’équilibreur de charge et le déploiement est terminé.

   >[!NOTE]
   >
   >Vous pouvez ignorer les modifications de l’équilibreur de charge dans les déploiements de développement et d’évaluation. En d’autres termes, pour l’environnement de développement, désolidarisez et attachez des étapes dans les deux pipelines hors production, et pour l’environnement d’évaluation, dans le pipeline de production.

### Phase de déploiement en production {#deployment-production-phase}

Le processus de déploiement vers des topologies de production diffère légèrement afin de minimiser l’impact sur les visiteurs et visiteuses du site AEM.

Les déploiements en production suivent généralement les mêmes étapes que ci-dessus, mais par roulements :

1. Déploiement des packages AEM sur l’instance de création.
1. Détachement de dispatcher1 de l’équilibreur de charge.
1. Déployez en parallèle les packages AEM sur publish1 et le package Dispatcher sur dispatcher1. Purgez le cache du Dispatcher.
1. Replacement du dispatcher1 dans l’équilibreur de charge.
1. Lorsque dispatcher1 fonctionne à nouveau, détachement de dispatcher2 de l’équilibreur de charge.
1. Déployez en parallèle les packages AEM sur publish2 et le package Dispatcher sur dispatcher2. Purgez le cache du Dispatcher.
1. Replacement du dispatcher2 dans la répartition de charge.

Ce processus se poursuit jusqu’à ce que le déploiement ait atteint toutes les instances de publication et tous les Dispatchers dans la topologie.

## Mode d’exécution d’urgence du pipeline {#emergency-pipeline}

Dans des situations critiques, il se peut que les clientes et clients Adobe Managed Services doivent déployer immédiatement les modifications de code dans leurs environnements d’évaluation et de production. Cette fonctionnalité leur permet de contourner le cycle de test Cloud Manager complet.

Pour résoudre ces problèmes, le pipeline de production de Cloud Manager peut être exécuté en mode d’urgence. Lorsque ce mode est utilisé, les étapes de test de sécurité et de performance ne sont pas exécutées. Toutes les autres étapes, y compris les étapes de validation configurées, sont exécutées comme dans le mode normal d’exécution du pipeline.

>[!NOTE]
>
>La fonction du mode d’exécution du pipeline d’urgence est activée programme par programme. L’activation est effectuée par l’équipe d’ingénierie du succès client.

### Utiliser le mode d’exécution d’urgence de pipeline {#using-emergency-pipeline}

Lorsque vous démarrez l’exécution d’un pipeline de production, vous pouvez choisir entre le mode normal et le mode d’urgence dans une boîte de dialogue. Cette option est disponible si la fonction du mode d’exécution du pipeline d’urgence est activée pour le programme. Ce choix est disponible une fois la fonction activée.

![Exécuter les options de pipeline](/help/assets/execution-emergency1.png)

Lors de l’affichage de la page des détails d’exécution du pipeline pour une exécution en mode d’urgence, le chemin de navigation en haut de l’écran affiche un indicateur signalant que le pipeline s’exécute en mode d’urgence.

![Chemins de navigation du mode d’urgence](/help/assets/execution-emergency2.png)

Vous pouvez également exécuter un pipeline en mode d’urgence à l’aide de l’API Cloud Manager ou de l’interface de ligne de commande. Pour démarrer une exécution en mode d’urgence, envoyez une requête `PUT` au point d’entrée d’exécution du pipeline avec le paramètre de requête `?pipelineExecutionMode=EMERGENCY` ou lors de l’utilisation de l’interface de ligne de commande :

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## Exécuter à nouveau un déploiement en production {#reexecute-deployment}

Dans de rares cas, les étapes de déploiement en production peuvent échouer pour des raisons transitoires. Dans ce cas, vous pouvez exécuter à nouveau l’étape de déploiement en production à condition qu’elle soit terminée, qu’elle ait été réussie, annulée ou ratée. La réexécution est prise en charge par l’utilisation du même pipeline qui comprend les trois étapes suivantes :

1. **Étape de validation** : il s’agit de la même validation que celle qui se produit lors de l’exécution normale d’un pipeline.
1. **Étape de création** : dans le contexte d’une réexécution, l’étape de création consiste à copier des artefacts, sans réellement exécuter un nouveau processus de création.
1. **Étape de déploiement en production** : utilise la même configuration et les mêmes options que l’étape de déploiement en production dans une exécution normale de pipeline.

Dans de telles circonstances, si une réexécution est possible, la page de statut du pipeline de production fournit l’option **Réexécuter** en regard de l’option habituelle **Télécharger le journal de création**.

![Option Réexécuter dans la fenêtre de la vue d’ensemble du pipeline](/help/assets/re-execute.png)

>[!NOTE]
>
>Lors d’une nouvelle exécution, l’étape de création est étiquetée dans l’interface utilisateur afin d’indiquer qu’elle copie (et non qu’elle recrée) des artefacts.

### Limites {#limitations}

* La réexécution de l’étape de déploiement en production n’est disponible que lors de la dernière exécution.
* La réexécution n’est pas disponible pour les exécutions de restauration ou les exécutions de mise à jour des notifications push.
* Si la dernière exécution a échoué à un moment donné avant l’étape de déploiement en production, une nouvelle exécution n’est pas possible.


### Exécuter à nouveau l’API {#reexecute-api}

En plus d’être disponible dans l’IU, l’[API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/?lang=fr#tag/Pipeline-Execution) peut servir à déclencher de nouvelles exécutions et à identifier les exécutions déclenchées comme nouvelles exécutions.

#### Déclencher une nouvelle exécution {#triggering}

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

La syntaxe de la valeur `href` du lien HAL est donnée à titre d’exemple. La valeur réelle doit toujours être lue à partir du lien HAL et non générée.

L’envoi d’une requête `PUT` à ce point d’entrée entraîne une réponse `201` en cas de réussite. Le corps de la réponse est la représentation de la nouvelle exécution. Cela revient à lancer une exécution ordinaire via l’API.

#### Identifier une exécution exécutée à nouveau {#identifying}

Le système identifie les exécutions exécutées à nouveau par la valeur `RE_EXECUTE` dans le champ de déclenchement.