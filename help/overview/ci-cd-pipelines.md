---
title: Pipelines CI/CD
description: Découvrez les pipelines CI/CD et comment ils gèrent les déploiements vers les environnements d’évaluation et de production dans Cloud Manager.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
TQID: https://experienceleague.adobe.com/BwkZH2MIbXrzSxf0yk9yeDZZIpw7-Ldue-OPQPkWrdg
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
  - id: ff09c71c-26a9-449a-85f8-2aeb8ce96100
subfeature_v2:
  - id: c14b2f98-ee16-4c49-b87b-919c91b01d9d
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 694d3e8dad6e2ba86186a4bf6fdda3739e1041da
workflow-type: tm+mt
source-wordcount: 1122
ht-degree: 50%

---

# Pipelines CI/CD {#ci-cd-pipeline}

Découvrez les pipelines CI/CD et comment ils gèrent les déploiements vers les environnements d’évaluation et de production dans Cloud Manager.

## Vue d’ensemble {#overview}

[!UICONTROL Cloud Manager] comprend un framework d’intégration continue/de diffusion continue (CI/CD) permettant aux équipes d’implémentation de tester et de diffuser rapidement des codes nouveaux ou mis à jour. Les équipes d’implémentation peuvent configurer et démarrer un pipeline CI/CD automatisé. Ce pipeline suit les bonnes pratiques de codage d’Adobe pour effectuer une analyse de code complète et garantir une qualité de code optimale.

Le pipeline CI/CD automatise également les processus de test d’unités et de performances pour accroître l’efficacité du déploiement et identifier de manière proactive les problèmes critiques dont la correction est coûteuse après le déploiement. Les équipes d’implémentation peuvent avoir accès à un rapport complet sur les performances du code afin d’avoir une vue d’ensemble des impacts potentiels sur les indicateurs de performance clés et les validations de sécurité critiques en cas de déploiement du code en production.

## À propos du processus de pipeline {#pipeline-process}

Le diagramme suivant illustre ce qui se produit une fois qu’une version est déclenchée dans [!UICONTROL Cloud Manager] à l’aide d’un pipeline.

![Processus de pipeline](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Étape du pipeline | Description |
| --- | --- |
| &#x200B;1. Démarrer une version | Une personne responsable de déploiement déclenche une version manuellement, avec une validation Git, ou selon un planning récurrent. |
| &#x200B;2. Création d’une balise de version | [!UICONTROL Cloud Manager] crée une balise Git pour marquer la version à l’aide d’un numéro de version généré automatiquement, par exemple `2018.531.245527.0000001222`. |
| &#x200B;3. Version créée en tant que avec version générée automatiquement | [!UICONTROL Cloud Manager] génère l’application avec le numéro de version nouvellement attribué. |
| &#x200B;4. Évaluation de la qualité du code | [!UICONTROL Cloud Manager] analyse le code source et fournit un résumé avant que le code puisse être déployé dans l’environnement d’évaluation. |
| &#x200B;5. Artefacts avec version stockés | Les artefacts de version sont stockés pour une utilisation ultérieure dans les étapes de déploiement. |
| &#x200B;6. Déploiement automatique des artefacts dans l’évaluation AMS AEM | L’artefact de version est déployé dans l’environnement d’évaluation. |
| &#x200B;7. Déclencher des tests automatisés | [!UICONTROL Cloud Manager] exécute les tests de performance et de sécurité sur l’artefact. |
| &#x200B;8. Déploiement du déclencheur de production | Une fois les tests automatisés terminés, [!UICONTROL Cloud Manager] démarre le déploiement en production. |
| &#x200B;9.  obtient un ou plusieurs artefacts à déployer | [!UICONTROL Cloud Manager] extrait les artefacts de version stockés. |
| &#x200B;10. Déploiement des artefacts en production | Les artefacts de version sont déployés dans l’environnement de production. |

### Sources de code {#code-sources}

Les pipelines peuvent également différer selon le type de code qu’ils déploient, en plus de la production et de la non-production.

* **[Pipelines full stack](#full-stack-pipeline)** - Déployez l’ensemble du code de l’application AEM avec les configurations HTTPD/Dispatcher.
* **[Pipelines de configuration de niveau web](#web-tier-config-pipelines)** - Déployez uniquement les configurations HTTPD/Dispatcher.

### Pipelines full stack {#full-stack-pipeline}

Les pipelines full stack déploient l’ensemble du code de l’application AEM sur le runtime AEM et, par défaut, déploient également les configurations de niveau web.

Les restrictions suivantes s’appliquent.

* Un utilisateur doit être connecté avec le rôle **Responsable de déploiement** pour configurer ou exécuter des pipelines.
* À tout moment, il ne peut y avoir qu’un seul pipeline full stack par environnement.

La section suivante décrit l’interaction du pipeline full stack avec un [pipeline de configuration de niveau web](#web-tier-config-pipelines).

* Le pipeline full stack pour un environnement ignore la configuration Dispatcher si le pipeline de configuration de niveau web correspondant existe.
* Si le pipeline de configuration de niveau web correspondant à l’environnement n’existe pas, l’utilisateur peut configurer le pipeline full stack pour inclure ou ignorer la configuration Dispatcher.

Les pipelines full stack peuvent être des pipelines de type qualité de code ou déploiement.

#### Configuration des pipelines full stack {#configure-full-stack}

Voir [Ajouter un pipeline de production](/help/using/production-pipelines.md#full-stack-code).Voir [Ajouter un pipeline hors production](/help/using/non-production-pipelines.md#add-non-production-pipeline).

### Pipelines de configuration de niveau web {#web-tier-config-pipelines}

Les pipelines de configuration de niveau web permettent le déploiement exclusif de la configuration HTTPD/Dispatcher pour l’exécution d’AEM, en la découplant des autres modifications de code. Il s’agit d’un pipeline rationalisé qui fournit aux utilisateurs qui souhaitent déployer uniquement les modifications de configuration de Dispatcher une méthode accélérée pour le faire en quelques minutes seulement.

>[!TIP]
>
>Les pipelines de configuration de niveau web vous permettent de stocker votre configuration web au même emplacement source ou à un autre emplacement que le pipeline de pile complète, en fonction de ce qui convient le mieux à votre structure de projet.

Les restrictions suivantes s’appliquent.

* Un utilisateur doit être connecté avec le rôle **Responsable de déploiement** pour configurer ou exécuter des pipelines.
* À tout moment, il ne peut y avoir qu’un seul pipeline de configuration de niveau web par environnement.
* L’utilisateur ne peut pas configurer de pipeline de configuration de niveau web lorsque le pipeline full stack correspondant est en cours d’exécution.

La section suivante décrit l’interaction du pipeline de configuration de niveau web avec le [pipeline de pile complète](#full-stack-pipeline).

* Si un pipeline de configuration de niveau web n’est pas configuré pour un environnement, l’utilisateur peut choisir d’inclure ou d’ignorer la configuration Dispatcher lors de la configuration du pipeline full stack.
* Une fois qu’un pipeline de configuration de niveau web est configuré pour un environnement, son pipeline full stack correspondant (s’il en existe un) ignore la configuration Dispatcher lors de l’exécution et du déploiement.
* Après la suppression d’un pipeline de configuration de niveau web, son pipeline full stack correspondant (s’il en existe un) est réinitialisé pour déployer des configurations Dispatcher lors de son exécution.

>[!NOTE]
>
>Pour les programmes AMS dont le déploiement bleu/vert est activé, les mises à jour de niveau web utilisent le déploiement en continu par défaut. Utilisez un pipeline de pile complète si vous avez besoin d’un déploiement bleu/vert pour les modifications de niveau web.

#### Configuration des pipelines de niveau web {#configure-web-tier}

Voir [Ajouter un pipeline de production](/help/using/production-pipelines.md#web-tier-config).Voir [Ajouter un pipeline hors production](/help/using/non-production-pipelines.md#add-non-production-pipeline).

### Versions plus rapides à l’aide de la création dynamique {#use=smart-build}

Cloud Manager utilise désormais une stratégie de création optimisée appelée **Smart Build**, qui utilise la mise en cache au niveau du module pour accélérer le processus de création. Lors de chaque génération, seuls les modules qui ont été modifiés sont reconstruits, tandis que les modules inchangés sont réutilisés à partir du cache.

La génération intelligente est disponible pour les pipelines de qualité de code et de déploiement de pile complète (développement, évaluation, production).

Voir [Ajouter un pipeline hors production](/help/using/non-production-pipelines.md#add-non-production-pipeline) et [À propos de l’utilisation de la création intelligente dans un pipeline hors production](/help/using/non-production-pipelines.md#about-smart-build).


### Configurer un pipeline CI/CD {#how-to-setup-a-ci-cd-pipeline}

Pour en savoir plus sur la configuration du pipeline, voir les documents [Configurer des pipelines de production](/help/using/production-pipelines.md) et [Configurer des pipelines hors production](/help/using/non-production-pipelines.md).

## Points de contrôle de qualité {#quality-gates}

Le pipeline CI/CD fournit des points de contrôle de qualité, ou critères d’acceptation, qui doivent être respectés avant que le code ne puisse passer de l’environnement d’évaluation à l’environnement de déploiement. Le pipeline comprend trois points de contrôle :

* Qualité du code
* Test de performance
* Tests de sécurité

Pour chacun de ces points de contrôle, trois niveaux de problèmes sont identifiés :

* **Critique** : les problèmes critiques identifiés par le point de contrôle entraînent un échec immédiat du pipeline.
* **Important** : les problèmes importants identifiés par le point de contrôle entraînent la suspension du pipeline. Une personne responsable de déploiement, de projet ou propriétaire d’entreprise peut contourner les problèmes, ce qui permet au pipeline de se poursuivre. Au contraire, les problèmes peuvent également être acceptés, ce qui entraîne l’arrêt du pipeline avec un échec.
* **Informations** : les problèmes d’informations identifiés par le point de contrôle sont fournis à titre purement informatif et sans incidence sur l’exécution du pipeline.

L’exemple suivant est une analyse du code avec les problèmes identifiés.

![Exemple d’analyse de code](/help/assets/quality-gate-failed.png)

### Configurer des points de contrôle {#how-to-setup-gates}

Consultez le document [Configurer des pipelines de production](/help/using/production-pipelines.md) pour obtenir plus d’informations sur la configuration de points de contrôle concernant votre code, la qualité et les performances.
