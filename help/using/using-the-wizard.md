---
title: Utilisation de l’assistant
description: Suivez cette page pour savoir comment utiliser l’assistant afin de créer un projet d’application AEM
feature: Prise en main
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 100%

---


# Utilisation de l’assistant {#using-wizard-to-create-an-aem-application-project}

Lorsque les clients se connectent à Cloud Manager, ils reçoivent un référentiel git vide. Les clients Adobe Managed Services (AMS) actuels (ou clients AEM sur site qui migrent vers AMS) auront généralement déjà leur code de projet dans git (ou un autre système de contrôle de version) et importeront leur projet dans le référentiel git Cloud Manager. Toutefois, les nouveaux clients n’ont pas de projets existants.

Pour faciliter la prise en main des nouveaux clients, Cloud Manager peut désormais créer un projet AEM minimal comme point de départ. Ce processus est basé sur l’[**AEM Project Archetype**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Suivez les étapes ci-dessous pour créer un projet d’application AEM dans Cloud Manager :

1. Une fois que vous vous êtes connecté à Cloud Manager et que la configuration du programme de base est terminée, une vignette d’appel à action spéciale s’affiche sur l’écran **Vue d’ensemble**, si le référentiel est vide.

   ![](assets/image2018-10-3_14-29-44.png)

1. Cliquez sur **Créer** pour ouvrir une boîte de dialogue qui permet à l’utilisateur de fournir les paramètres requis par AEM Project Archetype. Dans le formulaire par défaut, la boîte de dialogue demande deux valeurs :

   * **Titre** : par défaut, cette valeur est définie sur le *nom du programme*.

   * **Nouveau nom de branche** : par défaut, il s’agit d’un *gabarit*.

   ![](assets/screen_shot_2018-10-08at55825am.png)

   La boîte de dialogue comporte un tiroir qui peut être ouvert en cliquant sur la poignée vers le bas de la boîte de dialogue. Sous sa forme développée, la boîte de dialogue affiche tous les paramètres de configuration d’Archetype. La plupart de ces paramètres comportent des valeurs par défaut générées en fonction du **titre**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Par exemple, si le **titre** est ***We.Finance***, le paramètre d’identifiant de base de Maven Artifact est généré sous la forme de ***com.wefinance***. Si vous le souhaitez, vous pouvez modifier ces valeurs.
   >
   >
   >Par exemple, vous pouvez passer de la valeur générée ***com.wefinance*** à ***net.wefinance***.

1. Cliquez sur **Créer** à l’étape précédente pour créer le projet de démarrage en utilisant l’archétype et en validant la branche git nommée. Vous pouvez ensuite configurer le pipeline.