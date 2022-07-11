---
title: Phase d’évaluation
seo-title: Evaluation Phase
description: Découvrez comment la phase d’évaluation de l’assistant de mise à jour du produit évalue la complexité de la mise à niveau à l’aide du détecteur de motifs.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: ce2145da3b9e605e8a41bac28df520f14e255557
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 28%

---


# Phase d’évaluation {#evaluation}

La première phase de l’assistant de mise à jour du produit est la suivante : **[!UICONTROL Évaluation]** phase , qui évalue la complexité de la mise à niveau à l’aide du détecteur de motifs directement dans l’assistant. A la fin de cette étape, vous aurez accès à un rapport d&#39;évaluation.

Le rapport généré vous permet de vérifier l’éligibilité de l’instance d’auteur à la mise à niveau en détectant les motifs qui :

* enfreignent certaines règles concernant les zones qui seront affectées ou écrasées par la mise à niveau.

* Utilisez une fonctionnalité AEM 6.x ou une API qui n’est pas rétrocompatible avec la nouvelle version d’AEM et qui peut potentiellement échouer après la mise à niveau.

Le rapport sert d’évaluation de l’effort de développement impliqué dans la mise à niveau vers Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Pour en savoir plus sur le détecteur de motifs, consultez le document . [Évaluation de la complexité de la mise à niveau à l’aide du détecteur de motifs.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=en)

## Exécution de l’évaluation {#running}

Le détecteur de motifs peut s’exécuter dans n’importe quel environnement. Toutefois, afin d’augmenter le taux de détection et d’éviter tout ralentissement sur les instances critiques de l’entreprise, Cloud Manager l’exécute dans l’environnement d’évaluation de l’instance d’auteur.

Pour générer le rapport d’évaluation, procédez comme suit.

1. Démarrez l’assistant comme décrit dans le document. [Assistant de mise à jour du produit.](/help/product-update-wizard/overview.md)

1. Cliquez sur **[!UICONTROL Exécuter une évaluation]**.

   ![Exécution de l’évaluation](/help/assets/Run-Evaluation.png)

1. L’assistant vous informe de l’état de votre action. Vous remarquerez les états **en cours** ou **terminé** le cas échéant une fois le rapport d’évaluation généré.

1. Une fois le rapport généré, vous pouvez cliquer sur **[!UICONTROL Télécharger le rapport]** pour enregistrer une copie.

   ![Rapport créé](/help/assets/Evaluation-1.png)

La version actuelle de l’assistant de mise à jour du produit de Cloud Manager prend uniquement en charge la phase **Évaluation**. Les quatre autres phases appelées **Correction**, **Exécution**, **Validation** et **Achèvement** seront bientôt disponibles.
