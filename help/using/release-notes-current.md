---
title: Notes de mise à jour de la version 2021.7.0
description: Consultez cette page pour obtenir des informations sur la version 2021.7.0 de Cloud Manager
feature: Informations sur la version
source-git-commit: ee701dd2d0c3921455a0960cbb6ca9a3ec4793e7
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 31%

---

# Notes de mise à jour de la version 2021.7.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.7.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>Reportez-vous aux [Notes de mise à jour actuelles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr#getting-access) pour consulter les dernières notes de mise à jour de Cloud Manager dans AEM as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la mise à jour 2021.7.0 de [!UICONTROL Cloud Manager] est le 15 juillet 2021.
La prochaine version est prévue pour le 12 août 2021.

## Nouveautés {#whats-new}

* Les clients peuvent désormais utiliser les JDK Azul 8 et 11 pour leurs processus de génération Cloud Manager et peuvent choisir d’utiliser l’un de ces JDK pour les modules externes Maven compatibles avec les chaînes d’outils *ou* l’exécution complète du processus Maven.

* L’adresse IP sortante sortante sera désormais consignée dans le fichier journal de l’étape de création.

* Les boutons Gérer Git ont été renommés Accéder aux informations Git et la boîte de dialogue a été actualisée visuellement.

* Certaines reconfigurations de topologie inattendues peuvent entraîner la fin de la disponibilité des rapports de test détaillés dans la page des détails d’exécution du pipeline.

## Correctifs {#bug-fixes}

* La navigation manuelle vers la page des détails de l’exécution pour une exécution non existante n’affichait pas d’erreur, juste un écran de chargement sans fin.

* Dans certains cas, la reprise automatique pour les conteneurs en échec utilisés dans les performances de Sites ne prendra pas effet pendant 2 heures, ce qui entraîne un échec du test.

## Problèmes connus {#known-issues}

Les clients qui passent à l’utilisation des JDK Azul doivent savoir que toutes les applications existantes ne seront pas compilées sans erreur sur le JDK Azul. Il est vivement recommandé de tester localement avant de basculer.