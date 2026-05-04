---
title: Phase d’évaluation
seo-title: Evaluation Phase
description: Découvrez comment la phase d’évaluation de l’assistant de mise à jour du produit évalue la complexité de la mise à niveau à l’aide de la détection de motifs.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
TQID: https://experienceleague.adobe.com/dj-Wnq9FagNI3mzzVHcUH-sOufzb02D0juHqhtgpon0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 270
ht-degree: 59%

---

# Phase d’évaluation {#evaluation}

La première phase de l’assistant de mise à jour du produit est la phase **[!UICONTROL Évaluation]**. Il exécute la détection des motifs dans l’assistant pour évaluer la complexité de la mise à niveau. À la fin de cette étape, vous pouvez afficher le rapport d’évaluation.

Le rapport vérifie que l’instance de création est prête pour la mise à niveau en détectant des motifs pour les éléments suivants :

* Violations de règles dans les zones affectées ou remplacées par la mise à niveau.
* Il utilise des fonctionnalités ou des API AEM 6.x qui ne sont pas rétrocompatibles et qui peuvent échouer après la mise à niveau.

Ce rapport permet d’estimer l’effort de développement requis pour effectuer la mise à niveau vers Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Pour en savoir plus sur la détection de motifs, voir la section [Évaluer la complexité de la mise à niveau à l’aide de la détection de motifs](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector).

## Exécuter le rapport d’évaluation {#running}

La détection de motifs peut s’exécuter dans n’importe quel environnement. Toutefois, afin d’augmenter le taux de détection et d’éviter tout ralentissement des instances professionnelles essentielles, Cloud Manager l’exécute dans l’environnement d’évaluation de l’instance de création.

**Pour exécuter le rapport d’évaluation, procédez comme suit :**

1. Démarrez l’assistant tel que décrit dans le document [Assistant de mise à jour du produit](/help/product-update-wizard/overview.md).

1. Cliquez sur **[!UICONTROL Exécuter une évaluation]**.

   ![Exécuter une évaluation](/help/assets/Run-Evaluation.png)

1. L’assistant vous informe de l’état de votre action. Vous remarquerez les états **En cours** ou **Terminé** le cas échéant une fois le rapport d’évaluation généré.

1. Une fois le rapport généré, vous pouvez cliquer sur **[!UICONTROL Télécharger le rapport]** pour enregistrer une copie.

   ![Rapport créé](/help/assets/Evaluation-1.png)

L’assistant de mise à jour du produit en cours dans Cloud Manager prend uniquement en charge la phase **Évaluation**. Les quatre autres phases appelées **Correction**, **Exécution**, **Validation** et **Achèvement** seront bientôt disponibles.
