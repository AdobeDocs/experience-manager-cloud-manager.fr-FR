---
title: Notes de mise à jour de la version 2019.6.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.6.0
description: Consultez cette page pour obtenir des informations sur la version 2019.6.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.6.0 d’AEM Cloud Manager.
feature: Informations sur la version
exl-id: 5a87f191-8203-4cb9-a810-247aece41605
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 100%

---

# Notes de mise à jour de la version 2019.6.0 {#release-notes-for}

La version 2019.6.0 de [!UICONTROL Cloud Manager] ajoute de nouvelles règles de qualité du code et un assistant de mise à jour du produit. Pour plus d’informations, consultez les sections ci-après.

## Date de publication {#release-date}

La date de publication de la version 2019.6.0 de [!UICONTROL Cloud Manager] est le 20 juin 2019 .

## Nouveautés {#whats-new}

* Nouvel assistant de mise à jour du produit pour permettre aux clients d’exécuter une mise à jour d’AEM. Pour en savoir plus, consultez [Assistant de mise à jour du produit](overview-productupdate-wizard.md).
* Règles de qualité du code examinant les structures de contenu. Pour plus d’informations, consultez [Règles de qualité du code personnalisé](custom-code-quality-rules.md).
* La taille maximale d&#39;un push git a été augmentée à 1 Go.

## Correctifs {#bug-fixes}

* Dans certains cas, les pipelines ne pouvaient pas être démarrés suite à un échec précédent.

## Problèmes connus {#known-issues}

* Le téléchargement CSV de la qualité du code n’est pas toujours trié en fonction de la gravité.
* Des faux positifs peuvent être signalés par la règle *ConfigAndInstallShouldOnlyContainOsgiNodes* si les configurations OSGi sont placées dans un dossier imbriqué sous un dossier de *configuration*.
