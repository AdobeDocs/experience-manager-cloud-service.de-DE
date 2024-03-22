---
title: Validieren und Debuggen mit den Dispatcher-Tools
description: Erfahren Sie mehr über die lokale Validierung, das Debugging, die Dateistruktur mit flexiblem Modus und die Migration vom alten Modus zum flexiblen Modus.
feature: Dispatcher
exl-id: 9e8cff20-f897-4901-8638-b1dbd85f44bf
source-git-commit: 2cb57347856568da979b34832ce12cce295841dd
workflow-type: ht
source-wordcount: '3028'
ht-degree: 100%

---

# Validieren und Debuggen mit den Dispatcher-Tools {#Dispatcher-in-the-cloud}

## Einführung {#apache-and-dispatcher-configuration-and-testing}

>[!NOTE]
>Weitere Informationen zum Dispatcher in der Cloud und zum Herunterladen der Dispatcher-Tools finden Sie auf der Seite [Dispatcher in der Cloud](/help/implementing/dispatcher/disp-overview.md). Wenn sich Ihre Dispatcher-Konfiguration im alten Modus befindet, lesen Sie die [Dokumentation zum alten Modus](/help/implementing/dispatcher/validation-debug-legacy.md).

In den folgenden Abschnitten werden die Dateistruktur für den flexiblen Modus, die lokale Validierung, das Debugging und die Migration vom alten Modus zum flexiblen Modus beschrieben.

In diesem Artikel wird davon ausgegangen, dass die Dispatcher-Konfiguration Ihres Projekts die Datei `opt-in/USE_SOURCES_DIRECTLY` enthält. Diese Datei veranlasst das SDK und die Laufzeitumgebung, die Konfiguration auf eine im Vergleich zum alten Modus verbesserte Weise zu validieren und bereitzustellen. Dadurch werden Einschränkungen hinsichtlich der Anzahl und Größe von Dateien aufgehoben.

Wenn Ihre Dispatcher-Konfiguration jedoch die vorher genannte Datei nicht enthält, wird dringend empfohlen, vom alten Modus zum flexiblen Modus zu migrieren, wie im Abschnitt [Migration vom alten Modus zum flexiblen Modus](#migrating) beschrieben.

## Dateistruktur {#flexible-mode-file-structure}

Die Struktur des Dispatcher-Unterordners des Projekts sieht wie folgt aus:

```bash
./
├── conf.d
│   ├── available_vhosts
│   │   ├── my_site.vhost # Created by customer
│   │   └── default.vhost
│   ├── dispatcher_vhost.conf
│   ├── enabled_vhosts
│   │   ├── README
│   │   └── my_site.vhost -> ../available_vhosts/my_site.vhost  # Created by customer
│   └── rewrites
│   │   ├── default_rewrite.rules
│   │   └── rewrite.rules
│   └── variables
|       ├── custom.vars
│       └── global.vars
│── opt-in
│   └── USE_SOURCES_DIRECTLY
└── conf.dispatcher.d
    ├── available_farms
    │   ├── my_farm.farm # Created by customer
    │   └── default.farm
    ├── cache
    │   ├── default_invalidate.any
    │   ├── default_rules.any
    │   ├── marketing_query_parameters.any
    │   └── rules.any
    ├── clientheaders
    │   ├── clientheaders.any
    │   └── default_clientheaders.any
    ├── dispatcher.any
    ├── enabled_farms
    │   ├── README
    │   └── my_farm.farm -> ../available_farms/my_farm.farm  # Created by customer
    ├── filters
    │   ├── default_filters.any
    │   └── filters.any
    ├── renders
    │   └── default_renders.any
    └── virtualhosts
    │   ├── default_virtualhosts.any
    │   └── virtualhosts.any
    
```

Nachstehend finden Sie eine Erklärung zu wichtigen Dateien, die geändert werden können:

**Anpassbare Dateien**

Die folgenden Dateien sind anpassbar und werden bei der Bereitstellung in Ihre Cloud-Instanz übertragen:

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

Sie können über eine oder mehrere dieser Dateien verfügen. Sie enthalten `<VirtualHost>`-Einträge, die mit Host-Namen übereinstimmen und es Apache erlauben, den jeweiligen Domain-Traffic mit unterschiedlichen Regeln zu behandeln. Dateien werden im Verzeichnis `available_vhosts` erstellt und mit einer symbolischen Verknüpfung im Verzeichnis `enabled_vhosts` aktiviert. Aus den `.vhost`-Dateien werden andere Dateien wie Neuschreibungen und Variablen einbezogen.

>[!NOTE]
>
>Im flexiblen Modus sollten Sie relative Pfade anstelle von absoluten Pfaden verwenden.

Stellen Sie sicher, dass immer mindestens ein virtueller Host verfügbar ist, der den Server-Aliassen `\*.local`, `localhost`, und `127.0.0.1` entspricht, die für die Dispatcher-Invalidierung benötigt werden. Die Server-Aliasse `*.adobeaemcloud.net` und `*.adobeaemcloud.com` sind ebenfalls in mindestens einer vhost-Konfiguration erforderlich und werden für interne Adobe-Prozesse benötigt.

Wenn Sie den genauen Host abgleichen möchten, weil Sie mehrere vhost-Dateien haben, können Sie dem folgenden Beispiel folgen:

```
<VirtualHost *:80>
    ServerName    "example.com"
    # Put names of which domains are used for your published site/content here
    ServerAlias     "*example.com" "\*.local" "localhost" "127.0.0.1" "*.adobeaemcloud.net" "*.adobeaemcloud.com"
    # Use a document root that matches the one in conf.dispatcher.d/default.farm
    DocumentRoot "${DOCROOT}"
    # URI dereferencing algorithm is applied at Sling's level, do not decode parameters here
    AllowEncodedSlashes NoDecode
    # Add header breadcrumbs for help in troubleshooting which vhost file is chosen
    <IfModule mod_headers.c>
        Header add X-Vhost "publish-example-com"
    </IfModule>
  ...
</VirtualHost>
```

* `conf.d/enabled_vhosts/<CUSTOMER_CHOICE>.vhost`

Dieser Ordner enthält relative symbolische Links zu Dateien unter „conf.dispatcher.d/available_vhosts“.

Beispielbefehle, die zum Erstellen dieser symbolischen Verknüpfungen erforderlich sind:

Apple macOS, Linux und WSL

```
ln -s ../available_vhosts/wknd.vhost wknd.vhost
```

Microsoft Windows

```
mklink wknd.vhost ..\available_vhosts\wknd.vhost
```

>[!NOTE]
>
> Wenn Sie unter Windows mit symbolischen Links arbeiten, sollte sich Ihre Ausführung in einer Eingabeaufforderung mit erhöhten Rechten oder im Windows-Subsystem für Linux befinden, oder Sie sollten über die Berechtigung [Symbolische Links erstellen](https://docs.microsoft.com/de-de/windows/security/threat-protection/security-policy-settings/create-symbolic-links) verfügen.

* `conf.d/rewrites/rewrite.rules`

Diese Datei wird aus Ihren `.vhost`-Dateien einbezogen. Sie enthält eine Reihe von Neuschreibungsregeln für `mod_rewrite`.

* `conf.d/variables/custom.vars`

Diese Datei wird aus Ihren `.vhost`-Dateien einbezogen. Sie können an dieser Stelle Definitionen für Apache-Variablen einfügen.

* `conf.d/variables/global.vars`

Diese Datei wird aus Ihrer `dispatcher_vhost.conf`-Datei einbezogen. Sie können die Protokollebene von Dispatcher und Rewrite in dieser Datei ändern.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

Sie können eine oder mehrere dieser Dateien haben. Sie enthalten Farmen, um Hostnamen zuzuordnen und dem Dispatcher-Modul zu ermöglichen, jede Farm mit unterschiedlichen Regeln zu behandeln. Dateien werden im Verzeichnis `available_farms` erstellt und mit einer symbolischen Verknüpfung im Verzeichnis `enabled_farms` aktiviert. Aus den `.farm`-Dateien werden andere Dateien wie Filter, Cache-Regeln und andere übernommen.

* `conf.dispatcher.d/enabled_farms/<CUSTOMER_CHOICE>.farm`

Dieser Ordner enthält relative symbolische Links zu Dateien unter „conf.dispatcher.d/available_farms“.

Beispielbefehle, die zum Erstellen dieser symbolischen Verknüpfungen erforderlich sind:

Apple macOS, Linux und WSL

```
ln -s ../available_farms/wknd.farm wknd.farm
```

Microsoft Windows

```
mklink wknd.farm ..\available_farms\wknd.farm
```

>[!NOTE]
>
> Wenn Sie unter Windows mit symbolischen Links arbeiten, sollte sich Ihre Ausführung in einer Eingabeaufforderung mit erhöhten Rechten oder im Windows-Subsystem für Linux befinden, oder Sie sollten über die Berechtigung [Symbolische Links erstellen](https://docs.microsoft.com/de-de/windows/security/threat-protection/security-policy-settings/create-symbolic-links) verfügen.

* `conf.dispatcher.d/cache/rules.any`

Diese Datei wird aus Ihren `.farm`-Dateien einbezogen. Sie gibt Voreinstellungen für das Caching an.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

Diese Datei wird aus Ihren `.farm`-Dateien einbezogen. Sie gibt an, welche Anfragekopfzeilen an das Backend weitergeleitet werden sollen.

* `conf.dispatcher.d/filters/filters.any`

Diese Datei wird aus Ihren `.farm`-Dateien einbezogen. Sie enthält eine Reihe von Regeln, die ändern, welcher Traffic herausgefiltert werden und nicht bis zum Backend gelangen soll.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

Diese Datei wird aus Ihren `.farm`-Dateien einbezogen. Sie verfügt über eine Liste von Host-Namen oder URI-Pfaden, die per glob-Abgleich abgeglichen werden sollen. Durch diese Übereinstimmung wird ermittelt, welches Backend für die Bereitstellung einer Anfrage verwendet werden soll.

* `opt-in/USE_SOURCES_DIRECTLY`

Diese Datei ermöglicht eine flexiblere Dispatcher-Konfiguration und beseitigt frühere Einschränkungen in Bezug auf die Anzahl und Größe von Dateien. Außerdem bewirkt dies, dass das SDK und die Laufzeitumgebung die Konfiguration auf verbesserte Weise validieren und bereitstellen.

Die oben genannten Dateien verweisen auf die unten aufgeführten unveränderlichen Konfigurationsdateien. Änderungen an den unveränderlichen Dateien werden von Dispatchern in Cloud-Umgebungen nicht verarbeitet.

**Unveränderliche Konfigurationsdateien**

Diese Dateien sind Teil des Basis-Frameworks und erzwingen Standards und Best Practices. Die Dateien gelten als unveränderlich, da lokale Änderungen oder Löschungen keine Auswirkungen auf Ihre Bereitstellung haben. Der Grund dafür: Sie werden nicht in Ihre Cloud-Instanz übertragen.

Es wird empfohlen, dass die oben genannten Dateien auf die unten aufgeführten unveränderlichen Dateien verweisen, gefolgt von weiteren Anweisungen oder Überschreibungen. Wenn die Dispatcher-Konfiguration in einer Cloud-Umgebung bereitgestellt wird, wird die neueste Version der unveränderlichen Dateien verwendet, unabhängig davon, welche Version in der lokalen Entwicklung verwendet wurde.

* `conf.d/available_vhosts/default.vhost`

Enthält einen virtuellen Beispiel-Host. Erstellen Sie für Ihren eigenen virtuellen Host eine Kopie dieser Datei, passen Sie sie an, gehen Sie zu `conf.d/enabled_vhosts` und erstellen Sie eine symbolische Verknüpfung zu Ihrer angepassten Kopie.
Kopieren Sie die Datei „default.vhost“ nicht direkt in `conf.d/enabled_vhosts`.

Stellen Sie sicher, dass immer ein virtueller Host verfügbar ist, der mit den Server-Aliassen `\*.local`, `localhost` und `127.0.0.1` übereinstimmt, die für die Dispatcher-Invalidierung benötigt werden. Die Server-Aliase `*.adobeaemcloud.net` und `*.adobeaemcloud.com` werden für interne Adobe-Prozesse benötigt.

* `conf.d/dispatcher_vhost.conf`

Teil des Basis-Frameworks, das veranschaulicht, wie Ihre virtuellen Hosts und globalen Variablen einbezogen werden.

* `conf.d/rewrites/default_rewrite.rules`

Standard-Neuschreibungsregeln sind für ein Standardprojekt geeignet. Wenn Sie Anpassungen vornehmen müssen, ändern Sie `rewrite.rules`. Bei der Anpassung können Sie weiter zuerst die Standardregeln einbeziehen, wenn sie Ihren Anforderungen entsprechen.

* `conf.dispatcher.d/available_farms/default.farm`

Enthält eine beispielhafte Dispatcher-Farm. Erstellen Sie für Ihre eigene Farm eine Kopie dieser Datei, passen Sie sie an, gehen Sie zu `conf.d/enabled_farms` und erstellen Sie eine symbolische Verknüpfung zu Ihrer angepassten Kopie.

* `conf.dispatcher.d/cache/default_invalidate.any`

Teil des Basis-Frameworks, das beim Start generiert wird. Sie **müssen** diese Datei in jede Farm einbeziehen, die Sie definieren, und zwar im Abschnitt `cache/allowedClients`.

* `conf.dispatcher.d/cache/default_rules.any`

Standardmäßige Cache-Regeln, die für ein Standardprojekt geeignet sind. Wenn Sie Anpassungen vornehmen müssen, ändern Sie `conf.dispatcher.d/cache/rules.any`. Bei der Anpassung können Sie weiter zuerst die Standardregeln einbeziehen, wenn sie Ihren Anforderungen entsprechen.

* `conf.dispatcher.d/clientheaders/default_clientheaders.any`

Standardmäßige Anfragekopfzeilen zur Weiterleitung an das Backend, geeignet für ein Standardprojekt. Wenn Sie Anpassungen vornehmen müssen, ändern Sie `clientheaders.any`. Bei der Anpassung können Sie weiter zuerst die standardmäßigen Anfragekopfzeilen einbeziehen, wenn sie Ihren Anforderungen entsprechen.

* `conf.dispatcher.d/dispatcher.any`

Teil des Basis-Frameworks, das veranschaulicht, wie Ihre Dispatcher-Farmen einbezogen werden.

* `conf.dispatcher.d/filters/default_filters.any`

Standardfilter, die für ein Standardprojekt geeignet sind. Wenn Sie Anpassungen vornehmen müssen, ändern Sie `filters.any`. Bei der Anpassung können Sie weiter zuerst die Standardfilter einbeziehen, wenn sie Ihren Anforderungen entsprechen.

* `conf.dispatcher.d/renders/default_renders.any`

Teil des Basis-Frameworks; diese Datei wird beim Start generiert. Sie **müssen** diese Datei in jede Farm einbeziehen, die Sie definieren, und zwar im Abschnitt `renders`.

* `conf.dispatcher.d/virtualhosts/default_virtualhosts.any`

Standardmäßiges Host-Globbing für ein Standardprojekt. Wenn Sie Anpassungen vornehmen müssen, ändern Sie `virtualhosts.any`. Bei der Anpassung sollten Sie nicht das standardmäßige Host-Globbing einbeziehen, da dabei **jede** eingehende Anfrage abgeglichen wird.

## Unterstützte Apache-Module {#apache-modules}

Siehe [Unterstützte Apache-Module](/help/implementing/dispatcher/disp-overview.md#supported-directives).

## Lokale Validierung {#local-validation-flexible-mode}

>[!NOTE]
>
>Folgende Abschnitte enthalten Befehle aus den Mac- oder Linux®-Versionen des SDK, das Windows SDK kann jedoch auf ähnliche Weise verwendet werden.

Verwenden Sie das Skript `validate.sh` wie folgt:

```
$ validate.sh src/dispatcher
opt-in USE_SOURCES_DIRECTLY marker file detected
Phase 1: Dispatcher validator
Cloud manager validator 2.0.32
Phase 1 finished
Phase 2: httpd -t validation in docker image
values.csv not found in deployment folder: /Users/foo/src - using files in 'conf.d' and 'conf.dispatcher.d' subfolders directly
processing configuration subfolder: conf.d
processing configuration subfolder: conf.dispatcher.d
Running script /docker_entrypoint.d/10-check-environment.sh
Running script /docker_entrypoint.d/20-create-docroots.sh
Running script /docker_entrypoint.d/30-wait-for-backend.sh
Waiting until localhost is available
localhost resolves to ::1
Running script /docker_entrypoint.d/40-generate-allowed-clients.sh
Running script /docker_entrypoint.d/50-check-expiration.sh
Running script /docker_entrypoint.d/60-check-loglevel.sh
Running script /docker_entrypoint.d/70-check-forwarded-host-secret.sh
# Dispatcher configuration: (/etc/httpd/conf.dispatcher.d/dispatcher.any)
/farms {

... 

}
Syntax OK
Phase 2 finished
Phase 3: Immutability check
reading immutable file list from /etc/httpd/immutable.files.txt

...

no immutable file has been changed - check is SUCCESSFUL
Phase 3 finished
```

Das Skript umfasst die folgenden drei Phasen:

1. Es führt den Validator aus. Wenn die Konfiguration nicht gültig ist, schlägt das Skript fehl.
2. Es führt den Befehl `httpd -t` aus, um zu testen, ob die Syntax korrekt ist, sodass „Apache httpd“ gestartet werden kann. Bei Erfolg sollte die Konfiguration für die Bereitstellung bereit sein.
3. Überprüft, ob die Untergruppe der Dispatcher-SDK-Konfigurationsdateien, die unveränderlich sein sollen, wie im [Dateistruktur-Abschnitt](##flexible-mode-file-structure) beschrieben, nicht geändert wurde und der aktuellen SDK-Version entspricht.

Während einer Cloud Manager-Bereitstellung wird auch die `httpd -t`-Syntaxprüfung ausgeführt und alle Fehler werden in das `Build Images step failure`-Protokoll von Cloud Manager aufgenommen.

>[!NOTE]
>
>Im Abschnitt [Automatisches Laden und Validieren](#automatic-loading) finden Sie eine effiziente Alternative zum Ausführen von `validate.sh` nach jeder Konfigurationsänderung.

### Phase 1 {#first-phase}

Wenn eine Anweisung nicht in der Zulassungsliste enthalten ist, protokolliert das Tool einen Fehler und gibt einen Exit-Code zurück, der ungleich 0 ist. Außerdem werden alle Dateien mit dem Muster `conf.dispatcher.d/enabled_farms/*.farm` gescannt und folgende Punkte geprüft:

* Es gibt keine Filterregel, die „allows“ via `/glob` verwendet (weitere Informationen finden Sie unter [CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957)).
* Es wird keine Admin-Funktion verfügbar gemacht. Zum Beispiel Zugriff auf Pfade wie `/crx/de or /system/console`.

Das Validierungs-Tool meldet nur die verbotene Verwendung von Apache-Anweisungen, die nicht in der Whitelist enthalten sind. Es werden keine syntaktischen oder semantischen Probleme mit Ihrer Apache-Konfiguration gemeldet, da diese Informationen nur bei Apache-Modulen in einer laufenden Umgebung verfügbar sind.

Nachfolgend finden Sie Fehlerbehebungsverfahren für das Debugging häufiger Validierungsfehler, die vom Tool ausgegeben werden:

**Kann einen `conf.dispatcher.d`-Unterordner im Archiv nicht finden**

Ihr Archiv sollte Ordner `conf.d` und `conf.dispatcher.d` enthalten. Beachten Sie, dass Sie **nicht** das Präfix `etc/httpd` in Ihrem Archiv verwenden sollten.

**Keine Farm gefunden in`conf.dispatcher.d/enabled_farms`**

Ihre aktivierten Farmen sollten sich im angegebenen Unterordner befinden.

**Enthaltene Datei (…) muss wie folgt benannt sein: …**

Es gibt zwei Abschnitte in Ihrer Farm-Konfiguration, die eine bestimmte Datei enthalten **müssen**: `/renders` und `/allowedClients` im Abschnitt `/cache`. Diese Abschnitte müssen wie folgt aussehen:

```
/renders {
    $include "../renders/default_renders.any"
}
```

Und:

```
/allowedClients {
    $include "../cache/default_invalidate.any"
}
```

**Datei an unbekanntem Speicherort einbezogen: …**

Es gibt vier Abschnitte in Ihrer Farm-Konfiguration, in denen Sie Ihre eigene Datei einbeziehen können: `/clientheaders`, `filters`, `/rules` im Abschnitt `/cache` und `/virtualhosts`. Die darin enthaltenen Dateien müssen wie folgt benannt werden:

| Abschnitt | Dateinamen einbeziehen |
|------------------|--------------------------------------|
| `/clientheaders` | `../clientheaders/clientheaders.any` |
| `/filters` | `../filters/filters.any` |
| `/rules` | `../cache/rules.any` |
| `/virtualhosts` | `../virtualhosts/virtualhosts.any` |

Alternativ können Sie die **Standardversion** dieser Dateien einschließen, deren Namen das Wort `default_` vorangestellt wird, z. B. `../filters/default_filters.any`.

**Anweisung einbeziehen in (…), kein bekannter Speicherort: …**

Abgesehen von den sechs oben erwähnten Abschnitten ist die Verwendung der 
Anweisung `$include` nicht zulässig. So würde z. B. der folgende Text diesen Fehler erzeugen:

```
/invalidate {
    $include "../cache/invalidate.any"
}
```

**Zugelassene Clients/Renderer nicht einbezogen von: …**

Dieser Fehler tritt auf, wenn Sie im Abschnitt `/cache` kein „include“ für `/renders` und `/allowedClients` angeben. Siehe **einbezogene Datei (…) muss einen Namen haben: …**, um mehr zu erfahren.

**Filter darf kein glob-Muster nutzen, um Anfragen zuzulassen**

Es ist nicht sicher, Anfragen mit einer `/glob`-Stilregel zuzulassen, die mit der vollständigen Anfragezeile abgeglichen wird, beispielsweise

```
/0100 {
    /type "allow" /glob "GET *.css *"
}
```

Diese Anweisung soll Anfragen nach `css`-Dateien zulassen, lässt aber auch Anfragen nach **beliebigen** Ressourcen gefolgt von der Abfragezeichenfolge `?a=.css` zu. Daher ist die Verwendung solcher Filter verboten (siehe auch CVE-2016-0957).

**einbezogene Datei (…) stimmt mit keiner bekannten Datei überein**

Es gibt zwei Arten von Dateien in Ihrer virtuellen Apache-Host-Konfiguration, die als Include-Dateien definiert werden können: Umschreibungen und Variablen.

| Typ | Dateinamen einbeziehen |
|-----------|---------------------------------|
| Neuschreibungen | `conf.d/rewrites/rewrite.rules` |
| Variablen | `conf.d/variables/custom.vars` |

Im flexiblen Modus können auch andere Dateien eingeschlossen werden, sofern sie sich in Unterverzeichnissen (auf beliebiger Ebene) des Verzeichnisses `conf.d` mit dem folgenden Präfix befinden.

| Präfix des übergeordneten Verzeichnisses der Include-Datei |
|-------------------------------------|
| `conf.d/includes` |
| `conf.d/modsec` |
| `conf.d/rewrites` |

Sie können beispielsweise wie folgt eine Datei in ein neu erstelltes Unterverzeichnis unter `conf.d/includes` einfügen:

```
Include conf.d/includes/mynewdirectory/myincludefile.conf
```

Alternativ können Sie die **Standardversion** der Neuschreibungsregeln einbeziehen, deren Name `conf.d/rewrites/default_rewrite.rules` lautet.
Beachten Sie, dass es keine Standardversion der Variablendateien gibt.

**Veraltetes Konfigurations-Layout erkannt, Kompatibilitätsmodus wird aktiviert**

Diese Meldung weist darauf hin, dass Ihre Konfiguration das veraltete Layout von Version 1 aufweist, das eine vollständige Apache-Konfiguration und Dateien mit `ams_`-Präfixen enthält. Obwohl diese Konfiguration für
Abwärtskompatibilität weiterhin unterstützt wird, sollten Sie dennoch zum neuen Layout wechseln.

Die erste Phase kann auch **separat** anstatt vom Wrapper-Skript `validate.sh` ausgeführt werden.

Bei Ausführung mit Ihrem Maven-Artefakt oder Ihrem Unterverzeichnis `dispatcher/src` werden Validierungsfehler gemeldet:

```
$ validator full -relaxed dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-allowlisted directives:
  conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
  conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

Unter Windows unterscheidet der Dispatcher-Validator zwischen Groß- und Kleinschreibung. Daher kann er bei der Validierung der Konfiguration fehlschlagen, wenn Sie die Groß-/Kleinschreibung des Pfads, in dem sich Ihre Konfiguration befindet, nicht berücksichtigen, z. B.:

```
bin\validator.exe -relaxed full src
Cloud manager validator 2.0.xx
2021/03/15 18:15:40 Dispatcher configuration validation failed:
  conf.dispatcher.d\available_farms\default.farm:15: parent directory outside server root: c:\k\a\aem-dispatcher-sdk-windows-symlinks-testing3\dispatcher\src
```

Vermeiden Sie diesen Fehler, indem Sie den Pfad aus Windows Explorer kopieren und einfügen und dann an der Eingabeaufforderung einen `cd`-Befehl in diesen Pfad eingeben.

### Phase 2 {#second-phase}

In dieser Phase wird die Apache-Syntax überprüft, indem Apache HTTPD in einem Docker-Container gestartet wird. Docker muss lokal installiert sein, aber beachten Sie, dass es nicht erforderlich ist, AEM auszuführen.

>[!NOTE]
>
>Windows-Benutzerinnen und -Benutzer müssen Windows 10 Professional oder andere Distributionen verwenden, die Docker unterstützen. Dies ist eine Voraussetzung für das Ausführen und Debuggen von Dispatcher auf einem lokalen Computer.
>Sowohl für Windows als auch für macOS empfiehlt Adobe die Verwendung von Docker Desktop.

Diese Phase kann auch unabhängig über `bin/docker_run.sh src/dispatcher host.docker.internal:4503 8080` initiiert werden.

Während einer Cloud Manager-Bereitstellung wird auch die `httpd -t`-Syntaxprüfung durchgeführt, und alle Fehler werden in das Fehlerprotokoll des Cloud Manager Build Images-Schrittes aufgenommen.

### Phase 3 {#third-phase}

Wenn in dieser Phase ein Fehler auftritt, bedeutet dies, dass Adobe eine oder mehrere unveränderliche Dateien geändert hat. In diesem Fall müssen Sie die entsprechenden unveränderlichen Dateien durch die neue Version ersetzen, die im Verzeichnis `src` des SDK bereitgestellt wird. Das folgende Protokollbeispiel veranschaulicht dieses Problem:

```
Phase 3: Immutability check
reading immutable file list from /etc/httpd/immutable.files.txt
(...)
checking existing 'conf.dispatcher.d/clientheaders/default_clientheaders.any' for changes
immutable file 'conf.dispatcher.d/clientheaders/default_clientheaders.any' has been changed:
--- /etc/httpd/conf.dispatcher.d/clientheaders/default_clientheaders.any
+++ /etc/httpd-actual/conf.dispatcher.d/clientheaders/default_clientheaders.any
@@ -40,4 +40,3 @@
"Sling-uploadmode"
"x-requested-with"
"If-Modified-Since"
-"Authorization"
** error: immutable file 'conf.dispatcher.d/clientheaders/default_clientheaders.any' has been changed!
  
```

Diese Phase kann auch unabhängig über `bin/docker_immutability_check.sh src/dispatcher` ausgeführt werden.

Ihre lokalen unveränderlichen Dateien können aktualisiert werden, indem Sie das Skript `bin/update_maven.sh src/dispatcher` in Ihrem Dispatcher-Ordner ausführen, wobei `src/dispatcher` Ihr Dispatcher-Konfigurationsverzeichnis ist. Dieses Skript aktualisiert auch jede `pom.xml`-Datei im übergeordneten Verzeichnis, sodass die Maven-Unveränderlichkeitsprüfungen ebenfalls aktualisiert werden.

## Debuggen der Apache- und Dispatcher-Konfiguration {#debugging-apache-and-dispatcher-configuration}

Sie können Apache Dispatcher mit `./bin/docker_run.sh src/dispatcher docker.for.mac.localhost:4503 8080` lokal ausführen.

Wie bereits erwähnt, muss Docker lokal installiert sein und AEM muss nicht ausgeführt werden. Windows-Benutzerinnen und -Benutzer müssen Windows 10 Professional oder andere Distributionen verwenden, die Docker unterstützen. Dies ist eine Voraussetzung für das Ausführen und Debuggen von Dispatcher auf einem lokalen Computer.

Folgende Strategie kann verwendet werden, um die Protokollausgabe für das Dispatcher-Modul zu erhöhen und die Ergebnisse der `RewriteRule`-Bewertung in lokalen und Cloud-Umgebungen anzuzeigen.

Die Protokollierungsstufen für diese Module werden durch die Variablen `DISP_LOG_LEVEL` und `REWRITE_LOG_LEVEL` definiert. Sie können in der Datei `conf.d/variables/global.vars` festgelegt werden. Ihr relevanter Teil lautet:

```
# Log level for the dispatcher
#
# Possible values are: error, warn, info, debug and trace1
# Default value: warn
#
# Define DISP_LOG_LEVEL warn
 
# Log level for mod_rewrite
#
# Possible values are: error, warn, info, debug and trace1 - trace8
# Default value: warn
#
# To debug your RewriteRules, it is recommended to raise your log
# level to trace2.
#
# More information can be found at:
# https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging
#
# Define REWRITE_LOG_LEVEL warn
```

Wenn Sie Dispatcher lokal ausführen, werden Protokolle auch direkt an die Terminal-Ausgabe gedruckt. Meistens möchten Sie, dass sich diese Protokolle in DEBUG befinden. Dies kann durch Übergeben der Debug-Ebene als Parameter beim Ausführen von Docker erfolgen. Beispiel: `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh src docker.for.mac.localhost:4503 8080`.

Protokolle für Cloud-Umgebungen werden über den Protokoll-Serivice bereitgestellt, der in Cloud Manager verfügbar ist.

>[!NOTE]
>
>Für Umgebungen auf AEM as a Cloud Service ist „debug“ die maximale Ausführlichkeitsstufe. Die Trace-Protokollebene wird nicht unterstützt. Daher sollten Sie beim Arbeiten in Cloud-Umgebungen vermeiden, sie festzulegen.

### Automatisches erneutes Laden und Validieren {#automatic-reloading}

>[!NOTE]
>
>Aufgrund einer Beschränkung des Windows-Betriebssystems ist diese Funktion nur für Benutzerinnen und Benutzer von macOS und Linux® verfügbar.

Anstatt die lokale Validierung (`validate.sh`) auszuführen und den Docker-Container (`docker_run.sh`) jedes Mal zu starten, wenn die Konfiguration geändert wird, können Sie alternativ das Skript `docker_run_hot_reload.sh` ausführen. Das Skript überwacht alle Änderungen an der Konfiguration, lädt sie automatisch neu und führt die Überprüfung erneut aus. Durch die Verwendung dieser Option können Sie beim Debuggen erheblich Zeit sparen.

Sie können das Skript mit dem folgenden Befehl ausführen: `./bin/docker_run_hot_reload.sh src/dispatcher host.docker.internal:4503 8080`

Die ersten Zeilen der Ausgabe sehen ähnlich aus wie die für `docker_run.sh`. Zum Beispiel:

```
~ bin/docker_run_hot_reload.sh src host.docker.internal:8081 8082
opt-in USE_SOURCES_DIRECTLY marker file detected
Running script /docker_entrypoint.d/10-check-environment.sh
Running script /docker_entrypoint.d/15-check-pod-name.sh
Running script /docker_entrypoint.d/20-create-docroots.sh
Running script /docker_entrypoint.d/30-wait-for-backend.sh
Waiting until host.docker.internal is available
host.docker.internal resolves to 192.168.65.2
Running script /docker_entrypoint.d/40-generate-allowed-clients.sh
Running script /docker_entrypoint.d/50-check-expiration.sh
Running script /docker_entrypoint.d/60-check-loglevel.sh
Running script /docker_entrypoint.d/70-check-forwarded-host-secret.sh
Running script /docker_entrypoint.d/80-frontend-domain.sh
Running script /docker_entrypoint.d/zzz-import-sdk-config.sh
WARN Mon Jul  4 09:53:54 UTC 2022: Pseudo symlink conf.d seems to point to a non-existing file!
INFO Mon Jul  4 09:53:55 UTC 2022: Copied customer configuration to /etc/httpd.
INFO Mon Jul  4 09:53:55 UTC 2022: Start testing
Cloud manager validator 2.0.43
2022/07/04 09:53:55 No issues found
INFO Mon Jul  4 09:53:55 UTC 2022: Testing with fresh base configuration files.
INFO Mon Jul  4 09:53:55 UTC 2022: Apache httpd informationServer version: Apache/2.4.54 (Unix)
```

### Einfügen von benutzerdefinierten Umgebungsvariablen {#environment-variables}

Benutzerdefinierte Umgebungsvariablen können mit dem Dispatcher-SDK verwendet werden, indem sie in einer separaten Datei festgelegt und vor dem Start des lokalen Dispatchers in der Umgebungsvariable `ENV_FILE` referenziert werden.

Eine Datei mit benutzerdefinierten Umgebungsvariablen würde wie folgt aussehen:

```
COMMERCE_ENDPOINT=commerce-host
AEM_HTTP_PROXY_HOST=host.docker.internal
AEM_HTTP_PROXY_PORT=8000
```

Sie kann im lokalen Dispatcher-SDK mit den folgenden Befehlen verwendet werden:

```
export ENV_FILE=custom.env
./bin/docker_run.sh src/dispatcher docker.for.mac.localhost:4503 8080
```

## Verschiedene Dispatcher-Konfigurationen pro Umgebung {#different-dispatcher-configurations-per-environment}

Derzeit wird dieselbe Dispatcher-Konfiguration auf alle Umgebungen von AEM as a Cloud Service angewendet. Die Laufzeit verfügt über eine Umgebungsvariable `ENVIRONMENT_TYPE`, die den aktuellen Ausführungsmodus (Entwicklung, Staging oder Produktion) und ein „define“ enthält. „define“ kann `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` oder `ENVIRONMENT_PROD` lauten. In der Apache-Konfiguration kann die Variable direkt in einem Ausdruck verwendet werden. Alternativ kann „define“ zur Erstellung von Logik verwendet werden:

```
# Simple usage of the environment variable
ServerName ${ENVIRONMENT_TYPE}.company.com
 
# When more logic is required
<IfDefine ENVIRONMENT_STAGE>
  # These statements are for stage
  Define VIRTUALHOST stage.example.com
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  # These statements are for production
  Define VIRTUALHOST prod.example.com
</IfDefine>
```

In der Dispatcher-Konfiguration ist dieselbe Umgebungsvariable verfügbar. Wenn zusätzliche Logik erforderlich ist, definieren Sie die Variablen wie im Beispiel oben gezeigt und nutzen Sie sie dann im Abschnitt Dispatcher-Konfiguration:

```
/virtualhosts {
  { "${VIRTUALHOST}" }
}
```

Alternativ können Sie Cloud Manager-Umgebungsvariablen in Ihrer httpd/dispatcher-Konfiguration verwenden, jedoch keine Umgebungsgeheimnisse. Diese Methode ist besonders wichtig, wenn ein Programm mehrere Entwicklungsumgebungen hat und einige dieser Entwicklungsumgebungen unterschiedliche Werte für die httpd/dispatcher-Konfiguration haben. Es würde die gleiche ${VIRTUALHOST}-Syntax wie im obigen Beispiel verwendet werden, jedoch würden die Define-Deklarationen in der obigen Variablendatei nicht verwendet werden. Lesen Sie die [Cloud Manager-Dokumentation](/help/implementing/cloud-manager/environment-variables.md), um Anweisungen zur Konfiguration von Cloud Manager-Umgebungsvariablen zu erhalten.

Wenn Sie Ihre Konfiguration lokal testen, können Sie verschiedene Umgebungstypen simulieren, indem Sie die Variable `DISP_RUN_MODE` direkt an das Skript `docker_run.sh` übergeben:

```
$ DISP_RUN_MODE=stage docker_run.sh src docker.for.mac.localhost:4503 8080
```

Der Standardausführungsmodus, wenn kein Wert für DISP_RUN_MODE übergeben wird, ist „Dev“.
Für eine vollständige Liste der verfügbaren Optionen und Variablen führen Sie das Skript `docker_run.sh` ohne Argumente aus.

## Anzeigen der Dispatcher-Konfiguration, die von Ihrem Docker-Container verwendet wird {#viewing-dispatcher-configuration-in-use-by-docker-container}

Bei umgebungsspezifischen Konfigurationen kann es schwierig sein, die tatsächliche Dispatcher-Konfiguration zu bestimmen. Nachdem Sie Ihren Docker-Container mit `docker_run.sh` gestartet haben, kann er wie folgt ausgelesen werden:

* Bestimmen Sie die verwendete Docker-Container-ID:

```
$ docker ps
CONTAINER ID       IMAGE
d75fbd23b29        adobe/aem-ethos/dispatcher-publish:...
```

* Führen Sie die folgende Befehlszeile mit dieser Container-ID aus:

```
$ docker exec d75fbd23b29 httpd-test
# Dispatcher configuration: (/etc/httpd/conf.dispatcher.d/dispatcher.any)
/farms {
  /publishfarm {
    /clientheaders {
...
```

## Migration vom alten Modus zum flexiblen Modus {#migrating}

Mit der Cloud Manager-Version 2021.7.0 generieren neue Cloud Manager-Programme Maven-Projektstrukturen mit [AEM-Archetyp 28](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) oder höher, der die Datei **opt-in/USE_SOURCES_DIRECTLY** enthält. Dadurch werden frühere Einschränkungen des [veralteten Modus](/help/implementing/dispatcher/validation-debug-legacy.md) bezüglich der Anzahl und Größe von Dateien entfernt, was dazu führt, dass das SDK und die Laufzeitumgebung die Konfiguration auf verbesserte Weise validieren und bereitstellen. Wenn Ihre Dispatcher-Konfiguration nicht über diese Datei verfügt, wird eine Migration dringend empfohlen. Gehen Sie wie folgt vor, um einen sicheren Übergang zu gewährleisten:

1. **Lokale Tests.** Fügen Sie mithilfe des neuesten Dispatcher-Tools-SDK den Ordner und die Datei `opt-in/USE_SOURCES_DIRECTLY` hinzu. Befolgen Sie die Anweisungen in diesem Artikel zur „lokalen Validierung“, um zu testen, ob der Dispatcher lokal funktioniert.
1. **Cloud-Entwicklungstests:**
   * Übertragen Sie die Datei `opt-in/USE_SOURCES_DIRECTLY` in eine Git-Verzweigung, die von der produktionsfremden Pipeline in eine Cloud-Entwicklungsumgebung bereitgestellt wird.
   * Verwenden Sie Cloud Manager, um eine Bereitstellung in einer Cloud-Entwicklungsumgebung durchzuführen.
   * Führen Sie gründliche Tests durch. Es ist wichtig zu überprüfen, ob sich Ihre Apache- und Dispatcher-Konfiguration wie erwartet verhält, bevor Sie Änderungen in höheren Umgebungen bereitstellen. Überprüfen Sie das gesamte Verhalten im Zusammenhang mit Ihrer benutzerdefinierten Konfiguration. Senden Sie ein Support-Ticket, wenn Sie der Meinung sind, dass die bereitgestellte Dispatcher-Konfiguration Ihre benutzerdefinierte Konfiguration nicht widerspiegelt.

   >[!NOTE]
   >
   >Im flexiblen Modus sollten Sie relative Pfade anstelle von absoluten Pfaden verwenden.
1. **Bereitstellung für Produktion:**
   * Übertragen Sie die Datei `opt-in/USE_SOURCES_DIRECTLY` in eine Git-Verzweigung, die von der Produktions-Pipeline in die Staging- und Produktionsumgebungen der Cloud bereitgestellt wird.
   * Verwenden Sie Cloud Manager, um für die Staging-Umgebung bereitzustellen.
   * Führen Sie gründliche Tests durch. Es ist wichtig zu überprüfen, ob sich Ihre Apache- und Dispatcher-Konfiguration wie erwartet verhält, bevor Sie Änderungen in höheren Umgebungen bereitstellen. Überprüfen Sie das gesamte Verhalten im Zusammenhang mit Ihrer benutzerdefinierten Konfiguration. Senden Sie ein Support-Ticket, wenn Sie der Meinung sind, dass die bereitgestellte Dispatcher-Konfiguration Ihre benutzerdefinierte Konfiguration nicht widerspiegelt.
   * Verwenden Sie Cloud Manager, um die Bereitstellung für die Produktion fortzusetzen.
