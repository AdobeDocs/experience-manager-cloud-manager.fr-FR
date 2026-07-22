---
title: Présentation de Cloud Manager pour AMS
description: Commencez ici pour découvrir Cloud Manager pour Adobe Managed Services (AMS) et comment il permet aux entreprises d’auto-gérer Adobe Experience Manager en mode cloud.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
TQID: https://experienceleague.adobe.com/VR-H6ubMFgVrkfzDvY4JWYlUtM-Dkztdewr5LiSZK1w
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754bid: ff09c71c-26a9-449a-85f8-2aeb8ce96100
subfeature_v2: id: a4d14782-c381-4db2-89e3-8cf3f31b103cid: c14b2f98-ee16-4c49-b87b-919c91b01d9d
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ee4f497a8bb5fb2d37fd8283721ebc9891f9053a
workflow-type: tm+mt
source-wordcount: 1266
ht-degree: 69%

---

# Présentation de [!UICONTROL Cloud Manager] pour AMS {#introduction-to-cloud-manager}

Pour découvrir Cloud Manager pour AMS (Adobe Managed Services) et comment il permet aux entreprises d’auto-gérer Adobe Experience Manager en mode cloud, commencez ici.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Présentation de Cloud Manager pour AMS"
>abstract="Il permet aux entreprises de gérer elles-mêmes Adobe Experience Manager dans le cloud à l’aide d’un framework CI/CD. Ce framework permet aux équipes d’accélérer les personnalisations ou les mises à jour sans compromettre les performances ou la sécurité."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/cloud-manager/programs#cloud-manager" text="Créer des programmes"
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/cloud-manager/environments#cloud-manager" text="Créer des environnements"

## Présentation {#introduction}

[!UICONTROL Cloud Manager] for Adobe Experience Manager permet aux développeurs de créer des expériences client percutantes grâce à des workflows rationalisés, reposant sur les bonnes pratiques Adobe Experience Manager. Les pipelines CI/CD optimisés pour Adobe Experience Manager permettent de fusionner des workflows de développement en archivant votre code, qui est ensuite prêt pour la production. Pendant la phase de création, vos mises à jour de code personnalisé sont soigneusement testées par rapport aux bonnes pratiques pour fournir des applications fiables à vos clients. Cloud Manager utilise une approche d’API ouverte et vous permet de l’intégrer à vos systèmes sans interrompre les processus et outils existants.

>[!NOTE]
>
>Cette documentation décrit spécifiquement les fonctionnalités et les caractéristiques de Cloud Manager pour Adobe Managed Services (AMS).
>
>Retrouvez la documentation équivalente pour les clientes et clients AEM as a Cloud Service dans la [Documentation d’AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/home).

Avec Cloud Manager, votre équipe de développement bénéficie des fonctionnalités suivantes :

* Intégration continue/diffusion continue (CI/CD) du code pour réduire les cycles de développement de mois/semaines à jours/heures.
* Inspection du code, test de performance et validation de la sécurité basés sur les bonnes pratiques avant de passer à la production, afin de minimiser les interruptions de production.
* Connectivité de l’API pour compléter les processus DevOps existants.
* Mise à l’échelle automatique qui détecte la nécessité d’une capacité accrue et approvisionne automatiquement des segments Dispatcher/de publication supplémentaires.

![Flux CI/CD](/help/assets/screen_shot_2018-05-12at73843pm.png)Le flux du processus CI/CD utilisé dans [!UICONTROL Cloud Manager].

## Fonctionnalités clés de [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Les sections suivantes mettent en évidence les principales fonctionnalités de Cloud Manager.

### Interface en libre-service {#self-service-interface}

Pour découvrir et commencer à utiliser l’interface d’utilisation de [!UICONTROL Cloud Manager], consultez la rubrique [Première connexion](/help/getting-started/first-time-login.md).

L’interface utilisateur de  permet d’accéder à l’environnement cloud et au pipeline CI/CD et de les gérer facilement pour vos applications Adobe Experience Manager.

Vous définissez des indicateurs clés de performances (KPI) spécifiques à l’application, tels que le pic de pages vues par minute ou le temps de réponse attendu pour le chargement d’une page. Ces KPI servent de base pour mesurer le succès du déploiement. Les rôles et autorisations des différentes personnes membres de l’équipe peuvent être facilement définis. L’interface en libre-service vous offre un contrôle total. Elle fournit également des liens vers les ressources sur les bonnes pratiques et l’accès à des spécialistes d’Adobe pour obtenir des conseils lorsque vous en avez besoin.

### Pipeline CI/CD {#ci-cd-pipeline}

L’une des principales fonctionnalités de  est la possibilité d’utiliser un pipeline CI/CD optimisé pour accélérer la diffusion du code personnalisé ou des mises à jour, telles que l’ajout de composants sur le site web.

Grâce à l’interface utilisateur , vous pouvez configurer et démarrer votre pipeline CI/CD. Durant ce pipeline, une analyse approfondie du code est exécutée pour garantir que seules des applications de haute qualité transitent par l’environnement de production.

Pour en savoir plus sur la configuration des pipelines à partir de l’interface utilisateur de , voir [Configuration de pipelines de production](/help/using/production-pipelines.md) et [Configuration de pipelines hors production](/help/using/non-production-pipelines.md).

### Modes de déploiement flexibles {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] offre aux clients des modes de déploiement flexibles et configurables afin qu’ils puissent fournir des expériences en fonction de l’évolution des demandes métier.

Grâce à un mode de déclenchement automatique, le code est automatiquement déployé dans un environnement en fonction d’événements spécifiques tels que la validation du code. Vous pouvez également planifier des déploiements de code pendant les périodes spécifiées, même en dehors des heures de bureau.

Indépendamment du déclencheur de déploiement, les vérifications de qualité sont toujours effectuées dans le cadre de l’exécution du pipeline CI/CD, et ce, chaque fois qu’un déploiement est déclenché. Les contrôles de qualité comprennent l’inspection de code, les tests de sécurité et les tests de performance, qui sont tous fournis en tant que fonctionnalités standard sans effort requis de votre part ou de la part de vos partenaires.

Pour en savoir plus sur le déploiement de code et les vérifications de qualité, consultez la rubrique [Déploiement de code](/help/using/code-deployment.md).

## Fonctionnalités facultatives de Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager propose des fonctionnalités avancées supplémentaires qui s’appliquent à votre projet en fonction de la configuration et des besoins de votre environnement. Pour en discuter plus en détail, contactez votre ingénieur du succès client (CSE) ou votre représentant Adobe si ces fonctionnalités vous intéressent.

### Mise à l’échelle automatique {#autoscaling}

Lorsque l’environnement de production est soumis à une charge exceptionnellement élevée,  détecte la nécessité d’une capacité supplémentaire et approvisionne automatiquement la capacité supplémentaire à l’aide de sa fonction de mise à l’échelle automatique.

Dans un tel cas,  déclenche automatiquement le processus d&#39;approvisionnement de mise à l&#39;échelle automatique, envoie une notification de l&#39;événement de mise à l&#39;échelle automatique et approvisionne la capacité supplémentaire en quelques minutes. La capacité supplémentaire est fournie dans l’environnement de production et dans les mêmes régions, conformément aux spécifications système des nœuds Dispatcher/de publication en cours d’exécution.

La fonctionnalité de mise à l’échelle automatique s’applique au niveau Dispatcher/de publication, en utilisant la mise à l’échelle horizontale pour ajouter un à dix segments de paires Dispatcher/de publication. Toute capacité supplémentaire configurée est mise à l’échelle manuellement dans un délai de dix jours ouvrés, selon les indications du responsable du succès client Adobe.

>[!NOTE]
>
>Si vous souhaitez déterminer si la mise à l’échelle automatique convient à votre application, contactez votre CSE ou votre représentant ou représentante Adobe.

### Déploiements bleu/vert {#blue-green}

Le déploiement bleu/vert est une technique qui réduit les temps d’interruption et les risques en exécutant deux environnements de production identiques appelés bleu/vert.

À tout moment, seul un des environnements est actif, et cet environnement actif diffuse tout le trafic de production. En général, le bleu est l’environnement actif et le vert est inactif.

* Le déploiement bleu/vert est un module complémentaire des pipelines CI/CD de Cloud Manager dans lequel un deuxième ensemble d’instances de publication et de Dispatcher (vert) est créé et utilisé pour les déploiements. Les instances vertes sont ensuite associées à la répartition de charge de production et les anciennes instances (bleues) sont supprimées et interrompues.
* Cette implémentation de bleu/vert traite les instances comme transitoires et chaque itération d’un pipeline bleu/vert crée un ensemble de serveurs de publication et de Dispatcher.
* Une répartition de charge verte sera créée dans le cadre de la configuration. Cet équilibreur de charge ne change jamais et est la cible de votre URL verte ou « test ».
* Lors d’un déploiement bleu/vert, une réplique exacte des niveaux de publication/Dispatcher existants est créée.

#### Flux de déploiement bleu/vert {#flow}

Lorsque le déploiement bleu/vert est activé, le flux de déploiement diffère du flux de déploiement du service cloud standard.

| Étape | Déploiement bleu/vert | Déploiement standard |
| --- | --- | --- |
| 1 | Déploiement vers l’auteur | Déploiement vers l’auteur |
| 2 | Mise en pause pour le test | - |
| 3 | Une infrastructure verte est créée | - |
| 4 | Déploiement vers le niveau Publication verte/Dispatcher | Déploiement vers l’éditeur |
| 5 | Mise en pause pour le test (jusqu’à 24 heures) | - |
| 6 | Une infrastructure verte est ajoutée à l’équilibreur de charge de production | - |
| 7 | L’infrastructure bleue est supprimée de la répartition de charge de production | - |
| 8 | Suspendre pour la validation finale (jusqu’à 24 heures) | - |
| 9 | L’infrastructure bleue est automatiquement arrêtée | - |
| 10 | Fin du pipeline | - |

#### Implémentation bleue/verte {#implementing}

Les utilisateurs et utilisatrices d’AMS qui utilisent Cloud Manager pour les déploiements en production peuvent utiliser le déploiement bleu/vert. Toutefois, l’utilisation du déploiement bleu/vert nécessite une validation supplémentaire de vos environnements et une configuration par l’équipe d’ingénierie du service client Adobe.

Si le déploiement bleu/vert vous intéresse, tenez compte des exigences et limites suivantes et contactez votre CSE.

#### Exigences et limites {#limitations}

* Le bleu/vert est uniquement disponible pour les paires publication/Dispatcher.
* Les paires de prévisualisation Dispatcher/de publication ne font pas partie des déploiements bleu/vert.
* Chaque paire Dispatcher/publication est identique à toutes les autres paires Dispatcher/publication.
* Le bleu/vert n’est disponible que dans l’environnement de production.
* Le déploiement bleu/vert est disponible dans AWS, ainsi que dans Azure.
* Le bleu/vert n’est pas disponible pour les clientes et clients d’Assets uniquement.
