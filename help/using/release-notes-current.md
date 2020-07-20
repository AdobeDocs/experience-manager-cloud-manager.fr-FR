---
title: Notes de mise à jour de la version 2020.7.0
seo-title: Notes de mise à jour de la version 2020.7.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.7.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.7.0 d’AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 0d46abc386460ccbaf7ba10b93286bc8e4af2395
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 75%

---

# Notes de mise à jour de la version 2020.7.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2020.7.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la mise à jour 2020.7.0 de [!UICONTROL Cloud Manager] est le 09 juillet 2020.

## Nouveautés {#whats-new}

* L’association et la dissociation d’instances de répartiteur depuis les équilibreurs de charge au cours des déploiements de production s’effectuent de manière plus cohérente.

* Le conteneur de création Cloud Manager prend désormais en charge Java 8 et Java 11.

* Les pipelines de Cloud Manager prennent désormais en charge les variables et les secrets définis par le client.
Pour plus d&#39;informations, consultez Variables [de](/help/using/create-an-application-project.md#pipeline-variables) pipeline.

## Correctifs {#bug-fixes}

* Les options **Annuler** et **Enregistrer** sur la page Modification du pipeline hors production n’étaient pas toujours visibles.

* Certaines erreurs liées au u processus de qualité du code peuvent entraîner la génération incorrecte du fichier journal.

* Certains journaux d&#39;étape de pipeline volumineux n&#39;ont pas pu être téléchargés de manière cohérente via l&#39;interface utilisateur.

## Problèmes connus {#known-issues}

* Si un environnement AMS contient une instance de secours, le message consigné indique que l’instance est hors service, et non en mode de secours.

* En raison d’un changement dans le mode de calcul de la couverture du code, la version _minimale_ du module externe Jacoco est désormais 0.7.5.201505241946 (publiée en mai 2015). Les clients référençant explicitement une ancienne version recevront un message d’erreur dans le processus de qualité du code.
