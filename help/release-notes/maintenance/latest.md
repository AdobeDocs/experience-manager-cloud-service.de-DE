---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a3c414f9b5e575856a942e02661e8c70a7083495
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 89%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 19149 {#19149}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 19149, die am 21. Januar 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 18751.

Die Funktionsaktivierung von 2025.1.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-19149}

* ASSETS-45286: Anzeigen des granularen Fortschritts beim Herunterladen asynchroner Archivierungsaufträge.
* ASSETS-46296: Unterstützung für Dynamic Media-Vorlagen im Asset-Wähler.
* ASSETS-44796: Auslösen von Assets-Ereignissen für asynchrone DAM-Asset-Aufträge.

### Behobene Probleme {#fixed-issues-19149}

* GRANITE-55074: Sicherstellen, dass CORS-Antwort-Header für Fehlerantworten festgelegt sind.
* ASSETS-43755: Skalierbarkeitsverbesserungen für die Massenverarbeitung von Assets.
* ASSETS-45399: Umleiten nach Erstellung einer Asset-Live-Copy zur Assets-Konsole.
* ASSETS-45462: Probleme beim Browser-Caching von benutzerdefinierten Ordnerminiaturen.
* ASSETS-46398: Ausblenden von Download- und Neuverarbeitungsaktionen für DM-Vorlagen.
* ASSETS-44484: Probleme beim erneuten Speichern der Connected Assets-Konfiguration.
* ASSETS-44122: Bei Aufträgen zum asynchronen Kopieren von Assets wird der Zielordner beim Kopieren in den aktuellen Ordner nicht umbenannt.
* ASSETS-44463: Schaltfläche „CSV herunterladen“ ist beim erfolgreichen Metadatenexport nicht sichtbar.
* ASSETS-45134: Verschiebungsauftrag mit Zieltitel überschreibt alle Ordnertitel.
* ASSETS-45137: Konflikte mit Massen-Uploads über die Assets-Ansicht.
* ASSETS-45758: Für Asset-Beziehungen wird nach dem Hinzufügen einer Beziehung „Beschäftigt“/„Wird geladen“-Endlosanimation angezeigt.
* ASSETS-44148: NODE_MOVED-Ereignis in AEM kann unberechtigte NPE in Protokollen verursachen.
* ASSETS-28607: JS-Fehler beim Festlegen benutzerdefinierter Videominiaturen.
* GRANITE-55781: Verbessern der Gruppensynchronisierung zwischen Adobe Developer Console und AEM. Weitere Informationen unter [Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization).
* GRANITE-55754: Sicherstellen, dass SDK-Startskripte Java 21 unterstützen.
* GRANITE-54248: Scrollen durch alle Elemente in großen Asset-Ordnern nicht möglich.
* SCRNS-4597: Verbesserungen beim Anzeigen der Suchergebnisliste.


### Bekannte Probleme {#known-issues-19149}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-19149}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

#### Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen

Bei Verwendung der Adobe Admin Console für die Berechtigungsverwaltung dürfen die folgenden Gruppen NICHT verwendet werden, da sie nicht mehr mit AEM synchronisiert werden:
* AEM-Gruppen, die mit _GROUP_NAME_SUFFIX enden.
* Produktprofile aus anderen Umgebungen, Programmen oder Produkten.

Weitere Informationen finden Sie unter [Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization).

#### Einstellung des SPA-Editors {#deprecate-spa-editor}

[Der SPA-](/help/implementing/developing/hybrid/introduction.md) wird für neue Projekte ab Version 2025.1.0 nicht mehr unterstützt. Der SPA-Editor wird für bestehende Projekte weiterhin unterstützt, sollte jedoch nicht für neue Projekte verwendet werden.

Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind:

* [Der universelle Editor](/help/edge/wysiwyg-authoring/authoring.md) für die visuelle Bearbeitung.
* [Der Inhaltsfragment-Editor](/help/assets/content-fragments/content-fragments-managing.md) für die formularbasierte Bearbeitung

### Sicherheitskorrekturen {#security-19149}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt vier identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-19149}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.72.0 | [Oak-API 1.72.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.27.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
