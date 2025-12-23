---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 5e01d1674134db73fc0f5c0013e10170ad6747f7
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 19%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 23862 {#23862}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 23862, die am Mittwoch, 23. Dezember 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 23482.

Die Funktionsaktivierung von 2026.1.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-23862}

* CQ-4361812: Unterstützung für optionalen param-Ordnerpfad in der REST-API wurde hinzugefügt. Beschreibung: Ein neues Übersetzungsprojekt wird von der API erstellt und in dem Pfad platziert, der durch den optionalen `folderPath` angegeben wird. Andernfalls wird standardmäßig der Stammpfad des Projekts `/content/projects`.
* FORMS-21960: Es wurde Unterstützung für die Bearbeitung auf der Arbeitsfläche auf lokalen für interaktive Kommunikation hinzugefügt, ähnlich wie in forms-spa.
* FORMS-22001: Es wurde eine Anleitung hinzugefügt, mit der die große Anzahl von `/etc.clientlibs/toggles.json` in AEM Forms as a Cloud Service reduziert werden kann.
* FORMS-22496: Anzeigen des rohen ResponseBody im Invoke-Service.
* FORMS-22495: Fügen Sie die Platzhaltereigenschaft in der SetProperty-Regel hinzu.
* FORMS-21925: UBS-Fußnotenformatierung: Zeigt alle Fußnoten im Formular beim Laden des Formulars an.
* FORMS-20536: Verfügbar machen einer Option für die vollständige Antwort in eventPayload im Regeleditor ohne Zuordnung.
* SITES-37199: Repository-Durchlauf durch Trigger von Anmerkungsfunktionen über einen nicht validierten `authorizables.json` verursacht Leistungseinbußen.
* SITES-37118: Commerce Optimizer-Unterstützung im Produkt-Cockpit.
* SITES-38029: Protokolle für das Tracking von MSM-Push bei Änderungsereignissen hinzufügen.
* SITES-37050: Unterstützung für „Veröffentlichung erzwingen“, sodass die Veröffentlichung von Inhaltsfragmenten, auf die andere veröffentlichte Ressourcen verweisen, aufgehoben werden kann.
* SITES-37142: Zum Ein-/Auschecken eines Inhaltsfragments über die PATCH für Inhaltsfragmente wurde eine Funktion hinzugefügt.
* SITES-37613: Geben Sie im Endpunkt für CF-API-Berechtigungen das Einchecken zurück, wenn der Benutzer ein Inhaltsfragment einchecken kann, oder checken Sie aus, wenn der Benutzer ein Inhaltsfragment auschecken kann.
* SITES-37835: Beim Versuch, mehrere Inhaltsfragmente mit demselben Titel, aber ohne angegebenen Namen zu erstellen, wird automatisch ein neuer Name generiert, anstatt aufgrund eines Konflikts fehlzuschlagen.
* SITES-36823: Edge Delivery mit universellem Editor: Umgekehrte Zuordnungen für Indizes sind nicht mehr erforderlich.
* SITES-34751: Edge Delivery mit universellem Editor: schlägt bei der Veröffentlichung für nicht unterstützte Dateitypen und Pfade außerhalb des zulässigen Bereichs fehl (frühzeitiger Zugriff).
* SITES-37888: Edge Delivery mit universellem Editor: Verwenden Sie das Suffix Alt als Synonym für Text für Links.
* SITES-19850: Edge Delivery mit universellem Editor: Unterstützung für mehrere Blätter in Kalkulationstabellen hinzufügen.
* SITES-32490: Edge Delivery mit universellem Editor: Unterstützung für data-aue-component und benutzerdefinierte data-aue-label zu Blöcken und Standardinhalten hinzufügen.
* SITES-37794: Edge Delivery mit universellem Editor: Der Assistent zur Vereinfachung der Seitenerstellung.
* SITES-36963: Migrieren des Zielgruppen-/Segmentendpunkts zur Target-API v3 für die Workspace-Unterstützung.

### Behobene Probleme {#fixed-issues-23862}

* CQ-4361831: Es wurde ein Problem behoben, bei dem genai_dropdown_span nicht definiert wurde.
* CQ-4360895: Fehlerkorrektur - Die Anzahl der ungenauen Übersetzungsauftragsstatus in einem Projekt während gleichzeitiger Aktualisierungen wurde korrigiert.
* CQ-4361599: Inhaltsfragmente werden nach dem Upgrade 2025.7 nicht mehr aus Übersetzungsaufträgen übersprungen.
* CQ-4360747: Wiederholbare Übersetzungsaufträge wurden korrigiert, sodass zu oft leere Payloads und Trigger erstellt wurden (NullPointerException in ScheduleRepeatTranslationProject).
* CQ-4359994: Es wurde eine Inkonsistenz des destinationLanguage-Feldtyps für ein- und mehrsprachige Projekte behoben.
* SITES-38153: Korrigieren Sie CF-Veröffentlichungs-Referenzanbieter für UUID-basierte Verweise.
* SITES-37594: Leistungsverbesserungen für die Funktion „Modell nach Tags“.
* SITES-37337: FragmentCreateProcessor: Bieten Sie zusätzliche Fehlerdetails in den Protokollen an.
* SITES-33666: Nicht lokalisierte Fehlermeldung „JSON des Fragments kann nicht gedruckt werden“ im Inhaltsfragment-Editor.
* SITES-33675: Hartcodierte Zeichenfolge „undefiniert“ im Inhaltsfragment-Editor > Zugehörige Inhalte.
* SITES-30715: Nicht lokalisierte Zeichenfolge „Allgemein“ im Inhaltsfragment-Editor.
* SITES-28592: Nicht lokalisierte Zeichenfolgen im Inhaltsfragmentmodell-Editor > Dialogfeld „Modell ist gesperrt“.
* SITES-977: Die Zeichenfolgen „Tags“ und „Sammlungen“ sind auf der Seite „Inhaltsfragment bearbeiten“ nicht lokalisiert.
* SITES-29699: Nicht lokalisierte Typen zulässiger Assets im Inhaltsfragment-Editor.
* SITES-25240: Call to action-Felder im Teaser-Modal haben keine sichtbare Beschriftung.
* SITES-24869: Abgeschnittene QuickInfo im Vorlageneditor > Trennzeichen > Richtlinie.
* SITES-19313: Fehler wird nicht lokalisiert, wenn eine Komponente per Drag-and-Drop in den Vorlagen-Editor gezogen und dort abgelegt wird.
* SITES-18103: Nicht lokalisierte Zeichenfolgen im Seiteneditor > Workflow.
* SITES-17501: Nicht lokalisierte Zeichenfolgen im Vorlageneditor > Komponentenrichtlinien-Editor.
* SITES-15091: Zeichenfolgen werden in den Eigenschaften der Textkomponente des Experience Fragments nicht lokalisiert.
* SITES-8113: Die Zeichenfolge &quot;Assets&quot; ist im Dialogfeld „Bild auswählen“ für „Vorlagen“ im Menü „Tools“ nicht lokalisiert.
* SITES-37587: Die Erstellung einer Live Copy schlägt in PROD mit NPE in RolloutManagerImpl weiterhin fehl.
* SITES-37335: Eigenschaften der Live Copy-Seite zeigen in der Konsole einen Fehler in Bezug auf cq-Tags an.
* SITES-36972: Schaltfläche „Rollout“ fehlt in der bearbeitbaren Symbolleiste.
* SITES-36570: Das Erstellen von Live Copies schlägt nach der Aktivierung des Umschalters „Chunked Create Live Copy“ fehl.
* SITES-36158: Rollout schlägt aufgrund einer Ausnahme fehl mit Vorgang fehlgeschlagen.
* SITES-35655: Der neue CF-Editor zeigt die aktive Vererbung an, nachdem sie unterbrochen wurde.
* SITES-31425: Nicht lokalisierte Fehlermeldung „Fehler: {} Feld ist erforderlich“ wird im Workflow „Starten“ in Sites angezeigt.
* SITES-19802: QuickInfos sind in den Kernkomponenten „Site“ > „Inhaltsverzeichnis“ nicht lokalisiert.
* SITES-36543: Es wurde ein Problem behoben, durch das der Administrator ausgecheckte Inhaltsfragmente bearbeiten konnte.
* SITES-36967: Es wurden NullPointerExceptions behoben, die beim Versuch auftraten, Miniaturdaten für beschädigte Inhaltsfragmente zu generieren.
* SITES-37791: Es wurde ein Problem behoben, bei dem der Aufruf von FindAndReplace für Zeichenfolgen, die `$` enthalten, fehlschlug.
* SITES-37018: Leeres Fehler-Popup beim Kopieren einer Seite mit einem nicht zulässigen Vorlagenpfad.
* SITES-36243: Edge Delivery mit universellem Editor: Fix 404s beim Veröffentlichen von `sling:OrderedFolder`.
* SITES-37684: Edge Delivery mit universellem Editor: Behebung der Leistungsbeeinträchtigung in Umgebungen mit vielen Sites.
* SITES-37840: Edge Delivery mit universellem Editor: Beheben von Veröffentlichungsfehlern aufgrund eines veralteten Zugriffstokens für Edge Delivery.
* SITES-37933: Edge Delivery mit universellem Editor: Beheben von Veröffentlichungsfehlern für gelöschte Ressourcen in Launches.
* SITES-37870: Edge Delivery mit universellem Editor: Korrigieren Sie das fehlerhafte Rendering von benutzerdefinierten Seitenmetadaten, wenn die Unterstützung für mehrere Felder aktiviert ist.
* SITES-37349: Edge Delivery mit universellem Editor: Rendern Sie mehrere Felder mit einzelnen Einträgen als Liste mit einem einzelnen Listenelement.
* SITES-36148: Edge Delivery mit universellem Editor: Korrigieren Sie die data-aue-label-Kennzeichnung für zusammengesetzte Mehrfachfelder.

### Bekannte Probleme {#known-issues-23862}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-23862}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-23862}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion wurden 23 identifizierte Schwachstellen behoben, was für einen noch robusteren Systemschutz sorgt.

### Eingebettete Technologien {#embedded-tech-23862}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,88,0 | [Oak 1.88.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.88.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2,30,2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
