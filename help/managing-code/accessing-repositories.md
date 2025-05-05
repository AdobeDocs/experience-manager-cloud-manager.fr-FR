---
title: Informations d’accès au référentiel
description: Découvrez comment accéder à votre référentiel Git géré par Adobe et comment le gérer à l’aide de la gestion de compte Git en libre-service, à partir de Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 04fbc4a3fdba8b108055d66a4fdb1a31994cb18e
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Informations d’accès au référentiel {#accessing-repos}

Découvrez comment accéder à votre référentiel Git géré par Adobe et comment le gérer à l’aide de la gestion de compte Git en libre-service, à partir de Cloud Manager.

## Accéder aux informations du référentiel à partir de la page Vue d’ensemble {#overview-page}

Cloud Manager facilite la récupération des informations d’accès aux référentiels gérés par Adobe à l’aide du bouton **Accéder aux informations sur le référentiel** de la carte **Pipelines**.

La boîte de dialogue **Informations sur le référentiel** vous permet d’afficher les informations d’accès suivantes pour les référentiels gérés par Adobe :

* Le nom d’utilisateur ou d’utilisatrice Git.
* Le mot de passe Git.
* L’URL vers le référentiel Git de Cloud Manager.
* Des commandes Git préconfigurées pour ajouter rapidement un référentiel distant à votre référentiel Git et pour transférer du code.

  ![Fenêtre Informations sur le référentiel](assets/repository-info.png)

Les informations d’accès relatives aux [référentiels privés](/help/managing-code/private-repositories.md) ne sont pas disponibles dans Cloud Manager.

L’option **Accéder aux informations sur le référentiel** est visible par les utilisateurs et utilisatrices possédant les rôles **Développeur ou développeuse** ou **Responsable de déploiement**.

**Pour accéder aux informations du référentiel à partir de la page Vue d’ensemble :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans la page **Aperçu du programme**, sous la carte **Pipelines**, cliquez sur **Accéder aux informations sur le référentiel**.

   ![Bouton Accéder aux informations sur le référentiel de la carte Pipelines](/help/managing-code/assets/pipelines-card2.png)

1. Pour accéder au mot de passe, un nouveau mot de passe doit être généré. Dans la boîte de dialogue **Informations sur le référentiel**, sélectionnez **Générer un mot de passe**.

1. Dans la boîte de dialogue de confirmation, sélectionnez **Générer un mot de passe**.

1. À droite du champ **Mot de passe**, cliquez sur l’![Icône Copier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) pour copier le mot de passe dans le Presse-papiers.

   * La génération d’un mot de passe invalide le mot de passe précédent.
   * Cloud Manager n’enregistre pas le mot de passe. Il vous appartient d’enregistrer ce mot de passe en toute sécurité.
   * Étant donné que Cloud Manager n’enregistre pas le mot de passe, si vous le perdez, vous devez en régénérer un nouveau.

   ![Copier le mot de passe dans la boîte de dialogue Informations sur le référentiel](/help/managing-code/assets/repository-copy-password.png)

À l’aide de ces informations d’identification, vous pouvez cloner une copie locale du référentiel et apporter des modifications à ce référentiel local. Lorsque vous avez terminé, vous pouvez ensuite valider toutes les modifications du code vers le référentiel de code distant dans Cloud Manager.

## Accéder aux informations sur le référentiel à partir de la fenêtre Référentiels {#repositories-window}

La fonction **Accéder aux informations sur le référentiel** est également disponible sur la page [**Référentiels**](/help/managing-code/managing-repositories.md). Il affiche les mêmes informations sur l’accès aux référentiels gérés par Adobe.

## Révoquer un mot de passe d’accès {#revoke-password}

Vous pouvez révoquer un mot de passe d’accès à tout moment.

Pour ce faire, [créez un ticket d’assistance pour cette demande](https://experienceleague.adobe.com/fr?support-solution=Experience+Manager&amp;support-tab=home#support). Le ticket est traité en priorité et la révocation est généralement effectuée dans la journée.
