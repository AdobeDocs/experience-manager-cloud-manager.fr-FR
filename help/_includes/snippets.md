---
source-git-commit: 4ff440250b4ed0770c34a7042ec7d22c79ffe05e
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---
# Fragments de code (#snippets)

## Problèmes connus de la copie de contenu {#content-copy-known-issues}

Tenez compte du problème connu suivant lors de l&#39;utilisation de la fonctionnalité [de copie de contenu.](/help/using/content-copy.md)

* Si une ressource de l’environnement source est renommée, l’opération de copie de contenu peut échouer en raison d’UUID en conflit dans l’environnement cible.
   * Pour éviter cette erreur, au lieu de renommer des ressources, supprimez-les d’abord, puis recréez-les avec le nouveau nom de ressource souhaité.
