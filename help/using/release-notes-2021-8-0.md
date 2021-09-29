---
title: Notes de mise à jour de la version 2021.8.0
description: Consultez cette page pour obtenir des informations sur la version 2021.8.0 de Cloud Manager
feature: Release Information
source-git-commit: 3fccb0b577662ebc12b65777cbf9624e06d4259d
workflow-type: ht
source-wordcount: '164'
ht-degree: 100%

---

# Notes de mise à jour de la version 2021.8.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.8.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>Reportez-vous aux [Notes de mise à jour actuelles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr#getting-access) pour consulter les dernières notes de mise à jour de Cloud Manager dans AEM as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la mise à jour 2021.8.0 de [!UICONTROL Cloud Manager] est le 12 août 2021.


## Nouveautés {#whats-new}

* Fonctionnalité de libre-service pour permettre aux utilisateurs de créer et de gérer plusieurs référentiels via l’interface utilisateur de Cloud Manager.

* SonarQube lisait inutilement les données de l’historique Git. Avec les bases de code volumineuses, cela pouvait entraîner une pénalité de performance de build inutile.

* Une API est désormais disponible pour invalider le cache de dépendance Maven par pipeline.

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 29.

## Correctifs {#bug-fixes}

* Parfois, lorsqu’un pipeline est déclenché deux fois pour une raison quelconque, l’une ou l’autre des exécutions échoue avec l’erreur *Impossible de mettre à jour l’état d’exécution du pipeline*.