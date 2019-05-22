---
title: Notes de mise à jour de la version 2019.4.0
seo-title: Notes de mise à jour d’AEM Cloud Manager pour la version 2019.4.0
description: Consultez cette page pour obtenir des informations sur la version 2019.4.0 de Cloud Manager.
seo-description: Consultez cette page pour plus d’informations sur la version 2019.4.0 d’AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 8031df1c1ce9d7fee4ef33de289c6952370b7589

---


# Notes de mise à jour de la version 2019.4.0 {#release-notes-for}

La version 2019.4.0 [!UICONTROL de Cloud Manager] ne contient pas de modifications fonctionnelles significatives. Pour plus d&#39;informations, suivez les sections ci-dessous.

## Date de publication {#release-date}

La date de publication de [!UICONTROL Cloud Manager] version 2019.4.0 est le 18 avril 2019.

## Nouveautés {#whats-new}

* L&#39;interface utilisateur de Cloud Manager est désormais disponible en anglais, français, allemand et japonais.
* Les étapes de déploiement contiennent désormais le processus en cours d&#39;exécution, c&#39;est-à-dire qu&#39;une sauvegarde est en cours d&#39;exécution, que des packs sont en cours d&#39;installation et que des équilibreurs de charge sont en cours de configuration.

## Correctifs {#bug-fixes}

* L&#39;approche de déploiement utilisée pour les modifications du répartiteur a été améliorée afin de gérer d&#39;autres cas d&#39;utilisation.
* Certains types de taille d&#39;instance ne s&#39;affichaient pas correctement dans la page Environnements.
* Les règles de qualité du code CQBP -84-dépendances ont généré des faux positifs pour les bibliothèques Adobe incorporées, telles que les composants principaux de WCM et Asset Share Commons.
* Le bouton détaillé de l&#39;étape de numérisation du code était activé lorsque les détails étaient indisponibles.
* Le message d&#39;erreur lors de la spécification d&#39;une valeur non valide pour les pages vues par minute pour les pages vues par minute était incorrecte.
* La catégorie de déploiement sur un canal de non production n&#39;était pas correctement mise en majuscules.
* La carte d&#39;action de la carte **d&#39;action sur** la page Aperçu était incorrecte lorsque le référentiel git n&#39;était pas configuré correctement.

## Problèmes connus {#known-issues}

* Les valeurs SLA peuvent être arrondies incorrectement.
