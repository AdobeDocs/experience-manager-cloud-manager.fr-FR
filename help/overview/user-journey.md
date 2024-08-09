---
title: Parcours utilisateur
description: Ce document présente les différents scénarios d’intégration et explique comment démarrer votre parcours avec Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 94%

---


# Parcours utilisateur {#user-journey}

En tant qu’utilisateur d’Adobe Experience Manager, il se peut que vous :

* Soyez novice sur AEM.
* Utilisiez actuellement AEM 6.x.
* Deviez mettre à niveau vers AEM 6.5 pour utiliser [!UICONTROL Cloud Manager].

Ce document présente ces scénarios et explique votre parcours de prise en main de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] est disponible seulement auprès des clients d’Adobe Managed Services (AMS) qui utilisent AEM 6.4 ou une version ultérieure.

## Intégration {#onboarding}

Le processus d’intégration peut varier si vous êtes novice ou si vous êtes déjà client d’AMS.

### Novice d’Adobe Managed Services {#new-to-ams}

En tant que nouveau client, vous intégrerez [!UICONTROL Cloud Manager] dans le cadre du processus d’intégration à Adobe Managed Services.

Dans le cadre du processus d’intégration, vous recevrez un e-mail de bienvenue contenant les informations suivantes :

* URL d’accès à [!UICONTROL Cloud Manager].
* Instructions de connexion à [!UICONTROL Experience Cloud].
* Instructions d’utilisation d’Admin Console pour gérer vos utilisateurs et leurs autorisations respectives afin qu’ils puissent accéder à [!UICONTROL Cloud Manager] si nécessaire.

### Client d’Adobe Managed Services existant {#existing-customer}

En tant que client d’AMS existant, vous devrez d’abord mettre à niveau vos environnements de production et hors production vers AEM 6.4 ou ultérieure.

Lors de la mise à niveau, le système vous intégrera à Cloud Manager et fournira l’URL d’accès à [!UICONTROL Cloud Manager]. En outre, vous devrez utiliser Admin Console pour gérer les utilisateurs qui doivent accéder à [!UICONTROL Cloud Manager] ainsi que leurs autorisations respectives.

Votre projet AEM existant devra également se conformer aux bonnes pratiques recommandées, car vous commencerez à utiliser [!UICONTROL Cloud Manager] pour déployer de nouveaux changements de code dans vos environnements AEM.

Pour obtenir des informations supplémentaires sur les avantages de la mise à niveau vers AEM 6.5, consultez le document [Mise à niveau vers AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html?lang=fr).

## Accéder à [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Vous obtiendrez l’accès à [!UICONTROL Cloud Manager] et à vos environnements AEM simplement en vous connectant sur la page de destination d’[!UICONTROL Experience Cloud]. Pour ce faire, saisissez les informations d’identification qui vous ont été fournies par Adobe Identity Management et sélectionnez AEM dans l’interface de sélection de solutions.

Après la première connexion à [!UICONTROL Cloud Manager], vous avez accès à vos environnements AEM directement depuis l’interface utilisateur de [!UICONTROL Cloud Manager]. À ce stade, vous pouvez commencer à explorer toutes les possibilités offertes par [!UICONTROL Cloud Manager] et préparer votre première branche de code, à déployer dans vos environnements d’évaluation et de production.

Pour commencer à utiliser [!UICONTROL Cloud Manager], consultez le document [Première connexion](/help/getting-started/first-time-login.md).

Pour plus d’informations sur AEM, voir le document [Déploiement et maintenance](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=fr).

## Prise en main de [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Une fois la connexion à [!UICONTROL Cloud Manager] effectuée, vous pouvez commencer votre projet AEM en procédant comme suit :

1. Configurez votre environnement de référentiel de code.
1. Configurez votre équipe et les rôles.
   * Les appartenances aux rôles sont attribuées en ajoutant l’utilisateur à un profil [!UICONTROL Cloud Manager] à l’aide d’Admin Console.
1. Configurez les branches de code source dans le référentiel Git.
1. Définissez vos objectifs en termes d’ICP de charge et de performance.
1. Définissez des scénarios de test pour déployer votre code dans vos environnements d’évaluation et de production une fois toutes les vérifications de qualité effectuées avec succès.

## Parcours de bout en bout {#end-to-end-journey}

Le diagramme suivant illustre le parcours client à un haut niveau lors de l’utilisation du pipeline CI/CD de [!UICONTROL Cloud Manager] pour déployer vos changements de code dans vos environnements d’évaluation et de production.

![Parcours de bout en bout](/help/assets/screen_shot_2018-05-15at124004pm.png)
