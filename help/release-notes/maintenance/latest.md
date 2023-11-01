---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 01f148dbe885c96b27f88a88e7020a1008f4c1d3
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 23%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 14029 {#release-14029}

Nachfolgend sind die kontinuierlichen Verbesserungen für das Maintenance Release 14029 zusammengefasst, das am 25. Oktober 2023 veröffentlicht wurde. Diese Wartungsversion ist eine Aktualisierung der vorherigen Wartungsversion 13804.

2023.11.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de).

### Verbesserungen {#enhancements-14029}

* ASSETS-28551: Verbessern der Skalierbarkeit der Benutzeroberfläche &quot;Meine Linkfreigabe&quot;
* ASSETS-28566: Fügen Sie den Index dam:metadataForm Lucene hinzu
* ASSETS-29281: Aktualisierung von RAPI zum Senden von v2-Download-Ereignissen

### Behobene Probleme {#fixed-issues-14029}

* ASSETS-25199: Bild-Core-Komponente zeigt keine richtigen Smart-Zuschnitte an
* ASSETS-26142: unified-shell.js customEnvLabel wird nicht festgelegt oder erneut versucht, wenn die Erkennungsanforderung fehlschlägt oder unterbrochen wird
* ASSETS-26416: Relative Datumseigenschaft, die im Suchformular immer als &quot;Vor 1 Tag(en)&quot;definiert ist
* ASSETS-27321: Löschen des Gruppen-Cache bei Änderungen der Teammitgliedschaft
* ASSETS-27591: Korrigieren der Abhängigkeit von der alten org.json
* ASSETS-28439: Smart-Tags Blockierungsliste NPE, wenn die globale Blockierungsliste nicht konfiguriert ist
* ASSETS-28612: BlockedTagResolver-Korrektur in &quot;repository-api&quot;
* ASSETS-28634: Das OmniSearch-Feld im Adobe-Stock erhält keine Asset-Daten automatisch hinzugefügt
* ASSETS-28727: In der Liste &quot;Konfiguration von Verarbeitungsprofilen&quot;werden die angegebenen benutzerdefinierten Werte für Höhe und Breite nicht angezeigt
* ASSETS-29056: Hinzufügen von Transkodierungsausgabeformaten AEM standardmäßigen Verarbeitungsprofilen
* ASSETS-29105: Restriction Provider fehlt in SecurityProviderRegistration requiredServicePids im RDE-Funktionsmodell
* ASSETS-29106: Adobe-Stock-Ansicht gibt Fehler auf Unified Shell-aktivierten AEM aus
* ASSETS-29115: Konfigurationseigenschaft für Einschränkungsanbieter-Pfade entfernen
* ASSETS-29208: Fehler beim Hochladen von Assets, die durch Anfragen verursacht werden, die an einen Autoren-Pod gesendet werden, bevor der Dienst CompleteUploadAssetServlet registriert wird
* ASSETS-29297: Problem beim Erstellen der Option Suche mit ausgechecktem Filter speichern
* ASSETS-29363: Metadatenprofil, das keine Standardwerte für IPTC anwendet
* ASSETS-29404: Bericht &quot;Linkfreigaben&quot;auf Abfragegrenze gesetzt
* ASSETS-29431: Alte Funktionsmarkierungen entfernen
* ASSETS-29443: Unified Shell Hero bleibt sichtbar und anklickbar, wenn der Granite Shell-Kopfzeilenmodus in &quot;Auswahl&quot;geändert wird
* ASSETS-29476: scene7DAMService.getS7FileReference(asset) API-Aufruf gibt nicht den erwarteten Wert zurück.
* ASSETS-29515: Assets/Knoten mit &quot;jcr:lastModifiedBy&quot;: &quot;workflow-process-service&quot; werden in der Listenansicht als &quot;externer Benutzer&quot;angezeigt
* ASSETS-29579: Benutzer ohne Administratorrechte können Bildset nicht erstellen
* ASSETS-29631: Verwenden Sie dam:roles für sichere Bereitstellung/Suche
* ASSETS-29689: dc:roles (und die neue Eigenschaft dam:roles) sollte von AEM Seite gefiltert werden
* ASSETS-29738: Asset-Upload-Beschränkung schlägt mit NullPointerException fehl
* ASSETS-29779: Kleine Assets können nicht in Web verarbeitet werden, da sie sich nicht im Blob-Speicher befinden
* ASSETS-29892: Metadatenexport schlägt bei Ordner mit einer großen Anzahl von Assets fehl
* ASSETS-29996: &quot;Externer Benutzer&quot;als Modifikator beim zeitweisen Hochladen von Assets nur in der PROD-Instanz
* ASSETS-30167: HTML für adobe_dam:limits bricht nach dem Hochladen eines Assets ab
* ASSETS-30276: Link-Benutzeroberfläche freigeben: kann nicht über Asset-Details freigegeben werden
* ASSETS-30434: Ereignis &quot;Verarbeitung abgeschlossen&quot;für Asset wurde nicht an Pipeline gesendet
* ASSETS-30519: RAPI zu REDMetricsServletFilter hinzufügen
* CQ-4354413: QueryBuilder: Abfragen mit eckigen Klammern werden fälschlicherweise in xpath übersetzt
* CQ-4354834: Kommentar kann in Posteingangsaufgabe nicht hinzugefügt werden
* CQ-4354836: Workflow kann nicht gestartet werden oder Aufgabe über die Projektekonsole erstellen
* CQ-4354867: ToggleCondition-Referenz bezieht sich auf nicht vorhandenes Feld in InstanceActionServlet
* CQ-4354895: AEM Translation Kit: 12. Oktober
* GRANITE-45560: Allgemeine Schemabestellung in Eventing-Umschlag
* GRANITE-47267: Update auf Apache Felix HTTP Jetty 4.2.18
* GRANITE-47599: Inhaltsimporte schlagen seit der Aktualisierung 13323 fehl (JCRVLT-721)
* GRANITE-47873: Update auf Apache Felix Webconsole 4.9.6

### Bekannte Probleme {#known-issues-14029}

* ASSETS-31015: Dateien können nicht in Assets mit unbekannten Dateierweiterungen hochgeladen werden.

### Eingebettete Technologien {#embedded-tech-14029}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.56-T20230927085643-189caed | [Oak-API 1.56.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.56.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
