---
title: Configuration de la vérification GitHub pour les référentiels privés
description: Découvrez comment contrôler les pipelines créés automatiquement pour valider chaque demande d’extraction dans un référentiel privé.
source-git-commit: 85c1e22609dc5646d3de0ccc71e9423d4243e13a
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 7%

---


# Configuration de la vérification GitHub pour les référentiels privés {#github-check-config}

Découvrez comment contrôler les pipelines créés automatiquement pour valider chaque demande d’extraction dans un référentiel privé.

## Configuration des contrôles GitHub {#configuration}

Lorsque vous utilisez [référentiels privés,](private-repositories.md#using) a [pipeline de qualité de code de pile complet](/help/overview/ci-cd-pipelines.md) sera créé automatiquement. Ce pipeline démarre à chaque mise à jour de demande d’extraction.

Vous pouvez contrôler ces contrôles en créant un `.cloudmanager/pr_pipelines.yml` dans la branche par défaut du référentiel privé.

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
|---|---|---|---|
| `shouldDeletePreviousComment` | `true` ou `false` | `false` | Si vous souhaitez conserver uniquement le dernier commentaire avec les résultats de l’analyse du code sur cette requête d’extraction GitHub ou conserver tous les |
| `type` | `CI_CD` | n/a | Définit le comportement d’un pipeline CI/CD |
| `template.programID` | Entier | Aucune variable de pipeline n’est réutilisée | Peut être utilisé pour réutiliser la variable [variables de pipeline](/help/getting-started/build-environment.md#pipeline-variables) qui sont définis sur l’un des pipelines existants qui sont créés automatiquement par chaque requête de tirage. |
| `template.pipelineID` | Entier | Aucune variable de pipeline n’est réutilisée | Peut être utilisé pour réutiliser la variable [variables de pipeline](/help/getting-started/build-environment.md#pipeline-variables) qui sont définis sur l’un des pipelines existants qui sont créés automatiquement par chaque requête de tirage. |
| `namePrefix` | Chaîne | `Full Stack Code Quality Pipeline for PR` | Utilisé pour définir le nom du pipeline créé automatiquement |
| `importantMetricsFailureBehavior` | `CONTINUE` ou `FAIL` ou `PAUSE` | `CONTINUE` | Définition du comportement de mesure important du pipeline<br>`CONTINUE` = Si une mesure importante échoue, le pipeline avancera automatiquement<br>`FAIL` = Le pipeline se termine avec un état ÉCHEC si une mesure importante échoue<br>`PAUSE` = L’étape d’analyse du code recevra un état D’ATTENTE lorsqu’une mesure importante échoue et doit être reprise manuellement. |
