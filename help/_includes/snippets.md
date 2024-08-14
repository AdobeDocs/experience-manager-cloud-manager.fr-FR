---
source-git-commit: c772b3c576cac3a76433b67dc8a5233802996813
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 0%

---
# Fragments de code (#snippets)

## Problèmes connus de la copie de contenu {#content-copy-known-issues}

Vous devez connaître le problème connu suivant lors de l&#39;utilisation de la fonctionnalité [de copie de contenu.](/help/using/content-copy.md)

* Si une ressource de l’environnement source est renommée, l’opération de copie de contenu peut échouer en raison d’UUID en conflit dans l’environnement cible.
   * Pour éviter cette erreur, au lieu de renommer des ressources, supprimez-les d’abord, puis recréez-les avec le nouveau nom de ressource souhaité.
