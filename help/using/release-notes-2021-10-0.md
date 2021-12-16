---
title: Notes de mise à jour de la version 2021.10.0
description: Consultez cette page pour obtenir des informations sur la version 2021.10.0 de Cloud Manager
feature: Release Information
source-git-commit: 09dd8fe608d95cd9dbc95129cf86b9693c2839b5
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 100%

---

# Notes de mise à jour de la version 2021.10.0 {#release-notes-for}

La section ci-dessous présente les notes générales de mise à jour de la version 2021.10.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>Reportez-vous aux [Notes de mise à jour actuelles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=fr#getting-access) pour consulter les dernières notes de mise à jour de Cloud Manager dans AEM as a Cloud Service.

## Date de publication {#release-date}

[!UICONTROL Cloud Manager] version 2021.10.0 a été publié le 14 octobre 2021.

## Nouveautés {#whats-new}

* Les pipelines de production peuvent désormais être exécutés en mode « d’urgence », en contournant les étapes de test de sécurité et de performance pour les déploiements d’urgence.

* Pour des raisons de cohérence avec Cloud Service, les pipelines de production existants seront désormais référencés et étiquetés dans l’interface utilisateur en tant que pipelines « Pile complète » (Full Stack).

* La carte Pipeline a été actualisée afin d’afficher désormais une seule face intégrée qui affiche les pipelines de production et hors production. L’utilisateur peut sélectionner Exécuter/Pause/Reprendre directement dans le menu d’actions associé à chaque pipeline.

* Un utilisateur disposant du rôle Gestionnaire de déploiement peut désormais supprimer le pipeline de production en libre-service via l’interface utilisateur.

* Les expériences d’ajout et de modification de pipeline ont été actualisées afin d’utiliser désormais des modèles familiers et modernes.

* Les utilisateurs de Cloud Manager peuvent désormais envoyer des commentaires directement depuis l’interface utilisateur via **Commentaires** en haut à droite de la page d’accueil.

* Les graphiques annuels de SLA peuvent désormais être téléchargés à partir de l’interface utilisateur de Cloud Manager.

* Les exécutions de pipeline de qualité de code et hors production utilisent désormais un processus de clonage superficiel plus efficace au cours de l’étape de création, ce qui accélère la création pour les clients disposant de référentiels Git particulièrement volumineux.

* La documentation de l’API Cloud Manager comprend désormais un laboratoire interactif qui permet aux utilisateurs connectés de tester l’API depuis leur navigateur. Consultez [Laboratoire de l’API Cloud Manager](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) pour plus d’informations.

* L’info-bulle de la carte Programme offre des informations plus détaillées si une option de sélection est désactivée sous Accéder à. « Aucun environnement de production n’existe » s’affichera désormais.


## Correctifs {#bug-fixes}

* Lorsque les données lues à partir des systèmes internes n’étaient pas entrées correctement, cela pouvait entraîner la restitution incorrecte des données non liées fournies par les ingénieurs de service client dans Cloud Manager.

* Dans des situations client spécifiques, les artefacts non valides téléchargés lors de l’étape de création qui auraient dû entraîner l’échec de la création étaient ignorés.
