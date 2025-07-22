---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a4e023ca44c93124627912bae08dc3535d48400c
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 34%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 21644 {#21644}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 21644, die am Mittwoch, 22. Juli 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 21570.

Die Funktionsaktivierung von 2025.7.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-21644}

* ASSETS-39377: Verbessern Sie die Handhabung von 429s über Remote-Speicher im Assets Bulk Importer.
* ASSETS-46026: Konfigurierbare maximale Tiefe für Metadaten-Exporter.
* ASSETS-49172: Assets von Dynamic Media-Vorlagen sollten Metadaten vom Ordner erben.
* ASSETS-50209: Unterstützung für Teilzeichenfolgen in DM-Vorlagen.
* ASSETS-52326: Seite mit der AEM Assets-Konfiguration, auf der die Voreinstellungen für die Titelanzeige für Assets festgelegt werden.
* ASSETS-52805: CSV-Ausgabe-/Download-Unterstützung für Massenvorgänge hinzufügen.
* ASSETS-52873: Fügen Sie eine neue Konfiguration in den Ordnereigenschaften hinzu, um die KI-Verarbeitung für diesen Ordner zu deaktivieren.
* ASSETS-53535: Verbesserte Leistung beim Hochladen von YouTube-Videos.
* ASSETS-53612: Steuerung für die Hybridsuche in Assets Omnisearch.
* GRANITE-60183: Aktualisieren der commons-fileupload-Abhängigkeit auf 1.6.0.
* GRANITE-60287: QS auf Jackrabbit 2.22.1 aktualisieren.
* SITES-30452: Inhalts-API mit ASO - Vorschläge für Titel und Beschreibung.
* SITES-31677: Benutzerdefinierter Arbeitsbereich unterstützt den Export von AEM-Inhaltsfragmenten zu Target.
* SKYOPS-112741: Entfernen Sie das `com.adobe.granite.product.support` aus der AEM-CS SDK.

### Behobene Probleme {#fixed-issues-21644}

* ASSETS-12882: Probleme mit der Ausrichtung der Benutzeroberfläche nach dem Öffnen von Viewer-Vorgaben.
* ASSETS-48958: Problem mit dem Ändern des Veröffentlichungsstatus bei der Asset-Synchronisierung in der lokalen Sites-AEM.
* ASSETS-50856: `dam:processingAttempts` beim CompleteUpload nicht zurückgesetzt.
* ASSETS-51604: CSV-Datei des Linkfreigabeberichts enthält keine „shared with“-Daten.
* ASSETS-51783: Fallback zur DM-Konfiguration unter `/conf/global`, wenn mithilfe der Suchabfrage keine Konfiguration gefunden wird.
* ASSETS-51857: Elemente der Asset-Tabelle können nicht neu angeordnet werden.
* ASSETS-52169: Die neue Ausgabedarstellung des BAT-Computers ist fälschlicherweise in Asset-Downloads enthalten.
* ASSETS-52229: Fehlende Posteingangsbenachrichtigungen für Asset-Berichte in AEM as a Cloud Service.
* ASSETS-52399: Versionsfehler in com.day.cq.dam.api kann den Kundencode beschädigen.
* ASSETS-52780: Asset kann zur Vorschau markiert werden, auch ohne dass die Option aktiviert ist.
* ASSETS-52866: Migrierte DM-Videos verbleiben im Verarbeitungsstatus unter dem Ordner mit deaktivierter DM-Synchronisierung.
* ASSETS-53237: Dropdown-Liste „Farbprofil“ im Bildvorgabeneditor ist leer.
* ASSETS-53240: Asset-Bericht - Beim Abrufen der Größe der Asset-Ausgabedarstellung von Dynamic Media schlägt die Festplattenauslastung fehl.
* ASSETS-53446: Zeitweise auftretende Fehler bei der Aktualisierung des YouTube-Authentifizierungstokens aufgrund von NPE.
* ASSETS-53827: Die ACL-Validierung blockiert das Speichern von gemischten Mediensets.
* ASSETS-5403: Dynamic Media-Client-Bibliotheken, die in der Veröffentlichungsinstanz verwendet werden, sollten über `allowProxy=true` verfügen.
* ASSETS-54261: Beim Metadaten-Import treten Verbindungslecks auf, die blockiert werden, wenn die Datei nicht heruntergeladen werden kann.
* CQ-4359863: Die Tag-Suche funktioniert nicht ordnungsgemäß, wenn Schlüsselwörter im Inhaltsfragment-Editor/Asset-Editor nicht korrekt geordnet sind.
* CQ-4359958: Machen Sie die OpenAPI-Unterstützung mit AEM 6.5.22.0 und höher kompatibel.
* CQ-4360256: Fügen Sie den Servlet-Kontextpfad in den Anfragepfad für HTTP-Anfragen ein, die über den `/adobe` Servlet-Kontext verarbeitet werden.
* CQ-4360317: Fügen Sie eine Methode zum Festlegen der Kopfzeile für das Ablaufdatum hinzu, wenn Sie Antworten erstellen.
* GRANITE-60311: AEM SDK QuickStart - NPE zu „OSGi Installer Configuration Printer“.
* GS-15285: Benutzer werden als deaktiviert angezeigt.

### Bekannte Probleme {#known-issues-21644}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-21644}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-21644}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt vier identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-21644}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.80.0 | [Oak-API 1.80.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP-Server | 2.4.63 | [Apache httpd 2.4.63](https://github.com/apache/httpd/blob/2.4.63/CHANGES) |
| AEM-Kernkomponenten | 2.29.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
