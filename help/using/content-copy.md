---
title: Outil de copie de contenu
description: L’outil de copie de contenu de Cloud Manager permet aux utilisateurs de copier du contenu modifiable à la demande à partir de leurs environnements de production AEM vers des environnements inférieurs à des fins de test.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 435efe2e6cecae738a62869c55034113c09f70e7
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 95%

---

# Outil de copie de contenu {#content-copy}

L’outil de copie de contenu de Cloud Manager permet aux utilisateurs de copier du contenu modifiable à la demande à partir de leurs environnements de production AEM vers des environnements inférieurs à des fins de test.

## Présentation {#introduction}

Les données actuelles et réelles sont utiles à des fins de test, de validation et d’acceptation par l’utilisateur. L’outil de copie de contenu vous permet de copier du contenu de votre environnement de production AEM vers un environnement d’évaluation ou de développement pour de tels tests.

Le contenu à copier est défini par un jeu de contenu. Un jeu de contenu est constitué d’une liste de chemins JCR qui contiennent le contenu modifiable à copier d’un environnement source vers un environnement cible dans le même programme Cloud Manager. Les chemins d’accès suivants sont autorisés dans un jeu de contenu.

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
```

Lors de la copie de contenu, l’environnement source est la source de vérité.

* Si le contenu a été modifié dans l’environnement de destination, il sera remplacé par le contenu de la source si les chemins d’accès sont les mêmes.
* Si les chemins d’accès sont différents, le contenu de la source sera fusionné avec le contenu de la destination.

>[!NOTE]
>
>Contactez votre ingénieure ou ingénieur du succès client (CSE) pour activer cette fonctionnalité.

## Autorisations {#permissions}

Pour utiliser l’outil de copie de contenu, le rôle **Responsable de déploiement** doit être affecté à l’utilisateur ou à l’utilisatrice dans les environnements source et cible.

## Créer un jeu de contenu {#create-content-set}

Pour qu’un contenu puisse être copié, un jeu de contenu doit être défini. Une fois définis, les jeux de contenu peuvent être réutilisés pour copier du contenu. Pour créer un jeu de contenu, suivez la procédure décrite ci-après.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Accédez à la page **Jeux de contenu** à partir de l’écran **Environnements**.

1. Appuyez ou cliquez sur le bouton **Ajouter un jeu de contenu** en haut à droite de l’écran.

   ![Jeux de contenu](/help/assets/content-sets.png)

1. Dans l’onglet **Détails** de l’assistant, indiquez le nom et la description du jeu de contenu, puis appuyez ou cliquez sur **Continuer**.

   ![Détails du jeu de contenu](/help/assets/add-content-set-details.png)

1. Dans l’onglet **Chemins d’accès au contenu** de l’assistant, indiquez les chemins d’accès au contenu modifiable à inclure dans le jeu de contenu.

   1. Entrez le chemin dans le champ **Ajouter un chemin d’accès à inclure**.
   1. Appuyez ou cliquez sur le bouton **Ajouter un chemin** pour ajouter le chemin d’accès au jeu de contenu.
   1. Appuyez ou cliquez encore sur le bouton **Ajouter un chemin** si nécessaire.

   ![Ajouter des chemins à un jeu de contenu](/help/assets/add-content-set-paths.png)

1. Si vous devez affiner ou limiter votre jeu de contenu, les sous-chemins peuvent être exclus.

   1. Dans la liste des chemins d’accès inclus, appuyez ou cliquez sur l’icône **Ajouter des sous-chemins à exclure** à côté du chemin que vous devez limiter.
   1. Saisissez le sous-chemin d’accès à exclure sous le chemin d’accès sélectionné.
   1. Appuyez ou cliquez sur **Exclure le chemin**.
   1. Appuyez ou cliquez encore sur **Ajouter des sous-chemins à exclure** pour ajouter d’autres chemins à exclure si nécessaire.

   ![Exclusion de chemins](/help/assets/add-content-set-paths-excluded.png)

1. Vous pouvez modifier les chemins spécifiés si nécessaire.

   1. Appuyez ou cliquez sur le X à côté des sous-chemins exclus pour les supprimer.
   1. Appuyez ou cliquez sur le bouton représentant des points de suspension pour avoir accès aux options **Modifier** et **Supprimer**.

   ![Modification de la liste de chemins](/help/assets/add-content-set-excluded-paths.png)

1. Appuyez ou cliquez sur **Créer** pour créer le jeu de contenu.

Le jeu de contenu peut désormais être utilisé pour copier du contenu entre des environnements.

>[!NOTE]
>
>Vous pouvez ajouter jusqu’à 50 chemins dans un jeu de contenu.
>Il n’existe aucune limitation sur les chemins exclus.

## Modification d’un jeu de contenu {#edit-content-set}

Procédez de la même façon que lors de la création d’une étape de contenu. Au lieu d’appuyer ou de cliquer sur **Ajouter un jeu de contenu**, sélectionnez un jeu existant dans la console, puis sélectionnez **Modifier** dans le menu représentant des points de suspension.

![Modifier le jeu de contenu](/help/assets/edit-content-set.png)

Lors de la modification de votre jeu de contenu, vous devrez peut-être développer les chemins configurés pour que s’affichent les sous-chemins exclus.

## Copie de contenu {#copy-content}

Une fois qu’un jeu de contenu a été créé, vous pouvez l’utiliser pour copier du contenu. Pour copier du contenu, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Accédez à la page **Jeux de contenu** à partir de l’écran **Environnements**.

1. Sélectionnez un jeu de contenu dans la console, puis **Copier le contenu** dans le menu représentant des points de suspension.

   ![Copier le contenu](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Un environnement ne peut pas être sélectionné si :
   >
   >* L’utilisateur ne dispose pas des autorisations appropriées.
   >* Un pipeline en cours d’exécution ou une opération de copie de contenu est en cours dans l’environnement.

1. Dans la boîte de dialogue **Copier le contenu**, spécifiez la source et la destination de votre action de copie de contenu.

1. Vous pouvez choisir de supprimer ou de conserver les chemins d’exclusion dans l’environnement cible. Cochez la case `Do not delete exclude paths from destination` si vous souhaitez conserver les chemins d’exclusion spécifiés dans le jeu de contenu. Si cette case n’est pas cochée, les chemins d’exclusion sont supprimés dans l’environnement cible.

   ![Copie de contenu](/help/assets/copying-content.png)

1. Appuyez ou cliquez sur **Copier**.

Le processus de copie démarre. Le statut du processus de copie est répercuté dans la console pour le jeu de contenu sélectionné.

## Activité de copie de contenu {#copy-activity}

Vous pouvez surveiller le statut de vos processus de copie à la page **Activité de copie de contenu**.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Accédez à la page **Activité de copie de contenu** à partir de l’écran **Environnements**.

![Activité de copie de contenu](/help/assets/copy-content-activity.png)

### Statuts de la copie de contenu {#statuses}

Une fois que vous avez commencé à copier du contenu, le processus peut avoir l’un des statuts suivants.

| État | Description |
|---|---|
| En cours | L’opération de copie de contenu est en cours. |
| Échec | L’opération de copie de contenu a échoué. |
| Terminé | L’opération de copie de contenu est terminée avec succès. |

## Limites {#limitations}

L’outil de copie de contenu présente les limites suivantes.

* Une copie de contenu ne peut pas être effectuée d’un environnement inférieur vers un environnement supérieur.
* Une copie de contenu ne peut être effectuée que dans le même niveau (auteur-auteur ou publication-publication, par exemple).
* Une copie de contenu ne peut pas être effectuée sur plusieurs programmes et plusieurs régions.
* La copie de contenu pour la topologie basée sur le magasin de données cloud ne peut être effectuée que lorsque l’environnement source et de destination se trouve sur le même fournisseur de cloud.
* L’exécution simultanée d’opérations de copie de contenu sur le même environnement n’est pas possible.
* Une copie de contenu ne peut pas être effectuée si une opération principale est en cours d’exécution dans l’environnement de destination ou source, tel qu’un pipeline CI/CD.
* Vous pouvez spécifier jusqu’à cinquante chemins par jeu de contenu. Il n’existe aucune limitation sur les chemins exclus.
* L’outil de copie de contenu ne doit pas être utilisé comme outil de clonage ou de mise en miroir, car il ne peut pas effectuer le suivi du contenu déplacé ou supprimé sur la source.
* Une copie de contenu ne peut pas être suspendue ou annulée une fois qu’elle est lancée.
* L’outil de copie de contenu copie les ressources avec les métadonnées liées aux médias dynamiques de l’environnement supérieur vers l’environnement inférieur sélectionné.
   * Les ressources copiées doivent ensuite être retraitées à l’aide de la variable [Workflow des ressources de processus DAM](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-workflow.html?lang=fr) dans l’environnement inférieur afin d’utiliser la configuration dynamic media correspondante.
