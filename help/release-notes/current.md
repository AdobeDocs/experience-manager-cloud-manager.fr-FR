---
title: Notes de mise à jour de la version 2025.2.0 de Cloud Manager
description: En savoir plus sur la version 2025.2.0 de Cloud Manager dans Adobe Managed Services.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 51dd060ec9b922ace9ce537cac669c61154284e8
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 26%

---

# Notes de mise à jour de Cloud Manager 2025.2.0 dans Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

Découvrez la version de [!UICONTROL Cloud Manager] 2025.2.0 dans Adobe Managed Services.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/home).

## Dates de publication {#release-date}

La date de publication de la version 2025.2.0 de [!UICONTROL Cloud Manager] est le vendredi 13 février 2025.

La prochaine version est prévue le vendredi 13 mars 2025.

## Nouveautés {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* **SonarQube mis à niveau**

  À compter du jeudi 13 février 2025, l’étape de qualité du code Cloud Manager utilise désormais SonarQube 9.9.5.90363.

  Les règles mises à jour, disponibles pour AMS sur [ce lien](/help/using/code-quality-testing.md#code-quality-testing-step), déterminent les scores de sécurité et la qualité du code pour les pipelines Cloud Manager.

* SonarQube 9.9 est désormais le moteur d’analyse de la qualité du code par défaut pour tous les clients.

* **Prise en charge de l’environnement de création Java 17 et Java 21**

  Les clients peuvent désormais créer des versions avec Java 17 ou Java 21, grâce à des améliorations de performances et à de nouvelles fonctionnalités de langage. Voir [Environnement de création](/help/getting-started/build-environment.md) pour connaître les étapes de configuration, notamment la mise à jour de la description de votre projet Maven et certaines versions de bibliothèque.

  >[!NOTE]
  >Pour les environnements Cloud Service, lorsque la version de build est définie sur Java 17 ou Java 21, le runtime est défini par défaut sur Java 21.

* **Validation des copies de contenu étendue**

  Les règles de validation de la copie de contenu ont été mises à jour. Avec cette version, les utilisateurs ne peuvent plus déclencher de copie de contenu si des exécutions de pipeline sont actives dans l’environnement source ou de destination. Les utilisateurs doivent attendre que toutes les exécutions de pipeline en cours soient terminées avant de lancer une copie de contenu.

<!-- 
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features.

### Bring Your Own Git - now with support for GitLab and Bitbucket {#gitlab-bitbucket}

The **Bring Your Own Git** feature has been expanded to include support for external repositories, such as GitLab and Bitbucket. This new support is in addition to the already existing support for private and enterprise GitHub repositories. When you add these new repos, you can also link them directly to your pipelines. You can host these repositories on public cloud platforms or within your private cloud or infrastructure. This integration also removes the need for constant code synchronization with the Adobe repository and provides the ability to validate pull requests before merging them into a main branch.

Pipelines using external repositories (excluding GitHub-hosted ones) and the **Deployment Trigger** set to **On Git Changes** now start automatically.

See [Add external repositories in Cloud Manager](/help/managing-code/external-repositories.md).

![Add Repository dialog box](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Currently, the out-of-the-box pull request code quality checks are exclusive to GitHub-hosted repositories, but an update to extend this functionality to other Git vendors is in the works.

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
