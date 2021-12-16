---
title: Notes de mise à jour de la version 2021.12.0
description: Il s’agit des notes de mise à jour de la version 2021.12.0 de Cloud Manager.
feature: Release Information
source-git-commit: 910def6d82c09e0220a50a3cb34a61f2c7284cb9
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 3%

---

# Notes de mise à jour de la version 2021.12.0 de Cloud Manager {#release-notes}

La section suivante présente les notes générales de mise à jour pour [!UICONTROL Cloud Manager] version 2021.12.0.

>[!NOTE]
>
>Pour consulter les dernières notes de mise à jour de Cloud Manager en AEM as a Cloud Service, reportez-vous à la section [Cloud Manager dans les notes de mise à jour actuelles d’AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] version 2021.12.0 du 16 décembre 2021. La prochaine version est prévue pour janvier 2022.

## Nouveautés {#whats-new}

* Le hachage de validation, déjà visible dans l’interface utilisateur, est désormais également fourni dans l’API.
* La page Activité comprend désormais une fenêtre contextuelle pour l’exécution des pipelines qui fournit un résumé des détails du pipeline en un coup d’oeil.
* Des mises à jour pour inclure des détails supplémentaires présentés dans la page Activités ont été ajoutées.
* L’onglet Apprendre de Cloud Manager inclut désormais un accès rapide aux guides d’API et aux ressources associées.
* Un utilisateur disposant du rôle Gestionnaire de déploiement peut désormais lancer l’assistant de création de projet/branche pour un référentiel sans branche dans le menu d’actions de la page Référentiels.
* Le responsable de déploiement, qui se trouve dans le workflow d’ajout ou de modification de pipeline, est maintenant informé de la création d’une branche ou d’un projet si le référentiel sélectionné ne comporte aucune branche.
* Dans la fenêtre Modifier le pipeline de production , lorsqu’il existe plusieurs environnements intermédiaires pour la production, une liste déroulante pour la sélection d’environnement est disponible.

## Correctifs {#bug-fixes}

* Les pipelines de production de pile complète restent nommés &quot;Pipeline de production&quot; même si l’utilisateur saisit un nom différent dans le champ du nom.
