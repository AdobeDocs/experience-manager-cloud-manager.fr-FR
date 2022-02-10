---
title: Notes de mise à jour de la version 2021.3.0
description: Consultez cette page pour obtenir des informations sur la version 2021.3.0 de Cloud Manager
feature: Release Information
exl-id: e05b22fe-f071-4b69-9db1-e3d7ee4cfbcc
source-git-commit: 71d44c7e3673ca62fcd2203ecc0bc4ed9fa22002
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 95%

---

# Notes de mise à jour de la version 2021.3.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.3.0 de [!UICONTROL Cloud Manager].

## Date de publication {#release-date}

La date de publication de la mise à jour 2021.3.0 de [!UICONTROL Cloud Manager] est le 11 mars 2021.
La prochaine version est prévue pour le 8 avril 2021.

## Nouveautés {#whats-new}

* Un nouvel outil de qualité du code, l’[Outil d’optimisation du Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=fr#dispatcher-optimization-tool-rules), a été introduit pour valider la configuration du Dispatcher client.

* Les utilisateurs peuvent désormais consulter leurs rôles Cloud Manager en sélectionnant l’option **Afficher le(s) rôle(s) Cloud Manager** après avoir accédé à l’icône Profil utilisateur (en haut à droite) du shell unifié.

* Pour plus de clarté, le libellé **Application à approuver** a été renommé **Approbation de production**.

* Le libellé **Version** a été renommé **Balise Git** dans l’écran d’exécution du pipeline de production.

* Les libellés qui définissent le comportement lorsque des mesures importantes ne respectent pas le seuil défini ont été réétiquetés afin de refléter leur comportement réel : **Annuler immédiatement** et **Approuver immédiatement**. Reportez-vous au document [Configuration des pipelines de production](configuring-production-pipelines.md) pour plus d’informations.

* Les listes de classe et de méthode d’obsolescence ont été mises à jour en fonction de la version `2021.3.4997.20210303T022849Z-210225` du SDK AEM Cloud Service.

## Correctifs {#bug-fixes}

* Certains problèmes de qualité n’étaient pas été correctement détectés lorsque des packages étaient incorporés dans d’autres packages.

* Parfois, lorsque l’utilisateur quittait la page d’exécution du pipeline immédiatement après le démarrage d’un pipeline, un message d’erreur s’affichait indiquant que l’action a échoué, bien que l’exécution ait effectivement débuté.
