---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: d07fc976fe9c8e7872468048f80e525fe8484339
workflow-type: tm+mt
source-wordcount: '2584'
ht-degree: 9%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 15787 {#release-15787}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 15787, die am Freitag, 4. April 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 15575.

2024.3.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de).

### Verbesserungen {#enhancements-15787}

* SITES-19059 - Inhaltsfragmente - OpenAPI - Allow defaultValue for enum fields
* SITES-2013 - Inhaltsfragmente - OpenAPI - WCMScriptHelper sollte das Rendering abbrechen, wenn kein ServletResolver vorhanden ist
* SITES-19926 - Inhaltsfragmente - OpenAPI - Verbesserungen des OnOffTriggerProzessors
* SITES-17945 - Inhaltsfragmente - OpenAPI - Abrufen der zuletzt geänderten Metadaten für jede Version
* SITES-17298 - Inhaltsfragmente - OpenAPI - Berechtigungen für Inhaltsfragmentmodelle
* SITES-14255 - Inhaltsfragmente - OpenAPI - Überprüfen Sie die Eindeutigkeit von Textfeldern, wenn im Fragmentmodell eine eindeutige Markierung gesetzt ist
* SITES-15557 - Inhaltsfragmente - OpenAPI - Allow defaultValue for enum fields
* SITES-1559 - Inhaltsfragmente - OpenAPI - Aktualisierung der CF-Listen-API zum Abrufen nur direkt untergeordneter Inhaltsfragmente (BE)
* SITES-16052 - Inhaltsfragmente - OpenAPI - Fügen Sie die URL für die Instanz hinzu, in der eine Ressource verwendet werden könnte
* SITES-17944 - Inhaltsfragmente - OpenAPI - EIGENE JCR-ACLs-Zuordnung zum CF-Berechtigungsendpunkt
* SITES-17513 - Content Fragment Control Panel - Veröffentlichung von Inhaltsfragmenten rückgängig machen
* SITES-8831 - Content Fragment Control Plane - PUT - Aktualisieren eines Fragments mit vollständigen Informationen
* SITES-8836 - Inhaltsfragmente - OpenAPI - Control Panel - GET References - Get parent references of a fragment (by UUID)
* SITES-8986 - Inhaltsfragmente - OpenAPI - Inhaltsfragmentmodell veröffentlichen
* SITES-18073 - Inhaltsfragmente - OpenAPI - PreviewURL Pattern for a CFM
* SITES-15242 - Inhaltsfragmente - OpenAPI - Erweitern Sie die Veröffentlichungsereignisse, um Informationen zur Ebene bereitzustellen
* SITES-18702 - Inhaltsfragmente - OpenAPI - [Backend] Möglichkeit zur Veröffentlichung auf Ordnerebene
* SITES-20020 - Inhaltsfragmente - OpenAPI - Entfernen `X-Adobe-Accept-Unsupported-API` vor GA
* SITES-16066 - Inhaltsfragmente - Fragmenteditor - JS-URL der Asset-Auswahl ändern
* SITES-19326 - Inhaltsfragmente - Fragmenteditor - Aktualisieren von Links in der Assets-Benutzeroberfläche zum Öffnen des Inhaltsfragments im neuen CF-Editor
* SITES-10515 - Inhaltsfragmente - GraphQL-API - GraphQL - AbstractFetcher-Leistungsproblem Laden referenzierter Inhaltsfragmente
* SITES-17364 - Inhaltsfragmente - GraphQL-API - Rückgabe des vollständigen Namens für die Eigenschaften &quot;Geändert von&quot;und &quot;Veröffentlicht von&quot;
* SITES-19165 - Inhaltsfragmente - GraphQL-API - Zulassen der Verwendung, Referenzierung und Abfrage globaler Modelle in allen GraphQL-Endpunkten
* SITES-17768 - Inhaltsfragmente - GraphQL-API - Dynamic Media-URL für Bilder über _dmS7Url verfügbar machen
* SITES-11057 - Core-Backend - Vermeiden Sie das Laden aller Versionen beim Öffnen von Timeline > Versionen
* SKYOPS-63033 - HTTPD - Leerzeichen von Dispatcher-Umgebungsvariablen zuschneiden
* SKYOPS-65518 - HTTPD - Fehlschlagen des Validators, wenn im Dispatcher-Ordner unzulässige Dateinamen vorhanden sind
* SITES-19626 - Launches - Zusammenführen von lastUpdate-Feldern aus DAM und CFM in Hauptkomponenten
* SITES-19251 - Schnellsite - Erstellungsassistent - Unterstützt Sites Admin über die Seitenleiste, wenn der Designverweis nicht dem Site-Namen entspricht
* SITES-15430 - Universal Editor - Universal Editor unter AEM Domain
* CQ-4344966 - WCM - Übersetzung - Erstellen Sie ein Grundgerüst für die strukturelle Aktualisierung von Sites und Aktualisieren vorhandener Seiten für Assets
* CQ-4347312 - WCM - Übersetzung - Erstellen Sie einen Workflow zum Verknüpfen von &quot;cq:translationsourcejcruuid&quot;in vorhandenen Quell- und Sprachkopien
* CQ-4354509 - WCM - Übersetzung - Veröffentlichungsaufgabenereignisse [OSGi EventAdmin]
* SITES-16318 - Crosswalk - AEM-basiertes Authoring mit Edge Delivery Services
* FORMS-9889: Der Benutzer kann die POST-URL und die Cloud-Konfiguration hinzufügen, während er die Übermittlungsaktion für &quot;An REST-Endpunkt übermitteln&quot;konfiguriert
* Im Regeleditor haben Benutzer folgende Möglichkeiten:
   * FORMS-12160: Überprüfen Sie ein Feld, Bedienfeld oder Formular im Dann-Abschnitt der Wenn-Bedingung.
   * FORMS-12570: Zurücksetzen eines Felds, Bedienfelds oder Formulars im Dann-Abschnitt der Wenn-Bedingung.
   * FORMS-11541: Verwenden Sie Feldobjekte und globale Objekte im Regeleditor über die benutzerdefinierten Funktionen.
   * FORMS-11714: Definieren Sie Parameter als optional in der benutzerdefinierten Funktion. Standardmäßig sind in benutzerdefinierten Funktionen deklarierte Parameter obligatorisch.
   * FORMS-11756: Verwenden Sie die Zwischenspeicherung für benutzerdefinierte Funktionen, um die Antwortzeit beim Abrufen der benutzerdefinierten Funktionsliste im Regeleditor zu verbessern.
   * FORMS-12053: Fügen Sie in der &quot;Wenn&quot;-Bedingung eine &quot;else&quot;-Anweisung hinzu, um verschachtelte Bedingungen zu implementieren.
   * FORMS-11269: Verwenden Sie moderne ES10-JavaScript-Funktionen wie let- und pfeile Funktionen in der benutzerdefinierten Funktion für auf Kernkomponenten basierende Formulare.

* FORMS-9014: Verschiedene Verbesserungen in Bezug auf Barrierefreiheit bei der Komponente &quot;Freihandsignatur&quot;


### Behobene Probleme {#fixed-issues-15787}

* Verschiedene Probleme mit Barrierefreiheit und Internationalisierung behoben
* SITES-16966 - AEM: Nicht lokalisiert &quot;Nicht versioniert!&quot; Zeichenfolge in Sites > Wiederherstellen > Baum wiederherstellen
* SITES-16208 - Der ContentFragmentModelIdentifier legt eine irreführende Titeleigenschaft offen
* SITES-18024 - Wenn die If-Match-Kopfzeile fehlt, muss die Antwort 428 sein.
* SITES-18003 - Der Benutzer, der eine Version erstellt hat, wird nicht korrekt zurückgegeben
* SITES-17937 - Das Ereignis &quot;Inhaltsfragment erstellt&quot;wird ausgegeben, bevor die Autoren-Pods synchronisiert wurden
* SITES-18029 - Die Ereignisverarbeitungs-Pipeline hängt, wenn sie gleichzeitig von der JCR-Beobachtung benachrichtigt wird
* SITES-17882 - Entfernt die maximale Länge von Fragmenttextfeldern aus dem Schema
* SITES-19252 - Beheben von Inkonsistenzen im Zusammenhang mit dem HTTP-Status-Code 406 und 415
* SITES-16964 - [Backend] Die Sortierung nach &quot;Geändert von&quot;funktioniert nicht ordnungsgemäß
* SITES-17519 - Seiten-Eigenschafteneditor für Sites - Der lange Seitenname lässt die Schaltflächen nicht anklickbar werden
* SITES-16852 - Publish-API veröffentlicht Verweise mit NEUEM Status
* SITES-18833 - Eindeutige Beschränkung in nicht in OpenAPI-Endpunkten sichtbar
* SITES-15553 - Das Seitenbedienfeld von XF konnte nicht geladen werden, wenn die URL des XF einen Selektor enthält
* SITES-14340 - NPE in VersioningTimelineEventProvider.accept
* SITES-1605 - [Sites] DeletePageCommand gibt NPE aus, wenn der Quellpfad null ist
* SITES-16308 - [GB18030]: Warnmeldung wird angezeigt, wenn ein neuer Sites-Ordner mit dem Namen GB18030-Zeichen erstellt wird
* SITES-16304 - [GB18030]: Warnmeldung wird angezeigt, wenn ein neuer Experience Fragments-Ordner mit dem Namen GB18030-Zeichen erstellt wird
* SITES-8769 - Verbessern der StyleImpl-Leistung
* CQ-4343815 - Kampagne - Targeting - Standardvariante eines Teasers hat leere URL
* CQ-4355889 - Campaign - Targeting - Erstellen einer Zielgruppenanforderung schlägt mit der IMS-Konfiguration fehl.
* SITES-12460 - Campaign-Integration - Campaign-/AEM Cloud Service-Integration unterbrochen
* SITES-11571 - Inhaltsfragmente - GraphQL-API - PersistedQueryServlet sollte 400 s für fehlerhafte URLs senden
* SITES-19946 - Inhaltsfragmente - GraphQL-API - Modelle werden beim Start nicht mehr gescannt
* SITES-1605 - Core Backend - DeletePageCommand gibt im Falle eines Nullquellenpfads NPE aus
* SITES-5429 - Core Backend - ChildrenListServlet itemResourceType ermöglicht die direkte Ausführung von Code
* SITES-15553 - Experience Fragments - Das seitliche Bedienfeld von XF konnte nicht geladen werden, wenn die URL der XF einen Selektor enthält
* SITES-13666 - Headless - Admin - Error Log False Positive &quot;com.adobe.cq.dam.cfm.headless.ui.impl.models.CFHomeCardModelImpl Config Id not be null&quot;
* SITES-17164 - Seiten-Editor - [Cloud, 6.5 Forms] Die Vorschau des AF-Design-Editors ist fehlerhaft
* SITES-14340 - Sites Admin UI - NPE in VersioningTimelineEventProvider.accept ts
* SKYOPS-68611 - Sling - repoinit - Port sling repoinit Erstellt eine Pfadkorrektur in der Wartungsverzweigung
* CQ-4354678 - WCM - Übersetzung - Übersetzungsaufträge exportieren übersetzte Inhalte
* CQ-4355167 - WCM - Übersetzung - Beim Markieren eines Übersetzungsauftrags wird kein Popup angezeigt &quot;Abgeschlossen&quot;oder &quot;Archiv&quot;
* CQ-4355913 - WCM - Übersetzung - Sprachkarten von Übersetzungsprojekten mit Fehlerbehebung
* GRANITE-47694 - Workflow - Unteraufgaben können nicht in einem Workflow für Cloud für Benutzer ohne Administratorrechte abgerufen werden.
* ASSETS-31097 - Assets Cloud - Protokolle mit durchlaufenen Indexwarnungen für /bin/numberofentitiesinfolders.json gefüllt
* ASSETS-35860 - Assets Cloud - Falsche Zeitzonenkonvertierung in der AEM Assets-Spaltenansicht
* SITES-15260 - Klassische Benutzeroberfläche (alt) - Bulkedit fügt einfache Eigenschaften auf der Seite hinzu, wenn der Tabellenimport verwendet wird
* SITES-16834 - Klassische Benutzeroberfläche (alt) - Text fehlt nach der Bearbeitung von Text mit dem Bulk Editor, wenn Text Kommas enthält
* SITES-17767 - Inhaltsfragmente - Admin - Unterstützung von zulässigen cf-Modellen auch für Ordner ohne jcr:content -Knoten
* SITES-17683 - Inhaltsfragmente - Core-Backend - Inhaltsfragmente können mit Jackson Exporter nicht serialisiert werden
* SITES-18797 - Inhaltsfragmente - Core Backend - GraphQL-Ergebnisse werden nach Indexanpassung dupliziert
* SITES-18076 - Content Fragments - Core Backend - Text mit mehreren Werten hat einen falschen @TypeHint
* SITES-17856 - Inhaltsfragmente - Modelle und Modell-Editor - CF-Modelle werden nicht angezeigt, wenn config kein Ordner ist
* SITES-17071 - Core Backend - Spezifische Seite zeigt keine Version in der Timeline an
* SITES-17285 - Kernkomponenten - Inline-Bild-Zuschnitt unterscheidet sich in der Autoren- und Veröffentlichungsinstanz in AEMaCS
* SITES-19187 - Kernkomponenten - Zwei Methoden zum Platzieren von Assets in einer Bildkomponente erzielen unterschiedliche Ergebnisse im Dialogfeld
* SITES-20077 - Kernkomponenten - Inline-Bildbeschneidung - Zuschneiden ist falsch und Bilder sind verschwommen
* SITES-17211 - Experience Fragments - Experience Fragments component path picker dialog , in dem Experience Fragments angezeigt werden, die gelöscht werden
* SITES-17894 - Launches - Die Promotion verschachtelter Launches setzt Launch-Inhalte von seinem Vorgänger auf eine Version zurück
* SITES-16042 - MSM - Live Copies - Anmerkungen werden in der Live Copy nach Rollouts nicht korrekt angezeigt
* SITES-16691 - MSM - Live Copies - Wenn der Kunde aus dem Rollout-Symbol einer Komponente &quot;Rollout&quot;oder &quot;Rollout zu&quot;auswählt, ist die Schaltfläche &quot;Weiter&quot;ausgegraut.
* SITES-16733 - MSM - Live Copies - Blueprint-Index-Seite kann nicht bereitgestellt werden, wenn rep:policy auf Knoten angewendet wird
* SITES-17155 - MSM - Live Copies - Headers &amp; Footers werden bei der Umbenennung von LiveCopy wieder ins Englische übersetzt
* SITES-17492 - MSM - Live Copies - Inkonsistenzen AEM SeitenLive Copy-Layout
* SITES-19316 - MSM - Live Copies - Referenzlink zum Experience Fragment wird in der Sprachkopie nicht aktualisiert
* SITES-19347 - MSM - Live Copies - Meldungen zu Warenkorbabbrüchen - Langsamkeit der Prod-Autoren und Dienstausfall - Häufige Neustarts von Pods - Gesundheitswarnungen
* SITES-19790 - MSM - Live Copies - Falsche Vorschauinformationen nach der Live Copy-Erstellung
* SITES-20086 - MSM - Live Copies - MSM-Rollout für CF in Assets Rollout alle Live Copies, auch wenn eine Live Copy für das Rollout ausgewählt wurde
* SITES-20088 - MSM - Live Copies - Problem mit leeren Seiten Post XF-Rollout in Eigenschaften - AEM as a Cloud Service
* SITES-16854 - Seiten-Editor - Target-Ablageüberlagerung deckt ParSys in Komponenten mit der Funktion &quot;Bedienfeld auswählen&quot;
* CQ-4355563 - Projekte - Der Pfadparameter ist falsch. Füllen von &quot;?appId=aemshell&quot;für das Projekt-Posteingangssuchskript
* SITES-16876 - Schnellsite - Designbereitstellung - CSS und JS fehlen auf Vorschauseiten 2
* SITES-18418 - Sites Admin-Benutzeroberfläche - Die Funktion zum Anzeigen/Ausblenden für das Pfadfeld-Widget funktioniert nicht ordnungsgemäß, wenn ein Feld erforderlich ist
* SITES-19534 - Sites-Administrator-Benutzeroberfläche - Dialogfeld &quot;Effektive Berechtigungen&quot;kann nach der Aktualisierung AEM 6.5.19 nicht geöffnet werden
* SITES-19203 - Vorlagen-Editor - Bearbeitbare Vorlagenrichtlinien Textabweichung und Stilüberschneidung Löschen-Schaltfläche
* CQ-4354881 - WCM - Übersetzung - Der Pfad für Inhaltsfragmente wird auf &quot;source (en-us)&quot;festgelegt, wenn Inhaltsfragmente als Teil einer Seite übersetzt werden
* CQ-4355289 - WCM - Übersetzung - Nur die ersten 40 Elemente werden in Übersetzungs-Cloud Services angezeigt
* CQ-4355866 - WCM - Übersetzung - Übersetzungs-Workflow gibt Fehler für vorhandene Seiten aus
* CQ-4355797 - Workflow - OOTB-Workflow-Schritt kann nicht verwendet werden
* GRANITE-48938 - Workflow - Autor mit angehaltener Anzeige im Status &quot;ausstehende Veröffentlichung&quot;für Assets. Problem im neuen beibehaltenen Payload-Map-Cache.
* GRANITE-49036 - Workflow - Funktionsanforderung | Möglichkeit zur Planung und Konfiguration der Bereinigung von Workflow-Paketen
* SITES-17393 - Workflow-Erweiterungen - Inhaltsstruktur für Veröffentlichung schlägt fehl, wenn Workflow-Starter für cq:Tag verwendet werden
* SITES-17759 - Workflow-Erweiterungen - Baum-Activation-Workflow für Tags, die nicht in AEMaaCS funktionieren
* FORMS-12411: Auf Android-Geräten muss die `Maximum Number of Characters Validation` -Option funktioniert nicht für die Komponente TextBox für adaptive Formulare.
* FORMS-13377: Wenn ein Benutzer versucht, die benutzerdefinierte Schriftart hinzuzufügen und die Pipeline zum Konfigurieren auszuführen, schlägt der Fehler &quot;ContainerNotReady&quot;fehl
* FORMS-13267: Wenn ein Benutzer eine Dropdown-Komponente für ein adaptives Formular hinzufügt, kann die ID für das Dropdown-Menü nicht generiert werden
* FORMS-13544: Wenn ein Benutzer eine Container-Komponente für adaptive Formulare mit einem Assistentenlayout hinzufügt, funktioniert sie beim Erstellen von Formularen nicht ordnungsgemäß
* FORMS-13091, FORMS-13414: Wenn der Benutzer versucht, eine benutzerdefinierte Domänen-URL im Azure Blob-Speicher zu konfigurieren, schlägt dies fehl
* FORMS-13595: Wenn ein Benutzer versucht, das Formular an einem anderen Speicherort zu speichern, kann der Benutzer die Schaltflächen &quot;Ordner auswählen&quot;und &quot;Abbrechen&quot;nicht sehen, wenn die Browserauflösung auf 100 % eingestellt ist. Die Option ist jedoch sichtbar, wenn die Auflösung auf 75 % eingestellt ist
* FORMS-10952: Wenn ein Benutzer einem adaptiven Formular eine Dropdown-Komponente für ein adaptives Formular hinzufügt und die Eigenschaft &quot;Optionen festlegen&quot;auf Grundlage verschiedener benutzerdefinierter Regeln verwendet, funktioniert die Eigenschaft &quot;Optionen festlegen&quot;nur für die letzte Regel
* FORMS-11471: Das verzögerte Laden eines Fragments schlägt fehl, wenn der Aufruf &quot;emitter.json&quot;aufgrund einer Netzwerkunterbrechung fehlschlägt.
* FORMS-11786: Wenn ein Benutzer zwischen Monaten im Kalender-Widget wechselt, zeigt die Datumsauswahlkomponente eine zusätzliche Zeile an.
* FORMS-12093, FORMS-12093: Wenn ein Benutzer zum Senden eines Formulars das Kontrollkästchen für adaptive Formulare anklickt, wird der falsche Wert mit einem zusätzlichen  `\` wird im Textfeld gespeichert
* FORMS-11993: Wenn ein Benutzer mit der Komponente &quot;Foto aufnehmen&quot;auf einem iOS-Gerät auf ein Bild klickt, werden alle Bilder mit demselben Namen zum Ordner hinzugefügt
* FORMS-12555: Wenn ein Benutzer versucht, AEM Forms in eine Mailingplattform mit einer AEM veröffentlichten URL zu integrieren, fügt AEM Forms beim Rendern der Seite method=post nicht hinzu. Dieses Problem tritt auf, obwohl die POST in der Sendeaktion mit der URL festgelegt ist. Dadurch erkennt die Mailingplattform dies nicht als Formular
* FORMS-12938: Die HTML5-Formulare funktionieren nicht oder werden im Microsoft Edge-Browser mit dem IE-Kompatibilitätsmodus nicht ordnungsgemäß geladen
* FORMS-12032: Wenn ein Benutzer ein Formular sendet, zeigt der Pfad für den Pfad der Sendeaktion nicht richtig an
* FORMS-12445: Falsche Werte werden im Formulardatenmodell erfasst, nachdem die Reihenfolge der Optionsfeld-Optionen geändert und das Formular veröffentlicht wurde.
* FORMS-12947: Wenn ein Benutzer einem vorhandenen Wörterbuch eine neue Sprache hinzufügt, kann es nicht zusammengeführt oder hinzugefügt werden
* FORMS-11363: Wenn ein Benutzer ein Formular über Workspace sendet, tritt in den Tabellen ein Anzeigeproblem auf, während es wiedergegeben wird
* FORMS-11756: Wenn ein Benutzer die ES6-JavaScript-Funktionen wie `let` und `const` in benutzerdefinierten Funktionen kann der Regeleditor nicht geöffnet werden. Diese Wartungsversion unterstützt ES10
* FORMS-13164: Wenn der Benutzer eine PDF generiert, werden ihm nach der Übermittlung unerwartete leere Zeilen hinzugefügt.
* FORMS-13789: Wenn der Benutzer versucht, mehrere PDF zu generieren, schlägt die Ausgabe-Batch-API fehl
* FORMS-11483: Wenn ein Benutzer PDF in PDF/A-2B oder PDF/A-3B konvertiert, schlägt die Konvertierung fehl und es wird ein Validierungsfehler angezeigt.
* FORMS-10501: Wenn ein Benutzer HSM aufruft, sind die Dokumente zertifiziert, LTV wird jedoch nicht aktiviert
* FORMS-11546: Wenn ein Formularautor wiederholte Bedienfelder in einem adaptiven Formular verwendet, fehlt das ARIA-Attribut in den HTML-Tags. Dies verbessert die Barrierefreiheit wiederholter Bereiche des adaptiven Formulars
* FORMS-11826: Aufgrund der übereinstimmenden Beschriftungen Arial® labelledby und Arial® können die Bildschirmlesehilfen nicht zwischen diesen beiden unterscheiden. Um das Problem zu beheben, wird für die Formularfelder die Beschriftung „aria-labelledby“ durch „aria-describedby“ ersetzt. F). Dies verbessert die Barrierefreiheit von Adaptive Forms
* FORMS-12626, FORMS-13094: Benutzer können nicht über die Tastatur auf die Symbolleiste zugreifen, um Inhalte auf der Formulareditorseite zu speichern oder zu bearbeiten. Dieses Problem mit der Barrierefreiheit wurde behoben
* FORMS-13102: Während des Formularerstellungsprozesses fehlt es den auf der Seite &quot;Forms&quot;und &quot;Dokumente&quot;verfügbaren Symbolen an beschreibenden Funktionen für Personen mit unterschiedlichen Bedürfnissen. Dieses Problem mit der Barrierefreiheit wurde behoben

### Bekannte Probleme {#known-issues-15787}

* SITES-17934 - Inhaltsfragmente - Vorschau schlägt aufgrund des DoS-Schutzes für eine große Baumstruktur von Fragmenten fehl. Siehe [KB](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-23945)

### Eingestellte Funktionen und APIs {#deprecated-15787}

* [Einstellung der JWT-Anmeldedaten in Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

Werfen Sie einen Blick auf [Eingestellte und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) um zu erfahren, was in AEM as a Cloud Service veraltet oder entfernt wurde.

### Änderungshinweis {#change-notice-15787}

**Erforderliche Aktionen**

#### Festlegen der CM-Java-Version auf 11 {#set-java-version-11}

Die neue aem-sdk-api-Version enthält Klassen, die mit einem Java 11-Ziel kompiliert wurden und nicht mit der standardmäßigen JDK-Version 1.8 der Cloud Manager-Build-Umgebung kompatibel sind. Diese Aktualisierung erfordert, dass Maven mit JDK 11 ausgeführt wird.

Kundinnen und Kunden wird empfohlen, eine `.cloudmanager/java-version`-Datei im Stammverzeichnis ihres Git-Repositorys mit den folgenden Inhalten hinzuzufügen: `11`. Siehe [Build-Umgebung/Festlegen der Maven-JDK-Version](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#alternate-maven-jdk-version).


### Eingebettete Technologien {#embedded-tech-15787}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.60-T20240131102219-0cde853 | [Oak API 1.60.0-API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version 2.24.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
