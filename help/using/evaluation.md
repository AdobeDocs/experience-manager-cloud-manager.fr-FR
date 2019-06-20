---
title: Evaluation
seo-title: Evaluation
description: 'Cette page sert de point de départ à la phase d''évaluation dans l''Assistant de mise à jour des produits. '
seo-description: Cette page sert de point de départ à la phase d'évaluation dans l'Assistant de mise à jour des produits.
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: 47331787d45fe68144cb90c4b907560fe0079b3c

---


# Evaulation Phase {#evaluation}

Lorsque vous cliquez sur Démarrer la mise à jour, la première phase de l&#39;Assistant de mise à jour des produits est la phase d&#39;évaluation. Au cours de cette phase, vous pouvez évaluer la complexité de la mise à niveau avec le détecteur de modèle accessible directement à partir de l&#39;assistant. A la fin de cette étape, vous avez accès au rapport d&#39;évaluation.

Le rapport généré vous permet de vérifier l&#39;instance d&#39;auteur pour la mise à niveau en détectant les modèles utilisés :

* Enfreindre certaines règles et les domaines qui seront affectés ou remplacés par la mise à niveau.

* Utilisez une fonctionnalité AEM 6. x ou une API qui n&#39;est pas rétrocompatible sur le nouvel AEM et qui peut se briser après la mise à niveau.


Ceci donne une évaluation de l&#39;effort de développement impliqué dans la mise à niveau vers Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>To learn more about pattern detector, refer to [Assessing the Upgrade Complexity with the Pattern Detector](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Running the Evaluator {#running-evaluator}

Suivez les étapes ci-dessous pour exécuter l&#39;évaluateur :

1. Select [!UICONTROL Run evaluation] to run the pattern detector. Le détecteur de motif peut s&#39;exécuter dans n&#39;importe quel environnement. Toutefois, afin d&#39;augmenter le taux de détection et d&#39;éviter tout ralentissement des instances critiques, Cloud Manager l&#39;exécute sur l&#39;environnement d&#39;évaluation de l&#39;instance d&#39;auteur.

1. L&#39;assistant vous informe de l&#39;état de votre action. You will notice **In progress** or **completed** as applicable when the evaluation report is being generated.

Once the report is generated, you can select [!UICONTROL Download] to save a copy of the evaluation report.

>[!NOTE]
>The other four phases succeeding **Evaluation** namely **Remediation**, **Execution**, **Validation**, and **Completion** are coming soon and are not available in the current release.
