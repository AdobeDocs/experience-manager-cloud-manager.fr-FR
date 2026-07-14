---
title: Configurer les branches
description: Découvrez comment configurer votre première branche dans Git et son utilisation par le pipeline CI/CD pour déployer le code de votre application.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
TQID: https://experienceleague.adobe.com/Mxmx725a6m7J9UtwkI5o3tJGzZ7O3c3Bgv-fF393sZg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 1692390e24f8fa7d719bd8293a99586ec4ec36d4
workflow-type: tm+mt
source-wordcount: 314
ht-degree: 47%

---

# Configurer les branches {#configuring-branches}

Découvrez comment configurer votre première branche dans Git et comment le pipeline CI/CD l’utilise pour déployer le code de votre application.

## Configurer votre première branche dans Git {#setting-up-your-first-branch-in-git}

Un seul référentiel Git, initialement vide, [est fourni](/help/requirements/environment-provisioning.md) pour chaque programme intégré à Cloud Manager. Ce référentiel peut contenir autant de branches que nécessaire pour votre processus de développement, mais le pipeline CI/CD doit utiliser au moins une branche pour déployer le code de l’application en évaluation et en production. Il est conseillé d’utiliser le nom `main` pour cette branche. Cette approche est le comportement par défaut des clients Git lors de la configuration de nouveaux projets.

Par exemple, lorsque vous configurez un nouveau projet, vous exécutez un ensemble de commandes comme celui-ci :

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
>Il n’est pas nécessaire d’utiliser le client de la ligne de commande. Différents clients graphiques Git sont disponibles, soit en tant qu’applications autonomes, soit dans le cadre d’un environnement de développement intégré (IDE), tel qu’Eclipse ou IntelliJ. Tant que l’application cliente prend en charge Git avec HTTPS, elle est compatible avec .

## Transmettre votre première branche {#pushing-your-first-branch}

Une fois que vous avez validé au moins une révision, vous pouvez ajouter le référentiel [!UICONTROL Cloud Manager] en tant que référentiel distant, puis transmettre vos validations vers ce dernier.

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
>Votre CSE Adobe (ingénieur du succès client) fournit l’URL spécifique, ainsi que vos informations d’identification, lors de l’intégration à [!UICONTROL Cloud Manager].

## Branches supplémentaires {#additional-branches}

Une branche `main` est suffisante pour les projets simples, mais une stratégie d’embranchement plus complexe est recommandée. De nombreux clients suivent un processus au cours duquel des activités de développement de routine sont exécutées sur une branche appelée `develop`. La branche `develop` est ensuite fusionnée dans la branche `main` au moment d’un déploiement.

>[!TIP]
>
>Pour afficher les commandes Git courantes, reportez-vous au [Guide de référence Git](https://training.github.com/downloads/github-git-cheat-sheet/).
