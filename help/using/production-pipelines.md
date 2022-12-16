---
title: Configurer des pipelines de production
description: Découvrez comment créer et configurer des pipelines de production à l’aide de Cloud Manager afin de déployer votre code.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 39b38da17ed1cadf4f2e9633a9e76b537325316f
workflow-type: ht
source-wordcount: '1302'
ht-degree: 100%

---


# Configuration des pipelines de production {#configuring-production-pipelines}

Découvrez comment créer et configurer des pipelines de production à l’aide de Cloud Manager afin de déployer votre code. si vous souhaitez d’abord une présentation plus conceptuelle du fonctionnement des pipelines dans Cloud Manager, consultez le document [Pipelines CI/CD.](/help/overview/ci-cd-pipelines.md)

## Présentation {#overview}

En utilisant le volet **Paramètres du pipeline** dans [!UICONTROL Cloud Manager], vous pouvez créer deux types de pipelines différents.

* **Pipelines de production** - un pipeline de production est un pipeline spécialement conçu, composé d’une série d’étapes coordonnées pour mener le référentiel Git jusqu’à la production.
* **Pipelines hors production** - un pipeline hors production sert principalement à exécuter des analyses de qualité du code ou à déployer le code source dans un environnement de développement.

Ce document se concentre sur les pipelines de production. Pour plus d’informations sur la configuration des pipelines hors production, voir le document [Configuration de pipelines hors production.](/help/using/non-production-pipelines.md)

Le rôle du **responsable du déploiement** : il est chargé de la configuration du pipeline. La configuration du pipeline comprend :

1. La définition du déclencheur qui démarrera le pipeline ;
1. La définition des paramètres qui contrôlent le déploiement en production ;
1. La configuration des paramètres de test de performance.

>[!NOTE]
>
>Un pipeline ne peut être configuré que si le référentiel Git qui lui est associé dispose d’au moins une branche et que la [configuration du programme](/help/getting-started/program-setup.md) est terminée.

## Tutoriel vidéo {#video-tutorial-one}

Cette vidéo présente un aperçu du processus de création de pipeline, détaillé dans ce document.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## Ajouter un nouveau pipeline de production {#adding-production-pipeline}

Une fois que vous avez utilisé l’interface utilisateur [!UICONTROL Cloud Manager] pour configurer votre programme et que vous disposez d’au moins un environnement, vous êtes prêt à ajouter un pipeline de production.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la vignette **Pipelines** de la page **Aperçu du programme**, cliquez sur **+Ajouter** et sélectionnez **Ajout d’un pipeline de production**.

   ![Ajout d’un pipeline de production](/help/assets/configure-pipelines/add-prod1.png)

1. La boîte de dialogue **Ajout d’un pipeline de production** s’ouvre sur l’onglet de **Configuration** où plusieurs options de votre pipeline doivent être définies. Ces options sont regroupées en sections réductibles et sont décrites dans les étapes suivantes.

   1. Attribuez un nom explicite à votre pipeline dans le champ **Nom du pipeline**.

   1. Sous la section **Code source**, définissez où le pipeline récupère le code qu’il traitera.

      * **Référentiel** - cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.
      >[!TIP]
      >
      >Voir le document [Configuration du programme](/help/getting-started/program-setup.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

      * **Branche Git** - cette option définit à partir de quelle branche sélectionnée le pipeline doit récupérer le code.
      * **Emplacement du code** - cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.

      ![Définition des référentiels pour le pipeline](/help/assets/configure-pipelines/add-prod2.png)

   1. Sous la section **Environnements**, vous définissez ce qui déclenche un déploiement et comment il doit être déployé par environnement.

      1. Dans la section **ÉTAPE**, vous pouvez définir la manière dont le pipeline se déploie vers votre environnement d’évaluation.

         * **Déclencheur de déploiement** - vous disposez des options suivantes pour définir les déclencheurs de déploiement pour démarrer le pipeline.

            * **Manuel** - utilisez cette option pour démarrer manuellement le pipeline à l’aide de l’interface utilisateur de Cloud Manager.
            * **Lors des modifications Git** - cette option démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.
         * **Comportement en cas d’échecs de mesure importants** - lors de la configuration ou de la modification du pipeline, le responsable de déploiement peut définir le comportement du pipeline lorsqu’un échec important est rencontré à l’un des points de contrôle qualité. Les options disponibles sont les suivantes :

            * **Demander à chaque fois** - il s’agit du paramètre par défaut qui nécessite une intervention manuelle pour tout échec important.
            * **Défaillance immédiate** - si cette option est sélectionnée, le pipeline sera interrompu chaque fois qu’une défaillance importante aura lieu. Il s’agit essentiellement d’imiter un utilisateur qui rejetterait manuellement chaque échec.
            * **Continuer immédiatement** - si cette option est sélectionnée, le pipeline se poursuivra automatiquement chaque fois qu’une défaillance importante se produira. Il s’agit essentiellement d’émuler un utilisateur approuvant manuellement chaque échec.

         ![Déclencheur de déploiement](/help/assets/configure-pipelines/add-prod3.png)

         * **Options de déploiement** - vous pouvez accélérer certaines tâches de déploiement.

            * **Approbation après le déploiement d’évaluation** - cette approbation a lieu après le déploiement dans l’environnement d’évaluation avant que tout test ne soit effectué. Sinon, l’approbation se produit avant le déploiement en production, qui est effectué une fois tous les tests terminés.

            * **Ignorer les modifications de la répartition de charge** - les modifications de la répartition de charge ne sont pas effectuées.

         ![Options de déploiement intermédiaire](/help/assets/configure-pipelines/add-prod4.png)

         * **Configuration de Dispatcher** - le rôle du **responsable de déploiement** consiste à configurer un ensemble de chemins de contenu qui seront soit invalidés soit vidés du cache d’AEM Dispatcher lorsqu’un pipeline est exécuté. Ces actions de cache sont exécutées dans le cadre de l’étape du pipeline de déploiement, juste après le déploiement des packages de contenu. Ces paramètres utilisent le comportement standard d’AEM Dispatcher. Pour configurer :

            1. Sous **CHEMIN**, fournissez un chemin d’accès au contenu.
            1. Sous **TYPE**, sélectionnez l’action à effectuer sur ce chemin.

               * **Purge** - videz le cache.
               * **Invalider** - effectuez une invalidation du cache, comme lorsque le contenu est activé d’une instance de création vers une instance de publication.
            1. Cliquez sur **Ajouter un chemin** pour ajouter votre chemin spécifié. Vous pouvez ajouter jusqu’à 100 chemins par environnement.

         ![Configuration de Dispatcher](/help/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >En règle générale, l’utilisation de l’action Invalider est préférable, mais il peut y avoir des cas où la purge est nécessaire, notamment lors de l’utilisation des bibliothèques clientes HTML d’AEM.

      1. Dans la section **PRODUCTION**, vous pouvez définir la manière dont le pipeline se déploie dans votre environnement de production.

         * **Options de déploiement** - vous pouvez définir les paramètres contrôlant le déploiement en production.

            * **Utiliser l’approbation GoLive** - un déploiement doit être approuvé manuellement par un utilisateur ayant le rôle de **propriétaire d’entreprise**, **chef de projet** ou **responsable de déploiement** via l’interface utilisateur [!UICONTROL Cloud Manager].
            * **Planifié** - cette option interrompt le pipeline avant le déploiement en production pour permettre sa planification. Si cette option est sélectionnée, le pipeline s’arrêtera après le déploiement dans l’environnement d’évaluation et demandera à l’utilisateur l’action à entreprendre.
               * **Maintenant** - cette option permet de déployer immédiatement en production, terminant ainsi le pipeline.
               * **Date** - cette option permet à l’utilisateur de planifier une heure à laquelle le déploiement doit être terminé.
               * **Arrêter l’exécution** - cette option interrompt le déploiement en production.

            >[!TIP]
            >
            >Consultez le document [Code de déploiement](/help/using/code-deployment.md) pour découvrir comment définir le planning de déploiement ou exécuter le pipeline immédiatement.

            * **Solliciter la supervision de l’ingénieur support client (CSE)** - si cette option est choisie, un CSE est engagé pour véritablement démarrer le déploiement. Lors de la création ou de la modification d’un pipeline lorsque cette option est activée, le rôle **Responsable de déploiement** dispose des options suivantes.

               * **N’importe quel CSE** - cette option permet à tout CSE disponible de démarrer le déploiement.
               * **Mon CSE** - cette option permet uniquement au CSE spécifique affecté au client de démarrer le déploiement. Cela s’applique également au remplaçant désigné du CSE si le CSE attribué est indisponible.

            ![Options de déploiement en production](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configuration de Dispatcher** - définissez la configuration de Dispatcher pour votre environnement de production. Les options sont identiques à celles de l’environnement d’évaluation.










1. Cliquez sur **Continuer** pour accéder à l’onglet **Tests d’évaluation** où vous pouvez configurer les tests de performance d’AEM Sites et d’AEM Assets, en fonction des produits sous licence que vous possédez.

   >[!TIP]
   >
   >Consultez le document [Test de qualité du code](/help/using/code-quality-testing.md#performance-testing) pour plus de détails sur les options disponibles dans l’onglet **Test d’évaluation**.

   1. Sous la section **Diffusion du contenu des sites/Poids de charge distribué**, vous définissez comment le test de performance des sites est configuré en fonction de la pondération des requêtes de page entre les trois ensembles de pages, qui peuvent être activés ou désactivés.

      * **Pages dynamiques populaires**
      * **Autres pages dynamiques**
      * **Nouvelles pages**

      ![Poids de charge des sites](/help/assets/configure-pipelines/add-prod5.png)

   1. Sous la section **Distribution des tests de performance des ressources**, vous définissez la distribution de test des images et des PDF ainsi que la définition de vos propres ressources de test.

      * **Images** - réglez le curseur pour ajuster la répartition du test entre les images et les PDF.
      * **PDF** - réglez le curseur pour ajuster la répartition du test entre les images et les PDF.

      * Définissez vos propres ressources personnalisées en les chargeant.

         1. **FORMAT** - choisissez si votre ressource personnalisée est un PDF ou une image.
         1. **NOM DE FICHIER** - utilisez le bouton du navigateur de fichiers pour sélectionner une image sur votre ordinateur local.
         1. **Ajouter un fichier test** - cliquez pour charger la ressource sélectionnée.

      ![Distribution des tests des ressources](/help/assets/configure-pipelines/add-prod6.png)



1. Cliquez sur **Enregistrer** pour terminer l’ajout de votre pipeline de production.

## Les étapes suivantes {#the-next-steps}

Une fois que vous avez configuré le pipeline, vous devez déployer votre code. Consultez le document [Déploiement du code](/help/using/code-deployment.md) pour plus de détails.
