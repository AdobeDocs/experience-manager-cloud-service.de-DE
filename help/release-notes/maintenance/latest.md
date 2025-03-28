---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 67b9a5f73f1f8c599e902a0ac0d8efbc614c7f75
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 32%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version X {#X}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion X, die am 1. April 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 19823.

Die Funktionsaktivierung von 2025.4.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-X}

FORMS-19068: Übermittlungsaktionen für den AEP-Connector in Forms Manager-APIs werden nun unterstützt, um die Funktionen zur Formulardatenintegration zu verbessern.

FORMS-18513: Es wurde Unterstützung für die Umwandlung von Datenbäumen in AEP Connector implementiert, um die Assistentenfunktionen und Datenverarbeitungsfunktionen zu erweitern.

FORMS-18432: Es wurde eine formularspezifische (Regex-basierte) Client-seitige Vorbefüllungskonfiguration implementiert, um eine selektive Vorbefüllungsfunktion ohne Änderungen auf OSGi-Ebene zu ermöglichen.

FORMS-17551: Es wurde Unterstützung für Datensatzdokumente (DoR) für SharePoint-Listenintegrationen hinzugefügt.

### Behobene Probleme {#fixed-issues-X}

FORMS-19028: Die Client-seitige Vorbefüllungsfunktion unterbricht die Formularereignisverarbeitung, was verhindert, dass Value Commit- und DOMContentLoaded-Ereignisse beim Laden des Formulars ordnungsgemäß ausgelöst werden.

FORMS-18360: Verbesserte Verwaltung des SharePoint-Listenbereichs für Team-Sites in Forms Document Management zur Verbesserung der Datenorganisation und Zugriffskontrolle.

FORMS-18325: Die Cloud-Konfiguration für Adobe Experience Platform (AEP) wurde hinzugefügt, um die Funktionen für die Integration und Verarbeitung von Formulardaten zu verbessern.

FORMS-18213: Es wurde eine Funktion zum Ausblenden/Ausschließen deaktivierter Felder aus dem Datensatzdokument (DoR) implementiert, um die Dokumentklarheit und das Benutzererlebnis zu verbessern.

FORMS-18189: Die Handhabung benutzerdefinierter Funktionen wurde geändert, um die Fehlerprotokollierung für leere Client-Bibliotheken zu verhindern und die Fehleranzeige in der Benutzeroberfläche zu verbessern.

FORMS-18426: Die SharePoint-Listensuchfunktion schlägt fehl, wenn Listennamen Sonderzeichen enthalten (z. B. &quot;-„), was sich auf die Formularintegration mit SharePoint-Listen auswirkt.

FORMS-18375: Auf Foundation-Komponenten basierende Formulare wählen fälschlicherweise reCAPTCHA-Konfigurationen aus `conf/global` Ordner aus, wenn kein bestimmter Konfigurations-Container ausgewählt ist.

FORMS-18304: PDF/A-1b-Dokumente, die die Validierung in Acrobat und LiveCycle ES4 bestehen, werden in AEM 6.5 Forms aufgrund von geräteabhängigen Farbfehlern fälschlicherweise als nicht konform gekennzeichnet.

FORMS-18271: Der Forms-Design-Editor zeigt nicht lokalisierte Fehlermeldungen an, die das Benutzererlebnis bei der Konfiguration von Formularen und der Anpassung von Designs beeinträchtigen.

FORMS-18068: Probleme mit der fett gedruckten Textwiedergabe im Datensatzdokument (DoR) für Optionsfeld- und Kontrollkästchen-Gruppen unter Verwendung von Rich-Text-Feldern.

FORMS-7016: Die Reihenfolge des Tastaturfokus im Formular-Editor folgt nicht der logischen Navigation.

FORMS-6950: Es wurden erforderliche ARIA-Rollen und -Attribute zu den Strukturansichtskomponenten des Dateisystemnavigators hinzugefügt, um die Barrierefreiheit der Sprachausgabe zu verbessern und den WCAG 4.1.2-Standard für Name, Rolle und Wert (Stufe A) zu erfüllen.

### Bekannte Probleme {#known-issues-X}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-X}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-X}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt X identifizierte Schwachstellen und verstärkt unser Engagement für zuverlässigen Systemschutz.

### Eingebettete Technologien {#embedded-tech-X}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.76.0 | [Oak-API 1.76.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.27.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
