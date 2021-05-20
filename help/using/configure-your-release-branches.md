---
title: Configuration des branches de versions
seo-title: Configuration des branches de versions
description: Configuration des branches de versions dans Git pour AEM Cloud Manager
seo-description: Consultez cette page pour savoir comment configurer vos branches de versions dans Git.
uuid: d12a8b85-b7fd-4b55-a05a-a0f874ce598c
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 53807ea6-9464-429d-9322-85c9f405dff6
feature: Référentiels Git
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 94%

---

# Configuration des branches de versions {#configure-your-release-branches}

## Configuration de votre première branche dans Git {#setting-up-your-first-branch-in-git}

Un seul **référentiel Git**, initialement vide, est configuré pour chaque programme intégré dans Cloud Manager. Ce référentiel peut contenir autant de branches que suivies par le processus de développement. Toutefois, une branche au moins doit être utilisée par le pipeline CI/CD pour déployer le code de l’application en environnements intermédiaire et de production. Il est conseillé d’utiliser le nom `master` pour cette branche. Pour des raisons pratiques, il s’agit du comportement par défaut des clients Git lors de la configuration de nouveaux projets.

Par exemple, lorsque vous définissez un nouveau projet, vous exécuterez un ensemble de commandes comme celui-ci :

```shell
$ git init
Initialized empty Git repository in /Users/myname/workspace/new-project/.git/
... steps which add Maven build files and source code ...
$ git add pom.xml core/pom.xml core/src ui.apps/pom.xml ui.apps/src
$ git commit -m "initial commit"
 19 files changed, 777 insertions(+)
 create mode 100644 core/pom.xml
 create mode 100644 pom.xml
 create mode 100644 ui.apps/pom.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/config.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/definition/.content.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/filter.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/nodetypes.cnd
 create mode 100644 ui.apps/src/main/content/META-INF/vault/properties.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/apps/my-aem-project/install/.vltignore
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/_rep_policy.xml
```

>[!NOTE]
>
>Il n’est pas nécessaire d’utiliser le client de la ligne de commande. Il existe divers clients graphiques Git disponibles en tant qu’applications autonomes ou composants d’un IDE (environnement de développement intégré, par exemple), tel qu’Eclipse ou intelliJ. Tant que l’application cliente prend en charge Git avec HTTPS, elle doit être compatible avec [!UICONTROL Cloud Manager].

## Création de la première branche {#pushing-your-first-branch}

Une fois que vous avez validé au moins une révision, vous pouvez ajouter le référentiel [!UICONTROL Cloud Manager] en tant que **remote**, puis envoyer vos validations vers ce dernier :

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      master -> master
```

>[!NOTE]
>
>L’URL spécifique, ainsi que vos informations d’identification, vous seront fournies par votre ingénieur du service client lors de l’intégration à [!UICONTROL Cloud Manager].

## Branches supplémentaires {#additional-branches}

Une branche `master` unique peut suffire pour des projets très simples, mais dans la plupart des cas, une stratégie de branchement plus complexe est requise. La plupart des clients suivent un processus où les activités de développement quotidiennes sont exécutées sur une branche appelée `develop`. La branche de développement est fusionnée dans la branche `master` lorsqu’il est temps de procéder à un déploiement.

>[!NOTE]
>
>Pour afficher les commandes git courantes, consultez la [Aide-mémoire Git](https://github.github.com/training-kit/downloads/github-git-cheat-sheet).
