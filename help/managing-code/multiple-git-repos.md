---
title: Utiliser plusieurs référentiels Git
description: Au lieu de travailler directement avec le référentiel Git de Cloud Manager, vous pouvez apprendre à utiliser vos propres référentiels Git ou plusieurs autres.
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: ht
source-wordcount: '738'
ht-degree: 100%

---

# Utiliser plusieurs référentiels Git source {#working-with-multiple-source-git-repos}

Au lieu de travailler directement avec le référentiel Git de Cloud Manager, vous pouvez apprendre à utiliser vos propres référentiels Git ou plusieurs autres.

## Synchroniser des référentiels Git gérés par le client ou la cliente {#syncing-customer-managed-git-repositories}

Pour mettre à jour le référentiel Git Cloud Manager, configurez un processus de synchronisation automatisée si vous utilisez votre ou vos propres référentiels.

Selon l’emplacement d’hébergement de votre référentiel Git, il est possible d’utiliser une action GitHub ou une solution d’intégration continue comme Jenkins pour configurer l’automatisation. Si une automatisation a été mise en place, vous pouvez transférer automatiquement vos transmissions destinées à un référentiel Git vers celui de Cloud Manager.

Bien qu’une telle automatisation pour un seul référentiel Git détenu par le client ou la cliente soit simple, une configuration initiale plus impliquée est nécessaire pour plusieurs référentiels. Les contenus provenant de plusieurs répertoires Git doivent être associés à différents répertoires dans un seul référentiel Git de Cloud Manager. Le référentiel Git de Cloud Manager doit être configuré avec un `pom.xml` Maven racine qui répertorie les différents sous-projets dans la section Modules.

Vous trouverez ci-dessous un exemple de `pom.xml` pour deux référentiels Git appartenant à un client ou une cliente. Le premier projet est placé dans le répertoire nommé `project-a`, le second projet est placé dans le répertoire nommé `project-b`.

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

Ce fichier `pom.xml` racine est transmis vers une branche du référentiel Git de Cloud Manager. Les deux projets doivent ensuite être configurés pour transférer automatiquement les modifications vers le référentiel Git de Cloud Manager.

Par exemple, une transmission vers une branche du projet A peut déclencher une action GitHub. L’action extrait le projet A et le référentiel Git de Cloud Manager. Il copie tout le contenu du projet A dans le répertoire `project-a` du référentiel Git de Cloud Manager. Ensuite, il valide et transmet le changement.

À titre d’exemple, une modification apportée à la branche `main` du projet A est automatiquement transmise vers la branche `main` du référentiel Git de Cloud Manager. Bien entendu, il pourrait exister un mappage entre les branches, par exemple une transmission vers une branche nommée `dev` dans le projet A qui est transmise vers une branche nommée `development` dans le référentiel Git de Cloud Manager. Des étapes similaires sont nécessaires pour le projet B.

Selon la stratégie et les workflows d’embranchement, il est possible de configurer la synchronisation pour différentes branches. Si le référentiel Git utilisé ne propose pas de concept similaire aux actions GitHub, une intégration via Jenkins (ou un outil similaire) est également possible. Dans ce cas, un webhook déclenche un traitement Jenkins chargé d’effectuer le travail.

Suivez les étapes ci-dessous pour ajouter une nouvelle source ou un nouveau référentiel (la ou le troisième) :

1. Ajoutez une nouvelle action GitHub dans le nouveau référentiel pour transmettre les modifications de ce référentiel vers le référentiel Git de Cloud Manager.
1. Effectuez cette action au moins une fois pour vous assurer que le code du projet se trouve dans le référentiel Git de Cloud Manager.
1. Dans le référentiel Git de Cloud Manager, ajoutez une référence au nouveau répertoire dans le `pom.xml` Maven racine.

## Exemple d’action GitHub {#sample-github-action}

Une transmission vers la branche `main` déclenche ce genre d’action GitHub, qui est ensuite transmise dans un sous-répertoire du référentiel Git de Cloud Manager. Les actions GitHub doivent comporter deux secrets, `MAIN_USER` et `MAIN_PASSWORD`, pour pouvoir se connecter et effectuer des transmissions vers le référentiel Git de Cloud Manager.

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} https://${{ secrets.PAT }}@github.com/${MAIN_REPOSITORY}.git main 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf main/${PROJECT_DIR} 
          mv sub main/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C main add -f ${PROJECT_DIR}
          git -C main commit -F ../commit.txt
          git -C main push
```

Comme indiqué ci-dessus, l’utilisation d’une action GitHub est très flexible. Tout mappage entre les branches des référentiels Git peut être effectué, de même que tout mappage des projets Git distincts dans la disposition des répertoires du projet principal.

>[!NOTE]
>
>Le script ci-dessus utilise `git add` pour mettre à jour le référentiel, ce qui suppose que les suppressions sont incluses. Selon la configuration par défaut de Git, il peut être nécessaire de remplacer cette exigence par `git add --all`.

## Exemple de traitement Jenkins {#sample-jenkins-job}

Il s’agit d’un exemple de script pouvant être utilisé dans un traitement Jenkins ou similaire. Une modification dans un référentiel Git le déclenche. Le traitement Jenkins extrait l’état le plus récent de ce projet ou de cette branche, puis déclenche ce script.

Ce script extrait ensuite le référentiel Git de Cloud Manager et valide le code du projet dans un sous-répertoire.

Le traitement Jenkins doit comporter deux secrets, `MAIN_USER` et `MAIN_PASSWORD`, pour pouvoir se connecter et effectuer des transferts (push) vers le référentiel Git de Cloud Manager.

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

Comme indiqué ci-dessus, l’utilisation d’un traitement Jenkins est très flexible. Tout mappage entre les branches des référentiels Git peut être effectué, de même que tout mappage des projets Git distincts dans la disposition des répertoires du projet principal.

>[!NOTE]
>
>Le script ci-dessus utilise `git add` pour mettre à jour le référentiel, ce qui suppose que les suppressions sont incluses. Selon la configuration par défaut de Git, `git add` peut devoir être remplacé par `git add --all`.
