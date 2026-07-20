---
title: Annotations de la vérification GitHub
description: Découvrez comment les vérifications GitHub annotent les requêtes d’extraction de vos référentiels privés afin de vous fournir des commentaires utiles.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 147eec6368875aabb252d759909c0309a82ef3db
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 32%

---


# Annotations de la vérification GitHub {#github-annotations}

Découvrez comment GitHub vérifie les RP annotés pour vos référentiels privés afin de vous fournir des commentaires.

## Vue d’ensemble {#overview}

Si vous utilisez des [référentiels privés](private-repositories.md) pour votre programme Cloud Manager, consigne automatiquement l’exécution GitHub pour chaque demande d’extraction. Ces vérifications sont annotées avec des informations pour vous aider à identifier les problèmes liés à votre code dès que possible.

![Exemple d’annotations de vérification GitHub](assets/github-check-annotations.png)

Des problèmes de [qualité du code](/help/using/code-quality-testing.md) détectés par [SonarQube](/help/using/custom-code-quality-rules.md) sont clairement répertoriés.

![Exemple d’annotation de problème de code](assets/github-check-annotations-example.png)

La ligne exacte de code avec le problème est fournie et vous pouvez la sélectionner pour afficher le code approprié. Ces annotations sont fournies pour tous les problèmes de code, et pas seulement pour ceux de la requête de tirage.

![Exemple d’annotation de problème de code](assets/github-check-annotations-example-code.png)

Toutes les lignes annotées sont regroupées dans l’onglet **Fichiers modifiés** de la requête d’extraction GitHub. Les annotations des fichiers non modifiés dans la demande de tirage apparaissent dans une section distincte.

![Exemple d’annotations dans l’onglet Fichiers modifiés](assets/github-check-annotations-files-changed.png)

## Pipelines de qualité du code {#code-quality-pipelines}

Les résultats [Qualité du code](/help/using/code-quality-testing.md) sont également visibles dans le pipeline, que Cloud Manager déclenche automatiquement, au bas de l’onglet **Contrôles**. Elle est également accessible à partir des **Détails** de la vérification de la requête de tirage.

![Exemple d’annotations](assets/github-check-annotations-code-quality.png)

![Exemple d’annotations](assets/github-check-annotations-code-quality-2.png)

Vous pouvez également afficher les problèmes sous la forme d’un fichier CSV. Vous pouvez accéder à ces informations en [affichant les détails de l’exécution du pipeline dans Cloud Manager](/help/using/managing-pipelines.md).
