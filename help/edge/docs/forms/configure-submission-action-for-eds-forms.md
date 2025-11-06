---
title: Konfigurieren von Übermittlungsaktionen für AEM Forms mit Edge Delivery Services
description: Erfahren Sie, wie Sie mithilfe von Edge Delivery Services Übermittlungsaktionen in AEM Forms konfigurieren können. Wählen Sie zwischen dem Formularübermittlungsdienst und der Übermittlungsaktion in AEM Publish, um Formulardaten sicher und effizient zu verarbeiten.
feature: Edge Delivery Services
role: Admin, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 100%

---

# Konfigurieren von Übermittlungsaktionen für AEM Forms

Konfigurieren Sie die Handhabung von Formularübermittlungen, um Daten mithilfe von AEM Forms und Edge Delivery Services an Tabellen, E-Mail-Adressen oder Backend-Systeme zu leiten.

## Leitfaden für schnelle Entscheidungen

Wählen Sie Ihre Übermittlungsmethode:

| Methode | Am besten geeignet für | Setup-Komplexität | Anwendungsfälle |
|--------|----------|------------------|-----------|
| **Formularübermittlungsdienst** | Einfache Datenerfassung | Niedrig | Kontaktformulare, Umfragen, grundlegende Datenerfassung |
| **AEM Publish-Übermittlung** | Komplexe Workflows | Hoch | Unternehmensintegrationen, benutzerdefinierte Verarbeitung, Workflows |

## Voraussetzungen

Bevor Sie Übermittlungsaktionen konfigurieren, müssen Sie:

- AEM Forms as a Cloud Service-Instanz
- Edge Delivery Services-Projekt konfiguriert
- Formular, eingerichtet mithilfe der Dokumenterstellung oder des universellen Editors
- Erforderliche Berechtigungen für Ziele (Tabellen, E-Mail-Systeme oder AEM)

+++ Methode 1: Formularübermittlungsdienst

Der Formularübermittlungsdienst ist ein von Adobe gehosteter Endpunkt, der sich ideal für einfache Datenerfassungsszenarien eignet.

### Unterstützte Ziele

- **Tabellen**: Google Sheets, Microsoft Excel (OneDrive/SharePoint)
- **E-Mail**: Senden von Formulardaten an bestimmte E-Mail-Adressen

### Konfigurationsschritte

1. **Einrichten des Zielzugriffs**
   - Für Tabellen: Erteilen Sie Bearbeitungsberechtigungen für `forms@adobe.com` in der Zieltabelle.
   - Für E-Mail: Überprüfen Sie, ob E-Mail-Adressen von Empfängerinnen und Empfängern erreichbar sind.

2. **Konfigurieren der Formularübermittlung**
   - Öffnen Sie Ihr Formular in der Authoring-Umgebung.
   - Legen Sie die Übermittlungsaktion auf „Formularübermittlungsdienst“ fest.
   - Geben Sie die URL der Zieltabelle oder die E-Mail-Adressen an.
   - Speichern und veröffentlichen Sie das Formular.

3. **Testübermittlung**
   - Senden Sie Testdaten über das Formular.
   - Überprüfen Sie, ob die Daten im Ziel angezeigt werden.
   - Überprüfen Sie Fehlerprotokolle, wenn die Übermittlung fehlschlägt.

### Wichtige Hinweise

- Das Dienstkonto `forms@adobe.com` erfordert Bearbeitungszugriff auf Zieltabellen
- E-Mail-Benachrichtigungen werden sofort nach der Formularübermittlung gesendet
- Die Datenvalidierung erfolgt auf der Dienstebene

![Ablauf des Formularübermittlungsdiensts](/help/forms/assets/eds-fss.png)

+++

+++ Methode 2: Übermittlung per AEM Publish

Senden Sie Formulardaten zur komplexen Verarbeitung direkt an Ihre AEM as a Cloud Service-Veröffentlichungsinstanz.

### Verwendung von AEM Publish

- Benutzerdefinierte AEM-Workflows nach der Übermittlung erforderlich
- Integration des Formulardatenmodells (FDM) in Datenbanken
- Integration von Drittanbieterdiensten (Marketo, Power Automate, Workfront Fusion)
- Azure Blob Storage- oder SharePoint-Dokumentbibliotheken
- Komplexe Server-seitige Validierung oder Verarbeitungslogik

### Verfügbare Übermittlungsaktionen

- [An REST-Endpunkt senden](/help/forms/configure-submit-action-restpoint.md)
- [Per E-Mail senden (mithilfe der E-Mail-Dienste von AEM)](/help/forms/configure-submit-action-send-email.md)
- [Mit Formulardatenmodell senden](/help/forms/configure-data-sources.md)
- [AEM-Workflow aufrufen](/help/forms/aem-forms-workflow-step-reference.md)
- [An SharePoint senden](/help/forms/configure-submit-action-sharepoint.md)
- [An OneDrive senden](/help/forms/configure-submit-action-onedrive.md)
- [An Azure Blob Storage senden](/help/forms/configure-submit-action-azure-blob-storage.md)
- [An Microsoft Power Automate senden](/help/forms/forms-microsoft-power-automate-integration.md)
- [An Adobe Workfront Fusion Senden](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
- [An Adobe Marketo Engage senden](/help/forms/submit-adaptive-form-to-marketo-engage.md)

![Ablauf von AEM Publish-Übermittlung](/help/forms/assets/eds-aem-publish.png)

### Konfigurationsanforderungen

#### &#x200B;1. Aktualisieren der URL der AEM-Instanz in Edge Delivery

Aktualisieren Sie die URL der AEM Cloud Service-Instanz in der `constant.js`-Datei im `form`-Block unter `submitBaseUrl`. Sie können die URL basierend auf Ihrer Umgebung konfigurieren:

**Für eine Cloud Service-Instanz**

```js
export const submitBaseUrl = '<aem-publish-instance-URL>';
```

**Für die lokale Entwicklung**

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

3. Stellen Sie die Konfiguration über Cloud Manager bereit

Weitere Informationen zur Konfiguration des OSGi-Referrer-Filters finden Sie im Handbuch zu [Referrer-Filtern](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter).

#### &#x200B;3. CORS-Probleme (Cross-Origin Resource Sharing)

Konfigurieren Sie CORS-Einstellungen in AEM, um Anfragen von Ihren spezifischen Edge Delivery-Site-Domains zuzulassen:

**Entwickler-Localhost**

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true
```

**Edge Delivery Sites: Einzelnes Hinzufügen jede Site-Domain**

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc--adobe\.aem\.live$)#" CORSTrusted=true
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc1--adobe\.aem\.live$)#" CORSTrusted=true
```

**Veraltete Franklin-Domains (falls noch in Verwendung)**

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

1. Erstellen Sie das Formular im universellen Editor.
2. Konfigurieren Sie die Übermittlungsaktion für die AEM Forms-Zielaktion.
3. Geben Sie den Pfad des Übermittlungsendpunkts an.
4. Veröffentlichen Sie das Formular auf der Edge Delivery-Site.

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

+++ Gängige Probleme

| Problem | Lösung |
|-------|----------|
| **Formularübermittlung schlägt fehl** | Prüfen Sie Konsolenfehler, überprüfen Sie die Endpunkt-URL und verifizieren Sie Berechtigungen |
| **Eingebettetes Formular wird nicht angezeigt** | Konfigurieren Sie CORS-Kopfzeilen an der Formularquelle; überprüfen Sie die Formular-URL |
| **403/401-Fehler bei AEM** | Aktualisieren Sie den Sling Referrer-Filter, überprüfen Sie die Authentifizierungseinstellungen |
| **Daten erreichen die Tabelle nicht** | Überprüfen Sie, ob `forms@adobe.com` Bearbeitungszugriff hat, und überprüfen Sie die URL der Tabelle |
| **CORS-Fehler** | Fügen Sie der Formularquelle die richtigen `Access-Control-Allow-Origin`-Kopfzeilen hinzu |

+++

## Konfigurationsbeispiele

+++ Dokumentenbasiertes Formular mit Tabellen-Übermittlung

1. Erstellen einer Formularstruktur in Google Docs/Sheets
2. Konfigurieren des Endpunkts für den Formularübermittlungsdienst
3. Erteilen von `forms@adobe.com`-Bearbeitungszugriff auf die Zieltabelle
4. Veröffentlichen des Dokuments auf der Edge Delivery-Site
5. Übermittlung von Testformularen und Datenfluss

+++

+++ Formular im universellen Editor mit AEM Workflow

1. Erstellen von Formular im universellen Editor
2. Konfigurieren der Übermittlungsaktion zum Aufrufen eines AEM-Workflows
3. Einrichten von Dispatcher und Referrer-Filter in AEM Publish
4. Konfigurieren von CDN-Routing-Regeln
5. Veröffentlichen des Formulars und Testen der Workflow-Ausführung

+++

## Best Practices

- **Nutzen Sie den Formularübermittlungsdienst** für einfache Datenerfassungsszenarien
- **Wählen Sie AEM Publish**, wenn komplexe Verarbeitungsvorgänge oder Integrationen erforderlich sind
- **Testen Sie gründlich** in der Staging-Umgebung vor der Produktionsbereitstellung
- **Überwachen Sie Übermittlungen** mithilfe von AEM-Protokollen und Konsolenfehlern
- **Implementieren Sie eine ordnungsgemäße Fehlerbehandlung** bei fehlgeschlagenen Übermittlungen
- **Validieren Sie Daten** sowohl auf Client- als auch auf Server-Ebene
- **Nutzen Sie HTTPS** für alle Formularübermittlungen und Datenübertragungen

## Verwandte Themen

- [Dokumentenbasiertes Authoring mit EDS Forms](/help/edge/docs/forms/tutorial.md)
- [Universeller Editor mit EDS Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
- [AEM Forms-Übermittlungsdienst](/help/forms/forms-submission-service.md)
- [Konfigurieren von Datenquellen](/help/forms/configure-data-sources.md)
- [Referenz für AEM Forms Workflow](/help/forms/aem-forms-workflow-step-reference.md)
