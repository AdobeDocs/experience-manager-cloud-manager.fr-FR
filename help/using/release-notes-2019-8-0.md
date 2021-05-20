---
title: Notes de mise à jour de la version 2019.8.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.8.0
description: Consultez cette page pour obtenir des informations sur la version 2019.8.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.8.0 d’AEM Cloud Manager.
feature: Informations sur la version
exl-id: 9b3da506-76f1-439f-8de0-a5e2ee88b979
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 100%

---

# Notes de mise à jour de la version 2019.8.0 {#release-notes-for}

La version 2019.8.0 [!UICONTROL de Cloud Manager] prend en charge les modules de contenu créés de manière sélective, améliore les performances des compilations et corrige divers bogues mineurs.

## Date de publication {#release-date}

La date de publication de la mise à jour 2019.8.0 de [!UICONTROL Cloud Manager] est le 19 août 2019.

## Nouveautés {#whats-new}

* Nouvelle interface de ligne de commande pour l’API Cloud Manager, optimisée par l’[interface de ligne de commande Adobe I/O](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* Les packages de contenu spécifiques générés peuvent être déclarés comme ignorés et ne seront pas déployés. Pour plus d’informations, voir [Ignorer les packages de contenu](/help/using/setting-up-project.md#skipping-content-packages).
* Le jeu de dépendances préchargées dans le conteneur de génération a été retravaillé afin d’éviter toute requête réseau inutile.
* Le message sur la page d’aperçu de certains programmes configurés incorrectement a été amélioré.

## Correctifs {#bug-fixes}

* Lors de l’accès aux rapports SLA, l’année par défaut était 2018, et non 2019.
* Pour les noms d’environnement longs, le sélecteur d’environnement dans l’écran Rapports n’augmentait pas correctement la taille.
* La règle de qualité du code ***ConfigAndInstallShouldOnlyContainOsgiNodes*** a généré des faux positifs lors de l’utilisation du composant Sling Rewriter.
* La règle de qualité du code ***ConfigAndInstallShouldOnlyContainOsgiNodes*** a généré des faux positifs pour certaines structures de chemin d’accès peu courantes.
* Les clients de ressources uniquement n’ont peut-être pas toujours été capables de naviguer vers leurs environnements AEM.
* L’affichage de la boîte de dialogue Créer une branche et un projet varie selon le navigateur utilisé.
