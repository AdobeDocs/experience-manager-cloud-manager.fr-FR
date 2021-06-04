---
title: FAQ sur Cloud Manager
seo-title: FAQ sur Cloud Manager
description: Consultez la FAQ sur Cloud Manager pour obtenir des conseils de dépannage
seo-description: Consultez cette page pour obtenir des réponses aux questions les plus fréquentes sur Cloud Manager
feature: Prise en main
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# FAQ sur Cloud Manager {#cloud-manager-faqs}

La section suivante fournit des réponses aux questions les plus fréquentes relatives à Cloud Manager.

## Est-il possible d’utiliser Java 11 avec les builds de Cloud Manager ? {#java-11-cloud-manager}

Le build AEM Cloud Manager échoue en cas de tentative de basculement de la version Java 8 à Java 11. Le problème peut avoir de nombreuses causes et la plupart des causes les plus courantes sont documentées ci-dessous :

* Ajoutez le plug-in maven-toolchain-plugin avec les paramètres appropriés pour Java 11, comme indiqué [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=fr#getting-started).  Par exemple, consultez [l’exemple de code de projet wknd](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Si vous rencontrez l’erreur ci-dessous, vous devez supprimer l’utilisation de `maven-scr-plugin` et convertir toutes les annotations OSGi en annotations OSGi R6. Pour obtenir des instructions, consultez [ce lien](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Pour les builds de Cloud Manager, le plug-in Maven Enforcer échoue en présentant l’erreur `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Il s’agit d’un problème connu dû au fait que Cloud Manager utilisait une version différente de Java pour exécuter la commande maven plutôt que de compiler le code. Pour l’instant, évitez d’utiliser `requireJavaVersion` dans vos configurations maven-force-application-plugin.

## Notre déploiement est bloqué en raison de l’échec de la vérification de la qualité du code. Y a-t-il un moyen de contourner cette vérification ? {#deployment-stuck}

Tous les échecs de qualité du code, à l’exception de la *Cote de sécurité*, ne sont pas des mesures critiques ; ils peuvent donc être contournés en développant les éléments dans l’interface utilisateur des résultats.

Un utilisateur ayant un rôle de [responsable de déploiement, responsable de projet ou propriétaire d’entreprise](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=fr#requirements) peut, au choix, contourner les problèmes, auquel cas le pipeline continue, ou les accepter, auquel cas le pipeline s’arrête avec un échec.  Pour plus d’informations, consultez [Points de contrôle à trois niveaux lors de l’exécution d’un pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=fr#how-to-use).

## Les déploiements de Cloud Manager échouent à l’étape de test de performances dans les environnements Managed Services d’Adobe. Comment déboguer cette erreur pour transmettre les mesures critiques ? {#debug-critical-metrics}

Consultez [Présentation des résultats des tests](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) pour comprendre les résultats.

Quelques remarques sur l’étape de test de performance :

* L’*étape de performance* est une étape de performances web qui teste le temps de chargement de la page par un navigateur web.
* Les URL répertoriées dans le fichier *CSV* de résultat sont chargées dans un navigateur Chrome dans l’infrastructure de Cloud Manager pendant le test.
* Une des mesures échouant couramment est le *taux d’erreur*. Pour qu’une URL soit transmise, l’URL principale doit se charger avec l’état `200` et en moins de `20` secondes. Les chargements de page qui dépassent `20` secondes sont marqués comme des erreurs `504`.
* Si votre site requiert l’authentification des utilisateurs, consultez [Test de performances avec authentification](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=fr#how-to-use) pour configurer le test d’authentification de votre site.

## Sommes-nous autorisés à utiliser SNAPSHOT dans la version de projet Maven ? Comment le contrôle de version des packages et des fichiers jar par lots fonctionne-t-il pour les déploiements en évaluation et en production ? {#snapshot-version}

Reportez-vous aux scénarios suivants pour en savoir plus sur le contrôle de version des packages et des fichiers jar par lots pour les déploiements en évaluation et en production :

1. Pour les déploiements de développeurs, les fichiers de la branche Git `pom.xml` doivent contenir `-SNAPSHOT` à la fin de la valeur `<version>`. Cela permet les déploiements ultérieurs lorsque la version ne change pas. Pour les déploiements développeurs, aucune version automatique n’est ajoutée ou générée pour la build maven.

1. En cas de déploiement d’évaluation et de production, une version automatique est générée comme indiqué [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=fr#managing-code).

1. Pour le contrôle de version personnalisé dans les déploiements d’évaluation et de production, définissez une version maven en 3 parties telle que `1.0.0`. Mettez à jour la version chaque fois que vous devez effectuer un autre déploiement en production.

1. Cloud Manager ajoute automatiquement sa version aux versions d’évaluation et de production et crée même une branche Git. Aucune configuration spécifique n’est nécessaire. Si l’étape 3 ci-dessus est ignorée, le déploiement fonctionnera correctement et une version sera automatiquement définie.

1. Il n’y aura aucun problème si vous laissez la version avec `-SNAPSHOT` pour les versions ou déploiements d’évaluation et de production. Cloud Manager définit automatiquement un numéro de version approprié et crée pour vous une balise dans Git. Cette balise peut être référencée ultérieurement, si nécessaire.

1. Si vous souhaitez tester un code sur l’environnement de développement, vous pouvez créer une nouvelle branche Git et configurer le pipeline pour qu’il utilise cette autre branche. Cela peut s’avèrer utile lorsque le lancement des déploiements échoue et que vous souhaitez tester les versions plus anciennes du code pour déterminer à quel moment il a échoué.

   La commande Git ci-dessous crée une branche distante nommée *testbranch1* par rapport à une validation préexistante spécifique `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Cette branche spéciale peut être utilisée dans Cloud Manager sans affecter les autres branches :

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Consultez la [documentation Git](https://git-scm.com/book/en/v2/Git-Internals-Git-References) pour plus d’informations.

   Si vous souhaitez supprimer ultérieurement la branche de test, utilisez la commande delete :

   `git push origin --delete testbranch1`

## La compilation Maven échoue dans les déploiements de Cloud Manager, mais se crée localement sans erreurs. Comment déboguer ? {#maven-build-fail}

Consultez [Ressource Git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) pour plus d’informations.

## Impossible de définir une variable à l’aide des variables de pipeline définies par le Cloud Manager aio. Comment déboguer ces problèmes ? {#set-variable}

Si vous obtenez une erreur `403` lorsque vous tentez de référencer ou de définir des variables de pipeline au moyen de commandes similaires à celles ci-dessous, vous devez être ajouté en tant que rôle de produit *Responsable de déploiement* Cloud Manager dans Admin Console.\
Consultez [Autorisations d’API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) pour plus d’informations.

Commandes et erreurs connexes :

`$ aio cloudmanager:list-pipeline-variables 222`

*Erreur* : `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Erreur* : `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
