---
title: Konvertieren eines AMS in einen Adobe Experience Manager als Cloud Service Dispatcher-Konfiguration
description: Konvertieren eines AMS in einen Adobe Experience Manager als Cloud Service Dispatcher-Konfiguration
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '1342'
ht-degree: 22%

---


# Konvertieren eines AMS in einen Adobe Experience Manager (AEM) als Cloud Service Dispatcher-Konfiguration

## Einführung {#introduction}

Dieser Abschnitt enthält schrittweise Anweisungen zum Konvertieren einer AMS-Konfiguration.

>[!NOTE]
>It assumes that you have an archive with a structure similar to the one described in [Manage your Dispatcher Configurations](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html).

## Schritte zum Konvertieren eines AMS in AEM als Cloud Service Dispatcher-Konfiguration

1. **Archiv extrahieren und gegebenenfalls ein Präfix entfernen**

   Extrahieren Sie das Archiv in einen Ordner und stellen Sie sicher, dass der Beginn der unmittelbaren Unterordner mit conf, conf.d, conf.dispatcher.d und conf.modules.d übereinstimmt. Wenn nicht, verschieben Sie sie in der Hierarchie nach oben.

1. **Nicht verwendete Unterordner und Dateien entfernen**

   Entfernen Sie die Unterordner conf und conf.modules.d sowie die Dateien, die mit conf.d/*.conf übereinstimmen.

1. **Alle nicht veröffentlichten virtuellen Hosts entfernen**

1. **Entfernen Sie alle virtuellen Hostdateien**

   In conf.d/enabled_vhosts, die Autor, ungesund, Gesundheit, lc oder flush in ihrem Namen haben. Alle nicht verknüpften virtuellen Hostdateien in conf.d/available_vhosts können ebenfalls entfernt werden.

1. Virtual-Host-Abschnitte, die nicht auf Port 80 verweisen, entfernen oder kommentieren

   Wenn Sie in Ihren Virtual-Host-Dateien immer noch über Abschnitte verfügen, die sich ausschließlich auf andere Ports als Port 80 beziehen, z. B.

   `<VirtualHost *:443>`
   `...`
   `</VirtualHost>`, entfernen oder kommentieren Sie diese. Anweisungen in diesen Abschnitten werden nicht verarbeitet; wenn Sie sie jedoch beibehalten, bearbeiten Sie sie am Ende doch noch – ohne Auswirkungen. Das kann verwirrend sein.

1. **Neuschreibungen überprüfen**

   * Geben Sie den Ordner conf.d/rewrite ein.

   * Entfernen Sie alle Dateien mit den Namen &quot;base_rewrite.rules&quot;und &quot;xforwarded_forcessl_rewrite.rules&quot;. Denken Sie daran, dass Sie die Include-Anweisungen in den virtuellen Hostdateien entfernen, die auf sie verweisen.

   * Wenn conf.d/rewrite jetzt eine einzelne Datei enthält, sollte es in rewrite.rules umbenannt werden. Vergessen Sie nicht, die Include-Anweisungen, die sich auf diese Datei beziehen, auch in den virtuellen Hostdateien anzupassen.

   * Wenn der Ordner jedoch mehrere, für den virtuellen Host spezifische Dateien enthält, sollten deren Inhalte in die Include-Anweisung kopiert werden, die sich auf sie in den Dateien des virtuellen Hosts bezieht.

1. **Variablen überprüfen**

   1. Geben Sie den Ordner conf.d/variables ein.

   1. Entfernen Sie alle Dateien mit dem Namen ams_default.vars und denken Sie daran, dass Anweisungen zum Einschließen in den virtuellen Hostdateien, die auf sie verweisen, entfernt werden.

   1. Wenn conf.d/variables jetzt eine einzelne Datei enthält, sollte sie in custom.vars umbenannt werden. Vergessen Sie nicht, die Include-Anweisungen, die sich auf diese Datei beziehen, auch in den virtuellen Hostdateien anzupassen.

   1. Wenn der Ordner jedoch mehrere, für den virtuellen Host spezifische Dateien enthält, sollten deren Inhalte in die Include-Anweisung kopiert werden, die sich auf sie in den Dateien des virtuellen Hosts bezieht.

1. **Whitelists entfernen**

   Entfernen Sie den Ordner conf.d/whitelists und entfernen Sie Include-Anweisungen in den virtuellen Hostdateien, die auf eine Datei in diesem Unterordner verweisen.

1. **Nicht mehr verfügbare Variable ersetzen**

   In allen Virtual-Host-Dateien:

   Umbenennen von PUBLISH_DOCROOT in DOCROOTRemove-Abschnitte, die auf Variablen namens DISP_ID, PUBLISH_FORCE_SSL oder PUBLISH_WHITELIST_ENABLED verweisen

1. **Status prüfen, indem Sie den Validator ausführen**

   Führen Sie den Dispatcher-Validator mit dem Unterbefehl httpd in Ihrem Ordner aus:

   `$ validator httpd`
Wenn Fehler wegen fehlender include-Dateien auftreten, überprüfen Sie, ob diese Dateien korrekt umbenannt wurden.

   Wenn Sie Apache-Direktiven sehen, die nicht in der Whitelist enthalten sind, entfernen Sie sie.

1. **Alle Nicht-Publish-Farmen entfernen**

   Entfernen Sie alle Farmdateien in conf.dispatcher.d/enabled_farm, die Autor, ungesund, Gesundheit, lc oder Flush in ihrem Namen haben. Auch alle nicht verknüpften Farmdateien in conf.dispatcher.d/available_farm können entfernt werden.

1. **Farm-Dateien umbenennen**

   Alle Farmen in conf.dispatcher.d/enabled_farm müssen umbenannt werden, um dem Muster *.farm zu entsprechen. Daher sollte z.B. eine landwirtschaftliche Datei namens customerX_farm.any in customerX.farm umbenannt werden.

1. **Cache überprüfen**

   Geben Sie den Ordner conf.dispatcher.d/cache ein.

   Entfernen Sie alle Dateien mit dem Präfix ams_.

   Wenn conf.dispatcher.d/cache jetzt leer ist, kopieren Sie die Datei &quot;conf.dispatcher.d/cache/rules.any&quot;aus der standardmäßigen Dispatcher-Konfiguration in diesen Ordner. Die standardmäßige Dispatcher-Konfiguration befindet sich im Ordner src dieses SDK. Vergessen Sie nicht, die $include-Anweisungen anzupassen, die sich auf die Dateien ams_*_cache.any von Regeln in den landwirtschaftlichen Dateien beziehen.

   Wenn stattdessen &quot;conf.dispatcher.d/cache&quot;jetzt eine einzelne Datei mit dem Suffix _cache.any enthält, sollte sie in &quot;rules.any&quot;umbenannt werden. Vergessen Sie nicht, die $include-Anweisungen, die sich auf diese Datei beziehen, auch in den landwirtschaftlichen Dateien anzupassen.

   Wenn der Ordner jedoch mehrere, landwirtschaftliche spezifische Dateien mit diesem Muster enthält, sollte der Inhalt in die $include-Anweisung kopiert werden, die auf sie in den landwirtschaftlichen Dateien verweist.

   Entfernen Sie alle Dateien mit dem Suffix _invalidate_allowed.any.

   Kopieren Sie die Datei &quot;conf.dispatcher.d/cache/default_invalidate_any&quot;aus der standardmäßigen Dispatcher-Konfiguration in diesen Speicherort.

   Entfernen Sie in jeder Farm-Datei alle Inhalte im Abschnitt &quot;cache/allowedClients&quot;und ersetzen Sie sie durch:

   $include &quot;../cache/default_invalidate.any&quot;

1. **Client-Kopfzeilen überprüfen**

   Geben Sie den Ordner conf.dispatcher.d/clientheaders ein.

   Entfernen Sie alle Dateien mit dem Präfix ams_.

   Wenn conf.dispatcher.d/clientheaders jetzt eine einzelne Datei mit dem Suffix _clientheaders.any enthält, sollte sie in clientheaders.any umbenannt werden. Vergessen Sie nicht, die $include-Anweisungen, die sich auf diese Datei beziehen, auch in den landwirtschaftlichen Dateien anzupassen.

   Wenn der Ordner jedoch mehrere, landwirtschaftliche spezifische Dateien mit diesem Muster enthält, sollte der Inhalt in die $include-Anweisung kopiert werden, die auf sie in den landwirtschaftlichen Dateien verweist.

   Kopieren Sie die Datei &quot;conf.dispatcher/clientheaders/default_clientheaders.any&quot;aus der standardmäßigen Dispatcher-Konfiguration in diesen Speicherort.

   Ersetzen Sie in jeder Datei „clientheader include“-Anweisungen, die wie folgt aussehen:

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"`

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"`

   durch die Anweisung:

   `$include "../clientheaders/default_clientheaders.any"`

1. **Filter prüfen**

   * Geben Sie den Ordner conf.dispatcher.d/Filters ein.

   * Entfernen Sie alle Dateien mit dem Präfix ams_.

   * Wenn conf.dispatcher.d/Filters jetzt eine einzige Datei enthält, sollte sie in Filters.any umbenannt werden. Vergessen Sie nicht, die $include-Anweisungen, die sich auf diese Datei beziehen, auch in den landwirtschaftlichen Dateien anzupassen.

   * Wenn der Ordner jedoch mehrere, landwirtschaftliche spezifische Dateien mit diesem Muster enthält, sollte der Inhalt in die $include-Anweisung kopiert werden, die auf sie in den landwirtschaftlichen Dateien verweist.

   * Kopieren Sie die Datei &quot;conf.dispatcher/filters/default_filters.any&quot;aus der standardmäßigen Dispatcher-Konfiguration in diesen Speicherort.

   * Ersetzen Sie in jeder Farm-Datei alle „filter include“-Anweisungen, die wie folgt aussehen:

   * $include `"/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"`mit der Anweisung:

      `$include "../filters/default_filters.any"`

1. **Renders überprüfen**

   * Geben Sie den Ordner conf.dispatcher.d/renders ein.

   * Entfernen Sie alle Dateien in diesem Ordner.

   * Kopieren Sie die Datei &quot;conf.dispatcher.d/renders/default_renders.any&quot;aus der standardmäßigen Dispatcher-Konfiguration in diesen Speicherort.

   * Entfernen Sie in jeder Farm-Datei alle Inhalte im Abschnitt &quot;Rendering&quot;und ersetzen Sie sie durch:

      `$include "../renders/default_renders.any"`

1. **Virtualhosts überprüfen**

   * Rename the directory `conf.dispatcher.d/vhosts to conf.dispatcher.d/virtualhosts` and enter it.

   * Entfernen Sie alle Dateien mit dem Präfix `ams_`.

   * Wenn conf.dispatcher.d/virtualhosts jetzt eine einzelne Datei enthält, sollte sie in virtualhosts.any umbenannt werden. Vergessen Sie nicht, die $include-Anweisungen, die sich auf diese Datei beziehen, auch in den landwirtschaftlichen Dateien anzupassen.

   * Wenn der Ordner jedoch mehrere, landwirtschaftliche spezifische Dateien mit diesem Muster enthält, sollte der Inhalt in die $include-Anweisung kopiert werden, die auf sie in den landwirtschaftlichen Dateien verweist.

   * Kopieren Sie die Datei &quot;conf.dispatcher/virtualhosts/default_virtualhosts.any&quot;aus der standardmäßigen Dispatcher-Konfiguration in diesen Speicherort.

   * Ersetzen Sie in jeder Farm-Datei alle „filter include“-Anweisungen, die wie folgt aussehen:

      `$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"`
durch die Anweisung:

      `$include "../virtualhosts/default_virtualhosts.any"`


1. **Status prüfen, indem Sie den Validator ausführen**

   * Führen Sie den Dispatcher-Validator mit dem Unterbefehl dispatcher in Ihrem Ordner aus:

      `$ validator dispatcher`

   * Wenn Fehler wegen fehlender include-Dateien auftreten, überprüfen Sie, ob diese Dateien korrekt umbenannt wurden.

   * Wenn Fehler wegen einer nicht definierten Variable `PUBLISH_DOCROOT` auftreten, benennen Sie diese um in `DOCROOT`.

   * Weitere Informationen zu anderen Fehlern finden Sie im Abschnitt „Fehlerbehebung“ in der Dokumentation des Validator-Tools.

## Testen der Konfiguration mit einer lokalen Bereitstellung {#testing-config-local-deployment}

>[!IMPORTANT]
> Zum Testen Ihrer Konfiguration mit einer lokalen Bereitstellung ist eine Docker-Installation erforderlich.

Using the script `docker_run.sh` in the Dispatcher SDK, you can test that your configuration does not contain any other error that would only show up in deployment:

1. Implementierungsinformationen mit dem Validator generieren

   `validator full -d out`
Dadurch wird die vollständige Konfiguration validiert und Bereitstellungsinformationen generiert.

1. Beginn des Dispatchers in einem Dockerbild mit diesen Implementierungsinformationen

   Wenn Ihr AEM-Veröffentlichungs-Server auf Ihrem macOS-Computer ausgeführt wird und Port 4503 überwacht, können Sie Dispatcher wie folgt vor diesem Server starten:

   `$ docker_run.sh out docker.for.mac.localhost:4503 8080`

   Dadurch wird der Container gestartet und Apache am lokalen Port 8080 verfügbar gemacht.

## Using your new dispatcher configuration {#using-dispatcher-config}

If the validator no longer reports any issue and the docker container starts up without any failures or warnings, you are ready to move your configuration to a d`ispatcher/src` subdirectory of your git repository.