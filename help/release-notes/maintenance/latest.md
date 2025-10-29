---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9d081b468e42306c56238bee6117d92c6afd48d4
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 25%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 23122 {#23122}

Im Folgenden finden Sie eine Zusammenfassung der fortlaufenden Verbesserungen für die Wartungsversion 23122, die am Donnerstag, 29. Oktober 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 22943.

Die Funktionsaktivierung von 2025.11.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-23122}

* FORMS-21594: Sperren der Vorlage für interaktive Kommunikation und des Inhalts- und Layout-Layouts für Inhaltsautoren aktivieren.
* FORMS-20385: Unterstützt die XDP-Bearbeitung im Editor für interaktive Kommunikation.
* FORMS-10883: Unterstützung für JSON mit XHTML-Namespace-Tags in der DoR-Generierung, um ein genaues Rendering von Rich-Text-Daten sicherzustellen, die über APIs übermittelt werden.
* FORMS-21751: Funktionen der Arbeitsfläche - Textüberlauf, Benutzeroberfläche für Seitenumbruch.
* FORMS-22049: Editor für interaktive Kommunikation - Migration zu Spectrum 2.
* FORMS-22050: Unterstützung für dynamische Seitennummerierung im Editor für interaktive Kommunikation.
* FORMS-21606: Öffentliche OSGi-Render-SPIs für interaktive Kommunikation.
* FORMS-21613: Transaktionsberichte und Leistungsprotokollierung für Render-SPIs für interaktive Kommunikation.
* SITES-35092: Inhaltsfragmente - Neues Mixin- und Upgrade-Verfahren für die semantische Suche.
* SITES-32319: Bereitstellungs-OpenAPI - Support-Seitenverweise.
* SITES-20123: GraphQL: Unterstützt hochgestellte Elemente in JSON-Antworten.
* SITES-34744: Neue Eigenschaft „Karte“ in der Antwort des Inhaltsfragments, die Daten enthält, die zum Rendern einer Miniaturansicht verwendet werden können.
* SITES-34571: Zulassen, dass Auflistungsfelder leer sind.
* SITES-34812: Es wurde die Möglichkeit hinzugefügt, ein Inhaltsfragment ohne seine Referenzen abzurufen, indem der Parameter „references“ mit dem Wert „none“ verwendet wird.
* SITES-35176: Das Auschecken eines Inhaltsfragments über die Touch-optimierte Benutzeroberfläche verhindert jetzt die Bearbeitung des Inhaltsfragments im neuen Editor durch andere Benutzer.
* SITES-30371: Es wurde Unterstützung für UUID-basierte Referenzfelder hinzugefügt.
* SITES-19309: Beim Öffnen des Assistenten zum Verschieben von Seiten werden maximal 150 Verweise abgerufen.
* SITES-32515: Edge Delivery mit universellem Editor - Hinzufügen von Unterstützung für Mehrfachfelder und zusammengesetzte Mehrfachfelder (früher Zugriff).
* SITES-33784: Edge Delivery mit universellem Editor - Hinzufügen von Unterstützung für ld-json in Seitenmetadaten.
* SITES-34832: Edge Delivery mit universellem Editor - Öffentlichen Pfad einer Seite zur Antwort des Seiteninformations-Servlets hinzufügen.
* SITES-25893: Edge Delivery mit universellem Editor - Hinzufügen von Unterstützung für „strong“ und Hervorheben des Text-Renderings in Blöcken.
* SITES-26158: Edge Delivery mit universellem Editor - Hinzufügen von Unterstützung für Tabellen-Markup in Blöcken und Spalten (früher Zugriff).
* SITES-27949: Edge Delivery mit universellem Editor - Pfadzuordnung optional machen.

### Behobene Probleme {#fixed-issues-23122}

* CQ-4361144: Es wurde ein Problem behoben, bei dem Inhaltsfragmente aus Übersetzungsaufträgen übersprungen wurden.
* CQ-4355446: Die nicht lokalisierte Zeichenfolge im Übersetzungsprojekt, die im Dialogfeld „Übersetzungsauftrag abbrechen“ auftritt, wurde behoben.
* SITES-34555: GraphQL - QueryValidationError nach Bereitstellungen.
* SITES-35077: Inhaltsfragmente - Das Aufheben der Veröffentlichung schlägt für Fragmente mit Klammern aufgrund einer falschen URL-Codierung fehl.
* SITES-35374: Inhaltsfragmente - Bearbeitetes Inhaltsfragment verschwindet nach der Rückkehr.
* SITES-36130: NPE in `EditorRestrictionsStatusImpl`.
* SITES-35810: NullPointerException in Launches blockiert die Warteschlange publishEdgeDeliverySubscriber.
* SITES-34368: AEM CIF generiert 12 GraphQL-Aliase - überschreitet das Limit von Magento 2.4.6-P12 von 10.
* SITES-36193: Fehlerbehebungen am CCS-Connector.
* SITES-35169: Es wurde ein Problem behoben, das zu einer falschen Paginierung führte, wenn ungültige Fragmentressourcen von der Suche zurückgegeben wurden.
* SITES-34574: Es wurde ein Problem behoben, bei dem der Cursor in einigen Fällen nicht von der Inhaltsfragmentsuch-API zurückgegeben wurde.
* SITES-35520: Es wurde ein Problem behoben, das beim Versuch, Inhalte zu veröffentlichen, zu ClassCastException oder Timeouts führte.
* SITES-35210: Es wurde eine NullPointerException behoben, die beim Versuch auftrat, ein fehlerhaftes Fragment mit leerem Verweisfilter zu veröffentlichen.
* SITES-35933: Es wurde ein Fehler behoben, der dazu führte, dass leere „Aktivierungsanfrage“-Workflows nach der Veröffentlichung des Inhaltsfragments ausgelöst wurden.
* SITES-35925: Es wurde ein Fehler im Zusammenhang mit dem Patchen von Inhaltsfragmentmodellen behoben, durch den die Eigenschaften „übersetzbar“ und „showThumbnail“ aus dem Modell gelöscht wurden.
* SITES-35409: Es wurde ein Fehler behoben, der die erneute Veröffentlichung angepasster Fragmente beim Verschieben einer Seite verhinderte.
* SITES-15757: Es wurde ein Fehler behoben, der die erneute Veröffentlichung angepasster Seiten beim Verschieben einer Seite verhinderte.
* SITES-34638: Es wurde ein Fehler behoben, durch den Eigenschaften von übergeordneten Seiten beim Erstellen neuer Versionen nicht einbezogen wurden.
* SITES-35071: CSV-Export gibt ungefilterte Ergebnisse zurück, wenn Omnisearch zitierte Phrasen verwendet.
* SITES-32182: Edge Delivery mit universellem Editor - Beheben von Kodierungsproblemen mit URLs, die bereits kodierte Anforderungsparameter enthalten.
* SITES-34324: Edge Delivery mit universellem Editor - Fehlerbehebung beim Rendern von Links mit einem tel: -Protokoll.
* SITES-35333: Edge Delivery mit universellem Editor - Korrigieren Sie die Auswahl der Asset-Ausgabedarstellung für Bilder in Seitenmetadaten.
* SITES-35549: Edge Delivery mit universellem Editor - Korrigieren Sie doppelt kodierte HTML-Entitäten in Seitenmetadaten.

### Bekannte Probleme {#known-issues-23122}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-23122}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-23122}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion wurden 18 identifizierte Schwachstellen behoben, was für einen noch robusteren Systemschutz sorgt.

### Eingebettete Technologien {#embedded-tech-23122}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.86.0 | [Oak 1.86.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.86/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2,30,2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
