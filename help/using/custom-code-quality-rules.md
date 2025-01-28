---
title: Règles de qualité du code personnalisé
description: Découvrez les détails des règles de qualité du code personnalisé exécutées par Cloud Manager lors du test de qualité du code. Ces règles sont basées sur les bonnes pratiques de l’ingénierie AEM.
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: 1b7b703f7cba69878bd98aa971844741ebea7dba
workflow-type: ht
source-wordcount: '3490'
ht-degree: 100%

---


# Règles de qualité du code personnalisé {#custom-code-quality-rules}

Découvrez en détail les règles de qualité du code personnalisé exécutées par Cloud Manager dans le cadre des [tests de qualité de code](/help/using/code-quality-testing.md), basées sur les bonnes pratiques en matière d’ingénierie AEM.

>[!NOTE]
>
>Les exemples de code utilisés ici ne sont fournis qu’à titre indicatif. Reportez-vous à la [documentation relative aux concepts de SonarQube](https://docs.sonarsource.com/sonarqube-server/latest/) pour en savoir plus sur ses concepts et ses règles de qualité.

Les règles SonarQube complètes ne peuvent pas être téléchargées en raison d’informations exclusives d’Adobe. Vous pouvez télécharger la liste complète des règles [via ce lien](/help/assets/CodeQuality-rules-latest-AMS.xlsx). Poursuivez la lecture de ce document pour obtenir des descriptions et des exemples de règles.

>[!IMPORTANT]
>
>À compter du jeudi 13 février 2025 (Cloud Manager 2025.2.0), la qualité du code Cloud Manager utilisera une version 9.9 de SonarQube mise à jour et une liste mise à jour des règles que vous pouvez [télécharger ici](/help/assets/CodeQuality-rules-latest-AMS-2024-12-0.xlsx).

## Règles SonarQube {#sonarqube-rules}

La section suivante détaille les règles SonarQube exécutées par Cloud Manager.

### Ne pas utiliser de fonctions potentiellement dangereuses {#do-not-use-potentially-dangerous-functions}

* **Clé** : CQRules:CWE-676
* **Type** : vulnérabilité
* **Gravité** : majeure
* **Depuis** : version 2018.4.0

Les méthodes `Thread.stop()` et `Thread.interrupt()` peuvent générer des problèmes difficiles à reproduire et, dans certains cas, des failles de sécurité. Leur utilisation doit être minutieusement surveillée et validée. En règle générale, la transmission de messages est une méthode plus sûre pour atteindre des objectifs similaires.

#### Code non conforme {#non-compliant-code}

```java
public class DontDoThis implements Runnable {
  private Thread thread;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    thread.stop();  // UNSAFE!
  }
 
  public void run() {
    while (true) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

#### Code conforme {#compliant-code}

```java
public class DoThis implements Runnable {
  private Thread thread;
  private boolean keepGoing = true;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    keepGoing = false;
  }
 
  public void run() {
    while (this.keepGoing) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

### N’utilisez pas de chaînes de format pouvant être contrôlées en externe. {#do-not-use-format-strings-which-may-be-externally-controlled}

* **Clé** : CQRules:CWE-134
* **Type** : vulnérabilité
* **Gravité** : majeure
* **Depuis** : version 2018.4.0

L’utilisation d’une chaîne de format provenant d’une source externe (telle qu’un paramètre de requête ou un contenu créé par l’utilisateur ou l’utilisatrice) peut exposer une application aux attaques par déni de service. Dans certains cas, une chaîne de format peut être contrôlée en externe, mais elle n’est autorisée que si elle provient de sources approuvées.

#### Code non conforme {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### Les requêtes HTTP doivent toujours avoir des délais de socket et de connexion {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Clé** : CQRules:ConnectionTimeoutMechanism
* **Type** : bogue
* **Gravité** : critique
* **Depuis** : version 2018.6.0

Lors de l’exécution de requêtes HTTP à partir d’une application AEM, il est essentiel que les délais appropriés soient configurés afin d’éviter toute consommation inutile de threads. Malheureusement, le client HTTP par défaut de Java™, `java.net.HttpUrlConnection` et le client de composants HTTP Apache largement utilisé ne disposent pas d’un délai d’expiration par défaut. Par conséquent, les délais d’expiration doivent être explicitement configurés. Il est considéré comme une bonne pratique pour ces délais d’expiration de ne pas dépasser 60 secondes.

#### Code non conforme {#non-compliant-code-2}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void dontDoThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  HttpClient httpClient = builder.build();

  // do something with the client
}

public void dontDoThisEither() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

#### Code conforme {#compliant-code-1}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void doThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  RequestConfig requestConfig = RequestConfig.custom()
    .setConnectTimeout(5000)
    .setSocketTimeout(5000)
    .build();
  builder.setDefaultRequestConfig(requestConfig);
 
  HttpClient httpClient = builder.build();
   
  // do something with the client
}

public void orDoThis() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
  urlConnection.setConnectTimeout(5000);
  urlConnection.setReadTimeout(5000);
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

### Les objets `ResourceResolver` doivent toujours être fermés. {#resourceresolver-objects-should-always-be-closed}

* **Clé** : CQRules:CQBP-72
* **Type** : `Code Smell`
* **Gravité** : majeure
* **Depuis** : version 2018.4.0

Les objets `ResourceResolver` obtenus à partir de `ResourceResolverFactory` consomment des ressources système. Bien qu’il existe des mesures pour récupérer ces ressources lorsqu’un objet `ResourceResolver` n’est plus en cours d’utilisation, il est plus efficace de fermer explicitement tous les objets `ResourceResolver` ouverts en appelant la méthode `close()`.

Une idée relativement répandue est que les objets `ResourceResolver` créés à l’aide d’une session JCR existante ne doivent pas être fermés explicitement. Une autre idée répandue est que la fermeture de ces objets ferme la session JCR sous-jacente. Ce n’est pas le cas. Quelle que soit la manière dont un objet `ResourceResolver` est ouvert, il doit être fermé lorsqu’il n’est plus utilisé. Puisque `ResourceResolver` implémente l’interface `Closeable`, il est également possible d’utiliser la syntaxe `try-with-resources` plutôt que d’appeler explicitement `close()`.

#### Code non conforme {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Code conforme {#compliant-code-2}

```java
public void doThis(Session session) throws Exception {
  ResourceResolver resolver = null;
  try {
    resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
    // do something with the resolver
  } finally {
    if (resolver != null) {
      resolver.close();
    }
  }
}

public void orDoThis(Session session) throws Exception {
  try (ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object) session))){
    // do something with the resolver
  }
}
```

### N’utilisez pas les chemins de servlet Sling pour enregistrer les servlets. {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Clé** : CQRules:CQBP-75
* **Type** : `Code Smell`
* **Gravité** : majeure
* **Depuis** : version 2018.4.0

Comme décrit dans la [documentation Sling](https://sling.apache.org/documentation/the-sling-engine/servlets.html), il est déconseillé de lier les servlets aux chemins. Les servlets liés au chemin ne peuvent pas utiliser les contrôles d’accès JCR standard et, par conséquent, nécessitent une rigueur de sécurité supplémentaire. Plutôt que d’utiliser des servlets liés au chemin d’accès, il est recommandé de créer des nœuds dans le référentiel et d’enregistrer les servlets par type de ressource.

#### Code non conforme {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Les exceptions capturées doivent être consignées ou renvoyées, mais pas les deux. {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Clé** : CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

En règle générale, une exception doit être consignée une seule fois. Journaliser les exceptions à plusieurs reprises peut prêter à confusion, car il est difficile de connaître le nombre d’occurrences d’une exception. Le modèle le plus courant qui conduit à ce problème consiste à journaliser et à émettre une exception capturée.

#### Code non conforme {#non-compliant-code-6}

```java
public void dontDoThis() throws Exception {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
    throw e;
  }
}
```

#### Code conforme {#compliant-code-3}

```java
public void doThis() {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
  }
}

public void orDoThis() throws MyCustomException {
  try {
    someOperation();
  } catch (Exception e) {
    throw new MyCustomException(e);
  }
}
```

### Éviter les instructions de journal immédiatement suivies d’instructions de renvoi {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Clé** : CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

Un autre schéma courant à éviter consiste à consigner un message, puis à émettre immédiatement une exception. Ce problème indique généralement que le message d’exception sera dupliqué dans les fichiers journaux.

#### Code non conforme {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Code conforme {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Évitez de journaliser les informations lors de la gestion des requêtes GET ou HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Clé** : CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **Type** : `Code Smell`
* **Gravité** : mineure

En règle générale, le niveau de journal Informations doit être utilisé pour délimiter les actions importantes et, par défaut, AEM est configuré pour le journal au niveau Information ou au-dessus. Les méthodes GET et HEAD ne doivent jamais être en lecture seule et ne constituent donc pas des actions importantes. La journalisation au niveau INFO en réponse aux demandes GET ou HEAD est susceptible de créer un bruit journal significatif, rendant ainsi plus difficile l’identification des informations utiles dans les fichiers journaux. Lors de la gestion des requêtes GET ou HEAD, la journalisation doit se trouver aux niveaux WARN ou ERROR si quelque chose est erroné. Pour des informations de résolution des problèmes plus détaillées, la journalisation doit se trouver aux niveaux DEBUG ou TRACE.

>[!NOTE]
>
>Ce workflow ne s’applique pas à la journalisation de type access.log pour chaque requête.

#### Code non conforme {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Code conforme {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### N’utilisez pas `Exception.getMessage()` comme premier paramètre d’une instruction de journalisation. {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Clé** : CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

Il est recommandé que les messages de journal fournissent des informations contextuelles sur l’emplacement d’une exception dans l’application. Bien que le contexte puisse également être déterminé par l’utilisation des arborescences des appels de procédure, il est généralement plus facile de lire et de comprendre le message du journal. Par conséquent, lors de la journalisation d’une exception, il est déconseillé d’utiliser le message de l’exception comme message du journal. Le message d’exception doit détailler ce qui est erroné. En revanche, le message du journal doit informer le lecteur ou la lectrice de ce que faisait l’application lorsque l’exception s’est produite. Le message d’exception est toujours journalisé. En spécifiant votre propre message, les journaux sont plus faciles à comprendre.

#### Code non conforme {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Code conforme {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### La journalisation des blocs catch doit se trouver au niveau d’avertissement ou d’erreur {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **Clé** : CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

Comme le suggère leur nom, les exceptions Java™ doivent toujours être utilisées dans des circonstances exceptionnelles. Par conséquent, lorsqu’une exception est capturée, il est important de s’assurer que les messages du journal sont consignés au niveau approprié : AVERTISSEMENT ou ERREUR. Ces messages s’affichent ainsi correctement dans les journaux.

#### Code non conforme {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Code conforme {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Ne pas imprimer les arborescences des appels de procédure sur la console {#do-not-print-stack-traces-to-the-console}

* **Clé** : CQRules:CQBP-44---ExceptionPrintStackTrace
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

Le contexte est essentiel pour la compréhension des messages du journal. L’utilisation d’`Exception.printStackTrace()` entraîne seulement la sortie de la trace de la pile dans le flux d’erreurs standard, ce qui provoque la perte de tout le contexte. De plus, dans une application multi-thread telle qu’AEM, si plusieurs exceptions sont imprimées à l’aide de cette méthode en parallèle, leurs traces de pile peuvent se chevaucher, ce qui prête à confusion. Les exceptions ne doivent être consignées que dans la structure de journalisation.

#### Code non conforme {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### Code conforme {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Ne générez pas de sortie standard ou d’erreur standard. {#do-not-output-to-standard-output-or-standard-error}

* **Clé** : CQRules:CQBP-44—LogLevelConsolePrinters
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

La journalisation sur AEM doit toujours être effectuée via la structure de journalisation SLF4J. La génération directe d’une sortie standard ou d’un flux d’erreur standard perd les informations structurelles et contextuelles fournies par la structure de journalisation et peut entraîner quelquefois des problèmes de performances.

#### Code non conforme {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### Code conforme {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Évitez les chemins `/apps` et `/libs` codés en dur. {#avoid-hardcoded-apps-and-libs-paths}

* **Clé** : CQRules:CQBP-71
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

Les chemins commençant par `/libs` et `/apps` ne doivent généralement pas être codés en dur. Ces chemins sont généralement stockés par rapport au chemin de recherche Sling, qui est par défaut `/libs,/apps`. L’utilisation du chemin absolu peut introduire des défauts discrets qui n’apparaîtront que plus tard dans le cycle de vie du projet.

#### Code non conforme {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Code conforme {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### Le planificateur Sling ne doit pas être utilisé. {#sonarqube-sling-scheduler}

* **Clé** : CQRules:AMSCORE-554
* **Type** : compatibilité `Code Smell`/Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

N’utilisez pas le planificateur Sling pour les tâches qui nécessitent une exécution garantie. Les tâches planifiées Sling garantissent l’exécution et conviennent mieux aux environnements organisés avec ou sans grappes.

Voir la [documentation sur la gestion des traitements et des événements Apache Sling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) pour en savoir plus sur la façon dont les traitements Sling sont gérés dans des environnements en cluster.

### Les API AEM obsolètes ne doivent pas être utilisées. {#sonarqube-aem-deprecated}

* **Clé** : AMSCORE-553
* **Type** : compatibilité `Code Smell`/Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

La surface de l’API AEM est constamment revue pour identifier les API dont l’utilisation est déconseillée et qui sont donc considérées comme obsolètes.

Dans de nombreux cas, ces API sont abandonnées en y associant l’annotation standard Java™ *@Deprecated*. Elles sont à ce titre identifiées par la mention `squid:CallToDeprecatedMethod`.

Cependant, il arrive qu’une API devienne obsolète dans le contexte d’AEM, mais pas dans d’autres contextes. Cette règle identifie cette deuxième classe.

## Règles de contenu OakPAL {#oakpal-rules}

La section suivante présente les vérifications OakPAL exécutées par Cloud Manager.

>[!NOTE]
>
>OakPAL est une structure qui valide les packages de contenu à l’aide d’un référentiel Oak autonome. Un partenaire d’AEM et lauréat du prix 2019 AEM Rock Star North America l’a développée.

### Les clientes et clients ne doivent pas implémenter ni étendre les API de produit annotées avec @ProviderType {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Clé** : CQBP-84
* **Type** : bogue
* **Gravité** : critique
* **Depuis** : version 2018.7.0

L’API AEM contient des interfaces et des classes Java™ destinées uniquement à être utilisées, mais non implémentées, par du code personnalisé. Par exemple, seul AEM implémente l’interface `com.day.cq.wcm.api.Page`.

L’ajout de nouvelles méthodes à ces interfaces n’affecte pas le code existant, ce qui rend l’ajout de nouvelles méthodes rétrocompatibles. Cependant, si le code personnalisé implémente l’une de ces interfaces, il introduit un risque de rétrocompatibilité pour le client ou la cliente.

AEM annote les interfaces et les classes destinées uniquement pour leur implémentation avec `org.osgi.annotation.versioning.ProviderType` ou, parfois, avec l’annotation héritée `aQute.bnd.annotation.ProviderType`. Cette règle détecte les instances où le code personnalisé implémente une telle interface ou étend une classe.

#### Code non conforme {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Les packages des clientes et des clients ne doivent ni créer ni modifier les nœuds sous `/libs`. {#oakpal-customer-package}

* **Clé** : BannedPath
* **Type** : bogue
* **Gravité** : bloqueur
* **Depuis** : version 2019.6.0

En guise de bonne pratique, il a été établi depuis longtemps que l’arborescence de contenu `/libs` dans le référentiel de contenu AEM doit être considérée comme étant en lecture seule par les clients. La modification des nœuds et des propriétés sous `/libs` crée un risque significatif pour les mises à jour majeures et mineures. Les modifications apportées à `/libs` ne sont effectuées que par Adobe par le biais de canaux officiels.

### Les packages ne doivent pas contenir de configurations OSGi en double. {#oakpal-package-osgi}

* **Clé** : DuplicateOsgiConfigurations
* **Type** : bogue
* **Gravité** : majeure
* **Depuis** : version 2019.6.0

Le fait qu’un même composant OSGi soit configuré plusieurs fois est un problème courant qui se produit sur les projets complexes. Ce problème crée une ambiguïté quant à la configuration exploitable. Cette règle est « compatible avec le mode d’exécution » en ce qu’elle identifie uniquement les problèmes où le même composant est configuré plusieurs fois dans le même mode d’exécution ou la même combinaison de modes d’exécution.

#### Code non conforme {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Code conforme {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Les dossiers de configuration et d’installation ne doivent contenir que des nœuds OSGi {#oakpal-config-install}

* **Clé** : ConfigAndInstallShouldOnlyContainOsgiNodes
* **Type** : bogue
* **Gravité** : majeure
* **Depuis** : version 2019.6.0

Pour des raisons de sécurité, les chemins contenant `/config/` et `/install/` ne sont lisibles que par les utilisateurs administratifs dans AEM et doivent être utilisés uniquement pour la configuration OSGi et les lots OSGi. Placer d’autres types de contenu sous les chemins contenant ces segments donne un comportement d’application qui varie involontairement entre les personnes qui font partie de l’équipe d’administration et celles qui n’en font pas partie.

Un problème courant est l’utilisation de nœuds nommés `config` dans les boîtes de dialogue des composants ou lors de la spécification de la configuration de l’éditeur de texte enrichi pour la modification statique. Pour résoudre ce problème, le nœud incriminé doit être renommé avec un nom compatible. Pour la configuration de l’éditeur de texte enrichi, utilisez la propriété `configPath` sur le nœud `cq:inplaceEditing` pour spécifier le nouvel emplacement.

#### Code non conforme {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Code conforme {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### Les packages ne doivent pas se chevaucher. {#oakpal-no-overlap}

* **Clé** : PackageOverlaps
* **Type** : bogue
* **Gravité** : majeure
* **Depuis** : version 2019.6.0

Tout comme la règle [Les packages ne doivent pas contenir de configurations OSGi en double](#oakpal-package-osgi), ce problème est courant sur les projets complexes où le même chemin de nœud est écrit par plusieurs packages de contenu distincts. Bien que l’utilisation des dépendances des packages de contenu puisse servir à garantir un résultat cohérent, il est préférable d’éviter tout recouvrement.

### Le mode de création par défaut ne doit pas être défini sur l’interface d’utilisation classique. {#oakpal-default-authoring}

* **Clé** : ClassicUIAuthoringMode
* **Type** : compatibilité `Code Smell`/Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

La configuration OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` définit le mode de création par défaut dans AEM. Comme l’interface utilisateur classique a été abandonnée depuis AEM 6.4, un problème survient maintenant lorsque le mode de création par défaut est configuré sur l’interface utilisateur classique.

### Les boîtes de dialogue de composants doivent être de type interface d’utilisation tactile. {#oakpal-components-dialogs}

* **Clé** : ComponentWithOnlyClassicUIDialog
* **Type** : compatibilité `Code Smell`/Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

Les composants AEM avec une boîte de dialogue d’interface d’utilisation classique doivent également disposer d’une boîte de dialogue d’interface d’utilisation tactile pour une création et une compatibilité optimales avec le modèle de déploiement du Cloud Service, qui ne prend pas en charge l’interface d’utilisation classique. Cette règle vérifie les scénarios suivants :

* Un composant doté d’une boîte de dialogue d’interface utilisateur classique (c’est-à-dire un nœud enfant `dialog`) doit avoir une boîte de dialogue d’interface utilisateur tactile correspondante (c’est-à-dire un nœud enfant `cq:dialog`).
* Un composant doté d’une boîte de dialogue d’interface utilisateur classique (c’est-à-dire un nœud `design_dialog`) doit avoir une boîte de dialogue de conception d’interface utilisateur tactile correspondante (c’est-à-dire un nœud enfant `cq:design_dialog`).
* Un composant doté d’une boîte de dialogue d’interface utilisateur classique et d’une boîte de dialogue de conception d’interface utilisateur classique doit comporter à la fois une boîte de dialogue d’interface utilisateur tactile correspondante et une boîte de dialogue de conception d’interface utilisateur tactile correspondante.

La documentation des outils de modernisation d’AEM contient des informations et des outils pour convertir les composants de l’interface utilisateur classique en interface utilisateur tactile. Consultez la [documentation relative aux outils de modernisation d’AEM](https://opensource.adobe.com/aem-modernize-tools/) pour en savoir plus.

### Les agents de réplication inverse ne doivent pas être utilisés. {#oakpal-reverse-replication}

* **Clé** : ReverseReplication
* **Type** : compatibilité `Code Smell`/Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

La prise en charge de la réplication inverse n’est pas disponible dans les déploiements Cloud Service, comme décrit dans la section [Notes de mise à jour : suppression des agents de réplication](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes#replication-agents).

Les client(e)s qui utilisent la réplication inverse doivent contacter Adobe pour obtenir d’autres solutions.

### Les ressources contenues dans les bibliothèques clientes activées par proxy doivent se trouver dans un dossier nommé ressources. {#oakpal-resources-proxy}

* **Clé** : ClientlibProxyResource
* **Type** : bogue
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Les bibliothèques clientes AEM peuvent contenir des ressources statiques telles que des images et des polices. Comme décrit dans la [documentation relative à l’utilisation des bibliothèques côté client](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/developing/introduction/clientlibs#using-preprocessors), lorsque vous utilisez des bibliothèques clientes par proxy, ces ressources statiques doivent être contenues dans un dossier enfant nommé `resources` afin d’être référencées efficacement sur les instances de publication.

#### Code non conforme {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### Code conforme {#compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Utilisation de Cloud Service incompatible avec les processus de workflow {#oakpal-usage-cloud-service}

* **Clé** : CloudServiceIncompatibleWorkflowProcess
* **Type** : `Code Smell`
* **Gravité** : bloqueur
* **Depuis** : version 2021.2.0

Avec l’adoption de micro-services Assets pour le traitement des ressources dans AEM Cloud Service, plusieurs processus de workflow utilisés dans les versions on-premise et AMS d’AEM ne sont plus pris en charge ou sont devenus inutiles.

L’outil de migration dans le [référentiel GitHub d’AEM Assets as a Cloud Service](https://github.com/adobe/aem-cloud-migration) peut être utilisé pour mettre à jour les modèles de workflow lors de la migration vers AEM as a Cloud Service.

### L’utilisation de modèles statiques est découragée en faveur de modèles modifiables. {#oakpal-static-template}

* **Clé** : StaticTemplateUsage
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Bien que l’utilisation des modèles statiques ait été courante dans les projets AEM, les modèles modifiables sont vivement recommandés, car ils offrent la plus grande flexibilité et prennent en charge des fonctionnalités supplémentaires qui ne sont pas présentes dans les modèles statiques. Vous trouverez plus d’informations à ce sujet dans la [documentation relative aux modèles de page modifiables](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/developing/platform/templates/page-templates-editable).

La migration de modèles statiques vers des modèles modifiables peut être largement automatisée à l’aide des [outils de modernisation d’AEM](https://opensource.adobe.com/aem-modernize-tools/).

### L’utilisation des composants de base hérités n’est pas encouragée. {#oakpal-usage-legacy}

* **Clé** : LegacyFoundationComponentUsage
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Les composants de base hérités (c’est-à-dire les composants situés dans `/libs/foundation`) ont été abandonnés depuis plusieurs versions d’AEM au profit des [composants principaux](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/introduction). L’utilisation des composants de base hérités comme fondations pour les composants personnalisés, que ce soit par recouvrement ou par héritage, est déconseillée et ces composants doivent être convertis en composants principaux correspondants.

Les [Outils de modernisation d’AEM](https://opensource.adobe.com/aem-modernize-tools/) peuvent faciliter la conversion.

### Les nœuds de définition d’index de recherche personnalisée doivent être des enfants directs de `/oak:index`. {#oakpal-custom-search}

* **Clé** : OakIndexLocation
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

AEM Cloud Service exige que les définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) soient des nœuds enfants directs de `/oak:index`. Les index qui se trouvent à des emplacements différents doivent être déplacés pour être compatibles avec AEM Cloud Service. Vous trouverez plus d’informations sur les index de recherche dans la [documentation relative à la recherche et à l’indexation de contenu](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/indexing).

### Les nœuds de définition d’index de recherche personnalisée doivent avoir une compatVersion de 2. {#oakpal-custom-search-compatVersion}

* **Clé** : IndexCompatVersion
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

AEM Cloud Service exige que la propriété `compatVersion` soit définie sur `2` pour les définitions d’index de recherche personnalisée (c’est-à-dire pour les nœuds de type `oak:QueryIndexDefinition`). AEM Cloud Service ne prend en charge aucune autre valeur. Vous trouverez plus d’informations sur les index de recherche dans la [documentation relative à la recherche et à l’indexation de contenu](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/indexing).

### Les nœuds descendants des nœuds de définition d’index de recherche personnalisée doivent être de type `nt:unstructured`. {#oakpal-descendent-nodes}

* **Clé** : IndexDescendantNodeType
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Des problèmes difficiles à résoudre peuvent survenir lorsqu’un nœud de définition d’index de recherche personnalisée comporte des nœuds enfants non ordonnés. Pour éviter ces nœuds, il est recommandé que tous les nœuds descendants d’un nœud `oak:QueryIndexDefinition` soient de type `nt:unstructured`.

### Les nœuds de définition d’index de recherche personnalisée doivent contenir un nœud enfant nommé `indexRules` qui a des enfants. {#oakpal-custom-search-index}

* **Clé** : IndexRulesNode
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Un nœud de définition d’index de recherche personnalisée correctement défini doit contenir un nœud enfant appelé `indexRules`, qui doit avoir au moins un enfant. Vous trouverez plus d’informations à ce sujet dans la [documentation d’Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### Les nœuds de définition d’index de recherche personnalisée doivent respecter les conventions de nommage. {#oakpal-custom-search-definitions}

* **Clé** : IndexName
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Le Cloud Service AEM exige que les définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) soient nommés selon un modèle spécifique décrit dans [Recherche et indexation de contenu](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use).

### Les nœuds de définition d’index de recherche personnalisée doivent utiliser le type d’index Lucene. {#oakpal-index-type-lucene}

* **Clé** : IndexType
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

AEM Cloud Service exige que les définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) aient une propriété `type` dont la valeur est définie sur `lucene`. L’indexation avec ces types d’index hérités doit être mise à jour avant la migration vers AEM Cloud Service. Consultez la [documentation relative à la recherche et à l’indexation de contenu](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) pour en savoir plus.

### Les nœuds de définition d’index de recherche personnalisée ne doivent pas contenir de propriété nommée `seed`. {#oakpal-property-name-seed}

* **Clé** : IndexSeedProperty
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

AEM Cloud Service interdit aux définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) de contenir une propriété nommée `seed`. L’indexation avec cette propriété doit être mise à jour avant la migration vers AEM Cloud Service. Consultez la [documentation relative à la recherche et à l’indexation de contenu](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) pour en savoir plus.

### Les nœuds de définition d’index de recherche personnalisée ne doivent pas contenir de propriété nommée `reindex`. {#oakpal-reindex-property}

* **Clé** : IndexReindexProperty
* **Type** : `Code Smell`
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

AEM Cloud Service interdit aux définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) de contenir une propriété nommée `reindex`. L’indexation avec cette propriété doit être mise à jour avant la migration vers AEM Cloud Service. Consultez la [documentation relative à la recherche et à l’indexation de contenu](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) pour en savoir plus.

### Les nœuds de définition d’index ne doivent pas être déployés dans le module de contenu de l’interface d’utilisation. {#oakpal-ui-content-package}

* **Clé** : IndexNotUnderUIContent
* **Type** : amélioration
* **Gravité** : mineure
* **Depuis** : version 2024.6.0

AEM Cloud Service interdit le déploiement de définitions d’index de recherche personnalisées (nœuds de type `oak:QueryIndexDefinition`) dans le package de contenu de l’interface d’utilisation.

>[!WARNING]
>
>Nous vous conseillons vivement de résoudre ce problème dès que possible, car cela entraînera l’échec des pipelines à compter de la [version d’août 2024 de Cloud Manager.](/help/release-notes/current.md)

### La définition d’index en texte intégral personnalisé de type `damAssetLucene` doit comporter le préfixe `damAssetLucene`. {#oakpal-dam-asset-lucene}

* **Clé** : CustomFulltextIndexesOfTheDamAssetCheck
* **Type** : amélioration
* **Gravité** : mineure
* **Depuis** : version 2024.6.0

AEM Cloud Service interdit que les définitions d’index en texte intégral personnalisées de type `damAssetLucene` comprennent un préfixe autre que `damAssetLucene`.

>[!WARNING]
>
>Nous vous conseillons vivement de résoudre ce problème dès que possible, car cela entraînera l’échec des pipelines à compter de la [version d’août 2024 de Cloud Manager.](/help/release-notes/current.md)

### Les nœuds de définition d’index ne doivent pas contenir de propriétés portant le même nom. {#oakpal-index-property-name}

* **Clé** : DuplicateNameProperty
* **Type** : amélioration
* **Gravité** : mineure
* **Depuis** : version 2024.6.0

AEM Cloud Service interdit que les définitions d’index de recherche personnalisées (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) contiennent des propriétés portant le même nom.

>[!WARNING]
>
>Nous vous conseillons vivement de résoudre ce problème dès que possible, car cela entraînera l’échec des pipelines à compter de la [version d’août 2024 de Cloud Manager.](/help/release-notes/current.md)

### La personnalisation de certaines définitions d’index intégrées est interdite. {#oakpal-customizing-ootb-index}

* **Clé** : RestrictIndexCustomization
* **Type** : amélioration
* **Gravité** : mineure
* **Depuis** : version 2024.6.0

AEM Cloud Service interdit toute modification non autorisée des index intégrés suivants :

* `nodetypeLucene`
* `slingResourceResolver`
* `socialLucene`
* `appsLibsLucene`
* `authorizables`
* `pathReference`

>[!WARNING]
>
>Nous vous conseillons vivement de résoudre ce problème dès que possible, car cela entraînera l’échec des pipelines à compter de la [version d’août 2024 de Cloud Manager.](/help/release-notes/current.md)

### La configuration des générateurs de jetons dans les analyseurs doit être créée avec le nom `tokenizer`. {#oakpal-tokenizer}

* **Clé** : AnalyzerTokenizerConfigCheck
* **Type** : amélioration
* **Gravité** : mineure
* **Depuis** : version 2024.6.0

AEM Cloud Service interdit la création de générateurs de jetons dont les noms sont incorrects dans les analyseurs. Les générateurs de jetons doivent toujours être définis en tant que `tokenizer`.

### La configuration des définitions d’indexation ne doit pas contenir d’espaces. {#oakpal-indexing-definitions-spaces}

* **Clé** : PathSpacesCheck
* **Type** : amélioration
* **Gravité** : mineure
* **Depuis** : version 2024.7.0

AEM Cloud Service interdit la création de définitions d’indexation qui contiennent des propriétés avec des espaces.

### La configuration des définitions d’indexation ne doit pas contenir de propriété haystack0. {#oakpal-indexing-haystack0-property}

* **Clé** : HayStackPropertyCheck
* **Type** : amélioration
* **Gravité** : mineure
* **Depuis** : version 2024.12.0

AEM Cloud Service interdit la création de définitions d’indexation qui contiennent des propriétés haystack.

## Outil d’optimisation du Dispatcher {#dispatcher-optimization-tool-rules}

La section suivante répertorie les vérifications de l’outil d’optimisation du Dispatcher (DOT) exécutées par Cloud Manager. Suivez les liens de chaque vérification pour connaître sa définition et les détails de GitHub.

* [Jetons inattendus de la configuration du Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Citation sans correspondance de la configuration du Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Accolade manquante de la configuration du Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Accolade supplémentaire de la configuration du Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Propriété obligatoire manquante de la configuration du Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Propriété obsolète de la configuration du Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [Configuration du Dispatcher introuvable](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [Fichier Include de configuration httpd introuvable](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Généralités de la configuration du Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [Le cache de la batterie de publication du Dispatcher doit disposer de la fonction `serveStaleOnError` activée](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled).

* [Les filtres de la batterie de publication du Dispatcher doivent contenir les règles de refus par défaut de la version 6.x.x de l’archétype AEM](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [La propriété `statfileslevel` du cache de la batterie de publication du Dispatcher doit être >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2).

* [La propriété `gracePeriod` de la batterie de publication du Dispatcher doit être >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2).

* [Chaque batterie de Dispatcher doit avoir un nom unique](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [Les règles `ignoreUrlParams` du cache de la batterie de publication du Dispatcher doivent disposer d’une configuration de type Liste autorisée](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner).

* [Les filtres de la batterie de publication du Dispatcher doivent spécifier les autorisations des sélecteurs Sling selon une liste autorisée](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [Les filtres de la batterie de publication du Dispatcher doivent spécifier les modèles de suffixes Sling autorisés selon une liste autorisée](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [N’utilisez pas la directive « Require all granted » dans une section VirtualHost Directory dotée d’un chemin de répertoire racine](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
