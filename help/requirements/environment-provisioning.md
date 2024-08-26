---
title: Configuration d’environnement
description: Découvrez comment vos environnements sont configurés dans le cadre du processus d’intégration de Cloud Manager.
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 36%

---


# Approvisionnement de l’environnement {#environments-provisioning}

Découvrez comment vos environnements sont configurés dans le cadre du processus d’intégration de Cloud Manager.

## Configuration {#provisioning}

Pendant le processus d’intégration, Adobe met automatiquement en service tous les environnements cloud AEM que vous avez achetés et les associe à votre programme dans [!UICONTROL Cloud Manager]. Chaque abonnement Managed Services d’Adobe comprend AEM environnements cloud. Ils comprennent généralement au moins un environnement de production et un environnement intermédiaire. Elles peuvent également inclure un ou plusieurs environnements de développement ou de test.

## Courriel de bienvenue {#welcome-email}

Une fois le processus de configuration de l’environnement terminé, l’administrateur client désigné reçoit un e-mail de bienvenue confirmant qu’il a reçu l’accès à l’Adobe [!UICONTROL Experience Cloud]. L’e-mail de bienvenue contient des informations détaillées sur la prise en main des services [!UICONTROL Experience Cloud], les environnements cloud d’[!UICONTROL AEM Managed Services], ainsi que le portail libre-service de [!UICONTROL Cloud Manager]. En outre, l’e-mail contient des informations importantes, telles que les coordonnées de l’ingénieur du succès client (CSE), où trouver des ressources d’assistance, des forums, des FAQ et bien plus encore. Dans la liste des ressources fournies dans l’e-mail, vous obtenez également des détails sur la façon d’accéder à [!UICONTROL Cloud Manager] pour vos environnements cloud AEM.

## Étapes suivantes {#next-steps}

Après avoir reçu l’e-mail de bienvenue, vous pouvez vous connecter à [!UICONTROL Cloud Manager] en tant qu’administrateur système à l’aide de vos informations d’identification Adobe IMS. Une fois connecté, vous pouvez vérifier que vos environnements de production et vos autres environnements cloud d’AEM sont disponibles et s’exécutent correctement.

[!UICONTROL Cloud Manager] utilise ces environnements cloud AEM pour exécuter le pipeline CI/CD. Il déploie le code de son référentiel Git vers l’environnement d’évaluation. Il déploie ensuite le code dans votre environnement de production AEM. Vous pouvez également accéder à vos environnements cloud AEM directement depuis [!UICONTROL Cloud Manager] lorsque vous êtes prêt à commencer à créer des expériences numériques pour vos propriétés web.
