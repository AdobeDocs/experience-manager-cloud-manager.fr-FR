---
title: Présentation de Cloud Manager pour AMS
description: Commencez ici pour découvrir Cloud Manager pour Adobe Managed Services (AMS) et comment il permet aux entreprises d’auto-gérer Adobe Experience Manager en mode cloud.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 4c4a2688cab8e5c81efa4b7b5e26f3c7b5dc30d6
workflow-type: tm+mt
source-wordcount: '1256'
ht-degree: 49%

---


# Présentation de [!UICONTROL Cloud Manager] pour AMS {#introduction-to-cloud-manager}

Commencez ici pour découvrir Cloud Manager pour AMS (Adobe Managed Services) et comment il permet aux entreprises de gérer elles-mêmes Adobe Experience Manager dans le cloud.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Présentation de Cloud Manager pour AMS"
>abstract="Permet aux entreprises d’auto-gérer Adobe Experience Manager en mode cloud. Il comprend une structure d’intégration et de diffusion continues (CI/CD) qui permet aux équipes informatiques et aux partenaires d’implémentation d’accélérer la diffusion des personnalisations ou des mises à jour sans compromettre les performances ou la sécurité."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/cloud-manager/programs#cloud-manager" text="Créer des programmes"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/cloud-manager/environments#cloud-manager" text="Créer des environnements"

## Présentation {#introduction}

[!UICONTROL Cloud Manager] for Adobe Experience Manager permet aux développeurs de créer des expériences client percutantes grâce à des workflows rationalisés, reposant sur les bonnes pratiques Adobe Experience Manager. Les pipelines CI/CD optimisés pour Adobe Experience Manager vous permettent de fusionner facilement des processus de développement en archivant simplement votre code, qui peut ensuite passer à la phase de production. Pendant la phase de création, vos mises à jour de code personnalisé sont soigneusement testées par rapport aux bonnes pratiques pour fournir des applications fiables à vos clients. Cloud Manager utilise une approche d’API ouverte et vous permet de l’intégrer à vos systèmes sans interrompre les processus et outils existants.

>[!NOTE]
>
>Cette documentation décrit spécifiquement les fonctionnalités et les caractéristiques de Cloud Manager pour Adobe Managed Services (AMS).
>
>La documentation équivalente pour AEM as a Cloud Service se trouve dans la [documentation AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/home).

Avec Cloud Manager, votre équipe de développement bénéficie des fonctionnalités suivantes :

* Intégration continue/diffusion continue (CI/CD) du code afin de réduire le délai de mise sur le marché de plusieurs mois/semaines à plusieurs jours/heures.

* Inspection du code, tests de performance et validation de la sécurité basés sur les bonnes pratiques avant de passer en production afin de minimiser les interruptions de production.

* Connectivité de l’API pour compléter les processus DevOps existants.

* Mise à l’échelle automatique qui détecte intelligemment la nécessité d’une capacité accrue et apporte automatiquement des segments Dispatcher/publication supplémentaires en ligne.

![Flux CI/CD](/help/assets/screen_shot_2018-05-12at73843pm.png)Flux de processus CI/CD utilisé dans [!UICONTROL Cloud Manager].

## Fonctionnalités clés de [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Vous trouverez ci-dessous un aperçu plus détaillé de certaines fonctionnalités clés de Cloud Manager.

### Interface en libre-service {#self-service-interface}

L’interface utilisateur (IU) de [!UICONTROL Cloud Manager] vous permet d’accéder et de gérer facilement l’environnement cloud et le pipeline CI/CD pour vos applications Adobe Experience Manager.

Vous définissez des indicateurs de performances clés (IPC) spécifiques à l’application, tels que le pic de pages vues par minute ou le temps de réponse attendu au chargement de la page. Ces indicateurs de performance clés servent de base pour mesurer le succès du déploiement. Les rôles et autorisations des différents membres de l’équipe peuvent être facilement définis. L&#39;interface en libre-service vous offre un contrôle total. Il fournit également des liens vers les ressources sur les bonnes pratiques et l’accès à des experts en Adobe pour obtenir des conseils lorsque cela est nécessaire.

Pour découvrir et commencer à utiliser l’interface utilisateur de [!UICONTROL Cloud Manager], consultez la rubrique [Première connexion](/help/getting-started/first-time-login.md).

### Pipeline CI/CD {#ci-cd-pipeline}

[!UICONTROL Cloud Manager] permet de tirer parti d’un pipeline CI/CD optimisé pour accélérer la diffusion du code personnalisé ou des mises à jour, telles que l’ajout de composants sur le site web.

Grâce à l’interface utilisateur de [!UICONTROL Cloud Manager], les clients peuvent configurer et déclencher leur pipeline CI/CD. Durant ce pipeline, une analyse approfondie du code est exécutée pour garantir que seules des applications de haute qualité transitent par l’environnement de production.

Pour en savoir plus sur la configuration du pipeline à partir de l’interface utilisateur de [!UICONTROL Cloud Manager], voir [Configuration des pipelines de production](/help/using/production-pipelines.md) et [Configuration des pipelines hors production](/help/using/non-production-pipelines.md).

### Modes de déploiement flexibles {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] offre aux clients des modes de déploiement flexibles et configurables afin qu’ils puissent fournir des expériences en fonction de l’évolution des demandes métier.

Grâce à un mode de déclenchement automatique, le code est automatiquement déployé dans un environnement en fonction d’événements spécifiques tels que la validation du code. Vous pouvez également planifier des déploiements de code pendant les périodes spécifiées, même en dehors des heures de bureau.

Indépendamment du déclencheur de déploiement, les vérifications de qualité sont toujours effectuées dans le cadre de l’exécution du pipeline CI/CD, et ce, chaque fois qu’un déploiement est déclenché. Les contrôles de qualité incluent l’inspection du code, les tests de sécurité et les tests de performance, qui sont tous livrés d’usine sans aucun effort de votre part ou de vos partenaires.

Pour en savoir plus sur le déploiement des contrôles de code et de qualité, voir [Déploiement du code](/help/using/code-deployment.md).

## Fonctionnalités facultatives de Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager propose des fonctionnalités avancées supplémentaires, qui peuvent être utiles à votre projet en fonction de la configuration et des besoins de votre environnement. Si ces fonctionnalités vous intéressent, contactez votre ingénieur du service client ou votre représentant d’Adobe pour en discuter plus.

### Mise à l’échelle automatique {#autoscaling}

Lorsque l’environnement de production est soumis à une charge exceptionnellement élevée, [!UICONTROL Cloud Manager] détecte la nécessité d’augmenter la capacité et met automatiquement en ligne de la capacité supplémentaire grâce à sa fonction de mise à l’échelle automatique.

Dans un tel cas, [!UICONTROL Cloud Manager] déclenche automatiquement le processus d’approvisionnement de mise à l’échelle automatique, envoie une notification de l’événement de mise à l’échelle automatique et met en ligne la capacité supplémentaire en quelques minutes. La capacité supplémentaire est configurée dans l’environnement de production, dans les mêmes régions, et répond aux mêmes spécifications système que les noeuds Dispatcher/publication en cours d’exécution.

La fonction de mise à l’échelle automatique s’applique au niveau Dispatcher/publication, en utilisant la mise à l’échelle horizontale pour ajouter un à dix segments de paires Dispatcher/publication. Toute capacité supplémentaire configurée est mise à l’échelle manuellement dans un délai de dix jours ouvrés, comme déterminé par l’ingénieur du service client de l’Adobe.

>[!NOTE]
>
>Si vous souhaitez déterminer si la mise à l’échelle automatique est appropriée pour votre application, contactez l’ingénieur du service client ou votre représentant Adobe.

### Déploiements bleu/vert {#blue-green}

Le déploiement bleu/vert est une technique qui réduit les temps d’interruption et les risques en exécutant deux environnements de production identiques appelés bleu/vert.

À tout moment, seul un des environnements est actif, et cet environnement actif diffuse tout le trafic de production. En général, le bleu est l’environnement actif et le vert est inactif.

* Le déploiement bleu/vert est un module complémentaire des pipelines CI/CD de Cloud Manager dans lequel un deuxième ensemble d’instances de publication et de Dispatcher (vert) est créé et utilisé pour les déploiements. Les instances vertes sont ensuite associées à l’équilibreur de charge de production et les anciennes instances (bleues) sont supprimées et interrompues.
* Cette implémentation de bleu/vert traite les instances comme transitoires et chaque itération d’un pipeline bleu/vert crée un nouvel ensemble de serveurs de publication et Dispatcher.
* Un équilibreur de charge vert est créé dans le cadre de la configuration. Cet équilibreur de charge ne change jamais et est ce vers quoi vous devez pointer votre URL verte ou &quot;test&quot;.
* Lors d’un déploiement bleu/vert, une réplication exacte des niveaux Dispatcher/publication existants est créée.

#### Flux de déploiement bleu/vert {#flow}

Lorsque le déploiement bleu/vert est activé, le flux de déploiement diffère du flux de déploiement du service cloud standard.

| Étape | Déploiement bleu/vert | Déploiement standard |
|---|---|---|
| 1 | Déploiement vers l’auteur | Déploiement vers l’auteur |
| 2 | Mise en pause pour le test | - |
| 3 | Une infrastructure verte est créée | - |
| 4 | Déploiement vers le niveau de publication/Dispatcher vert | Déploiement vers l’éditeur |
| 5 | Mise en pause pour le test (jusqu’à 24 heures) | - |
| 6 | Une infrastructure verte est ajoutée à l’équilibreur de charge de production | - |
| 7 | L’infrastructure bleue est supprimée de l’équilibreur de charge de production |
| 8 | Suspendre pour la validation finale (jusqu’à 24 heures) | - |
| 9 | L’infrastructure bleue est automatiquement arrêtée | - |
| 10 | Fin du pipeline | - |

#### Implémentation bleue/verte {#implementing}

Tous les utilisateurs AMS qui utilisent Cloud Manager pour les déploiements en production peuvent utiliser le déploiement bleu/vert. Cependant, l’utilisation du déploiement bleu/vert nécessite une validation supplémentaire de vos environnements et une configuration par un ingénieur du service client Adobe.

Si le déploiement bleu/vert vous intéresse, tenez compte des exigences et limites suivantes et contactez votre ingénieur du service client.

#### Conditions requises et restrictions {#limitations}

* Le bleu/vert est uniquement disponible pour les paires Dispatcher/éditeur.
* Les paires Aperçu de Dispatcher/publication ne font pas partie des déploiements bleu/vert.
* Chaque paire Dispatcher/publication est identique à toutes les autres paires Dispatcher/éditeur.
* Le bleu/vert n’est disponible que dans l’environnement de production.
* Le bleu/vert est disponible dans AWS et Azure.
* Le bleu/vert n’est pas disponible pour les clients Assets uniquement.
