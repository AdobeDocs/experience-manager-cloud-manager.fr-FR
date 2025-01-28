---
title: Notes de mise à jour de la version 2025.1.0 de Cloud Manager
description: En savoir plus sur la version 2025.1.0 de Cloud Manager dans Adobe Managed Services.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: ca9a07354ff8316f531840a42d6ecdda5c072b9b
workflow-type: ht
source-wordcount: '196'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager 2025.1.0 dans Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Découvrez la version de [!UICONTROL Cloud Manager] 2025.1.0 dans Adobe Managed Services.

>[!NOTE]
>
>Consultez les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/home).

## Dates de publication {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

La date de publication de la version 2025.1.0 de [!UICONTROL Cloud Manager] est le mercredi 22 janvier 2024.

La prochaine version est prévue le jeudi 13 février 2025.

## Nouveautés {#what-is-new}

**Règles de Qualité du code - Mise à niveau de SonarQube :** l’étape de Qualité du code Cloud Manager commencera à utiliser SonarQube Server 9.9 avec la version 2025.2.0 de Cloud Manager, prévue le jeudi 13 février 2025.

Pour vous préparer, les règles SonarQube mises à jour sont désormais disponibles dans [Règles de Qualité du code](/help/using/code-quality-testing.md#code-quality-testing-step).

Vous pouvez consulter les nouvelles règles de façon anticipée en définissant la variable de texte de pipeline suivante (voir la capture d’écran ci-dessous) :

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

Définissez également la variable suivante pour vous assurer que l’étape de Qualité du code s’exécute pour la même validation (normalement ignorée pour le même `commitId`) :

`CM_DISABLE_BUILD_REUSE` = `true`

![Page de configuration des variables](/help/release-notes/assets/variables-config.png)

>[!NOTE]
>
>Adobe recommande de créer un pipeline de Qualité du code CI/CD, configuré sur la même branche que votre pipeline de production principal. Définissez les variables appropriées *avant* la version du 13 février 2025 pour vérifier que les nouvelles règles appliquées n’introduisent pas de bloqueurs.

<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
