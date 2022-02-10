---
title: Configuration des pipelines de production
description: Découvrez comment utiliser Cloud Manager pour créer et configurer des pipelines de production afin de déployer votre code.
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 205113735cc743e11e140b1161413002844f5b79
workflow-type: tm+mt
source-wordcount: '1557'
ht-degree: 18%

---

# Configuration des pipelines de production {#configuring-production-pipelines}

Découvrez comment utiliser Cloud Manager pour créer et configurer des pipelines de production afin de déployer votre code. si vous souhaitez d’abord une présentation plus conceptuelle du fonctionnement des pipelines dans Cloud Manager, reportez-vous à la section [Documentation de présentation du pipeline CI/CD.](ci-cd-pipeline.md)

>[!NOTE]
>
>Pour savoir comment configurer les pipelines CI/CD pour Cloud Manager dans AEM as a Cloud Service, voir [la documentation d’AEMaaCS ;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html#using-cloud-manager)

## Présentation {#understanding-the-flow}

Vous configurez les pipelines à l’aide de la méthode **Paramètres du pipeline** dans la [!UICONTROL Cloud Manager] Interface utilisateur.

Vous pouvez créer deux types de pipelines différents.

* **Pipelines de production** - Un pipeline de production est un pipeline personnalisé constitué d’une série d’étapes orchestrées permettant d’intégrer le code source jusqu’à la production.
* **Pipelines hors production** - Un pipeline hors production sert principalement à exécuter des analyses de qualité du code ou à déployer le code source dans un environnement de développement.

Ce document se concentre sur les pipelines de production. Pour plus d’informations sur la configuration des pipelines hors production, voir le document [Configuration de pipelines hors production.](configuring-non-production-pipelines.md)

Le **Responsable de déploiement** est responsable de la configuration du pipeline. La configuration du pipeline comprend :

1. Définition du déclencheur qui démarrera le pipeline.
1. Définition des paramètres contrôlant le déploiement en production.
1. Configuration des paramètres de test de performance.

>[!NOTE]
>
>Un pipeline ne peut pas être configuré tant que son référentiel git associé ne comporte pas au moins une branche et que [configuration du programme](setting-up-program.md) est terminée.

>[!NOTE]
>
>Vous pouvez modifier les paramètres du pipeline après la configuration initiale.

## Tutoriel vidéo {#video-tutorial-one}

Regardez cette vidéo pour un aperçu du processus de création de pipeline.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## Ajout d’un nouveau pipeline de production {#adding-production-pipeline}

Une fois que vous avez utilisé la variable [!UICONTROL Cloud Manager] L’interface utilisateur pour configurer votre programme et disposer d’au moins un environnement vous permet d’ajouter un pipeline de production.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Pipelines** de la carte **Aperçu du programme** et cliquez sur **+Ajouter** et sélectionnez **Ajout d’un pipeline de production**.

   ![Ajout d’un pipeline de production](/help/using/assets/configure-pipelines/add-prod1.png)

1. Le **Ajout d’un pipeline de production** s’ouvre sur la boîte de dialogue **Configuration** où plusieurs options de votre pipeline doivent être définies. Ces options sont regroupées en sections réductibles et sont décrites dans les étapes suivantes.

   1. Attribuez un nom explicite à votre pipeline dans la variable **Nom du pipeline** champ .

   1. Sous , **Code source** , vous définissez l’emplacement où le pipeline récupère le code qu’il traitera.

      * **Référentiel** - Cette option définit à partir de quel référentiel git le pipeline doit récupérer le code.
      >[!TIP]
      >
      >Voir le document [Configuration de votre programme](setting-up-program.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

      * **Branche Git** - Cette option définit à partir de quelle branche du pipeline sélectionné doit récupérer le code.
      * **Emplacement du code** - Cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.

      ![Définition des référentiels pour le pipeline](/help/using/assets/configure-pipelines/add-prod2.png)

   1. Sous , **Environnements** , vous définissez ce qui déclenche un déploiement et comment il doit être déployé par environnement.

      1. Dans le **ÉTAPE** , vous pouvez définir la manière dont le pipeline se déploie vers votre environnement d’évaluation.

         * **Déclencheur de déploiement** - Vous disposez des options suivantes pour définir les déclencheurs de déploiement pour démarrer le pipeline.

            * **Manuel** - Utilisez cette option pour démarrer manuellement le pipeline à l’aide de l’interface utilisateur de Cloud Manager.
            * **Lors des modifications Git** - Cette option démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.
         * **Comportement des échecs de mesure importants** - Lors de la configuration ou de la modification du pipeline, le responsable de déploiement a la possibilité de définir le comportement du pipeline en cas d’échec important dans l’un des points de contrôle qualité. Les options disponibles sont les suivantes :

            * **Demander à chaque fois** - Il s’agit du paramètre par défaut qui nécessite une intervention manuelle en cas d’échec important.
            * **Échec immédiat** - Si cette option est sélectionnée, le pipeline est annulé chaque fois qu’un échec important se produit. Cette option émule essentiellement un utilisateur rejetant manuellement chaque échec.
            * **Continuer immédiatement** - Si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Cette option émule essentiellement la validation manuelle de l’utilisateur à chaque échec.

         ![Déclencheur de déploiement](/help/using/assets/configure-pipelines/add-prod3.png)

         * **Options de déploiement** - Vous pouvez accélérer certaines tâches de déploiement.

            * **Approbation après déploiement dans l’environnement intermédiaire** - Cette approbation a lieu après le déploiement dans l’environnement d’évaluation avant que les tests ne soient effectués. Sinon, l’approbation se produit avant le déploiement en production, qui est effectué une fois tous les tests terminés.

            * **Ignorer les modifications de l’équilibreur de charge** - Les modifications de l’équilibreur de charge ne sont pas effectuées.

         ![Options de déploiement intermédiaire](/help/using/assets/configure-pipelines/add-prod4.png)

         * **Configuration de Dispatcher** - Le **Responsable de déploiement** Le rôle peut configurer un ensemble de chemins de contenu qui seront invalidés ou purgés du cache de Dispatcher AEM lorsqu’un pipeline est exécuté. Ces actions de cache seront effectuées dans le cadre de l’étape du pipeline de déploiement, juste après le déploiement des packages de contenu. Ces paramètres utilisent le comportement standard AEM Dispatcher. Pour configurer :

            1. Sous **CHEMIN** fournissez un chemin d’accès au contenu.
            1. Sous **TYPE**, sélectionnez l’action à effectuer sur ce chemin.
            * **Purge** - Effectuez une invalidation du cache, comme lorsque le contenu est activé d’une instance de création vers une instance de publication.
            * **Invalider** - Effectue une suppression du cache.
            1. Cliquez sur **Ajouter un chemin** pour ajouter le chemin spécifié. Vous pouvez ajouter jusqu’à 100 chemins par environnement.

         ![Configuration du Dispatcher](/help/using/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >En règle générale, l’utilisation de l’action d’invalidation est préférable, mais il peut arriver que la purge soit requise, en particulier lors de l’utilisation AEM bibliothèques clientes HTML.

      1. Dans le **PRODUCTION** , vous pouvez définir la manière dont le pipeline se déploie vers votre environnement de production.

         * **Options de déploiement** - Vous pouvez définir les paramètres contrôlant le déploiement en production.

            * **Utiliser l’approbation GoLive** - Un déploiement doit être approuvé manuellement par un utilisateur disposant de la fonction **Propriétaire de l’entreprise**, **Chef de projet** ou **Responsable de déploiement** via le [!UICONTROL Cloud Manager] Interface utilisateur.
            * **Planifié** - Cette option interrompt le pipeline avant le déploiement en production pour permettre sa planification. Si cette option est sélectionnée, le pipeline s’arrête après le déploiement dans l’environnement d’évaluation et invite l’utilisateur à effectuer l’action.
               * **Maintenant** - Cette option se déploie immédiatement en production, ce qui permet d’achever le pipeline.
               * **Date** - Cette option permet à l’utilisateur de planifier une heure à laquelle le déploiement doit être terminé.
               * **Arrêter l’exécution** - Cette option annule le déploiement en production.

            >[!TIP]
            >
            >Reportez-vous au document [Déployez votre code,](deploying-code.md) pour savoir comment définir la planification du déploiement ou exécuter immédiatement le pipeline.

            * **Utiliser la supervision par l&#39;ingénieur du service client** - Si cette option est sélectionnée, un ingénieur du service client est engagé pour démarrer le déploiement. Lors de la création ou de la modification d’un pipeline lorsque cette option est activée, la variable **Responsable de déploiement** possède les options suivantes.

               * **Tout ingénieur du service client** - Cette option permet à tout ingénieur du service client disponible de démarrer le déploiement.
               * **Mon ingénieur du service client** - Cette option permet uniquement à l’ingénieur du service client spécifique affecté au client de démarrer le déploiement. Cela s’applique également à la sauvegarde désignée de l’ingénieur du service client si l’ingénieur du service client affecté n’est pas disponible.

            ![Options de déploiement en production](/help/using/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configuration de Dispatcher** - Définissez la configuration du Dispatcher pour votre environnement de production. Les options sont identiques à celles de l’environnement d’évaluation.











1. Cliquez sur **Continuer** pour accéder au **Test d’évaluation** dans lequel vous pouvez configurer les tests de performance AEM Sites et AEM Assets, en fonction des produits sous licence que vous possédez.

   >[!TIP]
   >
   >Reportez-vous au document [Présentation des résultats de test](understand-your-test-results.md#performance-testing) pour plus d’informations sur les options disponibles dans la section **Test d’évaluation** .

   1. Sous , **Diffusion de contenu/poids de charge distribué des sites** , vous définissez comment les tests de performances des sites sont configurés en fonction de la pondération des requêtes de page entre les trois ensembles de pages, qui peuvent être activés ou désactivés.

      * **Pages dynamiques populaires**
      * **Autres pages dynamiques**
      * **Nouvelles pages**

      ![Poids de charge des sites](/help/using/assets/configure-pipelines/add-prod5.png)

   1. Sous , **Distribution des tests de performance des ressources** , vous définissez la distribution de test des images et des PDF ainsi que vos propres ressources de test.

      * **Images** - Réglez le curseur pour ajuster la division du test entre les images et les PDF.
      * **PDF** - Réglez le curseur pour ajuster la division du test entre les images et les PDF.

      * Définissez vos propres ressources personnalisées en les chargeant.

         1. **FORMAT** - Indiquez si votre ressource personnalisée est un PDF d’image.
         1. **FILENAME** - Utilisez le bouton de navigateur de fichiers pour sélectionner une image sur votre ordinateur local.
         1. **Ajouter un fichier test** - Cliquez sur pour charger la ressource sélectionnée.

      ![Distribution des tests de ressources](/help/using/assets/configure-pipelines/add-prod6.png)



1. Cliquez sur **Enregistrer** pour terminer l’ajout de votre pipeline de production.














### Modification d’un pipeline de production {#editing-prod-pipeline}

Vous pouvez modifier les configurations de pipeline à partir de la page **Aperçu du programme**.

Pour modifier la configuration du pipeline, procédez comme suit :

1. Accédez à la carte **Pipelines** à partir de votre page **Aperçu du programme**.

1. Cliquez sur **...** dans la carte **Pipelines** et cliquez sur **Modifier**, comme illustré dans l’image ci-dessous.

   ![](/help/using/assets/configure-pipelines/edit-prod1.png)

1. La boîte de dialogue **Modifier le pipeline de production** s’affiche.

   1. L’onglet **Configuration** vous permet de mettre à jour le **Nom du pipeline**, le **Référentiel**, la **Branche Git**, le **Déclencheur de déploiement**, le **Comportement en cas d’échec de mesure grave**, les **Options de déploiement** et les **Configurations du Dispatcher**.

      >[!NOTE]
      >Consultez [Ajout et gestion des référentiels](/help/using/cloud-manager-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.


   1. L’onglet de **Test dans l’environnement intermédiaire** vous offre la possibilité de sélectionner à nouveau les options dans **Diffusion de contenu de sites/poids de la charge distribuée** et **Distribution des tests de performance des ressources**.

1. Cliquez sur **Mettre à jour** une fois que vous avez terminé de modifier le pipeline.

### Autres actions de pipeline de production {#additional-prod-actions}

#### Exécution d’un pipeline de production {#run-prod}

Vous pouvez exécuter le pipeline de production à partir de la carte Pipelines :

1. Accédez à la carte **Pipelines** à partir de votre page **Aperçu du programme**.

1. Cliquez sur **...** dans la carte **Pipelines** et cliquez sur **Exécuter**, comme illustré dans l’image ci-dessous.

   ![](/help/using/assets/configure-pipelines/prod-run.png)

#### Suppression d’un pipeline de production {#delete-prod}

Vous pouvez supprimer le pipeline de production de la carte Pipelines :

1. Accédez à la carte **Pipelines** à partir de votre page **Aperçu du programme**.

1. Cliquez sur **...** dans la carte **Pipelines** et cliquez sur **Supprimer**, comme illustré dans l’image ci-dessous.

   ![](/help/using/assets/configure-pipelines/prod-delete.png)

   >[!NOTE]
   >Un utilisateur disposant du rôle Gestionnaire de déploiement peut désormais supprimer le pipeline de production en libre-service grâce à l’option **Supprimer** de la carte Pipeline.

