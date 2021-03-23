---
title: Notes de mise à jour de la version 2019.4.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.4.0
description: Consultez cette page pour obtenir des informations sur la version 2019.4.0 de Cloud Manager.
seo-description: Consultez cette page pour obtenir des informations sur la version 2019.4.0 d’AEM Cloud Manager.
feature: Informations sur la version
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 100%

---


# Notes de mise à jour de la version 2019.4.0 {#release-notes-for}

La version 2019.4.0 de [!UICONTROL Cloud Manager] ne contient pas de modifications fonctionnelles majeures. Pour plus d’informations, suivez les sections ci-après.

## Date de publication {#release-date}

La date de publication de la version 2019.4.0 de [!UICONTROL Cloud Manager] est le 18 avril 2019.

## Nouveautés {#whats-new}

* L’interface utilisateur de Cloud Manager est désormais disponible en allemand, en anglais, en français et en japonais.
* Les étapes de déploiement contiennent désormais le processus en cours d’exécution, c’est-à-dire une sauvegarde en cours d’exécution, des packages en cours d’installation et des équilibreurs de charge en cours de reconfiguration.

## Correctifs {#bug-fixes}

* La méthode de déploiement utilisée pour les modifications du Dispatcher a été améliorée afin de gérer des scénarios d’utilisation supplémentaires.
* Certains types de tailles d’instance ne s’affichaient pas correctement dans la page Environnements.
* Les règles de qualité du code CQBP-84-dependencies généraient des faux positifs pour les bibliothèques Adobe incorporées, telles que WCM Core Components et Asset Share Commons.
* Le bouton des détails de l’étape d’analyse du code était activé alors que les détails étaient indisponibles.
* Le message d’erreur affiché lors de la spécification d’une valeur non valide pour l’indicateur de performance clé des pages vues par minute comportait une limite inférieure incorrecte.
* La catégorie de déploiement sur un pipeline hors production n’était pas correctement mise en majuscules.
* La carte d’appel à l’action de la page **Aperçu** comportait un texte incorrect lorsque le référentiel git n’était pas configuré correctement.

## Problèmes connus {#known-issues}

* Les valeurs SLA peuvent être arrondies incorrectement.
