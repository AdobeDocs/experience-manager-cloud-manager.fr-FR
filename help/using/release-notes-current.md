---
title: Notes de mise à jour de la version 2022.3.0
description: Voici les notes de mise à jour de la version 2022.3.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 6e98f9d2fcd69799bad86d1e247212b26273bd0b
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 29%

---


# Notes de mise à jour de la version 2022.3.0 de Cloud Manager {#release-notes}

Cette page documente les notes de mise à jour pour [!UICONTROL Cloud Manager] version 2022.3.0.

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] la version 2022.3.0 est le 10 mars 2022. La prochaine version est prévue pour le 7 avril 2022.

## Nouveautés {#what-is-new}

* [Le `reliability_rating` mesure critique](understand-your-test-results.md) a été désactivé.
* Un utilisateur peut désormais trier les colonnes de la variable **Pipelines** dans Cloud Manager.

## Correctifs {#bug-fixes}

* [Le **Ignorer les modifications de l’équilibreur de charge** option](configuring-production-pipelines.md#adding-production-pipeline) peuvent désormais être correctement désactivés.
* [Le **Ignorer les modifications de l’équilibreur de charge** option](configuring-production-pipelines.md#adding-production-pipeline) s’affiche maintenant pour le workflow de modification du pipeline de déploiement.
* Un sous-ensemble de référentiels Git créés manuellement avait des valeurs de nom incorrectes qui affectaient [la fonction de réutilisation des artefacts de création.](setting-up-project.md#build-artifact-reuse) Les noms de ces référentiels ont été modifiés et les utilisateurs verront le nom corrigé dans l’API/interface utilisateur de Cloud Manager.
* [Lors de l’ajout ou de la modification d’un pipeline de qualité du code,](configuring-non-production-pipelines.md) les options permettant de gérer les échecs de mesures ne s’affichent plus.
* Les configurations de variable de pipeline inattendues ne provoquent plus d’erreurs lors de l’étape de création.
