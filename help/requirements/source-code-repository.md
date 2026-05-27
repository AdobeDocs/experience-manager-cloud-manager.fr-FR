---
title: Référentiel de code source
description: Découvrez les informations sur le référentiel Git qui est fourni pour chaque programme que vous avez dans Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
TQID: https://experienceleague.adobe.com/hdEpqKW0NluPs-w37SeLzpd-EHJNqb2nfSAMQ35man8
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 254
ht-degree: 100%

---

# Référentiel de code source {#source-code-repository}

Découvrez les informations sur le référentiel Git qui est fourni pour chaque programme que vous avez dans Cloud Manager.

## Référentiel de Cloud Manager {#cloud-manager-repository}

Votre abonnement à [!UICONTROL AEM Managed Services] comprend un référentiel de code source configuré et géré par Adobe. Chaque programme se voit attribuer un référentiel Git unique, où le code associé est stocké et sécurisé.

Il est considéré comme une bonne pratique de toujours utiliser le référentiel Git de Cloud Manager, qui est fourni vide, sans branche configurée ni exemple de projet. Cloud Manager fournit un jeton d’accès privé pour son référentiel Git, ce qui vous permet d’utiliser n’importe quel client Git pour créer des branches, gérer le code, récupérer l’historique de validation, etc.

Pour plus d’informations sur la configuration de branches dans Git, voir la section [Configurer des branches de versions](/help/getting-started/configuring-branches.md).

Pour plus d’informations sur l’utilisation du référentiel Git de Cloud Manager avec le pipeline CI/CD, voir les sections [Configurer des pipelines de production](/help/using/production-pipelines.md) et [Configurer des pipelines hors production](/help/using/non-production-pipelines.md).

## Référentiel On-Premise {#on-premise-repository}

Il se peut que vous possédiez un référentiel Git existant et que vous souhaitiez le conserver, auquel cas vous pouvez utiliser la fonctionnalité de Git pour plusieurs référentiels distants. Le développement quotidien continuerait alors dans votre référentiel Git. Lorsqu’une branche de version est prête pour un déploiement en production, vous pouvez placer votre dernier code dans le référentiel Git de Cloud Manager et déclencher le pipeline CI/CD de Cloud Manager.

Pour afficher les commandes Git courantes, consultez l’[Aide-mémoire Git](https://education.github.com/git-cheat-sheet-education.pdf).
