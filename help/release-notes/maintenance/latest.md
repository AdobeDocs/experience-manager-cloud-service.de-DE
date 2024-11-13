---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9a653fbe13b29fa60af7410fff178cbac6ca554d
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 74%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 18598 {#18598}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 18598, die am Donnerstag, 13. November 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 18311. Version 18459 wurde wegen eines Problems privat gemacht.

Die Funktionsaktivierung von 2024.11.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-18598}

* CQ-4357471: Unterstützung für Übersetzung mit i18n-Wörterbüchern in AEMaaCS hinzugefügt.
* FORMS-11646: Festlegen von globalContext-Variablen für AEM Forms-relevante Seiten.
* FORMS-14833: Die AEM Forms kann jetzt adaptive Formularfragmente in das endgültige Datensatzdokument (DoR) aufnehmen.
* FORMS-14255: Benutzer können jetzt von einer automatischen Speicherfunktion profitieren, mit der ein teilweise ausgefülltes Formular automatisch als Entwurf gespeichert wird. Sie können später zurückkehren, um das Ausfüllen auf demselben oder einem anderen Gerät abzuschließen.
* SITES-23591: Inhaltsfragmente: Aktualisierung von Inhaltsfragmenten für UUID-Unterstützung.
* SITES-25440: Inhaltsfragmente: CFM-Such-API zur Anzeige des Replikationsstatus.
* SITES-24369: Inhaltsfragmente: Verbesserungen an der OpenAPI-Dokumentation.
* SITES-25478: Inhaltsfragmente: Backend-Unterstützung für Verweise auf externe Assets hinzugefügt.
* SITES-26119: Inhaltsfragmente: Unterstützung für Verweise auf externe Assets im Referenztyp hinzugefügt.
* SITES-21199: Edge Delivery mit Universal Editor: Unterstützung für aus Seiten erstellte Vorlagen hinzugefügt.
* SITES-20311: Edge Delivery mit Universal Editor: Unterstützung für das Importieren von CSVs in Tabellen hinzugefügt.
* SITES-24821: Edge Delivery mit Universal Editor: Aem.page/aem.live wurde zum Standard für die Integration in Edge Delivery gemacht.

### Behobene Probleme {#fixed-issues-18598}

* CQ-4358730: CQPagePreviewGenerator schlägt fehl, wenn mehr als 10 Schlüssel übersetzt werden müssen.
* CQ-4358028: AEM Projekterstellung schlägt fehl, wenn ein Benutzer mit nur einer Gruppe &quot;Projekt-Administratoren&quot;eine neue Miniaturansicht auf die Projekterstellungsseite hochlädt.
* FORMS-14978: Aktivieren des Seitenladevorgangs für ein auf einer Kernkomponente basierendes Formular für den Design-Editor.
* FORMS-15682: Das Problem betrifft die FDM-Integration von AEM Forms und Dynamics. Wenn ein Benutzer ein Formular sendet, wird das Datensatzdokument (Document of Record, DOR) nicht als PDF-Anhang an das angegebene Entitätsfeld gesendet.
* FORMS-15799: Adobe Sign GovCloud-Signaturseite gibt keine Wiedergabe in iframe aus.
* FORMS-16113: Wenn ein Benutzer, der Administrator des Adobe Sign-Kontos ist, versucht, auf ein Dokument zuzugreifen, das von einem anderen Benutzer (auch einem Administrator) gesendet wurde, gibt die API für die Abruf-Vereinbarung möglicherweise eine andere Zustimmungs-ID zurück als diejenige, die beim Erstellen der Vereinbarung ursprünglich generiert wurde.
* FORMS-16596: Problem mit der Barrierefreiheit: Deaktivierte Schaltflächen werden von der Bildschirmlesehilfe nicht erkannt.
* GRANITE-53907: Dienstbenutzer können nicht als Workflow-Superuser identifiziert werden.
* SKYOPS-90560: Die neueste Version des Sling-Modells wirkt sich auf die Leistung beim Sling-Modell-Export aus.
* SITES-10575: MSM: Blueprint Bloomfilter Loader versucht, mehr als 100.000 Zeilen zu laden.
* SITES-20755: Inhaltsfragmente: Asset-Verweis mit UUID-Aktualisierung zeigt die Miniaturansicht nicht an.
* SITES-26253: Inhaltsfragmente: UUID-Migration: Das Thema „Sling-Auftrag“ wurde geändert, um es allgemein zu machen.
* SITES-21338: Inhaltsfragmente: referencedBy-Endpunkt gibt nicht den richtigen Seitenverweis zurück.
* SITES-24421: Inhaltsfragmente: Bearbeiten des CF-Endpunkts funktioniert nicht für über GET CF abgerufene Inhaltsfragmente.
* SITES-25461: Inhaltsfragmente: Beim Filtern nach Modell bei der Suche nach Inhaltsfragmenten sollte nicht zwischen Groß- und Kleinschreibung unterschieden werden.
* SITES-25471: Inhaltsfragmente: Fehlerbehebung bei der Validierung globaler Modelle im ModelValidatorServlet.
* SITES-25795: Inhaltsfragmente: Die CF-Modell-API schlägt fehl, wenn kein CQ-Datum festgelegt ist.
* SITES-25817: Inhaltsfragmente: Verbesserung an promoteLaunch: Letzte Promotion für CF-Launches wurde aktualisiert.
* SITES-26030: Inhaltsfragmente: /referencesTree-Endpunkt gibt einen benötigten Header nicht zurück.
* SITES-26031: Inhaltsfragmente: Replikationsstatus wird beim Endpunkt „CFM-Suche“ nicht zurückgegeben.
* SITES-26213: Inhaltsfragmente: Beim Rückgängigmachen der Veröffentlichung von Inhaltsfragmenten sollten nur veröffentlichte Verweise validiert werden.
* SITES-26226: Inhaltsfragmente: Workflow-Problem wird gestartet, wenn keiner der angegebenen Pfade verwendet werden kann.
* SITES-26238: Inhaltsfragmente: Die von der API zurückgegebenen Asset-Verweise haben eine andere Reihenfolge als die von JCR zurückgegebene Reihenfolge.
* SITES-25456: Ereignisse: Beim Verschieben einer Seite wird neben dem Ereignis „Seite verschoben“ das Ereignis „Seite gelöscht“ generiert.
* SITES-25658: Ereignisse: Ebene und sourceUrl werden in den Seiteninhaltsstatusereignissen nicht angegeben.
* SITES-6497: Launches: Das Erstellen einer Seite im Launch funktioniert nicht.
* SITES-25938: Launches: Unerwartete Löschung nach dem Übersetzungsprojekt.
* SITES-25393: Edge Delivery mit Universal Editor: Beim Rendern von formatiertem Rich Text mit einem einzigen Absatz gehen Textknoten verloren.
* SITES-24643: Edge Delivery mit Universal Editor: OpenGraph- und Twitter-Metadatenattribute funktionieren nicht im Seitenmetadatenmodell.
* SITES-25401: Experience Fragments: Langsame Aktualisierung der XF-Referenz.

### Bekannte Probleme {#known-issues-18598}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-18598}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-18598}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 21 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-18598}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.70.0 | [Oak-API 1.70.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.27.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
