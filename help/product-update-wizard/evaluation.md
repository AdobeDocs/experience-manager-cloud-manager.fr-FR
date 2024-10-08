---
title: Phase d’évaluation
seo-title: Evaluation Phase
description: Découvrez comment la phase d’évaluation de l’assistant de mise à jour du produit évalue la complexité de la mise à niveau à l’aide de la détection de motifs.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: ht
source-wordcount: '279'
ht-degree: 100%

---


# Phase d’évaluation {#evaluation}

La première phase de l’assistant de mise à jour du produit est la phase d’**[!UICONTROL évaluation]**, qui évalue la complexité de la mise à niveau à l’aide de la détection de motifs directement dans l’assistant. À la fin de cette étape, vous pouvez accéder au rapport d’évaluation.

Le rapport généré vous permet de vérifier l’éligibilité de l’instance de création pour la mise à niveau en détectant les motifs qui :

* enfreignent certaines règles liées aux zones affectées ou remplacées par la mise à niveau ;

* utilisent une fonctionnalité d’AEM 6.x ou une API non rétrocompatible avec la nouvelle version d’AEM et qui peut potentiellement échouer après la mise à niveau.

Ce rapport sert à évaluer l’ampleur des tâches de développement nécessaires pour effectuer une mise à niveau vers Adobe Experience Manager (AEM) 6.5.

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

La version actuelle de l’assistant de mise à jour du produit de Cloud Manager prend uniquement en charge la phase **Évaluation**. Les quatre autres phases appelées **Correction**, **Exécution**, **Validation** et **Achèvement** seront bientôt disponibles.
