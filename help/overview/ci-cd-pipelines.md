---
title: Pipelines CI/CD
description: Découvrez les pipelines CI/CD et comment ils gèrent les déploiements vers les environnements d’évaluation et de production dans Cloud Manager.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '562'
ht-degree: 100%

---


# Pipelines CI/CD {#ci-cd-pipeline}

Découvrez les pipelines CI/CD et comment ils gèrent les déploiements vers les environnements d’évaluation et de production dans Cloud Manager.

## Vue d’ensemble {#overview}

[!UICONTROL Cloud Manager] comprend un framework d’intégration continue/de diffusion continue (CI/CD) permettant aux équipes d’implémentation de tester et de diffuser rapidement des codes nouveaux ou mis à jour. Les équipes d’implémentation peuvent configurer et démarrer un pipeline CI/CD automatisé. Ce pipeline suit les bonnes pratiques de codage d’Adobe pour effectuer une analyse de code complète et garantir une qualité de code optimale.

Le pipeline CI/CD automatise également les processus de test d’unités et de performances pour accroître l’efficacité du déploiement et identifier de manière proactive les problèmes critiques dont la correction est coûteuse après le déploiement. Les équipes d’implémentation peuvent avoir accès à un rapport complet sur les performances du code afin d’avoir une vue d’ensemble des impacts potentiels sur les indicateurs de performance clés et les validations de sécurité critiques en cas de déploiement du code en production.

## À propos du processus de pipeline {#pipeline-process}

Le diagramme suivant illustre ce qui se produit une fois qu’une version est déclenchée dans [!UICONTROL Cloud Manager] à l’aide d’un pipeline.

![Processus de pipeline](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Étape du pipeline | Description |
| --- | --- |
| 1. Démarrage d’une version | Une personne responsable de déploiement déclenche une version manuellement, avec une validation Git, ou selon un planning récurrent. |
| 2. Création d’une balise de version | [!UICONTROL Cloud Manager] crée une balise Git pour marquer la version à l’aide d’un numéro de version généré automatiquement, par exemple `2018.531.245527.0000001222`. |
| 3. Création en tant que version avec une version générée automatiquement | [!UICONTROL Cloud Manager] génère l’application avec le numéro de version nouvellement attribué. |
| 4. Évaluation de la qualité du code | [!UICONTROL Cloud Manager] analyse le code source et fournit un résumé avant que le code puisse être déployé dans l’environnement d’évaluation. |
| 5. Artefacts versionnés stockés | Les artefacts de version sont stockés pour une utilisation ultérieure dans les étapes de déploiement. |
| 6. Déploiement automatique des artefacts dans l’évaluation AMS AEM | L’artefact de version est déployé dans l’environnement d’évaluation. |
| 7. Déclenchement des tests automatisés | [!UICONTROL Cloud Manager] exécute les tests de performance et de sécurité sur l’artefact. |
| 8. Déploiement du déclencheur de production | Une fois les tests automatisés terminés, [!UICONTROL Cloud Manager] démarre le déploiement en production. |
| 9. [!UICONTROL Cloud Manager] reçoit un ou plusieurs artefacts à déployer | [!UICONTROL Cloud Manager] extrait les artefacts de version stockés. |
| 10. Déploiement des artefacts en production | Les artefacts de version sont déployés dans l’environnement de production. |

### Configurer un pipeline CI/CD {#how-to-setup-a-ci-cd-pipeline}

Pour en savoir plus sur la configuration du pipeline, voir les documents [Configurer des pipelines de production](/help/using/production-pipelines.md) et [Configurer des pipelines hors production](/help/using/non-production-pipelines.md).

## Points de contrôle de qualité {#quality-gates}

Le pipeline CI/CD fournit des points de contrôle de qualité, ou critères d’acceptation, qui doivent être respectés avant que le code ne puisse passer de l’environnement d’évaluation à l’environnement de déploiement. Le pipeline comprend trois points de contrôle :

* Qualité du code
* Test de performance
* Test de sécurité

Pour chacun de ces points de contrôle, trois niveaux de problèmes sont identifiés :

* **Critique** : les problèmes critiques identifiés par le point de contrôle entraînent un échec immédiat du pipeline.
* **Important** : les problèmes importants identifiés par le point de contrôle entraînent la suspension du pipeline. Une personne responsable de déploiement, de projet ou propriétaire d’entreprise peut contourner les problèmes, ce qui permet au pipeline de se poursuivre. Au contraire, les problèmes peuvent également être acceptés, ce qui entraîne l’arrêt du pipeline avec un échec.
* **Informations** : les problèmes d’informations identifiés par le point de contrôle sont fournis à titre purement informatif et sans incidence sur l’exécution du pipeline.

L’exemple suivant est une analyse du code avec les problèmes identifiés.

![Exemple d’analyse de code](/help/assets/quality-gate-failed.png)

### Configurer des points de contrôle {#how-to-setup-gates}

Consultez le document [Configurer des pipelines de production](/help/using/production-pipelines.md) pour obtenir plus d’informations sur la configuration de points de contrôle concernant votre code, la qualité et les performances.
