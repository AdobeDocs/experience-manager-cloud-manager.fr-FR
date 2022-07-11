---
title: Parcours utilisateur
description: Ce document présente les différents scénarios d’intégration et explique votre parcours de prise en main de Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 11%

---


# Parcours utilisateur {#user-journey}

En tant qu’utilisateur Adobe Experience Manager, vous pouvez :

* Soyez novice en AEM.
* Utilisez actuellement AEM 6.x.
* La mise à niveau vers AEM version 6.5 doit être effectuée pour utiliser [!UICONTROL Cloud Manager].

Ce document présente ces scénarios et explique votre parcours de prise en main de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] n’est disponible que pour les clients Adobe Managed Services (AMS) utilisant AEM version 6.4 ou ultérieure.

## Intégration  {#onboarding}

Le processus d’intégration diffère selon que vous utilisez AMS ou que vous êtes déjà client AMS.

### Nouveautés d’Adobe Managed Services {#new-to-ams}

En tant que nouveau client, vous serez intégré à [!UICONTROL Cloud Manager] dans le cadre du processus d’intégration à Adobe Managed Services.

Dans le cadre du processus d’intégration, vous recevrez un e-mail de bienvenue contenant les informations suivantes :

* L’URL d’accès [!UICONTROL Cloud Manager]
* Instructions de connexion à [!UICONTROL Experience Cloud]
* Instructions d’utilisation du Admin Console pour la gestion de vos utilisateurs et de leurs autorisations respectives afin qu’ils puissent accéder à [!UICONTROL Cloud Manager] si nécessaire.

### Client Adobe Managed Services existant {#existing-customer}

En tant que client AMS existant, vous devrez d’abord mettre à niveau vos environnements de production et vos environnements hors production existants vers AEM 6.4 ou version ultérieure.

Au fur et à mesure de la mise à niveau, vous serez intégré à Cloud Manager et recevrez l’URL d’accès. [!UICONTROL Cloud Manager]. En outre, pour les utilisateurs qui doivent accéder à [!UICONTROL Cloud Manager], vous devez commencer à utiliser le Admin Console pour les gérer et leurs autorisations respectives.

Votre projet AEM existant devra également se conformer aux bonnes pratiques recommandées, car vous commencerez à utiliser [!UICONTROL Cloud Manager] pour déployer de nouveaux changements de code dans vos environnements AEM.

Pour obtenir des informations supplémentaires sur les avantages de la mise à niveau vers AEM 6.5, consultez le document [Mise à niveau vers AEM 6.5.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html)

## Accès à [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Vous aurez accès à [!UICONTROL Cloud Manager] et vos environnements AEM en vous connectant simplement à l’ [!UICONTROL Experience Cloud] landing page à l’aide de vos informations d’identification Identity Management d’Adobe et en sélectionnant AEM dans l’interface du sélecteur de solution.

Après la première connexion à [!UICONTROL Cloud Manager], vous avez accès à vos environnements AEM directement depuis l’interface utilisateur de [!UICONTROL Cloud Manager]. À ce stade, vous êtes prêt à explorer toutes les possibilités de [!UICONTROL Cloud Manager] et préparez votre première branche de code à déployer dans vos environnements intermédiaire et de production.

Pour commencer à utiliser [!UICONTROL Cloud Manager], voir le document [Première connexion](/help/getting-started/first-time-login.md).

Pour plus d’informations sur AEM, voir le document [Déploiement et maintenance.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html)

## Prise en main de [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Une fois connecté à [!UICONTROL Cloud Manager] vous pouvez commencer votre projet AEM en procédant comme suit :

1. Configuration de votre environnement de référentiel de code.
1. Configuration de votre équipe et de vos rôles.
   * Les rôles sont attribués en ajoutant un utilisateur à un [!UICONTROL Cloud Manager] profile à l’aide du Admin Console .
1. Configuration des branches de code source dans le référentiel git.
1. Définition de vos objectifs en termes d’indicateurs clés de charge et de performance.
1. Définir des scénarios de test pour déployer votre code dans vos environnements intermédiaire et de production, une fois que tous les contrôles de qualité ont été réussis.

## Parcours de bout en bout {#end-to-end-journey}

Ce diagramme illustre le parcours client à un niveau élevé lors de l’utilisation de [!UICONTROL Cloud Manager] Pipeline CI/CD pour déployer les modifications de code dans vos environnements d’évaluation et de production.

![Parcours de bout en bout](/help/assets/screen_shot_2018-05-15at124004pm.png)
