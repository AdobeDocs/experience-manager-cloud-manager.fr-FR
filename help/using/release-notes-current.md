---
title: Notes de mise à jour de la version 2020.10.0
seo-title: Notes de mise à jour de la version 2020.10.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.10.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.10.0 d’AEM Cloud Manager
translation-type: tm+mt
source-git-commit: aad2da58e5934999884553619dd97d42cc725d88
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 54%

---

# Notes de mise à jour de la version 2020.10.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2020.10.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

[!UICONTROL Cloud Manager] version 2020.10.0 a été publié le 01 octobre 2020.

## Correctifs {#bug-fixes}

* L’analyseur de liens utilisé pour les tests de performances considérait incorrectement certains types de ressources comme des liens Web valides.

* Dans certains cas, l’étape d’achèvement des tests de performances n’était pas correctement gérée, ce qui entraînait des étapes à long terme.

* Lorsque l’invalidation du cache du répartiteur était configurée pour les déploiements de production, l’invalidation était parfois exécutée deux fois.