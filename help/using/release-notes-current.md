---
title: Notes de mise à jour de la version 2021.2.0
seo-title: Notes de mise à jour de la version 2021.2.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2021.2.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2021.2.0 d’AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 67cdd39cb511763a42391c7896924a1433e4e58f
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 25%

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

* Les propriétés définies dans les fichiers `pom.xml` client précédés du préfixe Sonar seront désormais supprimées dynamiquement afin d’éviter les échecs d’analyse de la génération et de la qualité.

## Correctifs {#bug-fixes}

* À l&#39;occasion, le pipeline CI/CD (déploiement) a échoué lors d&#39;une étape d&#39;essai de performances en raison d&#39;un conteneur exécutant le test de charge qui a rencontré une erreur.

* Le conteneur de test de charge peut parfois signaler l’échec de l’exécution, même si une seule exception se produit. L&#39;échec ne sera signalé que si le processus de test ne peut pas être restauré.

* Certaines discordances de casse entre la façon dont les noms d&#39;environnement étaient stockés conduiraient à des échecs de test des performances.

* Certains échecs de pipeline étaient incorrectement signalés comme des erreurs de pipeline.