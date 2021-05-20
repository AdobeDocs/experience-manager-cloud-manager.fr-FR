---
title: Notes de mise à jour de la version 2021.2.0
seo-title: Notes de mise à jour de la version 2021.2.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2021.2.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2021.2.0 d’AEM Cloud Manager
exl-id: 4f3c3a63-141b-414f-a24e-1870e985873a
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 24%

---

# Notes de mise à jour de la version 2021.2.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.2.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la mise à jour de [!UICONTROL Cloud Manager] 2021.2.0 est le 11 février 2021.

## Nouveautés {#whats-new}

* L’archétype de projet AEM utilisé dans Project et Sandbox Creation a été mis à jour vers la version 25.

* La liste des API obsolètes identifiées lors de l’analyse du code a été affinée afin d’inclure d’autres classes et méthodes obsolètes dans les dernières versions du SDK Cloud Service.

* Les déploiements de production sont désormais déployés en parallèle sur les instances de publication et de dispatcher couplées.

* Profil SonarQube pour Cloud Manager mis à jour afin de supprimer la règle Sonar `squid:S2142`. Cela n’entre plus en conflit avec les vérifications d’interruption de thread.

* Les propriétés définies dans les fichiers `pom.xml` clients avec le préfixe sonar seront désormais supprimées dynamiquement afin d’éviter les échecs d’analyse de génération et de qualité.

* Des règles de qualité du code supplémentaires ont été ajoutées pour couvrir les problèmes de compatibilité du Cloud Service.

## Correctifs {#bug-fixes}

* Parfois, le pipeline CI/CD (déploiement) échouait lors d’une étape de test des performances en raison d’un conteneur exécutant le test de chargement qui entraînait une erreur.

* Parfois, le conteneur de test de chargement peut signaler l’exécution comme ayant échoué, même si une seule exception se produit. L’échec ne sera signalé que si le processus de test ne peut pas être restauré.

* Certaines incohérences de casse entre la manière dont les noms d’environnement étaient stockés entraînaient des échecs de test de performances.

* Certains échecs de pipeline étaient incorrectement signalés comme des erreurs de pipeline.
