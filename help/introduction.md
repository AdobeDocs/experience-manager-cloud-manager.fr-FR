---
title: Présentation de Cloud Manager pour AMS
description: Commencez ici pour découvrir Cloud Manager pour Adobe Managed Services (AMS) et comment il permet aux entreprises de gérer elles-mêmes Adobe Experience Manager dans le cloud.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 23%

---


# Introduction à [!UICONTROL Cloud Manager] pour AMS {#introduction-to-cloud-manager}

Commencez ici pour découvrir Cloud Manager pour Adobe Manage Services (AMS) et comment il permet aux entreprises de gérer elles-mêmes Adobe Experience Manager dans le cloud.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Présentation de Cloud Manager pour AMS"
>abstract="Permet aux entreprises de gérer elles-mêmes Adobe Experience Manager dans le cloud. Il comprend une structure d’intégration et de diffusion continues (CI/CD) qui permet aux équipes informatiques et aux partenaires d’implémentation d’accélérer la diffusion des personnalisations ou des mises à jour sans compromettre les performances ou la sécurité."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=fr#cloud-manager" text="Créer des programmes"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=fr#cloud-manager" text="Créer des environnements"

## Présentation {#introduction}

[!UICONTROL Cloud Manager] for Adobe Experience Manager permet aux développeurs de créer des expériences client percutantes grâce à des workflows rationalisés, reposant sur les bonnes pratiques Adobe Experience Manager. Les pipelines CI/CD optimisés pour Adobe Experience Manager vous permettent de fusionner facilement des workflows de développement en archivant simplement votre code, qui peut ensuite se déplacer jusqu’à être prêt pour la production. Pendant la phase de création, vos mises à jour de code personnalisé sont soigneusement testées par rapport aux bonnes pratiques pour fournir des applications fiables à vos clients. Cloud Manager utilise une approche API ouverte et vous permet de l’intégrer à vos systèmes sans interrompre les processus et outils existants.

>[!NOTE]
>
>Cette documentation décrit spécifiquement les fonctionnalités de Cloud Manager pour Adobe Managed Services (AMS).
>
>Vous trouverez la documentation équivalente pour AEM as a Cloud Service dans la section [AEM documentation as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/home.html?lang=fr)

Avec Cloud Manager, votre équipe de développement bénéficie des fonctionnalités suivantes :

* Intégration continue/diffusion continue (CI/CD) du code afin de réduire le temps de mise sur le marché de plusieurs mois/semaines à plusieurs jours/heures.

* Inspection du code, tests de performance et validation de la sécurité basés sur les bonnes pratiques avant de passer en production afin de minimiser les interruptions de production

* Connectivité de l’API pour compléter les processus DevOps existants

* Mise à l’échelle automatique qui détecte intelligemment la nécessité d’une capacité accrue et apporte automatiquement des segments Dispatcher/Publication supplémentaires en ligne

Cette image illustre le flux de processus CI/CD utilisé dans [!UICONTROL Cloud Manager]:

![Flux CI/CD](/help/assets/screen_shot_2018-05-12at73843pm.png)

## Fonctionnalités clés de [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Vous trouverez ci-dessous un aperçu plus détaillé de certaines fonctionnalités clés de Cloud Manager.

### Interface en libre-service {#self-service-interface}

L’interface utilisateur (IU) pour [!UICONTROL Cloud Manager] vous permet d’accéder facilement à l’environnement cloud et au pipeline CI/CD pour vos applications Adobe Experience Manager et de les gérer.

Vous définissez des indicateurs de performances clés (IPC) spécifiques à l’application (tels que le pic de pages vues par minute et le temps de réponse attendu pour un chargement de page) qui constituent la base de la mesure d’un déploiement réussi. Les rôles et autorisations des différents membres de l’équipe peuvent être facilement définis. L’interface en libre-service vous permet de contrôler vos activités, mais elle propose également des liens vers les bonnes pratiques et l’accès à des experts en Adobe qui peuvent vous donner les conseils nécessaires si nécessaire.

Pour découvrir et commencer à utiliser [!UICONTROL Cloud Manager]Interface utilisateur de , voir le document [Première connexion.](/help/getting-started/first-time-login.md)

### Pipeline CI/CD {#ci-cd-pipeline}

[!UICONTROL Cloud Manager] permet de tirer parti d’un pipeline CI/CD optimisé pour accélérer la diffusion du code personnalisé ou des mises à jour, telles que l’ajout de composants sur le site web.

Par le biais de la [!UICONTROL Cloud Manager] Dans l’interface utilisateur, vous pouvez configurer et lancer votre pipeline CI/CD. Dans le cadre de ce pipeline, une analyse approfondie du code est exécutée pour s’assurer que seules les applications de haute qualité sont transmises à l’environnement de production.

Pour en savoir plus sur la configuration du pipeline depuis l’interface utilisateur de [!UICONTROL Cloud Manager], consultez les documents [Configuration de pipelines de production](/help/using/production-pipelines.md) et [Configuration de pipelines hors production](/help/using/non-production-pipelines.md).

### Modes de déploiement flexibles {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] offre des modes de déploiement flexibles et configurables afin que vous puissiez diffuser des expériences en fonction de l’évolution des besoins de l’entreprise.

Avec un mode de déclenchement automatique, le code est automatiquement déployé dans un environnement en fonction d’événements spécifiques tels que la validation du code. Vous pouvez également planifier des déploiements de code pendant les périodes spécifiées, même en dehors des heures de bureau.

Indépendamment du déclencheur de déploiement, les contrôles de qualité sont toujours effectués dans le cadre de l’exécution du pipeline CI/CD chaque fois qu’un déploiement est déclenché. Les contrôles de qualité incluent, entre autres, l’inspection du code, les tests de sécurité et les tests de performance, qui sont tous livrés d’usine sans aucun effort de votre part ou de vos partenaires.

Pour en savoir plus sur le déploiement des contrôles de code et de qualité, consultez le document [Déploiement du code.](/help/using/code-deployment.md)

### Mise à l’échelle automatique {#autoscaling}

lorsque l&#39;environnement de production est soumis à une charge exceptionnellement élevée, [!UICONTROL Cloud Manager] détecte la nécessité d’une capacité supplémentaire et apporte automatiquement de la capacité supplémentaire en ligne à l’aide de sa fonction de mise à l’échelle automatique.

Dans un tel événement, [!UICONTROL Cloud Manager] déclenche automatiquement le processus de mise à l’échelle automatique, envoie une notification de l’événement de mise à l’échelle automatique et met la capacité supplémentaire en ligne en quelques minutes. La capacité supplémentaire est configurée dans l’environnement de production, dans la ou les mêmes régions, et répond aux mêmes spécifications système que les noeuds Dispatcher/Publication en cours d’exécution.

La fonction de mise à l’échelle automatique s’applique uniquement au niveau Dispatcher/publication et est exécutée à l’aide d’une méthode de mise à l’échelle horizontale, avec au moins un segment supplémentaire d’une paire dispatcher/publication jusqu’à dix segments au maximum. Toute capacité supplémentaire configurée sera mise à l’échelle manuellement dans un délai de dix jours ouvrés, selon les indications de l’ingénieur du service client.

>[!NOTE]
>
>Les clients qui souhaitent déterminer si la mise à l’échelle automatique est appropriée ou non pour leur application doivent contacter leur ingénieur du service client ou leur représentant Adobe.
