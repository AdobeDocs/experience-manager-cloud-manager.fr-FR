---
title: Test de qualité du code
description: Découvrez comment fonctionne le test de qualité du code des pipelines et comment il peut améliorer la qualité de vos déploiements.
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: fadcf560f08bf16d0d18172c620a450d0cb06225
workflow-type: tm+mt
source-wordcount: '2778'
ht-degree: 57%

---


# Test de qualité du code {#code-quality-testing}

Découvrez comment fonctionne le test de qualité du code des pipelines et comment il peut améliorer la qualité de vos déploiements.

## Présentation {#introduction}

Lors de l’exécution du pipeline, le logiciel capture plusieurs mesures. Ces mesures sont ensuite comparées aux indicateurs de performance clés (IPC) définis par le propriétaire de l’entreprise. Ou bien, elles sont comparées aux normes définies par Adobe Managed Services.

Ces résultats sont signalés à l’aide d’un système d’évaluation à trois niveaux.

## Évaluation à trois niveaux {#three-tiered-ratings}

Le pipeline comprend trois points de contrôle :

* Qualité du code
* Test de performance
* Test de sécurité

Pour chaque point de contrôle, il existe une structure à trois niveaux pour les problèmes identifiés par le point de contrôle.

* **Critique** - Problèmes entraînant un échec immédiat du pipeline.
* **Important** : problèmes qui entraînent la suspension du pipeline. Un responsable de déploiement, un chef de projet ou un propriétaire d’entreprise peuvent remplacer les problèmes. Si tel est le cas, le pipeline se poursuit comme prévu. Ils peuvent également accepter les problèmes, ce qui entraîne l’arrêt du pipeline avec un échec. Le remplacement des échecs importants est soumis à un [timeout](/help/using/code-deployment.md#timeouts).
* **Info** - Problèmes fournis uniquement à titre d’information et sans impact sur l’exécution du pipeline.

>[!NOTE]
>
>Dans un pipeline uniquement axé sur la qualité du code, les échecs importants du point de contrôle Qualité du code ne peuvent pas être remplacés car l’étape de test de qualité du code est la dernière étape du pipeline.

## Test de qualité du code {#code-quality-testing-step}

Cette étape de test évalue la qualité du code de votre application, qui est l’objectif principal d’un pipeline portant uniquement sur la qualité du code. Il est exécuté immédiatement après l’étape de création dans tous les pipelines de production et hors production. Pour en savoir plus, voir [Configuration des pipelines hors production](/help/using/non-production-pipelines.md).

Le test de qualité du code analyse le code source pour s’assurer qu’il répond à certains critères de qualité.

Le logiciel le met en oeuvre à l’aide d’une combinaison d’analyse SonarQube, d’examen au niveau du module de contenu avec OakPAL et de validation Dispatcher avec l’outil d’optimisation de Dispatcher.

Il existe plus de 100 règles combinant des règles Java génériques et des règles spécifiques à AEM. Certaines des règles spécifiques à AEM sont créées en fonction des bonnes pratiques de l’équipe d’ingénierie AEM et sont appelées [Règles de qualité du code personnalisé.](/help/using/custom-code-quality-rules.md)

>[!TIP]
>
>Vous pouvez télécharger la liste complète des règles [via ce lien.](/help/assets/CodeQuality-rules-latest-AMS.xlsx)

Les résultats des tests de qualité du code sont fournis sous forme d’évaluation, comme résumé dans ce tableau.

| Nom | Définition | Catégorie | Seuil d’échec |
|--- |--- |--- |--- |
| Note de sécurité | A = Aucune vulnérabilité<br/>B = au moins 1 vulnérabilité mineure<br/>C = au moins 1 vulnérabilité majeure<br/>D = au moins 1 vulnérabilité critique<br/>E = au moins 1 vulnérabilité bloquante | Critique | &lt; B |
| Note de fiabilité | A = Aucun bug<br/>B = au moins 1 bug mineur <br/>C = au moins 1 bug majeur<br/>D = au moins 1 bug critique<br/>E = au moins 1 bug bloquant | Important | &lt; C |
| Note de maintenabilité | Défini par le coût de remédiation en suspens pour les code smells, comme un pourcentage du temps qui a déjà été consacré à l’application.<br/><ul><li>A = &lt;= 5 %</li><li>B = 6-10 %</li><li>C = 11-20 %</li><li>D = 21-50 %</li><li>E = > 50 %</li></ul> | Important | &lt; A |
| Couverture | Défini par un mélange de couverture de ligne de test unitaire et de couverture de condition à l’aide de la formule : <br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = Conditions qui ont été évaluées comme `true` au moins une fois lors de l’exécution de tests unitaires</li><li>`CF` = Conditions qui ont été évaluées comme `false` au moins une fois lors de l’exécution de tests unitaires</li><li>`LC` = Lignes couvertes = lines_to_cover - uncover_lines</li><li>`B` = nombre total de conditions</li><li>`EL` = nombre total de lignes exécutables (lines_to_cover)</li></ul> | Important | &lt; 50 % |
| Tests unitaires ignorés | Nombre de tests unitaires ignorés | Infos | > 1 |
| Problèmes en cours | Types de problèmes généraux – Vulnérabilités, bogues et smells de code | Infos | > 0 |
| Lignes dupliquées | Défini comme le nombre de lignes impliquées dans les blocs dupliqués. Un bloc de code est considéré comme dupliqué dans les conditions suivantes.<br>Projets non Java :<ul><li>Il doit y avoir au moins 100 jetons successifs et dupliqués.</li><li>Ces jetons doivent être répartis au moins sur : </li><li>30 lignes de code pour COBOL </li><li>20 lignes de code pour ABAP </li><li>10 lignes de code pour d’autres langages</li></ul>Projets Java :<ul></li><li> Il devrait y avoir au moins 10 déclarations successives et dupliquées, quel que soit le nombre de jetons et de lignes.</li></ul>Les différences dans la mise en retrait ainsi que dans les littéraux de chaîne sont ignorées lors de la détection des doublons. | Infos | > 1 % |
| Compatibilité Cloud Service | Nombre de problèmes de compatibilité Cloud Service identifiés | Infos | > 0 |

>[!NOTE]
>
>Pour plus d’informations, voir [Définitions des mesures de SonarQube](https://docs.sonarsource.com/sonarqube/latest/user-guide/code-metrics/metrics-definition/).

>[!NOTE]
>
>Pour en savoir plus sur les règles de qualité du code personnalisé exécutées par [!UICONTROL Cloud Manager], reportez-vous au document [Règles de qualité du code personnalisé.](custom-code-quality-rules.md)

### Traitement des faux positifs {#dealing-with-false-positives}

Le processus d’analyse de la qualité n’est pas parfait et identifie parfois incorrectement les problèmes qui ne sont pas réellement problématiques. Ce scénario est connu sous le nom de faux positif.

Dans ces cas, le code source peut être annoté avec l’annotation standard Java `@SuppressWarnings` en spécifiant l’ID de la règle comme attribut d’annotation. Par exemple, un faux positif courant est que la règle de SonarQube permettant de détecter les mots de passe codés en dur peut être agressive sur la façon dont un mot de passe codé en dur est identifié.

Le code suivant est assez courant dans un projet AEM, qui comporte du code pour se connecter à un service externe.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube génère alors une vulnérabilité de bloqueur. Mais après avoir examiné le code, vous reconnaissez que ce problème n’est pas une vulnérabilité et vous pouvez annoter le code avec l’ID de règle approprié.

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
>Il est recommandé de rendre l’annotation `@SuppressWarnings` aussi spécifique que possible. En d’autres termes, annotez uniquement l’instruction ou le bloc spécifique qui cause le problème. Cependant, il est possible d’annoter au niveau de la classe. Cela permet de supprimer plus largement les avertissements.

## Test de sécurité {#security-testing}

[!UICONTROL Cloud Manager] exécute les contrôles d’intégrité de sécurité AEM existants sur l’environnement d’évaluation suite au déploiement et indique leur statut via l’interface utilisateur. Les résultats sont agrégés à partir de toutes les instances AEM de l’environnement.

Ces mêmes contrôles d’intégrité peuvent être exécutés à tout moment par l’intermédiaire de la console Web ou du tableau de bord d’opérations.

Si l’une des instances signale un échec pour un contrôle d’intégrité donné, l’ensemble de l’environnement ne réussit pas ce contrôle d’intégrité. Comme pour les tests de qualité du code et de performance, ces contrôles d’intégrité sont classés en catégories et signalés à l’aide du système de point de contrôle à trois niveaux. La seule différence est qu’il n’existe aucun seuil en cas de test de sécurité. Tous les contrôles d’intégrité réussissent ou non.

Le tableau suivant répertorie les contrôles d’intégrité :

| Nom | Implémentation du contrôle d’intégrité | Catégorie |
|---|---|---|
| La disponibilité de l’API d’ajout de pare-feu de désérialisation est dans un état acceptable. | [Disponibilité de l’API d’ajout de pare-feu de désérialisation](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | Critique |
| Le pare-feu de désérialisation est fonctionnel. | [Pare-feu de désérialisation fonctionnel](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | Critique |
| Le pare-feu de désérialisation est chargé. | [Pare-feu de désérialisation chargé](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | Critique |
| L’implémentation `AuthorizableNodeName` n’expose pas d’ID autorisable dans le nom/chemin du nœud. | [Génération de nom de nœud autorisé](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/security/security-checklist#security) | Critique |
| Les mots de passe par défaut ont été modifiés. | [Comptes de connexion par défaut](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/security#users-and-groups-in-aem) | Critique |
| Le servlet GET par défaut Sling est protégé contre les attaques par DOS. | Servlet Sling Get | Critique |
| Le gestionnaire Sling JavaScript est configuré correctement. | Gestionnaire JavaScript Sling | Critique |
| Le gestionnaire de script JSP Sling est correctement configuré. | Gestionnaire de script JSP Sling | Critique |
| SSL est configuré correctement. | Configuration SSL | Critique |
| Aucune politique de profil utilisateur évidemment risquée n’a été trouvée. | Accès par défaut au profil utilisateur | Critique |
| Le filtre Référent Sling est configuré pour empêcher les attaques CSRF. | [Filtre référent Sling](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/security/security-checklist#security) | Important |
| Le gestionnaire de bibliothèques HTML Adobe Granite est configuré correctement. | Configuration de gestionnaire de bibliothèque HTML CQ | Important |
| Le lot de prise en charge CRXDE est désactivé. | Prise en charge de CRXDE | Important |
| Le lot et le servlet Sling DavEx sont désactivés. | Contrôle d’intégrité DavEx | Important |
| L’exemple de contenu n’est pas installé. | Packages d’exemple de contenu | Important |
| Le filtre de requêtes WCM et le filtre de débogage WCM sont désactivés. | [Configuration des filtres WCM](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/configuring/osgi-configuration-settings#configuring) | Important |
| Le lot WebDAV Sling et le servlet sont correctement configurés. | Contrôle d’intégrité WebDAV | Important |
| Le serveur web est configuré pour empêcher le détournement de clics. | Configuration du serveur web | Important |
| La réplication n’utilise pas l’utilisateur `admin`. | Utilisateurs de réplication et de transport | Infos |

## Test de performance {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager exécute des tests de performances pour les programmes AEM Sites. Le test de performance est exécuté pendant environ 30 minutes en émulant des utilisateurs virtuels (conteneurs) qui simulent des utilisateurs réels pour accéder aux pages sur l’environnement d’évaluation, et par là le trafic qu’ils généreraient. Vous pouvez trouver ces pages à l’aide d’un robot d’exploration.

#### Utilisateurs virtuels {#virtual-users}

Cloud Manager crée une rotation des utilisateurs virtuels ou des conteneurs en fonction des IPC (temps de réponse et pages vues/min) définis par le rôle **Propriétaire de l’entreprise**. Ces KPI sont définis lors de la [création ou modification du programme](/help/getting-started/program-setup.md).

En fonction des indicateurs de performance clés définis, jusqu’à dix conteneurs simulant les utilisateurs réels sont démarrés. Les pages sélectionnées pour les tests sont divisées et attribuées à chaque utilisateur virtuel.

#### Robot d’exploration {#crawler}

Avant le début de la période de test de 30 minutes, Cloud Manager analyse l’environnement d’évaluation à l’aide d’un ensemble d’une ou de plusieurs URL sources configurées par l’ingénieur du service client. À partir de ces URL, le code HTML de chaque page est examiné et les liens sont parcourus en largeur d’abord.

* Ce processus d’exploration est limité par défaut à un maximum de 5 000 pages.
* Le nombre maximal de pages à tester peut être remplacé en définissant la [variable de pipeline](/help/getting-started/build-environment.md#pipeline-variables) `CM_PERF_TEST_CRAWLER_MAX_PAGES`.
   * Les valeurs autorisées sont `2000` - `7000`.
* Les requêtes du robot d’exploration ont un délai d’expiration fixe de 10 secondes.

#### Ensembles de pages pour les tests {#page-sets}

Trois jeux de pages sélectionnent les pages. Cloud Manager utilise les journaux d’accès des instances AEM à travers les environnements de production et d’évaluation pour déterminer les ensembles suivants :

* **Pages actives populaires** - Vérifie que les pages les plus populaires consultées par les clients en direct sont testées. Cloud Manager lit le journal des accès et détermine les 25 pages les plus consultées par les clients en direct pour générer une liste des `Popular Live Pages` principales. L’intersection de ces pages qui sont également présentes dans l’environnement d’évaluation est ensuite analysée dans l’environnement d’évaluation.

* **Autres pages actives** - Vérifie que les pages qui se situent en dehors des 25 premières pages actives populaires qui peuvent ne pas être populaires, mais qui sont importantes à tester, sont testées. Comme les pages actives populaires, elles sont extraites du journal d’accès et doivent également être présentes dans l’environnement d’évaluation.

* **Nouvelles pages** : teste les nouvelles pages qui ont peut-être été déployées uniquement vers l’évaluation et qui ne sont pas encore en production, mais qui doivent être testées.

##### Répartition du trafic entre les ensembles de pages sélectionnés {#distribution-of-traffic}

Vous pouvez choisir entre un et trois ensembles de pages dans l’onglet **Tests** de votre [configuration de pipeline.](/help/using/production-pipelines.md) La distribution du trafic est basée sur le nombre d’ensembles sélectionnés. En d’autres termes, si les trois éléments sont sélectionnés, 33 % du total des pages vues sont placées dans chaque jeu. Si deux sont sélectionnés, 50 % est affecté à chaque jeu. Si l’une d’elles est sélectionnée, 100 % du trafic est affecté à cet ensemble.

Prenons cet exemple.

* Il y a une répartition 50/50 entre les ensembles de pages en direct populaires et de nouvelles pages.
* Les autres pages en direct ne sont pas utilisées.
* L’ensemble des nouvelles pages contient 3 000 pages.
* L’indicateur de performance clé *pages vues par minute* est défini sur 200.

Pendant la période de test de 30 minutes :

* Chacune des 25 pages du jeu de pages actives le plus populaire est ouverte 120 fois : `((200 * 0.5) / 25) * 30 = 120`
* Chacune des 3 000 pages du nouvel ensemble de pages est ouverte une fois : `((200 * 0.5) / 3000) * 30 = 1`

#### Tests et compte rendu des performances {#testing-reporting}

Cloud Manager exécute des tests de performance pour les programmes AEM Sites en demandant des pages en tant qu’utilisateur non authentifié par défaut sur le serveur de publication d’évaluation pendant une période de test de 30 minutes. Il mesure les mesures virtuelles générées par l’utilisateur (temps de réponse, taux d’erreur, vues par minute, etc.) pour chaque page, ainsi que diverses mesures au niveau du système (unité centrale, mémoire, données réseau) pour toutes les instances.

Le tableau suivant résume la matrice de test de performance à l’aide du système de point de contrôle à trois niveaux :

| Mesure | Catégorie | Seuil d’échec |
|---|---|---|
| Taux d’erreur des demandes de pages | Critique | >= 2 % |
| Taux d’utilisation de l’UC | Critique | >= 80 % |
| Délai d’attente d’E/S de disque | Critique | >= 50 % |
| 95e centile du temps de réponse | Important | >= ICP de niveau programme |
| Délai de réponse max. | Important | >= 18 secondes |
| Nombre de pages vues par minute | Important | &lt; ICP de niveau programme |
| Utilisation de la bande passante de disque | Important | >= 90 % |
| Utilisation de la bande passante réseau | Important | >= 90 % |
| Demandes par minute | Infos | >= 6 000 |

Pour plus d’informations sur l’utilisation de l’authentification de base pour les tests de performance de Sites et Assets, consultez la section [Tests de performances authentifiés](#authenticated-performance-testing).

>[!NOTE]
>
>Les instances de création et de publication sont surveillées pendant le test. Si aucune mesure pour une instance n’est obtenue, cette mesure est signalée comme inconnue et l’étape correspondante échoue.

#### Test de performances avec authentification {#authenticated-performance-testing}

Si nécessaire, les clients AMS disposant de sites authentifiés peuvent spécifier un nom d’utilisateur et un mot de passe que Cloud Manager utilise pour accéder au site web lors des tests de performances des sites.

Le nom d’utilisateur et le mot de passe sont spécifiés sous la forme de variables de pipeline avec les noms `CM_PERF_TEST_BASIC_USERNAME` et `CM_PERF_TEST_BASIC_PASSWORD`.

Le nom d’utilisateur est stocké dans une variable `string` et le mot de passe dans une variable `secretString`. Si ces deux variables sont spécifiées, chaque requête du moteur de recherche du test de performance et des utilisateurs virtuels de test contient ces informations d’identification en tant qu’authentification HTTP de base.

Pour définir ces variables à l’aide de l’interface de ligne de commande de Cloud Manager, exécutez :

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Pour savoir comment utiliser l’API, consultez la documentation de l’API [Variables de pipeline de correctif](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchPipelineVariables) .

### AEM Assets {#aem-assets}

Cloud Manager effectue des tests de performance pour les programmes AEM Assets en chargeant de manière répétée des ressources pendant 30 minutes.

#### Exigences de l’intégration {#onboarding-requirement}

Pour les tests de performances Assets, votre ingénieur du service client crée un utilisateur et un mot de passe `cloudmanager` lors de l’intégration de l’auteur à l’environnement d’évaluation. Les étapes de test de performance nécessitent un utilisateur appelé `cloudmanager` et le mot de passe associé configuré par votre ingénieur du service client.

Cette méthode doit rester dans l’instance d’auteur avec ses autorisations inchangées. Sa modification ou sa suppression peut entraîner l’échec des tests de performances d’Assets.

#### Images et ressources pour les tests {#assets-for-testing}

Les clients peuvent charger leurs propres ressources pour les tester. Ce processus peut être effectué à partir de l’écran **Configuration du pipeline** ou **Modifier** . Les formats d’image courants tels que JPEG, PNG, GIF et BMP sont pris en charge, ainsi que les fichiers Photoshop, Illustrator et PostScript.

Si aucune image n’est téléchargée, Cloud Manager utilise une image par défaut et des documents de PDF à des fins de test.

#### Répartition des ressources pour les tests {#distribution-of-assets}

La répartition du nombre de ressources de chaque type qui sont chargées par minute est définie dans l’écran **Configuration du pipeline** ou **Modifier**.

Par exemple, si une répartition 70/30 est utilisée et que 10 ressources sont téléchargées par minute, 7 images et 3 documents sont téléchargés par minute.

#### Tests et compte rendu des performances {#testing-and-reporting}

Cloud Manager crée un dossier sur l’instance d’auteur à l’aide du nom d’utilisateur et du mot de passe configurés par l’ingénieur du service client. Les ressources sont ensuite chargées dans le dossier à l’aide d’une bibliothèque open source. Les tests exécutés par l’étape de test des ressources sont écrits à l’aide de cette [bibliothèque open source.](https://github.com/adobe/toughday2) Le temps de traitement de chaque ressource et diverses mesures au niveau du système sont mesurés pendant les 30 minutes que dure le test. Cette fonctionnalité permet de charger des images et des documents PDF.

>[!TIP]
>
>Pour en savoir plus, voir [Configuration de pipelines de production](/help/using/production-pipelines.md) . Voir [Configuration du programme](/help/getting-started/program-setup.md) pour savoir comment configurer votre programme et définir vos indicateurs clés de performance.

### Graphiques des résultats des tests de performance {#performance-testing-results-graphs}

Un certain nombre de mesures sont disponibles dans la **Boîte de dialogue des tests de performance**.

![Liste des mesures](/help/assets/understand_test-results-screen1.png)

Les panneaux de mesures peuvent être développés pour afficher un graphique, fournir un lien vers un téléchargement ou les deux.

![Mesures développées sous forme de graphique](/help/assets/screen_shot_2018-09-05at83933pm.png)

Cette fonctionnalité est disponible pour les mesures suivantes.

* **Utilisation de l’UC** - Graphique de l’utilisation de l’UC pendant la période de test

* **Durée d’attente d’E/S du disque** : graphique du temps d’attente d’E/S du disque pendant la période de test.

* **Taux d’erreur de page** : graphique des erreurs de page par minute pendant la période de test.
   * Fichier CSV répertoriant les pages qui ont généré une erreur lors du test

* **Utilisation de la bande passante de disque** - Graphique de l’utilisation de la bande passante du disque pendant la période de test

* **Utilisation de la bande passante du réseau** : graphique de l’utilisation de la bande passante du réseau pendant la période de test.

* **Temps de réponse maximal** : graphique du temps de réponse maximal par minute pendant la période de test.

* **Temps de réponse du 95e centile** : graphique montrant le temps de réponse du 95e centile par minute pendant la période de test.
   * Fichier CSV répertoriant les pages dont le 95e centile du temps de réponse a dépassé les ICP définis.

## Optimisation de l’analyse des packages de contenu {#content-package-scanning-optimization}

Dans le cadre du processus d’analyse de la qualité, Cloud Manager effectue une analyse des packages de contenu générés par la version Maven. Cloud Manager offre des optimisations pour accélérer ce processus, qui est efficace lorsque certaines contraintes de conditionnement sont observées.

L’optimisation clé est destinée aux projets qui génèrent un package &quot;all&quot; unique, contenant d’autres packages de contenu générés par la version, qui sont marqués comme ignorés. Lorsque Cloud Manager détecte ce scénario, plutôt que de décompresser le package « all », les packages de contenu individuels sont analysés directement et triés en fonction des dépendances. Par exemple, considérez la sortie de génération suivante.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (package de contenu)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (package de contenu ignoré)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (package de contenu ignoré)

Si les seuls éléments contenus dans `myco-all-1.0.0-SNAPSHOT.zip` sont les deux packages de contenu ignorés, les deux packages incorporés sont analysés au lieu du package de contenu « all ».

Pour les projets qui produisent des dizaines de packages incorporés, il a été démontré que cette optimisation permet de gagner jusqu’à 10 minutes par exécution de pipeline.

Un cas particulier peut se produire lorsque le package de contenu « all » contient une combinaison de packages de contenu ignorés et de lots OSGi. Par exemple, si `myco-all-1.0.0-SNAPSHOT.zip` contient les deux packages incorporés mentionnés précédemment ainsi qu’un ou plusieurs lots OSGi, un nouveau package de contenu minimal est créé avec uniquement les lots OSGi. Ce package est toujours nommé `cloudmanager-synthetic-jar-package` et les lots contenus sont placés dans `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
>
>* Cette optimisation n’a aucune incidence sur les modules déployés sur AEM.
>* La correspondance entre les modules de contenu incorporés et ignorés est basée sur les noms de fichier. Cette optimisation échoue si plusieurs modules de contenu ignorés partagent le même nom de fichier ou si le nom du fichier change lors de l’incorporation.
