---
title: Utilisation de l’assistant Nouveau projet
description: Consultez cette page pour savoir comment utiliser l’assistant pour créer un projet d’application AEM.
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: 7bc874a8dd14544c22201ef2c470faab84d31f8b
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 25%

---


# Utilisation de l’assistant Nouveau projet {#using-the-wizard}

Lorsque vous étiez intégré à Cloud Manager en tant que nouveau client, un référentiel Git vide vous était fourni. Pour vous aider à commencer, Cloud Manager propose un assistant qui vous aide à créer un projet AEM minimal basé sur [l’archétype de projet AEM](https://github.com/adobe/aem-project-archetype) comme point de départ.

Pour créer un projet AEM à l’aide de l’assistant, suivez les étapes suivantes.

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation appropriée.

1. Si cela n’est pas encore fait, [créez votre programme](program-setup.md). Lors de la création du programme, Cloud Manager détecte que les référentiels ne sont pas encore configurés. Une carte d’appel à l’action spéciale s’affiche alors sur l’écran **Overview**.

   ![Appel à l’action de création de projet](/help/assets/image2018-10-3_14-29-44.png)

1. Cliquez sur **Créer** pour démarrer l’assistant et fournir des valeurs importantes.

   * **Titre** - Titre du projet. Par défaut, il est défini sur le nom du programme.
   * **Nouveau nom de branche** - La branche initiale de vos référentiels Git. Par défaut, il est `main`.

   ![Valeurs du projet](/help/assets/screen_shot_2018-10-08at55825am.png)

1. La boîte de dialogue comporte un tiroir qui peut être ouvert en cliquant sur la poignée vers le bas. Sous sa forme développée, la boîte de dialogue affiche tous les paramètres de configuration de l’archétype de projet AEM. Ces paramètres ont des valeurs par défaut générées en fonction du **titre** que vous avez déjà fourni et qui ne nécessitent pas de modification. Ils sont expliqués ici pour vous fournir de plus amples informations.

   ![Paramètres détaillés de l’archétype](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Cliquez sur **Créer** pour créer le projet de démarrage à l’aide de l’archétype et validez sur la branche Git nommée.

Vous disposez maintenant d’un projet de base. Il est temps de configurer vos pipelines.

## Clients existants ou en cours de migration {#existing-migrating}

Si vous êtes un client actuel d’Adobe Managed Services (AMS) ou un client AEM sur site qui effectue une migration vers , il est probable que vous ayez déjà un code de projet dans Git ou dans un autre système de contrôle de version.

Dans ce cas, vous pouvez importer votre projet dans le référentiel Git de Cloud Manager.
