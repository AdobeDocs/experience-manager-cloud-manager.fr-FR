---
title: Autorisations basées sur les rôles
description: Consultez cette page pour en savoir plus sur les autorisations basées sur les rôles.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: 9cbe8f58cf04001ba9851ba321f03c7687e58014

---


# Autorisations basées sur les rôles {#role-based-permissions}

[!UICONTROL Cloud Manager] a des rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe du code et a l’autorisation de placer le code dans le **référentiel Git**. Un propriétaire d’entreprise dispose d’autorisations différentes qui lui permettent de définir des indicateurs de performance clés et d’approuver les déploiements.

## Rôles utilisateur {#user-roles}

La gestion des rôles pour [!UICONTROL Cloud Manager] s’effectue dans [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html). Tout utilisateur de [!UICONTROL Cloud Manager] doit être membre de l’organisation IMS du client et avoir le contexte du produit Adobe Managed Services. Des rôles spécifiques sont fournis en ajoutant un utilisateur à un profil de produit [!UICONTROL Cloud Manager] dans Admin Console.

Pour plus d’informations sur la configuration de vos rôles, consultez la rubrique [Configuration des utilisateurs et des rôles](setting-up-users-and-roles.md).

La liste suivante définit les rôles que vous pouvez attribuer dans Admin Console.

| **[!UICONTROL Cloud Manager]Rôle ** | **Description** |
|---|---|
| Propriétaire de l’entreprise | Primary user who completes the initial [!UICONTROL Cloud Manager] setup. Est responsable de la définition des ICP, approuve les déploiements en production et contourne les échecs de trois niveaux. |
| Responsable de programme | Utilise [!UICONTROL Cloud Manager] pour configurer les équipes et passer en revue les statuts et les ICP. Peut approuver des échecs importants de trois niveaux. |
| Responsable de déploiement | Gère les opérations de déploiement. Uses [!UICONTROL Cloud Manager] to execute stage and production deployments. Peut approuver des échecs importants de trois niveaux. Dispose d’un accès au référentiel Git. |
| Développeur | Développe et teste du code d’application personnalisé. Primarily uses [!UICONTROL Cloud Manager] to view status. Dispose d’un accès en validation au référentiel Git. |
| Ingénieur du service client | Prend en charge généralement les stratégies du service client pour les clients AMS. Interagit avec [!UICONTROL Cloud Manager] dans le but d’exécuter des déploiements nécessitant la supervision de l’ingénieur du service client. |
| Auteur de contenu | Generally does not interact with [!UICONTROL Cloud Manager]. This user may use the [!UICONTROL Cloud Manager] Program Switcher (having navigated from [!UICONTROL Experience Cloud]) to access Adobe Experience Manager (AEM). |

## Autorisations d’utilisateur {#user-permissions}

Chacun des rôles dispose d’autorisations spécifiques, de tâches préconfigurées, ou de permissions, inhérentes à chaque rôle. Ce tableau récapitule les fonctions disponibles et les rôles associés à chaque fonction.

Pour en savoir plus sur la configuration de vos utilisateurs, voir [Configuration des rôles et des utilisateurs](setting-up-users-and-roles.md).

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur | Ingénieur du service client |
|--- |--- |--- |--- |--- |--- |--- |
| Lecture de l’application | Lecture des indicateurs clés de performance du programme. | x | x | x | x | x |
| Écriture de l’application | Configuration ou modification du programme. | x |  |  |  |  |
| Ajout d’un programme | Ajout d’un nouveau programme. | x |  |  |  |  |
| Lecture de l’environnement | Voir les détails de l’environnement. | x | x | x | x | x |
| Création de l’exécution | Démarrage du pipeline. | x | x | x |  |  |
| Lecture de l’exécution | Voir le statut de l’exécution. | x | x | x | x | x |
| Relancer l’exécution | Relance l’exécution lorsqu’elle est en pause. | x | x | x |  | x |
| Approbation de l’exécution du déploiement en production | Fournit l’approbation de GoLive. | x | x | x |  |  |
| Planning d’exécution du déploiement en production | Planning du déploiement en production. | x | x | x |  | x |
| Exécution du déploiement en production | Déploie l’application en production lorsqu’elle est mise en pause dans le cadre de la supervision de l’ingénieur du service client. |  |  |  |  | x |
| Annuler l’exécution | Annuler l’exécution actuelle. |  |  | x |  |  |
| Contourner les échecs du point de contrôle de qualité | Approuver des échecs importants du point de contrôle qualité. | x | x | x |  |  |
| Création d’un pipeline | Configurer/modifier un pipeline. |  | x |  |  |  |
| Lecture d’un pipeline | Voir les détails du pipeline. | x | x | x | x | x |
| Écriture d’un pipeline | Configurer/modifier un pipeline. |  | x |  |  |  |
| Approbation de la modification d’un pipeline | Permet la modification de l’option Propriétaire de l’entreprise. |  | x |  |  |  |
| Déploiement géré par la modification du pipeline | Permet la modification de l’option Supervision par l’ingénieur du service client. |  | x |  |  |  |
| Suppression du tuyau | Permet de supprimer un tuyau. |  | x |  |  |  |
| Lecture de l’étape | Voir les résultats des mesures de qualité de l’étape. | x | x | x | x | x |
| Génération d’un jeton d’accès personnel | Accéder à Git. |  | x |  | x |  |

