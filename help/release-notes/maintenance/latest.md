---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 080a79cdc0e48a54570ea53618b1f0be164d5156
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 83%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 21331 {#21331}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 21331, die am 24. Juni 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 21193.

Die Funktionsaktivierung von 2025.7.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-21331}

* CQ-4356522: Optimierung von `WorkflowResourceStatusProvider`.
* FORMS-16458: Benutzeroberfläche zum Auswählen der Schrifteigenschaften (Schrift).
* FORMS-17707: AEP-Connector funktioniert für AEP-Plattform-Staging nicht.
* FORMS-19125: Unterstützung der automatischen Fragmentzuordnung im AF-Editor.
* FORMS-19336: Suche in der Datenquellstruktur im AF-Editor hinzugefügt.
* FORMS-19417: Unterstützung von Optionsschaltflächen in der Hierarchieansicht.
* FORMS-19603: Unterstützung von Musterseite und Design-Seite im Regel-Editor.
* SITES-5358: Inhaltsfragment-REST-API: Kopieren von Inhaltsfragmenten mit untergeordneten Elementen.
* SITES-10575: „MSM Blueprint Bloomfilter Loader“ versucht, mehr als 100.000 Zeilen zu laden.
* SITES-14542: Das Umbenennen/Verschieben einer Live Copy-Quellseite sollte die Veröffentlichung der umbenannten/verschobenen Live Copy-Seite auslösen, falls diese zuvor veröffentlicht war.
* SITES-19754: Edge Delivery mit universellem Editor: Hinzufügen einer für Menschen lesbaren Fehlermeldung, wenn die Integration Probleme aufweist.
* SITES-23499: Edge Delivery mit universellem Editor: Hinzufügen der Unterstützung mehrerer Felder, die für Blockoptionen verwendet werden sollen.
* SITES-23518: Edge Delivery mit Universal Editor: Hinzufügen der Unterstützung für Asset-Ausgabedarstellungen spezifisch für Edge Delivery.
* SITES-24436: Inhaltsfragmente-REST-API: Einführung eines lokalen Caches, um das Abrufen doppelter Verweise zu beschleunigen.
* SITES-25155: Inhaltsfragmente-REST-API: Veraltete Abfrageparameter „enabledForFolder“ in der Modellliste entfernen.
* SITES-25913: Inhaltsfragment-REST-API: Zeitgesteuerte Validierung von Ressourcen vor dem Start des Veröffentlichungs-Workflows.
* SITES-25976: Links in Experience Fragments werden nach dem MSM-Rollout nicht angepasst.
* SITES-26271: Inhaltsfragment-REST-API: Wechsel zum BFS-Durchlauf für den GET-Varianten-Endpunkt.
* SITES-27486: Universeller Editor – AEM-Integration.
* SITES-27775: Optimierte Suche nach Verweisen während der Veröffentlichung (verzögertes Laden von Metadaten).
* SITES-27782: Edge Delivery mit universellem Editor: Hinzufügen einer spezifischen Publisher-Abonnenten-Implementierung, um Inhalte in Edge Delivery zu veröffentlichen (vorzeitiger Zugriff).
* SITES-27792: Edge Delivery mit universellem Editor: Hinzufügen einer dedizierten Edge Delivery Service-Konfigurationsvorlage.
* SITES-28557: Inhaltsfragment-REST-API: Zulassen, dass E-Tags verwendet werden, die durch den Aufruf von `/cf/fragments/{fragmentId}` mit `references=direct` abgerufen wurden, um ein Inhaltsfragment zu patchen.
* SITES-28683: Zulassen, dass MSM LiveRelationship-Suchen den erweiterten Status überspringen.
* SITES-29601: Inhaltsfragment-REST-API: Validierung für Inhaltsfragmentverweise in Langtextfeldern.
* SITES-29614: Inhaltsfragment-REST-API: Rufen Sie einen Workflow mithilfe des `/cf/workflows/{workflowInstanceId}`-Endpunkts ab, wobei „workflowInstanceIda“ die von der Veröffentlichungsanfrage zurückgegebene ID ist.
* SITES-29615: Inhaltsfragment-REST-API: Listet alle Batch-Anfragen auf, die über POST-`/cf/batch` mithilfe von `GET /cf/batch` erstellt wurden.
* SITES-29874: Inhaltsfragmente-REST-API: Verweise aus Langtextfeldern von Inhaltsfragmenten werden jetzt abgerufen und hydriert.
* SITES-29930: Inhaltsfragment-REST-API: Hinzufügen von Metriken für den Workflow zum Veröffentlichen von Inhaltsfragmenten.
* SITES-29986: Inhaltsfragment-REST-API: Unterstützung der technischen Benennung des Inhaltsfragmentmodells.
* SITES-30088: Inhaltsfragment-REST-API: Veröffentlichung von Inhaltsfragmenten – Überspringen des Abrufs von Verweisen, wenn filterReferencesByStatus leer ist.
* SITES-30126: Inhaltsfragmente-REST-API: CF Leistungsverbesserung der Veröffentlichung: Überprüfung, ob eine Ressource ein Fragment ist, durch eine minimale Überprüfung ersetzt.
* SITES-30328: Edge Delivery mit universellem Editor: Hinzufügen der Unterstützung der Vorschau von Sidekick.
* SITES-30445: Inhaltsfragment-REST-API: Benutzeroberflächenschema des Inhaltsfragmentmodells: Hinzufügen einer Option, um den Anfangsstatus von reduzierbaren Elementen zu steuern.
* SITES-30604: Inhaltsfragmente-REST-API: Unterstützung der Einführung von Modell-Metadatenschemata in der neuen Benutzeroberfläche.
* SITES-30885: Optimierte JSON-Verarbeitung in persistierten Abfragen.
* SITES-30886: Inhaltsfragment-REST-API: GET-Workflows für den Inhaltsfragment-Endpunkt, die auf in Workflow-Metadaten gespeicherten Fragment-UUIDs basieren.
* SITES-31005: Verbesserte Benutzeroberfläche für Rollout-Aufträge, um den Fortschritt anzuzeigen.
* SITES-31020: Verbesserte Benutzeroberfläche für das Erstellen von Live Copy-Aufträgen, um den Fortschritt anzuzeigen.
* SITES-31111: Inhaltsfragment-REST-API: Zulassen, dass die Varianten-Patch-API Inhaltsfragmentverweise innerhalb von Inhaltsfragment-Launches akzeptiert.
* SITES-31343: Inhaltsfragment-REST-API: Hinzufügen von Filterung und Paginierung nach Datum zum Endpunkt, der Batch-Anfragen auflistet.
* SITES-31472: Das Löschen eines Launch kann dazu führen, dass das Repository angehalten wird, wenn der Launch sehr umfangreich ist.
* SITES-31641: Inhaltsfragmente-REST-API: Eigenschaft zu Modellfeldern hinzufügen, um dynamische Zuordnungen zu Erweiterungen zu speichern.
* SITES-31677: Benutzerdefinierter Arbeitsbereich unterstützt den Export von AEM-Inhaltsfragmenten zu Target.
* SITES-31770: Inhaltsfragment-REST-API: Leistungsverbesserungen bei PATCH.
* SITES-31782: Inhaltsfragment-REST-API: Hinzufügen einer Beschreibung für lokale Assets.
* SITES-32175: Zulassen von Zwischen-Commits für Live Copy-Erstellung und MSM-Seiten-Rollout.

### Behobene Probleme {#fixed-issues-21331}

* CQ-4359756: Übersetzungsregeln beziehen jetzt Filtereigenschaften auf Komponentenebene ein.
* CQ-4359826: Behebung des inkonsistenten Status im Panel zu Inhaltsfragmentverweisen.
* CQ-4359866: Die LanguageUtils-Klasse unterstützt jetzt Komponententests, ohne zusätzliche Abhängigkeiten hinzuzufügen.
* FORMS-13990: Forms-Service-APIs: Dokumenterstellung: Leeres Datenfeld gibt nach Auswahl 200 zurück, obwohl 400 erwartet wird.
* FORMS-14309: Forms-Service-APIs : Extrahieren von Daten als Antwort-Code-Berichtigung.
* FORMS-18526: Wenn eine Regel mit mehreren Feldern in Bedingungen kopiert wird, ändert sich das feste Feld nicht.
* FORMS-18977: Der DOR-Service übergibt den Titel des Dokuments nicht.
* FORMS-19047: Übersetzungen fehlen nach der Veröffentlichung eines adaptiven Formulars in AEM Forms unter SP22.
* FORMS-19234: Timeline-Funktion von PDFs in AEM Forms kann nicht verwendet werden.
* FORMS-19628: Das Ausschließen von Titeln verschachtelter Panels blendet im automatisch generierten DOR auch den Titel des Stamm-Panels aus.
* FORMS-19651: Korrektur einer Regel, bei der eine angeklickte Schaltfläche in einer binären Bedingung verwendet wird und dieselbe Schaltfläche auch in der „Dann“-Anweisung verwendet wird.
* FORMS-19808: FormsPortal – Entwürfe können nicht abgerufen werden, wenn verzögertes Laden aktiviert ist.
* FORMS-19887: Die Zugriffseigenschaft funktioniert in der HTML5-Vorschau nicht.
* SITES-15452: Eindeutige Inhaltsfragment-Elemente sollten beim Launch nicht mit ihren Kopien verglichen werden.
* SITES-24492: ARIA-Tablist hat keinen zugänglichen Namen.
* SITES-24623: Inhaltsfragment-REST-API: Beheben von ETag-Abweichungen zwischen Endpunkten für dasselbe Inhaltsfragment.
* SITES-24668: Die Funktion der Verweisleiste funktioniert nicht mehr, wenn der Zoom auf 400 % erhöht wird.
* SITES-24678: Die Statusmeldung der Verweisleiste wird von der Bildschirmlesehilfe nicht vorgelesen.
* SITES-24697: Der Ladestatus des Bildmodells wird von der Bildschirmlesehilfe nicht vorgelesen.
* SITES-24708: Die Funktion der Filterleiste funktioniert nicht mehr, wenn der Zoom auf 400 % erhöht wird.
* SITES-25235: Die Meldung zum Laden von Inhalten der Filterleiste wird von der Bildschirmlesehilfe nicht vorgelesen.
* SITES-25254: Die horizontale Bildlaufleiste wird im Karussell-Modal angezeigt, wenn Inhalte mit 320 Pixel angezeigt werden.
* SITES-25433: Edge Delivery mit universellem Editor: Korrektur des Renderings von Seitenversionen für mehrsprachige Site-Strukturen.
* SITES-26064: Inhaltsfragment-REST-API: Korrigieren Sie den Status-Code, der beim Erstellen eines Fragments und Abrufen einer `AccessDeniedException` im Backend zurückgegeben wird.
* SITES-26890: Bei Verwendung der Tastatur ist der Tastaturfokus „Tabellenüberschriften“ auf der Seite „Veröffentlichung verwalten“ nicht sichtbar.
* SITES-29075: Live Copy-Überblick funktioniert für Websites mit hohem Volumen nicht.
* SITES-29514: Edge Delivery mit universellem Editor: GitHub-/Projekt-URL wird beim Erstellen einer neuen Site obligatorisch gemacht.
* SITES-29691: Seite kann in spezifischen mit Launches zusammenhängenden Fällen nicht verschoben werden.
* SITES-29745: Inhaltsfragment-REST-API: Implementieren der Hydrierung von Verweisvarianten beim BFS-Durchlauf.
* SITES-29748: Korrektur der Render-Bedingungen, um im Inhaltsfragment-Editor Aktionen für Veröffentlichungsverwaltung/Schnellveröffentlichung anzuzeigen.
* SITES-29789: Problem mit der Änderung von Komponenten-Links auf kopierten Stammseiten.
* SITES-29987: Inhaltsfragment-REST-API: Das Erstellen und Bearbeiten von Inhaltsfragmentmodellen unterstützt `previewUrlPattern` nicht.
* SITES-30140: Problem mit zwei Fenstern beim Erstellen eines Inhaltsfragmentverweises.
* SITES-30327: Inhaltsfragment-REST-API: Durch das Veröffentlichen von Inhaltsfragmenten ohne Berechtigungen werden separate Workflows für jede Payload-Ressource erstellt.
* SITES-30333: Lesen von Asset-Metadaten aus JCR, um Probleme beim Parsen von XMP zu vermeiden.
* SITES-30353: GraphQL-DataFetchingExceptions für das Feld „src“ in AEM-Inhaltsfragmenten.
* SITES-30377: Edge Delivery mit universellem Editor: Bereinigen von Organisations- und Site-Namen.
* SITES-30386: Edge Delivery mit universellem Editor: Entfernen doppelter, veralteter UE `cors.js`.
* SITES-30583: Inhaltsfragment-REST-API: Tool zum Suchen und Ersetzen ändert alle Zeichen in Kleinbuchstaben.
* SITES-30585: Inhaltsfragment-REST-API: `previewUrlPattern` bei der Erstellung von Inhaltsfragmentmodellen mit Verweisen nicht festgelegt.
* SITES-30634: Alternativtext und Ausrichtung des RTE-Bilds funktionieren nicht einheitlich.
* SITES-30660: ADA-Compliance-Problem mit benutzerdefinierter AEM-Komponente.
* SITES-30695: Edge Delivery mit universellem Editor: Erhöhen der Rangfolge der Rewriter-Pipeline, um benutzerdefinierten Code nicht zu beeinträchtigen.
* SITES-30727: Komponenten können nicht per Drag-and-Drop in den Editor zur Produktionserstellung verschoben werden.
* SITES-30752: Verwenden Sie beim Generieren einer persistenten Abfrageantwort keine `If-modified-since`-/`last-modified`-Header.
* SITES-30871: DOM-Aktualisierungen werden nach dem afteredit-Listener ausgelöst.
* SITES-30877: Falscher Rollout-Status der untergeordneten Seite.
* SITES-30899: Mit der Option des späteren Rollouts können Sie fortfahren, ohne dass ein Datum ausgewählt ist.
* SITES-30947: Null-Pointer-Ausnahme aufgrund fehlender Verhaltenseigenschaft im Blueprint beim Rollout.
* SITES-31157: Inhaltsfragment-REST-API: Fehlschlagen des Patches ist ein Sonderfall.
* SITES-31162: Inhaltsfragmente-REST-API: Beheben Sie das Umwandlungsproblem für `DateTimeField` Feld in `ModelFieldMapper`.
* SITES-31174: Inhaltsfragment-REST-API: Tags wurden nicht zusammen mit der Veröffentlichungsanfrage veröffentlicht.
* SITES-31272: Sprachkopie von Assets kann nicht über PageManager.copy erstellt werden.
* SITES-31327: Inhaltsfragment-REST-API: Entfernen der ETag-Validierung in der GET-Fragmentanfrage.
* SITES-31387: JavaScript-Fehler „ns.ui.alert ist keine Funktion“ bei der erneuten Aktivierung der Vererbung von Ghost-Komponenten.
* SITES-31454: Inhaltsfragmente-REST-API: Entspannen Sie das Muster für Fragmentverweisfelder, um auch UUIDs zu akzeptieren.
* SITES-31455: Inhaltsfragment-REST-API: Beheben von ETag-Abweichungen zwischen Endpunkten für dasselbe Inhaltsfragmentmodell.
* SITES-31459: Inhaltsfragment-REST-API: Live Copy eines Inhaltsfragments kann nicht bearbeitet werden, wenn ein Inhaltsverweisfeld vorhanden ist.
* SITES-31467: JS-Fehler aus contexthub.authoring-hook.js im Seiteneditor.
* SITES-31487: Inhaltsfragment-REST-API: Zulassen, dass der Berechtigungsendpunkt für den Stammordner aufgerufen wird.
* SITES-31621: Edge Delivery mit universellem Editor: Entfernen einer leere Zeile aus Arbeitsblättern, die Live Copies sind.
* SITES-31676: Beim Erstellen oder Löschen von Komponenten bleibt unten auf der Seite ein leeres Feld.
* SITES-31822: Label von ClassicUI-Kontrollkästchen fehlt und ist für HTML kodiert.
* SITES-31857: Die Erstellung eines Inhaltsfragments schlägt in Ordnern mit einfachen Anführungszeichen fehl.
* SITES-31888: Das Löschen von Inhaltsfragmenten kann nicht in die Vorschau übertragen werden.
* SITES-31922: Inhaltsfragment-REST-API: Seitenverweise werden vom referencedBy-Endpunkt nicht zurückgegeben.
* SITES-31987: Beim Veröffentlichen in der Vorschau werden keine Vorschau-URLs für Inhaltsfragmente angezeigt.
* SITES-32095: Die automatische Aktualisierung schlägt beim Ereignis-Listener „afterchilddelete“ in der Live Copy fehl.
* SITES-32237: Edge Delivery mit universellem Editor: Korrektur des Renderns von leeren/falsch formatierten Textkomponenten.

### Bekannte Probleme {#known-issues-21331}

* SITES-33177: Abschnittsstile, die als kommagetrennte Zeichenfolgen gespeichert sind, sind fehlerhaft.

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
