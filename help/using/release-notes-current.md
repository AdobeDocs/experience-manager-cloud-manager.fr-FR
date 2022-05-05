---
title: Notes de mise à jour de la version 2022.5.0
description: Voici les notes de mise à jour de la version 2022.5.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 0ddfd152cb15731882d198d043dd8897b5073ab4
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 82%

---


# Notes de mise à jour de la version 2022.5.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2022.5.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] la version 2022.5.0 est le 5 mai 2022. La prochaine version est prévue pour le 9 juin 2022.

## Nouveautés {#what-is-new}

Vous pouvez accéder au journal de l’environnement AEM à l’aide du rôle Développeur .

## Correctifs {#bug-fixes}

* Un sous-ensemble de référentiels Git créés manuellement avait une valeur de nom incorrecte qui empêchait la fonction de réutilisation des artefacts de build d’être efficace. Les noms de ces référentiels ont été modifiés et les utilisateurs verront le nom corrigé dans l’API/interface utilisateur de Cloud Manager.
* Les artefacts de build des pipelines hors production ont été réutilisés de manière inappropriée sur les pipelines de production de pile pleine.
* Lors de l’ajout ou de la modification d’un pipeline de qualité du code, les options permettant de gérer les échecs de mesures ne s’affichent plus.
* Certaines configurations de variable de pipeline inattendues peuvent entraîner des erreurs lors de l’étape de création.
