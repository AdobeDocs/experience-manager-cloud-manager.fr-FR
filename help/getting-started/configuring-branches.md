---
title: Configurer les branches
description: Découvrez comment configurer votre première branche dans Git et son utilisation par le pipeline CI/CD pour déployer le code de votre application.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 4c051cd1696f8a00d0278131c9521ad4dcb956a3
workflow-type: ht
source-wordcount: '329'
ht-degree: 100%

---


# Configurer les branches {#configuring-branches}

Découvrez comment configurer votre première branche dans Git et son utilisation par le pipeline CI/CD pour déployer le code de votre application.

## Configurer votre première branche dans Git {#setting-up-your-first-branch-in-git}

Un seul référentiel Git, initialement vide, [est fourni](/help/requirements/environment-provisioning.md) pour chaque programme intégré à Cloud Manager. Ce référentiel peut contenir autant de branches que nécessaire pour votre processus de développement. Toutefois, au moins une branche doit être utilisée par le pipeline CI/CD pour déployer le code de l’application dans les environnements d’évaluation et de production. Il est conseillé d’utiliser le nom `main` pour cette branche. Pour des raisons pratiques, ce comportement est défini par défaut pour les clients Git lors de la configuration de nouveaux projets.

Par exemple, lorsque vous configurez un nouveau projet, vous exécuterez un ensemble de commandes comme celui-ci :

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
>Il n’est pas nécessaire d’utiliser le client de ligne de commande. Différents clients graphiques Git sont disponibles, soit en tant qu’applications autonomes, soit dans le cadre d’un environnement de développement intégré (IDE), tel qu’Eclipse ou IntelliJ. Tant que l’application cliente prend en charge Git avec HTTPS, elle doit être compatible avec [!UICONTROL Cloud Manager].

## Publier la première branche {#pushing-your-first-branch}

Une fois que vous avez validé au moins une révision, vous pouvez ajouter le référentiel [!UICONTROL Cloud Manager] en tant que dépôt distant, puis transférer vos validations vers ce dernier.

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      main -> main
```

>[!NOTE]
>
>L’URL spécifique, ainsi que vos informations d’identification, vous seront fournies par votre ingénieur chargé du succès client lors de l’intégration à [!UICONTROL Cloud Manager].

## Branches supplémentaires {#additional-branches}

Une branche `main` unique peut suffire pour des projets très simples, mais dans la plupart des cas, une stratégie de branchement plus complexe est requise. La plupart des clients suivent un processus où les activités de développement quotidiennes sont exécutées sur une branche appelée `develop`. La branche de développement est fusionnée dans la branche `main` lorsqu’il est temps de procéder à un déploiement.

>[!TIP]
>
>Pour afficher les commandes Git courantes, consultez l’[Aide-mémoire Git](https://github.github.com/training-kit/downloads/github-git-cheat-sheet).
