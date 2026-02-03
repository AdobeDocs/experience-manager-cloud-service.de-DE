---
title: Aufrufen einer zugehörigen Benutzeroberfläche in der Veröffentlichungsinstanz
description: Erfahren Sie, wie Sie die AEM Forms Associate-Benutzeroberfläche in Veröffentlichungsinstanzen integrieren und aufrufen können, damit kundenorientierte Fachleute personalisierte interaktive Kommunikationen in Echtzeit generieren können.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
hidefromtoc: true
source-git-commit: 6b90e8f2d26d6bfd22fbd94af0d6c68466c69bbb
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 3%

---


# Erzeugen von personalisierter Kommunikation mit der Associate-Benutzeroberfläche

<span> Die Funktion für interaktive Kommunikation ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie eine E-Mail von Ihrer Geschäftsadresse an `aem-forms-ea@adobe.com`, um Zugriff anzufordern.</span>

Die Associate-Benutzeroberfläche kann direkt auf Veröffentlichungsinstanzen aufgerufen werden, sodass kundenorientierte Fachleute wie Außendienstmitarbeiter und Service-Agenten während der Kundeninteraktionen in Echtzeit personalisierte Kommunikation generieren können.

Die nachstehende Tabelle zeigt die verschiedenen realen Szenarien, in denen die Associate-Benutzeroberfläche zum Senden personalisierter Nachrichten an Kunden verwendet werden kann:

| Branche | Nutzungsszenario |
|----------|----------|
| **Finanzdienstleistungen** | Generieren von Echtzeit-Kreditbestätigungsschreiben, Kontoauszügen und Risikoprofilzusammenfassungen während Kundensitzungen |
| **Versicherung** | Sofortige Zusammenfassungen der Versicherungsnachweise und der Schadensfallposition an den Serviceschaltern erstellen |
| **Gesundheitswesen** | Erstellen von Zusammenfassungen des Patientenbehandlungsplans mit berechneten Unternehmensbeträgen und Plänen |
| **Regierung** | Erstellen von Polizeiprüfungsberichten, Belegen des Bürgerdienstes und Zusammenfassungen der Fallaktualisierung vor Ort |

## Voraussetzungen

Bevor Sie die Benutzeroberfläche „Verknüpfen“ mit Ihrer Anwendung integrieren, stellen Sie sicher, dass Sie über Folgendes verfügen:

- AEM Forms Cloud Service-Veröffentlichungsinstanz
- In AEM erstellte und veröffentlichte interaktive Kommunikation
- Browser mit aktivierter Popup-Unterstützung
- Benutzer verknüpfen müssen Teil der Gruppe **forms-Associates** sein
- Authentifizierung konfiguriert - [SAML 2.0](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/authentication/saml-2-0)

>[!NOTE]
>
> Für die Benutzeroberfläche von Associate sind zusätzliche SAML-Konfigurationen erforderlich, die über die Standardeinrichtung hinausgehen, die im Artikel [SAML 2.0-Authentifizierung](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/authentication/saml-2-0) erläutert wird. Weitere Informationen finden Sie [ Abschnitt „Zusätzliche SAML-Konfigurationen für ](#additional-saml-configurations-for-associate-ui)-Benutzeroberfläche“.

### Zusätzliche SAML-Konfigurationen für die Associate-Benutzeroberfläche

Beim Konfigurieren der SAML 2.0-Authentifizierung für die Associate-Benutzeroberfläche müssen Sie die folgenden spezifischen Einstellungen in Ihren OSGi-Konfigurationsdateien anwenden.

#### SAML-Authentifizierungshandler

Erstellen Sie die Datei `com.adobe.granite.auth.saml.SamlAuthenticationHandler~saml.cfg.json` in `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish`:

```json
  {
    "path": ["/libs/fd/associate"],
    "serviceProviderEntityId": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com",
    "assertionConsumerServiceURL": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/saml_login",
    "idpUrl": "https://login.microsoftonline.com/{azure-tenant-id}/saml2",
    "idpCertAlias": "{your-certificate-alias}",
    "idpIdentifier": "https://sts.windows.net/{azure-tenant-id}/",
    "userIDAttribute": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
    "createUser": true,
    "userIntermediatePath": "saml",
    "synchronizeAttributes": [
      "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname=profile/givenName",
      "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname=profile/familyName",
      "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress=profile/email"
      ],
      "addGroupMemberships": true,
      "defaultGroups": ["forms-associates"],
      "defaultRedirectUrl": "/libs/fd/associate/ui.html",
      "idpHttpRedirect": false,
      "service.ranking": 5002
  }
```

| Eigenschaft | Beschreibung |
|----------|-------------|
| `path` | Muss für die Associate-Benutzeroberfläche auf `/libs/fd/associate` gesetzt werden |
| `defaultGroups` | Auf `forms-associates` setzen, um der erforderlichen Gruppe automatisch Benutzer zuzuweisen |
| `defaultRedirectUrl` | Leitet authentifizierte Benutzer zur Benutzeroberfläche von „Associate“ weiter |
| `idpHttpRedirect` | Muss für SP-initiierten Fluss `false` werden |
| `idpCertAlias` | Muss mit dem Zertifikatalias in Trust Store genau übereinstimmen (Groß-/Kleinschreibung beachten) |

#### Sling Authenticator

Aktualisieren Sie die Datei `org.apache.sling.engine.impl.auth.SlingAuthenticator~saml.cfg.json` in `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish`:

```json
{
  "sling.auth.requirements": ["+/libs/fd/associate/ui.html"],
  "sling.auth.anonymous": false
}
```

#### Dispatcher-Filter

Falls noch nicht vorhanden, fügen Sie Ihrer `dispatcher/src/conf.dispatcher.d/filters/filters.any`-Datei die folgenden Regeln hinzu:

```json
  # Allow Interactive Communications APIs and Associate UI
  /XXXX { /type "allow" /method '(GET|OPTIONS)' /url "/adobe/communications" }
  /XXXX { /type "allow" /method '(GET|POST|OPTIONS)' /url "/adobe/communications/*" }
  /XXXX { /type "allow" /method "GET" /url "/content/dam/fd:fonts/*" }
  /XXXX { /type "allow" /method '(GET|OPTIONS)' /url "/libs/fd/associate/*" }
```

>[!NOTE]
>
> Ersetzen Sie `XXXX` durch die entsprechende numerische Reihenfolge, die in der vorhandenen `filters.any`-Datei verwendet wird.

## Aufrufen der Associate-Benutzeroberfläche in der Veröffentlichungsinstanz

Um die Benutzeroberfläche „Verknüpfen“ von Ihrem Programm aus aufzurufen, konfigurieren Sie die URL der Veröffentlichungsinstanz, bereiten Sie die Daten-Payload vor und verwenden Sie die Integrationsfunktion, um die Benutzeroberfläche „Verknüpfen“ in einem neuen Browser-Fenster zu starten.

### Schritt 1: Konfigurieren der URL der Veröffentlichungsinstanz

Der Zugriff auf die Benutzeroberfläche von Associate erfolgt über einen bestimmten Endpunkt in Ihrer AEM Forms Cloud Service-Veröffentlichungsinstanz:

```javascript
const AEM_URL = 'https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/ui.html';
```

Ersetzen Sie `{program-id}` und `{env-id}` durch Ihre tatsächlichen Umgebungswerte.

### Schritt 2: Vorbereiten der Daten-Payload

Strukturieren Sie Ihre Daten-Payload wie folgt:

```javascript
const data = {
  id: "your-ic-id",              // Required: Interactive Communication ID
  prefill: {                      // Optional: Data to prefill the IC
    serviceName: "YourService",
    serviceParams: { key: "value" }
  },
  options: {}                     // Optional: Additional configuration options
};
```

**Payload-Komponenten:**

| Komponente | Erforderlich | Beschreibung |
|-----------|----------|-------------|
| `id` | Ja | Die Kennung der zu ladenden interaktiven Kommunikation (IC) |
| `prefill` | Nein | Enthält die Service-Konfiguration für das Vorbefüllen von Daten. |
| `prefill.serviceName` | Nein | Name des Formulardatenmodell-Service, der zum Vorbefüllen von Daten aufgerufen wird |
| `prefill.serviceParams` | Nein | Schlüssel-Wert-Paare, die an den Vorbefüllungs-Service übergeben werden |
| `options` | Nein | Zusätzliche Eigenschaften, die für die PDF-Darstellung unterstützt werden - locale, includeAttachments, embedFonts, makeAccessible |

### Schritt 3: Implementieren der Integrationsfunktion

Erstellen Sie eine JavaScript-Funktion, um die Associate-Benutzeroberfläche zu starten und die Nachrichtenkommunikation zu verarbeiten:

```javascript
function launchAssociateUI(icId, prefillService, prefillParams, options) {
  if (!icId) {
    console.error('IC ID required');
    return;
  }
   
  const data = {
    id: icId,
    prefill: {
      serviceName: prefillService || '',
      serviceParams: prefillParams || {}
    },
    options: options || {}
  };
   
  const AEM_URL = 'https://your-aem.adobeaemcloud.com/libs/fd/associate/ui.html';
  const win = window.open(AEM_URL, '_blank');
   
  if (!win) {
    alert('Please enable pop-ups for this site');
    return;
  }
   
  const readyHandler = (event) => {
    if (event.data && event.data.type === 'READY' && event.data.source === 'APP') {
      win.postMessage({ type: 'INIT', source: 'PORTAL', data: data }, '*');
      window.removeEventListener('message', readyHandler);
    }
  };
   
  window.addEventListener('message', readyHandler);
   
  // Fallback timeout in case READY message is missed
  setTimeout(() => {
    if (win && !win.closed) {
      win.postMessage({ type: 'INIT', source: 'PORTAL', data: data }, '*');
      window.removeEventListener('message', readyHandler);
    }
  }, 1000);
}
```

### Schritt 4: Funktion aufrufen

Rufen Sie die -Funktion mit entsprechenden Parametern auf:

```javascript
// Basic invocation with IC ID only
launchAssociateUI('12345', '', {}, {});

// With prefill service
launchAssociateUI('12345', 'FdmTestData', 
  { customerId: '101'}, {});

// With all parameters
launchAssociateUI('12345', 'FdmTestData', 
  { policyNumber: 'POL-123' }, 
  { locale: 'en', acrobatVersion: 'Acrobat_11' });
```

## Testen der Integration mit einer HTML-Beispielseite

Um zu sehen, wie die Benutzeroberfläche „Verknüpfen“ im Frontend angezeigt wird, und Ihre Integration zu testen, hier ein einfaches HTML-Beispiel. Auf dieser Beispielseite können Sie die IC-ID eingeben, Vorbefüllungs-Service-Parameter konfigurieren, PDF-Optionen festlegen und die Benutzeroberfläche „Verknüpfen“ auf Ihrer Veröffentlichungsinstanz starten.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Associate UI Integration</title>
  <style>
    body { 
      font-family: sans-serif; 
      max-width: 600px; 
      margin: 50px auto; 
      padding: 20px; 
    }
    .form-group { 
      margin: 20px 0; 
    }
    label { 
      display: block; 
      margin-bottom: 5px; 
      font-weight: bold; 
    }
    input, textarea { 
      width: 100%; 
      padding: 8px; 
      border: 1px solid #ccc; 
      border-radius: 4px; 
      box-sizing: border-box;
    }
    textarea { 
      height: 80px; 
      font-family: monospace; 
    }
    button { 
      padding: 10px 20px; 
      margin: 5px; 
      cursor: pointer; 
      border-radius: 4px;
    }
    .btn-primary { 
      background: #007bff; 
      color: white; 
      border: none; 
    }
    .btn-primary:hover {
      background: #0056b3;
    }
    .error { 
      color: red; 
      font-size: 12px; 
      display: none; 
    }
  </style>
</head>
<body>
  <h1>Launch Associate UI</h1>
  
  <form id="form">
    <div class="form-group">
      <label>IC ID *</label>
      <input type="text" id="icId" placeholder="Enter Interactive Communication ID" required>
    </div>
    
    <div class="form-group">
      <label>Prefill Service</label>
      <input type="text" id="serviceName" placeholder="e.g., CustomerDataService">
    </div>
    
    <div class="form-group">
      <label>Service Parameters (JSON)</label>
      <textarea id="serviceParams" placeholder='{"customerId": "12345"}'>{}</textarea>
      <span id="paramsError" class="error">Invalid JSON format</span>
    </div>
    
    <div class="form-group">
      <label>Options (JSON)</label>
      <textarea id="options" placeholder='{"mode": "edit", "locale": "en_US"}'>{}</textarea>
      <span id="optionsError" class="error">Invalid JSON format</span>
    </div>
    
    <button type="button" onclick="reset()">Reset</button>
    <button type="button" class="btn-primary" onclick="launch()">Launch Associate UI</button>
  </form>

  <script>
    // Replace with your AEM Publish instance URL
    const AEM_URL = 'https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/ui.html';
    
    function validateJSON(str, errorId) {
      const err = document.getElementById(errorId);
      try {
        const obj = JSON.parse(str || '{}');
        err.style.display = 'none';
        return obj;
      } catch (e) {
        err.style.display = 'block';
        return null;
      }
    }
    
    function launch() {
      const icId = document.getElementById('icId').value.trim();
      if (!icId) { 
        alert('IC ID is required'); 
        return; 
      }
      
      const params = validateJSON(document.getElementById('serviceParams').value, 'paramsError');
      const opts = validateJSON(document.getElementById('options').value, 'optionsError');
      
      if (!params || !opts) { 
        alert('Please fix JSON errors before launching'); 
        return; 
      }
      
      const data = {
        id: icId,
        prefill: {
          serviceName: document.getElementById('serviceName').value.trim(),
          serviceParams: params
        },
        options: opts
      };
      
      const win = window.open(AEM_URL, '_blank');
      if (!win) { 
        alert('Pop-up blocked. Please enable pop-ups for this site.'); 
        return; 
      }
      
      const handler = (e) => {
        if (e.data && e.data.type === 'READY' && e.data.source === 'APP') {
          win.postMessage({ type: 'INIT', source: 'PORTAL', data }, '*');
          window.removeEventListener('message', handler);
        }
      };
      
      window.addEventListener('message', handler);
      
      // Fallback timeout in case READY message is missed
      setTimeout(() => {
        if (win && !win.closed) {
          win.postMessage({ type: 'INIT', source: 'PORTAL', data }, '*');
          window.removeEventListener('message', handler);
        }
      }, 1000);
    }
    
    function reset() {
      document.getElementById('form').reset();
      document.getElementById('serviceParams').value = '{}';
      document.getElementById('options').value = '{}';
      document.getElementById('paramsError').style.display = 'none';
      document.getElementById('optionsError').style.display = 'none';
    }
  </script>
</body>
</html>
```

### Funktionsweise des Beispiels

1. **IC ID Field**: Geben Sie die Kennung der interaktiven Kommunikation ein (erforderlich)
2. **Vorbefüllungs-**: Geben Sie den Namen des Formulardatenmodell-Dienstes zum Vorbefüllen von Daten an
3. **Service-Parameter**: Geben Sie ein JSON-Objekt mit Parametern ein, die an den Vorbefüllungs-Service übergeben werden sollen
4. **Optionen**: Geben Sie Konfigurationsoptionen für PDF ein, z. B. locale, includeAttachments, embedFonts, makeAccessible
5. **Launch-Schaltfläche**: Öffnet die Associate-Benutzeroberfläche in einem neuen Fenster und sendet die Initialisierungsdaten

## Beispiele für Daten-Payloads

### Minimale Payload (nur IC)

Verwenden Sie diese Option, wenn keine Daten zum Vorbefüllen erforderlich sind:

```json
{
  "id": "12345",
  "prefill": { 
    "serviceName": "", 
    "serviceParams": {} 
  },
  "options": {}
}
```

### mit Vorbefüllungsdaten

Verwenden Sie diese Option, um die ID dynamisch mit Kundendaten zu füllen:

```json
{
  "id": "12345",
  "prefill": {
    "serviceName": "FdmTestData",
    "serviceParams": {
      "customerId": "101",
      "accountNumber": "ACC-98765"
    }
  },
  "options": {}
}
```

### Mit Konfigurationsoptionen

Hier können Sie zusätzliche Rendering-Optionen angeben:

```json
{
  "id": "12345ß",
  "prefill": {
    "serviceName": "FdmTestData",
    "serviceParams": { 
      "policyNumber": "POL-123" 
    }
  },
  "options": { 
      locale: "en_US",
      includeAttachments: "true",
      webOptimized: "false",
      embedFonts: "false",
      makeAccessible: "false"
  }
}
```

## Fehlerbehebung

### Popup blockiert

**Problem**: Das Fenster „Benutzeroberfläche zuordnen“ wird nicht geöffnet.

**Lösung**:
- Aktivieren von Popups für Ihre Domain in den Browser-Einstellungen
- Stellen Sie sicher, dass `window.open()` über eine Benutzeraktion aufgerufen wird (z. B. durch Klicken auf eine Schaltfläche)
- Testen mit verschiedenen Browsern, um das Blockierverhalten zu ermitteln

### Daten werden nicht geladen

**Problem**: Die interaktive Kommunikation wird geöffnet, aber es werden keine Daten angezeigt.

**Lösung**:
- Überprüfen Sie, ob die IC-ID korrekt ist und die IC veröffentlicht wurde
- Browser-Konsole auf JavaScript-Fehler prüfen
- Stellen Sie sicher, dass die `postMessage` genau mit der Spezifikation übereinstimmt
- Überprüfen, ob der Formulardatenmodell-Service richtig konfiguriert ist

### Authentifizierungsfehler

**Problem**: Der Benutzer erhält einen Authentifizierungsfehler, wenn die Benutzeroberfläche von Associate geöffnet wird.

**Lösung**:
- Konfigurieren der SAML 2.0-Authentifizierung auf der Veröffentlichungsinstanz
- Überprüfen Sie, ob der Benutzer zur Gruppe **forms-Associates** gehört
- Einstellungen für Sitzungs-Timeouts überprüfen

### CORS-Fehler

**Problem**: Fehler bei der herkunftsübergreifenden Ressourcennutzung in der Konsole.

**Lösung**:
- Für die Entwicklung: Verwenden von `'*'` als Zielursprung in `postMessage`
- Für die Produktion: Geben Sie die genaue Ursprungs-URL Ihrer Anwendung an
- Stellen Sie sicher, dass die CORS-Einstellungen der Veröffentlichungsinstanz Ihre Anwendungs-Domain zulassen.

## Best Practices

Befolgen Sie bei der Implementierung der Integration der Associate-Benutzeroberfläche die folgenden Best Practices:

1. **Validierung**: Überprüfen Sie vor dem Senden immer die IC-ID und die JSON-Payload
2. **Fehlerbehandlung**: Implementieren einer ordnungsgemäßen Fehlerbehandlung für `window.open()` Fehler
3. **Benutzererlebnis**: Zeigt eine Ladeanzeige an, während die Benutzeroberfläche „Verknüpfen“ initialisiert wird
4. **Speicherverwaltung**: Entfernen von Ereignis-Listenern nach der Initialisierung, um Speicherlecks zu vermeiden
5. **Testen**: Testen Sie die Integration mit aktivierten Popup-Blockern, um eine elegante Handhabung zu gewährleisten
6. **Benutzerberechtigungen**: Überprüfen Sie, ob Benutzer angemessenen Zugriff auf die Gruppe „forms-Associates“ haben

## Siehe auch

- [Zuordnen der Benutzeroberfläche im Editor für interaktive Kommunikation](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [Interaktive Kommunikation in der Cloud](/help/forms/early-access-ea-features.md#interactive-communications-on-cloud)
- [Funktionen für frühzeitigen Zugriff](/help/forms/early-access-ea-features.md)