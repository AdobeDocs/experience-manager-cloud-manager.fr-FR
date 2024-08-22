---
title: Outil de copie de contenu
description: L’outil de copie de contenu Cloud Manager permet aux utilisateurs de copier du contenu modifiable à la demande à partir des environnements de production hébergés par AMS AEM 6.x dans des environnements inférieurs pour les tests.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 39%

---


# L’outil de copie de contenu {#content-copy}

L’outil de copie de contenu Cloud Manager permet aux utilisateurs de copier du contenu modifiable à la demande à partir des environnements de production hébergés par AMS AEM 6.x dans des environnements inférieurs pour les tests.

## Présentation {#introduction}

Les données actuelles et réelles sont utiles à des fins de test, de validation et d’acceptation par l’utilisateur. L’outil de copie de contenu vous permet de copier du contenu de votre environnement d’AEM hébergé en production AMS 6.x vers des environnements d’évaluation ou de développement. Ce workflow prend en charge divers scénarios de test.

Un jeu de contenu définit le contenu à copier. Un jeu de contenu comprend une liste de chemins JCR avec le contenu modifiable à copier. Le contenu passe d’un environnement source à un environnement cible. Tout cela dans le même programme Cloud Manager.

Les chemins d’accès suivants sont autorisés dans un jeu de contenu :

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

Lors de la copie de contenu, l’environnement source est la source de vérité.

* Si vous modifiez du contenu dans l’environnement de destination, le contenu source le remplace si les chemins correspondent.
* Si les chemins d’accès sont différents, le contenu de la source est fusionné avec le contenu de la destination.

## Autorisations {#permissions}

Pour utiliser l’outil de copie de contenu, l’utilisateur doit se voir attribuer le rôle **Deployment Manager** dans les environnements source et cible.

## Création d’un jeu de contenu {#create-content-set}

Pour qu’un contenu puisse être copié, un jeu de contenu doit être défini. Une fois définis, les jeux de contenu peuvent être réutilisés pour copier du contenu. Pour créer un jeu de contenu, suivez la procédure décrite ci-après.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Overview** , accédez à l’écran **Environments** (Environnements).

1. Dans l’écran **Environments** (Environnements), accédez à la page **Content Sets** (Visionneuses de contenu).

1. Près du coin supérieur droit de l’écran, cliquez sur **Ajouter un jeu de contenu**.

   ![Jeux de contenu](/help/assets/content-sets.png)

1. Dans l’onglet **Détails** de l’assistant, indiquez un nom et une description pour le jeu de contenu, puis cliquez sur **Continuer**.

   ![Détails du jeu de contenu](/help/assets/add-content-set-details.png)

1. Dans l’onglet **Chemins d’accès au contenu** de l’assistant, indiquez les chemins d’accès au contenu modifiable à inclure dans le jeu de contenu.

   1. Entrez le chemin dans le champ **Ajouter un chemin d’accès à inclure**.
   1. Cliquez sur **Ajouter un chemin** pour ajouter le chemin d’accès au jeu de contenu.
   1. Le cas échéant, cliquez de nouveau sur **Ajouter un chemin**.

   ![Ajouter des chemins à un jeu de contenu](/help/assets/add-content-set-paths.png)

1. Si vous devez affiner ou limiter votre jeu de contenu, les sous-chemins peuvent être exclus.

   1. Dans la liste des chemins inclus, cliquez sur l’icône **Ajouter des sous-chemins d’exclusion** en regard du chemin que vous devez restreindre.
   1. Saisissez le sous-chemin à exclure du chemin sélectionné.
   1. Cliquez sur **Exclure le chemin**.
   1. Cliquez de nouveau sur **Ajouter des sous-chemins d’exclusion** pour ajouter des chemins d’accès supplémentaires à exclure, si nécessaire.

   ![Exclusion de chemins](/help/assets/add-content-set-paths-excluded.png)

1. Vous pouvez modifier les chemins spécifiés si nécessaire.

   1. Cliquez sur le `X` en regard des sous-chemins exclus pour les supprimer.
   1. Cliquez sur le bouton représentant des points de suspension en regard des chemins pour afficher les options **Edit** et **Delete** .

   ![Modification de la liste de chemins](/help/assets/add-content-set-excluded-paths.png)

1. Cliquez sur **Créer** pour créer le jeu de contenu.

Le jeu de contenu peut désormais être utilisé pour copier du contenu entre des environnements.

>[!NOTE]
>
>Vous pouvez ajouter jusqu’à 50 chemins dans un jeu de contenu.
>Il n’existe aucune limitation sur les chemins exclus.

## Editer un jeu de contenu {#edit-content-set}

Procédez de la même façon que lors de la création d’une étape de contenu. Au lieu de cliquer sur **Ajouter un jeu de contenu**, sélectionnez un jeu existant dans la console et sélectionnez **Modifier** dans le menu de points de suspension.

![Modifier le jeu de contenu](/help/assets/edit-content-set.png)

Lors de la modification de votre jeu de contenu, vous devrez peut-être développer les chemins configurés pour que s’affichent les sous-chemins exclus.

## Copier le contenu {#copy-content}

Une fois qu’un jeu de contenu a été créé, vous pouvez l’utiliser pour copier du contenu. Pour copier du contenu, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Overview** , accédez à l’écran **Environments** (Environnements).

1. Dans l’écran **Environments** (Environnements), accédez à la page **Content Sets** (Visionneuses de contenu).

1. Sélectionnez un jeu de contenu dans la console, puis **Copier le contenu** dans le menu représentant des points de suspension.

   ![Copier le contenu](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Un environnement ne peut pas être sélectionné si :
   >
   >* L’utilisateur ne dispose pas des autorisations appropriées.
   >* Un pipeline en cours d’exécution ou une opération de copie de contenu est en cours dans l’environnement.

1. Dans la boîte de dialogue **Copier le contenu**, spécifiez les environnements source et de destination pour votre action de copie de contenu.
   * Les régions de l&#39;environnement-cible doivent être identiques ou un sous-ensemble des régions de l&#39;environnement-source.

1. Vous pouvez choisir de supprimer ou de conserver les chemins d’exclusion dans l’environnement de destination. Cochez la case `Do not delete exclude paths from destination` pour conserver les `exclude paths` spécifiés dans le jeu de contenu. Si la case est décochée, les chemins d’exclusion sont supprimés dans l’environnement cible.

1. Vous pouvez choisir de copier l’historique des versions des chemins copiés de la source vers l’environnement de destination. Cochez la case `Copy Versions` si vous souhaitez copier tous les historiques de versions.

   ![Copie de contenu](/help/assets/copying-content.png)

1. Cliquez sur **Copier**.

Le processus de copie démarre. Le statut du processus de copie est répercuté dans la console pour le jeu de contenu sélectionné.

## Activité Copie de contenu {#copy-activity}

Vous pouvez surveiller le statut de vos processus de copie à la page **Activité de copie de contenu**.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/), puis sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Overview** , accédez à l’écran **Environments** (Environnements).

1. Dans l’écran **Environments** (Environnements), accédez à la page **Copier l’activité de contenu**.

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
* La copie de contenu ne peut être effectuée que dans le même niveau. En d’autres termes, auteur-auteur ou publication-publication.
* Une copie de contenu ne peut pas être effectuée sur plusieurs programmes et plusieurs régions.
* La copie de contenu pour la topologie basée sur l’entrepôt de données cloud ne peut être effectuée que lorsque l’environnement source et de destination se trouve sur le même fournisseur cloud et dans la même région.
* L’exécution simultanée d’opérations de copie de contenu dans le même environnement n’est pas possible.
* La copie de contenu ne peut pas être effectuée si une opération active est en cours d’exécution dans l’environnement de destination ou source, tel qu’un pipeline CI/CD.
* Vous pouvez spécifier jusqu’à cinquante chemins par jeu de contenu. Il n’existe aucune limitation sur les chemins exclus.
* L’outil de copie de contenu ne doit pas être utilisé comme outil de clonage ou de mise en miroir, car il ne peut pas effectuer le suivi du contenu déplacé ou supprimé sur la source.
* Une copie de contenu ne peut pas être suspendue ou annulée une fois qu’elle est lancée.
* L’outil de copie de contenu copie les ressources et les métadonnées Dynamic Media de l’environnement supérieur vers l’environnement inférieur sélectionné. Les ressources copiées doivent ensuite être retraitées à l’aide du [workflow Ressources de processus de gestion des actifs numériques](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/using/assets-workflow) sur l’environnement inférieur pour utiliser la configuration Dynamic Media correspondante.
* Le processus de copie de contenu est beaucoup plus rapide lorsque l’historique des versions n’est pas copié.
* [Les configurations Dynamic Media avec des ressources dont la taille est supérieure à 2 Go activées](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) ne sont pas prises en charge.
* Lorsque l’historique de version n’est pas copié, le processus de copie de contenu est sensiblement plus rapide.
* Les régions de l&#39;environnement-cible doivent être identiques ou un sous-ensemble des régions de l&#39;environnement-source.

## Problèmes connus {#known-issues}

{{content-copy-known-issues}}
