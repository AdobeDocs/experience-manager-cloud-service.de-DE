---
title: Migration der Dispatcher-Konfiguration von AMS zu AEM as a Cloud Service
description: 'Migration der Dispatcher-Konfiguration von AMS zu AEM as a Cloud Service '
feature: Dispatcher
source-git-commit: 19444aacbb86f93e7a5ea8bda2ca3c03a0a44f98
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 95%

---

# Migration der Dispatcher-Konfiguration von AMS zu AEM as a Cloud Service {#Dispatcher-in-the-cloud}

## Hauptunterschiede zwischen AMS Dispatcher und AEM as a Cloud Service {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

Die Apache- und Dispatcher-Konfiguration in AEM as a Cloud Service ähnelt der AMS-Konfiguration. Die Hauptunterschiede sind:

* In AEM as a Cloud Service können einige Apache-Direktiven nicht verwendet werden (z. B. `Listen` oder `LogLevel`).
* In AEM as a Cloud Service können nur einige Teile der Dispatcher-Konfiguration in include-Dateien eingefügt werden, und ihre Benennung ist wichtig. Beispielsweise müssen Filterregeln, die Sie über verschiedene Hosts hinweg wiederverwenden möchten, in einer Datei namens `filters/filters.any` abgelegt werden. Weitere Informationen finden Sie auf der Referenzseite.
* In AEM as a Cloud Service gibt es eine zusätzliche Validierung, um Filterregeln zu deaktivieren, die mit `/glob` geschrieben wurden. Dies dient der Vermeidung von Sicherheitsproblemen. Da `deny *` verwendet wird anstelle von `allow *` (was nicht verwendet werden kann), profitieren Kunden von einer lokalen Ausführung von Dispatcher und der Möglichkeit zum Ausprobieren: Sie können sich die Protokolle ansehen, um genau zu erfahren, welche Pfade die Dispatcher-Filter blockieren, damit sich diese hinzufügen lassen.

## Richtlinien für die Migration einer Dispatcher-Konfiguration von AMS zu AEM as a Cloud Service

Die Konfigurationsstruktur von Dispatcher unterscheidet sich bei Managed Services und AEM as a Cloud Service. Nachfolgend finden Sie eine schrittweise Anleitung zur Migration von der AMS Dispatcher-Konfiguration Version 2 zu AEM as Cloud Service.

## Konvertieren einer AMS- in eine AEM as a Cloud Service-Dispatcher-Konfiguration

Im folgenden Abschnitt finden Sie eine schrittweise Anleitung zum Konvertieren einer AMS-Konfiguration. Es wird davon ausgegangen, dass Sie über ein Archiv mit einer Struktur verfügen, die der in der [Cloud Manager-Dispatcher-Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html) beschriebenen ähnelt.

### Archiv extrahieren und gegebenenfalls ein Präfix entfernen

Extrahieren Sie das Archiv in einen Ordner und stellen Sie sicher, dass die unmittelbaren Unterordner mit `conf`, `conf.d`, `conf.dispatcher.d` und `conf.modules.d` beginnen. Wenn nicht, verschieben Sie sie in der Hierarchie nach oben.

### Nicht verwendete Unterordner und Dateien entfernen

Entfernen Sie die Unterordner `conf` und `conf.modules.d` sowie Dateien, die mit `conf.d/*.conf` übereinstimmen.

### Alle nicht veröffentlichten virtuellen Hosts entfernen

Entfernen Sie alle Virtual-Host-Dateien in `conf.d/enabled_vhosts`, die `author`, `unhealthy`, `health`, `lc` oder `flush` im Namen tragen. Alle Virtual-Host-Dateien in `conf.d/available_vhosts`, die nicht verknüpft sind, können ebenfalls entfernt werden.

### Virtual-Host-Abschnitte, die nicht auf Port 80 verweisen, entfernen oder kommentieren

Wenn Sie in Ihren Virtual-Host-Dateien immer noch über Abschnitte verfügen, die sich ausschließlich auf andere Ports als Port 80 beziehen, z. B:

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

Wenn `conf.dispatcher.d/cache` jetzt leer ist, kopieren Sie die Datei `conf.dispatcher.d/cache/rules.any` aus der standardmäßigen Dispatcher-Konfiguration in diesen Ordner. Die standardmäßige Dispatcher-Konfiguration befindet sich im Ordner `src` dieses SDK. Vergessen Sie nicht, auch die `$include`-Anweisungen anzupassen, die auf die `ams_*_cache.any`-Regeldateien in den Farm-Dateien verweisen.

Wenn `conf.dispatcher.d/cache` stattdessen nun eine einzelne Datei mit dem Suffix `_cache.any` enthält, sollte sie in `rules.any` umbenannt werden. Vergessen Sie nicht, auch die `$include`-Anweisungen anzupassen, die in den Farm-Dateien auf diese Datei verweisen.

Wenn der Ordner jedoch mehrere Farm-spezifische Dateien mit diesem Muster enthält, sollten deren Inhalte in die `$include`-Anweisung kopiert werden, die in den Farm-Dateien auf sie verweist.

Entfernen Sie alle Dateien mit dem Suffix `_invalidate_allowed.any`.

Kopieren Sie die Datei `conf.dispatcher.d/cache/default_invalidate_any` aus der standardmäßigen Dispatcher-Konfiguration von AEM as a Cloud Service an diesen Speicherort.

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

### Schritt 2: Dispatcher mit diesen Implementierungsinformationen in einem Docker-Image starten.

Wenn Ihr AEM-Publishing-Server auf Ihrem macOS-Computer ausgeführt und Port 4503 überwacht wird, können Sie Dispatcher wie folgt vor diesem Server starten:

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

Dadurch wird der Container gestartet und Apache am lokalen Port 8080 verfügbar gemacht.

### Neue Dispatcher-Konfiguration verwenden

Herzlichen Glückwunsch! Wenn der Validator kein Problem mehr meldet und der Docker-Container ohne Fehler oder Warnungen gestartet wird, können Sie Ihre Konfiguration in ein `dispatcher/src`-Unterverzeichnis Ihres Git-Repositorys verschieben.

**Kunden, die die AMS-Dispatcher-Konfiguration Version 1 verwenden, sollten sich an den Support wenden, um sich bei der Migration von Version 1 zu Version 2 helfen zu lassen, sodass die oben stehenden Anweisungen befolgt werden.**
