---
title: Notes de mise à jour de la version 2019.12.0
seo-title: Notes de mise à jour de la version 2019.12.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2019.12.0 de Cloud Manager.
seo-description: Consultez cette page pour obtenir des informations sur la version 2019.12.0 d’AEM Cloud Manager.
feature: Informations sur la version
exl-id: e173962f-587d-439e-a499-81ea98c52cc9
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Notes de mise à jour de la version 2019.12.0 {#release-notes-for}

La section suivante décrit les notes de mise à jour générales de la version 2019.12.0 de [!UICONTROL Cloud Manager], et ajoute des mises à jour à l’exécution de pipeline, ainsi que des améliorations au niveau des analyses de qualité du code.
Pour plus d’informations, consultez les sections ci-après.

## Date de publication {#release-date}

La date de publication de la mise à jour 2019.12.0 de [!UICONTROL Cloud Manager] est le 12 décembre 2019.

## Nouveautés {#whats-new}

* Les étapes d’exécution de pipeline indiquent désormais l’horodatage d’achèvement de chaque étape.
* Les analyses de qualité du code pour les projets qui ne contiennent pas de code Java indiquent désormais un taux de couverture du code de 100 %.
* Le contrôle de l’intégrité de la configuration du Dispatcher CQ a été supprimé.

## Correctifs {#bug-fixes}

* Les dates ne s’affichaient pas correctement dans certains navigateurs.
* Dans de rares cas, le pipeline de production passait à l’étape d’approbation alors que les tests de performances étaient toujours en cours d’exécution.
* Dans certains états, les boutons situés en haut de la page d’aperçu n’étaient pas correctement alignés.
* Dans certaines circonstances, des utilisateurs non autorisés voyaient un bouton pour démarrer le pipeline sans pouvoir cliquer dessus.
* Les boutons d’action pour les pipelines hors production s’affichaient parfois au mauvais endroit.
* Les modules présentant le type de nœud granite:Ranking ne pouvaient pas être analysés pour détecter certaines violations de règles de qualité.
* Certaines défaillances du processus de qualité du code étaient comptées comme des bogues de manière erronée.
* Il était impossible de charger les données de surveillance pour certaines topologies.
