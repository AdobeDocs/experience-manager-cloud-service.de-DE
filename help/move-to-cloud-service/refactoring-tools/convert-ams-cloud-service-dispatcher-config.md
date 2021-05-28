---
title: Konvertieren einer AMS-Konfiguration in eine Adobe Experience Manager as a Cloud Service-Dispatcher-Konfiguration
description: Konvertieren einer AMS-Konfiguration in eine Adobe Experience Manager as a Cloud Service-Dispatcher-Konfiguration
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '1340'
ht-degree: 99%

---


# Konvertieren einer AMS-Konfiguration in eine Adobe Experience Manager (AEM) as a Cloud Service-Dispatcher-Konfiguration

## Einführung {#introduction}

In diesem Abschnitt finden Sie eine schrittweise Anleitung zum Konvertieren einer AMS-Konfiguration.

>[!NOTE]
>Es wird davon ausgegangen, dass Sie über ein Archiv mit einer Struktur verfügen, die der in [Verwalten von Dispatcher-Konfigurationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html) beschriebenen ähnelt.

## Schritte zum Konvertieren einer AMS-Konfiguration in eine AEM as a Cloud Service-Dispatcher-Konfiguration

1. **Archiv extrahieren und gegebenenfalls ein Präfix entfernen**

   Extrahieren Sie das Archiv in einen Ordner und stellen Sie sicher, dass die unmittelbaren Unterordner mit „conf“, „conf.d“, „conf.dispatcher.d“ und „conf.modules.d“ beginnen. Wenn dies nicht der Fall ist, verschieben Sie sie in der Hierarchie nach oben.

1. **Nicht verwendete Unterordner und Dateien entfernen**

   Entfernen Sie die Unterordner „conf“ und „conf.modules.d“ sowie die Dateien, die mit „conf.d/*.conf“ übereinstimmen.

1. **Alle nicht veröffentlichten virtuellen Hosts entfernen**

1. **Alle virtuellen Host-Dateien entfernen**

   In „conf.d/enabled_vhosts“, deren Name „author“, „unhealthy“, „health“, „lc“ oder „flush“ enthält. Alle virtuellen Host-Dateien in „conf.d/available_vhosts“, die nicht verknüpft sind, können ebenfalls entfernt werden.

1. Virtual-Host-Abschnitte, die nicht auf Port 80 verweisen, entfernen oder kommentieren

   Wenn Sie in Ihren Virtual-Host-Dateien immer noch über Abschnitte verfügen, die sich ausschließlich auf andere Ports als Port 80 beziehen, z. B.

   `<VirtualHost *:443>`
   `...`
   `</VirtualHost>`, entfernen oder kommentieren Sie diese. Anweisungen in diesen Abschnitten werden nicht verarbeitet; wenn Sie sie jedoch beibehalten, bearbeiten Sie sie am Ende doch noch – ohne Auswirkungen. Das kann verwirrend sein.

1. **Überprüfen von Neuschreibungen**

   * Öffnen Sie das Verzeichnis „conf.d/rewrites“.

   * Entfernen Sie alle Dateien mit Namen „ase_rewrite.rules“ und „xforwarded_forcessl_rewrite.rules“. Denken Sie daran, die Include-Anweisungen in den darauf verweisenden virtuellen Host-Dateien zu entfernen.

   * Wenn „conf.d/rewrites“ jetzt eine einzelne Datei enthält, sollte sie in „rewrite.rules“ umbenannt werden. Denken Sie daran, die auf diese Datei verweisenden Include-Anweisungen auch in den virtuellen Host-Dateien anzupassen.

   * Wenn der Ordner jedoch mehrere virtuelle Host-spezifische Dateien enthält, sollte deren Inhalt in die Include-Anweisung kopiert werden, die in den virtuellen Host-Dateien auf sie verweist.

1. **Überprüfen von Variablen**

   1. Öffnen Sie das Verzeichnis „conf.d/variables“.

   1. Entfernen Sie alle Dateien mit Namen „ams_default.vars“. Denken Sie daran, die Include-Anweisungen in den darauf verweisenden virtuellen Host-Dateien zu entfernen.

   1. Wenn „conf.d/variables“ jetzt eine einzelne Datei enthält, sollte sie in „custom.vars“ umbenannt werden. Denken Sie daran, die auf diese Datei verweisenden Include-Anweisungen auch in den virtuellen Host-Dateien anzupassen.

   1. Wenn der Ordner jedoch mehrere virtuelle Host-spezifische Dateien enthält, sollte deren Inhalt in die Include-Anweisung kopiert werden, die in den virtuellen Host-Dateien auf sie verweist.

1. **Entfernen von Whitelists**

   Entfernen Sie den Ordner „conf.d/whitelists“. Denken Sie daran, die Include-Anweisungen in den darauf verweisenden virtuellen Host-Dateien zu entfernen.

1. **Ersetzen nicht mehr verfügbarer Variablen**

   In allen virtuellen Host-Dateien:

   Benennen Sie PUBLISH_DOCROOT in DOCROOT um
Entfernen Sie die Abschnitte, die auf Variablen mit den Namen DISP_ID, PUBLISH_FORCE_SSL oder PUBLISH_WHITELIST_ENABLED verweisen

1. **Prüfen des Status durch Ausführen des Validators**

   Führen Sie mit dem Unterbefehl „httpd“ den Dispatcher-Validator in Ihrem Verzeichnis aus:

   `$ validator httpd`
Wenn Fehler wegen fehlender Include-Dateien auftreten, überprüfen Sie, ob diese Dateien korrekt umbenannt wurden.

   Wenn Sie Apache-Direktiven sehen, die nicht in der Whitelist enthalten sind, entfernen Sie sie.

1. **Entfernen aller Nicht-Veröffentlichungs-Farmen**

   Entfernen Sie alle Farm-Dateien in „conf.dispatcher.d/enabled_farm“, deren Name „author“, „unhealthy“, „health“, „lc“ oder „flush“ enthält. Alle Farm-Dateien in „conf.dispatcher.d/available_farms“, die nicht verknüpft sind, können ebenfalls entfernt werden.

1. **Umbenennen von Farm-Dateien**

   Alle Farmen in „conf.dispatcher.d/enabled_farms“ müssen so umbenannt werden, dass sie dem Muster „*.farm“ entsprechen, sodass z. B. eine Farm-Datei mit dem Namen „customerX_farm.any“ in „customerX.farm“ umbenannt werden sollte.

1. **Überprüfen des Cache**

   Öffnen Sie das Verzeichnis „conf.dispatcher.d/cache“.

   Entfernen Sie alle Dateien mit dem Präfix „ams_“.

   Wenn „conf.dispatcher.d/cache“ jetzt leer ist, kopieren Sie die Datei „conf.dispatcher.d/cache/rules.any“ aus der standardmäßigen Dispatcher-Konfiguration in diesen Ordner. Die standardmäßige Dispatcher-Konfiguration befindet sich im Ordner „src“ des SDK. Vergessen Sie nicht, auch die „$include“-Anweisungen anzupassen, die in den Farm-Dateien auf die Regeldateien „ams_*_cache.any rule“ verweisen.

   Wenn „conf.dispatcher.d/cache“ stattdessen nun eine einzelne Datei mit dem Suffix „_cache.any“ enthält, sollte sie in „rules.any“ umbenannt werden. Vergessen Sie nicht, auch die „$include“-Anweisungen anzupassen, die in den Farm-Dateien auf diese Datei verweisen.

   Wenn der Ordner jedoch mehrere Farm-spezifische Dateien mit diesem Muster enthält, sollten deren Inhalte in die „$include“-Anweisung kopiert werden, die in den Farm-Dateien auf sie verweist.

   Entfernen Sie alle Dateien mit dem Suffix „_invalidate_allowed.any“.

   Kopieren Sie die Datei „conf.dispatcher.d/cache/default_invalidate_any“ aus der standardmäßigen Dispatcher-Konfiguration an diesen Speicherort.

   Entfernen Sie in allen Farm-Dateien den gesamten Inhalt im Abschnitt „cache/allowedClients“ und ersetzen Sie ihn durch:

   $include &quot;../cache/default_invalidate.any&quot;

1. **Überprüfen von Client-Kopfzeilen**

   Öffnen Sie das Verzeichnis „conf.dispatcher.d/clientheaders“.

   Entfernen Sie alle Dateien mit dem Präfix „ams_“.

   Wenn „conf.dispatcher.d/cache“ stattdessen nun eine einzelne Datei mit dem Suffix „_cache.any“ enthält, sollte sie in „rules.any“ umbenannt werden. Vergessen Sie nicht, auch die „$include“-Anweisungen anzupassen, die in den Farm-Dateien auf diese Datei verweisen.

   Wenn der Ordner jedoch mehrere Farm-spezifische Dateien mit diesem Muster enthält, sollten deren Inhalte in die „$include“-Anweisung kopiert werden, die in den Farm-Dateien auf sie verweist.

   Kopieren Sie die Datei „conf.dispatcher/clientheaders/default_clientheaders.any“ aus der standardmäßigen Dispatcher-Konfiguration an diesen Speicherort.

   Ersetzen Sie in jeder Datei „clientheader include“-Anweisungen, die wie folgt aussehen:

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"`

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"`

   durch die Anweisung:

   `$include "../clientheaders/default_clientheaders.any"`

1. **Prüfen des Filters**

   * Öffnen Sie das Verzeichnis „conf.dispatcher.d/filters“.

   * Entfernen Sie alle Dateien mit dem Präfix „ams_“.

   * Wenn „conf.dispatcher.d/filters“ jetzt eine einzelne Datei enthält, sollte sie in „filters.any“ umbenannt werden. Vergessen Sie nicht, auch die „$include“-Anweisungen anzupassen, die in den Farm-Dateien auf diese Datei verweisen.

   * Wenn der Ordner jedoch mehrere Farm-spezifische Dateien mit diesem Muster enthält, sollten deren Inhalte in die „$include“-Anweisung kopiert werden, die in den Farm-Dateien auf sie verweist.

   * Kopieren Sie die Datei „conf.dispatcher/filters/default_filters.any“ aus der standardmäßigen Dispatcher-Konfiguration an diesen Speicherort.

   * Ersetzen Sie in jeder Farm-Datei alle „filter include“-Anweisungen, die wie folgt aussehen:

   * $include `"/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"`
mit der Anweisung:

      `$include "../filters/default_filters.any"`

1. **Überprüfen von Renders**

   * Öffnen Sie das Verzeichnis „conf.dispatcher.d/renders“.

   * Entfernen Sie alle Dateien in diesem Ordner.

   * Kopieren Sie die Datei „conf.dispatcher.d/renders/default_renders.any“ aus der standardmäßigen Dispatcher-Konfiguration an diesen Speicherort.

   * Entfernen Sie in allen Farm-Dateien den gesamten Inhalt im Abschnitt „renders“ und ersetzen Sie ihn durch:

      `$include "../renders/default_renders.any"`

1. **Überprüfen von Virtualhosts**

   * Benennen Sie das Verzeichnis `conf.dispatcher.d/vhosts to conf.dispatcher.d/virtualhosts` um und öffnen Sie es.

   * Entfernen Sie alle Dateien mit dem Präfix `ams_`.

   * Wenn „conf.dispatcher.d/virtualhosts“ jetzt eine einzelne Datei enthält, sollte sie in „virtualhosts.any“ umbenannt werden. Vergessen Sie nicht, auch die „$include“-Anweisungen anzupassen, die in den Farm-Dateien auf diese Datei verweisen.

   * Wenn der Ordner jedoch mehrere Farm-spezifische Dateien mit diesem Muster enthält, sollten deren Inhalte in die „$include“-Anweisung kopiert werden, die in den Farm-Dateien auf sie verweist.

   * Kopieren Sie die Datei „conf.dispatcher/virtualhosts/default_virtualhosts.any“ aus der standardmäßigen Dispatcher-Konfiguration an diesen Speicherort.

   * Ersetzen Sie in jeder Farm-Datei alle „filter include“-Anweisungen, die wie folgt aussehen:

      `$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"`
durch die Anweisung:

      `$include "../virtualhosts/default_virtualhosts.any"`


1. **Prüfen des Status durch Ausführen des Validators**

   * Führen Sie mit dem Unterbefehl „dispatcher“ den Dispatcher-Validator in Ihrem Verzeichnis aus:

      `$ validator dispatcher`

   * Wenn Fehler wegen fehlender include-Dateien auftreten, überprüfen Sie, ob diese Dateien korrekt umbenannt wurden.

   * Wenn Fehler wegen einer nicht definierten Variable `PUBLISH_DOCROOT` auftreten, benennen Sie diese in `DOCROOT` um.

   * Weitere Informationen zu anderen Fehlern finden Sie im Abschnitt „Fehlerbehebung“ in der Dokumentation des Validator-Tools.

## Testen der Konfiguration mit einer lokalen Bereitstellung {#testing-config-local-deployment}

>[!IMPORTANT]
>
>Zum Testen Ihrer Konfiguration mit einer lokalen Bereitstellung ist eine Docker-Installation erforderlich.

Mithilfe des Skripts `docker_run.sh` im Dispatcher-SDK können Sie testen, ob Ihre Konfiguration keine anderen Fehler aufweist, die sich erst bei der Bereitstellung zeigen würden:

1. Bereitstellungsinformationen mit dem Validator generieren

   `validator full -d out`
Dadurch wird die vollständige Konfiguration validiert und Informationen zur Bereitstellung in „out“ werden generiert

1. Dispatcher mit diesen Bereitstellungsinformationen in einem Docker-Image starten

   Wenn Ihr AEM-Veröffentlichungs-Server auf Ihrem macOS-Computer ausgeführt und Port 4503 überwacht wird, können Sie Dispatcher wie folgt vor diesem Server starten:

   `$ docker_run.sh out docker.for.mac.localhost:4503 8080`

   Dadurch wird der Container gestartet und Apache am lokalen Port 8080 verfügbar gemacht.

## Verwenden der neuen Dispatcher-Konfiguration {#using-dispatcher-config}

Wenn der Validator kein Problem mehr meldet und der Docker-Container ohne Fehler oder Warnungen startet, können Sie Ihre Konfiguration in ein d`ispatcher/src`-Unterverzeichnis Ihres Git-Repositorys verschieben.