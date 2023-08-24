---
title: Notes de mise à jour de la version 2023.8.0
description: Voici les notes de mise à jour de la version 2023.8.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: f930f12b5f50dd96a1677ff7a56cf0e92a400556
workflow-type: ht
source-wordcount: '216'
ht-degree: 100%

---


# Notes de mise à jour de la version 2023.8.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2023.8.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de la version 2023.8.0 de [!UICONTROL Cloud Manager] est le 10 août 2023. La prochaine version est prévue pour le 7 septembre 2023.

## Nouveautés {#what-is-new}

* Des améliorations ont été apportées à la lisibilité et à l’affichage des messages d’erreur dans l’interface utilisateur de Cloud Manager.

## Correctifs {#bug-fixes}

* Les cas peu fréquents de blocage du processus de [copie de contenu](/help/using/content-copy.md) ont été corrigés.
* Un problème de test temporaire a été résolu pour les clients et clientes n’utilisant pas New Relic One.
* Les [règles de qualité du code personnalisé](/help/using/custom-code-quality-rules.md) `SupportedRunmode` et `ImmutableMutableMixedPackage` ont été supprimées de SonarQube, car elles ne s’appliquent qu’à AEM as a Cloud Service.
* Les utilisateurs et utilisatrices ne rencontreront plus de pipelines bloqués qui semblent être en état d’exécution.
* Le menu **Environnements** se ferme maintenant après avoir ouvert la boîte de dialogue modale **[Copier le contenu](/help/using/content-copy.md)**.
* La [réexécution d’un pipeline](/help/using/code-deployment.md#reexecute-deployment) n’est plus autorisée si l’exécution précédente n’a pas de `commitId` défini sur l’état de phase de création.
* Un message plus compréhensible s’affiche désormais pour les erreurs rares lorsqu’un utilisateur ou une utilisatrice clique sur un pipeline dans les écrans **Activité** ou **Pipeline**.
