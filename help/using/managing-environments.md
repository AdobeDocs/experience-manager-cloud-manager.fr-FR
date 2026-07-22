---
title: Gérer les environnements
description: Découvrez comment utiliser Cloud Manager pour gérer vos environnements.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
TQID: https://experienceleague.adobe.com/Dz3Z5i-gSNSorc7Na74RKgm3e0P9b-3vjVRdJvu6a0c
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 0dde660205ad28bc5924a5cc14404c48a0533ceb
workflow-type: tm+mt
source-wordcount: 261
ht-degree: 57%

---

# Gérer les environnements {#managing-environments}

Découvrez comment utiliser Cloud Manager pour gérer vos environnements.

## Page Vue d’ensemble {#overview-page}

La page **Aperçu** de Cloud Manager comprend la vignette **Environnements** qui répertorie tous les environnements AEM gérés.

Chacun des environnements répertoriés affiche l’état associé.

![Page Aperçu](/help/assets/Manage-Environ-Overview.png)

## Volet Environnements {#environments-tile}

Le volet **Environnements** affiche les environnements d’évaluation et de production configurés dans votre programme ainsi que le statut.

Le statut est l’état d’alimentation agrégé sur les nœuds d’environnement répertoriés dans l’ordre.

* Vert : tous les nœuds sont en cours d’exécution
* Rouge - Un ou plusieurs nœuds sont arrêtés.
* Bleu - Un ou plusieurs nœuds démarrent.
* Jaune : un ou plusieurs nœuds ont un état d’alimentation indisponible.

![Volet Environnements](/help/assets/Environments-card-new.png)

## Gérer les environnements {#managing-environments-with-cloud-manager}

Dans le volet **Environnements**, cliquez sur la ligne d’un environnement pour afficher l’écran **Environnements**.

L’écran **Environnements** affiche chaque environnement de production et d’évaluation dans votre programme. Le nom de l’environnement s’affiche au-dessus de chaque carte. La carte comprend un tableau des nœuds de l’environnement, ainsi que la taille du CPU, le stockage, la région et l’état.

>[!NOTE]
>
>Le **statut** du nœud représente l’état d’alimentation de la VM et ne reflète pas l’état d’AEM sur le serveur. Le statut peut être :

* Vert : en cours
* Rouge : à l’arrêt
* Bleu - Démarrage
* Jaune : non disponible

![Onglet Environnements](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Les détails d’environnement tels que le nom ne peuvent pas être modifiés une fois qu’ils ont été configurés.

>[!NOTE]
>
>Demandez vos journaux d’environnement par l’intermédiaire de votre représentant du succès client.

## Tutoriel vidéo {#video-tutorial}

Cette vidéo présente les environnements Cloud Manager composés d’instances AEM de création, de publication et de Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

*(3 minutes, 1 seconde)*
