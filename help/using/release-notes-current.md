---
title: Notes de mise à jour de la version 2022.3.0
description: Voici les notes de mise à jour de la version 2022.3.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 7611667d8c617d501f9b69cbc7c854c195a5ebbe
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 28%

---


# Notes de mise à jour de la version 2022.3.0 de Cloud Manager {#release-notes}

Cette page documente les notes de mise à jour pour [!UICONTROL Cloud Manager] version 2022.3.0.

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] la version 2022.3.0 est le 10 mars 2022. La prochaine version est prévue pour le 7 avril 2022.

## Nouveautés {#what-is-new}

* Les requêtes HTTP en sortie des tests de ressources proviennent désormais d’une plage d’adresses IP fixe.


## Correctifs {#bug-fixes}

* Le **Ignorer les modifications de l’équilibreur de charge** n’a pas pu être désactivée.
*Le **Ignorer les modifications de l’équilibreur de charge** ne s’affichait pas sur l’option Déploiement AMS Dev. **Modifier le processus de pipeline**.
* Un sous-ensemble de référentiels Git créés manuellement avait une valeur de nom incorrecte qui empêchait l’efficacité de la fonction de réutilisation des artefacts de build. Les noms de ces référentiels ont été modifiés et les utilisateurs verront le nom corrigé dans l’API/interface utilisateur de Cloud Manager.
* Les artefacts de build des pipelines hors production ont été réutilisés de manière inappropriée sur les pipelines de pile complète de production.
* Lors de l’ajout ou de la modification d’un pipeline de qualité du code, les options permettant de gérer les échecs de mesures ne s’affichent plus.
* Certaines configurations de variable de pipeline inattendues peuvent provoquer dans l’étape de création.
