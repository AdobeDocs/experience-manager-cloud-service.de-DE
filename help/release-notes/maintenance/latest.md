---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a842a5f0bd5561563a86f6f0b6e8abf8cfd679ec
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 24%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 24222 {#24222}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 24222, die am Mittwoch, 3. Februar 2026 veröffentlicht wurde. Die vorherige Wartungsversion war Version 23963.

Die Funktionsaktivierung von 2026.2.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-24222}

* CNTBF-604: Erstellen Sie eine neue Bundle-Version für den Content-Backflow.
* CQ-4361592: Hinzufügen von TypeHint-Unterstützung für die Projekterstellung und -aktualisierung.
* CQ-4362198: Neueste Übersetzungen von AEM- und Granite-Paketen.
* GRANITE-36205: Aktualisieren Sie die interne Oak-Release-Version auf die neueste Version.
* GRANITE-59211: OPTEL: Nonce-Unterstützung und Self-Service-Konfiguration hinzugefügt.
* GRANITE-62166: Aktualisieren Sie das Migrationspaket, um die Migrationsstatus aus dem Migrationstool wiederzuverwenden.
* GRANITE-62598: Redundante Eigenschaft entfernen, die vom Inhaltspaketfilter ausgeschlossen ist.
* GRANITE-62684: Ein Client-Socket-Timeout kann über skyline-ops konfiguriert werden.
* GRANITE-62702: Ersetzen Sie die Sling-Erkennung durch eine eigenständige Implementierung für die Online-Migration.
* GRANITE-62763: Aktualisieren der Guava-Ausnahmeliste für veraltete Inhalte basierend auf ASSETS Rotary.
* GRANITE-62771: Fehler bei Schnellstart-Builds, wenn neue veraltete Commons-Lang-Abhängigkeiten eingeführt werden.
* GRANITE-62987: Aktualisieren der Felix-Web-Konsole auf Version 5.0.18.
* GRANITE-63339: Verbesserter Lease-Mechanismus für Azure-Migrations-Status-Blob.
* GRANITE-63343: Unterstützung für die neueste Version des Sling-API-Bundles in workflow.core wurde hinzugefügt.
* GRANITE-63799: Bump OIDC Authentication Bundle-Version.
* GRANITE-63821: Aktualisieren des Schnellstarts auf die filevault-Version mit der Fehlerbehebung von JCRVLT-831/JCRVLT-839.
* GRANITE-63827: Aktualisieren Sie den Schnellstart auf die neueste öffentliche Version von Oak (1.90.0).
* GRANITE-63888: Aktualisieren Sie Quickstart auf Jackrabbit 2.22.3.
* GRANITE-64030: Hinzufügen von Keywords und Mustern zur Zulassungsliste für den Ausdruckssprachvalidator.
* GRANITE-64050: Erlauben Sie ausgeblendeten conf-Ordnern das Ausblenden externer Produktfunktionen.
* SITES-30452: Inhalts-API mit ASO - Vorschläge für Titel und Beschreibungen.
* SITES-38099: Aktualisieren Sie `testing-model.txt`, um eine höhere Version von Integritätsprüfungen zu verwenden.
* SKYOPS-43616: Migrieren von Jenkins-Anmeldeinformationen zu Vault in Dispatcher-Repositorys.
* SKYOPS-108584: Bump FACT-Tool von 0.6.0 bis 0.6.10.
* SKYOPS-115691: Aktualisieren Sie das CORS-Filterpaket, um bei PreFlight-Anfragen die Kopfzeile „Vary Origin“ hinzuzufügen.
* SKYOPS-123094: Aktualisieren von Apache-HTTP-Komponenten in Schnellstart.
* SKYOPS-123236: `rep:cugPolicy` in das Replikationspaket aufnehmen.
* SKYOPS-123240: Aktualisieren von CRXDE-Abhängigkeiten in Schnellstart.
* SKYOPS-123247: Aktualisieren des Sling XSS-Bundles in Schnellstart.
* SKYOPS-123250: Sling-Sicherheitspaket in Schnellstart aktualisieren.
* SKYOPS-123327: Java 21 für AEM-CS SDK erforderlich.
* SKYOPS-125574: Netcentric AC Tool-Pakete in Schnellstart aktualisieren.
* SKYOPS-126150: Verbessert den obersten Befehl für Thread-Dumps-Generator-Skript.

### Behobene Probleme {#fixed-issues-24222}

* FORMS-23687: Beheben eines SSV-Validierungsfehlers, wenn die Regel „enthält“ ohne Standardwert verwendet wird.
* GRANITE-48472: Lokalisierungsfehler beim Ändern des Kennworts auf der Registerkarte Benutzereinstellungen bearbeiten.
* GRANITE-50286: Layout-Problem in der Statusspalte des Benutzerverwaltungs-Modals behoben.
* GRANITE-52301: Localize kann Änderungen an der Sitzungszeichenfolge in Sicherheitsgruppen nicht übertragen.
* GRANITE-52920: Lokalisierungsfehler beim Erstellen eines Benutzers in Sicherheit Neuen Benutzer erstellen.
* GRANITE-54654: Lokalisieren Sie die Zeichenfolge im Dialogfeld „Sicherheit“ der Adobe IMS-Konfigurationen.
* GRANITE-56371: Korrigieren Sie das falsche Datenformat im Security Trust Store.
* GRANITE-62717: Aktualisieren des Crypto-Keystore für die JSafe-Kennwortverarbeitung mit Nicht-ASCII-Zeichen.
* GRANITE-62789: Aktualisieren Sie messaging-client, um den Modus „Keine weiteren Zustellversuche“ bei der Inhaltsverteilung zu unterstützen.
* GRANITE-62824: `NullPointerException` beim Zugriff auf die Registerkarte Gruppen im Benutzereditor beheben.
* GRANITE-63080: Import von `org.slf4j.spi` mit `slf4j 2.x` kompatibel machen.
* GRANITE-63210: Aktualisieren des Verteilungs-Kerns, um die Dispatcher-Invalidierung beim Start der Veröffentlichung zu beheben.
* GRANITE-63293: Beheben Sie den Verlust des erforderlichen Sternchens nach dem ersten Authoring.
* GRANITE-63360: Korrigieren Sie falsche Informationen, die angezeigt werden, wenn mehrere Pfade ausgewählt sind.
* SITES-36242: Einschränken Sie die GraphQL-Option „Regex ausführen“ ein, um die Umgehung des Dispatcher-Filters zu beheben.
* SKYOPS-84379: Verwenden Sie das neueste FACT-Tool, um die ordnungsgemäße Funktionsabfrage durch RDEs zu ermöglichen.
* SKYOPS-121216: Setzen Sie die Aktualisierung auf die Jackson 2.20.0-Bibliotheken zurück.

#### AEM Guides {#guides-24222}

* GUIDES-38198 : Beim Aktualisieren einer Inline-MathML-Gleichung mit der Option MathML bearbeiten im Kontextmenü wird der aktualisierte Wert erst angezeigt, wenn die Seite aktualisiert wurde.
* GUIDES-38276: Versionsbezeichnungen können nicht aus dem Bedienfeld „Versionsverlauf“ in der Assets-Benutzeroberfläche entfernt werden.
* GUIDES-36641: Beim Generieren der AEM Sites-Ausgabe werden die Zuordnungstitel, die Schlüsselwörter und Thementitel mit `<ph>` enthalten, nicht in die veröffentlichte Ausgabe aufgenommen.
* GUIDES-37837: Beim Versuch, ein Thema oder eine Zuordnung zu speichern, kann der Vorgang gelegentlich mit dem Fehler Fehler Datei konnte nicht gespeichert werden fehlschlagen, insbesondere während intensiver Asset-Verarbeitungsaufgaben oder Übersetzungs-Workflows, die im Hintergrund ausgeführt werden.
* GUIDES-27774: Der Bericht Beschädigte Liste enthält fälschlicherweise externe Links, gültige `keyrefs` und Schlüsselwörter, die im Rahmen der aktuellen Zuordnung ordnungsgemäß aufgelöst werden.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-24222}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-24222}

* AEMSRE-2896: Korrigieren Sie die benutzerdefinierte Handhabung der LogManager-Konfiguration.
* GRANITE-62802: Entfernen einer veralteten `commons-lang`-Abhängigkeit aus `granite.auth.saml`.
* GRANITE-62805: Entfernen einer veralteten `commons-lang`-Abhängigkeit aus `granite.httpcache.core`.
* GRANITE-62864: Entfernen einer veralteten `commons-lang`-Abhängigkeit aus `granite.jobs.async`.
* GRANITE-62865: Entfernen einer veralteten `commons-lang`-Abhängigkeit aus `granite.replication.core`.
* GRANITE-62868: Entfernen einer veralteten `commons-lang`-Abhängigkeit aus `granite.rest.api`.
* GRANITE-62895: Entfernen einer veralteten `commons-lang`-Abhängigkeit aus `translation.connector.msft.core`.
* GRANITE-63069: `com.adobe.granite.httpcache.core` verwerfen.
* GRANITE-63179: Entfernen einer veralteten `commons-lang`-Abhängigkeit aus `cq-workflow-impl`.
* GRANITE-63180: Veralteten `commons.lang`-Export aus `cq-mailer` Bundle entfernen.
* SKYOPS-123329: Abschaffung der Java 11-Unterstützung für AEM Ethos-Bereitstellungen und Aktualisierung von `commons-lang3`.
* SKYOPS-124983: Veraltete `nashorn.args` aus AEM-Startskripten entfernen.

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-24222}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion wurden 10 identifizierte Schwachstellen behoben, was für einen noch robusteren Systemschutz sorgt.

### Eingebettete Technologien {#embedded-tech-24222}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,90,0 | [Oak 1.90.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2,30,2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
