---
title: Notes de mise à jour de la version 2018.9.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2018.9.0
description: Consultez cette page pour obtenir des informations sur la mise à jour 2018.9.0 de Cloud Manager.
seo-description: Consultez cette page pour obtenir des informations sur la mise à jour 2018.9.0 d’AEM Cloud Manager.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 100%

---


# Notes de mise à jour de la version 2018.9.0 {#release-notes-for}

La mise à jour 2018.9.0 de [!UICONTROL Cloud Manager] prend en charge une API Adobe I/O, y compris les événements, pour l’intégration du pipeline CI/CD de [!UICONTROL Cloud Manager] à d’autres systèmes. Elle commence également la réécriture de la couche de l’interface utilisateur dans React.

## Date de publication {#release-date}

La date de publication de la mise à jour 2018.9.0 de [!UICONTROL Cloud Manager] est le 1er novembre 2018.

## Nouveautés {#whats-new}

* **Pipeline CI/CD** : nouveau système d’API et d’événements pour l’intégration du pipeline CI/CD de [!UICONTROL Cloud Manager] à d’autres systèmes. Pour plus d’informations, reportez-vous à la documentation de l’API de [!UICONTROL Cloud Manager] (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html).

* **Interface utilisateur** : introduction de la nouvelle couche de l’interface utilisateur qui est plus réactive.

## Correctifs {#bug-fixes}

* Dans la version 2018.8.0 de [!UICONTROL Cloud Manager], les durées de la page Activité étaient répertoriées en minutes et en heures, mais ces informations n’étaient pas répercutées dans l’en-tête du tableau.
* En de rares occasions, les clients ne pouvaient pas démarrer l’assistant de nouveau projet d&#39;application.
* L’étiquette du bouton dans la boîte de dialogue de l’assistant de nouveau projet d’application induisait en erreur.
* Dans certains cas, cliquer sur le bouton Détails de la page Activité redirigeait vers la page Aperçu.
* Certaines circonstances rares et inattendues entraînaient l’absence d’une carte sur la page Aperçu.
* L’icône Ressources s’affichait sur la page Liste des programmes pour tous les clients.
* En cas d’échecs back-end, il arrivait qu’une exécution de pipeline reste à l’étape *Valider*.
* Dans certains cas, la longueur de la description du programme était mal calculée.

## Problèmes connus {#known-issues}

* Les branches créées à l’aide de l’assistant de projet d’application ne peuvent pas contenir de tirets.
* La barre latérale de notification d’Adobe [!UICONTROL Experience Cloud] peut ne pas charger les notifications de manière cohérente. Toutefois, les notifications sont visibles dans Adobe [!UICONTROL Experience Cloud] et, si elles sont configurées, elles sont toujours envoyées par e-mail.

