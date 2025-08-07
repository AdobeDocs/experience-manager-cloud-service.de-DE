---
title: Konfigurieren von Übermittlungsaktionen für AEM Forms mit Edge Delivery Services
description: Erfahren Sie, wie Sie mithilfe von Edge Delivery Services Übermittlungsaktionen in AEM Forms konfigurieren können. Wählen Sie zwischen dem Formularübermittlungsdienst und der Übermittlungsaktion in AEM Publish, um Formulardaten sicher und effizient zu verarbeiten.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 12%

---

# Konfigurieren von Übermittlungsaktionen für AEM Forms

Konfigurieren Sie die Handhabung von Formularübermittlungen, um Daten mithilfe von AEM Forms mit Edge Delivery Services an Tabellen, E-Mail oder Backend-Systeme zu leiten.

## Schnellentscheidungsleitfaden

Wählen Sie Ihre Übermittlungsmethode:

| Methode | Am besten geeignet für | Setup-Komplexität | Anwendungsfälle |
|--------|----------|------------------|-----------|
| **Forms-Sendedienst** | Einfache Datenerfassung | Niedrig | Kontaktformulare, Umfragen, grundlegende Datenerfassung |
| **AEM-Veröffentlichungsübermittlung** | Komplexe Workflows | Hoch | Unternehmensintegrationen, benutzerdefinierte Verarbeitung, Workflows |

## Voraussetzungen

Bevor Sie Übermittlungsaktionen konfigurieren, müssen Sie:

- AEM Forms as a Cloud Service-Instanz
- Edge Delivery Services-Projekt konfiguriert
- Formular, erstellt mithilfe der Dokumenterstellung oder des universellen Editors
- Erforderliche Berechtigungen für Target-Ziele (Tabellen, E-Mail-Systeme oder AEM)

+++ Methode 1: Forms-Übermittlungsdienst

Der Forms Submission Service ist ein von Adobe gehosteter Endpunkt, der sich ideal für einfache Datenerfassungsszenarien eignet.

### Unterstützte Ziele

- **Tabellen**: Google Sheets, Microsoft Excel (OneDrive/SharePoint)
- **E-Mail**: Senden von Formulardaten an bestimmte E-Mail-Adressen

### Konfigurationsschritte

1. **Einrichten des Zielzugriffs**
   - Für Kalkulationstabellen: Erteilen Sie Bearbeitungsberechtigungen für `forms@adobe.com` in der Ziel-Kalkulationstabelle
   - Für E-Mail: Überprüfen, ob Empfänger-E-Mail-Adressen zugänglich sind

2. **Formularübermittlung konfigurieren**
   - Öffnen Sie das Formular in der Authoring-Umgebung
   - Sende-Aktion auf &quot;Forms Submission Service“ festlegen
   - Ziel-Kalkulationstabellen-URL oder E-Mail-Adressen angeben
   - Speichern und Veröffentlichen des Formulars

3. **Testübermittlung**
   - Senden von Testdaten über das Formular
   - Überprüfen, ob die Daten im Ziel angezeigt werden
   - Fehlerprotokolle überprüfen, wenn die Übermittlung fehlschlägt

### Wichtige Hinweise

- `forms@adobe.com` des Service-Kontos erfordert Bearbeitungszugriff auf Zieltabellen
- E-Mail-Benachrichtigungen werden sofort nach der Formularübermittlung gesendet
- Die Datenvalidierung erfolgt auf Service-Ebene

![Fluss des Forms-Übermittlungs-Service](/help/forms/assets/eds-fss.png)

+++

+++ Methode 2: AEM-Veröffentlichungsübermittlung

Senden Sie Formulardaten zur komplexen Verarbeitung direkt an Ihre AEM as a Cloud Service-Veröffentlichungsinstanz.

### Verwendung von AEM Publish

- Benutzerdefinierte AEM-Workflows nach der Übermittlung erforderlich
- Integration des Formulardatenmodells (FDM) in Datenbanken
- Integration von Drittanbieterdiensten (Marketo, Power Automate, Workfront Fusion)
- Azure Blob Storage- oder SharePoint-Dokumentbibliotheken
- Komplexe Server-seitige Validierungs- oder Verarbeitungslogik

### Verfügbare Übermittlungsaktionen

- [An REST-Endpunkt senden](/help/forms/configure-submit-action-restpoint.md)
- [E-Mail über AEM-E-Mail-Dienste senden](/help/forms/configure-submit-action-send-email.md)
- [Mit Formulardatenmodell senden](/help/forms/configure-data-sources.md)
- [AEM-Workflow aufrufen](/help/forms/aem-forms-workflow-step-reference.md)
- [An SharePoint senden](/help/forms/configure-submit-action-sharepoint.md)
- [An OneDrive senden](/help/forms/configure-submit-action-onedrive.md)
- [An Azure Blob Storage senden](/help/forms/configure-submit-action-azure-blob-storage.md)
- [An Microsoft Power Automate senden](/help/forms/forms-microsoft-power-automate-integration.md)
- [An Adobe Workfront Fusion Senden](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
- [An Adobe Marketo Engage senden](/help/forms/submit-adaptive-form-to-marketo-engage.md)

![Übermittlungsfluss der AEM-Veröffentlichung](/help/forms/assets/eds-aem-publish.png)

### Konfigurationsanforderungen

#### &#x200B;1. Konfiguration von AEM Dispatcher

Konfigurieren Sie Dispatcher auf Ihrer AEM-Veröffentlichungsinstanz:

- **Übermittlungspfade zulassen**: Ändern Sie `filters.any`, damit POST-Anfragen `/adobe/forms/af/submit/...` werden können
- **Keine Umleitungen**: Stellen Sie sicher, dass Dispatcher-Regeln keine Formularübermittlungspfade umleiten

#### &#x200B;2. OSGi Referrer-Filter

In der AEM OSGi-Konsole (`/system/console/configMgr`):

1. Suchen Sie nach „Apache Sling Referrer Filter“
2. Edge Delivery-Domain zur Liste „Hosts zulassen“ hinzufügen
3. Domänen wie `https://your-eds-domain.hlx.page` einschließen

#### &#x200B;3. CDN-Umleitungsregeln

Konfigurieren Sie Ihr Edge Delivery CDN, um Übermittlungen weiterzuleiten:

- Weiterleiten von Anfragen von `/adobe/forms/af/submit/...` an Ihre AEM-Veröffentlichungsinstanz
- Die Implementierung variiert je nach CDN-Anbieter (Fastly, Akamai, Cloudflare)

#### &#x200B;4. Konfiguration des Formulars

1. Erstellen eines Formulars im universellen Editor
2. Konfigurieren der Übermittlungsaktion für die AEM Forms-Zielaktion
3. Übermittlungsendpunktpfad angeben
4. Formular auf der Edge Delivery-Site veröffentlichen

+++

+++ Formulareinbettung (optional)

Einbetten von Formularen, die an einer Stelle erstellt wurden, in verschiedene Web-Seiten oder Sites.

### Anwendungsfälle

- Wiederverwenden von Standardformularen auf mehreren Landingpages
- Einbinden spezieller Formulare in von Dokumenten erstellte Inhalte
- Beibehaltung eines einzelnen Formulars in mehreren EDS-Projekten

### CORS-Konfiguration

Konfigurieren von Cross-Origin Resource Sharing in der Formularquelle:

1. **CORS-Header hinzufügen** um Quellantworten zu erstellen:
   - `Access-Control-Allow-Origin: https://your-host-domain.com`
   - `Access-Control-Allow-Methods: GET, OPTIONS`
   - `Access-Control-Allow-Headers: Content-Type`

2. **Beispielkonfiguration**:

       &#x200B;#-Konfiguration für die Site, auf der das Formular gehostet wird
       Kopfzeilen:
       - Pfad: /forms/**
       custom:
       access-control-allow-origin: https://host-domain.com
       access-control-allow-methods: GET, OPTIONS
   

### Einbettungsschritte

1. **Formular erstellen und veröffentlichen**
   - Erstellen eines Formulars mit dem Dokument-Authoring oder dem universellen Editor
   - Übermittlungsmethode konfigurieren (FSS oder AEM Publish)
   - In eigenständiger URL veröffentlichen

2. **Konfigurieren von CORS**
   - Einrichten von CORS-Headern auf der Formular-Quell-Site
   - Abruf des Formulars durch die Host-Seiten-Domain zulassen

3. **In Host-Seite einbetten**
   - Hinzufügen eines Formulareinbettungsblocks zur Host-Seite
   - Verweisen des Blocks auf die URL eines veröffentlichten Formulars
   - Veröffentlichen der Host-Seite

![Eingebettete Formulararchitektur](/help/forms/assets/eds-embedded-form.png)

+++

+++ Häufige Probleme

| Problem | Lösung |
|-------|----------|
| **Formularübermittlung schlägt fehl** | Überprüfen von Konsolenfehlern, Überprüfen der Endpunkt-URL, Bestätigen von Berechtigungen |
| **Eingebettetes Formular wird nicht angezeigt** | Konfigurieren von CORS-Headern an der Formularquelle, Überprüfen der Formular-URL |
| **403/401-Fehler bei AEM** | Sling Referrer-Filter aktualisieren, Authentifizierungseinstellungen überprüfen |
| **Daten erreichen das Arbeitsblatt nicht** | Überprüfen Sie, ob `forms@adobe.com` Bearbeitungszugriff hat, und überprüfen Sie die Tabellen-URL |
| **CORS-Fehler** | Fügen Sie der Formularquelle die richtigen `Access-Control-Allow-Origin` hinzu |

+++

## Konfigurationsbeispiele

+++ Dokumentenbasiertes Formular mit Tabellenübermittlung

1. Erstellen einer Formularstruktur in Google Docs/Sheets
2. Konfigurieren des Endpunkts für den Forms-Übermittlungsdienst
3. Zugriff `forms@adobe.com` Bearbeitung auf das Zielarbeitsblatt gewähren
4. Dokument auf Edge Delivery-Site veröffentlichen
5. Übermittlung und Datenfluss von Testformularen

+++

+++ Universeller Editor für Formulare mit AEM Workflow

1. Erstellen eines Formulars im universellen Editor
2. Konfigurieren der Sendeaktion zum „Aufrufen des AEM-Workflows“
3. Einrichten von Dispatcher und Referrer-Filter in AEM Publish
4. Konfigurieren von CDN-Routing-Regeln
5. Formular veröffentlichen und Workflow-Ausführung testen

+++

## Best Practices

- **Verwenden des Forms Submission Service** für einfache Datenerfassungsszenarien
- **Wählen Sie &quot;AEM Publish**, wenn komplexe Verarbeitung oder Integrationen erforderlich sind
- **Gründlicher Test** in der Staging-Umgebung vor der Produktionsbereitstellung
- **Übermittlungen überwachen** mithilfe von AEM-Protokollen und Konsolenfehlern
- **ordnungsgemäße Fehlerbehandlung implementieren** bei fehlgeschlagenen Übermittlungen
- **Daten validieren** sowohl auf Client- als auch auf Serverebene
- **HTTPS verwenden** für alle Formularübermittlungen und Datenübertragungen

## Verwandte Themen

- [Dokumentenbasiertes Authoring mit EDS Forms](/help/edge/docs/forms/tutorial.md)
- [Universeller Editor mit EDS Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
- [AEM Forms-Übermittlungsdienst](/help/forms/forms-submission-service.md)
- [Konfigurieren von Datenquellen](/help/forms/configure-data-sources.md)
- [AEM Forms Workflow-Referenz](/help/forms/aem-forms-workflow-step-reference.md)
