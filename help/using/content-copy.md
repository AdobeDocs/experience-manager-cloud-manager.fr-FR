---
title: Outil de copie de contenu
description: L’outil de copie de contenu de Cloud Manager permet aux utilisateurs et utilisatrices de copier du contenu modifiable à la demande à partir de leurs environnements de production AEM 6.x hébergés par AMS vers des environnements inférieurs à des fins de test.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '1144'
ht-degree: 100%

---


# Outil de copie de contenu {#content-copy}

L’outil de copie de contenu de Cloud Manager permet aux utilisateurs et utilisatrices de copier du contenu modifiable à la demande à partir de leurs environnements de production AEM 6.x hébergés par AMS vers des environnements inférieurs à des fins de test.

## Présentation {#introduction}

Les données actuelles et réelles sont utiles à des fins de test, de validation et d’acceptation par l’utilisateur. L’outil de copie de contenu permet de copier du contenu de votre environnement de production AEM 6.x hébergé par AMS vers un environnement d’évaluation ou de développement. Ce workflow prend en charge divers scénarios de test.

Un ensemble de contenu définit le contenu à copier. Un ensemble de contenu comprend une liste de chemins JCR avec le contenu modifiable à copier. Le contenu passe d’un environnement source à un environnement cible. Tout cela a lieu dans le même programme Cloud Manager.

Les chemins d’accès suivants sont autorisés dans un ensemble de contenu :

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

Pour utiliser l’outil de copie de contenu, le rôle **Responsable de déploiement** doit être affecté à l’utilisateur ou à l’utilisatrice dans les environnements source et cible.

## Créer un ensemble de contenu {#create-content-set}

Pour qu’un contenu puisse être copié, un jeu de contenu doit être défini. Une fois définis, les jeux de contenu peuvent être réutilisés pour copier du contenu. Pour créer un jeu de contenu, suivez la procédure décrite ci-après.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans la page **Vue d’ensemble**, accédez à l’écran **Environnements**.

1. Dans l’écran **Environnements**, accédez à la page **Ensembles de contenu**.

1. Dans le coin supérieur droit de l’écran, cliquez sur **Ajouter un ensemble de contenu**.

   ![Jeux de contenu](/help/assets/content-sets.png)

1. Dans l’onglet **Détails** de l’assistant, indiquez le nom et la description de l’ensemble de contenu, puis cliquez sur **Continuer**.

   ![Détails du jeu de contenu](/help/assets/add-content-set-details.png)

1. Dans l’onglet **Chemins d’accès au contenu** de l’assistant, indiquez les chemins d’accès au contenu modifiable à inclure dans le jeu de contenu.

   1. Entrez le chemin dans le champ **Ajouter un chemin d’accès à inclure**.
   1. Cliquez sur **Ajouter un chemin** pour ajouter le chemin d’accès au jeu de contenu.
   1. Le cas échéant, cliquez de nouveau sur **Ajouter un chemin**.

   ![Ajouter des chemins à un jeu de contenu](/help/assets/add-content-set-paths.png)

1. Si vous devez affiner ou limiter votre jeu de contenu, les sous-chemins peuvent être exclus.

   1. Dans la liste des chemins d’accès inclus, cliquez sur l’icône **Ajouter des sous-chemins d’exclusion** à côté du chemin que vous devez limiter.
   1. Saisissez le sous-chemin d’exclusion du chemin d’accès sélectionné.
   1. Cliquez sur **Exclure le chemin**.
   1. Cliquez de nouveau sur **Ajouter des sous-chemins d’exclusion** pour ajouter d’autres chemins à exclure, si nécessaire.

   ![Exclusion de chemins](/help/assets/add-content-set-paths-excluded.png)

1. Vous pouvez modifier les chemins spécifiés si nécessaire.

   1. Cliquez sur le `X` en regard des sous-chemins exclus pour les supprimer.
   1. Cliquez sur le bouton représentant des points de suspension en regard des chemins pour afficher les options **Modifier** et **Supprimer**.

   ![Modifier la liste de chemins](/help/assets/add-content-set-excluded-paths.png)

1. Cliquez sur **Créer** pour créer l’ensemble de contenu.

L’ensemble de contenu peut désormais être utilisé pour copier du contenu entre des environnements.

>[!NOTE]
>
>Vous pouvez ajouter jusqu’à 50 chemins dans un jeu de contenu.
>Il n’existe aucune limitation sur les chemins exclus.

## Modifier un ensemble de contenu {#edit-content-set}

Procédez de la même façon que lors de la création d’une étape de contenu. Au lieu de cliquer sur **Ajouter un ensemble de contenu**, sélectionnez un ensemble existant dans la console, puis sélectionnez **Modifier** dans le menu représentant des points de suspension.

![Modifier le jeu de contenu](/help/assets/edit-content-set.png)

Lors de la modification de votre jeu de contenu, vous devrez peut-être développer les chemins configurés pour que s’affichent les sous-chemins exclus.

## Copier le contenu {#copy-content}

Une fois qu’un jeu de contenu a été créé, vous pouvez l’utiliser pour copier du contenu. Pour copier du contenu, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans la page **Vue d’ensemble**, accédez à l’écran **Environnements**.

1. Dans l’écran **Environnements**, accédez à la page **Ensembles de contenu**.

1. Sélectionnez un jeu de contenu dans la console, puis **Copier le contenu** dans le menu représentant des points de suspension.

   ![Copier le contenu](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Un environnement ne peut pas être sélectionné si :
   >
   >* L’utilisateur ne dispose pas des autorisations appropriées.
   >* Un pipeline en cours d’exécution ou une opération de copie de contenu est en cours dans l’environnement.

1. Dans la boîte de dialogue **Copier le contenu**, spécifiez la source et les environnements de destination de votre action de copie de contenu.
   * Les régions de l’environnement cible doivent être identiques aux régions de l’environnement source ou en être un sous-ensemble.

1. Vous pouvez choisir de supprimer ou de conserver les chemins à exclure dans l’environnement de destination. Cochez la case `Do not delete exclude paths from destination` pour conserver les `exclude paths` spécifiés dans l’ensemble de contenu. Si cette case n’est pas cochée, les chemins d’exclusion sont supprimés dans l’environnement cible.

1. Vous pouvez choisir de copier l’historique des versions des chemins copiés de l’environnement source vers l’environnement de destination. Cochez la case `Copy Versions` si vous souhaitez copier tous les historiques de versions.

   ![Copier du contenu](/help/assets/copying-content.png)

1. Cliquez sur **Copier**.

Le processus de copie démarre. Le statut du processus de copie est répercuté dans la console pour le jeu de contenu sélectionné.

## Activité de copie de contenu {#copy-activity}

Vous pouvez surveiller le statut de vos processus de copie à la page **Activité de copie de contenu**.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans la page **Vue d’ensemble**, accédez à l’écran **Environnements**.

1. Dans l’écran **Environnement**, accédez à la page **Activité de copie de contenu**.

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
* Une copie de contenu ne peut être effectuée que dans le même niveau. En d’autres termes, création-création ou publication-publication.
* Une copie de contenu ne peut pas être effectuée sur plusieurs programmes et plusieurs régions.
* La copie de contenu pour la topologie basée sur le magasin de données cloud ne peut être effectuée que lorsque les environnements source et de destination se trouvent sur le même fournisseur de services cloud et dans la même région.
* L’exécution simultanée d’opérations de copie de contenu sur le même environnement n’est pas possible.
* Une copie de contenu ne peut pas être effectuée si une opération active est en cours d’exécution dans l’environnement de destination ou l’environnement source, tel qu’un pipeline CI/CD.
* Vous pouvez spécifier jusqu’à cinquante chemins par jeu de contenu. Il n’existe aucune limitation sur les chemins exclus.
* L’outil de copie de contenu ne doit pas être utilisé comme outil de clonage ou de mise en miroir, car il ne peut pas effectuer le suivi du contenu déplacé ou supprimé sur la source.
* Une copie de contenu ne peut pas être suspendue ou annulée une fois qu’elle est lancée.
* L’outil de copie de contenu copie les ressources avec les métadonnées liées à Dynamic Media, de l’environnement supérieur vers l’environnement inférieur sélectionné. Les ressources copiées doivent ensuite être retraitées à l’aide du [workflow Ressources de traitement de la gestion des ressources numériques](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/using/assets-workflow) dans l’environnement inférieur, afin d’utiliser la configuration de Dynamic Media correspondante.
* Le processus de copie de contenu est beaucoup plus rapide lorsque l’historique des versions n’est pas copié.
* [Les configurations Dynamic Media avec des ressources dont la taille est supérieure à 2 Go activées](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) ne sont pas prises en charge.
* Lorsque l’historique des versions n’est pas copié, le processus de copie de contenu est sensiblement plus rapide.
* Les régions de l’environnement cible doivent être identiques aux régions de l’environnement source ou en être un sous-ensemble.

## Problèmes connus {#known-issues}

{{content-copy-known-issues}}
