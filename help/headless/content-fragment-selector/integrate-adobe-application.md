---
title: Integrieren der Inhaltsfragmentauswahl in ein Adobe-Programm
description: Integrieren Sie den Inhaltsfragmentselektor in verschiedene Adobe-Programme.
role: Admin, User, Developer
source-git-commit: a16d9e9fa6483a89283c595372abcc437d1d962e
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 20%

---

# Integrieren des Inhaltsfragment-Selektors in das Adobe-Programm {#integrate-content-fragment-selector-with-adobe-application}

Der Inhaltsfragment-Selektor ermöglicht die Integration in verschiedene Adobe-Programme, damit diese nahtlos zusammenarbeiten können.

## Voraussetzungen {#prerequisites}

Verwenden Sie die folgenden Voraussetzungen, wenn Sie die Inhaltsfragmentauswahl in ein Adobe-Programm integrieren:

* [Voraussetzungen](/help/headless/content-fragment-selector/overview.md#prerequisites)
* imsOrg
* imsToken
* apikey

## Integrieren der Inhaltsfragmentauswahl in ein Adobe-Programm {#integrate-content-fragment-selector-with-an-adobe-application}

Das folgende Beispiel zeigt die Verwendung des Inhaltsfragment-Selektors, wenn ein Adobe-Programm unter Unified Shell ausgeführt wird oder wenn bereits ein `imsToken` für die Authentifizierung generiert wurde.

Fügen Sie das Inhaltsfragmentauswahl-Paket mit dem `script`-Tag in Ihren Code ein, wie im folgenden Beispiel gezeigt.

* Sobald das Skript geladen ist, kann die globale Variable `PureJSContentFragmentSelectors` verwendet werden.
* Definieren Sie den Inhaltsfragment-Selektor [Eigenschaften](/help/headless/content-fragment-selector/properties.md):

   * Die Eigenschaften `imsOrg` und `imsToken` sind beide für die Authentifizierung im Adobe-Programm erforderlich
   * Die `handleSelection`-Eigenschaft wird verwendet, um die ausgewählten Fragmente zu verarbeiten.

* Um den Inhaltsfragmentselektor zu rendern, rufen Sie die Funktion `renderFragmentSelector` auf.
* Der Inhaltsfragmentselektor wird im `<div>` Container-Element angezeigt.

Wenn Sie diese Schritte befolgen, können Sie den Inhaltsfragment-Selektor mit Ihrer Adobe-Anwendung verwenden.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>
<head>
    <title>Fragment Selector</title>
    <script src="https://experience.adobe.com/solutions/CQ-fragmentss-selectors/static-fragments/resources/fragments-selectors.js"></script>
    <script>
        // get the container element in which we want to render the FragmentSelector component
        const container = document.getElementById('fragment-selector-container');
        // imsOrg and imsToken are required for authentication in Adobe application
        const fragmentSelectorProps = {
            imsOrg: 'example-ims@AdobeOrg',
            imsToken: "example-imsToken",
            apiKey: "example-apiKey-associated-with-imsOrg",
            handleSelection: (fragmentss: SelectedFragmentType[]) => {},
        };
        // Call the `renderFragmentSelector` available in PureJSContentFragmentSelectors globals to render FragmenttSelector
        PureJSContentFragmentSelectors.renderFragmentSelector(container, fragmentSelectorProps);
    </script>
</head>

<body>
    <div id="fragment-selector-container" style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px;">
    </div>
</body>

</html>
```

### ImsAuthProps {#imsauthprops}

Die `ImsAuthProps`-Eigenschaften definieren die Authentifizierungsinformationen und den Fluss, mit dem der Inhaltsfragment-Selektor ein `imsToken` abruft. Durch Festlegen dieser Eigenschaften können Sie das Verhalten des Authentifizierungsflusses steuern und Listener für verschiedene Authentifizierungsereignisse registrieren.

Details zu Eigenschaften finden Sie unter [ImsAuthProps-Eigenschaften](/help/headless/content-fragment-selector/properties.md#imsauthprops-properties)

### ImsAuthService {#imsauthservice}

`ImsAuthService` Klasse verarbeitet den Authentifizierungsfluss für den Fragmentselektor. Sie ist für den Erhalt eines `imsToken` über den Adobe IMS-Authentifizierungsdienst verantwortlich. Die `imsToken` wird verwendet, um den Benutzer zu authentifizieren und den Zugriff auf das AEM as a Cloud Service-Repository zu autorisieren. `ImsAuthService` verwendet die `ImsAuthProps` Eigenschaften, um den Authentifizierungsfluss zu steuern und Listener für verschiedene Authentifizierungsereignisse zu registrieren. Sie können die Funktion `registerFragmentsSelectorsAuthService` verwenden, um die `ImsAuthService` beim Fragmentselektor zu registrieren. Die folgenden Funktionen sind in der Klasse `ImsAuthService` verfügbar. Wenn Sie jedoch die Funktion `registerFragmentsSelectorsAuthService` verwenden, müssen Sie diese Funktionen nicht direkt aufrufen.

Details zu Eigenschaften finden Sie unter [ImsAuthService-Eigenschaften](/help/headless/content-fragment-selector/properties.md#imsauthservice-properties)

### Validierung mit bereitgestelltem IMS-Token {#validation-with-provided-ims-token}

```javascript
<script>
    const apiToken="<valid IMS token>";
    function handleSelection(selection) {
    console.log("Selected fragment: ", selection);
    };
    function renderFragmentSelectorInline() {
    console.log("initializing Fragment Selector");
    const props = {
    "repositoryId": "delivery-p64502-e544757.adobeaemcloud.com",
    "apiKey": "ngdm_test_client",
    "imsOrg": "<IMS org>",
    "imsToken": apiToken,
    handleSelection,
    hideTreeNav: true
    }
    const container = document.getElementById('fragment-selector-container');
    PureJSContentFragmentSelectors.renderFragmentSelector(container, props);
    }
    $(document).ready(function() {
    renderFragmentSelectorInline();
    });
</script>
```

### Registrieren von Rückrufen des IMS-Dienstes {#register-callbacks-to-ims-service}

```java
// object `imsProps` to be defined as below 
let imsProps = {
    imsClientId: <IMS Client Id>,
        imsScope: "openid",
        redirectUrl: window.location.href,
        modalMode: true,
        adobeImsOptions: {
            modalSettings: {
            allowOrigin: window.location.origin,
},
        useLocalStorage: true,
},
onImsServiceInitialized: (service) => {
            console.log("onImsServiceInitialized", service);
},
onAccessTokenReceived: (token) => {
            console.log("onAccessTokenReceived", token);
},
onAccessTokenExpired: () => {
            console.log("onAccessTokenError");
// re-trigger sign-in flow
},
onErrorReceived: (type, msg) => {
            console.log("onErrorReceived", type, msg);
},
}
```
