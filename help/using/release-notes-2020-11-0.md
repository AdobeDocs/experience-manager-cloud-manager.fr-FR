---
title: Notes de mise à jour de la version 2020.11.0
seo-title: Notes de mise à jour de la version 2020.11.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.11.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.11.0 d’AEM Cloud Manager
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 100%

---

# Notes de mise à jour de la version 2020.11.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2020.11.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] version 2020.11.0 est le 12 novembre 2020.

## Nouveautés {#whats-new}

* L’onglet **Apprendre** de Cloud Manager est actualisé avec de nouvelles images dans l’interface utilisateur.

## Correctifs {#bug-fixes}

* Certaines erreurs de déploiement provoquées par les clients seront désormais explicitement affichées dans les journaux de déploiement.

* Le chargement des dépendances effectué avant l’exécution du build nécessitait le téléchargement d’un module externe Maven.

* Le lien du pied de page de Cloud Manager destiné à sélectionner une langue dirige désormais vers l’emplacement approprié.

* Parfois, pendant la numérisation du code, le processus SonarQube ne démarrait pas. Désormais, il sera automatiquement détecté et un redémarrage sera tenté.

* Au cours du processus d’analyse du site utilisé lors des tests de performances, les demandes qui atteignent le délai d’expiration aux trois premiers niveaux du parcours en profondeur feront automatiquement l’objet d’une nouvelle tentative.