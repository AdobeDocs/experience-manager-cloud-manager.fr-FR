---
title: Référentiel de code source
description: Découvrez le référentiel Git fourni pour chaque programme de Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 7%

---


# Référentiel de code Source {#source-code-repository}

Découvrez le référentiel Git fourni pour chaque programme de Cloud Manager.

## Référentiel Cloud Manager {#cloud-manager-repository}

Votre abonnement à [!UICONTROL AEM Managed Services] comprend un référentiel de code source configuré et géré par Adobe. Chaque programme se voit attribuer un référentiel Git unique, où votre code associé est stocké et sécurisé.

En règle générale, vous devez toujours utiliser le référentiel Git de Cloud Manager qui est vide sans aucune branche configurée ni exemple de projet. Cloud Manager fournit un jeton d’accès privé pour son référentiel Git, ce qui vous permet d’utiliser n’importe quel client Git pour créer des branches, gérer le code, récupérer l’historique de validation, etc.

Pour plus d’informations sur la configuration des branches dans Git, voir [Configuration des branches de versions](/help/getting-started/configuring-branches.md).

Pour plus d’informations sur l’utilisation du référentiel Git Cloud Manager avec le pipeline CI/CD, voir [ Configuration des pipelines de production ](/help/using/production-pipelines.md) et [Configuration des pipelines hors production](/help/using/non-production-pipelines.md) pour en savoir plus.

## Référentiel On-premise {#on-premise-repository}

Vous pouvez disposer d’un référentiel Git existant et souhaitez continuer à l’utiliser, auquel cas vous pouvez utiliser la fonctionnalité Git pour plusieurs référentiels distants. Le développement quotidien continue dans votre référentiel Git. Lorsqu’une branche de version est prête pour le déploiement en production, vous pouvez envoyer votre dernier code vers le référentiel Git de Cloud Manager et déclencher le pipeline CI/CD de Cloud Manager.

Pour afficher les commandes Git courantes, consultez l’ [Aide-mémoire Git](https://education.github.com/git-cheat-sheet-education.pdf).
