---
title: Utiliser l’assistant Nouveau projet
description: Suivez cette page pour savoir comment utiliser l’assistant afin de créer un projet d’application AEM.
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
TQID: https://experienceleague.adobe.com/zoiHL1lNC2XN-T9g0dh3pQyL4Yw3uYgFpHs8d6hkj3M
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: fa6be369b979682cebf68852603725d8754605ab
workflow-type: tm+mt
source-wordcount: 317
ht-degree: 54%

---

# Utiliser l’assistant de nouveau projet {#using-the-wizard}

Lorsque vous intégrez Cloud Manager en tant que nouveau client, vous recevez un référentiel Git vide. Pour vous aider à commencer, Cloud Manager propose un assistant qui vous aide à créer un projet AEM minimal basé sur l’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype) comme point de départ.

**Pour utiliser l’assistant Nouveau projet, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation appropriée.

1. Si cela n’est pas encore fait, [créez votre programme](program-setup.md). Lors de la création du programme, Cloud Manager détecte que le référentiel n’est pas configuré. Une vignette d’invite spéciale s’affiche alors sur l’écran **Présentation**.

   ![Appel à l’action de création de projet](/help/assets/image2018-10-3_14-29-44.png)

1. Cliquez sur **Créer** pour démarrer l’assistant et fournir des valeurs importantes.

   * **Titre** - Titre du projet. Par défaut, il est défini sur le nom du programme.
   * **Nouveau nom de la branche** - Branche initiale de votre référentiel Git. Par défaut,son nom est `main`.

   ![Valeurs du projet](/help/assets/screen_shot_2018-10-08at55825am.png)

1. La boîte de dialogue comporte une section que vous pouvez afficher en cliquant sur l’icône près du bas. Sous sa forme développée, la boîte de dialogue affiche tous les paramètres de configuration de l’archétype du projet AEM. Ces paramètres comportent des valeurs par défaut qui sont générées en fonction du **Titre** que vous avez déjà fourni et n’ont pas besoin d’être modifiés. Ils sont expliqués ici pour vous fournir de plus amples informations.

   ![Paramètres détaillés de l’archétype](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Cliquez sur **Créer** pour créer le projet de démarrage à l’aide de l’archétype et en validant la branche Git nommée.

Vous avez désormais un projet de base. Vous pouvez maintenant configurer vos pipelines.

## Clientes et clients existants ou en migration {#existing-migrating}

Si vous êtes un client actuel d’Adobe Managed Services (AMS) ou d’AEM sur site et que vous migrez, vous disposez d’un code de projet déjà dans Git ou dans un autre système de contrôle de version.

Dans ce cas, vous pouvez importer votre projet dans le référentiel Git de Cloud Manager.
