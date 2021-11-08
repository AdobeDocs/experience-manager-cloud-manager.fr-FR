---
title: Notes de mise à jour de la version 2021.11.0
description: Consultez cette page pour obtenir des informations sur la version 2021.11.0 de Cloud Manager
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: e6e5a17c16c42e0b0ed5aedd2f9a6360fd81d8cd
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 19%

---

# Notes de mise à jour de la version 2021.10.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.11.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>Reportez-vous aux [Notes de mise à jour actuelles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr#getting-access) pour consulter les dernières notes de mise à jour de Cloud Manager dans AEM as a Cloud Service.

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] version 2021.11.0 est le 04 novembre 2021.
La prochaine version est prévue pour le 9 décembre 2021.

## Nouveautés {#whats-new}

* L’identifiant de validation Git s’affiche désormais dans les détails d’exécution du pipeline, ce qui facilite le suivi du code qui a été créé.

* Le `x-request-id` L’en-tête de réponse est désormais visible dans le terrain de lecture de l’API sur [www.adobe.io](https://www.adobe.io/). Cet en-tête est utile lors de l’envoi de problèmes d’assistance clientèle à des fins de dépannage.

* En tant qu’utilisateur, je vois une carte Pipeline avec zéro pipeline me fournir des conseils appropriés.

* Une nouvelle page d’activité est désormais disponible, où vous pouvez afficher les activités telles que les exécutions de pipeline et de code, ainsi que les détails associés. Au fil du temps, les activités répertoriées dans cette page s’étendront avec le détail fourni.

* Une nouvelle page Pipelines avec une fenêtre contextuelle d’état et de survol permettant d’afficher facilement le résumé des détails est désormais disponible. Les exécutions de pipeline peuvent être visualisées avec les détails associés.

* L’API Modifier le pipeline prend désormais en charge la définition des chemins d’invalidation et de purge du dispatcher.

* L’API Edit Pipeline prend désormais en charge la modification de l’environnement utilisé dans les phases de déploiement.

* Une optimisation du processus d’analyse OakPal a été introduite pour les modules volumineux.

* Le fichier CSV de problème de qualité contient désormais l’horodatage de chaque problème de qualité.

* Le bouton Gérer de la page Environnements ne sera plus visible dans l’interface utilisateur.

## Correctifs {#bug-fixes}

* Certaines configurations de génération non orthodoxes entraînaient le stockage de fichiers inutiles dans le cache d’artefacts Maven du pipeline, ce qui entraînait des E/S réseau superflues lors du démarrage et de l’arrêt du conteneur de génération.

* L’API du PATCH de pipeline échoue si la phase de déploiement n’existe pas.

* Le `ClientlibProxyResourceCheck` la règle de qualité générait des problèmes de faux positifs lorsqu’il existait des bibliothèques clientes avec des chemins d’accès de base communs.

* Un message d’erreur indiquant que le nombre maximal de référentiels a été atteint ne précisait pas la raison de l’erreur.

* Dans de rares cas, les pipelines échouaient en raison d’une gestion inappropriée des reprises de certains codes de réponse.
