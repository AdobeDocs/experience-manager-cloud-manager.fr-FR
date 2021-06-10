---
title: Notes de mise à jour de la version 2021.6.0
description: Consultez cette page pour obtenir des informations sur la version 2021.6.0 de Cloud Manager
feature: Informations sur la version
source-git-commit: 5111a918b8063ab576ef587dc3c8d66ad976fc1a
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 27%

---

# Notes de mise à jour de la version 2021.6.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.6.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>Reportez-vous aux [Notes de mise à jour actuelles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr#getting-access) pour consulter les dernières notes de mise à jour de Cloud Manager dans AEM as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2021.6.0 de [!UICONTROL Cloud Manager] est le 10 juin 2021.
La prochaine version est prévue pour le 15 juillet 2021.

## Nouveautés {#whats-new}

* Les tests d’Assets et de Sites s’exécuteront désormais en parallèle (le cas échéant), réduisant ainsi le temps total d’exécution du pipeline. Cette fonctionnalité sera activée pour les clients au cours des prochaines semaines.

* Les dépendances Maven téléchargées lors de l’étape de création seront désormais mises en cache entre les exécutions de pipeline. Cette fonctionnalité sera activée pour les clients au cours des prochaines semaines.

* Le nom de branche par défaut utilisé lors de la création du projet et dans la commande push par défaut via la gestion des workflows git a été remplacé par `main`.

* La modification de l’expérience du programme dans l’interface utilisateur a été actualisée.

* La règle de qualité `ImmutableMutableMixCheck` a été mise à jour afin de classer les noeuds `/oak:index` comme étant immuables.

* Les règles de qualité `CQBP-84` et `CQBP-84--dependencies` ont été consolidées dans une seule règle.

* Dans certains cas, l’échec du calcul de la mesure Tests ignorés entraîne l’échec des exécutions de pipeline.

## Correctifs {#bug-fixes}

* Les définitions de noeud JCR contenant une nouvelle ligne après le nom de l’élément racine n’étaient pas correctement analysées.

* L’API de liste des référentiels ne filtre pas les référentiels supprimés.

* Un message d’erreur incorrect s’affichait lorsqu’une valeur non valide était fournie pour l’étape de planification.

* Dans certains cas, lorsque l’exécution du pipeline a atteint l’étape de déploiement en production et que l’utilisateur arrête l’exécution, le message d’état de déploiement dans l’interface utilisateur ne reflétait pas correctement ce qui se passait réellement.
