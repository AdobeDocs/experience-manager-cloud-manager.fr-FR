---
title: Référentiel de code source
description: Découvrez les informations sur le référentiel Git qui est fourni pour chaque programme que vous avez dans Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
TQID: https://experienceleague.adobe.com/hdEpqKW0NluPs-w37SeLzpd-EHJNqb2nfSAMQ35man8
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: b24e9550f11486e7ed8da31d5da27f85ad5acaf2
workflow-type: tm+mt
source-wordcount: 236
ht-degree: 44%

---

# Référentiel de code source {#source-code-repository}

Découvrez les informations sur le référentiel Git qui est fourni pour chaque programme que vous avez dans Cloud Manager.

## Référentiel de Cloud Manager {#cloud-manager-repository}

Votre abonnement à [!UICONTROL AEM Managed Services] comprend un référentiel de code source configuré et géré par Adobe. Chaque programme se voit attribuer un référentiel Git unique, où le code associé est stocké et sécurisé.

En règle générale, utilisez toujours le référentiel Git de Cloud Manager, qui est fourni vide, sans aucune branche configurée ni exemple de projet. Cloud Manager fournit un jeton d’accès privé pour son référentiel Git, ce qui vous permet d’utiliser n’importe quel client Git pour créer des branches, gérer le code, récupérer l’historique de validation, etc.

Pour plus d’informations sur la configuration de branches dans Git, voir la section [Configurer des branches de versions](/help/getting-started/configuring-branches.md).

Pour en savoir plus sur l’utilisation du référentiel Git de Cloud Manager avec le pipeline CI/CD, voir [Configuration des pipelines de production](/help/using/production-pipelines.md) et [Configuration de pipelines hors production](/help/using/non-production-pipelines.md).

## Référentiel local {#on-premise-repository}

Si vous disposez déjà d’un référentiel Git et que vous souhaitez continuer à l’utiliser, utilisez la fonctionnalité de Git pour plusieurs référentiels distants. Le développement se poursuit dans votre référentiel Git. Lorsqu’une branche de version est prête pour le déploiement en production, vous pouvez placer votre dernier code dans le référentiel Git de Cloud Manager et déclencher le pipeline CI/CD de Cloud Manager.

Pour afficher les commandes Git courantes, reportez-vous au [Guide de référence Git](https://education.github.com/git-cheat-sheet-education.pdf).
