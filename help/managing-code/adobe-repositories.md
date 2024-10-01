---
title: Ajout d’un référentiel d’Adobe dans Cloud Manager
description: Découvrez comment ajouter des référentiels gérés par Adobe dans Cloud Manager.
exl-id: 24c6ca97-ea70-41b8-b4c7-b8b0f406a57d
source-git-commit: 675568426df0df5890dd8c72bfb53c24a4c5d666
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 7%

---

# Ajout d’un référentiel d’Adobe dans Cloud Manager {#adobe-repositories}

Découvrez comment ajouter un référentiel géré par Adobe dans Cloud Manager.

La page **Référentiels** permet d’ajouter facilement des référentiels gérés par Adobe à un programme sélectionné.

**Pour ajouter un référentiel d’Adobe dans Cloud Manager :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée et le programme auquel vous souhaitez ajouter un référentiel géré par Adobe.

1. Sur la page **Aperçu du programme**, dans le menu latéral, cliquez sur l’onglet ![Icône Dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Référentiels** .

1. Sur la page **Référentiels**, près du coin supérieur droit, cliquez sur **Ajouter un référentiel**.

   ![Bouton Ajouter un référentiel](/help/managing-code/assets/repositories-tab.png)

1. Dans la boîte de dialogue **Ajouter un référentiel**, assurez-vous que **Adobe Repository** est sélectionné comme type de référentiel.

1. Dans les champs de texte respectifs, saisissez ce qui suit :

   * **Nom du référentiel** : nom expressif de votre nouveau référentiel.
   * **Aperçu de l’URL du référentiel** - Vous n’avez pas besoin de saisir un chemin d’URL ni de modifier le chemin existant, car l’infrastructure du référentiel est déjà en place et entièrement intégrée et gérée par Adobe.
   * **Description (facultatif)** - Description détaillée du référentiel.

   ![Boîte de dialogue Ajouter un référentiel](/help/managing-code/assets/repository-add-adobe.png)

1. Cliquez sur **Enregistrer**.
Votre nouveau référentiel est affiché dans le tableau de la page **Référentiels**.

Vous pouvez désormais associer un [pipeline CI/CD](/help/overview/ci-cd-pipelines.md) ou le gérer dans la page [**Référentiels**](/help/managing-code/managing-repositories.md).

>[!TIP]
>
>Vous pouvez également ajouter des référentiels GitHub que vous gérez vous-même, en tant que [référentiels privés](/help/managing-code/private-repositories.md).
