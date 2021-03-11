---
title: FAQ sur Cloud Manager
seo-title: FAQ sur Cloud Manager
description: Consultez la FAQ de Cloud Manager pour obtenir quelques conseils de dépannage
seo-description: Suivez cette page pour obtenir des réponses aux questions fréquentes sur Cloud Manager
translation-type: tm+mt
source-git-commit: cf5c02c8c594015b6baa00e1a8aaa2d898aa60a9
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 2%

---


# FAQ sur Cloud Manager {#cloud-manager-faqs}

La section suivante fournit des réponses aux questions fréquentes relatives à Cloud Manager.

## Est-il possible d’utiliser Java 11 avec les versions de Cloud Manager ? {#java-11-cloud-manager}

AEM version de Cloud Manager échoue lors de la tentative de basculement de la version Java 8 à 11. Le problème peut avoir de nombreuses causes et la plupart des causes les plus courantes sont documentées ci-dessous :

* Ajoutez le maven-toolchain-plugin avec les paramètres appropriés pour Java 11, comme indiqué [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started).  Par exemple, voir l&#39;exemple de code de projet [wknd](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Si vous rencontrez l&#39;erreur ci-dessous, vous devez supprimer l&#39;utilisation de `maven-scr-plugin` et convertir toutes les annotations OSGi en annotations OSGi R6. Pour obtenir des instructions, voir [ici](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Pour les versions de Cloud Manager, le module externe de mise en oeuvre maven échoue avec l’erreur `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Il s’agit d’un problème connu en raison duquel Cloud Manager utilisait une autre version de Java pour exécuter la commande maven plutôt que de compiler le code. Pour l’instant, omettez `requireJavaVersion` de vos configurations maven-force-application-plugin.

## Notre déploiement est bloqué en raison de l&#39;échec de la vérification de la qualité du code. Y a-t-il un moyen de contourner ce contrôle ? {#deployment-stuck}

Tous les échecs de qualité du code, à l’exception de *Cote de sécurité*, ne sont pas des mesures critiques ; ils peuvent donc être contournés en développant les éléments dans l’interface utilisateur des résultats.

Un utilisateur doté du rôle [Deployment Manager, Project Manager ou Business Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) peut remplacer les problèmes, auquel cas le pipeline se poursuit ou il peut accepter les problèmes, auquel cas le pipeline s&#39;arrête en cas d&#39;échec.  Voir [Portes à trois niveaux lors de l&#39;exécution d&#39;un pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=fr#how-to-use) pour plus d&#39;informations.

## Les déploiements de Cloud Manager échouent à l’étape de test des performances dans les environnements de services gérés d’Adobe. Comment déboguer ceci pour transmettre les mesures critiques ? {#debug-critical-metrics}

Voir [Comprendre vos résultats de test](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) pour comprendre les résultats.

Quelques remarques sur l&#39;étape du test de performances :

* L&#39;*étape de performances* est une étape de performances Web, c&#39;est-à-dire le temps de chargement de la page à l&#39;aide d&#39;un navigateur Web.
* Les URL répertoriées dans le fichier de résultat *CSV* sont chargées dans un navigateur Chrome dans l’infrastructure de Cloud Manager pendant le test.
* Une mesure courante qui échoue est le *taux d&#39;erreur*. Pour qu’une URL soit transmise, l’URL principale doit se charger avec l’état `200` et en moins de `20` secondes. Les chargements de page qui dépassent `20` secondes sont marqués comme des erreurs `504`.
* Si votre site requiert l’authentification des utilisateurs, voir [Test des performances authentifiées](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#how-to-use) pour configurer le test afin de l’authentifier sur votre site.

## Sommes-nous autorisés à utiliser SNAPSHOT dans la version du projet Maven ? Comment le contrôle de version des packages et des fichiers jar d’assemblage fonctionne-t-il pour les déploiements Stage et Production ? {#snapshot-version}

Reportez-vous aux scénarios suivants pour en savoir plus sur le contrôle de version des packages et des fichiers jar d’assemblage pour les déploiements Stage et Production :

1. Pour les déploiements de développeurs, les fichiers de la branche Git `pom.xml` doivent contenir `-SNAPSHOT` à la fin de la valeur `<version>`. Ceci permet un déploiement ultérieur lorsque la version ne change pas pour être toujours installée. Dans les déploiements de développeurs, aucune version automatique n’est ajoutée ou générée pour la création d’expert.

1. Dans le déploiement d’étape et de production, une version automatique est générée comme indiqué [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code).

1. Pour le contrôle de version personnalisé dans les déploiements d’étape et de production, définissez une version d’expert en 3 parties, telle que `1.0.0`. Augmentez la version chaque fois que vous devez effectuer un autre déploiement en production.

1. Cloud Manager ajoute automatiquement sa version aux versions d’évaluation et de production et crée même une branche Git. Aucune configuration spéciale n’est requise. Si l’étape 3 ci-dessus est ignorée, le déploiement fonctionnera correctement et une version sera automatiquement définie.

1. Il n’y a aucun problème, si vous laissez la version avec `-SNAPSHOT` pour les versions ou déploiements d’étape et de production. Cloud Manager définit automatiquement un numéro de version approprié et crée une balise pour vous dans Git. Cette balise peut être référencée ultérieurement, si nécessaire.

1. Si vous souhaitez tester du code expérimental sur l&#39;environnement de développement, vous pouvez créer une nouvelle branche Git et définir le pipeline pour utiliser cette autre branche. Cela s’avère utile lorsque le début des déploiements échoue et que vous souhaitez tester les versions plus anciennes du code pour déterminer à quel moment il a échoué.

   La commande Git ci-dessous crée une branche distante nommée *testbranch1* par rapport à une validation préexistante spécifique `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Cette branche spéciale peut être utilisée dans Cloud Manager sans affecter les autres branches :

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Consultez la [documentation Git](https://git-scm.com/book/en/v2/Git-Internals-Git-References) pour plus de détails.

   Si vous souhaitez supprimer ultérieurement la branche de test, utilisez la commande delete :

   `git push origin --delete testbranch1`

## La création Maven échoue dans les déploiements de Cloud Manager, mais se construit localement sans erreurs. Débogage? {#maven-build-fail}

Voir [Git Resource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) pour plus de détails.

## Impossible de définir une variable via les variables de pipeline définies par le gestionnaire de cloud d’aio. Comment déboguer ces problèmes ? {#set-variable}

Si vous obtenez une erreur `403` lorsque vous tentez de liste ou de définir des variables de pipeline au moyen de commandes similaires à celles ci-dessous, vous devez être ajouté en tant que rôle de produit *Deployment Manager* Cloud Manager dans le Admin Console.\
Voir [Autorisations d’API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) pour plus d’informations.

Commandes et erreurs connexes :

`$ aio cloudmanager:list-pipeline-variables 222`

*Erreur*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Erreur*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`