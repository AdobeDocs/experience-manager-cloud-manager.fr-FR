---
title: Pipelines CI/CD
description: Découvrez les pipelines CI/CD et comment ils gèrent les déploiements vers les environnements d’évaluation et de production dans Cloud Manager.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 30%

---


# Pipelines CI/CD {#ci-cd-pipeline}

Découvrez les pipelines CI/CD et comment ils gèrent les déploiements vers les environnements d’évaluation et de production dans Cloud Manager.

## Présentation {#overview}

[!UICONTROL Cloud Manager] comprend une structure d’intégration/diffusion continue (CI/CD) qui permet aux équipes d’implémentation de tester et de diffuser rapidement du code nouveau ou mis à jour. Par exemple, les équipes d’implémentation peuvent configurer et démarrer un pipeline CI/CD automatisé qui utilise les bonnes pratiques en matière de codage Adobe afin d’analyser précisément le code et d’en garantir la qualité.

Le pipeline CI/CD automatise également les processus de test d’unité et de performance afin d’accroître l’efficacité du déploiement et d’identifier de manière proactive les problèmes critiques qui coûtent cher à résoudre après le déploiement. Les équipes d’implémentation peuvent avoir accès à un rapport complet sur les performances du code afin d’avoir une vue d’ensemble des impacts potentiels sur les indicateurs de performance clés et les validations de sécurité critiques en cas de déploiement du code en production.

## Processus du pipeline {#pipeline-process}

Ce diagramme illustre ce qui se passe une fois qu’une version est déclenchée dans [!UICONTROL Cloud Manager] à l’aide d’un pipeline.

![Processus de pipeline](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Étape du pipeline | Description |
|---|---|
| 1. Démarrage d’une version | Un responsable de déploiement déclenche une version manuellement, avec une validation Git ou selon un calendrier récurrent. |
| 2. Création d’une balise de version | [!UICONTROL Cloud Manager] crée une balise git pour marquer la version à l’aide d’un numéro de version généré automatiquement, par exemple `2018.531.245527.0000001222`. |
| 3. Créé en tant que version avec génération automatique | [!UICONTROL Cloud Manager] génère l’application avec le numéro de version nouvellement attribué. |
| 4. Évaluation de la qualité du code | [!UICONTROL Cloud Manager] analyse le code source et fournit un résumé avant que le code puisse être déployé dans l’environnement d’évaluation. |
| 5. Artefact(s) versionné(s) stocké(s) | Les artefacts de version sont stockés pour une utilisation ultérieure dans les étapes de déploiement. |
| 6. Déploiement automatique du ou des artefacts vers l’AEM d’évaluation AMS | L’artefact de version est déployé dans l’environnement d’évaluation. |
| 7. Déclenchement de tests automatisés | [!UICONTROL Cloud Manager] exécute des tests de performance et de sécurité sur l’artefact. |
| 8. Déploiement du déclencheur de production | Une fois les tests automatisés terminés, [!UICONTROL Cloud Manager] lance le déploiement en production. |
| 9. [!UICONTROL Cloud Manager] obtient les artefacts à déployer | [!UICONTROL Cloud Manager] extrait les artefacts de version stockés. |
| 10. Déploiement d’artefacts en production | Les artefacts de version sont déployés dans l’environnement de production. |

### Configuration d’un pipeline CI/CD {#how-to-setup-a-ci-cd-pipeline}

Pour en savoir plus sur la configuration du pipeline, consultez les documents [Configuration de pipelines de production](/help/using/production-pipelines.md) et [Configuration de pipelines hors production](/help/using/non-production-pipelines.md).

## Points de contrôle de qualité {#quality-gates}

Le pipeline CI/CD fournit des points de contrôle de qualité, ou critères d’acceptation, qui doivent être remplis avant que le code puisse être déplacé de l’environnement d’évaluation vers l’environnement de déploiement. Le pipeline comprend trois points de contrôle :

* Qualité du code
* Test de performance
* Test de sécurité

Pour chacun de ces points de contrôle, trois niveaux de problèmes peuvent être identifiés :

* **Critique** - Les problèmes critiques identifiés par le point de contrôle entraînent l’échec immédiat du pipeline.
* **Important** - Les problèmes importants identifiés par le point de contrôle entraînent la suspension du pipeline. Un responsable de déploiement, un responsable de projet ou un propriétaire d’entreprise peuvent soit contourner les problèmes, auquel cas le pipeline continue, soit accepter les problèmes, auquel cas le pipeline s’arrête avec un échec.
* **Informations** - Les problèmes d’informations identifiés par le point de contrôle sont fournis uniquement à titre d’information et n’ont aucune incidence sur l’exécution du pipeline.

Il s’agit d’un exemple d’analyse du code avec les problèmes identifiés.

![Exemple d’analyse de code](/help/assets/quality-gate-failed.png)

### Configuration des points de contrôle {#how-to-setup-gates}

Consultez le document [Configuration de pipelines de production](/help/using/production-pipelines.md) pour obtenir plus d’informations sur la configuration de points de contrôle concernant votre code, la qualité et les performances.
