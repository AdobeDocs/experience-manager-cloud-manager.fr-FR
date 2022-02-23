---
title: Notes de mise à jour de la version 2022.01.0
description: Consultez les notes de mise à jour de la version 2022.01.0 de Cloud Manager ci-dessous.
feature: Release Information
source-git-commit: 099a4490e3a8578b9f3485fd1514d1e97db977ab
workflow-type: ht
source-wordcount: '149'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager version 2021.12.0 {#release-notes}

La section ci-dessous présente les notes générales de mise à jour de la version 2022.01.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Pour consulter les notes de mise à jour les plus récentes de Cloud Manager dans AEM as a Cloud Service, reportez-vous à la section [Notes de mise à jour actuelles de Cloud Manager dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de la version 2022.01.0 de [!UICONTROL Cloud Manager] est le 20 janvier 2022. La prochaine version est prévue pour le 10 février 2022.

## Nouveautés {#whats-new}

* Cloud Manager [évite de reconstruire la base du code lorsqu’il détecte que la même validation Git est utilisée](/help/using/setting-up-project.md#build-artifact-reuse) dans plusieurs exécutions de pipelines de piles pleines.
* Lors de la génération d’un mot de passe Git, la date d’expiration s’affiche.

## Correctifs {#bug-fixes}

* Les occurrences exceptionnelles de défaillances de pipelines faussement positives ont été corrigées.
* Pour les programmes ne comportant qu’un seul référentiel, l’écran d’exécution du pipeline affiche désormais le nom du référentiel.
