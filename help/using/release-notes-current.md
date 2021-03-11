---
title: Notes de mise à jour de la version 2021.3.0
seo-title: Notes de mise à jour de la version 2021.3.0 d’AEM Cloud Manager
description: Consultez cette page pour obtenir des informations sur la version 2021.3.0 de Cloud Manager
seo-description: Consultez cette page pour obtenir des informations sur la version 2021.3.0 d’AEM Cloud Manager
translation-type: tm+mt
source-git-commit: b5233e1932888b515d8dc26a6493cbd26686bc3c
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 26%

---

# Notes de mise à jour de la version 2021.3.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.3.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la mise à jour 2021.3.0 de [!UICONTROL Cloud Manager] est le 11 mars 2021.

## Nouveautés {#whats-new}

* Un nouvel outil de qualité du code a été introduit pour valider la configuration du répartiteur client (outil d&#39;optimisation du répartiteur).

* Les utilisateurs peuvent désormais voir leur ou leurs rôles Cloud Manager en sélectionnant l&#39;option **Rôle(s) de Vue Cloud Manager** après avoir accédé à l&#39;icône Profil utilisateur (en haut à droite) de l&#39;environnement de travail unifié.

* Pour plus de clarté, l&#39;étiquette **Demande d&#39;approbation** a été réétiquetée à **Approbation de production**.

* Le libellé **Version** a été réétiqueté en **Balise Git** dans l&#39;écran d&#39;exécution du pipeline de production.

* Les étiquettes qui définissent le comportement lorsque des mesures importantes ne respectent pas le seuil défini ont été réétiquetées pour refléter leur comportement réel : Annuler immédiatement et Approuver immédiatement.

* Les listes de classe et de méthode d’obsolescence ont été mises à jour en fonction de la version `2021.3.4997.20210303T022849Z-210225` du SDK Cloud Service AEM.

## Correctifs {#bug-fixes}

* Certains problèmes de qualité n&#39;ont pas été correctement détectés lorsque des paquets étaient incorporés dans d&#39;autres paquets.

* Parfois, si l’utilisateur quitte la page d’exécution du pipeline immédiatement après le démarrage d’un pipeline, un message d’erreur s’affiche indiquant que l’action a échoué, bien que l’exécution ait effectivement début.