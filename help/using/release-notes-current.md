---
title: Notes de mise à jour de la version 2020.11.0
seo-title: Notes de mise à jour de la version 2020.11.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2020.11.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2020.11.0 d’AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 30d782f5a095b1b07ec4f2039def9ba30a559325
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 31%

---

# Notes de mise à jour de la version 2020.11.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2020.11.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.11.0 is November 12, 2020.

## Nouveautés {#whats-new}

* L’onglet **Apprendre** de Cloud Manager est actualisé avec de nouvelles images dans l’interface utilisateur.

## Correctifs {#bug-fixes}

* Certaines erreurs de déploiement provoquées par les clients seront désormais explicitement affichées dans les journaux de déploiement.

* Le chargement des dépendances effectuées avant l&#39;exécution de la génération nécessitait le téléchargement d&#39;un module externe Maven.

* Le lien du pied de page de Cloud Manager permettant de sélectionner une langue accède désormais à l’emplacement approprié.

* Parfois, pendant la numérisation du code, le processus SonarQube ne se début pas. Désormais, cette détection sera automatiquement détectée et un redémarrage sera tenté.

* Au cours du processus d’analyse du site utilisé dans les tests de performances, les demandes dont le délai d’expiration aux trois premiers niveaux de traversée de profondeur sera automatiquement réessayé.