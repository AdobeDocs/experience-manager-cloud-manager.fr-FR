---
title: Ajouter des utilisateurs et des rôles
description: Découvrez comment utiliser Admin Console pour ajouter des utilisateurs et des rôles ainsi que créer des profils.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: ht
source-wordcount: '581'
ht-degree: 100%

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

>[!NOTE]
>
>Pour accéder à Admin Console et configurer votre équipe (utilisateurs et rôles), visitez [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

Afin d’accorder les autorisations appropriées basées sur les rôles aux utilisateurs de [!UICONTROL Cloud Manager], un administrateur de l’organisation du client doit créer des profils de produit sous le contexte du produit [!UICONTROL AEM Managed Services], chacun correspondant à l’un des quatre rôles de [!UICONTROL Cloud Manager] :

* Propriétaire de l’entreprise
* Responsable de déploiement
* Développeur
* Responsable de programme

Vous pouvez créer ou ajouter des utilisateurs/groupes à ces profils de produit avec Admin Console.

1. Connectez-vous à Admin Console et cliquez sur **Nouveau profil** pour ajouter un nouveau profil.

   ![Nouveau profil](/help/assets/admin_console_roles-1.png)

1. Fournissez les informations requises afin de configurer un nouveau rôle pour [!UICONTROL Cloud Manager].

   * **Nom du profil**
   * **Nom d’affichage**
   * **Groupe d’autorisations**

1. Cliquez sur **Terminé** pour terminer l’étape de création du profil.

Lors de la création de ces profils de produit, le **nom d’affichage** doit correspondre à la valeur technique définie par [!UICONTROL Cloud Manager] (voir le tableau ci-dessous). Vous pouvez entrer le **nom de profil** que vous souhaitez. Toutefois, afin d’éviter toute confusion, il est recommandé d’utiliser les valeurs de la colonne **Nom de profil recommandé**. Pour ce faire, lors de la création du profil du produit, désélectionnez **Identique au nom de profil** et spécifiez la valeur correspondante comme **Nom d’affichage**.

| **Rôle** | **Nom d’affichage (obligatoire)** | **Nom de profil recommandé** |
|---|---|---|
| Propriétaire de l’entreprise | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle du propriétaire de l’entreprise |
| Responsable de déploiement | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle de responsable de déploiement |
| Développeur | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle de développeur |
| Responsable de programme | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle de responsable de programme |

![Créer un profil](/help/assets/screen_shot_2018-05-04at171819.png)

Une fois que vous avez créé le profil du produit, vous pouvez ajouter des utilisateurs (ou des groupes) à celui-ci.

![Modifier un utilisateur](/help/assets/image2018-4-9_15-19-26.png)

![Groupes d’utilisateurs](/help/assets/image2018-4-9_15-16-47.png)
