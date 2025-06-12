---
title: Mises à jour du pack de services pour les environnements de développement - version bêta privée
description: Découvrez comment vous pouvez désormais lancer des mises à jour du pack de services pour les environnements de développement via l’interface utilisateur de Cloud Manager.
hide: true
hidefromtoc: true
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
source-git-commit: b2a14280e84bb934053968b0e93e33d30fb6086a
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 1%

---

# Mises à jour du pack de services pour les environnements de développement (version bêta privée) {#stage-prod-only}

Découvrez comment lancer des mises à jour du pack de services pour les environnements de développement via l’interface utilisateur de Cloud Manager.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour [le programme Private Beta](/help/release-notes/current.md#beta-program).

## Vue d’ensemble {#service-pack-updates-overview}

Vous pouvez lancer des mises à jour du Service Pack pour les environnements de développement via l’interface utilisateur de Cloud Manager. Cette fonctionnalité vous permet de vérifier les mises à jour du pack de services disponibles et de gérer le processus d’installation indépendamment.

**Principaux avantages**

* Permet un meilleur contrôle des mises à jour du pack de services Cloud Manager.
* Réduit la dépendance envers les ingénieurs du succès client (CSE) Adobe pour initier les mises à jour.
* Effectue le suivi de l’ensemble du processus de mise à jour via Cloud Manager.

**Limites actuelles**

* L’option de mise à jour en libre-service n’est disponible que pour les environnements de développement.
* Des rapports d’erreur limités sont disponibles pour les mises à jour ayant échoué.
* En cas de problème, vous devez contacter les ingénieurs du service client Adobe pour plus d’informations.

## Lancement d’une mise à jour du pack de services

1. Connectez-vous à Cloud Manager avec les privilèges de Responsable de déploiement .
1. Accédez à la page Aperçu du programme .
1. Sous la section Environnements , cliquez sur ![icône Plus, points de suspension](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

   ![Rechercher la mise à jour du pack de services dans le menu déroulant](/help/using/assets/service-pack-check-for-updates.png)

1. Dans le menu déroulant, cliquez sur ![Icône Ouvrir dans la lumière](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg) **Rechercher les mises à jour** pour rechercher les mises à jour du Service Pack disponibles.

   ![Une liste des mises à jour disponibles apparaît](/help/using/assets/service-pack-versions.png)

1. Cliquez sur la version du pack de services souhaitée dans la liste.
1. Cliquez sur **Mettre à jour le pack de services** pour lancer le processus de mise à jour.
1. Dans la boîte de dialogue de confirmation, passez en revue les détails et confirmez la mise à jour.

   Une fois confirmé, le processus d’installation démarre et la progression peut être suivie dans Cloud Manager.

## Suivre la mise à jour du pack de services

Après avoir lancé la mise à jour, vous pouvez surveiller la progression dans la page Activité de Cloud Manager.

**Pour suivre la mise à jour du pack de services :**

1. Accédez à la page Activité à partir du tableau de bord Cloud Manager.
1. Recherchez l’entrée Installation du pack de services .

   ![Installations du pack de services](/help/using/assets/service-pack-installation.png)

1. Cliquez sur l’entrée pour afficher la progression détaillée et les mises à jour de statut comme suit :

   ![ Progression de l’installation du pack de services ](/help/using/assets/service-pack-progression.png)

### Résolution des problèmes d’installation

* Si l’installation échoue, Cloud Manager déclenche automatiquement une restauration de l’état précédent.
* Si les problèmes persistent, cliquez sur **Télécharger le journal** pour collecter les journaux d’erreurs, puis contactez l’assistance Adobe pour résoudre les problèmes.

## Approuver ou refuser l&#39;exécution du pack de services

Une fois l’installation terminée, votre approbation (ou votre rejet) est nécessaire pour finaliser la mise à jour.

**Pour valider ou refuser l&#39;exécution du pack de services :**

1. Ouvrez la page d’activité dans Cloud Manager.
1. Recherchez la demande d&#39;approbation en attente pour la mise à jour du pack de services.

   ![Rejeter ou approuver la mise à jour du pack de services](/help/using/assets/service-pack-reject-approve.png)

1. Effectuez l’une des opérations suivantes :

   * Pour finaliser la mise à jour, cliquez sur **Approuver**.

   ![Validation du pack de services](/help/using/assets/service-pack-approve.png)

   * Pour annuler la mise à jour, cliquez sur **Rejeter**.
L’installation du pack de services est annulée et aucune modification n’est appliquée.

   ![ Rejet du pack de services ](/help/using/assets/service-pack-reject.png)
