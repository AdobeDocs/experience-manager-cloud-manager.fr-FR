---
title: Référentiel de code source
seo-title: Source Code Repository for Adobe AEM Cloud Manager
description: Consultez cette page pour en savoir plus sur le référentiel Git qui est fourni pour chaque programme que vous avez dans Cloud Manager.
seo-description: Follow this page to learn about the git repository that is provisioned for each program you have in Adobe AEM Cloud Manager.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
feature: Provisioning
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: ht
source-wordcount: '261'
ht-degree: 100%

---

# Référentiel de code source {#source-code-repository}

## Référentiel de Cloud Manager {#cloud-manager-repository}

Votre abonnement à [!UICONTROL AEM Managed Services] comprend un référentiel de code source configuré et géré par Adobe. Un seul et unique **référentiel Git** est affecté au programme de chaque client. Votre code associé y sera stocké et sécurisé.

En règle générale, vous devez toujours utiliser le référentiel Git de Cloud Manager, qui est fourni vide sans aucune branche configurée ni exemple de projet. Pour utiliser le référentiel Git de Cloud Manager, vous recevez un **jeton d’accès privé** qui vous permettra d’utiliser n’importe quel client compatible avec le Git pour créer des branches, stocker et récupérer votre code, répertorier l’historique de validation, etc.

Pour plus d’informations sur la configuration de branches dans Git, consultez [Configuration des branches de versions](configure-your-release-branches.md).

Pour plus d’informations sur la façon d’utiliser le **Référentiel Git** de Cloud Manager avec le pipeline CI/CD, reportez-vous aux documents [Configuration de pipelines de production](configuring-production-pipelines.md) et [Configuration de pipelines hors production](configuring-non-production-pipelines.md).

## Référentiel On-Premise {#on-premise-repository}

Dans certains cas, vous disposez déjà d’un référentiel Git et souhaitez continuer à l’utiliser. Dgitans ces cas-là, vous pouvez utiliser la fonctionnalité prise en charge par Git qui permet de disposer de plusieurs référentiels distants. Le développement quotidien continue de se faire dans votre référentiel Git. Lorsqu’une branche de version est prête pour un déploiement en production, vous placez votre dernier code dans le référentiel Git de Cloud Manager et déclenchez le pipeline CI/CD de Cloud Manager.

>[!NOTE]
>
>Pour afficher les commandes Git courantes, consultez l’[Aide-mémoire Git](https://education.github.com/git-cheat-sheet-education.pdf).
