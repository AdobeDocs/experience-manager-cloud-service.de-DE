---
title: Integrieren der zugehörigen Benutzeroberfläche für interaktive Kommunikationen zur Laufzeit
description: Erfahren Sie, wie Sie die AEM Forms Associate-Benutzeroberfläche in Ihr Programm integrieren, damit kundenorientierte Fachleute personalisierte interaktive Kommunikationen in Echtzeit auf Veröffentlichungsinstanzen generieren können.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
hidefromtoc: true
source-git-commit: b76f6dfe2462cec187d549234e9050f8ca9a8cdf
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 2%

---


# Integrieren der Associate-Benutzeroberfläche in Ihr Programm

<span> Die Funktion für interaktive Kommunikation ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie eine E-Mail von Ihrer Geschäftsadresse an `aem-forms-ea@adobe.com`, um Zugriff anzufordern.</span>

In diesem Artikel wird erläutert, wie Sie die Benutzeroberfläche „Verknüpfen“ in Ihr Programm integrieren und es kundenorientierten Fachleuten wie Außendienstmitarbeitern und Service-Agenten ermöglichen, in Echtzeit personalisierte interaktive Kommunikation in Veröffentlichungsinstanzen zu generieren.

## Voraussetzungen

Bevor Sie die Benutzeroberfläche „Verknüpfen“ mit Ihrer Anwendung integrieren, stellen Sie sicher, dass Sie über Folgendes verfügen:

- Interaktive Kommunikation erstellt und veröffentlicht
- Browser mit aktivierter Popup-Unterstützung
- Verknüpfen [Benutzer müssen Teil der Gruppe „forms-Associates“ sein](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/administrator-help/setup-organize-users/creating-configuring-roles#assign-a-role-to-users-and-groups)
- Authentifizierung konfiguriert mit einem [von AEM unterstützten Authentifizierungsmechanismus](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/authentication/authentication) (z. B. SAML 2.0, OAuth oder benutzerdefinierte Authentifizierungs-Handler)

>[!NOTE]
>
>- Dieser Artikel zeigt die Authentifizierungskonfiguration mithilfe von SAML 2.0 mit [Microsoft Entra ID (Azure AD) als Identitätsanbieter](https://learn.microsoft.com/en-us/power-pages/security/authentication/openid-settings).
>- Für die Benutzeroberfläche von Associate sind zusätzliche SAML-Konfigurationen erforderlich, die über die Standardeinrichtung hinausgehen, die im Artikel [SAML 2.0-Authentifizierung](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/authentication/saml-2-0) erläutert wird. Weitere Informationen finden Sie [&#x200B; Abschnitt „Zusätzliche SAML-Konfigurationen für &#x200B;](#additional-saml-configurations-for-associate-ui)-Benutzeroberfläche“.

### Zusätzliche SAML-Konfigurationen für die Associate-Benutzeroberfläche

Beim Konfigurieren der SAML 2.0-Authentifizierung für die Associate-Benutzeroberfläche müssen Sie die folgenden spezifischen Einstellungen in Ihren OSGi-Konfigurationsdateien anwenden.

#### SAML-Authentifizierungshandler

Der SAML-Authentifizierungs-Handler ist eine OSGi-Werkskonfiguration, die mehrere SAML-Konfigurationen für verschiedene Ressourcenbäume zulässt. Dies ermöglicht AEM-Bereitstellungen an mehreren Standorten und das Hinzufügen von zugehörigen Benutzeroberflächenressourcen zu Ihrem bestehenden SAML-Setup.

Erstellen Sie die Datei `com.adobe.granite.auth.saml.SamlAuthenticationHandler~saml.cfg.json` in `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish`:

```json
  {
    "path": ["/libs/fd/associate"],
    "serviceProviderEntityId": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com",
    "assertionConsumerServiceURL": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/saml_login"
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

Der Sling Authenticator erzwingt die Authentifizierung für den Zugriff auf Ressourcen der zugehörigen Benutzeroberfläche in der Veröffentlichungsinstanz.

Aktualisieren Sie die Datei `org.apache.sling.engine.impl.auth.SlingAuthenticator~saml.cfg.json` in `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish`:

```json
{
  "sling.auth.requirements": ["+/libs/fd/associate/ui.html"],
  "sling.auth.anonymous": false
}
```

#### Dispatcher-Filter

Fügen Sie die folgenden Regeln hinzu, um sicherzustellen, dass APIs für interaktive Kommunikation und die Benutzeroberfläche „Verknüpfen“ in der Veröffentlichungsinstanz korrekt funktionieren.

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

Dieser Abschnitt führt Sie durch den Start der Benutzeroberfläche „Associate“ von Ihrem eigenen Programm aus. Führen Sie diese Schritte aus, um schnell zu beginnen, beginnend mit einer einsatzbereiten Beispiel-HTML-Seite, und konfigurieren Sie sie dann für Ihre Umgebung.

### Schritt 1: Mit der HTML-Beispielseite beginnen

Um schnell zu testen und zu verstehen, wie die Integration der Associate-Benutzeroberfläche funktioniert, verwenden Sie die folgende HTML-Beispielseite. Kopieren Sie diesen Code in eine HTML-Datei und öffnen Sie sie in Ihrem Browser.

Dieses Beispiel bietet eine einfache Formularoberfläche, in der Sie Details zur interaktiven Kommunikation eingeben und die Benutzeroberfläche „Zuordnen“ mit einem Klick starten können.

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

### Schritt 2: Konfigurieren der URL der Veröffentlichungsinstanz

Bevor Sie die Benutzeroberfläche „Associate“ starten können, müssen Sie das Beispiel auf Ihre AEM Forms Cloud Service-Veröffentlichungsinstanz verweisen.

Suchen Sie im obigen HTML-Beispiel die folgende Zeile im Abschnitt `<script>` :

```javascript
const AEM_URL = 'https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/ui.html';
```

Ersetzen Sie die Platzhalterwerte durch Ihre tatsächlichen Umgebungsdetails:
- `{program-id}`: Ihre AEM Cloud Service-Programm-ID
- `{env-id}`: Ihre Umgebungs-ID

Wenn beispielsweise Ihre Programm-ID `12345` und die Umgebungs-ID `67890` ist, wird die URL zu:

```javascript
const AEM_URL = 'https://publish-p12345`-e67890.adobeaemcloud.com/libs/fd/associate/ui.html';
```

>[!NOTE]
>
> Aus Sicherheitsgründen werden Parameter wie die ID der interaktiven Kommunikation, der Vorbefüllungs-Service und Service-Parameter nicht über die URL weitergeleitet. Stattdessen werden diese Parameter sicher mithilfe der `postMessage`-API von JavaScript übergeben.

### Schritt 3: JavaScript-Integrationsfunktion verstehen

Im Beispiel verwendet HTML die folgende JavaScript-Funktion, um die Benutzeroberfläche „Associate“ zu starten. Diese Funktion validiert die IC-ID, erstellt die Daten-Payload, öffnet die Benutzeroberfläche „Associate“ in einem neuen Browser-Fenster und sendet die Daten über die `postMessage`-API des Browsers.

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

Die Funktion akzeptiert vier Parameter: die ID (erforderlich), den Namen des Vorbefüllungs-Services, die Parameter des Vorbefüllungs-Services und zusätzliche Optionen. Diese Parameter werden wie unten beschrieben in die Daten-Payload strukturiert.

### Schritt 4: Grundlegendes zur Struktur der Daten-Payload

**Payload-Format:**

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
| `prefill` | Optional | Enthält die Dienstkonfiguration zum Vorbefüllen von Daten |
| `prefill.serviceName` | Optional | Name des Formulardatenmodell-Service, der zum Vorbefüllen von Daten aufgerufen wird |
| `prefill.serviceParams` | Optional | Schlüssel-Wert-Paare, die an den Vorbefüllungs-Service übergeben werden |
| `options` | Optional | Zusätzliche Eigenschaften, die für die PDF-Darstellung unterstützt werden - locale, includeAttachments, embedFonts, makeAccessible |

#### Beispiele für Daten-Payloads

**Minimale Payload (nur IC-ID)**

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

**mit Vorbefüllungsdaten**

Verwenden Sie diese Option, um die ID dynamisch mit Kundendaten zu füllen:

```json
{
  "id": "12345",
  "prefill": {
    "serviceName": "IC_FDM",
    "serviceParams": {
      "customerId": "101",
      "accountNumber": "ACC-98765"
    }
  },
  "options": {}
}
```

**mit PDF-Rendering-Optionen**

Hier können Sie zusätzliche Rendering-Optionen angeben:

```json
{
  "id": "12345",
  "prefill": {
    "serviceName": "IC_FDM",
    "serviceParams": {
      "customerId": "101",
      "accountNumber": "ACC-98765"
    }
  },
  "options": { 
      "locale": "en_US",
      "includeAttachments": "true",
      "webOptimized": "false",
      "embedFonts": "false",
      "makeAccessible": "false"
  }
}
```

### Schritt 5: IC-ID eingeben und Benutzeroberfläche des zugeordneten Benutzers starten

Jetzt können Sie die Benutzeroberfläche von Associate über die HTML-Beispielseite starten:

1. **IC-ID eingeben**: Geben Sie im Feld **IC-ID** die Kennung Ihrer veröffentlichten interaktiven Kommunikation ein. Dies ist das einzige erforderliche Feld.

2. **Vorbefüllungs-Service konfigurieren** (optional): Wenn Sie den IC mit dynamischen Daten vorbefüllen möchten, geben Sie den Namen des Formulardatenmodell-Service in das Feld **Vorbefüllungs-Service** ein. Verwenden Sie beispielsweise `FdmTestData` für Beispieldaten oder `IC-FDM` für Testdaten.

3. **Dienstparameter hinzufügen** (optional): Geben Sie im Feld **Dienstparameter (JSON)** ein JSON-Objekt mit den Parametern ein, die für den Vorbefüllungs-Service erforderlich sind. Zum Beispiel:

   ```json
   {"customerId": "101", "accountNumber": "ACC-98765"}
   ```

4. **PDF-Optionen festlegen** (optional): Konfigurieren Sie im Feld **Optionen (JSON)** Rendering-Optionen wie Gebietsschema, Anlagen oder Einstellungen für die Barrierefreiheit.

5. **Klicken auf Benutzeroberfläche von Launch Associate**: Klicken Sie auf die Schaltfläche **Benutzeroberfläche von Launch Associate**. Ein neues Browser-Fenster mit der Benutzeroberfläche „Verknüpfen“ wird geöffnet, die mit der interaktiven Kommunikation vorgeladen wird.

>[!NOTE]
>
> Wenn sich das Fenster nicht öffnet, überprüfen Sie, ob Ihr Browser Popups für diese Site zulässt.

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

<!--## Best Practices

When implementing the Associate UI integration, follow these best practices:

1. **Validation**: Always validate the IC ID and JSON payload before sending
2. **Error Handling**: Implement proper error handling for `window.open()` failures
3. **User Experience**: Display a loading indicator while the Associate UI initializes
4. **Memory Management**: Remove event listeners after initialization to prevent memory leaks
5. **Testing**: Test the integration with popup blockers enabled to ensure graceful handling
6. **User Permissions**: Verify users have appropriate access to the forms-associates group-->

## Siehe auch

- [Zuordnen der Benutzeroberfläche im Editor für interaktive Kommunikation](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [Interaktive Kommunikation in der Cloud](/help/forms/early-access-ea-features.md#interactive-communications-on-cloud)
- [Funktionen für frühzeitigen Zugriff](/help/forms/early-access-ea-features.md)