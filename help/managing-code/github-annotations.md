---
title: Annotations de la vérification GitHub
description: Découvrez comment GitHub vérifie l’annotation des relations publiques pour vos référentiels privés afin de vous fournir des commentaires utiles.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 39%

---


# Annotations de vérification GitHub {#github-annotations}

Découvrez comment GitHub vérifie l’annotation des relations publiques pour vos référentiels privés afin de vous fournir des commentaires utiles.

## Vue d’ensemble {#overview}

Si vous utilisez des [référentiels privés](private-repositories.md) pour votre programme Cloud Manager, les contrôles dans GitHub sont automatiquement exécutés pour chaque requête de tirage. Ces vérifications sont annotées avec des informations utiles pour vous aider à comprendre dès que possible les problèmes liés à votre code.

![Exemple d’annotations de vérification GitHub](assets/github-check-annotations.png)

Des problèmes de [qualité du code](/help/using/code-quality-testing.md) détectés par [SonarQube](/help/using/custom-code-quality-rules.md) sont clairement répertoriés.

![Exemple d’annotation de problème de code](assets/github-check-annotations-example.png)

La ligne de code exacte avec le problème est fournie et vous pouvez cliquer dessus pour afficher le code approprié. Ces annotations sont fournies pour tous les problèmes de code, et pas seulement ceux qui ont été modifiés dans la requête de tirage.

![Exemple d’annotation de problème de code](assets/github-check-annotations-example-code.png)

Toutes les lignes annotées sont regroupées dans l’onglet **Fichiers modifiés** de la requête d’extraction GitHub. Les annotations des fichiers qui n’ont pas été modifiés dans la requête d’extraction apparaissent dans leur propre section.

![Exemple d’annotations dans l’onglet Fichiers modifiés](assets/github-check-annotations-files-changed.png)

## Pipelines de qualité du code {#code-quality-pipelines}

Les résultats [Qualité du code](/help/using/code-quality-testing.md) sont également visibles dans le pipeline, que Cloud Manager déclenche automatiquement au bas de l’onglet **Vérifications** . Ils sont également accessibles dans les **Détails** de la vérification de la requête d’extraction.

![Exemple d’annotations](assets/github-check-annotations-code-quality.png)

![Exemple d’annotations](assets/github-check-annotations-code-quality-2.png)

Vous pouvez également visualiser les problèmes sous la forme d’un fichier CSV. Cette méthode peut être récupérée en [ affichant les détails de l’exécution du pipeline dans Cloud Manager](/help/using/managing-pipelines.md).
