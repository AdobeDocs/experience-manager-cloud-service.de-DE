---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 3686697c85273ccc13e80b8d7f4ad1ff3c79845d
workflow-type: ht
source-wordcount: '632'
ht-degree: 100%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 21706 {#21706}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 21706, die am 24. Juli 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 21570.

>[!NOTE]
>
>Version 21644 wurde als privat eingestuft und durch Version 21706 ersetzt.

Die Funktionsaktivierung von 2025.7.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-21706}

* ASSETS-39377: Bessere Verarbeitung von 429s über Remote-Speicher im Assets-Massenimport-Tool.
* ASSETS-46026: Konfigurierbare maximale Tiefe für Metadaten-Export-Tool.
* ASSETS-49172: Assets in Dynamic Media-Vorlagen sollten Metadaten aus Ordner erben.
* ASSETS-50209: Unterstützung für Teilzeichenfolgen in DM-Vorlagen.
* ASSETS-52326: Seite mit der AEM Assets-Konfiguration zum Festlegen von Voreinstellungen für die Titelanzeige für Assets.
* ASSETS-52805: Neue CSV-Ausgabe-/Download-Unterstützung für Massenvorgänge.
* ASSETS-52873: Neue Konfiguration in den Ordnereigenschaften, um die KI-Verarbeitung für diesen Ordner zu deaktivieren.
* ASSETS-53535: Bessere Leistung beim Hochladen von YouTube-Videos.
* ASSETS-53612: Steuerung für die Hybridsuche in Assets Omnisearch.
* GRANITE-60183: Aktualisierung der commons-io-Abhängigkeit auf 1.6.0.
* GRANITE-60287: Aktualisierung von QS auf Jackrabbit 2.22.1.
* SITES-30452: Inhalts-API mit ASO – Vorschläge für Titel und Beschreibung.
* SITES-31677: Benutzerdefinierter Arbeitsbereich unterstützt den Export von AEM-Inhaltsfragmenten in Target.
* SKYOPS-112741: Entfernen des Pakets `com.adobe.granite.product.support` aus dem AEM-CS-SDK.

### Behobene Probleme {#fixed-issues-21706}

* ASSETS-12882: Probleme mit der Ausrichtung der Benutzeroberfläche nach dem Öffnen von Viewer-Vorgaben.
* ASSETS-48958: Problem beim Ändern des Veröffentlichungsstatus durch die Asset-Synchronisierung im lokalen Sites-AEM.
* ASSETS-50856: `dam:processingAttempts` beim completeUpload nicht zurückgesetzt.
* ASSETS-51604: CSV-Datei des Link-Freigabeberichts enthält keine „Shared With“-Daten.
* ASSETS-51783: Fallback zur DM-Konfiguration unter `/conf/global`, wenn mit der Suchabfrage keine Konfiguration gefunden wird.
* ASSETS-51857: Elemente der Asset-Tabelle können nicht neu angeordnet werden.
* ASSETS-52169: Die neue Ausgabedarstellung des BAT-Computers ist fälschlicherweise in Asset-Downloads enthalten.
* ASSETS-52229: Fehlende Posteingangsbenachrichtigungen für Asset-Berichte in AEM as a Cloud Service.
* ASSETS-52399: Versionsfehler in com.day.cq.dam.api kann den Kunden-Code beschädigen.
* ASSETS-52780: Asset kann zur Vorschau markiert werden, selbst wenn die Option nicht aktiviert ist.
* ASSETS-52866: Migrierte DM-Videos verbleiben im Verarbeitungsstatus unter dem Ordner mit deaktivierter DM-Synchronisierung.
* ASSETS-53237: Dropdown-Liste „Farbprofil“ im Bildvorgaben-Editor ist leer.
* ASSETS-53240: Asset-Bericht „Festplattenauslastung“ schlägt beim Abrufen der Größe der Asset-Ausgabedarstellung von Dynamic Media fehl.
* ASSETS-53446: Zeitweise auftretende Fehler bei der Aktualisierung des YouTube-Authentifizierungs-Tokens aufgrund von NPE.
* ASSETS-53827: Die ACL-Validierung blockiert das Speichern von gemischten Medien-Sets.
* ASSETS-5403: Dynamic Media-Client-Bibliotheken, die in der Veröffentlichungsinstanz verwendet werden, sollten über `allowProxy=true` verfügen.
* ASSETS-54261: Beim Metadaten-Import treten Verbindungslecks auf und der Import wird blockiert, wenn die Datei nicht heruntergeladen werden kann.
* CQ-4359863: Die Tag-Suche funktioniert nicht ordnungsgemäß, wenn Keywords im Inhaltsfragment-Editor/Asset-Editor nicht die korrekte Reihenfolge haben.
* CQ-4359958: OpenAPI-Unterstützung kompatibel mit AEM 6.5.22.0 und höher.
* CQ-4360256: Einfügen des Servlet-Kontextpfads in den Anfragepfad für HTTP-Anfragen, die über den `/adobe`-Servlet-Kontext verarbeitet werden.
* CQ-4360317: Neue Methode zum Festlegen der Kopfzeile für das Ablaufdatum beim Erstellen von Antworten.
* GRANITE-60311: AEM SDK QuickStart - NPE bei „OSGi Installer Configuration Printer“.
* GS-15285: Benutzende werden als deaktiviert angezeigt.

### Bekannte Probleme {#known-issues-21706}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-21706}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-21706}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt vier identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-21706}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.80.0 | [Oak-API 1.80.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.63 | [Apache Httpd 2.4.63](https://github.com/apache/httpd/blob/2.4.63/CHANGES) |
| AEM-Kernkomponenten | 2.29.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
