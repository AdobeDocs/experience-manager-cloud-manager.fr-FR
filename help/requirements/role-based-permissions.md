---
title: Autorisations basées sur les rôles
description: Découvrez les autorisations préconfigurées basées sur les rôles de Cloud Manager pour gérer l’accès à vos ressources cloud.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 99%

---


# Autorisations basées sur les rôles {#role-based-permissions}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe du code et a l’autorisation de placer le code dans le référentiel Git. Une personne propriétaire d’entreprise dispose de différents autorisations lui permettant de définir des indicateurs de performance clés (KPI) et d’approuver les déploiements.

>[!NOTE]
>
>Cette documentation décrit les autorisations basées sur les rôles de Cloud Manager pour Adobe Managed Services (AMS).
>
>Retrouvez la documentation équivalente pour AEM as a Cloud Service dans la [Présentation de Cloud Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions) de la documentation AEM as a Cloud Service.

## Rôles d’utilisateur ou d’utilisatrice {#user-roles}

La gestion des rôles pour [!UICONTROL Cloud Manager] s’effectue dans [Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html). Toute personne utilisant [!UICONTROL Cloud Manager] doit être membre de l’organisation IMS du client ou de la cliente et avoir le contexte du produit Adobe Managed Services. Des rôles spécifiques sont fournis en ajoutant un utilisateur ou une utilisatrice à un profil de produit [!UICONTROL Cloud Manager] dans Admin Console.

Pour plus d’informations sur la configuration de vos rôles, consultez la rubrique [Configuration des utilisateurs et utilisatrices et des rôles](/help/requirements/users-and-roles.md).

Ce tableau répertorie les rôles que vous pouvez affecter dans Admin Console.

| Rôle dans [!UICONTROL Cloud Manager] | Description |
|---|---|
| Propriétaire de l’entreprise | La personne principale effectue la configuration de [!UICONTROL Cloud Manager] initiale et est chargée de définir les KPI, d’approuver les déploiements en production et de remplacer les échecs à 3 niveaux importants si nécessaire. |
| Créateur ou créatrice de contenu | Cette personne n’interagit généralement pas avec Cloud Manager, mais peut utiliser le sélecteur de programme Cloud Manager (à partir d’Experience Cloud) pour accéder à Adobe Experience Manager (AEM). |
| Équipe d’ingénierie du service client | La personne prend principalement en charge le service client AMS et engage avec [!UICONTROL Cloud Manager] pour exécuter les déploiements. Ces déploiements nécessitent la supervision de l’équipe d’ingénierie du service client (CSE) Adobe. |
| Responsable de déploiement | Cette personne gère les opérations de déploiement à l’aide de [!UICONTROL Cloud Manager] pour exécuter des déploiements d’évaluation et de production, peut approuver des échecs à 3 niveaux importants si nécessaire, et a accès au référentiel Git. |
| Développeur ou développeuse | Cette personne développe et teste des codes d’application personnalisés, utilise principalement [!UICONTROL Cloud Manager] pour afficher le statut du déploiement et dispose d’un accès en validation au référentiel Git. |
| Responsable de programme | Cette personne utilise [!UICONTROL Cloud Manager] pour effectuer la configuration de l’équipe, réviser le statut, afficher les KPI et approuver les échecs à 3 niveaux importants si nécessaire. |

## Autorisations d’utilisateur ou d’utilisatrice {#user-permissions}

Chacun des rôles est associé à des autorisations préconfigurées spécifiques. Ce tableau récapitule les autorisations disponibles et les rôles qui peuvent les exécuter.

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur ou développeuse | Ingénieur du service client |
| --- | --- | --- | --- | --- | --- | --- |
| `Read the Application` | Lire les KPI du programme | x | x | x | x | x |
| `Write Application` | Configuration ou modification du programme | x | | | | |
| `Add Program` | Ajouter un nouveau programme | x |  |  |  |  |
| `Read Environment` | Voir les détails de l’environnement | x | x | x | x | x |
| `Create Execution` | Démarrer le pipeline | x | x | x | | |
| `Read Execution` | Voir le statut de l’exécution | x | x | x | x | x |
| `Resume Execution` | Possibilité de reprendre l’exécution en pause | x | x | x | | x |
| `Execution Approve Deploy to Production` | Fournir une approbation de mise en production | x | x | x | | |
| `Execution Schedule Deploy to Production` | Planifier le déploiement en production | x | x | x | | x |
| `Execution Deploy to Production` | Déployer l’application en production lorsqu’elle est mise en pause dans le cadre de la supervision de l’ingénieur du succès client (CSE). |  |  |  |  | x |
| `Execution Cancel` | Annuler l’exécution actuelle |  |  | x |  |  |
| `Execution Override Quality Gate Failures` | Approuver des échecs importants du point de contrôle Qualité | x | x | x |  |  |
| `Pipeline Create` | Configurer/modifier un pipeline |  | x |  |  |  |
| `Pipeline Read` | Voir les détails du pipeline | x | x | x | x | x |
| `Pipeline Write` | Configurer/modifier un pipeline |  | x |  |  |  |
| P`ipeline Modify Approval` | Permet de modifier l’option Propriétaire de l’entreprise |  | x |  |  |  |
| `Pipeline Modify Managed Deployment` | Permet de modifier l’option Supervision de l’ingénieur du succès client (CSE) |  | x |  |  |  |
| `Pipeline Delete` | Autorise la suppression du pipeline |  | x |  |  |  |
| `Step Read` | Voir les résultats des mesures de qualité de l’étape | x | x | x | x | x |
| `Generate Personal Access Token` | Accéder à Git |  | x |  | x |  |

<!-- CQDOC-22080 | Download log files  |  |  | x |  | x |  | -->

Pour en savoir plus sur la configuration de vos utilisateurs et utilisatrices, voir [Configuration des rôles et des utilisateurs et utilisatrices](/help/requirements/users-and-roles.md).

>[!TIP]
>
>Des profils d’autorisation personnalisés avec des autorisations configurables sont également disponibles. Pour plus d’informations, voir la section [Autorisations personnalisées](/help/using/custom-permissions.md).
