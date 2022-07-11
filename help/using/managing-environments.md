---
title: Gestion des environnements
description: Découvrez comment utiliser Cloud Manager pour gérer vos environnements.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 80f8707e00357f5a08dd835b846c9ee610f3e573
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 41%

---


# Gestion des environnements {#managing-environments}

Découvrez comment utiliser Cloud Manager pour gérer vos environnements.

## Page Aperçu {#overview-page}

La page **Aperçu** de Cloud Manager comprend la vignette **Environnements** qui répertorie tous les environnements AEM gérés.

Chacun des environnements répertoriés affiche l’état associé.

![Page Aperçu](/help/assets/Manage-Environ-Overview.png)

## Mosaïque Environnements {#environments-tile}

Le **Environnements** affiche les environnements de production et d’évaluation configurés dans votre programme, ainsi que l’état.

L’état est l’état d’alimentation cumulée sur les noeuds de l’environnement dans l’ordre de priorité suivant.

* Vert : tous les noeuds sont en cours d’exécution
* Rouge : un ou plusieurs noeuds sont arrêtés.
* Bleu : un ou plusieurs noeuds s’affichent.
* Jaune : un ou plusieurs noeuds ont un état d’alimentation indisponible.

![Mosaïque Environnements](/help/assets/Environments-card-new.png)

## Gestion des environnements {#managing-environments-with-cloud-manager}

Sur le **Environnements** mosaïque, cliquez sur **Gérer** pour afficher la variable **Environnements** écran.

Le **Environnements** affiche une carte pour les environnements de production et d’évaluation (le cas échéant) de votre programme. Le nom de l’environnement est visible au-dessus de chaque carte. La carte comprend un tableau des nœuds de l’environnement, ainsi que la taille du processeur, du stockage, de la région et de l’état.

>[!NOTE]
>
>Le **statut** du nœud représente l’état d’alimentation de la VM et ne reflète pas l’état d’AEM sur le serveur. L’état peut être :

* Vert - En cours
* Rouge - Stoppé
* Bleu - À venir
* Jaune - Non disponible

![Onglet Environnements](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Si vous avez besoin de vos journaux d’environnement, ils peuvent être demandés par l’intermédiaire de votre ingénieur du service client.

## Tutoriel vidéo {#video-tutorial}

Cette vidéo présente un aperçu des environnements Cloud Manager composés d’instances de création, de publication et de Dispatcher AEM.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)
