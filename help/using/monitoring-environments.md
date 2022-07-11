---
title: Surveillance des environnements
description: Découvrez comment surveiller vos environnements dans Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 5907ca6337d33c26ff19a14bfeb358cd9f7b935d
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 52%

---


# Surveillance des environnements {#monitoring-environments}

Découvrez comment surveiller vos environnements dans Cloud Manager.

## Seuils de mesure {#thresholds}

La surveillance du système dans [!UICONTROL Cloud Manager] est réalisée en observant les instances dans un environnement et en suivant diverses mesures pour chaque instance. Chaque mesure comporte deux seuils définis : un seuil d&#39;avertissement et un seuil critique.

Si une mesure dépasse son seuil critique, elle est considérée comme étant dans un état critique. Si une mesure est supérieure à son seuil d’avertissement (mais inférieure à son seuil critique), elle est considérée comme étant dans un état d’avertissement. Les seuils sont définis par Adobe Managed Services et peuvent être visualisés dans [!UICONTROL Cloud Manager]. Dans la plupart des cas, les seuils sont cohérents entre les clients. Mais dans certains cas, Adobe Managed Services modifie les seuils pour répondre aux besoins spécifiques des clients. Les questions relatives aux seuils doivent être adressées à l’ingénieur du service client.

## Accès à la surveillance du système {#accessing-system-monitoring}

Pour accéder à la surveillance du système, procédez comme suit.

1. Connectez-vous à la page d’entrée **Managed Services - Programmes**.

   ![Programmes de services gérés](/help/assets/ProgramLanding.png)

1. Cliquez sur la quatrième icône de la carte du programme.

   ![Paramètres](/help/assets/first-timea1.png)


Vous pouvez également accéder au **Surveillance du système** page d’entrée dans la **Rapports** élément de menu de navigation globale dans [!UICONTROL Cloud Manager].

## Présentation de la surveillance du système {#system-monitoring-overview}

La page d’aperçu de la surveillance du système répertorie les environnements surveillés dans le programme et les rapports sur leur intégrité de haut niveau dans quatre catégories distinctes :

* Hôte
* Stockage
* Réseau
* Application

L’état de chaque catégorie est un résumé des mesures individuelles. Si une mesure d’une catégorie est dans un état critique, l’ensemble de la catégorie est dans un état critique aux fins de la page d’aperçu. La même synthèse peut être affichée au niveau d’un environnement et au niveau d’une instance.

![Surveillance du système - Aperçu](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Par défaut, lorsque vous accédez à cette page, les instances d’environnement de production sont visibles, mais d’autres environnements peuvent également être affichés.

## Détails de la surveillance du système {#system-monitoring-detail}

Pour afficher les détails de mesures spécifiques, vous pouvez soit cliquer sur l’une des catégories dans la navigation de gauche, soit cliquer sur l’un des indicateurs de catégorie d’une instance spécifique. Chaque page de détail présente une série de graphiques pour les mesures de cette catégorie. Vous pouvez afficher les mesures de toutes les instances dans un environnement ou pour une instance spécifique. Vous pouvez basculer entre l’environnement et les instances à l’aide des listes déroulantes dans le coin supérieur droit.

![Sélectionner l’environnement](/help/assets/System_Monitoring1.png)

La navigation à gauche affiche les mesures disponibles dans la catégorie sélectionnée pour laquelle il existe des données pour l’environnement et les instances sélectionnés.

![Mesures de surveillance](/help/assets/System_Monitoring2.png)

Un graphique séparé indique l’état et les données dans le temps avec les seuils. Si plusieurs instances sont affichées, les données de chaque instance se trouvent sur une série distincte.

![Graphique de mesures](/help/assets/Monitoring_Graphs1.png)

Une série peut être masquée dans un graphique en cliquant dessus dans la légende.
Par exemple, si vous cliquez sur la série de seuil d’avertissement, vous ne verrez que le seuil critique.

![Modifier le graphique](/help/assets/Monitoring_Graphs2.png)

### Définitions des mesures {#metric-definitions}

#### Hôte {#host}

* **Chargement par noyau**: Le nombre de processus en cours d’exécution par le processeur ou qui se trouvent dans un état d’attente calculé en moyenne sur une période d’une (charge1), cinq (charge5) et quinze (charge15) minutes.
* **Nombre de processus**: Le nombre de processus actuellement ouverts
* **Nombre d’utilisateurs**: Nombre d’utilisateurs disposant d’une principale session shell
* **Utilisation de la mémoire**: Pourcentage de mémoire système actuellement allouée
* **Mémoire JVM**: Taille (en mégaoctets) du segment de mémoire Java alloué
* **Espace de la vieille génération**: Pourcentage de mémoire de l’ancienne génération de la JVM allouée

#### Réseau {#network}

* **Vérification du port CQ**: Temps de réponse en secondes pour accéder au port d’AEM ou de Dispatcher
   * Il existe différentes mesures pour la création, la publication et le dispatcher.

#### Stockage {#storage}

* **Espace disque**: Espace disque utilisé (en mégaoctets) pour chaque point de montage sur l’hôte
   * Il existe différentes mesures pour chaque point de montage.
   * Au minimum, il existe des mesures pour `/` et `/mnt`, mais d’autres mesures de point de montage peuvent être disponibles en fonction de la configuration d’instance spécifique.
* **Taille du dossier**
* **Boutique de segments AEM**: Espace disque utilisé (en gigaoctets) pour l’entrepôt de segments AEM

#### Application {#application}

* **Agent de réplication**: Durée (en secondes) d’un événement de réplication de test
   * Il existe des mesures distinctes pour chaque agent de réplication.
* **Purge du Dispatcher**: Le nombre d’éléments actuellement dans la file d’attente de vidage du dispatcher

## Création de rapports de contrat SLA {#sla-reporting}

Les clients peuvent voir les performances de leur environnement d’AEM de production par rapport à leur contrat de niveau de service (SLA). Cette option est disponible dans un sous-menu de la **Rapports** écran.

Le graphique suivant montre les performances mensuelles du contrat SLA pour 2018.

![Graphique SLA 2018](/help/assets/SLA-Reports-one.png)

Comme pour les graphiques de surveillance du système, le fait de survoler un point de données affiche les valeurs correspondant à ce mois.

![Survol des points de données](/help/assets/SLA-Reports-two.png)

Le **Analyse des événements** La section située sous ce graphique présente l’ensemble des incidents survenus pour le programme au cours de l’année sélectionnée. Chaque incident comporte une période, une cause et un ensemble de commentaires.

![Analyse des événements](/help/assets/sla-reporting3.png)

## Mesures SLA {#sla-metrics}

* **Contrat d’auteur** : il s’agit du contrat SLA défini dans le cadre de votre contrat avec Adobe Managed Services pour le niveau auteur.
* **Contrat SLA d’auteur AMS** : il s’agit de la période de disponibilité mesurée du niveau auteur de production comptabilisant les incidents causés par Adobe ou par nos fournisseurs.
* **Contrat SLA d’auteur** : il s’agit de la période de disponibilité mesurée du niveau auteur ignorant le temps d’arrêt planifié, tel que les fenêtres de maintenance.
* **Contrat utilisateur final** : il s’agit du contrat SLA défini dans votre contrat avec Adobe Managed Services pour le niveau publication.
* **Contrat SLA utilisateur final AMS** : il s’agit de la période de disponibilité mesurée du niveau publication de production comptabilisant les incidents causés par Adobe ou par nos fournisseurs.
* **Contrat SLA utilisateur final** : il s’agit de la période de disponibilité mesurée du niveau publication ignorant le temps d’arrêt planifié, tel que les fenêtres de maintenance.

## Tutoriel vidéo {#video-tutorial}

Cette vidéo fournit un aperçu de l’utilisation des graphiques générés par les rapports Cloud Manager pour une vue d’ensemble de vos environnements de programme.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
