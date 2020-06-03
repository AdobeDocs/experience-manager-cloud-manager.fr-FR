---
title: Notes de mise à jour de la version 2020.4.0
seo-title: Notes de mise à jour de la version 2020.4.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.4.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.4.0 d’AEM Cloud Manager
translation-type: ht
source-git-commit: 278858465592482449080fedc3c0165805db223d
workflow-type: ht
source-wordcount: '243'
ht-degree: 100%

---

# Notes de mise à jour de la version 2020.4.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2020.4.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la version 2020.4.0 de [!UICONTROL Cloud Manager] est le 9 avril 2020.

## Nouveautés {#whats-new}

* Modifications de la page d’aperçu de navigation de Cloud Manager pour permettre à l’utilisateur de modifier un programme ou d’en changer.
* Modifications permettant à l’utilisateur de modifier un programme à partir de la carte de programme sur la page d’entrée de Cloud Manager.
* Nouveau statut du pipeline **Exécution de pipeline** affiché au niveau de l’environnement auquel il est associé.
* Améliorations de la lisibilité de la page d’exécution de pipeline. Cela inclut l’affichage du nom du pipeline (pipeline hors production uniquement) et du type, ainsi qu’un badge pour indiquer si le statut du pipeline est En cours/Annulé/Échec.
* Le processus utilisé pour générer les mots de passe Git est maintenant plus résilient face aux problèmes de la couche de service sous-jacente.

## Correctifs {#bug-fixes}

* Les données de surveillance pouvaient parfois s’afficher de manière incorrecte ou pas du tout en fonction de variations mineures des valeurs techniques.
* La configuration Maven utilisée dans le conteneur de build a été mise à jour afin d’éviter les blocages lors du téléchargement des métadonnées d’artefact.
* Le processus de test des performances d’Assets ne parvenait parfois pas à déchiffrer le mot de passe AEM, ce qui provoquait l’échec des tests.
* Certaines topologies avec des instances de secours pouvaient présenter des faux négatifs lors des tests de sécurité.
* Si l’environnement d’évaluation contenait une instance arrêtée, l’étape de test de sécurité échouait parfois.
* Les notifications Experience Cloud n’étaient pas toujours reçues.

