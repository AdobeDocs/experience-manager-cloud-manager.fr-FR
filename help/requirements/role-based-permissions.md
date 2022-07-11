---
title: Autorisations basées sur les rôles
description: Découvrez les autorisations préconfigurées basées sur les rôles de Cloud Manager pour gérer l’accès à vos ressources cloud.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 522e5fbc650a8159602eb1aeaf42d64f4e23e8b4
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 32%

---


# Autorisations basées sur les rôles {#role-based-permissions}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe du code et dispose de l’autorisation de transférer le code vers le référentiel git. Un propriétaire d’entreprise dispose d’autorisations différentes lui permettant de définir les indicateurs de performances clés (IPC) et d’approuver les déploiements.

## Rôles utilisateur {#user-roles}

Gestion des rôles pour [!UICONTROL Cloud Manager] est effectué à l’aide de la fonction [Admin Console.](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) Tout utilisateur de [!UICONTROL Cloud Manager] doit être membre de l’organisation IMS du client et avoir le contexte du produit Adobe Managed Services. Des rôles spécifiques sont fournis en ajoutant un utilisateur à un [!UICONTROL Cloud Manager] profil de produit dans le Admin Console.

Pour en savoir plus sur la configuration de vos rôles, consultez le document [Configuration des utilisateurs et des rôles.](/help/requirements/users-and-roles.md)

Ce tableau répertorie les rôles que vous pouvez affecter dans le Admin Console.

| **Rôle dans** [!UICONTROL Cloud Manager] | Description |
|---|---|
| Propriétaire de l’entreprise | Il s’agit de l’utilisateur Principal qui effectue la première [!UICONTROL Cloud Manager] est chargé de définir les indicateurs de performance clés, d’approuver les déploiements en production et de remplacer les échecs de trois niveaux importants si nécessaire. |
| Responsable de programme | Cet utilisateur utilise [!UICONTROL Cloud Manager] pour effectuer la configuration de l’équipe, vérifier l’état, afficher les indicateurs de performance clés et approuver des échecs de trois niveaux importants si nécessaire. |
| Responsable de déploiement | Cet utilisateur gère les opérations de déploiement à l’aide de [!UICONTROL Cloud Manager] pour exécuter des déploiements dans les environnements intermédiaires et de production, peut approuver des échecs importants à trois niveaux lorsque cela est nécessaire et a accès au référentiel git. |
| Développeur | Cet utilisateur développe et teste du code d’application personnalisé, principalement utilise [!UICONTROL Cloud Manager] pour afficher l’état du déploiement et disposer d’un accès en validation au référentiel git. |
| Ingénieur du service client | Cet utilisateur prend généralement en charge le succès client pour les clients AMS et interagit avec [!UICONTROL Cloud Manager] dans le but d’exécuter des déploiements nécessitant la supervision de l’ingénieur du service client. |
| Auteur de contenu | Cet utilisateur n’interagit généralement pas avec [!UICONTROL Cloud Manager], mais peut utiliser la variable [!UICONTROL Cloud Manager] programme wwitcher (ayant navigué depuis [!UICONTROL Experience Cloud]) pour accéder à Adobe Experience Manager (AEM). |

## Autorisations d’utilisateur {#user-permissions}

Chacun des rôles est associé à des autorisations préconfigurées spécifiques. Ce tableau répertorie les autorisations disponibles et les rôles pouvant les exécuter.


| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur | Ingénieur du service client |
|--- |--- |--- |--- |--- |--- |--- |
| Lecture de l’application | Lecture des indicateurs clés de performance du programme | x | x | x | x | x |
| Écriture de l’application | Configuration ou modification du programme | x |  |  |  |  |
| Ajout d’un programme | Ajouter un nouveau programme | x |  |  |  |  |
| Lecture de l’environnement | Voir les détails de l’environnement | x | x | x | x | x |
| Création de l’exécution | Démarrage du pipeline | x | x | x |  |  |
| Lecture de l’exécution | Voir le statut de l’exécution | x | x | x | x | x |
| Relancer l’exécution | Relance l’exécution lorsqu’elle est en pause | x | x | x |  | x |
| Approbation de l’exécution du déploiement en production | Approbation de la mise en ligne | x | x | x |  |  |
| Planning d’exécution du déploiement en production | Planification du déploiement en production | x | x | x |  | x |
| Exécution du déploiement en production | Déploiement de l’application en production en pause pour la supervision par l’ingénieur du service client |  |  |  |  | x |
| Annuler l’exécution | Annuler l’exécution actuelle |  |  | x |  |  |
| Contourner les échecs du point de contrôle de qualité | Approuver les échecs importants du point de contrôle qualité | x | x | x |  |  |
| Création d’un pipeline | Configuration/modification du pipeline |  | x |  |  |  |
| Lecture d’un pipeline | Voir les détails du pipeline | x | x | x | x | x |
| Écriture d’un pipeline | Configurez/modifiez le pipeline. |  | x |  |  |  |
| Approbation de la modification d’un pipeline | Permet la modification de l’option Propriétaire de l’entreprise |  | x |  |  |  |
| Déploiement géré par la modification du pipeline | Permet la modification de l’option de supervision de l’ingénieur du service client. |  | x |  |  |  |
| Suppression de pipeline | Autorise la suppression du pipeline |  | x |  |  |  |
| Lecture de l’étape | Voir les résultats des mesures de qualité de l’étape | x | x | x | x | x |
| Génération d’un jeton d’accès personnel | Accès à git |  | x |  | x |  |

Pour en savoir plus sur la configuration de vos utilisateurs, consultez le document . [Configuration des utilisateurs et des rôles.](/help/requirements/users-and-roles.md)
