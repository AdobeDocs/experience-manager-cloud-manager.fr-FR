---
title: Notes de mise à jour de la version 2019.7.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.7.0
description: Consultez cette page pour obtenir des informations sur la version 2019.7.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.7.0 d’AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 7cfa0cf66efd5891263bfcc83a5149daec5c8b67

---

# Notes de mise à jour de la version 2019.7.0 {#release-notes-for}

[!UICONTROL La version] 2019.7.0 de Cloud Manager ajoute de nouvelles règles de qualité du code et de nouveaux assistant de mise à jour du produit. Pour plus d’informations, consultez les sections ci-après.

## Date de publication {#release-date}

La date de publication de la mise à jour 2019.7.0 de [!UICONTROL Cloud Manager] est le 18 juillet 2019 .

## Nouveautés {#whats-new}

Il existe désormais une notification Experience Cloud envoyée au début d'un déploiement de production.

## Correctifs {#bug-fixes}

* Dans certains cas, Cloud Manager effectuait une analyse de code statique sur les fichiers Python et PHP.
* Les packs contenant des installhooars filevault n'étaient pas systématiquement exécutés par l'étape de qualité du code.
* Dans certaines combinaisons, les problèmes de qualité du code n'étaient pas systématiquement triés.
* La page d'exécution du canal a été confrontée à quelques problèmes visuels.
* L'étape de test des performances peut échouer de manière aléatoire une partie du temps dû aux contraintes de ressources provenant de l'infrastructure de cloud sous-jacente.
* Certaines générations de clients échouaient en raison de problèmes de réseau.