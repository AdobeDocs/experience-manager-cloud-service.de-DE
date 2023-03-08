---
title: Neueste Versionshinweise zur Wartung [!DNL Adobe Experience Manager] as a Cloud Service.
description: Neueste Versionshinweise zur Wartung [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: edb8949b532b80a55106e706a49e2ada68722a67
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 7%

---


# Versionshinweise zur Wartungsversion {#maintenance-release-notes}

Im folgenden Abschnitt werden die technischen Versionshinweise für die neueste Wartungsversion von Experience Manager as a Cloud Service beschrieben.

## Version 11289 {#release-11289}

Nachfolgend sind die kontinuierlichen Verbesserungen für das Maintenance Release 11289 zusammengefasst, das am 7. März 2023 veröffentlicht wurde. Dieses Maintenance Release ist eine Aktualisierung von dem vorherigen Maintenance Release 10912.

Die Aktivierung der Funktionen für dieses Maintenance Release bietet Ihnen das vollständige Funktionsumfang. Siehe [Aktuelle Versionshinweise](/help/release-notes/release-notes-cloud/release-notes-current.md) für ausführliche Informationen.

### Bekannte Probleme {#known-issues}

Führen Sie kein Upgrade durch, wenn Sie CORS verwenden. In dieser Version wurde ein Problem identifiziert, das sich auf die Inhaltsbereitstellungsfunktion von GraphQL auswirkte. Eine Änderung der standardmäßigen AEM Dispatcher-Konfiguration bezüglich der Art und Weise, wie in GraphQL persistente Abfragen zwischengespeichert werden, kann die Bereitstellung solcher Abfragen mit GraphQL-Inhalten beeinträchtigen. Dieses Problem wird in unserem nächsten Maintenance Release behoben.

### Behobene Probleme {#fixed-issues}

#### Sites {#sites-issues}

- SITES-11584 Es wurde ein Problem mit Live Copies behoben, das nicht für Seiten mit Anmerkungen erstellt werden konnte
- SITES-11683 MSM Live Copies mit teilweise gebrochener Vererbung deaktiviert

#### Assets {#assets-issues}

- ASSETS-20879 Korrektur der Regression, die die korrekte Funktionsweise der Benutzeroberfläche von Asset-Berichten verhinderte und zu falschen Ergebnissen in generierten Berichten führte.
- ASSETS-21020 Problem beim fehlerhaften Asset-Download behoben - Bildprofil ist nach dem Verschieben eines Assets nicht vorhanden
- ASSETS-21023 Problem mit Bildausgabeformaten in Dynamic Media behoben, die den Zugriff über die API verhinderten

#### Formulare {#forms-issues}

- Ohne

#### Platform {#platform-issues}

- GRANITE-44467 - Es wurde ein Fehler behoben, der dazu führte, dass der Import beim Aktualisieren eines vorhandenen Knotens fehlschlug. Filevault bewahrte unter bestimmten Instanzen keine Mixin-Typen und untergeordneten Knoten auf

### Eingebettete Technologien {#embedded-tech}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.44-T20221206170501-6d59064 | [Oak API 1.44.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| AEM SLING-API | Version 2.27.0 | [Apache Sling API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Sprachspezifikation für HTML-Vorlagen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version 2.21.2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
