---
title: Benutzerspezifische Regeln für Code-Qualität
description: Auf dieser Seite werden die benutzerspezifischen Code-Qualitätsregeln beschrieben, die von Cloud Manager im Rahmen von [Code-Qualitätstests] ausgeführt werden. Sie basieren auf Best Practices von AEM Engineering.
exl-id: f40e5774-c76b-4c84-9d14-8e40ee6b775b
source-git-commit: 4567581eb02c928f1493defdab667cc713fc222a
workflow-type: tm+mt
source-wordcount: '3464'
ht-degree: 48%

---

# Benutzerspezifische Regeln für Code-Qualität {#custom-code-quality-rules}

>[!CONTEXTUALHELP]
>
>id="aemcloud_nonbpa_customcodequalityrules"
>title="Custom Code Quality Rules"
>abstract="This page describes the custom code quality rules executed by Cloud Manager as part of code quality testing. They are based on best practices from AEM Engineering."

Auf dieser Seite werden die benutzerspezifischen Code-Qualitätsregeln beschrieben, die von Cloud Manager im Rahmen von [Codequalitätstests.](/help/implementing/cloud-manager/code-quality-testing.md) Sie basieren auf Best Practices von AEM Engineering.

>[!NOTE]
Die hier bereitgestellten Code-Beispiele dienen nur Veranschaulichungszwecken. Siehe SonarQube [Dokumentation zu Konzepten](https://docs.sonarqube.org/7.4/user-guide/concepts/) , um mehr über SonarQube-Konzepte und -Qualitätsregeln zu erfahren.

## SonarQube-Regeln {#sonarqube-rules}

Im folgenden Abschnitt werden die von Cloud Manager ausgeführten SonarQube-Regeln beschrieben.

### Verwenden Sie keine potenziell gefährlichen Funktionen {#do-not-use-potentially-dangerous-functions}

* **Schlüssel**: CQRules:CWE-676
* **Typ**: Sicherheitslücke
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

Die Methoden `Thread.stop()` und `Thread.interrupt()` kann schwer reproduzierbare Probleme und in einigen Fällen Sicherheitslücken verursachen. Daher sollte deren Verwendung sorgfältig überwacht und validiert werden. Im Allgemeinen ist die Nachrichtenübergabe eine sicherere Möglichkeit, ähnliche Ziele zu erreichen.

#### Nicht konformer Code {#non-compliant-code}

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

#### Konformer Code {#compliant-code}

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

### Verwenden Sie keine Formatzeichenfolgen, die möglicherweise extern kontrolliert werden {#do-not-use-format-strings-which-may-be-externally-controlled}

* **Schlüssel**: CQRules:CWE-134
* **Typ**: Sicherheitslücke
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

Durch die Verwendung einer Formatzeichenfolge aus einer externen Quelle (z. B. einem Anbfrageparameter oder benutzergenerierten Inhalten) kann ein Programm für Denial-of-Service-Angriffe anfällig werden. In einigen Situationen wird eine Formatzeichenfolge extern kontrolliert. In diesem Fall darf sie jedoch nur aus vertrauenswürdigen Quellen verwendet werden.

#### Nicht konformer Code {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP-Anforderungen sollten immer Socket- und Verbindungs-Timeouts aufweisen {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Schlüssel**: CQRules:ConnectionTimeoutMechanism
* **Typ**: Fehler
* **Schweregrad**: Kritisch
* **Seit**: Version 2018.6.0

Beim Ausführen von HTTP-Anfragen aus einem AEM-Programm muss unbedingt sichergestellt sein, dass korrekte Zeitüberschreitungswerte konfiguriert werden, um unnötige Thread-Nutzung zu vermeiden. Leider ist das Standardverhalten des standardmäßigen HTTP-Clients (`java.net.HttpUrlConnection`) und der häufig verwendete Apache HTTP Components-Client darf niemals eine Zeitüberschreitung bewirken. Daher müssen Timeouts explizit festgelegt werden. Als Best Practice gilt, diese Zeitüberschreitungen bei maximal 60 Sekunden zu definieren.

#### Nicht konformer Code {#non-compliant-code-2}

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

#### Konformer Code {#compliant-code-1}

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

### ResourceResolver-Objekte sollten immer geschlossen werden {#resourceresolver-objects-should-always-be-closed}

* **Schlüssel**: CQRules:CQBP-72
* **Typ**: Code Smell
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

`ResourceResolver` Objekte, die von der `ResourceResolverFactory` Systemressourcen verbrauchen. Obwohl es Maßnahmen gibt, um diese Ressourcen zurückzufordern, wenn ein `ResourceResolver` nicht mehr verwendet wird, ist es effizienter, alle geöffneten `ResourceResolver` -Objekte durch Aufruf der `close()` -Methode.

Ein relativ häufiges Missverständnis ist, dass `ResourceResolver` Objekte, die mit einer vorhandenen JCR-Sitzung erstellt wurden, sollten nicht explizit geschlossen werden. Andernfalls wird die zugrunde liegende JCR-Sitzung geschlossen. Das ist nicht der Fall. Unabhängig davon, wie eine `ResourceResolver` geöffnet ist, sollte sie geschlossen werden, wenn sie nicht mehr verwendet wird. Seit `ResourceResolver` implementiert die `Closeable` -Schnittstelle, ist es auch möglich, die `try-with-resources` -Syntax anstatt explizit aufzurufen `close()`.

#### Nicht konformer Code {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Konformer Code {#compliant-code-2}

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

### Verwenden Sie keine Sling Servlet-Pfade, um Servlets zu registrieren {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Schlüssel**: CQRules:CQBP-75
* **Typ**: Code Smell
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

Wie in der [Sling-Dokumentation](http://sling.apache.org/documentation/the-sling-engine/servlets.html) beschrieben, sollten Servlets nicht über Pfade verknüpft werden. Pfadgebundene Servlets können keine standardmäßigen JCR-Zugriffssteuerungselemente verwenden, sodass besonders strenge Sicherheitsmaßnahmen erforderlich sind. Statt pfadgebundene Servlets zu verwenden, wird empfohlen, Knoten im Repository zu erstellen und Servlets nach Ressourcentyp zu registrieren.

#### Nicht konformer Code {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Ausnahmefehler sollten protokolliert oder ausgegeben werden, nicht beide {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Schlüssel**: CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Im Allgemeinen sollte eine Ausnahme genau einmal protokolliert werden. Die mehrfache Protokollierung von Ausnahmen kann verwirren, da unklar ist, wie oft eine Ausnahme aufgetreten ist. Dies wird vor allem dadurch verursacht, dass eine erfasste Ausnahme sowohl protokolliert als auch ausgegeben wird.

#### Nicht konformer Code {#non-compliant-code-6}

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

#### Konformer Code {#compliant-code-3}

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

### Vermeiden Sie Protokollanweisungen, die unmittelbar auf eine Throw-Anweisung folgen {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Schlüssel**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Ein weiteres gängiges Muster, das vermieden werden sollte, ist die Protokollierung einer Nachricht, direkt gefolgt von der Auslösung einer Ausnahme. Dadurch erscheint die Ausnahmemeldung in Protokolldateien meist doppelt.

#### Nicht konformer Code {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Konformer Code {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Vermeiden Sie die Protokollierung bei INFO bei der Verarbeitung von GET- oder HEAD-Anfragen {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Schlüssel**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **Typ**: Code Smell
* **Schweregrad**: Gering

Im Allgemeinen sollten mit der Protokollierungsstufe INFO wichtige Aktionen abgegrenzt werden. Standardmäßig ist AEM so konfiguriert, dass auf der INFO-Ebene oder höher protokolliert wird. GET- und HEAD-Methoden sollten nur schreibgeschützte Vorgänge sein und stellen daher keine wichtigen Aktionen dar. Die Protokollierung auf INFO-Ebene als Antwort auf GET- oder HEAD-Anfragen füllt das Protokoll wahrscheinlich mit erheblichen Mengen überflüssiger Informationen, sodass es schwieriger wird, nützliche Informationen in Protokolldateien zu finden. Bei der Verarbeitung von GET- oder HEAD-Anfragen sollte die Protokollierung entweder bei einem Fehler auf WARN- oder ERROR-Ebene erfolgen oder auf DEBUG- oder TRACE-Ebene, wenn eine tiefgehendere Fehlerbehebung hilfreich wäre.

>[!NOTE]
Dies gilt nicht für `access.log`-type-Protokollierung für jede Anfrage.

#### Nicht konformer Code {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Konformer Code {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### Verwenden Sie nicht Exception.getMessage() als ersten Parameter einer Protokollierungsanweisung {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Schlüssel**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Als Best Practice sollten Protokollmeldungen kontextbezogene Informationen darüber enthalten, wo eine Programmausnahme aufgetreten ist. Während der Kontext auch mit Stacktraces bestimmt werden kann, ist die Protokollmeldung meist besser lesbar und verständlicher. Daher ist es bei der Protokollierung einer Ausnahme nicht empfehlenswert, die Ausnahmemeldung als Protokollmeldung zu verwenden. Die Ausnahmemeldung enthält Informationen zu Fehlern, während die Protokollmeldung verwendet werden sollte, um einem Protokollleser mitzuteilen, was die Anwendung gerade tat, als die Ausnahme auftrat. Die Ausnahmemeldung wird weiterhin protokolliert. Durch die Angabe Ihrer eigenen Nachricht werden die Logs einfach verständlicher.

#### Nicht konformer Code {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Konformer Code {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Die Protokollierung in Catch-Blöcken sollte auf WARN- oder ERROR-Ebene erfolgen {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **Schlüssel**: CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Wie der schon Name sagt, sollten Java-Ausnahmen immer in außergewöhnlichen Fällen verwendet werden. Wenn eine Ausnahme erfasst wird, muss daher sichergestellt werden, dass Protokollmeldungen auf der entsprechenden Ebene protokolliert werden, entweder WARN oder ERROR. damit diese Meldungen in den Protokollen korrekt angezeigt werden.

#### Nicht konformer Code {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Konformer Code {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Drucken Sie keine Stack-Traces in der Konsole {#do-not-print-stack-traces-to-the-console}

* **Schlüssel**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Wie bereits erwähnt, ist Kontext beim Verständnis von Protokollmeldungen äußerst wichtig. Verwenden `Exception.printStackTrace()` führt dazu, dass nur die Stacktrace an den Standard-Fehlerstream ausgegeben wird, wodurch der gesamte Kontext verloren geht. Wenn in einer Multi-Thread-Anwendung wie AEM mehrere Ausnahmen parallel mit dieser Methode gedruckt werden, können sich ihre Stacktraces überschneiden, was erhebliche Verwirrung verursacht. Ausnahmen sollten daher nur über das Protokollierungs-Framework protokolliert werden.

#### Nicht konformer Code {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### Konformer Code {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Ausgabe nicht in Standardausgabe oder Standardfehler {#do-not-output-to-standard-output-or-standard-error}

* **Schlüssel**: CQRules:CQBP-44—LogLevelConsolePrinters
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Die Anmeldung in AEM sollte immer über das Protokollierungs-Framework (SLF4J) erfolgen. Durch die direkte Ausgabe an Standardausgabe- oder Standardfehler-Ströme gehen strukturelle und kontextbezogene Informationen verloren, die vom Protokollings-Framework bereitgestellt werden. Außerdem kann diese Vorgehensweise in einigen Fällen zu Leistungseinbußen führen.

#### Nicht konformer Code {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### Konformer Code {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Vermeiden Sie hartcodierte /apps- und /libs-Pfade {#avoid-hardcoded-apps-and-libs-paths}

* **Schlüssel**: CQRules:CQBP-71
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Im Allgemeinen beginnen Pfade mit `/libs` und `/apps` sollten nicht fest codiert werden, da die Pfade, auf die sie verweisen, am häufigsten als Pfade relativ zum Sling-Suchpfad gespeichert werden, der auf `/libs,/apps` Standardmäßig. Durch den absoluten Pfad können geringfügige Fehler entstehen, die erst später im Projektlebenszyklus deutlich werden.

#### Nicht konformer Code {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Konformer Code {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### Sling-Planung sollte nicht verwendet werden {#sonarqube-sling-scheduler}

* **Schlüssel**: CQRules:AMSCORE-554
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Die Sling-Planung darf nicht für Aufgaben verwendet werden, die eine garantierte Ausführung erfordern. Über Sling geplante Aufträge garantieren die Ausführung und eignen sich besser für Umgebungen mit und ohne Cluster.

Weitere Informationen zum Umgang mit Sling-Aufträgen in einer Umgebung mit Clustern finden Sie unter [Apache Sling Eventing und Job Handling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html).

### AEM veraltete APIs sollten nicht verwendet werden {#sonarqube-aem-deprecated}

* **Schlüssel**: AMSCORE-553
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Die AEM-API-Oberfläche wird ständig überarbeitet, um APIs zu identifizieren, von deren Verwendung abgeraten wird und die daher als veraltet gelten.

In vielen Fällen werden diese APIs mithilfe des standardmäßigen Java-Codes nicht mehr unterstützt `@Deprecated` -Anmerkung und als solche, wie durch `squid:CallToDeprecatedMethod`.

Es gibt jedoch Fälle, in denen eine API im Kontext von AEM veraltet ist, in anderen Kontexten jedoch nicht. Diese Regel identifiziert diese zweite Klasse.


## OakPAL-Inhaltsregeln {#oakpal-rules}

Im folgenden Abschnitt werden die von Cloud Manager ausgeführten OakPAL-Prüfungen beschrieben.

>[!NOTE]
OakPAL ist ein Framework, das Inhaltspakete mithilfe eines eigenständigen Oak-Repositorys validiert. Es wurde von einem AEM Partner und Gewinner des AEM Rockstar North America Awards 2019 entwickelt.

### Produkt-APIs, die mit @ProviderType kommentiert sind, sollten von Kunden nicht implementiert oder erweitert werden {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Schlüssel**: CQBP-84
* **Typ**: Fehler
* **Schweregrad**: Kritisch
* **Seit**: Version 2018.7.0

Die AEM-API enthält Java-Schnittstellen und -Klassen, die durch benutzerdefinierten Code lediglich verwendet, aber nicht implementiert werden sollen. Zum Beispiel ist die Schnittstelle `com.day.cq.wcm.api.Page` nur für die Implementierung durch AEM ausgelegt.

Wenn zu diesen Schnittstellen neue Methoden hinzugefügt werden, wirken sich diese zusätzlichen Methoden nicht auf den vorhandenen Code aus, der diese Schnittstellen verwendet. Daher wird das Hinzufügen neuer Methoden zu diesen Schnittstellen als abwärtskompatibel betrachtet. Wenn jedoch benutzerdefinierter Code eine dieser Schnittstellen implementiert, führt dieser benutzerspezifische Code ein Abwärtskompatibilitätsrisiko für den Kunden ein.

Schnittstellen und Klassen, die nur von AEM implementiert werden sollen, werden mit `org.osgi.annotation.versioning.ProviderType` oder in einigen Fällen eine ähnliche Legacy-Anmerkung `aQute.bnd.annotation.ProviderType`. Diese Regel identifiziert die Fälle, in denen eine solche Schnittstelle implementiert oder eine Klasse durch benutzerdefinierten Code erweitert wird.

#### Nicht konformer Code {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Benutzerdefinierte Lucene-Oak-Indizes müssen über eine Tika-Konfiguration verfügen. {#oakpal-indextikanode}

* **Schlüssel**: IndexTikaNode
* **Typ**: Fehler
* **Schweregrad**: Blocker
* **Seit**: 2021.8.0

Mehrere vordefinierte AEM Oak-Indizes enthalten eine Tika-Konfiguration und Anpassungen dieser Indizes müssen eine Tika-Konfiguration enthalten. Diese Regel überprüft auf Anpassungen der Indizes `damAssetLucene`, `lucene` und `graphqlConfig` und löst ein Problem aus, wenn entweder der Knoten `tika` fehlt oder wenn im Knoten `tika` ein untergeordneter Knoten mit dem Namen `config.xml` fehlt.

Siehe Abschnitt [Indizierungsdokumentation](/help/operations/indexing.md#preparing-the-new-index-definition) Weitere Informationen zum Anpassen von Indexdefinitionen.

#### Nicht konformer Code {#non-compliant-code-indextikanode}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
```

#### Konformer Code {#compliant-code-indextikanode}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Benutzerdefinierte Lucene-Oak-Indizes dürfen nicht synchron sein {#oakpal-indexasync}

* **Schlüssel**: IndexAsyncProperty
* **Typ**: Fehler
* **Schweregrad**: Blocker
* **Seit**: 2021.8.0

Oak-Indizes des Typs `lucene` muss immer asynchron indiziert sein. Andernfalls kann es zu einer Instabilität des Systems kommen. Weitere Informationen zur Struktur von Lucene-Indizes finden Sie in der [Dokumentation zu Oak.](https://jackrabbit.apache.org/oak/docs/query/lucene.html#index-definition)

#### Nicht konformer Code {#non-compliant-code-indexasync}

```text
+ oak:index
    + damAssetLucene-1-custom
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - type: lucene
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

#### Konformer Code {#compliant-code-indexasync}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Benutzerdefinierte DAM Asset Lucene Oak-Indizes sind ordnungsgemäß strukturiert  {#oakpal-damAssetLucene-sanity-check}

* **Schlüssel**: IndexDamAssetLucene
* **Typ**: Fehler
* **Schweregrad**: Blocker
* **Seit**: 2021.6.0

Damit die Asset-Suche in AEM Assets ordnungsgemäß funktioniert, müssen die Anpassungen des `damAssetLucene`-Oak-Index einem Satz von Richtlinien entsprechen, die für diesen Index spezifisch sind. Diese Regel überprüft, ob die Indexdefinition eine Eigenschaft mit mehreren Werten mit dem Namen `tags` , der den Wert enthält `visualSimilaritySearch`.

#### Nicht konformer Code {#non-compliant-code-damAssetLucene}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - type: lucene
      + tika
        + config.xml
```

#### Konformer Code {#compliant-code-damAssetLucene}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Kundenpakete sollten keine Knoten unter /libs erstellen oder ändern {#oakpal-customer-package}

* **Schlüssel**: BannedPath
* **Typ**: Fehler
* **Schweregrad**: Kritisch
* **Seit**: Version 2019.6.0

Es ist seit langem eine bewährte Methode, dass die `/libs` Die Inhaltsstruktur im AEM Content Repository sollte von Kunden als schreibgeschützt betrachtet werden. Ändern von Knoten und Eigenschaften unter `/libs` verursacht ein erhebliches Risiko für größere und kleinere Aktualisierungen. Änderungen an `/libs` sollten nur durch Adobe über offizielle Kanäle erfolgen.

### Pakete dürfen keine doppelten OSGi-Konfigurationen enthalten {#oakpal-package-osgi}

* **Schlüssel**: DuplicateOsgiConfigurations
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2019.6.0

Ein häufig auftretendes Problem bei komplexen Projekten besteht darin, dass dieselbe OSGi-Komponente mehrmals konfiguriert ist. Dadurch entsteht eine Unklarheit darüber, welche Konfiguration anwendbar sein wird. Diese Regel ist &quot;runmode-basiert&quot;, da sie nur Probleme erkennt, bei denen dieselbe Komponente mehrmals im selben Ausführungsmodus oder in einer Kombination von Ausführungsmodi konfiguriert ist.

>[!NOTE]
Diese Regel führt zu Problemen, wenn dieselbe Konfiguration unter demselben Pfad in mehreren Paketen definiert ist, einschließlich der Fälle, in denen dasselbe Paket in der Gesamtliste der erstellten Pakete dupliziert ist.
Wenn der Build zum Beispiel Pakete mit den Namen `com.myco:com.myco.ui.apps` und `com.myco:com.myco.all` erstellt, wobei `com.myco:com.myco.all` `com.myco:com.myco.ui.apps` einbettet, werden alle Konfigurationen innerhalb von `com.myco:com.myco.ui.apps` als Duplikat gemeldet.
Dies ist im Allgemeinen der Fall, dass die [Richtlinien für die Inhaltspaketstruktur.](/help/implementing/developing/introduction/aem-project-content-package-structure.md). In diesem speziellen Beispiel wird das -Paket `com.myco:com.myco.ui.apps` fehlt die `<cloudManagerTarget>none</cloudManagerTarget>` -Eigenschaft.

#### Nicht konformer Code {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Konformer Code {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Konfigurationen und Installationsordner dürfen nur OSGi-Knoten enthalten {#oakpal-config-install}

* **Schlüssel**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2019.6.0

Aus Sicherheitsgründen enthalten Pfade, die `/config/` und `/install/` sind nur von Administratoren in AEM lesbar und sollten nur für OSGi-Konfigurationen und OSGi-Bundles verwendet werden. Das Platzieren anderer Inhaltstypen in Pfade mit diesen Segmenten führt dazu, dass sich das Programm abhängig davon anders verhält, ob sie von Administratoren- oder Nicht-Administratoren verwendet wird.

Ein häufig auftretendes Problem ist die Verwendung von Knoten mit der Bezeichnung `config` in Komponentendialogfeldern oder beim Angeben der Rich-Text-Editor-Konfiguration für die Inline-Bearbeitung. Um dies zu beheben, sollte der fehlerhafte Knoten in einen kompatiblen Namen umbenannt werden. Nutzen Sie bei der Rich-Text-Editor-Konfiguration die Eigenschaft `configPath` im Knoten `cq:inplaceEditing`, um den neuen Speicherort anzugeben.

#### Nicht konformer Code {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Konformer Code {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### Pakete sollten nicht überlappen {#oakpal-no-overlap}

* **Schlüssel**: PackageOverlaps
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2019.6.0

Ähnlich wie bei [Pakete sollten keine doppelte OSGi-Konfigurationsregel enthalten.](#oakpal-package-osgi) Dies ist ein häufiges Problem bei komplexen Projekten, bei denen der gleiche Knotenpfad von mehreren separaten Inhaltspaketen in geschrieben wird. Mit Inhaltspaketabhängigkeiten kann zwar ein konsistentes Ergebnis sichergestellt werden, Überlappungen sollten aber dennoch von vorneherein vermieden werden.

### Der standardmäßige Authoring-Modus sollte nicht die klassische Benutzeroberfläche sein {#oakpal-default-authoring}

* **Schlüssel**: ClassicUIAuthoringMode
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Die OSGi-Konfiguration `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` definiert den standardmäßigen Authoring-Modus in AEM. weil [Die klassische Benutzeroberfläche wird seit AEM 6.4 nicht mehr unterstützt.](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html) Es tritt jetzt ein Problem auf, wenn der standardmäßige Authoring-Modus für die klassische Benutzeroberfläche konfiguriert ist.

### Komponenten mit Dialogfeldern sollten Dialogfelder für die Touch-Benutzeroberfläche aufweisen {#oakpal-components-dialogs}

* **Schlüssel**: ComponentWithOnlyClassicUIDialog
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

AEM Komponenten mit einem Dialogfeld für die klassische Benutzeroberfläche sollten immer über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche verfügen, um ein optimales Authoring-Erlebnis zu bieten und mit dem Cloud Service-Bereitstellungsmodell kompatibel zu sein, bei dem die klassische Benutzeroberfläche nicht unterstützt wird. Diese Regel überprüft die folgenden Szenarien:

* Eine Komponente mit einem Dialogfeld für die klassische Benutzeroberfläche (d. h. eine `dialog` untergeordneter Knoten) muss über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche verfügen (d. h. über eine `cq:dialog` untergeordneten Knoten).
* Eine Komponente mit einem Design-Dialogfeld für die klassische Benutzeroberfläche (d. h. eine `design_dialog` -Knoten) muss über ein entsprechendes Design-Dialogfeld für die Touch-Benutzeroberfläche verfügen (d. h. über eine `cq:design_dialog` untergeordneten Knoten).
* Eine Komponente mit einem Dialogfeld für die klassische Benutzeroberfläche und einem Design-Dialogfeld für die klassische Benutzeroberfläche muss sowohl über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche als auch über ein entsprechendes Design-Dialogfeld für die Touch-Benutzeroberfläche verfügen.

Die Dokumentation zu den AEM-Modernisierungs-Tools enthält Dokumentation und Tools zum Konvertieren von Komponenten aus der klassischen Benutzeroberfläche in die Touch-Benutzeroberfläche. Siehe [Dokumentation zu AEM Modernisierungs-Tools](https://opensource.adobe.com/aem-modernize-tools/pages/tools.html) für weitere Details.

### Pakete sollten keinen veränderlichen und unveränderlichen Inhalt mischen {#oakpal-packages-immutable}

* **Schlüssel**: ImmutableMutableMixedPackage
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Um mit dem Cloud Service-Bereitstellungsmodell kompatibel zu sein, müssen einzelne Inhaltspakete entweder Inhalte für die unveränderlichen Bereiche des Repositorys enthalten (d. h. `/apps` und `/libs`) oder den veränderlichen Bereich (d. h. alles, was nicht in `/apps` oder `/libs`), aber nicht beides. Beispielsweise ist ein Paket, das beide `/apps/myco/components/text and /etc/clientlibs/myco` enthält, nicht mit Cloud Service kompatibel und führt dazu, dass ein Problem gemeldet wird.

>[!NOTE]
Die Regel [Kundenpakete sollten keine Knoten unter /libs erstellen oder ändern](#oakpal-customer-package) gilt immer.

Weitere Informationen finden Sie unter [AEM-Projektstruktur](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

### Rückwärtsreplikations-Agenten sollten nicht verwendet werden {#oakpal-reverse-replication}

* **Schlüssel**: ReverseReplication
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

In Cloud Service-Implementierungen ist keine Unterstützung für die Rückwärtsreplikation verfügbar, wie im AEM as a Cloud Service [Versionshinweise.](/help/release-notes/aem-cloud-changes.md#replication-agents)

Kunden, die die Rückwärtsreplikation verwenden, sollten sich für alternative Lösungen an Adobe wenden.

### Ressourcen, die in Proxy-aktivierten Client-Bibliotheken enthalten sind, sollten sich in einem Ordner befinden, der Ressourcen heißt {#oakpal-resources-proxy}

* **Schlüssel**: ClientlibProxyResource
* **Typ**: Fehler
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Client-Bibliotheken können statische Ressourcen wie Bilder und Schriftarten enthalten. Wie im Dokument beschrieben [Verwendung von Präprozessoren,](/help/implementing/developing/introduction/clientlibs.md#using-preprocessors) Bei Verwendung von Proxyclient-Bibliotheken müssen diese statischen Ressourcen in einem untergeordneten Ordner mit dem Namen `resources` um effektiv auf die Veröffentlichungsinstanzen verwiesen zu werden.

#### Nicht konformer Code {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### Konformer Code {#compliant-proxy-enabled}

```tet
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Verwendung inkompatibler Workflow-Prozesse in Cloud Service {#oakpal-usage-cloud-service}

* **Schlüssel**: CloudServiceIncompatibleWorkflowProcess
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2021.2.0

Mit der Umstellung auf Asset-Microservices für die Asset-Verarbeitung auf AEM as a Cloud Service sind mehrere Workflow-Prozesse, die in On-Premise- und AMS-Versionen von AEM verwendet wurden, entweder nicht mehr unterstützt oder nicht mehr erforderlich.

Das Migrationstool im [as a Cloud Service GitHub-Repository für AEM Assets](https://github.com/adobe/aem-cloud-migration) kann verwendet werden, um Workflow-Modelle während der Migration auf AEM as a Cloud Service zu aktualisieren.

### Die Verwendung statischer Vorlagen wird zugunsten bearbeitbarer Vorlagen empfohlen. {#oakpal-static-template}

* **Schlüssel**: StaticTemplateUsage
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Die Verwendung von statischen Vorlagen war in AEM-Projekten stets weit verbreitet. Editierbare Vorlagen werden jedoch dringend empfohlen, da sie die größte Flexibilität bieten und zusätzliche Funktionen unterstützen, die in statischen Vorlagen nicht vorhanden sind. Weitere Informationen finden Sie im Dokument . [Seitenvorlagen.](/help/implementing/developing/components/templates.md)

Die Migration von statischen zu bearbeitbaren Vorlagen kann mithilfe der [AEM Modernisierungs-Tools.](https://opensource.adobe.com/aem-modernize-tools/)

### Die Verwendung älterer Foundation-Komponenten wird nicht empfohlen {#oakpal-usage-legacy}

* **Schlüssel**: LegacyFoundationComponentUsage
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Die veralteten Foundation-Komponenten (d. h. Komponenten unter `/libs/foundation`) wurden [für mehrere AEM veraltet](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html) zugunsten der Kernkomponenten. Die Verwendung der Foundation-Komponenten als Grundlage für benutzerdefinierte Komponenten (ob durch Überlagerung oder Vererbung) wird empfohlen und sollte in die entsprechenden Kernkomponenten konvertiert werden.

Diese Konvertierung kann durch die [AEM Modernisierungs-Tools.](https://opensource.adobe.com/aem-modernize-tools/)

### Nur unterstützte Runmode-Namen und -Reihenfolge sollten verwendet werden {#oakpal-supported-runmodes}

* **Schlüssel**: SupportedRunmode
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM as a Cloud Service erzwingt eine strikte Benennungsrichtlinie für Ausführungsmodusnamen und eine strikte Reihenfolge für diese Ausführungsmodi. Die Liste der unterstützten Ausführungsmodi finden Sie im Dokument . [Bereitstellen in AEM as a Cloud Service](/help/implementing/deploying/overview.md#runmodes) und jede Abweichung davon wird als Problem identifiziert.

### Benutzerdefinierte Suchindex-Definitionsknoten müssen direkte untergeordnete Elemente von /oak:index sein. {#oakpal-custom-search}

* **Schlüssel**: OakIndexLocation
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM as a Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) direkt untergeordnete Knoten von `/oak:index`. Indizes an anderen Orten müssen verschoben werden, um mit AEM as a Cloud Service kompatibel zu sein. Weitere Informationen zu Suchindizes finden Sie im Dokument . [Inhaltssuche und -indizierung.](/help/operations/indexing.md)

### Benutzerdefinierte Suchindex-Definitionsknoten müssen eine compatVersion von 2 haben. {#oakpal-custom-search-compatVersion}

* **Schlüssel**: IndexCompatVersion
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM as a Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) muss die Variable `compatVersion` Eigenschaft auf `2`. Andere Werte werden von AEM as a Cloud Service nicht unterstützt. Weitere Informationen zu Suchindizes finden Sie unter [Inhaltssuche und indizierung.](/help/operations/indexing.md)

### Abhängige Knoten von benutzerdefinierten Suchindex-Definitionsknoten müssen vom Typ nt:unstructured sein. {#oakpal-descendent-nodes}

* **Schlüssel**: IndexDescendantNodeType
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Schwer behebbare Probleme können auftreten, wenn ein Knoten mit einer benutzerdefinierten Suchindex-Definition ungeordnete untergeordnete Knoten enthält. Um diese Situation zu vermeiden, wird empfohlen, dass alle untergeordneten Knoten eines `oak:QueryIndexDefinition` node be of type `nt:unstructured`.

### Benutzerdefinierte Suchindex-Definitionsknoten müssen einen untergeordneten Knoten namens indexRules enthalten, der untergeordnete Elemente enthält {#oakpal-custom-search-index}

* **Schlüssel**: IndexRulesNode
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Ein ordnungsgemäß definierter benutzerdefinierter Suchindex-Definitionsknoten muss einen untergeordneten Knoten mit dem Namen `indexRules` die wiederum mindestens ein Kind haben müssen. Weitere Informationen finden Sie im [Oak-Dokumentation.](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

### Benutzerdefinierte Suchindex-Definitionsknoten müssen Namenskonventionen folgen {#oakpal-custom-search-definitions}

* **Schlüssel**: IndexName
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM as a Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) muss nach einem bestimmten Muster benannt werden, das im Dokument beschrieben wird [Inhaltssuche und -indizierung.](/help/operations/indexing.md)

### Benutzerdefinierte Suchindex-Definitionsknoten müssen den Index-Typ-Lucene verwenden  {#oakpal-index-type-lucene}

* **Schlüssel**: IndexType
* **Typ**: Fehler
* **Schweregrad**: Blocker
* **Seit**: Version 2021.2.0 (Änderung von Typ und Schweregrad in 2021.8.0)

AEM as a Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) haben eine `type` -Eigenschaft mit dem Wert `lucene`. Die Indizierung mit älteren Indextypen muss vor der Migration auf AEM as a Cloud Service aktualisiert werden. Siehe Dokument [Inhaltssuche und -indizierung](/help/operations/indexing.md#how-to-use) für weitere Informationen.

### Benutzerdefinierte Suchindex-Definitionsknoten dürfen keine Eigenschaft mit dem Namen Seed enthalten {#oakpal-property-name-seed}

* **Schlüssel**: IndexSeedProperty
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM as a Cloud Service verbietet benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`), die eine Eigenschaft namens `seed`. Die Indizierung mit dieser Eigenschaft muss vor der Migration auf AEM as a Cloud Service aktualisiert werden. Siehe Dokument . [Inhaltssuche und -indizierung](/help/operations/indexing.md#how-to-use) für weitere Informationen.

### Benutzerdefinierte Suchindex-Definitionsknoten dürfen keine Eigenschaft namens reindex enthalten. {#oakpal-reindex-property}

* **Schlüssel**: IndexReindexProperty
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM as a Cloud Service verbietet benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`), die eine Eigenschaft namens `reindex`. Die Indizierung mit dieser Eigenschaft muss vor der Migration auf AEM as a Cloud Service aktualisiert werden. Siehe Dokument . [Inhaltssuche und -indizierung](/help/operations/indexing.md#how-to-use) für weitere Informationen.
