---
title: Configuration des pipelines de production
description: Découvrez comment créer et configurer des pipelines de production à l’aide de Cloud Manager afin de déployer votre code.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1247'
ht-degree: 47%

---


# Configuration des pipelines de production {#configuring-production-pipelines}

Découvrez comment créer et configurer des pipelines de production à l’aide de Cloud Manager afin de déployer votre code. Si vous souhaitez d’abord une présentation plus conceptuelle du fonctionnement des pipelines dans Cloud Manager, reportez-vous à la section [Pipelines CI/CD](/help/overview/ci-cd-pipelines.md).

## Présentation {#overview}

En utilisant le volet **Paramètres du pipeline** dans [!UICONTROL Cloud Manager], vous pouvez créer deux types de pipelines différents.

* **Pipelines de production** - Un pipeline de production est un pipeline créé spécifiquement à partir d’une série d’étapes orchestrées pour intégrer du code source depuis votre référentiel Git jusqu’à la production.
* **Pipelines hors production** - un pipeline hors production sert principalement à exécuter des analyses de qualité du code ou à déployer le code source dans un environnement de développement.

Ce document se concentre sur les pipelines de production. Pour plus d’informations sur la configuration des pipelines hors production, voir le document [Configuration des pipelines hors production](/help/using/non-production-pipelines.md).

Le rôle du **responsable du déploiement** : il est chargé de la configuration du pipeline. La configuration du pipeline comprend :

1. Définition du déclencheur qui lance le pipeline.
1. La définition des paramètres qui contrôlent le déploiement en production ;
1. La configuration des paramètres de test de performance.

>[!NOTE]
>
>Un pipeline ne peut pas être configuré tant que son référentiel Git associé ne comporte pas au moins une branche et que la [configuration du programme](/help/getting-started/program-setup.md) n’est pas terminée.

## Ajout d’un nouveau pipeline de production {#adding-production-pipeline}

Après avoir utilisé l’interface utilisateur [!UICONTROL Cloud Manager] pour configurer votre programme et disposer d’au moins un environnement, vous êtes prêt à ajouter un pipeline de production.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Cliquez sur **+Ajouter**, puis sélectionnez **Ajouter un pipeline de production**.

   ![Ajout d’un pipeline de production](/help/assets/configure-pipelines/add-prod1.png)

1. La boîte de dialogue **Ajout d’un pipeline de production** s’ouvre sur l’onglet de **Configuration** où plusieurs options de votre pipeline doivent être définies. Ces options sont regroupées en sections réductibles et sont décrites dans les étapes suivantes.

   1. Attribuez un nom explicite à votre pipeline dans le champ **Nom du pipeline**.

   1. Sous la section **Code Source** , vous définissez l’emplacement où le pipeline récupère le code qu’il traite.

      * **Repository** - Définit le référentiel Git que le pipeline doit récupérer le code.

      >[!TIP]
      >
      >Voir le document [Configuration du programme](/help/getting-started/program-setup.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

      * **Branche Git** - Définit à partir de quelle branche du pipeline sélectionné doit récupérer le code.
      * **Emplacement du code** - Définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.

      ![Définition des référentiels pour le pipeline](/help/assets/configure-pipelines/add-prod2.png)

   1. Sous la section **Environnements**, vous définissez ce qui déclenche un déploiement et comment il doit être déployé par environnement.

      1. Dans la section **ÉTAPE**, vous pouvez définir la manière dont le pipeline se déploie vers votre environnement d’évaluation.

         * **Déclencheur de déploiement** - vous disposez des options suivantes pour définir les déclencheurs de déploiement pour démarrer le pipeline.

            * **Manuel** - Démarrez le pipeline manuellement à l’aide de l’interface utilisateur de Cloud Manager.
            * **Lors des modifications Git** - Démarrez le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.

         * **Comportement en cas d’échecs de mesure importants** - lors de la configuration ou de la modification du pipeline, le responsable de déploiement peut définir le comportement du pipeline lorsqu’un échec important est rencontré à l’un des points de contrôle qualité. Les options disponibles sont les suivantes :

            * **Demander à chaque fois** - Le paramètre par défaut et nécessite une intervention manuelle en cas d’échec important.
            * **Fail Immédiatement** - Le pipeline est annulé chaque fois qu’un échec important se produit. Il émule un utilisateur rejetant manuellement chaque échec.
            * **Continuer immédiatement** - Le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Il émule un utilisateur approuvant manuellement chaque échec.

         ![Déclencheur de déploiement](/help/assets/configure-pipelines/add-prod3.png)

         * **Options de déploiement** - vous pouvez accélérer certaines tâches de déploiement.

            * **Approbation après le déploiement d’évaluation** - cette approbation a lieu après le déploiement dans l’environnement d’évaluation avant que tout test ne soit effectué. Dans le cas contraire, l’approbation se produit avant le déploiement en production, qui est effectué une fois tous les tests terminés.

            * **Ignorer les modifications de la répartition de charge** - les modifications de la répartition de charge ne sont pas effectuées.

         ![Options de déploiement intermédiaire](/help/assets/configure-pipelines/add-prod4.png)

         * **Configuration Dispatcher** - Le rôle **Gestionnaire de déploiement** peut configurer un ensemble de chemins de contenu qui sont invalidés ou purgés du cache Dispatcher d’AEM lorsqu’un pipeline est exécuté. Ces actions de cache sont effectuées dans le cadre de l’étape du pipeline de déploiement, juste après le déploiement des packages de contenu. Ces paramètres utilisent le comportement standard d’AEM Dispatcher. Pour effectuer la configuration, procédez comme suit :

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

            * **Utiliser l’approbation Go Live** - Un utilisateur disposant du rôle **Propriétaire de l’entreprise**, **Gestionnaire de projets** ou **Responsable de déploiement** par le biais de l’interface utilisateur [!UICONTROL Cloud Manager] doit approuver manuellement un déploiement.
            * **Planifié** - Arrête le pipeline avant le déploiement en production pour lui permettre d’être planifié. Si cette option est sélectionnée, le pipeline s’arrête après le déploiement dans l’environnement d’évaluation et invite l’utilisateur à effectuer l’action.
               * **`Now`** - Déploie immédiatement en production, achevant ainsi le pipeline.
               * **Date** - Permet à l’utilisateur de planifier une heure à laquelle le déploiement doit être terminé.
               * **Arrêter l’exécution** - Interrompt le déploiement en production.

           >[!TIP]
           >
           >Voir [Déploiement du code](/help/using/code-deployment.md) pour savoir comment définir la planification du déploiement ou exécuter immédiatement le pipeline.

            * **Utiliser la supervision par l’ingénieur du service client** - Si cette option est sélectionnée, un ingénieur du service client est engagé pour démarrer le déploiement réel. Lors de la création ou de la modification d’un pipeline lorsque cette option est activée, le rôle **Responsable de déploiement** dispose des options suivantes.

               * **Tout ingénieur du service client** - Permet à l’ingénieur du service client disponible de démarrer le déploiement.
               * **Mon ingénieur du service client** - Permet uniquement à l’ingénieur du service client spécifique affecté au client de démarrer le déploiement. Cette option s’applique également à la sauvegarde désignée de l’ingénieur du service client si l’ingénieur du service client affecté n’est pas disponible.

           ![Options de déploiement en production](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configuration de Dispatcher** - Définissez la configuration de Dispatcher pour votre environnement de production. Les options sont identiques à celles de l’environnement d’évaluation.

1. Cliquez sur **Continuer** pour passer à l’onglet **Test d’évaluation** où vous pouvez configurer les tests de performance AEM Sites et AEM Assets, en fonction des produits sous licence que vous possédez.

   >[!TIP]
   >
   >Voir [Test de qualité du code](/help/using/code-quality-testing.md#performance-testing) pour plus d’informations sur les options disponibles dans l’onglet **Test d’évaluation**.

   1. Dans la section **Diffusion du contenu des sites/Poids de charge distribué** , vous configurez les tests de performance du site en fonction de la pondération des requêtes de page parmi trois ensembles de pages. Vous pouvez activer ou désactiver les jeux de pages selon vos besoins.

      * **Pages dynamiques populaires**
      * **Autres pages dynamiques**
      * **Nouvelles pages**

      ![Poids de charge des sites](/help/assets/configure-pipelines/add-prod5.png)

   1. Dans la section **Distribution des tests de performance Assets**, vous définissez la distribution des tests des images et des PDF et définissez vos propres ressources de test.

      * **Images** - réglez le curseur pour ajuster la répartition du test entre les images et les PDF.
      * **PDF** - réglez le curseur pour ajuster la répartition du test entre les images et les PDF.

      * Définissez vos propres ressources personnalisées en les chargeant.

         1. **FORMAT** - choisissez si votre ressource personnalisée est un PDF ou une image.
         1. **NOM DE FICHIER** - utilisez le bouton du navigateur de fichiers pour sélectionner une image sur votre ordinateur local.
         1. **Ajouter un fichier test** - cliquez pour charger la ressource sélectionnée.

      ![Distribution des tests des ressources](/help/assets/configure-pipelines/add-prod6.png)

1. Cliquez sur **Enregistrer** pour terminer l’ajout de votre pipeline de production.

## Étapes suivantes {#the-next-steps}

Une fois que vous avez configuré le pipeline, vous déployez votre code. Pour plus d’informations, voir [Déploiement du code](/help/using/code-deployment.md) .

## Tutoriel vidéo {#video-tutorial-one}

Cette vidéo présente un aperçu du processus de création de pipeline, détaillé dans ce document.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)
