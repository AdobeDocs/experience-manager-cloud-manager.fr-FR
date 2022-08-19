---
title: Référentiel de code source
description: Découvrez les informations sur le référentiel Git qui est fourni pour chaque programme que vous avez dans Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: ht
source-wordcount: '267'
ht-degree: 100%

---


# Référentiel de code source {#source-code-repository}

Découvrez les informations sur le référentiel Git qui est fourni pour chaque programme que vous avez dans Cloud Manager.

## Référentiel de Cloud Manager {#cloud-manager-repository}

Votre abonnement à [!UICONTROL AEM Managed Services] comprend un référentiel de code source configuré et géré par Adobe. Chaque programme se voit attribuer un référentiel Git unique, où le code associé sera stocké et sécurisé.

Il est considéré comme une bonne pratique de toujours utiliser le référentiel Git de Cloud Manager, qui est fourni vide, sans branche configurée ni exemple de projet. Un jeton d’accès privé vous sera fourni pour vous permettre d’utiliser le référentiel Git de Cloud Manager. Il vous permettra d’utiliser n’importe quel client Git pour créer des branches, stocker et récupérer votre code, répertorier l’historique des validations, etc.

Pour plus d’informations sur la configuration de branches dans Git, consultez [Configurer des branches de versions](/help/getting-started/configuring-branches.md).

Pour plus d’informations sur l’utilisation du Référentiel Git de Cloud Manager avec le pipeline CI/CD, reportez-vous aux documents [Configurer des pipelines de production](/help/using/production-pipelines.md) et [Configurer des pipelines hors production](/help/using/non-production-pipelines.md).

## Référentiel On-Premise {#on-premise-repository}

Il se peut que vous possédiez un référentiel Git existant et que vous souhaitiez le conserver, auquel cas vous pouvez utiliser la fonctionnalité de Git pour plusieurs référentiels distants. Le développement quotidien continuerait alors dans votre référentiel Git. Lorsqu’une branche de version est prête pour un déploiement en production, vous pouvez placer votre dernier code dans le référentiel Git de Cloud Manager et déclencher le pipeline CI/CD de Cloud Manager.

Pour afficher les commandes Git courantes, reportez-vous à l’[Aide-mémoire Git](https://education.github.com/git-cheat-sheet-education.pdf) sur le site web GitHub.
