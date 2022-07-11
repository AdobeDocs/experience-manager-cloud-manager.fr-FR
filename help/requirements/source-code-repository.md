---
title: Référentiel de code source
description: Découvrez le référentiel git fourni pour chaque programme de Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 4%

---


# Référentiel de code source {#source-code-repository}

Découvrez le référentiel git fourni pour chaque programme de Cloud Manager.

## Référentiel de Cloud Manager {#cloud-manager-repository}

Votre [!UICONTROL Managed Services AEM] abonnement comprend un référentiel de code source configuré et géré par Adobe. Chaque programme se voit attribuer un référentiel git unique, où votre code associé sera stocké et sécurisé.

En règle générale, vous devez toujours utiliser le référentiel git de Cloud Manager, qui est vide sans aucune branche configurée ni exemple de projet. Pour utiliser le référentiel git de Cloud Manager, vous disposez d’un jeton d’accès privé qui vous permet d’utiliser n’importe quel client git pour créer des branches, stocker et récupérer votre code, répertorier l’historique de validation, etc.

Pour plus d’informations sur la configuration des branches dans Git, voir [Configuration des branches de versions](/help/getting-started/configuring-branches.md)

Pour plus d’informations sur l’utilisation du référentiel git de Cloud Manager avec le pipeline CI/CD, reportez-vous aux documents . [Configuration des pipelines de production](/help/using/production-pipelines.md) et [Configuration de pipelines hors production](/help/using/non-production-pipelines.md) pour en savoir plus.

## Référentiel On-Premise {#on-premise-repository}

Vous pouvez disposer d’un référentiel git existant et souhaitez continuer à l’utiliser, auquel cas vous pouvez utiliser la fonctionnalité git pour plusieurs référentiels distants. Le développement quotidien continue dans votre référentiel git. Lorsqu’une branche de version est prête pour un déploiement en production, vous pouvez envoyer votre dernier code vers le référentiel git de Cloud Manager et déclencher le pipeline CI/CD de Cloud Manager.

Pour afficher les commandes git courantes, voir [Aide-mémoire Git](https://education.github.com/git-cheat-sheet-education.pdf) sur le site web GitHub.
