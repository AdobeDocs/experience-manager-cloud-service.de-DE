---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 2677e8fbdf6b21ce2d1d848000401c826bc5f289
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 37%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 14538 {#release-14538}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 14538, die am Donnerstag, 6. Dezember 2023 veröffentlicht wurde. Diese Wartungsversion ist eine Aktualisierung der vorherigen Wartungsversion 14227.

2023.12.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de).

### Verbesserungen {#enhancements-14538}

* GRANITE-46723: Benutzersynchronisierung - SAML-Migration von der Standardsynchronisierung zur IDP-basierten Synchronisierung.
* OAK-10311: Replikation - Optimierung des Blob-Vergleichs, um die Replikationszeit großer Asset-Batches in AEM zu reduzieren.
* OAK-10511: Replikation - Reduzieren Sie Netzwerk-Round-Trips, um die Replikationszeit großer Assets in AEM zu reduzieren.
* GRANITE-48334: Herausgeber - Sammlungsskript fehlt für RUM.

### Behobene Probleme {#fixed-issues-14538}

* CQ-4354867: ToggleCondition -Referenz bezieht sich auf nicht vorhandenes Feld in InstanceActionServlet.
* CQ-4349948: Lokalisierung der Zeichenfolgen &quot;Profileigenschaften&quot;in &quot;Benutzereinstellungen bearbeiten&quot;unter &quot;Tools > Sicherheit > Benutzer&quot;.
* GRANITE-44541: Lokalisierung der Fehlerdialogfelder zum Hinzufügen der privaten Schlüsseldatei im Bildschirm &quot;Benutzer bearbeiten&quot;> &quot;Keystore&quot;unter Tools → Sicherheit → Benutzer.
* GRANITE-45341: Lokalisierung von Erfolgs-/Fehlerzeichenfolgen zur Aktivierung/Deaktivierung der Benutzeraktion unter Tools > Sicherheit > Benutzer.
* GRANITE-46650: Lokalisierung der Fehlermeldung &quot;UserId/Password mismatch.&quot; Zeichenfolge unter Tools > Sicherheit > Dialogfeld &quot;Benutzer erstellen&quot;.
* GRANITE-47764: Aktualisierung auf Sling-Modelle API 1.5.0: Die Injection auf eine statische Variable in einem Sling-Modell führt zu Kompilierungsfehlern (SLING-11507).
* GRANITE-48452: Senden leerer Client-Bibliotheken mit Status-Code 200.
* GRANITE-48410: ResourceResolver ist nicht geschlossen.
* ASSETS-31297: Verhindern des Löschens kopierter Assets aus dynamischen Medien.
* ASSETS-30811: Referenzaktualisierungen für &quot;Blocktag-Dienst&quot;gebunden.
* GRANITE-46418: Sling-Ereignisse in AEM aktualisieren: GaugeSupport hat unendliche Rekursion in registerWithSuffix (SLING-11918).

### Bekannte Probleme {#known-issues-14538}

Keine

### Eingebettete Technologien {#embedded-tech-14538}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.58-T20231123092841-619e1bd | [Oak API 1.58.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.58.0/index.html) |
| AEM SLING-API | Version 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version 2.23.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
