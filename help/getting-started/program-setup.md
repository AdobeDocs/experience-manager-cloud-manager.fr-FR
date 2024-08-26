---
title: Configuration du programme
description: Après l’intégration, le propriétaire de l’entreprise doit effectuer une configuration initiale du programme.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 55%

---


# Configuration du programme {#program-setup}

Après l’intégration, le propriétaire de l’entreprise configure le programme en ajoutant une description et en définissant des indicateurs de performances clés (IPC). Ces indicateurs de performance clés sont ensuite utilisés pour les tests de performance.

## Configuration du programme avec [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

Pour configurer le programme et définir les KPI, procédez comme suit :

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation appropriée.

1. Cliquez sur **Configurer le programme** pour lancer le processus de configuration.

   ![Configurer le programme](/help/assets/set-up-program/setup1.png)

1. Dans la boîte de dialogue **Configurer le programme**, vous pouvez saisir les informations du programme sur trois onglets :

   * **Général**
   * **KPI**
   * **Approvisionnement**

1. Dans l’onglet **Général**, ajoutez une description pour votre programme et, éventuellement, téléchargez une miniature en cliquant sur **Modifier la photo**.

   ![Onglet Général](/help/assets/Setup_Program-General.png)

1. Dans l’onglet **KPI**, définissez vos KPI. Des KPI distincts sont définis pour **AEM Sites** et **AEM Assets**. Spécifiez les indicateurs de performance clés pour les produits sous licence que vous possédez.

   Voir la section [KPI](#kpis) pour plus de détails sur la façon dont les KPI sont mesurés dans Cloud Manager.

   ![Définition des KPI](/help/assets/Setup_Program-KPIs.png)

1. Dans l’onglet **Approvisionnement**, vous pouvez définir les options de mise à l’échelle à la demande de vos environnements si la mise à l’échelle automatique est activée pour votre programme.

   La mise à l’échelle automatique s’applique uniquement à l’environnement de production et peut ne pas être disponible pour tous les programmes clients.

   ![Options d’approvisionnement](/help/assets/Setup_Program-Provisioning.png)

1. Cliquez sur **Enregistrer**.

Votre programme est créé. L’approvisionnement des ressources peut prendre plusieurs minutes avant que le programme ne soit prêt à l’emploi.

## Modifier un programme {#editing-program}

Vous pouvez modifier les programmes une fois qu’ils ont été configurés. Pour modifier un programme, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation appropriée.

1. Accédez au programme sur l’écran d’accueil de Cloud Manager.

1. Cliquez sur **Modifier le programme** pour mettre à jour ou modifier votre programme à partir de la page **Vue d’ensemble**.

   ![Option Modifier le programme](/help/assets/set-up-program/edit-program1.png)

1. La boîte de dialogue **Modifier le programme** s’affiche, vous permettant de mettre à jour votre programme. Voir la section [Configuration du programme avec Cloud Manager](#program-setup-cloud-manager) pour plus de détails sur les champs disponibles.

   ![Boîte de dialogue Modifier le programme](/help/assets/set-up-program/edit-program-general.png)

1. Cliquez sur **Mettre à jour** pour enregistrer vos modifications.

Les modifications sont immédiatement enregistrées dans Cloud Manager, mais ne sont pas répercutées dans vos environnements avant la prochaine exécution du pipeline.

Si vous n’avez pas encore créé de pipeline, voir [Configuration des pipelines de production](/help/using/production-pipelines.md) et [Configuration des pipelines hors production](/help/using/non-production-pipelines.md).

## Basculer entre les programmes {#swithing-programs}

Lorsque vous travaillez sur un programme, vous pouvez basculer rapidement vers un autre programme sans revenir à la page de présentation de Cloud Manager.

Utilisez la barre d’actions pour passer à un autre programme, modifier le programme actuel ou ajouter un nouveau programme.

![Sélecteur de programmes](/help/assets/set-up-program/setup2.png)

## KPI {#kpis}

Les indicateurs de performance clés des sites sont mesurés sur les tests exécutés dans l’environnement intermédiaire. En règle générale, les KPI sont adaptés aux capacités de l’environnement d’évaluation.

Par exemple, un utilisateur qui attend une moyenne de 1 000 pages vues par minute dans son environnement de production et qui dispose de quatre serveurs Dispatcher/publication en production doit mettre ce scénario à l’échelle de 250 pages vues par minute. Ce scénario suppose que leur environnement d’évaluation se compose d’une seule paire de serveurs de publication/dispatcher.

Les tests de performances d’Assets impliquent le chargement répété de ressources sur une période de 30 minutes. Le temps de traitement de chaque ressource et de diverses mesures au niveau du système sont mesurés tout au long du test.

De plus, de nombreux utilisateurs disposeront d’un réseau de diffusion de contenu (CDN), tel qu’Akamai ou CloudFront devant leur environnement de production. Étant donné que [!UICONTROL Cloud Manager] effectue directement des tests par rapport à l’environnement d’évaluation, l’indicateur de performance clé doit refléter uniquement le trafic prévu pour transiter par le réseau de diffusion de contenu. C&#39;est-à-dire que le cache manque. En règle générale, cette expérience est un sous-ensemble relativement petit du trafic de production total.

## Vue d’ensemble vidéo {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
