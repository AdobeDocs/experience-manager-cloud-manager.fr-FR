---
title: Ajouter des utilisateurs et des rôles
description: Découvrez comment utiliser Admin Console pour ajouter des utilisateurs et des rôles ainsi que créer des profils.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: dd96d773ea3e6b9c45886fe41b28d3dd70cb8a61
workflow-type: tm+mt
source-wordcount: '774'
ht-degree: 96%

---


# Ajouter des utilisateurs et des rôles {#add-users-and-roles}

De nombreuses fonctionnalités de [!UICONTROL Cloud Manager] nécessitent des autorisations spécifiques. Par exemple, seuls certains utilisateurs sont autorisés à définir les indicateurs de performance clés (ICP) d’un programme. Ces autorisations sont regroupées de manière logique en rôles.

[!UICONTROL Cloud Manager] définit actuellement quatre rôles pour les utilisateurs qui régissent la disponibilité de fonctionnalités spécifiques :

* Propriétaire de l’entreprise
* Responsable de programme
* Responsable de déploiement
* Développeur

>[!NOTE]
>
>Pour utiliser [!UICONTROL Cloud Manager], vous devez disposer d’un Adobe ID et du contexte du produit Adobe Managed Services.

## Définitions des rôles {#role-definitions}

Ce tableau résume les rôles.

| Rôle dans [!UICONTROL Cloud Manager] | Description |
|--- |--- |
| Propriétaire de l’entreprise | Cet utilisateur est chargé de définir les indicateurs de performance clés, d’approuver les déploiements en production et de remplacer les échecs importants à 3 niveaux si nécessaire. |
| Responsable de programme | Cet utilisateur utilise [!UICONTROL Cloud Manager] pour effectuer la configuration de l’équipe, réviser l’état, afficher les ICP et approuver les échecs importants à 3 niveaux si nécessaire. |
| Responsable de déploiement | Cet utilisateur gère les opérations de déploiement et utilise [!UICONTROL Cloud Manager] pour exécuter des déploiements d’évaluation/de production, modifier les pipelines CI/CD ou approuver des échecs importants à 3 niveaux si nécessaire. Il peut également accéder au référentiel Git. |
| Développeur | Cet utilisateur développe et teste des codes d’application personnalisés et utilise principalement [!UICONTROL Cloud Manager] pour afficher l’état du déploiement. Il peut accéder au référentiel Git pour les validations de code. |
| Ingénieur du succès client | Cet utilisateur prend généralement en charge le succès client pour les clients AMS et interagit avec [!UICONTROL Cloud Manager] dans le but d’exécuter des déploiements nécessitant la supervision du CSE. |
| Auteur de contenu | Cet utilisateur n’interagit généralement pas avec [!UICONTROL Cloud Manager] mais peut utiliser le sélecteur de programmes de [!UICONTROL Cloud Manager] pour accéder à AEM. |

>[!NOTE]
>
>Dans Admin Console, la personne désignée comme développeur n’a aucun rapport avec le rôle de développeur dans [!UICONTROL Cloud Manager].

## Utiliser Admin Console pour créer un profil {#using-admin-console-to-create-a-profile}

Les rôles de [!UICONTROL Cloud Manager] sont gérés depuis Admin Console. Des rôles spécifiques sont attribués en ajoutant un utilisateur à un profil de produit [!UICONTROL Cloud Manager].

Admin Console fournit un emplacement centralisé pour gérer les droits Adobe dans l’ensemble de votre organisation. Pour en savoir plus sur Adobe Admin Console, consultez la documentation d’[Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html).

Afin d’accorder les autorisations appropriées basées sur les rôles aux utilisateurs de [!UICONTROL Cloud Manager], un administrateur de l’organisation du client doit créer des profils de produit sous le contexte du produit [!UICONTROL AEM Managed Services], chacun correspondant à l’un des quatre rôles de [!UICONTROL Cloud Manager] :

* Propriétaire de l’entreprise
* Responsable de déploiement
* Développeur
* Responsable de programme

Vous pouvez créer ou ajouter des utilisateurs/groupes à ces profils de produit avec Admin Console.

1. Connectez-vous à Admin Console à l’adresse [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

1. Cliquez sur l’onglet **Présentation**, cliquez sur le produit à modifier dans la vignette **Produits et services**. S’il n’y est pas répertorié, cherchez le produit dans l’onglet **Produits** et cliquez dessus.

   ![Onglet de présentation d’Admin Console](/help/assets/admin-console-overview.png)

1. Dans l’onglet **Produits**, cliquez sur l’environnement dans lequel vous souhaitez ajouter des utilisateurs/groupes à des profils de produit.

   ![Onglet Produits d’Admin Console](/help/assets/admin-console-product.png)

1. Dans l’onglet **Profil de produit** du produit, cliquez sur **Nouveau profil** pour ajouter un profil.

   ![Nouveau profil](/help/assets/admin-console-product-profiles.png)

1. Fournissez les informations requises afin de configurer un nouveau rôle pour [!UICONTROL Cloud Manager].

   * **Nom du profil** - Le **Nom du profil** peut être de n’importe quel type, mais pour éviter toute confusion, il est recommandé d’utiliser les valeurs de la colonne **Nom de profil recommandé**.
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

## Affecter de profils à des utilisateurs ou à des groupes d’utilisateurs {#assign-profiles}

Une fois que vous avez créé des profils de produit, vous pouvez leur affecter des utilisateurs ou des groupes d’utilisateurs.

1. Connectez-vous à Admin Console à l’adresse [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

1. Dans Admin Console, choisissez l’onglet **Utilisateurs**.

   ![Onglet Utilisateurs](/help/assets/admin-console-users.png)

1. Cliquez sur **Utilisateurs** dans le panneau de navigation de gauche, puis cliquez sur un utilisateur pour le modifier.

1. Cliquez sur le bouton représentant des points de suspension dans la section **Produits** et sélectionnez **Modifier**.

   ![Modifier l’utilisateur](/help/assets/admin-console-edit-user.png)

1. Dans la boîte de dialogue **Modifier des produits et des groupes d’utilisateurs**, cliquez sur le bouton représentant le signe plus et sélectionnez les profils à affecter à l’utilisateur.

   * Si l’utilisateur est déjà affecté aux rôles, le bouton représentant le signe plus sera un bouton de modification (un crayon), mais fonctionnera de la même manière.

   ![Modifier des produits et des groupes d’utilisateurs](/help/assets/admin-console-edit-products-and-user-groups.png)

1. Cliquez sur **Enregistrer** pour enregistrer les profils de l’utilisateur.

Répétez les mêmes étapes pour affecter des profils à des groupes d’utilisateurs, mais sélectionnez **Groupes d’utilisateurs** dans le panneau de navigation de gauche dans l’onglet **Utilisateurs**. Cliquez sur un groupe d’utilisateurs et sélectionnez l’onglet **Profils de produit attribués** et cliquez sur **Attribuer profil de produit** pour affecter des profils.

![Affecter des profils à un groupe](/help/assets/admin-console-edit-user-groups.png)
