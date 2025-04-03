---
title: Utiliser l’assistant Nouveau projet
description: Suivez cette page pour savoir comment utiliser l’assistant afin de créer un projet d’application AEM.
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: f3617eb50147f5af33282cb0f25ada7dc423d434
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 92%

---


# Utiliser l’assistant de nouveau projet {#using-the-wizard}

Lorsque vous avez intégré Cloud Manager en tant que nouveau client, un référentiel Git vide vous a été fourni. Pour vous aider à commencer, Cloud Manager propose un assistant qui vous aide à créer un projet AEM minimal basé sur [l’archétype de projet AEM](https://github.com/adobe/aem-project-archetype) comme point de départ.

Pour créer un projet AEM à l’aide de l’assistant, suivez les étapes suivantes.

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation appropriée.

1. Si cela n’est pas encore fait, [créez votre programme](program-setup.md). Lors de la création du programme, Cloud Manager détecte que les référentiels ne sont pas encore configurés. Une carte d’appel à l’action spéciale s’affiche alors sur l’écran **Vue d’ensemble**.

   ![Appel à l’action de création de projet](/help/assets/image2018-10-3_14-29-44.png)

1. Cliquez sur **Créer** pour démarrer l’assistant et fournir des valeurs importantes.

   * **Titre** - Titre du projet. Par défaut, il est défini sur le nom du programme.
   * **Nouveau nom de branche** - Branche initiale de vos référentiels Git. Par défaut,son nom est `main`.

   ![Valeurs du projet](/help/assets/screen_shot_2018-10-08at55825am.png)

1. La boîte de dialogue comporte un tiroir qui s’ouvre lorsque vous cliquez sur la poignée en la tirant vers le bas de la boîte de dialogue. Sous sa forme développée, la boîte de dialogue affiche tous les paramètres de configuration de l’archétype du projet AEM. Ces paramètres comportent des valeurs par défaut qui sont générées en fonction du **Titre** que vous avez déjà fourni et n’ont pas besoin d’être modifiés. Ils sont expliqués ici pour vous fournir de plus amples informations.

   ![Paramètres détaillés de l’archétype](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Cliquez sur **Créer** pour créer le projet de démarrage à l’aide de l’archétype et en validant la branche Git nommée.

Vous avez désormais un projet de base. Il est temps de configurer vos pipelines.

## Clientes et clients existants ou en migration {#existing-migrating}

Si vous faites actuellement partie de la clientèle d’Adobe Managed Services (AMS) ou d’AEM On-Premise en migration, il est probable que vous disposiez déjà d’un code de projet dans Git ou dans un autre système de contrôle de version.

Dans ce cas, vous pouvez importer votre projet dans le référentiel Git de Cloud Manager.
