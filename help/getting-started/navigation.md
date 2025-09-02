---
title: Navigation dans l’interface d’utilisation de Cloud Manager
description: Découvrez l’organisation de l’interface d’utilisation de Cloud Manager et comment gérer vos programmes et vos environnements.
exl-id: 9c1545ce-1c6d-417f-a6f4-fe53caef3433
source-git-commit: cc41d4716aa3c3683010b6dd392b5355b129d1ef
workflow-type: tm+mt
source-wordcount: '1530'
ht-degree: 52%

---


# Navigation dans l’interface utilisateur de Cloud Manager {#navigation}

Découvrez l’organisation de l’interface d’utilisation de Cloud Manager et comment gérer vos programmes et vos environnements.

L’interface d’utilisation de Cloud Manager est composée principalement de deux interfaces graphiques :

* [La console Mes programmes](#my-programs-console) permet d’afficher et de gérer tous vos programmes.
* [La fenêtre Vue d’ensemble du programme](#program-overview) permet de consulter les détails d’un programme individuel et de le gérer.

## Console Mes programmes {#my-programs-console}

Lorsque vous vous connectez à Cloud Manager à l’adresse [experience.adobe.com](https://experience.adobe.com/experiencemanager) et sélectionnez l’organisation appropriée, vous accédez à la console **Mes programmes**.

![Console Mes programmes](/help/getting-started/assets/cloud-manager-my-programs-console.png)

La console **Mes programmes** donne un aperçu de tous les programmes auxquels vous avez accès dans l’organisation sélectionnée. Elle est constituée de plusieurs éléments.

|   | Aire | Description |
| --- | --- | --- |
| 1 | [ Barres d’outils ](#toolbars-my-programs-toolbars) | À utiliser pour la sélection d’organisations, les alertes et les paramètres de compte. |
| 2 | Onglet du panneau latéral gauche | Différents onglets vous permettent d’activer/désactiver l’affichage actuel de vos programmes, notamment <br><ul><li>**Experience Manager** ouvre la page d’accueil de vos différentes solutions AEM</li><li>**Tous les programmes** qui affiche tous les programmes disponibles.</li><li>**Licence** ouvre le tableau de bord des licences. Le tableau de bord des licences s’applique uniquement aux *programmes AEM as a Cloud Service* (AEMaaCS), et non aux programmes Adobe Managed Services tels qu’AEM 6.5 et AEM 6.5 LTS. Pour déterminer le type de service de votre programme (AEMaaCS ou AMS), consultez la section [Cartes de programme](#program-cards) de cet article. Par défaut, les onglets sont fermés et peuvent être affichés à l’aide du menu déroulant ![icône Afficher le menu, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) situé sur le côté gauche de l’en-tête de [Cloud Manager](#cloud-manager-header).</li></ol> |
| 3 | [Mes programmes](#my-programs-section) | Répertorie tous les programmes disponibles que vous pouvez sélectionner.<br>Voir [Programmes et types de programmes](/help/getting-started/program-setup.md) pour plus d’informations sur les programmes. |
| 4 | [Appels à l’action et statistiques](#cta-statistics) | Donne un aperçu de votre activité récente. |
| 5 | [Liens rapides ](#quick-links) | Accès rapide aux ressources associées. |


### Barres d’outils {#my-programs-toolbars}

Il y a deux barres d’outils superposées.

#### En-tête de Cloud Manager {#cloud-manager-header}

Le premier est l’en-tête de Cloud Manager. L’en-tête est persistant lorsque vous naviguez dans Cloud Manager. Il s’agit d’un élément ancré qui permet d’accéder aux paramètres et aux informations relatifs à l’ensemble des programmes Cloud Manager.

![En-tête Experience Cloud](/help/getting-started/assets/cloud-manager-header-toolbar.png)

| Aire | Description |
| --- | --- |
| ![Afficher l&#39;icône du menu, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) | Un menu déroulant qui permet d’accéder à des onglets pour des parties spécifiques d’un programme individuel.<br>Pour déterminer le type de service de votre programme (AMS ou AEMaaCS), reportez-vous à la section [Cartes de programme](#program-cards) de ce document. |
| ![Icône rouge et blanche Adobe ](/help/getting-started/assets/AdobeLogoWhiteOnRed.svg) Cloud Manager | Cliquez pour ouvrir la console **Mes programmes** de Cloud Manager, où que vous soyez dans Cloud Manager. |
| *`Name of selected organization`* | Le sélecteur d’organisation affiche l’organisation dans laquelle vous êtes actuellement connecté (dans cet exemple, *Interne Foundation*). Cliquez pour passer à une autre organisation si votre Adobe ID est associé à plusieurs organisations. |
| ![Icône Commentaires](/help/getting-started/assets/AppComment.svg) Commentaires | Cliquez pour fournir des commentaires à Adobe à propos de Cloud Manager. |
| ![Icône de l’assistant AI](/help/getting-started/assets/AIChat.svg) | L’assistant d’IA offre une interface conversationnelle conçue pour rationaliser la recherche de réponses à vos requêtes liées à AEM. Voir [Assistant IA](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/ai-assistant/ai-assistant-in-aem) |
| ![Icône d’aide](https://spectrum.adobe.com/static/icons/workflow_18/Smock_HelpOutline_18_N.svg) | Cliquez pour fournir un accès rapide aux ressources d’apprentissage et de support. |
| ![Icône de cloche blanche](/help/getting-started/assets/Bell.svg) | Cliquez pour afficher le nombre de [notifications](/help/using/notifications.md) incomplètes actuellement attribuées. |
| ![Icône Applications](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) | Cliquez pour passer rapidement de la page d’accueil d’AEM aux solutions AEM |
| *`Dynamic Account icon`* | Cliquez sur la photo de l’utilisateur pour accéder à vos **Paramètres du compte** et **Paramètres du programme** ou pour vous déconnecter.<br>Si vous choisissez de ne pas ajouter d’image d’utilisateur, une icône est attribuée de manière aléatoire (comme illustré dans l’image de la barre d’outils ci-dessus). |

<!--
1. The ![Show menu icon, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) icon on the left side of the header is  
   * The License Dashboard only applies to AEM as a Cloud Service programs, not AMS programs.
   * To determine the type of service your program has (AMS or AEMaaCS), see the [Program Cards section](#program-cards) of this document.
1. The **Adobe Cloud Manager** button takes you back to the **My Programs** console of Cloud Manager no matter where you are in Cloud Manager.
1. Click **Feedback** to provide feedback to Adobe about Cloud Manager.
1. The organization selector displays the organization that you are currently signed into (in this example, Foundation Internal). Click to switch to another organization if your Adobe ID is associated with multiple.
1. Clicking the solutions switcher lets you quickly jump to other Experience Cloud solutions.
1. The Help icon provides quick access to learning and support resources.
1. The notifications icon is badged with the number of currently assigned incomplete [notifications](/help/using/notifications.md)
1. Select the icon representing your user to access your user settings. If you do not select a user picture, an icon is randomly assigned. -->

#### Barre d’outils du programme {#program-toolbar}

La barre d’outils des programmes fournit des liens pour basculer entre les programmes Cloud Manager et des actions contextuelles.

Barre d&#39;outils du programme Cloud Manager ![](/help/getting-started/assets/cloud-manager-programs-toolbar.png)

|   | Aire | Description |
| --- | --- | --- |
| 1 | Mes programmes | Cliquez pour ouvrir une liste déroulante dans laquelle vous pouvez choisir d’ajouter un programme, de sélectionner d’autres programmes existants ou de revenir à la page d’accueil d’Experience Manager. |
| 2 | ![Icône Infos](/help/getting-started/assets/Info.svg) Prise en main | Cliquez sur pour accéder au [parcours de documentation d’intégration](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/onboarding/journey/overview) afin de vous familiariser avec Cloud Manager.<br>Le parcours d’intégration est conçu pour Cloud Manager sur Adobe Experience Manager as a Cloud Service (AEMaaCS) et non pour Cloud Manager sur Adobe Managed Services (AMS). Cependant, de nombreux concepts sont identiques. |
| 3 | *`Dynamic action button`* | Le bouton d’action propose des actions contextuelles sur lesquelles vous pouvez cliquer, telles que **Ajouter un programme** (illustré dans l’exemple ci-dessus) ou ajouter un domaine. |

### Appels à l’action et statistiques {#cta-statistics}

La section Appels à l’action et statistiques fournit des données agrégées pour votre organisation. Par exemple, si vous avez terminé de configurer vos programmes, les statistiques de vos activités des 90 derniers jours peuvent s’afficher, incluant ce qui suit :

* Le nombre de [déploiements](/help/using/code-deployment.md)
* Le nombre de [problèmes relatifs à la qualité du code](/help/using/code-quality-testing.md) identifiés
* Le nombre de versions

Si vous êtes au commencement de la configuration de votre organisation, vous pouvez obtenir des conseils sur les étapes suivantes ou des ressources de documentation.

### Mes programmes {#my-programs-section}

Le contenu principal de la console Mes programmes est la section **Mes programmes** qui répertorie vos programmes sous la forme de cartes individuelles. Cliquez sur une carte pour accéder à la page **Vue d’ensemble du programme** du programme concerné pour obtenir plus d’informations sur le programme.

Selon vos privilèges, il se peut que vous ne puissiez pas sélectionner certains programmes.

Vous pouvez utiliser les options de tri suivantes pour trouver rapidement le programme souhaité :

![Options de tri](/help/getting-started/assets/cloud-manager-my-programs-sorting.png)

* Trier par :
   * Date de création
   * Nom du programme
   * Statut
* ![Icône Trier vers le bas](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderDown_18_N.svg) / ![Icône Trier vers le haut](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderUp_18_N.svg) Trier les programmes vers le bas ou vers le haut, respectivement.
* ![Icône classique de la vue grille](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ClassicGridView_18_N.svg) / ![Icône ou liste à puces de texte](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TextBulleted_18_N.svg) Affichez les programmes sous forme de grille ou de liste, respectivement.

#### Cartes de programme {#program-cards}

Une carte ou une ligne dans un tableau représente chaque programme et propose une vue d’ensemble du programme et des liens rapides permettant d’agir.

![Vignette du programme](/help/getting-started/assets/cloud-manager-program-card.png)

* Image du programme (si configurée)
* Nom du programme (dans l’exemple ci-dessus, *WKND Magazine*)
* Type de service :
   * **Experience Manager** pour les programmes AMS
   * **Cloud Experience Manager** pour les [programmes AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/home)
* Statut (dans l’exemple ci-dessus, *Prêt*)
* Solutions configurées
* Date de création

Cliquez sur ![Icône Infos](/help/getting-started/assets/Info.svg) pour accéder rapidement à des informations supplémentaires sur le programme (utiles dans la vue Liste).

![Fenêtre contextuelle d’informations dans Cloud Manager AMS](/help/getting-started/assets/cloud-manager-information-view.png)

Cliquez sur ![icône Plus, points de suspension](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) pour accéder à des actions supplémentaires que vous pouvez effectuer sur le programme.

![Bouton représentant des points de suspension pour les programmes](/help/getting-started/assets/cloud-manager-program-ellipsis.png)

* Page de départ Experience Manager
* Accéder à un [environnement](/help/using/managing-environments.md) particulier du programme
* Ouvrir la [vue d’ensemble du programme](#program-overview)
* [Modifier le programme](/help/getting-started/program-setup.md)
* Afficher la surveillance

### Liens rapides {#quick-links}

La section Liens rapides donne accès à des ressources connexes utiles.

## Fenêtre Vue d’ensemble du programme {#program-overview}

Si vous sélectionnez un programme dans la console [**Mes programmes**](#my-programs-console), vous accédez à la page **Vue d’ensemble du programme**.

![Vue d’ensemble du programme](/help/getting-started/assets/cloud-manager-program-overview.png)

**Présentation du programme** vous donne accès à tous les détails d’un programme Cloud Manager. Comme **Mes programmes**, il est composé de plusieurs parties.

1. Des [barres d’outils](#program-overview-toolbar) pour revenir rapidement à la console **Mes programmes** et naviguer dans le programme.
1. [Zone des onglets](#program-tabs) pour basculer entre les différents aspects du programme.
1. Un [appel à l’action](#cta) basé sur les dernières actions du programme.
1. Associé [Environnements](#environments) du programme.
1. Pipelines [Pipelines](#pipelines) associés du programme.

### Barres d’outils {#program-overview-toolbar}

Les barres d’outils de la Vue d’ensemble du programme sont similaires à celles de la [console Mes programmes](#my-programs-toolbars). Seules les différences sont indiquées ici.

#### En-tête de Cloud Manager {#cloud-manager-header-2}

L’en-tête Cloud Manager comporte un menu déroulant ![icône Afficher le menu, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) qui s’ouvre automatiquement pour afficher les onglets navigables de la Présentation du programme.

Cliquez sur ![Afficher l’icône de menu, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour masquer les onglets.

#### Barre d’outils du programme {#program-toolbar-2}

La barre d’outils du programme permet de basculer rapidement vers d’autres programmes, mais permet également d’accéder à des actions contextuelles telles que l’ajout et la modification du programme.

![Barre d’outils du programme](assets/cloud-manager-program-toolbar.png)

De plus, si vous masquez les onglets à l’aide de ![Afficher l’icône du menu, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), la barre d’outils peut toujours afficher l’onglet sur lequel vous vous trouvez actuellement.

### Onglets des programmes {#program-tabs}

Chaque programme comporte de nombreuses options et des données associées. Ces données sont regroupées dans des onglets afin de faciliter la navigation dans le programme. Les onglets permettent d’accéder aux éléments suivants :

* Vue d’ensemble : vue d’ensemble du programme, telle que décrite dans le présent document.
* [Activité](/help/using/managing-pipelines.md#activity) : historique des exécutions de pipeline du programme.
* [Pipelines](/help/using/managing-pipelines.md#pipelines) : tous les pipelines configurés pour le programme.
* [Référentiels](/help/managing-code/managing-repositories.md) : tous les référentiels configurés pour le programme.
* [Rapports](/help/using/monitoring-environments.md#system-monitoring-overview) : mesures, telles que les données SLA.
* [Environnements](/help/using/managing-environments.md) : tous les environnements configurés pour le programme.
* [Jeux de contenu](/help/using/content-copy.md) : jeux de contenu créé à des fins de copie.
* [Activité Copie de contenu](/help/using/content-copy.md) : activités de copie de contenu.
* Parcours de formation : ressources de formation supplémentaires pour Cloud Manager.

Par défaut, lorsque vous ouvrez un programme, vous accédez à l’onglet **Vue d’ensemble**. L’onglet actif est mis en surbrillance. Sélectionnez un autre onglet pour afficher ses détails.

Utilisez ![Afficher l’icône de menu, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) dans l’en-tête [Cloud Manager](#cloud-manager-header-2) pour masquer les onglets.

### Appel à l’action {#cta}

La section Appel à l’action fournit des informations utiles en fonction du statut de votre programme. Pour un nouveau programme, vous verrez peut-être les prochaines étapes, ainsi qu’un rappel d’une date de mise en service, [définie lors de la création du programme](/help/getting-started/program-setup.md).

Pour un programme actif, vous pouvez voir le statut de votre dernier déploiement accompagné de liens pour obtenir plus de détails pour démarrer un nouveau déploiement.

![Appel à l’action](assets/info-banner.png)

### Carte Environnements {#environments}

La carte **Environnements** vous fournit une vue d’ensemble de vos environnements, ainsi que des liens vers les actions rapides.

La carte **Environnements** répertorie seulement trois environnements. Cliquez sur **Tout afficher** pour voir tous les environnements du programme.

Voir la section [Gérer les environnements](/help/using/managing-environments.md) pour plus d’informations sur la gestion de vos environnements.

### Carte Pipelines {#pipelines}

La carte **Pipelines** fournit une vue d’ensemble de vos pipelines ainsi que des liens vers les actions rapides.

La vignette **Pipelines** répertorie seulement trois pipelines. Cliquez sur **Tout afficher** pour voir tous les pipelines du programme.

Voir la section [Gérer les pipelines](/help/using/managing-pipelines.md) pour plus d’informations sur la gestion des pipelines.

### Ressources utiles {#useful-resources}

La section **Ressources utiles** fournit des liens vers des ressources de formation supplémentaires pour Cloud Manager.
