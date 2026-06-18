---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: e643c01f59df53cf57b287e05b2b5495f459b43e
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 40%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## 26635 {#release-26635}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 26635, die am 17. Juni 2026 veröffentlicht wurde. Die vorherige Wartungsversion war Version 26353.

Die Aktivierung von Funktionen in 2026.6.0 stellt den vollständigen Funktionssatz für diese Wartungsversion bereit. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-26635}

* GRANITE-67251: `cqSiteSearch` eingeführt, ein neuer vordefinierter Index, der über dem `cq:Searchable` Mixin-Typ definiert ist. Dies ermöglicht eine differenzierte Kontrolle darüber, welche Inhalte in den Site-Index aufgenommen werden, und bietet eine vollständige Site-Suche für AEM-Websites, einschließlich semantischer Suche.
* GRANITE-68099: Die eingebettete Apache Jackrabbit Oak wurde auf die neueste öffentliche Version (2.2.0) aktualisiert.
* SKYOPS-135241: Einführung eines AEM-Präfixes für unveränderliche Farm-Filter, um Namenskonflikte mit kundendefinierten Konfigurationen zu vermeiden.

### Behobene Probleme {#fixed-issues-26635}

Keine.

#### AEM Guides {#guides-26635}

* GUIDES-46275: Bildabmessungen, die mit Einheiten wie `mm` angegeben wurden, werden nicht korrekt gerendert, sodass Bilder mit ihrer Originalgröße anstelle der angegebenen Abmessungen angezeigt werden.
* GUIDES-45800: Durch Kopieren und Einfügen von `<keywords>` innerhalb von `<topicmeta>` innerhalb einer `<keydef>` oder `<topicref>` werden die Keywords in unerwünschte fremde Tags eingefügt.
* GUIDES-45409: Wenn eine Zuordnung einen externen `topicref` enthält, der auf eine Nicht-DITA-Ressource verweist (z. B. `.html`), wird ihre Vorschau nicht in der Assets-Benutzeroberfläche angezeigt.
* GUIDES-45254: Beim Arbeiten mit `.plt`- und `.css`-Dateien in PDF-Vorlagen ist die Option **IDs generieren** im Kontextmenü der rechten Maustaste verfügbar, obwohl sie für diese Dateitypen nicht anwendbar ist.
* GUIDES-45508: Das Anwenden einer Grundlinie auf eine Zuordnung mit vielen Assets verzögert das Laden des Übersetzungsberichts für die ausgewählte Sprache, was manchmal zu einer Zeitüberschreitung der Anfrage führt, bevor der Bericht gerendert wird.
* GUIDES-45511: Die QuickInfo für das Symbol **Versionsverlauf** fehlt im linken Bedienfeld der Benutzeroberfläche „Überprüfen“ neben dem Themennamen.
* GUIDES-44942: Beim Hinzufügen von Fragen zu einem Quiz mithilfe der Option Aus Fragenbank einfügen werden kurze Antwortfragen nicht aufgelistet, obwohl eine gültige Frage-ID vorhanden ist.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-26635}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-26635}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-26635}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 10 identifizierte Schwachstellen und verstärkt unser Engagement für zuverlässigen Systemschutz.

### Eingebettete Technologien {#embedded-tech-26635}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 2.2.0 | [Oak 2.2.0-API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/2.2.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.67 | [Apache httpd 2.4.67](https://apache.googlesource.com/httpd/+/refs/tags/2.4.67/CHANGES) |
| Dispatcher | 2.0.274 |  |
| AEM-Kernkomponenten | 2.31.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
| Java 21 | 21.0.11 | [JDK 21.0.11](https://www.oracle.com/java/technologies/javase/21-0-11-relnotes.html) |

