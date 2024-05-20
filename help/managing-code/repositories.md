---
title: Référentiels Cloud Manager
description: Découvrez comment créer, modifier et accéder à des référentiels pour vos programmes Cloud Manager.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 1d4ab9704fdb743b097e24be335fbf069d1e78bd
workflow-type: ht
source-wordcount: '762'
ht-degree: 100%

---


# Référentiels Cloud Manager {#cloud-manager-repos}

Les référentiels sont l’endroit où vous pouvez gérer votre code à l’aide de Git. Découvrez comment créer des référentiels pour vos programmes Cloud Manager.

## Accéder aux référentiels {#accessing-repos}

Vous pouvez accéder à vos référentiels Git et les gérer en libre-service à partir de Cloud Manager.

Pour accéder à votre référentiel, utilisez le bouton **Accéder aux informations sur le référentiel** disponible dans Cloud Manager, notamment sur la vignette de pipeline.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la vignette **Pipelines** de la page **Présentation du programme**. C’est là que se trouve l’option **Accéder aux informations sur le référentiel**, qui vous permet de gérer et d’accéder à votre référentiel Git [configuré avec ce pipeline](/help/using/production-pipelines.md).

   ![Bouton Accéder aux informations sur le référentiel](/help/assets/access-repo1.png)

1. Appuyez ou cliquez sur le bouton **Accéder aux informations sur le référentiel** pour ouvrir une boîte de dialogue qui affiche les éléments suivants :

   * URL vers le référentiel Git ;
   * Nom d’utilisateur ou d’utilisatrice
   * mot de passe ;
   * commande Git à exécuter pour cloner le référentiel localement.

   ![Boîte de dialogue d’informations sur le référentiel](/help/assets/access-repo-create.png)

Utilisez les informations fournies pour cloner le référentiel localement afin de pouvoir commencer le développement local.

>[!NOTE]
>
>L’option **Accéder aux informations sur le référentiel** est visible par les utilisateurs possédant le rôle **Développeur** ou **Responsable de déploiement**.

## Ajouter des référentiels {#add-repos}

Pour ajouter des référentiels dans Cloud Manager, procédez comme suit :

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Aperçu du programme**, cliquez sur l’onglet **Référentiels** et accédez à la page **Référentiels**.

1. Cliquez sur **Ajouter un référentiel** pour lancer l’assistant.

   >[!NOTE]
   >
   >Vous devez avoir le rôle **Responsable de déploiement** ou **Propriétaire de l’entreprise** pour ajouter un référentiel.

   ![Ajouter un référentiel](/help/assets/create-repo2.png)

1. Saisissez le nom et la description demandés, puis cliquez sur **Enregistrer**.

   ![Détails du référentiel](/help/assets/repo-1.png)

1. Sélectionnez **Enregistrer**.

Le référentiel que vous venez de créer s’affiche.

Vous pouvez sélectionner les référentiels créés dans Cloud Manager lorsque vous [créez vos pipelines](/help/overview/ci-cd-pipelines.md).

## Afficher et modifier des référentiels {#edit-repos}

Pour modifier et afficher les référentiels dans Cloud Manager, procédez comme suit :

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Présentation du programme**, cliquez sur l’onglet **Référentiels** et accédez à la page **Référentiels**. Ici, vous pouvez afficher les détails de vos référentiels existants.

1. Sélectionnez le référentiel et cliquez sur le bouton représentant des points de suspension à droite du tableau pour **copier l’URL du référentiel** ou **afficher et mettre à jour** votre référentiel.

![Modifier le référentiel](/help/assets/create-repo3.png)

## Supprimer des référentiels {#delete-repos}

Pour supprimer un référentiel, suivez les mêmes étapes que [pour afficher et modifier des référentiels](#edit-repos), mais sur la page **Référentiels**, sélectionnez **Supprimer** à partir du bouton représentant des points de suspension du référentiel à supprimer.

Notez que lorsqu’un référentiel est supprimé dans Cloud Manager, il est marqué comme supprimé et n’est plus accessible à l’utilisateur ou à l’utilisatrice, mais il est conservé dans le système à des fins de récupération.

Si vous essayez de créer un référentiel après avoir supprimé un référentiel portant le même nom, vous recevrez le message d’erreur « Une erreur s’est produite lors de la tentative de création du référentiel. Contactez votre CSE ou l’assistance Adobe. »

Si vous recevez ce message d’erreur, contactez l’assitance Adobe pour obtenir de l’aide afin de renommer le référentiel supprimé ou de choisir un autre nom pour votre nouveau référentiel.

## Prise en charge des sous-modules Git {#git-submodule-support}

Les sous-modules Git peuvent être utilisés pour fusionner le contenu de plusieurs branches dans des référentiels Git au moment de la création.

Lorsque le processus de création de Cloud Manager s’exécute, une fois le référentiel configuré pour le pipeline cloné et la branche configurée extraite, si la branche contient un fichier `.gitmodules` dans le répertoire racine, la commande est exécutée.

```
$ git submodule update --init
```

Cette procédure extrait chaque sous-module dans le répertoire approprié. Cette technique constitue une alternative potentielle à l’[utilisation de plusieurs référentiels Git sources](/help/managing-code/multiple-git-repos.md) pour les organisations qui maîtrisent l’utilisation des sous-modules Git et qui ne souhaitent pas gérer de processus de fusion externe.

Par exemple, supposons qu’il existe trois référentiels, chacun contenant une seule branche nommée `main`. Dans le référentiel « principal », c’est-à-dire celui qui est configuré dans les pipelines, la branche `main` contient un fichier `pom.xml` qui déclare les projets contenus dans les deux autres référentiels :

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

Lors de l’utilisation de sous-modules Git, veuillez tenir compte des points suivants :

* L’URL Git doit se trouver exactement dans la syntaxe décrite ci-dessus.
* Pour des raisons de sécurité, n’incorporez pas les informations d’identification dans ces URL.
* Seuls les sous-modules situés à la racine de la branche sont pris en charge.
* Les références des sous-modules Git sont stockées vers des validations Git spécifiques.
   * Par conséquent, lorsque des modifications sont apportées au référentiel de sous-module, la validation référencée doit être mise à jour, par exemple à l’aide de `git submodule update --remote`.
* Sauf indication contraire, il est vivement recommandé d’utiliser des sous-modules « superficiels ».
   * Pour ce faire, exécutez `git config -f .gitmodules submodule.<submodule path>.shallow true` pour chaque sous-module.
