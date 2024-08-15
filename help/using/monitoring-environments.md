---
title: Surveillance des environnements
description: Découvrez comment surveiller vos environnements dans Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 4c4a2688cab8e5c81efa4b7b5e26f3c7b5dc30d6
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 33%

---


# Surveiller les environnements {#monitoring-environments}

Découvrez comment surveiller vos environnements dans Cloud Manager.

## Seuils de mesure {#thresholds}

La surveillance du système dans [!UICONTROL Cloud Manager] est réalisée en observant les instances dans un environnement et en suivant diverses mesures pour chaque instance. Chaque mesure a deux seuils définis : un seuil de *avertissement* et un seuil *critique*.

Si une mesure est supérieure à son seuil d’avertissement (mais inférieure à son seuil critique), elle est considérée comme étant dans un état d’avertissement.

Si une mesure dépasse son seuil critique, elle est considérée comme étant dans un état critique.

Adobe Managed Services définit les seuils, que vous pouvez afficher dans [!UICONTROL Cloud Manager]. Dans la plupart des cas, les seuils sont cohérents entre les clients, mais dans certains cas, Adobe Managed Services modifie les seuils pour répondre aux besoins spécifiques des clients. Posez toutes les questions que vous avez concernant les seuils à votre ingénieur du service client.

## Surveillance du système d’accès {#accessing-system-monitoring}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation et le programme appropriés.

1. Cliquez sur le bouton représentant des points de suspension du programme que vous souhaitez surveiller.
1. Dans le menu, sous l’en-tête **Gérer**, cliquez sur **Afficher la surveillance** pour ouvrir la page **Rapports** qui affiche les informations de surveillance du système.

   ![Paramètres](/help/assets/first-timea1.png)

.

## Présentation de la surveillance du système {#system-monitoring-overview}

La section **Surveillance du système** de la page **Rapports** répertorie les environnements surveillés dans le programme. Il fait état de leur état de santé général dans les quatre catégories distinctes suivantes :

* Hôte
* Stockage
* Réseau
* Application

L’état de chaque catégorie est un résumé des mesures individuelles. Si une mesure d’une catégorie est dans un état critique, l’ensemble de la catégorie est dans un état critique aux fins de la page d’aperçu. La même synthèse peut être affichée au niveau d’un environnement et au niveau d’une instance.

![Présentation de la surveillance du système](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Par défaut, lorsque vous accédez à cette page, les instances d’environnement de production sont visibles, mais d’autres environnements peuvent également être affichés.

## Détails de la surveillance du système {#system-monitoring-detail}

Pour afficher les détails de mesures spécifiques, cliquez sur l’une des colonnes de catégories d’une instance spécifique ou sur le titre de la catégorie dans le volet de navigation de gauche. Chaque page de détail présente une série de graphiques pour les mesures de cette catégorie. Vous pouvez afficher les mesures de toutes les instances dans un environnement ou pour une instance spécifique. Vous pouvez basculer entre l’environnement et les instances à l’aide des listes déroulantes dans le coin supérieur droit.

![Sélectionner l’environnement](/help/assets/System_Monitoring1.png)

La navigation à gauche affiche les mesures disponibles dans la catégorie actuellement sélectionnée pour laquelle il existe des données pour l’environnement et les instances sélectionnés.

Un graphique séparé indique l’état et les données dans le temps avec les seuils. Si plusieurs instances sont affichées, les données de chaque instance se trouvent dans une série distincte.

![Graphique de mesures](/help/assets/Monitoring_Graphs1.png)

Une série peut être masquée dans un graphique en cliquant dessus dans la légende.
Par exemple, si vous cliquez sur la série de seuil d’avertissement, seul le seuil critique s’affiche.

![Modifier le graphique](/help/assets/Monitoring_Graphs2.png)

### Définitions des mesures {#metric-definitions}

#### Hôte {#host}

* **Load Per Core** : nombre de processus que le processeur exécute. Ou, le nombre de processus en file d’attente dont l’état est en attente a été calculé en moyenne sur une période de un (load1), cinq (load5) et quinze (load15) minutes.
* **Process Count** : nombre de processus actuellement ouverts.
* **Nombre d’utilisateurs** : nombre d’utilisateurs ayant une session shell active.
* **Utilisation de la mémoire** : pourcentage de la mémoire système actuellement allouée.
* **Mémoire JVM** : taille (en mégaoctets) du tas Java alloué.
* **Espace d’ancienne génération** : pourcentage de la mémoire de l’ancienne génération de la JVM allouée actuellement.

#### Réseau {#network}

* **Vérification du port CQ** : délai de réponse en secondes pour accéder au port AEM ou Dispatcher. Il existe différentes mesures pour l’auteur, la publication et Dispatcher.

#### Stockage  {#storage}

* **Espace disque** : espace disque utilisé (en mégaoctets) pour chaque point de montage sur l’hôte. Il existe différentes mesures pour chaque point de montage. Il existe au minimum des mesures pour `/` et `/mnt`, mais des mesures de point de montage supplémentaires peuvent être disponibles en fonction de la configuration d’instance spécifique.
* **Taille du dossier**
* **Boutique de segments d’AEM** : espace disque utilisé (en gigaoctets) pour l’entrepôt de segments AEM.

#### Application {#application}

* **Agent de réplication** : durée, en secondes, d’un événement de réplication de test.
   * Il existe des mesures distinctes pour chaque agent de réplication.
* **Dispatcher Flush** : nombre d’éléments actuellement dans la file d’attente de purge de Dispatcher

## Rapports SLA {#sla-reporting}

Vous pouvez consulter les performances de votre environnement de production AEM correspondant au contrat de niveau de service (SLA) auquel vous avez souscrit.

Le graphique suivant montre les performances mensuelles du contrat de niveau de service pour 2019.

![Graphique SLA pour 2018](/help/assets/SLA-Reports-one.png)

Comme pour les graphiques de surveillance du système, le fait de survoler un point de données affiche les valeurs correspondant à ce mois.

![Survol des points de données](/help/assets/SLA-Reports-two.png)

La section **Analyse des événements** sous ce graphique affiche l’ensemble des incidents qui se sont produits pour le programme au cours de l’année sélectionnée. Chaque incident comporte une période, une cause et un ensemble de commentaires.

![Analyse des événements](/help/assets/sla-reporting3.png)

## Mesures SLA {#sla-metrics}

* **Contrat d’auteur** : SLA défini dans votre contrat avec Adobe Managed Services pour le niveau auteur.
* **SLA d’auteur AMS** : temps de disponibilité mesuré du niveau de création de production, tenant compte des incidents causés par les fournisseurs ou par Adobe.
* **Author SLA** : temps de disponibilité mesuré du niveau auteur ignorant le temps d’arrêt planifié tel que les fenêtres de maintenance.
* **Contrat utilisateur final** : SLA défini dans votre contrat avec Adobe Managed Services pour le niveau publication.
* **SLA utilisateur final AMS** : temps de disponibilité mesuré du niveau de publication de production, tenant compte des incidents causés par les fournisseurs ou par Adobe.
* **SLA de l’utilisateur final** : temps de disponibilité mesuré du niveau publication ignorant le temps d’arrêt planifié tel que les fenêtres de maintenance.

## Tutoriel vidéo {#video-tutorial}

Cette vidéo présente l’utilisation des graphiques générés par les rapports Cloud Manager pour une vue d’ensemble de vos environnements de programme.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
