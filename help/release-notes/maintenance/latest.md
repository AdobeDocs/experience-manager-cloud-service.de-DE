---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 79dcf8a4e9834beeb466ed9270a3f5c6aa67aa9a
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 29%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 16145 {#release-16145}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 16145, die am Donnerstag, 1. Mai 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 15977.

2024.4.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-16145}

* ASSETS-23489: Verbesserungen bei Repository-Einblicken.
* ASSETS-26926: Verbesserungen bei der Dynamic Media-Upload-Analyse.
* ASSETS-30351: Das Dialogfeld &quot;Herunterladen&quot;sollte Dynamic Media-Ausgabedarstellungsgrößen asynchron laden.
* ASSETS-30379: Verbesserte Auflösung von DRM-Lizenzen beim Download.
* ASSETS-31058: Ausgabedarstellungen für smartes Zuschneiden in AEM Assets-Benutzeroberfläche auf der Registerkarte &quot;Ausgabedarstellungen&quot;und generieren Bilder mit smartem Zuschnitt, wenn der Benutzer auf diese Ausgabedarstellungen klickt.
* ASSETS-31218: Unterstützung für benannten smartcrop in der Asset-Bereitstellungs-API hinzugefügt.
* ASSETS-31979: Fügen Sie visuelle Indikatoren hinzu und deaktivieren Sie UI-Funktionen während der Vorgänge Async Assets.
* ASSETS-32735: Ereignisse zur Aktualisierung von Asset-Metadaten.
* ASSETS-34661: API für DM-Vorschau- und/oder Bereitstellungs-URLs aus der AEMaaCS-Veröffentlichung.
* ASSETS-37259: XMP Verbesserungen bei der Analyse.
* ASSETS-37263: Zulassen der Löschung fehlgeschlagener asynchroner Assets-Aufträge.
* CNTBF-114: Verbesserungen des Inhalts-Rückflusses.
* CNTBF-148: Verbesserungen des Inhalts-Rückflusses.
* CQ-4356992: Neueste AEM und Granite-Übersetzungen.
* SITES-19326: Update der Links in der Assets-Benutzeroberfläche, um CF im neuen CF-Editor zu öffnen.
* SITES-20686: GraphQL - Dynamic Media-URL über _dmS7Url verfügbar machen (für Nicht-Bild-Assets).
* SKYOPS-68091: Aktualisierung auf Java 11.0.20.

### Behobene Probleme {#fixed-issues-16145}

* ASSETS-32321: Die Auflösung des Nachbearbeitungs-Workflows schlägt fehl, wenn im Vorgängerordner der Unterknoten &quot;jcr:content&quot;fehlt.
* ASSETS-33856: JPEG Image Preset lädt die Datei als TXT herunter.
* ASSETS-34096: Fehlerbehebung der Touch-optimierten UI-Ansicht für asynchronen Download-Bericht.
* ASSETS-34493: Fehler beim Laden des Download-Dialogfelds, nachdem ein Umschalten zwischen Funktionen für mehrere Unternehmen aktiviert wurde.
* ASSETS-34824: URL kopieren wird für DM-deaktivierte Ordner leer angezeigt.
* ASSETS-35226: Nachbearbeitungs-Workflow nicht aufgelöst, wenn im DAM-Stamm angegeben.
* ASSETS-35559: Verringern Sie das Fehlerprotokoll beim DM-Batch-Upload auf WARN.
* ASSETS-35860: Falsche Zeitzonenkonvertierung in der AEM Assets-Spaltenansicht.
* ASSETS-35935: Falsche Ordnernavigation nach dem Schließen der Payload-Überprüfung.
* ASSETS-35961: Die Schaltfläche &quot;Zuschneiden hinzufügen&quot;funktioniert unter dem Bildprofil nicht.
* ASSETS-36227: Deaktiviert den FolderPreviewUpdaterImpl-Dienst bei der Veröffentlichung.
* ASSETS-36943: Fehlerhafte Spalten, wenn CF- und andere Nicht-CF-Elemente in einem Ordner in der Listenansicht vorhanden sind.
* ASSETS-36990: Exportierte Metadatenaufträge schlagen bei einer großen Anzahl von Eigenschaften fehl oder sind langsam.
* ASSETS-37113: Auftrag zur erneuten Verarbeitung von Assets wird sofort beendet, wenn die Abfrage nur CF-Ergebnisse zurückgibt.
* ASSETS-37260: Metadatenexport in AEM kann ungültige CSV-Datei erzeugen.
* ASSETS-37261: PPTx- und PDF-Anmerkungsproblem in AEM Assets.
* ASSETS-37282: Potenzielle langsame Anfrage zum Öffnen großer Ordner.
* ASSETS-37330: Massen-Import von OneDrive erstellt falsche AEM Ordnerstruktur.
* ASSETS-37609: Entfernen Sie die alte &quot;scene7 conf lookup&quot;.
* ASSETS-38016: Einige Metadaten-Aktualisierungen werden in Ereignissen nicht ordnungsgemäß verfolgt.
* CQ-4357161: AEM Posteingang-Payload-Bildschirm gibt 404 zurück.
* GRANITE-50041: Ausgabedarstellung hinzufügen funktioniert nicht, wenn die Auflösung größer als 1440 Pixel Breite ist, wenn nur die Option &quot;Ausgabedarstellung hinzufügen&quot;in der Dropdown-Option enthalten ist.
* GRANITE-50279: Ungeordnete Wochennamen in der Coral Datepicker-Komponente.
* SCRNS-3949: Die Anforderungszeit für den Abruf des Screens-Kanals ist zu lang.
* SCRNS-3981: [Sequenzkanal] Der schwarze Bildschirm wurde angezeigt, wenn die Reihenfolge der Elemente beim Laden/Entladen verzerrt war.
* SCRNS-4180: [Sequenzkanal] Die Sequenz wird bei Kanälen mit Videos mit einer Dauer von -1 bei Wiederherstellung aus der Fallback-Miniaturansicht angehalten.
* SCRNS-4245: [Sequenzkanal] Eingeschränkte Dauer des leeren Bildschirms beim Laden eines Videos und Umschalten von der Fallback-Miniaturansicht aus.
* SITES-16055: Korrigieren Sie Live Copy- und Live Copy-Quelllinks auf der entsprechenden Eigenschaftsseite.
* SCRNS-4243: Fehlende Schaltflächen im Content Provider für Benutzer ohne Administratorrechte.

### Bekannte Probleme {#known-issues-16145}

Keine

### Eingestellte Funktionen und APIs {#deprecated-16145}

* [Einstellung der JWT-Anmeldedaten in Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

* Ab dem 1. Mai 2024 wird Adobe Dynamic Media die Unterstützung für Folgendes einstellen:

   * SSL (Secure Socket Layer) 2.0
   * SSL 3.0
   * TLS (Transport Layer Security) 1.0 und 1.1
   * Die folgenden schwachen Verschlüsselungsverfahren in TLS 1.2:
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_RSA_WITH_AES_256_GCM_SHA384`
      * `TLS_RSA_WITH_AES_256_CBC_SHA256`
      * `TLS_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_AES_128_GCM_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
      * `TLS_RSA_WITH_SDES_EDE_CBC_SHA`


Informationen zu veralteten oder entfernten Elementen in AEM as a Cloud Service finden Sie unter [Eingestellte und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md).

### Eingebettete Technologien {#embedded-tech-16145}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.62.0 | [Oak-API 1.62.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| AEM SLING-API | 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.20–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.24.6 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
