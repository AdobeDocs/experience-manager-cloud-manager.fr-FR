---
title: Notes de mise à jour de la version 2024.2.0
description: Voici les notes de mise à jour de la version 2024.2.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 524471a87217c15dae96c3e6aee57426b43dcccb
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 61%

---


# Notes de mise à jour de la version 2024.2.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2024.2.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] la version 2024.2.0 est le 16 février 2024. La prochaine version est prévue pour le 16 mars 2024.

## Nouveautés {#what-is-new}

* Comme faisant partie de [déploiement,](/help/using/code-deployment.md) le cache de Dispatcher a été vidé à l’emplacement **Joindre Dispatcher** étape . Afin de vous permettre de tester les modifications sur chaque noeud avant de l’associer à l’équilibreur de charge de l’application, après avoir déployé du code sur un éditeur particulier, vous pouvez désormais tester les modifications directement à partir du Dispatcher associé avant de joindre ce Dispatcher à l’équilibreur de charge.
* [Environnement de création](/help/getting-started/build-environment.md) a été mis à jour vers les versions Maven 3.9.4 et JDK jdk-11.0.22 et jdk1.8.0_401.

## Programme d’adoption précoce {#early-adoption}

Prenez part à notre programme d’adoption précoce pour avoir la possibilité de tester certaines fonctionnalités à venir.

### Apporter votre propre GitHub {#byo-github}

Si vous utilisez GitHub pour gérer vos référentiels, [vous pouvez désormais valider le code directement dans vos référentiels GitHub via Cloud Manager.](/help/managing-code/byo-github.md) Cette intégration élimine la nécessité de constamment synchroniser le code avec le référentiel Adobe et vous permet de vérifier les requêtes d’extraction avant de les fusionner dans les branches principales. Cette fonctionnalité est réservée au GitHub public. La prise en charge du GitHub auto-hébergé n’est pas disponible.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à `Grp-CloudManager_BYOG@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID.

## Correctifs {#bug-fixes}

* Le JDK des conteneurs de génération a été mis à jour vers une version qui résout [JDK-8313765.](https://bugs.openjdk.org/browse/JDK-8313765)
