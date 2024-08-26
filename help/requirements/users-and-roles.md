---
title: Ajouter des utilisateurs et des rôles
description: Découvrez comment utiliser l’Admin Console pour ajouter des utilisateurs et des rôles, et créer des profils.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 65%

---


# Ajouter des utilisateurs et utilisatrices et des rôles {#add-users-and-roles}

De nombreuses fonctionnalités de [!UICONTROL Cloud Manager] nécessitent des autorisations spécifiques. Par exemple, seuls certains utilisateurs sont autorisés à définir les indicateurs de performance clés (ICP) d’un programme. Ces autorisations sont regroupées de manière logique en rôles.

[!UICONTROL Cloud Manager] définit actuellement quatre rôles pour les utilisateurs, qui régissent la disponibilité de fonctionnalités spécifiques :

* Propriétaire de l’entreprise
* Responsable de programme
* Responsable de déploiement
* Développeur

>[!NOTE]
>
>Pour utiliser [!UICONTROL Cloud Manager], vous devez disposer d’un Adobe ID et du contexte du produit Adobe Managed Services.

## Définitions de rôle {#role-definitions}

Le tableau suivant résume les rôles dans Cloud Manager.

| Rôle [!UICONTROL Cloud Manager] | Description |
| --- | --- |
| Propriétaire de l’entreprise | Responsable de la définition des indicateurs de performance clés, de l’approbation des déploiements en production et de la surévaluation des échecs de trois niveaux importants lorsque cela est nécessaire. |
| Responsable de programme | Ils utilisent [!UICONTROL Cloud Manager] pour configurer l’équipe, passer en revue l’état, afficher les indicateurs de performance clés et approuver des échecs de trois niveaux importants si nécessaire. |
| Responsable de déploiement | Gère les opérations de déploiement et utilise [!UICONTROL Cloud Manager] pour exécuter les déploiements d’évaluation et de production, modifier les pipelines CI/CD et approuver les échecs à trois niveaux critiques si nécessaire. Ils ont également accès au référentiel Git. |
| Développeur ou développeuse | Développe et teste du code d’application personnalisé. Il utilise principalement [!UICONTROL Cloud Manager] pour afficher l’état du déploiement et peut accéder au référentiel Git pour les validations de code. |
| Ingénieur du succès client | L’ingénieur du service client prend généralement en charge le succès client pour les clients AMS. Ils interagissent avec [!UICONTROL Cloud Manager] dans le but d’exécuter des déploiements nécessitant la supervision de l’ingénieur du service client. |
| Auteur ou autrice de contenu | Ils n’interagissent généralement pas avec [!UICONTROL Cloud Manager], mais peuvent utiliser le sélecteur de programme [!UICONTROL Cloud Manager] pour accéder à AEM. |

>[!NOTE]
>
>Dans Admin Console, la personne désignée comme développeur n’a aucun rapport avec le rôle de développeur dans [!UICONTROL Cloud Manager].

## Créer un profil à l’aide de l’Admin Console {#using-admin-console-to-create-a-profile}

Les rôles de [!UICONTROL Cloud Manager] sont gérés depuis Admin Console. Des rôles spécifiques sont attribués en ajoutant un utilisateur à un profil de produit [!UICONTROL Cloud Manager].

Admin Console fournit un emplacement centralisé pour gérer les droits Adobe dans l’ensemble de votre organisation. Pour en savoir plus sur Adobe Admin Console, voir [Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html).

Un administrateur doit créer de nouveaux profils de produit sous le contexte du produit [!UICONTROL Managed Services] pour attribuer des autorisations basées sur les rôles aux utilisateurs de [!UICONTROL Cloud Manager], correspondant à chacun des quatre rôles [!UICONTROL Cloud Manager].

* Propriétaire de l’entreprise
* Responsable de déploiement
* Développeur
* Responsable de programme

Vous pouvez créer ou ajouter des utilisateurs ou des groupes à ces profils de produit avec l’Admin Console.

1. Connectez-vous à Admin Console à l’adresse [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

1. Cliquez sur l’onglet **Overview** , puis sur le produit à modifier sur la carte **Products and Services** . S’il n’y est pas répertorié, cherchez le produit dans l’onglet **Produits** et cliquez dessus.

   ![Onglet de présentation d’Admin Console](/help/assets/admin-console-overview.png)

1. Dans l’onglet **Produits**, cliquez sur l’environnement dans lequel vous souhaitez ajouter des utilisateurs/groupes à des profils de produit.

   ![Onglet Produits d’Admin Console](/help/assets/admin-console-product.png)

1. Dans l’onglet **Profil de produit** du produit, cliquez sur **Nouveau profil** pour ajouter un profil.

   ![Nouveau profil](/help/assets/admin-console-product-profiles.png)

1. Fournissez les informations requises afin de configurer un nouveau rôle pour [!UICONTROL Cloud Manager].

   * **Nom de profil** : vous pouvez saisir le **nom de profil** que vous souhaitez. Toutefois, afin d’éviter toute confusion, il est recommandé d’utiliser les valeurs de la colonne **Nom de profil recommandé**.
   * **Nom d’affichage** - Le **nom d’affichage** doit correspondre à la valeur technique définie par [!UICONTROL Cloud Manager] (voir le tableau ci-dessous).
   * **Groupe d’autorisations** - Vous pouvez choisir un groupe d’autorisations pour le profil (pas toujours disponible).

   ![Créer un profil](/help/assets/screen_shot_2018-05-04at171819.png)

   | Rôle | Nom d’affichage (obligatoire) | Nom de profil recommandé |
   |---|---|---|
   | Propriétaire de l’entreprise | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle du propriétaire de l’entreprise |
   | Responsable de déploiement | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle de responsable de déploiement |
   | Développeur | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle de développeur |
   | Responsable de programme | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle de responsable de programme |


1. Cliquez sur **Terminé** pour enregistrer le nouveau profil.

## Affecter des profils à des utilisateurs et utilisatrices ou à des groupes d’utilisateurs et utilisatrices {#assign-profiles}

Une fois que vous avez créé des profils de produit, vous pouvez leur affecter des utilisateurs et utilisatrices ou des groupes d’utilisateurs et utilisatrices.

1. Connectez-vous à Admin Console à l’adresse [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

1. Dans Admin Console, choisissez l’onglet **Utilisateurs**.

   ![Onglet Utilisateurs](/help/assets/admin-console-users.png)

1. Cliquez sur **Utilisateurs et utilisatrices** dans le panneau de navigation de gauche, puis cliquez sur le nom d’une personne pour effectuer des modifications.

1. Cliquez sur le bouton représentant des points de suspension dans la section **Produits** et sélectionnez **Modifier**.

   ![Modification de l’utilisateur ou de l’utilisatrice](/help/assets/admin-console-edit-user.png)

1. Dans la boîte de dialogue **Modifier des produits et des groupes d’utilisateurs et utilisatrices**, cliquez sur le bouton représentant le signe plus et sélectionnez les profils à affecter à la personne.

   * Si la personne est déjà affectée aux rôles, le bouton représentant le signe plus sera un bouton de modification (un crayon), mais fonctionnera de la même manière.

   ![Modifier des produits et des groupes d’utilisateurs](/help/assets/admin-console-edit-products-and-user-groups.png)

1. Cliquez sur **Enregistrer** pour enregistrer les profils de l’utilisateur.

Répétez les mêmes étapes pour affecter des profils à des groupes d’utilisateurs, mais sélectionnez **Groupes d’utilisateurs** dans le panneau de navigation de gauche dans l’onglet **Utilisateurs**. Cliquez sur un groupe d’utilisateurs et utilisatrices et sélectionnez l’onglet **Profils de produit affectés**, puis cliquez sur **Affecter un profil de produit** pour affecter des profils.

![Affectation de profils à un groupe](/help/assets/admin-console-edit-user-groups.png)
