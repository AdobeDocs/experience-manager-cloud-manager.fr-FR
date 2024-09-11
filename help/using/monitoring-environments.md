---
title: Surveiller les environnements
description: Découvrez comment surveiller vos environnements dans Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '910'
ht-degree: 100%

---


# Surveiller les environnements {#monitoring-environments}

Découvrez comment surveiller vos environnements dans Cloud Manager.

## Seuils pour les mesures {#thresholds}

La surveillance du système dans [!UICONTROL Cloud Manager] est réalisée en observant les instances individuelles dans un environnement et en suivant diverses mesures pour chaque instance. Chaque mesure possède deux seuils définis : un seuil d’*avertissement* et un seuil *critique*.

Si une mesure est supérieure à son seuil d’avertissement (mais inférieure à son seuil critique), elle est considérée comme étant dans un état d’avertissement.

Si une mesure dépasse son seuil critique, elle est considérée comme étant dans un état critique.

Adobe Managed Services définit les seuils, que vous pouvez afficher dans [!UICONTROL Cloud Manager]. Dans la plupart des cas, les seuils sont cohérents entre les clientes et clients. Mais dans certains cas, Adobe Managed Services modifie les seuils pour répondre à leurs besoins spécifiques. Posez toutes les questions que vous avez concernant les seuils à votre équipe d’ingénierie du service client.

## Accéder à la surveillance du système {#accessing-system-monitoring}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation et le programme appropriés.

1. Cliquez sur le bouton représentant des points de suspension du programme que vous souhaitez surveiller.
1. Dans le menu, sous l’en-tête **Gérer**, cliquez sur **Afficher la surveillance** pour ouvrir la page **Rapports** qui affiche les informations de surveillance du système.

   ![Paramètres](/help/assets/first-timea1.png)

.

## Vue d’ensemble de la surveillance du système {#system-monitoring-overview}

La section **Surveillance du système** de la page **Rapports** répertorie les environnements surveillés dans le programme. Elle rend compte de leur intégrité de haut niveau dans les quatre catégories distinctes suivantes :

* Hôte
* Stockage
* Réseau
* Application

Le statut de chaque catégorie est un résumé des mesures individuelles. Si une mesure d’une catégorie est dans un état critique, l’ensemble de la catégorie est dans un état critique aux fins de la page de vue d’ensemble. La même synthèse peut être affichée au niveau d’un environnement et au niveau d’une instance.

![Présentation de la surveillance du système](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Par défaut, lorsque vous accédez à cette page, les instances d’environnement de production sont visibles, mais d’autres environnements peuvent également être affichés.

## Détails de la surveillance du système {#system-monitoring-detail}

Pour consulter les détails de mesures spécifiques, cliquez sur l’une des colonnes de catégorie d’une instance spécifique ou sur le titre de la catégorie dans le volet de navigation de gauche. Chaque page de détail présente une série de graphiques pour les mesures de cette catégorie. Vous pouvez afficher les mesures de toutes les instances dans un environnement ou pour une instance spécifique. Vous pouvez basculer entre l’environnement et les instances à l’aide des listes déroulantes dans le coin supérieur droit.

![Sélectionner l’environnement](/help/assets/System_Monitoring1.png)

La navigation à gauche affiche les mesures disponibles dans la catégorie sélectionnée pour laquelle il existe des données pour l’environnement et les instances sélectionnés.

Un graphique séparé indique le statut et les données dans le temps avec les seuils. Si plusieurs instances sont affichées, les données de chaque instance se trouvent dans une série distincte.

![Graphique de mesures](/help/assets/Monitoring_Graphs1.png)

Une série peut être masquée dans un graphique en cliquant dessus dans la légende.
Par exemple, si vous cliquez sur la série de seuil d’avertissement, vous ne verrez que le seuil critique.

![Modification de graphique](/help/assets/Monitoring_Graphs2.png)

### Définitions des mesures {#metric-definitions}

#### Hôte {#host}

* **Charger par noyau** : nombre de processus que le processeur exécute. Ou, le nombre de processus en file d’attente dont l’état est en attente a été calculé en moyenne sur une période d’une (load1), de cinq (load5) et de quinze (load15) minutes.
* **Nombre de processus** : nombre de processus actuellement ouverts.
* **Nombre d’utilisateurs et d’utilisatrices** : nombre d’utilisateurs et d’utilisatrices disposant d’une session shell active.
* **Utilisation de la mémoire** : pourcentage de la mémoire système actuellement allouée.
* **Mémoire JVM** : taille (en mégaoctets) du tas Java alloué.
* **Espace de l’ancienne génération** : pourcentage de la mémoire de la JVM de l’ancienne génération actuellement allouée.

#### Réseau {#network}

* **Vérification du port CQ** : délai de réponse en secondes pour accéder au port AEM ou Dispatcher. Il existe différentes mesures pour les instances de création et de publication et le Dispatcher.

#### Stockage {#storage}

* **Espace disque** : espace disque utilisé (en mégaoctets) pour chaque point de montage sur l’hôte. Il existe différentes mesures pour chaque point de montage. Au minimum, les mesures `/` et `/mnt` sont disponibles, mais des mesures de point de montage supplémentaires peuvent être disponibles selon la configuration d’instance spécifique.
* **Taille du dossier**
* **Banque de segments AEM** : espace disque utilisé (en gigaoctets) pour la banque de segments AEM.

#### Application {#application}

* **Agent de réplication** : durée, en secondes, d’un événement de réplication de test.
   * Il existe des mesures distinctes pour chaque agent de réplication.
* **Vidage du Dispatcher** : nombre d’éléments actuellement présents dans la file d’attente de vidage du Dispatcher

## Création de rapports SLA {#sla-reporting}

Vous pouvez consulter les performances de votre environnement de production AEM correspondant au contrat de niveau de service (SLA) auquel vous avez souscrit.

Le graphique suivant montre les performances mensuelles du contrat de niveau de service pour 2019.

![Graphique SLA pour 2018](/help/assets/SLA-Reports-one.png)

Comme pour les graphiques de surveillance du système, le fait de survoler un point de données affiche les valeurs correspondant à ce mois.

![Survol des points de données](/help/assets/SLA-Reports-two.png)

La section **Analyse des événements**, située sous ce graphique, affiche l’ensemble des incidents survenus pour le programme au cours de l’année sélectionnée. Chaque incident comporte une période, une cause et un ensemble de commentaires.

![Analyse des événements](/help/assets/sla-reporting3.png)

## Mesures SLA {#sla-metrics}

* **Contrat de création** : il s’agit de l’accord SLA défini dans le cadre de votre contrat avec Adobe Managed Services pour le niveau création.
* **SLA de création AMS** : il s’agit de la période de disponibilité mesurée du niveau création de production comptabilisant les incidents causés par Adobe ou par nos fournisseurs.
* **SLA de création** : il s’agit de la période de disponibilité mesurée du niveau création ignorant le temps d’arrêt planifié, tel que les fenêtres de maintenance.
* **Contrat d’utilisation finale** : il s’agit de l’accord SLA défini dans votre contrat avec Adobe Managed Services pour le niveau de publication.
* **SLA d’utilisation finale AMS** : il s’agit de la période de disponibilité mesurée du niveau de publication de production comptabilisant les incidents causés par Adobe ou par nos fournisseurs.
* **SLA d’utilisation finale** : il s’agit de la période de disponibilité mesurée du niveau de publication ignorant le temps d’arrêt planifié, tel que les fenêtres de maintenance.

## Tutoriel vidéo {#video-tutorial}

Cette vidéo présente une vue d’ensemble de l’utilisation des graphiques générés par les rapports Cloud Manager pour une vue d’ensemble de vos environnements de programme.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
