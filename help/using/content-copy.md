---
title: Outil Copie de contenu
description: L’outil de copie de contenu de Cloud Manager permet aux utilisateurs de copier du contenu modifiable à la demande à partir de leurs environnements de production AEM vers des environnements inférieurs à des fins de test.
source-git-commit: 360cbf7e3a21e530a4e43f13f6d414dae4afa104
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 7%

---


# Outil Copie de contenu {#content-copy}

L’outil de copie de contenu de Cloud Manager permet aux utilisateurs de copier du contenu modifiable à la demande à partir de leurs environnements de production AEM vers des environnements inférieurs à des fins de test.

## Présentation {#introduction}

Les données actuelles et réelles sont utiles à des fins de test, de validation et d’acceptation par l’utilisateur. L’outil de copie de contenu vous permet de copier du contenu de votre environnement d’AEM de production vers un environnement d’évaluation ou de développement pour de tels tests.

Le contenu à copier est défini par un jeu de contenu. Un jeu de contenu est constitué d’une liste de chemins JCR qui contiennent le contenu modifiable à copier d’un environnement source vers un environnement cible dans le même programme Cloud Manager. Les chemins d’accès suivants sont autorisés dans un jeu de contenu.

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
```

Lors de la copie de contenu, l’environnement source est la source de vérité.

* Si le contenu a été modifié dans l’environnement de destination, il sera remplacé par le contenu de la source, si les chemins d’accès sont identiques.
* Si les chemins d’accès sont différents, le contenu de la source est fusionné avec le contenu de la destination.

## Autorisations {#permissions}

Pour utiliser l’outil de copie de contenu, l’utilisateur doit être affecté à la fonction **Responsable de déploiement** dans les environnements source et cible.

## Création d’un jeu de contenu {#create-content-set}

Pour qu’un contenu puisse être copié, un jeu de contenu doit être défini. Une fois définis, les jeux de contenu peuvent être réutilisés pour copier du contenu. Pour créer un jeu de contenu, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Accédez au **Visionneuses de contenu** de la page **Environnements** écran.

1. Appuyez ou cliquez sur le bouton **Ajouter un jeu de contenu** en haut à droite de l’écran.

   ![Visionneuses de contenu](/help/assets/content-sets.png)

1. Sur le **Détails** dans l’assistant, indiquez le nom et la description du jeu de contenu, puis appuyez ou cliquez sur **Continuer**.

   ![Détails du jeu de contenu](/help/assets/add-content-set-details.png)

1. Sur le **Chemins du contenu** de l’assistant, indiquez les chemins d’accès au contenu modifiable à inclure dans le jeu de contenu.

   1. Entrez le chemin dans la **Ajouter un chemin d’inclusion** champ .
   1. Appuyez ou cliquez sur le bouton **Ajouter un chemin** pour ajouter le chemin d’accès au jeu de contenu.
   1. Appuyez ou cliquez sur le bouton **Ajouter un chemin** au besoin.

   ![Ajout de chemins à un jeu de contenu](/help/assets/add-content-set-paths.png)

1. Si vous devez affiner ou restreindre votre jeu de contenu, les sous-chemins peuvent être exclus.

   1. Dans la liste des chemins d’accès inclus, appuyez ou cliquez sur l’icône **Ajouter des sous-chemins d’exclusion** en regard du chemin que vous devez restreindre.
   1. Saisissez le sous-chemin d’accès à exclure sous le chemin d’accès sélectionné.
   1. Appuyez ou cliquez sur **Exclure le chemin**.
   1. Appuyez ou cliquez sur **Ajouter des sous-chemins d’exclusion** pour ajouter d’autres chemins à exclure, le cas échéant.

   ![Exclusion de chemins](/help/assets/add-content-set-paths-excluded.png)

1. Vous pouvez modifier les chemins spécifiés, si nécessaire.

   1. Appuyez ou cliquez sur le X en regard des sous-chemins exclus pour les supprimer.
   1. Appuyez ou cliquez sur le bouton représentant des points de suspension en regard des chemins d’accès à afficher. **Modifier** et **Supprimer** options.

   ![Modification de la liste de chemins](/help/assets/add-content-set-excluded-paths.png)

1. Appuyez ou cliquez sur **Créer** pour créer le jeu de contenu.

Le jeu de contenu peut désormais être utilisé pour copier du contenu entre les environnements.

## Modification d’un jeu de contenu {#edit-content-set}

Suivez les mêmes étapes que lors de la création d’une étape de contenu. Au lieu d’appuyer ou de cliquer sur **Ajouter un jeu de contenu**, sélectionnez un jeu existant dans la console, puis sélectionnez **Modifier** dans le menu points de suspension.

![Modifier le jeu de contenu](/help/assets/edit-content-set.png)

Lors de la modification de votre jeu de contenu, vous devrez peut-être développer les chemins configurés pour afficher les sous-chemins exclus.

## Copie de contenu {#copy-content}

Une fois qu’un jeu de contenu a été créé, vous pouvez l’utiliser pour copier du contenu. Pour copier du contenu, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Accédez au **Visionneuses de contenu** de la page **Environnements** écran.

1. Sélectionnez un jeu de contenu dans la console, puis sélectionnez **Copier le contenu** dans le menu points de suspension.

   ![Copie de contenu](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Un environnement ne peut pas être sélectionné si :
   >
   >* L’utilisateur ne dispose pas des autorisations appropriées.
   >* Un pipeline en cours d’exécution ou une opération de copie de contenu est en cours dans l’environnement.


1. Dans le **Copier le contenu** , spécifiez la source et la destination de votre action de copie de contenu.

   ![Copie de contenu](/help/assets/copying-content.png)

1. Appuyez ou cliquez sur **Copier**.

Le processus de copie démarre. L’état du processus de copie est répercuté dans la console pour le jeu de contenu sélectionné.

## Activité Copie de contenu {#copy-activity}

Vous pouvez surveiller l’état de vos processus de copie dans le **Copie de l’activité de contenu** page.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Accédez au **Copie de l’activité de contenu** de la page **Environnements** écran.

![Activité Copie de contenu](/help/assets/copy-content-activity.png)

### États de la copie de contenu {#statuses}

Une fois que vous avez commencé à copier du contenu, le processus peut avoir l’un des états suivants.

| État | Description |
|---|---|
| En cours | L’opération de copie de contenu est en cours |
| Échec | L’opération de copie de contenu a échoué |
| Terminé | Opération de copie de contenu terminée |

## Limites {#limitations}

L’outil de copie de contenu présente les limites suivantes.

* Une copie de contenu ne peut pas être effectuée d’un environnement inférieur vers un environnement supérieur.
* La copie de contenu ne peut être effectuée que dans le même niveau (auteur-auteur ou publication-publication).
* Il n’est pas possible de copier du contenu sur plusieurs programmes.
* L’exécution simultanée d’opérations de copie de contenu sur le même environnement n’est pas possible.
* La copie de contenu ne peut pas être effectuée si une opération principale est en cours d’exécution dans l’environnement de destination ou source, tel qu’un pipeline CI/CD.
* Vous pouvez spécifier jusqu’à dix chemins par jeu de contenu. Il n’y a aucune limitation sur les chemins exclus.
* L’outil de copie de contenu ne doit pas être utilisé comme outil de clonage ou de mise en miroir, car il ne peut pas effectuer le suivi du contenu déplacé ou supprimé sur la source.
* L’outil de copie de contenu ne dispose d’aucune fonctionnalité de contrôle de version et ne peut pas détecter automatiquement le contenu modifié ou le contenu nouvellement créé dans l’environnement source dans un jeu de contenu depuis la dernière opération de copie de contenu.
   * Si vous souhaitez mettre à jour votre environnement de destination avec des modifications de contenu uniquement depuis la dernière opération de copie de contenu, vous devez créer un jeu de contenu. Dans cet ensemble, spécifiez les chemins d’accès sur l’instance source où des modifications ont été apportées depuis la dernière opération de copie de contenu.
* Les informations de version ne sont pas incluses dans une copie de contenu.
