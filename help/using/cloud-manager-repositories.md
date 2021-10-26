---
title: Référentiels Cloud Manager
description: Référentiels Cloud Manager
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 17f79fdc7278cae532485570a6e2b8700683ef0d
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 95%

---

# Référentiels Cloud Manager {#cloud-manager-repos}

Les référentiels créés et disponibles dans Cloud Manager peuvent être affichés et gérés à partir de la page Référentiels.

## Ajout et gestion de référentiels {#add-manage-repos}

Suivez les étapes ci-dessous pour afficher et gérer les référentiels dans Cloud Manager :

1. Sur la page **Aperçu du programme**, cliquez sur l’onglet **Référentiels** et accédez à la page **Référentiels**.

1. Cliquez sur **Ajouter un référentiel** pour lancer l’assistant.

   >[!NOTE]
   >Un utilisateur possédant le rôle Gestionnaire de déploiement ou Propriétaire de l’entreprise doit être connecté pour pouvoir ajouter un référentiel.

   ![](assets/create-repo2.png)


1. Saisissez le nom et la description demandés, puis cliquez sur **Enregistrer**.

   ![](assets/repo-1.png)

1. Sélectionnez **Enregistrer**. Le référentiel que vous venez de créer s’affiche dans le tableau, comme illustré ci-dessous.

   ![](assets/create-repo3.png)

   >[!NOTE]
   >Les référentiels créés dans Cloud Manager peuvent également être sélectionnés au cours des étapes d’ajout ou de modification du pipeline.

1. Vous pouvez sélectionner le référentiel et cliquer sur les options de menu à l’extrémité droite de la table pour **Copier l’URL du référentiel**, **Afficher et mettre à jour** ou **Supprimer** votre référentiel, comme illustré dans la figure ci-dessous.

   ![](assets/create-repo3.png)



## Prise en charge des sous-modules Git {#git-submodule-support}

Les sous-modules Git peuvent être utilisés pour fusionner le contenu de plusieurs branches dans des référentiels Git au moment de la création. Lorsque le processus de création de Cloud Manager s’exécute, une fois le référentiel configuré pour le pipeline cloné et la branche configurée extraite, si la branche contient un fichier `.gitmodules` dans le répertoire racine, la commande est exécutée.

```
$ git submodule update --init
```

Cette procédure extrait chaque sous-module dans le répertoire approprié. Cette technique constitue une alternative potentielle à l’[utilisation de plusieurs référentiels Git sources](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/working-with-multiple-source-git-repositories.html?lang=fr) pour les organisations qui maîtrisent l’utilisation des sous-modules Git et qui ne souhaitent pas gérer de processus de fusion externe.

Par exemple, supposons qu’il existe trois référentiels, chacun contenant une seule branche nommée « main ». Dans le référentiel « principal », c’est-à-dire celui qui est configuré dans les pipelines, la branche principale contient un fichier pom.xml qui déclare les projets contenus dans les deux autres référentiels :

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

```
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Vous obtenez un fichier `.gitmodules` qui ressemble à ceci :

```
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

Lors de l’utilisation de sous-modules Git, prenez en compte les points suivants :

* L’URL Git doit se trouver exactement dans la syntaxe décrite ci-dessus. Pour des raisons de sécurité, n’incorporez pas les informations d’identification dans ces URL.
* Seuls les sous-modules situés à la racine de la branche sont pris en charge.
* Les références des sous-modules Git sont stockées vers des validations git spécifiques. Par conséquent, lorsque des modifications sont apportées au référentiel de sous-module, la validation référencée doit être mise à jour, par exemple à l’aide de `git submodule update --remote`.
* Sauf si nécessaire, il est vivement recommandé d’utiliser des sous-modules &quot;superficiels&quot;. Pour ce faire, exécutez `git config -f .gitmodules submodule.<submodule path>.shallow true` pour chaque sous-module.
