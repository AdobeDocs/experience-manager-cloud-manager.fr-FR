---
title: Ajout d’un pipeline de production
description: Découvrez comment créer et configurer des pipelines de production à l’aide de Cloud Manager afin de déployer votre code.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
TQID: https://experienceleague.adobe.com/WH6W8bZNCWo0BAGLwnMOPpB3bk5P6Fd7c5b-dRT5Vc0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: badb64b816e83ca08a39b2b39eda13335f6a3c1d
workflow-type: tm+mt
source-wordcount: 1665
ht-degree: 73%

---

# Ajout d’un pipeline de production {#configuring-production-pipelines}

Découvrez comment créer et configurer des pipelines de production à l’aide de Cloud Manager afin de déployer votre code. Si vous souhaitez d’abord obtenir une vue d’ensemble plus conceptuelle du fonctionnement des pipelines dans Cloud Manager, reportez-vous au document [Pipelines CI/CD](/help/overview/ci-cd-pipelines.md).

## Vue d’ensemble {#overview}

En utilisant le volet **Paramètres du pipeline** dans [!UICONTROL Cloud Manager], vous pouvez créer deux types de pipelines différents.

* **Pipelines de production** : un pipeline de production est un pipeline spécialement conçu, composé d’une série d’étapes coordonnées pour mener le code source depuis le référentiel Git jusqu’à la production.
* **Pipelines hors production** - un pipeline hors production sert principalement à exécuter des analyses de qualité du code ou à déployer le code source dans un environnement de développement.

Ce document se concentre sur les pipelines de production. Pour plus d’informations sur la configuration des pipelines hors production, voir le document [Configurer des pipelines hors production](/help/using/non-production-pipelines.md).

Le rôle du **responsable du déploiement** : il est chargé de la configuration du pipeline. La configuration du pipeline comprend :

1. la définition du déclencheur qui démarrera le pipeline ;
1. La définition des paramètres qui contrôlent le déploiement en production ;
1. La configuration des paramètres de test de performance.

>[!NOTE]
>
>Un pipeline ne peut être configuré que si le référentiel Git qui lui est associé dispose d’au moins une branche et que la [configuration du programme](/help/getting-started/program-setup.md) est terminée.

## Ajouter un nouveau pipeline de production {#adding-production-pipeline}

Une fois que vous avez utilisé l’interface d’utilisation de [!UICONTROL Cloud Manager] pour configurer votre programme et que vous disposez d’au moins un environnement, vous pouvez ajouter un pipeline de production.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme**.

1. Cliquez sur **+Ajouter** et sélectionnez **Ajouter un pipeline de production**.

   ![Ajout d’un pipeline de production](/help/assets/configure-pipelines/add-prod7.png)

1. La boîte de dialogue **Ajout d’un pipeline de production** s’ouvre sur l’onglet de **Configuration** où plusieurs options de votre pipeline doivent être définies. Ces options sont regroupées en sections réductibles et sont décrites dans les étapes suivantes.

   1. Attribuez un nom explicite à votre pipeline dans le champ **Nom du pipeline**.

   1. Sous la section **Environnements**, vous définissez ce qui déclenche un déploiement et comment il doit être déployé par environnement.

      1. Dans la section **ÉTAPE**, vous pouvez définir la manière dont le pipeline se déploie vers votre environnement d’évaluation.

         * **Déclencheur de déploiement** - vous disposez des options suivantes pour définir les déclencheurs de déploiement pour démarrer le pipeline.

            * **Manuel** : démarrez manuellement le pipeline à l’aide de l’interface d’utilisation de Cloud Manager.
            * **Lors des modifications Git** : démarrez le pipeline CI/CD lorsque des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.

         * **Comportement en cas d’échecs de mesure importants** - lors de la configuration ou de la modification du pipeline, le responsable de déploiement peut définir le comportement du pipeline lorsqu’un échec important est rencontré à l’un des points de contrôle qualité. Les options disponibles sont les suivantes :

            * **Demander à chaque fois** : paramètre par défaut, qui nécessite une intervention manuelle lors de n’importe quel échec important.
            * **Échouer immédiatement** : le pipeline sera interrompu dès qu’un échec important aura lieu. Il s’agit de l’émulation d’un utilisateur ou d’une utilisatrice qui rejette manuellement chaque échec.
            * **Continuer immédiatement** : le pipeline se poursuivra automatiquement chaque fois qu’un échec important se produira. Il s’agit de l’émulation d’un utilisateur ou d’une utilisatrice qui approuve manuellement chaque échec.

         ![Déclencheur de déploiement](/help/assets/configure-pipelines/add-prod3.png)

         * **Options de déploiement** - vous pouvez accélérer certaines tâches de déploiement.

            * **Approbation après le déploiement d’évaluation** - cette approbation a lieu après le déploiement dans l’environnement d’évaluation avant que tout test ne soit effectué. Sinon, l’approbation se produit avant le déploiement en production, qui est effectué une fois tous les tests terminés.

            * **Ignorer les modifications de la répartition de charge** - les modifications de la répartition de charge ne sont pas effectuées.

         ![Options de déploiement intermédiaire](/help/assets/configure-pipelines/add-prod4.png)

         * **Configuration du Dispatcher** : le rôle de la personne **Responsable de déploiement** consiste à configurer un ensemble de chemins de contenu qui sont soit invalidés soit vidés du cache d’AEM Dispatcher lorsqu’un pipeline est exécuté. Ces actions de cache sont exécutées dans le cadre de l’étape du pipeline de déploiement, juste après le déploiement des modules de contenu. Ces paramètres utilisent le comportement standard d’AEM Dispatcher. Pour effectuer la configuration, procédez comme suit :

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

            * **Utiliser l’approbation de mise en production** : une personne ayant le rôle de **Propriétaire d’entreprise**, **Responsable de projet** ou **Responsable de déploiement** via l’interface d’utilisation de [!UICONTROL Cloud Manager] doit approuver manuellement un déploiement.
            * **Planifié** : interrompt le pipeline avant le déploiement en production pour permettre sa planification. Si cette option est sélectionnée, le pipeline s’arrête après le déploiement dans l’environnement d’évaluation et demandera à l’utilisateur ou à l’utilisatrice quelle action entreprendre.
               * **`Now`** : déploie immédiatement en production, terminant ainsi le pipeline.
               * **Date** : permet à l’utilisateur ou à l’utilisatrice de planifier une heure à laquelle le déploiement doit être terminé.
               * **Arrêter l’exécution** : interrompt le déploiement en production.

           >[!TIP]
           >
           >Voir la section [Déploiement du code](/help/using/code-deployment.md) pour découvrir comment définir le planning de déploiement ou exécuter le pipeline immédiatement.

            * **Solliciter la supervision par le responsable du succès client** : si cette option est choisie, une personne responsable du succès client est engagée pour véritablement démarrer le déploiement. Lors de la création ou de la modification d’un pipeline lorsque cette option est activée, le rôle **Responsable de déploiement** dispose des options suivantes.

               * **Toute personne faisant partie de l’équipe d’ingénierie du service client** : permet à un ingénieur ou à une ingénieure du service client disponible de démarrer le déploiement.
               * **Ma personne faisant partie de l’équipe d’ingénierie du service client** : permet uniquement à la personne faisant partie de l’équipe d’ingénierie du service client spécifique affectée au client ou à la cliente de démarrer le déploiement. Cette option s’applique également à la personne remplaçante désignée de l’ingénieur ou de l’ingénieure du service client indisponible.

           ![Options de déploiement en production](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configuration du Dispatcher** : définissez la configuration du Dispatcher pour votre environnement de production. Les options sont identiques à celles de l’environnement d’évaluation.

1. Cliquez sur **Continuer** pour accéder à l’onglet **Code Source** dans lequel vous sélectionnez le type de code à déployer et configurez le référentiel source.

   1. Sous **Sélectionner le code à déployer**, choisissez le type de déploiement :

      * **[Code de pile complète](#full-stack-code)** - Code de votre application AEM complète.
      * **[Configuration de niveau web](#web-tier-config)** - Propriétés Dispatcher pour stocker, traiter et diffuser des pages web au client.

      Voir [Pipelines CI/CD](/help/overview/ci-cd-pipelines.md#code-sources) pour plus d’informations sur ces types de déploiement. Les étapes restantes pour terminer la configuration du pipeline dépendent du type que vous avez sélectionné. Suivez les liens ci-dessus pour accéder à la section appropriée de ce document.

1. Cliquez sur **Continuer** pour accéder à l’onglet **Tests de l’environnement d’évaluation** où vous pouvez configurer les tests de performances d’AEM Sites et d’AEM Assets, en fonction des produits sous licence que vous possédez. {#stage-testing}

   >[!TIP]
   >
   >Voir la section [Test de qualité du code](/help/using/code-quality-testing.md#performance-testing) pour plus de détails sur les options disponibles dans l’onglet **Tests de l’environnement d’évaluation**.

   1. Dans la section **Diffusion de contenu de sites/poids de la charge distribuée**, vous configurez les tests de performance du site en fonction de la pondération des requêtes de page parmi trois ensembles de pages. Vous pouvez activer ou désactiver les ensembles de pages selon vos besoins.

      * **Pages dynamiques populaires**
      * **Autres pages dynamiques**
      * **Nouvelles pages**

      ![Poids de charge des sites](/help/assets/configure-pipelines/add-prod8.png)

   1. Sous la section **Distribution des tests de performances des ressources**, vous définissez la distribution de test des images et des PDF ainsi que vos propres ressources de test.

      * **Images** - réglez le curseur pour ajuster la répartition du test entre les images et les PDF.
      * **PDF** - réglez le curseur pour ajuster la répartition du test entre les images et les PDF.

      * Définissez vos propres ressources personnalisées en les chargeant.

         1. **FORMAT** - choisissez si votre ressource personnalisée est un PDF ou une image.
         1. **NOM DE FICHIER** - utilisez le bouton du navigateur de fichiers pour sélectionner une image sur votre ordinateur local.
         1. **Ajouter un fichier test** - cliquez pour charger la ressource sélectionnée.

      ![Distribution des tests des ressources](/help/assets/configure-pipelines/add-prod6.png)

1. Cliquez sur **Enregistrer** pour terminer l’ajout de votre pipeline de production.

### Code full stack {#full-stack-code}

Un pipeline de code full stack déploie des versions de code front-end et back-end avec une configuration HTTPD/Dispatcher.

>[!NOTE]
>
>Si un pipeline de production full stack existe déjà, cette sélection est désactivée.

**Pour configurer un pipeline de production de code de pile complète, procédez comme suit**

1. Dans l&#39;onglet **Code**, définissez les options suivantes.

   * **Référentiel** : définit à partir de quel référentiel Git le pipeline doit récupérer le code.

   >[!TIP]
   >
   >Voir le document [Configuration du programme](/help/getting-started/program-setup.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - Définit à partir de quelle branche le pipeline doit récupérer le code.
   * **Ignorer la configuration de niveau Web** – Lorsque cette case est cochée, le pipeline ne déploie pas votre configuration de niveau web. Si un pipeline de configuration de niveau web existe déjà pour le même environnement, cette case à cocher est automatiquement sélectionnée et désactivée, car la configuration de niveau web est gérée par ce pipeline à la place. Lorsqu’il n’existe aucun pipeline de configuration de niveau web, vous pouvez sélectionner ou désélectionner cette option pour contrôler si le pipeline de pile complète déploie la configuration Dispatcher.

   ![Source du code de pile complète](/help/assets/configure-pipelines/add-prod-fullstack-source.png)

1. Cliquez sur **Continuer** pour accéder à l’onglet **Test d’évaluation**. Voir [Test d’évaluation](#stage-testing) pour plus d’informations.

### Configuration de la couche web {#web-tier-config}

Un pipeline de configuration de niveau web déploie uniquement la configuration HTTPD/Dispatcher. Voir [Pipelines CI/CD](/help/overview/ci-cd-pipelines.md#deployment-types) pour plus d’informations sur ce type de pipeline.

>[!NOTE]
>
>Si un pipeline de production de configuration de niveau web existe déjà, cette sélection est désactivée.

Si vous créez un pipeline de configuration de niveau web pour un environnement avec un pipeline full stack existant, la configuration de niveau web dans le pipeline full stack est ignorée. Cette modification affecte uniquement la configuration de niveau web dans cet environnement.

**Pour configurer un pipeline de production de configuration de niveau web, procédez comme suit**

1. Dans l&#39;onglet **Code**, définissez les options suivantes.

   * **Référentiel** - Dans la liste déroulante, sélectionnez le référentiel Git contenant la configuration de niveau web.
   * **Branche Git** - Sélectionnez la branche dans le référentiel choisi que Cloud Manager utilise pour le déploiement.
   * **Emplacement du code** - Saisissez le chemin d’accès dans le référentiel sélectionné qui contient la configuration de niveau web à déployer. L’emplacement par défaut est la racine du référentiel (`/`).

   >[!NOTE]
   >
   >Si l’emplacement du code ne pointe pas vers l’emplacement du code du Dispatcher, du code d’application supplémentaire peut être extrait dans le package d’artefact et déployé vers le Dispatcher, ce qui entraîne l’échec d’Apache au redémarrage et l’échec du pipeline. Veillez à définir le chemin d’accès correct aux fichiers du Dispatcher dans le référentiel.

   ![Source de configuration de niveau web](/help/assets/configure-pipelines/add-prod-webtier-source.png)

1. Cliquez sur **Continuer** pour accéder à l’onglet **Test d’évaluation**. Voir [Test d’évaluation](#stage-testing) pour plus d’informations.

## Étapes suivantes {#the-next-steps}

Une fois que vous avez configuré le pipeline, vous devez déployer votre code. Voir la section [Déploiement du code](/help/using/code-deployment.md) pour plus d’informations.

## Tutoriel vidéo {#video-tutorial-one}

Cette vidéo présente une vue d’ensemble du processus de création de pipeline, détaillé dans ce document.

>[!VIDEO](https://video.tv.adobe.com/v/327601?captions=fre_fr)
