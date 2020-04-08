---
title: Protokollierung
description: Erfahren Sie, wie Sie globale Parameter für den zentralen Protokollierungsdienst konfigurieren, bestimmte Einstellungen für einzelne Dienste festlegen oder eine Datenprotokollierung anfordern können.
translation-type: tm+mt
source-git-commit: 114bc678fc1c6e3570d6d2a29bc034feb68aa56d

---


# Protokollierung{#logging}

AEM als Cloud-Dienst-Angebot können Sie Folgendes konfigurieren:

* Globale Parameter für den zentralen Protokollierungsdienst
* Anforderung einer Datenprotokollierung; eine spezielle Protokollierungskonfiguration zum Anfordern von Informationen
* Bestimmte Einstellungen für einzelne Dienste, beispielsweise zum Festlegen einer einzelnen Protokolldatei und des Formats von Protokollmeldungen

Für die lokale Entwicklung werden Protokolleinträge in lokale Dateien im `/crx-quickstart/logs` Ordner geschrieben.

Auf Cloud-Umgebung können Entwickler Protokolle über Cloud Manager herunterladen oder ein Befehlszeilenwerkzeug verwenden, um die Protokolle zu verkleinern.

>[!NOTE]
>
>Die Anmeldung bei AEM als Cloud-Dienst basiert auf Sling-Prinzipien. Weitere Informationen finden Sie unter [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

## Globale Protokollierung {#global-logging}

Die Konfiguration [Apache Sling Logging Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based) dient zum Konfigurieren des Root-Loggers. Dadurch werden die globalen Einstellungen für die Anmeldung bei AEM als Cloud-Dienst definiert:

* Protokollierungsstufe
* Speicherort der zentralen Protokolldatei
* Anzahl der aufzubewahrenden Versionen
* Versionsrotation; entweder maximale Größe oder Zeitintervall
* Format zum Schreiben der Protokollmeldungen

## Logger und Writer für einzelne Dienste {#loggers-and-writers-for-individual-services}

Zusätzlich zu den Einstellungen für die globale Protokollierung können Sie mit AEM als Cloud-Dienst bestimmte Einstellungen für einen einzelnen Dienst konfigurieren:

* Bestimmte Protokollierungsstufe
* Speicherort der jeweiligen Protokolldatei
* Anzahl der aufzubewahrenden Versionen
* Versionsrotation; entweder maximale Größe oder Zeitintervall
* Format zum Schreiben der Protokollmeldungen
* Logger (OSGi-Dienst, der die Protokollmeldungen bereitstellt)

So können Sie die Protokollmeldungen für einen einzelnen Dienst in einer separaten Datei kanalisieren. Dies kann insbesondere beim Entwickeln oder Testen nützlich sein, etwa wenn Sie für einen bestimmten Dienst auf eine höhere Protokollierungsstufe angewiesen sind.

AEM als Cloud-Dienst verwendet Folgendes, um Protokollmeldungen in eine Datei zu schreiben:

1. Ein **OSGi-Dienst** (Logger) schreibt eine Protokollmeldung.
1. Ein **Logging Logger** (Protokollierungslogger) formatiert diese Meldung gemäß Ihren Angaben.
1. Ein **Logging Writer** (Protokollierungswriter) schreibt all diese Meldungen in die von Ihnen definierte physische Datei.

Diese Elemente sind über die folgenden Parameter mit den entsprechenden Elementen verknüpft:

* **Protokollfunktion**

   Definieren Sie die Dienste, die die Nachrichten generieren.

* **Protokolldatei (Protokollprotokollierung)**

   Definieren Sie die physische Datei zum Speichern der Protokollmeldungen.

   Auf diese Weise werden Logging Logger und Logging Writer miteinander verknüpft. Der Wert muss für die herzustellende Verbindung mit den Parametern in der Logging-Writer-Konfiguration übereinstimmen.

* **Protokolldatei (Protokollautor)**

   Definieren Sie die physische Datei, in die die Protokollmeldungen geschrieben werden.

   Der Wert muss mit den Parametern in der Logging-Writer-Konfiguration übereinstimmen. Andernfalls erfolgt kein Abgleich. Liegt keine Übereinstimmung vor, wird ein impliziter Writer mit der Standardkonfiguration (tägliche Protokollrotation) erstellt.

### Standardlogger und -writer {#standard-loggers-and-writers}

Bestimmte Protokollfunktionen und Writer sind in einer AEM-Standardinstallation als Cloud-Dienst enthalten.

Das erste Paar ist ein Sonderfall, da sowohl `request.log`- als auch `access.log`-Dateien gesteuert werden:

* Der Logger:

   * Apache Sling Customizable Request Data Logger

      (org.apache.sling.engine.impl.log.RequestLoggerService)

   * schreibt Meldungen zu Anforderungsinhalt in die Datei `request.log`.

* Ist verknüpft mit:

   * Apache Sling Request Logger

      (org.apache.sling.engine.impl.log.RequestLogger)

   * Writes the messages to either `request.log` or `access.log`.

Eine Anpassung ist hier ggf. möglich, obwohl die Standardkonfiguration für die meisten Installationen geeignet ist.

Die anderen Paare folgen der Standardkonfiguration:

* Der Logger:

   * Apache Sling Logging Logger-Konfiguration

      (org.apache.sling.commons.log.LogManager.factory.config)

   * Schreibt `Information` Nachrichten an `logs/error.log`.

* Ist mit dem folgenden Writer verknüpft:

   * Apache Sling Logging Writer Configuration

      (org.apache.sling.commons.log.LogManager.factory.writer)

* Der Logger:

   * Apache Sling Logging Logger Configuration (org.apache.sling.commons.log.LogManager.factory.config.649d51b7-6425-45c9-81e6-2697a03d6be7)

   * Schreibt `Warning` Nachrichten für `../logs/error.log` den Dienst `org.apache.pdfbox`.

* Ist nicht mit einem bestimmten Writer verknüpft, sodass ein impliziter Writer mit Standardkonfiguration (tägliche Protokollrotation) verwendet wird.

## Protokollebene festlegen {#setting-the-log-level}

Um die Protokollierungsstufen für Cloud-Umgebung zu ändern, sollte die Sling Logging OSGI-Konfiguration geändert und anschließend eine vollständige Neubereitstellung durchgeführt werden. Da dies nicht sofort geschieht, sollten Sie vorsichtig sein, um ausführliche Protokolle zu Produktions-Umgebung zu aktivieren, die viel Traffic erhalten. In Zukunft wird es möglicherweise Mechanismen geben, um die Protokollierungsstufe schneller zu ändern.

>[!NOTE]
>
> Um die unten aufgeführten Konfigurationsänderungen durchzuführen, müssen Sie sie auf einer lokalen Entwicklungs-Umgebung erstellen und dann als Cloud-Dienstinstanz an eine AEM-Instanz senden. Weitere Informationen dazu finden Sie unter [Bereitstellen auf AEM als Cloud-Dienst](/help/implementing/deploying/overview.md).

### Aktivieren der DEBUG-Protokollebene {#activating-the-debug-log-level}

>[!WARNING]
>
> Die globale Aktivierung der DEBUG-Protokollebene erzeugt eine große Menge an Informationen, die sich nur schwer durchblättern lassen. Es wird empfohlen, diese Option nur für Dienste zu aktivieren, für die Debugging erforderlich ist. Weitere Informationen finden Sie unter [Anmelder und Autoren für individuelle Dienste](logging.md#loggers-and-writers-for-individual-services).

Die standardmäßige Protokollebene ist INFO, DEBUG-Meldungen werden also nicht protokolliert.
Um die DEBUG-Protokollebene zu aktivieren, legen Sie die Variable

``` /libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level ```

auf „debug“ ein. Lassen Sie die DEBUG-Protokollebene nicht länger als notwendig aktiviert, da hierdurch zahlreiche Protokolle generiert werden.
Eine Zeile in der Debugdatei beginnt gewöhnlich mit DEBUG, gefolgt von der Angabe der Protokollebene, der Aktion des Installationsprogramms und der Protokollmeldung. Beispiel:

``` DEBUG 3 WebApp Panel: WebApp successfully deployed ```

Die Protokollebenen lauten wie folgt:

| 0 | Schwerwiegender Fehler | Die Aktion ist fehlgeschlagen, und das Installationsprogramm kann nicht fortgesetzt werden. |
|---|---|---|
| 1 | Fehler | Die Aktion ist fehlgeschlagen. Die Installation wird fortgesetzt, aber ein CRX-Teil wurde nicht ordnungsgemäß installiert und funktioniert daher nicht. |
| 2 | Warnung | Die Aktion war erfolgreich, hatte aber Probleme. CRX funktioniert ggf. nicht ordnungsgemäß. |
| 3 | Informationen | Die Aktion war erfolgreich. |

### Erstellen eigener Logger und Writer {#creating-your-own-loggers-and-writers}

Sie können ein eigenes Logger-/Writer-Paar definieren:

1. Erstellen Sie eine neue Instanz der Werkskonfiguration [Apache Sling Logging Logger Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based).

   1. Geben Sie die Protokolldatei an.
   1. Geben Sie den Logger an.
   1. Konfigurieren Sie die anderen Parameter nach Bedarf.

1. Erstellen Sie eine neue Instanz der Werkskonfiguration [Apache Sling Logging Writer Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based).

   1. Geben Sie die Protokolldatei an – diese muss mit der Angabe für den Logger übereinstimmen.
   1. Konfigurieren Sie die anderen Parameter nach Bedarf.

### Erstellen einer benutzerdefinierten Protokolldatei {#create-a-custom-log-file}

>[!NOTE]
>
>Beim Arbeiten mit Adobe Experience Manager gibt es verschiedene Methoden zum Verwalten der Konfigurationseinstellungen für diese Dienste.

Unter bestimmten Umständen müssen Sie möglicherweise eine benutzerdefinierte Protokolldatei mit einer anderen Protokollebene erstellen. Gehen Sie dazu im Repository wie folgt vor:

1. If not already existing, create a new configuration folder ( `sling:Folder`) for your project `/apps/<*project-name*>/config`.
1. Under `/apps/<*project-name*>/config`, create a node for the new Apache Sling Logging Logger Configuration:

   * Name: `org.apache.sling.commons.log.LogManager.factory.config-<*identifier*>` (da dies eine Protokollfunktion ist)

      Where `<*identifier*>` is replaced by free text that you (must) enter to identify the instance (you cannot omit this information).

      Beispiel: `org.apache.sling.commons.log.LogManager.factory.config-MINE`

   * Typ: `sling:OsgiConfig`
   >[!NOTE]
   >
   >Although not a technical requirement, it is advisable to make `<*identifier*>` unique.

1. Legen Sie die folgenden Eigenschaften des Knotens fest:

   * Name: `org.apache.sling.commons.log.file`

      Typ: String

      Wert: die Protokolldatei angeben; zum Beispiel `logs/myLogFile.log`

   * Name: `org.apache.sling.commons.log.names`

      Typ: Zeichenfolge[] (Zeichenfolge + Multi)

      Wert: Geben Sie die OSGi-Dienste an, für die die Protokollfunktion Meldungen protokollieren soll. zum Beispiel alle folgenden Elemente:

      * `org.apache.sling`
      * `org.apache.felix`
      * `com.day`
   * Name: `org.apache.sling.commons.log.level`

      Typ: String

      Wert: die erforderliche Protokollierungsstufe ( `debug`, `info`, `warn` oder `error`) angeben; zum Beispiel `debug`

   * Konfigurieren Sie ggf. weitere Parameter:

      * Name: `org.apache.sling.commons.log.pattern`

         Typ: `String`

         Wert: das Muster der Protokollmeldung nach Bedarf angeben; zum Beispiel

         `{0,date,dd.MM.yyyy HH:mm:ss.SSS} *{4}* [{2}] {3} {5}`
   >[!NOTE]
   >
   >`org.apache.sling.commons.log.pattern` unterstützt bis zu sechs Argumente.

   >{0} Der Zeitstempel des Typs `java.util.Date`
   >
   >{1} die Protokollmarke{2} der Name des aktuellen Threads{3} der Name der Protokollfunktion{4} die Protokollierungsstufe{5} die Protokollmeldung

   >Falls der Protokollaufruf den Parameter `Throwable` enthält, wird der StackTrace an die Meldung angefügt.

   >[!CAUTION]
   „org.apache.sling.commons.log.names“ muss einen Wert enthalten.

   >[!NOTE]
   Die Protokollierungspfade sind vom Speicherort-`crx-quickstart`abhängig.
   Eine Protokolldatei wie:
   `logs/thelog.log`

   >wird daher geschrieben in:
   `` ` ` `<*cq-installation-dir*>/``crx-quickstart/logs/thelog.log&quot;.
   Und eine Protokolldatei wie:
   `../logs/thelog.log`

   >wird in folgendes Verzeichnis geschrieben:
   ` <*cq-installation-dir*>/logs/`
&quot;(z. B. neben ` `&lt;*cq-installation-dir*>/`crx-quickstart/`)

1. Dieser Schritt muss nur ausgeführt werden, wenn ein neuer Writer erforderlich ist (d. h. mit einer Konfiguration, die vom standardmäßigen Writer abweicht). 

   >[!CAUTION]
   Eine neue Logging-Writer-Konfiguration ist nur erforderlich, wenn die vorhandene Standardkonfiguration nicht geeignet ist.

   >Wenn kein expliziter Writer konfiguriert ist, erstellt das System automatisch einen impliziten Writer auf Basis der Standardkonfiguration.

   Erstellen Sie `/apps/<*project-name*>/config`unter einen Knoten für die neue `Apache Sling Logging Writer` Konfiguration:

   * Name: `org.apache.sling.commons.log.LogManager.factory.writer-<*identifier*>` (da dies ein Schriftsteller ist)

      Wie beim Logger `<*identifier*>` wird durch freien Text ersetzt, den Sie (müssen) eingeben, um die Instanz zu identifizieren (Sie können diese Informationen nicht auslassen). Beispiel: `org.apache.sling.commons.log.LogManager.factory.writer-MINE`

   * Typ: `sling:OsgiConfig`
   >[!NOTE]
   Although not a technical requirement, it is advisable to make `<*identifier*>` unique.

   Legen Sie die folgenden Eigenschaften des Knotens fest:

   * Name: `org.apache.sling.commons.log.file`

      Typ: `String`

      Wert: Geben Sie die Protokolldatei so an, dass sie mit der im Protokollprogramm angegebenen Datei übereinstimmt.

      für dieses Beispiel `../logs/myLogFile.log`.

   * Konfigurieren Sie ggf. weitere Parameter:

      * Name: `org.apache.sling.commons.log.file.number`

         Typ: `Long`

         Value: specify the number of log files you want kept; for example, `5`

      * Name: `org.apache.sling.commons.log.file.size`

         Typ: `String`

         Value: specify as required to control file rotation by size/date; for example, `'.'yyyy-MM-dd`
   >[!NOTE]
   `org.apache.sling.commons.log.file.size` steuert die Rotation der Protokolldatei durch eine der folgenden Einstellungen:
   * eine maximalen Dateigröße
   * einen Zeit-/Terminplan
   um anzugeben, wann eine neue Datei erstellt wird (und die vorhandene Datei gemäß dem Namensmuster umbenannt wird).
   * Eine Größenbeschränkung kann mit einer Zahl angegeben werden. If no size indicator is given, then this is taken as the number of bytes, or you can add one of the size indicators - `KB`, `MB`, or `GB` (case is ignored).
   * Sie können einen Zeit-/Terminplan nach dem `java.util.SimpleDateFormat`-Muster angeben. Dieser gibt den Zeitraum an, in dem die Datei rotiert wird, sowie das Suffix, das an die rotierte Datei angehängt wurde (zur einfachen Identifizierung).
   Der Standardwert lautet &#39;.&#39;yyyy-MM-dd (für die tägliche Protokollrotation).
   So wird beispielsweise um Mitternacht am 20. Januar 2010 (oder sobald die erste Protokollmeldung nach diesem Zeitpunkt ausgegeben wird), ../logs/error.log in ../logs/error.log.2010-01-20 umbenannt. Die Protokollierung für den 21. Januar erfolgt in (ein neues und leeres) ../logs/error.log und geht bei der nächsten Änderung zum nächsten Datum über. 
       | `&#39;.&#39;yyyy-MM` |Rotation at the beginning of each month |
       |---|---|
       | `&#39;.&#39;jjjj-ww&quot;|Drehung am ersten Wochentag (abhängig vom Gebietsschema). |
       | `&#39;.&#39;yyyy-MM-dd`|Rotation jeden Tag um Mitternacht. |
       | `&#39;.&#39;yyyy-MM-dd-a`|Rotation um Mitternacht und Mittag jeden Tages. |
       | `&#39;.&#39;yyyy-MM-dd-HH&quot;|Rotation am Anfang jeder Stunde. |
       | `&#39;.&#39;JJJJ-MM-TT-HH-mm&quot;|Drehung zu Beginn jeder Minute. |
       
       Note: When specifying a time/date:
       1. You should &quot;escape&quot; literal text within a pair of single quotes (&#39; &#39;);
       this is to avoid certain characters being interpreted as pattern letters.
       1. Verwenden Sie nur Zeichen, die für einen gültigen Dateinamen im Optionsfeld zulässig sind.
   

1. Lesen Sie die neue Protokolldatei mit dem von Ihnen ausgewählten Tool.

   The log file created by this example will be `../crx-quickstart/logs/myLogFile.log`.

The Felix Console also provides information about Sling Log Support at `../system/console/slinglog`; for example `https://localhost:4502/system/console/slinglog`.draf