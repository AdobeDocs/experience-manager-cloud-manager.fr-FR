---
title: Notifications
description: Découvrez comment Cloud Manager vous informe des événements importants.
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '561'
ht-degree: 100%

---


# Notifications {#notifications}

Découvrez comment Cloud Manager vous informe des événements importants.

## Notifications dans Cloud Manager {#cloud-manager-notifications}

[!UICONTROL Cloud Manager] vous envoie des notifications lorsqu’un pipeline de production démarre et se termine (avec succès ou non) au début d’un déploiement en production, ainsi que lorsque les étapes **Approbation de mise en production** et **Planifié** sont atteintes. Ces notifications sont envoyées via le système de notification [!UICONTROL Experience Cloud].

>[!NOTE]
>
>Les notifications Approbation et Planifié sont envoyées uniquement aux utilisateurs occupant les rôles de **Propriétaire d’entreprise**, **Gestionnaire de programme** et **Responsable de déploiement**.

Les notifications s’affichent dans une barre latérale dans [!UICONTROL Cloud Manager] et dans [!UICONTROL Experience Cloud] d’Adobe.

Les nouvelles notifications sont signalées sur l’icone en forme de cloche dans l’en-tête.

![Icône de notifications](/help/assets/notifications-bell-badged.png)

Cliquez sur l’icône en forme de cloche pour ouvrir la barre latérale et afficher les notifications. L’onglet **Notifications** dans la barre latérale répertorie les notifications les plus récentes, telles que les confirmations de déploiement. Les notifications concernent vos environnements.

![Barre latérale de notifications](/help/assets/notifications-activities.png)

L’onglet **Annonces** comprend les annonces de produits Adobe. Les annonces concernent le produit.

![Barre latérale de notifications](/help/assets/notificaitons-announcements.png)

Cliquez sur une notification ou une annonce pour en afficher les détails. Les notifications liées à des activités telles que les déploiements de pipeline vous permettent d’accéder aux informations de cette activité, telles que la fenêtre d’exécution du pipeline.

Cliquez sur l’option **Tout afficher** au bas du panneau pour afficher toutes les annonces dans votre boîte de réception.

Cliquez sur l’option **Tout marquer comme lu** au bas du panneau pour marquer toutes les notifications non lues comme lues et effacer le badge de l’icône en forme de cloche.

## Configuration des notifications {#configuration}

Vous pouvez personnaliser le mode de réception des notifications et les notifications que vous recevez.

Cliquez sur l’icône en forme d’engrenage en bas de la barre latérale de notifications.

![Icône Paramètres de notification](/help/assets/notifications-configuration.png)

La fenêtre **Préférences Experience Cloud** s’ouvre et vous pouvez définir vos abonnements aux notifications et comment vous recevez les notifications.

### Abonnements {#subscriptions}

Les abonnements définissent les produits pour lesquels vous recevez des notifications et leur type.

![Abonnements aux notifications](/help/assets/notifications-subscriptions.png)

Par défaut, vous recevez toutes les notifications pour tous les produits. Cliquez sur **Personnaliser** à côté d’un produit pour définir les types de notifications que vous recevez pour ce produit.

![Personnalisation de l’abonnement aux notifications](/help/assets/notifications-subscriptions-customize.png)

### Priorité {#priority}

Les alertes de priorité sont marquées d’une balise **ÉLEVÉE**. Vous pouvez les configurer pour les recevoir exclusivement en tant qu’alertes. Dans la section **Priorité**, vous pouvez définir les catégories qui remplissent les critères de notification de priorité.

![Priorité des notifications](/help/assets/notifications-priority.png)

Utilisez le menu déroulant pour ajouter à la liste des catégories qui remplissent les critères de priorité. Cliquez sur le `X` à côté des noms de catégorie pour les supprimer.

### Alertes {#alerts}

Les alertes s’affichent dans le coin supérieur droit de la fenêtre pendant quelques secondes. Utilisez la section **Alertes** pour définir les notifications pour lesquelles vous recevez des alertes.

![Alertes de notification](/help/assets/notifications-alerts.png)

Vous pouvez définir le comportement des alertes.

* **Afficher les alertes pour** - définit les types de notifications qui déclenchent des alertes
* **Les alertes doivent rester à l’écran jusqu’à ce que vous les supprimiez** : contrôle si les alertes doivent persister, sauf si vous les ignorez activement.
* **Durée** - définit la durée pendant laquelle l’alerte doit rester à l’écran si vous n’avez pas choisi de la conserver.

### E-mails {#emails}

Les notifications sont disponibles dans l’interface utilisateur web de toutes les solutions Adobe [!UICONTROL Experience Cloud]. Vous pouvez également choisir d’envoyer ces notifications par e-mail dans la section **E-mails**.

![E-mails de notification](/help/assets/notifications-emails.png)

Par défaut, aucun e-mail n‘est envoyé. Vous pouvez choisir de recevoir des e-mails :

* Immédiatement
* Chaque jour
* Chaque semaine

Lorsque vous choisissez **Notifications instantanées**, les e-mails sont envoyés immédiatement pour chaque notification. Pour **Résumé quotidien** et **Résumé hebdomadaire**, vous pouvez choisir le moment où votre résumé quotidien est envoyé, et le jour et le moment où votre résumé hebdomadaire est envoyé.
