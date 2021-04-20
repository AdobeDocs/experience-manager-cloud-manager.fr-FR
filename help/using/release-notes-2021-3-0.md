---
title: Notes de mise à jour de la version 2021.3.0
description: Consultez cette page pour obtenir des informations sur la version 2021.3.0 de Cloud Manager
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea,e05b22fe-f071-4b69-9db1-e3d7ee4cfbcc
translation-type: tm+mt
source-git-commit: 9c3e748f8aed969af861b505ee336eb5501d826f
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

* Un nouvel outil de qualité du code [Outil d&#39;optimisation du répartiteur](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) a été introduit pour valider la configuration du répartiteur client.

* Les utilisateurs peuvent désormais voir leur ou leurs rôles Cloud Manager en sélectionnant l&#39;option **Rôle(s) de Vue Cloud Manager** après avoir accédé à l&#39;icône Profil utilisateur (en haut à droite) de l&#39;environnement de travail unifié.

* Pour plus de clarté, l&#39;étiquette **Demande d&#39;approbation** a été réétiquetée à **Approbation de production**.

* Le libellé **Version** a été réétiqueté en **Balise Git** dans l&#39;écran d&#39;exécution du pipeline de production.

* Les étiquettes qui définissent le comportement lorsque des mesures importantes ne respectent pas le seuil défini ont été réétiquetées afin de refléter leur comportement réel : **Annuler immédiatement** et **Approuver immédiatement**. Voir [Configuration des paramètres du pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager) pour plus de détails.

* Les listes de classe et de méthode d’obsolescence ont été mises à jour en fonction de la version `2021.3.4997.20210303T022849Z-210225` du SDK Cloud Service AEM.

## Correctifs {#bug-fixes}

* Certains problèmes de qualité n&#39;ont pas été correctement détectés lorsque des paquets étaient incorporés dans d&#39;autres paquets.

* Parfois, si l’utilisateur quitte la page d’exécution du pipeline immédiatement après le démarrage d’un pipeline, un message d’erreur s’affiche indiquant que l’action a échoué, bien que l’exécution ait effectivement début.
