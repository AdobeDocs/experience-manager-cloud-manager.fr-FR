---
title: Référentiel de code source
seo-title: Référentiel de code source pour Adobe AEM Cloud Manager
description: Consultez cette page pour en savoir plus sur le référentiel git qui est fourni pour chacun de vos programmes dans Cloud Manager.
seo-description: Consultez cette page pour en savoir plus sur le référentiel git fourni pour chacun de vos programmes dans Adobe AEM Cloud Manager.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: conditions requises
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
translation-type: ht
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Référentiel de code source {#source-code-repository}

## Référentiel de Cloud Manager {#cloud-manager-repository}

Votre abonnement à [!UICONTROL AEM Managed Services] comprend un référentiel de code source configuré et géré par Adobe. Un seul et unique **référentiel git** est affecté au programme de chaque client. Votre code associé y sera stocké et sécurisé.

En règle générale, vous devez toujours utiliser le référentiel git de Cloud Manager, qui est fourni vide sans aucune branche configurée ni exemple de projet. Pour utiliser le référentiel git de Cloud Manager, vous recevez un **jeton d’accès privé** qui vous permettra d’utiliser n’importe quel client compatible avec le git pour créer des branches, stocker et récupérer votre code, répertorier l’historique de validation, etc.

Pour plus d’informations sur la configuration de branches dans git, consultez [Configuration des branches de versions](configure-your-release-branches.md).

Pour plus d’informations sur l’utilisation du **référentiel Git** de Cloud Manager avec le pipeline CI/CD, consultez la section [Configuration du pipeline CI/CD](configuring-pipeline.md).

## Référentiel sur site {#on-premise-repository}

Dans certains cas, vous disposez déjà d’un référentiel git et souhaitez continuer à l’utiliser. Dans ces cas-là, vous pouvez utiliser la fonctionnalité prise en charge par git qui permet de disposer de plusieurs référentiels distants. Le développement quotidien continue de se faire dans votre référentiel git. Lorsqu’une branche de version est prête pour un déploiement en production, vous placez votre dernier code dans le référentiel git de Cloud Manager et déclenchez le pipeline CI/CD de Cloud Manager.

>[!NOTE]
>
>Pour afficher les commandes git courantes, consultez l’[Aide-mémoire Git](https://education.github.com/git-cheat-sheet-education.pdf).

