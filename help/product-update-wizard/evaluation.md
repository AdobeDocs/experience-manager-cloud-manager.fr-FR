---
title: Phase d’évaluation
seo-title: Evaluation Phase
description: Découvrez comment la phase d’évaluation de l’assistant de mise à jour du produit évalue la complexité de la mise à niveau à l’aide de la détection de motifs.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 75%

---


# Phase d’évaluation {#evaluation}

La première phase de l’assistant de mise à jour du produit est la phase d’**[!UICONTROL Évaluation]**, qui évalue la complexité de la mise à niveau à l’aide de la détection de motifs directement dans l’assistant. À la fin de cette étape, vous avez accès au rapport d’évaluation.

Le rapport généré permet de vérifier l’éligibilité de l’instance d’auteur pour la mise à niveau en détectant les motifs qui :

* enfreignent certaines règles concernant les zones qui seront affectées ou remplacées par la mise à niveau.

* utilisent une fonctionnalité d’AEM 6.x ou une API non rétrocompatible avec la nouvelle version d’AEM et qui peut potentiellement échouer après la mise à niveau.

Ce rapport sert à évaluer l’ampleur des tâches de développement nécessaires pour effectuer une mise à niveau vers Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Pour en savoir plus sur le détecteur de motifs, voir [Évaluation de la complexité de la mise à niveau à l’aide du détecteur de motifs](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=fr).

## Exécution du rapport d’évaluation {#running}

Le détecteur de motifs peut s’exécuter dans n’importe quel environnement. Toutefois, afin d’augmenter le taux de détection et d’éviter tout ralentissement des instances professionnelles essentielles, Cloud Manager l’exécutera dans l’environnement d’évaluation de l’instance d’auteur.

**Pour exécuter le rapport d’évaluation :**

1. Démarrez l’assistant comme décrit dans le document [Assistant de mise à jour du produit](/help/product-update-wizard/overview.md).

1. Cliquez sur **[!UICONTROL Exécuter l’évaluation]**.

   ![Exécuter une évaluation](/help/assets/Run-Evaluation.png)

1. L’assistant vous informe de l’état de votre action. Notez **En cours** ou **terminé** comme applicable lorsque le rapport d’évaluation est en cours de génération.

1. Une fois le rapport généré, vous pouvez cliquer sur **[!UICONTROL Télécharger le rapport]** pour enregistrer une copie.

   ![Rapport créé](/help/assets/Evaluation-1.png)

La version actuelle de l’assistant de mise à jour du produit de Cloud Manager prend uniquement en charge la phase **Évaluation**. Les quatre autres phases appelées **Correction**, **Exécution**, **Validation** et **Achèvement** seront bientôt disponibles.
