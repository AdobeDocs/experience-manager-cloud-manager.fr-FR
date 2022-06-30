---
title: Déploiement de votre code
seo-title: Deploy your Code
description: Fournit un aperçu du processus de déploiement dans Cloud Manager.
seo-description: Learn how to deploy your code once you have configured your pipeline (repository, environment, and testing environment)
uuid: 4e3807e1-437e-4922-ba48-0bcadf293a99
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 832a4647-9b83-4a9d-b373-30fe16092b15
feature: Code Deployment
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: 4c86446127c8cd66f964b192f3602f02fd2ddf8e
workflow-type: ht
source-wordcount: '1615'
ht-degree: 100%

---

# Déploiement de votre code {#deploy-your-code}

## Déploiement du code avec Cloud Manager {#deploying-code-with-cloud-manager}

>[!NOTE]
>Pour en savoir plus sur le déploiement du code pour Cloud Manager dans AEM as a Cloud Service, consultez [ce lien](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr#using-cloud-manager).

Une fois que vous avez configuré votre pipeline de production (référentiel, environnement et environnement de test), vous êtes prêt à déployer votre code.

1. Cliquez sur **Déployer** dans Cloud Manager pour lancer le processus de déploiement.

   ![](assets/Deploy1.png)

1. L’écran **Exécution du pipeline** s’affiche.

   Cliquez sur **Compilation** pour lancer le processus.

   ![](assets/Deploy2.png)

1. Le processus de création complet déploie le code.

   Les étapes suivantes sont impliquées dans le processus de création :

   1. Déploiement dans l’environnement intermédiaire
   1. Test dans l’environnement intermédiaire
   1. Déploiement dans l’environnement de production

   >[!NOTE]
   >
   >En outre, vous pouvez examiner les étapes de divers processus de déploiement en affichant les journaux ou en examinant les résultats pour les critères de test.

   Le **Déploiement dans l’environnement intermédiaire** comprend les étapes suivantes :

   * Validation : cette étape permet de s’assurer que le pipeline est configuré pour utiliser les ressources actuellement disponibles ; par exemple, la branche configurée existe, les environnements sont disponibles, etc.
   * Test unitaire et version : cette étape exécute un processus de création en conteneur. Voir [Présentation de l’environnement de création](/help/using/build-environment-details.md) pour plus d’informations sur l’environnement de création.
   * Analyse du code : cette étape évalue la qualité du code de votre application. Pour plus d’informations sur le processus de test, voir [Présentation des résultats des tests](understand-your-test-results.md).
   * Déployer dans l’environnement intermédiaire

   ![](assets/Stage_Deployment1.png)

   Le **test dans l’environnement intermédiaire** comprend les étapes suivantes :

   * Tests de sécurité : cette étape évalue l’impact du code de votre application sur la sécurité de l’environnement AEM. Pour plus d’informations sur le processus de test, voir [Présentation des résultats des tests](understand-your-test-results.md).
   * Tests de performance : cette étape évalue les performances du code de votre application. Pour plus d’informations sur le processus de test, voir [Présentation des résultats des tests](understand-your-test-results.md).

   ![](assets/Stage_Testing1.png)

   Le **déploiement en environnement de production** comprend les étapes suivantes :

   * **Application à approuver** (si activée).
   * **Planification du déploiement en production** (si activée).
   * **Assistance de l’ingénieur du service client** (si activée).
   * **Déploiement en environnement de production**

   ![](assets/Prod_Deployment1.png)

   >[!NOTE]
   >
   >La **planification du déploiement en production** est activée lors de la configuration du pipeline.
   >
   >
   >Grâce à cette option, vous pouvez planifier le déploiement en production ou cliquer sur **Maintenant** pour exécuter immédiatement le déploiement en production.
   >
   >
   >La date et l’heure planifiées sont indiquées dans le fuseau horaire de l’utilisateur.
   >
   >
   >Cliquez sur **Confirmer** pour vérifier vos paramètres.

   ![](assets/Production_Deployment1.png)

   Une fois que vous avez confirmé la planification du déploiement, votre déploiement du code se termine.

   L’écran suivant s’affiche lorsque l’option **Maintenant** est sélectionnée à l’étape précédente.

   ![](assets/Production_Deployment2.png)

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

## Processus de déploiement {#deployment-process}

La section suivante décrit le déploiement des packages AEM et dispatcher dans les phases intermédiaires et de production.

Cloud Manager télécharge tous les fichiers target/*.zip générés par le processus de création vers un emplacement de stockage.  Ces artefacts sont récupérés à partir de cet emplacement pendant les phases de déploiement du pipeline.

Lorsque Cloud Manager se déploie sur des topologies autres que de production, l’objectif est de réaliser le déploiement aussi rapidement que possible ; les artefacts sont donc déployés simultanément sur tous les nœuds, comme suit :

1. Cloud Manager détermine si chaque artefact est un package AEM ou dispatcher.
1. Cloud Manager supprime tous les dispatchers de l’équilibreur de charge pour isoler l’environnement pendant le déploiement.

   Sauf configuration contraire, vous pouvez ignorer les modifications de l’équilibreur de charge dans les déploiements de développement et en environnement intermédiaire, c’est-à-dire détacher et attacher des étapes dans les deux pipelines hors production, pour les environnements de développement et le pipeline de production, pour les environnements intermédiaires.

   ![](assets/load_balancer.png)

   >[!NOTE]
   >
   >Cette fonctionnalité devrait principalement être utilisée par les clients 1-1-1.

1. Chaque artefact AEM est déployé sur chacune des instances AEM par le biais des API de Package Manager, avec des dépendances de packages qui déterminent l’ordre de déploiement.

   Pour en savoir plus sur l’utilisation de packages pour installer de nouvelles fonctionnalités, transférer du contenu entre des instances et sauvegarder le contenu du référentiel, reportez-vous à la section Utilisation de packages.

   >[!NOTE]
   >
   >Tous les artefacts AEM sont déployés à la fois sur l’instance de création et les instances de publication. Les modes d’exécution doivent être utilisés lorsque des configurations spécifiques à un nœud sont requises. Pour en savoir plus sur la façon dont les modes d’exécution vous permettent d’ajuster votre instance AEM à des fins spécifiques, consultez Modes d’exécution.

1. L’artefact dispatcher est déployé sur chaque dispatcher comme suit :

   1. Les configurations actuelles sont sauvegardées et copiées vers un emplacement temporaire.
   1. Toutes les configurations sont supprimées, à l’exception des fichiers non modifiables. Pour plus d’informations, consultez la section Gestion des configurations du Dispatcher. Cela permet de vider les répertoires pour qu’aucun fichier orphelin ne soit abandonné.
   1. L’artefact est extrait dans le répertoire `httpd`.  Les fichiers non modifiables ne sont pas remplacés. Toute modification apportée aux fichiers non modifiables dans votre référentiel git sera ignorée au moment du déploiement.  Ces fichiers sont essentiels à la structure du dispatcher AMS et ne peuvent pas être modifiés.
   1. Apache effectue un test de configuration. Si aucune erreur n’est trouvée, le service est rechargé. Si une erreur se produit, les configurations sont restaurées à partir de la sauvegarde, le service est rechargé et l’erreur est renvoyée à Cloud Manager.
   1. Chaque chemin spécifié dans la configuration de pipeline est invalidé ou purgé du cache du dispatcher.

   >[!NOTE]
   >Cloud Manager exige que l’artefact du dispatcher contienne le jeu de fichiers complet.  Tous les fichiers de configuration du dispatcher doivent être présents dans le référentiel git. Les fichiers ou dossiers manquants entraînent l’échec du déploiement.

1. Après le déploiement réussi de tous les packages AEM et de dispatcher sur tous les nœuds, les dispatchers sont ajoutés à l’équilibreur de charge et le déploiement est terminé.

   >[!NOTE]
   >Vous pouvez ignorer les modifications de l’équilibreur de charge dans les déploiements de développement et d’évaluation, c’est-à-dire, détacher et attacher des étapes dans les deux pipelines hors production pour les environnements de développement, ainsi que dans le pipeline de production, pour les environnements d’évaluation.

### Phase de déploiement en production {#deployment-production-phase}

Le processus de déploiement des topologies de production diffère légèrement afin de minimiser l’impact sur les visiteurs d’AEM Site.

Les déploiements en production suivent généralement les mêmes étapes que ci-dessus, mais par roulements :

1. Déploiement des packages AEM sur l’instance de création.
1. Détachement de dispatcher1 de l’équilibreur de charge.
1. Déploiement en parallèle des packages AEM sur publish1 et du package dispatcher sur dispatcher1. Purge du cache du Dispatcher.
1. Replacement du dispatcher1 dans l’équilibreur de charge.
1. Lorsque dispatcher1 fonctionne à nouveau, détachement de dispatcher2 de l’équilibreur de charge.
1. Déploiement en parallèle des packages AEM sur publish2 et du package dispatcher sur dispatcher2. Purge du cache du Dispatcher.
1. Replacement du dispatcher2 dans l’équilibreur de charge.
Ce processus se poursuit jusqu’à ce que le déploiement ait atteint toutes les instances de publication et tous les Dispatchers dans la topologie.

## Mode d’exécution d’urgence du pipeline {#emergency-pipeline}

Dans les situations critiques, les clients d’Adobe Managed Services peuvent devoir déployer les modifications de code dans leurs environnements intermédiaire et de production sans attendre l’exécution d’un cycle de test complet de Cloud Manager.

Pour résoudre ces problèmes, le pipeline de production de Cloud Manager peut être exécuté en mode *d’urgence*. Lorsque ce mode est utilisé, les étapes de test de sécurité et de performance ne sont pas exécutées ; toutes les autres étapes, y compris les étape de validation configurées, sont exécutées comme dans le mode normal d’exécution du pipeline.

>[!NOTE]
>La fonctionnalité Mode d’exécution d’urgence du pipeline est activée au niveau du programme par les ingénieurs de réussite client.

### Utilisation du mode d’exécution d’urgence de pipeline {#using-emergency-pipeline}

Lorsque vous démarrez l’exécution d’un pipeline de production, si cette fonctionnalité a été activée, vous pouvez le faire en mode normal ou d’urgence à partir de la boîte de dialogue, comme illustré ci-dessous.

![](assets/execution-emergency1.png)

En outre, en affichant la page des détails d’exécution du pipeline pour une exécution en mode d’urgence, le chemin de navigation en haut de l’écran affiche un indicateur indiquant que le mode d’urgence a été utilisé pour cette exécution en particulier.

![](assets/execution-emergency2.png)

Vous pouvez également créer une exécution de pipeline dans ce mode d’urgence à l’aide de l’API Cloud Manager ou de l’interface de ligne de commande. Pour démarrer une exécution en mode d’urgence, envoyez une requête PUT au point d’entrée d’exécution du pipeline avec le paramètre de requête `?pipelineExecutionMode=EMERGENCY` ou lors de l’utilisation de l’interface de ligne de commande :

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

>[!IMPORTANT]
>L’utilisation de l’indicateur `--emergency` peut nécessiter une mise à jour vers la dernière version de l’`aio-cli-plugin-cloudmanager`.

## Réexécuter un déploiement en production {#Reexecute-Deployment}

La réexécution de l’étape de déploiement en production est prise en charge pour les exécutions où l’étape de déploiement en production est terminée. Le type d’achèvement n’est pas important : le déploiement peut être réussi (uniquement pour les programmes AMS), annulé ou non réussi. Cela dit, le cas d’utilisation principal doit être celui où l’étape de déploiement en production a échoué pour des raisons transitoires. La réexécution crée une nouvelle exécution à l’aide du même pipeline. Cette nouvelle exécution se compose de trois étapes :

1. L’étape de validation : il s’agit essentiellement de la même validation qui se produit lors de l’exécution normale d’un pipeline.
1. L’étape de création : dans le contexte d’une réexécution, l’étape de création consiste à copier des artefacts, sans réellement exécuter un nouveau processus de création.
1. L’étape de déploiement en production : elle utilise la même configuration et les mêmes options que l’étape de déploiement en production dans une exécution normale de pipeline.

L’étape de création peut être libellée de façon légèrement différente dans l’interface utilisateur afin de refléter le fait qu’elle copie (et ne récrée pas) des artefacts.

![](assets/Re-deploy.png)

Restrictions :

* La réexécution de l’étape de déploiement en production n’est disponible que lors de la dernière exécution.
* La réexécution n’est pas disponible pour les exécutions de restauration.
* Si la dernière exécution est une exécution de restauration, la réexécution n’est pas possible.
* Si la dernière exécution est une exécution de mise à jour des notifications push, la réexécution n’est pas possible.
* Si la dernière exécution a échoué à un moment donné avant l’étape de déploiement en production, la réexécution n’est pas possible.

### Réexécuter l’API {#Reexecute-API}

### Identifier une exécution de réexécution

Pour déterminer si une exécution est une exécution de ré-exécution, le champ déclencheur peut être examiné. Sa valeur sera *RE_EXECUTE*.

### Déclencher une nouvelle exécution

Pour déclencher une réexécution, une requête PUT doit être envoyée au lien HAL ```http://ns.adobe.com/adobecloud/rel/pipeline/reExecute``` à l’état d’étape de déploiement en production. Si ce lien est présent, l’exécution peut être redémarrée à partir de cette étape. En cas d’absence, l’exécution ne peut pas être redémarrée à partir de cette étape. Dans la version initiale, ce lien sera uniquement présent lors de l’étape de déploiement en production, mais les prochaines versions peuvent prendre en charge le démarrage du pipeline à partir d’autres étapes. Exemple :

```Javascript
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


La syntaxe de la valeur *href* du lien HAL ci-dessus n’est pas destinée à être utilisée comme point de référence. La valeur réelle doit toujours être lue à partir du lien HAL et non générée.

L’envoi d’une requête *PUT* vers ce point d’entrée entraîne la génération d’une réponse *201* en cas de réussite, le corps de la réponse étant la représentation de la nouvelle exécution. Cela revient à lancer une exécution régulière via l’API.
