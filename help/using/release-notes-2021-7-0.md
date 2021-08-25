---
title: Notes de mise à jour de la version 2021.7.0
description: Consultez cette page pour obtenir des informations sur la version 2021.7.0 de Cloud Manager
feature: Informations sur la version
source-git-commit: e490a8f1dd17e63f35ed00d4cdf95b6e7a07b150
workflow-type: ht
source-wordcount: '264'
ht-degree: 100%

---

# Notes de mise à jour de la version 2021.7.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.7.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>Reportez-vous aux [Notes de mise à jour actuelles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr#getting-access) pour consulter les dernières notes de mise à jour de Cloud Manager dans AEM as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la mise à jour 2021.7.0 de [!UICONTROL Cloud Manager] est le 15 juillet 2021.
La prochaine version est prévue pour le 12 août 2021.

## Nouveautés {#whats-new}

* Les clients peuvent désormais utiliser les JDK Azul 8 et 11 pour leurs processus de génération Cloud Manager et peuvent choisir d’utiliser un de ces JDK pour les plug-ins Maven compatibles avec les chaînes d’outils *ou* pour l’exécution du processus Maven complet.

* L’adresse IP sortante sera désormais consignée dans le fichier journal de l’étape de génération.

* Les boutons **Gérer Git** ont été renommés **Accéder aux informations Git** et le visuel de la boîte de dialogue a été rafraîchi.

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 28.

* Des reconfigurations topologiques inattendues pouvaient entraîner l’indisponibilité des rapports de test détaillés dans la page des détails d’exécution du pipeline.

## Correctifs {#bug-fixes}

* La navigation manuelle vers la page des détails de l’exécution pour une exécution non existante n’affichait pas d’erreur, mais simplement un écran de chargement sans fin.

* Dans certains cas, la reprise automatique pour les conteneurs en échec utilisés dans les performances de Sites ne prenait pas effet pendant 2 heures, ce qui entraînait l’échec du test.

## Problèmes connus {#known-issues}

Les clients basculant sur les JDK Azul doivent savoir que toutes les applications existantes ne seront pas compilées sans erreur sur le JDK Azul. Il est vivement recommandé d’exécuter un test local avant de basculer.