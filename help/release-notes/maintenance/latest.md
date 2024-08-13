---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: f12e60cdfce24dd2f6c1400157180d16b1b98653
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 20%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 17393 {#release-17393}

Im Folgenden finden Sie eine Zusammenfassung der kontinuierlichen Verbesserungen für die Wartungsversion 17393, die am Mittwoch, 13. August 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 17258.

Die Funktionsaktivierung von 2024.8.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-17393}

* FORMS-15436 - Behandeln Sie Ausnahmefehler in der Adobe Sign Status Scheduler ordnungsgemäß.
* FORMS-15362 - Fügen Sie die Konfiguration für Forms-Foundation in aemds hinzu, um die Anmeldung zu aktivieren.
* FORMS-15261 - SPA wird im Forms-Editor nicht dargestellt.
* FORMS-15138 - Umgang mit der Abwärtskompatibilität doppelter Daten aufgrund der JSON-Aktualisierung von Sling Commons.
* FORMS-15113 - Änderung des Schlüsselnamens zum Sid von visitorId für das RUM-Tracking.
* FORMS-15103 - In einem Formular angehängte Assets werden nicht in der Edge-Bereitstellung veröffentlicht.
* FORMS-15082 - JSON-Schema zur Zuordnung zu benutzerdefinierten adaptiven Formularkomponenten.
* FORMS-15002 - Vorlagentypregistrierung von v1-Fragmenten.
* FORMS-14845 - Unterstützung für xdpRef in Kernkomponentenbasisformularen über Forms Manager.
* FORMS-14840 - Forms Prefill Service-Fehler.
* FORMS-14836 - Verbesserung der Benutzeroberfläche von Forms Manager zur Auflistung von AF1-Fragmentvorlagen.
* FORMS-14834 - Vorlagenunterstützung für Fragmente in AF1.
* FORMS-14275 - Überschreiben der Dankeseite und Danksagungsmeldung im Einbettungscontainer
* FORMS-13623 - Automatische Speicherfunktion für V2 aktivieren.
* FORMS-8651 - Warndialogfeld zum Ändern der Konfiguration des Datenmodells auf der Seite &quot;Formulareigenschaften&quot;.
* SITES-23310 - Content Fragments REST API: Verhindern von Zirkelabhängigkeiten in verschachtelten Verweisen für Inhaltsfragmente.
* SITES-23285 - REST-API für Inhaltsfragmente: Erstellen Sie einen Endpunkt, um alle verfügbaren Sprachen aufzulisten.
* SITES-22857 - Content Fragments REST API: Kontrollkästchen-Auflistungsfelder sollten nicht zulassen, dass mehrere Eigenschaften auf &quot;false&quot;gesetzt sind.
* SITES-22813 - Content Fragments REST API: Definieren Sie Min-/Max-Eigenschaften für Auflistungsfelder.
* SITES-22031 - REST-API für Inhaltsfragmente: Rufen Sie zulässige Inhaltsfragmentmodelle für den Ordner eines Fragments ab.
* SITES-17640 - Content Fragments REST API: Validierung der Publish-Vorgänge für Inhaltsfragmente.
* SITES-22677 - Content Fragments REST API: Rufen Sie eine flache Liste von nachkommenden Verweisen ab
* SITES-22207 - Bei der Inhaltserstellung dupliziertes Modell
* SITES-23093 - Eventing: Fügen Sie Payloads Tags für Inhaltsfragmentmodellereignisse hinzu.
* SITES-23092 - Eventing: Fügen Sie Payloads Tags für Inhaltsfragment-Ereignisse hinzu.
* SITES-22447 - Unterstützung der Vererbung von Experience Fragment-Eigenschaften zur Registerkarte Grundlegende Eigenschaften hinzufügen.
* SITES-12209 - Verbessern der Leistung des Richtlinien-Editors durch Hinzufügen von cq:policy zum Index.

### Behobene Probleme {#fixed-issues-17393}

* CQ-4358028 - Projekt konnte nicht erstellt werden, wenn Miniaturansichten hochgeladen wurden.
* CQ-4357891 - Sequenzfehler des exportierten XLIFF.
* CQ-4357059 - Übersetzungsauftrag dauert Stunden, bis 503 Timeouts in AEMaaCS auftreten.
* FORMS-15320 - Die Übermittlung per E-Mail funktioniert nicht in einem auf Kernkomponenten basierenden Formular.
* FORMS-15272 - AEM Forms - Kontrollkästchengruppe, die nur einen Wert sendet.
* FORMS-15269 - Produktbezogene Probleme nach der Wartungsversion 16461.
* FORMS-15174 - JsonSchemaParser isValid-Problem.
* FORMS-15095 - Mehrzeiliger Text-Feld kann in AEM Forms nicht nur auf Bedienfelder, sondern auch auf Bedienfelder mit Containern gestaffelt werden.
* FORMS-15057 - FDM Sharepoint list gibt Anlagenfehler für Übermittlung aus > 999.
* FORMS-15011 - Core Editor verursacht Konsolenfehler beim Öffnen eines Formulars im Editor.
* FORMS-14809 - SDK-Ordner werden nicht automatisch im freigegebenen temporären Ordner erstellt.
* FORMS-14327 - Forms-Dienst-APIs : Extract data:- gibt 500 Antwort-Code, wenn ein nicht interaktives PDF-Dokument in der Eingabe bereitgestellt wird.
* FORMS-7475 - Die Sortierung funktioniert nicht auf der Seite zur Erstellung adaptiver Formulare.
* FORMS-3309 - Wenn beim Senden eines Formulars mehrere Optionen ausgewählt sind, wird in einem generierten DoR nur eine Option angezeigt.
* SITES-23646 - GraphQL-Modellen-Endpunkt schlägt bei mit OpenAPI erstellten Modellen fehl, wenn Felder eindeutig sind.
* SITES-23637 - Content Fragments REST API: OpenAPI verwendet nicht den richtigen Werttyp für Auflistungen.
* SITES-23573 - Content Fragments REST API: Live-Beziehungen werden in GET Content Fragments nicht durch uuid berücksichtigt.
* SITES-23535 - Content Fragments REST API: Auflistungsmehrfelder des Inhaltsfragmentmodells haben leere Werte.
* SITES-23534 - Content Fragments REST API: Content Fragment Validation ClassCastException.
* SITES-23524 - Anpassen des GraphQL BFF-Modellendpunkts zur Unterstützung von Auflistungsfeldern mit mehreren Feldern.
* SITES-23467 - Content Fragments REST API: Suchmodelle schlagen aufgrund eines Cursorproblems fehl.
* SITES-23327 - ArrayIndexOutOfBoundsException in AuditLogTimelineEventProvider während der Beschreibung der Timeline-Ereignisverarbeitung.
* SITES-23277 - Content Fragments REST API: Die Live-Beziehungsüberprüfung des Inhaltsfragmentfelds sollte nur für Live Copies durchgeführt werden.
* SITES-23232 - Benutzerdefinierte Validierung funktioniert in der neuen Benutzeroberfläche des CF-Editors nicht.
* SITES-23090 - Content Fragments REST API: Titel eines gesperrten Inhaltsfragments kann nicht aktualisiert werden.
* SITES-22981 - Das Weiterleiten eines verschachtelten Launches, der nicht tief verankert ist, wird nicht veröffentlicht.
* SITES-22870 - PathAttributesHandler.processSrcAttr ArrayIndexOutOfBoundsException.
* SITES-22814 - Content Fragments REST API: Die Werte der Feldauflistungsfragmente für Kontrollkästchen sollten anhand der im Modell definierten Schlüssel geordnet werden.
* SITES-22716 - Problem mit der Live-Nutzungsliste für OOTB-Komponenten.
* SITES-22457 - Das Bewerben eines Launches, der nicht tief ist, aktualisiert den Quellinhalt nicht.
* SITES-22449 - Änderungen in Inhaltsfragmenten können nach AEM P20-Aktualisierung nicht gespeichert werden.
* SITES-22279 - Content Fragments REST API: Dem Inhaltsfragment fehlt das eindeutige Attribut für Auflistungstypen.
* SITES-22203 - Content Fragments REST API: Align Management-APIs, um auf dieselbe Situation zu reagieren.
* SITES-21973 - Content Fragments REST API: Dem Modell fehlt das eindeutige Attribut für Auflistungstypen.
* SITES-20364 - 302 Umleitungen funktionieren nicht mit Selektor in URL.
* SITES-21198 - VersionPreviewServlet: Die Bereinigung wird gleichzeitig auf allen Clusterknoten ausgeführt, die Zusammenführungskonflikte verursachen, und blockiert Commits
* GRANITE-53094 - Repository-basierte JS-Use-Objekte können bei Verwendung relativer Pfade nicht gefunden werden.

### Bekannte Probleme {#known-issues-17393}

Keine.

### Änderungshinweis {#change-notice-17393}

* AEM as a Cloud Service deaktiviert ab September 2024 die Serialisierung von Ressourcen-Konfliktlösern über das Sling Model Exporter-Framework. Weitere Informationen finden Sie in der [Dokumentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md).

### Eingestellte Funktionen und APIs {#deprecated-17393}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Eingebettete Technologien {#embedded-tech-17393}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.66.0 | [Oak-API 1.66.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.66.0/index.html) |
| AEM SLING-API | 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.25.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
