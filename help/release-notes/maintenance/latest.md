---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 0f16c31a5fea1fc538fbeabe6db182ad3a30560d
workflow-type: tm+mt
source-wordcount: '1619'
ht-degree: 13%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 21772 {#21772}

Im Folgenden finden Sie eine Zusammenfassung der kontinuierlichen Verbesserungen für die Wartungsversion 21772, die am Donnerstag, 6. August 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 21706.

Die Funktionsaktivierung von 2025.8.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Neue Funktionen  {#new-features-21772}

* SITES-30049: Neuer Endpunkt zum Abrufen der Sprachkopien eines Inhaltsfragments anhand seiner UUID hinzugefügt.

### Verbesserungen {#enhancements-21772}

* CQ-4358722 : Es wurden Lokalisierungsprobleme behoben, die durch unterschiedliche Gebietsschema-Codes zwischen Java 11 und Java 17 verursacht wurden.
* FORMS-19624: Interaktive Kommunikation (IC) aktiviert. Sie ermöglicht Unternehmen die Bereitstellung personalisierter On-Demand-Kommunikation, z. B. Kontoauszüge, Rechnungen und Korrespondenz, indem strukturierte Vorlagen mit dynamischen Daten kombiniert werden. Mit Funktionen wie Web-basiertem Vorlagendesign, wiederverwendbaren Inhaltsfragmenten, regelbasierten Varianten und nahtloser Datenintegration ermöglicht IC eine konsistente und skalierbare Kundenkommunikation über alle Kanäle hinweg.
* FORMS-19587, FORMS-17107, FORMS-19591, FORMS-19582, FORMS-20129, FORMS-20002, FORMS-19593, FORMS-20655, FORMS-19583, FORMS-18024, FORMS-19581: Der Regeleditor für adaptive Forms wurde folgendermaßen verbessert:
   * Die `validate` in der Funktionsliste kann jetzt Bereiche, Felder und Formulare überprüfen.
   * Verbessertes Client-seitiges Analyse benutzerdefinierter Funktionen zur Unterstützung von ES10+-Funktionen und statischen Importen.
   * Im Regeleditor wurde eine vordefinierte Schaltfläche zum Herunterladen des Datensatzdokuments (DoR) hinzugefügt.
   * Es wurde Unterstützung für dynamische Variablen in Regeln hinzugefügt.
   * Erstellung von Regeln basierend auf benutzerdefinierten Ereignissen ermöglicht.
   * Regeln für wiederholbare Bereiche werden jetzt im richtigen Kontext und nicht nur in der letzten Bereichsinstanz ausgeführt.
   * Regeln können jetzt auf der Grundlage von Abfrageparametern, UTM-Parametern und Browser-Parametern ausgelöst werden.
   * Es wurde Unterstützung für formularspezifische benutzerdefinierte Funktionsskripte im EDS (Experience Data Store) hinzugefügt.
   * Es wurde Unterstützung für die Verwendung von `EVENT_PAYLOAD` in der Aktion „Navigieren zu“ im Erfolgs-Handler des Regeleditors hinzugefügt.
   * Unterstützte Funktionsaufrufe innerhalb von Eingabeparametern im Regeleditor und sichergestellte Regeln werden nicht gespeichert, wenn im Funktionsaufruf erforderliche Parameter fehlen.
   * Beschädigte Regeln in der Benutzeroberfläche des Regeleditors hervorgehoben.
* FORMS-18450: reCAPTCHA V2 (einschließlich unsichtbarem reCAPTCHA) ist jetzt in adaptivem Forms einfacher einzurichten und zu verwenden. Die Konfiguration wird jetzt an einem Ort verwaltet, sodass Sie den Spam-Schutz in Ihren Formularen einfacher aktivieren können.
* FORMS-18385: Es wurde Unterstützung für die AFP-Generierung von XDP- und -Daten in AEM Forms über den Ausgabe-Service hinzugefügt.
* FORMS-17789: Dem Herunterladen des Datensatzdokuments (DoR) wurde eine vordefinierte Schaltfläche im Regeleditor hinzugefügt.
* FORMS-20313, FORMS-2896: Es wurde Unterstützung für die `dorExclude` hinzugefügt, um bestimmte Funktionen in Kernkomponenten-basierten Formularen zu deaktivieren.
* FORMS-20262: Verarbeitet ungültige Dateianhänge (0 Byte) auf der Client-Seite.
* FORMS-18347: Verbesserte Protokollierung des adaptiven Forms-Editors für fehlende Formular-Container-Proxy-Komponenten.
* FORMS-16205: Ausschließen deaktivierter Komponenten aus dem Datensatzdokument (DoR) in Kernkomponenten-basierten Formularen.
* FORMS-10836: Geänderte Ausrichtung der Master-Seiteneigenschaften im Datensatzdokument (DoR) für Sprachen mit Rechts-nach-links-Schreibrichtung.
* SITES-33025: Neuen CF-Editor über ID statt Pfad öffnen.
* SITES-32741: Asynchrone Aktualisierung von Seitenverweisen auf Inhaltsfragmente durch Trigger.
* SITES-32087: GraphQL: Hinzufügen von Unterstützung für `_ignoreCase` auf StringArray.
* SITES-12211: Verbesserte Leistung im Vorlageneditor
* SITES-32861: Leistungsverbesserung für die Erstellung von Live Copies durch segmentierte Verarbeitung.
* SITES-21383: Leistungsoptimierung für Löschvorgänge von Inhaltsfragmenten beim Start.
* SITES-31165: Leistungssteigerung durch die Aufteilung von Rollout-Vorgängen in verwaltbare Blöcke.
* SITES-21353: Verbesserung der Abfrageleistung für Inhaltsfragment-Launches mithilfe der Datenbankindizierung.
* SITES-30495: Verbesserung zur Unterstützung von UUID-basierten Fragmentverweisen in Inhaltsfragment-Launches.
* SITES-32151: API-Verbesserung, die Container-Eigenschaftsfunktionen verfügbar macht.
* SITES-26849: Passen Sie Rückverweise an, wenn eine Inhaltsfragmentvariante verschoben oder gelöscht wird.
* SITES-31846: Fügen Sie die Option zum Kopieren/Einfügen von Stammfragmenten und Verweisen in denselben Ordner für den Vorgang zum Kopieren der Baumstruktur hinzu.
* SITES-30241: Passen Sie Verweise an, die sich in einem Langtextfeld befinden, wenn Sie ein Fragment verschieben, umbenennen oder löschen.
* SITES-32684: Verbesserter Mechanismus zum Synchronisieren von Registerkartenänderungen im Benutzeroberflächenschema.
* SITES-33308: Hinzufügen eines Wiederholungsmechanismus zum Synchronisieren von Änderungen am Benutzeroberflächenschema beim Bearbeiten von Modellen.
* SITES-32247: Fehlende Dialogfeldausrichtung bei Personalization und UI in der Komponente „Text und Personalization&quot;.
* SITES-32261: Experience Fragment i18n wurde nicht auf das Feld angewendet.
* SITES-32666: Vorlagenprädikat enthält `\n`, die dazu führen, dass die HTML-Suche fehlschlägt.
* SITES-32674: Die Bildauswahl für vorgestellte Bildfelder funktioniert trotz `cq:showOnCreate` nicht für den Seitenerstellungsassistenten.
* SITES-32014: Edge Delivery mit universellem Editor: Hinzufügen der automatischen Konfiguration von CORS-Richtlinien für localhost, aem.page und aem.live
* SITES-26532: Edge Delivery mit universellem Editor: Unterstützung für lokalisierte URLs hinzufügen (früher Zugriff).
* SITES-30887: Hinzufügen von in Workflow-Metadaten gespeicherten Inhaltsfragment-UUIDs.

### Behobene Probleme {#fixed-issues-21772}

* CQ-4360190: Es wurde ein `UnsupportedOperationException` behoben, das beim Versuch auftrat, „add“ für ein keySet zu verwenden, das den Vorgang nicht unterstützt.
* CQ-4360421: Es wurde ein Problem mit der Verschlüsselung des Microsoft Translator-Abonnementschlüssels behoben, um die Sicherheit und Kompatibilität zu verbessern.
* FORMS-20980: Probleme mit der Barrierefreiheit der Tastatur in der Datumsauswahl mit dem benutzerdefinierten Anzeigeformat in adaptivem Forms wurden behoben.
* FORMS-20498: Es wurde eine Prüfung auf Nullzeiger-Ausnahmen in OdataResponse hinzugefügt, um Laufzeitfehler zu vermeiden.
* FORMS-20947: Behebung mehrerer Probleme im Zusammenhang mit der Barrierefreiheit, einschließlich Verstößen gegen Bildschirmlesehilfen und Problemen beim Abschneiden/Überlappen von Text.
* FORMS-21030, FORMS-20630: Gelöste Probleme mit Dropdown-Feldern, die für mehrere Auswahlen in adaptiven Formularen konfiguriert sind. Die generierte PDF enthält jetzt alle ausgewählten Werte korrekt.
* FORMS-19579: Es wurde ein Problem behoben, bei dem die Regel „Dienst aufrufen“ beim erneuten Speichern nicht automatisch korrigiert wurde.
* FORMS-20734: Fehlerkorrektur - Das Duplizieren von Signaturfeldern in PDF-Dokumenten, die vom Output-Service für XFAF-basierte PDF-Eingabevorlagen generiert wurden, wurde korrigiert.
* FORMS-20934: Das Dropdown-Menü für das Attribut für automatisches Ausfüllen in der Authoring-Benutzeroberfläche von AEM Forms wurde korrigiert, um doppelte Einträge zu entfernen und alle standardmäßigen Token für die automatische Vervollständigung von HTML einzuschließen.
* FORMS-20700: Das Flackern des Dropdown-Hilfetextes beim ersten Laden in AEM Forms wurde behoben.
* FORMS-20307: Es wurde ein Problem behoben, bei dem auf einer Sites-Seite eingebettete Formulare nicht mit 4-stelligen Gebietsschemata übersetzt wurden.
* FORMS-20493: Es wurde das Problem behoben, bei dem Formulare beim Abrufen von Daten automatisch aktualisiert wurden, was zu Unannehmlichkeiten für Benutzende führte.
* FORMS-18455: Der adaptive Forms-Editor für Kernkomponenten wurde verbessert, sodass nun Punkte für verwendete Datenobjekte in der Datenquellenstruktur angezeigt werden können.
* FORMS-19373: Es wurden Replikationsfehler für Veröffentlichungsumgebungen verhindert, in denen keine Replikationsagenten konfiguriert sind.
* FORMS-20042: Fehlerkorrektur - Die beschädigte Eigenschaftenansicht wurde korrigiert, die durch die Apache Sling GET Servlet-Konfiguration mit aktivierter HTML-Konfiguration verursacht wurde.
* FORMS-20036, FORMS-19978: Behobene Probleme mit der Einhaltung von PDF/A-1b und der Validierung.
* FORMS-19166: pagedatasource.jsp wurde in das Servlet verschoben, um die Klarheit der Fehlerstapelablaufverfolgung zu verbessern, und es wurden weitere Leitplanken und Protokollierungen hinzugefügt.
* FORMS-16466: Es wurden Probleme behoben, bei denen wiederholbare Bereiche in AEM Forms nicht korrekt ausgefüllt wurden.
* FORMS-19629: Behobene Probleme beim Parsen des Kunden-JSON-Schemas mit ungültigen Ergebnissen.
* LC-3923083: Fehler „Pfadobjekt nicht getaggt“ für umrandete Elemente in XDP-Vorlagen wurde behoben.
* SITES-33177: Edge Delivery mit universellem Editor: Korrigieren Sie fehlerhafte Abschnittsstile, wenn sie als kommagetrennte Zeichenfolgen gespeichert werden.
* SITES-33262: Edge Delivery mit universellem Editor: Korrigieren von Blöcken ohne Umbruch des Seitenrenderings und der Veröffentlichung mit Namen.
* SITES-33309: Edge Delivery mit universellem Editor: `IllegalArgumentException` beim Schreiben in eine Tabelle mit einem Schrägstrich in Spalten beheben.
* SITES-33408: Edge Delivery mit universellem Editor: Tabellen korrigieren, die nach Änderungen nicht als geändert angezeigt werden.
* SITES-31992: GraphQL: Beheben Sie sporadische Fehler beim Scannen von Modellen während des Bundle-Starts.
* SITES-29967: GraphiQL: Lange Abfragenamen sind abgeschnitten.
* SITES-26266: Inhaltsverweise, die nicht mit `/` beginnen, werden nicht von der BE-Antwort (Java-API) zurückgegeben.
* SITES-17874: Persistierte Abfragen von GraphQL: Fehlerbehebung bei der Codierung für den Inhaltstyp application/graphql-response+json.
* SITES-24506: Sprachausgaben werden über Suchergebnisse informiert.
* SITES-25268: Verbesserungen der Sprachausgabe für Anmerkungen.
* SITES-32366: Ergebnisse der Rechtschreibprüfung verborgen hinter dem RTE-Dialogfeld.
* SITES-32829: Verbesserungen am MediaQuery-Emulator zum Analysieren der Medienabfrage auf Ebene 3 und 4.
* SITES-32278: Taggen von Feldern korrigiert, um die Feldbezeichnung korrekt zu verwenden.
* SITES-25244: Horizontale Leiste wird im Bildmodal nicht mehr angezeigt.
* SITES-33395: Rollout-Schaltflächenfunktion für die Synchronisierung der Live Copy von Inhaltsfragmenten wurde korrigiert.
* SITES-33147: Es wurde ein Problem mit der Service-Bindung behoben, das die Live-Beziehungsfunktion beeinträchtigte.
* SITES-33528: Problem mit der Beibehaltung von Zeitstempeln während der Launch-Promotion wurde behoben.
* SITES-33014: Übermäßige Warnungsprotokollgenerierung von LaunchesAdapterFactory wurde behoben.
* SITES-32305: Die Funktion zum Unterbrechen der Live Copy-Vererbung nach Layout-Änderungen wurde korrigiert.
* SITES-32268: Deaktivieren der URL-Codierung für die Inhaltsfragmentsuche.
* SITES-32772: Eigenschaft, die in den Feldern der Variante gesperrt ist, war immer falsch, wenn die Verbesserungen von SITES-31455 aktiviert wurden - im Zusammenhang mit der Vereinheitlichung des eTag-Werts.
* SITES-32696: Es wurde ein Problem behoben, bei dem ein Live Copy-Feld für Inhaltsfragmente mit gebrochener Vererbung nicht mehr bearbeitet werden konnte.
* SITES-31712: Langsame Abfragen über die Omni-Suche in der Produktions-Autoreninstanz.
* SITES-33039: Seitenereignisse werden nicht korrekt ausgelöst.
* SITES-31192: Experience Fragments verlieren den Versionsverlauf nach dem Verschieben.
* SITES-33529: Fehler beim Verknüpfen der ACS-Kampagnenvorlagen mit AEM-Seiten.
* SITES-33678: Ein Umschalter für SITES-33529 hinzufügen.
* SITES-33468: AEMaaCS kann keine Verbindung zu ACS herstellen.

### Geänderte Funktionalität {#altered-functionality-21772}

* SITES-26344: Vereinheitlichen der Validierung von `fragmentId`/`modelId` zwischen Endpunkten - diese IDs werden jetzt validiert, und es wird ein 400-Status-Code zurückgegeben, wenn sie nicht gültig sind.
* SITES-29598: Überprüfen von Inhaltsfragmentverweisen, die in Fragmentverweisfeldern hinzugefügt werden, wenn ein Inhaltsfragmentmodell aktualisiert wird.

### Bekannte Probleme {#known-issues-21772}

* SITES-31791: Inhaltsfragmente GraphQL - Abfrage schlägt fehl mit „Maximale Feldanzahl überschritten“. Siehe [Knowledgebase-Artikel](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27231).

### Eingestellte Funktionen und APIs {#deprecated-21772}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-21772}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 35 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.


### Eingebettete Technologien {#embedded-tech-21772}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.80.0 | [Oak-API 1.80.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.63 | [Apache Httpd 2.4.63](https://github.com/apache/httpd/blob/2.4.63/CHANGES) |
| AEM-Kernkomponenten | 2.29.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |

