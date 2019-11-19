---
title: Gestion des environnements
seo-title: Gestion des environnements
description: 'null'
seo-description: Consultez cette page pour afficher la liste des environnements de production et des environnements hors production utilisés pour configurer et exécuter le pipeline CI/CD dans Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
translation-type: ht
source-git-commit: c81243708d938a8bffdec8a35f32a2cf552c1c95

---


# Gestion des environnements {#manage-your-environments}

La page **Aperçu** de Cloud Manager comprend la vignette **Environnements** qui répertorie tous les environnements AEM gérés.

Chacun des environnements répertoriés affiche l’état associé.

![](assets/Manage-Environ-Overview.png)

## Tutoriel vidéo {#video-tutorial}

### Présentation de l’environnement de Cloud Manager {#environ-video}

La vidéo suivante présente un aperçu des environnements Cloud Manager composés d’instances AEM Author, AEM Publish et Dispatcher


>[!VIDEO](https://video.tv.adobe.com/v/26318/?captions=fre_fr)

## Accès aux environnements dans Cloud Manager {#accessing-environments-in-cloud-manager}

La vignette **Environnements** affiche les environnements intermédiaires et de production configurés dans votre programme ainsi que le statut.

Le statut est l’état d’alimentation cumulée sur les nœuds de l’environnement. Il est vert si tous les nœuds sont en cours d’exécution, rouge si même un seul nœud est à l’arrêt, bleu si même un seul nœud est à venir et jaune si même un seul nœud a un état d’alimentation indisponible (dans cet ordre de priorité).

![](assets/Environments-card-new.png)

### Environnements {#environments}

Cliquez sur **Gérer** pour afficher l’écran **Environnements**.

L’écran **Environnements** affiche une carte pour les environnements de *production* et *intermédiaires* (selon le cas) dans votre programme. Le nom de l’environnement est visible au-dessus de chaque carte. La carte comprend un tableau des nœuds de l’environnement, ainsi que la taille du processeur, du stockage, de la région et de l’état.

>[!NOTE]
>
>Le **statut** du nœud représente l’état d’alimentation de la VM et ne reflète pas l’état d’AEM sur le serveur. L’état peut être **En cours d’exécution** (cercle vert), **Arrêté** (cercle rouge), **À venir** (cercle bleu) ou **Indisponible** (cercle jaune).

![](assets/Environments-tab.png)
