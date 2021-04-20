---
title: Notes de mise à jour de la version 2018.7.0
seo-title: Notes de mise à jour de la version 2018.7.0
description: En savoir plus sur Cloud Manager version 2018.7.0
seo-description: Consultez cette page pour obtenir des informations sur la version 2018.7.0 de Cloud Manager.
uuid: d7b49e32-01dc-48ce-b744-e6a806fbdd8a
contentOwner: jsyal
topic-tags: release-notes
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b64bf9ab-27ed-4f33-adc8-d73d34094f1b
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 98%

---


# Notes de mise à jour de la version 2018.7.0 {#release-notes-for}

La section ci-dessous décrit la mise à jour 2018.7.0 de [!UICONTROL Cloud Manager] qui offre une fonctionnalité *de mise à l’échelle automatique*.

**La mise à l’échelle automatique** est activée par l’intermédiaire d’une échelle horizontale en dehors `Dispatcher/Publish` des segments dans l’environnement de production afin de prendre en charge une augmentation soudaine de la charge, du volume, de l’accès et d’autres mesures surveillées définies.

## Date de publication {#release-date}

La date de publication de la mise à jour 2018.7.0 de [!UICONTROL Cloud Manager] est le lundi 10 septembre 2018.

## Nouveautés {#what-s-new}

* **Mise en service** : [!UICONTROL Cloud Manager] pourra désormais automatiquement mettre à l’échelle l’environnement de production sur le programme client en effectuant une mise à l’échelle horizontale avec les segments Dispatcher/Publish. Dans la configuration du programme, ajout de la section Mise en service qui s’affiche si la mise à l’échelle automatique est activée sur le programme client. Pour en savoir plus, consultez la section [Configuration de votre programme](setting-up-program.md).

* **Environnements** : il est maintenant possible d’afficher une vue détaillée des environnements intermédiaires et de production ainsi que la taille, le stockage, la région et l’état des nœuds associés à chaque environnement. Pour en savoir plus, consultez la section [Gestion des environnements](manage-your-environment.md).

* **Analyse de la qualité du code** : nouvelle règle pour identifier une utilisation incorrecte de l’API. Pour en savoir plus, consultez la section [Règles de qualité du code personnalisé](custom-code-quality-rules.md).

* **Tests de performance** : en consultant les résultats des tests de performance, les graphiques suivants sont disponibles : Utilisation de l’UC, Délai d’attente d’E/S de disque, Taux d’erreur de page, Utilisation de la bande passante de disque, Utilisation de la bande passante réseau, Délai de réponse de page max. et Délai de réponse de page du 95e percentile. Reportez-vous à la section *Test de performance* de la page [ Présentation des résultats des tests](understand-your-test-results.md).

* **Tests de performance** : lors de la consultation des résultats des tests de performance, la liste des erreurs de page et des demandes lentes peut être téléchargée. Reportez-vous à la section *Test de performance* de la page [Présentation des résultats des tests](understand-your-test-results.md).

## Correctifs {#bug-fixes}

* Dans certains cas, la synchronisation du système interne échouait, ce qui générait des vues incohérentes des données.
* Dans certains cas, le déclencheur manuel du pipeline n’était pas automatiquement sélectionné, ce qui entraînait des problèmes de validation de formulaire.
* Des scripts de build de clients spécifiques pouvaient entraîner des échecs lors de l’étape de génération basée sur les incompatibilités des modules externes.

## Problèmes connus {#known-issues}

* Bien que les clients puissent sélectionner le déclencheur de validation, il se peut que le pipeline ne démarre pas lors de nouvelles validations.
* La barre latérale de notification [!UICONTROL Experience Cloud] peut ne pas charger les notifications de manière cohérente. Toutefois, les notifications sont visibles dans [!UICONTROL Experience Cloud] et, si elles sont configurées, elles sont toujours envoyées par e-mail.

