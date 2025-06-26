---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 467e21aff1c2164be729598d03f30f6a9e90c8aa
workflow-type: tm+mt
source-wordcount: '1758'
ht-degree: 11%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 21331 {#21331}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 21331, die am Mittwoch, 24. Juni 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 21193.

Die Funktionsaktivierung von 2025.7.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-21331}

* CQ-4356522: `WorkflowResourceStatusProvider`.
* FORMS-16458: Benutzeroberfläche zum Auswählen der Schriftarteigenschaften (Schriftart).
* FORMS-17707: AEP-Connector funktioniert nicht für AEP Platform-Staging.
* FORMS-19125: Unterstützt die automatische Fragmentzuordnung im AF-Editor.
* FORMS-19336: Suche in Data Source Tree im AF-Editor hinzugefügt.
* FORMS-19417: Unterstützung von Optionsschaltflächen in der Hierarchieansicht.
* FORMS-19603: Unterstützung von Musterseite und Designseite sowohl im Regeleditor.
* SITES-5358: Inhaltsfragment-REST-API: Kopieren von Inhaltsfragmenten mit untergeordneten Elementen.
* SITES-10575: „MSM Blueprint Bloomfilter Loader“ versucht, mehr als 100000 Zeilen zu laden.
* SITES-14542: Beim Umbenennen/Verschieben einer Live Copy-Quellseite sollte der Trigger die umbenannte/verschobene Live Copy-Seite veröffentlichen, falls diese zuvor veröffentlicht wurde.
* SITES-19754: Edge Delivery mit universellem Editor: Fügen Sie eine für Menschen lesbare Fehlermeldung hinzu, wenn die Integration Probleme aufweist.
* SITES-23499: Edge Delivery mit universellem Editor: Unterstützung für mehrere Felder hinzufügen, die für Blockoptionen verwendet werden sollen.
* SITES-23518: Edge Delivery mit universellem Editor: Hinzufügen von Unterstützung für Edge Delivery-spezifische Asset-Ausgabedarstellungen.
* SITES-24436: Inhaltsfragmente-REST-API: Einführung eines lokalen Caches, um das Abrufen doppelter Verweise zu beschleunigen.
* SITES-25155: Inhaltsfragmente-REST-API: Veraltete Abfrageparameter „enabledForFolder“ in der Modellliste entfernen.
* SITES-25913: Inhaltsfragment-REST-API: Zeitgesteuerte Validierung von Ressourcen vor dem Start des Veröffentlichungs-Workflows.
* SITES-25976: Links in Experience Fragments werden nach dem MSM-Rollout nicht angepasst.
* SITES-26271: Inhaltsfragment-REST-API: Wechseln Sie zum BFS-Durchlauf für den Endpunkt &quot;GET-Variante“.
* SITES-27486: Universeller Editor - AEM-Integration.
* SITES-27775: Optimierte Referenzsuche während der Veröffentlichung (verzögertes Laden von Metadaten).
* SITES-27782: Edge Delivery mit universellem Editor: Hinzufügen einer bestimmten Publisher-Abonnenten-Implementierung, um Inhalte in Edge Delivery zu veröffentlichen (früher Zugriff).
* SITES-27792: Edge Delivery mit universellem Editor: Hinzufügen einer dedizierten Edge Delivery-Service-Konfigurationsvorlage.
* SITES-28557: Inhaltsfragment-REST-API: Zulassen, dass E-Tags verwendet werden, die durch den Aufruf von `/cf/fragments/{fragmentId}` mit `references=direct` abgerufen wurden, um ein Inhaltsfragment zu patchen.
* SITES-28683: Lassen Sie zu, dass MSM LiveRelationship-Suchen den erweiterten Status überspringen.
* SITES-29601: Inhaltsfragment-REST-API: Validierung für Inhaltsfragmentverweise in Langtextfeldern.
* SITES-29614: Inhaltsfragment-REST-API: Rufen Sie einen Workflow mithilfe des `/cf/workflows/{workflowInstanceId}`-Endpunkts ab, wobei „workflowInstanceIda“ die von der Veröffentlichungsanfrage zurückgegebene ID ist.
* SITES-29615: Inhaltsfragment-REST-API: Listet alle Batch-Anfragen auf, die über POST-`/cf/batch` mithilfe von `GET /cf/batch` erstellt wurden.
* SITES-29874: Inhaltsfragmente-REST-API: Verweise aus Langtextfeldern von Inhaltsfragmenten werden jetzt abgerufen und hydriert.
* SITES-29930: Inhaltsfragment-REST-API: Metriken für den Workflow zum Veröffentlichen von Inhaltsfragmenten hinzufügen.
* SITES-29986: Inhaltsfragment-REST-API: unterstützt die technische Benennung des CF-Modells.
* SITES-30088: Inhaltsfragment-REST-API: CF-Veröffentlichung - Abruf von Verweisen überspringen, wenn filterReferencesByStatus leer ist.
* SITES-30126: Inhaltsfragmente-REST-API: CF Leistungsverbesserung der Veröffentlichung: Überprüfung, ob eine Ressource ein Fragment ist, durch eine minimale Überprüfung ersetzt.
* SITES-30328: Edge Delivery mit universellem Editor: Hinzufügen von Unterstützung für die Vorschau von Sidekick.
* SITES-30445: Inhaltsfragmente-REST-API: Schema der CF-Modell-Benutzeroberfläche: Fügen Sie eine Option hinzu, um den Anfangsstatus von „reduzierbar“ zu steuern.
* SITES-30604: Inhaltsfragmente-REST-API: unterstützt die Übernahme von Modell-Metadatenschemata in der neuen Benutzeroberfläche.
* SITES-30885: Optimierte JSON-Verarbeitung in persistierten Abfragen.
* SITES-30886: Inhaltsfragment-REST-API: GET-Workflows für den Endpunkt „Inhaltsfragment“, die auf in Workflow-Metadaten gespeicherten Fragment-UUIDs basieren.
* SITES-31005: Die Benutzeroberfläche für Rollout-Aufträge wurde verbessert, um den Fortschritt anzuzeigen.
* SITES-31020: Verbesserte Benutzeroberfläche für das Erstellen von Live Copy-Aufträgen, um den Fortschritt anzuzeigen.
* SITES-31111: Inhaltsfragment-REST-API: Zulassen, dass die Varianten-Patch-API Inhaltsfragmentverweise innerhalb von Inhaltsfragment-Launches akzeptiert.
* SITES-31343: Inhaltsfragment-REST-API: Hinzufügen von Filterung und Paginierung nach Datum zum Endpunkt, der Batch-Anfragen auflistet.
* SITES-31472: Das Löschen von Launch kann dazu führen, dass das Repository angehalten wird, wenn der Launch massiv ist.
* SITES-31641: Inhaltsfragmente-REST-API: Eigenschaft zu Modellfeldern hinzufügen, um dynamische Zuordnungen zu Erweiterungen zu speichern.
* SITES-31677: Benutzerdefinierter Arbeitsbereich unterstützt den Export von AEM-Inhaltsfragmenten nach Target.
* SITES-31770: Inhaltsfragment-REST-API: Leistungsverbesserungen bei PATCH.
* SITES-31782: Inhaltsfragment-REST-API: Fügen Sie eine Beschreibung für lokale Assets hinzu.
* SITES-32175: Erlauben Sie mittlere Commits für die Live Copy-Erstellung und den MSM-Seiten-Rollout.

### Behobene Probleme {#fixed-issues-21331}

* CQ-4359756: Übersetzungsregeln umfassen jetzt Filtereigenschaften auf Komponentenebene.
* CQ-4359826: Löst einen inkonsistenten Status im Bedienfeld Inhaltsfragmentreferenz auf.
* CQ-4359866: Die LanguageUtils-Klasse unterstützt jetzt Komponententests, ohne zusätzliche Abhängigkeiten hinzuzufügen.
* FORMS-13990: Forms-Service-APIs: Dokumenterstellung : Datenfeld, das leer gelassen wird, nachdem es ausgewählt wurde, gibt 200 zurück, wenn erwartet wird, dass 400 ist.
* FORMS-14309: Forms Service-APIs : Extrahieren Sie Daten als Antwort-Code-Berichtigung.
* FORMS-18526: Wenn eine Regel mit mehreren Feldern in Bedingungen kopiert wird, ändert sich das feste Feld nicht.
* FORMS-18977: Der DOR-Service übergibt den Titel des Dokuments nicht.
* FORMS-19047: Übersetzungen fehlen nach der Veröffentlichung eines adaptiven Formulars auf AEM Forms auf SP22.
* FORMS-19234: Zeitleisten-Funktion von PDFs in AEM Forms kann nicht verwendet werden.
* FORMS-19628: Blendet im automatisch generierten DOR beim Ausschließen verschachtelter Bereichstitel auch den Stammbereichstitel aus.
* FORMS-19651: Regel korrigieren, wenn eine angeklickte Schaltfläche in einer binären Bedingung verwendet wird und dieselbe Schaltfläche auch in der Then-Anweisung verwendet wird.
* FORMS-19808: FormsPortal - Entwürfe können nicht abgerufen werden, wenn verzögertes Laden aktiviert ist.
* FORMS-19887: Die Zugriffseigenschaft funktioniert in der HTML5-Vorschau nicht.
* SITES-15452: Eindeutige CF-Elemente sollten beim Launch nicht mit ihren Kopien verglichen werden.
* SITES-24492: ARIA-Tablist hat keinen barrierefreien Namen.
* SITES-24623: Inhaltsfragment-REST-API: Beheben von E-Tag-Abweichungen zwischen Endpunkten für dieselbe CF.
* SITES-24668: Die Funktion „Verweise“ der Leiste funktioniert nicht mehr, wenn der Zoom auf 400 % erhöht wird.
* SITES-24678: Die Statusmeldung Verweise auf die Leiste wird von der Bildschirmlesehilfe nicht angekündigt.
* SITES-24697: Der Ladestatus des Bildmodells wird von der Bildschirmlesehilfe nicht angekündigt.
* SITES-24708: Die Funktion der Filterleiste funktioniert nicht mehr, wenn der Zoom auf 400 % erhöht wird.
* SITES-25235: Die Nachricht Laden von Inhalten der Filterleiste wird von der Bildschirmlesehilfe nicht angekündigt.
* SITES-25254: Horizontale Bildlaufleiste wird im Karussell-Modal angezeigt, wenn Inhalte mit 320 Pixel angezeigt werden.
* SITES-25433: Edge Delivery mit universellem Editor: Korrigieren Sie das Rendering von Seitenversionen für mehrsprachige Site-Strukturen.
* SITES-26064: Inhaltsfragment-REST-API: Korrigieren Sie den Status-Code, der beim Erstellen eines Fragments und Abrufen einer `AccessDeniedException` im Backend zurückgegeben wird.
* SITES-26890: Bei Verwendung der Tastatur ist der Tastaturfokus „Tabellenüberschriften“ auf der Seite „Veröffentlichung verwalten“ nicht sichtbar.
* SITES-29075: Live Copy-Übersicht funktioniert nicht für Websites mit hohem Volumen.
* SITES-29514: Edge Delivery mit universellem Editor: Machen Sie GitHub/Projekt-URL beim Erstellen einer neuen Site obligatorisch.
* SITES-29691: Seite kann im spezifischen Fall, der mit Launches zusammenhängt, nicht verschoben werden.
* SITES-29745: Inhaltsfragment-REST-API: Implementieren der Hydrierung von Verweisvarianten bei der BFS-Durchlaufphase.
* SITES-29748: Korrigieren Sie die Render-Bedingungen, um im CF-Editor verwaltete Veröffentlichungs-/Schnellveröffentlichungsaktionen anzuzeigen.
* SITES-29789: Problem mit der Änderung von Komponenten-Links auf kopierten Stammseiten.
* SITES-29987: Inhaltsfragmente-REST-API: Das Erstellen und Bearbeiten von Inhaltsfragmentmodellen unterstützt keine `previewUrlPattern`.
* SITES-30140: Problem mit zwei Fenstern beim Erstellen eines Inhaltsfragmentverweises.
* SITES-30327: Inhaltsfragment-REST-API: Durch das Veröffentlichen von Inhaltsfragmenten ohne Berechtigungen werden separate Workflows für jede Payload-Ressource erstellt.
* SITES-30333: Lesen von Asset-Metadaten aus jcr, um Probleme beim Parsen von XMP zu vermeiden.
* SITES-30353: GraphQL DataFetchingExceptions für das Feld „src“ in AEM-Inhaltsfragmenten.
* SITES-30377: Edge Delivery mit universellem Editor: Bereinigen von Organisations- und Site-Namen.
* SITES-30386: Edge Delivery mit universellem Editor: Entfernen doppelter, veralteter UE-`cors.js`.
* SITES-30583: Inhaltsfragmente-REST-API: Tool zum Suchen und Ersetzen, mit dem alle Zeichen in Kleinbuchstaben geändert werden.
* SITES-30585: Inhaltsfragment-REST-API: `previewUrlPattern` bei der Erstellung von CFMs mit Verweisen nicht festgelegt.
* SITES-30634: ALT-Text und Ausrichtung des RTE-Bildes funktionieren nicht konsistent.
* SITES-30660: ADA-Compliance-Problem mit benutzerdefinierter AEM-Komponente.
* SITES-30695: Edge Delivery mit universellem Editor: Erhöhen Sie das Ranking der Rewriter-Pipeline, um benutzerdefinierten Code nicht zu beeinträchtigen.
* SITES-30727: Komponenten können nicht per Drag-and-Drop in den Produktionsautoren-Editor verschoben werden.
* SITES-30752: Verwenden Sie beim Generieren einer persistenten Abfrageantwort keine `If-modified-since`-/`last-modified`-Kopfzeilen.
* SITES-30871: DOM-Aktualisierungen, nachdem der AfterEdit-Listener ausgelöst wurde.
* SITES-30877: Falscher Rollout-Status der untergeordneten Seite.
* SITES-30899: Mit der Option „Später auslagern“ können Sie fortfahren, ohne dass ein Datum ausgewählt ist.
* SITES-30947: Nullzeiger-Ausnahme aufgrund fehlender Verhaltenseigenschaft beim Blueprint-Rollout.
* SITES-31157: Inhaltsfragment-REST-API: Patch schlägt fehl ist ein Sonderfall.
* SITES-31162: Inhaltsfragmente-REST-API: Beheben Sie das Umwandlungsproblem für `DateTimeField` Feld in `ModelFieldMapper`.
* SITES-31174: Inhaltsfragment-REST-API: Tags wurden nicht zusammen mit der Veröffentlichungsanfrage veröffentlicht.
* SITES-31272: Sprachkopie von Assets kann nicht über PageManager.copy erstellt werden.
* SITES-31327: Inhaltsfragment-REST-API: Entfernen der ETag-Validierung in der GET-Fragmentanforderung.
* SITES-31387: JavaScript-Fehler &quot;ns.ui.alert ist keine Funktion“ bei der erneuten Aktivierung der Vererbung von Ghost-Komponenten.
* SITES-31454: Inhaltsfragmente-REST-API: Entspannen Sie das Muster für Fragmentverweisfelder, um auch UUIDs zu akzeptieren.
* SITES-31455: Inhaltsfragmente-REST-API: Beheben von E-Tag-Abweichungen zwischen Endpunkten für dasselbe Inhaltsfragmentmodell.
* SITES-31459: Inhaltsfragment-REST-API: CF-Live Copy kann nicht bearbeitet werden, wenn ein Inhaltsreferenz-Feld vorhanden ist.
* SITES-31467: js-errors aus contexthub.authoring-hook.js im Seiteneditor.
* SITES-31487: Inhaltsfragment-REST-API: Zulassen, dass der Berechtigungsendpunkt für den Stammordner aufgerufen wird.
* SITES-31621: Edge Delivery mit universellem Editor: Leere Zeile aus Arbeitsblättern entfernen, die Live Copies sind.
* SITES-31676: Beim Erstellen oder Löschen von Komponenten bleibt unten auf der Seite ein leeres Feld.
* SITES-31822: Checkbox-Beschriftung der ClassicUI fehlt und ist für HTML kodiert.
* SITES-31857: Die CF-Erstellung schlägt in Ordnern mit einfachen Anführungszeichen fehl.
* SITES-31888: Das Löschen von Inhaltsfragmenten kann nicht in die Vorschau übertragen werden.
* SITES-31922: Inhaltsfragment-REST-API: Seitenverweise werden vom referenzierten By-Endpunkt nicht zurückgegeben.
* SITES-31987: Beim Veröffentlichen in der Vorschau werden keine Vorschau-URLs für Inhaltsfragmente angezeigt.
* SITES-32095: Die automatische Aktualisierung schlägt beim Ereignis-Listener „afterchildDelete“ in der Live Copy fehl.
* SITES-32237: Edge Delivery mit universellem Editor: Korrigieren Sie das Rendern von leeren/falsch formatierten Textkomponenten.

### Bekannte Probleme {#known-issues-21331}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-21331}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-21331}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 21 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-21331}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.80.0 | [Oak-API 1.80.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.29.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
