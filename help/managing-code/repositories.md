---
title: Référentiels Cloud Manager
description: Découvrez comment accéder à des référentiels, les créer et les modifier pour vos programmes Cloud Manager.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 49%

---


# Référentiels Cloud Manager {#cloud-manager-repos}

Les référentiels sont l’emplacement où vous gérez votre code à l’aide de git. Découvrez comment créer des référentiels pour vos programmes Cloud Manager.

## Accès aux référentiels {#accessing-repos}

Vous pouvez accéder à vos référentiels Git et les gérer en libre-service à partir de Cloud Manager.

Pour accéder à votre référentiel, utilisez le **Accès aux informations sur le référentiel** est disponible dans Cloud Manager, notamment sur la carte du pipeline.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à **Pipelines** de la carte **Aperçu du programme** et vous verrez le **Accès aux informations sur le référentiel** option d’accès et de gestion de votre référentiel git [configuré avec ce pipeline.](/help/using/production-pipelines.md)

   ![Bouton Accéder aux informations du référentiel](/help/assets/access-repo1.png)

1. Si vous passez à la variable **Non-production** onglet pipeline , **Accès aux informations sur le référentiel** est également disponible ici, car [configuré pour le pipeline.](/help/using/non-production-pipelines.md)

   ![Pipelines hors production](/help/assets/access-repo-nonprod.png)

1. Cliquez sur le bouton **Accès aux informations sur le référentiel** pour ouvrir une boîte de dialogue qui affiche :

   * URL vers le référentiel git
   * nom d’utilisateur ;
   * Mot de passe
   * Commande Git à exécuter pour cloner le référentiel localement

   ![Boîte de dialogue d’informations du référentiel](/help/assets/access-repo-create.png)

Utilisez les informations fournies pour cloner le référentiel localement afin de pouvoir commencer le développement local.

>[!NOTE]
>
>L’option **Accéder aux informations sur le référentiel** est visible par les utilisateurs possédant le rôle Développeur ou Gestionnaire de déploiement.********

## Ajout de référentiels {#add-repos}

Pour ajouter des référentiels dans Cloud Manager, procédez comme suit :

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Aperçu du programme**, cliquez sur l’onglet **Référentiels** et accédez à la page **Référentiels**.

1. Cliquez sur **Ajouter un référentiel** pour lancer l’assistant.

   >[!NOTE]
   >
   >Vous devez avoir la variable **Responsable de déploiement** ou **Propriétaire de l’entreprise** rôle pour ajouter un référentiel.

   ![Ajouter un référentiel](/help/assets/create-repo2.png)

1. Saisissez le nom et la description demandés, puis cliquez sur **Enregistrer**.

   ![Détails du référentiel](/help/assets/repo-1.png)

1. Sélectionnez **Enregistrer**.

Le référentiel que vous venez de créer s’affiche.

![Nouveau référentiel créé](/help/assets/create-repo3.png)

Vous pouvez sélectionner les référentiels créés dans Cloud Manager lorsque vous [créez vos pipelines.](/help/overview/ci-cd-pipelines.md)

## Affichage et modification des référentiels {#edit-repos}

Pour modifier et afficher les référentiels dans Cloud Manager, procédez comme suit :

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Aperçu du programme**, cliquez sur l’onglet **Référentiels** et accédez à la page **Référentiels.** Ici, vous pouvez afficher les détails de vos référentiels existants.

1. Sélectionnez le référentiel et cliquez sur le bouton représentant des points de suspension à l’extrémité droite du tableau pour **Copier l’URL du référentiel**, **Afficher et mettre à jour** ou **Supprimer** votre référentiel.

![Modifier le référentiel](/help/assets/create-repo3.png)

## Prise en charge des sous-modules Git {#git-submodule-support}

Les sous-modules Git peuvent être utilisés pour fusionner le contenu de plusieurs branches dans des référentiels Git au moment de la création.

Lorsque le processus de création de Cloud Manager s’exécute, une fois le référentiel configuré pour le pipeline cloné et la branche configurée extraite, si la branche contient un fichier `.gitmodules` dans le répertoire racine, la commande est exécutée.

```
$ git submodule update --init
```

Cette procédure extrait chaque sous-module dans le répertoire approprié. Cette technique constitue une alternative potentielle à l’[utilisation de plusieurs référentiels Git sources](/help/managing-code/multiple-git-repos.md) pour les organisations qui maîtrisent l’utilisation des sous-modules Git et qui ne souhaitent pas gérer de processus de fusion externe.

Par exemple, supposons qu’il existe trois référentiels, chacun contenant une seule branche nommée `main`. Dans le référentiel &quot;Principal&quot;, c’est-à-dire celui configuré dans les pipelines, la variable `main` comporte une branche `pom.xml` déclarant les projets contenus dans les deux autres référentiels :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

Vous pouvez ensuite ajouter des sous-modules pour les deux autres référentiels :

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Vous obtenez un fichier `.gitmodules` qui ressemble à ceci :

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Vous trouverez plus d’informations sur les sous-modules Git dans le [Manuel de référence Git](https://git-scm.com/book/fr/v2/Git-Tools-Submodules).

### Limites {#limitations}

Lors de l’utilisation de sous-modules git, veuillez tenir compte des points suivants :

* L’URL git doit se trouver exactement dans la syntaxe décrite ci-dessus.
* Pour des raisons de sécurité, n’incorporez pas les informations d’identification dans ces URL.
* Seuls les sous-modules situés à la racine de la branche sont pris en charge.
* Les références des sous-modules Git sont stockées vers des validations git spécifiques.
   * Par conséquent, lorsque des modifications sont apportées au référentiel de sous-module, la validation référencée doit être mise à jour, par exemple à l’aide de `git submodule update --remote`.
* Sauf si nécessaire, il est vivement recommandé d’utiliser des sous-modules « superficiels ». 
   * Pour ce faire, exécutez `git config -f .gitmodules submodule.<submodule path>.shallow true` pour chaque sous-module.
