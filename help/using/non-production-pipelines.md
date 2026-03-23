---
title: Ajout d’un pipeline hors production
description: Découvrez comment utiliser Cloud Manager pour créer et configurer des pipelines hors production afin de déployer votre code.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 2a022c10ce64bb42d4bffd63bea01de25af0bd41
workflow-type: tm+mt
source-wordcount: '1992'
ht-degree: 27%

---

# Ajout d’un pipeline hors production {#configuring-non-production-pipelines}

Découvrez comment utiliser Cloud Manager pour créer et configurer des pipelines hors production afin de déployer votre code. Si vous souhaitez d’abord obtenir une vue d’ensemble plus conceptuelle du fonctionnement des pipelines dans Cloud Manager, reportez-vous au document [Pipelines CI/CD](/help/overview/ci-cd-pipelines.md).

## Vue d’ensemble {#overview}

En utilisant le volet **Pipelines** dans [!UICONTROL Cloud Manager], le **Responsable de déploiement** peut créer deux types de pipelines différents.

* **Pipelines de production** - un pipeline de production est un pipeline spécialement conçu, composé d’une série d’étapes coordonnées permettant de mener le code source jusqu’à la production.
* **Pipelines hors production** - un pipeline hors production sert principalement à exécuter des analyses de qualité du code ou à déployer le code source dans un environnement de développement.

Ce document se concentre sur les pipelines hors production. Pour plus de détails sur la configuration des pipelines de production, voir le document [Configurer des pipelines de production](/help/using/production-pipelines.md).

Il existe deux types de pipelines hors production :

* **Pipelines de qualité du code** : ceux-ci exécutent des analyses de qualité du code sur le code dans une branche Git et exécutent les étapes de création et de qualité du code.
* **Pipelines de déploiement** : outre l’exécution des étapes de création et de qualité du code, identiques à celles des pipelines de qualité du code, ces pipelines déploient le code dans un environnement hors production.

>[!NOTE]
>
>Un pipeline ne peut être configuré que si le référentiel Git qui lui est associé dispose d’au moins une branche et que la [configuration du programme](/help/getting-started/program-setup.md) est terminée. Consultez le document [Référentiels Cloud Manager](/help/managing-code/managing-repositories.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

## Ajout d’un nouveau pipeline hors production {#add-non-production-pipeline}

Après avoir configuré un programme et au moins un environnement dans l’interface utilisateur de Cloud Manager, vous pouvez ajouter des pipelines hors production. Utilisez ces pipelines pour tester la qualité de votre code avant de le déployer dans des environnements de production.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la vignette Pipelines à partir de l’écran d’accueil de Cloud Manager. Cliquez sur **Ajouter** et sélectionnez **Ajouter un pipeline hors production**.

   ![Ajouter un pipeline hors production](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Sous l’onglet **Configuration** de la boîte de dialogue **Ajouter un pipeline hors production**, sélectionnez le type de pipeline que vous souhaitez créer, l’un des éléments suivants :

   * **Pipeline de qualité du code** - Crée un pipeline qui génère le code, exécute des tests unitaires et évalue la qualité du code sans le déployer dans un environnement.
   * **Pipeline de déploiement** - Crée un pipeline qui génère le code, exécute des tests unitaires, évalue la qualité du code et le déploie dans un environnement.

   ![Choix du type de pipeline](/help/using/assets/add-non-production-pipeline-cm-ams.png)

>[!BEGINTABS]

>[!TAB Pipeline de la qualité du code - Onglet Configuration]

| Section | Option | Description |
| --- | --- | --- |
| **Configuration du pipeline** | **Nom du pipeline hors production** | Fournissez une description de votre pipeline dans le champ **Nom du pipeline hors production**. |
|  | **Test** | Visible uniquement lors de la modification d’un pipeline hors production.<br>L’interface utilisateur affiche les catégories de test que le pipeline exécute dans le cadre de la validation de la qualité du code.<ul><li>**Test de code statique** - Analyse le code pour détecter les problèmes de qualité et d’exactitude.<li>**Tests de charge/performance** - Évalue le comportement lié aux performances dans le cadre des tests de pipeline.<li>**Tests de sécurité** - Vérifie le code et la sortie du pipeline pour les problèmes de sécurité. |
| **Options de déploiement** | **Déclencheur de déploiement** | <ul><li>**Manuel** : vous permet de lancer le pipeline manuellement.<li>**Lors des modifications Git** : démarre le pipeline lorsque des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire. |
|  | **Comportement en cas d’échecs de mesures importants** | <ul><li>**Demander à chaque fois** – Ce comportement est le paramètre par défaut qui nécessite une intervention manuelle lors de tout échec important.<li>**Défaillance immédiate** - si cette option est sélectionnée, le pipeline est interrompu chaque fois qu’une défaillance importante se produit. Il émule essentiellement un utilisateur rejetant manuellement chaque échec.<li>**Continuer immédiatement** - si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Il émule essentiellement la validation manuelle de chaque échec par un utilisateur.</li></ul> |
|  | Case à cocher **Approuver après le déploiement dans l’environnement intermédiaire** | Visible uniquement lors de la modification d’un pipeline hors production.<br>Sélectionnez cette option pour exiger une approbation après le déploiement dans l’environnement d’évaluation avant que le pipeline puisse continuer. Si cette option n’est pas sélectionnée, le pipeline se poursuit en fonction du comportement configuré. |

>[!TAB Pipeline de déploiement - Onglet Configuration]

| Section | Option | Description |
| --- | --- | --- |
| **Configuration du pipeline** | **Nom du pipeline hors production** | Fournissez une description de votre pipeline dans le champ **Nom du pipeline hors production**. |
|   | **Environnement de déploiement éligible** | Si votre pipeline est un pipeline de déploiement, vous devez sélectionner les environnements dans lesquels Cloud Manager déploie le code. |
|   | **Test** | Visible uniquement lors de la modification d’un pipeline hors production.<br>L’interface utilisateur affiche les catégories de test que le pipeline exécute dans le cadre de la validation de la qualité du code.<ul><li>**Test de code statique** - Analyse le code pour détecter les problèmes de qualité et d’exactitude.<li>**Tests de charge/performance** - Évalue le comportement lié aux performances dans le cadre des tests de pipeline.<li>**Tests de sécurité** - Vérifie le code et la sortie du pipeline pour les problèmes de sécurité.</li></ul> |
| **Options de déploiement** | **Déclencheur de déploiement** | <ul><li>**Manuel** : vous permet de lancer le pipeline manuellement.<li>**Lors des modifications Git** : démarre le pipeline lorsque des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire. |
|   | **Comportement en cas d’échecs de mesures importants** | <ul><li>**Demander à chaque fois** - Le paramètre par défaut invite l’utilisateur à décider comment procéder lorsqu’une mesure importante échoue.<li>**Échec immédiat** - Le pipeline est annulé chaque fois qu’une mesure importante échoue. Il s’agit essentiellement de l’émulation d’un utilisateur ou d’une utilisatrice qui rejette manuellement chaque échec.<li>**Continuer immédiatement** - Le pipeline se poursuit automatiquement chaque fois qu’une mesure importante échoue. Il s’agit essentiellement de l’émulation d’un utilisateur ou d’une utilisatrice qui approuve manuellement chaque échec.</li></ul> |
|  | Case à cocher **Approuver après le déploiement dans l’environnement intermédiaire** | Visible uniquement lors de la modification d’un pipeline hors production.<br>Sélectionnez cette option pour exiger une approbation après le déploiement dans l’environnement d’évaluation avant que le pipeline puisse continuer. Si cette option n’est pas sélectionnée, le pipeline se poursuit en fonction du comportement configuré. |
|  | Case **Ignorer les modifications de la répartition de charge** | Sélectionnez cette option pour empêcher le pipeline d’effectuer des modifications de la répartition de charge pendant le déploiement. |
|  | **Configuration** | Le rôle **Responsable de déploiement** permet de configurer un ensemble de chemins de contenu qui sont soit invalidés soit vidés du cache d’AEM Dispatcher lorsqu’un pipeline est exécuté. Ces actions de cache sont exécutées dans le cadre de l’étape du pipeline de déploiement, juste après le déploiement des modules de contenu. Ces paramètres utilisent le comportement standard d’AEM Dispatcher. Pour configurer `Dispatcher`, procédez comme suit :<ul><li>Sous **CHEMIN**, indiquez un chemin d’accès au contenu que le pipeline doit vider ou invalider.<li>Sous **TYPE**, sélectionnez l’action à effectuer sur ce chemin.<ul><li>**Vidage** - Effectuez une suppression du cache sur le chemin d’accès spécifié.</li><li>**Invalider** - effectuez une invalidation du cache, comme lorsque le contenu est activé d’une instance de création vers une instance de publication.</li><li>Cliquez sur **Ajouter un chemin** pour ajouter votre chemin spécifié. Vous pouvez ajouter jusqu’à 100 chemins par environnement.</li></ul> |
| **Pipeline** | Case à cocher **Contrôle de l’expérience** | Sélectionnez cette option pour inclure une étape de contrôle de l’expérience dans le pipeline. Lorsqu’il est activé, le pipeline inclut l’étape Contrôle de l’expérience après l’onglet Code Source . |

>[!ENDTABS]

1. Dans le coin inférieur droit de la boîte de dialogue **Ajouter un pipeline hors production**, cliquez sur **Continuer**.
1. Sélectionnez le type de code que le pipeline est configuré pour créer et déployer.

>[!BEGINTABS]

>[!TAB Onglet Code Source - Code de pile complète]

Déploie l’ensemble de l’application AEM, y compris le code de l’application et, par défaut, la configuration de niveau web.

| Section | Option | Description |
| --- | --- | --- |
| **Code** | **Référentiel** | Dans la liste déroulante , choisissez le référentiel Git que le pipeline utilise comme source. Cloud Manager crée le code à partir du référentiel que vous choisissez ici. |
|   | **Branche Git** | Dans la liste déroulante , choisissez la branche du référentiel sélectionné à partir de laquelle le pipeline doit être créé. La valeur par défaut est `main`. Le pipeline utilise la branche choisie comme source pour la création et le déploiement. Si nécessaire, cliquez sur **Actualiser** pour mettre à jour la liste des branches disponibles pour le référentiel sélectionné. Utilisez cette option si une branche créée récemment n’apparaît pas dans la liste. |
|   | **Créer une stratégie** | <ul><li>**Version complète** - Génère tous les modules du référentiel à chaque fois<li>BETA **Smart Build** - crée uniquement les modules qui ont été modifiés depuis la dernière validation.<br>En savoir plus sur [l’utilisation de Smart Build dans un pipeline hors production](#about-smart-build).</li></ol>**Important** : la création intelligente est disponible uniquement pour les pipelines de qualité du code et de déploiement de code de pile complète de développement. |
|   | Case à cocher **Ignorer la configuration de niveau web** | Sélectionnez cette option pour ignorer le déploiement de la configuration de niveau web dans un pipeline de code de pile complète. Laissez l’option désélectionnée pour déployer la configuration de niveau web avec le code du pipeline. |
| **Pipeline** | Case à cocher **Contrôle de l’expérience** | Sélectionnez cette option pour inclure une étape de contrôle de l’expérience dans le pipeline. Lorsqu’il est activé, le pipeline inclut l’étape Contrôle de l’expérience après l’onglet Code Source . |

>[!TAB Code Source - Configuration de niveau web]

Déploie uniquement la configuration de niveau web, telle que les propriétés Dispatcher utilisées pour stocker, traiter et diffuser des pages web au client. Lorsque vous sélectionnez **Configuration de niveau web**, Cloud Manager crée un pipeline dédié au déploiement de la configuration de niveau web.

Si un pipeline de pile complète existe déjà, Cloud Manager affiche un avis indiquant que la création d’un pipeline de configuration de niveau web entraîne l’exclusion de la configuration de niveau web par le pipeline de pile complète existant. Une fois que vous avez créé le pipeline de configuration de niveau web, Cloud Manager gère les déploiements de configuration de niveau web via ce pipeline au lieu du pipeline de pile complète.

| Section | Option | Description |
| --- | --- | --- |
| **Code** | **Référentiel** | Dans la liste déroulante, sélectionnez le référentiel Git contenant la configuration de niveau web. |
|   | **Branche Git** | Sélectionnez la branche dans le référentiel choisi que Cloud Manager utilise pour le déploiement. Si nécessaire, cliquez sur **Actualiser** pour mettre à jour la liste des branches disponibles pour le référentiel sélectionné. Utilisez cette option si une branche créée récemment n’apparaît pas dans la liste. |
|   | **Emplacement du code** | Saisissez le chemin d’accès dans le référentiel sélectionné qui contient la configuration de niveau web à déployer. L’emplacement par défaut est la racine du référentiel (`/`). |

>[!ENDTABS]

1. Cliquez sur **Enregistrer**.

## À propos de l’utilisation de la création dynamique dans un pipeline hors production{#about-smart-build}

La **version intelligente** dans Cloud Manager est une stratégie de création optimisée pour les pipelines hors production. La génération intelligente réduit les temps de génération en mettant en cache les modules et en ne reconstruisant que les modules qui ont été modifiés depuis la dernière exécution réussie. Les modules inchangés sont réutilisés à partir du cache, tandis que seuls les modules modifiés et leurs dépendances sont reconstruits, ce qui améliore l’efficacité des workflows de développement itératifs.

La génération intelligente n&#39;est actuellement disponible que pour les éléments suivants :

* Pipelines de la qualité du code.
* Développez des pipelines de déploiement full stack.

>[!NOTE]
>
>La première exécution après l’activation de la création dynamique se comporte comme une création complète, car le cache est vide.

Le build intelligent est recommandé lorsque vous disposez des éléments suivants :
* Vous développez et validez activement des modifications incrémentielles fréquentes.
* Votre projet contient plusieurs modules Maven.
* Les versions complètes prennent beaucoup de temps.

La création intelligente n’est pas toujours idéale lorsque vous disposez des éléments suivants :
* Votre version repose principalement sur des modules externes qui effectuent des opérations en dehors du graphique de dépendance de Maven.
* Vous avez besoin d’une validation de reconstruction complète à chaque exécution.

### Présentation des performances de build{#smart-build-performance}

Le gain de performances de l’utilisation de la création dynamique dépend de plusieurs facteurs, notamment des éléments suivants :

* Nombre de modules dans le projet.
* La fréquence et l’étendue des modifications de code.
* La distribution des dépendances entre les modules.

En règle générale, les projets comportant de nombreux modules indépendants peuvent bénéficier de la plus grande amélioration.

### Désinscription du cache par module{#smart-build-cache-optout}

Smart Build fournit un contrôle affiné qui vous permet de désactiver la mise en cache pour des modules spécifiques. Cette fonctionnalité est utile lorsque certains modules :

* Utilisez des plug-ins, tels que `exec-maven-plugin` ou `maven-antrun-plugin`.
* Effectuer des opérations de fichier non suivies par les dépendances Maven.
* Produire des résultats incohérents lors de la mise en cache.

### Désactiver la mise en cache pour un module{#smart-build-disable-caching}

Vous pouvez ajouter la propriété suivante au `pom.xml` du module concerné :

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

Cette syntaxe force le module à se recréer à chaque exécution de pipeline tandis que les autres modules continuent à bénéficier de la mise en cache.

### Restrictions et considérations lors de l’utilisation de la création dynamique{#smart-build-limitations}

Gardez les points suivants à l’esprit lorsque vous utilisez la création dynamique :

* Smart Build repose sur l’analyse des dépendances Maven.
* Les modifications en dehors du graphique de dépendance peuvent ne pas déclencher de reconstructions.
* Certains plug-ins peuvent ne pas être entièrement compatibles avec la mise en cache.
* Vous pouvez revenir à la **version complète** à tout moment en modifiant le pipeline hors production.

Si vous rencontrez un comportement de build inattendu, envisagez de désactiver la mise en cache de modules spécifiques ou de changer temporairement votre stratégie de build en **Version complète**.

### Dépannage des problèmes de création dynamique{#smart-build-troubleshoot}

| Problème | Solutions suggérées |
| --- | --- |
| Les résultats de build sont incohérents | · Désactivez la mise en cache pour les modules concernés.<br>· Vérifiez le comportement des plug-ins (en particulier des plug-ins `exec`/`antrun`). |
| Aucune amélioration des performances | · Assurez-vous que plusieurs exécutions ont eu lieu (préchauffage du cache).<br>· Vérifiez si la plupart des modules changent fréquemment. |
| Artefacts inattendus ou modifications manquantes | · Vérifiez si les modifications ne se trouvent pas en dehors du suivi des dépendances Maven.<br>· Utilisez **Version complète** pour la vérification. |

Voir [Ajouter un pipeline hors production](#add-non-production-pipeline) la section Activation de la création dynamique.



<!-- 
1. If you chose to add a **Deployment Pipeline**, select the target deployment environment from the **Eligible Deployment Environments** dropdown.

1. Provide the repository where the pipeline should retrieve the code.

   * **Repository** - Defines from which Git repo that the pipeline should retrieve the code.
   * **Git Branch** - Defines from which branch in Git that the selected pipeline should retrieve the code.

1. Define your deployment options.

   1. Under **Deployment Trigger**, define what event activates the pipeline.

      * **Manual** - Lets you manually start the pipeline.
      * **On Git Changes** - Starts the pipeline when commits are added to the configured Git branch. With this option, you can still start the pipeline manually, as required.

   1. For deployment pipelines, under **Important Metric Failures Behavior**, define the behavior of the pipeline when an important failure is encountered in any of the quality gates.

       * **Ask every time** - The default setting and requires manual intervention on any important failure.
       * **Fail Immediately** - The pipeline is canceled whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.
       * **Continue Immediately** - The pipeline proceeds automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.

   1. **Dispatcher Configuration** - The **Deployment Manager** role can configure a set of content paths that are either invalidated or flushed from the AEM Dispatcher cache when a pipeline is run. These cache actions are performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure:

      1. Under **PATH** provide a content path.
      1. Under **TYPE**, select the action to be taken on that path.

         * **Flush** - Perform a cache deletion.
         * **Invalidate** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.
         
      1. Click **Add Path** to add your specified path. You can add up to 100 paths per environment.

1. Click **Save**.
-->

## Étapes suivantes {#the-next-steps}

Après avoir configuré le pipeline, vous pouvez déployer votre code. Voir la section [Déploiement du code](/help/using/code-deployment.md) pour plus d’informations.

## Tutoriel vidéo {#video-tutorial}

Cette vidéo présente une vue d’ensemble du processus de création de pipeline, détaillé dans ce document.

>[!VIDEO](https://video.tv.adobe.com/v/327614?captions=fre_fr)
