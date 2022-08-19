---
title: Autorisations basées sur les rôles
description: Découvrez les autorisations préconfigurées basées sur les rôles de Cloud Manager pour gérer l’accès à vos ressources cloud.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 522e5fbc650a8159602eb1aeaf42d64f4e23e8b4
workflow-type: ht
source-wordcount: '565'
ht-degree: 100%

---


# Autorisations basées sur les rôles {#role-based-permissions}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe des codes et dispose de l’autorisation de placer le code dans le référentiel Git. Un propriétaire d’entreprise dispose de différents autorisations lui permettant de définir des indicateurs de performance clés (KPI) et d’approuver les déploiements.

## Rôles utilisateur {#user-roles}

La gestion des rôles pour [!UICONTROL Cloud Manager] s’effectue dans [Admin Console.](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) Tout utilisateur de [!UICONTROL Cloud Manager] doit être membre de l’organisation IMS du client et avoir le contexte du produit Adobe Managed Services. Des rôles spécifiques sont fournis en ajoutant un utilisateur à un profil de produit [!UICONTROL Cloud Manager] dans Admin Console.

Pour plus d’informations sur la configuration de vos rôles, consultez le document [Configuration des utilisateurs et des rôles.](/help/requirements/users-and-roles.md)

Ce tableau répertorie les rôles que vous pouvez affecter dans Admin Console.

| Rôle dans [!UICONTROL Cloud Manager] | Description |
|---|---|
| Propriétaire de l’entreprise | L’utilisateur principal effectue la configuration de [!UICONTROL Cloud Manager] initiale et est chargé de définir les KPI, d’approuver les déploiements en production et de remplacer les échecs à 3 niveaux importants si nécessaire. |
| Responsable de programme | Cet utilisateur utilise [!UICONTROL Cloud Manager] pour effectuer la configuration de l’équipe, réviser le statut, afficher les KPI et approuver les échecs à 3 niveaux importants si nécessaire. |
| Responsable de déploiement | Cet utilisateur gère les opérations de déploiement à l’aide de [!UICONTROL Cloud Manager] pour exécuter des déploiements d’évaluation et de production, peut approuver des échecs à 3 niveaux importants si nécessaire et a accès au référentiel git. |
| Développeur | Cet utilisateur développe et teste des codes d’application personnalisés, utilise principalement [!UICONTROL Cloud Manager] pour afficher le statut du déploiement et dispose d’un accès en validation au référentiel Git. |
| Ingénieur du succès client | Cet utilisateur prend généralement en charge le succès client pour les clients AMS et interagit avec [!UICONTROL Cloud Manager] dans le but d’exécuter des déploiements nécessitant la supervision de l’ingénieur du succès client (CSE). |
| Créateur de contenu | Cet utilisateur n’interagit généralement pas avec [!UICONTROL Cloud Manager], mais peut utiliser le sélecteur de programme [!UICONTROL Cloud Manager] (ayant navigué depuis [!UICONTROL Experience Cloud]) pour accéder à Adobe Experience Manager (AEM). |

## Autorisations d’utilisateur {#user-permissions}

Chacun des rôles est associé à des autorisations préconfigurées spécifiques. Ce tableau récapitule les autorisations disponibles et les rôles qui peuvent les exécuter.


| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur | Ingénieur du service client |
|--- |--- |--- |--- |--- |--- |--- |
| Lecture de l’application | Lire les KPI du programme | x | x | x | x | x |
| Écriture de l’application | Configuration ou modification du programme | x |  |  |  |  |
| Ajout d’un programme | Ajouter un nouveau programme | x |  |  |  |  |
| Lecture de l’environnement | Voir les détails de l’environnement | x | x | x | x | x |
| Création de l’exécution | Démarrer le pipeline | x | x | x |  |  |
| Lecture de l’exécution | Voir le statut de l’exécution | x | x | x | x | x |
| Relancer l’exécution | Relance l’exécution lorsqu’elle est en pause | x | x | x |  | x |
| Approbation de l’exécution du déploiement en production | Fournir une approbation de mise en production | x | x | x |  |  |
| Planning d’exécution du déploiement en production | Planifier le déploiement en production | x | x | x |  | x |
| Exécution du déploiement en production | Déployer l’application en production lorsqu’elle est mise en pause dans le cadre de la supervision de l’ingénieur du succès client (CSE). |  |  |  |  | x |
| Annuler l’exécution | Annuler l’exécution actuelle |  |  | x |  |  |
| Contourner les échecs du point de contrôle de qualité | Approuver des échecs importants du point de contrôle Qualité | x | x | x |  |  |
| Création d’un pipeline | Configurer/modifier un pipeline |  | x |  |  |  |
| Lecture d’un pipeline | Voir les détails du pipeline | x | x | x | x | x |
| Écriture d’un pipeline | Configurez/modifiez le pipeline. |  | x |  |  |  |
| Approbation de la modification d’un pipeline | Permet de modifier l’option Propriétaire de l’entreprise |  | x |  |  |  |
| Déploiement géré par la modification du pipeline | Permet de modifier l’option Supervision de l’ingénieur du succès client (CSE) |  | x |  |  |  |
| Suppression de pipeline | Autorise la suppression du pipeline |  | x |  |  |  |
| Lecture de l’étape | Voir les résultats des mesures de qualité de l’étape | x | x | x | x | x |
| Génération d’un jeton d’accès personnel | Accéder à Git |  | x |  | x |  |

Pour en savoir plus sur la configuration de vos utilisateurs, voir le document [Configuration des utilisateurs et des rôles.](/help/requirements/users-and-roles.md)
