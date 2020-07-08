---
title: Notes de mise à jour de la version 2020.7.0
seo-title: Notes de mise à jour de la version 2020.7.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.7.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.7.0 d’AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 26492dc02371d21670778f3cd60d26146439548e
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 36%

---

# Notes de mise à jour de la version 2020.7.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2020.7.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la mise à jour 2020.6.0 de [!UICONTROL Cloud Manager] est le 09 juillet 2020.

## Nouveautés {#whats-new}

* Désormais, la détection et l’association d’instances de répartiteur à partir des équilibreurs de charge au cours des déploiements de production s’effectuent de manière plus cohérente.

* Le conteneur de création de Cloud Manager prend désormais en charge Java 8 et Java 11.

* Les pipelines de Cloud Manager prennent désormais en charge les variables et les secrets définis par le client.

## Correctifs {#bug-fixes}

* Les options **Annuler** et **Enregistrer** sur la page Modification du pipeline hors production n’étaient pas toujours visibles.

* Certains échecs du processus de qualité du code peuvent entraîner la génération incorrecte du fichier journal.

* Certains journaux d&#39;étape de pipeline volumineux n&#39;ont pas pu être téléchargés de manière cohérente via l&#39;interface utilisateur.

## Problèmes connus {#known-issues}

* Lorsqu’un environnement AMS contient une instance de secours, le message consigné indique que l’instance est hors service et non en mode de secours.
