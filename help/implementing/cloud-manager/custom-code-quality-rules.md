---
title: Qualitätsregeln für benutzerspezifischen Code
description: Erfahren Sie mehr über die benutzerspezifischen Regeln für die Code-Qualität von Cloud Manager, die auf Best Practices von Adobe Experience Manager Engineering basieren, um durch gründliche Tests hochwertigen Code sicherzustellen.
exl-id: f40e5774-c76b-4c84-9d14-8e40ee6b775b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2573eb5f8a8ff21a8e30b94287b554885cd1cd89
workflow-type: tm+mt
source-wordcount: '4421'
ht-degree: 74%

---

# Qualitätsregeln für benutzerspezifischen Code {#custom-code-quality-rules}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_customcodequalityrules"
>title="Qualitätsregeln für benutzerspezifischen Code"
>abstract="Erfahren Sie mehr über die benutzerspezifischen Regeln für die Code-Qualität von Cloud Manager, die auf Best Practices von Adobe Experience Manager Engineering basieren, um durch gründliche Tests hochwertigen Code sicherzustellen."

Erfahren Sie mehr über die benutzerspezifischen Regeln für die Code-Qualität von Cloud Manager, die auf Best Practices von Adobe Experience Manager Engineering basieren, um durch gründliche Tests einen hochwertigen Code sicherzustellen. Siehe auch [Tests der Codequalität](/help/implementing/cloud-manager/code-quality-testing.md).

>[!NOTE]
>
>Vollständige SonarQube-Regeln stehen aufgrund von proprietären Informationen von Adobe nicht zum Download zur Verfügung. Sie können die vollständige Liste von Regeln [über diesen Link](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx) herunterladen. Lesen Sie dieses Dokument weiter, um Beschreibungen und Beispiele für die Regeln zu erhalten.

>[!NOTE]
>
>Die hier bereitgestellten Code-Beispiele dienen nur Veranschaulichungszwecken. In der [Dokumentation zu SonarQube-Konzepten](https://docs.sonarsource.com/sonarqube/latest/) finden Sie Informationen zu SonarQube-Konzepten und Qualitätsregeln.

## Regeln für SonarQube {#sonarqube-rules}

Im folgenden Abschnitt werden die SonarQube-Regeln beschrieben, die von Cloud Manager ausgeführt werden.

### Verwenden Sie keine potenziell gefährlichen Funktionen {#do-not-use-potentially-dangerous-functions}

* **Schlüssel**: CQRules:CWE-676
* **Typ**: Sicherheitslücke
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

Die Methoden `Thread.stop()` und `Thread.interrupt()` können schwer zu reproduzierende Probleme und in einigen Fällen Sicherheitslücken verursachen. Daher sollte deren Verwendung sorgfältig überwacht und validiert werden. Im Allgemeinen ist die Nachrichtenübergabe eine sicherere Möglichkeit, ähnliche Ziele zu erreichen.

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

Durch die Verwendung einer Formatzeichenfolge aus einer externen Quelle (z. B. einem Abfrageparameter oder nutzergenerierten Inhalten) kann ein Programm für Denial-of-Service-Angriffe anfällig werden. Es gibt Fälle, in denen eine Formatzeichenfolge von außen gesteuert werden kann, jedoch nur aus vertrauenswürdigen Quellen zulässig ist.

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

Bei HTTP-Anfragen in einer Experience Manager-Anwendung ist es wichtig, geeignete Timeouts zu konfigurieren, um unnötigen Thread-Verbrauch zu vermeiden.
Standardmäßig sind sowohl der Java™ HTTP Client (java.net.HttpUrlConnection) als auch der häufig verwendete Apache HTTP Components-Client keine Zeitüberschreitungen vorschreiben. Daher müssen sie manuell konfiguriert werden. Als Best Practice empfiehlt sich, Timeouts auf maximal 60 Sekunden festzulegen.

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

public void orDoThis () {
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

ResourceResolver-Objekte, die von `ResourceResolverFactory` abgerufen werden, verbrauchen Systemressourcen. Obwohl es Möglichkeiten gibt, diese Ressourcen freizugeben, wenn ein `ResourceResolver` nicht mehr verwendet wird, ist es effizienter, alle offenen `ResourceResolver`-Objekte explizit durch Aufruf der Methode `close()` zu schließen.

Ein häufiges Missverständnis besteht darin, dass `ResourceResolver`-Objekte, die mit einer vorhandenen JCR-Sitzung erstellt wurden, nicht explizit geschlossen werden sollten oder dass das Schließen sie betrifft die JCR-Sitzung. Diese Informationen sind falsch. Ein `ResourceResolver` sollte immer geschlossen werden, wenn er nicht mehr benötigt wird. Da `ResourceResolver` die `Closeable` -Schnittstelle implementiert, können Sie auch die `try-with-resources` -Syntax verwenden, anstatt `close()` direkt aufzurufen.

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

### Erfasste Ausnahmen sollten entweder protokolliert oder ausgelöst werden, aber nicht beides {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Schlüssel**: CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Im Allgemeinen sollte eine Ausnahme genau einmal protokolliert werden. Das mehrfache Protokollieren von Ausnahmen kann zu Verwirrung führen. Der Grund dafür ist, dass unklar ist, wie oft eine Ausnahme aufgetreten ist. Das häufigste Muster, das zu diesem Effekt führt, ist das Protokollieren und Ausgeben einer gefundenen Ausnahme.

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

### Throw-Anweisungen sollten möglichst nicht unmittelbar auf Log-Anweisungen folgen {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Schlüssel**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Ein weiteres gängiges Muster, das vermieden werden sollte, ist die Protokollierung einer Nachricht, direkt gefolgt von der Auslösung einer Ausnahme. Dadurch wird die Ausnahmemeldung in Protokolldateien meist doppelt aufgeführt.

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

Allgemein sollten mit der Protokollebene INFO wichtige Aktionen abgegrenzt werden. Standardmäßig ist Experience Manager so konfiguriert, dass auf der INFO-Ebene oder darüber protokolliert wird. GET- und HEAD-Methoden sollten nur schreibgeschützte Vorgänge sein und stellen daher keine wichtigen Aktionen dar. Eine Protokollierung auf INFO-Ebene als Antwort auf GET- oder HEAD-Anfragen füllt das Protokoll wahrscheinlich mit erheblichen Mengen überflüssiger Informationen, sodass es schwieriger wird, nützliche Informationen in Protokolldateien zu finden. Melden Sie sich beim Umgang mit GET- oder HEAD-Anfragen auf den WARN- oder ERROR-Ebenen an, wenn etwas schief gelaufen ist. Verwenden Sie DEBUG- oder TRACE-Ebenen, wenn detaillierte Informationen zur Fehlerbehebung erforderlich sind.

>[!NOTE]
>
>Gilt nicht für die Protokollierung im Typ `access.log` für jede Anfrage.

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

Als Best Practice sollten Protokollmeldungen kontextbezogene Informationen darüber enthalten, wo eine Programmausnahme aufgetreten ist. Obwohl der Kontext auch mit Stacktraces bestimmt werden kann, ist die Protokollmeldung meist besser lesbar und verständlicher. Daher ist es bei der Protokollierung einer Ausnahme nicht empfehlenswert, die Ausnahmemeldung als Protokollmeldung zu verwenden. Die Ausnahmemeldung erklärt, was schiefgelaufen ist, während die Protokollmeldung den Leser darüber informieren sollte, was die Anwendung bei Eintreten der Ausnahme getan hat. Die Ausnahmemeldung wird dennoch protokolliert. Durch die Spezifizierung Ihrer eigenen Nachricht sind die Protokolle leichter verständlich.

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

Wie schon der Name sagt, sollten Java™-Ausnahmen immer in Ausnahmefällen verwendet werden. Wenn eine Ausnahme erfasst wird, muss daher sichergestellt sein, dass Protokollmeldungen auf der entsprechenden Ebene – WARN oder ERROR – protokolliert werden. Dadurch wird sichergestellt, dass diese Meldungen in den Protokollen korrekt angezeigt werden.

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

Wie bereits erwähnt, ist Kontext beim Verständnis von Protokollmeldungen äußerst wichtig. Durch Verwendung von `Exception.printStackTrace()` wird nur der Stacktrace an den Standardfehler-Stream ausgegeben, während der gesamte Kontext verloren geht. Außerdem kann es bei mehrprozessgestützten Anwendungen wie Experience Manager beim parallelen Drucken mehrerer Ausnahmen mit dieser Methode zu einer Überlappung der Stacktraces kommen, was erhebliche Verwirrung verursacht. Ausnahmen sollten daher nur über das Protokollierungs-Framework protokolliert werden.

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

### Nicht an Standardausgabe oder Standardfehler ausgeben {#do-not-output-to-standard-output-or-standard-error}

* **Schlüssel**: CQRules:CQBP-44—LogLevelConsolePrinters
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Die Anmeldung in Experience Manager sollte immer über das Protokollierungs-Framework (SLF4J) erfolgen. Bei der direkten Ausgabe an die Standardausgabe oder den Standardfehler-Stream gehen die vom Protokollierungs-Framework bereitgestellten Struktur- und Kontextinformationen verloren. Manchmal kann dies zu Leistungsproblemen führen.

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

### Vermeiden von fest programmierten Apps und Libs-Pfaden {#avoid-hardcoded-apps-and-libs-paths}

* **Schlüssel**: CQRules:CQBP-71
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Pfade, die mit `/libs` und `/apps` beginnen, sollten im Allgemeinen nicht hartcodiert sein. Diese Pfade werden normalerweise relativ zum Sling-Suchpfad gespeichert, der standardmäßig auf `/libs,/apps` festgelegt ist. Durch die Angabe des absoluten Pfads können geringfügige Fehler entstehen, die erst später im Projektlebenszyklus deutlich werden.

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

### Sling-Scheduler nicht verwenden {#sonarqube-sling-scheduler}

* **Schlüssel**: CQRules:AMSCORE-554
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Verwenden Sie den Sling-Scheduler nicht für Aufgaben, die eine garantierte Ausführung erfordern. Über Sling geplante Vorgänge garantieren die Ausführung und eignen sich besser für Umgebungen mit und ohne Cluster.

Weitere Informationen zum Umgang mit Sling-Vorgängen in Cluster-Umgebungen finden Sie unter [Apache Sling-Ereignisse und -Vorgangsverarbeitung](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html).

### Keine nicht mehr unterstützten Experience Manager-APIs verwenden {#sonarqube-aem-deprecated}

* **Schlüssel**: AMSCORE-553
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Die Experience Manager-API-Oberfläche wird ständig geprüft, um APIs zu identifizieren, deren Verwendung nicht mehr empfohlen wird und die deshalb als nicht mehr unterstützt gelten.

In vielen Fällen sind diese APIs unter Verwendung der Standard-Java™-Annotation `@Deprecated` als veraltet eingestuft und durch `squid:CallToDeprecatedMethod` gekennzeichnet. 

Es gibt jedoch auch Fälle, in denen eine API im Experience Manager-Kontext veraltet ist, in anderen Kontexten jedoch nicht. Diese Regel identifiziert diese zweite Gruppe. 

### Verwenden Sie in Sling-Modellen keine @Inject-Anmerkung mit @Optional. {#sonarqube-slingmodels-inject-optional}

* **Schlüssel**: InjectAnnotationWithOptionalInjectionCheck
* **Typ**: Software-Qualität
* **Schweregrad**: Gering
* **Seit**: Version 2023.11

Das Apache Sling-Projekt rät von der Verwendung der `@Inject`-Anmerkung im Kontext von Sling-Modellen ab, da dies zu einer schlechten Leistung führen kann, wenn sie mit der `DefaultInjectionStrategy.OPTIONAL` (entweder auf Feld- oder Klassenebene) verwendet wird. Stattdessen sollten spezifischere Injektionen (wie die Anmerkungen `@ValueMapValue` oder `@OsgiInjector`) verwendet werden.

Lesen Sie die [Apache Sling-Dokumentation](https://sling.apache.org/documentation/bundles/models.html#discouraged-annotations-1) für weitere Informationen über die empfohlenen Anmerkungen und die Gründe, aus denen diese Empfehlung überhaupt ausgesprochen wurde.


### Wiederverwenden von HTTPClient-Instanzen {#sonarqube-reuse-httpclient}

* **Schlüssel**: AEMSRE-870
* **Typ**: Software-Qualität
* **Schweregrad**: Gering
* **Seit**: Version 2023.11

AEM Anwendungen erreichen häufig andere Anwendungen über das HTTP-Protokoll, und der Apache HttpClient ist eine häufig verwendete Bibliothek, um dies zu erreichen. Die Erstellung eines solchen HttpClient-Objekts bringt jedoch einen gewissen Mehraufwand mit sich, sodass diese Objekte so weit wie möglich wiederverwendet werden sollten.

Diese Regel überprüft, ob ein solches HttpClient-Objekt in einer Methode nicht privat, sondern auf Klassenebene global ist, sodass es wiederverwendet werden kann. In diesem Fall sollte das HttpClient-Feld im Konstruktor der Klasse oder der `activate()`-Methode festgelegt werden (wenn diese Klasse eine OSGi-Komponente/ein OSGi-Dienst ist).

Lesen Sie das [Optimierungshandbuch](https://hc.apache.org/httpclient-legacy/performance.html) des HttpClient für einige Best Practices für die Verwendung des HttpClient.

#### Nicht konformer Code {#non-compliant-code-14}

```java
public void doHttpCall() {
  HttpClient httpclient = HttpClients.createDefault();
  // do something with the httpclient
}
```

#### Konformer Code {#compliant-code-11}

```java
public class myClass {

  HttpClient httpclient;

  public void doHttpCall() {
    // do something with the httpclient
  }

}
```

## Inhaltsregeln für OakPAL {#oakpal-rules}

Im folgenden Abschnitt werden die von Cloud Manager durchgeführten OakPAL-Prüfungen vorgestellt.

>[!NOTE]
>
>OakPAL ist ein Framework, das Inhaltspakete mit einem eigenständigen Oak-Repository validiert. Ein Experience Manager Partner, der 2019 den Experience Manager Rockstar North America Award gewann, entwickelte ihn.

### Kunden sollten mit @ProviderType kommentierte Produkt-APIs nicht implementieren oder erweitern{#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Schlüssel**: CQBP-84
* **Typ**: Fehler
* **Schweregrad**: Kritisch
* **Seit**: Version 2018.7.0

Die Experience Manager-API enthält Java™-Schnittstellen und -Klassen, die nur für die Verwendung - aber nicht Implementierung - durch benutzerdefinierten Code vorgesehen sind. Beispielsweise sollte nur Experience Manager die Schnittstelle `com.day.cq.wcm.api.Page` implementieren.

Wenn diesen Schnittstellen neue Methoden hinzugefügt werden, wirken sich diese zusätzlichen Methoden nicht auf vorhandenen Code aus, der diese Schnittstellen verwendet. Daher wird das Hinzufügen neuer Methoden zu diesen Schnittstellen als abwärtskompatibel betrachtet. Wenn jedoch benutzerdefinierter Code eine dieser Schnittstellen implementiert, erzeugt dieser benutzerspezifische Code ein Abwärtskompatibilitätsrisiko für den Kunden.

Schnittstellen und Klassen — wie durch Experience Manager implementiert — werden mit `org.osgi.annotation.versioning.ProviderType` oder manchmal einer ähnliche Legacy-Anmerkung `aQute.bnd.annotation.ProviderType` gekennzeichnet. Diese Regel identifiziert Fälle, in denen benutzerdefinierter Code eine solche Schnittstelle implementiert oder eine Klasse erweitert.

#### Nicht konformer Code {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Benutzerdefinierte Lucene-Oak-Indizes müssen über eine Tika-Konfiguration verfügen {#oakpal-indextikanode}

* **Schlüssel**: IndexTikaNode
* **Typ**: Fehler
* **Schweregrad**: Blocker
* **Seit**: 2021.8.0

Mehrere vorkonfigurierte Experience Manager Oak-Indizes enthalten eine Tika-Konfiguration und Anpassungen dieser Indizes müssen eine Tika-Konfiguration enthalten. Diese Regel überprüft auf Anpassungen der Indizes `damAssetLucene`, `lucene` und `graphqlConfig` und löst ein Problem aus, wenn entweder der Knoten `tika` fehlt oder wenn im Knoten `tika` ein untergeordneter Knoten mit dem Namen `config.xml` fehlt.

Weitere Informationen zum Anpassen von Indexdefinitionen finden Sie in der [Dokumentation zur Indizierung](/help/operations/indexing.md#preparing-the-new-index-definition).

#### Nicht konformer Code {#non-compliant-code-indextikanode}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
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

Oak-Indizes des Typs `lucene` muss immer asynchron indiziert werden. Andernfalls kann es zu einer Instabilität des Systems kommen. Weitere Informationen zur Struktur von Lucene-Indizes finden Sie in der [Dokumentation zu Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html#index-definition).

#### Nicht konformer Code {#non-compliant-code-indexasync}

```text
+ oak:index
    + damAssetLucene-1-custom
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - type: lucene
      - tags: [visualSimilaritySearch]
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
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Benutzerdefinierte DAM-Asset-Lucene-Oak-Indizes sind ordnungsgemäß strukturiert {#oakpal-damAssetLucene-sanity-check}

* **Schlüssel**: IndexDamAssetLucene
* **Typ**: Fehler
* **Schweregrad**: Blocker
* **Seit**: 2021.6.0

Damit die Asset-Suche in Experience Manager Assets ordnungsgemäß funktioniert, müssen die Anpassungen des `damAssetLucene` Oak-Index einem Satz von Richtlinien entsprechen, die für diesen Index spezifisch sind. Diese Regel überprüft, ob die Indexdefinition eine Eigenschaft mit mehreren Werten namens `tags` aufweisen muss, die den Wert `visualSimilaritySearch` enthält.

#### Nicht konformer Code {#non-compliant-code-damAssetLucene}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
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
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Kundenpakete sollten keine Knoten unter libs erstellen oder ändern {#oakpal-customer-package}

* **Schlüssel**: BannedPath
* **Typ**: Fehler
* **Schweregrad**: Kritisch
* **Seit**: Version 2019.6.0

Gemäß einer bewährten Best Practice sollte die `/libs`-Inhaltsstruktur im Experience Manager-Content-Repository von Kunden als schreibgeschützt konfiguriert werden. Das Ändern von Knoten und Eigenschaften unter `/libs` ist bei großen und kleineren Aktualisierungen mit erheblichen Risiken verbunden. Verwenden Sie Adobe über offizielle Kanäle, um Änderungen an `/libs` vorzunehmen.

### Pakete sollten keine doppelten OSGi-Konfigurationen enthalten {#oakpal-package-osgi}

* **Schlüssel**: DuplicateOsgiConfigurations
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2019.6.0

Ein häufig auftretendes Problem bei komplexen Projekten besteht darin, dass dieselbe OSGi-Komponente mehrfach konfiguriert wurde. Dadurch ist nicht mehr eindeutig, welche Konfiguration gelten soll. Diese Regel beachtet den jeweiligen Ausführungsmodus, da sie nur Probleme erkennt, bei denen dieselbe Komponente mehrmals im gleichen Ausführungsmodus oder in der gleichen Kombination aus Ausführungsmodi konfiguriert ist.

>[!NOTE]
>
>Diese Regel führt zu Problemen, wenn dieselbe Konfiguration unter demselben Pfad in mehreren Paketen definiert ist, einschließlich der Fälle, in denen dasselbe Paket in der Gesamtliste der erstellten Pakete dupliziert ist.
>
>Wenn der Build zum Beispiel Pakete mit den Namen `com.myco:com.myco.ui.apps` und `com.myco:com.myco.all` erstellt, wobei `com.myco:com.myco.ui.apps` in `com.myco:com.myco.all` eingebettet ist, werden alle Konfigurationen innerhalb von `com.myco:com.myco.ui.apps` als Duplikat gemeldet.
>
>Im Allgemeinen entspricht diese Situation nicht den [Richtlinien für die Inhaltspaketstruktur](/help/implementing/developing/introduction/aem-project-content-package-structure.md). In diesem Beispiel fehlt dem Paket `com.myco:com.myco.ui.apps` die Eigenschaft `<cloudManagerTarget>none</cloudManagerTarget>`.

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

### Konfigurations- und Installationsordner sollten nur OSGi-Knoten enthalten {#oakpal-config-install}

* **Schlüssel**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2019.6.0

Aus Sicherheitsgründen sind Pfade, die `/config/` und `/install/` enthalten, nur von Benutzenden mit Administratorrechten in Experience Manager lesbar und sollten nur für OSGi-Konfigurationen und OSGi-Bundles verwendet werden. Wenn Sie andere Inhaltstypen in Pfade platzieren, die diese Segmente enthalten, unterscheidet sich das Anwendungsverhalten unbeabsichtigt zwischen Admin- und Nicht-Admin-Benutzern.

Ein häufig auftretendes Problem ist die Verwendung von Knoten mit der Bezeichnung `config` in Komponentendialogfeldern oder beim Angeben der Rich-Text-Editor-Konfiguration für die Inline-Bearbeitung. Um dieses Problem zu beheben, sollte der fehlerhafte Knoten umbenannt und mit einem kompatiblen Namen versehen werden. Nutzen Sie bei der Rich-Text-Editor-Konfiguration die Eigenschaft `configPath` im Knoten `cq:inplaceEditing`, um den neuen Speicherort anzugeben.

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

### Pakete sollten sich nicht überlappen {#oakpal-no-overlap}

* **Schlüssel**: PackageOverlaps
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2019.6.0

Ähnlich wie bei der Regel [Pakete dürfen keine doppelten OSGi-Konfigurationen enthalten](#oakpal-package-osgi) ist diese Situation ein häufig auftretendes Problem bei komplexen Projekten, bei denen derselbe Knotenpfad von mehreren separaten Inhaltspaketen in geschrieben wird. Die Verwendung von Abhängigkeiten zwischen Inhaltspaketen kann zwar ein konsistentes Ergebnis gewährleisten, doch ist es besser, Überschneidungen ganz zu vermeiden.

### Der standardmäßige Authoring-Modus sollte nicht die klassische Benutzeroberfläche sein {#oakpal-default-authoring}

* **Schlüssel**: ClassicUIAuthoringMode
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Die OSGi-Konfiguration `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` definiert den standardmäßigen Authoring-Modus in Experience Manager. Da die klassische Benutzeroberfläche seit Experience Manager 6.4 nicht mehr unterstützt wird, tritt jetzt ein Problem auf, wenn als standardmäßiger Authoring-Modus die klassische Benutzeroberfläche konfiguriert ist.

### Komponenten mit Dialogfeldern sollten Dialogfelder für die Touch-Benutzeroberfläche haben {#oakpal-components-dialogs}

* **Schlüssel**: ComponentWithOnlyClassicUIDialog
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Experience Manager-Komponenten mit einem Dialogfeld für die klassische Benutzeroberfläche sollten immer über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche verfügen. Beide bieten ein optimales Authoring-Erlebnis, das mit dem Cloud Service-Bereitstellungsmodell kompatibel ist, bei dem die klassische Benutzeroberfläche nicht mehr unterstützt wird. Diese Regel überprüft die folgenden Szenarien:

* Eine Komponente mit einem Dialogfeld für die klassische Benutzeroberfläche (d. h. einem untergeordneten `dialog`-Knoten) muss über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche verfügen (d. h. über einen untergeordneten `cq:dialog`-Knoten).
* Eine Komponente mit einem Design-Dialogfeld für die klassische Benutzeroberfläche (d. h. einem `design_dialog`-Knoten) muss über ein entsprechendes Design-Dialogfeld für die Touch-Benutzeroberfläche verfügen (d. h. über einen untergeordneten `cq:design_dialog`-Knoten).
* Eine Komponente mit einem Dialogfeld für die klassische Benutzeroberfläche und einem Design-Dialogfeld für die klassische Benutzeroberfläche muss sowohl über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche als auch über ein entsprechendes Design-Dialogfeld für die Touch-Benutzeroberfläche verfügen.

Die Dokumentation zu den Experience Manager-Modernisierungs-Tools bietet Dokumentation und Tools zum Konvertieren von Komponenten aus der klassischen Benutzeroberfläche in die Touch-Benutzeroberfläche. Weitere Details finden Sie in der [Dokumentation zu den Experience Manager-Modernisierungs-Tools](https://opensource.adobe.com/aem-modernize-tools/).

### In Paketen sollten veränderliche und unveränderliche Inhalte nicht gemischt werden {#oakpal-packages-immutable}

* **Schlüssel**: ImmutableMutableMixedPackage
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Um mit dem Cloud Service-Bereitstellungsmodell kompatibel zu sein, müssen einzelne Inhaltspakete entweder Inhalte für die unveränderlichen Bereiche des Repositorys (d. h. `/apps` und `/libs`) oder den veränderlichen Bereich (d. h. alles, was nicht in `/apps` oder `/libs` ist) enthalten, aber nicht beides. Beispielsweise ist ein Paket, das sowohl `/apps/myco/components/text` als auch `/etc/clientlibs/myco` enthält, nicht mit Cloud Service kompatibel und führt dazu, dass ein Problem gemeldet wird.

>[!NOTE]
>
>Die Regel [Kundenpakete sollten keine Knoten unter libs](#oakpal-customer-package) erstellen oder ändern.

Weitere Details finden Sie unter [Experience Manager-Projektstruktur](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

### Verwenden Sie keine Agenten für Rückwärtsreplikation {#oakpal-reverse-replication}

* **Schlüssel**: ReverseReplication
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Die Unterstützung für die Rückwärtsreplikation ist in Cloud-Service-Bereitstellungen nicht verfügbar, wie in den [Versionshinweisen](/help/release-notes/aem-cloud-changes.md#replication-agents) zu Experience Manager as a Cloud Service beschrieben.

Kunden, die die Rückwärtsreplikation verwenden, sollten sich für alternative Lösungen an Adobe wenden.

### In Proxy-fähigen Client-Bibliotheken enthaltene Ressourcen sollten sich in einem Ordner mit dem Namen „resources“ befinden {#oakpal-resources-proxy}

* **Schlüssel**: ClientlibProxyResource
* **Typ**: Fehler
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Experience Manager-Client-Bibliotheken können statische Ressourcen wie Bilder und Schriftarten enthalten. Wie im Dokument [Verwenden von Präprozessoren](/help/implementing/developing/introduction/clientlibs.md#using-preprocessors) beschrieben, müssen diese statischen Ressourcen bei der Verwendung von geproxidierten Client-Bibliotheken in einem untergeordneten Ordner namens `resources` enthalten sein, damit sie effektiv auf den Veröffentlichungsinstanzen referenziert werden können.

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

### Verwenden von mit Cloud Service inkompatiblen Workflow-Prozessen {#oakpal-usage-cloud-service}

* **Schlüssel**: CloudServiceIncompatibleWorkflowProcess
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2021.2.0

Mit der Umstellung auf Asset-Microservices für die Asset-Verarbeitung in Adobe Experience Manager as a Cloud Service werden jetzt mehrere Workflow-Prozesse, die in On-Premise- und AMS-Versionen verwendet werden, nicht mehr unterstützt. Viele dieser Workflows sind ebenfalls überflüssig geworden.

Mit dem Migrations-Tool im [GitHub-Repository für Experience Manager as a Cloud Service-Assets](https://github.com/adobe/aem-cloud-migration) können Workflow-Modelle während der Migration in Experience Manager as a Cloud Service aktualisiert werden.

### Es wird empfohlen anstelle von statischen Vorlagen bearbeitbare Vorlagen zu verwenden. {#oakpal-static-template}

* **Schlüssel**: StaticTemplateUsage
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Auch wenn die Verwendung statischer Vorlagen in Experience Manager-Projekten früher üblich war, empfiehlt Adobe bearbeitbare Vorlagen zu verwenden, da sie die beste Flexibilität bieten und zusätzliche Funktionen besitzen, die in statischen Vorlagen nicht vorhanden sind. Weitere Informationen finden Sie im Dokument [Seitenvorlagen](/help/implementing/developing/components/templates.md).

Die Migration von statischen zu bearbeitbaren Vorlagen kann mithilfe des [Experience Manager-Modernisierungs-Tools](https://opensource.adobe.com/aem-modernize-tools/) weitgehend automatisiert werden.

### Die Verwendung veralteter Foundation-Komponenten wird nicht empfohlen {#oakpal-usage-legacy}

* **Schlüssel**: LegacyFoundationComponentUsage
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Die veralteten Foundation-Komponenten (d. h. Komponenten unter `/libs/foundation`) werden seit mehreren Versionen von Experience Manager nicht mehr verwendet und wurden durch die Kernkomponenten ersetzt. Von der Verwendung der Foundation-Komponenten als Basis für benutzerdefinierte Komponenten – sei es durch Überlagerung oder Vererbung – wird abgeraten. Sie sollten in die entsprechende Kernkomponente konvertiert werden.

[Experience Manager-Modernisierungs-Tools](https://opensource.adobe.com/aem-modernize-tools/) können diese Konvertierung erleichtern.

### Verwenden Sie nur unterstützte Ausführungsmodusnamen und -reihenfolgen {#oakpal-supported-runmodes}

* **Schlüssel**: SupportedRunmode
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Experience Manager as a Cloud Service erzwingt eine strikte Benennungsrichtlinie für Ausführungsmodusnamen und eine strikte Reihenfolge für diese Ausführungsmodi. Die Liste der unterstützten Ausführungsmodi wird im Dokument [Bereitstellen auf Experience Manager as a Cloud Service](/help/implementing/deploying/overview.md#runmodes) begründet und jede Abweichung von dieser Liste wird als Problem identifiziert.

### Knoten für benutzerdefinierte Suchindex-Definitionen müssen direkt untergeordnete Knoten von `/oak:index` sein {#oakpal-custom-search}

* **Schlüssel**: OakIndexLocation
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Experience Manager as a Cloud Service verlangt, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten vom Typ `oak:QueryIndexDefinition`) direkt untergeordnete Knoten von `/oak:index` sein müssen. Indizes in anderen Speicherorten müssen so verschoben werden, dass sie mit Experience Manager as a Cloud Service kompatibel sind. Weitere Informationen zu Suchindizes finden Sie im Dokument [Inhaltssuche und -indizierung](/help/operations/indexing.md).

### Knoten für benutzerdefinierte Suchindex-Definitionen benötigen eine compatVersion von 2 {#oakpal-custom-search-compatVersion}

* **Schlüssel**: IndexCompatVersion
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Experience Manager as a Cloud Service erfordert, dass die Eigenschaft `compatVersion` für benutzerdefinierte Suchindex-Definitionen (wie Knoten vom Typ `oak:QueryIndexDefinition`) auf `2` festgelegt wird. Adobe Experience Manager as a Cloud Service unterstützt keine anderen Werte. Weitere Informationen zu Suchindizes finden Sie unter [Inhaltssuche und -indizierung](/help/operations/indexing.md) .

### Untergeordnete Knoten von benutzerdefinierten Suchindex-Definitionsknoten müssen dem Typ `nt:unstructured ` entsprechen{#oakpal-descendent-nodes}

* **Schlüssel**: IndexDescendantNodeType
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Schwer behebbare Probleme können auftreten, wenn ein Knoten einer benutzerdefinierten Suchindex-Definition unstrukturierte untergeordnete Knoten enthält. Um diese Situation zu vermeiden, sollten alle untergeordneten Knoten eines `oak:QueryIndexDefinition`-Knotens dem Typ `nt:unstructured` sein.

### Knoten einer benutzerdefinierten Suchindex-Definition müssen einen untergeordneten Knoten mit dem Namen indexRules enthalten, der wiederum untergeordnete Knoten enthält {#oakpal-custom-search-index}

* **Schlüssel**: IndexRulesNode
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Ein ordnungsgemäß definierter benutzerdefinierter Suchindex-Definitionsknoten muss einen untergeordneten Knoten namens `indexRules` enthalten, der wiederum mindestens ein untergeordnetes Element aufweisen muss. Weitere Informationen finden Sie in der [Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### Knoten für benutzerdefinierte Suchindex-Definitionen müssen Benennungskonventionen folgen {#oakpal-custom-search-definitions}

* **Schlüssel**: IndexName
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Experience Manager as a Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) nach einem bestimmten Muster benannt werden, das im Dokument [Inhaltssuche und -indizierung](/help/operations/indexing.md) beschrieben wird.

### Knoten für benutzerdefinierte Suchindex-Definitionen müssen den Indextyp Lucene verwenden {#oakpal-index-type-lucene}

* **Schlüssel**: IndexType
* **Typ**: Fehler
* **Schweregrad**: Blocker
* **Seit**: Version 2021.2.0 (Änderung von Typ und Schweregrad in 2021.8.0)

Experience Manager as a Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten vom Typ `oak:QueryIndexDefinition`) eine `type`-Eigenschaft mit dem definierten Wert `lucene` aufweisen. Die Indizierung mit veralteten Indextypen muss vor der Migration auf Experience Manager as a Cloud Service aktualisiert werden. Weitere Informationen finden Sie unter [Inhaltssuche und -indizierung](/help/operations/indexing.md#how-to-use).

### Knoten einer benutzerdefinierten Suchindex-Definition dürfen keine Eigenschaft namens „seed“ enthalten {#oakpal-property-name-seed}

* **Schlüssel**: IndexSeedProperty
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Experience Manager as a Cloud Service verbietet es, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten vom Typ `oak:QueryIndexDefinition`) eine Eigenschaft mit dem Namen `seed` enthalten. Die Indizierung mit dieser Eigenschaft muss vor der Migration auf Experience Manager as a Cloud Service aktualisiert werden. Weitere Informationen finden Sie im Dokument [Inhaltssuche und -indizierung](/help/operations/indexing.md#how-to-use).

### Knoten für die benutzerdefinierte Suchindex-Definition dürfen keine Eigenschaft namens „reindex“ enthalten  {#oakpal-reindex-property}

* **Schlüssel**: IndexReindexProperty
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Experience Manager as a Cloud Service verbietet es, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten vom Typ `oak:QueryIndexDefinition`) eine Eigenschaft mit dem Namen `reindex` enthalten. Die Indizierung mit dieser Eigenschaft muss vor der Migration auf Experience Manager as a 
Cloud Service aktualisiert werden. Weitere Informationen finden Sie im Dokument [Inhaltssuche und -indizierung](/help/operations/indexing.md#how-to-use).

### Benutzerdefinierte DAM-Asset-Lucene-Knoten dürfen nicht `queryPaths` angeben {#oakpal-damAssetLucene-queryPaths}

* **Schlüssel**: IndexDamAssetLucene
* **Typ**: Fehler
* **Schweregrad**: Blocker
* **Seit**: Version 2022.1.0

#### Nicht konformer Code {#non-compliant-code-damAssetLucene-queryPaths}

```text
+ oak:index
    + damAssetLucene-1-custom-1
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: [/content/dam]
      - queryPaths: [/content/dam]
      - type: lucene
      + tika
        + config.xml
```

#### Konformer Code {#compliant-code-damAssetLucene-queryPaths}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: [/content/dam]
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Wenn die Definition des benutzerdefinierten Suchindex `compatVersion` enthält, muss sie auf 2 gesetzt werden {#oakpal-compatVersion}

* **Schlüssel**: IndexCompatVersion
* **Typ**: Code Smell
* **Schweregrad**: Hoch
* **Seit**: Version 2022.1.0


### Der Indexknoten, der `includedPaths` angibt, sollte auch `queryPaths` mit denselben Werten angeben {#oakpal-included-paths-without-query-paths}

* **Schlüssel**: IndexIncludedPathsWithoutQueryPaths
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2023.1.0

Konfigurieren Sie für benutzerdefinierte Indizes `includedPaths` und `queryPaths` mit identischen Werten. Wenn einer angegeben ist, muss der andere damit übereinstimmen. Es gibt jedoch einen Sonderfall für Indizes von `damAssetLucene`, einschließlich der benutzerdefinierten Versionen. Geben Sie für diese Fälle nur `includedPaths` an.

### Indexknoten, die `nodeScopeIndex` für den generischen Knotentyp angeben, sollten auch `includedPaths` und `queryPaths` angeben {#oakpal-full-text-on-generic-node-type}

* **Schlüssel**: IndexFulltextOnGenericType
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2023.1.0

Wenn Sie die Eigenschaft `nodeScopeIndex` für einen „generischen“ Knotentyp wie `nt:unstructured` oder `nt:base` festlegen, müssen Sie auch die Eigenschaften `includedPaths` und `queryPaths` angeben.
Der Knotentyp &quot;`nt:base`&quot; kann als &quot;generisch&quot;betrachtet werden, da alle Knotentypen von ihm erben. Wenn Sie also `nodeScopeIndex` auf `nt:base` festlegen, werden alle Knoten im Repository indexiert. Ebenso wird auch `nt:unstructured` als „generisch“ betrachtet, da es in Repositorys viele Knoten mit diesem Typ gibt.

#### Nicht konformer Code {#non-compliant-code-full-text-on-generic-node-type}

```text
+ oak:index/acme.someIndex-custom-1
  - async: [async, nrt]
  - evaluatePathRestrictions: true
  - tags: [visualSimilaritySearch]
  - type: lucene
    + indexRules
      - jcr:primaryType: nt:unstructured
      + nt:base
        - jcr:primaryType: nt:unstructured
        + properties
          + acme.someIndex-custom-1
            - nodeScopeIndex: true
```

#### Konformer Code {#compliant-code-full-text-on-generic-node-type}

```text
+ oak:index/acme.someIndex-custom-1
  - async: [async, nrt]
  - evaluatePathRestrictions: true
  - tags: [visualSimilaritySearch]
  - type: lucene
  - includedPaths: ["/content/dam/"] 
  - queryPaths: ["/content/dam/"]
    + indexRules
      - jcr:primaryType: nt:unstructured
      + nt:base
        - jcr:primaryType: nt:unstructured
        + properties
          + acme.someIndex-custom-1
            - nodeScopeIndex: true
```

### Die Eigenschaft queryLimitReads der Abfrage-Engine sollte nicht überschrieben werden. {#oakpal-query-limit-reads}

* **Schlüssel**: OverrideOfQueryLimitReads
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2023.1.0

Das Überschreiben des Standardwerts kann dazu führen, dass Seitenaufrufe zu langsam erfolgen, insbesondere wenn mehr Inhalt hinzugefügt wird.

### Mehrere aktive Versionen desselben Index {#oakpal-multiple-active-versions}

* **Schlüssel**: IndexDetectMultipleActiveVersionsOfSameIndex
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2023.1.0

#### Nicht konformer Code {#non-compliant-code-multiple-active-versions}

```text
+ oak:index
  + damAssetLucene-1-custom-1
    ...
  + damAssetLucene-1-custom-2
    ...
  + damAssetLucene-1-custom-3
    ...
```

#### Konformer Code {#compliant-code-multiple-active-versions}

```text
+ damAssetLucene-1-custom-3
    ...
```


### Der Name vollständig benutzerdefinierter Indexdefinitionen sollte den offiziellen Richtlinien entsprechen. {#oakpal-fully-custom-index-name}

* **Schlüssel**: IndexValidFullyCustomName
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2023.1.0

Das erwartete Muster für vollständig benutzerdefinierte Indexnamen lautet: `[prefix].[indexName]-custom-[version]`. Weitere Informationen finden Sie im Dokument [Inhaltssuche und -indizierung](/help/operations/indexing.md).

### Dieselbe Eigenschaft mit unterschiedlichen analysierten Werten in derselben Indexdefinition {#oakpal-same-property-different-analyzed-values}

#### Nicht konformer Code {#non-compliant-code-same-property-different-analyzed-values}

```text
+ indexRules
  + dam:Asset
    + properties
      + status
        - name: status
        - analyzed: true
  + dam:cfVariationNode
    + properties
      + status
        - name: status
```

#### Konformer Code {#compliant-code-same-property-different-analyzed-values}

Beispiel:

```text
+ indexRules
  + dam:Asset
    + properties
      + status
        - name: status
        - analyzed: true
  + dam:cfVariationNode
    + properties
      + status
        - name: status
        - analyzed: true
```

Beispiel:

```text
+ indexRules
  + dam:Asset
    + properties
      + status
        - name: status
  + dam:cfVariationNode
    + properties
      + status
        - name: status
        - analyzed: true
```

Wenn die analysierte Eigenschaft nicht explizit festgelegt ist, lautet der Standardwert false.

### Tags-Eigenschaft {#tags-property}

* **Schlüssel**: IndexHasValidTagsProperty
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2023.1.0

Achten Sie bei bestimmten Indizes darauf, die Tags-Eigenschaft und die aktuellen Werte beizubehalten. Das Hinzufügen neuer Werte zur Tags-Eigenschaft ist zwar zulässig, das Löschen vorhandener Werte (oder der Eigenschaft insgesamt) kann jedoch zu unerwarteten Ergebnissen führen.

### Indexdefinitionsknoten dürfen nicht im Inhaltspaket der Benutzeroberfläche bereitgestellt werden {#oakpal-ui-content-package}

* **Schlüssel**: IndexNotUnderUIContent
* **Typ**: Verbesserung
* **Schweregrad**: Gering
* **Seit**: Version 2024.6.0

AEM Cloud Service verbietet die Bereitstellung benutzerdefinierter Suchindex-Definitionen (Knoten vom Typ `oak:QueryIndexDefinition`) im Inhaltspaket der Benutzeroberfläche.

>[!WARNING]
>
>Sie sollten dieses Problem so bald wie möglich beheben, da es Pipeline-Fehler verursachen kann, die mit der Version [Cloud Manager August 2024](/help/implementing/cloud-manager/release-notes/current.md) beginnen.

### Benutzerdefinierte Volltext-Indexdefinition des Typs damAssetLucene muss korrekt mit dem Präfix &#39;damAssetLucene&#39; versehen werden {#oakpal-dam-asset-lucene}

* **Schlüssel**: CustomFulltextIndexesOfTheDamAssetCheck
* **Typ**: Verbesserung
* **Schweregrad**: Gering
* **Seit**: Version 2024.6.0

AEM Cloud Service verbietet es, benutzerdefinierte Volltext-Indexdefinitionen des Typs `damAssetLucene` mit anderen Präfixen als `damAssetLucene` zu versehen.

>[!WARNING]
>
>Beheben Sie dieses Problem so bald wie möglich, da es Pipeline-Fehler verursachen kann, die mit der Version [Cloud Manager August 2024](/help/implementing/cloud-manager/release-notes/current.md) beginnen.

### Indexdefinitionsknoten dürfen keine Eigenschaften mit demselben Namen enthalten {#oakpal-index-property-name}

* **Schlüssel**: DuplicateNameProperty
* **Typ**: Verbesserung
* **Schweregrad**: Gering
* **Seit**: Version 2024.6.0

AEM Cloud Service verbietet es, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) Eigenschaften mit demselben Namen enthalten.

>[!WARNING]
>
>Beheben Sie dieses Problem so bald wie möglich, da es Pipeline-Fehler verursachen kann, die mit der Version [Cloud Manager August 2024](/help/implementing/cloud-manager/release-notes/current.md) beginnen.

### Das Anpassen bestimmter vorkonfigurierter Indexdefinitionen ist verboten {#oakpal-customizing-ootb-index}

* **Schlüssel**: RestrictIndexCustomization
* **Typ**: Verbesserung
* **Schweregrad**: Gering
* **Seit**: Version 2024.6.0

AEM Cloud Service verbietet unbefugte Änderungen der folgenden vorkonfigurierten Indizes:

* `nodetypeLucene`
* `slingResourceResolver`
* `socialLucene`
* `appsLibsLucene`
* `authorizables`
* `pathReference`

>[!WARNING]
>
>Beheben Sie dieses Problem so bald wie möglich, da es Pipeline-Fehler verursachen kann, die mit der Version [Cloud Manager August 2024](/help/implementing/cloud-manager/release-notes/current.md) beginnen.

### Die Konfiguration der Tokenizer in Analyzern sollte mit dem Namen &#39;tokenizer&#39; erstellt werden {#oakpal-tokenizer}

* **Schlüssel**: AnalyzerTokenizerConfigCheck
* **Typ**: Verbesserung
* **Schweregrad**: Gering
* **Seit**: Version 2024.6.0

AEM Cloud Service verbietet die Erstellung von Tokenizern mit falschen Namen in Analyzern. Tokenizer sollten immer als `tokenizer` definiert werden.

>[!WARNING]
>
>Beheben Sie dieses Problem so bald wie möglich, da es Pipeline-Fehler verursachen kann, die mit der Version [Cloud Manager August 2024](/help/implementing/cloud-manager/release-notes/current.md) beginnen.

### Die Konfiguration von Indexdefinitionen darf keine Leerzeichen enthalten {#oakpal-indexing-definitions-spaces}

* **Schlüssel**: PathSpacesCheck
* **Typ**: Verbesserung
* **Schweregrad**: Gering
* **Seit**: Version 2024.7.0

AEM Cloud Service verbietet die Erstellung von Indexdefinitionen, die Eigenschaften mit Leerzeichen enthalten.
