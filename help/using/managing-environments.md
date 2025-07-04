---
title: Gérer les environnements
description: Découvrez comment utiliser Cloud Manager pour gérer vos environnements.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 0b7c926120798e2fdb635752192f4ab2e12c1e24
workflow-type: ht
source-wordcount: '273'
ht-degree: 100%

---


# Gérer les environnements {#managing-environments}

Découvrez comment utiliser Cloud Manager pour gérer vos environnements.

## Page Vue d’ensemble {#overview-page}

La page **Aperçu** de Cloud Manager comprend la vignette **Environnements** qui répertorie tous les environnements AEM gérés.

Chacun des environnements répertoriés affiche l’état associé.

![Page Aperçu](/help/assets/Manage-Environ-Overview.png)

## Volet Environnements {#environments-tile}

Le volet **Environnements** affiche les environnements d’évaluation et de production configurés dans votre programme ainsi que le statut.

Le statut est l’état d’alimentation cumulée sur les nœuds de l’environnement dans l’ordre de priorité suivant.

* Vert : tous les nœuds sont en cours d’exécution
* Rouge : un ou plusieurs nœuds sont arrêtés.
* Bleu : un ou plusieurs nœuds sont à venir.
* Jaune : un ou plusieurs nœuds ont un état d’alimentation indisponible.

![Volet Environnements](/help/assets/Environments-card-new.png)

## Gérer les environnements {#managing-environments-with-cloud-manager}

Dans le volet **Environnements**, cliquez sur la ligne d’un environnement pour afficher l’écran **Environnements**.

L’écran **Environnements** affiche chaque environnement d’évaluation et de production dans votre programme. Le nom de l’environnement est visible au-dessus de chaque carte. La carte comprend un tableau des nœuds de l’environnement, ainsi que la taille du processeur, du stockage, de la région et de l’état.

>[!NOTE]
>
>Le **statut** du nœud représente l’état d’alimentation de la VM et ne reflète pas l’état d’AEM sur le serveur. Le statut peut être :

* Vert : en cours
* Rouge : à l’arrêt
* Bleu : à venir
* Jaune : non disponible

![Onglet Environnements](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Les détails d’environnement tels que le nom ne peuvent pas être modifiés une fois qu’ils ont été configurés.

>[!NOTE]
>
>Demandez vos journaux d’environnement à l’équipe d’ingénierie du succès clientèle.

## Tutoriel vidéo {#video-tutorial}

La vidéo suivante présente un aperçu des environnements Cloud Manager composés d’instances de création, de publication et de Dispatcher AEM.

>[!VIDEO](https://video.tv.adobe.com/v/34716?captions=fre_fr)

*(3 minutes, 1 seconde)*
