---
title: Validieren und Debuggen mit den Dispatcher Tools
description: Validieren und Debuggen mit den Dispatcher Tools
feature: Dispatcher
exl-id: 9e8cff20-f897-4901-8638-b1dbd85f44bf
source-git-commit: 4dff6bf09fe9337c70adb654d3eff27f5b45f518
workflow-type: ht
source-wordcount: '2512'
ht-degree: 100%

---

# Validieren und Debuggen mit den Dispatcher Tools {#Dispatcher-in-the-cloud}

## Einführung {#apache-and-dispatcher-configuration-and-testing}

>[!NOTE]
>Weitere Informationen zum Dispatcher in der Cloud und zum Herunterladen der Dispatcher-Tools finden Sie auf der Seite [Dispatcher in der Cloud](/help/implementing/dispatcher/disp-overview.md). Wenn sich Ihre Dispatcher-Konfiguration im alten Modus befindet, lesen Sie die [Dokumentation zum alten Modus](/help/implementing/dispatcher/validation-debug-legacy.md).

In den folgenden Abschnitten werden die Dateistruktur für den flexiblen Modus, die lokale Validierung, das Debugging und die Migration vom alten Modus zum flexiblen Modus beschrieben.

In diesem Artikel wird davon ausgegangen, dass die Dispatcher-Konfiguration Ihres Projekts die Datei `opt-in/USE_SOURCES_DIRECTLY` enthält. Dadurch überprüfen das SDK und die Laufzeitumgebung die Konfiguration im Vergleich zum alten Modus und stellen sie besser bereit. Dadurch werden Einschränkungen hinsichtlich der Anzahl und Größe von Dateien beseitigt.

Wenn Ihre Dispatcher-Konfiguration jedoch nicht die oben genannte Datei enthält, wird **dringend empfohlen**, vom alten Modus zum flexiblen Modus zu migrieren, wie im Abschnitt [Migration vom alten Modus zum flexiblen Modus](#migrating) beschrieben.

## Dateistruktur {#flexible-mode-file-structure}

Die Struktur des Dispatcher-Unterordners des Projekts sieht wie folgt aus:

```bash
./
├── conf.d
│   ├── available_vhosts
│   │   └── default.vhost
│   ├── dispatcher_vhost.conf
│   ├── enabled_vhosts
│   │   ├── README
│   │   └── default.vhost -> ../available_vhosts/default.vhost
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
    │   └── default.farm
    ├── cache
    │   ├── default_invalidate.any
    │   ├── default_rules.any
    │   └── rules.any
    ├── clientheaders
    │   ├── clientheaders.any
    │   └── default_clientheaders.any
    ├── dispatcher.any
    ├── enabled_farms
    │   ├── README
    │   └── default.farm -> ../available_farms/default.farm
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

* `conf.d/rewrites/rewrite.rules`

Diese Datei wird aus Ihren `.vhost`-Dateien einbezogen. Sie enthält eine Reihe von Neuschreibungsregeln für `mod_rewrite`.

* `conf.d/variables/custom.vars`

Diese Datei wird aus Ihren `.vhost`-Dateien einbezogen. Sie können an dieser Stelle Definitionen für Apache-Variablen einfügen.

* `conf.d/variables/global.vars`

Diese Datei wird aus der Datei `dispatcher_vhost.conf` einbezogen. Sie können die Protokollebene von Dispatcher und Rewrite in dieser Datei ändern.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

Sie können eine oder mehrere dieser Dateien haben. Sie enthalten Farmen, um Hostnamen zuzuordnen und dem Dispatcher-Modul zu ermöglichen, jede Farm mit unterschiedlichen Regeln zu behandeln. Dateien werden im Verzeichnis `available_farms` erstellt und mit einer symbolischen Verknüpfung im Verzeichnis `enabled_farms` aktiviert. Aus den `.farm`-Dateien werden andere Dateien wie Filter, Cache-Regeln und andere einbezogen.

* `conf.dispatcher.d/cache/rules.any`

Diese Datei wird aus Ihren `.farm`-Dateien einbezogen. Sie gibt Voreinstellungen für das Caching an.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

Diese Datei wird aus Ihren `.farm`-Dateien einbezogen. Sie gibt an, welche Anfragekopfzeilen an das Backend weitergeleitet werden sollen.

* `conf.dispatcher.d/filters/filters.any`

Diese Datei wird aus Ihren `.farm`-Dateien einbezogen. Sie enthält eine Reihe von Regeln, die ändern, welcher Traffic herausgefiltert werden und nicht bis zum Backend gelangen soll.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

Diese Datei wird aus Ihren `.farm`-Dateien einbezogen. Sie verfügt über eine Liste von Host-Namen oder URI-Pfaden, die per glob-Abgleich abgeglichen werden sollen. Dadurch wird ermittelt, welches Backend für die Bereitstellung einer Anfrage verwendet werden soll.

* `opt-in/USE_SOURCES_DIRECTLY`

Diese Datei ermöglicht eine flexiblere Dispatcher-Konfiguration und beseitigt frühere Einschränkungen in Bezug auf die Anzahl und Größe von Dateien. Außerdem bewirkt dies, dass das SDK und die Laufzeitumgebung die Konfiguration auf verbesserte Weise validieren und bereitstellen.

Die oben genannten Dateien verweisen auf die unten aufgeführten unveränderlichen Konfigurationsdateien. Änderungen an den unveränderlichen Dateien werden von Dispatchern in Cloud-Umgebungen nicht verarbeitet.

**Unveränderliche Konfigurationsdateien**

Diese Dateien sind Teil des Basis-Frameworks und erzwingen Standards und Best Practices. Die Dateien gelten als unveränderlich, da lokale Änderungen oder Löschungen keine Auswirkungen auf Ihre Bereitstellung haben. Der Grund dafür: Sie werden nicht in Ihre Cloud-Instanz übertragen.

Es wird empfohlen, dass die oben genannten Dateien auf die unten aufgeführten unveränderlichen Dateien verweisen, gefolgt von weiteren Anweisungen oder Überschreibungen. Wenn die Dispatcher-Konfiguration in einer Cloud-Umgebung implementiert wird, wird die neueste Version der unveränderlichen Dateien verwendet, unabhängig davon, welche Version in der lokalen Entwicklung verwendet wurde.

* `conf.d/available_vhosts/default.vhost`

Enthält einen virtuellen Beispiel-Host. Erstellen Sie für Ihren eigenen virtuellen Host eine Kopie dieser Datei, passen Sie sie an, gehen Sie zu `conf.d/enabled_vhosts` und erstellen Sie eine symbolische Verknüpfung zu Ihrer angepassten Kopie.

Stellen Sie sicher, dass immer ein virtueller Host verfügbar ist, der dem ServerAlias `\*.local` und auch localhost entspricht, der für interne Adobe-Prozesse benötigt wird.

* `conf.d/dispatcher_vhost.conf`

Teil des Basis-Frameworks, das veranschaulicht, wie Ihre virtuellen Hosts und globalen Variablen einbezogen werden.

* `conf.d/rewrites/default_rewrite.rules`

Standardmäßige Neuschreibungsregeln, die für ein Standardprojekt geeignet sind. Wenn Sie Anpassungen vornehmen müssen, ändern Sie `rewrite.rules`. Bei der Anpassung können Sie weiter zuerst die Standardregeln einbeziehen, wenn sie Ihren Anforderungen entsprechen.

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
>Folgende Abschnitte enthalten Befehle aus den Mac- oder Linux-Versionen des SDK, das Windows SDK kann jedoch auf ähnliche Weise verwendet werden.

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
2. Es führt den Befehl `httpd -t` aus, um zu testen, ob die Syntax korrekt ist, sodass Apache httpd gestartet werden kann. Bei Erfolg sollte die Konfiguration für die Implementierung bereit sein.
3. Überprüft, ob die Untergruppe der Dispatcher-SDK-Konfigurationsdateien, die, wie im Abschnitt [Dateistruktur](##flexible-mode-file-structure) beschrieben, unveränderlich sein sollen, nicht geändert wurde.

Während einer Cloud Manager-Implementierung wird auch die `httpd -t`-Syntaxprüfung ausgeführt und alle Fehler werden in das `Build Images step failure`-Protokoll von Cloud Manager aufgenommen.

### Phase 1 {#first-phase}

Wenn eine Anweisung nicht in der Zulassungsliste enthalten ist, protokolliert das Tool einen Fehler und gibt einen Exit-Code zurück, der ungleich 0 ist. Außerdem werden alle Dateien mit dem Muster `conf.dispatcher.d/enabled_farms/*.farm` gescannt und folgende Punkte geprüft:

* Es gibt keine Filterregel, die „allows“ via `/glob` verwendet (weitere Informationen finden Sie unter [CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957)).
* Es wird keine Admin-Funktion verfügbar gemacht. Zum Beispiel Zugriff auf Pfade wie `/crx/de or /system/console`.

Beachten Sie, dass das Validierungs-Tool nur die verbotene Verwendung von Apache-Anweisungen meldet, die nicht in der Zulassungsliste enthalten sind. Es werden keine syntaktischen oder semantischen Probleme mit Ihrer Apache-Konfiguration gemeldet, da diese Informationen nur bei Apache-Modulen in einer laufenden Umgebung verfügbar sind.

Nachfolgend finden Sie Fehlerbehebungsverfahren für das Debugging häufiger Validierungsfehler, die vom Tool ausgegeben werden:

**kann einen `conf.dispatcher.d`-Unterordner im Archiv nicht finden**

Ihr Archiv sollte Ordner `conf.d` und `conf.dispatcher.d` enthalten. Beachten Sie, dass Sie **nicht** das Präfix `etc/httpd` in Ihrem Archiv verwenden sollten.

**kann keine Farm finden in`conf.dispatcher.d/enabled_farms`**

Ihre aktivierten Farmen sollten sich im angegebenen Unterordner befinden.

**einbezogene Datei (...) muss einen Namen haben: ...**

Es gibt zwei Abschnitte in Ihrer Farm-Konfiguration, die eine bestimmte Datei enthalten **müssen**: `/renders` und `/allowedClients` im Abschnitt `/cache`. Diese Abschnitte müssen wie folgt aussehen:

```
/renders {
    $include "../renders/default_renders.any"
}
```

und:

```
/allowedClients {
    $include "../cache/default_invalidate.any"
}
```

**Datei an unbekanntem Speicherort einbezogen: ...**

Es gibt vier Abschnitte in Ihrer Farm-Konfiguration, in denen Sie Ihre eigene Datei einbeziehen können: `/clientheaders`, `filters`, `/rules` im Abschnitt `/cache` und `/virtualhosts`. Die darin enthaltenen Dateien müssen wie folgt benannt werden:

| Abschnitt | Dateinamen einbeziehen |
|------------------|--------------------------------------|
| `/clientheaders` | `../clientheaders/clientheaders.any` |
| `/filters` | `../filters/filters.any` |
| `/rules` | `../cache/rules.any` |
| `/virtualhosts` | `../virtualhosts/virtualhosts.any` |

Alternativ können Sie die **Standardversion** dieser Dateien einbeziehen, deren Namen das Wort `default_` vorangestellt ist, z. B. `../filters/default_filters.any`.

**Anweisung einbeziehen in (...), kein bekannter Speicherort: ...**

Abgesehen von den sechs oben erwähnten Bereichen ist die Verwendung der `$include`-Anweisung nicht zulässig; es würde z. B. der folgende Fehler ausgegeben:

```
/invalidate {
    $include "../cache/invalidate.any"
}
```

**zulässige Clients/Renders nicht einbezogen von: ...**

Dieser Fehler wird generiert, wenn Sie keine Einbeziehung für `/renders` und `/allowedClients` im Abschnitt `/cache` angeben. Siehe **einbezogene Datei (...) muss einen Namen haben: ...**, um mehr zu erfahren.

**Filter darf kein glob-Muster nutzen, um Anfragen zuzulassen**

Es ist nicht sicher, Anfragen mit einer `/glob`-Stilregel zuzulassen, die mit der vollständigen Anfragezeile abgeglichen wird, z. B.

```
/0100 {
    /type "allow" /glob "GET *.css *"
}
```

Diese Anweisung soll Anfragen nach `css`-Dateien zulassen, lässt aber auch Anfragen nach **beliebigen** Ressourcen gefolgt von der Abfragezeichenfolge `?a=.css` zu. Daher ist die Verwendung solcher Filter verboten (siehe auch CVE-2016-0957).

**einbezogene Datei (...) stimmt mit keiner bekannten Datei überein**

Es gibt zwei Arten von Dateien in Ihrer Apache-Virtual-Host-Konfiguration, die wie folgt definiert werden können: Neuschreibungen und Variablen.
Die darin enthaltenen Dateien müssen wie folgt benannt werden:

| Typ | Dateinamen einbeziehen |
|-----------|---------------------------------|
| Neuschreibungen | `conf.d/rewrites/rewrite.rules` |
| Variablen | `conf.d/variables/custom.vars` |

Alternativ können Sie die **Standardversion** der Neuschreibungsregeln einbeziehen, deren Name `conf.d/rewrites/default_rewrite.rules` lautet.
Beachten Sie, dass es keine Standardversion der Variablendateien gibt.

**Veraltetes Konfigurations-Layout erkannt, Kompatibilitätsmodus wird aktiviert**

Diese Meldung weist darauf hin, dass Ihre Konfiguration das veraltete Layout von Version 1 aufweist, das eine vollständige Apache-Konfiguration und Dateien mit `ams_`-Präfixen enthält. Zwar wird dies für Abwärtskompatibilität weiterhin unterstützt, doch sollten Sie zum neuen Layout wechseln.

Beachten Sie, dass die erste Phase auch **separat ausgeführt** werden kann, anstatt vom Wrapper-`validate.sh`-Skript.

Bei Ausführung mit Ihrem Maven-Artefakt oder Ihrem `dispatcher/src`-Unterverzeichnis werden Validierungsfehler gemeldet:

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

Diese Phase überprüft die Apache-Syntax, indem Docker in einem Image gestartet wird. Docker muss lokal installiert sein, aber beachten Sie, dass es nicht erforderlich ist, AEM auszuführen.

>[!NOTE]
>
>Windows-Benutzer müssen Windows 10 Professional oder andere Distributionen verwenden, die Docker unterstützen. Dies ist eine Voraussetzung für das Ausführen und Debuggen von Dispatcher auf einem lokalen Computer.

Diese Phase kann auch unabhängig über `bin/docker_run.sh src/dispatcher host.docker.internal:4503 8080` ausgeführt werden.

Bei einer Cloud Manager-Implementierung wird auch die `httpd -t`-Syntax-Prüfung ausgeführt und etwaige Fehler werden in das Fehlerprotokoll für den Schritt „Erstellen von Images von Cloud Manager“ aufgenommen.

### Phase 3 {#third-phase}

Wenn in dieser Phase ein Fehler auftritt, bedeutet dies, dass Adobe eine oder mehrere unveränderliche Dateien geändert hat. Sie müssen die entsprechenden unveränderlichen Dateien durch die neue Version ersetzen, die im Verzeichnis `src` des SDK bereitgestellt wird. Das folgende Protokollbeispiel veranschaulicht dieses Problem:

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

## Debuggen der Apache- und Dispatcher-Konfiguration {#debugging-apache-and-dispatcher-configuration}

Beachten Sie, dass Sie den Apache-Dispatcher lokal mit `./bin/docker_run.sh src/dispatcher docker.for.mac.localhost:4503 8080` ausführen können.

Wie bereits erwähnt, muss Docker lokal installiert sein und AEM muss nicht ausgeführt werden. Windows-Benutzer müssen Windows 10 Professional oder andere Distributionen verwenden, die Docker unterstützen. Dies ist eine Voraussetzung für das Ausführen und Debuggen von Dispatcher auf einem lokalen Computer.

Folgende Strategie kann verwendet werden, um die Protokollausgabe für das Dispatcher-Modul zu erhöhen und die Ergebnisse der `RewriteRule`-Bewertung in lokalen und Cloud-Umgebungen anzuzeigen.

Die Protokollierungsstufen für diese Module werden durch die Variablen `DISP_LOG_LEVEL` und `REWRITE_LOG_LEVEL` definiert. Sie können in der Datei `conf.d/variables/global.vars` festgelegt werden. Ihr relevanter Teil lautet:

```
# Log level for the dispatcher
#
# Possible values are: Error, Warn, Info, Debug and Trace1
# Default value: Warn
#
# Define DISP_LOG_LEVEL Warn
 
# Log level for mod_rewrite
#
# Possible values are: Error, Warn, Info, Debug and Trace1 - Trace8
# Default value: Warn
#
# To debug your RewriteRules, it is recommended to raise your log
# level to Trace2.
#
# More information can be found at:
# https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging
#
# Define REWRITE_LOG_LEVEL Warn
```

Wenn Sie Dispatcher lokal ausführen, werden Protokolle auch direkt an die Terminal-Ausgabe gedruckt. Meistens möchten Sie, dass sich diese Protokolle in DEBUG befinden. Dies kann durch Übergeben der Debug-Ebene als Parameter beim Ausführen von Docker erfolgen. Beispiel: `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh src docker.for.mac.localhost:4503 8080`.

Protokolle für Cloud-Umgebungen werden über den Protokoll-Serivice bereitgestellt, der in Cloud Manager verfügbar ist.

## Verschiedene Dispatcher-Konfigurationen pro Umgebung {#different-dispatcher-configurations-per-environment}

Derzeit wird dieselbe Dispatcher-Konfiguration auf alle AEM as a Cloud Service-Umgebungen angewendet. Die Laufzeitumgebung verfügt über eine Umgebungsvariable `ENVIRONMENT_TYPE`, die den aktuellen Ausführungsmodus (dev, stage oder prod) sowie eine Definition enthält. Die Definition kann `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` oder `ENVIRONMENT_PROD` lauten. In der Apache-Konfiguration kann die Variable direkt in einem Ausdruck verwendet werden. Alternativ kann „define“ zur Erstellung von Logik verwendet werden:

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

Wenn Sie Ihre Konfiguration lokal testen, können Sie verschiedene Umgebungstypen simulieren, indem Sie die Variable direkt `DISP_RUN_MODE` an das `docker_run.sh`-Skript übergeben:

```
$ DISP_RUN_MODE=stage docker_run.sh src docker.for.mac.localhost:4503 8080
```

Der Standardausführungsmodus, wenn kein Wert für DISP_RUN_MODE übergeben wird, ist „dev“.
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

Mit der Cloud Manager-Version 2021.7.0 generieren neue Cloud Manager-Programme Maven-Projektstrukturen mit [AEM-Archetyp 28](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) oder höher, der die Datei **opt-in/USE_SOURCES_DIRECTLY** enthält. Dadurch werden frühere Einschränkungen des [alten Modus](/help/implementing/dispatcher/validation-debug-legacy.md) bezüglich der Anzahl und Größe von Dateien entfernt, was dazu führt, dass das SDK und die Laufzeitumgebung die Konfiguration auf verbesserte Weise validieren und bereitstellen. Wenn Ihre Dispatcher-Konfiguration nicht über diese Datei verfügt, wird eine Migration dringend empfohlen. Gehen Sie wie folgt vor, um einen sicheren Übergang zu gewährleisten:

1. **Lokale Tests.** Fügen Sie mithilfe des neuesten Dispatcher-Tools-SDK den Ordner und die Datei `opt-in/USE_SOURCES_DIRECTLY` hinzu. Befolgen Sie die Anweisungen in diesem Artikel zur „lokalen Validierung“, um zu testen, ob der Dispatcher lokal funktioniert.
2. **Cloud-Entwicklungstests:**
   * Übertragen Sie die Datei `opt-in/USE_SOURCES_DIRECTLY` in eine Git-Verzweigung, die von der produktionsfremden Pipeline in eine Cloud-Entwicklungsumgebung bereitgestellt wird.
   * Verwenden Sie Cloud Manager, um eine Bereitstellung in einer Cloud-Entwicklungsumgebung durchzuführen.
   * Führen Sie gründliche Tests durch. Es ist wichtig zu überprüfen, ob sich Ihre Apache- und Dispatcher-Konfiguration wie erwartet verhält, bevor Sie Änderungen in höheren Umgebungen implementieren. Überprüfen Sie das gesamte Verhalten im Zusammenhang mit Ihrer benutzerdefinierten Konfiguration! Senden Sie ein Support-Ticket, wenn Sie der Meinung sind, dass die bereitgestellte Dispatcher-Konfiguration Ihre benutzerdefinierte Konfiguration nicht widerspiegelt.
3. **Bereitstellung für Produktion:**
   * Übertragen Sie die Datei `opt-in/USE_SOURCES_DIRECTLY` in eine Git-Verzweigung, die von der Produktions-Pipeline in die Staging- und Produktionsumgebungen der Cloud bereitgestellt wird.
   * Verwenden Sie Cloud Manager, um für die Staging-Umgebung bereitzustellen.
   * Führen Sie gründliche Tests durch. Es ist wichtig zu überprüfen, ob sich Ihre Apache- und Dispatcher-Konfiguration wie erwartet verhält, bevor Sie Änderungen in höheren Umgebungen implementieren. Überprüfen Sie das gesamte Verhalten im Zusammenhang mit Ihrer benutzerdefinierten Konfiguration! Senden Sie ein Support-Ticket, wenn Sie der Meinung sind, dass die bereitgestellte Dispatcher-Konfiguration Ihre benutzerdefinierte Konfiguration nicht widerspiegelt.
   * Verwenden Sie Cloud Manager, um die Implementierung für die Produktion fortzusetzen.
