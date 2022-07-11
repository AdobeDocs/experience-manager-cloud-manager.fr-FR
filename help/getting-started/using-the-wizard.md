---
title: Utilisation de l’assistant Nouveau projet
description: Suivez cette page pour savoir comment utiliser l’assistant afin de créer un projet d’application AEM
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: cb791a4f148ba394687b5e824b75fe1386d83c18
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 9%

---


# Utilisation de l’assistant Nouveau projet {#using-the-wizard}

Lorsque vous êtes intégré à Cloud Manager en tant que nouveau client, un référentiel Git vide vous est fourni. Pour vous aider à prendre en main, Cloud Manager propose un assistant pour créer un projet d’AEM minimal basé sur les [AEM Archétype de projet](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype) comme point de départ.

Pour créer un projet AEM à l’aide de l’assistant, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation appropriée.

1. Si ce n’est déjà fait, [créez votre programme.](program-setup.md) Une fois le programme créé, Cloud Manager reconnaît que les référentiels ne sont pas encore configurés et une carte spéciale d’appel à l’action s’affiche sur la page **Présentation** écran.

   ![Créer un projet CTA](/help/assets/image2018-10-3_14-29-44.png)

1. Cliquez sur **Créer** pour démarrer l’assistant et fournir des valeurs importantes.

   * **Titre** - Il s’agit du titre du projet. Par défaut, il est défini sur le nom du programme.
   * **Nouveau nom de branche** - Il s’agit de la branche initiale de vos référentiels Git et, par défaut, sera `main`.

   ![Valeurs du projet](/help/assets/screen_shot_2018-10-08at55825am.png)

1. La boîte de dialogue comporte un tiroir qui peut être ouvert en cliquant sur la poignée vers le bas. Sous sa forme développée, la boîte de dialogue affiche tous les paramètres de configuration de l’archétype de projet AEM. Ces paramètres comportent des valeurs par défaut qui sont générées en fonction de la variable **Titre** vous avez déjà fourni des informations et n’avez pas besoin d’être modifié. Elles sont expliquées ici pour votre information.

   ![Paramètres détaillés de l’archétype](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Cliquez sur **Créer** pour créer le projet starter en utilisant l’archétype et en validant la branche git nommée.

Vous avez maintenant un projet de base ! Vous pouvez maintenant configurer vos pipelines.

## Clients existants ou en migration {#existing-migrating}

Si vous êtes un client actuel d’Adobe Managed Services (AMS) ou un AEM sur site qui effectue une migration vers , il est probable que vous disposiez déjà d’un code de projet dans git ou dans un autre système de contrôle de version.

Dans ce cas, vous importez votre projet dans le référentiel git de Cloud Manager.
