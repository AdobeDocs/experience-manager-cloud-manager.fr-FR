---
title: Notes de mise à jour de la version 2022.5.0
description: Voici les notes de mise à jour de la version 2022.5.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 84cc4352488002ad40102ea2c507af652d9012a1
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 66%

---


# Notes de mise à jour de la version 2022.5.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2022.5.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] la version 2022.5.0 est le 5 mai 2022. La prochaine version est prévue pour le 9 juin 2022.

## Nouveautés {#what-is-new}

Les requêtes HTTP sortantes des tests de ressources proviennent désormais d’une plage d’adresses IP fixe.

## Correctifs {#bug-fixes}

* L’option de modification &quot;Ignorer l’équilibreur de charge&quot; n’a pas pu être désactivée.
* L’option Ignorer les modifications de l’équilibreur de charge ne s’affichait pas dans le workflow de pipeline de modification Déploiement de développement AMS .
* Un sous-ensemble de référentiels GIT créés manuellement avait une valeur de nom incorrecte qui empêchait l’efficacité de la fonction de réutilisation des artefacts de build. Les noms de ces référentiels ont été modifiés et les utilisateurs verront le nom corrigé dans l’API/interface utilisateur de Cloud Manager.
* Les artefacts de build des pipelines hors production ont été réutilisés de manière inappropriée sur les pipelines de production de pile pleine.
* Lors de l’ajout ou de la modification d’un pipeline de qualité du code, les options permettant de gérer les échecs de mesures ne s’affichent plus.
* Certaines configurations de variable de pipeline inattendues peuvent entraîner des erreurs lors de l’étape de création.
