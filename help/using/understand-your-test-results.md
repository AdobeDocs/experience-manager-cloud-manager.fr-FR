---
title: Présentation des résultats de test
description: Découvrez le fonctionnement du test de qualité du code des pipelines et comment il peut améliorer la qualité de vos déploiements.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
feature: CI-CD Pipeline, Test Results
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: 2179314120911cac8a0dd99a8b57974751959871
workflow-type: tm+mt
source-wordcount: '2901'
ht-degree: 30%

---

# Présentation des résultats de test {#understand-your-test-results}

Découvrez le fonctionnement du test de qualité du code des pipelines et comment il peut améliorer la qualité de vos déploiements.

## Présentation {#introduction}

Pendant l’exécution du pipeline, un certain nombre de mesures sont capturées et comparées soit aux indicateurs de performances clés (IPC) définis par le propriétaire de l’entreprise, soit aux normes définies par Adobe Managed Services.

Ces rapports sont signalés à l’aide d’un système d’évaluation à trois niveaux, tel que défini dans la section suivante.

>[!NOTE]
>
>Pour en savoir plus sur les tests pris en charge par Cloud Manager pour AEM as a Cloud Service, reportez-vous à la section [AEM documentation as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/test-results/overview-test-results.html).


## Classement à trois niveaux  {#three-tier-gates-while-running-a-pipeline}

Le pipeline comprend trois points de contrôle :

* Qualité du code
* Test de performance
* Test de sécurité

Pour chacun de ces points de contrôle, il existe une structure à trois niveaux pour les problèmes identifiés.

* **Critique** - Il s’agit de problèmes qui entraînent l’échec immédiat du pipeline.
* **Important** - Il s’agit de problèmes qui entraînent la suspension du pipeline. Un responsable de déploiement, un responsable de projet ou un propriétaire d’entreprise peuvent soit contourner les problèmes, auquel cas le pipeline continue, soit accepter les problèmes, auquel cas le pipeline s’arrête avec un échec. Le remplacement des échecs importants est soumis à une [délai d’expiration.](deploying-code.md#timeouts)
* **Infos** - Il s’agit de problèmes qui sont fournis uniquement à titre d’information et qui n’ont aucun impact sur l’exécution du pipeline.

>[!NOTE]
>
>Dans un pipeline portant uniquement sur la qualité du code, les échecs importants du point de contrôle Qualité du code ne peuvent pas être remplacés, car l’étape de test de qualité du code est la dernière étape du pipeline.

## Test de qualité du code {#code-quality-testing}

Cette étape évalue la qualité du code de votre application, qui est l’objectif principal d’un pipeline de qualité de code uniquement. Elle est exécutée immédiatement après l’étape de création dans tous les pipelines hors production et de production. Reportez-vous au document [Configuration de pipelines hors production](configuring-non-production-pipelines.md) pour en savoir plus.

### Présentation du test de qualité du code {#understanding-code-quality-testing}

Le test de qualité du code analyse le code source pour s’assurer qu’il répond à certains critères de qualité. Cela est mis en oeuvre par une combinaison d’analyse SonarQube, d’examen au niveau du module de contenu à l’aide d’OakPAL et de validation du Dispatcher à l’aide de l’outil d’optimisation de Dispatcher.

Il existe plus de 100 règles combinant des règles Java génériques et des règles spécifiques à AEM. Certaines des règles spécifiques à AEM sont créées en fonction des bonnes pratiques de l’équipe d’ingénierie AEM et sont appelées [Règles de qualité du code personnalisées.](/help/using/custom-code-quality-rules.md)

>[!NOTE]
>
>Vous pouvez télécharger la liste complète des règles [via ce lien.](/help/using/assets/CodeQuality-rules-latest-AMS.xlsx)

Les résultats des tests de qualité du code sont fournis en tant que **évaluations**. Le tableau suivant résume les notes attribuées à divers critères de test.

| Nom | Définition | Catégorie | Seuil d’échec |
|--- |--- |--- |--- |
| Note de sécurité | A = Aucune vulnérabilité<br/>B = Au moins 1 vulnérabilité mineure<br/>C = Au moins 1 vulnérabilité majeure<br/>D = Au moins 1 vulnérabilité critique<br/>E = Au moins 1 vulnérabilité de bloqueur | Critique | &lt; B |
| Note de fiabilité | A = Aucun bogue<br/>B = Au moins 1 bogue mineur <br/>C = Au moins 1 bogue majeur<br/>D = Au moins 1 bogue critique<br/>E = Au moins 1 bogue de blocage | Important | &lt; C |
| Note de maintenabilité | Défini par le coût de correction en suspens pour le code sent comme un pourcentage du temps qui a déjà été consacré à l’application.<br/><ul><li>A = &lt;=5 %</li><li>B = 6-10 %</li><li>C = 11-20 %</li><li>D = 21-50 %</li><li>E = > 50 %</li></ul> | Important | &lt; A |
| Couverture | Défini par un mélange de couverture de ligne de test unitaire et de couverture de condition à l’aide de la formule : <br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = Conditions qui ont été évaluées comme `true` au moins une fois lors de l’exécution de tests unitaires</li><li>`CF` = Conditions qui ont été évaluées comme `false` au moins une fois lors de l’exécution de tests unitaires</li><li>`LC` = Lignes couvertes = lines_to_cover - uncover_lines</li><li>`B` = nombre total de conditions</li><li>`EL` = nombre total de lignes exécutables (lines_to_cover)</li></ul> | Important | &lt; 50 % |
| Tests unitaires ignorés | Nombre de tests unitaires ignorés | Infos | > 1 |
| Problèmes en cours | Types de problèmes généraux – Vulnérabilités, bogues et smells de code | Infos | > 0 |
| Lignes dupliquées | Défini comme le nombre de lignes impliquées dans les blocs dupliqués. Un bloc de code est considéré comme dupliqué dans les conditions suivantes.<br>Projets non Java :<ul><li>Il doit y avoir au moins 100 jetons successifs et dupliqués.</li><li>Ces jetons doivent être répartis au moins sur : </li><li>30 lignes de code pour COBOL </li><li>20 lignes de code pour ABAP </li><li>10 lignes de code pour d’autres langages</li></ul>Projets Java :<ul></li><li> Il doit y avoir au moins 10 instructions successives et dupliquées, quel que soit le nombre de jetons et de lignes.</li></ul>Les différences dans la mise en retrait ainsi que dans les littéraux de chaîne sont ignorées lors de la détection des doublons. | Infos | > 1 % |
| Compatibilité Cloud Service | Nombre de problèmes de compatibilité Cloud Service identifiés | Infos | > 0 |

>[!NOTE]
>
>Voir [Définitions des mesures de SonarQube](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) pour plus d’informations.

>[!NOTE]
>
>Pour en savoir plus sur les règles de qualité du code personnalisé exécutées par [!UICONTROL Cloud Manager], reportez-vous au document . [Règles de qualité du code personnalisé.](custom-code-quality-rules.md)

### Traitement des faux positifs {#dealing-with-false-positives}

Le processus d’analyse de qualité n’est pas parfait et identifiera parfois de manière incorrecte des problèmes qui ne sont pas réellement problématiques. On parle alors de **faux positif**.

Dans ce cas, une annotation Java `@SuppressWarnings` standard spécifiant l’ID de règle comme attribut d’annotation peut être inscrite dans le code source. Par exemple, un faux positif courant est que la règle SonarQube permettant de détecter les mots de passe codés en dur peut être agressive sur la manière dont un mot de passe codé en dur est identifié.

Le code suivant est assez courant dans un projet AEM, qui comporte du code pour se connecter à un service externe.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube génère alors une vulnérabilité de bloqueur. Mais après avoir examiné le code, vous reconnaissez qu’il ne s’agit pas d’une vulnérabilité et vous pouvez annoter le code avec l’ID de règle approprié.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Cependant, si le code était en fait le suivant :

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

La bonne solution consiste alors à supprimer le mot de passe codé en dur.

>[!NOTE]
>
>Bien qu’il soit préférable de rendre l’annotation `@SuppressWarnings` aussi précise que possible, c’est-à-dire de n’annoter que l’énoncé ou le bloc qui cause le problème, il est tout de même possible de le faire à un niveau qui se rapporte à la classe.

## Test de sécurité {#security-testing}

[!UICONTROL Cloud Manager] exécute le **AEM contrôles de l’intégrité de la sécurité** sur l’environnement d’évaluation suivant le déploiement et indique l’état via l’interface utilisateur. Les résultats sont agrégés à partir de toutes les instances AEM de l’environnement.

Ces mêmes contrôles de l’intégrité peuvent être exécutés à tout moment via la console web ou le tableau de bord des opérations.

Si l’une des instances signale un échec pour un contrôle d’intégrité donné, l’environnement entier ne réussit pas ce contrôle. Comme pour les tests de qualité et de performance du code, ces contrôles de l’intégrité sont organisés en catégories et signalés à l’aide du système de point de contrôle à trois niveaux. La seule différence réside dans le fait qu’il n’existe aucun seuil dans le cas des tests de sécurité. Tous les contrôles d’intégrité sont réussis ou échouent.

Le tableau suivant répertorie les contrôles de l’intégrité.

| Nom | Implémentation de la vérification de l’intégrité | Catégorie |
|---|---|---|
| La préparation de l’API d’ajout de pare-feu de désérialisation est dans un état acceptable. | [Disponibilité de l’API d’ajout de pare-feu de désérialisation](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | Critique |
| Le pare-feu de désérialisation est fonctionnel.. | [Pare-feu de désérialisation fonctionnel](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | Critique |
| Le pare-feu de désérialisation est chargé.. | [Pare-feu de désérialisation chargé](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | Critique |
| `AuthorizableNodeName` La mise en oeuvre n’expose pas l’ID autorisable dans le nom/chemin du noeud. | [Génération de nom de nœud autorisé](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | Critique |
| Les mots de passe par défaut ont été modifiés.. | [Comptes de connexion par défaut](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html#users-and-groups-in-aem) | Critique |
| Le servlet GET par défaut Sling est protégé contre les attaques par DOS. | Servlet Sling Get | Critique |
| Le gestionnaire de script Java Sling est correctement configuré. | Gestionnaire de script Java Sling | Critique |
| Le gestionnaire de script JSP Sling est correctement configuré. | Gestionnaire de script JSP Sling | Critique |
| SSL est correctement configuré.. | Configuration SSL | Critique |
| Aucune stratégie de profil utilisateur évidemment non sécurisée n’est trouvée. | Accès par défaut au profil utilisateur | Critique |
| Le filtre Référent Sling est configuré pour empêcher les attaques CSRF. | [Filtre référent Sling](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | Important |
| Le Gestionnaire de bibliothèques de HTMLS Adobe Granite est correctement configuré. | Configuration de gestionnaire de bibliothèque HTML CQ | Important |
| Le lot Prise en charge CRXDE est désactivé.. | Prise en charge de CRXDE | Important |
| Le lot DavEx Sling et le servlet sont désactivés.. | Contrôle d’intégrité DavEx | Important |
| L’exemple de contenu n’est pas installé.. | Packages d’exemple de contenu | Important |
| Le filtre de requête WCM et le filtre de débogage WCM sont désactivés.. | [Configuration des filtres WCM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html#configuring) | Important |
| Le lot WebDAV Sling et le servlet sont correctement configurés.. | Contrôle d’intégrité WebDAV | Important |
| Le serveur web est configuré pour empêcher les clics publicitaires.. | Configuration du serveur web | Important |
| La réplication n’utilise pas le `admin` utilisateur. | Utilisateurs de réplication et de transport | Infos |

## Test de performance {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager exécute des tests de performances pour les programmes AEM Sites. Le test de performance est exécuté pendant environ 30 minutes en faisant tourner des utilisateurs virtuels (conteneurs) qui simulent les utilisateurs réels pour accéder aux pages dans les environnements d’évaluation afin de simuler le trafic. Vous pouvez trouver ces pages à l’aide d’un crawler.

#### Utilisateurs virtuels {#virtual-users}

Le nombre d’utilisateurs ou de conteneurs virtuels qui sont générés par Cloud Manager est déterminé par les indicateurs de performance clés (temps de réponse et pages vues/min) définis par l’utilisateur avec la variable **Propriétaire de l’entreprise** role while [création ou modification du programme.](setting-up-program.md) En fonction des indicateurs de performance clés définis, jusqu’à 10 conteneurs qui simulent les utilisateurs réels seront démarrés. Les pages sélectionnées pour le test sont fractionnées et affectées à chaque utilisateur virtuel.

#### Crawler {#crawler}

Avant le début de la période de test de 30 minutes, Cloud Manager explore l’environnement d’évaluation à l’aide d’un ensemble d’une ou de plusieurs URL sources configurées par l’ingénieur du service client. À partir de ces URL, le code HTML de chaque page est examiné et les liens sont parcourus en largeur d’abord. Ce processus d’exploration est limité à un maximum de 5 000 pages. Les requêtes du robot d’exploration ont un délai d’expiration fixe de 10 secondes.

#### Ensembles de pages à tester {#page-sets}

Les pages sont sélectionnées dans trois ensembles de pages. Cloud Manager utilise les journaux d’accès des instances AEM dans les environnements de production et d’évaluation pour déterminer les compartiments suivants.

* **Pages actives populaires** - Cette option est sélectionnée pour vous assurer que les pages les plus populaires consultées par les clients en direct sont testées. Cloud Manager lit le journal d’accès et détermine les 25 pages les plus consultées en direct par les clients afin de générer la liste des premières `Popular Live Pages`. L’intersection de ceux-ci, également présents dans l’environnement d’évaluation, est ensuite analysée dans l’environnement d’évaluation.

* **Autres pages actives** - Cette option est sélectionnée pour s’assurer que les pages qui se situent en dehors des 25 premières pages actives populaires qui peuvent ne pas être populaires, mais importantes à tester sont testées. Comme les pages actives populaires, elles sont extraites du journal d’accès et doivent également être présentes dans l’environnement d’évaluation.

* **Nouvelles pages** - Cette option est sélectionnée pour tester les nouvelles pages qui peuvent avoir été déployées uniquement vers l’évaluation et qui ne sont pas encore en production, mais qui doivent être testées.

##### Répartition du trafic entre les jeux de pages sélectionnés {#distribution-of-traffic}

Vous pouvez choisir entre un et les trois jeux sur le **Tests** de votre [configuration du pipeline.](configuring-production-pipelines.md) La répartition du trafic est basée sur le nombre d’ensembles sélectionnés. En d’autres termes, si les trois éléments sont sélectionnés, 33 % du total des pages vues sont placées dans chaque jeu. Si deux sont sélectionnés, 50 % est affecté à chaque jeu. Si l’une d’elles est sélectionnée, 100 % du trafic est affecté à cet ensemble.

Examinons cet exemple.

* Il existe une répartition 50/50 entre les pages actives populaires et les nouveaux ensembles de pages.
* Les autres pages actives ne sont pas utilisées.
* Le nouveau jeu de pages contient 3 000 pages.
* L’indicateur de performance clé des pages vues par minute est défini sur 200.

Pendant la période test de 30 minutes :

* Chacune des 25 pages du jeu de pages actives le plus populaire sera ouverte 120 fois : `((200 * 0.5) / 25) * 30 = 120`
* Chacune des 3 000 pages du nouvel ensemble de pages sera ouverte une fois : `((200 * 0.5) / 3000) * 30 = 1`

#### Tests et reporting {#testing-reporting}

Cloud Manager exécute des tests de performance pour les programmes AEM Sites en demandant des pages en tant qu’utilisateur non authentifié par défaut sur le serveur de publication intermédiaire pendant une période de test de 30 minutes. Il mesure les mesures virtuelles générées par l’utilisateur (temps de réponse, taux d’erreur, vues par minute, etc.) pour chaque page, ainsi que pour différentes mesures au niveau du système (UCT, mémoire, données réseau) pour toutes les instances.

Le tableau suivant résume la matrice des tests de performance à l’aide du système de point de contrôle à trois niveaux.

| Mesure | Catégorie | Seuil d’échec |
|---|---|---|
| Taux d’erreur de demande de page | Critique | >= 2 % |
| Taux d’utilisation de l’UC | Critique | >= 80 % |
| Délai d’attente d’E/S de disque | Critique | >= 50 % |
| Délai de réponse du 95e percentile | Important | >= ICP de niveau programme |
| Délai de réponse max. | Important | >= 18 secondes |
| Nombre de pages vues par minute | Important | &lt; ICP de niveau programme |
| Utilisation de la bande passante de disque | Important | >= 90 % |
| Utilisation de la bande passante réseau | Important | >= 90 % |
| Demandes par minute | Infos | >= 6 000 |

Consultez la section [Test de performance authentifiée](#authenticated-performance-testing) pour plus d’informations sur l’utilisation de l’authentification de base pour les tests de performances de Sites et Assets.

>[!NOTE]
>
>Les instances de création et de publication sont surveillées pendant la période du test. Si aucune mesure pour une instance n’est obtenue, cette mesure est signalée comme inconnue et l’étape correspondante échoue.

#### Facultatif - Test de performance authentifiée {#authenticated-performance-testing}

Si nécessaire, les clients AMS disposant de sites authentifiés peuvent spécifier un nom d’utilisateur et un mot de passe que Cloud Manager utilisera pour accéder au site web lors des tests de performances des sites.

Le nom d’utilisateur et le mot de passe sont spécifiés sous la forme de variables de pipeline avec les noms . `CM_PERF_TEST_BASIC_USERNAME` et `CM_PERF_TEST_BASIC_PASSWORD`.

Le nom d’utilisateur doit être stocké dans une `string` et le mot de passe doit être stocké dans une variable `secretString` . Si ces deux éléments sont spécifiés, chaque requête du robot de tests de performances et des utilisateurs virtuels de test contiendra ces informations d’identification sous forme d’authentification HTTP basique.

Pour définir ces variables à l’aide de l’interface de ligne de commande de Cloud Manager, exécutez :

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Reportez-vous au document [Correction des variables de pipeline de l’utilisateur](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Variables/patchPipelineVariables) pour savoir comment utiliser l’API.

### AEM Assets {#aem-assets}

Cloud Manager exécute des tests de performances pour les programmes AEM Assets en chargeant régulièrement des ressources pendant une période de test de 30 minutes.

#### Configuration requise pour l’intégration {#onboarding-requirement}

Pour les tests de performances d’Assets, votre ingénieur du service client va créer un `cloudmanager` utilisateur et mot de passe lors de l’intégration de l’auteur à l’environnement d’évaluation. Les étapes de test de performance nécessitent un utilisateur appelé `cloudmanager` et le mot de passe associé configuré par votre ingénieur du service client. Cela ne doit pas être supprimé de l’instance d’auteur ni ses autorisations modifiées. Toute modification entraînera probablement l’échec des tests de performances Assets.

#### Images et ressources à tester {#assets-for-testing}

Les clients peuvent charger leurs propres ressources pour les tester. Vous pouvez le faire à partir de la fonction **Configuration du pipeline** ou **Modifier** écran. Les formats d’image courants tels que JPEG, PNG, GIF et BMP sont pris en charge, ainsi que les fichiers Photoshop, Illustrator et Postscript.

Si aucune image n’est téléchargée, Cloud Manager utilise une image par défaut et des documents de PDF à des fins de test.

#### Répartition des ressources pour les tests {#distribution-of-assets}

La répartition du nombre de ressources de chaque type chargées par minute est définie dans la variable **Configuration du pipeline** ou **Modifier** écran.

Par exemple, si une répartition 70/30 est utilisée et que 10 ressources sont téléchargées par minute, 7 images et 3 documents seront téléchargés par minute.

#### Tests et reporting {#testing-and-reporting}

Cloud Manager crée un dossier sur l’instance d’auteur à l’aide du nom d’utilisateur et du mot de passe configurés par l’ingénieur du service client dans la variable [Conditions requises pour l’intégration](#onboaring-requirements) . Les ressources sont ensuite chargées dans le dossier à l’aide d’une bibliothèque open source. Les tests exécutés par l’étape de test des ressources sont écrits à l’aide d’une [bibliothèque open source.](https://github.com/adobe/toughday2) Le temps de traitement de chaque ressource et diverses mesures au niveau du système sont mesurés pendant le test d’une durée de 30 minutes. Cette fonctionnalité peut télécharger des images et des documents de PDF.

>[!TIP]
>
>Reportez-vous au document [Configuration des pipelines de production](configuring-production-pipelines.md) pour en savoir plus. Reportez-vous au document [Configuration de votre programme](setting-up-program.md) pour savoir comment configurer votre programme et définir vos indicateurs de performance clés.

### Graphiques des résultats de tests de performance {#performance-testing-results-graphs}

Un certain nombre de mesures sont disponibles dans la variable **Boîte de dialogue Test de performance**

![Liste des mesures](assets/understand_test-results-screen1.png)

Les panneaux de mesures peuvent être développés pour afficher un graphique, fournir un lien de téléchargement ou les deux.

![Mesures développées sous forme de graphique](assets/screen_shot_2018-09-05at83933pm.png)

Cette fonctionnalité est disponible pour les mesures suivantes.

* **Utilisation de l’UC**
   * Graphique montrant l’utilisation du processeur pendant la période de test

* **Délai d’attente d’E/S de disque**
   * Graphique montrant le temps d’attente d’E/S du disque pendant la période de test

* **Taux d’erreur de page**
   * Graphique montrant les erreurs de page par minute pendant la période de test
   * Fichier CSV répertoriant les pages qui ont généré une erreur pendant le test

* **Utilisation de la bande passante de disque**
   * Graphique de l’utilisation de la bande passante du disque pendant la période de test

* **Utilisation de la bande passante réseau**
   * Graphique de l’utilisation de la bande passante du réseau pendant la période de test

* **Délai de réponse max.**
   * Graphique montrant le délai de réponse maximal par minute pendant la période de test

* **Délai de réponse du 95e percentile**
   * Graphique montrant le délai de réponse du 95e percentile par minute pendant la période de test
   * Fichier CSV répertoriant les pages dont le délai de réponse du 95ème centile a dépassé les ICP définis

## Optimisation de l’analyse des modules de contenu {#content-package-scanning-optimization}

Dans le cadre du processus d’analyse de la qualité, Cloud Manager analyse les packages de contenu générés par la version Maven. Cloud Manager offre des optimisations pour accélérer ce processus, qui sont efficaces lorsque certaines contraintes de conditionnement sont observées. Le plus significatif est l’optimisation effectuée pour les projets qui génèrent un module de contenu unique, généralement appelé &quot;tout&quot;, qui contient un certain nombre d’autres modules de contenu générés, qui sont marqués comme ignorés. Lorsque Cloud Manager détecte ce scénario, plutôt que de décompresser le module &quot;all&quot;, les modules de contenu individuels sont analysés directement et triés en fonction des dépendances. Prenons l’exemple de la sortie de génération suivante.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (skipped-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (skipped-content-package)

Si les seuls éléments à l’intérieur `myco-all-1.0.0-SNAPSHOT.zip` sont les deux packages de contenu ignorés, puis les deux packages incorporés seront analysés au lieu du package de contenu &quot;all&quot;.

Pour les projets qui produisent des dizaines de packages incorporés, cette optimisation a été affichée pour économiser jusqu’à 10 minutes par exécution de pipeline.

Un cas particulier peut se produire lorsque le module de contenu &quot;all&quot; contient une combinaison de modules de contenu ignorés et de lots OSGi. Par exemple, si `myco-all-1.0.0-SNAPSHOT.zip` contenait les deux packages incorporés mentionnés précédemment ainsi qu’un ou plusieurs lots OSGi, puis un nouveau package de contenu minimal est créé avec uniquement les lots OSGi. Ce module est toujours nommé `cloudmanager-synthetic-jar-package` et les lots contenus sont placés dans `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
>
>* Cette optimisation n’a aucune incidence sur les modules déployés sur AEM.
>* La correspondance entre les modules de contenu incorporés et les modules de contenu ignorés étant basée sur les noms de fichier, cette optimisation ne peut pas être effectuée si plusieurs modules de contenu ignorés portent exactement le même nom de fichier ou si le nom de fichier est modifié lors de l’incorporation.