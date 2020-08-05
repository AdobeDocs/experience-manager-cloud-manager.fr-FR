---
title: Notes de mise à jour de la version 2020.7.0
seo-title: Notes de mise à jour de la version 2020.7.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.7.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.7.0 d’AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 3be958aa21d5423ddf371c286825d01afd554c4b
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 100%

---

# Notes de mise à jour de la version 2020.7.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2020.7.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la mise à jour 2020.7.0 de [!UICONTROL Cloud Manager] est le 09 juillet 2020.

## Nouveautés {#whats-new}

* L’association et la dissociation d’instances de répartiteur depuis les équilibreurs de charge au cours des déploiements de production s’effectuent de manière plus cohérente.

* Le conteneur de création Cloud Manager prend désormais en charge Java 8 et Java 11.

* Les pipelines de Cloud Manager prennent désormais en charge les variables et les secrets définis par le client.
Pour plus d’informations, consultez [Variables de pipeline](/help/using/create-an-application-project.md#pipeline-variables).

## Correctifs {#bug-fixes}

* Les options **Annuler** et **Enregistrer** sur la page Modification du pipeline hors production n’étaient pas toujours visibles.

* Certaines erreurs liées au u processus de qualité du code peuvent entraîner la génération incorrecte du fichier journal.

* Certains journaux d&#39;étape de pipeline volumineux n&#39;ont pas pu être téléchargés de manière cohérente via l&#39;interface utilisateur.

## Problèmes connus {#known-issues}

* Si un environnement AMS contient une instance de secours, le message consigné indique que l’instance est hors service, et non en mode de secours.

* En raison d’un changement au niveau du mode de calcul de la couverture du code, la version _minimale_ du plug-in Jacoco est désormais 0.7.5.201505241946 (publiée en mai 2015). Un message d’erreur sera généré dans le processus de qualité du code pour les clients qui référencent une version plus ancienne de manière explicite.
