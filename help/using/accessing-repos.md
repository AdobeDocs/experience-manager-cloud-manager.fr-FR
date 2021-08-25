---
title: Accès aux référentiels
seo-title: Accès aux référentiels
description: Cette page vous explique comment accéder au référentiel Git et le gérer.
seo-description: Consultez cette page pour découvrir comment accéder à votre référentiel Git et le gérer.
feature: Référentiels Git
exl-id: 403fc93d-60fc-4439-8c9d-0a512ca34458
source-git-commit: 5bbe76a46b7a15ccbab85c4487d2a20aaf59a4e7
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 63%

---

# Accès aux référentiels {#accessing-repos}

Vous pouvez accéder à votre référentiel Git et le gérer à l’aide de la gestion de compte Git en libre-service à partir de l’interface utilisateur de Cloud Manager.

## Utilisation de la gestion de compte Git en libre-service {#self-service-git}

Utilisez le bouton **Accéder aux informations sur le référentiel** disponible dans l’interface utilisateur de Cloud Manager, notamment sur la carte du pipeline.

1. Accédez à la carte **Pipelines** à partir de votre page **Aperçu du programme**.

1. Vous verrez l’option **Accéder à Repo Info** pour accéder à votre référentiel Git et le gérer.

   ![](assets/access-repo1.png)

   De plus, si vous sélectionnez l’onglet de pipeline **Non-production**, vous y verrez également l’option **Accéder à Repo Info**.

   ![](assets/access-repo-nonprod.png)


   >[!NOTE]
   >L’option **Accéder à Repo Info** est visible par les utilisateurs avec le rôle Développeur ou Gestionnaire de déploiement . Lorsque l’utilisateur clique sur ce bouton, il accède à une boîte de dialogue qui lui permet de trouver l’URL de son référentiel Git Cloud Manager, ainsi que son nom d’utilisateur et son mot de passe.

   ![](assets/access-repo-create.png)

   Les points importants à prendre en compte pour gérer votre Git dans Cloud Manager sont les suivants :

   * **URL** : URL du référentiel
   * **Nom d’utilisateur** : nom d’utilisateur
   * **Mot de passe** : valeur affichée lorsque vous cliquez sur le bouton **Générer un mot de passe**.


      >[!NOTE]
      >Un utilisateur peut extraire une copie de son code et effectuer des modifications dans le référentiel de code local. Une fois prêt, l’utilisateur peut valider les modifications de code dans le référentiel de code distant dans Cloud Manager.