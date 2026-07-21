---
title: Intégration des utilisateurs
description: Découvrez les différents scénarios d’intégration et la prise en main de Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
TQID: https://experienceleague.adobe.com/EnNaMZzu5bLUD3Jjsp6ovqFvoFM30ju4FOQJfmySLEk
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 2cd89edca1c1dfac7f1b7b68eccdf1416efb4724
workflow-type: tm+mt
source-wordcount: 567
ht-degree: 62%

---

# Intégration des utilisateurs {#user-journey}

En tant qu’utilisateur d’AEM (Adobe Experience Manager), vous êtes dans l’un des scénarios suivants :

* Vous débutez sur AEM.
* Vous utilisez actuellement AEM 6.x.
* Vous devez effectuer la mise à niveau vers AEM 6.5 pour utiliser [!UICONTROL Cloud Manager].

Ce document décrit ces trois scénarios et explique le processus de prise en main de .

>[!NOTE]
>
>[!UICONTROL Cloud Manager] est disponible seulement auprès des clients d’Adobe Managed Services (AMS) qui utilisent AEM 6.4 ou une version ultérieure.

## Intégration {#onboarding}

Le processus d’intégration peut varier si vous êtes novice ou si vous êtes déjà client d’AMS.

### Novice d’Adobe Managed Services {#new-to-ams}

En tant que nouveau client, vous intégrez  dans le cadre du processus d’intégration à Adobe Managed Services.

Dans le cadre du processus d’intégration, vous recevrez un e-mail de bienvenue contenant les informations suivantes :

* URL d’accès à [!UICONTROL Cloud Manager].
* Instructions de connexion à [!UICONTROL Experience Cloud].
* Instructions d’utilisation d’Admin Console pour gérer vos utilisateurs et leurs autorisations respectives afin qu’ils puissent accéder à Cloud Manager si nécessaire.

### Personne faisant déjà partie de la clientèle d’Adobe Managed Services {#existing-customer}

En tant que personne faisant déjà partie de la clientèle d’AMS, vous devrez d’abord mettre à niveau vos environnements de production et hors production vers AEM 6.4 ou une version ultérieure.

Lors de la mise à niveau, le système vous intégrera à Cloud Manager et fournira l’URL d’accès à [!UICONTROL Cloud Manager]. En outre, vous devrez utiliser Admin Console pour gérer les utilisateurs et utilisatrices qui doivent accéder à [!UICONTROL Cloud Manager] ainsi que leurs autorisations respectives.

Votre projet AEM existant doit également se conformer aux pratiques recommandées, car vous commencez à utiliser [!UICONTROL Cloud Manager] pour déployer de nouveaux changements de code dans vos environnements AEM.

Pour obtenir des informations supplémentaires sur les avantages de la mise à niveau vers AEM 6.5, voir [Mise à niveau vers AEM 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade).

## Accéder à [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Connectez-vous à la page de destination [!UICONTROL Experience Cloud] à l’aide de vos informations d’identification Adobe Identity Management. Sélectionnez AEM dans le sélecteur de solutions pour accéder à [!UICONTROL Cloud Manager] et à vos environnements AEM.

Après la première connexion à [!UICONTROL Cloud Manager], vous avez accès à vos environnements AEM directement depuis l’interface d’utilisation de [!UICONTROL Cloud Manager]. À ce stade, vous êtes prêt à utiliser toutes les fonctionnalités de  et à préparer votre première branche de code à déployer dans vos environnements d’évaluation et de production.

Pour commencer à utiliser [!UICONTROL Cloud Manager], consultez le document [Première connexion](/help/getting-started/first-time-login.md).

Pour des informations complémentaires sur AEM, voir le document [Déploiement et maintenance](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Commencer avec [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Une fois la connexion à [!UICONTROL Cloud Manager] effectuée, vous pouvez commencer votre projet AEM en procédant comme suit :

1. Configurez votre environnement de référentiel de code.
1. Configurez votre équipe et les rôles. L’appartenance à un rôle est affectée en ajoutant l’utilisateur ou l’utilisatrice à à un profil [!UICONTROL Cloud Manager] à l’aide d’Admin Console.
1. Configurez les branches de code source dans le référentiel Git.
1. Définissez vos KPI de charge et de performance (indicateurs clés de performance).
1. Définissez des scénarios de test pour déployer votre code dans vos environnements d’évaluation et de production une fois toutes les vérifications de qualité effectuées.

## Présentation du processus {#end-to-end-journey}

Le diagramme suivant résume le processus d’utilisation du pipeline CI/CD  pour déployer vos modifications de code dans vos environnements d’évaluation et de production.

parcours client pour l’intégration à Cloud Manager, présentant le chemin d’accès aux nouveaux clients et aux clients existants par le biais de la configuration ou des mises à niveau de l’environnement, de la gestion des utilisateurs et des rôles, de la mise en œuvre du projet et du pipeline CI/CD.](/help/assets/screen_shot_2018-05-15at124004pm.png)![
