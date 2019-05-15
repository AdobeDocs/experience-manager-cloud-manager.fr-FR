---
title: Notes de mise à jour de la version 2019.2.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.2.0
description: Consultez cette page pour obtenir des informations sur la mise à jour 2019.2.0 de Cloud Manager.
seo-description: Consultez cette page pour obtenir des informations sur la mise à jour 2019.2.0 d’AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notes de mise à jour de la version 2019.2.0 {#release-notes-for}

La mise à jour 2019.2.0 de [!UICONTROL Cloud Manager] contient une nouvelle fonctionnalité de surveillance système. Les clients peuvent ainsi afficher l’état de leurs environnements Adobe Managed Services au niveau du système.


## Date de publication {#release-date}

La date de publication de la mise à jour de [!UICONTROL Cloud Manager] 2019.2.0 est le 21 février 2019.

## Nouveautés {#whats-new}

* Nouvelle fonctionnalité de surveillance système. Pour en savoir plus, consultez [Surveillance de vos environnements](monitor-your-environments.md).
* Le module de dispatcher dans les projets générés par l’assistant contient désormais un fichier Lisez-moi.
* L’ordre de tri des problèmes d’analyse du code a été amélioré afin de correspondre à la priorité du problème.
* Les instances intermédiaires sont maintenant toujours restaurées à l&#39;équilibreur de charge, même dans le cas d’un échec de déploiement.
* Un nouveau rôle de développeur API est disponible dans Admin Console, ce qui permet à des utilisateurs spécifiques d’obtenir l’autorisation de créer des intégrations dans la console Adobe I/O. Consultez [la section Gestion des développeurs](https://www.adobe.com/go/aac_api_prod_learn) pour en savoir plus.
* La version de Maven Archetype a été mise à jour vers la version 16.
* La version de Maven a été mise à jour vers la version 3.6.0.

## Correctifs {#bug-fixes}

* Dans certains cas, les pipelines ne s’exécutaient pas lorsque l’environnement cible était hébergé par Azure.
* L’ordre des environnements était incohérent.
* Les tests de performance pouvaient échouer lorsque les chemins de page découverts contenaient une virgule.
* Lorsqu’une exécution de pipeline était lancée à partir de l’interface utilisateur Web, le bouton Précédent du navigateur ne fonctionnait pas correctement.
* Les liens En savoir plus sur la page Aperçu n’ouvraient pas de nouvel onglet.
* Une vignette de programme n’était peut-être pas visible immédiatement après son chargement.
* Dans certains cas, l’analyse du code échouait en raison de la configuration spécifique au projet.
* Le lien En savoir plus sur la carte Pipelines hors production redirigeait à un endroit incorrect.
* Lorsqu’un point de contrôle qualité était remplacé, l’état s’affichait de manière incohérente.
* Les clients qui utilisaient des topologies de secours à froid recevaient des résultats incorrects pour les tests de sécurité.
* Lors de la création d’un projet à l&#39;aide de l’assistant, il n’était pas possible de créer une branche contenant le caractère « tiret ».

## Problèmes connus {#known-issues}

* Lorsque les données de surveillance sont actualisées, toutes les séries masquées sont affichées.
* Les clients souhaitant consulter leurs rapports SLA existants devront naviguer manuellement jusqu’à la prochaine version.

   Pour concevoir cette URL, suivez le modèle (`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`). Par exemple, si l’URL d’Experience Cloud est (`https://weretailprod.experiencecloud.adobe.com`), votre URL des rapports SLA est (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`).

   Ce problème devrait être résolu dans la prochaine version avec la disponibilité des rapports SLA dans [!UICONTROL Cloud Manager].
