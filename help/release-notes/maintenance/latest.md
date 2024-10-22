---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9278ec9bb5bccd7b40cd65a120f296faba454b9c
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 38%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 18311 {#18311}

Im Folgenden finden Sie eine Zusammenfassung der kontinuierlichen Verbesserungen für die Wartungsversion 18311, die am Mittwoch, 22. Oktober 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 18175.

Die Funktionsaktivierung von 2024.10.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-18311}

* ASSETS-41820 : Indizierungsverbesserungen für die Verarbeitung von Watchdog.
* ASSETS-43720 : Funktionsverbesserungen bei der Verarbeitung von Watchdog.
* ASSETS-42554 : Leistungsverbesserungen für große Ordner.
* SKYOPS-77603 : Verwaltung von Weiterleitungen durch Geschäftsbenutzer.

### Behobene Probleme {#fixed-issues-18311}

* ASSETS-37534 : Änderungen bei der Suche, um die für die Validierungszielgruppe verwendete Eigenschaft nicht anzuzeigen.
* ASSETS-38322 : Veröffentlichungskriterien entfernen, Konfiguration des Veröffentlichungsereignisses entfernen.
* ASSETS-40482 : Problem mit der Barrierefreiheit bei Wiedergabe/Pause und Stummschaltung/Unmute-Schaltfläche im Scene7-Videoplayer.
* ASSETS-40593 : Die Fehlerseite tritt nach dem Klicken auf die Schaltfläche &quot;Eigenschaften&quot;in Assets > Dateien auf.
* ASSETS-40598 : Synchronisieren Sie smarte Zuschnitte, wenn nicht synchronisierte Assets in einen synchronisierungsfähigen Ordner verschoben werden.
* ASSETS-40743 : Probleme mit dem Auslösen des Dialogfelds &quot;Asset ersetzen&quot;, wenn bestimmte Zeichen im Dateinamen vorhanden sind.
* ASSETS-40825 : Assets-Suchfacetten verschwinden nach der Bearbeitung des Suchformulars.
* ASSETS-41007 : Beim Löschen auf AEM verlässt das verwaiste Assets manchmal beim Versand.
* ASSETS-41172 : Dynamic Media-Vorlagen - Sonderzeichen sind im Namen nicht zulässig.
* ASSETS-41896 : Assets, die in der Eigenschaft cq:discarded im Ordner erwähnt wird, sollte NICHT in Brand Portal veröffentlicht werden.
* ASSETS-42067: Dynamic Media-Vorlagen - Download gibt einen Fehler aus.
* ASSETS-42070 : Dynamic Media-Vorlagen - Benutzer ohne Administratorrechte sollten Zugriff auf Vorlagen zum Erstellen/Bearbeiten haben.
* ASSETS-42344: Synchronisation von Connected Assets getrennt - Wiederverbindung und Beratung für Kunden.
* ASSETS-42620 : Problem mit der Vorschauoption von Asset-Versionen - zeigt eine leere Vorschau an, wenn wir das Asset öffnen.
* ASSETS-42701 : Problem mit Web-optimierter Bildbereitstellung und Zuschneiden.
* ASSETS-42966 : Asynchrone Barrikade kann bei Fehlern entsperrt werden, da mehrere Aufträge denselben Pfad teilen.
* ASSETS-43072 : Dynamic Media-Vorlagen - Vorlage verweist auf Suchumbrüche in einem ungültigen Verweis.
* ASSETS-43212: Internationalisierungsprobleme im Metadatenschema-Editor.
* ASSETS-43202 : Fehlerkorrekturen für die Auswahl von Anmerkungen, die aus der Timeline gedruckt werden sollen.
* ASSETS-43502 : AEM CS Vorhandenen Bildvorgabennamen wird nicht auf Seite bearbeiten angezeigt.
* ASSETS-43538: Auftrag zum asynchronen Kopieren von Assets verwendet falsche Eigenschaften für den Quellpfad.
* ASSETS-43798 : Überprüfen Sie vor dem Kopieren von Assets, ob der Zielpfad erreicht wurde.
* ASSETS-43945 : Erhöhen Sie die Wiederholungsverzögerung für die Warteschlange asynchroner Assets auf 20 Minuten.
* ASSETS-44025 : Async delete assets job schlägt bei der Auswahl einzelner Assets fehl.
* SITES-26128 : Klassenausnahme in CreateLiveCopyStep.
* SCRNS-4551 : [SG Pools] Der Screens-Kanal, der die Videokomponente enthält, zeigt &quot;Allgemeiner Seitenfehler&quot;in der Browservorschau und im Player an

### Bekannte Probleme {#known-issues-18311}

* FORMS-15818: Angaben „Komponenten-Beschreibungseintrag `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` nicht gefunden“ in Server-Protokollen. Dies sind harmlose Protokollanweisungen.

### Eingestellte Funktionen und APIs {#deprecated-18311}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-18311}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 3 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-18311}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.70.0 | [Oak-API 1.70.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.27.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
