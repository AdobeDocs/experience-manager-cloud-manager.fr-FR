---
title: Vérifications des demandes de tirage pour les référentiels privés
description: Découvrez comment contrôler les pipelines créés automatiquement afin de valider chaque requête d’extraction dans un référentiel privé.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
TQID: https://experienceleague.adobe.com/duceoXUt2SqWI0ZXzyuqZtszLfJkWr53G5O5ze4nxTY
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 237
ht-degree: 95%

---

# Vérifications des demandes d’extraction pour les référentiels privés {#github-check-config}

<!--OLD TITLE THAT I THOUGHT WAS BETTER Check configuration for private repositories -->

Découvrez comment contrôler les pipelines créés automatiquement afin de valider chaque requête d’extraction dans un référentiel privé.

## Configuration des vérifications de référentiel privé {#configuration}

Lors de l’utilisation de [référentiels privés](private-repositories.md#using), un [pipeline de qualité de code de pile pleine](/help/overview/ci-cd-pipelines.md) est créé automatiquement. Ce pipeline démarre à chaque mise à jour de demande d’extraction.

Vous pouvez contrôler ces vérifications en créant un fichier `.cloudmanager/pr_pipelines.yml` dans la branche par défaut du référentiel privé.

```yaml
pullRequest:
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
| `shouldDeletePreviousComment` | `true` ou `false` | `false` | Conserver uniquement le dernier commentaire avec les résultats de l’analyse du code pour cette requête d’extraction GitHub, ou tout conserver. |
| `type` | `CI_CD` | n/a | Définit le comportement d’un pipeline CI/CD. |
| `template.programID` | Entier | Aucune variable de pipeline n’est réutilisée. | Vous pouvez réutiliser les [variables de pipeline](/help/getting-started/build-environment.md#pipeline-variables) définies sur un pipeline existant, que chaque requête d’extraction crée automatiquement. |
| `template.pipelineID` | Entier | Aucune variable de pipeline n’est réutilisée. | Vous pouvez réutiliser les [variables de pipeline](/help/getting-started/build-environment.md#pipeline-variables) définies sur un pipeline existant, que chaque requête d’extraction crée automatiquement. |
| `namePrefix` | Chaîne | `Full Stack Code Quality Pipeline for PR` | Utilisée pour définir le nom du pipeline créé automatiquement. |
| `importantMetricsFailureBehavior` | `CONTINUE` ou `FAIL` ou `PAUSE` | `CONTINUE` | Définit le comportement en cas d’échec de mesure grave du pipeline.<br>`CONTINUE` = Si une mesure importante échoue, le pipeline se poursuit automatiquement.<br>`FAIL` = Le pipeline se termine avec le statut ÉCHEC si une mesure importante échoue.<br>`PAUSE` = L’étape d’analyse du code reçoit un statut EN ATTENTE lorsqu’une mesure importante échoue et doit être reprise manuellement. |
