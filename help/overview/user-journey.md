---
title: Parcours d’utilisateur ou d’utilisatrice
description: Découvrez les différents scénarios d’intégration et la prise en main de Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '532'
ht-degree: 100%

---


# Parcours d’utilisateur ou d’utilisatrice {#user-journey}

En tant qu’utilisateur ou utilisatrice d’AEM (Adobe Experience Manager), vous vous trouvez probablement dans l’un des cas de figure suivants :

* Vous débutez sur AEM.
* Vous utilisez actuellement AEM 6.x.
* Vous devez effectuer la mise à niveau vers AEM 6.5 pour utiliser [!UICONTROL Cloud Manager].

Ce document présente ces trois cas de figure et explique votre parcours de prise en main de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] est disponible seulement auprès des clients d’Adobe Managed Services (AMS) qui utilisent AEM 6.4 ou une version ultérieure.

## Intégration {#onboarding}

Le processus d’intégration peut varier si vous êtes novice ou si vous êtes déjà client d’AMS.

### Novice d’Adobe Managed Services {#new-to-ams}

En tant que nouveau client ou nouvelle cliente, nous vous présenterons [!UICONTROL Cloud Manager] dans le cadre du processus d’intégration à Adobe Managed Services.

Dans le cadre du processus d’intégration, vous recevrez un e-mail de bienvenue contenant les informations suivantes :

* URL d’accès à [!UICONTROL Cloud Manager].
* Instructions de connexion à [!UICONTROL Experience Cloud].
* Instructions d’utilisation d’Admin Console pour gérer vos utilisateurs et utilisatrices et leurs autorisations respectives afin qu’ils puissent accéder à [!UICONTROL Cloud Manager] si nécessaire.

### Personne faisant déjà partie de la clientèle d’Adobe Managed Services {#existing-customer}

En tant que personne faisant déjà partie de la clientèle d’AMS, vous devrez d’abord mettre à niveau vos environnements de production et hors production vers AEM 6.4 ou une version ultérieure.

Lors de la mise à niveau, le système vous intégrera à Cloud Manager et fournira l’URL d’accès à [!UICONTROL Cloud Manager]. En outre, vous devrez utiliser Admin Console pour gérer les utilisateurs et utilisatrices qui doivent accéder à [!UICONTROL Cloud Manager] ainsi que leurs autorisations respectives.

Votre projet AEM existant devra également se conformer aux bonnes pratiques recommandées, car vous commencerez à utiliser [!UICONTROL Cloud Manager] pour déployer de nouvelles modifications de code dans vos environnements AEM.

Pour obtenir des informations supplémentaires sur les avantages de la mise à niveau vers AEM 6.5, voir [Mise à niveau vers AEM 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade).

## Accéder à [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Connectez-vous à la page de destination [!UICONTROL Experience Cloud] à l’aide de vos informations d’identification Adobe Identity Management. À partir de là, sélectionnez AEM dans le sélecteur de solution pour accéder à [!UICONTROL Cloud Manager] et à vos environnements AEM.

Après la première connexion à [!UICONTROL Cloud Manager], vous avez accès à vos environnements AEM directement depuis l’interface d’utilisation de [!UICONTROL Cloud Manager]. À ce stade, vous pouvez commencer à explorer toutes les possibilités offertes par [!UICONTROL Cloud Manager] et préparer votre première branche de code, à déployer dans vos environnements d’évaluation et de production.

Pour commencer à utiliser [!UICONTROL Cloud Manager], consultez le document [Première connexion](/help/getting-started/first-time-login.md).

Pour des informations complémentaires sur AEM, voir le document [Déploiement et maintenance](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Commencer avec [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Une fois la connexion à [!UICONTROL Cloud Manager] effectuée, vous pouvez commencer votre projet AEM en procédant comme suit :

1. Configurez votre environnement de référentiel de code.
1. Configurez votre équipe et les rôles. Les appartenances aux rôles sont attribuées en ajoutant l’utilisateur ou l’utilisatrice à un profil [!UICONTROL Cloud Manager] à l’aide d’Admin Console.
1. Configurez les branches de code source dans le référentiel Git.
1. Définissez vos objectifs en termes de KPI (indicateurs clés de performance) de charge et de performance.
1. Définissez des scénarios de test pour déployer votre code dans vos environnements d’évaluation et de production une fois toutes les vérifications de qualité effectuées.

## Parcours de bout en bout {#end-to-end-journey}

Le diagramme suivant illustre le parcours client à un haut niveau lors de l’utilisation du pipeline CI/CD de [!UICONTROL Cloud Manager] pour déployer vos modifications de code dans vos environnements d’évaluation et de production.

![Parcours de bout en bout](/help/assets/screen_shot_2018-05-15at124004pm.png)
