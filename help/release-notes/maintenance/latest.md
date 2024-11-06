---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 90e1ca38bd517215a631573987462a716bfed160
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 32%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 18459 {#18459}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 18459, die am Mittwoch, 5. November 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 18311.

Die Funktionsaktivierung von 2024.11.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-18459}

* CQ-4357471: Unterstützung für i18n-Wörterbuchübersetzung in AEMaaCS hinzugefügt.
* SITES-23591: Inhaltsfragmente: Aktualisierung von Inhaltsfragmenten für UUID-Unterstützung.
* SITES-25440: Content Fragments: CFM Search API zur Anzeige des Replikationsstatus.
* SITES-24369: Inhaltsfragmente: Verbesserungen der OpenAPI-Dokumentation.
* SITES-25478: Inhaltsfragmente: Fügen Sie Backend-Unterstützung für externe Asset-Verweise hinzu.
* SITES-26119: Inhaltsfragmente: Unterstützung externer Asset-Referenzen im Referenztyp hinzufügen.
* SITES-21199: Edge Delivery mit Universal Editor: Unterstützt Vorlagen, die aus Seiten erstellt wurden.
* SITES-20311: Edge Delivery mit Universal Editor: Unterstützt jetzt das Importieren von CSVs in Tabellen.
* SITES-24821: Edge Delivery mit Universal Editor: Legen Sie als Standard für die Integration in Edge Delivery aem.page/aem.live fest.

### Behobene Probleme {#fixed-issues-18459}

* CQ-4358730: CQPagePreviewGenerator schlägt fehl, wenn mehr als 10 Schlüssel übersetzt werden müssen.
* FORMS-14978: Aktivieren des Seitenladevorgangs für ein auf einer Kernkomponente basierendes Formular für den Design-Editor.
* FORMS-16596: Problem mit der Barrierefreiheit: Deaktivierte Schaltflächen werden vom Reader &quot;Bildschirm&quot;nicht erkannt.
* SITES-10575: MSM: Blueprint Bloomfilter Loader versucht, mehr als 100.000 Zeilen zu laden.
* SITES-20755: Inhaltsfragmente: Asset-Referenz mit UUID-Aktualisierung zeigt die Miniaturansicht nicht an.
* SITES-26253: Inhaltsfragmente: UUID-Migration: Ändern Sie das Thema des Sling-Auftrags in &quot;generisch&quot;.
* SITES-21338: Inhaltsfragmente: referencedBy -Endpunkt gibt nicht den richtigen Seitenverweis zurück.
* SITES-24421: Inhaltsfragmente: Der Endpunkt &quot;CF bearbeiten&quot;funktioniert nicht für über GET CF abgerufene Inhaltsfragmente.
* SITES-25461: Inhaltsfragmente: Beim Filtern nach Modell bei der Suche nach Inhaltsfragmenten sollte nicht zwischen Groß- und Kleinschreibung unterschieden werden.
* SITES-25471: Inhaltsfragmente: Fehlerbehebung bei der Validierung globaler Modelle im ModelValidatorServlet.
* SITES-25795: Inhaltsfragmente: Die CF-Modell-API schlägt fehl, wenn kein CQ-Datum festgelegt ist.
* SITES-25817: Content Fragments: Enhance promoteLaunch: update last promotion for CF Launches.
* SITES-26030: Inhaltsfragmente: Endpoint /referencesTree gibt den benötigten Header nicht zurück.
* SITES-26031: Inhaltsfragmente: Der Replikationsstatus wird beim CFM-Suchendpunkt nicht zurückgegeben.
* SITES-26213: Inhaltsfragmente: Inhaltsfragmente, deren Veröffentlichung rückgängig gemacht wird, sollten nur veröffentlichte Verweise validieren.
* SITES-26226: Inhaltsfragmente: Workflow-Problem starten, wenn keiner der angegebenen Pfade verwendet werden kann.
* SITES-26238: Inhaltsfragmente: Die von der API zurückgegebenen Asset-Referenzen haben eine andere Reihenfolge als die von JCR zurückgegebene Reihenfolge.
* SITES-25456: Ereignisse: Beim Verschieben einer Seite wird neben dem Ereignis &quot;Seite verschoben&quot;ein Ereignis generiert, bei dem die Seite gelöscht wurde.
* SITES-25658: Ereignisse: Die Tier- und sourceUrl-Elemente werden in den Seiteninhaltsstatusereignissen nicht angegeben.
* SITES-6497: Launches: Seite im Launch erstellen funktioniert nicht.
* SITES-25938: Launches: Unerwartete Löschungen nach der Übersetzung.
* SITES-25393: Edge Delivery mit Universal Editor: Textknoten gehen beim Rendern von formatiertem Rich Text mit einem einzigen Absatz verloren.
* SITES-24643: Edge Delivery mit Universal Editor: OpenGraph- und twitter-Metadatenattribute funktionieren nicht im Seitenmetadatenmodell.
* SITES-25401: Experience Fragments: Langsame XF-Referenzaktualisierung


### Bekannte Probleme {#known-issues-18459}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-18459}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-18459}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 21 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-18459}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.70.0 | [Oak-API 1.70.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.27.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
