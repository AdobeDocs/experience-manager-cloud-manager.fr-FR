---
title: FAQ relatives à Cloud Manager
description: Découvrez les réponses aux questions les plus fréquemment posées sur Cloud Manager pour les clients AMS.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 52%

---


# FAQ relatives à Cloud Manager {#cloud-manager-faqs}

Ce document fournit des réponses aux questions les plus fréquemment posées sur Cloud Manager pour les clients AMS.

## Est-il possible d’utiliser Java 11 avec les builds de Cloud Manager ? {#java-11}

Oui. Vous devez ajouter le `maven-toolchains-plugin` avec les paramètres appropriés pour Java 11.

* Ce processus est documenté [ici](/help/getting-started/using-the-wizard.md).
* Pour obtenir un exemple, reportez-vous à l’ [exemple de code de projet WKND](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

## Ma version échoue et affiche une erreur concernant maven-scr-plugin, après le passage de Java 8 à Java 11. Que puis-je faire ? {#maven-src-plugin}

Votre build AEM Cloud Manager échoue en cas de tentative de basculement de Java 8 à Java 11. Si vous rencontrez l’erreur ci-dessous, vous devez supprimer `maven-scr-plugin` et convertir toutes les annotations OSGi en annotations OSGi R6.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Pour obtenir des instructions sur la façon de supprimer ce module externe, [voir ici](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/).

## Mon build échoue avec une erreur mentionnant RequireJavaVersion après la bascule de Java 8 à Java 11. Que puis-je faire ? {#requirejavaversion}

Pour les versions de Cloud Manager, la variable `maven-enforcer-plugin` peut échouer à cause de cette erreur.

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

Ce problème connu est dû au fait que Cloud Manager utilise une autre version de Java pour exécuter la commande Maven plutôt que le code de compilation. Omettez `requireJavaVersion` de vos configurations `maven-enforcer-plugin`.

## La vérification de la qualité du code a échoué et le déploiement est maintenant bloqué. Y a-t-il un moyen de contourner cette vérification ? {#deployment-stuck}

Oui. Tous les échecs de qualité du code, à l’exception des évaluations de sécurité, ne sont pas des mesures critiques. Ils peuvent donc être contournés dans le cadre d’un pipeline de déploiement en développant les éléments dans l’interface utilisateur des résultats.

Un utilisateur disposant du rôle [ Deployment Manager, Project Manager ou Business Owner](/help/requirements/users-and-roles.md#role-definitions) peut remplacer les problèmes. Dans ce cas, le pipeline se poursuit. Ou bien, ils peuvent accepter les problèmes, auquel cas le pipeline s’arrête avec un échec.

Voir les documents [Mur à trois niveaux lors de l’exécution d’un pipeline](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) et [Configuration de pipelines hors production](/help/using/non-production-pipelines.md#understanding-the-flow) pour plus d’informations.

## Les déploiements de Cloud Manager échouent à l’étape de test de performances dans les environnements Managed Services d’Adobe. Comment ce problème peut-il être débogué pour transmettre les mesures critiques ? {#debug-critical-metrics}

Il n’y a pas de réponse unique à cette question. Toutefois, les points suivants concernant l’étape de test de performance peuvent s’avérer utiles :

* Cette étape est une étape de performances web. En d’autres termes, il est temps de charger la page à l’aide d’un navigateur web.
* Les URL répertoriées dans le fichier CSV de résultats sont chargées dans un navigateur Chrome, dans l’infrastructure de Cloud Manager, au cours du test.
* Le taux d’erreur est une mesure courante qui échoue. Ainsi, pour qu’une URL soit transmise, l’URL principale doit se charger avec l’état `200` et en moins de `20` secondes. Si le chargement d’une page dépasse `20` secondes, il est marqué comme une erreur `504`.
* Si votre site nécessite une authentification de l’utilisateur, reportez-vous à la section [Présentation des résultats de test](/help/using/code-quality-testing.md#authenticated-performance-testing) pour configurer le test afin que vous puissiez vous authentifier sur votre site.

Pour plus d’informations sur les contrôles de qualité, voir [Présentation des résultats de test](/help/using/code-quality-testing.md) .

## Puis-je utiliser SNAPSHOT pour la version du projet Maven ? {#snapshot}

Oui. Pour les déploiements de développeurs, les fichiers de la branche Git `pom.xml` doivent contenir `-SNAPSHOT` à la fin de la valeur `<version>`.

Cela permet aux déploiements ultérieurs d’être toujours installés lorsque la version n’a pas changé. Pour les déploiements de développeurs, aucune version automatique n’est ajoutée ou générée pour la build maven.

Vous pouvez également définir la version sur `-SNAPSHOT` pour les builds ou déploiements d’évaluation et de production. Cloud Manager définit automatiquement un numéro de version approprié et crée pour vous une balise dans Git. Cette balise peut être référencée ultérieurement, si nécessaire.

De plus amples détails sur la gestion des versions sont [documentés ici](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling).

## Comment le contrôle de version des packages et des offres groupées fonctionne-t-il pour les déploiements d’évaluation et de production ? {#staging-production}

Dans les déploiements d’évaluation et de production, une version automatique est générée [comme documenté ici](/help/managing-code/maven-project-version.md).

Pour le contrôle de version personnalisé dans les déploiements d’évaluation et de production, définissez une version maven en trois parties, telle que `1.0.0`. Passez à la version supérieure à chaque déploiement en production.

Cloud Manager ajoute automatiquement sa version aux versions d’évaluation et de production et crée une branche Git. Aucune configuration spécifique n’est nécessaire. Si vous ne définissez pas de version Maven comme décrit précédemment, le déploiement s’effectue quand même et une version est automatiquement définie.

## Ma build Maven échoue lors des déploiements de Cloud Manager, mais elle est pourtant créée localement sans la moindre erreur. Quel est le problème ? {#maven-build-fail}

Pour plus d’informations, voir cette [ressource Git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) .

## Je ne parviens pas à définir une variable à l’aide d’une commande AIO. Que puis-je faire ? {#set-variable}

Il se peut que vous receviez une erreur 403, comme celle qui suit, lorsque vous tentez de répertorier ou de définir des variables de pipeline par le biais de commandes `aio`.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

Dans ce cas, l’utilisateur exécutant ces commandes doit être ajouté au rôle **Responsable de déploiement** dans Admin Console.

Consultez [Autorisations d’API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/) pour plus d’informations.
