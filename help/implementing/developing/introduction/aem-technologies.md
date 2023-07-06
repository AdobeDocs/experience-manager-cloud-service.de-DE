---
title: Technische Grundlagen von AEM
description: Eine Übersicht über die technischen Grundlagen von AEM, einschließlich der Art und Weise, wie AEM und grundlegende Technologien wie JCR, Sling und OSGi strukturiert sind.
exl-id: ab6e7fe9-a25d-4351-a005-f4466cc0f40e
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '2144'
ht-degree: 63%

---

# Technische Grundlagen von AEM {#aem-technical-foundations}

AEM ist eine solide Plattform, die auf bewährten, skalierbaren und flexiblen Technologien basiert. Dieses Dokument gibt einen detaillierten Überblick über die verschiedenen AEM und ist als technischer Anhang für einen Full-Stack-AEM-Entwickler gedacht. Es ist nicht als Anleitung für den Einstieg gedacht. Wenn Sie mit AEM Entwicklung noch nicht vertraut sind, lesen Sie [Erste Schritte bei der Entwicklung von AEM Sites - WKND-Tutorial](develop-wknd-tutorial.md) als ersten Schritt.

>[!TIP]
>
>Bevor Sie sich eingehender mit den Kerntechnologien von AEM befassen, empfiehlt es sich, [Erste Schritte bei der Entwicklung von AEM Sites – WKND-Tutorial](develop-wknd-tutorial.md) durchzugehen.

## Grundlagen {#fundamentals}

Als modernes Content-Management-System setzt AEM auf Standard-Web-Technologien:

* Der Zyklus „Anfrage/Antwort“ (XMLHttpRequest/XMLHttpResponse)
* HTML
* CSS
* JavaScript

Die zugrunde liegenden Inhalts-Repository- und Business-Logikebenen basieren auf Java™-Technologien:

* JCR
* Sling
* OSGi

## Java™ Content-Repository {#java-content-repository}

Der Java™ Content-Repository-Standard (JCR) [JSR 283](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html) legt eine hersteller- und implementierungsunabhängige Methode für den bidirektionalen Zugriff auf Inhalte auf einer granularen Ebene in einem Content-Repository fest. Maßgeblich für Spezifikationen ist Adobe Research (Switzerland) AG.

Das [JCR API 2.0](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html)-Paket `javax.jcr.*` wird für den direkten Zugriff und die Bearbeitung von Repository-Inhalten verwendet.

AEM basiert auf einem JCR.

## Apache Jackrabbit Oak {#jackrabbit-oak}

[Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/) ist eine Implementierung eines skalierbaren und hochleistungsfähigen hierarchischen Content-Repositorys, das als Grundlage für moderne, erstklassige Websites und andere anspruchsvolle Content-Programme verwendet werden kann und dem JCR-Standard entspricht.

Jackrabbit Oak (auch als Oak bezeichnet) ist die Implementierung des JCR-Standards, auf dem AEM aufgebaut ist.

## Sling-Anfrageverarbeitung {#sling-request-processing}

AEM basiert auf [Sling](https://sling.apache.org/index.html), einem auf REST-Prinzipien basierenden Web-Anwendungs-Framework, das eine einfache Entwicklung von inhaltsorientierten Programmen ermöglicht. Sling verwendet ein JCR-Repository wie Apache Jackrabbit Oak als Datenspeicher. Sling ist Teil der Apache Software Foundation – weitere Informationen finden Sie bei Apache.

### Einführung in Sling {#introduction-to-sling}

Bei Verwendung von Sling ist der Typ des zu rendernden Inhalts nicht die erste Verarbeitungsüberlegung. Die Hauptüberlegung besteht vielmehr darin, ob die URL zu einem Inhaltsobjekt aufgelöst wird, für das dann ein Skript gefunden werden kann, um das Rendering durchzuführen. Dieser Prozess bietet Autoren von Web-Inhalten hervorragende Unterstützung beim Erstellen von Seiten, die einfach an ihre Anforderungen angepasst werden können.

Die Vorteile dieser Flexibilität zeigen sich in Programmen mit einer großen Auswahl verschiedener Inhaltselemente oder wenn Sie Seiten benötigen, die einfach angepasst werden können. Insbesondere bei der Implementierung eines Web-Content-Management-Systems wie AEM.

Siehe [Entdecken Sie Sling in 15 Minuten](https://sling.apache.org/documentation/getting-started/discover-sling-in-15-minutes.html) für die ersten Schritte zur Entwicklung mit Sling.

Im folgenden Diagramm wird die Auflösung des Sling-Skripts erläutert. Es zeigt, wie Sie von einer HTTP-Anforderung zum Inhaltsknoten, vom Inhaltsknoten zum Ressourcentyp, vom Ressourcentyp zum Skript gelangen und welche Skriptvariablen verfügbar sind.

![Verstehen der Auflösung des Apache Sling-Skripts](assets/sling-cheatsheet-01.png)

Im folgenden Diagramm werden die verborgenen, aber leistungsstarken Anforderungsparameter erläutert, die Sie mit `SlingPostServlet`, den Standard-Handler für alle POST-Anforderungen. Der Handler bietet Ihnen unzählige Optionen zum Erstellen, Ändern, Löschen, Kopieren und Verschieben von Knoten im Repository.

![Verwenden des SlingPostServlet](assets/sling-cheatsheet-02.png)

### Sling ist inhaltszentriert {#sling-is-content-centric}

Sling ist *inhaltzentriert*. Dies bedeutet, dass sich die Verarbeitung auf den Inhalt konzentriert, da jede (HTTP-)Anforderung in Form einer JCR-Ressource (eines Repository-Knotens) Inhalten zugeordnet wird:

* Das erste Ziel ist die Ressource (JCR-Knoten), die die Inhalte enthält.
* Zweitens befindet sich die Darstellung bzw. das Skript in den Ressourceneigenschaften mit bestimmten Teilen der Anforderung (z. B. Selektoren und/oder die Erweiterung).

### RESTful Sling {#restful-sling}

Aufgrund der inhaltsorientierten Philosophie implementiert Sling einen REST-orientierten Server und bietet damit ein neues Konzept für Web-Anwendungs-Frameworks. Die Vorteile:

* RESTful, nicht nur an der Oberfläche; Ressourcen und Darstellungen korrekt innerhalb des Servers modelliert werden
* Entfernt ein oder mehrere Datenmodelle.
   * Andere Content-Management-Frameworks erfordern möglicherweise URL-Struktur, Geschäftsobjekte und DB-Schema, um auf eine Ressource zuzugreifen.
   * Die Verwendung von Sling reduziert dies auf: URL = resource = JCR-Struktur

### URL-Zerlegung {#url-decomposition}

In Sling wird die Verarbeitung durch die URL der Benutzeranfrage gesteuert. Sie definiert den Inhalt, der von den entsprechenden Skripten angezeigt werden soll, und Informationen werden aus der URL extrahiert.

Analysieren Sie die folgende URL:

```text
https://myhost/tools/spy.printable.a4.html/a/b?x=12
```

Sie können sie in ihre zusammengesetzten Teile aufschlüsseln:

| protocol | host |  | content path | Selektoren | Erweiterung |  | Suffix |  | params |
|---|---|---|---|---|---|---|---|---|---|
| `https://` | `myhost` | `/` | `tools/spy` | `.printable.a4.` | `html` | `/` | `a/b` | `?` | `x=12` |

* **protocol** – HTTPS
* **host** – Domain der Site.
* **Inhaltspfad** - Pfad, der den zu rendernden Inhalt angibt und mit der Erweiterung verwendet wird. In diesem Beispiel wird `tools/spy.html`
* **Selektoren** - Verwendung für alternative Methoden zur Darstellung des Inhalts; in diesem Beispiel eine druckerfreundliche Version im A4-Format
* **extension** – Inhaltsformat; gibt außerdem das Skript an, das zum Rendern verwendet werden soll.
* **suffix** – kann verwendet werden, um zusätzliche Information anzugeben.
* **params** - Alle Parameter, die für dynamischen Inhalt erforderlich sind

#### Von URL zu Inhalt und Skripten {#from-url-to-content-and-scripts}

Anwendung der Prinzipien der URL-Zerlegung:

* Das Mapping verwendet den aus der Anfrage extrahierten Inhaltspfad, um die Ressource zu lokalisieren.
* Wenn die entsprechende Ressource gefunden wurde, wird der Sling-Ressourcentyp extrahiert und zum Suchen des Skripts verwendet, das zum Rendern des Inhalts verwendet werden soll.

Die folgende Abbildung zeigt den verwendeten Mechanismus, der in den folgenden Abschnitten ausführlicher erläutert wird.

![URL-Mapping-Mechanismus](assets/url-mapping.png)

Mit Sling geben Sie an, welches Skript eine bestimmte Entität rendert (indem Sie die Eigenschaft `sling:resourceType` im JCR-Knoten festlegen). Dieser Mechanismus bietet mehr Freiheit als einer, in dem das Skript auf die Datenentitäten zugreift (wie es eine SQL-Anweisung in einem PHP-Skript tun würde), da eine Ressource mehrere Ausgabedarstellungen haben kann.

#### Zuordnen von Anfragen zu Ressourcen {#mapping-requests-to-resources}

Die Anfrage wird zerlegt und die notwendigen Informationen werden extrahiert. Das Repository wird nach der angeforderten Ressource (Inhaltsknoten) durchsucht:

* Zunächst prüft Sling, ob ein Knoten an der in der Anfrage angegebenen Position existiert; z. B. `../content/corporate/jobs/developer.html`
* Wird kein Knoten gefunden, dann wird die Erweiterung entfernt und die Suche wiederholt; z. B, `../content/corporate/jobs/developer`
* Wenn kein Knoten gefunden wird, gibt Sling den HTTP-Code 404 (Nicht gefunden) zurück.

Sling ermöglicht auch, dass andere Elemente als JCR-Knoten Ressourcen sind. Diese Funktion ist jedoch eine erweiterte Funktion.

### Auffinden des Skripts {#locating-the-script}

Wenn die entsprechende Ressource (Inhaltsknoten) gefunden wird, wird der **Sling-Ressourcentyp** extrahiert. Dieser Pfad lokalisiert das Skript, das zum Rendern des Inhalts verwendet werden soll.

Der vom `sling:resourceType` angegebene Pfad kann wie folgt sein:

* Absolut
* Relativ zu einem Konfigurationsparameter

>[!TIP]
>
>Relative Pfade werden von der Adobe empfohlen, da sie die Portabilität erhöhen.

Alle Sling-Skripte werden in Unterordnern von `/apps` (veränderlich, Benutzerskripte) oder `/libs` (unveränderlich, Systemskripte), die in dieser Reihenfolge durchsucht wird.

Einige andere zu beachtende Punkte sind:

* Wenn die Methode (GET, POST) erforderlich ist, wird sie in Großbuchstaben wie z. B. gemäß der HTTP-Spezifikation angegeben. `jobs.POST.esp`
* Es werden verschiedene Skript-Engines unterstützt. Gebräuchlich und empfohlen sind jedoch HTL und JavaScript.

Die Liste der von der angegebenen Instanz von AEM unterstützten Skript-Engines wird in der Felix Management Console aufgeführt (`http://<host>:<port>/system/console/slingscripting`).

Wenn der `sling:resourceType` bei Verwendung des obigen Beispiels `hr/jobs` lautet, gilt Folgendes:

* GET/HEAD-Anfragen und URLs, die auf `.html` enden (Standardanfragetypen, Standardformat)
   * Das Skript ist `/apps/hr/jobs/jobs.esp`; den letzten Abschnitt der `sling:resourceType` bildet den Dateinamen.
* POST-Anfragen (alle Anfragetypen außer GET/HEAD, der Methodenname muss in Großbuchstaben angegeben werden)
   * POST wird im Skriptnamen verwendet.
   * Das Skript ist `/apps/hr/jobs/jobs.POST.esp`.
* URLs in anderen Formaten, die nicht mit `.html` enden.
   * Beispiel: `../content/corporate/jobs/developer.pdf`
   * Das Skript ist `/apps/hr/jobs/jobs.pdf.esp`; das Suffix zum Skriptnamen hinzugefügt wird.
* URLs mit Selektoren
   * Selektoren können verwendet werden, um denselben Inhalt in einem alternativen Format anzuzeigen. Beispielsweise eine druckerfreundliche Version, einen RSS-Feed oder eine Zusammenfassung.
   * Wenn Sie sich eine druckerfreundliche Version ansehen, in der der Selektor `print`; wie in `../content/corporate/jobs/developer.print.html`
   * Das Skript ist `/apps/hr/jobs/jobs.print.esp`; Der Selektor wird dem Skriptnamen hinzugefügt.
* Wenn nicht, `sling:resourceType` definiert wird, dann:
   * Der Inhaltspfad wird verwendet, um nach einem geeigneten Skript zu suchen (wenn der pfadbasierte `ResourceTypeProvider` ist aktiv).
   * Zum Beispiel würde das Skript für `../content/corporate/jobs/developer.html` eine Suche in `/apps/content/corporate/jobs/` erzeugen.
   * Der primäre Knotentyp wird verwendet.
* Wenn überhaupt kein Skript gefunden wird, wird das Standardskript verwendet.
   * Die Standardausgabe wird als Nur-Text (`.txt`), HTML (`.html`) und JSON (`.json`), die alle die Eigenschaften des Knotens auflistet (entsprechend formatiert). Die Standardversion für die Erweiterung `.res` oder für Anfragen ohne Anfrageerweiterung besteht darin, die Ressource (sofern möglich) zu spoolen.
* Für die HTTP-Fehlerbehandlung (Codes 403 oder 404) sucht Sling nach einem Skript in einer der folgenden Situationen:
   * Im Speicherort `/apps/sling/servlet/errorhandler` für benutzerdefinierte Skripte
   * oder im Speicherort des Standardskripts `/libs/sling/servlet/errorhandler/404.jsp`

Wenn mehrere Skripte für eine bestimmte Anfrage gelten, wird das Skript mit der besten Übereinstimmung ausgewählt. Je genauer eine Übereinstimmung ist, desto besser ist sie. Mit anderen Worten: Je mehr Selektor-Treffer, desto besser, unabhängig von einer Übereinstimmung bei Anfrageerweiterung oder Methodenname.

Beispiel: Eine Anfrage zum Zugriff auf die Ressource



* `/content/corporate/jobs/developer.print.a4.html`

vom Typ

* `sling:resourceType="hr/jobs"`

Angenommen, Sie haben die folgende Liste von Skripten am richtigen Speicherort:

1. `GET.esp`
1. `jobs.esp`
1. `html.esp`
1. `print.esp`
1. `print.html.esp`
1. `print/a4.esp`
1. `print/a4/html.esp`
1. `print/a4.html.esp`

Dann wäre die Reihenfolge der Bevorzugung (8) - (7) - (6) - (5) - (4) - (3) - (2) - (1).

Zusätzlich zu den Ressourcentypen (hauptsächlich definiert durch die `sling:resourceType` -Eigenschaft), gibt es auch den Supertyp der Ressource. Dieser Typ wird durch die `sling:resourceSuperType` -Eigenschaft. Diese Supertypen werden ebenfalls berücksichtigt, wenn Sie versuchen, ein Skript zu finden. Der Vorteil von Ressourcensupertypen besteht darin, dass sie eine Hierarchie von Ressourcen bilden können, wobei der Standard-Ressourcentyp `sling/servlet/default` (von den Standard-Servlets verwendet) effektiv der Stamm ist.

Der Ressourcensupertyp einer Ressource kann auf zwei Arten definiert werden:

* durch die Eigenschaft `sling:resourceSuperType` der Ressource.
* durch die Eigenschaft `sling:resourceSuperType` des Knotens, auf den der `sling:resourceType` zeigt.

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
   * Er ist `[ c, b, a, <default>]`
* während für `/y`
   * die Hierarchie `[ c, a, <default>]` lautet

Der Grund dafür ist, dass `/y` hat die `sling:resourceSuperType` Eigenschaft, während `/x` ist nicht vorhanden und daher wird der Supertyp vom Ressourcentyp übernommen.

#### Sling-Skripte können nicht direkt aufgerufen werden {#sling-scripts-cannot-be-called-directly}

In Sling können Skripte nicht direkt aufgerufen werden, da dies das strikte Konzept eines REST-Servers beeinträchtigen würde. würden Sie Ressourcen und Darstellungen mischen.

Wenn Sie die Repräsentation (das Skript) direkt aufrufen, blenden Sie die Ressource in Ihrem Skript aus, sodass das Framework (Sling) nicht mehr davon weiß. Sie verlieren so bestimmte Funktionen:

* automatische Handhabung von HTTP-Methoden außer GET, einschließlich:
   * POST, PUT, DELETE, das mit einer standardmäßigen Sling-Implementierung verarbeitet wird
   * das `POST.jsp`-Skript in Ihrem `sling:resourceType`-Speicherort
* Ihre Code-Architektur ist nicht mehr so sauber oder so klar strukturiert, wie sie es sein sollte. Von größter Bedeutung für die Entwicklung im großen Umfang

### Sling-API {#sling-api}

Verwendet das Sling-API-Paket, `org.apache.sling.*`und Tag-Bibliotheken.

### Referenzieren von vorhandenen Elementen mithilfe von sling:include {#referencing-existing-elements-using-sling-include}

Eine letzte Überlegung ist die Notwendigkeit, auf vorhandene Elemente innerhalb der Skripte zu verweisen.

Komplexere Skripte (Aggregieren von Skripten) greifen auf mehrere Ressourcen zu (z. B. Navigation, Seitenleiste, Fußzeile, Elemente einer Liste), indem sie die *resource*.

In diesem Fall können Sie die `sling:include("/<path>/<resource>")` Befehl. Sie umfasst effektiv die Definition der referenzierten Ressource.

## OSGi {#osgi}

OSGi (Open Services Gateway Initiative) definiert eine Architektur für die Entwicklung und Bereitstellung modularer Programme und Bibliotheken (es wird auch als Dynamic Module System für Java bezeichnet™). OSGi-Container erlauben es Ihnen, Ihr Programm in einzelne Module aufzuteilen (JAR-Dateien mit zusätzlichen Metainformationen und sogenannten Bundles in OSGi-Terminologie) und die Querabhängigkeiten zwischen ihnen zu verwalten mit:

* Services, die innerhalb des Containers implementiert sind
* einem Vertrag zwischen dem Container und Ihrem Programm

Diese Services und Verträge bieten eine Architektur, die es einzelnen Elementen ermöglicht, sich dynamisch für die Zusammenarbeit zu entdecken.

Ein OSGi-Framework bietet Ihnen dann dynamisches Laden/Entladen, Konfiguration und Steuerung dieser Bundles - ohne dass ein Neustart erforderlich ist.

>[!NOTE]
>
>Ausführliche Informationen zur OSGi-Technologie finden Sie auf der [OSGi-Website](https://www.osgi.org).
>
>Speziell die Seite mit grundlegenden Informationen beinhaltet eine Sammlung von Präsentationen und Tutorials.

Mit dieser Architektur können Sie Sling mit anwendungsspezifischen Modulen erweitern. Sling und damit AEM verwendet die [Apache Felix](https://felix.apache.org/documentation/index.html)-Implementierung von OSGi. Beides sind Sammlungen von OSGi-Bundles, die in einem OSGi-Framework ausgeführt werden.

Mit dieser Funktion können Sie die folgenden Aktionen für beliebige Pakete innerhalb Ihrer Installation durchführen:

* Installieren
* Starten
* Anhalten
* Aktualisieren
* Deinstallieren
* Siehe Neuester Status .
* Greifen Sie auf detailliertere Informationen zu bestimmten Bundles zu, z. B. symbolischer Name, Version und Speicherort.

Weitere Informationen finden Sie unter [Konfigurieren von OSGi für AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).

## Struktur innerhalb des Repositorys {#structure-within-the-repository}

Die folgende Liste gibt einen Überblick über die Struktur, die Sie im Repository sehen.

* `/apps` – programmbezogen; enthält für Ihre Website spezifische Komponentendefinitionen. Die von Ihnen entwickelten Komponenten können auf den Standardkomponenten basieren, die unter `/libs/core/wcm/components` verfügbar sind.
* `/content` – Inhalt, der für Ihre Website erstellt wurde.
* `/etc`
* `/home` – Anwender- und Gruppeninformationen.
* `/libs` – Bibliotheken und Definitionen, die zum Kern von AEM gehören. Die Unterordner in `/libs` stellen die vordefinierten AEM dar. Der Inhalt in `/libs` kann nicht geändert werden. Die für Ihre Website spezifischen Funktionen sollten unter `/apps` erstellt werden.
* `/tmp` - Temporärer Arbeitsbereich.
* `/var` – Dateien, die sich ändern und vom System aktualisiert werden, wie Audit-Logs, Statistiken, Event-Handling.

>[!CAUTION]
>
>Änderungen an dieser Struktur oder an den darin enthaltenen Dateien sollten sorgfältig vorgenommen werden. Machen Sie sich unbedingt mit den Auswirkungen der Änderungen vertraut, die Sie vornehmen möchten.
>
>Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen. Für Konfiguration und andere Änderungen kopieren Sie das Element aus `/libs` nach `/apps` und nehmen Änderungen in `/apps`.
