---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 1a128e35be06d018ec25fb0e6a479cfd0d242dbd
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 12%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 14227 {#release-14227}

Nachfolgend sind die kontinuierlichen Verbesserungen für das Maintenance Release 14227 zusammengefasst, das am 9. November 2023 veröffentlicht wurde. Diese Wartungsversion ist eine Aktualisierung der vorherigen Wartungsversion 14029. Das Maintenance Release 14227 ersetzt 14157, um ein Problem zu beheben.

2023.11.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de).

### Verbesserungen {#enhancements-14227}

<!--* ASSETS-29631: Assets Cloud: Use dam:roles for secure delivery/search.-->
* CQ-4354515: Übersetzungen: Option zur Unterdrückung der Übersetzung referenzierter Ressourcen.
* FORMS-9993: Schritte zum Verschieben von Forms-Kernkomponenten in Skyline definieren.
* FORMS-10570: Integrierte EC-APIs zur API - Erster Router.
* GRANITE-48143: Upgrade von Sling ResourceMerger auf 1.4.4.
* SITES-14874: Eventing: Erweitern Sie die CFM-Struktur für Modellereignisse, um Metadatenänderungen einzuschließen.
* SITES-2719: Inhaltsfragmente: Tagging-Unterstützung für Inhaltsfragmentvarianten (wieder aktiviert).
* SITES-3619: Inhaltsfragmente: GraphQL CF-Varianten-Tags werden in JSON ausgegeben und nach Varianten-Tag gefiltert (erneut aktiviert).
* SITES-13750: Inhaltsfragmente: Löschen von Tags für ein Inhaltsfragmentmodell.
* SITES-13920: Inhaltsfragmente: Unterstützung der Konfiguration von minItems für mehrere Felder (Vorabversion).
* SITES-14080: Inhaltsfragmente: Tag &quot;Löschen&quot;einer Inhaltsfragmentvariante.
* SITES-14770: Inhaltsfragmente: Fragmentvarianten sollten die Eigenschaft fieldTags enthalten.
* SITES-15356: Inhaltsfragmente: Wird beim Erstellen einer Ressource als Antwort-Header zurückgegeben.
* SITES-15357: Inhaltsfragmente: Zulassen der Veröffentlichung von Fragmenten ohne deren Verweise.
* SITES-15938: Inhaltsfragmente: Fehlende Inhaltsreferenzmetadaten.
* SITES-16078: Inhaltsfragmente: Füllen Sie die Überprüfungsergebnis-Eigenschaft der Variante aus, wenn ein Fragment abgerufen wird.
* SITES-16545: Inhaltsfragmente: Fügen Sie einen Endpunkt zum Abrufen der Verweise auf die Variante eines Inhaltsfragments hinzu.
* SITES-16853: Inhaltsfragmente: Entfernen Sie /adobe/sites/cf/fragments/{fragmentId}/variation/{name}/tags -Endpunkt.

### Behobene Probleme {#fixed-issues-14227}

* Verschiedene Probleme mit der Barrierefreiheit behoben
* ASSETS-31015: Dateien können nicht in Assets mit unbekannten Dateierweiterungen hochgeladen werden.
* ASSETS-24739: Deaktivieren Sie Frame.io Custom Action Endpoint bei der Veröffentlichung.
* CMGR-49845: Content Backflow: Problem mit der Identifizierung des richtigen Stammpfads für den jeweiligen Checkpoint.
* CMGR-49709: Content Backflow: Aktualisieren Sie den Eigenschaftenfilter, um zusätzliche Eigenschaften zu ignorieren.
* CQ-4354503: Adobe IMS-Konfiguration wird zufällig entfernt.
* CQ-4354414: ConfigurationReplicationEventHandler erstellt viele einzelne Flush-Aktionen.
* CQ-4354401: Übersetzungen: Von Projekten erstellte Assets müssen gespeichert werden, bevor die Asset-Verarbeitung gestartet wird.
* CQ-4354430: Übersetzungen: Fehler beim Hinzufügen von Assets, die nicht Teil einer Sprachordnerstruktur sind, zu einem Übersetzungsprojekt.
* CQ-4354412: Übersetzungen: Löschen des Inhalts des Übersetzungsauftrags, nicht löschen alle referenzierten Inhalte.
* CQ-4354636: Übersetzungen: Beim Erstellen einer Sprachkopie auf Sprachstammenebene werden Pfade auf der Seite nicht angepasst.
* CQ-4354700: Workflows: Workflow-Nutzlastbildschirm wird nicht geladen.
* CQ-4354834: Workflows: Es ist nicht möglich, Kommentare in Workflow-Posteingangsaufgaben hinzuzufügen.
* FORMS-11302: Der Titel der im RTE bearbeiteten Komponente wird unter &quot;Editor für adaptive Formulare > Regeleditor&quot;falsch angezeigt.
* GRANITE-45706: Import mit i18n schlägt fehl, wenn der Schlüsselwert ‚Äú‘) Äù aufweist.
* SITES-14156: Eventing: Publish-Ereignisse werden nicht immer gesendet.
* SITES-14520: GraphQL: Schlechte Leistung bei paginierten grafischen Abfragen aufgrund von FT_SITES-2719.
* SITES-16444: GraphQL: DataFetchingException für gleichnamige Felder, die in der GraphQL-Abfrage fehlen.
* SITES-16225: GraphQL: Von der Java-API zurückgegebene Content-Typen von Modell- und Fragment-RTE-Feldern sind nicht korrekt.
* SITES-15373: Inhaltsfragmente: Die /adobe/sites/cf/fragments/{fragmentId}/variation/{name}/tags -Endpunkt verwendet nicht die richtigen Ressourcenbenennungskonventionen.
* SITES-15709: Inhaltsfragmente: Endpunktproblem Modell erstellen beim Erstellen eines booleschen Felds.
* SITES-15727: Inhaltsfragmente: Feld des Typs &quot;Tag&quot;kann nur einmal im Modell-Editor hinzugefügt werden.
* SITES-15782: Inhaltsfragmente: Fehlende eindeutige Eigenschaft vom Feldmodell des Auflistungstyps.
* SITES-15786: Inhaltsfragmente: Inhaltsfragmente können nicht in einem Ordner erstellt werden, der &quot;.
* SITES-15790: Inhaltsfragmente: Update des Location-Headers für die Versionserstellung.
* SITES-15923: Inhaltsfragmente: CF Admin zeigt nicht alle Ordner an.
* SITES-15987: Inhaltsfragmente: Abrufen von 500 beim Erstellen einer Variante.
* SITES-16067: Inhaltsfragmente: Der MIME-Typ des Felds für lange Textfragmente kann nicht geändert werden.
* SITES-16074: Inhaltsfragmente: Tag-Felder, die keine Zeichenfolge sind[] kann nicht aus JCR abgerufen werden.
* SITES-16079: Inhaltsfragmente: /fragments/{id}/references begann, um Duplikate zurückzugeben.
* SITES-16118: Inhaltsfragmente: Wenn ein Fragment gepatcht wird und ein Fragmentfeld im Modell fehlt, wird eine Ausnahme ausgelöst.
* SITES-16119: Inhaltsfragmente: Wenn die Fragmentmetadaten nicht erkannte Felder enthalten, wird eine Ausnahme ausgelöst.
* SITES-16121: Inhaltsfragmente: Beim Abrufen eines Modelldatumsfelds wird eine Ausnahme ausgelöst.
* SITES-16123: Inhaltsfragmente: Wenn es sich bei einer Ressource nicht um ein Inhaltsfragment handelt, löst der Endpunkt get fragments eine Ausnahme aus.
* SITES-16208: Inhaltsfragmente: Der ContentFragmentModelIdentifier stellt eine irreführende Titeleigenschaft bereit.
* SITES-16707: Inhaltsfragmente: Inhaltsfragmentmodelle werden nicht korrekt gelesen.
* SITES-16818: Inhaltsfragmente: Führen Sie das Löschen nur durch, wenn Tags vorhanden sind.
* SITES-16207: Inhaltsfragmente: Der Vorgang &quot;POST /adobe/sites/cf/models&quot;gibt zwei verschiedene OK-Statuscodes zurück.
* SITES-15616: Inhaltsfragmente: Der Veröffentlichungsendpunkt veröffentlicht manchmal nicht alle Verweise eines Inhaltsfragments.
* SITES-16027: Inhaltsfragmente: Referenzinformationen zu Varianten fehlen in der Fragmentantwort.
* SITES-16243: Inhaltsfragmente: Suchen und Ersetzen funktioniert nicht mit Feldern mit &quot;Render as: Multiple&quot;.
* SITES-16250: Inhaltsfragmente: Beim Patchen eines CF wird manchmal eine falsche eTag-Kopfzeile zurückgegeben.
* SITES-16686: Inhaltsfragmente: Inhaltsfragmente, die keine Fragmente sind, werden serialisiert, wenn die übergeordnete Referenz die maximale Tiefe erreicht.
* SITES-12880: Fast-Track: Fix-Lokalisierung für Sites > Einrichten von Analytics.
* SITES-16103: Experience Fragments: Target-Optionen werden aufgrund eines Konsolenfehlers nicht unter Cloud Services angezeigt.
* SITES-16001: MSM: Fähigkeit, Komponenten mit mehreren Feldern bei der Erstellung von Live Copy aus der Rollout-Konfiguration auszuschließen.
* SITES-16559: MSM: Rollout-Konfigurationen wurden während des Rollout-Prozesses für Experience Fragments entfernt.
* SITES-16797: MSM: Erneutes Aktivieren der Vererbung für ein CF-Feld im Editor korrigiert.
* SITES-16273: Seiten-Editor: Kopieren Sie den Einfügefehler in AEM Sites-Seiten aus der Zwischenablage.
* SITES-16126: Sites-Administrator: Die Authoring-Leistung ist für Benutzer ohne Administratorrechte nach SITES-10288 langsam.
* FORMS-10534: Im Regeleditor tritt bei der Auswahl der booleschen Operandenoption ein Fehler auf.
* FORMS-10248: Wenn der Datenwert vom Typ &quot;Boolesch&quot;ist, können Regeln Werte für Optionsfelder oder Kontrollkästchen-Komponenten nicht ordnungsgemäß festlegen.
* FORMS-11361: Die Dropdown-Komponente wählt standardmäßig automatisch die erste Option aus der Liste aus.
* FORMS-11413: Ein Fehler im Zusammenhang mit dem Forms Portal-Vorbefüllungs-Service wird von Adaptive Forms ausgelöst, auch wenn der Dienst nicht verwendet wird.
* FORMS-11433: Wenn eine Nicht-Formular-Komponente in einem adaptiven Formular enthalten ist, kann der Sendevorgang nicht abgeschlossen werden.
* FORMS-11206: Wenn ein Benutzer versucht, einen Veröffentlichungs-Workflow für ein adaptives Formular zu planen, funktioniert er nicht wie erwartet.
* FORMS-11546: Der Lighthouse hat eine fehlende ARIA-Beschriftung für wiederholte Bedienfelder in einem adaptiven Formular erkannt, was sich auf die Barrierefreiheit auswirkt.
* FORMS-11095: Das ARIA-Attribut wurde falsch für Telefonnummer, E-Mail-Adresse und Zahlenfelder definiert, was zu Zugänglichkeitsproblemen führt.

### Bekannte Probleme {#known-issues-14227}

Keine

### Eingebettete Technologien {#embedded-tech-14227}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.56-T20230927085643-189caed | [Oak-API 1.56.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.56.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
