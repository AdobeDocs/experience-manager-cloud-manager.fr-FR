---
title: Autorisations basées sur les rôles
description: Découvrez les autorisations préconfigurées basées sur les rôles de Cloud Manager pour gérer l’accès à vos ressources cloud.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 54%

---


# Autorisations basées sur les rôles {#role-based-permissions}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe du code et a l’autorisation de placer le code dans le référentiel Git. Un propriétaire d’entreprise dispose de différents autorisations lui permettant de définir des indicateurs de performance clés (KPI) et d’approuver les déploiements.

>[!NOTE]
>
>Cette documentation décrit les autorisations basées sur les rôles de Cloud Manager pour Adobe Managed Services (AMS).
>
>Retrouvez la documentation équivalente pour AEM as a Cloud Service dans la [Présentation de Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions) de la documentation AEM as a Cloud Service.

## Rôles utilisateur {#user-roles}

La gestion des rôles pour [!UICONTROL Cloud Manager] est effectuée à l’aide de [Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html). Tout utilisateur de [!UICONTROL Cloud Manager] doit être membre de l’organisation IMS du client et avoir le contexte du produit Managed Services Adobe. Des rôles spécifiques sont fournis en ajoutant un utilisateur à un profil de produit [!UICONTROL Cloud Manager] dans Admin Console.

Pour en savoir plus sur la configuration de vos rôles, voir [Configuration des utilisateurs et des rôles](/help/requirements/users-and-roles.md).

Le tableau suivant répertorie les rôles que vous pouvez affecter dans l’Admin Console.

| Rôle [!UICONTROL Cloud Manager] | Description |
|---|---|
| Propriétaire de l’entreprise | L’utilisateur principal qui effectue la configuration initiale de [!UICONTROL Cloud Manager] et est chargé de définir les indicateurs de performance clés, d’approuver les déploiements de production et de remplacer les échecs à trois niveaux importants si nécessaire. |
| Auteur ou autrice de contenu | L’utilisateur n’interagit généralement pas avec Cloud Manager, mais il peut utiliser le sélecteur de programme Cloud Manager (depuis Experience Cloud) pour accéder à Adobe Experience Manager (AEM). |
| Ingénieur du succès client | L’utilisateur prend principalement en charge le succès client AMS et engage [!UICONTROL Cloud Manager] pour exécuter les déploiements. Ces déploiements nécessitent la supervision d’un ingénieur du service client Adobe. |
| Responsable de déploiement | L’utilisateur gère les opérations de déploiement à l’aide de [!UICONTROL Cloud Manager] pour exécuter les déploiements dans les environnements intermédiaires et de production, peut approuver des échecs importants à trois niveaux si nécessaire et a accès au référentiel Git. |
| Développeur ou développeuse | L’utilisateur développe et teste du code d’application personnalisé, utilise principalement [!UICONTROL Cloud Manager] pour afficher l’état de déploiement et dispose d’un accès en validation au référentiel Git. |
| Responsable de programme | L’utilisateur utilise [!UICONTROL Cloud Manager] pour effectuer la configuration de l’équipe, passer en revue l’état, afficher les indicateurs de performance clés et peut approuver des échecs de trois niveaux importants si nécessaire. |

## Autorisations d’utilisateur {#user-permissions}

Chacun des rôles possède des autorisations préconfigurées spécifiques. Le tableau suivant répertorie les autorisations disponibles et les rôles pouvant les exécuter.

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur | Ingénieur du service client |
| --- | --- | --- | --- | --- | --- | --- |
| Lecture de l’application | Lire les KPI du programme | x | x | x | x | x |
| Écriture de l’application | Configuration ou modification du programme | x | | | | |
| Ajout d’un programme | Ajouter un nouveau programme | x | | | | |
| Lecture de l’environnement | Voir les détails de l’environnement | x | x | x | x | x |
| Création de l’exécution | Démarrer le pipeline | x | x | x | | |
| Lecture de l’exécution | Voir le statut de l’exécution | x | x | x | x | x |
| Relancer l’exécution | Possibilité de reprendre l’exécution en pause | x | x | x | | x |
| Approbation de l’exécution du déploiement en production | Fournir une approbation de mise en production | x | x | x | | |
| Planning d’exécution du déploiement en production | Planifier le déploiement en production | x | x | x | | x |
| Exécution du déploiement en production | Déployer l’application en production lorsqu’elle est mise en pause dans le cadre de la supervision de l’ingénieur du succès client (CSE). | | | | | x |
| Annuler l’exécution | Annuler l’exécution actuelle | | | x | | |
| Contourner les échecs du point de contrôle de qualité | Approuver des échecs importants du point de contrôle Qualité | x | x | x | | |
| Création d’un pipeline | Configurer/modifier un pipeline | | x | | | |
| Lecture d’un pipeline | Voir les détails du pipeline | x | x | x | x | x |
| Écriture d’un pipeline | Configurer/modifier un pipeline | | x | | | |
| Approbation de la modification d’un pipeline | Permet de modifier l’option Propriétaire de l’entreprise | | x | | | |
| Déploiement géré par la modification du pipeline | Permet de modifier l’option Supervision de l’ingénieur du succès client (CSE) | | x | | | |
| Suppression de pipeline | Autorise la suppression du pipeline | | x | | | |
| Lecture de l’étape | Voir les résultats des mesures de qualité de l’étape | x | x | x | x | x |
| Génération d’un jeton d’accès personnel | Accéder à Git | | x | | x | |

Pour en savoir plus sur la configuration de vos utilisateurs, voir [Configuration des utilisateurs et des rôles](/help/requirements/users-and-roles.md).

>[!TIP]
>
>Des profils d’autorisation personnalisés avec des autorisations configurables sont également disponibles. Pour plus d’informations, voir [Autorisations personnalisées](/help/using/custom-permissions.md) .
