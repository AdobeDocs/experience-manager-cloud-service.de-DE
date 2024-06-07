---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: de06178f66c95baef15de19296a654f1ed4a0387
workflow-type: ht
source-wordcount: '383'
ht-degree: 100%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 16544 {#release-16544}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 16544, die am 4. Juni 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 16461.

Die Funktionsaktivierung in 2024.6.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-16544}

* GRANITE-41133: Unterstützung von Jakarta Servlet API 5 und OSGi Servlet Whiteboard API.
* GRANITE-51355: org.slf4j.event wurde eingestellt.
* GRANITE-51565: AEM verliert die lokale Gruppenbeziehung zur externen Gruppe, wenn die lokale Gruppe aus AEM veröffentlicht wird.
* GRANITE-51707: Setzen des Cookies saml_request_path während der HTTP-Umleitung zur Authentifizierung.
* GRANITE-52010: Aktualisierung der Jackrabbit-Version auf 2.20.16.
* GRANITE-52057: Update von Filevault auf 3.7.3-T20240514105118-694f6aea zur Reparatur von JCRVLT-745.
* SKYOPS-35998: Aktualisieren der &#39;Sling RepoInit&#39;-Abhängigkeiten: Repoinit Parser 1.9.0, Repoinit JCR 1.1.46.

### Behobene Probleme {#fixed-issues-16544}

* GRANITE-51375: idp-sync gibt NPE aus, wenn kein Zwischenpfad angegeben ist.
* GUIDES-17171: Beim Kopieren und Einfügen von Themen mit einer Größe von mehr als 15 KB tritt ein unerwarteter Fehler auf.
* GUIDES-17088: Die Funktionalität zum Ändern des Dokumentstatus vom Bedienfeld **Dateieigenschaften** aus ist fehlerhaft und wechselt in den Status *Entwurf*.
* GUIDES-16931: Verknüpfte Bilder aus den Themen werden nach der Versionserstellung nicht in der Grundlinie angezeigt.
* GUIDES-16896: Wiederverwendbare Inhaltsbedienfelder listen keine Elemente auf, wenn die **Benutzereinstellungen** so festgelegt sind, dass Dateien je nach **Dateiname** angezeigt werden.

Weitere Informationen zu den neuen und verbesserten Funktionen und zu den Problemen, die in den Experience Manager Guides behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-16544}

Keine

### Änderungshinweis {#change-notice-16544}

AEM as a Cloud Service deaktiviert ab September 2024 die Serialisierung von Ressourcen-Konfliktlösern über das Sling Model Exporter-Framework. Weitere Informationen finden Sie in der [Dokumentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md).

### Eingestellte Funktionen und APIs {#deprecated-16544}

Informationen zu veralteten oder entfernten Elementen in AEM as a Cloud Service finden Sie unter [Eingestellte und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md).

### Eingebettete Technologien {#embedded-tech-16544}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.64.0 | [Oak-API 1.64.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| AEM SLING-API | 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.25.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
