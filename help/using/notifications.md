---
title: Notifications
description: Découvrez comment Cloud Manager vous informe des événements importants.
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
TQID: https://experienceleague.adobe.com/WBAHeIAH1XL6oVy342wLaUAoAHkUoN1AbcAl2Erkte4
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 65b260abe417925f26d647fb9857d32c30455f9b
workflow-type: tm+mt
source-wordcount: 562
ht-degree: 52%

---

# Notifications {#notifications}

Découvrez comment Cloud Manager vous informe des événements importants.

## Notifications dans Cloud Manager {#cloud-manager-notifications}

Des notifications sont envoyées lorsqu’un pipeline de production démarre et se termine (avec succès ou non) au cours d’un déploiement en production. ainsi que lorsque les étapes **Approbation de mise en production** et **Planifié** sont atteintes. Ces notifications sont envoyées via le système de notification [!UICONTROL Experience Cloud].

>[!NOTE]
>
>Les notifications Approbation et Planifié sont envoyées uniquement aux utilisateurs occupant les rôles de **Propriétaire d’entreprise**, **Gestionnaire de programme** et **Responsable de déploiement**.

Les notifications s’affichent dans une barre latérale dans [!UICONTROL Cloud Manager] et dans [!UICONTROL Experience Cloud] d’Adobe.

L’icône représentant une cloche dans l’en-tête affiche un indicateur lorsque vous recevez de nouvelles notifications.

![Icône de notifications](/help/assets/notifications-bell-badged.png)

Cliquez sur l’icône en forme de cloche pour ouvrir la barre latérale et afficher les notifications. L’onglet **Notifications** dans la barre latérale répertorie les notifications les plus récentes, telles que les confirmations de déploiement. Les notifications concernent vos environnements.

![Barre latérale de notifications](/help/assets/notifications-activities.png)

L’onglet **Annonces** comprend les annonces de produits Adobe. Les annonces fournissent des informations sur le produit.

![Barre latérale de notifications](/help/assets/notificaitons-announcements.png)

Cliquez sur une notification ou une annonce pour en afficher les détails. Les notifications liées à des activités telles que les déploiements de pipeline vous permettent d’accéder aux détails de cette activité, tels que la fenêtre d’exécution du pipeline.

Cliquez sur l’option **Afficher tout** au bas du panneau pour afficher toutes les annonces dans votre boîte de réception.

Cliquez sur l’option **Tout marquer comme lu** au bas du panneau pour marquer toutes les notifications non lues comme lues et supprimer le badge de l’icône en forme de cloche.

## Configuration des notifications {#configuration}

Vous pouvez personnaliser le mode de réception des notifications et les notifications que vous recevez.

Cliquez sur l’icône en forme d’engrenage en bas de la barre latérale de notifications.

![Icône Paramètres de notification](/help/assets/notifications-configuration.png)

La fenêtre **Préférences Experience Cloud** qui s’affiche vous permet de définir vos abonnements aux notifications et la manière dont vous recevez les notifications.

### Abonnements {#subscriptions}

Les abonnements définissent les produits pour lesquels vous recevez des notifications et les notifications que vous recevez.

![Abonnements aux notifications](/help/assets/notifications-subscriptions.png)

Par défaut, vous recevez toutes les notifications pour tous les produits. Pour définir les types de notifications que vous recevez pour un produit, cliquez sur **Personnaliser** en regard de celui-ci.

![Personnalisation de l’abonnement aux notifications](/help/assets/notifications-subscriptions-customize.png)

### Priorité {#priority}

Les alertes de priorité sont marquées d’une balise **ÉLEVÉE**. Vous pouvez les configurer pour qu’ils soient envoyés exclusivement en tant que notifications. Dans la section **Priorité**, vous pouvez définir les catégories qui remplissent les critères de notification de priorité.

![Priorité des notifications](/help/assets/notifications-priority.png)

Utilisez le menu déroulant pour ajouter à la liste des catégories qui remplissent les critères de priorité. Cliquez sur l’icône de suppression en regard des noms de catégorie pour les supprimer.

### Alertes {#alerts}

Les alertes s’affichent dans le coin supérieur droit de la fenêtre pendant quelques secondes. Utilisez la section **Alertes** pour définir les notifications pour lesquelles vous recevez des alertes.

![Alertes de notification](/help/assets/notifications-alerts.png)

Vous pouvez définir le comportement des alertes.

* **Afficher les alertes pour** - Définit les types de notifications qui déclenchent des alertes.
* **Les alertes restent à l’écran jusqu’à ce que vous les supprimiez** - Contrôle si les alertes persistent, sauf si vous les ignorez activement.
* **Durée** - Définit la durée pendant laquelle l’alerte reste à l’écran si vous n’avez pas choisi de la conserver.

### E-mails {#emails}

Les notifications sont disponibles dans l’interface utilisateur web de toutes les solutions Adobe [!UICONTROL Experience Cloud]. Pour recevoir ces notifications par e-mail, inscrivez-vous dans la section **E-mails**.

![E-mails de notification](/help/assets/notifications-emails.png)

Par défaut, aucun e-mail n’est envoyé. Vous pouvez choisir de recevoir des e-mails comme suit :

* Immédiatement
* Chaque jour
* Chaque semaine

Lorsque vous choisissez **Notifications instantanées**, les e-mails sont envoyés immédiatement pour chaque notification. Pour **Résumé quotidien** et **Résumé hebdomadaire**, vous pouvez choisir le moment où votre résumé quotidien est envoyé, et le jour et le moment où votre résumé hebdomadaire est envoyé.
