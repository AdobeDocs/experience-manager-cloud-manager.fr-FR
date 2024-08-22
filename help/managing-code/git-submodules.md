---
title: Prise en charge des sous-modules Git
description: Découvrez comment utiliser les sous-modules Git pour fusionner le contenu de plusieurs branches dans des référentiels Git au moment de la création.
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 20%

---

# Prise en charge des sous-modules Git pour les référentiels d’Adobe {#git-submodule-support}

Les sous-modules Git peuvent être utilisés pour fusionner le contenu de plusieurs branches dans des référentiels Git au moment de la création.

Lorsque le processus de création Cloud Manager s’exécute, il commence par cloner le référentiel du pipeline et extrait la branche configurée. Si la branche contient un fichier `.gitmodules` dans le répertoire racine, la commande est exécutée.

```
$ git submodule update --init
```

Ce processus extrait chaque sous-module dans le répertoire approprié. Cette technique est une alternative potentielle à [l’utilisation de plusieurs référentiels Git source](/help/managing-code/multiple-git-repos.md) pour les entreprises qui utilisent facilement des sous-modules Git et qui ne souhaitent pas gérer de processus de fusion externe.

Par exemple, supposons qu’il existe trois référentiels, chacun contenant une seule branche nommée `main`. Dans le référentiel &quot;principal&quot;, c’est-à-dire celui configuré dans les pipelines, la branche `main` possède un fichier `pom.xml` déclarant les projets contenus dans les deux autres référentiels :

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

Vous ajoutez ensuite des sous-modules pour les deux autres référentiels :

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Les résultats du fichier `.gitmodules` ressemblent à ce qui suit :

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

Pour plus d’informations sur les sous-modules Git, consultez le [manuel de référence Git](https://git-scm.com/book/fr/v2/Git-Tools-Submodules) .

## Limites {#limitations}

Lors de l’utilisation de sous-modules Git, tenez compte des points suivants :

* L’URL Git doit se trouver exactement dans la syntaxe décrite ci-dessus.
* Pour des raisons de sécurité, n’incorporez pas les informations d’identification dans ces URL.
* Seuls les sous-modules situés à la racine de la branche sont pris en charge.
* Les références de sous-module Git sont stockées dans des validations Git spécifiques. Par conséquent, lorsque des modifications sont apportées au référentiel de sous-module, la validation référencée doit être mise à jour. Par exemple, en utilisant `git submodule update --remote`.
* Sauf si nécessaire, Adobe vous recommande d’utiliser des sous-modules &quot;superficiels&quot; en exécutant `git config -f .gitmodules submodule.<submodule path>.shallow true` pour chaque sous-module.


## Prise en charge des sous-modules Git pour les référentiels privés {#private-repositories}

La prise en charge des sous-modules Git lors de l’utilisation de [référentiels privés](private-repositories.md) est largement la même que lors de l’utilisation de référentiels Adobe.

Cependant, après avoir configuré votre fichier `pom.xml` et exécuté les commandes `git submodule`, vous devez ajouter un fichier `.gitmodules` dans le répertoire racine du référentiel de l’agrégateur pour que Cloud Manager détecte la configuration du sous-module.

![fichier .gitmodules](assets/gitmodules.png)

![Agrégateur](assets/aggregator.png)

### Limites et recommandations {#limitations-recommendations-private-repos}

Lors de l’utilisation de sous-modules Git avec des référentiels privés, tenez compte des limites suivantes.

* Les URL Git des sous-modules peuvent être au format HTTPS ou SSH, mais elles doivent être liées à un référentiel Github.com . L’ajout d’un sous-module de référentiel d’Adobe à un référentiel d’agrégateur GitHub ou vice versa ne fonctionne pas.
* Les sous-modules GitHub doivent être accessibles pour l’application GitHub Adobe.
* [Les limites de l’utilisation des sous-modules Git avec des référentiels gérés par Adobe ](#limitations-recommendations) s’appliquent également.
