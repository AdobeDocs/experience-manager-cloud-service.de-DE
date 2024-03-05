---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 77a4b445d9117959ed8855aef445c02529178800
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 12%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 15262 {#release-15262}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 15262, die am Mittwoch, 5. März 2024 veröffentlicht wurde. Das vorherige Wartungsversion war Version 14697.

2024.3.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de).

### Verbesserungen {#enhancements-15262}

* ASSETS-30632: Es wurde eine separate Brand Portal-Spalte zum Veröffentlichungsstatus in der Listenansicht hinzugefügt.
* ASSETS-30934: Unterstützung für `Iptc4xmpCore:AltTextAccessibility` und `Iptc4xmpCore:ExtDescrAccessibility` Eigenschaften zum Asset-Metadaten-Editor.
* ASSETS-31297: Verbessern Sie die Prüfungen, um das Löschen kopierter Assets aus dynamischen Medien zu verhindern.
* ASSETS-33246: Definition des Release-Index `damAssetLucene-10`.
* ASSETS-33590: Unterstützung für Webwiedergaben für Videos in Verarbeitungsprofilen hinzugefügt.
* GRANITE-36205: Oak-Version auf 1.60-T20240131102219-0cde853 aktualisieren.
* SITES-19326: Aktualisieren Sie die Links in der Assets-Benutzeroberfläche, um das Inhaltsfragment in dem neuen CF-Editor zu öffnen.
* GUIDES-12945: KI-gestützte intelligente Vorschläge zum Hinzufügen von Inhaltsverweisen beim Erstellen von Inhalten
* GUIDES-12706: Überarbeitete Versionsverlaufsfunktion im Web-Editor
* GUIDES-14948: Verbessertes Benutzererlebnis im Übersetzungsbereich
* GUIDES-8782: Verbesserte Suchlogik im Dialogfeld &quot;Element einfügen&quot;
* GUIDES-14681: Möglichkeit, mehrere Ausgabevorgaben mit dynamischen Grundlinien zu veröffentlichen
* Eine vollständige Liste der Verbesserungen in AEM Handbüchern finden Sie unter : [Neue Funktionen in AEM Handbüchern](https://experienceleague.adobe.com/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2402-release/whats-new-2024-2-0.html?lang=en#release-info)

### Behobene Probleme {#fixed-issues-15262}

* ASSETS-15977: Entfernt veraltete Suchereignisse der Version 1 und Pipeline-Hersteller.
* ASSETS-18088: Aktualisierung der Abhängigkeiten der Batik-Bibliothek auf Version 1.17.
* ASSETS-21965: Der Workflow für Metadaten-Writeback darf nur bei Änderungen an Asset-Metadaten gestartet werden.
* ASSETS-26368: Geplante Massen-Importvorgänge werden nicht entfernt, wenn die Auftragskonfiguration nicht vorhanden ist.
* ASSETS-26549: Assets/Knoten mit &quot;jcr:lastModifiedBy&quot;: &quot;workflow-process-service&quot; werden in der Listenansicht als &quot;externer Benutzer&quot;angezeigt.
* ASSETS-26842: Aktualisieren Sie den Text &quot;Firefly&quot;, um &quot;App Builder&quot;im Verarbeitungsprofil zu lesen.
* ASSETS-28708: Sehr langsame Antwort für einige IMS-Token-Anfragen.
* ASSETS-28767: Inkonsistenter Veröffentlichungsstatus für Assets, wenn Ordner große Anzahl an Assets enthalten. der veröffentlichten Assets.
* ASSETS-29011: Smartes Zuschneiden ist für schreibgeschützte Benutzer sichtbar.
* ASSETS-29348: AssetMoveEventHandler kann zu viel Speicher verbrauchen.
* ASSETS-29738: Die Einschränkungen beim Hochladen von Assets scheitern bei NullPointerException für WFF-Dateien.
* ASSETS-30068: Grundlagen des Massenimports von Assets, um den Status COMPLETED_WITH_ERROR für &quot;Auftrag abgeschlossen, aber mit Fehler&quot;einzuschließen.
* ASSETS-30261: Falsche imsUserId, die für Asset-Ereignisse an die Pipeline gesendet werden.
* ASSETS-30538: Option &quot;Seite anzeigen&quot;fehlt nach dem Verschieben einer PDF-Datei.
* ASSETS-30626: Fehlende Erstellung von Versandanfragen für Assets mit leerer assetId.
* ASSETS-30756: Die Aktion &quot;Assistent für das Verschieben von Assets&quot;schlägt fehl, wenn der Ordnername auf &quot;html&quot;endet.
* ASSETS-30810: Tags vor dem Rendern der alten YouTube-Konfiguration bereinigen.
* ASSETS-31015: Assets mit der Dateinamenerweiterung .msg können nicht hochgeladen werden.
* ASSETS-31038: Aufgabenereignisse, die beim Benachrichtigungsdienst empfangen werden, werden nicht verarbeitet.
* ASSETS-31097: Deaktivieren Sie die asynchrone Kopie für WCM-Inhalt, um traversale Abfragewarnungen zu vermeiden.
* ASSETS-31256: Assets/Knoten mit &quot;jcr:lastModifiedBy&quot;: &quot;workflow-process-service&quot; werden in der Listenansicht als &quot;externer Benutzer&quot;angezeigt.
* ASSETS-31260: Das Dropdown-Feld für Asset-Metadaten-Formulare funktioniert nicht ordnungsgemäß, wenn die Dropdown-JSON-Datei eine große Liste enthält.
* ASSETS-31280: Assets werden beim Hinzufügen zu einer Sammlung in einer reduzierten Struktur heruntergeladen.
* ASSETS-31301: `dynamicmedia_sly.js` kann nicht korrekt von der Anwendungs-API instanziiert werden.
* ASSETS-31330: ko_KR: Nicht lokalisierte Zeichenfolgen in Untertiteln und Audiospuren.
* ASSETS-31405: Die InDesign-Serververarbeitung schlägt bei großen InDesign-Layouts fehl.
* ASSETS-31570: Unified Shell - Asset-Details &quot;Speichern und schließen&quot;, &quot;Abbrechen&quot;-Schaltflächen müssen mehrmals gedrückt werden, um zu funktionieren.
* ASSETS-31673: Massenimport bei großen Dropbox-Dateien fehlgeschlagen.
* ASSETS-32108: AEM Assets speichert benutzerdefinierte Kartengrößen nicht in den Anzeigeeinstellungen.
* ASSETS-32230: Aktualisieren Sie die minimale Laufzeitversion des com.adobe.aem.repoapi-Bundles.
* ASSETS-32544: Metadaten-Exportauftrag schlägt gelegentlich fehl.
* ASSETS-32679: Zwischenspeicherungsprobleme mit Asset-Vorschau (PDF).
* ASSETS-32754: Aufgaben können nicht Benutzern zugewiesen werden, die sich zuvor nicht angemeldet haben.
* ASSETS-32755: Konfigurieren Sie das Auftragsthema com/adobe/cq/dam/assetmove , um eine geordnete Warteschlange zu verwenden.
* ASSETS-32899: Die Suche in Sammlungen ist extrem langsam.
* ASSETS-33098: AEM Assets-Suchfacetten &quot;Tag-Eigenschaft&quot;funktionieren nicht erwartungsgemäß.
* ASSETS-33454: Aktivität &quot;Prüfungsaufgabe&quot;und Kommentare werden nicht in der Zeitleiste angezeigt.
* ASSETS-34088: PDF-Vorschau funktioniert nicht auf AEM Assets.
* ASSETS-34155: Dynamic Media - Aktualisierte AEM Viewer / 2024.1.0.
* ASSETS-34684: Umgang mit mehreren Werten dc:title in der Inhaltsstruktur.
* ASSETS-34789: Behebung von Normalisierungsproblemen bei der Prüfung von Dateinamenkonflikten.
* DXML-13276: AEM Guides - Integrieren von Indizes in GraniteContent und Entfernen dieser aus der Bibliothek.
* GRANITE-47995: Löschvorgänge können aufgrund von Konflikten mit der Eigenschaft &quot;cq:isDelivered&quot;fehlschlagen.
* GRANITE-48079: Aktivieren Sie POST-Anfragen für die OAuth-Validierung von Online-Token.
* GRANITE-48143: Upgrade von org.apache.sling.resourcemerger auf 1.4.4 .
* GRANITE-49031: Update auf Jackson 2.16.1.
* SCRNS-3961: Screens - Sequenzkanal: Die in der Überblendung &quot;Ausblenden&quot;verwendete Jquery-Animation führt zu schwarzem Bildschirm.
* SITES-15868: Verbessern der Leistung für die Auflistung von Fragmenten.
* SITES-16079: `/fragments/{id}/references` begann, Duplikate zurückzugeben.
* SITES-16118: Wenn ein Fragment gepatcht wird und ein Fragmentfeld im Modell fehlt, wird eine Ausnahme ausgelöst.
* SITES-16121: Beim Abrufen eines Modelldatumsfelds wird eine Ausnahme ausgelöst.
* SITES-16207: Der Vorgang &quot;POST /adobe/sites/cf/models&quot;gibt zwei verschiedene OK-Statuscodes zurück.
* SITES-17361: Einbetten von Jsoup in das Site-Headless-Bundle erneut.
* SITES-17768: GraphQL gibt die Dynamic Media-URL für Assets aus, auf die in Inhaltsfragmenten verwiesen wird.
* SKYOPS-66622: Absturz der Autorenbereitstellung nach Ausführung einer BuildTransform-aktivierten Pipeline.
* SKYOPS-69977: Adaptives Bildservlet lädt das Bild nach der letzten Aktualisierung nicht.
* GUIDES-15045: Rechtschreibprüfung im Editor lässt keine Auswahl von Vorschlägen zu.
* GUIDES-14968: Die globale Navigationsschaltfläche funktioniert nicht und das Dashboard wird nicht geladen.
* GUIDES-14943: Beim nativen PDF-Publishing funktionieren benutzerdefinierte Attribute innerhalb von Bedingungsvorgaben nicht für das native PDF-Publishing.
* GUIDES-15085: Bei der nativen PDF-Veröffentlichung werden Schlüsselverweise für die Adobe Experience Manager-Guides vom Dezember 2023 nicht aufgelöst.
* GUIDES-13486: **Baseline-Filter** -Dateien funktionieren nicht mit dem Dateinamen im Web-Editor.
* Eine vollständige Liste der in AEM Handbüchern behobenen Probleme finden Sie unter : [Behobene Probleme mit AEM Guides](https://experienceleague.adobe.com/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2402-release/fixed-issues-2024-2-0.html?lang=en#release-info)

### Bekannte Probleme {#known-issues-15262}

Keine

### Änderungshinweis {#change-notice-15262}

**Erforderliche Aktion**

Künftige Änderungen erfordern die Bibliothek [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) in Ihren benutzerdefinierten Funktionstests verwendet werden, um auf mindestens eine Version zu aktualisieren **1.2.1**

Stellen Sie sicher, dass Ihre Abhängigkeit in `it.tests/pom.xml` wurde aktualisiert.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

Diese Änderung ist nach dem 6. April 2024 erforderlich.

Wenn die Abhängigkeitsbibliothek nicht aktualisiert wird, treten Pipeline-Fehler beim Schritt &quot;Benutzerdefinierte Funktionstests&quot;auf.

### Eingebettete Technologien {#embedded-tech-15262}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.60-T20240131102219-0cde853 | [Oak API 1.60.0-API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
