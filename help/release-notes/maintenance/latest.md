---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 1251f36ece4449d8be6a40f34421351161bf3b23
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 18%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 12549 {#release-12549}

Nachfolgend sind die kontinuierlichen Verbesserungen für das Maintenance Release 12549 zusammengefasst, das am 4. Juli 2023 veröffentlicht wurde. Diese Wartungsversion ist eine Aktualisierung der vorherigen Wartungsversion 12255. Das Maintenance Release 12549 ersetzt 12441, um zwei Probleme zu beheben.

2023.7.0 Die Funktionsaktivierung stellt den vollständigen Funktionsumfang für dieses Maintenance Release bereit. Siehe [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) für weitere Informationen.

### Verbesserungen {#enhancements-12549}

- Forms-5054: Hinzugefügte Unterstützung für alle [statues](https://opensource.adobe.com/acrobat-sign/acrobat_sign_events/webhookeventsagreements.html) unterstützt von Adobe Sign.

### Behobene Probleme {#fixed-issues-12549}

- Verschiedene Aktualisierungen zur Barrierefreiheit
- SITES-12688: Seiten-Editor: Logischer Operator ODER in der Asset Finder-Suche nicht ordnungsgemäß funktioniert
- SITES-4951: Seiten-Editor: Die Tag-Suche im Seiteneditor findet keine Untertags
- SITES-12465: Experience Fragments: Pfeiltasten funktionieren nicht im Dialogfeld Experience Fragment-Komponente
- SITES-12893: Experience Fragments: Anwenden einer zirkulären Referenzvalidierung für Experience Fragments
- SITES-12715: Experience Fragments: Cloud Service-Konfigurationen, die auf den Experience Fragments-Ordner angewendet werden, bleiben nicht bestehen
- SITES-13097: Experience Fragments: Es ist nicht möglich, Experience Fragments zu einem Übersetzungsprojekt hinzuzufügen
- SITES-13165: GraphQL: Standardverhalten für das Filtern von Nullwerten wiederherstellen
- SITES-12577: Link-Checker: Transformator schreibt Links nicht gelegentlich um
- SITES-13559: MSM: Beim Rollout einer Komponente wird die Ausnahme &quot;Ist nicht änderbar&quot;ausgelöst
- SITES-11757: MSM: Rollout-Konfiguration von übergeordneter Seite übernehmen wird für untergeordnete Seiten nicht zurückgesetzt
- SITES-14073: Sites-Admin: CSV-Bericht schlägt mit 500 fehl, wenn keine zu exportierende Eigenschaft ausgewählt wird
- Forms-7648: Die maximale Anzahl von Ziffern in einer Komponente vom Typ &quot;Numerisches Feld&quot;kann nicht überprüft werden. Das Überprüfungsskript funktioniert nicht.
- Forms-8177: Wenn der Forms-Dienst aktiv ist, wird die `com.adobe.aem.formsndocuments.publish.AssetReferenceProvider Failed to retrieve asset dependencies` Fehlerereignisse.
- Forms-8300: Wenn ein Benutzer versucht, eine Aufgabe zuzuweisen, nachdem er sie geöffnet hat, lädt die Delegierungsantwort die Aufgabe neu, anstatt die Benutzeroberfläche AEM Posteingangs des Benutzers zu öffnen.
- Forms-8500: Im Microsoft® Edge-Browser mit aktivierter IE-Modus-Option kann HTML5 Forms nicht geöffnet werden.
- Forms-8541: Beim Rendern einer adaptiven Forms tritt eine Nullzeiger-Ausnahme auf.
- Forms-8964: Wenn ein Formular auf einem Android™-Gerät in Google Chrome oder Mozilla Firefox geöffnet wird, kann der in der Textfeldkomponente eingegebene Text nicht entfernt werden.
- Forms-9026: Wenn ein Benutzer ein adaptives Formular erstellt, das auf einem komplexen und gültigen JSON-Schema basiert, verwandte JSON-Schemafelder in den adaptiven Forms-Editor zieht, um adaptive Forms-Felder zu erstellen, und das Fenster des adaptiven Forms-Editors aktualisiert, werden alle Felder gelöscht und der Editor für adaptive Forms wird leer angezeigt.
- Forms-9263: Wenn der Anzeigetext einer Kontrollkästchenoption Sonderzeichen enthält, können Benutzer solche Kontrollkästchen nicht auswählen.
- Forms-8668: Beim Rendern einer PDF-Vorschau eines Formulars werden einige nicht erforderliche Java™-Stack-Dumps in den Fehlerprotokollen angezeigt. Es gibt jedoch keine Probleme beim Rendern des Formulars.
- Forms-8116: Wenn Regeln auf die Komponente Adaptiver Forms-Container angewendet werden, werden die angewendeten Regeln nicht gespeichert.
- Forms-7906: Wenn ein adaptives Formular zu einer AEM Sites-Container-Komponente hinzugefügt wird, kann der Regeleditor nicht geöffnet werden.
- Forms-8846: Die Eigenschaft &quot;Bindungsverweis&quot;funktioniert nicht für die Komponente Adaptive Forms-Anlagen.
- Forms-9072: Wenn Sie beim Erstellen eines Formularfragments nach einem Schema suchen, gibt das Suchergebnis kein Schema zur Auswahl zurück.
- Forms: Es wurden mehrere Fehler im Zusammenhang mit der Barrierefreiheit behoben, um die Barrierefreiheit von AEM Forms-Funktionen zu verbessern.

### Bekannte Probleme {#known-issues-12549}

- SKYOPS-61385: Beim neuesten Dispatcher-Update wurden bestimmte ungültige reguläre Ausdrücke, die zuvor still von ignoriert wurden, von `libpcre1` von der aktualisierten `libpcre2` während der Bereitstellung. Die Dispatcher-Konfigurationsprüfung wird in Kürze aktualisiert, um diese auch noch früher zu identifizieren.

### Eingebettete Technologien {#embedded-tech-12549}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.50-T20230405052634-f9df4aa | [Oak-API 1.50.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.50.0/index.html) |
| AEM SLING-API | Version: 2.27.0 | [Apache Sling-API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
