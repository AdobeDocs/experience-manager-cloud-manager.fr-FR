---
title: Copie de contenu pour la cohérence de l’environnement
description: La copie de contenu dans Cloud Manager permet aux utilisateurs de copier du contenu modifiable à la demande à partir des environnements de production Adobe Experience Manager 6.x hébergés par Adobe Managed Services dans des environnements inférieurs pour les tests.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 16cc1aa0ff45126df9100f337b6259a3f248038f
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 34%

---


# Copie de contenu pour assurer la cohérence de l’environnement {#content-copy}

La copie de contenu dans Cloud Manager permet aux utilisateurs de copier du contenu modifiable à la demande à partir des environnements de production Adobe Experience Manager 6.x hébergés par Adobe Managed Services dans des environnements inférieurs pour les tests.

## À propos de la copie de contenu {#introduction}

Les données actuelles et réelles sont utiles à des fins de test, de validation et d’acceptation par l’utilisateur. La copie de contenu vous permet de copier du contenu de votre environnement d’AEM hébergé en production AMS 6.x vers des environnements d’évaluation ou de développement. Ce workflow prend en charge divers scénarios de test.

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

### Autorisations {#permissions}

Pour utiliser la fonction Copie de contenu, l’utilisateur doit être affecté au rôle **Gestionnaire de déploiement** dans les environnements source et cible.

## Création d’un jeu de contenu {#create-content-set}

Pour qu’un contenu puisse être copié, un jeu de contenu doit être défini. Une fois définis, les jeux de contenu peuvent être réutilisés pour copier du contenu. Pour créer un jeu de contenu, suivez la procédure décrite ci-après.

**Pour créer un jeu de contenu :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour ouvrir le menu de gauche.

1. Dans le menu de gauche, sous la page **Services**, cliquez sur l’icône ![ ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Visionneuses de contenu**.

1. Près du coin supérieur droit de la page, cliquez sur **Ajouter un jeu de contenu**.

   ![Jeux de contenu](/help/assets/content-sets.png)

1. Dans la boîte de dialogue **`Add Content Set`**, dans l’onglet **Détails**, dans les champs **Nom** et **Description**, saisissez un nom et une description facultative du jeu de contenu, puis cliquez sur **Continuer**.

   ![Détails du jeu de contenu](/help/assets/add-content-set-details.png)

1. Sur l’onglet **Chemins d’accès au contenu**, dans le champ de texte **Chemin**, spécifiez un chemin d’accès au contenu qui peut être modifié et qui doit être inclus dans le jeu de contenu.

   Seuls les chemins commençant par `/content`, `/conf`, `/etc`, `/var/workflow/models` ou `/var/commerce` peuvent être inclus.

1. Cliquez sur **![Icône d’ajout de dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) Ajouter chemin** pour ajouter (ou inclure) le chemin d’accès au jeu de contenu.

1. (Facultatif) Si nécessaire, ajoutez des chemins d’accès supplémentaires (jusqu’à 50) si nécessaire en répétant les deux étapes précédentes. Sinon, passez à l’étape suivante.

   ![Ajouter des chemins à un jeu de contenu](/help/assets/add-content-set-paths.png)

1. (Facultatif) Pour réduire votre jeu de contenu, vous pouvez éventuellement spécifier des sous-chemins dans un chemin de contenu inclus qui doit être exclu.

   1. À droite d’un chemin de contenu inclus que vous souhaitez restreindre, cliquez sur ![Icône de suppression de dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg).
   1. Dans le champ de texte, saisissez un chemin relatif au chemin racine affiché dans la boîte de dialogue.
   1. Cliquez sur ![Icône de suppression de dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **Exclure le chemin**.
   1. Si nécessaire, répétez les étapes i à iii. ci-dessus pour ajouter d’autres chemins d’exclusion ; il n’y a aucune limitation. Sinon, passez à l’étape suivante.

   ![Exclusion de chemins](/help/assets/add-content-set-paths-excluded.png)

1. (En option) Effectuez l’une des actions suivantes :

   1. Cliquez sur ![Icône Cross size 500](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) à droite d’un sous-chemin exclu pour le supprimer.
   1. Cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/ui_18/More.svg) à droite d’un chemin de contenu inclus, puis cliquez sur **Edit** ou **Delete**.

   ![Modifier la liste de chemins](/help/assets/add-content-set-excluded-paths.png)

1. Cliquez sur **Créer**. Vous pouvez désormais utiliser le jeu de contenu pour copier du contenu entre les environnements.

## Modification ou suppression d’un jeu de contenu {#edit-content-set}

Lorsque vous modifiez un jeu de contenu, vous devrez peut-être développer les chemins configurés pour afficher les sous-chemins exclus.

**Pour modifier ou supprimer un jeu de contenu :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour ouvrir le menu de gauche.

1. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône de boîte ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Visionneuses de contenu**.

1. Dans le tableau de la page **Visionneuses de contenu**, cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/ui_18/More.svg) à droite d’un chemin de contenu inclus, puis cliquez sur **Modifier** ou **Supprimer**.

![Modifier le jeu de contenu](/help/assets/edit-content-set.png)


## Copier le contenu {#copy-content}

Une fois un jeu de contenu créé, vous pouvez l’utiliser pour copier du contenu.

Un environnement peut ne pas être sélectionné si l’une des conditions suivantes s’applique :

* L’utilisateur ne dispose pas des autorisations requises.
* Une opération de pipeline ou de copie de contenu est en cours d’exécution dans l’environnement.

**Pour copier du contenu :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour ouvrir le menu de gauche.

1. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône de boîte ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Visionneuses de contenu**.

1. Dans le tableau de la page **Visionneuses de contenu**, à droite d’un chemin de contenu inclus que vous souhaitez copier, cliquez sur ![Icône Plus](https://spectrum.adobe.com/static/icons/ui_18/More.svg), puis sur **Copier le contenu**.

   ![Copier le contenu](/help/assets/copy-content.png)

1. Dans la boîte de dialogue **Copier le contenu**, sélectionnez l’environnement **Source** et l’environnement **Destination** pour votre action de copie de contenu.

   * Les régions d’un environnement de destination doivent être un sous-ensemble de régions d’un environnement source.
   * Les problèmes de compatibilité sont vérifiés avant d’exécuter une action de copie de contenu. Lorsque vous sélectionnez l’environnement **Destination**, le système valide automatiquement les environnements source et de destination. Si la validation échoue, le processus s’arrête et un message d’erreur s’affiche dans la boîte de dialogue pour expliquer la raison de l’échec.

     ![Copier du contenu](/help/assets/copying-content.png)

1. (Facultatif) Effectuez l’une des opérations suivantes :

   1. Pour *conserver* les chemins exclus dans l’environnement de destination, cochez la case **`Do not delete exclude paths from destination`**. Ce paramètre préserve les chemins d’accès exclus spécifiés dans le jeu de contenu.
   1. Pour *supprimer* les chemins exclus dans l’environnement de destination, désélectionnez **`Do not delete exclude paths from destination`**. Ce paramètre supprime les chemins exclus spécifiés dans le jeu de contenu.
   1. Pour copier l’historique des versions des chemins de l’environnement source vers l’environnement de destination, cochez la case **Copier les versions**. Le processus de copie de contenu est beaucoup plus rapide lorsque l’historique de version est *et non* copié.



1. Cliquez sur **Copier**. Le statut du processus de copie est répercuté dans la console pour le jeu de contenu sélectionné.

## Vérification de l’état d’une copie de contenu {#copy-activity}

Vous pouvez surveiller le statut de vos processus de copie à la page **Activité de copie de contenu**.

**Pour vérifier l’état d’une copie de contenu :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour ouvrir le menu de gauche.

1. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône Historique ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **Copier l’activité de contenu**.

   ![Activité de copie de contenu](/help/assets/copy-content-activity.png)

   Un processus de copie de contenu peut avoir l’un des états suivants :

   | État | Description |
   | --- | --- |
   | En cours | L’opération de copie de contenu est en cours. |
   | Terminé | L’opération de copie de contenu s’est terminée avec succès. |
   | Échec | L’opération de copie de contenu a échoué. |


## Limites de la copie de contenu {#limitations}

* Une copie de contenu ne peut pas être effectuée d’un environnement inférieur vers un environnement supérieur.
* Une copie de contenu ne peut être effectuée que dans le même niveau. En d’autres termes, création-création ou publication-publication.
* Une copie de contenu ne peut pas être effectuée sur plusieurs programmes et plusieurs régions.
* La copie de contenu pour la topologie basée sur le magasin de données cloud ne peut être effectuée que lorsque les environnements source et de destination se trouvent sur le même fournisseur de services cloud et dans la même région.
* L’exécution simultanée d’opérations de copie de contenu sur le même environnement n’est pas possible.
* Une copie de contenu ne peut pas être effectuée si une opération active est en cours d’exécution dans l’environnement de destination ou l’environnement source, tel qu’un pipeline CI/CD.
* La copie de contenu ne doit pas être utilisée comme outil de clonage ou de mise en miroir, car elle ne peut pas suivre le contenu déplacé ou supprimé de la source.
* Une copie de contenu ne peut pas être suspendue ou annulée une fois qu’elle est lancée.
* La copie de contenu duplique les ressources et les métadonnées Dynamic Media de l’environnement supérieur vers l’environnement inférieur sélectionné. Les ressources copiées doivent ensuite être retraitées à l’aide du [workflow Ressources de traitement de la gestion des ressources numériques](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/using/assets-workflow) dans l’environnement inférieur, afin d’utiliser la configuration de Dynamic Media correspondante.
* [Les configurations Dynamic Media avec des ressources dont la taille est supérieure à 2 Go activées](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) ne sont pas prises en charge.
* Les régions de l’environnement cible doivent être identiques aux régions de l’environnement source ou en être un sous-ensemble.

## Problèmes connus de la copie de contenu {#known-issues}

{{content-copy-known-issues}}
