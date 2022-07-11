---
title: Configuration du programme
description: Après l’intégration, le propriétaire de l’entreprise devra effectuer une configuration initiale du programme.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 22%

---


# Configuration du programme {#program-setup}

Après l’intégration, le propriétaire de l’entreprise termine la configuration initiale du programme, y compris la définition de la description du programme et la définition des indicateurs de performance clés (IPC), qui sont utilisés pour les tests de performance.

## Configuration du programme avec [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

Pour configurer le programme et définir les indicateurs de performance clés, procédez comme suit :

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation appropriée.

1. Cliquez sur **Configuration du programme** pour lancer le processus de configuration.

   ![Configuration du programme](/help/assets/set-up-program/setup1.png)

1. Dans le **Configuration du programme** vous pouvez saisir les informations du programme dans trois onglets :

   * **Général**
   * **KPI**
   * **Configuration**

1. Sur le **Général** , ajoutez une description pour votre programme et, éventuellement, téléchargez une miniature en cliquant sur **Modifier la photo**.

   ![Onglet Général](/help/assets/Setup_Program-General.png)

1. Sur le **KPI** , définissez vos indicateurs de performance clés. Dans cet exemple, des indicateurs de performance clés distincts sont définis pour **AEM Sites** et **AEM Assets**. Vous pouvez spécifier les indicateurs de performance clés pour les produits sous licence que vous possédez.

   * Voir la section [IPC](#kpis) pour plus d’informations sur la manière dont les indicateurs de performance clés sont mesurés dans Cloud Manager.

   ![Définition des indicateurs clés de performance](/help/assets/Setup_Program-KPIs.png)

1. Sur le **Mise en service** vous pouvez définir les options de mise à l’échelle à la demande de vos environnements si la mise à l’échelle automatique est activée pour votre programme.

   * La mise à l’échelle automatique s’applique uniquement à l’environnement de production et peut ne pas être disponible pour tous les programmes clients.

   ![Options de configuration](/help/assets/Setup_Program-Provisioning.png)

1. Cliquez sur **Enregistrer** pour terminer l’assistant de configuration.

Votre programme sera créé. Plusieurs minutes peuvent s’écouler avant que les ressources ne soient mises en service avant que le programme ne soit prêt à l’emploi.

## Modification d’un programme {#editing-program}

Vous pouvez modifier les programmes une fois qu’ils ont été configurés. Pour modifier un programme, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) et sélectionnez l’organisation appropriée.

1. Accédez au programme sur l’écran d’accueil de Cloud Manager.

1. Cliquez sur **Modifier le programme** pour mettre à jour ou modifier votre programme à partir du **Présentation** page.

   ![Option Modifier le programme](/help/assets/set-up-program/edit-program1.png)

1. Le **Modifier le programme** s’affiche, ce qui vous permet de mettre à jour votre programme. Voir la section [Configuration du programme avec Cloud Manager](#program-setup-cloud-manager) pour plus d’informations sur les champs disponibles.

   ![Boîte de dialogue Modifier le programme](/help/assets/set-up-program/edit-program-general.png)

1. Cliquez sur **Mettre à jour** pour enregistrer vos modifications.

Notez que les modifications sont enregistrées immédiatement dans Cloud Manager, mais ne seront pas répercutées dans vos environnements avant la prochaine exécution du pipeline.

Si vous n’avez pas encore créé de pipeline, consultez les documents [Configuration des pipelines de production](/help/using/production-pipelines.md) et [Configuration de pipelines hors production.](/help/using/non-production-pipelines.md)

## Changement de programme {#swithing-programs}

Lorsque vous travaillez sur un programme, vous pouvez passer rapidement à un autre programme sans revenir à la page d’aperçu de Cloud Manager.

Utilisez la barre d’actions pour passer à un autre programme, modifier le programme actuel ou ajouter un nouveau programme.

![Sélecteur de programme](/help/assets/set-up-program/setup2.png)

## IPC {#kpis}

Les indicateurs de performance clés des sites sont mesurés sur les tests exécutés dans l’environnement d’évaluation. En règle générale, ces indicateurs de performance clés sont réduits pour s’adapter aux fonctionnalités de l’environnement d’évaluation.

Par exemple, un utilisateur qui attend une moyenne de 1 000 pages vues par minute dans son environnement de production et qui dispose de quatre dispatchers/serveurs de publication en production doit réduire cette valeur à 250 pages vues par minute. Cela suppose que leur environnement d’évaluation se compose d’une seule paire de serveurs de publication/dispatcher.

Les tests de performance des ressources sont effectués en chargeant plusieurs ressources à plusieurs reprises pendant une période de test de 30 minutes et en mesurant le temps de traitement de chaque ressource ainsi que diverses mesures au niveau du système.

Vous pouvez disposer d’un réseau de diffusion de contenu (CDN) tel qu’Akamai ou CloudFront devant votre environnement de production. Depuis [!UICONTROL Cloud Manager] tests directement par rapport à l’environnement d’évaluation, l’indicateur de performance clé doit refléter uniquement le trafic prévu pour passer par le réseau de diffusion de contenu, c’est-à-dire les pertes de cache. En règle générale, il s’agira d’un sous-ensemble relativement petit du trafic de production total.

## Présentation vidéo {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
