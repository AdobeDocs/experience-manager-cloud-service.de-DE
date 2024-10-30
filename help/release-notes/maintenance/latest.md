---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9278ec9bb5bccd7b40cd65a120f296faba454b9c
workflow-type: ht
source-wordcount: '569'
ht-degree: 100%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 18311 {#18311}

Im Folgenden finden Sie eine Zusammenfassung der fortlaufenden Verbesserungen für die Wartungsversion 18311, die am 22. Oktober 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 18175.

Die Funktionsaktivierung von 2024.10.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-18311}

* ASSETS-41820: Indizierungsverbesserungen für die Verarbeitung von Watchdog.
* ASSETS-43720: Funktionsverbesserungen bei der Verarbeitung von Watchdog.
* ASSETS-42554: Leistungsverbesserungen für große Ordner.
* SKYOPS-77603: Verwaltung von Weiterleitungen durch Geschäftsbenutzende.

### Behobene Probleme {#fixed-issues-18311}

* ASSETS-37534: Änderungen bei der Suche, damit die für das Genehmigungsziel verwendete Eigenschaft nicht angezeigt wird.
* ASSETS-38322: Entfernung der Konfiguration des Anbieters von Veröffentlichungskriterien, Entfernung der Veröffentlichungsereignis-Funktion.
* ASSETS-40482: Problem mit der Barrierefreiheit bei Wiedergabe/Pause und Schaltfläche für Stummschaltung/Aufhebung der Stummschaltung im Scene7-Video-Player.
* ASSETS-40593: Fehlerseite wird nach Klicken auf die Schaltfläche „Eigenschaften“ in „Assets“ > „Dateien“ angezeigt.
* ASSETS-40598: Synchronisation intelligenter Zuschnitte, wenn nicht synchronisiertes Asset in einen synchronisierungsfähigen Ordner verschoben wird.
* ASSETS-40743: Probleme mit dem Auslösen des Dialogfelds „Asset ersetzen“, wenn bestimmte Zeichen im Dateinamen vorhanden sind.
* ASSETS-40825: Assets-Suchfacetten verschwinden nach Bearbeitung des Suchformulars.
* ASSETS-41007: Beim Löschen in AEM werden manchmal verwaiste Assets bei der Bereitstellung hinterlassen.
* ASSETS-41172: Dynamic Media-Vorlagen – Sonderzeichen im Namen nicht zulässig.
* ASSETS-41896: Assets, die in der Eigenschaft „cq:discarded“ im Ordner erwähnt werden, sollten NICHT in Brand Portal veröffentlicht werden.
* ASSETS-42067: Dynamic Media-Vorlagen - Download gibt einen Fehler aus.
* ASSETS-42070: Dynamic Media-Vorlagen – Benutzende ohne Adminrechte sollten Zugriff auf das Erstellen/Bearbeiten von Vorlagen haben.
* ASSETS-42344: Synchronisation von Connected Assets getrennt – Wiederverbindung und Beratung für Kundschaft.
* ASSETS-42620: Problem mit der Vorschauoption von Asset-Versionen – zeigt beim Öffnen des Assets leere Vorschau an.
* ASSETS-42701: Problem mit Web-optimierter Bildbereitstellung und Bildzuschnitt.
* ASSETS-42966: Asynchrone Barrikade kann bei Fehlern entsperrt werden, wenn mehrere Aufträge denselben Pfad teilen.
* ASSETS-43072: Dynamic Media-Vorlagen – Vorlage verweist auf Suchumbrüche in einem ungültigen Verweis.
* ASSETS-43212: Internationalisierungsprobleme im Metadatenschema-Editor.
* ASSETS-43202: Fehlerkorrekturen für die Auswahl von Anmerkungen, die aus der Timeline gedruckt werden sollen.
* ASSETS-43502: AEM CS – Vorhandener Bildvorgabenname wird nicht unter „Seite bearbeiten“ angezeigt.
* ASSETS-43538: Auftrag zum asynchronen Kopieren von Assets verwendet falsche Eigenschaft für Quellpfad.
* ASSETS-43798: Prüfung des Zielpfads vor dem Kopieren von Assets.
* ASSETS-43945: Erhöhen der Wiederholungsverzögerung für die Warteschlange asynchroner Assets auf 20 Minuten.
* ASSETS-44025: Asynchroner Auftrag zum Löschen von Assets schlägt bei der Auswahl einzelner Assets fehl.
* SITES-26128: Ausnahmefehler beim Umsetzen der Klasse in CreateLiveCopyStep.
* SCRNS-4551: [SG Pools] Screens-Kanal, der die Videokomponente enthält, zeigt in Browser-Vorschau sowie Player „Allgemeiner Seitenfehler“ an

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
