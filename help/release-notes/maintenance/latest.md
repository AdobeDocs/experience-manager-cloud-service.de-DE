---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a58225edb8ca49db9743db6c9c5b08c786fa0144
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 27%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 24464 {#release-24464}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 24464, die am Mittwoch, 17. Februar 2026 veröffentlicht wurde. Die vorherige Wartungsversion war Version 24288.

Die Funktionsaktivierung von 2026.2.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-24464}

* AEMARCH-264: Hinzufügen von Unterstützung für die Validierung bedingter Anfragen basierend auf RequestEntity.
* AEMARCH-269: Anzeigen von JavaEE-Validierungs-APIs für OpenAPI-Implementierungen.
* AEMARCH-276: Bereitstellen von i18n-Unterstützung über RequestEntity.
* ASSETS-10995: Legen Sie ein Limit für die Anzahl der Assets im Zip-Download fest.
* ASSETS-50788: Aktualisieren der Such-API zur Verwendung der Asset-Metadaten-GET-API.
* ASSETS-50946: Zuordnen des Anfragetexts mithilfe der Metadaten-GET-API zu JCR-Metadaten.
* ASSETS-55866: Senden Sie keine neue Anfrage für dasselbe Asset, bis die vorherige Verarbeitung abgeschlossen ist.
* ASSETS-60300: API zum Abrufen des asynchronen Auftragskontexts und -ergebnisses bereitstellen.
* ASSETS-60574: Unterstützung für die neueste Version des Sling-API-Bundles hinzufügen.
* ASSETS-61049: Fortsetzung der Entwicklung des Metadaten-Managers für Bundles.
* ASSETS-61692: Semantische Suche standardmäßig in der Open Search-API durchführen.
* ASSETS-61696: BAM-Route und MFE-Wrapper in der Asset-Ansicht.
* ASSETS-61854: Senden Sie die GenStudio-Lösung in einer Aktivierungs-/Deaktivierungsnachricht.
* ASSETS-61973: Erstellen Sie eine API in AEM zum Verwalten von Eingabeaufforderungen.
* ASSETS-62182: Asset Compute-Ereignishandler für die C2PA-Manifest-Ausgabedarstellung.
* ASSETS-62311: Probleme mit der Suchregression.
* ASSETS-62413: Unterstützung für customModifier-Felder in jeder Ebene in JSON hinzufügen.
* ASSETS-62432: API-PR zum Löschen von Mergeordnern.
* ASSETS-62540: Erhöhen Sie die für die Touch-optimierte Benutzeroberfläche in Schnellstart.
* ASSETS-62622: Verarbeiten Sie den Suchmodus in MatchQuery.
* ASSETS-62671: Korrigieren Sie den Operator MatchQuery startsWith .
* ASSETS-62780: Umschalten zwischen Funktionen für die Ordner-API.
* ASSETS-62988: Ausblenden der C2PA-Manifest-Ausgabedarstellung, sodass sie auf der Registerkarte „Ausgabedarstellungen“ angezeigt wird.
* ASSETS-63336: Die Vorlagensynchronisierung von AEM mit DM sollte nur für DAM-Metadaten mit Namespace erfolgen.
* ASSETS-63375: Asset-Upload-Experimentelle OpenAPIs hinter den Funktions-Umschalter stellen.
* ASSETS-63453: Stellen Sie sicher, dass alle Benutzer die Omnisearch-Konfiguration lesen können.
* GRANITE-63744: Erlaubt das Verbinden asynchroner Aufträge mit Sling-Aufträgen.
* GRANITE-64567: Automatische Deaktivierung der semantischen Suche nach SKU-Suchen.
* GUIDES-41187: Hinzufügen von Kopfzeilen für die Verwendung von Handbüchern.
* SITES-30452: Inhalts-API mit ASO - Vorschläge für Titel und Beschreibungen.
* SITES-33116: Pfadüberprüfung korrigieren.
* SITES-34234: Seiteneditor: Zustand der Inhaltsstruktur beibehalten.

### Behobene Probleme {#fixed-issues-24464}

* ASSETS-43198: E-Mails mit Benachrichtigungen zum Ablauf von Assets berücksichtigen nicht die Voreinstellungen der Benutzersprache.
* ASSETS-51840: Verbesserungen bei der Asset-Verarbeitung.
* ASSETS-52061: Nach Auswahl der gespeicherten Suche kann nicht zurück navigiert werden.
* ASSETS-53155: Asset-Inhaltsverbesserungen.
* ASSETS-53745: Für den Dynamic Media-Download muss die Auswahl des Original-Assets aufgehoben werden, bevor die Web-Vorgabe ausgewählt wird.
* ASSETS-54260: Asset-Inhaltskorrekturen.
* ASSETS-54787: Asset-Inhaltsverbesserungen.
* ASSETS-57391: Asset-Inhaltsaktualisierungen.
* ASSETS-59213: cq-dynamicmedia-core ist von der veralteten Bibliothek commons-lang abhängig.
* ASSETS-59214: Die CQ-Scene7-Bildbearbeitung hängt von der veralteten Bibliothek commons-lang ab.
* ASSETS-59546: cq-remotedam-client-core benötigt veraltete commons-lang-library.
* ASSETS-59703: cq-dam-core ist von der veralteten Bibliothek „commons-lang“ abhängig.
* ASSETS-59705: cq-dam-handler hängt von veralteter commons-lang-Bibliothek ab.
* ASSETS-59707: cq-dam-inDesign ist von der veralteten Bibliothek commons-lang abhängig.
* ASSETS-59709: cq-scene7-core ist von der veralteten Bibliothek commons-lang abhängig.
* ASSETS-59929: Der CSV-Export aus Metadaten funktioniert nicht, wenn das Feld ein Zeilenumbruchzeichen enthält.
* ASSETS-60241: Asynchroner Verschiebungsauftrag schlägt beim Umbenennen des Ordners fehl.
* ASSETS-61134: Entfernen Sie comparissionVersion-Tags aus POM-Dateien.
* ASSETS-61309: Interne Verweise werden durch Verschieben/Kopieren von Inhaltsfragmenten nicht mehr aktualisiert.
* ASSETS-61730: Umleitung zu „Direkter Binärzugriff“ sollte die Asset-Kodierung berücksichtigen.
* ASSETS-62358: Die CSV-Datei des Assets-Berichts enthält beschädigte Werte im Inhaltspfad.
* ASSETS-62610: Lizenzschaltfläche für Adobe Stock in der Benutzeroberfläche von Assets deaktiviert.
* ASSETS-62613: NPE in `downloadasset`/`saveas`.
* ASSETS-62656: Omnisearch-Datenanzeige wird für Nicht-Assets-KI-Suchen falsch angezeigt.
* GRANITE-55387: Das Korrigieren von in Anführungszeichen eingeschlossenen Wörtern löscht das gesamte Wort.
* GRANITE-61240: RCE über gespeicherte XSS in lazycontainer.js.
* GRANITE-64101: OOTB-Indizes, die in ES konvertiert wurden, wurden beim Neustart wieder auf Lucene zurückgesetzt.
* SITES-24530: Berührungsziel der Schließen/Entfernen-Schaltflächen im Suchmodal nicht groß genug.
* SITES-31425: Nicht lokalisierte Fehlermeldung im Workflow „Starten“.

### Bekannte Probleme {#known-issues-24464}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-24464}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-24464}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion wurden 14 identifizierte Schwachstellen behoben, was für einen noch robusteren Systemschutz sorgt.

### Eingebettete Technologien {#embedded-tech-24464}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,90,0 | [Oak 1.90.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2,30,4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |

