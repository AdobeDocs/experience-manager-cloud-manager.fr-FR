---
title: Ajouter des référentiels privés dans Cloud Manager
description: Découvrez comment configurer Cloud Manager pour utiliser vos propres référentiels GitHub privés.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 93%

---


# Ajouter des référentiels privés dans Cloud Manager {#private-repositories}

Découvrez comment configurer Cloud Manager pour utiliser vos propres référentiels GitHub privés.

## Vue d’ensemble {#overview}

La configuration de Cloud Manager avec vos référentiels GitHub privés vous permet de valider le code directement dans GitHub, éliminant ainsi la nécessité de se synchroniser fréquemment avec le référentiel Adobe.

>[!NOTE]
>
>Cette fonctionnalité est réservée au GitHub public. La prise en charge du GitHub auto-hébergé n’est pas disponible.

## Configuration {#configuration}

La configuration se compose de deux étapes principales :

1. [Ajouter un référentiel](#add-repo)
1. [Validation de la propriété du référentiel privé](#validate-ownership)



### Ajouter un référentiel {#add-repo}

1. Dans Cloud Manager, dans la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Référentiels** pour basculer vers la page **Référentiels** et cliquez sur **Ajouter un référentiel**.

1. Dans la boîte de dialogue **Ajouter un référentiel**, sélectionnez **Référentiel privé** comme type de référentiel.

1. Fournir des détails de votre référentiel

   * **Nom du référentiel** : un nom expressif.
   * **URL du référentiel** : l’URL du référentiel, qui doit se terminer par `.git`.
   * **Description** (facultatif) : une description plus longue du référentiel selon les besoins.

   ![Ajout de votre propre référentiel.](/help/assets/repositories/add-own-github.png)

1. Cliquez sur **Enregistrer**.

>[!TIP]
>
>Pour plus d’informations sur la gestion des référentiels dans Cloud Manager, consultez le document [Référentiels Cloud Manager](/help/managing-code/managing-repositories.md).



### Validation de la propriété d’un référentiel privé {#validate-ownership}

Cloud Manager connaît désormais votre référentiel GitHub, mais il doit toujours y accéder. Pour accorder l’accès, vous devez installer l’application GitHub d’Adobe et vérifier que vous êtes propriétaire du référentiel spécifié.

1. Lorsque vous avez ajouté votre propre référentiel, la boîte de dialogue **Validation de la propriété du référentiel privé** s’ouvre.

   ![Validation de la propriété du référentiel privé.](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager utilise une application GitHub pour interagir de manière sécurisée avec votre référentiel.

   Une personne propriétaire de votre organisation GitHub doit installer l’application qui se trouve à l’adresse `https://github.com/apps/cloud-manager-for-aem` et accorder l’accès au référentiel. Consultez la documentation GitHub pour plus de détails.

1. Pour renforcer la sécurité, vous devez créer un fichier secret dans la branche par défaut de votre référentiel. Cliquez sur **Générer**.

1. Confirmez la génération du fichier secret en cliquant sur **Confirmer**.

   ![Confirmation de la génération du secret](/help/assets/repositories/confirm-generation.png)

1. Dans la boîte de dialogue **Validation de la propriété du référentiel privé**, Cloud Manager a généré le contenu dans le champ **Contenu du fichier secret**. Copiez le contenu de ce champ.

   Le contenu du fichier secret ne s’affichera qu’une seule fois. Si vous ne copiez pas le contenu avant de fermer cette fenêtre, vous devrez générer le secret à nouveau.

   ![Copie du contenu du fichier secret.](/help/assets/repositories/new-secret.png)

1. Créez un fichier dans la branche par défaut de votre référentiel GitHub appelé `.well-known/adobe/cloud-manager-challenge`, collez le contenu du fichier secret dans ce fichier et enregistrez-le.

1. Une fois que l’application est installée et que le fichier secret existe dans le référentiel, vous pouvez cliquer sur **Valider** dans la boîte de dialogue **Validation de la propriété du référentiel privé**.

L’application peut être installée et vous pouvez générer un fichier secret dans n’importe quel ordre. Toutefois, vous devez effectuer les deux étapes avant de pouvoir valider.

Jusqu’à la validation, le référentiel est répertorié avec une icône rouge indiquant qu’il n’est pas encore validé et qu’il ne peut pas encore être utilisé.

![Référentiel non validé.](/help/assets/repositories/unvalidated-repo.png)

Notez que la colonne **Type** permet d’identifier facilement les référentiels fournis par Adobe (**Adobe**) et vos propres référentiels GitHub (**GitHub**).

Pour revenir au référentiel ultérieurement et terminer la validation, accédez à la page **Référentiels**. Cliquez sur ![Icône Plus, points de suspension](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard du référentiel GitHub que vous avez ajouté, puis cliquez sur **Validation de la propriété**.


## Utiliser des référentiels privés avec Cloud Manager {#using}

Une fois le référentiel GitHub validé dans Cloud Manager, l’intégration est terminée et vous pouvez utiliser le référentiel avec Cloud Manager.

**Pour utiliser des référentiels privés avec Cloud Manager :**

1. Lorsque vous créez une demande d’extraction, une vérification GitHub démarre automatiquement.

   ![Vérifications GitHub](/help/assets/repositories/github-checks.png)

1. Un [pipeline de qualité de code de pile pleine](/help/using/managing-pipelines.md) est créé automatiquement pour chaque demande d’extraction. Ce pipeline démarre à chaque mise à jour de demande d’extraction.

1. La vérification GitHub reste en cours d’exécution jusqu’à ce que les vérifications de qualité du code soient terminées. Les résultats de la qualité du code sont ensuite propagés à la vérification GitHub.

   ![Vérifications de la qualité du code GitHub.](/help/assets/repositories/github-code-quality.png)

Lorsque la demande d’extraction est fermée ou fusionnée, le pipeline de qualité de code de pile pleine créé est automatiquement supprimé.

>[!TIP]
>
>Consultez le document [Annotations de vérification GitHub](github-annotations.md) pour plus de détails sur les informations fournies par GitHub lors de l’exécution des vérifications des requêtes d’extraction.

>[!TIP]
>
>Vous pouvez contrôler les pipelines créés automatiquement pour valider chaque requête d’extraction dans un référentiel privé. Consultez le document [Configuration de la vérification GitHub pour les référentiels privés](github-check-config.md) pour plus d’informations.



## Associer des référentiels privés à des pipelines {#pipelines}

Les référentiels privés validés peuvent être associés à des [pipelines full-stack et front-end.](/help/overview/ci-cd-pipelines.md).



## Limites {#limitations}

Certaines limites s’appliquent lors de l’utilisation de référentiels privés avec Cloud Manager.

* Les pipelines de niveau web et de configuration ne sont pas pris en charge pour les référentiels privés.
* Aucune balise Git ne sera créée et transmise lors de l’utilisation de référentiels privés sur des pipelines de pile pleine de production.
* Si l’application GitHub d’Adobe est supprimée de votre organisation GitHub, la fonctionnalité de validation des demandes d’extraction est supprimée pour tous les référentiels.
* Les pipelines qui utilisent des référentiels privés et le déclencheur de build non validé ne sont pas démarrés automatiquement lorsqu’une nouvelle validation est poussée dans la branche sélectionnée.
* La [fonctionnalité de réutilisation des artefacts](/help/getting-started/project-setup.md#build-artifact-reuse) ne s’applique pas aux référentiels privés.
* Vous ne pouvez pas suspendre la validation de la demande d’extraction à l’aide de la vérification GitHub à partir de Cloud Manager. Si le référentiel GitHub est validé dans Cloud Manager, ce dernier tente toujours de valider les demandes d’extraction créées pour ce référentiel.
