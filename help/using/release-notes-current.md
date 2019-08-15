---
title: Notes de mise à jour de la version 2019.8.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.8.0
description: Consultez cette page pour obtenir des informations sur la version 2019.8.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.8.0 d’AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 365cd6dfe65059c0c529f774bbcda946d47b0db5

---

# Notes de mise à jour de la version 2019.8.0 {#release-notes-for}

La version 2019.8.0 [!UICONTROL de Cloud Manager] prend en charge les packages de contenu créé de manière sélective, améliore les performances de création et corrige divers bogues mineurs.

## Date de publication {#release-date}

La date de publication de la mise à jour 2019.8.0 de [!UICONTROL Cloud Manager] est le jeudi 19 août 2019.

## Nouveautés {#whats-new}

* Nouvelle interface de ligne de commande vers l'API Cloud Manager, optimisée par l'interface de ligne de commande [d'Adobe I/S](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* Les packages de contenu spécifiques générés par la version peuvent être déclarés comme sautés et ne seront pas déployés. Consultez ***la section Saut de contenu de*** contenu dans [Création d'un projet d'application AEM](create-an-application-project.md) pour plus d'informations.
* Le jeu de dépendances préchargées dans le conteneur de création a été retravaillé afin d'éviter toute requête réseau inutile.
* Le message sur la page d'aperçu de certains programmes configurés incorrectement a été amélioré.

## Correctifs {#bug-fixes}

* Lors de l'accès aux rapports SLA, l'année par défaut était 2018, et non 2019.
* Pour les noms d'environnement longs, le sélecteur d'environnement dans l'écran Rapports n'était pas correctement augmenté.
* La règle de qualité du code ***configandinstallaidonlycontainosginodes*** a généré false positifs lors de l'utilisation du composant Sling Réwriter.
* La règle de qualité du code ***configandinstallaidonlycontainosginodes*** a généré des faux positifs pour certaines structures de chemin peu courantes.
* Les clients de ressources uniquement n'ont peut-être pas été toujours capables de naviguer dans leurs environnements AEM.
* La boîte de dialogue [!UICONTROL Créer une branche et un projet] est rendue différemment dans différents navigateurs.
