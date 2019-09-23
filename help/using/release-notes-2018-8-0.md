---
title: Notes de mise à jour de la version 2018.8.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2018.8.0
description: Consultez cette page pour plus d’informations sur la mise à jour 2018.8.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la mise à jour 2018.8.0 d’AEM Cloud Manager.
uuid: e8aaba32-89b4-4bc5-b295-09b753252612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 9222ac3b-525e-47c1-b481-ac9d22e3d559
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b

---


# Notes de mise à jour de la version 2018.8.0 {#release-notes-for}

La mise à jour 2018.8.0 de [!UICONTROL Cloud Manager] prend désormais en charge le déclenchement automatique du pipeline CI/CD lors des validations git, ainsi qu’un nouvel assistant pour la création de projets d’application dans git basée sur AEM Project Archetype.

## Date de publication {#release-date}

La date de publication de la mise à jour 2018.8.0 de [!UICONTROL Cloud Manager] est le jeudi 4 octobre 2018.

## Nouveautés {#what-s-new}

* **Configuration du programme** : nouvel assistant pour créer un projet d’application dans git à l’aide d’AEM Project Archetype. Consultez la section [Création d’un projet d’application AEM](create-an-application-project.md) pour en savoir plus.

* **Pipeline CI/CD** : les modifications ci-dessous ont été ajoutées au pipeline CI/CD. Pour en savoir plus, consultez la section [Configuration de votre pipeline CI/CD](configuring-pipeline.md).

   * Ajout du déclencheur Lors des modifications Git qui démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche git configurée.
   * Sur l’écran d’accueil, les cartes sont désormais liées à des sections spécifiques de la page d’exécution du pipeline.
   * La page Activité répertorie désormais la branche spécifique utilisée pour chaque exécution.
   * La page Activité indique désormais la durée en heures et en minutes.
   * La page Exécution du pipeline affiche désormais le nom de version/balise créé pour l’exécution.
   * Mise à jour d’Apache Maven vers la version 3.5.3.

* **Navigation** : les modifications ci-dessous ont été ajoutées à [!UICONTROL Cloud Manager].

   * Le lien Ressources dans la navigation globale donne accès au Runbook dans Sharepoint.
   * Le menu Aide a été réorganisé afin d’inclure plus de contenus spécifiques à [!UICONTROL Cloud Manager].

## Correctifs {#bug-fixes}

* Certains détails de la boîte de dialogue de Test de performance n’étaient pas visibles dans Firefox.
* Les dépassements de délai entre les systèmes internes provoquaient parfois des échecs de déploiement.
* La couleur de l’icône de la page Activité n’était pas correcte pour certaines exécutions de pipeline réussies.
* Dans certains cas, la boîte de dialogue Test de performance répertoriait plusieurs fois la même mesure.
* Si une nouvelle instance était ajoutée après le démarrage du pipeline CI/CD, le déploiement n’était pas exécuté sur l’instance nouvellement créée.

## Problèmes connus {#known-issues}

* Les branches créées à l’aide de l’assistant de projet d’application ne peuvent pas contenir de tirets.
* La barre latérale de notification [!UICONTROL Experience Cloud] peut ne pas charger les notifications de manière cohérente. Toutefois, les notifications sont visibles dans [!UICONTROL Experience Cloud] et, si elles sont configurées, elles sont toujours envoyées par e-mail.

