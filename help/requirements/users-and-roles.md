---
title: Ajout d’utilisateurs et de rôles
description: Découvrez comment utiliser le Admin Console pour ajouter des utilisateurs et des rôles et créer des profils.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 30%

---


# Ajout d’utilisateurs et de rôles {#add-users-and-roles}

De nombreuses fonctionnalités [!UICONTROL Cloud Manager] nécessitent des autorisations spécifiques à utiliser. Par exemple, seuls certains utilisateurs sont autorisés à définir les indicateurs de performance clés (IPC) d’un programme. Ces autorisations sont regroupées de manière logique en rôles.

[!UICONTROL Cloud Manager] définit actuellement quatre rôles pour les utilisateurs qui régissent la disponibilité de fonctionnalités spécifiques :

* Propriétaire de l’entreprise
* Responsable de programme
* Responsable de déploiement
* Développeur

>[!NOTE]
>
>Pour utiliser [!UICONTROL Cloud Manager], vous devez disposer d’un Adobe ID et du contexte du produit Adobe Managed Services.

## Définitions de rôle {#role-definitions}

Ce tableau résume les rôles.

| **Rôle dans** [!UICONTROL Cloud Manager] | Description |
|--- |--- |
| Propriétaire de l’entreprise | Cet utilisateur est chargé de définir les indicateurs de performance clés, d’approuver les déploiements en production et de surcharger les échecs de trois niveaux importants si nécessaire. |
| Responsable de programme | Cet utilisateur utilise [!UICONTROL Cloud Manager] pour effectuer la configuration de l’équipe, vérifier l’état, afficher les indicateurs de performance clés et approuver des échecs de trois niveaux importants si nécessaire. |
| Responsable de déploiement | Cet utilisateur gère les opérations de déploiement et utilise [!UICONTROL Cloud Manager] pour exécuter des déploiements d’évaluation/de production, modifiez les pipelines CI/CD, approuvez des échecs à trois niveaux importants si nécessaire et pouvez accéder au référentiel git. |
| Développeur | Cet utilisateur développe et teste du code d’application personnalisé et utilise principalement [!UICONTROL Cloud Manager] pour afficher l’état du déploiement et accéder au référentiel git pour les validations de code. |
| Ingénieur du service client | Cet utilisateur prend généralement en charge le succès client pour les clients AMS et interagit avec [!UICONTROL Cloud Manager] dans le but d’exécuter des déploiements nécessitant la supervision de l’ingénieur du service client. |
| Auteur de contenu | Cet utilisateur n’interagit généralement pas avec [!UICONTROL Cloud Manager] mais peut utiliser la variable [!UICONTROL Cloud Manager] sélecteur de programme pour accéder à AEM. |

>[!NOTE]
>
>Le développeur dans le Admin Console n’est pas lié au rôle Développeur dans [!UICONTROL Cloud Manager].

## Utilisation d’Admin Console pour créer un profil {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] Les rôles sont gérés à partir du Admin Console. Des rôles spécifiques sont fournis en ajoutant un utilisateur à un [!UICONTROL Cloud Manager] profil de produit.

Le Admin Console est un emplacement central pour la gestion de vos droits d’Adobe dans l’ensemble de votre organisation. Pour en savoir plus sur Adobe Admin Console, consultez la documentation d’[Admin Console.](https://helpx.adobe.com/fr/enterprise/using/admin-console.html)

>[!NOTE]
>
>Pour accéder à Admin Console et configurer votre équipe (utilisateurs et rôles), rendez-vous sur la page [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

Afin de fournir les autorisations appropriées basées sur les rôles à [!UICONTROL Cloud Manager] utilisateurs, un administrateur de l’entreprise du client doit créer de nouveaux profils de produit sous le [!UICONTROL Managed Services AEM] contexte du produit correspondant à chacun des quatre [!UICONTROL Cloud Manager] rôles :

* Propriétaire de l’entreprise
* Responsable de déploiement
* Développeur
* Responsable de programme

Vous pouvez créer ou ajouter des utilisateurs/groupes à ces profils de produit avec le Admin Console .

1. Connectez-vous au Admin Console et cliquez sur **Nouveau profil** pour ajouter un nouveau profil.

   ![Nouveau profil](/help/assets/admin_console_roles-1.png)

1. Fournissez les informations nécessaires pour configurer un nouveau rôle pour [!UICONTROL Cloud Manager].

   * **Nom du profil**
   * **Nom d’affichage**
   * **Groupe d’autorisations**

1. Cliquez sur **Terminé** pour terminer l’étape de création du profil.

Lors de la création de profils de produit, la variable **Nom d’affichage** doit être la valeur technique définie par [!UICONTROL Cloud Manager] (voir le tableau suivant). Le **Nom du profil** peut être n’importe quoi, mais pour éviter toute confusion, il est recommandé d’utiliser les valeurs de la variable **Nom de profil recommandé** colonne . Pour ce faire, lors de la création du profil du produit, désélectionnez **Identique au nom de profil** et spécifiez la valeur correspondante comme **Nom d’affichage**.

| **Rôle** | **Nom d’affichage (obligatoire)** | **Nom de profil recommandé** |
|---|---|---|
| Propriétaire de l’entreprise | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle du propriétaire de l’entreprise |
| Responsable de déploiement | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle de responsable de déploiement |
| Développeur | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle de développeur |
| Responsable de programme | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] : rôle de responsable de programme |

![Créer un nouveau profil](/help/assets/screen_shot_2018-05-04at171819.png)

Une fois que vous avez créé un profil de produit, vous pouvez ajouter des utilisateurs (ou groupes) à ces profils de produit.

![Modification d’un utilisateur](/help/assets/image2018-4-9_15-19-26.png)

![Groupes d’utilisateurs](/help/assets/image2018-4-9_15-16-47.png)
