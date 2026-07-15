---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 09c52e32e6ffff2c69fb24f28e99a65477b434ec
workflow-type: tm+mt
source-wordcount: '1311'
ht-degree: 15%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## 27083 {#release-27083}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 27083, die am 15. Juli 2026 veröffentlicht wurde. Die vorherige Wartungsversion war Version 26908.

Die Aktivierung von Funktionen in 2026.7.0 stellt den vollständigen Funktionssatz für diese Wartungsversion bereit. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-27083}

* CQ-4354303:Added Möglichkeit, die Übersetzungskonfiguration zu löschen.
* FORMS-23746: Nicht übereinstimmende Datentypen zwischen den Workflow-Schritten „InvokeDDX“ und „Asset-Upload“, die ihre Verwendung nacheinander verhindert haben.
* FORMS-24585: AEP-Connector mit einfacherer Bereitstellung.
* FORMS-25250: Einführung in den ConvertPDF-Service.
* FORMS-26044: Virensuche/Malware-Suche nach Uploads in AF1- und Kernkomponenten-basierten Formularen hinzugefügt.
* GRANITE-69298: Hinzufügen von `cqPageContent-5` und `graphqlConfig-3` Indizes.
* SITES-42563: Edge Delivery mit universellem Editor: Veröffentlichungsfehler im universellen Editor und in Sites Admin anzeigen (früher Zugriff).
* SITES-42792: Abgeschnittener Platzhalter „Pfad von Launch Source auswählen“ im Filterbedienfeld unter „Tools“ > „Allgemein“ > „Launches“.
* SITES-43178: AEM: Das lokalisierte Zeitformat umfasst AM/PM in „Tools“ > „Sites“ > „Launches“.
* SITES-44344: Inhalts-API: MSM-/Sprachkopien als Teil der übergeordneten Site behandeln.
* SITES-44598: Schaltfläche Preflight in der Kopfzeilenleiste des Editors präsentieren.
* SITES-44676: Die Suchergebnisse für Inhaltsfragmente enthalten jetzt die Metadatenschema-ID für jedes Fragment.
* SITES-44767: Es wurde ein Standard-Metadatenschema für Inhaltsfragmente hinzugefügt.
* SITES-45651: Das Beispiel für ein OpenAPI-Inhaltsfragment in der API-Spezifikation wurde korrigiert.
* SITES-45664: Es wurde ein neuer GET-`/cf/metadata/schemas`-Endpunkt hinzugefügt, um filterbare Metadateneigenschaften abzurufen.
* SITES-45725: Inhalts-API: Anfragekorrelationsfilter hinzufügen, um Oak-Durchlauf-SLO-Warnungen zu aktivieren.
* SITES-45817: Edge Delivery mit universellem Editor: Überprüfen von Edge-Bereitstellungsrollen und -Berechtigungen beim Veröffentlichen (früher Zugriff).
* SITES-45842: Edge Delivery mit universellem Editor: Bewahren Sie die universelle Editor-Instrumentierung für schreibgeschützte und Überprüfungs-/Kommentar-Anwendungsfälle auf.
* SITES-45848: Edge Delivery mit universellem Editor: `json-ld` vor der Veröffentlichung validieren.
* SITES-46768: Edge Delivery mit universellem Editor: Probleme bei der Site-Erstellung im Assistenten zur Site-Erstellung anzeigen.

### Behobene Probleme {#fixed-issues-27083}

* CQ-4364078: Das Umschreiben interner Links in Experience Fragments durch die Sprachkopie wurde korrigiert.
* CQ-4364077: Fehlerkorrektur bei der Erstellung von Sprachkopien aufgrund von OakState0001-Konflikten.
* CQ-4363949: Fehlerkorrektur: Das falsche Hinzufügen unveränderter referenzierter Experience Fragments in der Nur-Update-Übersetzung wurde korrigiert.
* CQ-4363942: Die Tags-Benutzeroberfläche: Dropdown-Liste „Sprache hinzufügen“ zeigt jetzt nicht aufgeführte Gebietsschemata an, die trotz ihrer Speicherung in JCR nicht sichtbar waren.
* CQ-4363527: Fehlerkorrektur in der Benutzeroberfläche des Sprachkopie-Widgets für Agent-Methode und Anbieter behoben.
* FORMS-25979: Aktualisierung der Bibliothek „Underscore.js“ (1.13.6 → 1.13.8+) im AEM Forms-Add-on.
* FORMS-18969: Es wurde ein Problem behoben, bei dem AEM Forms-Designs Benutzende daran hinderte, die Formularvorschau zu aktualisieren.
* FORMS-25184: Fehlende Punkte für Datenbindungsanzeigen im seitlichen Bedienfeld „Datenquellen“ für Kernkomponenten-basierte Formulare (AF v2) wurden behoben.
* FORMS-18721: Es wurde ein Problem behoben, das verhinderte, dass AEM Forms-Designs die Basis-Client-Bibliothek aktualisieren konnten.
* FORMS-19235: Es wurde ein Anwendungsfehler behoben, der vertrauliche Informationen in Forms Manager verfügbar machen konnte.
* FORMS-25369: Es wurde ein Problem behoben, bei dem das Kopieren eines Designs keine clientlib-Abhängigkeiten aus den Basis-Metadaten der Client-Bibliothek übernahm.
* FORMS-25372: Es wurden Vorbefüllungsfehler und JSON-Zusammenführungsprobleme behoben, die sich auf eingebettete adaptive Forms auswirkten.
* FORMS-24853: Fehlerkorrektur: Registerkarten-Problem mit der Komponente „Freihandsignatur“ (Foundation-Komponente) in adaptivem Forms wurde behoben.
* SITES-41928: Die Überschneidung von ContextHub und Unified Shell macht das Komponentenmenü im Editor unzugänglich.
* SITES-46579: Inhalts-API: Korrigieren des Repository-Durchlaufs in der Sprachkopieabfrage von RelationshipService - Definieren des Index und Umschreiben der Abfrage.
* SITES-44192: Forms/Content-API: Die Content-API gibt 404 für EDS-Formulare zurück, die `sling:configRef` anstelle von `cq:conf` verwenden.
* SITES-29367: GraphQL: Schützen Sie ModelManager vor fehlerhaften `cqPageLucene`.
* SITES-46521: Inhalts-API: `jcr:path` in der Abfrage verursacht das Durchlaufen von Abfragen.
* SITES-46784: GraphQL: Modelle im ModelManager müssen dedupliziert werden.
* SITES-46304: Inhalts-API: Die Seitensuche mit der Inhalts-API schließt `/content/campaigns` im Hintergrund aus.
* SITES-46769: GraphQL: DataCache pro Anfrage mit großen Inhaltsfragmentmodellen führt zu OOM-Ausnahmen.
* SITES-46570: Inhalts-API: Verwenden Sie den Operanden „Indizierter Pfad()“ in der Push-Down-Liste der Abfragevorlagen für den Index.
* SITES-24497: Wiederholte Landmarken erhalten jetzt unterschiedliche Bezeichnungen, sodass die technischen Hilfsmittel zwischen ihnen unterscheiden können.
* SITES-24525: Falsche Überschriftenrolle korrigiert, die modalen Schaltflächen zugewiesen ist - Bildschirmlesehilfen geben sie jetzt als Schaltflächen aus.
* SITES-24703: Die Fokusanzeige für Listenfeld-Popup-Schaltflächen ist jetzt vollständig sichtbar und nicht mehr abgeschnitten.
* SITES-25217: Das Informationssymbol wurde vergrößert, um die Mindestanforderung an die Zielgröße zu erfüllen.
* SITES-25263: Der Wert „aria-hasPopup“ im Timewarp-Datumsfeld wurde korrigiert, sodass die Sprachausgabe ihn korrekt ausgibt.
* SITES-25308: Erhöhter Kontrast auf den Fokusindikatoren der Schaltfläche „Demografische Symbolleiste“, um das WCAG-Minimum zu erreichen.
* SITES-25318: Verbesserter Textkontrast für Eingabefelder in der Symbolleiste „Demografie“.
* SITES-25364: Eingabeanweisungen sind jetzt programmgesteuert mit ihrem Kontrollkästchen verknüpft, sodass sie von technischen Hilfsmitteln gemeinsam angekündigt werden.
* SITES-25377: Die Assets-Seitenleiste lädt ihren Inhalt nicht mehr neu, wenn das Filterfeld den Fokus erhält.
* SITES-40752: Verbesserte Tastaturnavigation durch die Komponentenliste des seitlichen Bedienfelds.
* SITES-41121: Verhindert, dass Bildschirmlesehilfen neben dem Komponentennamen eine ausgeblendete Gruppenbezeichnung ankündigen.
* SITES-43802: Eine falsche Zeichenfolge „false“ entfernt, die im Modal „Komponente einfügen“ angezeigt wurde.
* SITES-46720: Seiteneigenschaften-Radios verlieren die gespeicherte Auswahl nach der Aktualisierung von 2026.05+ (SDK ≥ 26353) - Werte werden Client-seitig gelöscht.
* SITES-46680: CF-Launch kann aufgrund der Sling-Servlet-Zuordnung im benutzerdefinierten Code nicht erstellt werden.
* SITES-46327: Bei der Erstellung eines Launches mit aktivierter Option „Live-Daten der Quellseite übernehmen“ wird das Experience Fragment von der Quellseite nicht vererbt und einige Links funktionieren auch nicht mehr.
* SITES-45969: Untergeordnete Seiten, die bei der Launch-Promotion gelöscht werden, wenn „neue Vorlage“ + „Unterseiten einschließen“ verwendet werden.
* SITES-45723: SITES-44245 Fix Breaks Launches: empty-genericFrom guard unterdrückt legitime Neuschreibungen von Launch-Referenzen.
* SITES-45689: Zeitweise auftretende MSM-Rollout-Fehler - „Kein Source-Pfad“ &amp; AccessDeniedException.
* SITES-44918: Indonesischer Sprach-Code, der IN anstelle der ID angezeigt wird.
* SITES-41427: XF-Rollout meldet Erfolg, schlägt aber im Hintergrund fehl, wenn keine Live Copy vorhanden ist - Anforderung einer ordnungsgemäßen Handhabung oder automatischen Erstellung
* SITES-36149: Duplizierung von Komponenten in Launch nach der Veröffentlichung mit Live-Synchronisierung.
* SITES-25970: Das Rollout-Dialogfeld für die Komponenten-Benutzeroberfläche wird ausgeschnitten.
* SITES-30707: Es wurde eine hartcodierte „Allgemein“-Beschriftung im Inhaltsfragment-Editor korrigiert, um die Lokalisierung zu unterstützen.
* SITES-44228: Es wurde ein Problem behoben, bei dem beim Löschen eines referenzierten Inhaltsfragments, auf das über die UUID verwiesen wird, die referenzierten Fragmente nicht angepasst wurden.
* SITES-45171: Es wurde ein Problem behoben, bei dem in der Veröffentlichungsanfrage fälschlicherweise ein Aktivierungsanfrage-Workflow Trigger werden konnte.
* SITES-46303: Versionsabruf wurde korrigiert, um unnötige Kartenmigrationsversuche zu vermeiden.
* SITES-46713: Fehlerkorrektur für PATCH-Vorgänge, wenn Benutzende keine für die Kartenmigration erforderlichen Löschberechtigungen haben.
* SITES-46590: Es wurde eine Regression behoben, bei der durch eine Rückkehr zu einer früheren Version in der Zeitleiste die Miniaturansicht der Asset-Karte in der Admin-Ansicht von Assets nicht aktualisiert wurde.
* SITES-47292: Edge Delivery mit universellem Editor: Korrigieren Sie das Rendering zusammengeführter Tags in Seitenmetadaten.

### Bekannte Probleme {#known-issues-27083}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-27083}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-27083}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion wurden 18 identifizierte Schwachstellen behoben, was für einen noch robusteren Systemschutz sorgt.

### Eingebettete Technologien {#embedded-tech-27083}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 2.2.0 | [Oak 2.2.0-API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/2.2.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.67 | [Apache httpd 2.4.67](https://apache.googlesource.com/httpd/+/refs/tags/2.4.67/CHANGES) |
| Dispatcher | 2.0.274 |  |
| AEM-Kernkomponenten | 2.31.2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
| Java 21 | 21.0.11 | [JDK 21.0.11](https://www.oracle.com/java/technologies/javase/21-0-11-relnotes.html) |
