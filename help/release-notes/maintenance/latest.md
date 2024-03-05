---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: b2bd6fc61b0d8b79d03ebf9eca7d994a622cc6f2
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 100%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 14697 {#release-14697}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 14697, die am 18. Dezember 2023 veröffentlicht wurde. Sie ersetzt Version 14538, in der es ein Problem gab. Das vorherige Wartungsversion war Version 14227.

2023.12.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de).

### Verbesserungen {#enhancements-14697}

* GRANITE-46723: Benutzersynchronisierung – SAML-Migration von der Standardsynchronisierung zur IDP-basierten Synchronisierung.
* OAK-10311: Replikation – Optimierung des Blob-Vergleichs zur Reduzierung der Replikationszeit großer Asset-Batches in AEM.
* OAK-10511: Replikation – Reduzieren der Netzwerk-Round-Trips zur Reduzierung der Replikationszeit großer Assets in AEM.
* GRANITE-48334: Herausgeber – Sammlungsskript fehlt für RUM.

### Behobene Probleme {#fixed-issues-14697}

* CQ-4354867: ToggleCondition-Referenz bezieht sich auf ein in InstanceActionServlet nicht vorhandenes Feld.
* CQ-4349948: Lokalisierung der Zeichenfolgen „Profileigenschaften“ in „Benutzereinstellungen bearbeiten“ unter „Tools“ → „Sicherheit“ → „Benutzer“.
* GRANITE-44541: Lokalisierung der Fehlerdialogfelder zum Hinzufügen einer privaten Schlüsseldatei im Bildschirm „Benutzer bearbeiten“ > „Keystore“ unter Tools → Sicherheit → Benutzer.
* GRANITE-45341: Lokalisierung von Erfolgs-/Fehlerzeichenfolgen zur Aktivierung/Deaktivierung der Benutzeraktion unter Tools → Sicherheit → Benutzer.
* GRANITE-46650: Lokalisierung der Fehlermeldung „UserId/Kennwort stimmt nicht überein.“ Zeichenfolge unter Tools → Sicherheit → Dialogfeld „Benutzer erstellen“.
* GRANITE-47764: Aktualisierung auf Sling-Modelle-API 1.5.0: Die Injektion einer statischen Variable in einem Sling-Modell führt zu Kompilierungsfehlern (SLING-11507).
* GRANITE-48452: Senden leerer Client-Bibliotheken mit Status-Code 200.
* GRANITE-48410: ResourceResolver wird nicht geschlossen.
* ASSETS-31297: Verhindern des Löschens kopierter Assets aus dynamischen Medien.
* ASSETS-30811: Referenzaktualisierungen für „Tag-Blockierungs-Dienst“ gebunden.
* GRANITE-46418: Aktualisieren von Sling-Ereignissen in AEM: GaugeSupport hat unendliche Rekursion in registerWithSuffix (SLING-11918).
* GRANITE-48937: Regressionsfehler aus Wartungsversion 14538 behoben, bei dem Omnisearch auf der Seite aem/start.html nicht funktioniert.

### Bekannte Probleme {#known-issues-14697}

* GRANITE-49031: Regression, die in einer `@JsonIgnore`-Anmerkung resultiert, wird in transienten Feldern ignoriert.

### Eingebettete Technologien {#embedded-tech-14697}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.58-T20231123092841-619e1bd | [Oak-API 1.58.0-API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.58.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
