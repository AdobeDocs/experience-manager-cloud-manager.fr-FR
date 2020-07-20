---
title: Notes de mise à jour de la version 2019.8.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.8.0
description: Consultez cette page pour obtenir des informations sur la version 2019.8.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.8.0 d’AEM Cloud Manager.
translation-type: ht
source-git-commit: c07e88564dc1419bd0305c9d25173a8e0e1f47cf
workflow-type: ht
source-wordcount: '234'
ht-degree: 100%

---

# Notes de mise à jour de la version 2019.8.0 {#release-notes-for}

La version 2019.8.0 [!UICONTROL de Cloud Manager] prend en charge les modules de contenu créés de manière sélective, améliore les performances des compilations et corrige divers bogues mineurs.

## Date de publication {#release-date}

La date de publication de la mise à jour 2019.8.0 de [!UICONTROL Cloud Manager] est le 19 août 2019.

## Nouveautés {#whats-new}

* Nouvelle interface de ligne de commande pour l’API Cloud Manager, optimisée par l’[interface de ligne de commande Adobe I/O](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* Les modules de contenu spécifiques générés par la compilation peuvent être déclarés comme pouvant être ignorés et ne seront pas déployés. Pour plus d’informations, consultez la section ***Omission des packages de contenu*** dans [Création d’un projet d’application AEM](/help/using/create-an-application-project.md).
* Le jeu de dépendances préchargées dans le conteneur de génération a été retravaillé afin d’éviter toute requête réseau inutile.
* Le message sur la page d’aperçu de certains programmes configurés incorrectement a été amélioré.

## Correctifs {#bug-fixes}

* Lors de l’accès aux rapports SLA, l’année par défaut était 2018, et non 2019.
* Pour les noms d’environnement longs, le sélecteur d’environnement dans l’écran Rapports n’augmentait pas correctement la taille.
* La règle de qualité du code ***ConfigAndInstallShouldOnlyContainOsgiNodes*** a généré des faux positifs lors de l’utilisation du composant Sling Rewriter.
* La règle de qualité du code ***ConfigAndInstallShouldOnlyContainOsgiNodes*** a généré des faux positifs pour certaines structures de chemin d’accès peu courantes.
* Les clients de ressources uniquement n’ont peut-être pas toujours été capables de naviguer vers leurs environnements AEM.
* L’affichage de la boîte de dialogue Créer une branche et un projet varie selon le navigateur utilisé.
