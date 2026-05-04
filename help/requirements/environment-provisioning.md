---
title: Configuration d’environnement
description: Découvrez comment vos environnements sont configurés dans le cadre du processus d’intégration de Cloud Manager.
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
TQID: https://experienceleague.adobe.com/xLjZdRZeCiqF0KxHQ1nBI4IBBsh4BDTqETv79lrypR0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 299
ht-degree: 100%

---

# Approvisionnement d’environnement {#environments-provisioning}

Découvrez comment vos environnements sont configurés dans le cadre du processus d’intégration de Cloud Manager.

## Configuration {#provisioning}

Pendant le processus d’intégration, Adobe configure automatiquement tous les environnements cloud AEM que vous avez achetés et les associe à votre programme dans [!UICONTROL Cloud Manager]. Chaque abonnement Adobe Managed Services comprend les environnements cloud AEM. Ils comprennent généralement au moins un environnement de production et un environnement d’évaluation. Ils peuvent éventuellement inclure un ou plusieurs environnements de développement ou de test.

## E-mail de bienvenue {#welcome-email}

Une fois le processus de configuration de l’environnement terminé, la personne cliente chargée de l’administration désignée reçoit un e-mail de bienvenue confirmant que l’accès à Adobe [!UICONTROL Experience Cloud] lui a été accordé. L’e-mail de bienvenue contient des informations détaillées sur la prise en main des services [!UICONTROL Experience Cloud], les environnements cloud d’[!UICONTROL AEM Managed Services], ainsi que le portail libre-service de [!UICONTROL Cloud Manager]. En outre, l’e-mail contient des informations importantes, telles que les coordonnées du responsable du succès client, où trouver des ressources d’assistance, des forums, des questions fréquentes et bien plus encore. La liste des ressources fournies dans l’e-mail contient également des informations sur le mode d’accès à [!UICONTROL Cloud Manager] pour vos environnements cloud AEM.

## Étapes suivantes {#next-steps}

Après avoir reçu l’e-mail de bienvenue, vous pouvez vous connecter à [!UICONTROL Cloud Manager] en tant qu’administrateur ou administratrice système à l’aide de vos informations d’identification Adobe IMS. Une fois la connexion effectuée, vous pouvez vérifier que vos environnements cloud de production et hors production AEM sont disponibles et s’exécutent correctement.

[!UICONTROL Cloud Manager] utilise ces environnements cloud AEM pour exécuter le pipeline CI/CD. Il déploie le code de son référentiel Git vers l’environnement d’évaluation. Il déploie ensuite le code dans votre environnement de production AEM. Vous pouvez également accéder à vos environnements cloud AEM directement à partir de [!UICONTROL Cloud Manager] lorsque vous souhaitez créer des expériences numériques pour vos propriétés web.
