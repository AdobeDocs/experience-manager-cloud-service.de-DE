---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 5f37aea31823e45298cf1cb57461d01b4634b5cf
workflow-type: tm+mt
source-wordcount: '1561'
ht-degree: 13%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 24678 {#release-24678}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 24678, die am Donnerstag, 4. März 2026 veröffentlicht wurde. Die vorherige Wartungsversion war Version 24464.

Die Funktionsaktivierung von 2026.3.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-24678}

* FORMS-18927: Benutzerdefinierte MIME-Typen und Dateierweiterungen werden nun in der AEM Forms-Dateianlagenkomponente unterstützt, sodass Benutzende eine größere Auswahl an Dokumenttypen anhängen können.
* FORMS-18211, FORMS-22936: Bei Benutzenden trat ein Barrierefreiheitsproblem auf, bei dem Kontrollkästchen innerhalb eines `<fieldset>` nicht korrekt gruppiert wurden, wobei die Gruppentitel nicht in einem `<legend>` als erstes untergeordnetes Element verschachtelt war. Dies betraf Benutzende mit Behinderungen, die für die Navigation auf Bildschirmlesehilfen angewiesen sind. Die auf Kernkomponenten basierende adaptive Forms hat jetzt die Unterstützung von Feldsets und Legenden eingeführt, um die Barrierefreiheit zu verbessern.
Es wurde die Option Feldsatz im Bedienfeld hinzugefügt, mit der Benutzende verwandte Felder in ihren Formularen effektiver organisieren und gruppieren können.
* FORMS-23880: Design-Editor wird in Kernkomponenten unterstützt. Diese Verbesserung ermöglicht es Benutzenden, Designs innerhalb der Kernkomponenten effizienter anzupassen und zu verwalten, wodurch ihre Designflexibilität und ihr Arbeitsablauf verbessert werden.
* FORMS-21772: Versionsunterstützung wurde zur Forms-Verwaltungsoberfläche hinzugefügt. Diese Verbesserung ermöglicht es Benutzenden, Versionen für Kernkomponenten und Foundation-Komponenten zu erstellen und abzurufen, die auf adaptivem Forms, Formularfragmenten, Designs und binärem Assets basieren, und verbessert so die Asset-Verwaltung und Versionskontrolle.
* FORMS-23094: Client-seitiges Parsing für Foundation-Komponenten-basiertes adaptives Forms hinzugefügt, sodass Unternehmenskunden ihre Formulare in die Cloud migrieren können. Diese Verbesserung unterstützt EcmaScript-Funktionen in den Code-Editor-Regeln, die zuvor nicht unterstützt wurden, was einen reibungsloseren Migrationsprozess erleichtert.
* FORMS-23853: Es wurde Unterstützung zum Überschreiben von reCAPTCHA in der Sling-Komponente hinzugefügt. Diese Verbesserung ermöglicht es Benutzenden, reCAPTCHA-Einstellungen anzupassen, was die Flexibilität und Sicherheit für Unternehmenskunden verbessert.
* SITES-34936: Edge Delivery mit universellem Editor: Filtern von Inhaltsfragmenten nach Modell für die Veröffentlichung hinzufügen.
* SITES-36203: Edge Delivery mit universellem Editor: Umschalten des Typs „Code hinzufügen“, um Unterstützung für mehrere Felder und zusammengesetzte Felder zu aktivieren.
* SITES-37037: Edge Delivery mit universellem Editor: Verbessern des Tabellenimports, um das Trennzeichen automatisch zu erkennen.
* SITES-37804: Edge Delivery mit universellem Editor: Hinzufügen von Unterstützung für Authoring in geschlossenen Benutzergruppen (früher Zugriff).
* SITES-38990: Edge Delivery mit universellem Editor: Hinzufügen von Unterstützung für Ausschlüsse zu Pfadzuordnungen.
* SITES-39171: Edge Delivery mit universellem Editor: Hinzufügen von Unterstützung für `cq:tags` in Blöcken und Blockelementen.
* SITES-40042: Edge Delivery mit universellem Editor: Konfigurieren Sie den Konfigurations-Service als Standard für neue Sites.
* SITES-37649: GraphQL: Unterstützt das Filtern mehrzeiliger Textfelder auf JCR-Ebene.
* SITES-37843: GraphQL: Das Filtern nach Feldern mit mehreren Werten (Sammlungen) wird auf JCR-Ebene nicht unterstützt.
* SITES-37540: Replace &amp; ReplaceAll-Vorgänge für CF-Feldwerte (Suchen und Ersetzen für einen bestimmten Feldnamen).
* SITES-37741: Fügen Sie die Eigenschaft „Karte“ in der Antwort auf die Fragmentvariante hinzu (Kartenansicht in der Admin-Benutzeroberfläche).
* SITES-37754: Veröffentlichen des Ordners über API: Strukturvalidierung bei Bedarf, wenn `validateReferences` auf „true“ gesetzt ist.
* SITES-37756: Anzeigen von Ein-/Auscheckstatusinformationen für ein Inhaltsfragment.
* SITES-37805: Schemaaktualisierung: Geänderte Fragmente können nicht umbenannt/verschoben werden (Dokumentation).
* SITES-37847: Verbesserte Leistung für die Abfrage von Lent Content ReferenceProvider SQL-2 (LentContent retrieve).
* SITES-39255: Aktualisieren der OpenAPI-Implementierung auf die neuesten Java-API-Änderungen für das zusammengesetzte Feld.
* SITES-37096: Die Langsamkeit der Launch-Konsole wurde entfernt, wenn verwaiste Knoten vorhanden sind.
* SITES-38117: Eine Möglichkeit finden, untergeordnete Launches ohne Leistungseinbußen abzufragen.
* SITES-38317: Benutzer, der den Workflow gestartet hat, zu den Metadaten hinzufügen (tatsächlicher Benutzer statt allgemeiner, wenn er von einem Dienstbenutzer ausgeführt wird).
* SITES-39203: Zeigt an, wer den Workflow gestartet hat (anstelle des allgemeinen Benutzers, wenn er vom Dienstbenutzer ausgeführt wird).
* SITES-13083: Lokalisieren von Fehlerzeichenfolgen im Dialogfeld Sites > Live Copy-Erstellung .
* SITES-13389: Lokalisieren Sie die Zeichenfolge „Erstellte Version von … vor dem Hochstufen des Launches“ in Sites > Zeitleiste.
* SITES-16176: Lokalisieren von Zeichenfolgen im Seiteneditor > Dialogfeld „Konfiguration der Bild-v3-Komponente“.
* SITES-35702: Nicht lokalisierte Zeichenfolge „Live Copy aktuell mit begrenzter Vererbung“ auf der Registerkarte „Live Copy-Übersicht“.
* SITES-35748: Nicht lokalisierte Kontrollkästchen „Auswahl der Produktvariante aktivieren“ im „Inhaltsfragmentmodell-Editor“.
* SITES-35750: Nicht lokalisierter Platzhalter „Produkt-SKU(s), durch `#` Zeichen getrennt“ im Eingabefeld im „Inhaltsfragmentmodell-Editor“.
* SITES-37113: Nicht lokalisiertes Dialogfeld „Vererbung abbrechen“ auf der Registerkarte &quot;CIF-Konfigurationen“.
* SITES-25240: Fehlerbehebung bei der Barrierefreiheit für das Teaser-Modal call to action.
* SITES-25531: Behebung der Barrierefreiheit für den Farbkontrast im Suchmodal.
* SITES-37115: Abgeschnittene Symbole im Wiener Demo-Store.

### Behobene Probleme {#fixed-issues-24678}

* CQ-4361552: i18n-JSON-Wörterbuch korrigiert, das in HTML mit Escape-Zeichen versehene Unicode in Importübersetzungen beibehält.
* CQ-4361634: Experience Fragments können nicht ausgewählt werden und werden nicht zum Übersetzungsprojekt hinzugefügt.
* CQ-4362072: Fehlerkorrektur: Der Schritt „AEMaaCS-Übersetzungs-Workflow - DE > ES“ kann keine Seite zum Übersetzungsprojekt hinzufügen.
* FORMS-23741: Es traten Probleme auf, bei denen die Upload-Schritte „InvokeDDX“ und „Asset“ nicht kaskadierend ausgeführt wurden, sodass zwei separate Workflow-Ausführungen erforderlich waren. Dies wirkte sich auf die Produktionsumgebung mit AEM as a Cloud Service mit dem Sites- und Forms-Add-on aus.
* FORMS-23877: Bei der Erstellung von Formularen direkt auf Sites-Seiten mit einer älteren Kernkomponentenversion traten Probleme mit benutzerdefinierten Funktionen auf, die nicht zur Laufzeit geladen wurden.
* FORMS-24038: Bei Benutzenden traten Probleme mit der Navigationsschaltfläche auf, wenn dynamisch weitere Registerkarten hinzugefügt wurden.
* FORMS-23721: Es wurde ein Problem behoben, bei dem Überprüfungsmuster, die für Texteingaben im Dialogfeld „Bearbeiten“ konfiguriert wurden, nicht beibehalten wurden. Zuvor wurde der Musterwert gespeichert, aber nicht beibehalten oder in der Benutzeroberfläche angezeigt, was bei Formularautoren zu Verwirrung führte.
* FORMS-23456: Bei der Verwendung der Tabellenkomponente in Adaptive Forms sind auf Mobilgeräten von Sprachausgaben falsche Ankündigungen für ausgeblendete Kopfzeilen in einer Tabelle aufgetreten. Ein ausgeblendeter Tabellenkopf wurde aus dem Kontext angekündigt, was bei Benutzern, die auf iOS VoiceOver und Android TalkBack angewiesen sind, zu Verwirrung führte.
* FORMS-23454: Bei der Datumsauswahl für auf Kernkomponenten basierende adaptive Forms sind Probleme aufgetreten. Bei der Eingabe ungültiger Datumswerte wird das System automatisch auf mögliche geschlossene Datumswerte korrigiert.
* FORMS-23117: Es kam vor, dass hCAPTCHA in Foundation-Komponenten, die auf adaptivem Forms basieren, nicht korrekt übersetzt wurde.
* FORMS-22634: Bei Benutzenden trat ein Problem auf, bei dem E-Mail-Anhänge nicht enthalten waren, wenn sowohl die Optionen „Anhang einschließen“ als auch &quot;HTML-Vorlage verwenden“ verwendet wurden.
* FORMS-23288: Es sind Probleme mit Adaptive Forms aufgetreten, das in die Asset Share Commons-Modale eingebettet ist. Das Formular konnte nicht korrekt geladen werden, wenn die URL in der Mitte des Pfads `.html`.
* FORMS-19198: Beim Einbetten von Formularen mit Dispatcher-Regeln sind 404-Fehler aufgetreten. Die Fehler sind bei URLs wie /etc.clientlibs/toggles.json, der RUM-Bibliothek und analyticsparserconfigparser.json aufgetreten, da der URL-Rewriter diese URLs nicht neu schreiben konnte.
* SITES-33799: Edge Delivery mit universellem Editor: Korrigieren Sie optimierte Videoausgabedarstellungen, die nicht veröffentlicht wurden.
* SITES-35082: Edge Delivery mit universellem Editor: Entfernen leerer Absätze sowie vorangestellter und nachgestellter Zeilenumbrüche aus Rich-Texten.
* SITES-35524: Edge Delivery mit universellem Editor: Beheben von Veröffentlichungsfehlern für Pfade, die Nicht-ASCII-Sonderzeichen enthalten.
* SITES-38647: Edge Delivery mit universellem Editor: Beheben von Leistungsengpässen in Umgebungen mit vielen Sites.
* SITES-40521: Edge Delivery mit universellem Editor: Korrigieren Sie doppelte Klassennamen für Blöcke und Blockelemente.
* SITES-37887: GraphQL: UUID-Suchen nach größeren Ergebnismengen können zu verlängerten Antwortzeiten führen.
* SITES-38412: Fragmente können in Launch nicht gepatcht werden, wenn ein eindeutiges Feld/ein eindeutiger Slug vorhanden ist (die eindeutige Einschränkung schließt jetzt CFs in Launches aus).
* SITES-38606: Validierungsfehler beim Hinzufügen einer Variante zu CF mit Fragmentverweis-UUID (hydratisierte CFs, auf die in Varianten von uuid verwiesen wird).
* SITES-39489: Assets-Benutzeroberfläche mit Fragmenten aus cq:discarded-Ordnern (aus Management-API-Antworten entfernte CFs mit Soft-Löschung).
* SITES-39517: GET CF mit einem zusammengesetzten Feld, das eine Auflistung enthält, schlägt mit 500 fehl.
* SITES-40072: Zusammengesetzte Felder mit Registerkarten geben leere Platzhalterwerte zurück.
* SITES-39575: Live Copy-Speicherung entfernt `cq:rolloutConfigs` - Rollout-Konfiguration verloren.
* SITES-39694: Produktionsbereitstellungen schlagen mit NPE fehl.
* SITES-39761: NavigationItem.getLink() gibt in der Navigationskomponente von CIF v2 null zurück.
* SITES-40519: Das MSM-Rollout schlägt mit NullPointerException fehl, wenn die Live Copy-Zielressource null ist.
* SITES-17531: Hartcodierte Zeichenfolge „Smart Crop Preview“ im Seiteneditor > Bild > Smartes Zuschneiden.
* SITES-31575: Die QuickInfo „Informationen“ ist im Seiteneditor > Karussellkomponente > Eigenschaften nicht vollständig sichtbar.
* SITES-34215: Die JS-Komponente zur automatischen Vervollständigung löst einen sofortigen Validierungsfehler für das erforderliche Pfadfeld auf der Registerkarte „Dialogfeld“ aus.
* SITES-35218: Einige AEM-Kernkomponenten rendern ein leeres alt-Tag nicht ordnungsgemäß.
* SITES-37114: Abgeschnittene QuickInfo „Catalog UID-Unterstützung aktivieren“ auf der Registerkarte &quot;CIF-Konfigurationen“.
* SITES-36138: Abfrage ohne Index erkannt (Vorfall).
* SITES-37682: Außerkraftsetzung des Inhaltstyps in `/libs/cq/Page/Page.css.jsp` und `/libs/cq/Page/Page.js.jsp.`
* SITES-38709: Text-RTE der klassischen Benutzeroberfläche zeigt unbearbeitetes HTML nach dem Upgrade auf 6.5.24.
* SITES-39630: Aktualisierungen verschachtelter Inhaltsfragmente werden nicht in exportierten Target-Angeboten widergespiegelt.
* SITES-39696: Einschaltzeit/Ausschaltzeit für Planung der Aktivierung/Deaktivierung funktioniert nicht.
* SITES-39824: Beim Exportieren von Experience Fragments nach Adobe Target wird 500 (NPE) zurückgegeben.
* SITES-40253: Zeitweise 500 Fehler bei `/bin/cif/invalidate-cache` - Oak-Konflikte unter `/var/cif/cacheinvalidation`.
* SITES-40341: Korrigieren Sie base64-Inline-Bilder im styles-Tag in `HtmlToJsonConvertorImpl`.

### Bekannte Probleme {#known-issues-24678}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-24678}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-24678}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion wurden 15 identifizierte Schwachstellen behoben, was für einen noch robusteren Systemschutz sorgt.

### Eingebettete Technologien {#embedded-tech-24678}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,90,0 | [Oak 1.90.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2,30,4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |

