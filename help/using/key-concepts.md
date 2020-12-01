---
title: Concepts clés
seo-title: Concepts clés
description: Cette page répertorie les termes clés associés à Cloud Manager.
seo-description: Consultez cette page pour comprendre les termes clés associés à Cloud Manager.
uuid: 2a37810b-98f8-4f01-90de-1e52c754ad16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: b702dfc0-3534-4d90-af19-8559d8baf6a6
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 100%

---


# Concepts clés {#key-concepts}

Cette page décrit la terminologie de base employée dans Cloud Manager. Il est vivement conseillé de lire cette page avant de consulter la documentation de Cloud Manager.

**Application** Ensemble de personnalisations et de configurations créées par un client pour adapter la solution sous-jacente en fonction de ses domaines d’application et besoins spécifiques. Une application est une unité logique pouvant être composée de plusieurs artefacts.

Par exemple, *We.Retail*.

**Artefact** Unité déployable. Résultat d’un processus de compilation qui transforme le code source en une seule unité. Par exemple, un fichier Zip contenant le code source.

**Référentiel d’artefacts** Emplacement de stockage où sont enregistrés et sécurisés les artefacts spécifiques des clients.

**Environnement** Groupe de machines virtuelles au sein d’un programme. Pour AEM, cette fonction est composée d’une instance Author (éventuellement avec une instance Author à reprise progressive supplémentaire), de zéro ou plusieurs instances Publish, d’une ou plusieurs instances Dispatcher et d’un équilibreur de charge.

**Référentiel Git** Emplacement où est stocké le code source spécifique au client, accessible à l’aide du protocole Git.

**Instance** Serveur virtuel spécifique qui exécute la solution AEM. Les instances représentent une seule unité logique du point de vue du déploiement.

**Organisation** Conception Adobe qui représente un client Enterprise. Une société peut avoir plusieurs organisations en fonction de la configuration initiale dans le système de gestion des identités d’Adobe.

**Pipeline** Ensemble d’étapes de déploiement exécutées les unes après les autres.

**Produit** Ensemble spécifique de fonctionnalités au sein d’une solution mise sous licence par une organisation. Les différents programmes au sein d’une même organisation peuvent être associés à différents ensembles de produits. Par exemple, Sites, Ressources de Formulaires.

**Programme** Ensemble d’environnements qui prennent en charge un regroupement logique d’initiatives client, correspondant en règle générale à un accord de niveau de service (SLA) acheté. Chaque programme comprend un environnement de production précis et peut intégrer un grand nombre d’environnements hors production.

**Solution** Une des solutions [!UICONTROL Experience Cloud] d’Adobe. Par exemple, Adobe Experience Manager, Adobe Target ou Adobe Analytics.

**Etape** Ensemble d’instructions configurées qui exécute une unité de travail, composante d’un pipeline.
