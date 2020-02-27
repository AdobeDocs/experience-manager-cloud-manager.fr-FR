---
title: Sécurité et confidentialité
seo-title: Sécurité et confidentialité pour AEM Cloud Manager
description: Consultez cette page pour en savoir plus sur la sécurité et la confidentialité de vos ressources (code/artefacts).
seo-description: Consultez cette page pour en savoir plus sur la sécurité et la confidentialité de vos ressources (code/artefacts) grâce à AEM Cloud Manager.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: 7cbc42108a6ccc8f7303eb76fd8ca2e9027f49e0

---


# Sécurité et confidentialité {#security-and-privacy}

[!UICONTROL Cloud Manager] a des rôles préconfigurés avec les autorisations appropriées. Cette section met en évidence la sécurité et la confidentialité de vos ressources (code/artefacts) à l’aide d’AEM Cloud Manager. Additionally, [!UICONTROL Cloud Manager] has pre-configured roles with appropriate permissions.

Pour en savoir plus sur les rôles que vous pouvez affecter dans la console d’administration et sur les autorisations de rôle utilisateur, reportez-vous à la section Permissions basées sur [les](/help/using/role-based-permissions.md)rôles.


## Isolation de ressource {#resource-isolation}

Les clients qui utilisent [!UICONTROL Cloud Manager] auront besoin de leurs informations d’identification IMS pour s’authentifier, car toute autorisation liée à [!UICONTROL Cloud Manager] sera configurée et liée à leur organisation IMS. Pendant le processus d’intégration, l’équipe chargée de la configuration s’assure que l’isolation de ressource est mise en place dans [!UICONTROL Cloud Manager].

## Sécurité des données {#data-security}

Code in [!UICONTROL Cloud Manager] is encrypted in transit. Les binaires créées par Cloud Manager sont également chiffrées en transit et chiffrées lors de leur stockage.

Chaque client obtient son propre **référentiel Git**. Le code est sécurisé et n’est partagé avec aucune autre **organisation**.

## Confidentialité des données {#data-privacy}

[!UICONTROL Cloud Manager] respecte les principes de confidentialité définis par Adobe. Les développeurs affectent le code en toute sécurité dans le **référentiel Git** sur HTTPS.

The User Interface (UI) for [!UICONTROL Cloud Manager]  is built on top of services that comply to a common control framework that is defined by Adobe. User Interface for [!UICONTROL Cloud Manager] uses secure services from several cloud providers.
