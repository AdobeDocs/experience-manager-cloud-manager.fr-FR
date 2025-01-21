---
title: Copie de contenu pour la cohérence de l’environnement
description: La copie de contenu dans Cloud Manager permet de copier du contenu modifiable à la demande à partir des environnements de production Adobe Experience Manager 6.x hébergés par Adobe Managed Services dans des environnements inférieurs pour les tests.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 84b3366481c2efd497583627eac67046452f6c38
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 98%

---


# Copie de contenu pour la cohérence de l’environnement {#content-copy}

La copie de contenu dans Cloud Manager permet de copier du contenu modifiable à la demande à partir des environnements de production Adobe Experience Manager 6.x hébergés par Adobe Managed Services dans des environnements inférieurs pour les tests.

## À propos de la copie de contenu {#introduction}

Les données actuelles et réelles sont utiles à des fins de test, de validation et d’acceptation par l’utilisateur ou l’utilisatrice. La copie de contenu permet de copier du contenu de votre environnement de production AEM 6.x hébergé par AMS vers un environnement d’évaluation ou de développement. Ce workflow prend en charge divers scénarios de test.

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

Si vous modifiez du contenu dans l’environnement de destination, le contenu source le remplace si les chemins correspondent.

Si les chemins d’accès sont différents, le contenu de la source est fusionné avec le contenu de la destination.

### Autorisations {#permissions}

Pour utiliser la copie de contenu, le rôle **Responsable de déploiement** doit être affecté à l’utilisateur ou à l’utilisatrice dans les environnements source et cible.

## Créer un ensemble de contenu {#create-content-set}

Pour qu’un contenu puisse être copié, un jeu de contenu doit être défini. Une fois définis, les jeux de contenu peuvent être réutilisés pour copier du contenu. Pour créer un jeu de contenu, suivez la procédure décrite ci-après.

**Pour créer un ensemble de contenu :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour ouvrir le menu de gauche.

1. Dans le menu de gauche, sous la page **Services**, cliquez sur ![Icône de boîte](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Ensembles de contenu**.

1. Près du coin supérieur droit de la page, cliquez sur **Ajouter un ensemble de contenu**.

   ![Jeux de contenu](/help/assets/content-sets.png)

1. Dans la boîte de dialogue **`Add Content Set`**, dans l’onglet **Détails**, dans les champs **Nom** et **Description**, saisissez un nom et une description facultative de l’ensemble de contenu, puis cliquez sur **Continuer**.

   ![Détails du jeu de contenu](/help/assets/add-content-set-details.png)

1. Dans l’onglet **Chemins d’accès au contenu**, dans le champ de texte **Chemin**, spécifiez un chemin d’accès au contenu qui peut être modifié et qui doit être inclus dans l’ensemble de contenu.

   Seuls les chemins commençant par `/content`, `/conf`, `/etc`, `/var/workflow/models` ou `/var/commerce` peuvent être inclus.

1. Cliquez sur ![Icône d’ajout de dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) **Ajouter un chemin** pour ajouter (ou inclure) le chemin d’accès au jeu de contenu.

1. (Facultatif) Si nécessaire, ajoutez des chemins d’accès supplémentaires (jusqu’à 50) en répétant les deux étapes précédentes. Autrement, passez à l’étape suivante.

   ![Ajouter des chemins à un jeu de contenu](/help/assets/add-content-set-paths.png)

1. (Facultatif) Pour réduire votre ensemble de contenu, vous pouvez éventuellement spécifier des sous-chemins dans un chemin de contenu inclus qui doit être exclu.

   1. À droite d’un chemin de contenu inclus que vous souhaitez restreindre, cliquez sur ![icône de suppression de dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg).
   1. Dans le champ de texte, saisissez un chemin relatif au chemin racine affiché dans la boîte de dialogue.
   1. Cliquez sur ![Icône de suppression de dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **Exclure le chemin**.
   1. Si nécessaire, répétez les étapes i à iii. ci-dessus pour ajouter d’autres chemins d’exclusion. Il n’y a aucune limitation. Autrement, passez à l’étape suivante.

   ![Exclusion de chemins](/help/assets/add-content-set-paths-excluded.png)

1. (En option) Effectuez l’une des actions suivantes :

   1. Cliquez sur ![Icône en forme de croix](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) à droite d’un sous-chemin exclu pour le supprimer.
   1. Cliquez sur ![Icône Plus](https://spectrum.adobe.com/static/icons/ui_18/More.svg) à droite d’un chemin de contenu inclus, puis cliquez sur **Modifier** ou **Supprimer**.

   ![Modifier la liste de chemins](/help/assets/add-content-set-excluded-paths.png)

1. Cliquez sur **Créer**. Vous pouvez désormais utiliser l’ensemble de contenu pour copier du contenu entre les environnements.

## Modifier ou supprimer un ensemble de contenu {#edit-content-set}

Lors de la modification de votre ensemble de contenu, vous devrez peut-être développer les chemins configurés pour que s’affichent les sous-chemins exclus.

**Pour modifier ou supprimer un ensemble de contenu**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour ouvrir le menu de gauche.

1. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône de boîte](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Ensembles de contenu**.

1. Dans le tableau de la page **Ensembles de contenu**, cliquez sur ![Icône Plus](https://spectrum.adobe.com/static/icons/ui_18/More.svg) à droite d’un chemin de contenu inclus, puis cliquez sur **Modifier** ou **Supprimer**.

![Modifier l’ensemble de contenu](/help/assets/edit-content-set.png)

## Copier le contenu {#copy-content}

Une fois qu’un ensemble de contenu a été créé, vous pouvez l’utiliser pour copier du contenu.

Un environnement peut ne pas être sélectionné si l’une des conditions suivantes s’applique :

* La personne ne dispose pas des autorisations requises.
* Une opération de pipeline ou de copie de contenu est en cours d’exécution dans l’environnement.

**Pour copier du contenu :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour ouvrir le menu de gauche.

1. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône de boîte](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Ensembles de contenu**.

1. Dans le tableau de la page **Ensembles de contenu**, à droite d’un chemin de contenu inclus que vous souhaitez copier, cliquez sur ![Icône Plus](https://spectrum.adobe.com/static/icons/ui_18/More.svg), puis sur **Copier le contenu**.

   ![Copier le contenu](/help/assets/copy-content.png)

1. Dans la boîte de dialogue **Copier le contenu**, spécifiez les environnements de **source** et de **destination** de votre action de copie de contenu.

   * Les régions de l’environnement de destination doivent être un sous-ensemble des régions de l’environnement source.
   * Les problèmes de compatibilité sont vérifiés avant d’exécuter une action de copie de contenu. Lorsque vous sélectionnez l’environnement de **destination**, le système valide automatiquement les environnements source et de destination. Si la validation échoue, le processus s’arrête et un message d’erreur s’affiche dans la boîte de dialogue pour expliquer la raison de l’échec.

     ![Copier du contenu](/help/assets/copying-content.png)

1. (Facultatif) Effectuez l’une des opérations suivantes :

   1. Pour *conserver* les chemins exclus dans l’environnement de destination, cochez la case **`Do not delete exclude paths from destination`**. Ce paramètre préserve les chemins d’accès exclus spécifiés dans l’ensemble de contenu.
   1. Pour *supprimer* les chemins exclus dans l’environnement de destination, désélectionnez **`Do not delete exclude paths from destination`**. Ce paramètre supprime les chemins exclus spécifiés dans l’ensemble de contenu.
   1. Pour copier l’historique des versions des chemins de l’environnement source vers l’environnement de destination, cochez la case **Copier les versions**. Le processus de copie de contenu est beaucoup plus rapide lorsque l’historique des versions *n’est pas* copié.

1. Cliquez sur **Copier**. Le statut du processus de copie est répercuté dans la console pour l’ensemble de contenu sélectionné.

## Vérifier le statut d’une copie de contenu {#copy-activity}

Vous pouvez surveiller le statut de vos processus de copie à la page **Activité de copie de contenu**.

**Pour vérifier le statut d’une copie de contenu :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour ouvrir le menu de gauche.

1. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône Historique](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **Activité de copie de contenu**.

   ![Activité de copie de contenu](/help/assets/copy-content-activity.png)

   Un processus de copie de contenu peut présenter l’un des statuts suivants :

   | État | Description |
   | --- | --- |
   | En cours | L’opération de copie de contenu est en cours. |
   | Terminé | L’opération de copie de contenu est terminée. |
   | Échec | L’opération de copie de contenu a échoué. |

## Limites de la copie de contenu {#limitations}

* Une copie de contenu ne peut pas être effectuée d’un environnement inférieur vers un environnement supérieur.
* Une copie de contenu ne peut être effectuée que dans le même niveau. En d’autres termes, création-création ou publication-publication.
* Une copie de contenu ne peut pas être effectuée sur plusieurs programmes et plusieurs régions.
* La copie de contenu pour la topologie basée sur le magasin de données cloud ne peut être effectuée que lorsque les environnements source et de destination se trouvent sur le même fournisseur de services cloud et dans la même région.
* L’exécution simultanée d’opérations de copie de contenu sur le même environnement n’est pas possible.
* Une copie de contenu ne peut pas être effectuée si une opération active est en cours d’exécution dans l’environnement de destination ou l’environnement source, tel qu’un pipeline CI/CD.
* La copie de contenu ne doit pas être utilisé comme outil de clonage ou de mise en miroir, car elle ne peut pas effectuer le suivi du contenu déplacé ou supprimé sur la source.
* Une copie de contenu ne peut pas être suspendue ou annulée une fois qu’elle est lancée.
* La copie de contenu copie les ressources avec les métadonnées liées à Dynamic Media, de l’environnement supérieur vers l’environnement inférieur sélectionné. Les ressources copiées doivent ensuite être retraitées à l’aide du [workflow Ressources de traitement de la gestion des ressources numériques](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/using/assets-workflow) dans l’environnement inférieur, afin d’utiliser la configuration de Dynamic Media correspondante.
* [Les configurations Dynamic Media avec des ressources dont la taille est supérieure à 2 Go activées](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) ne sont pas prises en charge.
* Les régions de l’environnement cible doivent être identiques à ou être un sous-ensemble des régions de l’environnement source.

## Problèmes connus de la copie de contenu {#known-issues}

{{content-copy-known-issues}}
