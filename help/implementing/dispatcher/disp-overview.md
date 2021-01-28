---
title: Dispatcher in der Cloud
description: 'Dispatcher in der Cloud '
translation-type: tm+mt
source-git-commit: 49b2f4abf64e404fcda7ea8d35e3ab9dc5fec90f
workflow-type: tm+mt
source-wordcount: '4119'
ht-degree: 87%

---


# Dispatcher in der Cloud {#Dispatcher-in-the-cloud}

## Konfiguration und Testen von Apache und Dispatcher {#apache-and-dispatcher-configuration-and-testing}

In diesem Abschnitt wird beschrieben, wie Sie die Apache- und Dispatcher-Konfigurationen von AEM as a Cloud Service strukturieren und vor der Bereitstellung in Cloud-Umgebungen lokal validieren und ausführen. Außerdem wird das Debugging in Cloud-Umgebungen beschrieben. Weitere Informationen zu Dispatcher finden Sie in der [AEM Dispatcher-Dokumentation](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/dispatcher.html).

>[!NOTE]
>Windows-Benutzer müssen Windows 10 Professional oder andere Distributionen verwenden, die Docker unterstützen. Dies ist eine Voraussetzung für das Ausführen und Debuggen von Dispatcher auf einem lokalen Computer. Folgende Abschnitte enthalten Befehle mit den Mac- oder Linux-Versionen des SDK, das Windows SDK kann jedoch auf ähnliche Weise verwendet werden.

## Dispatcher Tools {#dispatcher-sdk}

Die Dispatcher Tools sind Teil des gesamten AEM as a Cloud Service-SDK und bieten:

* eine Vanilla-Dateistruktur mit den Konfigurationsdateien, die in ein Maven-Projekt für Dispatcher aufgenommen werden sollen.
* Tooling für Kunden, um zu überprüfen, ob die Dispatcher-Konfiguration nur AEM als vom Cloud Service unterstützte Direktiven enthält.        Darüber hinaus überprüft die Tooling, ob die Syntax korrekt ist, sodass Apache erfolgreich Beginn ausführen kann.
* ein Docker-Image, das Dispatcher lokal aufruft.

## Herunterladen und Extrahieren der Tools {#extracting-the-sdk}

Die Dispatcher-Tools, die zum [AEM als Cloud Service-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) gehören, können von einer ZIP-Datei unter [Softwareverteilung](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html) heruntergeladen werden. Jede neue Konfiguration, die in dieser neuen Dispatcher-Tools-Version verfügbar ist, kann für die Bereitstellung auf Cloud-Umgebung verwendet werden, auf denen diese AEM in der Cloud oder höher ausgeführt werden.

Entpacken Sie das SDK, das Dispatcher-Tools für macOS/Linux und Windows bündelt.

**Machen Sie für macOS/Linux** das Dispatcher-Tool Artefakt ausführbar und führen Sie es aus. Es extrahiert selbst die Dispatcher Tools-Dateien unter dem Verzeichnis, in dem Sie sie gespeichert haben (wobei `version` die Version der Dispatcher Tools ist).

```bash
$ chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
$ ./aem-sdk-dispatcher-tools-<version>-unix.sh
Verifying archive integrity...  100%   All good.
Uncompressing aem-sdk-dispatcher-tools-<version>-unix.sh 100%
```

**Unter Windows** extrahieren Sie das ZIP-Archiv für Dispatcher Tooling.

## Dateistruktur {#file-structure}

Die Struktur des Dispatcher-Unterordners des Projekts wird nachfolgend beschrieben und sollte in den Dispatcher-Ordner des Maven-Projekts kopiert werden:

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
        ├── default_virtualhosts.any
        └── virtualhosts.any
```

Nachstehend finden Sie eine Erklärung zu wichtigen Dateien, die geändert werden können:

**Anpassbare Dateien**

Die folgenden Dateien sind anpassbar und werden bei der Bereitstellung in Ihre Cloud-Instanz übertragen:

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

Sie können über eine oder mehrere dieser Dateien verfügen. Sie enthalten `<VirtualHost>`-Einträge, die mit Host-Namen übereinstimmen und es Apache erlauben, den jeweiligen Domänen-Traffic mit unterschiedlichen Regeln zu behandeln. Dateien werden im Verzeichnis `available_vhosts` erstellt und mit einer symbolischen Verknüpfung im Verzeichnis `enabled_vhosts` aktiviert. Aus den `.vhost`-Dateien werden andere Dateien wie Neuschreibungen und Variablen einbezogen.

* `conf.d/rewrites/rewrite.rules`

Diese Datei wird aus Ihren `.vhost`-Dateien einbezogen. Sie enthält eine Reihe von Neuschreibungsregeln für `mod_rewrite`.

>[!NOTE]
>
>Zu diesem Zeitpunkt muss eine einzelne Rewrite-Datei anstelle Site-spezifischer Dateien verwendet werden. Diese Dateigröße muss kleiner als 1 MB sein.

* `conf.d/variables/custom.vars`

Diese Datei wird aus Ihren `.vhost`-Dateien einbezogen. Sie können an dieser Stelle Definitionen für Apache-Variablen einfügen.

* `conf.d/variables/global.vars`

Diese Datei wird aus der Datei `dispatcher_vhost.conf` heraus einbezogen. Sie können Dispatcher ändern und die Protokollebene in dieser Datei neu schreiben.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

Sie können über eine oder mehrere dieser Dateien verfügen; und sie enthalten Farmen, um Host-Namen abzustimmen und es dem Dispatcher-Modul zu ermöglichen, jede Farm mit unterschiedlichen Regeln zu behandeln. Dateien werden im Verzeichnis `available_farms` erstellt und mit einer symbolischen Verknüpfung im Verzeichnis `enabled_farms` aktiviert. Aus den `.farm`-Dateien werden andere Dateien wie Filter, Cache-Regeln und andere einbezogen.

* `conf.dispatcher.d/cache/rules.any`

Diese Datei wird aus Ihren `.farm`-Dateien einbezogen. Sie gibt Voreinstellungen für das Caching an.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

Diese Datei wird aus Ihren `.farm`-Dateien einbezogen. Sie gibt an, welche Anfragekopfzeilen an das Backend weitergeleitet werden sollen.

* `conf.dispatcher.d/filters/filters.any`

Diese Datei wird aus Ihren `.farm`-Dateien einbezogen. Sie enthält eine Reihe von Regeln, die ändern, welcher Traffic herausgefiltert werden und nicht bis zum Backend gelangen soll.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

Diese Datei wird aus Ihren `.farm`-Dateien einbezogen. Sie verfügt über eine Liste von Host-Namen oder URI-Pfaden, die per glob-Abgleich abgeglichen werden sollen. Dadurch wird ermittelt, welches Backend für die Bereitstellung einer Anfrage verwendet werden soll.

Die oben genannten Dateien verweisen auf die unten aufgeführten unveränderlichen Konfigurationsdateien. Änderungen an den unveränderlichen Dateien werden von Dispatchern in Cloud-Umgebungen nicht verarbeitet.

**Unveränderliche Konfigurationsdateien**

Diese Dateien sind Teil des Basis-Frameworks und erzwingen Standards und Best Practices. Die Dateien gelten als unveränderlich, da lokale Änderungen oder Löschungen keine Auswirkungen auf Ihre Bereitstellung haben. Der Grund dafür: Sie werden nicht in Ihre Cloud-Instanz übertragen.

Es wird empfohlen, dass die oben genannten Dateien auf die unten aufgeführten unveränderlichen Dateien verweisen, gefolgt von weiteren Anweisungen oder Überschreibungen. Wenn die Dispatcher-Konfiguration in einer Cloud-Umgebung bereitgestellt wird, wird die neueste Version der unveränderlichen Dateien verwendet, unabhängig davon, welche Version in der lokalen Entwicklung verwendet wurde.

* `conf.d/available_vhosts/default.vhost`

Enthält einen virtuellen Beispiel-Host. Erstellen Sie für Ihren eigenen virtuellen Host eine Kopie dieser Datei, passen Sie sie an, gehen Sie zu `conf.d/enabled_vhosts` und erstellen Sie eine symbolische Verknüpfung zu Ihrer angepassten Kopie.

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

>[!NOTE]
>
>Der Maven-Archetyp von AEM as a Cloud Service generiert dieselbe Dateistruktur der Dispatcher-Konfiguration.

In den folgenden Abschnitten wird beschrieben, wie Sie die Konfiguration lokal validieren, damit sie beim Bereitstellen einer internen Version das zugehörige Qualitäts-Gate in Cloud Manager übergeben kann.

## Lokale Validierung unterstützter Direktiven in der Dispatcher-Konfiguration {#local-validation-of-dispatcher-configuration}

Das Validierungs-Tool ist im SDK `bin/validator` als macOS-, Linux- oder Windows-Binärdatei verfügbar, sodass Kunden die gleiche Validierung ausführen können, die Cloud Manager beim Erstellen und Bereitstellen einer Version vornimmt.

Es wird wie folgt aufgerufen: `validator full [-d folder] [-w allowlist] zip-file | src folder`

Das Tool überprüft, ob die Dispatcher-Konfiguration die entsprechenden Richtlinien verwendet, die von AEM als Cloud-Dienst unterstützt werden, indem alle Dateien mit dem Muster `conf.d/enabled_vhosts/*.vhost` überprüft werden. Die in den Apache-Konfigurationsdateien zulässigen Anweisungen können aufgelistet werden, indem Sie den Zulassungslistenbefehl des Validators ausführen:

```
$ validator allowlist
Cloud manager validator 2.0.4
 
Allowlisted directives:
  <Directory>
  ...
  
```

In der folgenden Tabelle werden die unterstützten Apache-Module angezeigt:

| Modulname | Referenzseite |
|---|---|
| `core` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/core.html) |
| `mod_access_compat` | [https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html) |
| `mod_alias` | [https://httpd.apache.org/docs/2.4/mod/mod_alias.html](https://httpd.apache.org/docs/2.4/mod/mod_alias.html) |
| `mod_allowmethods` | [https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html](https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html) |
| `mod_authn_core` | [https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html) |
| `mod_authn_file` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_file.html) |
| `mod_authz_core` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_core.html) |
| `mod_authz_groupfile` | [https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html) |
| `mod_deflate` | [https://httpd.apache.org/docs/2.4/mod/mod_deflate.html](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html) |
| `mod_dir` | [https://httpd.apache.org/docs/2.4/mod/mod_dir.html](https://httpd.apache.org/docs/2.4/mod/mod_dir.html) |
| `mod_env` | [https://httpd.apache.org/docs/2.4/mod/mod_env.html](https://httpd.apache.org/docs/2.4/mod/mod_env.html) |
| `mod_filter` | [https://httpd.apache.org/docs/2.4/mod/mod_filter.html](https://httpd.apache.org/docs/2.4/mod/mod_filter.html) |
| `mod_headers` | [https://httpd.apache.org/docs/2.4/mod/mod_headers.html](https://httpd.apache.org/docs/2.4/mod/mod_headers.html) |
| `mod_mime` | [https://httpd.apache.org/docs/2.4/mod/mod_mime.html](https://httpd.apache.org/docs/2.4/mod/mod_mime.html) |
| `mod_remoteip` | [https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html](https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html) |
| `mod_reqtimeout` | [https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html](https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html) |
| `mod_rewrite` | [https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html) |
| `mod_security` | [https://modsecurity.org/](https://modsecurity.org/) |
| `mod_setenvif` | [https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html) |
| `mod_substitute` | [https://httpd.apache.org/docs/2.4/mod/mod_substitute.html](https://httpd.apache.org/docs/2.4/mod/mod_substitute.html) |
| `mod_userdir` | [https://httpd.apache.org/docs/2.4/mod/mod_userdir.html](https://httpd.apache.org/docs/2.4/mod/mod_userdir.html) |

Kunden können keine beliebigen Module hinzufügen. Es werden jedoch ggf. zusätzliche Module in Betracht gezogen, die in Zukunft in das Produkt aufgenommen werden. Die Kunden können die Liste der für eine bestimmte Dispatcher-Version verfügbaren Anweisungen finden, indem sie den Zulassungslistenbefehl des Validators im SDK ausführen, wie oben beschrieben.

Die Zulassungsliste enthält eine Liste der Apache-Anweisungen, die in einer Kundenkonfiguration zulässig sind. Wenn eine Anweisung nicht in der Zulassungsliste enthalten ist, protokolliert das Tool einen Fehler und gibt einen Exit-Code zurück, der ungleich 0 ist. Wenn in der Befehlszeile keine Zulassungsliste angegeben ist (auf diese Weise sollte sie aufgerufen werden), verwendet das Tool eine standardmäßige Zulassungsliste, die Cloud Manager vor der Bereitstellung in Cloud-Umgebungen zur Validierung nutzt.

Außerdem werden alle Dateien mit dem Muster `conf.dispatcher.d/enabled_farms/*.farm` gescannt und folgende Punkte geprüft:

* Es gibt keine Filterregel, die „allows“ via `/glob` verwendet (weitere Informationen finden Sie unter [CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957)).
* Es wird keine Admin-Funktion verfügbar gemacht. Zum Beispiel Zugriff auf Pfade wie `/crx/de or /system/console`.

Bei Ausführung mit Ihrem Maven-Artefakt oder Ihrem `dispatcher/src`-Unterverzeichnis werden Validierungsfehler gemeldet:

```
$ validator full dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-allowlisted directives:
  conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
  conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

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

## Lokale Validierung der Konfigurationssyntax des Dispatchers, damit apache httpd Beginn {#local-validation}

Sobald festgestellt wurde, dass die Konfiguration des Dispatcher-Moduls nur unterstützte Direktiven enthält, sollten Sie überprüfen, ob die Syntax korrekt ist, damit apache Beginn machen kann. Um dies zu testen, muss der Docker lokal installiert sein. Beachten Sie, dass AEM nicht laufen muss.

Verwenden Sie das Skript `validate.sh` wie folgt:

```
$ validate.sh src/dispatcher
Phase 1: Dispatcher validator
2019/06/19 16:02:55 No issues found
Phase 1 finished
Phase 2: httpd -t validation in docker image
Running script /docker_entrypoint.d/10-create-docroots.sh
Running script /docker_entrypoint.d/20-wait-for-backend.sh
Waiting until aemhost is available
aemhost resolves to xx.xx.xx.xx
Running script /docker_entrypoint.d/30-allowed-clients.sh
# Dispatcher configuration: (/etc/httpd/conf.dispatcher.d/dispatcher.any)
/farms {
...
}
Syntax OK
Phase 2 finished
```

Das Skript führt Folgendes aus:

1. Es führt den Validator aus dem vorherigen Abschnitt aus, um sicherzustellen, dass nur die unterstützten Direktiven einbezogen werden. Wenn die Konfiguration nicht gültig ist, schlägt das Skript fehl.
2. Es führt das `httpd -t command` aus, um zu testen, ob die Syntax so korrekt ist, dass apache httpd Beginn kann. Bei erfolgreichem Abschluss sollte die Konfiguration bereit für die Bereitstellung sein.
3. Überprüft, ob die Untergruppe der Dispatcher SDK-Konfigurationsdateien, die wie im Abschnitt [Dateistruktur](#file-structure) beschrieben unveränderlich sein sollen, nicht geändert wurde. Dies ist eine neue Prüfung, die mit AEM SDK-Version v2021.1.4738 eingeführt wurde und die auch Dispatcher Tools Version 2.0.36 enthält. Vor dieser Aktualisierung haben Kunden möglicherweise fälschlicherweise angenommen, dass alle lokalen SDK-Änderungen dieser unveränderlichen Dateien auch auf die Cloud-Umgebung angewendet werden.

Während einer Cloud Manager-Bereitstellung wird auch die `httpd -t syntax`-Prüfung ausgeführt und alle Fehler werden in das Cloud Manager `Build Images step failure`-Protokoll aufgenommen.

## Lokales Testen der Apache- und Dispatcher-Konfiguration {#testing-apache-and-dispatcher-configuration-locally}

Sie können Ihre Apache- und Dispatcher-Konfiguration auch lokal testen. Dazu muss der Docker lokal installiert sein und Ihre Konfiguration, um die Validierung wie oben beschrieben zu bestehen.

Führen Sie das Validator-Tool aus (beachten Sie, dass es sich von dem zuvor erwähnten `validator.sh` unterscheidet), indem Sie den Parameter `-d` verwenden, der einen Ordner mit allen Dispatcher-Konfigurationsdateien ausgibt. Führen Sie dann das Skript `docker_run.sh` aus und übergeben Sie diesen Ordner als Argument. Durch Angabe der Anschlussnummer (hier: 8080), um den Dispatcher-Endpunkt anzuzeigen, wird ein Docker-Container gestartet, der den Dispatcher mit Ihrer Konfiguration ausführt.

```
$ validator full -d out src/dispatcher
2019/06/19 16:02:55 No issues found
$ docker_run.sh out docker.for.mac.localhost:4503 8080
Running script /docker_entrypoint.d/10-create-docroots.sh
Running script /docker_entrypoint.d/20-wait-for-backend.sh
Waiting until aemhost is available
aemhost resolves to xx.xx.xx.xx
Running script /docker_entrypoint.d/30-allowed-clients.sh
Starting httpd server
...
```

Dadurch wird Dispatcher in einem Container gestartet, wobei sein Backend auf eine AEM-Instanz verweist, die auf Ihrem lokalen macOS-Computer über Port 4503 ausgeführt wird.

## Debuggen der Apache- und Dispatcher-Konfiguration {#debugging-apache-and-dispatcher-configuration}

Die folgende Strategie kann verwendet werden, um die Protokollausgabe für das Dispatcher-Modul zu erhöhen und die Ergebnisse der `RewriteRule`-Auswertung sowohl in lokalen als auch in Cloud-Umgebung zu sehen.

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

Wenn Dispatcher lokal ausgeführt wird, werden Protokolle direkt in die Terminalausgabe gedruckt. Meistens sollen diese Protokolle in DEBUG sein, was durch Übergeben der Debug-Ebene als Parameter bei Ausführung von Docker erreicht werden kann. Beispiel: `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`.

Protokolle für Cloud-Umgebung werden über den Protokolldienst bereitgestellt, der in Cloud Manager verfügbar ist.

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

Wenn Sie Ihre Konfiguration lokal testen, können Sie verschiedene Umgebungstypen simulieren, indem Sie die Variable direkt `DISP_RUN_MODE` an das `docker_run.sh`-Skript übergeben:

```
$ DISP_RUN_MODE=stage docker_run.sh out docker.for.mac.localhost:4503 8080
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

## Hauptunterschiede zwischen AMS Dispatcher und AEM as a Cloud Service {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

Wie auf der obigen Referenzseite beschrieben, ähnelt die Apache- und Dispatcher-Konfiguration in AEM as a Cloud Service der AMS-Konfiguration. Die Hauptunterschiede sind:

* In AEM as a Cloud Service können einige Apache-Direktiven nicht verwendet werden (z. B. `Listen` oder `LogLevel`).
* In AEM as a Cloud Service können nur einige Teile der Dispatcher-Konfiguration in include-Dateien eingefügt werden, und ihre Benennung ist wichtig. Beispielsweise müssen Filterregeln, die Sie über verschiedene Hosts hinweg wiederverwenden möchten, in einer Datei namens `filters/filters.any` abgelegt werden. Weitere Informationen finden Sie auf der Referenzseite.
* In AEM as a Cloud Service gibt es eine zusätzliche Validierung, um Filterregeln zu deaktivieren, die mit `/glob` geschrieben wurden. Dies dient der Vermeidung von Sicherheitsproblemen. Da `deny *` verwendet wird anstelle von `allow *` (was nicht verwendet werden kann), profitieren Kunden von einer lokalen Ausführung von Dispatcher und der Möglichkeit zum Ausprobieren: Sie können sich die Protokolle ansehen, um genau zu erfahren, welche Pfade die Dispatcher-Filter blockieren, damit sich diese hinzufügen lassen.

## Richtlinien für die Migration einer Dispatcher-Konfiguration von AMS zu AEM as a Cloud Service

Die Konfigurationsstruktur von Dispatcher unterscheidet sich bei Managed Services und AEM as a Cloud Service. Nachfolgend finden Sie eine schrittweise Anleitung zur Migration von der AMS Dispatcher-Konfiguration Version 2 zu AEM as a Cloud Service.

## Konvertieren einer AMS- in eine AEM as a Cloud Service-Dispatcher-Konfiguration

Im folgenden Abschnitt finden Sie eine schrittweise Anleitung zum Konvertieren einer AMS-Konfiguration. Es wird davon ausgegangen, dass Sie über ein Archiv mit einer Struktur verfügen, die der in der [Cloud Manager-Dispatcher-Konfiguration](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html) beschriebenen ähnelt.

### Archiv extrahieren und gegebenenfalls ein Präfix entfernen

Extrahieren Sie das Archiv in einen Ordner und stellen Sie sicher, dass die unmittelbaren Unterordner mit `conf`, `conf.d`, `conf.dispatcher.d` und `conf.modules.d` beginnen. Wenn nicht, verschieben Sie sie in der Hierarchie nach oben.

### Nicht verwendete Unterordner und Dateien entfernen

Entfernen Sie die Unterordner `conf` und `conf.modules.d` sowie Dateien, die mit `conf.d/*.conf` übereinstimmen.

### Alle nicht veröffentlichten virtuellen Hosts entfernen

Entfernen Sie alle Virtual-Host-Dateien in `conf.d/enabled_vhosts`, die `author`, `unhealthy`, `health`, `lc` oder `flush` im Namen tragen. Alle Virtual-Host-Dateien in `conf.d/available_vhosts`, die nicht verknüpft sind, können ebenfalls entfernt werden.

### Virtual-Host-Abschnitte, die nicht auf Port 80 verweisen, entfernen oder kommentieren

Wenn Sie in Ihren Virtual-Host-Dateien immer noch über Abschnitte verfügen, die sich ausschließlich auf andere Ports als Port 80 beziehen, z. B.

```
<VirtualHost *:443>
...
</VirtualHost>
```

, entfernen oder kommentieren Sie diese. Anweisungen in diesen Abschnitten werden nicht verarbeitet; wenn Sie sie jedoch beibehalten, bearbeiten Sie sie am Ende doch noch – ohne Auswirkungen. Das kann verwirrend sein.

### Neuschreibungen überprüfen

Rufen Sie Verzeichnis `conf.d/rewrites` auf.

Entfernen Sie alle Dateien mit Namen `base_rewrite.rules` und `xforwarded_forcessl_rewrite.rules` und denken Sie daran, `Include`-Anweisungen in den Virtual-Host-Dateien, die auf sie verweisen, zu entfernen.

Wenn `conf.d/rewrites` jetzt eine einzelne Datei enthält, sollte sie in `rewrite.rules` umbenannt werden. Vergessen Sie nicht, die `Include`-Anweisungen, die auf diese Datei verweisen, auch in den Virtual-Host-Dateien anzupassen.

Wenn der Ordner jedoch mehrere Virtual-Host-spezifische Dateien enthält, sollte deren Inhalt in die `Include`-Anweisung kopiert werden, die in den Virtual-Host-Dateien auf sie verweist.

### Variablen überprüfen

Rufen Sie Verzeichnis `conf.d/variables` auf.

Entfernen Sie alle Dateien mit dem Namen `ams_default.vars` und denken Sie daran, `Include`-Anweisungen in den Virtual-Host-Dateien zu entfernen, die auf sie verweisen.

Wenn `conf.d/variables` jetzt eine einzelne Datei enthält, sollte sie in `custom.vars` umbenannt werden. Vergessen Sie nicht, die `Include`-Anweisungen, die auf diese Datei verweisen, auch in den Virtual-Host-Dateien anzupassen.

Wenn der Ordner jedoch mehrere Virtual-Host-spezifische Dateien enthält, sollte deren Inhalt in die `Include`-Anweisung kopiert werden, die in den Virtual-Host-Dateien auf sie verweist.

### Entfernen von Zulassungslisten

Entfernen Sie den Ordner `conf.d/whitelists` und entfernen Sie `Include`-Anweisungen in den Virtual-Host-Dateien, die auf eine Datei in diesem Unterordner verweisen.

### Nicht mehr verfügbare Variable ersetzen

In allen virtuellen Host-Dateien:

Benennen Sie `PUBLISH_DOCROOT` in `DOCROOT` um.
Entfernen Sie Abschnitte, die auf Variablen mit den Namen `DISP_ID`, `PUBLISH_FORCE_SSL` oder `PUBLISH_WHITELIST_ENABLED` verweisen.

### Status prüfen, indem Sie den Validator ausführen

Führen Sie mit dem Unterbefehl `httpd` den Dispatcher-Validator in Ihrem Verzeichnis aus:

```
$ validator httpd .
```

Wenn Fehler wegen fehlender include-Dateien auftreten, überprüfen Sie, ob diese Dateien korrekt umbenannt wurden.

Wenn Sie Apache-Anweisungen sehen, die nicht in der Zulassungsliste enthalten sind, entfernen Sie sie.

### Alle Nicht-Publish-Farmen entfernen

Entfernen Sie alle Farm-Dateien in `conf.dispatcher.d/enabled_farms`, die im Namen `author`, `unhealthy`, `health`, `lc` oder `flush` tragen. Alle Farm-Dateien in `conf.dispatcher.d/available_farms`, die nicht verknüpft sind, können ebenfalls entfernt werden.

### Farm-Dateien umbenennen

Alle Farmen in `conf.d/enabled_farms` müssen nach dem Muster `*.farm` umbenannt werden, sodass z. B. eine Farm-Datei namens `customerX_farm.any` in `customerX.farm` umbenannt werden sollte.

### Cache überprüfen

Rufen Sie Verzeichnis `conf.dispatcher.d/cache` auf.

Entfernen Sie alle Dateien mit dem Präfix `ams_`.

Wenn `conf.dispatcher.d/cache` jetzt leer ist, kopieren Sie die Datei `conf.dispatcher.d/cache/rules.any` aus der standardmäßigen Dispatcher-Konfiguration in diesen Ordner. Die standardmäßige Dispatcher-Konfiguration befindet sich im Ordner `src` des SDK. Vergessen Sie nicht, auch die `$include`-Anweisungen anzupassen, die auf die `ams_*_cache.any`-Regeldateien in den Farm-Dateien verweisen.

Wenn `conf.dispatcher.d/cache` stattdessen nun eine einzelne Datei mit dem Suffix `_cache.any` enthält, sollte sie in `rules.any` umbenannt werden. Vergessen Sie nicht, auch die `$include`-Anweisungen anzupassen, die in den Farm-Dateien auf diese Datei verweisen.

Wenn der Ordner jedoch mehrere Farm-spezifische Dateien mit diesem Muster enthält, sollten deren Inhalte in die `$include`-Anweisung kopiert werden, die in den Farm-Dateien auf sie verweist.

Entfernen Sie alle Dateien mit dem Suffix `_invalidate_allowed.any`.

Kopieren Sie die Datei `conf.dispatcher.d/cache/default_invalidate_any` aus der standardmäßigen Dispatcher-Konfiguration von AEM in der Cloud an diesen Speicherort.

Entfernen Sie in allen Farm-Dateien den gesamten Inhalt im Abschnitt `cache/allowedClients` und ersetzen Sie ihn durch:

```
$include "../cache/default_invalidate.any"
```

### Client-Kopfzeilen überprüfen

Rufen Sie Verzeichnis `conf.dispatcher.d/clientheaders` auf.

Entfernen Sie alle Dateien mit dem Präfix `ams_`.

Wenn `conf.dispatcher.d/clientheaders` jetzt eine einzelne Datei mit dem Suffix `_clientheaders.any` enthält, sollte sie in `clientheaders.any` umbenannt werden. Vergessen Sie nicht, auch die `$include`-Anweisungen anzupassen, die in den Farm-Dateien auf diese Datei verweisen.

Wenn der Ordner jedoch mehrere Farm-spezifische Dateien mit diesem Muster enthält, sollten deren Inhalte in die `$include`-Anweisung kopiert werden, die in den Farm-Dateien auf sie verweist.

Kopieren Sie die Datei `conf.dispatcher/clientheaders/default_clientheaders.any` aus der standardmäßigen AEM as a Cloud Service-Dispatcher-Konfiguration an diesen Speicherort.

Ersetzen Sie in jeder Datei „clientheader include“-Anweisungen, die wie folgt aussehen:

```
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"
```

durch die Anweisung:

```
$include "../clientheaders/default_clientheaders.any"
```

### Filter prüfen

Rufen Sie Verzeichnis `conf.dispatcher.d/filters` auf.

Entfernen Sie alle Dateien mit dem Präfix `ams_`.

Wenn `conf.dispatcher.d/filters` jetzt eine einzelne Datei enthält, sollte sie in `filters.any` umbenannt werden. Vergessen Sie nicht, auch die `$include`-Anweisungen anzupassen, die in den Farm-Dateien auf diese Datei verweisen.

Wenn der Ordner jedoch mehrere Farm-spezifische Dateien mit diesem Muster enthält, sollten deren Inhalte in die `$include`-Anweisung kopiert werden, die in den Farm-Dateien auf sie verweist.

Kopieren Sie die Datei `conf.dispatcher/filters/default_filters.any` aus der standardmäßigen AEM as a Cloud Service-Dispatcher-Konfiguration an diesen Speicherort.

Ersetzen Sie in jeder Farm-Datei alle „filter include“-Anweisungen, die wie folgt aussehen:

```
$include "/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"
```

durch die Anweisung:

```
$include "../filters/default_filters.any"
```

### Renders überprüfen

Rufen Sie Verzeichnis `conf.dispatcher.d/renders` auf.

Entfernen Sie alle Dateien in diesem Ordner.

Kopieren Sie die Datei `conf.dispatcher.d/renders/default_renders.any` aus der standardmäßigen AEM as a Cloud Service-Dispatcher-Konfiguration an diesen Speicherort.

Entfernen Sie in allen Farm-Dateien den gesamten Inhalt im Abschnitt `renders` und ersetzen Sie ihn durch:

```
$include "../renders/default_renders.any"
```

### Virtualhosts überprüfen

Benennen Sie das Verzeichnis `conf.dispatcher.d/vhosts` um in `conf.dispatcher.d/virtualhosts` und geben Sie es ein.

Entfernen Sie alle Dateien mit dem Präfix `ams_`.

Wenn `conf.dispatcher.d/virtualhosts` jetzt eine einzelne Datei enthält, sollte sie in `virtualhosts.any` umbenannt werden. Vergessen Sie nicht, auch die `$include`-Anweisungen anzupassen, die in den Farm-Dateien auf diese Datei verweisen.

Wenn der Ordner jedoch mehrere Farm-spezifische Dateien mit diesem Muster enthält, sollten deren Inhalte in die `$include`-Anweisung kopiert werden, die in den Farm-Dateien auf sie verweist.

Kopieren Sie die Datei `conf.dispatcher/virtualhosts/default_virtualhosts.any` aus der standardmäßigen AEM as a Cloud Service-Dispatcher-Konfiguration an diesen Speicherort.

Ersetzen Sie in jeder Farm-Datei alle „filter include“-Anweisungen, die wie folgt aussehen:

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

durch die Anweisung:

```
$include "../virtualhosts/default_virtualhosts.any"
```

### Status prüfen, indem Sie den Validator ausführen

Führen Sie mit dem `dispatcher`-Unterbefehl den AEM as a Cloud Service-Dispatcher-Validator in Ihrem Verzeichnis aus:

```
$ validator dispatcher .
```

Wenn Fehler wegen fehlender include-Dateien auftreten, überprüfen Sie, ob diese Dateien korrekt umbenannt wurden.

Wenn Fehler wegen einer nicht definierten Variable `PUBLISH_DOCROOT` auftreten, benennen Sie diese in `DOCROOT` um.

Weitere Informationen zu anderen Fehlern finden Sie im Abschnitt „Fehlerbehebung“ in der Dokumentation des Validator-Tools.

### Konfiguration mit einer lokalen Bereitstellung testen (Docker-Installation erforderlich)

Mithilfe des Skripts `docker_run.sh` in den AEM as a Cloud Service-Dispatcher Tools können Sie testen, ob Ihre Konfiguration keine andere Fehler aufweist, die sich erst bei der Bereitstellung zeigen würden:

### Schritt 1: Bereitstellungsinformationen mit dem Validator generieren.

```
validator full -d out .
```

Dadurch wird die vollständige Konfiguration validiert und werden in `out` Bereitstellungsinformationen generiert.

### Schritt 2: Dispatcher mit diesen Bereitstellungsinformationen in einem Docker-Image starten.

Wenn Ihr AEM-Veröffentlichungs-Server auf Ihrem macOS-Computer ausgeführt und Port 4503 überwacht wird, können Sie Dispatcher wie folgt vor diesem Server starten:

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

Dadurch wird der Container gestartet und Apache am lokalen Port 8080 verfügbar gemacht.

### Neue Dispatcher-Konfiguration verwenden

Herzlichen Glückwunsch! Wenn der Validator kein Problem mehr meldet und der Docker-Container ohne Fehler oder Warnungen gestartet wird, können Sie Ihre Konfiguration in ein `dispatcher/src`-Unterverzeichnis Ihres Git-Repositorys verschieben.

**Kunden, die die AMS-Dispatcher-Konfiguration Version 1 verwenden, sollten sich an den Support wenden, um sich bei der Migration von Version 1 zu Version 2 helfen zu lassen, sodass die oben stehenden Anweisungen befolgt werden.**
