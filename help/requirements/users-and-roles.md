---
title: Ajouter des utilisateurs et des rôles
description: Découvrez comment utiliser Admin Console pour ajouter des utilisateurs et utilisatrices et des rôles ainsi que créer des profils.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: 53fb666ab6caff7a697d7f1942ce25f2bf27a2ce
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 89%

---


# Ajouter des utilisateurs et utilisatrices et des rôles {#add-users-and-roles}

De nombreuses fonctionnalités de [!UICONTROL Cloud Manager] nécessitent des autorisations spécifiques. Par exemple, seuls certains utilisateurs sont autorisés à définir les indicateurs de performance clés (ICP) d’un programme. Ces autorisations sont regroupées de manière logique en rôles.

[!UICONTROL Cloud Manager] définit actuellement quatre rôles pour les utilisateurs et utilisatrices qui régissent la disponibilité de fonctionnalités spécifiques :

* Propriétaire de l’entreprise
* Responsable de programme
* Responsable de déploiement
* Développeur ou développeuse

>[!NOTE]
>
>Pour utiliser [!UICONTROL Cloud Manager], vous devez disposer d’un Adobe ID et du contexte du produit Adobe Managed Services.

## Définitions de rôle {#role-definitions}

Le tableau suivant résume les rôles dans Cloud Manager.

| Rôle dans [!UICONTROL Cloud Manager] | Description |
| --- | --- |
| Propriétaire de l’entreprise | Est responsable de la définition des KPI, approuve les déploiements en production et contourne les échecs à 3 niveaux si nécessaire. |
| Responsable de programme | Cette personne utilise [!UICONTROL Cloud Manager] pour effectuer la configuration de l’équipe, réviser le statut, afficher les KPI et approuver les échecs importants à 3 niveaux si nécessaire. |
| Responsable de déploiement | Gère les opérations de déploiement et utilise [!UICONTROL Cloud Manager] pour exécuter les déploiements d’évaluation et de production, modifier les pipelines CI/CD et approuver les échecs importants à 3 niveaux si nécessaire. Cette personne a également accès au référentiel Git. |
| Développeur ou développeuse | Cette personne développe et teste des codes d’application personnalisés et utilise principalement [!UICONTROL Cloud Manager] pour afficher le statut du déploiement. Elle peut accéder au référentiel Git pour les validations de code. |
| Équipe d’ingénierie du service client | Cette personne prend en charge généralement le service client pour les clientes et clients AMS. Elle interagit avec [!UICONTROL Cloud Manager] dans le but d’exécuter des déploiements nécessitant la supervision de l’équipe d’ingénierie du service client. |
| Créateur ou créatrice de contenu | Cette personne n’interagit généralement pas avec [!UICONTROL Cloud Manager] mais peut utiliser le sélecteur de programmes de [!UICONTROL Cloud Manager] pour accéder à AEM. |

>[!NOTE]
>
>Dans Admin Console, la personne désignée pour le développement n’a aucun rapport avec le rôle de développement dans [!UICONTROL Cloud Manager].

## Créer un profil à l’aide d’Admin Console {#using-admin-console-to-create-a-profile}

Les rôles de [!UICONTROL Cloud Manager] sont gérés depuis Admin Console. Des rôles spécifiques sont attribués en ajoutant un utilisateur à un profil de produit [!UICONTROL Cloud Manager].

Admin Console fournit un emplacement centralisé pour gérer les droits Adobe dans l’ensemble de votre organisation. Pour en savoir plus sur Adobe Admin Console, consultez [Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html).

Un administrateur ou une administratrice doit créer des profils de produit sous le contexte du produit [!UICONTROL AEM Managed Services] pour attribuer des autorisations basées sur les rôles aux utilisateurs et utilisatrices de [!UICONTROL Cloud Manager], correspondant à chacun des quatre rôles [!UICONTROL Cloud Manager].

* Propriétaire de l’entreprise
* Responsable de déploiement
* Développeur ou développeuse
* Responsable de programme

Vous pouvez créer ou ajouter des utilisateurs, des utilisatrices ou des groupes à ces profils de produit avec Admin Console.

1. Connectez-vous à Admin Console à l’adresse [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

1. Cliquez sur l’onglet **Vue d’ensemble**, puis sur le produit à modifier dans la vignette **Produits et services**. S’il n’y est pas répertorié, cherchez le produit dans l’onglet **Produits** et cliquez dessus.

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
   | Développeur ou développeuse | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle de développeur |
   | Responsable de programme | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle de responsable de programme |


1. Cliquez sur **Terminé** pour enregistrer le nouveau profil.

## Affecter des profils à des utilisateurs et utilisatrices ou à des groupes d’utilisateurs et utilisatrices {#assign-profiles}

Une fois que vous avez créé des profils de produit, vous pouvez leur affecter des utilisateurs et utilisatrices ou des groupes d’utilisateurs et utilisatrices.

1. Connectez-vous à Admin Console à l’adresse [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

1. Dans Admin Console, choisissez l’onglet **Utilisateurs**.

   ![Onglet Utilisateurs](/help/assets/admin-console-users.png)

1. Cliquez sur **Utilisateurs et utilisatrices** dans le panneau de navigation de gauche, puis cliquez sur le nom d’une personne pour effectuer des modifications.

1. Cliquez sur ![icône Plus, points de suspension](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) dans la section **Produits** et cliquez sur **Modifier**.

   ![Modification de l’utilisateur ou de l’utilisatrice](/help/assets/admin-console-edit-user.png)

1. Dans la boîte de dialogue **Modifier des produits et des groupes d’utilisateurs**, cliquez sur ![Ajouter une icône, puis sur un signe plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) et sélectionnez les profils à affecter à l’utilisateur.

   * Si l’utilisateur est déjà affecté aux rôles, le bouton ![Ajouter, plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) est un bouton de modification (un crayon), mais fonctionne de la même manière.

   ![Modifier des produits et des groupes d’utilisateurs](/help/assets/admin-console-edit-products-and-user-groups.png)

1. Cliquez sur **Enregistrer** pour enregistrer les profils de l’utilisateur.

Répétez les mêmes étapes pour affecter des profils à des groupes d’utilisateurs, mais sélectionnez **Groupes d’utilisateurs** dans le panneau de navigation de gauche dans l’onglet **Utilisateurs**. Cliquez sur un groupe d’utilisateurs et sélectionnez le **Profils de produit attribués** puis cliquez sur **Attribuer un profil de produit** pour affecter des profils.

![Affectation de profils à un groupe](/help/assets/admin-console-edit-user-groups.png)
