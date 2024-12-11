---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c8a798e1f1b7234f91682b6e5ef7072e024df022
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 18751 {#18751}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 18751, die am Donnerstag, 11. Dezember 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 18598.

Die Funktionsaktivierung von 2025.1.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-18751}

* SKYOPS-88509: Java 21-Unterstützung für das AEM SDK.

### Behobene Probleme {#fixed-issues-18751}

* ASSETS-42802: Die Schaltfläche &quot;Zurück&quot;auf MFE funktioniert nicht immer und zeigt einen zusätzlichen Dialog an.
* ASSETS-44148: Festes NODE_MOVED-Ereignis in AEM kann zu NPE führen.
* ASSETS-44418: Korrektes Env korrigieren ist nicht in der Skyline konfiguriert.
* ASSETS-44821: Ereignisfilter für Upload-Ereignisse wurde dahingehend korrigiert, dass Formular-URL-kodierte Daten für Upload-Ereignisse einbezogen werden.
* CNTBF-298: Die behobene Inhaltskopie schlägt bei UUID-Konflikten fehl.
* CNTBF-331: [content-copy-bundle] Version 2.0.14.
* FORMS-16572: Entfernen Sie Fehler bei Workflow-Tests für Java 21 SDK-Build.
* GRANITE-36205: Automatisierte Aktualisierung für interne Oak-Versionen in QS.
* GRANITE-53704: Sling Discovery im Repository-Dienst neu bewerten.
* GRANITE-54300: Update von Oak auf die neueste öffentliche Version (1.70.0).
* GRANITE-54416: Update von Filevault auf Version 3.8.2.
* GRANITE-54462: Konfigurieren Sie SubscriberAgents für die Verwendung von hc.tags von &quot;systemready&quot;.
* GRANITE-54542: Aktualisieren der allgemeinen Abhängigkeit auf 2.17.0.
* GRANITE-54658: Fügen Sie OSGi-Konfigurationen für &quot;delayFactor&quot;und &quot;batch-size&quot;für &quot;fullGC&quot;in QS hinzu.
* GRANITE-54696: Erweiterter Importbereich für die Jackrabbit-API.
* GRANITE-54803: Deaktivieren Sie ClusterAtExchange in AEM, wenn imsauth aktiv ist.
* GRANITE-55095: Update von Oak auf die neueste öffentliche Version (1.72.0).
* GUIDES-2006: Der als Fertig markierte Dokumentstatus kehrt vor dem Speichern einer neuen Version zu Entwurf zurück, wodurch der Status Fertig in keiner Dokumentversion beibehalten wird.
* GUIDES-21840: In der nativen PDF-Ausgabe fehlen Kapiteltitel im Inhaltsverzeichnis, was zu einer falschen Hierarchie führt.
* GUIDES-19558: Bearbeiten und Speichern einer Grundlinie in einem Cloud-Setup-Timeout nach 1 Minute, wenn die Grundlinie über eine große Anzahl von Themen oder Karten verfügt.
* GUIDES-19733: Die Zuordnungsübersetzung mithilfe der Grundlinie wird langsam, und schließlich kann die Liste aller zugehörigen Themen und Zuordnungsdateien nicht geladen werden.
* SITES-26798: Die automatische Promotion starten aktualisiert nicht den Promotion-Status (Promotion Date).
* SITES-27137: Entfernung der Abhängigkeit von Sling-Metriken vom MSM-Kern.
* SKYOPS-75446: Fehlerkorrektur - AEM gibt manchmal 404 oder Seiten mit fehlendem Inhalt zurück.
* SKYOPS-76366: Keine Jetty-Threadpool-Metriken in AEM Version 15977 und höher.
* SKYOPS-82371: java.io.IOException: classFile.delete() failed.
* SKYOPS-83369: AEM -Bereitstellungen können nicht gestartet werden, wenn bei der Ausführung des Umwandlungsauftrags keine Bundles generiert werden.
* SKYOPS-83910: Es wurden Parallelitätsprobleme in SKYOPS-82371 behoben.
* SKYOPS-84821: Setzen Sie die sling.include.checkcontenttype-Konfiguration des Sling-Hauptservlets auf &quot;true&quot;.
* SKYOPS-85798: Vorgang &quot;Fixed Transform&quot;generiert leere Indexdefinitionen.
* SKYOPS-86251: Aktualisieren Sie auf AEM Analyser Core 1.5.6 und aktivieren Sie den Produktpaketimport-Analyser im Transformationsauftrag.
* SKYOPS-86710: Minimieren Sie Testfehler für Java 21 SDK-Build.
* SKYOPS-86745: Aktualisierung auf Sling ResourceResolver 1.12.2.
* SKYOPS-89616: Es wurde ein Fehler behoben, der dazu führte, dass in Adobe Developer Console kein technisches Konto erstellt werden konnte.
* SKYOPS-89691: Fehlerhafte Artefakt-ID behoben, die für ASM-Warnungen verwendet wurde.
* SKYOPS-89699: Fehlende Warnungen für alte Groovy-Versionen, eingebettet in den Geschmack &quot;orbinson&quot;der Groovy Console.
* SKYOPS-88664: Protokollieren und schützen Sie vor einem Fall, wenn die heruntergeladene Map-Datei eine Grenze von mehr als 1024 aufweist.
* SKYOPS-89734: Dispatcher-Bild 2.0.235 veröffentlichen.

Weitere Informationen zu den neuen und verbesserten Funktionen und zu den Problemen, die in den Experience Manager Guides behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-18751}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-18751}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-18751}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 3 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-18751}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,72,0 | [Oak-API 1.72.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.27.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
