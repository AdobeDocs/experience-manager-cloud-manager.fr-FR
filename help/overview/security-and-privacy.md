---
title: Sécurité et confidentialité
description: Découvrez la sécurité et la confidentialité de vos ressources de code et d’artefact dans Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 70%

---


# Sécurité et confidentialité {#security-and-privacy}

Découvrez la sécurité et la confidentialité de vos ressources de code et d’artefact dans Cloud Manager.

## Rôles et autorisations {#roles}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées.

Pour en savoir plus sur les rôles que vous pouvez affecter dans Admin Console et sur les autorisations des rôles d’utilisation, voir la section [Autorisations basées sur les rôles](/help/requirements/role-based-permissions.md).

## isolation des ressources {#resource-isolation}

Les clients de [!UICONTROL Cloud Manager] ont besoin de leurs informations d’identification IMS pour s’authentifier, car toutes les autorisations liées à [!UICONTROL Cloud Manager] sont liées à leurs organisations IMS. Pendant le processus d’intégration, l’équipe d’approvisionnement s’assure que l’isolation de ressource est mise en place dans [!UICONTROL Cloud Manager].

## Sécurité des données {#data-security}

Le code dans [!UICONTROL Cloud Manager] est chiffré en transit. Les fichiers binaires créés par Cloud Manager sont également chiffrés en transit et lors de leur stockage.

Chaque client obtient son propre référentiel Git et le code est sécurisé et n’est partagé avec aucune autre organisation.

## Confidentialité des données {#data-privacy}

[!UICONTROL Cloud Manager] adhère aux principes de confidentialité définis par Adobe. Les développeurs affectent le code en toute sécurité dans les référentiels Git via HTTPS.

L’interface utilisateur de [!UICONTROL Cloud Manager] repose sur des services conformes à un framework de contrôle commun d’Adobe. L’interface utilisateur de [!UICONTROL Cloud Manager] utilise les services sécurisés de plusieurs fournisseurs de cloud.
