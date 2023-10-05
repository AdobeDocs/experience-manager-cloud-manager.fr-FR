---
title: Notes de mise à jour de la version 2023.10.0
description: Voici les notes de mise à jour de la version 2023.10.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 851364e74864c28b3bcd9285dfbe06ddb530eb10
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 49%

---


# Notes de mise à jour de la version 2023.10.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2023.10.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de la version 2023.10.0 de [!UICONTROL Cloud Manager] est le 5 octobre 2023. La prochaine version est prévue pour le 2 novembre 2023.

## Nouveautés {#what-is-new}

* La variable **Responsable de déploiement** rôle peut [configurez un ensemble de chemins de contenu qui seront invalidés ou purgés du cache de Dispatcher AEM lorsqu’un pipeline hors production est exécuté.](/help/using/non-production-pipelines.md)
   * Ces actions de cache sont exécutées dans le cadre de l’étape du pipeline de déploiement, juste après le déploiement des packages de contenu.
   * Ces paramètres utilisent le comportement standard d’AEM Dispatcher.
* Avec la version d’octobre 2023 de Cloud Manager, les versions Java sont mises à jour par le biais d’un déploiement progressif.
   * Les versions mineures de Java 8, 11 et Maven ont été mises à jour et seront déployées par étapes au cours des deux prochains mois. La nouvelle version comporte plusieurs correctifs de sécurité et correctifs. Les nouvelles versions sont les suivantes :
   * *Maven : 3.8.8*
   * *Version Java 8 : /usr/lib/jvm/jdk1.8.0_371*
   * *Version Java 11 : /usr/lib/jvm/jdk-11.0.20*
   * [Voir l’avis d’OpenJDK](https://openjdk.org/groups/vulnerability/advisories/) pour plus d’informations sur la sécurité et les correctifs de bogues dans ces mises à jour JDK.
