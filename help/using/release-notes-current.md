---
title: Notes de mise à jour de la version 2021.2.0
seo-title: Notes de mise à jour de la version 2021.2.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2021.2.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2021.2.0 d’AEM Cloud Manager
translation-type: tm+mt
source-git-commit: d956c7a2d3833e357920a9602e4f5a5b37f2c98a
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 24%

---

# Notes de mise à jour de la version 2021.2.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.2.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la mise à jour de [!UICONTROL Cloud Manager] 2021.2.0 est le 11 février 2021.

## Nouveautés {#whats-new}

* L&#39;archétype de projet AEM utilisé dans Project and Sandbox Creation a été mis à jour vers la version 25.

* La liste des API obsolètes identifiées lors de l’analyse du code a été affinée afin d’inclure d’autres classes et méthodes obsolètes dans les dernières versions du SDK Cloud Service.

* Désormais, les déploiements de production sont déployés en parallèle sur les instances de publication et de répartiteur paires.

* Profil SonarQube pour Cloud Manager mis à jour pour supprimer la règle Sonar `squid:S2142`. Ceci ne sera plus en conflit avec les vérifications d&#39;interruption de thread.

* Les propriétés définies dans les fichiers `pom.xml` client précédés d&#39;un sonar seront désormais supprimées dynamiquement afin d&#39;éviter les échecs d&#39;analyse de la génération et de la qualité.

* Des règles de qualité de code supplémentaires ont été ajoutées pour couvrir les problèmes de compatibilité des Cloud Service.

## Correctifs {#bug-fixes}

* À l&#39;occasion, le pipeline CI/CD (déploiement) a échoué lors d&#39;une étape d&#39;essai de performances en raison d&#39;un conteneur exécutant le test de charge qui a rencontré une erreur.

* Le conteneur de test de charge peut parfois signaler l’échec de l’exécution, même si une seule exception se produit. L&#39;échec ne sera signalé que si le processus de test ne peut pas être restauré.

* Certaines discordances de casse entre la façon dont les noms d&#39;environnement étaient stockés conduiraient à des échecs de test des performances.

* Certains échecs de pipeline étaient incorrectement signalés comme des erreurs de pipeline.