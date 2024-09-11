---
title: Informations d’accès au référentiel
description: Découvrez comment accéder à votre référentiel Git géré par Adobe et comment le gérer à l’aide de la gestion de compte Git en libre-service, à partir de Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '361'
ht-degree: 100%

---

# Informations d’accès au référentiel {#accessing-repos}

Découvrez comment accéder à votre référentiel Git géré par Adobe et comment le gérer à l’aide de la gestion de compte Git en libre-service, à partir de Cloud Manager.

## Accéder aux informations du référentiel à partir de la page Vue d’ensemble {#overview-page}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme**.

   ![Bouton Accéder aux informations sur le référentiel de la carte Environnements](assets/pipelines-card.png)

1. Cliquez sur **Accéder aux informations sur le référentiel**. Dans la boîte de dialogue **Informations sur le référentiel pour…**, vous pouvez afficher les éléments suivants :

   * Le nom d’utilisateur ou d’utilisatrice Git.
   * Le mot de passe Git.
   * L’URL vers le référentiel Git de Cloud Manager.
   * Des commandes Git préconfigurées pour ajouter rapidement un référentiel distant à votre référentiel Git et pour transférer du code.

   ![Fenêtre Informations sur le référentiel](assets/access-repo-info.png)

1. Pour accéder au mot de passe, un nouveau mot de passe doit être généré. Cliquez sur **`Generate password`**.

1. Dans la boîte de dialogue **Voulez-vous vraiment…**, confirmez la génération de mot de passe en cliquant sur **Générer un mot de passe**.

   ![Confirmation de la génération du mot de passe](assets/confirm-password-generation.png)

1. Dans le champ **Mot de passe**, le mot de passe est généré. Cliquez sur l’icône Copier pour le copier dans le presse-papiers.

   * La génération d’un mot de passe invalide le mot de passe précédent.
   * Cloud Manager n’enregistre pas votre mot de passe d’accès. Veillez à enregistrer ce mot de passe en toute sécurité.
   * Si vous perdez le mot de passe, vous devez en générer un nouveau.

   ![Exemple de mot de passe généré](assets/generated-password.png)

À l’aide de ces informations d’identification, vous pouvez cloner une copie locale du référentiel et apporter des modifications à ce référentiel local. Lorsque vous avez terminé, vous pouvez ensuite valider toutes les modifications du code vers le référentiel de code distant dans Cloud Manager.

>[!NOTE]
>
>* L’option **Accéder aux informations sur le référentiel** est visible par les personnes possédant le rôle **Développeur ou développeuse** et/ou **Responsable de déploiement**.
>* Le bouton **Accéder aux informations sur le référentiel** n’affiche que les informations d’accès au référentiel pour les référentiels gérés par Adobe. Les informations d’accès relatives aux [référentiels privés](private-repositories.md) ne sont pas disponibles dans Cloud Manager.

## Accéder aux informations sur le référentiel à partir de la fenêtre Référentiels {#repositories-window}

Le bouton **Accéder aux informations sur le référentiel** est également présent dans la barre d’outils de la fenêtre [**Référentiels**](managing-repositories.md). Il affiche les mêmes informations sur l’accès aux référentiels gérés par Adobe.

## Révoquer un mot de passe d’accès {#revoke-password}

Vous pouvez révoquer un mot de passe d’accès à tout moment. [Créez un ticket d’assistance pour une telle requête](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support).

Le ticket est traité en priorité et la révocation est généralement effectuée dans la journée.
