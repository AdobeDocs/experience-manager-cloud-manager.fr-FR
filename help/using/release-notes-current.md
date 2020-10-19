---
title: Notes de mise à jour de la version 2020.10.0
seo-title: Notes de mise à jour de la version 2020.10.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.10.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.10.0 d’AEM Cloud Manager
translation-type: ht
source-git-commit: aad2da58e5934999884553619dd97d42cc725d88
workflow-type: ht
source-wordcount: '106'
ht-degree: 100%

---

# Notes de mise à jour de la version 2020.10.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2020.10.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

[!UICONTROL Cloud Manager] version 2020.10.0 a été publié le 1er octobre 2020.

## Correctifs {#bug-fixes}

* Le moteur de recherche utilisé pour les tests de performances prenait en compte de manière incorrecte certains types de ressources comme des liens web valides.

* Dans certains cas, l’étape d’achèvement des tests de performances n’était pas correctement gérée, ce qui entraînait des étapes très longues.

* Lorsque l’invalidation du cache du dispatcher était configurée pour les déploiements de production, cette invalidation était parfois exécutée deux fois.