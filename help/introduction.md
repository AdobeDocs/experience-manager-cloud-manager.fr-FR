---
title: Présentation de Cloud Manager pour AMS
description: Commencez ici pour découvrir Cloud Manager pour Adobe Managed Services (AMS) et comment il permet aux entreprises d’auto-gérer Adobe Experience Manager en mode cloud.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 14e35882765783b234ca35da14257279af5130a0
workflow-type: ht
source-wordcount: '1311'
ht-degree: 100%

---


# Présentation de [!UICONTROL Cloud Manager] pour AMS {#introduction-to-cloud-manager}

Commencez ici pour découvrir Cloud Manager pour Adobe Managed Services (AMS) et comment il permet aux entreprises d’auto-gérer Adobe Experience Manager en mode cloud.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Présentation de Cloud Manager pour AMS"
>abstract="Permet aux entreprises d’auto-gérer Adobe Experience Manager en mode cloud. Il comprend une structure d’intégration et de diffusion continues (CI/CD) qui permet aux équipes informatiques et aux partenaires d’implémentation d’accélérer la diffusion des personnalisations ou des mises à jour sans compromettre les performances ou la sécurité."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=fr#cloud-manager" text="Créer des programmes"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=fr#cloud-manager" text="Créer des environnements"

## Présentation {#introduction}

[!UICONTROL Cloud Manager] for Adobe Experience Manager permet aux développeurs de créer des expériences client percutantes grâce à des workflows rationalisés, reposant sur les bonnes pratiques Adobe Experience Manager. Les pipelines CI/CD optimisés pour Adobe Experience Manager permettent de fusionner facilement des workflows de développement en archivant simplement votre code, qui peut ensuite être mis en production. Pendant la phase de création, vos mises à jour de code personnalisé sont soigneusement testées par rapport aux bonnes pratiques pour fournir des applications fiables à vos clients. Cloud Manager utilise une approche d’API ouverte et vous permet de l’intégrer à vos systèmes sans interrompre les processus et outils existants.

>[!NOTE]
>
>Cette documentation décrit spécifiquement les fonctionnalités et les caractéristiques de Cloud Manager pour Adobe Managed Services (AMS).
>
>Retrouvez la documentation équivalente pour les clients AEM as a Cloud Service dans la [Documentation d’AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/home.html?lang=fr).

Avec Cloud Manager, votre équipe de développement bénéficie des fonctionnalités suivantes :

* Intégration continue/diffusion continue (CI/CD) du code pour réduire le délai de mise sur le marché de plusieurs mois/semaines à quelques jours/heures.

* Inspection du code, test de performance et validation de la sécurité basés sur les bonnes pratiques avant de passer à la production, afin de minimiser les interruptions de production.

* Connectivité de l’API pour compléter les processus DevOps existants.

* La mise à l’échelle automatique détecte intelligemment la nécessité d’une capacité accrue et met automatiquement en ligne un ou plusieurs segments supplémentaires Dispatcher/de publication.

L’image suivante illustre le flux du processus CI/CD utilisé dans [!UICONTROL Cloud Manager] :

![Flux CI/CD](/help/assets/screen_shot_2018-05-12at73843pm.png)

## Fonctionnalités clés de [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Vous trouverez ci-dessous un aperçu plus détaillé de certaines fonctionnalités clés de Cloud Manager.

### Interface en libre-service {#self-service-interface}

L’interface utilisateur de [!UICONTROL Cloud Manager] permet aux clients et de gérer et d’accéder facilement à l’environnement cloud et au pipeline CI/CD pour leurs applications Adobe Experience Manager.

Les clients définissent des indicateurs de performances clés (ICP) spécifiques à l’application, tels que le nombre de pages maximum vues par minute et le temps de réponse attendu pour le chargement d’une page, qui constituent la base de la mesure d’un déploiement réussi. Les rôles et autorisations des différents membres de l’équipe peuvent être facilement définis. Bien que la nouvelle interface en libre-service soit sous votre contrôle, elle propose également des liens vers des ressources de bonnes pratiques. Elle vous permet aussi d’accéder aux experts d’Adobe, qui peuvent vous fournir les conseils nécessaires en cas de besoin.

Pour découvrir et commencer à utiliser l’interface utilisateur de [!UICONTROL Cloud Manager], consultez le document [Première connexion](/help/getting-started/first-time-login.md).

### Pipeline CI/CD {#ci-cd-pipeline}

[!UICONTROL Cloud Manager] permet de tirer parti d’un pipeline CI/CD optimisé pour accélérer la diffusion du code personnalisé ou des mises à jour, telles que l’ajout de composants sur le site web.

Grâce à l’interface utilisateur de [!UICONTROL Cloud Manager], les clients peuvent configurer et déclencher leur pipeline CI/CD. Durant ce pipeline, une analyse approfondie du code est exécutée pour garantir que seules des applications de haute qualité transitent par l’environnement de production.

Pour en savoir plus sur la configuration du pipeline depuis l’interface utilisateur de [!UICONTROL Cloud Manager], consultez les documents [Configuration de pipelines de production](/help/using/production-pipelines.md) et [Configuration de pipelines hors production](/help/using/non-production-pipelines.md).

### Modes de déploiement flexibles {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] offre aux clients des modes de déploiement flexibles et configurables afin qu’ils puissent fournir des expériences en fonction de l’évolution des demandes métier.

Grâce à un mode de déclenchement automatique, le code est automatiquement déployé dans un environnement en fonction d’événements spécifiques tels que la validation du code. Vous pouvez également planifier des déploiements de code pendant les périodes spécifiées, même en dehors des heures de bureau.

Indépendamment du déclencheur de déploiement, les vérifications de qualité sont toujours effectuées dans le cadre de l’exécution du pipeline CI/CD, et ce, chaque fois qu’un déploiement est déclenché. Les vérifications de qualité incluent, entre autres, l’inspection de code, les tests de sécurité et les tests de performance, et ne requièrent littéralement aucun effort de la part des clients ou de leurs partenaires.

Pour en savoir plus sur le déploiement de code et les vérifications de qualité, consultez le document [Déploiement du code](/help/using/code-deployment.md).

## Fonctionnalités facultatives de Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager propose des fonctionnalités avancées supplémentaires qui peuvent être utiles à votre projet en fonction de la configuration et des besoins de votre environnement. Si ces fonctionnalités vous intéressent, veuillez contacter votre ingénieur du succès client (CSE) ou votre représentant Adobe pour en discuter.

### Mise à l’échelle automatique {#autoscaling}

Lorsque l’environnement de production est soumis à une charge exceptionnellement élevée, [!UICONTROL Cloud Manager] détecte la nécessité d’augmenter la capacité et met automatiquement en ligne de la capacité supplémentaire grâce à sa fonction de mise à l’échelle automatique.

Dans un tel cas, [!UICONTROL Cloud Manager] déclenche automatiquement le processus d’approvisionnement de mise à l’échelle automatique, envoie une notification de l’événement de mise à l’échelle automatique et met en ligne la capacité supplémentaire en quelques minutes. La capacité supplémentaire est fournie dans l’environnement de production, dans la ou les mêmes régions et conformément aux spécifications système des nœuds Dispatcher/de publication exécutés.

La mise à l’échelle automatique s’applique uniquement au niveau du Dispatcher/de publication et s’exécute à l’aide d’une méthode de mise à l’échelle horizontale, avec au minimum un segment supplémentaire d’une paire Dispatcher/de publication et jusqu’à dix segments maximum. Toute capacité supplémentaire configurée est mise à l’échelle manuellement dans un délai de dix jours ouvrés, selon les indications de l’ingénieur chargé du succès client (CSE).

>[!NOTE]
>
>Si vous souhaitez déterminer si la mise à l’échelle automatique est appropriée pour votre application, veuillez contacter votre CSE ou votre représentant Adobe.

### Déploiements bleu/vert {#blue-green}

Le déploiement bleu/vert est une technique qui réduit les temps d’interruption et les risques en exécutant deux environnements de production identiques appelés bleu/vert.

À tout moment, seul un des environnements est actif, et cet environnement actif diffuse tout le trafic de production. En général, le bleu est l’environnement actif et le vert est inactif.

* Le déploiement bleu/vert est un module complémentaire des pipelines CI/CD de Cloud Manager dans lequel un deuxième ensemble d’instances de publication et de Dispatcher (vert) est créé et utilisé pour les déploiements. Les instances vertes sont ensuite associées à l’équilibreur de charge de production et les anciennes instances (bleues) sont supprimées et interrompues.
* Cette implémentation de bleu/vert traite les instances comme transitoires et chaque itération d’un pipeline bleu/vert crée un nouvel ensemble de serveurs de publication et de Dispatcher.
* Un équilibreur de charge vert sera créé dans le cadre de la configuration. Cet équilibreur de charge ne changera jamais et est ce vers quoi vous devez pointer votre URL verte ou « test ».
* Lors d’un déploiement bleu/vert, une réplication exacte des niveaux de publication/Dispatcher existants est créée.

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
| 8 | L’infrastructure bleue est automatiquement arrêtée | - |

#### Implémentation bleue/verte {#implementing}

Tous les utilisateurs d’AMS qui utilisent Cloud Manager pour les déploiements en production peuvent utiliser le déploiement bleu/vert. Toutefois, l’utilisation du déploiement bleu/vert nécessite une validation supplémentaire de vos environnements et une configuration par un CSE Adobe.

Si le déploiement bleu/vert vous intéresse, veuillez tenir compte des exigences et limites suivantes et contacter votre CSE.

#### Exigences et limites {#limitations}

* Le bleu/vert est uniquement disponible pour les paires publication/Dispatcher.
* Les paires Aperçu de Dispatcher/publication ne font pas partie des déploiements bleu/vert.
* Chaque paire Dispatcher/publication est identique à toutes les autres paires Dispatcher/publication.
* Le bleu/vert n’est disponible que dans l’environnement de production.
* Le bleu/vert est disponible dans AWS ainsi que dans Azure.
* Le bleu/vert n’est pas disponible pour les clients d’Assets uniquement.
