---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 3be366e5fa0a7625203a052426be6a2fd2412cf6
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 100%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 16145 {#release-16145}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 16145, die am 1. Mai 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 15977.

2024.5.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-16145}

* ASSETS-23489: Verbesserungen bei Repository-Einblicken.
* ASSETS-26926: Verbesserungen bei der Dynamic Media-Upload-Analyse.
* ASSETS-30351: Mit dem Dialogfeld „Herunterladen“ können Dynamic Media-Ausgabedarstellungsgrößen asynchron geladen werden.
* ASSETS-30379: Verbesserte Auflösung von DRM-Lizenzen beim Download.
* ASSETS-31058: Ausgabedarstellungen für smartes Zuschneiden in AEM Assets-Benutzeroberfläche auf der Registerkarte „Ausgabedarstellungen“ und Generieren von Bildern mit smartem Zuschneiden, wenn auf diese Ausgabedarstellungen geklickt wird.
* ASSETS-31218: Unterstützung für benanntes smartes Zuschneiden in der Asset-Bereitstellungs-API hinzugefügt.
* ASSETS-31979: Hinzufügen von visuellen Indikatoren und Deaktivieren der benutzeroberflächenspezifischen Funktionen während Async-Assets-Vorgängen.
* ASSETS-32735: Verbesserungen für Ereignisse zur Aktualisierung von Asset-Metadaten.
* ASSETS-34661: API für DM-Vorschau- und/oder Bereitstellungs-URLs aus der AEMaaCS-Veröffentlichung.
* ASSETS-37259: Verbesserungen bei der XMP-Analyse.
* ASSETS-37263: Zulassen der Löschung fehlgeschlagener asynchroner Assets-Aufträge.
* CNTBF-114: Verbesserungen des Inhaltsrückflusses.
* CNTBF-148: Verbesserungen des Inhaltsrückflusses.
* CQ-4356992: Neueste AEM und Granite-Übersetzungen.
* SITES-19326: Update der Links in der Assets-Benutzeroberfläche, um CF im neuen CF-Editor zu öffnen.
* SITES-20686: GraphQL – Verfügbarmachung von Dynamic Media-URL über _dmS7Url (für Nicht-Bild-Assets).
* SKYOPS-68091: Aktualisierung auf Java 11.0.20.

### Behobene Probleme {#fixed-issues-16145}

* ASSETS-32321: Die Auflösung des Nachbearbeitungs-Workflows schlägt fehl, wenn im Vorgängerordner der Unterknoten „jcr:content“ fehlt.
* ASSETS-33856: JPEG-Bildvorgabe lädt die Datei als TXT-Datei herunter.
* ASSETS-34096: Fehlerbehebung der Ansicht des Download-Berichts für Touch-Benutzeroberfläche.
* ASSETS-34493: Fehler beim Laden des Download-Dialogfelds, nachdem das Umschalten zwischen Funktionen für mehrere Unternehmen aktiviert wurde.
* ASSETS-34824: URL kopieren wird für DM-deaktivierte Ordner leer angezeigt.
* ASSETS-35226: Nachbearbeitungs-Workflow wird nicht aufgelöst, wenn im DAM-Stamm angegeben.
* ASSETS-35559: Reduzierung des Fehlerprotokolls beim DM-Batch-Upload auf WARN.
* ASSETS-35860: Falsche Zeitzonenkonvertierung in der AEM Assets-Spaltenansicht.
* ASSETS-35935: Falsche Ordnernavigation nach dem Schließen der Payload-Überprüfung.
* ASSETS-35961: Die Schaltfläche „Zuschneiden hinzufügen“ funktioniert unter dem Bildprofil nicht.
* ASSETS-36227: Der FolderPreviewUpdaterImpl-Service wird bei der Veröffentlichung deaktiviert.
* ASSETS-36943: Fehlerhafte Spalten, wenn CF- und andere Nicht-CF-Elemente in einem Ordner in der Listenansicht vorhanden sind.
* ASSETS-36990: Exportierte Metadatenaufträge schlagen bei einer großen Anzahl von Eigenschaften fehl oder sind langsam.
* ASSETS-37113: Auftrag zur erneuten Verarbeitung von Assets wird sofort beendet, wenn die Abfrage nur CF-Ergebnisse zurückgibt.
* ASSETS-37260: Metadatenexport in AEM kann eine ungültige CSV-Datei erzeugen.
* ASSETS-37261: PPTx- und PDF-Anmerkungsproblem in AEM Assets.
* ASSETS-37282: Potenzielle langsame Anfrage zum Öffnen großer Ordner.
* ASSETS-37330: Massenimport von OneDrive erstellt falsche AEM Ordnerstruktur.
* ASSETS-37609: Entfernen des alten „scene7 conf lookup“.
* ASSETS-38016: Einige Metadaten-Aktualisierungen werden in Ereignissen nicht ordnungsgemäß verfolgt.
* CQ-4357161: Payload-Bildschirm im AEM-Posteingang gibt 404 zurück.
* GRANITE-50041: Ausgabedarstellung hinzufügen funktioniert nicht, wenn die Auflösung größer als 1.440 Pixel Breite ist und wenn nur die Option „Ausgabedarstellung hinzufügen“ in der Dropdown-Option enthalten ist.
* GRANITE-50279: Ungeordnete Wochennamen in der Coral Datepicker-Komponente.
* SCRNS-3949: Die Anforderungszeit für den Abruf des Screens-Kanals ist zu lang.
* SCRNS-3981: [Sequenzkanal] Es wurde ein schwarzer Bildschirm angezeigt, wenn die Sequenz der Elemente beim Laden/Entladen verzerrt war.
* SCRNS-4180: [Sequenzkanal] Die Sequenz wird bei Kanälen mit Videos mit einer Dauer von -1 bei Wiederherstellung aus der Fallback-Miniaturansicht angehalten.
* SCRNS-4245: [Sequenzkanal] Eingeschränkte Dauer des leeren Bildschirms beim Laden eines Videos und Umschalten von der Fallback-Miniaturansicht aus.
* SITES-16055: Korrigieren von Live Copy und Live Copy-Quell-Links auf der entsprechenden Eigenschaftsseite.
* SCRNS-4243: Fehlende Schaltflächen im Inhaltsanbieter für Benutzende ohne Administratorrechte.

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
