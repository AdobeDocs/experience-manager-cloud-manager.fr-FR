---
title: Configuration de la vérification GitHub pour les référentiels privés
description: Découvrez comment contrôler les pipelines créés automatiquement afin de valider chaque demande d’extraction dans un référentiel privé.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 39%

---

# Configuration des contrôles GitHub pour les référentiels privés {#github-check-config}

Découvrez comment contrôler les pipelines créés automatiquement afin de valider chaque demande d’extraction dans un référentiel privé.

## Configuration des contrôles GitHub {#configuration}

Lors de l’utilisation de [référentiels privés](private-repositories.md#using), un [pipeline de qualité de code de pile complet](/help/overview/ci-cd-pipelines.md) est créé automatiquement. Ce pipeline démarre à chaque mise à jour de demande d’extraction.

Vous pouvez contrôler ces vérifications en créant un fichier `.cloudmanager/pr_pipelines.yml` dans la branche par défaut du référentiel privé.

```yaml
github:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR 
    importantMetricsFailureBehavior: CONTINUE
```

| Paramètre | Valeurs possibles | Valeur par défaut | Description |
| --- | --- | --- | --- |
| `shouldDeletePreviousComment` | `true` ou `false` | `false` | Si vous souhaitez conserver uniquement le dernier commentaire avec les résultats de l’analyse du code sur cette demande d’extraction GitHub ou conserver tout. |
| `type` | `CI_CD` | n/a | Définit le comportement d’un pipeline CI/CD. |
| `template.programID` | Entier | Aucune variable de pipeline n’est réutilisée. | Vous pouvez réutiliser les [variables de pipeline](/help/getting-started/build-environment.md#pipeline-variables) définies sur un pipeline existant, que chaque requête de tirage crée automatiquement. |
| `template.pipelineID` | Entier | Aucune variable de pipeline n’est réutilisée. | Vous pouvez réutiliser les [variables de pipeline](/help/getting-started/build-environment.md#pipeline-variables) définies sur un pipeline existant, que chaque requête de tirage crée automatiquement. |
| `namePrefix` | Chaîne | `Full Stack Code Quality Pipeline for PR` | Utilisé pour définir le nom du pipeline créé automatiquement. |
| `importantMetricsFailureBehavior` | `CONTINUE` ou `FAIL` ou `PAUSE` | `CONTINUE` | Définit le comportement de mesure important du pipeline<br>`CONTINUE` = Si une mesure importante échoue, le pipeline se déplace automatiquement<br>`FAIL` = Le pipeline se termine avec un état ÉCHEC si une mesure importante échoue<br>`PAUSE` = L’étape d’analyse du code reçoit un état D’ATTENTE lorsqu’une mesure importante échoue et doit être reprise manuellement. |
