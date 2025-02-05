---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 77d8ebeaa3914f4a91d2cf27ccc5b048e64d6b38
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 22%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 19352 {#19352}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 19352, die am Donnerstag, 5. Februar 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 19149.

Die Funktionsaktivierung von 2025.2.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-19352}

* FORMS-13998: Akkordeon-Komponente hinzufügen.
* FORMS-17913: Kartenvariante für Optionsfeldgruppe hinzufügen.
* FORMS-17333: Aktivieren von HTML-E-Mail-Vorlagen bei der Übermittlung von AEM-Formularen.
* FORMS-17702: Aktivieren Sie die in Ausgabesynchronisierungs-APIs generierten PDF-Dateien, um sie in den Azure Blob-Speicher hochzuladen.
* SITES-28282: Edge Delivery mit universellem Editor: Geben Sie Basispfad, Site-Name und Organisation als Seiteninformationen für eine beliebige Seite an.
* SITES-27055: Edge Delivery mit universellem Editor: Unterstützen Sie Abfrageparameter im Reverse-Proxy-Servlet.
* SITES-26796: Edge Delivery mit universellem Editor: Unterstützt benutzerdefinierte Spalten für die Taxonomie-Tabelle.
* SITES-26087: Edge Delivery mit universellem Editor: Unterstützt den CSV-Export für Tabellen.
* SITES-26265: Edge Delivery mit universellem Editor: Zeigt das TA-Konto zur Integration mit Edge Delivery in der Konfigurations-Benutzeroberfläche an.
* SITES-20372: Edge Delivery mit universellem Editor: Aktivieren einfacher MSM-Anwendungsfälle für Tabellen.
* SITES-26681: Edge Delivery mit universellem Editor: Unterstützt den Parameter ?sheet= für die Taxonomie-Arbeitsblätter in der Autoreninstanz.
* SITES-26479: [Schema] Status der geplanten Veröffentlichung des Inhaltsfragmentmodells.
* SITES-25944: [Live Copy-Übersicht] Fügen Sie den Status „Live Copy aktuell mit begrenzter Vererbung“ hinzu.
* SITES-28713: [V2] Hinzufügen von strukturierter Datenunterstützung zum Content Scraper.
* SITES-27896: CommentsTab wird automatisch bei Benachrichtigungen geöffnet.
* SITES-26720: Es sollte nicht zulässig sein, eine ganze Sammlung aus dem Asset-Wähler auszuwählen.
* SITES-27875: Beliebige bearbeitbare Elemente in einem Container können standardmäßig verschoben werden.
* SITES-28340: Dark Alley Universal Editor Service Plugin.
* SITES-26098: Möglichkeit, die Veröffentlichung referenzierter Seiten beim Veröffentlichen eines Inhaltsfragments zu vermeiden.
* SITES-27789: Unterstützung der data-aue-component des Datenattributs im DOM.
* SITES-25997: Verbessern von Varianten zur Unterstützung des geänderten Datums.
* SITES-28023: GraphQL-Ausgabe für Remote-Asset-Referenzen (Repository + Asset-ID).
* SITES-26058: Status-Endpunkt des geplanten Inhaltsfragmentmodells.
* SITES-25108: Modellmigration für UUID-Referenzen.
* SITES-26630: Status-Endpunkt der geplanten Veröffentlichung von Inhaltsfragmenten für mehrere Inhaltsfragmente.
* SITES-23432: Verbesserte Funktion zum Löschen von Verweisen.
* SITES-25797: Unterstützung für externe Asset-Verweise - GraphQL.
* SITES-17514: Endpunktverbesserung zum Rückgängigmachen der Veröffentlichung des Inhaltsfragments.
* SITES-14633: Validieren des Inhaltsfragmentmodells Erstellen Sie Payloads vor der Installation - Probelauf.

### Behobene Probleme {#fixed-issues-19352}

* SITES-28415: Edge Delivery mit universellem Editor: Korrigieren Sie die Schaltfläche Offene Eigenschaften für Tabellen.
* SITES-26669: Edge Delivery mit universellem Editor: Beheben von Problemen beim Hochladen von CSV-Dateien, die in UTF-8 mit einer STL als Tabelle kodiert sind.
* SITES-26543: Edge Delivery mit universellem Editor: Korrigieren Sie leere Blöcke, ohne dass ein Modell falsches Markup rendert.
* SITES-26857: Edge Delivery mit universellem Editor: Korrigieren Sie das Authentifizierungstoken der Site, das in der Benutzeroberfläche für dateibasierte Konfigurationen angezeigt wird.
* SITES-26662: Edge Delivery mit universellem Editor: Beheben von Problemen mit Massendaten, bei denen Groß- und Kleinschreibung berücksichtigt wird.
* SITES-28133: Wenn Publish eine „Vorschau“ anzeigt, sind die Inhalte in der Produktionsumgebung verfügbar.
* SITES-27187: Geplante Seiten-/Asset-Aktivierung einschließlich (experimenteller) Verweise, die nicht veröffentlicht werden können.
* SITES-27264: 2 Selenium-Tests im Zusammenhang mit der Erstellung von Inhaltsfragmenten und Live Copies schlagen auf der primären Instanz konsequent fehl.
* SITES-26559: Pin der Abfrage für Inhaltsfragmentmodelle an den cqPageLucene-Index.
* SITES-24469: Auf interaktive Elemente kann nicht über die Tastatur zugegriffen werden.
* SITES-24518: Die Schaltflächen Name und Modell in der übergeordneten Referenztabelle können nicht über die Tastatur aufgerufen werden.
* SITES-27937: UISchema-Einschränkungen werden nach der Aktualisierung des Modells auf null gesetzt.
* SITES-27852: Im Modell-UISchema fehlen Kategorisierungen.
* SITES-27904: MetadataSchema fehlt in der Liste/Suche von Inhaltsfragmentmodellen für die vollständige Projektion.
* SITES-26827: Die Auflistung von Fragmenten endet in einer Endlosschleife.
* SITES-27678: [Performance] Verhindern Sie das unnötige Abrufen von _references.
* SITES-27589: UUID-Upgrade-Fehler für Inhaltsfragmentmodelle mit mehreren Inhalts-/Fragmentverweisfeldern.
* SITES-26679: Beim Rückgängigmachen der Veröffentlichung von Inhaltsfragmentmodellen sollten nur veröffentlichte Verweise überprüft werden.
* SITES-26666: referencesTree- und references-Endpunkt werden mit unterschiedlichen Ergebnissen zurückgegeben.
* SITES-26499: Falsche Reihenfolge des Tag-Feldwerts in GET-Fragment(en) &amp; PATCH.
* SITES-26585: Korrigieren Sie den Fehler „Kleine Beschreibung“ im Schema.
* SITES-26647: Die Referenzvalidierung „Endpunkt löschen“ und „Veröffentlichung aufheben“ kann für Benutzende ohne Administratorrechte fehlschlagen.
* SITES-26458: [Inhaltsfragmentmodell durchsuchen] Filtern nach Replikationsstatus korrigieren.
* SITES-23513: [Inhaltsfragmentmodell-Editor] Die Validierung für die Eigenschaft „Fragmentverweis“ - „Zulässiges Inhaltsfragmentmodell“ schlägt fehl.
* SITES-26575: Wenn Sie die Veröffentlichung eines Fragments in der Vorschau rückgängig machen, sollte der previewStatus aktualisiert werden.
* SITES-26571: Seitenverweise können nicht gespeichert werden, wenn FT_SITES-12435 aktiviert ist.
* SITES-26660: Der Vergleich der Inhaltsfragmentversion ist möglicherweise fehlerhaft, wenn @ContentType vom Typ „Zeichenfolge“ ist.
* SITES-26626: Fehlende customErrorMessage in Zahlen- und booleschen Feldern.
* SITES-26268: Fehlerhafter Status-Code wird zurückgegeben, wenn ein Verweis beim Erstellen eines Fragments ungültig ist.

### Bekannte Probleme {#known-issues-19352}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-19352}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-19352}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 36 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-19352}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.72.0 | [Oak-API 1.72.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.27.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
