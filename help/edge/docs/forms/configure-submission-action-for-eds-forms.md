---
title: Konfigurieren von Übermittlungsaktionen für AEM Forms mit Edge Delivery Services
description: Erfahren Sie, wie Sie mithilfe von Edge Delivery Services Übermittlungsaktionen in AEM Forms konfigurieren können. Wählen Sie zwischen dem Formularübermittlungsdienst und der Übermittlungsaktion in AEM Publish, um Formulardaten sicher und effizient zu verarbeiten.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: 2d16a9bd1f498dd0f824e867fd3b5676fb311bb3
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 13%

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

#### &#x200B;1. Aktualisieren der AEM-Instanz-URL in Edge Delivery

Aktualisieren Sie die URL der AEM Cloud Service-Instanz in der `constant.js`-Datei im `form` unter `submitBaseUrl`. Sie können die URL basierend auf Ihrer Umgebung konfigurieren:

**Für Cloud Service-Instanz**

```js
export const submitBaseUrl = '<aem-publish-instance-URL>';
```

**Für lokale Entwicklung**

```js
export const submitBaseUrl = 'http://localhost:<port-number>';
```

#### &#x200B;2. OSGi Referrer-Filter

Konfigurieren Sie den Referrer-Filter, um Ihre spezifischen Edge Delivery-Site-Domains zuzulassen:

1. Erstellen oder aktualisieren Sie die OSGi-Konfigurationsdatei: `org.apache.sling.security.impl.ReferrerFilter.cfg.json`

2. Fügen Sie die folgende Konfiguration mit Ihren spezifischen Site-Domains hinzu:

   ```json
   {
     "allow.empty": false,
     "allow.hosts": [
       "main--abc--adobe.aem.live",
       "main--abc1--adobe.aem.live"
     ],
     "allow.hosts.regexp": [
       "https://.*\\.aem\\.live:443",
       "https://.*\\.aem\\.page:443",
       "https://.*\\.hlx\\.page:443",
       "https://.*\\.hlx\\.live:443"
     ],
     "filter.methods": [
       "POST",
       "PUT",
       "DELETE",
       "COPY",
       "MOVE"
     ],
     "exclude.agents.regexp": [
       ""
     ]
   }
   ```

3. Bereitstellen der Konfiguration über Cloud Manager

Weitere Informationen zur Konfiguration des OSGi-Referrer-Filters finden Sie im [Referrer-Filter](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter)Handbuch.

#### &#x200B;3. CORS-Probleme (Cross-Origin Resource Sharing)

Konfigurieren Sie CORS-Einstellungen in AEM, um Anfragen von Ihren spezifischen Edge Delivery-Site-Domains zuzulassen:

**Entwickler-Localhost**

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true
```

**Edge Delivery Sites - Jede Site-Domain einzeln hinzufügen**

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc--adobe\.aem\.live$)#" CORSTrusted=true
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc1--adobe\.aem\.live$)#" CORSTrusted=true
```

**Ältere Franklin-Domains (falls noch in Verwendung)**

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

>[!NOTE]
>
>Ersetzen Sie `main--abc--adobe.aem.live` und `main--abc1--adobe.aem.live` durch Ihre tatsächlichen Site-Domains. Jede Site, die vom selben Repository gehostet wird, erfordert einen separaten CORS-Konfigurationseintrag.

Weitere Informationen zur CORS-Konfiguration finden Sie im [CORS-Konfigurationshandbuch](https://experienceleague.adobe.com/de/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors).


Informationen zum Aktivieren von CORS für Ihre lokale Entwicklungsumgebung finden Sie im Artikel [Grundlegendes zu CORS (Cross-Origin Resource Sharing)](https://experienceleague.adobe.com/de/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing) .

<!--
#### 4. CDN Redirect Rules

Configure your Edge Delivery CDN to route submissions:

- Route requests from `/adobe/forms/af/submit/...` to your AEM Publish instance
- Implementation varies by CDN provider (Fastly, Akamai, Cloudflare)-->

#### &#x200B;4. Konfiguration des Formulars

1. Erstellen eines Formulars im universellen Editor
2. Konfigurieren der Übermittlungsaktion für die AEM Forms-Zielaktion
3. Übermittlungsendpunktpfad angeben
4. Formular auf der Edge Delivery-Site veröffentlichen

+++
<!--
+++ Form Embedding

Embed forms created in one location into different web pages or sites.

### Use Cases

- Reuse standard forms across multiple landing pages
- Include specialized forms in Document-Authored content
- Maintain single form across multiple EDS projects

### CORS Configuration

Configure Cross-Origin Resource Sharing on the form source:

1. **Add CORS Headers** to form source responses:
   - `Access-Control-Allow-Origin: https://your-host-domain.com`
   - `Access-Control-Allow-Methods: GET, OPTIONS`  
   - `Access-Control-Allow-Headers: Content-Type`

2. **Example Configuration**:

        # Configuration for site hosting the form
        headers:
          - path: /forms/**
            custom:
              Access-Control-Allow-Origin: https://host-domain.com
              Access-Control-Allow-Methods: GET, OPTIONS

### Embedding Steps

1. **Create and Publish Form**
   - Build form using Document Authoring or Universal Editor
   - Configure submission method (FSS or AEM Publish)
   - Publish to standalone URL

2. **Configure CORS**
   - Set up CORS headers on form source site
   - Allow host page domain to fetch form

3. **Embed in Host Page**
   - Add form embedding block to host page
   - Point block to published form URL
   - Publish host page

![Embedded Form Architecture](/help/forms/assets/eds-embedded-form.png)

+++-->

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
