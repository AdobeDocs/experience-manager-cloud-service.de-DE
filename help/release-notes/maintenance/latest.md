---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 0dab7428d8ae5ec4c11a88ff310fad649a365868
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 20%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 13665 {#release-13665}

Nachfolgend sind die kontinuierlichen Verbesserungen für das Maintenance Release 13665 zusammengefasst, das am 27. September 2023 veröffentlicht wurde. Dieses Maintenance Release ersetzt Version 13420.

2023.10.0 Die Funktionsaktivierung bietet die vollständigen Funktionen für dieses Maintenance Release. Siehe [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) für weitere Informationen.

### Verbesserungen {#enhancements-13665}

* Verschiedene Verbesserungen an den Inhaltsfragment-APIs.
* ASSETS-26713: Assets-Dashboard: Das neue Dashboard der Experience-Benutzeroberfläche ist jetzt über die Touch-Benutzeroberfläche erreichbar.
* SITES-11206: Inhaltsfragmente: Such-API für Inhaltsfragmente.
* SITES-11262: Inhaltsfragmente: Schaltfläche zum Wechseln zum neuen Inhaltsfragment-Editor.
* SITES-15447: Kernkomponenten: Version 2.23.4.

### Behobene Probleme {#fixed-issues-13665}

* Verschiedene Übersetzungsaktualisierungen.
* CQ-4354428: Workflows: Aufgabe im Posteingang kann nicht abgeschlossen werden.
* SITES-9733: Inhaltsfragmente: Asset-Verweise im Inhaltsfragmentverweis-Bedienfeld zeigen Verweise auf 0 (null).
* SITES-14561: Inhaltsfragmente: Korrigierte und verbesserte HTML zur Markup-Konvertierung.
* SITES-14882: Inhaltsfragmente: Sobald wir Inhaltsfragmente bearbeiten und die Registerkarte schließen, ohne auf die Schaltfläche &quot;Speichern&quot;oder &quot;Schließen&quot;zu klicken, werden die Werte gespeichert.
* SITES-15167: Inhaltsfragmente: Durch das Patchen einer Variante mit einer ungültigen Payload werden nicht 400, sondern 500 zurückgegeben.
* SITES-15514: Inhaltsfragmente: Falsch formatierte Markdown-Ausgabe für Tabellen in RTE.
* SITES-15661: Inhaltsfragmente: Verwenden Sie keine eindeutigen Einschränkungen und ordnen Sie Elemente in Referenzfeldern in der Fragments-API neu an.
* SITES-15730: Screens: Screens-Kanalvorschau-Funktion funktioniert nicht auf Dashboard.
* SITES-15995: Inhaltsfragmente: MIME-Typen von Modellen und langen Textfeldern für Fragmente sind fest codiert.
* SITES-16074: Inhaltsfragmente: Tag-Felder, die keine Zeichenfolge sind[] kann nicht aus JCR abgerufen werden.
* SITES-16084: Inhaltsfragmente: CFHomeCardModelImpl fehlt der Zielnavigator.
* SITES-14773: Experience Fragments: Die Link-Referenz wird im Experience Fragment nicht aktualisiert.
* SITES-14899: Experience Fragments: Mehrere Angebote, die für XF-Varianten in Target erstellt wurden.
* SITES-8590: GraphQL: Kodierungsprobleme mit Variablen in persistenten Abfragen.
* SITES-9224: GraphQL: Ausnahmefehler &quot;Writer has been closed&quot;in GraphQLServlet.
* SITES-14800: GraphQL: Ausnahme bei persistenten GraphQL-Abfragen mit Variablen.
* SITES-15586: GraphQL: Problem mit persistenten Abfragen, die mit Nullwerten filtern.
* SITES-15622: GraphQL: Problem mit persistenten Abfragen mit Zahlen und booleschen Parametern.
* SITES-15654: GraphQL: Problem mit Vereinigungen und Eigenschaften mit demselben Namen.
* SITES-15267: Launches: Die Promotion nimmt keine Launch-Seiten auf, die vor der Änderung der Launch-Konfiguration geändert wurden.
* SITES-15406: Launches: Launch-Seite kann nicht hinzugefügt werden.
* SITES-15427: Starts: Inkonsistentes Verhalten des Bereichs &quot;Aktuelle Seite und Unterseiten bewerben&quot;.
* SITES-15429: Launches: Authoring-Seiten, die beim Anzeigen von Launches gelöscht wurden.
* SITES-15462: Launches: Der Prozess &quot;Automatische Promotion&quot;veröffentlicht Seiten außerhalb des Promotion-Bereichs.
* SITES-15815: Starts: Gelöschte Seite aus Launch bewirkt, dass Launch die Seite nicht erfolgreich weiterleitet.
* SITES-15223: Seiten-Editor: Es ist nicht möglich, die Größe von Komponenten im Emulator für die Tablet-Größe zu ändern.
* SITES-15463: Seitenvorlagen: Vorlagen können nicht veröffentlicht werden.

### Bekannte Probleme {#known-issues-13665}

Ohne

### Eingebettete Technologien {#embedded-tech-13665}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.54-T20230817132355-3800a65 | [Oak-API 1.54.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
