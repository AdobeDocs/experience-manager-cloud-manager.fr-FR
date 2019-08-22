---
title: Notes de mise à jour de la version 2019.8.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.8.0
description: Consultez cette page pour obtenir des informations sur la version 2019.8.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.8.0 d’AEM Cloud Manager.
translation-type: ht
source-git-commit: 365cd6dfe65059c0c529f774bbcda946d47b0db5

---

# Notes de mise à jour de la version 2019.8.0 {#release-notes-for}

La version 2019.8.0 [!UICONTROL de Cloud Manager] prend en charge les modules de contenu créés de manière sélective, améliore les performances des compilations et corrige divers bogues mineurs.

## Date de publication {#release-date}

La date de publication de la mise à jour 2019.8.0 de [!UICONTROL Cloud Manager] est le 19 août 2019.

## Nouveautés {#whats-new}

* Nouvelle interface de ligne de commande pour l’API Cloud Manager, optimisée par l’[interface de ligne de commande Adobe I/O](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* Les modules de contenu spécifiques générés par la compilation peuvent être déclarés comme pouvant être ignorés et ne seront pas déployés. Pour plus d’informations, consultez la section ***Omission des packages de contenu*** dans [Création d’un projet d’application AEM](create-an-application-project.md).
* Le jeu de dépendances préchargées dans le conteneur de génération a été retravaillé afin d’éviter toute requête réseau inutile.
* Le message sur la page d’aperçu de certains programmes configurés incorrectement a été amélioré.

## Correctifs {#bug-fixes}

* Lors de l’accès aux rapports SLA, l’année par défaut était 2018, et non 2019.
* Pour les noms d’environnement longs, le sélecteur d’environnement dans l’écran Rapports n’augmentait pas correctement la taille.
* La règle de qualité du code ***ConfigAndInstallShouldOnlyContainOsgiNodes*** a généré des faux positifs lors de l’utilisation du composant Sling Rewriter.
* La règle de qualité du code ***ConfigAndInstallShouldOnlyContainOsgiNodes*** a généré des faux positifs pour certaines structures de chemin d’accès peu courantes.
* Les clients de ressources uniquement n’ont peut-être pas toujours été capables de naviguer vers leurs environnements AEM.
* La boîte de dialogue [!UICONTROL Create a Branch and Project] (Créer un embranchement et un projet) est rendue différemment dans différents navigateurs.
