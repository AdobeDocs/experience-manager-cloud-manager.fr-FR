---
title: Présentation des résultats de tests
seo-title: Présentation des résultats de tests
description: En savoir plus sur les portes à trois niveaux lors de l’exécution d’un pipeline dans Cloud Manager
seo-description: Consultez cette page pour en savoir plus sur les points de contrôle à trois niveaux lors de l’exécution d’un pipeline, l’analyse de code et les tests de performance et de sécurité validant votre programme dans Cloud Manager.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
translation-type: tm+mt
source-git-commit: 7061910ae2cb0aae10876faf448838570f02d9be
workflow-type: tm+mt
source-wordcount: '2599'
ht-degree: 70%

---


# Présentation des résultats de tests {#understand-your-test-results}

Pendant l’exécution de pipeline, un certain nombre de mesures sont capturées et comparées soit aux indicateurs de performance clés (ICP) définis par le propriétaire de l’entreprise, soit aux normes définies par Adobe Managed Services.

Celles-ci sont signalées à l’aide du système de contrôle à trois niveaux tel que défini dans cette section.

## Points de contrôle à trois niveaux lors de l’exécution d’un pipeline {#three-tier-gates-while-running-a-pipeline}

Le pipeline comprend trois points de contrôle :

* Qualité du code
* Test de performance
* Test de sécurité

Pour chaque point de contrôle, il existe une structure à trois niveaux pour les problèmes identifiés.

* **Critique** : il s’agit des problèmes identifiés par le point de contrôle qui entraînent l’échec immédiat du pipeline.
* **Important** : il s’agit des problèmes identifiés par le point de contrôle qui entraînent la suspension du pipeline. Un responsable de déploiement, un responsable de projet ou un propriétaire d’entreprise peuvent soit contourner les problèmes, auquel cas le pipeline continue, soit accepter les problèmes, auquel cas le pipeline s’arrête avec un échec.
* **Informations** : il s’agit des problèmes identifiés par le point de contrôle qui sont fournis uniquement à titre d’information et qui n’ont aucune incidence sur l’exécution du pipeline.

>[!NOTE]
>
>Dans un pipeline de qualité du code uniquement, les échecs importants du point de contrôle Test de qualité du code ne peuvent pas être remplacés car l’étape Test de qualité du code est la dernière du pipeline.

## Test de qualité du code {#code-quality-testing}

Cette étape évalue la qualité du code de votre application. Il s’agit de l’objectif principal d’un pipeline dédié uniquement à la qualité du code et cette étape est exécutée immédiatement après l’étape de création dans tous les pipelines, aussi bien en et hors production. Voir [Configuration de votre pipeline CI-CD](/help/using/configuring-pipeline.md) pour en savoir plus sur les différents types de pipelines.

### Présentation du test de qualité du code {#understanding-code-quality-testing}

Au cours du test de qualité du code, le code source est analysé afin de s’assurer qu’il répond à certains critères de qualité. Actuellement, ceci est mis en oeuvre par une combinaison de SonarQube, d’examen au niveau du package de contenu à l’aide d’OakPAL et de validation du répartiteur à l’aide de l’outil d’optimisation du répartiteur. Il existe plus de 100 règles combinant des règles Java génériques et des règles spécifiques à AEM. Certaines des règles spécifiques à AEM sont créées en fonction des bonnes pratiques de l’équipe d’ingénierie AEM et sont appelées [Règles de qualité du code personnalisées](/help/using/custom-code-quality-rules.md).

>[!NOTE]
>Vous pouvez télécharger la liste complète des règles [ici](/help/using/assets/CodeQuality-rules-AMS.xlsx).

Les résultats de cette étape sont fournis sous forme de *note*. Le tableau ci-dessous résume les notes attribuées à divers critères de test :

| Nom | Définition | Catégorie | Seuil d’échec |
|--- |--- |--- |--- |
| Note de sécurité | A = 0 vulnérabilité <br/>B = au moins 1 vulnérabilité mineure<br/> C = au moins 1 vulnérabilité majeure <br/>D = au moins 1 vulnérabilité critique <br/>E = au moins 1 vulnérabilité de blocage | Critique | &lt; B |
| Note de fiabilité | A = 0 bogue <br/>B = au moins 1 bogue mineur <br/>C = au moins 1 bogue majeur <br/>D = au moins 1 bogue critique <br/>E = au moins 1 bogue bloqueur | Important | &lt; C |
| Note de maintenabilité | Le coût de correction en suspens pour les smells du code est : <br/><ul><li>&lt;=5 % du temps qui s’est déjà écoulé dans l’application, la note est A </li><li>entre 6 et 10 % la note est B </li><li>entre 11 et 20 % la note est C </li><li>entre 21 et 50 % la note est D</li><li>tout ce qui dépasse 50 % est E</li></ul> | Important | &lt; A |
| Couverture | Combinaison de couverture de ligne de tests unitaires et de couverture de condition utilisant cette formule : <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`<br/> où : CT = conditions qui ont été évaluées comme « vrai » au moins une fois lors de l’exécution de tests unitaires <br/>CF = conditions qui ont été évaluées comme « faux » au moins une fois <br/>LC = lignes couvertes = lines_ to_ cover - uncover_ lines <br/><br/> B = nombre total de conditions <br/>EL = nombre total de lignes exécutables (lines_to_cover) | Important | &lt; 50 % |
| Tests unitaires ignorés | Nombre de tests unitaires ignorés. | Infos | > 1 |
| Problèmes en cours | Types de problèmes généraux - Vulnérabilités, bogues et smells de code | Infos | > 0 |
| Lignes dupliquées | Nombre de lignes impliquées dans des blocs dupliqués. <br/>Pour qu’un bloc de code soit considéré comme dupliqué : <br/><ul><li>**Projets non Java :**</li><li>Il doit y avoir au moins 100 jetons successifs et dupliqués.</li><li>Ces jetons doivent être répartis au moins sur : </li><li>30 lignes de code pour COBOL </li><li>20 lignes de code pour ABAP </li><li>10 lignes de code pour d’autres langages</li><li>**Projets Java :**</li><li> Il devrait y avoir au moins 10 instructions successives et dupliquées, quel que soit le nombre de jetons et de lignes.</li></ul> <br/>Les différences dans la mise en retrait ainsi que dans les littéraux de chaîne sont ignorées lors de la détection des doublons. | Infos | > 1 % |
| Compatibilité Cloud Service | Nombre de problèmes de compatibilité Cloud Service identifiés. | Infos | > 0 |


>[!NOTE]
>
>Pour des définitions plus détaillées, consultez [Définitions des mesures](https://docs.sonarqube.org/display/SONAR/Metric+Definitions).

>[!NOTE]
>
>Pour en savoir plus sur les règles de qualité du code personnalisé exécutées par [!UICONTROL Cloud Manager], reportez-vous à la section [Règles de qualité du code personnalisé](custom-code-quality-rules.md).

### Traitement des faux positifs {#dealing-with-false-positives}

Le processus d’analyse de qualité n’est pas parfait et identifiera parfois de manière incorrecte des problèmes qui ne sont pas réellement problématiques. On parle alors de « faux positif ».

Dans ce cas, une annotation Java `@SuppressWarnings` standard spécifiant l’ID de règle comme attribut d’annotation peut être inscrite dans le code source. Par exemple, la règle SonarQube permettant de détecter les mots de passe codés en dur peut être agressive sur la façon dont un mot de passe codé en dur est identifié.

Pour prendre un exemple spécifique, ce code serait assez courant dans un projet AEM qui comporte un code pour se connecter à un service externe :

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube lèvera alors une vulnérabilité de bloqueur. Après avoir examiné le code, vous identifiez qu’il ne s’agit pas d’une vulnérabilité et pouvez l’annoter avec l’identifiant de règle approprié.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

En revanche, si le code était le suivant :

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

La bonne solution consiste alors à supprimer le mot de passe codé en dur.

>[!NOTE]
>
>Bien qu’il soit préférable de rendre l’annotation `@SuppressWarnings` aussi précise que possible, c’est-à-dire de n’annoter que l’énoncé ou le bloc qui cause le problème, il est tout de même possible de le faire à un niveau qui se rapporte à la classe.

## Test de sécurité {#security-testing}

[!UICONTROL Cloud Manager] exécute les ***contrôles de sécurité AEM*** à sur l’instance d’évaluation suite au déploiement et indique leur statut via l’interface utilisateur. Les résultats sont agrégés à partir de toutes les instances AEM de l’environnement.

Si l’une des **instances** signale un échec pour un contrôle d’intégrité donné, l’**environnement** entier ne réussit pas ce contrôle. Comme pour les tests de qualité du code et de performance, ces contrôles sont classés en catégories et signalés à l’aide du système de point de contrôle à trois niveaux. La seule différence réside dans le fait qu’il n’existe aucun seuil dans le cas des tests de sécurité. Tous les contrôles d’intégrité réussissent ou non.

Le tableau suivant répertorie les contrôles actuels :

| **Nom** | **Implémentation de la vérification de l’intégrité** | **Catégorie** |
|---|---|---|
| La disponibilité de l’API d’ajout de pare-feu de désérialisation est dans un état acceptable. | Disponibilité de l’API d’ajout de pare-feu de désérialisation | Critique |
| Le pare-feu de désérialisation est fonctionnel. | Pare-feu de désérialisation fonctionnel | Critique |
| Le pare-feu de désérialisation est chargé. | Pare-feu de désérialisation chargé | Critique |
| L’implémentation d’AuthorizableNodeName n’expose pas l’ID autorisable dans le nom/chemin du nœud. | Génération de nom de nœud autorisé | Critique |
| Les mots de passe par défaut ont été modifiés. | Comptes de connexion par défaut | Critique |
| Le servlet GET par défaut Sling est protégé contre les attaques par DOS. | Servlet Sling Get | Critique |
| Le gestionnaire de script Java Sling est correctement configuré. | Gestionnaire de script Java Sling | Critique |
| Le gestionnaire de script JSP Sling est correctement configuré. | Gestionnaire de script JSP Sling | Critique |
| SSL est correctement configuré. | Configuration SSL | Critique |
| Aucune stratégie de profil d’utilisateur évidemment risquée trouvée | Accès par défaut au profil utilisateur | Critique |
| Le filtre référent Sling est configuré pour empêcher les attaques CSRF. | Filtre référent Sling | Important |
| Le gestionnaire de bibliothèque HTML Adobe Granite est correctement configuré. | Configuration de gestionnaire de bibliothèque HTML CQ | Important |
| Le lot Prise en charge CRXDE est désactivé. | Prise en charge de CRXDE | Important |
| Le lot DavEx Sling et le servlet sont désactivés. | Contrôle d’intégrité DavEx | Important |
| L’exemple de contenu n’est pas installé. | Packages d’exemple de contenu | Important |
| Le filtre de requête WCM et le filtre de débogage WCM sont désactivés. | Configuration des filtres WCM | Important |
| Le lot WebDAV Sling et le servlet sont correctement configurés. | Contrôle d’intégrité WebDAV | Important |
| Le serveur web est configuré pour empêcher les clics publicitaires. | Configuration du serveur web | Important |
| La réplication n’utilise pas l’utilisateur « admin ». | Utilisateurs de réplication et de transport | Infos |

## Test de performance {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager exécute des tests de performances pour les programmes AEM Sites. Le test de performances est exécuté pendant environ 30 minutes en faisant tourner des utilisateurs virtuels (conteneurs) qui simulent des utilisateurs réels pour accéder aux pages sur l’environnement de la scène et simuler le trafic. Ces pages se trouvent à l’aide d’un analyseur de liens.

1. **Utilisateurs virtuels**

   Le nombre d’utilisateurs ou de conteneurs virtuels qui sont déclenchés par Cloud Manager est déterminé par les indicateurs de performance clés (temps de réponse et pages vues/min) définis par l’utilisateur dans le rôle Propriétaire de l’entreprise, tandis que [la création ou la modification du programme](setting-up-program.md) est effectuée. En fonction des indicateurs de performance clés définis, jusqu’à 10 conteneurs de simulation des utilisateurs réels seront exécutés. Les pages sélectionnées pour le test sont fractionnées et attribuées à chaque virtuel.

1. **Crawler**

   Avant le début de cette période de test de 30 minutes, Cloud Manager explore l’environnement d’évaluation à l’aide d’une ou de plusieurs URL sources configurées par l’ingénieur du service client. À partir de ces URL, le code HTML de chaque page est examiné et les liens sont parcourus en largeur d’abord. Ce processus d’exploration est limité à un maximum de 5 000 pages. Les requêtes du robot d’exploration ont un délai d’expiration fixe de 10 secondes.

1. **Jeux de pages à tester**

   Les pages sont sélectionnées par trois jeux de pages. Cloud Manager utilise les journaux d’accès des instances AEM dans Production et Stage pour déterminer les trois compartiments suivants :

   * *Pages* dynamiques populaires : Cette option est sélectionnée pour vérifier que les pages les plus populaires consultées par les clients en direct sont testées. Cloud Manager lit le journal d’accès et détermine les 25 pages les plus consultées par les clients en direct afin de générer une liste de `Popular Live Pages` principales pages. L’intersection de ces éléments qui sont également présents dans Stage est ensuite analysée sur Stage environnement.

   * *Autres pages* actives : Cette option est sélectionnée pour vous assurer que les pages qui ne figurent pas dans les 25 premières pages en direct populaires qui ne sont pas populaires mais qui sont importantes à tester sont testées. Tout comme les pages en direct populaires, elles sont extraites du journal d’accès et doivent également être présentes sur la scène.

   * *Nouvelles pages* : Cette option est sélectionnée pour tester les nouvelles pages qui n&#39;ont peut-être été déployées qu&#39;à l&#39;état et pas encore à la production, mais qui doivent être testées.

      **Répartition du trafic entre les jeux de pages sélectionnés**

      Vous pouvez choisir n&#39;importe quel jeu entre un et les trois jeux dans l&#39;onglet &quot;Tests&quot; de votre configuration de pipeline (Insérer un lien). La répartition du trafic dépend du nombre d’ensembles sélectionnés. Si les trois ensembles sont sélectionnés, 33 % du nombre total des pages vues sont placées dans chaque ensemble, si deux ensembles sont sélectionnés, 50 % sont dirigées vers chaque ensemble, si un seul est sélectionné, 100 % du trafic va vers cet ensemble.

      Par exemple, supposons qu’il y ait une division de 50 à 50 % entre les pages en direct les plus populaires et le jeu Nouvelles pages (dans cet exemple, Autres pages en direct n’est pas utilisé) et le jeu Nouvelles pages contient 3 000 pages. L’indicateur de performance clé des pages vues par minute est défini sur 200. Pendant la période test de 30 minutes :

      * Chacune des 25 pages des pages actives populaires est demandée 120 fois – ((200 x 0,5) : 25) x 30 = 120

      * Chacune des 3 000 pages des nouvelles pages sera demandée une fois - ((200 x 0,5) : 3 000) x 30 = 1

### Tests et Rapports {#testing-reporting}

Cloud Manager exécute des tests de performances pour les programmes AEM Sites en demandant des pages (en tant qu’utilisateur non authentifié par défaut) sur le serveur de publication d’étape pendant une période de test de 30 minutes et en mesurant les mesures générées par l’utilisateur (virtuel) (temps de réponse, taux d’erreur, vues par minute, etc.). pour chaque page, ainsi que pour différentes mesures au niveau du système (UC, mémoire, données réseau) pour toutes les instances.\
Le tableau suivant récapitule les mesures des tests de performances par rapport à l&#39;utilisation du système de portes à trois niveaux :

Le tableau suivant résume la matrice des tests de performance à l’aide du système de point de contrôle à trois niveaux :

| **Mesure** | **Catégorie** | **Seuil d’échec** |
|---|---|---|
| Taux d’erreur de demande de page % | Critique | >= 2 % |
| Taux d’utilisation de l’UC | Critique | >= 80 % |
| Délai d’attente d’E/S de disque | Critique | >= 50 % |
| Délai de réponse du 95e percentile | Important | >= ICP de niveau programme |
| Délai de réponse max. | Important | >= 18 secondes |
| Nombre de pages vues par minute | Important | &lt; ICP de niveau programme |
| Utilisation de la bande passante de disque | Important | >= 90 % |
| Utilisation de la bande passante réseau | Important | >= 90 % |
| Demandes par minute | Infos | >= 6 000 |

Pour plus d&#39;informations sur l&#39;utilisation de l&#39;authentification de base pour les tests de performances des sites et ressources, consultez la section **Authenticated Performance Testing** ci-dessous.

>[!NOTE]
>Chaque instance est surveillée pendant la période du test, tant pour la publication que pour l’auteur. Si aucune mesure n’est obtenue pour une seule instance, cette mesure est signalée comme inconnue et l’étape correspondante échoue.

#### Test de performances avec authentification {#authenticated-performance-testing}

Cette fonctionnalité est facultative Sites.
Les clients AMS disposant de sites authentifiés peuvent spécifier un nom d’utilisateur et un mot de passe que Cloud Manager utilisera pour accéder au site web lors des tests de performances des sites.
Le nom d’utilisateur et le mot de passe sont spécifiés sous la forme de variables de pipeline avec les noms `CM_PERF_TEST_BASIC_USERNAME` et `CM_PERF_TEST_BASIC_PASSWORD`.
Bien que cela ne soit pas strictement requis, il est recommandé d’utiliser le type de variable de chaîne pour le nom d’utilisateur et le type de variable secretString pour le mot de passe. Si ces deux éléments sont spécifiés, chaque requête du robot de tests de performances et des utilisateurs virtuels de test contiendra ces informations d’identification sous forme d’authentification HTTP basique.

Pour définir ces variables à l’aide de l’interface de ligne de commande de Cloud Manager, exécutez :

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Consultez [Variables](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Variables/patchPipelineVariables) pour savoir comment utiliser l&#39;API.

### AEM Assets {#aem-assets}

Cloud Manager exécute des tests de performances pour les programmes AEM Assets en téléchargeant régulièrement des fichiers pendant une période de test de 30 minutes.

1. **Configuration requise pour l’intégration**

   Pour les tests de performances des ressources, votre ingénieur de réussite client créera un utilisateur `cloudmanager` (et un mot de passe) lors de l’intégration de l’environnement Auteur à l’étape. Les étapes du test de performances nécessitent l’utilisateur nommé `cloudmanager` et le mot de passe associé configuré par votre CSE. Il ne doit pas être supprimé de l’auteur ni modifié en autorisations par écrit. Ce faisant, les tests de performances des ressources échoueront probablement.

1. **Images et ressources à tester**

   Les clients peuvent télécharger leurs propres fichiers pour les tester. Vous pouvez le faire à partir de l’écran Configuration du pipeline ou Modifier. Les formats d’image courants tels que JPEG, PNG, GIF et BMP sont pris en charge, ainsi que les fichiers Photoshop, Illustrator et Postscript. Cependant, si aucune image n’est téléchargée, Cloud Manager utilise une image par défaut et un document PDF à des fins de test.

1. **Distribution des ressources pour les tests**

   La répartition du nombre de ressources de chaque type qui sont téléchargées par minute est définie dans l’écran Configuration du pipeline ou Modifier.
Par exemple, si une répartition 70/30 est utilisée, comme illustré dans le schéma ci-dessous. Dix ressources sont téléchargées par minute, 7 images et 3 documents.

1. **Tests et Rapports**

   Cloud Manager crée un dossier sur l’instance d’auteur, en utilisant le nom d’utilisateur et le mot de passe configurés par le CSE à l’étape 1 (Exigences d’Onbbrading), comme mentionné ci-dessus, et télécharge des fichiers dans le dossier à l’aide d’une bibliothèque opensource. Les tests exécutés par l’étape de test des ressources sont écrits à l’aide de cette bibliothèque open source - https://github.com/adobe/toughday2. Le temps de traitement de chaque ressource ainsi que diverses mesures au niveau du système sont mesurés sur la durée de test de 30 minutes. Cette fonctionnalité peut télécharger des images et des documents PDF.

   >[!NOTE]
   >Pour en savoir plus sur la configuration des tests de performances, consultez la rubrique [Configuration de votre pipeline CI/CD](configuring-pipeline.md). Reportez-vous à [Configuration de votre Programme](setting-up-program.md) pour savoir comment configurer votre programme et définir vos IPC, voir .

### Graphiques des résultats de tests de performance {#performance-testing-results-graphs}

De nouveaux graphiques et des options de téléchargement ont été ajoutés à la boîte de dialogue Résultats des tests de performance.

Lorsque vous ouvrez la boîte de dialogue Test de performance, les panneaux de mesures peuvent être développés pour afficher un graphique, fournir un lien de téléchargement ou les deux.

Dans la version 2018.7.0 de [!UICONTROL Cloud Manager], cette fonctionnalité est disponible pour les mesures suivantes :

* **Utilisation de l’UC**
   * Graphique montrant l’utilisation de l’UC pendant la période de test.

* **Délai d’attente d’E/S de disque**
   * Graphique montrant le délai d’attente d’E/S de disque pendant la période de test.

* **Taux d’erreur de page**
   * Graphique montrant les erreurs de page par minute pendant la période de test.
   * Fichier CSV répertoriant les pages qui ont généré une erreur pendant le test.

* **Utilisation de la bande passante de disque**
   * Graphique de l’utilisation de la bande passante par le disque pendant la période de test.

* **Utilisation de la bande passante réseau**
   * Graphique montrant l’utilisation de la bande passante par le réseau pendant la période de test.

* **Délai de réponse max.**
   * Graphique montrant le délai de réponse maximal par minute pendant la période de test.

* **Délai de réponse du 95e percentile**
   * Graphique montrant le délai de réponse du 95e percentile par minute pendant la période de test.
   * Fichier CSV répertoriant les pages dont le délai de réponse du 95ème centile a dépassé les ICP définis.

Les illustrations suivantes montrent les graphiques des tests de performance :

![](assets/understand_test-results-screen1.png)

![](assets/screen_shot_2018-09-05at83933pm.png)

