---
title: Qualitätsregeln für benutzerspezifischen Code
description: Diese Seite beschreibt die Qualitätsregeln für benutzerspezifischen Code, die von Cloud Manager im Rahmen der Code-Qualitätstests ausgeführt werden. Sie basieren auf Best Practices von Adobe Experience Manager Engineering.
exl-id: f40e5774-c76b-4c84-9d14-8e40ee6b775b
source-git-commit: 2935338b847f7e852dfd31c93a61e737e8a3ec80
workflow-type: tm+mt
source-wordcount: '3485'
ht-degree: 46%

---

# Benutzerspezifische Code-Qualitätsregeln {#custom-code-quality-rules}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_customcodequalityrules"
>title="Qualitätsregeln für benutzerspezifischen Code"
>abstract="Diese Seite beschreibt die Qualitätsregeln für benutzerspezifischen Code, die von Cloud Manager im Rahmen der Code-Qualitätstests ausgeführt werden. Sie basieren auf Best Practices von Adobe Experience Manager Engineering."

Diese Seite beschreibt die Qualitätsregeln für benutzerspezifischen Code, die von Cloud Manager im Rahmen der [Code-Qualitätstests](/help/implementing/cloud-manager/code-quality-testing.md) ausgeführt werden. Sie basieren auf Best Practices des Experience Manager Engineering.

>[!NOTE]
>
>Die hier bereitgestellten Code-Beispiele dienen nur Veranschaulichungszwecken. In der [Dokumentation zu SonarQube-Konzepten](https://docs.sonarqube.org/latest/) finden Sie Informationen zu SonarQube-Konzepten und Qualitätsregeln.

## SonarQube-Regeln {#sonarqube-rules}

Im folgenden Abschnitt werden die SonarQube-Regeln beschrieben, die von Cloud Manager ausgeführt werden.

### Verwenden Sie keine potenziell gefährlichen Funktionen {#do-not-use-potentially-dangerous-functions}

* **Schlüssel**: CQRules:CWE-676
* **Typ**: Sicherheitslücke
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

Die Methoden `Thread.stop()` und `Thread.interrupt()` kann schwer reproduzierbare Probleme und manchmal Sicherheitslücken verursachen. Daher sollte deren Verwendung sorgfältig überwacht und validiert werden. Im Allgemeinen ist die Nachrichtenübergabe eine sicherere Möglichkeit, ähnliche Ziele zu erreichen.

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

### Verwenden Sie keine Formatzeichenfolgen, die extern gesteuert werden können {#do-not-use-format-strings-which-may-be-externally-controlled}

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

### HTTP-Anfragen sollten immer Zeitüberschreitungswerte für Sockets und Verbindungen enthalten {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Schlüssel**: CQRules:ConnectionTimeoutMechanism
* **Typ**: Fehler
* **Schweregrad**: Kritisch
* **Seit**: Version 2018.6.0

Beim Ausführen von HTTP-Anfragen aus einer Experience Manager-Anwendung muss sichergestellt werden, dass ordnungsgemäße Timeouts konfiguriert sind, um unnötigen Thread-Verbrauch zu vermeiden. Leider ist das Standardverhalten des Standard-HTTP-Clients (`java.net.HttpUrlConnection`) und der häufig verwendete Apache HTTP Components-Client eine Zeitüberschreitung verhindert, sodass Timeouts explizit festgelegt werden müssen. Als Best Practice gilt, diese Zeitüberschreitungen bei maximal 60 Sekunden zu definieren.

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

### ResourceResolver-Objekte immer schließen {#resourceresolver-objects-should-always-be-closed}

* **Schlüssel**: CQRules:CQBP-72
* **Typ**: Code Smell
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

`ResourceResolver`-Objekte, die aus `ResourceResolverFactory` abgerufen werden, verbrauchen Systemressourcen. Obwohl es Möglichkeiten gibt, diese Ressourcen freizugeben, wenn ein `ResourceResolver` nicht mehr verwendet wird, ist es effizienter, alle offenen `ResourceResolver`-Objekte explizit durch Aufruf der Methode `close()` zu schließen.

Ein relativ häufiges Missverständnis ist, dass `ResourceResolver` -Objekte, die mit einer vorhandenen JCR-Sitzung erstellt wurden, sollten nicht explizit geschlossen werden oder die zugrunde liegende JCR-Sitzung dadurch geschlossen wird. Dies ist nicht der Fall. Gleichgültig, wie ein `ResourceResolver` geöffnet wird, sollte es geschlossen werden, wenn es nicht mehr benötigt wird. Da `ResourceResolver` die `Closeable`-Schnittstelle implementiert, kann auch die Syntax `try-with-resources` statt eines expliziten Aufrufs von `close()` verwendet werden.

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

### Verwenden Sie keine Sling-Servlet-Pfade zum Registrieren von Servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Schlüssel**: CQRules:CQBP-75
* **Typ**: Code Smell
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

Wie in der [Sling-Dokumentation](https://sling.apache.org/documentation/the-sling-engine/servlets.html) beschrieben, sollten Servlets nicht über Pfade verknüpft werden. Pfadgebundene Servlets können keine standardmäßigen JCR-Zugriffssteuerungselemente verwenden, sodass besonders strenge Sicherheitsmaßnahmen erforderlich sind. Statt pfadgebundene Servlets zu verwenden, wird empfohlen, Knoten im Repository zu erstellen und Servlets nach Ressourcentyp zu registrieren.

#### Nicht konformer Code {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Ausnahmefehler sollten protokolliert oder ausgegeben werden, nicht beides {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

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

### Vermeiden Sie Protokollanweisungen, die unmittelbar von einer Throw-Anweisung gefolgt werden {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Schlüssel**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Ein weiteres gängiges Muster, das vermieden werden sollte, ist die Protokollierung einer Nachricht, direkt gefolgt von der Auslösung einer Ausnahme. Diese Vorgehensweise weist im Allgemeinen darauf hin, dass die Ausnahmemeldung in Protokolldateien dupliziert wird.

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

### Vermeiden Sie beim Verarbeiten von GET- oder HEAD-Anfragen die Protokollierung bei INFO {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Schlüssel**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **Typ**: Code Smell
* **Schweregrad**: Gering

Im Allgemeinen sollte die INFO-Protokollebene verwendet werden, um wichtige Aktionen abzugrenzen. Standardmäßig ist Experience Manager so konfiguriert, dass die Protokollierung auf INFO-Ebene oder höher erfolgt. GET- und HEAD-Methoden sollten nur schreibgeschützte Vorgänge sein und stellen daher keine wichtigen Aktionen dar. Die Protokollierung auf INFO-Ebene als Reaktion auf GET- oder HEAD-Anfragen führt wahrscheinlich zu beträchtlichem Protokollgeräusch, wodurch die Identifizierung nützlicher Informationen in Protokolldateien erschwert wird. Bei der Verarbeitung von GET- oder HEAD-Anfragen sollte die Protokollierung entweder bei einem Fehler auf WARN- oder ERROR-Ebene erfolgen oder auf DEBUG- oder TRACE-Ebene, wenn eine tiefgehendere Fehlerbehebung hilfreich wäre.

>[!NOTE]
>
>Dies gilt nicht für `access.log`-type-Protokollierung für jede Anfrage.

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

### Verwenden Sie nicht Exception.getMessage() als ersten Parameter einer Protokollanweisung {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Schlüssel**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Als Best Practice sollten Protokollmeldungen kontextbezogene Informationen darüber enthalten, wo eine Programmausnahme aufgetreten ist. Während der Kontext auch mithilfe von Stacktraces bestimmt werden kann, ist die Protokollmeldung im Allgemeinen leichter zu lesen und zu verstehen. Daher ist es bei der Protokollierung einer Ausnahme nicht empfehlenswert, die Ausnahmemeldung als Protokollmeldung zu verwenden. Die Ausnahmemeldung enthält Informationen zu Fehlern, während die Protokollmeldung verwendet werden sollte, um einem Protokollleser mitzuteilen, was die Anwendung getan hat, als die Ausnahme aufgetreten ist. Die Ausnahmemeldung wird weiterhin protokolliert. Durch Angabe Ihrer eigenen Nachricht sind die Protokolle leichter verständlich.

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

Wie der Name schon sagt, sollten Java™-Ausnahmen immer in Ausnahmefällen verwendet werden. Wenn eine Ausnahme erfasst wird, muss daher sichergestellt sein, dass Protokollmeldungen auf der entsprechenden Ebene – WARN oder ERROR – protokolliert werden. damit diese Meldungen in den Protokollen korrekt angezeigt werden.

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

### Drucken Sie keine Stacktraces in der Konsole {#do-not-print-stack-traces-to-the-console}

* **Schlüssel**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Wie bereits erwähnt, ist Kontext beim Verständnis von Protokollmeldungen äußerst wichtig. Verwenden `Exception.printStackTrace()` führt dazu, dass nur die Stacktrace an den Standard-Fehlerstream ausgegeben wird, wodurch der gesamte Kontext verloren geht. Wenn in einer Multi-Thread-Anwendung wie Experience Manager mehrere Ausnahmen parallel mit dieser Methode gedruckt werden, können sich ihre Stacktraces überschneiden, was erhebliche Verwirrung verursacht. Ausnahmen sollten daher nur über das Protokollierungs-Framework protokolliert werden.

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

Die Protokollierung in Experience Manager sollte immer über das Protokollierungs-Framework (SLF4J) erfolgen. Bei der direkten Ausgabe an die standardmäßigen Ausgabe- oder Standard-Fehlerströme gehen die vom Protokollierungs-Framework bereitgestellten Struktur- und Kontextinformationen verloren. Manchmal kann es zu Leistungsproblemen kommen.

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

Im Allgemeinen sollten Pfade, die mit `/libs` und `/apps` beginnen, nicht hartcodiert werden, da die Pfade, auf die sie verweisen, meist als Pfade relativ zum Sling-Suchpfad (der standardmäßig auf `/libs,/apps` festgelegt ist) gespeichert werden. Durch die Angabe des absoluten Pfads können geringfügige Fehler entstehen, die erst später im Projektlebenszyklus deutlich werden.

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

### Sling Scheduler nicht verwenden {#sonarqube-sling-scheduler}

* **Schlüssel**: CQRules:AMSCORE-554
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Verwenden Sie die Sling-Planung nicht für Aufgaben, für die eine garantierte Ausführung erforderlich ist. Über Sling geplante Aufträge garantieren die Ausführung und eignen sich besser für Umgebungen mit und ohne Cluster.

Siehe [Apache Sling Eventing und Job Handling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) , um mehr darüber zu erfahren, wie Sling-Aufträge in Clusterumgebungen verarbeitet werden.

### Verwenden Sie keine veralteten Experience Manager-APIs {#sonarqube-aem-deprecated}

* **Schlüssel**: AMSCORE-553
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Die Oberfläche der Experience Manager-API wird ständig überarbeitet, um APIs zu identifizieren, für die von einer Nutzung abzuraten ist und die daher als veraltet betrachtet werden.

Häufig werden diese APIs mit dem Standard-Java™ nicht mehr unterstützt `@Deprecated` -Anmerkung und als solche, wie durch `squid:CallToDeprecatedMethod`.

Es gibt jedoch Fälle, in denen eine API im Kontext von Experience Manager nicht mehr unterstützt wird, in anderen Kontexten jedoch nicht mehr unterstützt wird. Diese Regel identifiziert diese zweite Klasse.


## OakPAL-Inhaltsregeln {#oakpal-rules}

Im folgenden Abschnitt werden die von Cloud Manager durchgeführten OakPAL-Prüfungen vorgestellt.

>[!NOTE]
>
>OakPAL ist ein Framework, das Inhaltspakete mit einem eigenständigen Oak-Repository validiert. Es wurde von einem Experience Manager Partner und Gewinner des Experience Managers Rockstar North America Award 2019 entwickelt.

### Produkt-APIs, die mit @ProviderType kommentiert wurden, sollten von Kunden nicht implementiert oder erweitert werden {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Schlüssel**: CQBP-84
* **Typ**: Fehler
* **Schweregrad**: Kritisch
* **Seit**: Version 2018.7.0

Die Experience Manager-API enthält Java™-Schnittstellen und -Klassen, die nur für die Verwendung - aber nicht Implementierung - durch benutzerdefinierten Code vorgesehen sind. Beispielsweise die -Benutzeroberfläche `com.day.cq.wcm.api.Page` nur von Experience Manager implementiert werden.

Wenn neue Methoden zu diesen Schnittstellen hinzugefügt werden, wirken sich diese zusätzlichen Methoden nicht auf vorhandenen Code aus, der diese Schnittstellen verwendet. Daher wird das Hinzufügen neuer Methoden zu diesen Schnittstellen als abwärtskompatibel betrachtet. Wenn jedoch benutzerdefinierter Code eine dieser Schnittstellen implementiert, führt dieser benutzerspezifische Code ein Abwärtskompatibilitätsrisiko für den Kunden ein.

Schnittstellen und Klassen — wie von Experience Manager implementiert — werden mit `org.osgi.annotation.versioning.ProviderType` oder manchmal eine ähnliche Legacy-Anmerkung `aQute.bnd.annotation.ProviderType`. Diese Regel identifiziert die Fälle, in denen eine solche Schnittstelle durch benutzerdefinierten Code implementiert wird (oder eine Klasse erweitert wird).

#### Nicht konformer Code {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Benutzerdefinierte Lucene Oak-Indizes müssen über eine Tika-Konfiguration verfügen {#oakpal-indextikanode}

* **Schlüssel**: IndexTikaNode
* **Typ**: Fehler
* **Schweregrad**: Blocker
* **Seit**: 2021.8.0

Mehrere vordefinierte Experience Manager-Oak-Indizes enthalten eine Tika-Konfiguration und Anpassungen dieser Indizes müssen eine Tika-Konfiguration enthalten. Diese Regel überprüft auf Anpassungen der Indizes `damAssetLucene`, `lucene` und `graphqlConfig` und löst ein Problem aus, wenn entweder der Knoten `tika` fehlt oder wenn im Knoten `tika` ein untergeordneter Knoten mit dem Namen `config.xml` fehlt.

Weitere Informationen zum Anpassen von Indexdefinitionen finden Sie unter [Dokumentation zur Indizierung](/help/operations/indexing.md#preparing-the-new-index-definition).

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

Oak-Indizes des Typs `lucene` muss immer asynchron indiziert werden. Andernfalls kann es zu einer Instabilität des Systems kommen. Weitere Informationen zur Struktur von Lucene-Indizes finden Sie im [Oak-Dokumentation.](https://jackrabbit.apache.org/oak/docs/query/lucene.html#index-definition)

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

Damit die Asset-Suche in Experience Manager Assets ordnungsgemäß funktioniert, passen Sie die `damAssetLucene` Der Oak-Index muss einen Satz von Richtlinien befolgen, die für diesen Index spezifisch sind. Diese Regel überprüft, ob die Indexdefinition über eine Eigenschaft mit mehreren Werten mit dem Namen `tags` verfügt, die den Wert `visualSimilaritySearch` enthält.

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

Es ist seit langem eine bewährte Methode, dass die `/libs` Die Inhaltsstruktur im Experience Manager-Inhalts-Repository sollte von Kunden als schreibgeschützt betrachtet werden. Das Ändern von Knoten und Eigenschaften unter `/libs` ist mit erheblichen Risiken für umfassende und kleinere Aktualisierungen verbunden. Änderungen an `/libs` muss durch Adobe auf offizieller Ebene erfolgen.

### Pakete sollten keine doppelten OSGi-Konfigurationen enthalten {#oakpal-package-osgi}

* **Schlüssel**: DuplicateOsgiConfigurations
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2019.6.0

Ein häufig auftretendes Problem bei komplexen Projekten besteht darin, dass dieselbe OSGi-Komponente mehrmals konfiguriert ist. Dieses Problem führt zu einer Unklarheit darüber, welche Konfiguration anwendbar ist. Diese Regel ist &quot;runmode-basiert&quot;, da sie nur Probleme identifiziert, bei denen dieselbe Komponente mehrmals im selben Ausführungsmodus oder in einer Kombination von Ausführungsmodi konfiguriert ist.

>[!NOTE]
>
>Diese Regel erzeugt Probleme, bei denen dieselbe Konfiguration im selben Pfad in mehreren Paketen definiert ist, einschließlich der Fälle, in denen dasselbe Paket in der Gesamtliste der erstellten Pakete dupliziert wird.
>
>Wenn der Build beispielsweise Pakete mit dem Namen `com.myco:com.myco.ui.apps` und `com.myco:com.myco.all` where `com.myco:com.myco.all` Einbettungen `com.myco:com.myco.ui.apps`, dann alle Konfigurationen in `com.myco:com.myco.ui.apps` werden als Duplikate gemeldet.
>
>Dies ist im Allgemeinen der Fall, dass die [Richtlinien für die Inhaltspaketstruktur](/help/implementing/developing/introduction/aem-project-content-package-structure.md). In diesem speziellen Beispiel wird das -Paket `com.myco:com.myco.ui.apps` fehlt die `<cloudManagerTarget>none</cloudManagerTarget>` -Eigenschaft.

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

### Konfigurations- und Installationsordner dürfen nur OSGi-Knoten enthalten {#oakpal-config-install}

* **Schlüssel**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2019.6.0

Aus Sicherheitsgründen enthalten Pfade, die `/config/` und `/install/` sind nur von Administratoren in Experience Manager lesbar und sollten nur für OSGi-Konfigurationen und OSGi-Bundles verwendet werden. Das Platzieren anderer Inhaltstypen in Pfade mit diesen Segmenten führt dazu, dass sich das Programm abhängig davon anders verhält, ob sie von Administratoren- oder Nicht-Administratoren verwendet wird.

Ein häufig auftretendes Problem ist die Verwendung von Knoten mit der Bezeichnung `config` in Komponentendialogfeldern oder beim Angeben der Rich-Text-Editor-Konfiguration für die Inline-Bearbeitung. Um dieses Problem zu beheben, sollte der fehlerhafte Knoten in einen kompatiblen Namen umbenannt werden. Verwenden Sie für die Konfiguration des Rich-Text-Editors den `configPath` -Eigenschaft auf `cq:inplaceEditing` -Knoten, um den neuen Speicherort anzugeben.

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

### Pakete sollten sich nicht überschneiden {#oakpal-no-overlap}

* **Schlüssel**: PackageOverlaps
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2019.6.0

Ähnlich wie bei der Regel [Pakete dürfen keine doppelten OSGi-Konfigurationen enthalten](#oakpal-package-osgi) ist dies ein häufiges Problem bei komplexen Projekten, bei denen mehrere separate Inhaltspakete in denselben Knotenpfad schreiben. Mit Inhaltspaketabhängigkeiten kann zwar ein konsistentes Ergebnis sichergestellt werden, Überlappungen sollten aber dennoch von vorneherein vermieden werden.

### Der standardmäßige Authoring-Modus sollte nicht die klassische Benutzeroberfläche sein {#oakpal-default-authoring}

* **Schlüssel**: ClassicUIAuthoringMode
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Die OSGi-Konfiguration `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` definiert den standardmäßigen Authoring-Modus in Experience Manager. weil [Die klassische Benutzeroberfläche wird seit Experience Manager 6.4 nicht mehr unterstützt.](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html?lang=de), tritt jetzt ein Problem auf, wenn der standardmäßige Authoring-Modus für die klassische Benutzeroberfläche konfiguriert ist.

### Komponenten mit Dialogfeldern sollten Dialogfelder für die Touch-Benutzeroberfläche haben {#oakpal-components-dialogs}

* **Schlüssel**: ComponentWithOnlyClassicUIDialog
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Experience Manager-Komponenten mit einem Dialogfeld für die klassische Benutzeroberfläche sollten immer über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche verfügen. Beide bieten ein optimales Authoring-Erlebnis und sind mit dem Cloud Service-Bereitstellungsmodell kompatibel, bei dem die klassische Benutzeroberfläche nicht unterstützt wird. Diese Regel überprüft die folgenden Szenarien:

* Eine Komponente mit einem Dialogfeld für die klassische Benutzeroberfläche (d. h. einem untergeordneten `dialog`-Knoten) muss über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche verfügen (d. h. über einen untergeordneten `cq:dialog`-Knoten).
* Eine Komponente mit einem Design-Dialogfeld für die klassische Benutzeroberfläche (d. h. einem `design_dialog`-Knoten) muss über ein entsprechendes Design-Dialogfeld für die Touch-Benutzeroberfläche verfügen (d. h. über einen untergeordneten `cq:design_dialog`-Knoten).
* Eine Komponente mit einem Dialogfeld für die klassische Benutzeroberfläche und einem Design-Dialogfeld für die klassische Benutzeroberfläche muss sowohl über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche als auch über ein entsprechendes Design-Dialogfeld für die Touch-Benutzeroberfläche verfügen.

Die Dokumentation zu den Experience Manager-Modernisierungs-Tools enthält Dokumentation und Tools zum Konvertieren von Komponenten aus der klassischen Benutzeroberfläche in die Touch-Benutzeroberfläche. Siehe [Dokumentation zu den Experience Manager-Modernisierungs-Tools](https://opensource.adobe.com/aem-modernize-tools/) für weitere Details.

### Pakete sollten keinen veränderlichen und unveränderlichen Inhalt mischen {#oakpal-packages-immutable}

* **Schlüssel**: ImmutableMutableMixedPackage
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Um mit dem Cloud Service-Bereitstellungsmodell kompatibel zu sein, müssen einzelne Inhaltspakete entweder Inhalte für die unveränderlichen Bereiche des Repositorys (`/apps` und `/libs`) oder dem veränderlichen Bereich (alles, was nicht in `/apps` oder `/libs`), aber nicht beides. Beispiel: ein Paket, das beide `/apps/myco/components/text` und `/etc/clientlibs/myco` ist nicht mit Cloud Service kompatibel und verursacht die Meldung eines Problems.

>[!NOTE]
>
>Die Regel [Kundenpakete sollten Knoten unter /libs nicht erstellen oder ändern](#oakpal-customer-package) ist immer gültig.

Siehe [Experience Manager-Projektstruktur](/help/implementing/developing/introduction/aem-project-content-package-structure.md) für weitere Details.

### Verwenden Sie keine Agenten für Rückwärtsreplikation {#oakpal-reverse-replication}

* **Schlüssel**: ReverseReplication
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

In Cloud Service-Implementierungen ist keine Unterstützung für die Rückwärtsreplikation verfügbar, wie im Abschnitt zum Experience Manager as a Cloud Service [Versionshinweise.](/help/release-notes/aem-cloud-changes.md#replication-agents)

Kunden, die die Rückwärtsreplikation verwenden, sollten sich für alternative Lösungen an Adobe wenden.

### Ressourcen, die in proxy-aktivierten Client-Bibliotheken enthalten sind, sollten sich in einem Ordner mit dem Namen Ressourcen befinden {#oakpal-resources-proxy}

* **Schlüssel**: ClientlibProxyResource
* **Typ**: Fehler
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Experience Manager-Client-Bibliotheken können statische Ressourcen wie Bilder und Schriftarten enthalten. Wie im Dokument [Verwenden von Präprozessoren](/help/implementing/developing/introduction/clientlibs.md#using-preprocessors) beschrieben, müssen diese statischen Ressourcen bei der Verwendung von Proxy-fähigen Client-Bibliotheken in einem untergeordneten Ordner namens „`resources`“ enthalten sein, damit sie in den Veröffentlichungsinstanzen effektiv referenziert werden können.

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

### Nutzung von Workflow-Prozessen, die mit Cloud Services inkompatibel sind {#oakpal-usage-cloud-service}

* **Schlüssel**: CloudServiceIncompatibleWorkflowProcess
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2021.2.0

Mit dem Wechsel zu Asset-Microservices für die Asset-Verarbeitung auf dem Experience Manager as a Cloud Service wurden mehrere Workflow-Prozesse, die in On-Premise- und AMS-Versionen von Experience Manager verwendet wurden, entweder nicht mehr unterstützt oder nicht mehr erforderlich.

Das Migrationstool im [GitHub-Repository für Experience Manager as a Cloud Service Assets](https://github.com/adobe/aem-cloud-migration) kann verwendet werden, um Workflow-Modelle während der Migration zu Experience Manager as a Cloud Service zu aktualisieren.

### Die Verwendung statischer Vorlagen wird zugunsten bearbeitbarer Vorlagen empfohlen {#oakpal-static-template}

* **Schlüssel**: StaticTemplateUsage
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Auch wenn die Verwendung statischer Vorlagen in Experience Manager-Projekten historisch üblich ist, empfiehlt Adobe bearbeitbare Vorlagen, da sie die größte Flexibilität bieten und zusätzliche Funktionen unterstützen, die in statischen Vorlagen nicht vorhanden sind. Weitere Informationen finden Sie im Dokument [Seitenvorlagen](/help/implementing/developing/components/templates.md).

Die Migration von statischen zu bearbeitbaren Vorlagen kann mithilfe der [Experience Manager-Modernisierungs-Tools.](https://opensource.adobe.com/aem-modernize-tools/)

### Die Verwendung älterer Foundation-Komponenten wird nicht empfohlen {#oakpal-usage-legacy}

* **Schlüssel**: LegacyFoundationComponentUsage
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Die veralteten Foundation-Komponenten (d. h. Komponenten unter `/libs/foundation`) wurden [veraltet für mehrere Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html?lang=de) zugunsten der Kernkomponenten. Von der Verwendung der Foundation-Komponenten als Basis für benutzerdefinierte Komponenten – sei es durch Überlagerung oder Vererbung – wird abgeraten und sie sollten in die entsprechende Kernkomponente konvertiert werden.

Diese Konvertierung kann durch die [Experience Manager-Modernisierungs-Tools.](https://opensource.adobe.com/aem-modernize-tools/)

### Verwenden Sie nur unterstützte Ausführungsmodusnamen und -reihenfolge {#oakpal-supported-runmodes}

* **Schlüssel**: SupportedRunmode
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Experience Manager as a Cloud Service erzwingt eine strikte Benennungsrichtlinie für Ausführungsmodusnamen und eine strikte Reihenfolge für diese Ausführungsmodi. Die Liste der unterstützten Ausführungsmodi finden Sie im Dokument . [Bereitstellen in Experience Manager as a Cloud Service](/help/implementing/deploying/overview.md#runmodes) und jede Abweichung davon wird als Problem erkannt.

### Benutzerdefinierte Suchindex-Definitionsknoten müssen direkt untergeordnete Elemente von /oak:index sein. {#oakpal-custom-search}

* **Schlüssel**: OakIndexLocation
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Für den as a Cloud Service Experience Manager müssen benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) direkt untergeordnete Knoten von `/oak:index`. Indizes an anderen Orten müssen verschoben werden, um mit Experience Manager as a Cloud Service kompatibel zu sein. Weitere Informationen zu Suchindizes finden Sie im Dokument [Inhaltssuche und -indizierung](/help/operations/indexing.md).

### Benutzerdefinierte Suchindex-Definitionsknoten müssen eine compatVersion von 2 haben. {#oakpal-custom-search-compatVersion}

* **Schlüssel**: IndexCompatVersion
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Für Experience Manager as a Cloud Service müssen benutzerdefinierte Suchindex-Definitionen (z. B. Knoten des Typs `oak:QueryIndexDefinition`) muss die Variable `compatVersion` Eigenschaft auf `2`. Andere Werte werden vom Experience Manager as a Cloud Service nicht unterstützt. Weitere Informationen zu Suchindizes finden Sie unter [Inhaltssuche und -indizierung.](/help/operations/indexing.md)

### Nachstehende Knoten der benutzerdefinierten Suchindex-Definitionsknoten müssen vom Typ nt:unstructured sein {#oakpal-descendent-nodes}

* **Schlüssel**: IndexDescendantNodeType
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Die Fehlerbehebung kann schwierig sein, wenn ein benutzerdefinierter Suchindex-Definitionsknoten ungeordnete untergeordnete Knoten hat. Um diese Situation zu vermeiden, wird empfohlen, dass alle untergeordneten Knoten eines `oak:QueryIndexDefinition` node be of type `nt:unstructured`.

### Die Definitionsknoten des benutzerdefinierten Suchindex müssen einen untergeordneten Knoten namens indexRules enthalten, der untergeordnete Elemente enthält {#oakpal-custom-search-index}

* **Schlüssel**: IndexRulesNode
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Ein korrekt definierter benutzerdefinierter Suchindex-Definitionsknoten muss einen untergeordneten Knoten namens `indexRules` enthalten, der wiederum mindestens einen untergeordneten Knoten haben muss. Weitere Informationen finden Sie in der [Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### Benutzerdefinierte Suchindex-Definitionsknoten müssen Namenskonventionen entsprechen {#oakpal-custom-search-definitions}

* **Schlüssel**: IndexName
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Für den as a Cloud Service Experience Manager müssen benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) muss nach einem bestimmten Muster benannt werden, das im Dokument beschrieben wird [Inhaltssuche und -indizierung.](/help/operations/indexing.md)

### Benutzerdefinierte Suchindex-Definitionsknoten müssen den Indextyp Lucene verwenden  {#oakpal-index-type-lucene}

* **Schlüssel**: IndexType
* **Typ**: Fehler
* **Schweregrad**: Blocker
* **Seit**: Version 2021.2.0 (Änderung von Typ und Schweregrad in 2021.8.0)

Für den as a Cloud Service Experience Manager müssen benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) haben eine `type` -Eigenschaft mit dem Wert `lucene`. Die Indizierung mit älteren Indextypen muss vor der Migration zu Experience Manager as a Cloud Service aktualisiert werden. Weitere Informationen finden Sie unter [Inhaltssuche und -indizierung](/help/operations/indexing.md#how-to-use).

### Benutzerdefinierte Suchindex-Definitionsknoten dürfen keine Eigenschaft mit dem Namen Seed enthalten. {#oakpal-property-name-seed}

* **Schlüssel**: IndexSeedProperty
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Experience Manager as a Cloud Service untersagt benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`), die eine Eigenschaft namens `seed`. Die Indizierung mit dieser Eigenschaft muss vor der Migration zu Experience Manager as a Cloud Service aktualisiert werden. Weitere Informationen finden Sie im Dokument [Inhaltssuche und -indizierung](/help/operations/indexing.md#how-to-use).

### Benutzerdefinierte Suchindex-Definitionsknoten dürfen keine Eigenschaft namens reindex enthalten. {#oakpal-reindex-property}

* **Schlüssel**: IndexReindexProperty
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Experience Manager as a Cloud Service untersagt benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`), die eine Eigenschaft namens `reindex`. Die Indizierung mit dieser Eigenschaft muss vor der Migration zu Experience Manager as a Cloud Service aktualisiert werden. Weitere Informationen finden Sie im Dokument [Inhaltssuche und -indizierung](/help/operations/indexing.md#how-to-use).
