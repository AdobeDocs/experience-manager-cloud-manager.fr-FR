---
title: Sécurité et confidentialité
description: Découvrez la sécurité et la confidentialité de vos ressources de code et d’artefact dans Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: d7751757c1d3bda3d60406a1d39cb41c61f5c863
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 25%

---


# Sécurité et confidentialité {#security-and-privacy}

Découvrez la sécurité et la confidentialité de vos ressources de code et d’artefact dans Cloud Manager.

## Rôles et autorisations {#roles}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées.

Pour en savoir plus sur les rôles que vous pouvez affecter dans les autorisations de rôle de Admin Console et d’utilisateur, reportez-vous au document . [Autorisations basées sur les rôles.](/help/requirements/role-based-permissions.md)

## Isolation de ressource {#resource-isolation}

[!UICONTROL Cloud Manager] les clients ont besoin de leurs informations d’identification IMS pour s’authentifier en tant que toutes les autorisations liées à [!UICONTROL Cloud Manager] sont liées à leurs organisations IMS. Pendant le processus d’intégration, l’équipe chargée de la configuration s’assure que l’isolation des ressources est appliquée dans [!UICONTROL Cloud Manager].

## Sécurité des données {#data-security}

Le code dans [!UICONTROL Cloud Manager] est chiffré en transit. Les fichiers binaires créés par Cloud Manager sont également chiffrés en transit et lors de leur stockage.

Chaque client obtient son propre référentiel git et le code est sécurisé et n’est partagé avec aucune autre organisation.

## Confidentialité des données {#data-privacy}

[!UICONTROL Cloud Manager] adhère aux principes de confidentialité définis par Adobe. Les développeurs affectent le code en toute sécurité dans des référentiels git via HTTPS.

[!UICONTROL Cloud Manager]L’interface utilisateur de repose sur des services conformes à un framework de contrôle commun d’Adobe qui. [!UICONTROL Cloud Manager]L’interface utilisateur de utilise des services sécurisés de plusieurs fournisseurs cloud.
