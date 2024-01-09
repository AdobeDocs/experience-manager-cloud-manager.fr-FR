---
title: Utiliser vos propres référentiels GitHub dans Cloud Manager
description: Découvrez comment configurer Cloud Manager pour qu’il fonctionne avec vos propres référentiels GitHub.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: 3bb59686a3c25e47e5c747bb8d5f626055e54a06
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 100%

---


# Utiliser vos propres référentiels GitHub dans Cloud Manager {#byo-github}

En configurant Cloud Manager pour qu’il fonctionne avec vos propres référentiels GitHub, vous pouvez valider votre code directement dans votre référentiel GitHub via Cloud Manager, rendant ainsi inutile la synchronisation cohérente de votre code avec le référentiel Adobe.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour le [programme d’adoption précoce.](/help/release-notes/current.md#early-adoption)

## Configuration {#configuration}

La configuration se compose de deux étapes principales :

1. [Ajout d’un référentiel](#add-repo)
1. [Validation de la propriété du référentiel privé](#validate-ownership)

### Ajouter un référentiel {#add-repo}

1. Dans Cloud Manager, dans la page **Vue d’ensemble du programme**, appuyez ou cliquez sur l’onglet **Référentiels** pour basculer vers la page **Référentiels** et cliquez sur **Ajouter un référentiel**.

1. Dans la boîte de dialogue **Ajouter un référentiel**, sélectionnez **Référentiel privé** comme type de référentiel.

1. Fournir des détails de votre référentiel

   * **Nom du référentiel** : un nom expressif.
   * **URL du référentiel** : l’URL du référentiel, qui doit se terminer par `.git`.
   * **Description** (facultatif) : une description plus longue du référentiel selon les besoins.

   ![Ajout de votre propre référentiel.](/help/assets/repositories/add-own-github.png)

1. Cliquez ou appuyez sur **Enregistrer**.

>[!TIP]
>
>Pour plus d’informations sur la gestion des référentiels dans Cloud Manager, consultez le document [Référentiels Cloud Manager.](/help/managing-code/repositories.md)

### Valider la propriété du référentiel privé {#validate-ownership}

Cloud Manager connaît désormais votre référentiel GitHub, mais il doit toujours y accéder. Pour accorder l’accès, vous devez installer l’application GitHub d’Adobe et vérifier que vous êtes propriétaire du référentiel spécifié.

1. Après avoir ajouté votre propre référentiel, la boîte de dialogue **Validation de la propriété du référentiel privé** s’ouvre.

   ![Validation de la propriété du référentiel privé.](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager utilise une application GitHub pour interagir de manière sécurisée avec votre référentiel.
   * Une personne propriétaire de votre organisation GitHub doit installer l’application qui se trouve à l’adresse `https://github.com/apps/cloud-manager-for-aem` et accordez l’accès au référentiel.
   * Reportez-vous à la documentation de GitHub pour plus d’informations sur la procédure à suivre.

1. Pour renforcer la sécurité, vous devez créer un fichier secret dans la branche par défaut de votre référentiel. Appuyez ou cliquez sur **Générer**.

1. Confirmez la génération du fichier secret en appuyant ou en cliquant sur **Confirmer**.

   ![Confirmation de la génération du secret.](/help/assets/repositories/confirm-generation.png)

1. De retour dans la fenêtre **Validation de la propriété du référentiel privé**, Cloud Manager a généré le contenu du fichier privé dans le champ **Contenu du fichier secret**. Copiez le contenu de ce champ.

   * Le contenu du fichier secret ne s’affichera qu’une seule fois. Si vous ne copiez pas le contenu avant de fermer cette fenêtre, vous devrez générer le secret à nouveau.

   ![Copie du contenu du fichier secret.](/help/assets/repositories/new-secret.png)

1. Créez un fichier dans la branche par défaut de votre référentiel GitHub appelé `.well-known/adobe/cloud-manager-challenge`, collez le contenu du fichier secret dans ce fichier et enregistrez-le.

1. Une fois que l’application est installée et que le fichier secret existe dans le référentiel, vous pouvez appuyer ou cliquer sur **Valider** dans la boîte de dialogue **Validation de la propriété du référentiel privé**.

L’application peut être installée et un fichier secret peut être créé dans n’importe quel ordre. Toutefois, vous devez effectuer les deux étapes avant de pouvoir valider.

Jusqu’à la validation, le référentiel est répertorié avec une icône rouge indiquant qu’il n’est pas encore validé et qu’il ne peut pas encore être utilisé.

![Référentiel non validé.](/help/assets/repositories/unvalidated-repo.png)

Notez que la colonne **Type** permet d’identifier facilement les référentiels fournis par Adobe (**Adobe**) et vos propres référentiels GitHub (**GitHub**).

Si vous devez revenir au référentiel à une date ultérieure pour terminer la validation, sur la page **Référentiels**, appuyez ou cliquez sur le bouton représentant des points de suspension dans la ligne représentant le référentiel GitHub que vous venez d’ajouter et sélectionnez **Validation de propriété** dans le menu déroulant.

## Utiliser vos propres référentiels GitHub avec Cloud Manager {#using}

Une fois le référentiel GitHub validé dans Cloud Manager, l’intégration est terminée et vous pouvez utiliser le référentiel avec Cloud Manager.

1. Lorsque vous créez une demande d’extraction, une vérification GitHub démarre automatiquement.

   ![Vérifications GitHub.](/help/assets/repositories/github-checks.png)

1. Un [pipeline de qualité de code de pile pleine](/help/using/managing-pipelines.md) est créé automatiquement pour chaque demande d’extraction. Ce pipeline démarre à chaque mise à jour de demande d’extraction.

1. La vérification GitHub reste à l’état d’exécution jusqu’à ce que les vérifications de la qualité du code soient terminées. Les résultats de la qualité du code sont ensuite propagés à la vérification GitHub.

   ![Vérifications de la qualité du code GitHub.](/help/assets/repositories/github-code-quality.png)

Lorsque la demande d’extraction est fermée ou fusionnée, le pipeline de qualité de code de pile pleine créé est automatiquement supprimé.

## Limites {#limitations}

Gardez à l’esprit les limites suivantes lorsque vous utilisez vos propres référentiels GitHub avec Cloud Manager.

* Vous ne pouvez pas utiliser les référentiels GitHub comme source directe de référentiel pour les pipelines que vous gérez.
   * Cette fonctionnalité est prévue.
* Vous ne pouvez pas suspendre la validation de la demande d’extraction à l’aide de la vérification GitHub à partir de Cloud Manager.
   * Si le référentiel GitHub est validé dans Cloud Manager, ce dernier tente toujours de valider les demandes d’extraction créées pour ce référentiel.
Si l’application GitHub d’Adobe est supprimée de votre organisation GitHub, la fonctionnalité de validation des demandes d’extraction est supprimée pour tous les référentiels.
