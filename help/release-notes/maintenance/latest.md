---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c8a798e1f1b7234f91682b6e5ef7072e024df022
workflow-type: ht
source-wordcount: '693'
ht-degree: 100%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 18751 {#18751}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 18751, die am 11. Dezember 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 18598.

Die Funktionsaktivierung von 2025.1.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-18751}

* SKYOPS-88509: Java 21-Unterstützung für das AEM SDK.

### Behobene Probleme {#fixed-issues-18751}

* ASSETS-42802: Die Schaltfläche „Zurück“ auf MFE funktionierte nicht immer und zeigte ein zusätzliches Dialogfeld an.
* ASSETS-44148: Behobenes NODE_MOVED-Ereignis in AEM, das NPE verursachen konnte.
* ASSETS-44418: Die korrigierte Umgebung war nicht für Skyline konfiguriert.
* ASSETS-44821: Der Ereignisfilter für die Aktualisierung wurde korrigiert, um mit der Formular-URL codierte Daten für Upload-Ereignisse einzuschließen.
* CNTBF-298: Behobenes Fehlschlagen einer Inhaltskopie mit UUID-Konflikten.
* CNTBF-331: [content-copy-bundle] Version 2.0.14.
* FORMS-16572: Testfehler für „Workflow entfernen“ für den Java 21 SDK-Build.
* GRANITE-36205: Automatisiertes Update für interne Oak-Versionen in QS.
* GRANITE-53704: Neubewertung von Sling Discovery im Repository-Dienst.
* GRANITE-54300: Update von Oak auf die neueste öffentliche Version (1.70.0).
* GRANITE-54416: Update von Filevault auf Version 3.8.2.
* GRANITE-54462: Konfigurieren von SubscriberAgents sodass sie hc.tags von „systemready“ verwenden.
* GRANITE-54542: Aktualisierung der commons-io-Abhängigkeit auf 2.17.0.
* GRANITE-54658: Hinzufügen von DelayFactor- und Batch-OSGi-Konfigurationen für FullGC in QS.
* GRANITE-54696: Erweiterter Importbereich für Jackrabbit-API.
* GRANITE-54803: Deaktivieren von ClusterAtExchange in AEM, wenn imsauth aktiv ist.
* GRANITE-55095: Update von Oak auf die neueste öffentliche Version (1.72.0).
* GUIDES-20006: Der als „Fertig“ markierte Dokumentstatus wird vor dem Speichern einer neuen Version wieder auf „Entwurf“ zurückgesetzt, was dazu führt, dass der Status „Fertig“ in keiner Dokumentversion bestehen bleibt.
* GUIDES-21840: In der nativen PDF-Ausgabe fehlen Kapiteltitel im Inhaltsverzeichnis, was zu einer falschen Hierarchie führt.
* GUIDES-19558: Beim Bearbeiten und anschließenden Speichern einer Baseline in einer Cloud-Einrichtung tritt nach einer Minute eine Zeitüberschreitung auf, wenn die Baseline eine große Anzahl von Themen oder Karten enthält.
* GUIDES-19733: Die Kartenübersetzung mithilfe der Baseline wird langsam und kann letztendlich nicht die Liste aller zugehörigen Themen und Zuordnungsdateien laden.
* SITES-26798: „Automatische Promotion starten“ aktualisiert nicht den Promotions-Status (das Promotions-Datum).
* SITES-27137: Entfernen der Abhängigkeit von Sling Commons-Metriken aus dem MSM-Kern.
* SKYOPS-75446: Fehler behoben, dass AEM manchmal eine 404-Seite oder Seiten mit fehlendem Inhalt zurückgibt.
* SKYOPS-76366: Keine Jetty-Threadpool-Metriken in AEM-Version 15977 und höher.
* SKYOPS-82371: java.io.IOException: classFile.delete() fehlgeschlagen.
* SKYOPS-83369: AEM-Bereitstellungen können nicht gestartet werden, wenn die Ausführung des Transformationsvorgangs keine Bundles generiert.
* SKYOPS-83910: Parallelitätsprobleme behoben, die in SKYOPS-82371 festgestellt wurden.
* SKYOPS-84821: Festlegen der Konfiguration „sling.includes.checkcontenttype“ des Sling-Haupt-Servlets auf „true“.
* SKYOPS-85798: Es wurde der Fehler behoben, dass ein Transformationsauftrag leere Indexdefinitionen definiert.
* SKYOPS-86251: Upgrade auf AEM Analyzer-Kern 1.5.6 und Aktivieren des Produkt-Package-Import-Analyzers im Transformationsauftrag.
* SKYOPS-86710: Entfernen von Minify-Testfehlern für den Java 21 SDK-Build.
* SKYOPS-86745: Aktualisierung auf Sling ResourceResolver 1.12.2.
* SKYOPS-89616: Es wurde ein Problem behoben, durch das in der Adobe Developer Console kein technisches Konto erstellt werden konnte.
* SKYOPS-89691: Falsche Artefakt-ID korrigiert, die für ASM-Warnungen verwendet wird.
* SKYOPS-89699: Fehlende Warnungen für alte Groovy-Versionen, die in die „Orbinson“-Variante der Groovy-Konsole eingebettet sind.
* SKYOPS-88664: Protokollierung und Schutz für den Fall, dass eine heruntergeladene Kartendatei die Obergrenze von 1024 Zeilen überschreitet.
* SKYOPS-89734: Freigabe des Dispatcher-Images 2.0.235.

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
| AEM Oak | 1.72.0 | [Oak-API 1.72.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html?lang=de) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.27.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
