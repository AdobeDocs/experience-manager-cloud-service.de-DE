---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 2e90e40a0fe439653987a23792a4c1ec612aafd6
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 63%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 21570 {#21570}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 21570, die am Mittwoch, 15. Juli 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 21484.

>[!NOTE]
>
>[Release 21484](/help/release-notes/maintenance/2025/2025-7-0.md#21484) wurde als privat eingestuft und durch Release 21570 ersetzt.

Die Funktionsaktivierung von 2025.7.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-21570}

* Migriert zu Apache HTTPD 2.4.63

### Behobene Probleme {#fixed-issues-21570}

* SKYOPS-112722: Es wurde ein Problem behoben, das dazu führte, dass die Vanity-URL-Auflösung fehlschlug

### Bekannte Probleme {#known-issues-21570}

* Der zugehörige AEM SDK verfügt über eine andere Release-ID (21575) und ist über das Software Distribution-Portal verfügbar.
* Apache HTTP Server Version 2.4.63 hat eine grundlegende Änderung in der Verarbeitung von Fragezeichen (`mod_rewrite`) in URLs durch `?` eingeführt. Diese Änderung wurde implementiert, um die Verwendung des `UnsafeAllow3F`-Flags zu verhindern, das als Sicherheitsrisiko betrachtet wurde. Dies betrifft alle `RewriteRule`-Anweisungen, die sich auf die Erkennung von Fragezeichen in URL-Mustern stützen.

### Eingestellte Funktionen und APIs {#deprecated-21570}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-21570}

Keine

### Eingebettete Technologien {#embedded-tech-21570}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.80.0 | [Oak-API 1.80.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP-Server | 2.4.63 | [Apache httpd 2.4.63](https://github.com/apache/httpd/blob/2.4.63/CHANGES) |
| AEM-Kernkomponenten | 2.29.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
