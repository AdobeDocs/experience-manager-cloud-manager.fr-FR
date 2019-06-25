---
title: Sécurité et confidentialité
seo-title: Sécurité et confidentialité pour AEM Cloud Manager
description: Consultez cette page pour en savoir plus sur la sécurité et la confidentialité de vos ressources (code/artefacts).
seo-description: Consultez cette page pour en savoir plus sur la sécurité et la confidentialité de vos ressources (code/artefacts) grâce à AEM Cloud Manager.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: ht
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Sécurité et confidentialité {#security-and-privacy}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe du code et a l’autorisation de placer le code dans le **référentiel Git**. Un propriétaire d’entreprise dispose d’autorisations différentes qui lui permettent de définir des indicateurs de performance clés et d’approuver les déploiements.

## Autorisations basées sur les rôles {#role-based-permissions}

### Rôles d’utilisateur {#user-roles}

La gestion des rôles de [!UICONTROL Cloud Manager] est effectuée dans [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html). Tout utilisateur de [!UICONTROL Cloud Manager] doit être membre de l’organisation IMS du client et avoir le contexte du produit Adobe Managed Services. Des rôles spécifiques sont fournis en ajoutant un utilisateur à un profil de produit [!UICONTROL Cloud Manager] dans Admin Console.

Pour plus d’informations sur la configuration de vos rôles, consultez la rubrique [Configuration des utilisateurs et des rôles](setting-up-users-and-roles.md).

La liste suivante définit les rôles que vous pouvez attribuer dans Admin Console.

| Rôle **dans**[!UICONTROL Cloud Manager] | **Description** |
|---|---|
| Propriétaire de l’entreprise | Utilisateur principal qui effectue la configuration initiale de [!UICONTROL Cloud Manager]. Est responsable de la définition des ICP, approuve les déploiements en production et contourne les échecs de trois niveaux. |
| Responsable de programme | Utilise [!UICONTROL Cloud Manager] pour configurer les équipes et passer en revue les statuts et les IPC. Peut approuver des échecs importants de trois niveaux. |
| Responsable de déploiement | Gère les opérations de déploiement. Utilise [!UICONTROL Cloud Manager] pour exécuter les déploiements dans les environnements intermédiaires/de production. Peut approuver des échecs importants de trois niveaux. Dispose d’un accès au référentiel Git. |
| Développeur | Développe et teste du code d’application personnalisé. Utilise principalement [!UICONTROL Cloud Manager] pour consulter les statuts. Dispose d’un accès en validation au référentiel Git. |
| Ingénieur du service client | Prend en charge généralement les stratégies du service client pour les clients AMS. Interagit avec [!UICONTROL Cloud Manager] dans le but d’exécuter des déploiements nécessitant la supervision de l’ingénieur du service client. |
| Auteur de contenu | N’interagit généralement pas avec [!UICONTROL Cloud Manager]. Cet utilisateur peut utiliser le commutateur de programmes de [!UICONTROL Cloud Manager](depuis [!UICONTROL Experience Cloud]) pour accéder à Adobe Experience Manager (AEM). |

### Autorisations d’utilisateur {#user-permissions}

Chacun des rôles dispose d’autorisations spécifiques, de tâches préconfigurées, ou de permissions, inhérentes à chaque rôle. Ce tableau récapitule les fonctions disponibles et les rôles associés à chaque fonction.

Pour en savoir plus sur le configuration de vos utilisateurs, consultez [Configuration des rôles et des utilisateurs](setting-up-users-and-roles.md).

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur | Ingénieur du service client |
|--- |--- |--- |--- |--- |--- |--- |
| Lecture de l’application | Voir les détails du programme. | x | x | x | x | x |
| Écriture de l’application | Configuration du programme (y compris des ICP). | x |  |  |  |  |
| Lecture de l’environnement | Voir les détails de l’environnement. | x | x | x | x | x |
| Création de l’exécution | Démarrage du pipeline. | x | x | x |  |  |
| Lecture de l’exécution | Voir le statut de l’exécution. | x | x | x | x | x |
| Relancer l’exécution | Relance l’exécution lorsqu’elle est en pause. | x | x | x |  | x |
| Approbation de l’exécution du déploiement en production | Fournit l’approbation de GoLive. | x | x | x |  |  |
| Planning d’exécution du déploiement en production | Planning du déploiement en production. | x | x | x |  | x |
| Exécution du déploiement en production | Déploie l’application en production lorsqu’elle est mise en pause dans le cadre de la supervision de l’ingénieur du service client. |  |  |  |  | x |
| Annuler l’exécution | Annuler l’exécution actuelle. | x | x | x |  |  |
| Contourner les échecs du point de contrôle de qualité | Approuver des échecs importants du point de contrôle qualité. | x | x | x |  |  |
| Création d’un pipeline | Configurer/modifier un pipeline. |  | x |  |  |  |
| Lecture d’un pipeline | Voir les détails du pipeline. | x | x | x | x | x |
| Écriture d’un pipeline | Configurer/modifier un pipeline. |  | x |  |  |  |
| Approbation de la modification d’un pipeline | Permet la modification de l’option Propriétaire de l’entreprise. |  | x |  |  |  |
| Déploiement géré par la modification du pipeline | Permet la modification de l’option Supervision par l’ingénieur du service client. |  | x |  |  |  |
| Lecture de solution | Lire les ICP du programme | x | x | x | x | x |
| Écriture de solution | Configurer le programme (ICP compris)/Modifier le pipeline | x |  |  |  |  |
| Lecture de l’étape | Voir les résultats des mesures de qualité de l’étape. | x | x | x | x | x |

## Isolation de ressource {#resource-isolation}

Les clients qui utilisent [!UICONTROL Cloud Manager] auront besoin de leurs informations d’identification IMS pour s’authentifier, car toute autorisation liée à [!UICONTROL Cloud Manager] sera configurée et liée à leur organisation IMS. Pendant le processus d’intégration, l’équipe chargée de la configuration s’assure que l’isolation de ressource est mise en place dans [!UICONTROL Cloud Manager].

## Sécurité des données {#data-security}

Le code dans [!UICONTROL Cloud Manager] est chiffré en transit. Les binaires créées par Cloud Manager sont également chiffrées en transit et chiffrées lors de leur stockage.

Chaque client obtient son propre **référentiel Git**. Le code est sécurisé et n’est partagé avec aucune autre **organisation**.

## Confidentialité des données {#data-privacy}

[!UICONTROL Cloud Manager] adhère aux principes de confidentialité définis par Adobe. Les développeurs affectent le code en toute sécurité dans le **référentiel Git** sur HTTPS.

L’[interface utilisateur (IU) !DNL de [!UICONTROL Cloud Manager]] est créée sur des services conformes à une structure de contrôle courante qui est définie par Adobe. L’[interface utilisateur (IU) !DNL de [!UICONTROL Cloud Manager]] utilise des services sécurisés de plusieurs fournisseurs cloud.
