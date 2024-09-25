---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 22f8ffc3e3acec9846a2f868be48195ca62df88b
workflow-type: tm+mt
source-wordcount: '1343'
ht-degree: 17%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 17964 {#release-17964}

Im Folgenden finden Sie eine Zusammenfassung der kontinuierlichen Verbesserungen für die Wartungsversion 17964, die am Donnerstag, 25. September 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 17689.

Die Funktionsaktivierung von 2024.10.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-17964}

* ASSETS - 37750: [Priorität 4] [GraphQL] Unterstützung für DM scene7-URLs: Bild-Smart-Zuschnitte.
* CQ - 4354583: [AEMaaCS] Übersetzungsprozessereignisse über die Adobe-Pipeline senden.
* CQ - 4357642: Aktualisieren der MSFT-Anmeldeinformationen in OOTB Connector.
* CQ - 4358217: Deserialisieren Sie den Anfrageinhalt aus der Anfrageentität.
* CQ - 4358342: Registrieren Sie RequestProcessors für nur eine HTTP-Methode.
* FORMS - 10781: Erweitern Sie den Regeleditor, um Regeln für das nächste/vorherige Element in einem Bereich zu erstellen.
* FORMS - 14595: [Browserless Feature] Werte fehlen im DoR, wenn vorausgefüllte Daten zur Berechnung des DoR für Browser-loses Rendering verwendet werden.
* FORMS - 15619: AEM Forms - Aktualisiertes Übersetzungs-Kit
* FORMS - 16113: [Adobe Sign]Der Vertragsstatus kann von einem anderen Benutzer nicht aktualisiert werden.
* FORMS - 16155: [Regel-Editor] Async-Funktion implementieren.
* GRANITE - 53872: Fügen Sie neue env vars für die IMS-Client-ID hinzu.
* SITES - 23738: Release Core Components 2.27.0.
* SITES - 16610: Inhaltsfragmente: Rufen Sie den Endpunkt Startdetails ab.
* SITES - 16614: Inhaltsfragmente: Rebase Launch-Endpunkt.
* SITES - 16615: Inhaltsfragmente: Launch-Endpunkt bewerben.
* SITES - 24215: Inhaltsfragmente: Implementieren Sie den Endpunkt Get Launch sources .
* SITES - 20336: Inhaltsfragmente: Verbesserung der Validierung beim Löschen eines Inhaltsfragmentmodells.
* SITES - 21090: Inhaltsfragmente: Unterstützung für Mindest-/Höchstwerte in Bruchteilen für Zahlenfelder hinzugefügt
* SITES - 21658: Inhaltsfragmente: Upgrade zur Verwendung von UUID-Referenzen.
* SITES - 23054: Inhaltsfragmente: Inhaltsfragmentmodelle kopieren.
* SITES - 23264: Inhaltsfragmente: Erstellen Sie ein statisches Schema eines Modells.
* SITES - 23265: Inhaltsfragmente: Zeigen Sie das statische Schema eines Modells über den GET-Endpunkt des Benutzeroberflächenschemas an.
* SITES - 23266: Inhaltsfragmente: Möglichkeit, Inhaltsfragmentmodellen Einschränkungen hinzuzufügen.
* SITES - 23778: Inhaltsfragmente: Inhaltsfragmentmodelle für die Suche sollten die Suche nach Modellen ermöglichen, die noch nie veröffentlicht wurden.
* SITES - 23335: Inhaltsfragmente: Unterstützung für externe Asset-Referenzen hinzugefügt.
* SITES - 24626: Content Fragments: RTC: Permissions for UUID migration: 2.
* SITES - 24786: Inhaltsfragmente: Verbesserungen für den Endpunkt `referencesTree`.
* SITES - 24833: Inhaltsfragmente: Entfernen Sie die Überprüfung der HTML-Eingabe anhand einer Liste zulässiger HTML-Tags.
* SITES - 23380: GraphQL: Verwenden Sie eine geeignete API, um Asset-Metadaten zu lesen.
* SITES - 22864: [Edge Delivery] Universal Editor mit neuer AEM Inhaltsstrukturintegration H2 2024.
* SITES - 23584: Foundation-Komponententests schlagen in Java 17 fehl.
* SITES - 23662: Eventing: Benutzer, der eine Veröffentlichungsanforderung Trigger, kann nicht aus JCR-Protokollanweisungen in Serverprotokollen extrahiert werden.
* SITES - 23301: Unterstützung für den Start eines neuen Workflows zur Erstellung von Ordnerstrukturen bei der Erstellung von Übersetzungen von Inhaltsfragmenten hinzugefügt.
* SITES - 23336: Inhaltsfragmente: Unterstützung für externe Asset-Referenzen hinzufügen
* SITES - 24091: MSM-Inhaltspaket-Aufspaltung: Master.
* SITES - 24114: isSourceRenderCondition: Reduzieren Sie die Fehlerprotokollmeldung auf DEBUG.
* SITES - 24166: Remote-Asset-Schadensbegrenzung für den Touch-UI-Editor.
* SITES - 24409: Registrieren Sie alle Anforderungsprozessoren nur auf einer HTTP-Methode.
* SITES - 25008: Verbessern der Handhabung von PersistenceExceptions- und Berechtigungsproblemen.
* SITES - 24821: [Xwalk] Legen Sie als Standard aem.page / aem.live fest.

### Behobene Probleme {#fixed-issues-17964}

* CQ - 4356887: Inkonsistenz beim Übersetzungsstatus für Akamai Technologies Inc.
* CQ - 4357878: Das Übersetzungs-Framework legt bei der Übersetzung von Fehlern beim Anbieter keinen Fehlerstatus fest.
* CQ - 4358028: Projekt konnte nicht erstellt werden, wenn Miniaturansichten hochgeladen wurden.
* CQ - 4358290: Die Target-Einstellung funktioniert nicht auf der veröffentlichten Seite.
* FORMS - 13173: Fehlausrichtung der Dropdown-Liste im adaptiven Formular > Regeleditor > Objekt ablegen.
* FORMS - 13873: AFv2: (&quot;-&quot;) im Komponentennamen führt zu einem Fehler bei den Regeln.
* FORMS - 14340: Fehler bei der Instanziierung von FormsAndDocumentOmniSearchHandler und CloudStorageSubmitActionInserter.
* FORMS - 15363: Anzeigename im Regeleditor.
* FORMS - 15381: Benutzeroberflächenverbesserung der Nachricht zum Autorisierungsumfang .
* FORMS - 15595: Problem mit AEM Formular-TnC-Komponente Einverständnistext-Zeilenumbruch.
* FORMS - 15623: AEMaaCS Forms - Alternativen zum Aktualisieren mehrerer Tabellen in Dynamics mit einer POST.
* FORMS - 15682: AEM Forms - DOR kann nicht an Dynamics FDM gebunden werden.
* FORMS - 15799: Adobe Sign GovCloud-Signaturseite gibt keine Wiedergabe in iFrame an.
* FORMS - 15835: Problem mit URL-Neuschreibungen nach der Übermittlung.
* FORMS - 16091: Verwendung der umstrukturierten Binary.java.
* FORMS - 16096: Forms-Benutzer hat keinen Zugriff auf das Dialogfeld &quot;restendpoint&quot;.
* FORMS - 16139: Hinzufügen der erforderlichen Protokollierung für DoR in Form von Kernkomponenten.
* FORMS - 6935: Status der aktiven Komponente weist kein Kontrastverhältnis zwischen 3 und 1 auf.
* FORMS - 7018: Leeres Element wird ausgewählt.
* GRANITE - 53028: NPE in ExternalProcessPollingHandler.
* GRANITE - 53907: Dienstbenutzer können nicht als Workflow-Superuser identifiziert werden.
* SITES - 24405: Inhaltsfragmente: Erweiterte Informationen für Auflistungen sollten zuverlässiger sein
* SITES - 23024: Inhaltsfragmente: Die Auflistung gibt nicht gesperrt zurück: &quot;true&quot;in GET-Fragmenten.
* SITES - 23269: Inhaltsfragmente: Das Erstellen von Inhaltsfragmenten ermöglicht das Festlegen gesperrter Felder.
* SITES - 23337: Inhaltsfragmente: Batch-Endpunkt mit `body` schlägt mit der Casting-Ausnahme fehl.
* SITES - 23474: Inhaltsfragmente: Bei der Paginierung sollten fehlerhafte Ressourcen in Suchinhaltsfragmenten ausgeschlossen werden.
* SITES - 23615: Inhaltsfragmente: Inhaltsfragmentkopie AuthoringInfo wird nicht aktualisiert
* SITES - 23668: Inhaltsfragmente: Patch-Live Copy mit Multifield schlägt mit 400 fehl
* SITES - 23695: Inhaltsfragmente: Registerkartenbeschreibung ist in UiSchema nicht verfügbar
* SITES - 23704: Inhaltsfragmente: Auflistungen mit mehreren Werten werden in _extendedInfo nicht unterstützt
* SITES - 23781: Inhaltsfragmente: Duplizierte Werte sind in Auflistungsfeldern nicht zulässig
* SITES - 24150: Inhaltsfragmente: Inhaltsfragmentversionen Es fehlen Authoring-Daten zur Erstellung
* SITES - 24230: Inhaltsfragmente: Korrigieren Sie die Filterung nach dem Replikationsstatus `modified` in den Suchinhaltsfragmentmodellen
* SITES - 24233: Inhaltsfragmente: Das Filtern nach `publishedBy` kann nicht veröffentlichte Ressourcen in Suchinhaltsfragmentmodellen einschließen
* SITES - 24355: Inhaltsfragmente: Die Live-Beziehung wird für von Ordnern erstellte Inhaltsfragmente nicht berücksichtigt
* SITES - 24816: Inhaltsfragmente: ValidationStatus -Nachrichten sind inkonsistent.
* SITES - 23896: Eventing: More Events (Eventing): More Events (Veranstaltungen) werden mit einem Page Moved-Ereignis zusammengefügt
* SITES - 23899: Eventing: Seitenereignisse werden verzögert oder gar nicht generiert
* SITES - 23961: Eventing: Das Erstellen von Inhaltsfragmentmodellen mit Verweisen schlägt fehl, wenn der Konfigurationsordner vorhanden ist
* SITES - 23963: Eventing: Ereignissen, die die Seite gelöscht haben, kommen manchmal nicht mehr vor
* SITES - 23443: GraphQL: GraphQL Cursor Query Inkonsistentes Verhalten.
* SITES - 10994: Die Tastaturfokussierung ist nicht logisch.
* SITES - 16357: AEM: Die Schaltfläche ist auf der Registerkarte &quot;Setup Analytics&quot;im Menü &quot;Sites&quot;abgeschnitten.
* SITES - 19836: Die Ghost-Komponente im Container wird in Veröffentlichungs- und Vorschauinstanzen angezeigt.
* SITES - 22348: Die Seite &quot;Live Copy-Übersicht&quot;kann nicht geladen werden, wenn sie über 100 Live Copies für ein Projekt sind.
* SITES - 22960: Nicht geschlossener Ressourcen-Resolver in ContentFragmentModelOmniSearchHandler.
* SITES - 23284: URL-Codierung, die ein leeres Pfadbrowser-Dialogfeld verursacht.
* SITES - 23505: Komponenten zeigen falsche URLs an, wenn die Seite an einen anderen Ort verschoben wird.
* SITES - 23574: Kann für viele Seiten keine Vorschau anzeigen/mit aktuellen Versionen vergleichen
* SITES - 23585: Problem mit der Wiederherstellung der Vererbung für Komponenten mit cq:responsive Knoten
* SITES - 23650: Diskrepanz bei der Anzahl der eingehenden Links in AEM Autorenumgebung
* SITES - 23659: Content Language Servlet-Regression, verursacht durch den Umschalter FT_* SITES - 9757
* SITES - 23759: Assets, die zu Experience Fragment hinzugefügt wurde, wird nicht mit Launches veröffentlicht
* SITES - 24025: 302 Weiterleitungen in AEM zurückgegebenen Location-Header mit internem DNS anstelle des öffentlichen DNS
* SITES - 24036: Untersuchung erforderlich für AEM RTE-Beständige Zeichen im ASCII-Format
* SITES - 24317: Proxy Configuration not working with Basic Authentication
* SITES - 24918: [Xwalk] behebt 504-Fehler, die gelegentlich bei Verwendung der dedizierten IP-Ausdrücke zurückgegeben wurden.

### Bekannte Probleme {#known-issues-17964}

* FORMS - 15818: Component descriptor entry `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` not found -Anweisungen in Serverprotokollen. Dies sind harmlose Protokollanweisungen.

### Eingestellte Funktionen und APIs {#deprecated-17964}

Beachten Sie, dass wir gerade dabei sind, `com.day.cq.wcm.api` zu aktualisieren. Mit der aktuellen Version haben wir einige der Methoden und Klassen als `@Deprecated` markiert. Diese werden in zukünftigen Versionen entfernt. Daher sollten Sie erwägen, zu den vorgeschlagenen Alternativen zu wechseln, wenn Sie eine davon verwenden.

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-17964}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Dieses Maintenance Release behebt 16 identifizierte Schwachstellen und stärkt unser Engagement für einen robusten Systemschutz.

### Eingebettete Technologien {#embedded-tech-17964}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.68.0 | [Oak-API 1.68.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2,27,0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
