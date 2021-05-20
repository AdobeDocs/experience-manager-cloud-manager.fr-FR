---
title: Notes de mise à jour de la version 2021.3.0
description: Consultez cette page pour obtenir des informations sur la version 2021.3.0 de Cloud Manager
feature: Informations sur la version
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 503d9b25855633737c49e3e278a3a76052ed84d1
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 18%

---

# Notes de mise à jour de la version 2021.3.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.3.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la mise à jour 2021.3.0 de [!UICONTROL Cloud Manager] est le 11 mars 2021.
La prochaine version est prévue pour le 8 avril 2021.

## Nouveautés {#whats-new}

* Un nouvel outil de qualité du code [Outil d’optimisation du Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) a été introduit pour valider la configuration du Dispatcher client.

* Les utilisateurs peuvent désormais voir leur ou leurs rôles Cloud Manager en sélectionnant l’option **Afficher le ou les rôles Cloud Manager** après avoir accédé à l’icône Profil utilisateur (en haut à droite) de Shell unifié.

* Le libellé **Demande d’approbation** a été renommé **Approbation de production** pour plus de clarté.

* Le libellé **Version** a été renommé **Balise Git** dans l’écran d’exécution du pipeline de production.

* Les étiquettes qui définissent le comportement lorsque des mesures importantes ne correspondent pas au seuil défini ont été réétiquetées afin de refléter leur comportement réel : **Annuler immédiatement** et **Approuver immédiatement**. Pour plus d’informations, voir [Configuration des paramètres du pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager) .

* Les listes d’obsolescence des classes et des méthodes ont été mises à jour en fonction de la version `2021.3.4997.20210303T022849Z-210225` du SDK Cloud Service AEM.

## Correctifs {#bug-fixes}

* Certains problèmes de qualité n’ont pas été correctement découverts lorsque des modules étaient incorporés dans d’autres modules.

* Parfois, si l’utilisateur quitte la page d’exécution du pipeline immédiatement après le démarrage d’un pipeline, un message d’erreur s’affiche indiquant que l’action a échoué, bien que l’exécution ait réellement commencé.
