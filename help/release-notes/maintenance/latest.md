---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c5152543550b5f81bf0b79741f288b0c16648584
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 48%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 20476 {#20476}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 20476, die am Mittwoch, 15. April 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 20133.

Die Funktionsaktivierung von 2025.4.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-20476}

* CNTBF-411: Hinzufügen der Möglichkeit, Sling-Aufträge zu löschen, falls sie von JCR gelöscht werden.
* CQ-4359813: AEM Translation Kit: 20. März.
* CQ-4359811: Granite Translation Kit: 20. März.
* GRANITE-57863: Update von Filevault auf Version 3.8.4.
* GRANITE-56154: Konfigurieren Sie exponentielle Wiederholungsversuche in oak-segment-azure.
* GRANITE-55999: Leistung von UserPropertiesService verbessern.
* GRANITE-55781: Vermeiden Sie redundante Neukonfigurationen der Benutzermitgliedschaft.
* GRANITE-53956: Aktualisieren Sie Azure SDK V8 auf V12 für oak-segment-azure.
* GRANITE-50654: Entfernen Sie auf der Registerkarte „Prinzipalberechtigungen“ standardmäßig die Last „Alle“ am Frontend.
* SKYOPS-103444: Update auf Sling ResourceResolver 1.12.6.
* SKYOPS-101147: caconfig-impl aktualisieren.
* SKYOPS-97124: Hinzufügen von Analyzer-Warnungen für veraltete Versionen des SPIFly-Bundles.
* SKYOPS-95826: Aktualisieren der Java-Laufzeitversionen auf 11.0.26 und 21.0.6.
* SKYOPS-53671: Verwenden Sie vom Kunden installierte Artefakte aus Funktionsmodellen für AEM-Neustarts (RDE).

### Behobene Probleme {#fixed-issues-20476}

* ASSETS-49027: [Regression] Der AemRequestEventFilter unterbricht POST-Anfragen an die OSGi-Web-Konsole.
* ASSETS-44956: Keine Dynamic Media-Ausgabedarstellung auswählen. Skript-Tags sollten in die Komponente auf oberster Ebene geladen werden.
* CNTBF-410: Null-Zeiger CheckJob getId im ContentCopy-Bundle.
* CNTBF-341: ContentCopy-Exportindex liegt außerhalb der Grenzen.
* CQ-4355411: QuickInfos werden im Dialogfeld „Benutzereinstellungen“ weiterhin angezeigt.
* GRANITE-57265: Dropdown-Auswahlwerte werden nicht ausgewählt.
* GRANITE-57067: Fehlende effektive Richtlinien für die Benutzeroberfläche.
* SITES-30727: Drag-and-Drop kann bei Unterkomponenten im AEM-Editor fehlschlagen.
* SKYOPS-90607: Sling-Aufträge werden in inaktiver Bereitstellung/veränderlichem Inhalt ausgeführt.
* SKYOPS-95722: Entfernen Sie `MaxPermSize` aus Schnellstart-Flags in AEM-SDK.
* SKYOPS-103569: Bestimmte Bilder können nicht mit Java 21 geladen werden: `javax.imageio.IIOException: Cannot create Sun JPEGImageReader backend`.

### Bekannte Probleme {#known-issues-20476}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-20476}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-20476}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 5 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-20476}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,78,0 | [Oak-API 1.78.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.78.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.28.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
