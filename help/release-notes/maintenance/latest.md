---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: b6fe2a58bb16c70cef48426ec49dda474195c023
workflow-type: tm+mt
source-wordcount: '1612'
ht-degree: 10%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 16357 {#release-16357}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 16357, die am Donnerstag, 22. Mai 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 16145.

2024.5.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-16357}

* SITES-19579: Java-API zum Migrieren von Inhaltsfragmenten von einem Modell zum anderen.
* SITES-19698: [API öffnen] Erstellen Sie einen Lesevorgang zum Verwalten eines Benutzeroberflächenschemas pro Modell in der OpenAPI-Definition.
* SITES-19834: Adobe I/O-Ereignis fehlende IDs zum Veröffentlichen/Rückgängigmachen der Veröffentlichung.
* SITES-20146: Aktivieren Sie die Vorschau-Version/Vergleichen für verschobene Seiten.
* SITES-19973: CFM Search API Implementation.
* SITES-2033: Verbesserung der Validierung beim Erstellen von Inhaltsfragmenten.
* SITES-20334: Verbesserung der Validierung beim Bearbeiten von Inhaltsfragmentmodellen.
* SITES-20585: Verbessern der Inhaltsfragmentsuche-API zum Filtern nach Gebietsschema.
* SITES-20594: Gibt den vollständigen Namen des Benutzers zurück, der eine Ressource erstellt/ändert/repliziert.
* SITES-20601: [OpenAPI] Aktualisieren Sie die CF-Such-API, um nur das Abrufen von direkt untergeordneten Inhaltsfragmenten zuzulassen.
* SITES-20656: [BE] Geben Sie eine Option an, die beim Ersetzen einer Zeichenfolge die Groß-/Kleinschreibung widerspiegelt.
* SITES-20405: [Xwalk] Unterstützung von mimeType für das Ausblenden von Feldern.
* SITES-17854: Unterstützung der UUID für CF- und Asset-Referenzen (Pfizer MVP).
* SITES-1955: Simple Model API for UI schema.
* SITES-1961 [API öffnen] Erstellen Sie einen Schreib-/Aktualisierungsvorgang für die Verwaltung eines Benutzeroberflächenschemas pro Modell in der OpenAPI-Definition.
* SITES-19614: [Xwalk] Paginierung des Arbeitsblatts/unendlicher Bildlauf.
* SITES-2005: Die Autoren-Pipeline sollte eine konfigurierbare Ereignisverzögerung aufweisen.
* SITES-20121: Allow defaultValue for enum fields.
* SITES-20342: [Backend] Auf Ordnerebene veröffentlichen - Filter hinzufügen, um nur Inhaltsfragmente zu veröffentlichen.
* SITES-20355: Entfernen Sie Inhaltsfragmentmodelle und Berechtigungs-API-Servlets.
* SITES-20387: Beim Navigieren in den Tag-Administrator wird immer die Tag-Nutzung berechnet.
* SITES-20495: [BE] Möglichkeit, die Berechtigung zum Veröffentlichen auf Ordnerebene zu erhalten.
* SITES-20653: [Xwalk] fügen Sie experiment-start-date und -end-date hinzu.
* SITES-2066: [Xwalk] Die von Experimenten sollten beim Authoring standardmäßig deaktiviert werden.
* SITES-20752: [cq-wcm-core] Apple startet für Inhaltsfragmente.
* SITES-20946: Fügen Sie eTag als Eigenschaft im Endpunkt LIST-Modelle hinzu.
* SITES-20947: [persistence] Rufen Sie die Unteraufgabe nach der Inhaltsfragment-ID ab.
* SITES-21012: Modell-Metadatenschema mit Produkt zusammenführen
* SITES-21769: Verwenden Sie das Pfadpräfix /jcr:id/ für den Abruf der Ressource nach ID.
* ASSETS-30379: DRM License Check führt den gesamten Baum von Assets, die heruntergeladen werden.
* ASSETS-35535: [Datenintegrationsfehler] Bei v1-Ereignissen müssen leere Asset-Downloads ignoriert werden.
* SITES-21550: [Xwalk] Benutzerdefinierte Metadaten: Anzahl, Datum, Uhrzeit, Zeitfelder.
* SITES-20149: RTC: [cq-wcm-launches-core] Exportieren Sie eine neue API für Launches für CFs.
* SITES-20150: RTC: [cq-command] Hinzufügen neuer Methoden zur vorhandenen API.
* SITES-20451: Fügen Sie das Sidecar-Plugin zu wcm-commons hinzu.
* SITES-20499: [MSM][Async] Extrahieren Sie den Code aus AsyncOperationServlet in eine Dienstprogrammklasse.
* SITES-20763: Aktualisierung der Bereitstellungs-API-Endpunkte in der Sites-Integration.
* SITES-20583: Fügen Sie eTag als Eigenschaft in `LIST`/search fragments.
* CQ-4356445: Event Producer &amp; Schema Implementation.
* CQ-4356625: Verbessern der Autorisierungsüberprüfung in languageCopyrendercondition.jsp.
* CQ-4356629: Verbessern der Autorisierungsüberprüfung in isWorkflowUser -Renderbedingung.
* CQ-4356934: Vereinfachen Sie die RequestProcessor-API beim Arbeiten mit ResponseEntities.
* CQ-4357214: Anforderungsprozessoren dürfen nicht von der Servlet-Logik abhängig sein.
* SITES-16392: Fehlgeschlagene Launch-Erstellung sollte keinen Speicherinhalt belassen.
* SITES-20238: [RTC] Pfizer MVP - Fügen Sie die CF-API hinzu, um CF-Pfade zu IDs aufzulösen, und umgekehrt.
* SITES-21043: [CF][launches] Leistungsverbesserungen bei Seitenanschlüssen gegenüber Cloud Service.
* SITES-21044: [CF][launches] Asynchrone Seitenportale bearbeiten die Payload-Implementierung in Cloud Service.
* FORMS-9606: Zuvor konnten im Editor für adaptive Forms nur Feldwerte der Antwort eines Aufrufdienstes zugeordnet werden. Nun können Autoren jede Eigenschaft des Felds der Antwort des Aufrufdienstes zuordnen.
* FORMS-7483: AEM Forms JSON Schema Parser unterstützt jetzt das JSON-Schema (2020-12).
* FORMS-13209: Ein Handler ist enthalten, der die standardmäßigen Handler für die erfolgreiche Übermittlung von adaptiven Forms und für fehlgeschlagene Übermittlung außer Kraft setzt. Sie können diese Handler über den adaptiven Forms-Regeleditor konfigurieren.
* FORMS-13612: Bildschirmlesehilfen lesen jetzt Fehlermeldungen, Kurzbeschreibungen und lange Beschreibungen für Felder im komponentenbasierten adaptiven Forms. Darüber hinaus wurde Unterstützung hinzugefügt, um Eingaben in adaptiven Formularen zu invalidieren, wenn das Formular Fehler enthält und nicht für die Übermittlung gültig ist.
* FORMS-12052: Ein Formularautor kann jetzt benutzerdefinierte Funktionen anwenden, um Daten vor der Übermittlung vorab zu verarbeiten.
* FORMS-11295: Unterstützung für SHA256 mit ECDSA-Algorithmus für AEM Forms Digital Signature hinzugefügt.
* FORMS-9432: Der Cloud-Konfiguration der Datenquelle wurde ein zusätzlicher Content-Typ (REST-Endpunkt) hinzugefügt. Sie ermöglicht die Übermittlung von Daten in Schlüssel/Wert-Paaren an einen authentifizierten Endpunkt.

### Behobene Probleme {#fixed-issues-16357}

* SITES-20608: Experience Fragment mit aktivierter Personalisierung, wenn es in eine Vorlage aufgenommen wird, verursacht eine Endlosschleife.
* SITES-19554 [Xwalk] Tabelleneditor: Zellen können nicht gelöscht werden.
* SITES-19971: Durch das Patchen eines CFM mit Registerkarten ändert sich die Reihenfolge der Felder.
* SITES-20168: Inhaltsfragmentmodell `locked` -Feld nicht ordnungsgemäß aktualisiert.
* SITES-20522: Beschädigte Inhaltsfragmente brechen den Endpunkt /adobe/sites/cf/fragments .
* SITES-20816: CF OpenAPI - Output Inkonsistency with missing model for referenced fragment.
* SITES-21239: Entfernt zirkuläre Abhängigkeit von ContentFragmentSearchService.
* SITES-20582: Die Suche und Auflistung von Inhaltsfragmenten sollte die Tiefe 0 zulassen.
* SITES-20559: [MSM][XF][Lufthansa] Beim Rollout von Experience Fragments von Master/Sprache zu Land/Sprache werden die Verweise nicht aktualisiert.
* SITES-17772: AEM: Benutzer mit Administratorgruppe können die Seite nicht entsperren, was ein anderer Benutzer gesperrt hat.
* SITES-20401: [Xwalk] Abschnittsmetadaten unterstützen keine Eigenschaften mit mehreren Werten.
* SITES-21391: [OpenAPI-Ereignis] Beim Ändern des Titels oder der Tags (Eigenschaften) eines Inhaltsfragmentmodells werden keine Ereignisse ausgelöst.
* SKYOPS-73234: Anstieg des Fehlerprotokollfehlers bei AEM Assets Global DAM Program Upgrade auf AEM Version 15553 und PR Id 35362.
* SKYOPS-75341: NoSuchMethodError in distribution Crosswalk bundle.
* SCRNS-3945: Skyline: Unlokalisierte Zeichenfolge &quot;Geplant&quot;in Screens.
* SITES-20586: Zeitstempel der Vorlage &quot;Veröffentlicht&quot;wird nicht aktualisiert.
* SITES-16674: Kontrollkästchen Rollout-Konfigurationen übernehmen funktioniert nicht mit Live Copy-Eigenschaften.
* SITES-18680: Referenzvarianten in der grafischen Abfrage (Apple) können nicht abgerufen werden.
* SITES-21233: [CoreCmp] Accordion für GS1 US nach der Aktualisierung auf 15860 unterbrochen.
* SITES-20367: Problem beim Löschen von Launches in AEM.
* CQ-4357161: Payload-Bildschirm im AEM-Posteingang gibt 404 zurück.
* SITES-20214: Problem mit AEM Rollout-Konfigurationssequenz beim Speichern.
* SITES-20364: 302 Umleitungen funktionieren nicht mit Selektor in URL.
* SITES-20547: Kürzte Pfade in der Liste &quot;Ausgeschlossene Pfade in Live Copy&quot;auf AEM as a Cloud Service.
* SITES-20691: Einschränkungen für Experience Fragment-Vorlagen nicht berücksichtigt cq:allowedTemplates.
* SITES-21122: AEM CS Live Copy-Defekt mit Inhaltsfragmenten.
* ASSETS-38723: NPE, der von MetadataRulesProviderImpl ausgegeben wird, wenn getReadRulesForMetadataChildNodes() aufgerufen wird, bevor this.readRules initialisiert wird.
* SITES-11727 [GQL] Bei Inhaltsfragmentverweisen fehlt die volle Hydratation von Daten.
* SITES-19462: Die Asset-Suche funktioniert in AEM Cloud nicht ordnungsgemäß.
* SITES-19994: Schaltflächenüberwachung schließen, wenn Benutzer versuchen, Inhaltsfragmente zu schließen.
* SITES-20029: Inhaltsfragmentversionen werden direkt nach dem Schließen erstellt, ohne den Inhalt zu ändern.
* SITES-21316: Fragmentvorschau: Vorschau schlägt aufgrund von Codeänderungen von SITES-11727 fehl.
* SITES-20023: FileUpload funktioniert nicht für Remote(Next Generation assets)-Assets in multifield.
* ASSETS-37611: Der Workflow &quot;Vorgang zum Abschließen der Anforderung&quot;wird für nicht veröffentlichte Assets ausgelöst.
* CQ-4357278: DispatcherServlet gibt NPE aus, wenn getRequestBodyType null zurückgibt.
* CQ-4357279: Die Anforderungsverarbeitung schlägt fehl, wenn für eine Anforderung kein pathInfo vorhanden ist.
* SITES-20496: [Xwalk] Option &quot;Keine Eigenschaften&quot;bei der Auswahl der Tabelle in der Site-Admin.
* FORMS-13827: Im Regeleditor für adaptive Forms unterstützt der Vorgang WHEN derzeit keine verschiedenen Feldtypen mit Datumsauswahl.
* FORMS-13786: Im Regeleditor für adaptive Forms funktioniert die Drag &amp; Drop-Funktion nicht für benutzerdefinierte Funktionen.
* FORMS-13587: Im adaptiven Forms-Editor funktioniert die Funktion &quot;Geräteemulator&quot;nicht ordnungsgemäß für auf Kernkomponenten basierende adaptive Forms.
* FORMS-14376 Wenn ein Benutzer die Schaltfläche &quot;Zurücksetzen&quot;drückt, treten Konsolenfehler auf, wenn der statische Text als ungebunden markiert ist.
* FORMS-13801: Auch wenn die Bedingungskomponente deaktiviert ist, bleibt das entsprechende Kontrollkästchen aktiviert.
* FORMS-11952: Wenn ein Formular gesendet wird, beginnt die vom Formular generierte Sende-URL mit /content/ anstelle von /portale/ und leitet die Anfrage falsch weiter. Dadurch wird verhindert, dass die Anfrage die gewünschten Server erreicht.
* FORMS-13616: Die Datumsauswahl zeigt das aktuelle Datum als einen Tag nach hinten an, was wahrscheinlich auf ein Zeitzonenproblem zurückzuführen ist. Aufgrund dieser Inkonsistenz und eines zusätzlichen Anzeigemuster-Problems ist es schwierig, das richtige Datumsformat festzulegen.
* FORMS-13829: Das Dropdown-Menü, das durch Regeln zur Imimierung der Optionsfeldfunktionalität gesteuert wird, wird nach dem Löschen und erneuten Auswählen einer Auswahl nicht korrekt ausgefüllt. Das gewünschte Verhalten besteht darin, dass einzelne Kontrollkästchen als Optionsfelder fungieren, sodass jeweils nur eine Auswahl möglich ist und die Auswahl aller Optionen aufgehoben werden kann.
* FORMS-14244: In einem adaptiven Formular, das auf einer XDP mit eingebetteten Skripten auf Kontrollkästchen basiert, werden die Skripten nach diesen Kontrollkästchen nicht für Elemente ausgeführt.
* FORMS-14267: Bei Benutzern treten konsistente Timeout-Fehler auf, wenn API-Anfragen in Entwicklungs-, Staging- und Produktionsumgebungen gesendet werden. Diese Anfragen beziehen sich auf das Generieren von PDF, manchmal mit vorausgefüllten Daten über die Datenbindung. Das Problem führt zu einem hängenden Prozess, bei dem es zu einem Timeout kommt, der aber nach dem Fehler wieder versucht wird.
* FORMS-11589: Für Benutzer mit nur der AEM Forms-Lösung (ohne andere Lösungen) funktioniert die Frontend-Pipeline nicht.
* FORMS-13896: Ausgabe, Daten und Zahlen im DoR (Datensatzdokument) werden in arabischer Sprache angezeigt, unabhängig davon, ob die Eingabedaten mit gregorianischen Zahlen zusammengeführt werden.

### Bekannte Probleme {#known-issues-16357}

Keine

### Eingestellte Funktionen und APIs {#deprecated-16357}

Informationen zu veralteten oder entfernten Elementen in AEM as a Cloud Service finden Sie unter [Eingestellte und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md).

### Eingebettete Technologien {#embedded-tech-16357}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.62.0 | [Oak-API 1.62.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| AEM SLING-API | 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2,25,4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
