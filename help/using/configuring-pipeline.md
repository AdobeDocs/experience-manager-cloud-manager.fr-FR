---
title: Configuration de votre pipeline CI/CD
seo-title: Configure your CI/CD Pipeline
description: Consultez cette page pour configurer les paramètres de votre pipeline depuis Cloud Manager.
seo-description: Before you start to deploy your code, you must configure your pipeline settings from the AEM Cloud Manager.
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 2be8f290b58fff2991f876c37dd1b499bc6c5352
workflow-type: tm+mt
source-wordcount: '1842'
ht-degree: 100%

---

# Configuration de votre pipeline CI/CD {#configure-your-ci-cd-pipeline}

>[!NOTE]
>Pour savoir comment configurer le pipeline CI/CD pour Cloud Manager dans AEM as a Cloud Service, consultez [ce lien](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=fr#using-cloud-manager).

La page suivante explique comment configurer le **pipeline**. Pour consulter d’autres informations conceptuelles sur le fonctionnement du pipeline, voir la section [Présentation du pipeline CI/CD](ci-cd-pipeline.md).


## Présentation du flux {#understanding-the-flow}

Vous pouvez configurer votre pipeline à partir de la vignette **Paramètres du pipeline** dans l’interface utilisateur de [!UICONTROL Cloud Manager].

Le responsable de déploiement est chargé de la configuration du pipeline. Pour ce faire, vous devez d’abord sélectionner une branche dans le **référentiel git**. La configuration du pipeline comprend :

* la définition du déclencheur qui le démarrera ;
* la définition des paramètres qui contrôlent le déploiement en production ;
* la configuration des paramètres de test de performance.

## Tutoriel vidéo {#video-tutorial-one}

### Configuration du pipeline dans Cloud Manager {#config-pipeline-video}

La configuration du pipeline de production CI/CD définit le déclencheur qui lancera le pipeline, les paramètres contrôlant le déploiement en production et les paramètres de test de performances.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## Configuration du pipeline {#setting-up-the-pipeline}

>[!CAUTION]
>
>Le pipeline ne peut être configuré que si le référentiel Git dispose d’au moins une branche et que la [configuration du programme](setting-up-program.md) est terminée.

Avant de commencer le déploiement du code, vous devez configurer les paramètres de votre pipeline à partir de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Vous pouvez modifier les paramètres du pipeline après la configuration initiale.

### Ajout d’un nouveau pipeline de production à partir de la carte Pipelines {#adding-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez au moins d’un environnement basé sur l’interface utilisateur de [!UICONTROL Cloud Manager], vous êtes prêt à ajouter un pipeline de production.

Pour configurer le comportement et les préférences de votre pipeline de production, procédez comme suit :

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Cliquez sur **+Ajouter** et sélectionnez **Ajouter un pipeline de production**.

   ![](/help/using/assets/configure-pipelines/add-prod1.png)

1. La boîte de dialogue **Ajouter un pipeline de production** s’affiche.

   1. Saisissez le **Nom du pipeline**. Vous pouvez choisir le **Référentiel** et la **Branche Git**.

      ![](/help/using/assets/configure-pipelines/add-prod2.png)

   1. Vous pouvez configurer le **Déclencheur de déploiement** et le **Comportement en cas d’échec de mesure grave** à partir des **Options de déploiement**.

      ![](/help/using/assets/configure-pipelines/add-prod3.png)


      Vous pouvez affecter les déclencheurs de déploiement suivants au démarrage du pipeline :

      * **Manuel** : l’utilisation de l’interface lance le pipeline manuellement.
      * **Lors des modifications Git** : démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche git configurée. Même si vous sélectionnez cette option, vous pouvez toujours démarrer le pipeline manuellement.

      Lors de la configuration ou de la modification du pipeline, le responsable de déploiement peut définir le comportement du pipeline en cas d’échec important à l’un des points de contrôle qualité.

      Cela s’avère utile pour les clients qui souhaitent davantage de processus automatisés. Les options disponibles sont les suivantes :

      * **Demander à chaque fois** : il s’agit du paramètre par défaut, qui nécessite une intervention manuelle lors de n’importe quel échec important.
      * **Annuler immédiatement en cas d’échec** : si cette option est sélectionnée, le pipeline sera annulé chaque fois qu’un échec important se produira. Cette option émule essentiellement un utilisateur rejetant manuellement chaque échec.
      * **Continuer immédiatement** : si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Cette option émule essentiellement la validation manuelle de l’utilisateur à chaque échec.
   1. Sélectionnez les **Options de déploiement**.

      ![](/help/using/assets/configure-pipelines/add-prod4.png)

      * Les fonctions **Approuver après le déploiement dans l’environnement d’évaluation** fonctionnent de la même manière que l’approbation avant le déploiement en production, mais ce processus se produit immédiatement après l’étape de déploiement dans l’environnement intermédiaire, c’est-à-dire avant que les tests ne soient effectués, contrairement à l’approbation avant le déploiement en production, qui est effectuée une fois tous les tests terminés.

      * **Ignorer les modifications de la répartition de charge** ignore les modifications.
   1. Sélectionnez la **Configuration du Dispatcher** pour l’environnement intermédiaire. Saisissez le chemin d’accès, sélectionnez l’action dans **Type**, puis cliquez sur **Ajouter un chemin**. Vous pouvez spécifier jusqu’à 100 chemins par environnement.

      ![](/help/using/assets/configure-pipelines/dispatcher-stage.png)

   1. Sélectionnez les **Options de déploiement** pour la production. Définissez maintenant les paramètres contrôlant le déploiement en production.

      ![](/help/using/assets/configure-pipelines/prod-deploymentoptions.png)

      Les trois options disponibles sont les suivantes :

      * **Utiliser l’approbation GoLive** : un déploiement doit être approuvé manuellement par un propriétaire d’entreprise, un responsable de projet ou un responsable de déploiement via l’interface utilisateur [!UICONTROL Cloud Manager].

      * **Planifié** : cette option permet à l’utilisateur d’activer le déploiement en production planifié.

         >[!NOTE]
         >Si l’option **Planifié** est sélectionnée, vous pouvez planifier le déploiement en production sur le pipeline **après** le déploiement en environnement intermédiaire (et **Utiliser l’approbation GoLive**, si cette option a été activée) pour attendre la définition d’une planification. L’utilisateur peut également choisir d’exécuter le déploiement en production immédiatement.
         >
         >Consultez [Déploiement de votre code](deploying-code.md) pour définir la planification du déploiement ou exécuter la production immédiatement.

         * **Utiliser la supervision par l’ingénieur du service client** : un ingénieur du service client participe au démarrage du déploiement. Lors de la configuration ou de la modification du pipeline lorsque la supervision par l’ingénieur du service client est activée, le responsable de déploiement peut sélectionner l’une des options suivantes :

            * **Tout ingénieur du service client** : fait référence à tout ingénieur du service client disponible.
            * **Mon ingénieur du service client** : fait référence à un ingénieur du service client spécifique affecté au client ou un remplaçant, si l’ingénieur du service client est absent du bureau.
   1. Paramétrez les **Configurations du Dispatcher** pour la production. Saisissez le chemin d’accès, sélectionnez l’action dans **Type**, puis cliquez sur **Ajouter un chemin**. Vous pouvez spécifier jusqu’à 100 chemins par environnement.

      ![](/help/using/assets/configure-pipelines/dispatcher-prod.png)

      En tant que responsable de déploiement, vous avez la possibilité de configurer un ensemble de chemins de contenu qui seront **invalidés** ou **purgés** du cache du Dispatcher AEM des instances de publication, lors de la configuration ou de la modification du pipeline.

      Vous pouvez configurer un ensemble distinct de chemins pour le déploiement Intermédiaire et Production. Si elles sont configurées, ces actions de cache sont exécutées dans le cadre de l’étape du pipeline de déploiement, juste après le déploiement des packages de contenu. Ces paramètres utilisent le comportement du Dispatcher AEM standard : invalider effectue une invalidation du cache, comme lorsque le contenu est activé d’Author vers Publish ; purger effectue une suppression de cache.

      En règle générale, l’utilisation de l’action invalider est préférable mais il se peut que la purge soit requise, notamment lors de l’utilisation des bibliothèques clients HTML AEM.

      >[!NOTE]
      >
      >Pour plus d’informations sur la mise en cache du Dispatcher, consultez [Présentation du Dispatcher](dispatcher-configurations.md).





1. Cliquez sur **Continuer** une fois que vous avez sélectionné toutes les options.

1. Sélectionnez vos options au cours de l’étape de **Test dans l’environnement intermédiaire**. Vous pouvez configurer des tests de performance *AEM Sites* et *AEM Assets*, selon les produits sous licence que vous possédez. Pour plus d’informations, consultez [Tests de performance](understand-your-test-results.md#performance-testing).

   1. Sélectionnez vos options dans **Diffusion de contenu de sites/poids de la charge distribuée**. Consultez [AEM Sites en test de performance](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=fr#aem-sites) pour plus d’informations.

      ![](/help/using/assets/configure-pipelines/add-prod5.png)

   1. Sélectionnez vos options dans **Distribution des tests de performance des ressources**. Consultez [AEM Assets en test de performance](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=fr#aem-assets) pour plus d’informations.

      ![](/help/using/assets/configure-pipelines/add-prod6.png)

1. Cliquez sur **Enregistrer** pour terminer l’ajout du pipeline de production.

### Modification d’un pipeline de production {#editing-prod-pipeline}

Vous pouvez modifier les configurations de pipeline à partir de la page **Aperçu du programme**.

Pour modifier le pipeline configuré, procédez comme suit :

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Cliquez sur **...** dans la carte **Pipelines** et cliquez sur **Modifier**, comme illustré ci-dessous.

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

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Cliquez sur **...** dans la carte **Pipelines** et cliquez sur **Exécuter**, comme illustré ci-dessous.

   ![](/help/using/assets/configure-pipelines/prod-run.png)

#### Suppression d’un pipeline de production {#delete-prod}

Vous pouvez supprimer le pipeline de production de la carte Pipelines :

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Cliquez sur **...** dans la carte **Pipelines** et cliquez sur **Supprimer**, comme illustré ci-dessous.

   ![](/help/using/assets/configure-pipelines/prod-delete.png)

   >[!NOTE]
   >Un utilisateur disposant du rôle Gestionnaire de déploiement peut désormais supprimer le pipeline de production en libre-service via l’option **Supprimer** de la carte Pipeline.

## Pipelines de qualité de code et hors production uniquement

En plus du pipeline principal qui se déploie vers les environnements intermédiaire et de production, les clients peuvent configurer des pipelines supplémentaires, appelés **Pipelines hors production**. Ces pipelines exécutent toujours les étapes de génération et de qualité de code. Si besoin est, elles peuvent aussi déployer vers l’environnement Adobe Managed Services.

## Tutoriel vidéo {#video-tutorial-two}

### Pipelines hors production et de la qualité du code uniquement de Cloud Manager {#non-prod-video}

Les pipelines CI/CD hors production sont divisés en deux catégories : les pipelines de qualité du code et les pipelines de déploiement. Les pipelines de qualité du code canalisent tout le code d’une branche Git pour génération et évaluation par rapport à l’analyse de la qualité du code de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

### Ajout d’un pipeline hors production {#add-non-production-pipeline}

Sur l’écran d’accueil, ces pipelines sont répertoriés dans une nouvelle carte :

1. Accédez à la carte **Pipelines** à partir de l’écran d’accueil de Cloud Manager. Cliquez sur **+Ajouter** et sélectionnez **Ajouter un pipeline hors production**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. La boîte de dialogue **Ajouter un pipeline hors production** s’affiche. Sélectionnez le type de pipeline que vous souhaitez créer, au choix : **Pipeline de la qualité du code** ou **Pipeline de déploiement**.

   Vous pouvez également configurer le **Déclencheur de déploiement** et le **Comportement en cas d’échec de mesure grave** à partir des **Options de déploiement**. Cliquez sur **Continuer**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add2.png)


1. Le nouveau pipeline hors production s’affiche désormais dans la variable carte **Pipelines**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add4.png)


   Le pipeline s’affiche sur la carte de l’écran d’accueil avec trois actions, comme illustré ci-dessous :

   * **Ajouter** : permet d’ajouter un nouveau pipeline.
   * **Accéder aux informations sur le référentiel** : permet à l’utilisateur d’obtenir les informations nécessaires pour accéder au référentiel Git de Cloud Manager.
   * **En savoir plus** : suivez ce lien pour en savoir plus sur les ressources de documentation du pipeline CI/CD.

### Modification d’un pipeline hors production {#editing-nonprod-pipeline}

Vous pouvez modifier les configurations de pipeline à partir de la **Carte Pipelines** de la page d’**Aperçu du programme**.

Suivez les étapes ci-dessous pour modifier le pipeline hors production configuré :

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Sélectionnez le pipeline hors production et cliquez sur **...**. Cliquez sur **Modifier** comme illustré dans la figure ci-dessous.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit1.png)

1. La boîte de dialogue **Modifier le pipeline de production** vous permet de mettre à jour le **Nom du pipeline**, le **Référentiel**, la **Branche Git**, le **Déclencheur de déploiement** et le **Comportement en cas d’échec de mesure grave**.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit2.png)

   >[!NOTE]
   >Consultez [Ajout et gestion des référentiels](/help/using/cloud-manager-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

   Vous pouvez affecter les déclencheurs de déploiement suivants au démarrage du pipeline :

   * **Manuel** : l’utilisation de l’interface lance le pipeline manuellement.
   * **Lors des modifications Git** : démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche git configurée. Même si vous sélectionnez cette option, vous pouvez toujours démarrer le pipeline manuellement.

   Lors de la configuration ou de la modification du pipeline, le responsable de déploiement peut définir le comportement du pipeline en cas d’échec important à l’un des points de contrôle qualité. Cela s’avère utile pour les clients qui souhaitent davantage de processus automatisés. Les options disponibles sont les suivantes :

   * **Demander à chaque fois** : il s’agit du paramètre par défaut, qui nécessite une intervention manuelle lors de n’importe quel échec important.
   * **Annuler immédiatement en cas d’échec** : si cette option est sélectionnée, le pipeline sera annulé chaque fois qu’un échec important se produira. Cette option émule essentiellement un utilisateur rejetant manuellement chaque échec.
   * **Continuer immédiatement** : si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Cette option émule essentiellement la validation manuelle de l’utilisateur à chaque échec.


1. Cliquez sur **Mettre à jour** une fois terminée la modification du pipeline hors production.

### Autres actions de pipeline hors production {#additional-nonprod-actions}

#### Exécution d’un pipeline hors production {#run-nonprod}

Vous pouvez exécuter le pipeline de production à partir de la carte Pipelines :

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Cliquez sur **...** dans la carte **Pipelines** et cliquez sur **Exécuter**, comme illustré ci-dessous.

   ![](/help/using/assets/configure-pipelines/nonprod-run1.png)

#### Suppression d’un pipeline hors production {#delete-nonprod}

Vous pouvez supprimer le pipeline de production de la carte Pipelines :

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Cliquez sur **...** dans la carte **Pipelines** et cliquez sur **Supprimer**, comme illustré ci-dessous.

   ![](/help/using/assets/configure-pipelines/nonprod-delete.png)


## Étapes suivantes {#the-next-steps}

Une fois que vous avez configuré le pipeline, vous devez déployer votre code.

Pour plus d’informations, consultez [Déploiement de votre code](deploying-code.md).
