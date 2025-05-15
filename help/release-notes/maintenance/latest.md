---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 6493c48797c09fa4598c2c0ff86c9cc1fafa758c
workflow-type: tm+mt
source-wordcount: '1448'
ht-degree: 15%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 20783 {#20783}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 20783, die am Mittwoch, 13. Mai 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 20626.

Die Funktionsaktivierung von 2025.5.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-20783}

* FORMS-19125: Der Editor für adaptive Formulare der Kernkomponente wurde verbessert, um die automatische Zuordnung verfügbarer adaptiver Formularfragmente zu unterstützen, wenn ein entsprechender Abschnitt aus der Datenquellenstruktur auf der Arbeitsfläche des Formulars abgelegt wird. Dies bringt eine wichtige Produktivitätsfunktion vom Foundation-Editor zu den Kernkomponenten.
* FORMS-17107: AEM Forms bietet jetzt ein verbessertes Client-seitiges benutzerdefiniertes Funktions-Parsing. Dazu gehört die Unterstützung moderner JavaScript-Funktionen (ECMAScript ES10+), z. B. die optionale Verkettung, und es wird die Möglichkeit eingeführt, statische Importe in benutzerdefinierten Funktionsskripten zu verwenden. Auf diese Weise können Entwickelnde Code besser organisieren, ESM-Module verwenden und frühere Einschränkungen entfernen, die bei benutzerdefinierten Funktionen in Adaptive Forms auf der Grundlage von Kernkomponenten und Edge Delivery Services aufgetreten sind, insbesondere für Benutzende, die zuvor Problemumgehungen für diese Funktionen benötigten.
* SITES-27775: Optimierte Referenzsuche während der Veröffentlichung.
* SITES-30885: Optimierte JSON-Verarbeitung in persistierten Abfragen.
* SITES-25433: Edge Delivery mit universellem Editor: Unterstützt das vollständige Seiten-Rendering beim Vergleichen alter Versionen.
* SITES-27792: Edge Delivery mit universellem Editor: Spezifische Vorlage für Edge Delivery-Service-Konfigurationen hinzufügen
* SITES-19754: Edge Delivery mit universellem Editor: Überzeugende Fehlermeldung, wenn das Setup beschädigt ist.
* SITES-30328: Edge Delivery mit universellem Editor: Vorschau von der Sidekick-Unterstützung.
* SITES-23499: Edge Delivery mit universellem Editor: Lassen Sie die Verwendung mehrerer Felder für Blockoptionen zu.
* SITES-29987: Hinzufügen einer Funktion zum Festlegen von `previewUrlPattern` beim Erstellen von Inhaltsfragmentmodellen.
* SITES-29874: Hinzufügen von Unterstützung für LongTextField-Verweise in der Inhaltsfragment-API.
* SITES-29601: Hinzufügen einer Validierung für Inhaltsfragmente, auf die über LongText-Felder verwiesen wird.
* SITES-24623: Machen Sie von GET und der SEARCH Fragments-API zurückgegebene E-Tags für Patches nutzbar.
* SITES-28557: URL-`references` im PATCH-Inhaltsfragment zulassen.
* SITES-5358: [OpenAPI] Kopieren von Inhaltsfragmenten mit untergeordneten Elementen.
* SITES-29614: GET-Workflow-Endpunkt.
* SITES-29615: Auflisten der Batch-Anforderungen API-Endpunkt.
* SITES-25130: Aktualisieren der Kernkomponenten auf 2.28.0
* SITES-10575: „MSM Blueprint Bloomfilter Loader“ versucht, >100&#39;000 Zeilen zu laden.
* SITES-26711: Links für RTE-Textfelder werden nicht so aktualisiert, dass sie auf die Live Copy beim MSM-Rollout verweisen.
* SITES-25976: Links in Experience Fragments werden nach dem MSM-Rollout nicht angepasst.

### Behobene Probleme {#fixed-issues-20783}

* ASSETS-50994: Eingehender Traffic wird bei AemRequestEventFilter blockiert.
* CQ-4358591: Fehlende Projekte für einige Sprachen, wenn Sprachkopien über das Bedienfeld „Sites-Referenz“ mit der Option „Übersetzungsprojekte erstellen“ erstellt werden.
* CQ-4359108: Das XLIFF 2.0-Format schlägt bei der Verwendung des Imports/Exports für menschliche Übersetzung fehl.
* CQ-4358722: Die Lokalisierung funktioniert aufgrund unterschiedlicher Gebietsschema-Codes in Java 11 und Java 17 nicht für ältere ISO-Codes.
* FORMS-19808: Beim Speichern eines großen Formulars, das Fragmente enthält, die für verzögertes Laden aktiviert wurden, können Entwürfe nicht vom Benutzer abgerufen werden.
* FORMS-19887: Ein Dropdown-Feld in einem XFA-Formular, das zunächst auf den schreibgeschützten Zugriff festgelegt war, ändert sich nicht in einen Status „offen/bearbeitbar“, wenn das Formular in HTML5 gerendert wird. Das Feld bleibt schreibgeschützt und verhindert Benutzerinteraktionen, im Gegensatz zum PDF-Rendering, bei dem es wie erwartet funktioniert.
* FORMS-19651: Im Regeleditor funktioniert eine Regel nicht ordnungsgemäß, wenn ein Schaltflächenklick in einer binären Bedingung verwendet wird. Dieselbe Schaltfläche wird auch in der „then“-Anweisung dieser Regel verwendet.
* FORMS-19628: In einem automatisch generierten Datensatzdokument (DoR) für das auf Kernkomponenten basierende adaptive Forms wird beim Ausschließen des Titels eines verschachtelten Bereichs aus dem DoR fälschlicherweise der Titel des Stammbereichs ausgeblendet, wenn im Stammbereich die Option „Rich-Text für Titel zulassen“ aktiviert ist.
* FORMS-18977: PDFs, die vom Datensatzdokument-Service (DoR) generiert wurden, fehlt der Dokumenttitel. Dies kann zu Verstößen gegen die Barrierefreiheitsstandards von PDF/UA und WCAG 2.1 führen, da der Dokumenttitel ein erforderliches Attribut für barrierefreie PDFs ist.
* FORMS-18526: Wenn eine Regel, die mehrere Felder in ihren Bedingungen enthält, von einem Feld in ein anderes kopiert wird, behält ein fester Feldverweis innerhalb dieser Bedingungen fälschlicherweise den Verweis auf das ursprüngliche Quellfeld bei, anstatt auf das neue Feld zu aktualisieren, in das die Regel kopiert wird.
* FORMS-19047: Nachdem ein adaptives Formular geändert und erneut in AEM Forms veröffentlicht wurde (insbesondere 6.5.22.0), fehlen möglicherweise Übersetzungen für bestimmte Formularelemente, insbesondere für Textfelder.
* FORMS-19234: Die Zeitleisten-Funktion für PDFs in AEM Forms, mit der Benutzende Details zur Erstellung und Versionierung einer PDF anzeigen können, funktioniert nicht mehr, nachdem eine PDF unter dem Abschnitt &quot;Forms und Dokumente“ hochgeladen wurde.
* FORMS-18196: Die `generatePrintedOutput` (oder `generatePdfOutput`) Synchronisierungs-HTTP-API gibt fälschlicherweise einen 200-Antwort-Code (Erfolg) anstelle des erwarteten 400-Fehler-Codes (Bad Request) zurück, wenn die optionalen, für die XDP-Vorlage erforderlichen Felddaten in der Anfrage leer bleiben.
* FORMS-19336: Im Kernkomponenten-Editor für adaptive Formulare (AF2-Editor) funktioniert die Suchfunktion in der Data Source Tree nicht ordnungsgemäß oder nicht wie erwartet, was Benutzende daran hindert, bestimmte Datenelemente einfach zu finden.
* FORMS-17707: Der AEP (Adobe Experience Platform)-Connector funktioniert nicht ordnungsgemäß, wenn er für die Verbindung mit Staging-Umgebungen der AEP-Plattform konfiguriert ist.
* FORMS-18526: Beim Kopieren einer Regel, deren Bedingungen auf mehreren Feldern basieren, wird ein Feld, auf das in den Bedingungen oder Aktionen der Regel verwiesen wird (d. h. nicht das primäre Feld, das die Regel auslöst), nicht aktualisiert und verweist nicht korrekt auf das neue Feld, in das die Regel kopiert wird. Stattdessen verweist sie weiterhin auf das ursprüngliche Quellfeld, aus dem die Regel kopiert wurde.
* FORMS-18474: Eine Regel, die den Fokus auf ein bestimmtes Bedienfeld oder eine bestimmte Komponente legt, wenn sich der Wert eines bestimmten Felds ändert (z. B. Feld „A„), was fälschlicherweise durch eine Änderung in einem beliebigen Formularfeld ausgelöst wird. Wenn beispielsweise das Feld „B“ geändert wird, ist der Fokus weiterhin auf den vorgesehenen Bereich festgelegt, obwohl die Regel nur für Änderungen am Feld „A“ konfiguriert wurde.
* GRANITE-58276: OSGi-Abhängigkeitszyklen verhindern, dass die HTL Script Engine Factory ordnungsgemäß funktioniert.
* OAK-11673: Oak-segment-azure v12 CPU Anstieg verursacht durch refreshLease.
* SITES-30752: Verwenden Sie beim Generieren einer persistenten Abfrageantwort keine `If-modified-since`-/`last-modified`-Kopfzeilen.
* SITES-30353: GraphQL DataFetchingExceptions für das Feld „src“ in AEM-Inhaltsfragmenten.
* SITES-30333: Lesen von Asset-Metadaten aus jcr, um Probleme beim Parsen von XMP zu vermeiden.
* SITES-30140: Problem mit zwei Fenstern beim Erstellen eines Inhaltsfragmentverweises.
* SITES-29748: Korrigieren Sie die Render-Bedingungen, um im CF-Editor verwaltete Veröffentlichungs-/Schnellveröffentlichungsaktionen anzuzeigen.
* SITES-15452: Eindeutige CF-Elemente sollten beim Launch nicht mit ihren Kopien verglichen werden.
* SITES-30386: Edge Delivery mit universellem Editor: Duplizierte UE cors.js führt dazu, dass UE beim Hinzufügen von Inhalten Abschnitte dupliziert.
* SITES-29745: Es wurde ein seltenes Problem behoben, bei dem Variationen von Verweisen nicht hydratisiert waren.
* SITES-30585: „previewUrlPattern“ kann beim Erstellen von Modellen mit Verweisen nicht festgelegt werden.
* SITES-30327: Durch das Veröffentlichen von Inhaltsfragmenten ohne Berechtigungen werden separate Workflows für jede Payload-Ressource erstellt.
* SITES-29528: ETag kann nicht für das Caching auf einer Veröffentlichungsinstanz verwendet werden.
* SITES-30583: Tool zum Suchen und Ersetzen, mit dem alle Zeichen in Kleinbuchstaben geändert werden.
* SITES-31157: Patch schlägt aufgrund von inkonsistentem E-Tag fehl.
* SITES-31327: [OpenAPI] Die Anforderung eines Inhaltsfragments in der Autoreninstanz kann mit 304 antworten.
* SITES-29691: NullPointerException beim Versuch, eine Seite zu verschieben.
* SITES-30728: OnTime/OffTime veröffentlicht/hebt die Veröffentlichung nicht wie erwartet auf, wenn es in den Asset-Eigenschaften konfiguriert wurde.
* SITES-29789: Änderung des Komponentenlinks auf kopierten Stammseiten in AEM.
* SITES-29191: Es können nicht mehr als 20 SKUs zur Produktlisten-Komponente hinzugefügt werden.
* SITES-30372: Smartes Zuschneiden funktioniert nicht auf der AEM-Kernkomponente „Bild (V2)“.
* SITES-28693: Die Teaser-Komponente rendert fehlerhafte HTML, wenn der Titel leer ist.
* SITES-28668: Launch kann nicht mit LaunchPromotionParameters beworben werden.
* SITES-31005: Verbesserte Benutzeroberfläche für Rollout-Aufträge , um dem Kunden den Fortschritt anzuzeigen.
* SITES-31020: Verbesserte Benutzeroberfläche zum Erstellen von Live Copy-Aufträgen , um dem Kunden den Fortschritt zu zeigen.
* SITES-29816: Fehler „Ressource nicht gefunden“ beim Erstellen einer Live Copy des Experience Fragments.
* SITES-29363: Die Schaltfläche „Live Copy zurücksetzen“ funktioniert nicht für eine verschachtelte Live Copy-Inhaltshierarchie.
* SKYOPS-106509: Zusätzliche Add-Open-Flags zur Unterstützung des GSON-reflektierenden Zugriffs auf Java 21 hinzufügen.

### Bekannte Probleme {#known-issues-20783}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-20783}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-20783}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 19 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-20783}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,78,1-T20250429061757 | [Oak-API 1.78.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.78.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.29.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
