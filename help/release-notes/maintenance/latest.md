---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a091dd6b1b69d77f9eeb50065e8946af0133f4f9
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 42%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 19149 {#19149}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 19149, die am Mittwoch, 21. Januar 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 18751.

Die Funktionsaktivierung von 2025.1.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-19149}

* ASSETS-45286: Anzeigen des granularen Fortschritts beim asynchronen Download-Archivierungsauftrag.
* ASSETS-46296: Unterstützung für Dynamic Media-Vorlagen im Asset-Wähler.
* ASSETS-44796: Auslösen von Assets-Ereignissen für asynchrone DAM-Asset-Aufträge.

### Behobene Probleme {#fixed-issues-19149}

* GRANITE-55074: Stellen Sie sicher, dass CORS-Antwortkopfzeilen für Fehlerantworten festgelegt werden.
* ASSETS-43755: Skalierbarkeitsverbesserungen für die Massenverarbeitung von Assets.
* ASSETS-45399: Nach der Erstellung einer Asset-Live Copy zur Assets-Konsole umleiten.
* ASSETS-45462: Probleme mit der Browserzwischenspeicherung bei benutzerdefinierten Ordnerminiaturen.
* ASSETS-46398: Ausblenden von Download- und Neuverarbeitungsaktionen für DM-Vorlagen.
* ASSETS-44484: Probleme beim erneuten Speichern der Connected Assets-Konfiguration.
* ASSETS-44122: Der Vorgang zum asynchronen Kopieren von Assets benennt den Zielordner beim Kopieren in den aktuellen Ordner nicht um.
* ASSETS-44463: Schaltfläche „CSV herunterladen“ ist beim erfolgreichen Metadatenexport nicht sichtbar.
* ASSETS-45134: Verschiebt einen Auftrag mit dem Zieltitel überschreibt alle Ordnertitel.
* ASSETS-45137: Konflikte mit Massen-Uploads über die Assets-Ansicht.
* ASSETS-45758: Asset-Beziehungen erhalten nach dem Hinzufügen einer Beziehung eine Animation mit unendlichem Beschäftigen/Laden.
* ASSETS-44148: NODE_MOVED-Ereignis in AEM kann unberechtigten NPE in Protokollen verursachen.
* ASSETS-28607: JS-Fehler beim Festlegen einer benutzerdefinierten Videominiatur.
* GRANITE-55781: Verbessern Sie die Gruppensynchronisierung zwischen Adobe Developer Console und AEM. Weitere Informationen finden [ unter „Änderungen bei der Benutzergruppen- und Produktprofilsynchronisierung](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization).
* GRANITE-55754: Stellen Sie sicher, dass SDK-Startskripte Java 21 unterstützen.
* GRANITE-54248: Es kann nicht durch alle Elemente im großen Asset-Ordner gescrollt werden.
* SCRNS-4597: Verbesserungen bei der Suchergebnisliste.


### Bekannte Probleme {#known-issues-19149}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-19149}

Bei Verwendung der Adobe Admin Console für die Berechtigungsverwaltung DÜRFEN DIE FOLGENDEN GRUPPEN NICHT VERWENDET WERDEN, da sie nicht mehr mit AEM synchronisiert werden:
* AEM-Gruppen, die mit _GROUP_NAME_SUFFIX enden.
* Produktprofile aus anderen Umgebungen, Programmen oder Produkten.

Weitere Informationen finden Sie unter [Änderungen bei der Benutzergruppen- und Produktprofilsynchronisierung](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization).


Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-19149}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt vier identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-19149}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.72.0 | [Oak-API 1.72.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html?lang=de) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.27.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
