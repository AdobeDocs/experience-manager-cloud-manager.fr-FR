---
title: Notes de mise à jour de la version 2021.10.0
description: Consultez cette page pour obtenir des informations sur la version 2021.10.0 de Cloud Manager
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: b28f8f1bedb92428d332716510cbf0fd714fada6
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 20%

---

# Notes de mise à jour de la version 2021.10.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.10.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>Reportez-vous aux [Notes de mise à jour actuelles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr#getting-access) pour consulter les dernières notes de mise à jour de Cloud Manager dans AEM as a Cloud Service.

## Date de publication {#release-date}

[!UICONTROL Cloud Manager] version 2021.10.0 a été publié le 14 octobre 2021.
La prochaine version est prévue pour le 4 novembre 2021.

## Nouveautés {#whats-new}

* Les pipelines de production peuvent désormais être exécutés en mode &quot;urgence&quot;, en contournant les étapes de test de sécurité et de performance pour les déploiements d’urgence.

* Pour des raisons de cohérence avec Cloud Service, les pipelines de déploiement existants seront désormais référencés et étiquetés dans l’interface utilisateur comme pipelines &quot;Pile complète&quot;.

* La carte du pipeline a été actualisée afin d’afficher désormais une seule face intégrée qui affiche les pipelines de production et hors production. L’utilisateur peut sélectionner Exécuter/Pause/Reprendre directement dans le menu d’actions associé à chaque pipeline.

* Un utilisateur disposant du rôle Gestionnaire de déploiement peut désormais supprimer le pipeline de production en libre-service via l’interface utilisateur.

* L’ajout et la modification d’expériences de pipeline ont été actualisés afin d’utiliser désormais des modèles familiers et modernes.

* Les utilisateurs de Cloud Manager peuvent désormais envoyer leurs commentaires directement depuis l’interface utilisateur via le bouton **Commentaires** en haut à droite de la page d’entrée.

* Les graphiques SLA annuels peuvent désormais être téléchargés à partir de l’interface utilisateur de Cloud Manager.

* Les exécutions de pipeline de qualité de code et hors production utilisent désormais un processus de clonage superficiel plus efficace au cours de l’étape de création, ce qui accélère la création pour les clients disposant de référentiels Git particulièrement volumineux.

* La documentation de l’API Cloud Manager comprend désormais un terrain de lecture interactif qui permet aux utilisateurs connectés de tester l’API depuis leur navigateur. Voir [Jeu d’API Cloud Manager](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) pour plus d’informations.

* L’info-bulle de la carte Programme est plus descriptive si une option de sélection sous &quot;Accéder à&quot; est désactivée. Il dira désormais &quot;Aucun environnement de production n’existe&quot;.


## Correctifs {#bug-fixes}

* Lorsque les données lues à partir des systèmes internes n’étaient pas entrées correctement, cela pouvait entraîner le mauvais reflet des données non liées fournies par les ingénieurs du service client dans Cloud Manager.

* Dans des situations client spécifiques, les artefacts non valides téléchargés lors de l’étape de création qui aurait dû entraîner l’échec de la version étaient ignorés.
