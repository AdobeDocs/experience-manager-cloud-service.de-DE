---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 5474d0c4295cf8eb576cc416589727c67ffafac7
workflow-type: tm+mt
source-wordcount: '1195'
ht-degree: 20%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 23320 {#23320}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 23320, die am Donnerstag, 12. November 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 22943.

Die Funktionsaktivierung von 2025.11.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Versions-Roadmap von Experience Manager](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

>[!NOTE]
>
>Die Veröffentlichung 23122 wurde am 3. November als privat eingestuft.

### Verbesserungen {#enhancements-23320}

* CQ-4361363: Neueste AEM und Granite-Übersetzungen.
* FORMS-21594: Sperren der Vorlage für interaktive Kommunikation und des Inhalts- und Layout-Layouts für Inhaltsautoren aktivieren.
* FORMS-20385: Unterstützt die XDP-Bearbeitung im Editor für interaktive Kommunikation.
* FORMS-10883: Unterstützung für JSON mit XHTML-Namespace-Tags in der DoR-Generierung, um ein genaues Rendering von Rich-Text-Daten sicherzustellen, die über APIs übermittelt werden.
* FORMS-21751: Funktionen der Arbeitsfläche - Textüberlauf, Benutzeroberfläche für Seitenumbruch.
* FORMS-22049: Editor für interaktive Kommunikation - Migration zu Spectrum 2.
* FORMS-22050: Unterstützung für dynamische Seitennummerierung im Editor für interaktive Kommunikation.
* FORMS-21606: Öffentliche OSGi-Render-SPIs für interaktive Kommunikation.
* FORMS-21613: Transaktionsberichte und Leistungsprotokollierung für Render-SPIs für interaktive Kommunikation.
* GRANITE-62394: Joda-time auf 2.12.7 aktualisiert.
* GRANITE-36205: Aktualisieren Sie Oak auf Version 1.88.0.
* GRANITE-62020: Verbessern der Wiederholungsrichtlinie für `RepositoryServiceHttpClient`.
* GRANITE-62169: Aktualisieren Sie commons-lang auf 3.19.0.
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
* SITES-35811: Neuen Index in Inhaltsfragmentabfragen verwenden.
* SKYOPS-120857: Aktualisieren von filevault auf 4.1.4.
* SKYOPS-118390: JCR-Ressource auf 3.3.6 aktualisieren.
* SKYOPS-121082: Aktualisieren von Versionen von `org.apache.sling.discovery.standalone`-, `org.apache.sling.jcr.packageinit`- und `org.apache.sling.commons.fsclassloader` Sling-Bundles.

### Behobene Probleme {#fixed-issues-23320}

* ASSETS-58926: Korrigieren Sie die Miniaturbildfunktion für Videoänderungen in DM.
* ASSETS-58623: Korrigieren Sie NPE in Omnisearch, wenn die Konfiguration vorhanden ist.
* CQ-4361144: Es wurde ein Problem behoben, bei dem Inhaltsfragmente aus Übersetzungsaufträgen übersprungen wurden.
* CQ-4355446: Die nicht lokalisierte Zeichenfolge im Übersetzungsprojekt, die im Dialogfeld „Übersetzungsauftrag abbrechen“ auftritt, wurde behoben.
* CQ-4360747: Es wurde ein Problem behoben, bei dem wiederholbare Übersetzungsaufträge zu oft leere Payloads und Trigger erstellen.
* GRANITE-61318: Es wurde ein Problem behoben, bei dem der Assistent zur Seitenerstellung nur Pflichtfelder auf der Registerkarte „Allgemein“ hervorhebt.
* GRANITE-60514: Es wurde ein Problem behoben, bei dem geplante Veröffentlichungen während der Ausführung der Full-Stack-Pipeline angehalten wurden.
* GRANITE-61019: Problem mit GC beim ersten Ausführen nach einem Neustart von AEM beheben.
* GRANITE-60456: Problem behoben, das auftrat, wenn ein Administrator die Eigenschaftsseite eines Benutzers öffnet.
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

#### AEM Guides {#guides-23320}

* GUIDES-33597: Wenn ein leeres `prop` ohne Attribute oder Werte zu einer DITAVAL-Datei hinzugefügt wird, können keine zusätzlichen `prop` hinzugefügt werden.
* GUIDES-33693: Wenn Sie ein bearbeitetes Bild über die Experience Manager Guides-Benutzeroberfläche erneut hochladen, wird die ursprüngliche Ausgabedarstellung des Bildes aktualisiert, aber der zugehörige DITA-Inhalt zeigt weiterhin die vorherige Bildversion an.
* GUIDES-35607: Fehlerprotokolle, die beim Hochladen eines Assets über die Assets-Benutzeroberfläche oder beim Erstellen einer neuen Datei über die Editor-Benutzeroberfläche generiert werden, verwenden fälschlicherweise den Begriff `predecessor` anstatt in der Protokollmeldung `successor` zu verwenden.
* GUIDES-37649: Beim Veröffentlichen einer DITA-Zuordnung mit Baseline auf AEM Sites (mit veralteter Komponentenzuordnung) werden auch die Zuordnungselemente mit dem Attribut `processing-role = resource-only` veröffentlicht.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).


### Bekannte Probleme {#known-issues-23320}

* FORMS-22633: Formularübermittlungen können fehlschlagen, wenn benutzerdefinierter Code verwendet wird, der auf den GuideBridge-APIs (`getData` oder `getDataXML`) basiert. Wenn dieses Problem auftritt, wenden Sie sich bitte an den Adobe-Support.

### Eingestellte Funktionen und APIs {#deprecated-23320}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-23320}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion wurden 31 identifizierte Schwachstellen behoben, was für einen noch robusteren Systemschutz sorgt.

### Eingebettete Technologien {#embedded-tech-23320}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,88,0 | [Oak 1.88.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.88/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2,30,2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
