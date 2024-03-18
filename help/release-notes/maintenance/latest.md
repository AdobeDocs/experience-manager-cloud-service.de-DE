---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: b0198fee3fb8c2f02f50819bea5757e5b8373ac1
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 87%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 15262 {#release-15262}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 15262, die am  6. März 2024 veröffentlicht wurde. Das vorherige Wartungsversion war Version 14697.

2024.3.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de).

### Verbesserungen {#enhancements-15262}

* ASSETS-30632: Eine separate Brand Portal-Spalte zum Veröffentlichungsstatus in der Listenansicht wurde hinzugefügt.
* ASSETS-30934: Unterstützung für die Eigenschaften `Iptc4xmpCore:AltTextAccessibility` und `Iptc4xmpCore:ExtDescrAccessibility` wurde im Asset-Metadaten-Editor hinzugefügt.
* ASSETS-31297: Verbessern der Prüfungen, um das Löschen von kopierten Assets von dynamischen Medien zu verhindern.
* ASSETS-33246: Definition des Versions-Index `damAssetLucene-10`.
* ASSETS-33590: Unterstützung für WebM-Ausgabedarstellungen für Videos in Verarbeitungsprofilen wurde hinzugefügt.
* GRANITE-36205: Update der Oak-Version auf 1.60-T20240131102219-0cde853.
* SITES-19326: Update der Links in der Assets-Benutzeroberfläche, um CF im neuen CF-Editor zu öffnen.
* GUIDES-12945: KI-gestützte intelligente Vorschläge zum Hinzufügen von Inhaltsverweisen beim Erstellen von Inhalten
* GUIDES-12706: Überarbeitete Versionsverlaufsfunktion im Web-Editor
* GUIDES-14948: Verbessertes Benutzererlebnis im Übersetzungsbedienfeld
* GUIDES-8782: Verbesserte Suchlogik im Dialogfeld „Element einfügen“
* GUIDES-14681: Möglichkeit, mehrere Ausgabevorgaben mit dynamischen Baselines zu veröffentlichen
* Eine vollständige Liste der Verbesserungen in AEM Guides finden Sie unter: [Neue Funktionen in AEM Guides](https://experienceleague.adobe.com/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2402-release/whats-new-2024-2-0.html?lang=de#release-info)

### Behobene Probleme {#fixed-issues-15262}

* ASSETS-15977: Entfernung veralteter v1-Suchereignisse und Pipeline-Producer.
* ASSETS-18088: Update der Abhängigkeiten der Batik-Bibliothek auf Version 1.17.
* ASSETS-21965: Der Workflow für Metadaten-Writeback darf nur bei Änderungen an Asset-Metadaten gestartet werden.
* ASSETS-26368: Geplante Massen-Importvorgänge werden nicht entfernt, wenn die Auftragskonfiguration nicht vorhanden ist.
* ASSETS-26549: Assets/Knoten mit „jcr:lastModifiedBy“: „workflow-process-service“ werden in der Listenansicht als „externer Benutzer“ angezeigt.
* ASSETS-26842: Update des „Firefly“-Texts, um „App Builder“ im Verarbeitungsprofil zu lesen.
* ASSETS-28708: Sehr langsame Antwort für einige IMS-Token-Anfragen.
* ASSETS-28767: Inkonsistenter Veröffentlichungsstatus für Assets, wenn Ordner eine große Anzahl der veröffentlichten Assets enthalten.
* ASSETS-29011: Smartes Zuschneiden ist für Benutzende mit schreibgeschütztem Zugriff sichtbar.
* ASSETS-29348: AssetMoveEventHandler kann zu viel Speicher verbrauchen.
* ASSETS-29738: Die Einschränkungen beim Hochladen von Assets scheitern bei NullPointerException für WOFF-Dateien.
* ASSETS-30068: Massenimport in Assets Essentials, um den Status „COMPLETED_WITH_ERROR“ für „Auftrag fehlerhaft abgeschlossen“ einzuschließen.
* ASSETS-30261: Falsche imsUserId, die für Asset-Ereignisse an die Pipeline gesendet wird.
* ASSETS-30538: Option zum Anzeigen der Seite fehlt nach dem Verschieben einer PDF-Datei.
* ASSETS-30626: Fehler beim Erstellen von Bereitstellungsanfragen für Assets mit leerer assetId.
* ASSETS-30756: Die Aktion des Assistenten zum Verschieben von Assets schlägt fehl, wenn der Ordnername auf „html“ endet.
* ASSETS-30810: Bereinigung von Tags vor dem Rendern der alten YouTube-Konfiguration.
* ASSETS-31015: Assets mit der Dateinamenerweiterung „.msg“ können nicht hochgeladen werden.
* ASSETS-31038: Aufgabenereignisse, die beim Benachrichtigungsdienst empfangen werden, werden nicht verarbeitet.
* ASSETS-31097: Deaktivierung der asynchronen Kopie für WCM-Inhalte, um traversale Abfrage-Warnungen zu vermeiden.
* ASSETS-31256: Assets/Knoten mit „jcr:lastModifiedBy“: „workflow-process-service“ werden in der Listenansicht als „externer Benutzer“ angezeigt.
* ASSETS-31260: Das Dropdown-Feld für Asset-Metadaten-Formulare funktioniert nicht ordnungsgemäß, wenn die Dropdown-JSON-Datei eine große Liste enthält.
* ASSETS-31280: Assets werden beim Hinzufügen zu einer Sammlung in einer reduzierten Struktur heruntergeladen.
* ASSETS-31301: `dynamicmedia_sly.js` kann nicht korrekt von der Anwendungs-API instanziiert werden.
* ASSETS-31330: ko_KR: Nicht lokalisierte Zeichenfolgen in Untertiteln und Audiospuren.
* ASSETS-31405: Die InDesign-Server-Verarbeitung schlägt bei großen InDesign-Layouts fehl.
* ASSETS-31570: Unified Shell – Die Schaltflächen „Speichern und Schließen“ und „Abbrechen“ in den Asset-Details müssen mehrmals gedrückt werden, damit sie funktionieren.
* ASSETS-31673: Massenimport für große Dropbox-Dateien schlug fehl.
* ASSETS-32108: AEM Assets speichert benutzerdefinierte Kartengrößen nicht in den Anzeigeeinstellungen.
* ASSETS-32230: Update der minimalen Laufzeitversion von com.adobe.aem.repoapi-Bundle.
* ASSETS-32544: Metadaten-Exportauftrag schlägt gelegentlich fehl.
* ASSETS-32679: Zwischenspeicherungsprobleme mit der Asset-Vorschau (PDF).
* ASSETS-32754: Aufgaben können nicht an Benutzende zugewiesen werden, die sich zuvor nicht angemeldet haben.
* ASSETS-32755: Konfiguration des Auftrags-Themas com/adobe/cq/dam/assetmove zur Verwendung einer geordneten Warteschlange.
* ASSETS-32899: Die Suche in Sammlungen ist extrem langsam.
* ASSETS-33098: AEM Assets-Suchfacetten „Tag-Eigenschaft“ funktionieren nicht erwartungsgemäß.
* ASSETS-33454: Die Aktivität „Aufgabe überprüfen“ und Kommentare dazu werden nicht in der Zeitleiste angezeigt.
* ASSETS-34088: PDF-Vorschau funktioniert nicht auf AEM-Assets.
* ASSETS-34155: Dynamic Media – Aktualisierte AEM-Viewer / 2024.1.0.
* ASSETS-34684: Behandlung von mehrwertigen dc:title in der Inhaltsstruktur.
* ASSETS-34789: Behebung von Normalisierungsproblemen bei der Prüfung von Dateinamenkonflikten.
* DXML-13276: AEM Guides – Integrieren von Indizes in GraniteContent und Entfernen dieser aus der Bibliothek.
* GRANITE-47995: Löschvorgänge können aufgrund von Konflikten mit der Eigenschaft „cq:isDelivered“ fehlschlagen.
* GRANITE-48079: Aktivierung von POST-Anfragen für die OAuth-Online-Token-Validierung.
* GRANITE-48143: Upgrade von Sling ResourceMerger auf 1.4.4.
* GRANITE-49031: Update auf Jackson 2.16.1.
* SCRNS-3961: Screens – Sequenzkanal: Die in dem Übergang „Verblassen“ verwendete jQuery-Animation führt zu einem schwarzen Bildschirm.
* SITES-15868: Verbesserung der Leistung für die Auflistung von Fragmenten.
* SITES-16079: `/fragments/{id}/references` begann, Duplikate zurückzugeben.
* SITES-16118: Wenn ein Fragment gepatcht wird und ein Fragmentfeld im Modell fehlt, wird eine Ausnahme ausgelöst.
* SITES-16121: Beim Abrufen eines Modelldatumsfelds wird eine Ausnahme ausgelöst.
* SITES-16207: Der POST-Vorgang „/adobe/sites/cf/models“ gibt zwei verschiedene OK-Status-Codes zurück.
* SITES-17361: Neueinbindung von Jsoup in das Sites-Headless-Bundle.
* SITES-17768: GraphQL gibt die Dynamic Media-URL für Assets aus, auf die in Inhaltsfragmenten verwiesen wird.
* SKYOPS-66622: Absturz der Autorenbereitstellung nach Ausführung einer buildTransform-aktivierten Pipeline.
* SKYOPS-69977: Adaptives Bild-Servlet lädt das Bild nach dem letzten Update nicht.
* GUIDES-15045: Die Rechtschreibprüfung im Editor lässt keine Auswahl von Vorschlägen zu.
* GUIDES-14968: Die globale Navigationsschaltfläche funktioniert nicht und das Dashboard wird nicht geladen.
* GUIDES-14943: Bei der nativen PDF-Veröffentlichung funktionieren benutzerdefinierte Attribute innerhalb von Bedingungsvorgaben nicht für die native PDF-Veröffentlichung.
* GUIDES-15085: Bei der nativen PDF-Veröffentlichung werden Schlüsselverweise für die Adobe Experience Manager Guides vom Dezember 2023 nicht aufgelöst.
* GUIDES-13486: **Baseline-Filter**-Dateien funktionieren im Web-Editor nicht mit dem Dateinamen.
* Eine vollständige Liste der in AEM Guides behobenen Probleme finden Sie unter [Behobene Probleme in AEM Guides](https://experienceleague.adobe.com/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2402-release/fixed-issues-2024-2-0.html?lang=de#release-info)

### Bekannte Probleme {#known-issues-15262}

* ASSETS-35923: `UnsupportedClassVersionError` Schritt zum Erstellen der CM-Pipeline nach der Aktualisierung `aem-sdk-api` Version auf `2024.2.15262.20240224T002940Z-231200`. **Erfordert Kundenaktion zum Festlegen der Java-Version von CM auf 11**, siehe [Build-Umgebung/Festlegen der Maven-JDK-Version](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/create-application-project/build-environment-details.html?lang=en#alternate-maven-jdk-version)
* ASSETS-35860: Falsche Zeitzonenkonvertierung in der AEM Assets-Spaltenansicht.
* SCRNS-4171: Windows Screens wird beim Aktualisieren auf 15262 und Veröffentlichen eines Kanals leer angezeigt und funktioniert nicht mehr.
* GRANITE-50774: GraniteContent sollte die deterministische Reihenfolge der Eigenschaftswerte zum Zeitpunkt der Init-Zeit verwenden.

### Änderungshinweis {#change-notice-15262}

**Erforderliche Aktionen**

#### Setzen Sie die Java-Version von CM auf 11 {#set-java-version-11}

Die neue Version von aem-sdk-api enthält Klassen, die mit einem Java 11-Ziel kompiliert wurden und nicht mit dem standardmäßigen JDK Version 1.8 der Cloud Manager-Build-Umgebung kompatibel sind. Diese Aktualisierung erfordert, dass Maven mit JDK 11 ausgeführt wird.

Kunden wird empfohlen, eine `.cloudmanager/java-version` -Datei im Stammverzeichnis ihres Git-Repo mit den folgenden Inhalten: `11`. [Build-Umgebung/Festlegen der Maven-JDK-Version](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/create-application-project/build-environment-details.html?lang=en#alternate-maven-jdk-version)

#### Aktualisieren von aem-cloud-testing-clients auf 1.2.1 {#update-aem-cloud-testing-clients}

Bevorstehende Änderungen erfordern, dass die in Ihren benutzerdefinierten Funktionstests verwendete Bibliothek [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) mindestens auf Version **1.2.1** aktualisiert wird.

Stellen Sie sicher, dass Ihre Abhängigkeit in `it.tests/pom.xml` aktualisiert wurde.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

Diese Änderung muss vor dem 6. April 2024 vorgenommen werden.

Wenn die Abhängigkeitsbibliothek nicht aktualisiert wird, treten Pipeline-Fehler beim Schritt „Benutzerdefinierte Funktionstests“ auf.

### Eingebettete Technologien {#embedded-tech-15262}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.60-T20240131102219-0cde853 | [Oak API 1.60.0-API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
