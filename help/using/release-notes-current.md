---
title: Notes de mise à jour de la version 2022.4.0
description: Voici les notes de mise à jour de la version 2022.4.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 3d4eea13c0f2e9c4030bbfd3b7c5c25336548498
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 27%

---


# Notes de mise à jour de la version 2022.4.0 de Cloud Manager {#release-notes}

Cette page présente les notes de mise à jour de la version 2022.4.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] la version 2022.4.0 est le 7 avril 2022. La prochaine version est prévue pour le 5 mai 2022.

## Nouveautés {#what-is-new}

* Des améliorations ont été apportées à la durée et au taux de succès des étapes de création de pipeline. Elles seront progressivement déployées pour tous les clients tout au long du mois d’avril.
* Vous pouvez désormais facilement trouver une branche Git en saisissant les premiers caractères du nom dans le champ de saisie de l’assistant d’ajout et de modification de pipeline, puis en sélectionnant parmi des correspondances suggérées.
* Le **Pipelines** a désormais une pagination afin d’améliorer la convivialité des programmes avec un grand nombre de pipelines.
   * 50 lignes par page s’affichent dans le tableau.
* La version de la variable [AEM Archétype de projet](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) Mise à jour de la version 36 de pour l’utilisation de Cloud Manager.
* Le JDK Oracle est désormais le JDK par défaut pour le développement et le fonctionnement des applications AEM. Le processus de création de Cloud Manager passe automatiquement à l’utilisation du JDK Oracle, même si une autre option est explicitement sélectionnée dans la chaîne d’outils Maven.
   * Pour en savoir plus sur le basculement vers JDK Oracle, reportez-vous à la section [la documentation sur l’environnement de création .](/help/using/build-environment-details.md#using-java-support)
   * Reportez-vous à la section [FAQ sur la politique de prise en charge de Java pour Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65/assets/Java_Policy_for_Adobe_Experience_Manager.pdf) pour répondre aux questions courantes sur ce changement.
