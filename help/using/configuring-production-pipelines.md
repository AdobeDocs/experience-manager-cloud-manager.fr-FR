---
title: Configurer des pipelines de production
description: Découvrez comment utiliser Cloud Manager pour créer et configurer des pipelines de production afin de déployer votre code.
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 205113735cc743e11e140b1161413002844f5b79
workflow-type: ht
source-wordcount: '1557'
ht-degree: 100%

---

# Configurer des pipelines de production {#configuring-production-pipelines}

Découvrez comment utiliser Cloud Manager pour créer et configurer des pipelines de production afin de déployer votre code. si vous souhaitez d’abord une présentation plus conceptuelle du fonctionnement des pipelines dans Cloud Manager, reportez-vous à la [Documentation de présentation des pipelines CI/CD.](ci-cd-pipeline.md)

>[!NOTE]
>
>Pour savoir comment configurer les pipelines CI/CD pour Cloud Manager dans AEM as a Cloud Service, consultez [la documentation AEMaaCS.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=fr#using-cloud-manager)

## Présentation {#understanding-the-flow}

Vous configurez les pipelines à partir de la mosaïque **Paramètres du pipeline** dans l’interface utilisateur de [!UICONTROL Cloud Manager].

Vous pouvez créer deux types de pipelines différents.

* **Pipelines de production** - un pipeline de production est un pipeline spécialement conçu, composé d’une série d’étapes coordonnées permettant de mener le code source jusqu’à la production.
* **Pipelines hors production** - un pipeline hors production sert principalement à exécuter des analyses de qualité du code ou à déployer le code source dans un environnement de développement.

Ce document se concentre sur les pipelines de production. Pour plus d’informations sur la configuration des pipelines hors production, voir le document [Configuration de pipelines hors production.](configuring-non-production-pipelines.md)

Le rôle du **responsable du déploiement** : il est chargé de la configuration du pipeline. La configuration du pipeline comprend :

1. La définition du déclencheur qui démarrera le pipeline ;
1. La définition des paramètres qui contrôlent le déploiement en production ;
1. La configuration des paramètres de test de performance.

>[!NOTE]
>
>Un pipeline ne peut être configuré que si le référentiel Git qui lui est associé dispose d’au moins une branche et que la [configuration du programme](setting-up-program.md) est terminée.

>[!NOTE]
>
>Vous pouvez modifier les paramètres du pipeline après la configuration initiale.

## Tutoriel vidéo {#video-tutorial-one}

Regardez cette vidéo pour un aperçu du processus de création de pipeline.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## Ajouter un nouveau pipeline de production {#adding-production-pipeline}

Une fois que vous avez utilisé l’interface utilisateur [!UICONTROL Cloud Manager] pour configurer votre programme et que vous disposez d’au moins un environnement, vous êtes prêt à ajouter un pipeline de production.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la vignette **Pipelines** de la page **Aperçu du programme**, cliquez sur **+Ajouter** et sélectionnez **Ajout d’un pipeline de production**.

   ![Ajout d’un pipeline de production](/help/using/assets/configure-pipelines/add-prod1.png)

1. La boîte de dialogue **Ajout d’un pipeline de production** s’ouvre sur l’onglet de **Configuration** où plusieurs options de votre pipeline doivent être définies. Ces options sont regroupées en sections réductibles et sont décrites dans les étapes suivantes.

   1. Attribuez un nom explicite à votre pipeline dans le champ **Nom du pipeline**.

   1. Sous la section **Code source**, définissez où le pipeline récupère le code qu’il traitera.

      * **Référentiel** - cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.
      >[!TIP]
      >
      >Voir le document [Configuration de votre programme](setting-up-program.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

      * **Branche Git** - cette option définit à partir de quelle branche sélectionnée le pipeline doit récupérer le code.
      * **Emplacement du code** - cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.

      ![Définition des référentiels pour le pipeline](/help/using/assets/configure-pipelines/add-prod2.png)

   1. Sous la section **Environnements**, vous définissez ce qui déclenche un déploiement et comment il doit être déployé par environnement.

      1. Dans la section **ÉTAPE**, vous pouvez définir la manière dont le pipeline se déploie vers votre environnement d’évaluation.

         * **Déclencheur de déploiement** - vous disposez des options suivantes pour définir les déclencheurs de déploiement pour démarrer le pipeline.

            * **Manuel** - utilisez cette option pour démarrer manuellement le pipeline à l’aide de l’interface utilisateur de Cloud Manager.
            * **Lors des modifications Git** - cette option démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.
         * **Comportement en cas d’échecs de mesure importants** - lors de la configuration ou de la modification du pipeline, le responsable de déploiement peut définir le comportement du pipeline lorsqu&#39;un échec important est rencontré à l’un des points de contrôle qualité. Les options disponibles sont les suivantes :

            * **Demander à chaque fois** - il s’agit du paramètre par défaut qui nécessite une intervention manuelle pour tout échec important.
            * **Défaillance immédiate** : si cette option est sélectionnée, le pipeline sera interrompu chaque fois qu’une défaillance importante aura lieu. Il s’agit essentiellement d’imiter un utilisateur qui rejetterait manuellement chaque échec.
            * **Continuer immédiatement** - si cette option est sélectionnée, le pipeline se poursuivra automatiquement chaque fois qu’une défaillance importante se produira. Il s&#39;agit essentiellement d&#39;émuler un utilisateur approuvant manuellement chaque échec.

         ![Déclencheur de déploiement](/help/using/assets/configure-pipelines/add-prod3.png)

         * **Options de déploiement** - vous pouvez accélérer certaines tâches de déploiement.

            * **Approbation après le déploiement d’évaluation** - cette approbation a lieu après le déploiement dans l’environnement d’évaluation avant que tout test ne soit effectué. Sinon, l’approbation se produit avant le déploiement en production, qui est effectué une fois tous les tests terminés.

            * **Ignorer les modifications de la répartition de charge** - Les modifications de la répartition de charge ne sont pas effectuées.

         ![Options de déploiement intermédiaire](/help/using/assets/configure-pipelines/add-prod4.png)

         * **Configuration de Dispatcher** - Le rôle du **responsable de déploiement** consiste à configurer un ensemble de chemins de contenu qui seront soit invalidés soit vidés du cache d’AEM Dispatcher lorsqu’un pipeline est exécuté. Ces actions de cache sont exécutées dans le cadre de l’étape du pipeline de déploiement, juste après le déploiement des packages de contenu. Ces paramètres utilisent le comportement standard d’AEM Dispatcher. Pour configurer :

            1. Sous **CHEMIN**, fournissez un chemin d’accès au contenu.
            1. Sous **TYPE**, sélectionnez l’action à effectuer sur ce chemin.
            * **Purge** - effectuez une invalidation du cache, comme lorsque le contenu est activé d’une instance de création vers une instance de publication.
            * **Invalider** - effectue une suppression du cache.
            1. Cliquez sur **Ajouter un chemin** pour ajouter votre chemin spécifié. Vous pouvez ajouter jusqu’à 100 chemins par environnement.

         ![Configuration de Dispatcher](/help/using/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >En règle générale, l’utilisation de l’action Invalider est préférable, mais il peut y avoir des cas où la purge est nécessaire, notamment lors de l’utilisation des bibliothèques clientes HTML d’AEM.

      1. Dans la section **PRODUCTION**, vous pouvez définir la manière dont le pipeline se déploie dans votre environnement de production.

         * **Options de déploiement** - vous pouvez définir les paramètres contrôlant le déploiement en production.

            * **Utiliser l’approbation GoLive** - un déploiement doit être approuvé manuellement par un utilisateur ayant le rôle de **propriétaire d’entreprise**, **chef de projet** ou **responsable de déploiement** via l’interface utilisateur [!UICONTROL Cloud Manager].
            * **Planifié** - Cette option interrompt le pipeline avant le déploiement en production pour permettre sa planification. Si cette option est sélectionnée, le pipeline s’arrêtera après le déploiement dans l’environnement d’évaluation et demandera à l’utilisateur l’action à entreprendre.
               * **Maintenant** - cette option permet de déployer immédiatement en production, terminant ainsi le pipeline.
               * **Date** - cette option permet à l’utilisateur de planifier une heure à laquelle le déploiement doit être terminé.
               * **Arrêter l’exécution** - cette option interrompt le déploiement en production.

            >[!TIP]
            >
            >Référez-vous au document [Déployer votre code](deploying-code.md), pour savoir comment définir la planification du déploiement ou exécuter le pipeline immédiatement.

            * **Solliciter la supervision de l’ingénieur support client (CSE)** - si cette option est choisie, un CSE est engagé pour véritablement démarrer le déploiement. Lors de la création ou de la modification d’un pipeline lorsque cette option est activée, le rôle **Responsable de déploiement** dispose des options suivantes.

               * **N’importe quel CSE** - cette option permet à tout CSE disponible de démarrer le déploiement.
               * **Mon CSE** - Cette option permet uniquement au CSE spécifique affecté au client de démarrer le déploiement. Cela s’applique également au remplaçant désigné du CSE si le CSE attribué est indisponible.

            ![Options de déploiement en production](/help/using/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configuration de Dispatcher** - définissez la configuration de Dispatcher pour votre environnement de production. Les options sont identiques à celles de l’environnement d’évaluation.











1. Cliquez sur **Continuer** pour accéder à l’onglet **Tests d’évaluation** où vous pouvez configurer les tests de performance d’AEM Sites et d’AEM Assets, en fonction des produits sous licence que vous possédez.

   >[!TIP]
   >
   >Reportez-vous au document [Comprendre les résultats de vos tests](understand-your-test-results.md#performance-testing) pour plus d’informations sur les options disponibles dans l’onglet **Test d’évaluation**.

   1. Sous la section **Diffusion du contenu des sites/Poids de charge distribué**, vous définissez comment le test de performance des sites est configuré en fonction de la pondération des requêtes de page entre les trois ensembles de pages, qui peuvent être activés ou désactivés.

      * **Pages dynamiques populaires**
      * **Autres pages dynamiques**
      * **Nouvelles pages**

      ![Poids de charge des sites](/help/using/assets/configure-pipelines/add-prod5.png)

   1. Sous la section **Distribution des tests de performance des ressources**, vous définissez la distribution de test des images et des PDF ainsi que la définition de vos propres ressources de test.

      * **Images** - réglez le curseur pour ajuster la répartition du test entre les images et les PDF.
      * **PDF** - réglez le curseur pour ajuster la répartition du test entre les images et les PDF.

      * Définissez vos propres ressources personnalisées en les chargeant.

         1. **FORMAT** - choisissez si votre ressource personnalisée est un PDF ou une image.
         1. **NOM DE FICHIER** - utilisez le bouton du navigateur de fichiers pour sélectionner une image sur votre ordinateur local.
         1. **Ajouter un fichier test** - cliquez pour charger la ressource sélectionnée.

      ![Distribution des tests des ressources](/help/using/assets/configure-pipelines/add-prod6.png)



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

