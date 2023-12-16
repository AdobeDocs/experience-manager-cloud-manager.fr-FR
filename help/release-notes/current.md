---
title: Notes de mise à jour de la version 2023.12.0
description: Voici les notes de mise à jour de la version 2023.12.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 2ac254508e4015fea21c4fcd087703ac5fbeeec6
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 63%

---


# Notes de mise à jour de la version 2023.12.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2023.12.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] version 2023.12.0 du 14 décembre 2023. La prochaine version est prévue pour le 18 janvier 2024.

## Nouveautés {#what-is-new}

* Les [autorisations personnalisées de Cloud Manager](/help/using/custom-permissions.md) vous permettent de créer des profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès aux programmes, aux pipelines et aux environnements pour les utilisateurs et utilisatrices de Cloud Manager.
* Déploiement de mises à jour dans la variable [environnement de création](/help/getting-started/build-environment.md) that [annoncé et commencé avec la version d’octobre de Cloud Manager](/help/release-notes/2023/2023-10-0.md) ont été terminées.
   * Ajout de la prise en charge du noeud 18 pour [pipelines front-end et pile complète.](/help/overview/ci-cd-pipelines.md)
   * La version mineure de Java 8 a été mise à jour vers `jdk1.8.0_371`.
   * La version mineure de Java 11 a été mise à jour vers `jdk-11.0.20`.
   * Maven a été mis à jour vers la version 3.8.8.
      * Maven désactive désormais toutes les variables non sécurisées `http://*` miroirs par défaut.
      * [Adobe recommande](/help/getting-started/build-environment.md#https-maven) Les utilisateurs mettent à jour leurs référentiels Maven pour utiliser HTTPS au lieu de HTTP.
* L’image de base du conteneur de génération a été mise à jour vers Ubuntu 22.04.

## Programme d’adoption précoce {#early-adoption}

Prenez part à notre programme d’adoption précoce pour avoir la possibilité de tester certaines fonctionnalités à venir.

### Apporter votre propre GitHub {#byo-github}

Si vous utilisez GitHub pour gérer vos référentiels, [vous pouvez désormais valider le code directement dans vos référentiels GitHub via Cloud Manager.](/help/managing-code/byo-github.md) Cette intégration élimine la nécessité de synchroniser de manière cohérente le code avec le référentiel Adobe et vous permet de vérifier les demandes d’extraction avant de les fusionner dans les branches principales.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à `Grp-CloudManager_BYOG@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID.
