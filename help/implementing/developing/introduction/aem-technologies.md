---
title: AEM Technische Stiftungen
description: Eine Übersicht über die technischen Grundlagen von AEM, einschließlich der Art und Weise, wie AEM strukturiert und grundlegende Technologien wie JCR, Sling und OSGi sind.
translation-type: tm+mt
source-git-commit: 750fded1564de2b11f6c104cc70befc4453405b4
workflow-type: tm+mt
source-wordcount: '2187'
ht-degree: 39%

---


# AEM Technische Stiftungen {#aem-technical-foundations}

AEM ist eine robuste Plattform, die auf bewährten, skalierbaren und flexiblen Technologien basiert. Dieses Dokument gibt einen detaillierten Überblick über die verschiedenen Teile, aus denen AEM bestehen, und ist als technischer Anhang für einen AEM-Entwickler gedacht. Es ist nicht als Anleitung zum Einstieg gedacht. Wenn Sie neu bei AEM Entwicklung sind, konsultieren Sie als ersten Schritt das [Erste Schritte mit der Entwicklung von AEM Sites - WKND Tutorial](develop-wknd-tutorial.md) .

>[!TIP]
>
>Bevor Sie in die Kerntechnologien von AEM tauchen, empfiehlt Adobe die Fertigstellung des [Erste Schritte AEM Sites - WKND Tutorials.](develop-wknd-tutorial.md)

## Fundamentals {#fundamentals}

Als modernes Content-Management-System setzt AEM auf Standard-Webtechnologien:

* Der Zyklus &quot;request-response&quot;(XMLHttpRequest/XMLHttpResponse)
* HTML
* CSS
* JavaScript

Die zugrunde liegenden Ebenen für Content Repository und Geschäftslogik basieren auf Java-Technologien:

* JCR
* Sling
* OSGi-

## Java Content Repository {#java-content-repository}

Der Java Content Repository-Standard [JSR 283](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/index.html) legt eine herstellerunabhängige und implementierungsunabhängige Methode für den bidirektionalen Zugriff auf Inhalte auf einer granularen Ebene in einem Content-Repository fest. Der Leiter der Spezifikation ist bei der Adobe Research (Switzerland) AG angesiedelt.

Das [JCR API 2.0](https://docs.adobe.com/docs/en/spec/javax.jcr/javadocs/jcr-2.0/index.html) -Paket `javax.jcr.*` wird für den direkten Zugriff und die Bearbeitung von Repository-Inhalten verwendet.

AEM basiert auf einem JCR.

## Apache Jackrabbit Oak {#jackrabbit-oak}

[Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/) ist eine Implementierung eines skalierbaren und hochleistungsfähigen hierarchischen Inhalts-Repositorys, das als Grundlage für moderne Websites und andere anspruchsvolle Content-Anwendungen von Weltklasse verwendet werden kann und dem JCR-Standard entspricht.

Jackrabbit Oak (auch als Oak bezeichnet) ist die Implementierung des JCR-Standards, auf dem AEM aufgebaut ist.

## Sling-Anforderungsverarbeitung {#sling-request-processing}

AEM basiert auf [Sling](https://sling.apache.org/site/index.html), einem auf REST-Prinzipien basierenden Webanwendungs-Framework, das eine einfache Entwicklung von inhaltsorientierten Anwendungen ermöglicht. Sling verwendet ein JCR-Repository wie Apache Jackrabbit Oak als Datenspeicher. Sling ist Teil der Apache Software Foundation - weitere Informationen finden Sie unter Apache.

### Einführung in Sling {#introduction-to-sling}

Bei Verwendung von Sling ist der Typ des zu rendernden Inhalts nicht die erste Verarbeitungsüberlegung. Stattdessen ist die Hauptüberlegung, ob die URL zu einem Inhaltsobjekt aufgelöst wird, für das dann ein Skript gefunden werden kann, um das Rendering durchzuführen. Dies bietet Autoren von Web-Inhalten eine hervorragende Unterstützung beim Erstellen von Seiten, die leicht an ihre Anforderungen angepasst werden können.

Die Vorteile dieser Flexibilität zeigen sich in Anwendungen mit einer großen Auswahl verschiedener Inhaltselemente oder wenn Sie Seiten benötigen, die einfach angepasst werden können. Insbesondere bei der Implementierung eines Web-Content-Management-Systems wie AEM.

See [Discover Sling in 15 minutes](https://sling.apache.org/documentation/getting-started/discover-sling-in-15-minutes.html) for the first steps for developing with Sling.

Das folgende Diagramm erläutert die Sling-Skriptauflösung: Es wird gezeigt, wie Sie von der HTTP-Anforderung zum Inhaltsknoten, vom Inhaltsknoten zum Ressourcentyp, vom Ressourcentyp zum Skript gelangen und welche Skriptvariablen verfügbar sind.

![Verstehen der Auflösung des Apache Sling-Skripts](assets/sling-cheatsheet-01.png)

The following diagram explains all the hidden, but powerful, request parameters you can use when dealing with the `SlingPostServlet`, the default handler for all POST requests that gives you endless options for creating, modifying, deleting, copying and moving nodes in the repository.

![Verwenden des SlingPostServlet](assets/sling-cheatsheet-02.png)

### Sling ist inhaltszentriert {#sling-is-content-centric}

Sling ist *inhaltszentriert*. Dies bedeutet, dass sich die Verarbeitung auf den Inhalt konzentriert, da jede (HTTP-)Anforderung auf den Inhalt in Form einer JCR-Ressource (eines Repository-Knotens) abgebildet wird:

* Das erste Ziel ist die Ressource (JCR-Knoten), die die Inhalte enthält
* Zweitens befindet sich die Darstellung oder das Skript in Verbindung mit bestimmten Teilen der Anforderung aus den Ressourceneigenschaften (z. B. Selektoren und/oder Erweiterung)

### RESTful Sling {#restful-sling}

Sling setzt aufgrund seiner inhaltlichen Philosophie einen REST-orientierten Server ein und bietet damit ein neues Konzept in Web-Applikationsrahmen. Die Vorteile sind:

* Sehr RESTful, nicht nur an der Oberfläche; Ressourcen und Darstellungen werden im Server korrekt modelliert
* Entfernt ein oder mehrere Datenmodelle
   * Andere Content-Management-Frameworks erfordern möglicherweise URL-Struktur, Geschäftsobjekte und DB-Schema, um auf eine Ressource zuzugreifen.
   * Bei Verwendung von Sling ist dies auf Folgendes reduziert: URL = Ressource = JCR-Struktur

### URL-Zerlegung {#url-decomposition}

In Sling wird die Verarbeitung durch die URL der Benutzeranforderung gesteuert. Dies definiert den Inhalt, der von den entsprechenden Skripten angezeigt werden soll. Um dies zu erreichen, werden die Informationen aus der URL extrahiert.

Wenn wir die folgende URL analysieren:

```text
https://myhost/tools/spy.printable.a4.html/a/b?x=12
```

können wir sie in ihre zusammengesetzten Teile zerlegen:

| protocol | host |  | content path | selector(s) | extension |  | suffix |  | param(s) |
|---|---|---|---|---|---|---|---|---|---|
| `https://` | `myhost` | `/` | `tools/spy` | `.printable.a4.` | `html` | `/` | `a/b` | `?` | `x=12` |

* **Protokoll** - HTTPS
* **host** - Domäne der Site
* **Inhaltspfad** : Pfad, der den zu rendernden Inhalt angibt und in Kombination mit der Erweiterung verwendet wird; in diesem Beispiel übersetzen sie `tools/spy.html`
* **Auswahl(en)** - Wird für alternative Methoden zur Wiedergabe des Inhalts verwendet; in diesem Beispiel eine druckerfreundliche Version im Format A4
* **extension** - Inhaltsformat gibt auch das für die Wiedergabe zu verwendende Skript an
* **Suffix** - Kann zur Angabe zusätzlicher Informationen verwendet werden
* **param(s)** - Alle für dynamischen Inhalt erforderlichen Parameter

#### Von URL zu Inhalt und Skripten {#from-url-to-content-and-scripts}

Verwenden der Prinzipien der URL-Auflösung:

* Die Zuordnung verwendet den aus der Anforderung extrahierten Inhaltspfad, um die Ressource zu suchen.
* Wenn sich die entsprechende Ressource befindet, wird der Sling-Ressourcentyp extrahiert und verwendet, um das Skript zu finden, das für die Wiedergabe des Inhalts verwendet werden soll.

Die folgende Abbildung zeigt den verwendeten Mechanismus, der in den folgenden Abschnitten ausführlicher erörtert wird.

![URL-Zuordnungsmechanismus](assets/url-mapping.png)

With Sling, you specify which script renders a certain entity (by setting the `sling:resourceType` property in the JCR node). Dieser Mechanismus bietet mehr Freiheit als einer, in dem das Skript auf die Datenentitäten zugreift (wie es eine SQL-Anweisung in einem PHP-Skript tun würde), da eine Ressource mehrere Darstellungen haben kann.

#### Mapping Requests to Resources {#mapping-requests-to-resources}

Die Anfrage wird zerlegt und die notwendigen Informationen werden extrahiert. Das Repository wird nach der angeforderten Ressource (Inhaltsknoten) durchsucht:

* First Sling checks whether a node exists at the location specified in the request; e.g. `../content/corporate/jobs/developer.html`
* If no node is found, the extension is dropped and the search repeated; e.g. `../content/corporate/jobs/developer`
* Wenn kein Knoten gefunden wird, gibt Sling den http-Code 404 (Nicht gefunden) zurück.

Sling erlaubt auch anderen Elementen als JCR-Knoten, als Ressourcen zu fungieren, dies ist jeodch eine erweiterte Funktion.

### Locating the Script {#locating-the-script}

Wenn die entsprechende Ressource (Inhaltsknoten) gefunden wird, wird der **Sling-Ressourcentyp** extrahiert. Dies ist ein Pfad, der das Skript findet, das zum Rendern des Inhalts verwendet wird.

The path specified by the `sling:resourceType` can be either:

* Absolut
* Relativ zu einem Konfigurationsparameter

>[!TIP]
>
>Relative Pfade werden von der Adobe empfohlen, da sie die Portabilität erhöhen.

Alle Sling-Skripten werden in Unterordnern von `/apps` (veränderliche, benutzerdefinierte Skripten) oder `/libs` (unveränderliche, systemspezifische Skripten) gespeichert, die in dieser Reihenfolge durchsucht werden.

Einige andere zu beachtende Punkte sind:

* When the method (GET, POST) is required, it will be specified in uppercase as according to the HTTP specification e.g. `jobs.POST.esp`
* Verschiedene Skriptmaschinen werden unterstützt, die gebräuchlichen, empfohlenen Skripten sind jedoch HTL und JavaScript.

The list of script engines supported by the given instance of AEM are listed on the Felix Management Console ( `http://<host>:<port>/system/console/slingscripting`).

Using the previous example, if the `sling:resourceType` is `hr/jobs` then for:

* GET/HEAD-Anforderungen und URLs, die in `.html` (Standard-Anforderungstypen, Standardformat) enden
   * Das Skript wird `/apps/hr/jobs/jobs.esp`verwendet. im letzten Abschnitt der `sling:resourceType` Formulare der Dateiname.
* Anforderungen an die POST (alle Anforderungstypen außer GET/HEAD, der Methodenname muss in Großbuchstaben angegeben werden)
   * POST wird im Skriptnamen verwendet.
   * The script will be `/apps/hr/jobs/jobs.POST.esp`.
* URLs in anderen Formaten, die nicht mit `.html`
   * Beispiel `../content/corporate/jobs/developer.pdf`
   * Das Skript wird `/apps/hr/jobs/jobs.pdf.esp`verwendet. Das Suffix wird dem Skriptnamen hinzugefügt.
* URLs mit Selektoren
   * Selektoren können verwendet werden, um denselben Inhalt in einem alternativen Format anzuzeigen. Zum Beispiel eine druckerfreundliche Version, einen RSS-Feed oder eine Zusammenfassung.
   * Wenn wir uns eine druckerfreundliche Version ansehen, in der der Selektor angezeigt werden könnte `print`; wie in `../content/corporate/jobs/developer.print.html`
   * Das Skript wird `/apps/hr/jobs/jobs.print.esp`verwendet. Der Selektor wird dem Skriptnamen hinzugefügt.
* If no `sling:resourceType` has been defined then:
   * The content path will be used to search for an appropriate script (if the path based `ResourceTypeProvider` is active).
   * For example, the script for `../content/corporate/jobs/developer.html` would generate a search in `/apps/content/corporate/jobs/`.
   * Der primäre Knotentyp wird verwendet.
* Wenn kein Skript gefunden wird, wird das Standard-Skript verwendet.
   * The default rendition is currently supported as plain text (`.txt`), HTML (`.html`) and JSON (`.json`), all of which will list the node&#39;s properties (suitably formatted). The default rendition for the extension `.res`, or requests without a request extension, is to spool the resource (where possible).
* Für die HTTP-Fehlerbehandlung (Codes 403 oder 404) sucht Sling nach einem Skript, entweder:
   * Speicherort `/apps/sling/servlet/errorhandler` für benutzerdefinierte Skripten
   * Oder der Speicherort des Standardskripts `/libs/sling/servlet/errorhandler/404.jsp`

Wenn mehrere Skripte für eine bestimmte Anfrage gelten, wird das Skript mit der besten Übereinstimmung ausgewählt. Je genauer eine Übereinstimmung ist, desto besser ist sie; Mit anderen Worten: je mehr Selektorübereinstimmungen, desto besser, unabhängig von einer Anfrageerweiterung oder einer Übereinstimmung des Methodennamens.

Beispiel: Eine Anforderung zum Zugriff auf die Ressource

* `/content/corporate/jobs/developer.print.a4.html`

vom Typ

* `sling:resourceType="hr/jobs"`

Angenommen, wir haben die folgende Liste von Skripten am richtigen Speicherort:

1. `GET.esp`
1. `jobs.esp`
1. `html.esp`
1. `print.esp`
1. `print.html.esp`
1. `print/a4.esp`
1. `print/a4/html.esp`
1. `print/a4.html.esp`

Dann wäre die Reihenfolge der Bevorzugung (8) - (7) - (6) - (5) - (4) - (3) - (2) - (1).

Zusätzlich zu den Ressourcentypen (primär definiert durch die Eigenschaft `sling:resourceType`) gibt es auch den Super-Typ der Ressource. This is generally indicated by the `sling:resourceSuperType` property. Diese Supertypen werden ebenfalls berücksichtigt, wenn Sie versuchen, ein Skript zu finden. Der Vorteil von Ressourcensupertypen besteht darin, dass sie eine Hierarchie von Ressourcen bilden können, wobei der Standard-Ressourcentyp `sling/servlet/default` (von den Standard-Servlets verwendet) effektiv der Stamm ist.

Der Ressourcensupertyp einer Ressource kann auf zwei Arten definiert werden:

* by the `sling:resourceSuperType` property of the resource.
* by the `sling:resourceSuperType` property of the node to which the `sling:resourceType` points.

Beispiel:

* `/`
   * `a`
   * `b`
      * `sling:resourceSuperType = a`
   * `c`
      * `sling:resourceSuperType = b`
   * `x`
      * `sling:resourceType = c`
   * `y`
      * `sling:resourceType = c`
      * `sling:resourceSuperType = a`

Die Typhierarchie von:

* `/x`
   * Is `[ c, b, a, <default>]`
* while for `/y`
   * Die Hierarchie ist `[ c, a, <default>]`

This is because `/y` has the `sling:resourceSuperType` property whereas `/x` does not and therefore its supertype is taken from its resource type.

#### Sling Scripts Cannot be Called Directly {#sling-scripts-cannot-be-called-directly}

In Sling können Skripte nicht direkt aufgerufen werden, da dies das strenge Konzept eines REST-Servers sprengen würde. Sie würden Ressourcen und Repräsentationen mischen.

Wenn Sie die Repräsentation (das Skript) direkt aufrufen, blenden Sie die Ressource in Ihrem Skript aus, sodass das Framework (Sling) nicht mehr davon weiß. Somit verlieren Sie bestimmte Eigenschaften:

* Automatische Verarbeitung von HTTP-Methoden außer GET, einschließlich:
   * POST, PUT, DELETE, die mit einer Sling-Standardimplementierung behandelt werden
   * Das `POST.jsp` Skript an Ihrem `sling:resourceType` Speicherort
* Ihre Codearchitektur ist nicht mehr so sauber und klar strukturiert, wie es sein sollte. von größter Bedeutung für die Entwicklung im großen Maßstab

### Sling-API {#sling-api}

Dabei werden das Sling API-Paket `org.apache.sling.*`und Tag-Bibliotheken verwendet.

### Referenzieren von vorhandenen Elementen mithilfe von sling:include {#referencing-existing-elements-using-sling-include}

Eine letzte Überlegung ist die Notwendigkeit, auf vorhandene Elemente innerhalb der Skripte zu verweisen.

More complex scripts (aggregating scripts) might need to access multiple resources (for example navigation, sidebar, footer, elements of a list) and do so by including the *resource*.

Dazu können Sie den `sling:include("/<path>/<resource>")` Befehl verwenden. Dies umfasst effektiv die Definition der referenzierten Ressource.

## OSGi-{#osgi}

OSGi (Open Services Gateway Initiative) definiert eine Architektur zur Entwicklung und Bereitstellung modularer Anwendungen und Bibliotheken (auch als dynamisches Modulsystem für Java bezeichnet). OSGi-Container erlauben es Ihnen, Ihre Anwendung in einzelne Module aufzuteilen (JAR-Dateien mit zusätzlichen Metainformationen und sogenannten Bundles in OSGi-Terminologie) und die Querabhängigkeiten zwischen ihnen zu verwalten mit:

* Im Container implementierte Dienste
* Vertrag zwischen dem Container und Ihrem Antrag

Diese Dienste und Verträge bieten eine Architektur, die es einzelnen Elementen ermöglicht, sich dynamisch für die Zusammenarbeit zu entdecken.

Ein OSGi-Framework bietet Ihnen dann dynamisches Laden/Entladen, Konfiguration und Kontrolle dieser Bundles - ohne dass ein Neustart erforderlich ist.

>[!NOTE]
>
>Full information on OSGi technology can be found at the [OSGi website](https://www.osgi.org).
>
>Speziell die Seite mit grundlegenden Informationen beinhaltet eine Sammlung von Präsentationen und Tutorials.

Diese Architektur ermöglicht es Ihnen, Sling um anwendungsspezifische Module zu erweitern. Sling und damit AEM nutzt die [Apache Felix](https://felix.apache.org/) Implementierung von OSGi. Beides sind Sammlungen von OSGi-Bundles, die in einem OSGi-Framework ausgeführt werden.

Dies ermöglicht es Ihnen, die folgenden Handlungen innerhalb Ihrer Installation für ein beliebiges Paket durchzuführen:

* Installieren
* Anfang
* Stopp
* Aktualisieren
* Deinstallieren
* Siehe Aktuellen Status
* Greifen Sie auf detailliertere Informationen (z.B. symbolischer Name, Version, Speicherort usw.) zu den jeweiligen Bundles zu

Weitere Informationen finden Sie unter OSGi [konfigurieren für AEM als Cloud Service](/help/implementing/deploying/configuring-osgi.md) .

## Struktur innerhalb des Repositorys {#structure-within-the-repository}

Die folgende Liste gibt einen Überblick über die Struktur, die Sie im Repository sehen.

* `/apps` - Antragsbezogen; enthält für Ihre Website spezifische Komponentendefinitionen. The components that you develop can be based on the out of the box components available at `/libs/core/wcm/components`.
* `/content` - Für Ihre Website erstellte Inhalte.
* `/etc`
* `/home` - Benutzer- und Gruppeninformationen.
* `/libs` - Bibliotheken und Definitionen, die zum Kern der AEM gehören. Die Unterordner in `/libs` stellen die vordefinierten AEM Funktionen dar. Der Inhalt in `/libs` darf nicht geändert werden. Funktionen, die für Ihre Website spezifisch sind, sollten unter `/apps`vorgenommen werden.
* `/tmp` - Zeitweiliger Arbeitsbereich.
* `/var` - Dateien, die sich ändern und vom System aktualisiert werden; wie Prüfprotokolle, Statistiken, Ereignis-Bearbeitung.

>[!CAUTION]
>
>Änderungen an dieser Struktur oder an den darin enthaltenen Dateien sollten sorgfältig vorgenommen werden. Vergewissern Sie sich, dass Sie die Auswirkungen von Änderungen, die Sie vornehmen, vollständig verstehen.
>
>Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen. For configuration and other changes copy the item from `/libs` to `/apps` and make any changes within `/apps`.
