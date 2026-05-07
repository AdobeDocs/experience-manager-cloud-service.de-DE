---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: d00af3aee8c2a42233bfc0f914a4e24abe921e08
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 30%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## 25892 {#release-25892}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 25892, die am 7. Mai 2026 veröffentlicht wurde. Die vorherige Wartungsversion war Version 25520.

Die Aktivierung von Funktionen in 2026.5.0 stellt den vollständigen Funktionssatz für diese Wartungsversion bereit. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

>[!NOTE]
>
>Version 25821 wurde als privat gekennzeichnet.

### Verbesserungen {#enhancements-25892}

* CQ-4362304: Erstellen Sie Richtlinien für das Frontend und aktualisieren Sie die LLM-Konfigurations-Benutzeroberfläche.
* GRANITE-39546: Aktualisieren von Apache Tika auf 3.x.
* GRANITE-53957: Aktualisieren Sie Azure SDK V8 auf V12 für oak-blob-azure.
* GRANITE-61245: Alle Verwendungszwecke von commons-lang entfernen (durch commons-lang3 ersetzen).
* GRANITE-64748: Bump OIDC Authentication Handler.
* GRANITE-64764: Aktualisieren Sie den Apache Commons-Text auf 1.15.0.
* GRANITE-64963: Aktualisieren von Filevault auf 4.2.0.
* GRANITE-66197: Hinzufügen von Microsoft Graph API E-Mail-Unterstützung für M365-Mandanten.
* GRANITE-66449: Aktualisieren der Maven-Plug-ins für die Java 17-API-Unterstützung.
* GRANITE-66473: Hinzufügen der Coffein-Cache-Bibliothek zu base-granite.
* GRANITE-66836: Aktualisieren des Schnellstarts auf Oak 2.0.0.
* SKYOPS-129301: Setzen Sie die JavaDoc-Konformitätsstufe der APIs auf Java 17.
* SKYOPS-129351: Aktualisieren von Reaktiv-Streams und Reactor-Core für die Kompatibilität mit MCP SDK.
* SKYOPS-131412: Aktualisieren Sie Apache Commons Exec auf die neueste Version.
* SKYOPS-131432: Felix SCR auf 2.2.14 aktualisieren.
* SKYOPS-131907: Aktualisieren der Sling-API-Regionen auf 1.1.10.
* SKYOPS-131938: Aktualisieren Sie GSON auf die neueste Version.
* SKYOPS-132173: Aktualisieren des Apache Commons-Codecs auf die neueste Version.
* SKYOPS-132182: Sling-Mandanten-Paket aktualisieren.
* SKYOPS-132267: Aktualisieren `org.osgi.service.component` Anmerkung.
* SKYOPS-132272: Sling Feature Model-Bundle aktualisieren.
* SKYOPS-132525: Schnellstart-Analyzer hinzufügen, um neue API-Entfernungen zu verhindern.
* SKYOPS-134408: `com.adobe.granite.asset.core` auf 2.2.82 aktualisieren.
* SKYOPS-137750: `com.adobe.granite.comments` auf 1.0.40 aktualisieren.
* SKYOPS-137759: `com.adobe.granite.jobs.async.ui.commons` auf 3.2.4 aktualisieren.
* SKYOPS-138356: `com.adobe.granite.oauth.server` auf 1.1.36 aktualisieren.
* SKYOPS-138739: SnakeYAML auf 2.6 aktualisieren.

### Behobene Probleme {#fixed-issues-25892}

* ASSETS-59546: Entfernen von Abhängigkeiten von veralteten Bibliotheken für „commons-lang“.
* ASSETS-64831: AssetProcessorProcess - Zurücksetzen der Anzahl von Verarbeitungsversuchen verursacht blockierte Assets.
* ASSETS-66683: Genehmigungsschleife aufgrund eines Upload-Blob-Fehlers.
* CNTBF-613: Korrigieren des Zugriffs verweigert (JCR-101) beim Registrieren von Knotentypen.
* GRANITE-44537: Zeichenfolge in „Land/Region“ nicht in AEM lokalisiert.
* GRANITE-61760: Fehlgeschlagene Aktivierung von AdminUserInitializer korrigieren.
* GRANITE-64543: Die Antwort auf Berechtigungsbeschränkungen folgt nicht der API-Struktur.
* GRANITE-66692: Interner Classloader reagiert nicht auf Paketaktualisierungen.
* GRANITE-66732: Verwenden Sie Aktivierungen anstelle von Service-Komponenten für Pakete der Startebene 1.
* GRANITE-66846: Für die AEM-Berechtigungs-API werden keine `rep:ntNames` angezeigt.
* SITES-39267: PagePath in Beziehungsketteneinträgen wiederherstellen.
* SITES-43715: Die Berechtigungsprüfung schlägt beim Lesen des Ressourcenstatus fehl.

#### AEM Guides {#guides-25892}

* GUIDES-45110: Wenn Sie ein Bild im Editor über das Dialogfeld **Datei auswählen** auswählen, werden nur Rasterformate (wie JPG, PNG und GIF) angezeigt. Vektordateien (z. B. `.ai` und `.eps`) werden nicht angezeigt und können nicht ausgewählt werden.
* GUIDES-41938: Wenn Sie ein Thema in einem Ordner mit Leerzeichen im Namen erstellen, wird fälschlicherweise ein doppelter Ordner erstellt, in dem Leerzeichen durch Bindestriche ersetzt werden, und das Thema wird dort anstelle des ursprünglichen Ordners gespeichert.
* GUIDES-38377: Wenn Änderungen an einer Ausgabevorgabe in einem Ordnerprofil auf bestehende Zuordnungen angewendet werden, wird der gespeicherte **Veröffentlichungskontext** für die AEM Sites-Vorgabe zurückgesetzt.
* GUIDES-43547: Wenn große Themen oder Karten geöffnet werden, reagiert die Autoreninstanz nicht mehr, was in einigen Fällen einen Neustart erforderlich macht.
* GUIDES-32520: Wenn Rücktaste für Elemente verwendet wird, scrollt der Editor unabhängig von der Cursor-Position zum Anfang des Themas (Editor 2.0).

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-25892}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-25892}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-25892}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 19 identifizierte Schwachstellen und verstärkt unser Engagement für zuverlässigen Systemschutz.

### Eingebettete Technologien {#embedded-tech-25892}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 2.0.0 | [Oak 2.0.0-API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/2.0.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2.30.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
