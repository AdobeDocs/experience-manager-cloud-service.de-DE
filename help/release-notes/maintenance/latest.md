---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 558babc0124a8ee8c1337b91c5ef016ed238c935
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 48%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 16544 {#release-16544}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 16544, die am Mittwoch, 4. Juni 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 16461.

Die Funktionsaktivierung in 2024.6.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-16544}

* GRANITE-41133: Unterstützung von Jakarta Servlet API 5 und OSGi Servlet Whiteboard API.
* GRANITE-51355: Veraltete org.slf4j.event.
* GRANITE-51565: AEM verliert die lokale Gruppenbeziehung zur externen Gruppe, wenn die lokale Gruppe aus AEM veröffentlicht wird.
* GRANITE-51707: Setzen Sie das Cookie saml_request_path während der HTTP-Umleitung zur Authentifizierung.
* GRANITE-52010: Jackrabbit-Version auf 2.20.16 aktualisieren.
* GRANITE-52057: Update von Filevault auf 3.7.3-T20240514105118-694f6aea zur Behebung von JCRVLT-745.
* SKYOPS-35998: Aktualisieren der &#39;Sling RepoInit&#39;-Abhängigkeiten : Repoinit Parser 1.9.0, Repoinit JCR 1.1.46.

### Behobene Probleme {#fixed-issues-16544}

* DXML-17171: AEM Guides: Der Kopieren und Einfügen von Themen mit einer Größe von mehr als 15 KB schlägt mit einem unerwarteten Fehler fehl.
* DXML-17088: AEM Guides: Die Funktion zum Ändern des Dokumentstatus vom **Dateieigenschaften** nicht ordnungsgemäß funktioniert und Änderungen an der *Entwurf* state.
* DXML-16931: AEM Handbücher: Verknüpfte Bilder aus den Themen werden nach der Versionserstellung nicht in der Grundlinie angezeigt.
* DXML-16896: AEM Handbücher: Wiederverwendbare Inhaltsbedienfelder listen keine Elemente auf, wenn die **Benutzereinstellungen** werden festgelegt, um Dateien anzuzeigen, indem **Dateiname**.
* GRANITE-51375: idp-sync gibt NPE aus, wenn kein Zwischenpfad angegeben ist.

### Bekannte Probleme {#known-issues-16544}

Keine

### Eingestellte Funktionen und APIs {#deprecated-16544}

Informationen zu veralteten oder entfernten Elementen in AEM as a Cloud Service finden Sie unter [Eingestellte und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md).

### Eingebettete Technologien {#embedded-tech-16544}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,64,0 | [Oak-API 1.64.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| AEM SLING-API | 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.25.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
