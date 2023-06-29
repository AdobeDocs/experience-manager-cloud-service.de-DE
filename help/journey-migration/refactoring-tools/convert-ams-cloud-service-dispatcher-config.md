---
title: Konvertieren einer AMS-Konfiguration in eine Adobe Experience Manager as a Cloud Service-Dispatcher-Konfiguration
description: Konvertieren einer AMS-Konfiguration in eine Adobe Experience Manager as a Cloud Service-Dispatcher-Konfiguration
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 43%

---


# Konvertieren einer AMS-Konfiguration in eine Adobe Experience Manager (AEM) as a Cloud Service-Dispatcher-Konfiguration

## Einführung {#introduction}

Dieser Abschnitt enthält schrittweise Anweisungen zum Konvertieren einer AMS-Konfiguration.

>[!NOTE]
>Es wird davon ausgegangen, dass Sie über ein Archiv mit einer Struktur verfügen, die der in [Verwalten von Dispatcher-Konfigurationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/getting-started/dispatcher-configurations.html) beschriebenen ähnelt.

## Schritte zum Konvertieren einer AMS-Konfiguration in eine AEM as a Cloud Service-Dispatcher-Konfiguration

1. **Archiv extrahieren und gegebenenfalls ein Präfix entfernen**

   Extrahieren Sie das Archiv in einen Ordner und stellen Sie sicher, dass die unmittelbaren Unterordner mit &quot;conf&quot;, &quot;conf.d&quot;, &quot;conf.dispatcher.d&quot;und &quot;conf.modules.d&quot;beginnen. Ist dies nicht der Fall, verschieben Sie sie in der Hierarchie nach oben.

1. **Nicht verwendete Unterordner und Dateien entfernen**

   Entfernen Sie die Unterordner &quot;conf&quot;und &quot;conf.modules.d&quot;sowie Dateien, die mit &quot;conf.d/*.conf&quot;übereinstimmen.

1. **Alle nicht veröffentlichten virtuellen Hosts entfernen**

1. **Alle virtuellen Host-Dateien entfernen**

   In &quot;conf.d/enabled_vhosts&quot;, deren Name &quot;author&quot;, &quot;unhealthy&quot;, &quot;health&quot;, &quot;lc&quot;oder &quot;flush&quot;enthält. Alle virtuellen Host-Dateien in „conf.d/available_vhosts“, die nicht verknüpft sind, können ebenfalls entfernt werden.

1. Entfernen Sie Virtual-Host-Abschnitte, die nicht auf Port 80 verweisen, oder kommentieren Sie sie aus

   Wenn Sie in Ihren Virtual-Host-Dateien immer noch über Abschnitte verfügen, die sich ausschließlich auf andere Ports als Port 80 beziehen, z. B,

   `<VirtualHost *:443>`
   `...`
   `</VirtualHost>`, entfernen oder kommentieren Sie diese. Anweisungen in diesen Abschnitten werden nicht verarbeitet, aber wenn Sie sie beibehalten, können Sie sie dennoch ohne Auswirkungen bearbeiten, was verwirrend ist.

1. **Überprüfen von Neuschreibungen**

   * Öffnen Sie das Verzeichnis „conf.d/rewrites“.

   * Entfernen Sie alle Dateien mit Namen „ase_rewrite.rules“ und „xforwarded_forcessl_rewrite.rules“. Denken Sie daran, die Include-Anweisungen in den darauf verweisenden virtuellen Host-Dateien zu entfernen.

   * Wenn &quot;conf.d/rewrites&quot;jetzt eine einzelne Datei enthält, sollte sie in &quot;rewrite.rules&quot;umbenannt werden. Vergessen Sie nicht, auch die auf diese Datei verweisenden Include-Anweisungen in den virtuellen Host-Dateien anzupassen.

   * Wenn der Ordner jedoch mehrere Virtual-Host-spezifische Dateien enthält, sollte deren Inhalt in die Include-Anweisung kopiert werden, die in den Virtual-Host-Dateien auf sie verweist.

1. **Überprüfen von Variablen**

   1. Öffnen Sie das Verzeichnis „conf.d/variables“.

   1. Entfernen Sie alle Dateien mit Namen „ams_default.vars“. Denken Sie daran, die Include-Anweisungen in den darauf verweisenden virtuellen Host-Dateien zu entfernen.

   1. Wenn &quot;conf.d/variables&quot;jetzt eine einzelne Datei enthält, sollte sie in &quot;custom.vars&quot;umbenannt werden. Vergessen Sie nicht, auch die auf diese Datei verweisenden Include-Anweisungen in den Virtual-Host-Dateien anzupassen.

   1. Wenn der Ordner jedoch mehrere Virtual-Host-spezifische Dateien enthält, sollte deren Inhalt in die Include-Anweisung kopiert werden, die in den Virtual-Host-Dateien auf sie verweist.

1. **Entfernen von Whitelists**

   Entfernen Sie den Ordner „conf.d/whitelists“. Denken Sie daran, die Include-Anweisungen in den darauf verweisenden virtuellen Host-Dateien zu entfernen.

1. **Ersetzen nicht mehr verfügbarer Variablen**

   In allen virtuellen Host-Dateien:

   Benennen Sie PUBLISH_DOCROOT in DOCROOT um
Entfernen Sie die Abschnitte, die auf Variablen mit den Namen DISP_ID, PUBLISH_FORCE_SSL oder PUBLISH_WHITELIST_ENABLED verweisen

1. **Prüfen des Status durch Ausführen des Validators**

   Führen Sie den Dispatcher-Validator mit dem Unterbefehl httpd in Ihrem Verzeichnis aus:

   `$ validator httpd`
Wenn Fehler wegen fehlender &quot;include&quot;-Dateien auftreten, überprüfen Sie, ob diese Dateien korrekt umbenannt wurden.

   Wenn Sie Apache-Direktiven sehen, die nicht in der Whitelist enthalten sind, entfernen Sie sie.

1. **Entfernen aller Nicht-Veröffentlichungs-Farmen**

   Entfernen Sie alle Farm-Dateien in &quot;conf.dispatcher.d/enabled_farms&quot;, deren Name &quot;author&quot;, &quot;unhealthy&quot;, &quot;health&quot;, &quot;lc&quot;oder &quot;flush&quot;enthält. Alle Farm-Dateien in „conf.dispatcher.d/available_farms“, die nicht verknüpft sind, können ebenfalls entfernt werden.

1. **Umbenennen von Farm-Dateien**

   Alle Farmen in &quot;conf.dispatcher.d/enabled_farms&quot;müssen so umbenannt werden, dass sie dem Muster *.farm entsprechen. Benennen Sie beispielsweise `customerX_farm.any` nach `customerX.farm`.

1. **Überprüfen des Cache**

   Öffnen Sie das Verzeichnis „conf.dispatcher.d/cache“.

   Entfernen Sie alle Dateien mit dem Präfix `ams_`.

   Wenn &quot;conf.dispatcher.d/cache&quot;jetzt leer ist, kopieren Sie die Datei `conf.dispatcher.d/cache/rules.any` aus der standardmäßigen Dispatcher-Konfiguration in diesen Ordner. Die standardmäßige Dispatcher-Konfiguration befindet sich im Ordner src dieses SDK. Vergessen Sie nicht, die &quot;$include&quot;-Anweisungen anzupassen, die auf die `ams_*_cache.any` Regeldateien in den Farm-Dateien.

   Wenn stattdessen &quot;conf.dispatcher.d/cache&quot;jetzt eine einzelne Datei mit dem Suffix enthält `_cache.any`, sollte es in `rules.any`. Denken Sie daran, auch die &quot;$include&quot;-Anweisungen anzupassen, die in den Farm-Dateien auf diese Datei verweisen.

   Wenn der Ordner jedoch mehrere Farm-spezifische Dateien mit diesem Muster enthält, sollte deren Inhalt in die &quot;$include&quot;-Anweisung kopiert werden, die in den Farm-Dateien auf sie verweist.

   Entfernen Sie alle Dateien mit dem Suffix `_invalidate_allowed.any`.

   Kopieren Sie die Datei &quot;conf.dispatcher.d/cache/default_invalidate_any&quot;aus der standardmäßigen Dispatcher-Konfiguration an diesen Speicherort.

   Entfernen Sie in allen Farm-Dateien den gesamten Inhalt im Abschnitt „cache/allowedClients“ und ersetzen Sie ihn durch:

   $include &quot;../cache/default_invalidate.any&quot;

1. **Überprüfen von Client-Kopfzeilen**

   Öffnen Sie das Verzeichnis „conf.dispatcher.d/clientheaders“.

   Entfernen Sie alle Dateien mit dem Präfix `ams_`.

   Wenn &quot;conf.dispatcher.d/clientheaders&quot;eine einzelne Datei mit dem Suffix enthält `_clientheaders.any`umbenennen in `clientheaders.any`. Denken Sie daran, auch die &quot;$include&quot;-Anweisungen anzupassen, die in den Farm-Dateien auf diese Datei verweisen.

   Wenn der Ordner jedoch mehrere Farm-spezifische Dateien mit diesem Muster enthält, sollte deren Inhalt in die &quot;$include&quot;-Anweisung kopiert werden, die in den Farm-Dateien auf sie verweist.

   Datei kopieren `conf.dispatcher/clientheaders/default_clientheaders.any` aus der standardmäßigen Dispatcher-Konfiguration an diesen Speicherort.

   Ersetzen Sie in jeder Farm-Datei alle `clientheader` &quot;include&quot;-Anweisungen, die wie folgt aussehen:

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"`

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"`

   durch die Anweisung:

   `$include "../clientheaders/default_clientheaders.any"`

1. **Prüfen des Filters**

   * Öffnen Sie das Verzeichnis „conf.dispatcher.d/filters“.

   * Entfernen Sie alle Dateien mit dem Präfix `ams_`.

   * Wenn &quot;conf.dispatcher.d/filters&quot;jetzt eine einzelne Datei enthält, benennen Sie sie in um. `filters.any`. Denken Sie daran, auch die &quot;$include&quot;-Anweisungen anzupassen, die in den Farm-Dateien auf diese Datei verweisen.

   * Wenn der Ordner jedoch mehrere Farm-spezifische Dateien mit diesem Muster enthält, sollte deren Inhalt in die &quot;$include&quot;-Anweisung kopiert werden, die in den Farm-Dateien auf sie verweist.

   * Datei kopieren `conf.dispatcher/filters/default_filters.any` aus der standardmäßigen Dispatcher-Konfiguration an diesen Speicherort.

   * Ersetzen Sie in jeder Farm-Datei alle Filteranweisungen &quot;include&quot;, die wie folgt aussehen:

   * $include `"/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"`
mit der Anweisung:

     `$include "../filters/default_filters.any"`

1. **Überprüfen von Renders**

   * Öffnen Sie das Verzeichnis „conf.dispatcher.d/renders“.

   * Entfernen Sie alle Dateien in diesem Ordner.

   * Datei kopieren `conf.dispatcher.d/renders/default_renders.any` aus der standardmäßigen Dispatcher-Konfiguration an diesen Speicherort.

   * Entfernen Sie in allen Farm-Dateien den gesamten Inhalt im Abschnitt „renders“ und ersetzen Sie ihn durch:

     `$include "../renders/default_renders.any"`

1. **Überprüfen von Virtualhosts**

   * Benennen Sie das Verzeichnis `conf.dispatcher.d/vhosts to conf.dispatcher.d/virtualhosts` um und öffnen Sie es.

   * Entfernen Sie alle Dateien mit dem Präfix `ams_`.

   * Wenn &quot;conf.dispatcher.d/virtualhosts&quot;jetzt eine einzelne Datei enthält, benennen Sie sie um in `virtualhosts.any`. Denken Sie daran, auch die &quot;$include&quot;-Anweisungen anzupassen, die in den Farm-Dateien auf diese Datei verweisen.

   * Wenn der Ordner jedoch mehrere Farm-spezifische Dateien mit diesem Muster enthält, sollte deren Inhalt in die &quot;$include&quot;-Anweisung kopiert werden, die in den Farm-Dateien auf sie verweist.

   * Datei kopieren `conf.dispatcher/virtualhosts/default_virtualhosts.any` aus der standardmäßigen Dispatcher-Konfiguration an diesen Speicherort.

   * Ersetzen Sie in jeder Farm-Datei alle Filteranweisungen &quot;include&quot;, die wie folgt aussehen:

     `$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"`
durch die Anweisung:

     `$include "../virtualhosts/default_virtualhosts.any"`


1. **Prüfen des Status durch Ausführen des Validators**

   * Führen Sie den Dispatcher-Validator mit dem Dispatcher-Unterbefehl in Ihrem Verzeichnis aus:

     `$ validator dispatcher`

   * Wenn Fehler wegen fehlender &quot;include&quot;-Dateien auftreten, überprüfen Sie, ob diese Dateien korrekt umbenannt wurden.

   * Wenn Fehler wegen einer nicht definierten Variable `PUBLISH_DOCROOT` auftreten, benennen Sie diese in `DOCROOT` um.

   * Weitere Informationen zu anderen Fehlern finden Sie im Abschnitt „Fehlerbehebung“ in der Dokumentation des Validator-Tools.

## Testen der Konfiguration mit einer lokalen Bereitstellung {#testing-config-local-deployment}

>[!IMPORTANT]
>
>Zum Testen Ihrer Konfiguration mit einer lokalen Bereitstellung ist eine Docker-Installation erforderlich.

Mithilfe des Skripts `docker_run.sh` im Dispatcher-SDK können Sie testen, ob Ihre Konfiguration keine anderen Fehler aufweist, die sich erst bei der Bereitstellung zeigen würden:

1. Bereitstellungsinformationen mit dem Validator generieren.

   `validator full -d out`
Validiert die vollständige Konfiguration und generiert Bereitstellungsinformationen in &quot;out&quot;.

1. Starten Sie den Dispatcher in einem Docker-Bild mit diesen Bereitstellungsinformationen.

   Wenn Ihr AEM-Publishing-Server auf Ihrem macOS-Computer ausgeführt und Port 4503 überwacht wird, können Sie Dispatcher wie folgt vor diesem Server starten:

   `$ docker_run.sh out docker.for.mac.localhost:4503 8080`

   Startet den Container und stellt Apache auf dem lokalen Port 8080 bereit.

## Verwenden der neuen Dispatcher-Konfiguration {#using-dispatcher-config}

Wenn der Validator kein Problem mehr meldet und der Docker-Container ohne Fehler oder Warnungen startet, können Sie Ihre Konfiguration in ein d`ispatcher/src`-Unterverzeichnis Ihres Git-Repositorys verschieben.