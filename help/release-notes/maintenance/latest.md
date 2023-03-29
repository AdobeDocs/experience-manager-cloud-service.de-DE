---
title: Aktuelle Versionshinweise zur Wartung [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise zur Wartung [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: 7e66c9f26211bd92119c74f311f3e9b3195a8d98
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 6%

---


# Versionshinweise zur Wartungsversion {#maintenance-release-notes}

Im folgenden Abschnitt finden Sie die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 11382 {#release-11382}

Nachfolgend sind die kontinuierlichen Verbesserungen für die Wartungsversion 11382 zusammengefasst, die am 28. März 2023 veröffentlicht wurde. Dieses Maintenance Release ist eine Aktualisierung von dem vorherigen Maintenance Release 11289.

Die Aktivierung der Funktionen für dieses Maintenance Release bietet Ihnen das vollständige Funktionsumfang. Siehe [Aktuelle Versionshinweise](/help/release-notes/release-notes-cloud/release-notes-current.md) für ausführliche Informationen.

### Behobene Probleme {#fixed-issues}

- ASSETS-21023 - Ausgabedarstellung für smartes Zuschneiden wurde behoben, bei der Kunden in der Publisher-Instanz aller AEM Umgebungen eine Nullzeiger-Ausnahme bemerken konnten, wenn versucht wurde, über die API auf diese Ausgabedarstellungen zuzugreifen.
- SKYOPS-49280 - Bei der Installation einer Konfiguration oder eines Bundle-Updates mit RDE in Publish kann das Ergebnis möglicherweise nicht beobachtet werden, da der Cache des Publish-Dispatchers nicht ungültig gemacht wird

#### Sites {#sites-issues}

- SITES-7796 - Möglichkeit für Inhaltsautoren, das Übergeordnete Inhaltsfragment und die entsprechenden Varianten beim Export in Target zu veröffentlichen

#### Assets {#assets-issues}

- ASSETS-20076 - Unterstützung für Video-Wasserzeichen hinzugefügt, die mit der aktuellen Unterstützung für Bild-Wasserzeichen übereinstimmen
- ASSETS-21428 - Hinzufügung von Ausschlüssen für CSS-Änderungen

#### Formulare {#forms-issues}

- CQ-4351502 - Aktualisieren der Service-Benutzerzuordnung, um Lesezugriff in Sites zu ermöglichen

#### Platform {#platform-issues}

- SITES-11040 - Bedingte Aktivierung der beibehaltenen Abfrage-Zwischenspeicherung in GraphQL im Dispatcher

### Eingebettete Technologien {#embedded-tech}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.44-T20221206170501-6d59064 | [Oak API 1.44.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| AEM SLING-API | Version 2.27.0 | [Apache Sling API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Sprachspezifikation für HTML-Vorlagen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version 2.21.2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
