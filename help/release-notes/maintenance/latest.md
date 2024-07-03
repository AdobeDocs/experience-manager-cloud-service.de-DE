---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9303ecadea38d83bd71ed0d440067bae5c419940
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 20%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 16971 {#release-16971}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 16971, die am Donnerstag, 3. Juli 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 16799.

Die Funktionsaktivierung in 2024.7.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-16971}

* SITES-22948: Entfernen Sie Commerce-Referenzen in Foundation-Inhalten für AEM CS.
* SITES-22141: [Inhaltsfragmente] SegmentNotFoundException von CFM ModelChangeRepositoryImpl nach OnRC.
* SITES-21893: Problem mit dem Zuschneiden von Bildern in der Autoreninstanz.
* SITES-21788: [Inhaltsfragmente] Zeigen Sie NOTE im CF- und CF-Modell-Editor an, wenn uiSchema für das Modell aktiviert ist.
* SITES-21688: MSM-Rollout aktualisiert den Pfad von Experience Fragment (XF) auf Live Copy-Seiten nicht.
* SITES-21659: Gibt den vollständigen Namen des Benutzers zurück, der eine Modell-Ressource erstellt/ändert/repliziert.
* SITES-21609: OpenAPI-Endpunkt zum Migrieren von Inhaltsfragmenten von einem Modell zum anderen.
* SITES-21598: [API öffnen] Erstellen von CFM: Gibt einen Fehler zurück, wenn der angegebene Konfigurationspfad nicht vorhanden ist.
* SITES-21491: [API öffnen] Der CF-PATCH-Endpunkt sollte Live-Beziehungen auf Feldebene berücksichtigen.
* SITES-21434: [API öffnen] Der CF-GET-Endpunkt sollte Live-Beziehungen auf Feldebene berücksichtigen.
* SITES-21415: CF-Editor - unterstützt UUID-Referenzen.
* SITES-21326: [API öffnen] Geben Sie Informationen zum Vorhandensein von Verweisen für ein Inhaltsfragment an.
* SITES-21310: [API öffnen] Fügen Sie die ID des Inhaltsfragments in der Antwort der Übersetzungs-API hinzu.
* SITES-20859: CF Open API - Rückgabeverweise beim Abrufen eines Fragments nach Pfad.
* SITES-20687: [API öffnen] Endpunkt zum Abrufen des Batch-Verarbeitungsstatus.
* SITES-20657: [API öffnen] Stellen Sie eine Option für das gesamte match-Wort bereit, wenn Sie eine Zeichenfolge mit `FindAndReplace` -Endpunkt.
* SITES-20587: [API öffnen] Erstellen `COPY` -Endpunkt für Inhaltsfragmente.
* SITES-20584: [API öffnen] Optimieren Sie das Abrufen von Verweisen.
* SITES-20308: [API öffnen] Aktivieren Sie die Stapelverarbeitung in der API.
* SITES-19976: [API öffnen] Generisches Benutzeroberflächenschema für bedingte Felder.
* SITES-19556 [Inhaltsfragmente] Aktualisieren Sie uiSchema , wenn es beim Bearbeiten des Modells vorhanden ist.
* SITES-18056: [API öffnen] Schließen Sie beim Veröffentlichen eines Inhaltsfragments in der Vorschau Verweise ein.
* SITES-16898: [Schema] OpenAPI-Endpunkt zum Migrieren von Inhaltsfragmenten von einem Modell zum anderen.
* SITES-16609: Endpunkt &quot;Listenstarts&quot;.
* SITES-16606: Launch-Endpunkt erstellen.
* SITES-21617: [Xwalk] Machen Sie Seiteneigenschaften/Metadaten innerhalb der EU bearbeitbar.
* SITES-19614: [Xwalk] Seitenumbruch im Tabelleneditor und unendlicher Bildlauf.
* SITES-22163: [Xwalk] Verbesserte Unterstützung für Inhalte, die von der Veröffentlichungsstufe für Edge Delivery Sites bereitgestellt werden.
* SITES-22109: [Xwalk] Verbesserte Handhabung der Nachbearbeitung von Rich-Text-Markups.
* SITES-2035: [Xwalk] Verbesserte Handhabung von MSM und Launches.
* SITES-21839: [Xwalk] Verbesserte Pfadzuordnung und Bereinigung für nicht von Edge Delivery bereitgestellte Inhalte.

### Behobene Probleme {#fixed-issues-16971}

* CQ-4356898: [Übersetzung] OutOfMemory-Fehler für CF, der eine ungewöhnlich große Anzahl von Links enthält.
* CQ-4357055 [Übersetzung] Automatische Übersetzung funktioniert nicht mit der Rest-API.
* CQ-4353931: [Übersetzung] Fügen Sie jcr:uuid in der Übersetzungsquellenseite/xf/asset hinzu, wenn es fehlt.
* CQ-4357591: [Übersetzung] Ändern Sie den Workflow &quot;JCR:UUID verknüpfen&quot;, damit er für Seiten/XF funktioniert.
* FORMS-14844: Adaptive Forms ermöglicht die Übermittlung von Formularen trotz fehlerhafter reCAPTCHA-Überprüfung.
* FORMS-14984: Forms mit CAPTCHA überspringt die Validierung, wenn &quot;submitMetaData&quot;in den gesendeten Daten fehlt.
* FORMS-14477: Die Optionen &quot;Is After&quot;und &quot;Is Before&quot;im Regeleditor funktionieren bei der Datumsauswahl-Validierung nicht mehr.
* FORMS-14019: Die Funktion &quot;Dienst aufrufen&quot;des Regeleditors funktioniert nicht im universellen Editor.
* FORMS-14336: Wenn kein Formularfeld ausgewählt ist, sollte der Editor mit dem Fokus auf das gesamte Formularelement geöffnet werden.
* FORMS-15061: Der Laderenkreis bleibt bei Verwendung der Dienstoption im Regeleditor unbegrenzt bestehen.
* SITES-22457: Wenn Sie einen Launch bewerben, der nicht tief ist, wird der Quellinhalt nicht aktualisiert.
* SITES-22748: [Inhaltsfragmente] Verbesserte Fehlerbehebung für den Auftrag zum Aktualisieren von Inhaltsfragmenten
* SITES-22349 [Inhaltsfragmente] ContentType für leere mehrzeilige cf-Elemente kann nicht geändert werden.
* SITES-22343 [Inhaltsfragmente] Der Semantik-Typ &quot;Aufzählung&quot;ist fehlerhaft.
* SITES-22194: Nach dem Festlegen der Umleitung funktioniert model.json nicht mehr.
* SITES-21953: [API öffnen] Das Tag wird basierend auf der Reihenfolge des validationStatus geändert.
* SITES-21894: [API öffnen] Verbessern der Validierung des übergeordneten Pfads beim Erstellen von CFs.
* SITES-21887: [API öffnen] Ungültiges ETag, das vom Endpunkt POST Variations zurückgegeben wird.
* SITES-21657: [API öffnen] Verbessern Sie die Validierung für die Eigenschaft &quot;CF Search Path&quot;.
* SITES-21949: Ungültige Cursor-APIs für Suche-APIs geben 500 zurück.
* SITES-20927: Such-APIs geben einen 500-Wert zurück, wenn die Abfrage fehlt.
* SITES-20544 [API öffnen] Ändern Sie die Generierung von Veröffentlichungspaketnamen, um Oak-Konflikte zu vermeiden.
* SITES-19710: CVE-2022-47937 - Entfernen Sie alle Verwendungen von org.apache.sling.commons.json aus dem Seiteneditor.
* SITES-11992 [Zugänglichkeit] Auswahlschaltfläche für Anmerkungsmuster fehlt ein zugänglicher Name.
* SITES-10979: [Zugänglichkeit] Die Bezeichnung ist nicht persistent.
* SITES-10962: [Zugänglichkeit] Schaltfläche: Schaltfläche hat keine Rolle.
* SITES-10905: [Zugänglichkeit] Der Status der aktiven Komponente weist kein Kontrastverhältnis zwischen 3 und 1 auf.
* SITES-2974:  [Zugänglichkeit] - Horizontaler Bildlauf mit 320 px Breite.
* SITES-22026: Experience Fragments können in AEM nicht zwischen Ordnern verschoben werden
* SITES-22106: Problem mit Sprachwechsel-Funktionen im neuen Inhaltsfragment-Editor
* SITES-21980: Inkonsistente Handhabung für UUID-basierte Referenztypen.
* SITES-7257: NPE in ThumbnailServlet.

### Bekannte Probleme {#known-issues-16971}

Keine

### Änderungshinweis {#change-notice-16971}

* AEM as a Cloud Service deaktiviert ab September 2024 die Serialisierung von Ressourcen-Konfliktlösern über das Sling Model Exporter-Framework. Weitere Informationen finden Sie in der [Dokumentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md).

### Eingestellte Funktionen und APIs {#deprecated-16971}

Informationen zu veralteten oder entfernten Elementen in AEM as a Cloud Service finden Sie unter [Eingestellte und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md).

### Eingebettete Technologien {#embedded-tech-16971}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.64.0 | [Oak-API 1.64.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| AEM SLING-API | 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.25.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
