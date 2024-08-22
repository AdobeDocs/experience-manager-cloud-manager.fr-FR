---
title: Parcours utilisateur
description: Découvrez les différents scénarios d’intégration et la prise en main de Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 24%

---


# Parcours utilisateur {#user-journey}

En tant qu’utilisateur d’AEM (Adobe Experience Manager), vous pouvez probablement réaliser l’un des scénarios suivants :

* Tu es nouveau à AEM.
* Vous utilisez actuellement AEM 6.x.
* Vous devez effectuer la mise à niveau vers AEM 6.5 pour utiliser [!UICONTROL Cloud Manager].

Ce document présente ces trois scénarios et explique votre parcours à prendre en main [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] est disponible seulement auprès des clients d’Adobe Managed Services (AMS) qui utilisent AEM 6.4 ou une version ultérieure.

## Intégration {#onboarding}

Le processus d’intégration peut varier si vous êtes novice ou si vous êtes déjà client d’AMS.

### Novice d’Adobe Managed Services {#new-to-ams}

En tant que nouveau client, vous allez être intégré à [!UICONTROL Cloud Manager] dans le cadre du processus d’intégration à Adobe Managed Services.

Dans le cadre du processus d’intégration, vous recevez un e-mail de bienvenue contenant les informations suivantes :

* URL d’accès à [!UICONTROL Cloud Manager].
* Instructions pour se connecter à [!UICONTROL Experience Cloud].
* Instructions d’utilisation d’Admin Console pour gérer vos utilisateurs et leurs autorisations respectives afin qu’ils puissent accéder à [!UICONTROL Cloud Manager] si nécessaire.

### Client Managed Services Adobe actuel {#existing-customer}

En tant que client AMS existant, vous devez d’abord mettre à niveau vos environnements de production et vos environnements hors production existants vers AEM version 6.4 ou ultérieure.

Pendant la mise à niveau, vous êtes intégré à Cloud Manager et vous recevez l’URL pour accéder à [!UICONTROL Cloud Manager]. De plus, pour les utilisateurs qui doivent accéder à [!UICONTROL Cloud Manager], vous devez commencer à utiliser l’Admin Console pour les gérer et leurs autorisations respectives.

Votre projet AEM existant doit également se conformer aux bonnes pratiques recommandées, car vous commencez à utiliser [!UICONTROL Cloud Manager] pour déployer de nouveaux changements de code dans vos environnements AEM.

Pour obtenir des informations supplémentaires sur les avantages de la mise à niveau vers AEM 6.5, voir [Mise à niveau vers AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade).

## Accès à [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Connectez-vous à la page d’entrée [!UICONTROL Experience Cloud] à l’aide de vos informations d’identification Identity Management d’Adobe. À partir de là, sélectionnez AEM dans le sélecteur de solution pour accéder à [!UICONTROL Cloud Manager] et à vos environnements AEM.

Après vous être connecté à [!UICONTROL Cloud Manager] pour la première fois, vous avez accès à vos environnements AEM directement depuis l’interface utilisateur de [!UICONTROL Cloud Manager]. À ce stade, vous pouvez commencer à explorer toutes les possibilités offertes par [!UICONTROL Cloud Manager] et préparer votre première branche de code, à déployer dans vos environnements d’évaluation et de production.

Pour commencer à utiliser [!UICONTROL Cloud Manager], reportez-vous à la section [Première connexion](/help/getting-started/first-time-login.md).

Pour plus d’informations sur les AEM, voir [Déploiement et maintenance](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Prise en main de [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Après vous être connecté à [!UICONTROL Cloud Manager], vous pouvez commencer votre projet AEM en procédant comme suit :

1. Configurez votre environnement de référentiel de code.
1. Configurez votre équipe et vos rôles. Les appartenances aux rôles sont attribuées en ajoutant l’utilisateur à un profil [!UICONTROL Cloud Manager] à l’aide d’Admin Console.
1. Configurez vos branches de code source dans le référentiel Git.
1. Définissez vos objectifs en termes d’indicateurs clés de charge et de performance (indicateurs de performance clés).
1. Définissez des scénarios de test pour déployer votre code correctement dans vos environnements intermédiaire et de production une fois tous les contrôles de qualité terminés.

## Parcours de bout en bout {#end-to-end-journey}

Ce diagramme illustre le parcours client à un niveau élevé lors de l’utilisation du pipeline CI/CD [!UICONTROL Cloud Manager] pour déployer vos modifications de code dans vos environnements d’évaluation et de production.

![Parcours de bout en bout](/help/assets/screen_shot_2018-05-15at124004pm.png)
