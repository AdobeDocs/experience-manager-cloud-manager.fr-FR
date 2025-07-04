---
title: Autorisations personnalisées
description: Découvrez comment utiliser des autorisations personnalisées pour créer des profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès aux programmes, aux pipelines et aux environnements pour les utilisateurs et utilisatrices de Cloud Manager.
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 98%

---

# Autorisations personnalisées {#custom-permissions}

Découvrez comment utiliser des autorisations personnalisées pour créer des profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès aux programmes, aux pipelines et aux environnements pour les utilisateurs et utilisatrices de Cloud Manager.

## Présentation {#introduction}

Cloud Manager dispose d’un ensemble de rôles prédéfinis qui régissent l’accès aux différentes fonctionnalités de Cloud Manager :

* Propriétaire de l’entreprise
* Responsable de programme
* Responsable de déploiement
* Développeur ou développeuse

Les autorisations personnalisées permettent aux utilisateurs et utilisatrices de créer des profils d’autorisation personnalisés avec des autorisations configurables, afin de restreindre l’accès des utilisateurs et utilisatrices de Cloud Manger aux programmes, aux pipelines et aux environnements.

>[!TIP]
>
>Pour plus d’informations sur les rôles prédéfinis, voir la section [Autorisations basées sur les rôles](/help/requirements/role-based-permissions.md).

## Utiliser les autorisations personnalisées {#using}

La création et l’utilisation de vos autorisations personnalisées nécessitent les trois étapes suivantes :

1. [Créez un profil de produit](#create).
1. [Attribuez des autorisations personnalisées au nouveau profil de produit](#assign-permissions).
1. [Affectez des utilisateurs et utilisatrices au nouveau profil de produit](#assign-users).

Cette section décrit ces étapes en détails. Il peut se révéler utile de consulter les sections [Termes](#terms) et [Autorisations configurables](#configurable-permissions) lors de la création de vos propres autorisations personnalisées.

>[!NOTE]
>
>Vous devez disposer de droits d’administration sur le produit dans Admin Console pour créer des profils et gérer les autorisations de Cloud Manager.

### Créer un profil de produit {#create}

Vous devez d’abord créer un profil de produit auquel vous pourrez attribuer des autorisations personnalisées.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).

1. Sélectionnez le produit **AEM Managed Services**.

1. Recherchez l’instance dont le nom correspond au modèle `*-cloud-manager` et cliquez pour gérer les utilisateurs et utilisatrices et les autorisations.

1. Une redirection vers l’onglet **Produits** d’Admin Console se produit, dans lequel vous pouvez gérer les utilisateurs et utilisatrices et les autorisations de Cloud Manager. Dans Admin Console, cliquez sur **Nouveau profil**.

![Bouton Nouveau profil.](/help/assets/admin-console-new-profile.png)

1. Fournissez les détails généraux du profil.

   * **Nom du profil de produit** : un nom descriptif du profil.
   * **Nom d’affichage** : nom abrégé affiché dans l’interface d’utilisation (options).
   * **Description** : une description informative du profil expliquant son objectif (facultatif).
   * **Avertir les utilisateurs et utilisatrices par e-mail** : lorsque cette option est sélectionnée, les utilisateurs et utilisatrices sont avertis par e-mail lorsqu’ils sont ajoutés à ce profil ou supprimés de celui-ci.

1. Cliquez sur **Enregistrer**.

Le nouveau profil de produit est enregistré et visible dans la liste des profils de produits dans l’Admin Console.

### Attribuer des autorisations personnalisées au nouveau profil de produit {#assign-permissions}

Maintenant que vous disposez d’un nouveau profil de produit, vous pouvez lui attribuer des autorisations personnalisées.

1. Dans Admin Console, cliquez sur le nom du [profil de produit que vous venez de créer](#create).

1. Dans la fenêtre qui s’ouvre, sélectionnez l’onglet **Autorisations** pour afficher la liste des autorisations modifiables.

   ![Autorisations modifiables.](/help/assets/permissions-tab.png)

1. Cliquez sur le lien **Modifier** pour obtenir l’autorisation de le modifier.

1. La fenêtre **Modifier les autorisations** s’ouvre.
   * L’autorisation que vous avez sélectionnée à l’étape précédente est sélectionnée dans la colonne de gauche.
   * Les éléments d’autorisation disponibles pour l’affectation de l’autorisation se trouvent dans la colonne du milieu intitulée **Autorisations disponibles**.
   * Les éléments d’autorisation attribués se trouvent dans la colonne de droite intitulée **Éléments d’autorisation inclus**.

   ![Modification des éléments d’autorisation](/help/assets/edit-permission-items.png)

1. Cliquez sur l’icône de signe plus (`+`) en regard de l’élément d’autorisation pour l’ajouter à la colonne **Éléments d’autorisation inclus**. Si nécessaire, cliquez sur l’icône `i` en regard d’un élément d’autorisation pour en savoir plus.

1. Dans la partie supérieure de la colonne **Autorisations disponibles**, cliquez sur **Ajouter tout** pour ajouter toutes les autorisations. De même, cliquez sur **Tout supprimer** pour supprimer toutes les autorisations sélectionnées précédemment.

1. Cliquez sur **Enregistrer** lorsque vous avez terminé de définir les éléments d’autorisation pour votre nouveau profil de produit.

Votre nouveau profil de produit est maintenant enregistré avec ses autorisations personnalisées.

### Affecter des utilisateurs et utilisatrices au nouveau profil de produit {#assign-users}

Vous pouvez désormais affecter des personnes au nouveau profil de produit que vous avez créé avec des autorisations personnalisées.

1. Dans Admin Console, cliquez sur le nom du [nouveau profil de produit auquel vous venez d’affecter des autorisations personnalisées](#assign-permissions).

1. Dans la fenêtre qui s’ouvre, sélectionnez l’onglet **Utilisateurs et utilisatrices**.

1. Cliquez sur **Ajouter des utilisateurs et utilisatrices** et affectez des personnes à votre nouveau profil de produit avec des autorisations personnalisées.

Voir la section **Ajouter des utilisateurs et des utilisatrices et des groupes d’utilisateurs et utilisatrices à un profil de produit** du document [Gérer des profils de produit pour les utilisateurs et utilisatrices d’entreprise](https://helpx.adobe.com/fr/enterprise/using/manage-product-profiles.html) pour plus d’informations sur l’utilisation d’Admin Console.

## Autorisations configurables {#configurable-permissions}

Les autorisations suivantes sont disponibles pour créer des profils personnalisés.

| Autorisation | Description |
| --- | --- |
| `Program Access` | Autoriser des personnes à accéder aux programmes |
| `Program Edit` | Autoriser les personnes à modifier des programmes |
| `Pipeline Create` | Autoriser les personnes à créer des pipelines |
| `Pipeline Delete` | Autoriser les personnes à supprimer des pipelines |
| `Pipeline Edit` | Autoriser les personnes à modifier les pipelines |
| `Production Deployments Approve/Reject` | Autoriser les personnes à approuver ou rejeter une étape de déploiement en production |
| `Pipeline Executions Cancel` | Autoriser les personnes à annuler les exécutions de pipeline |
| `Pipeline Executions Start` | Autoriser les personnes à démarrer de nouvelles exécutions de pipeline |
| `Override/Reject Important Metric Failures` | Autoriser les personnes à remplacer et à rejeter les échecs de mesures importantes |
| `Production Deployments Schedule` | Autoriser des personnes à planifier une étape de déploiement en production |
| `Repository Info Access` | Autoriser les personnes à accéder aux informations du référentiel et à générer un mot de passe d’accès |
| `Repository Create` | Autoriser les personnes à créer des référentiels Git |
| `Repository Delete` | Autoriser les personnes à supprimer des référentiels Git |
| `Repository Edit` | Autoriser les personnes à modifier les référentiels Git |
| `Repository Code Generate` | Autoriser les personnes à générer des projets à partir de l’archétype |
| `Content Copy Manage` | Autoriser les personnes à gérer les opérations de copie de contenu |

### Autorisations au niveau de l’organisation {#organization-level}

Les autorisations au niveau de l’organisation sont toujours appliquées à tous les programmes d’une organisation.

**Accès aux informations sur le référentiel** est un exemple d’autorisation au niveau de l’organisation dans Cloud Manager. Cette autorisation permet aux personnes de générer un nom d’utilisateur ou d’utilisatrice, un mot de passe et une URL de référentiel pour accéder aux projets des clientes et clients et y contribuer. Bien que le nom d’utilisateur ou d’utilisatrice et le mot de passe restent cohérents dans tous les référentiels de l’organisation, chaque programme dispose d’une URL de référentiel unique.

Voir la section [Référentiel de code source](/help/requirements/source-code-repository.md) pour plus d’informations.

## Termes {#terms}

Les termes suivants sont utilisés pour créer et gérer des autorisations personnalisées et des rôles prédéfinis.

| Terme | Description |
| --- | --- |
| Autorisations prédéfinies | Rôles prédéfinis tels que **Propriétaire de l’entreprise**, **Responsable de déploiement**, etc. pour régir différentes fonctionnalités de Cloud Manager. Pour plus d’informations sur les rôles prédéfinis, voir la section [Autorisations basées sur les rôles](/help/requirements/role-based-permissions.md). |
| Autorisations personnalisées | Fonctionnalités de Cloud Manager qui permettent aux utilisateurs et utilisatrices de créer des profils d’autorisation pour définir des rôles afin de régir les fonctionnalités prises en charge de Cloud Manager |
| Profil d’autorisation | Créé dans Admin Console pour gérer les autorisations configurables qui s’appliqueront aux utilisateurs et utilisatrices faisant partie du profil d’autorisation. |
| Autorisation configurable | Les autorisations de Cloud Manager peuvent être configurées dans le profil d’autorisation. |
| Élément d’autorisation | Ressource de programme, d’environnement ou de pipeline sur laquelle une autorisation peut être appliquée. |

Les éléments d’autorisation se rapportent à la portée dans laquelle les autorisations seront appliquées. En règle générale, il s’agit de l’un des éléments suivants.

| Type d’élément d’autorisation | Exemple | Description |
| --- | --- | --- |
| Organisation | Organisation:entrepriseA | Toutes les ressources applicables d’une organisation. Une ressource peut être un programme, un environnement ou un pipeline. Si l’utilisateur ou l’utilisatrice ajoute une organisation pour n’importe quelle autorisation, toutes les nouvelles ressources de cette organisation auront également cette autorisation. |
| Programme | Programme A | Toutes les ressources applicables d’un programme. |
| Environnement | Programme A : environnement | Applicable dans un environnement spécifique. |
| Pipeline | Programme A : pipeline | Applicable sur un pipeline spécifique. |

## Limites {#limitations}

Gardez à l’esprit les limites suivantes lorsque vous utilisez des autorisations personnalisées :

* Un [ensemble limité d’autorisations est disponible](#configurable-permissions) pour créer des profils personnalisés.
* Les ressources telles que le programme, l’environnement, le pipeline, etc. créées dans Cloud Manager peuvent prendre jusqu’à deux minutes pour s’afficher dans Admin Console pour la configuration des autorisations.
* Dans de rares cas où le service d’autorisations personnalisées ne répond pas, les profils prédéfinis sont toujours disponibles et les utilisateurs et utilisatrices des profils prédéfinis disposent toujours d’un accès approprié.

## Questions fréquentes {#faq}

### Quels profils d’autorisation sont des profils d’autorisation prédéfinis ?

* Propriétaire de l’entreprise
* Responsable de programme
* Responsable de déploiement
* Développeur ou développeuse

Pour plus d’informations sur les rôles prédéfinis, voir la section [Autorisations basées sur les rôles](/help/requirements/role-based-permissions.md).

### Qu’advient-il des profils d’autorisation prédéfinis lors de l’introduction de profils personnalisés ?

Les profils de produits et les rôles de Cloud Manager par défaut continuent de fonctionner comme auparavant.

### Puis-je modifier des profils d’autorisation prédéfinis ?

Non, les profils par défaut ne sont pas modifiables. Vous ne pouvez pas ajouter d’autorisations au profil d’autorisation par défaut, ni les supprimer de celui-ci. Vous pouvez uniquement ajouter ou supprimer des utilisateurs et utilisatrices aux/des profils prédéfinis.

### Dois-je supprimer les profils d’autorisation prédéfinis puisque les profils personnalisés sont désormais disponibles ?

Les profils d’autorisation prédéfinis ne doivent pas être supprimés de l’Admin Console.

### Puis-je ajouter des utilisateurs et utilisatrices à plusieurs profils d’autorisation ?

Oui, un utilisateur ou une utilisatrice peut faire partie de plusieurs profils, y compris des profils d’autorisation prédéfinis et personnalisés. Lorsqu’une personne est affectée à plusieurs profils, les autorisations combinées de tous les profils d’autorisation affectés lui seront disponibles.

### Que se passe-t-il si une personne est autorisée à modifier un environnement/pipeline mais n’a pas accès à un programme contenant l’environnement/le pipeline ?

Dans ce cas, la personne ne pourra pas accéder à l’environnement ou au pipeline si elle ne dispose pas des autorisations **Accès au programme** contenant l’environnement ou le pipeline.

### Que se passe-t-il si je dispose de programmes AEM as a Cloud Service et AMS dans la même organisation IMS ? Puis-je gérer les autorisations d’un profil ? {#ams-and-aemaacs}

Créez un profil distinct pour chaque type de produit. C’est-à-dire, un pour AEM as a Cloud Service et un pour Adobe Managed Services ou AMS.
