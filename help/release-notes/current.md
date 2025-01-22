---
title: Notes de mise à jour de la version 2025.1.0 de Cloud Manager
description: En savoir plus sur la version 2025.1.0 de Cloud Manager dans Adobe Managed Services.
feature: Release Information
source-git-commit: c25508b24f00b8f8cfa7bae3cc4b0d6ecf684db3
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 40%

---

# Notes de mise à jour de Cloud Manager 2025.1.0 dans Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Découvrez la version de [!UICONTROL Cloud Manager] 2025.1.0 dans Adobe Managed Services.

>[!NOTE]
>
>Consultez les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/home).

## Dates de publication {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

La date de publication de la version 2025.1.0 de [!UICONTROL Cloud Manager] est le mardi 22 janvier 2024.

La prochaine version est prévue le vendredi 13 février 2025.

## Nouveautés {#what-is-new}

**Règles de qualité du code :** l’étape de qualité du code Cloud Manager commencera à utiliser SonarQube Server 9.9 avec la version Cloud Manager 2025.2.0, prévue pour le jeudi 13 février 2025.

Pour vous préparer, les règles SonarQube mises à jour sont désormais disponibles à l’adresse [Règles de qualité du code](/help/using/code-quality-testing.md#code-quality-testing-step).

Vous pouvez « vérifier rapidement » les nouvelles règles en définissant la variable de texte de pipeline suivante (voir la capture d’écran ci-dessous) :

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

En outre, définissez la variable suivante pour vous assurer que l’étape de qualité du code s’exécute pour la même validation (normalement ignorée pour la même `commitId`) :

`CM_DISABLE_BUILD_REUSE` = `true`

![Page de configuration des variables](/help/release-notes/assets/variables-config.png)

>[!NOTE]
>
>Adobe recommande de créer un pipeline de qualité du code CI/CD, configuré sur la même branche que votre pipeline de production principal. Définissez les variables appropriées *avant* dans la version du 13 février 2025 pour vérifier que les nouvelles règles appliquées n’introduisent pas de bloqueurs.

<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
