---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 86a25919bd35d0213c8626517411f186e5c7d8f3
workflow-type: tm+mt
source-wordcount: '1550'
ht-degree: 13%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## 26353 {#release-26353}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 26353, die am 3. Juni 2026 veröffentlicht wurde. Die vorherige Wartungsversion war Version 26309.

Die Aktivierung von Funktionen in 2026.6.0 stellt den vollständigen Funktionssatz für diese Wartungsversion bereit. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-26353}

* CQ-4360727: Es wurden Tags und Asset-Metadaten hinzugefügt und i18n-Wörterbucheintrag unterstützt für agentische Übersetzungs-Workflows in AEM Translation.
* CQ-4363507: Verbesserte Handhabung von Dispatcher mit langer Laufzeit, um die Stabilität in Übersetzungs-Workflows zu erhöhen.
* FORMS-24887: Die Generierung von Datensatzdokumenten (DoR) unterstützt jetzt das Ausschließen von Anhängen aus dem Portable Document Format (PDF) für DoR. Unternehmen können die Größe von DoR-Dateien reduzieren, wenn Anhänge separat an das Ziel gesendet werden.
* FORMS-21919: Die Generierung von Datensatzdokumenten (Document of Record, DoR) wird jetzt für adaptive Forms-Kernkomponenten unterstützt, die in Sites eingebettet sind. Autoren können DoR-Ausgaben direkt aus eingebetteten Formularen generieren, ohne Formulare aus dem Sites-Kontext zu verschieben.
* FORMS-24318: Autorinnen und Autoren können jetzt den Dokumentenablauf (`daysUntilSigningDeadline`) beim Konfigurieren der Übermittlungsaktion &quot;PDF per E-Mail senden“ in adaptiven Forms festlegen. An Adobe Sign übermittelte Vereinbarungen berücksichtigen den konfigurierten Wert, anstatt standardmäßig keinen Ablauf festzulegen.
* SITES-32578: MSM OpenAPI - Definieren des Aufrufs zum Zurücksetzen der Vererbung .
* SITES-32580: MSM OpenAPI - Trennen implementieren.
* SITES-32581: MSM OpenAPI - Zurücksetzen implementieren.
* SITES-32582: MSM OpenAPI - Implementieren des Aussetzens.
* SITES-41333: MSM OpenAPI - Implementieren einer Wiederaufnahme.
* SITES-35050: Version der Kernkomponenten 2.31.0.
* SITES-43855: Leistungsverbesserung bei der Starterstellung/Bearbeitung von Inhaltsfragmenten, die kleiner sind als die Batch-Größe.
* SITES-44267: Fehlerkorrektur - Das MSM-OpenAPI-Schema stimmt nicht mehr überein.
* SITES-44323: Entfernen des Endpunkts „Live Copy löschen“ aus dem MSM-OpenAPI-Schema.
* SITES-44430: MSM OpenAPI - Fehlerbehebung: Live Copy-ID-Validierung der Get-Vererbungsdetails.
* SITES-45016: CIF-Komponenten 2.18.4 veröffentlichen.
* SITES-11784: Inhaltsfragment-Editor: Erheblich verbesserte Ladeleistung für Fragmente, die viele Rich-Text-Editor(RTE)-Felder enthalten.
* SITES-42675: Neuer Endpunkt für die Suche nach Varianten eines bereitgestellten Inhaltsfragments eingeführt.
* SITES-32196: Vorname und Nachname der Benutzerin bzw. des Benutzers separat abrufen - API-Antworten zeigen den Vor- und Nachnamen des Erstellers/Modifikators/Herausgebers separat sowie den vollständigen Namen an.
* SITES-34223: Das Löschen von Seiten wird asynchron ausgeführt.
* SITES-42899: Weitere Versuche zum Löschen asynchroner Seiten, um die Zuverlässigkeit zu verbessern.
* SITES-42912: Leistungsverbesserungen für die Referenzanpassung beim Verschieben von Ordnern.
* SITES-43942: Edge Delivery mit universellem Editor - Veröffentlichen von Bildern, die die maximale Bildbreite und -höhe überschreiten, wird abgelehnt.
* SITES-42979: Edge Delivery mit universellem Editor - Veröffentlichen von Assets ohne Erweiterung ablehnen.
* SITES-42730: Edge Delivery mit universellem Editor - Entfernen der Editor-Instrumentierung für gesperrte Seiten.
* SITES-42706: Edge Delivery mit universellem Editor - Unterstützt Site-übergreifende Verknüpfungen bei Multi-Site-Setups.
* SITES-30753: Edge Delivery mit universellem Editor - Ersetzen Sie die Edge-Host-Konfiguration durch eine konfigurierbare Cache-TTL für die Bearbeitung.

### Behobene Probleme {#fixed-issues-26353}

* CQ-4361979: Behobene übersetzte Unterseiten, die nach der Übersetzung von Experience Fragments in AEM auf Englisch zurückgesetzt wurden.
* CQ-4362438: Interne Links in Experience Fragments wurden von der festen Sprachkopie während der Übersetzung in AEM Translation nicht neu geschrieben.
* CQ-4363421: Es wurde eine Fehlerbehebung für den Microsoft-Übersetzungs-Workflow hinzugefügt, die einen Fehler wegen ungültigem Zielsprachen-Code für vereinfachtes Chinesisch (zh-CN) für große Inhalte in der AEM-Übersetzung zurückgibt.
* FORMS-24826: Formularübermittlungen werden im Produktionsmandanten von MiniMed EForm Sandbox nicht abgeschlossen. Externe Kunden, die Formulare vor der Verwendung in der Produktion validieren, können ihre Workflows nicht abschließen.
* FORMS-25126: Der Regeleditor für adaptive Forms lässt keine Änderungen an zuvor erstellten Regeln zu, wodurch Aktualisierungen der Geschäftslogik verhindert und die Formularwartung verlangsamt werden.
* FORMS-25129: Das Umbenennen eines Felds, um Leerzeichen einzuschließen, unterbricht das Verhalten des Regeleditors. Das generierte Skript wird nicht mehr erwartungsgemäß ausgeführt, und die zugehörige Formularlogik funktioniert nicht mehr.
* FORMS-25480: Bei der Datensatzdokument-Ausgabe (DoR) aus Vorlagen mit Bedienfeldern, für die „wrapData“ auf „true“ festgelegt ist (z. B. „wrapInData.xdp„), können Bedienfelddaten weggelassen werden, was die Genauigkeit der generierten Dokumente verringert.
* FORMS-25501: Adobe Sign-Workflows verbleiben im Status „Ausstehend“, wenn der Signaturstatus nach dem Adobe Sign-Schritt nicht zurückgegeben wird, was die nachgelagerte Verarbeitung blockiert.
* SITES-24497: Orientierungspunkte desselben Typs sind nicht gekennzeichnet.
* SITES-24525: Falsche Überschriftenrolle für modale Schaltflächen wird verwendet.
* SITES-24703: Fokusanzeige für die Popup-Schaltfläche des Listenfelds ist abgeschnitten.
* SITES-25217: Infosymbol ist zu klein.
* SITES-25263: Datumsfeld im Timewarp-Modal wurde `aria-haspopup=dialog`.
* SITES-25308: Fokusanzeige von Schaltflächen in der demografischen Symbolleiste erfüllt nicht die minimalen Kontrastanforderungen.
* SITES-25364: Eingabeanweisungen sind nicht mit dem Kontrollkästchen im Code verknüpft.
* SITES-25377: Inhalt in der Seitenleiste Assets wird neu geladen, wenn das Filterfeld den Fokus erhält.
* SITES-28592: Nicht lokalisierte Zeichenfolgen im Inhaltsfragmentmodell-Editor > Dialogfeld „Modell ist gesperrt“.
* SITES-31978: Die Seitenspaltenvorschau in Sites führt zu OOM, wenn die Replikationswarteschlange riesig ist. Die Seitenspaltenvorschau lädt nicht mehr die vollständige Replikationswarteschlange in den Speicher, sodass OOM vermieden wird, wenn die Warteschlange sehr groß ist.
* SITES-37955: Edge Delivery mit universellem Editor: Beheben Sie das Überspringen von Replikationsprüfungen für referenzierte Assets.
* SITES-39242: Fehlende Miniaturansicht des Modells in der Konfiguration mit lokalisierten Zeichen im Namen in Inhaltsfragmentmodellen.
* SITES-40216: Edge Delivery mit universellem Editor: Korrigieren Sie das Rückgängigmachen der Veröffentlichung der Quellseite einer Live Copy mit aktivierten lokalisierten URLs.
* SITES-40639: Die Vererbung wird rückgängig gemacht, und die Auswahl zum Synchronisieren des CF-Elements im LC-Ordner funktioniert NICHT.
* SITES-40752: Die Komponentenliste des Seitenbereichs kann über die Tastatur aufgerufen werden.
* SITES-41121: Die Sprachausgabe gibt den Komponentennamen und einen unsichtbaren Gruppennamen aus.
* SITES-41163: Im Dialogfeld „Seitenverschiebung/erneute Veröffentlichung“ wird für seit der letzten Veröffentlichung ohne Warnung geänderte Seiten die Option „Erneut veröffentlichen“ nicht mehr vorausgewählt, um eine versehentliche Veröffentlichung von laufend bearbeiteten Inhalten zu verhindern.
* SITES-41397: ETag für Listen-/Suchprojektionszusammenfassung stimmt jetzt mit GET-by-UUID überein, wenn die Werte der Checkbox-Aufzählung in einer anderen Reihenfolge gepatcht werden, als das Modell definiert.
* SITES-41785: Falscher Stammpfad und Name hinzugefügt, um ein Live Copy-Auftragsergebnis für Seiten zu erstellen.
* SITES-41928: Die Überschneidung von ContextHub und Unified Shell macht das Komponentenmenü im Editor unzugänglich.
* SITES-42086: Verwaister Seitenknoten verbleibt nach dem Verschieben der Seite in der Vorschau - Beim Verschieben der Seite in der Vorschau wird der alte Seitenknoten vollständig entfernt, anstatt eine verwaiste `cq:Page` ohne `jcr:content` zu hinterlassen.
* SITES-42700: Der MSM OpenAPI r- Synchronize-Endpunkt gibt eine Antwort von 500 zurück, wenn keine Live Copy gefunden wird.
* SITES-42705: Die Unterbrechen der Vererbung für Miniaturansichten in den Seiteneigenschaften schützt `/jcr:content/image` Knoten nicht vor dem Rollout.
* SITES-42735: Untersuchung von Fehlern beim Erstellen von Live Copies, wenn FT_SITES-32861 aktiviert ist.
* SITES-42736: Beim MSM-Rollout wird nur der erste Hyperlink im RTE aktualisiert.
* SITES-42889: Eigenschaft „sourceRootResource“ des Seitenstarts auf der Quellseite als UUID festgelegt:referenceable wenn Mixin angewendet
* SITES-42953: Beim Rollout werden DAM-Links mit Dateierweiterungen in Großbuchstaben auf nicht vorhandene Pfade umgeschrieben.
* SITES-42986: Nicht lokalisierte Zeichenfolgen in Skyline > Commerce.
* SITES-43034: Launches - Die Spalte „Live-Datum“ wird alphanumerisch anstatt chronologisch sortiert.
* SITES-43047: Manueller Rollout für flache Live Copies nach der Version 2026.2 übersprungen.
* SITES-43116: Dialogfeld „MSM-Rollout“ bleibt stecken (Spinner wird nie abgeschlossen) - NPE in `<code>AsyncOperationServlet.doGet</code>`.
* SITES-43180: GraphQL: Es wurde ein Problem behoben, bei dem Abfragen, die doppelte Feldaliase verwendeten, unvollständige Ergebnisse zurückgaben - Unterfelder, die nur im zweiten Alias vorhanden waren, wurden leise aus der Antwort entfernt.
* SITES-43196: MSM OpenAPI - Der Aufruf „Get a Live Copy Source Details“ (Live Copy--Details abrufen) sollte 400 zurückgeben, wenn die CF keine Quelle ist.
* SITES-43197: MSM OpenAPI - `PUT /{liveCopyId}/brokenInheritanceElements` gibt bei Erfolg 204 zurück, gibt aber laut Dokumentation 200 zurück.
* SITES-43198: MSM OpenAPI - Hinzufügen einer 400-fach fehlerhaften Anfrage zum Aufrufschema „Abrufen der Details der Live Copy“ und „Abrufen der Live Copy-Quellen“.
* SITES-43413: Die Aktion „Rollout“ auf Komponentenebene löst den JS-Fehler „doRollout undefined“ aus - schlägt fehl.
* SITES-43498: Inhaltsfragment-Editor: Es wurde ein Speicherfehler für Fragmente behoben, die `DateTime` Felder enthielten, deren Millisekundenwert auf eine nachfolgende Null endet (z. B. 14:12:16.610Z).
* SITES-43516: Zeitweise auftretende Fehler bei Seitenereignissen wurden behoben
* SITES-43543: GraphQL: Fehlerkorrektur bei der Schemaerstellung, wenn Inhaltsfragmentmodelle über Tag-basierte Suchen in Konfigurationshierarchien auf andere Modelle verweisen.
* SITES-43668: Fehlerhaftes Umschreiben von URL-Verweisen während des Blueprint-Rollouts mit verschachtelten Live Copies.
* SITES-43802: Zeichenfolge „false“, die im Modal „Komponente einfügen“ auf AEM Sites angezeigt wird.
* SITES-44145: Die verschachtelte Launch-Promotion überspringt die Produktionsversion und verhindert ein Rollback.
* SITES-44204: MSM OpenAPI r- Zurücksetzen r- Etag-Pfad korrigieren, leeren Text unterstützen.
* SITES-44433: Edge Delivery mit universellem Editor: Beheben der Bereinigung von `og:image`, `twitter:image` und `og:image_secure` bei der Veröffentlichung.
* SITES-44682: Batch-Deaktivierung von Blueprint-Seiten Trigger duplizieren Rollout-Ereignisse für untergeordnete Seiten.

### Bekannte Probleme {#known-issues-26353}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-26353}

* Die Textzusammenfassung von Inhaltsfragmenten wird in der nächsten AEM as a Cloud Service-Hauptversion 2026.7 eingestellt. Es wird empfohlen, stattdessen AEM Generate-Varianten zu verwenden.

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-26353}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 34 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-26353}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 2.0.0 | [Oak 2.0.0-API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/2.0.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2.31.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
