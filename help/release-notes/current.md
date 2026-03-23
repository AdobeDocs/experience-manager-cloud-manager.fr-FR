---
title: Notes de mise à jour de la version 2026.3.0 de Cloud Manager
description: Découvrez la version 2026.3.0 de Cloud Manager sur Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: b7e651b72d1943aef69c1c69915d4752a6163931
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 16%

---

# Notes de mise à jour de la version 2026.3.0 de Cloud Manager sur Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Découvrez la version  2026.3.0 d’Adobe Managed Services.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/home).

## Dates de publication {#release-date}

La date de publication de  2026.3.0 est le jeudi 5 mars 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prochaine version prévue est le jeudi 2 avril 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Nouveautés {#what-is-new}

* **Prise en charge de l’extensibilité de l’interface utilisateur dans AEM Experience Hub**
La prise en charge des extensions d’interface utilisateur dans [AEM Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) est désormais activée, ce qui permet aux développeurs d’étendre l’interface avec des fonctionnalités et des widgets personnalisés créés à l’aide d’Adobe App Builder.

  Pour en savoir plus, voir [AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/).

* **Les pipelines de configuration prennent désormais en charge les secrets gérés**

  Les utilisateurs peuvent désormais ajouter et gérer des secrets directement dans les pipelines de configuration de Cloud Manager. Ces secrets remplacent en toute sécurité les valeurs dans la spécification de configuration du pipeline et prennent en charge les déploiements flexibles spécifiques à un environnement.

  ![Option Afficher/Modifier les variables dans le menu déroulant d’un pipeline sélectionné](/help/release-notes/assets/view-edit-variables-option.png)
  *Option Afficher/Modifier les variables dans le menu déroulant d’un pipeline sélectionné.*

  ![Boîte de dialogue Configuration des variables &#x200B;](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*Boîte de dialogue Configuration des variables.*

* **Stabilité, performances et fiabilité améliorées**

  Cette version comprend des mises à jour d’optimisation et de maintenance qui ont amélioré la stabilité, les performances et la fiabilité de Cloud Manager.


## Programmes bêta {#beta-program}

Participez aux programmes Beta de Cloud Manager pour obtenir un accès exclusif aux fonctionnalités à venir avant leur publication générale.

Les opportunités suivantes sont actuellement disponibles :

<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

### Versions plus rapides avec mise en cache du module {#quick-build-cm-pipelines}

Un nouveau modèle de version compile uniquement les modules modifiés (plutôt que le référentiel entier) à l’aide de la mise en cache au niveau du module pour réduire les temps de création. Elle s’applique aux pipelines Qualité du code et Pile complète .

![Boîte de dialogue Modifier le pipeline hors production présentant les deux options de stratégie de création qui sont Création complète et Création intelligente](/help/release-notes/assets/non-production-pipeline-edit.png)
*Boîte de dialogue Modifier le pipeline hors production présentant les deux options de stratégie de création qui sont Création complète et Création intelligente.*

Dans la boîte de dialogue **Ajouter/Modifier un pipeline**, sous l’onglet **Code Source**, une nouvelle section **Stratégie de build** vous permet de choisir l’une des options de build suivantes :

* **Version complète** — crée tous les modules du référentiel à chaque exécution.
* **Version intelligente** : crée uniquement les modules qui ont été modifiés depuis la dernière validation, ce qui réduit la durée globale de la création.

Voir [Ajouter un pipeline hors production](/help/using/non-production-pipelines.md#add-non-production-pipeline) et [À propos de l’utilisation de la création intelligente dans un pipeline hors production](/help/using/non-production-pipelines.md#about-smart-build).

Vous contrôlez les pipelines qui utilisent **génération intelligente**. Pendant la version bêta, cette option s’affiche uniquement pour les pipelines **Qualité du code** et **Déploiement du code de pile complète de développement**.

Cela vous intéresse ? Envoyez un e-mail à l’adresse [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) avec votre ID d’organisation et votre ID de programme Adobe.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## Correctifs {#bug-fixes}

Il n’existe aucun correctif de bugs significatif dans la version de mars 2026 de Cloud Manager on AMS.

<!--
Known Issues {#known-issues}

* A 
-->
