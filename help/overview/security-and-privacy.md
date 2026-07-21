---
title: Sécurité et confidentialité
description: Découvrez la sécurité et la confidentialité de vos ressources de code et d’artefact dans Adobe Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
TQID: https://experienceleague.adobe.com/mtWOzJnzV8k403LlyD9Fn9WSE5XTgjHzyVuA4j62MMg
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: d5a34a9f6d050eaff241c0f42c9cf023cbc8036a
workflow-type: tm+mt
source-wordcount: 201
ht-degree: 26%

---

# Sécurité et confidentialité {#security-and-privacy}

Découvrez la sécurité et la confidentialité de vos ressources de code et d’artefact dans Adobe Cloud Manager.

## Rôles et autorisations {#roles}

Cloud Manager dispose de rôles préconfigurés avec les autorisations appropriées.

Pour en savoir plus sur les rôles que vous pouvez affecter dans Admin Console et sur les autorisations des rôles d’utilisation, voir la section [Autorisations basées sur les rôles](/help/requirements/role-based-permissions.md).

## Isolation de ressource {#resource-isolation}

Les clients Cloud Manager ont besoin de leurs informations d’identification IMS pour s’authentifier, car toutes les autorisations liées à Cloud Manager sont liées à leurs organisations IMS. Pendant le processus d’intégration, l’équipe d’approvisionnement s’assure que l’isolation de ressource est mise en place dans Cloud Manager.

## Sécurité des données {#data-security}

Le code Cloud Manager est chiffré en transit. Cloud Manager crée des fichiers binaires qui sont également chiffrés lors de la transmission et stockés dans un format chiffré.

Chaque client obtient son propre référentiel Git. Le code est sécurisé et n’est partagé avec aucune autre organisation.

## Confidentialité des données {#data-privacy}

Cloud Manager adhère aux principes de confidentialité définis par Adobe. L’équipe de développement transmet le code en toute sécurité dans le référentiel Git sur HTTPS.

L’interface utilisateur de Cloud Manager utilise des services conformes au framework de contrôle commun d’Adobe. L’interface utilisateur de Cloud Manager utilise les services sécurisés de plusieurs fournisseurs de cloud.
