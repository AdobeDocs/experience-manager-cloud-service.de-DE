---
title: Asset-Selektor für [!DNL Adobe Experience Manager] als ein [!DNL Cloud Service]
description: Verwenden Sie den Asset-Selektor, um die Metadaten und Ausgabeformate von Assets in Ihrer Applikation zu suchen, zu finden und abzurufen.
contentOwner: KK
role: Admin,User
exl-id: b968f63d-99df-4ec6-a9c9-ddb77610e258
source-git-commit: b9fe6f4c2f74d5725575f225f8d9eb2e5fbfceb7
workflow-type: tm+mt
source-wordcount: '3908'
ht-degree: 50%

---


# Micro-Front-End-Asset-Selektor {#Overview}

Der Micro-Front-End-Asset-Selektor bietet eine Benutzeroberfläche, die sich problemlos in das [!DNL Experience Manager Assets]-Repository integrieren lässt, sodass Sie die im Repository verfügbaren digitalen Assets durchsuchen und für die Erstellung von Applikationen verwenden können.

Die Micro-Front-End-Benutzeroberfläche wird über das Asset-Selektor-Paket in Ihrer Applikation verfügbar gemacht. Alle Aktualisierungen des Pakets werden automatisch importiert, und der zuletzt bereitgestellte Asset-Selektor wird automatisch in Ihrer Applikation geladen.

![Übersicht](assets/overview.png)

Der Asset-Selektor bietet viele Vorteile, z. B.:

* Einfache Integration mit einem der [Adobe](#asset-selector-ims) oder [Nicht-Adobe](#asset-selector-non-ims) Anwendungen, die die Vanilla JavaScript-Bibliothek verwenden.
* Einfach zu verwalten, da Aktualisierungen des Assets-Wähler-Pakets automatisch für den Asset-Selektor bereitgestellt werden, der für Ihre Applikation verfügbar ist. Es sind keine Aktualisierungen innerhalb Ihrer Applikation erforderlich, um die neuesten Änderungen zu laden.
* Einfachere Anpassung, da Eigenschaften verfügbar sind, die die Anzeige des Asset-Selektors in Ihrer Applikation steuern.
* Volltextsuche, vordefinierte und benutzerdefinierte Filter, um schnell zu Assets zu navigieren, die für das Authoring-Erlebnis verwendet werden können.
* Möglichkeit, innerhalb einer IMS-Organisation zur Asset-Auswahl zwischen Repositorys zu wechseln.
* Möglichkeit, Assets nach Namen, Abmessungen und Größe zu sortieren und in der Listen-, Raster-, Galerie- oder Wasserfallansicht anzuzeigen.

<!--Perform the following tasks to integrate and use Asset Selector with your [!DNL Experience Manager Assets] repository:

1. [Install Asset Selector](#installation)
2. [Integrate Asset Selector using Vanilla JS](#integration-using-vanilla-js)
3. [Use Asset Selector](#using-asset-selector)
-->

<!--
## Setting up Asset Selector {#asset-selector-setup}

![Asset Selector set up](assets/asset-selector-prereqs.png)
-->

## Voraussetzungen{#prereqs}

Sie müssen die folgenden Kommunikationsmethoden sicherstellen:

* Die Anwendung wird unter HTTPS ausgeführt.
* Die URL der Anwendung befindet sich in der Zulassungsliste der Umleitungs-URLs durch den IMS-Client.
* Der IMS-Anmeldefluss wird mithilfe eines Popup-Fensters im Webbrowser konfiguriert und wiedergegeben. Daher sollten Popups im Zielbrowser aktiviert oder zugelassen werden.

Verwenden Sie die oben genannten Voraussetzungen, wenn Sie einen IMS-Authentifizierungs-Workflow der Asset-Auswahl benötigen. Wenn Sie bereits mit dem IMS-Workflow authentifiziert sind, können Sie stattdessen die IMS-Informationen hinzufügen.

>[!IMPORTANT]
>
> Dieses Repository dient als zusätzliche Dokumentation, die die verfügbaren APIs und Nutzungsbeispiele für die Integration von Asset Selector beschreibt. Bevor Sie versuchen, die Asset-Auswahl zu installieren oder zu verwenden, stellen Sie sicher, dass Ihr Unternehmen Zugriff auf die Asset-Auswahl im as a Cloud Service Experience Manager Assets-Profil erhalten hat. Wenn Sie noch nicht bereitgestellt wurden, können Sie diese Komponenten nicht integrieren oder verwenden. Um die Bereitstellung anzufordern, sollte Ihr Programmadministrator ein Support-Ticket erstellen, das von Admin Console als P2 gekennzeichnet ist, und die folgenden Informationen einschließen:
>
>* Domänennamen, auf denen die integrative Anwendung gehostet wird.
>* Nach der Bereitstellung wird Ihr Unternehmen mit `imsClientId`, `imsScope`und ein `redirectUrl` entspricht den angeforderten Umgebungen, die für die Konfiguration der Asset-Auswahl erforderlich sind. Ohne diese gültigen Eigenschaften können Sie die Installationsschritte nicht ausführen.

## Installation {#installation}

Der Asset-Selektor ist über beide ESM-CDN verfügbar (z. B. [esm.sh](https://esm.sh/)/[Skypack](https://www.skypack.dev/)) und [UMD](https://github.com/umdjs/umd) -Version.

In Browsern mit **UMD-Version** (empfohlen):

```
<script src="https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/assets-selectors.js"></script>

<script>
  const { renderAssetSelector } = PureJSSelectors;
</script>
```

In Browsern mit `import maps`-Unterstützung mit **ESM CDN-Version**:

```
<script type="module">
  import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
</script>
```

In der Deno/Webpack Module Federation mit **ESM CDN-Version**:

```
import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
```

## Asset-Selektor mit Vanilla JS integrieren {#integration-using-vanilla-js}

Sie können jede [!DNL Adobe] oder Nicht-Adobe-Anwendung mit [!DNL Experience Manager Assets] Repository erstellen und Assets aus der Anwendung auswählen. Siehe [Asset-Selektor-Integration mit verschiedenen Anwendungen](#asset-selector-integration-with-apps).

Die Integration erfolgt durch den Import des Asset-Selektor-Pakets und die Verbindung zu Assets as a Cloud Service unter Verwendung der Vanilla JavaScript-Bibliothek. Bearbeiten einer `index.html` oder einer entsprechenden Datei in Ihrer Anwendung, um:

* Authentifizierungsdetails zu definieren
* Zugriff auf das Assets as a Cloud Service-Repository zu erhalten
* Anzeigeeigenschaften des Asset-Selektors zu konfigurieren

Sie können eine Authentifizierung durchführen, ohne einige der IMS-Eigenschaften zu definieren, wenn:

* Sie eine [!DNL Adobe]-Applikation auf [Unified Shell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=de) integrieren.
* Für die Authentifizierung wurde bereits ein IMS-Token generiert.

## Integrieren der Asset-Auswahl in verschiedene Anwendungen {#asset-selector-integration-with-apps}

Sie können die Asset-Auswahl in verschiedene Anwendungen integrieren, z. B.:

* [Integrieren der Asset-Auswahl in eine [!DNL Adobe] Applikation](#adobe-app-integration-vanilla)
* [Integrieren der Asset-Auswahl in eine Nicht-Adobe-Anwendung](#adobe-non-app-integration)

>[!BEGINTABS]

<!--Integration with an Adobe application content starts here-->

>[!TAB Integration mit einer Adobe-Anwendung]

### Voraussetzungen{#prereqs-adobe-app}

Verwenden Sie die folgenden Voraussetzungen, wenn Sie die Asset-Auswahl in eine [!DNL Adobe] application:

* [Kommunikationsmethoden](#prereqs)
* imsOrg
* imsToken
* apikey

### Integrieren der Asset-Auswahl in eine [!DNL Adobe] Applikation {#adobe-app-integration-vanilla}

Im folgenden Beispiel wird die Verwendung des Asset-Selektors beim Ausführen eines [!DNL Adobe] Anwendung unter Unified Shell oder wenn Sie bereits `imsToken` zur Authentifizierung generiert wurde.

Fügen Sie das Asset-Wähler-Paket mit dem `script`-Tag in Ihren Code ein, wie in _Zeilen 6 bis 15_ des folgenden Beispiels zu sehen. Sobald das Skript geladen ist, kann die globale Variable `PureJSSelectors` verwendet werden. Definieren Sie die [Eigenschaften](#asset-selector-properties) des Asset-Wählers wie in _Zeilen 16 bis 23_ zu sehen. Die `imsOrg` und `imsToken` -Eigenschaften sind beide für die Authentifizierung in der Adobe-Anwendung erforderlich. Die `handleSelection`-Eigenschaft wird verwendet, um die ausgewählten Assets zu behandeln. Um den Asset-Wähler zu rendern, rufen Sie die `renderAssetSelector`-Funktion wie in _Zeile 17_ erwähnt auf. Der Asset-Wähler wird im Container-Element `<div>` angezeigt, wie in _Zeilen 21 und 22_ zu sehen.

Wenn Sie die folgenden Schritte ausführen, können Sie die Asset-Auswahl mit Ihrem [!DNL Adobe] Anwendung.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>
<head>
    <title>Asset Selector</title>
    <script src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/assets-selectors.js"></script>
    <script>
        // get the container element in which we want to render the AssetSelector component
        const container = document.getElementById('asset-selector-container');
        // imsOrg and imsToken are required for authentication in Adobe application
        const assetSelectorProps = {
            imsOrg: 'example-ims@AdobeOrg',
            imsToken: "example-imsToken",
            apiKey: "example-apiKey-associated-with-imsOrg",
            handleSelection: (assets: SelectedAssetType[]) => {},
        };
        // Call the `renderAssetSelector` available in PureJSSelectors globals to render AssetSelector
        PureJSSelectors.renderAssetSelector(container, assetSelectorProps);
    </script>
</head>

<body>
    <div id="asset-selector-container" style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px;">
    </div>
</body>

</html>
```

<!--For detailed example, visit [Asset Selector Code Example](https://github.com/adobe/aem-assets-selectors-mfe-examples).-->

+++**ImsAuthProps**
Die `ImsAuthProps` Eigenschaften definieren die Authentifizierungsinformationen und den Ablauf, mit dem der Asset-Selektor eine `imsToken`. Durch Festlegen dieser Eigenschaften können Sie steuern, wie sich der Authentifizierungsfluss verhält, und Listener für verschiedene Authentifizierungsereignisse registrieren.

| Eigenschaftsname | Beschreibung |
|---|---|
| `imsClientId` | Ein string -Wert, der die für Authentifizierungszwecke verwendete IMS-Client-ID darstellt. Dieser Wert wird von Adobe bereitgestellt und ist spezifisch für Ihre Adobe AEM CS-Organisation. |
| `imsScope` | Beschreibt die bei der Authentifizierung verwendeten Bereiche. Die Bereiche bestimmen den Umfang des Zugriffs, den die Anwendung auf die Ressourcen Ihrer Organisation hat. Mehrere Bereiche können durch Kommas getrennt werden. |
| `redirectUrl` | Stellt die URL dar, an die der Benutzer nach der Authentifizierung weitergeleitet wird. Dieser Wert wird normalerweise auf die aktuelle URL der Anwendung gesetzt. Wenn eine `redirectUrl` nicht geliefert wird, `ImsAuthService` verwendet die zum Registrieren der `imsClientId` |
| `modalMode` | Ein boolescher Wert, der angibt, ob der Authentifizierungsfluss in einem modalen (Popup) angezeigt werden soll oder nicht. Wenn auf `true`, wird der Authentifizierungsfluss in einem Popup-Fenster angezeigt. Wenn auf `false`, wird der Authentifizierungsfluss bei vollständigem Neuladen der Seite angezeigt. _Hinweis:_ für eine bessere UX können Sie diesen Wert dynamisch steuern, wenn das Popup-Fenster des Browsers deaktiviert ist. |
| `onImsServiceInitialized` | Eine Callback-Funktion, die aufgerufen wird, wenn der Adobe IMS-Authentifizierungsdienst initialisiert wird. Diese Funktion akzeptiert einen Parameter, `service`, ein Objekt, das den Adobe IMS-Dienst darstellt. Siehe [`ImsAuthService`](#imsauthservice-ims-auth-service) für weitere Details. |
| `onAccessTokenReceived` | Eine Callback-Funktion, die aufgerufen wird, wenn eine `imsToken` wird vom Adobe IMS-Authentifizierungsdienst empfangen. Diese Funktion akzeptiert einen Parameter, `imsToken`, eine Zeichenfolge, die das Zugriffstoken darstellt. |
| `onAccessTokenExpired` | Eine Callback-Funktion, die aufgerufen wird, wenn ein Zugriffstoken abgelaufen ist. Diese Funktion wird normalerweise verwendet, um einen neuen Authentifizierungsfluss Trigger, um ein neues Zugriffstoken zu erhalten. |
| `onErrorReceived` | Eine Callback-Funktion, die aufgerufen wird, wenn während der Authentifizierung ein Fehler auftritt. Diese Funktion akzeptiert zwei Parameter: den Fehlertyp und die Fehlermeldung. Der Fehlertyp ist eine Zeichenfolge, die den Fehlertyp darstellt, und die Fehlermeldung ist eine Zeichenfolge, die die Fehlermeldung darstellt. |

+++

+++**ImsAuthService**
`ImsAuthService` -Klasse verarbeitet den Authentifizierungsfluss für die Asset-Auswahl. Sie ist für den Erhalt einer `imsToken` über den Adobe IMS-Authentifizierungsdienst. Die `imsToken` wird verwendet, um den Benutzer zu authentifizieren und den Zugriff auf die [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Assets-Repository. ImsAuthService verwendet die `ImsAuthProps` -Eigenschaften, um den Authentifizierungsfluss zu steuern und Listener für verschiedene Authentifizierungsereignisse zu registrieren. Sie können die bequeme [`registerAssetsSelectorsAuthService`](#purejsselectorsregisterassetsselectorsauthservice) -Funktion zum Registrieren der _ImsAuthService_ -Instanz mit der Asset-Auswahl. Die folgenden Funktionen sind im `ImsAuthService` -Klasse. Wenn Sie jedoch die _registerAssetsSelectorsAuthService_ -Funktion verwenden, müssen Sie diese Funktionen nicht direkt aufrufen.

| Funktionsname | Beschreibung |
|---|---|
| `isSignedInUser` | Bestimmt, ob der Benutzer derzeit beim Dienst angemeldet ist, und gibt entsprechend einen booleschen Wert zurück. |
| `getImsToken` | Ruft die Authentifizierung ab `imsToken` für den derzeit angemeldeten Benutzer, der zum Authentifizieren von Anforderungen für andere Dienste wie zum Beispiel zum Generieren von Asset-Ausgabedarstellungen verwendet werden kann. |
| `signIn` | Startet den Anmeldeprozess für den Benutzer. Diese Funktion verwendet die `ImsAuthProps` , um die Authentifizierung in einem Popup- oder einem vollständigen Seiten-Neuladen anzuzeigen. |
| `signOut` | Signiert den Benutzer aus dem Dienst, macht sein Authentifizierungstoken ungültig und fordert ihn auf, sich erneut anzumelden, um auf geschützte Ressourcen zuzugreifen. Durch Aufrufen dieser Funktion wird die aktuelle Seite neu geladen. |
| `refreshToken` | Aktualisiert das Authentifizierungstoken für den derzeit angemeldeten Benutzer, verhindert das Auslaufen des Tokens und stellt einen unterbrechungsfreien Zugriff auf geschützte Ressourcen sicher. Gibt ein neues Authentifizierungstoken zurück, das für nachfolgende Anforderungen verwendet werden kann. |

+++

+++**Validierung mit bereitgestelltem IMS-Token**

```
<script>
    const apiToken="<valid IMS token>";
    function handleSelection(selection) {
    console.log("Selected asset: ", selection);
    };
    function renderAssetSelectorInline() {
    console.log("initializing Asset Selector");
    const props = {
    "repositoryId": "delivery-p64502-e544757.adobeaemcloud.com",
    "apiKey": "ngdm_test_client",
    "imsOrg": "<IMS org>",
    "imsToken": apiToken,
    handleSelection,
    hideTreeNav: true
    }
    const container = document.getElementById('asset-selector-container');
    PureJSSelectors.renderAssetSelector(container, props);
    }
    $(document).ready(function() {
    renderAssetSelectorInline();
    });
</script>
```

+++

+++**Callbacks des IMS-Dienstes registrieren**

```
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

+++

<!--Integration with non-Adobe application content starts here-->

>[!TAB Integration mit einer Nicht-Adobe-Anwendung]

<!--### Integrate Asset Selector with a [!DNL non-Adobe] application {#adobe-non-app-integration}-->

### Voraussetzungen {#prereqs-non-adobe-app}

Verwenden Sie die folgenden Voraussetzungen, wenn Sie Asset Selector in eine Nicht-Adobe-Anwendung integrieren:

* [Kommunikationsmethoden](#prereqs)
* imsClientId
* imsScope
* redirectUrl
* imsOrg
* apikey

Asset Selector unterstützt die Authentifizierung für die [!DNL Experience Manager Assets] Repository mit Identity Management System (IMS)-Eigenschaften, z. B. `imsScope` oder `imsClientID` wenn Sie es in eine Nicht-Adobe-Anwendung integrieren.

+++**Konfigurieren des Asset-Selektors für eine Nicht-Adobe-Anwendung**
Um die Asset-Auswahl für eine Nicht-Adobe-Anwendung zu konfigurieren, müssen Sie zunächst ein Support-Ticket für die Bereitstellung und dann die Integrationsschritte protokollieren.

**Support-Ticket anmelden**
Schritte zum Protokollieren eines Support-Tickets über die Admin Console:

1. Hinzufügen **Asset-Auswahl mit AEM Assets** im Titel des Tickets.

1. Geben Sie in der Beschreibung die folgenden Details an:

   * [!DNL Experience Manager Assets] as a [!DNL Cloud Service] URL (Programm-ID und Umgebungs-ID).
   * Domänennamen, auf denen die Nicht-Adobe-Webanwendung gehostet wird.
+++

+++**Integrationsschritte**
Verwenden Sie dieses Beispiel `index.html` zur Authentifizierung bei der Integration von Asset Selector in eine Nicht-Adobe-Anwendung.

Greifen Sie mithilfe des `Script` Tagging, wie in *Linie 9* nach *Zeile 11* des Beispiels `index.html` -Datei.

*Zeile 14* nach *Linie 38* Im Beispiel werden die Eigenschaften des IMS-Flusses beschrieben, z. B. `imsClientId`, `imsScope`, und `redirectURL`. Die Funktion erfordert, dass Sie mindestens einen der `imsClientId` und `imsScope` Eigenschaften. Wenn Sie keinen Wert für `redirectURL`, wird die registrierte Umleitungs-URL für die Client-ID verwendet.

Da Sie keine `imsToken` generieren, verwenden Sie die `registerAssetsSelectorsAuthService` und `renderAssetSelectorWithAuthFlow` Funktionen, wie in den Zeilen 40 bis 50 des Beispiels dargestellt `index.html` -Datei. Verwenden Sie die `registerAssetsSelectorsAuthService` Funktion vor `renderAssetSelectorWithAuthFlow` zur Registrierung `imsToken` mit der Asset-Auswahl. [!DNL Adobe] empfiehlt, `registerAssetsSelectorsAuthService` wenn Sie die Komponente instanziieren.

Definieren Sie die Authentifizierungs- und anderen as a Cloud Service Zugriffseigenschaften für Assets im `const props` -Abschnitt, wie in *Zeile 54* nach *Linie 60* des Beispiels `index.html` -Datei.

Die `PureJSSelectors` globale Variable, erwähnt in *Zeile 65* wird verwendet, um die Asset-Auswahl im Webbrowser zu rendern.

Die Asset-Auswahl wird im `<div>` Container-Element, wie unter *Zeile 74* nach *Zeile 81*. Das Beispiel verwendet ein Dialogfeld zum Anzeigen der Asset-Auswahl.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta charset="utf-8">
    <title>Asset Selectors</title>
    <link rel="stylesheet" href="index.css">
    <script id="asset-selector"
        src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/asset-selectors.js"></script>
    <script>

        const imsProps = {
            imsClientId: "<obtained from IMS team>",
            imsScope: "openid, <other scopes>",
            redirectUrl: window.location.href,
            modalMode: true, // false to open in a full page reload flow
            onImsServiceInitialized: (service) => {
                // invoked when the ims service is initialized and is ready
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

        function load() {
            const registeredTokenService = PureJSSelectors.registerAssetsSelectorsAuthService(imsProps);
            imsInstance = registeredTokenService;
        };

        // initialize the IMS flow before attempting to render the asset selector
        load();
        

        //function that will render the asset selector
            const otherProps = {
            // any other props supported by asset selector
            }
            const assetSelectorProps = {
                "imsOrg": "imsorg",
                ...otherProps
            }
             // container element on which you want to render the AssetSelector/DestinationSelector component
            const container = document.getElementById('asset-selector');

            /// Use the PureJSSelectors in globals to render the AssetSelector/DestinationSelector component
            PureJSSelectors.renderAssetSelectorWithAuthFlow(container, assetSelectorProps, () => {
                const assetSelectorDialog = document.getElementById('asset-selector-dialog');
                assetSelectorDialog.showModal();
            });
        }
    </script>

</head>
<body class="asset-selectors">
    <div>
        <button onclick="renderAssetSelectorWithAuthFlowFlow()">Asset Selector - Select Assets with Ims Flow</button>
    </div>
        <dialog id="asset-selector-dialog">
            <div id="asset-selector" style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px;">
            </div>
        </dialog>
    </div>
</body>

</html>
```

+++

+++**Zugriff auf Bereitstellungs-Repository nicht möglich**

>[!TIP]
>
>Wenn Sie die Asset-Auswahl mithilfe des Workflows Anmelden integriert haben, aber trotzdem nicht auf das Versand-Repository zugreifen können, stellen Sie sicher, dass Browser-Cookies bereinigt werden. Andernfalls erhalten Sie `invalid_credentials All session cookies are empty` in der Konsole.

>[!ENDTABS]

## Asset-Auswahleigenschaften {#asset-selector-properties}

Sie können die Asset-Wähler-Eigenschaften verwenden, um die Darstellung des Asset-Wählers anzupassen. In der folgenden Tabelle sind die Eigenschaften aufgeführt, mit denen Sie den Asset-Wähler anpassen und verwenden können.

| Eigenschaft | Typ | Erforderlich | Standard | Beschreibung |
|---|---|---|---|---|
| *Leiste* | Boolesch | Nein | Falsch | Wenn als `true` markiert, wird der Asset-Wähler in der linken Leistenansicht gerendert. Wenn als `false` markiert, wird der Asset-Wähler in der modalen Ansicht gerendert. |
| *imsOrg* | Zeichenfolge | Ja | | Die Adobe Identity Management System (IMS)-ID, die bei der Bereitstellung von [!DNL Adobe Experience Manager] als [!DNL Cloud Service] für Ihre Organisation zugewiesen wird. Der `imsOrg`-Schlüssel ist erforderlich, damit authentifiziert wird, ob sich die Organisation, auf die Sie zugreifen, unter Adobe IMS befindet oder nicht. |
| *imsToken* | Zeichenfolge | Nein | | Für die Authentifizierung verwendeter IMS-Bearer-Token. `imsToken` ist erforderlich, wenn Sie eine [!DNL Adobe] -Anwendung für die Integration. |
| *apiKey* | Zeichenfolge | Nein | | API-Schlüssel, der für den Zugriff auf den AEM Discovery-Dienst verwendet wird. `apiKey` ist erforderlich, wenn Sie eine [!DNL Adobe] Anwendungsintegration. |
| *rootPath* | Zeichenfolge | Nein | /content/dam/ | Ordnerpfad, aus dem der Asset-Wähler Ihre Assets anzeigt. `rootPath` kann auch in Form einer Verkapselung verwendet werden. Bei dem folgenden Pfad `/content/dam/marketing/subfolder/` können Sie mit dem Asset-Wähler beispielsweise nicht durch übergeordnete Ordner navigieren, sondern nur die untergeordneten Ordner anzeigen. |
| *path* | Zeichenfolge | Nein | | Pfad, der zum Navigieren zu einem bestimmten Asset-Verzeichnis verwendet wird, wenn der Asset-Wähler gerendert wird. |
| *filterSchema* | Array | Nein | | Modell, das zum Konfigurieren von Filtereigenschaften verwendet wird. Dies ist nützlich, wenn Sie bestimmte Filteroptionen des Asset-Wählers einschränken möchten. |
| *filterFormProps* | Objekt | Nein | | Geben Sie die Filtereigenschaften an, die Sie zur Verfeinerung Ihrer Suche verwenden müssen. Beispielsweise MIME-Typ, JPG, PNG, GIF. |
| *selectedAssets* | Array `<Object>` | Nein |                 | Geben Sie ausgewählte Assets an, wenn der Asset-Wähler gerendert wird. Es ist ein Array von Objekten erforderlich, das eine ID-Eigenschaft der Assets enthält. Zum Beispiel: `[{id: 'urn:234}, {id: 'urn:555'}]` Ein Asset muss im aktuellen Verzeichnis verfügbar sein. Wenn Sie ein anderes Verzeichnis verwenden müssen, geben Sie auch einen Wert für die Eigenschaft `path` an. |
| *acvConfig* | Objekt | Nein | | Asset Collection View-Eigenschaft, die ein Objekt enthält, das eine benutzerdefinierte Konfiguration enthält, um Standardwerte zu überschreiben. Diese Eigenschaft wird auch mit `rail` -Eigenschaft, um die Schienenansicht des Asset-Viewers zu aktivieren. |
| *i18nSymbols* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | Nein |                 | Wenn die OOTB-Übersetzungen nicht ausreichen, um die Anforderungen Ihrer Anwendung zu erfüllen, können Sie eine Benutzeroberfläche bereitstellen, über die Sie Ihre eigenen benutzerdefinierten lokalisierten Werte über die `i18nSymbols` prop. Wenn Sie über diese Schnittstelle einen Wert übergeben, werden die bereitgestellten Standardübersetzungen überschrieben und stattdessen Ihre eigenen verwendet. Um die Überschreibung vorzunehmen, müssen Sie ein gültiges [Message Descriptor](https://formatjs.io/docs/react-intl/api/#message-descriptor)-Objekt an den Schlüssel von `i18nSymbols` übergeben, den Sie überschreiben möchten. |
| *intl* | Objekt | Nein | | Der Asset-Selektor bietet standardmäßige OOTB-Übersetzungen. Sie können die Übersetzungssprache auswählen, indem Sie eine gültige Gebietsschema-Zeichenfolge durch die `intl.locale`-Eigenschaft bereitstellen. Zum Beispiel: `intl={{ locale: "es-es" }}` </br></br> Die unterstützten Gebietsschema-Zeichenfolgen folgen den [ISO 639 – Codes](https://www.iso.org/iso-639-language-codes.html) für die Darstellung von Namen von Sprachen. </br></br> Liste der unterstützten Gebietsschemata: Englisch: „en-us“ (Standard), Spanisch: „es-es“, Deutsch: „de-de“, Französisch: „fr-fr“, Italienisch: „it-it“, Japanisch: „ja-jp“, Koreanisch: „ko-kr“, Portugiesisch: „pt-br“, Chinesisch (Vereinfacht): „zh-cn“, Chinesisch (Taiwan): „zh-tw“ |
| *repositoryId* | Zeichenfolge | Nein | &#39;&#39; | Repository, aus dem der Asset-Wähler den Inhalt lädt. |
| *additionalAemSolutions* | `Array<string>` | Nein | [ ] | Damit können Sie eine Liste mit zusätzlichen AEM-Repositorys hinzufügen. Wenn in dieser Eigenschaft keine Informationen bereitgestellt werden, werden nur die Medienbibliothek oder AEM Assets-Repositorys berücksichtigt. |
| *hideTreeNav* | Boolesch | Nein |  | Gibt an, ob die Navigationsseitenleiste der Asset-Baumstruktur ein- oder ausgeblendet werden soll. Sie wird nur in der modalen Ansicht verwendet und daher gibt es keine Auswirkung dieser Eigenschaft in der Leistenansicht. |
| *onDrop* | Funktion | Nein | | Die Eigenschaft ermöglicht die Ablagefunktion eines Assets. |
| *dropOptions* | `{allowList?: Object}` | Nein | | Konfiguriert Ablagefunktionen mithilfe der „Zulassungsliste“. |
| *colorScheme* | Zeichenfolge | Nein | | Design konfigurieren (`light` oder `dark`) für den Asset-Wähler. |
| *handleSelection* | Funktion | Nein | | Wird mit einem Array von Asset-Elementen aufgerufen, wenn Assets ausgewählt sind und die Schaltfläche `Select` im Modal angeklickt wird. Diese Funktion wird nur in der modalen Ansicht aufgerufen. Verwenden Sie für die Leistenansicht die Funktionen `handleAssetSelection` oder `onDrop`. Beispiel: <pre>handleSelection=(assets: Asset[])==> {...}</pre> Siehe [Ausgewählter Asset-Typ](#selected-asset-type) für Details. |
| *handleAssetSelection* | Funktion | Nein | | Wird mit einem Array von Elementen aufgerufen, während die Assets ausgewählt oder deren Auswahl aufgehoben wird. Dies ist nützlich, wenn Sie auf Assets warten möchten, während die Benutzenden sie auswählen. Beispiel: <pre>handleSelection=(assets: Asset[])==> {...}</pre> Siehe [Ausgewählter Asset-Typ](#selected-asset-type) für Details. |
| *onClose* | Funktion | Nein | | Wird aufgerufen, wenn die `Close`-Schaltfläche in der modalen Ansicht gedrückt wird. Dies wird nur in der `modal`-Ansicht aufgerufen und in der `rail`-Ansicht nicht beachtet. |
| *onFilterSubmit* | Funktion | Nein | | Wird mit Filterelementen aufgerufen, wenn Benutzende andere Filterkriterien ändern. |
| *selectionType* | Zeichenfolge | Nein | Einzelperson | Konfiguration für `single`- oder `multiple`-Auswahl von Assets auf einmal. |
| *DragOptions.Zulassungsliste* | Boolesch | Nein | | Die -Eigenschaft wird verwendet, um das Ziehen von nicht auswählbaren Assets zuzulassen oder zu verweigern. |
| *aemTierType* | Zeichenfolge | Nein | | Sie können damit festlegen, ob Assets aus der Bereitstellungsebene, der Autorenstufe oder beidem angezeigt werden sollen. <br><br> Syntax: `aemTierType:[0: "author" 1: "delivery"` <br><br> Wenn zum Beispiel beide `["author","delivery"]` verwendet werden, zeigt der Repository-Umschalter Optionen für Autor und Bereitstellung an. |
| *handleNavigateToAsset* | Funktion | Nein | | Es handelt sich um eine Callback-Funktion, die die Auswahl eines Assets verarbeitet. |
| *noWrap* | Boolesch | Nein | | Die *noWrap* -Eigenschaft hilft beim Rendern der Asset-Auswahl im Seitenleiste-Bedienfeld. Wenn diese Eigenschaft nicht erwähnt wird, wird die *Dialogfeldansicht* Standardmäßig. |
| *dialogSize* | kleine, mittlere, große, Vollbild- oder Vollbild-Übernahme | Zeichenfolge | Optional | Sie können das Layout durch Angabe der Größe mithilfe der angegebenen Optionen steuern. |
| *colorScheme* | hell oder dunkel | Nein | | Diese Eigenschaft wird verwendet, um das Design einer Asset-Selektor-Anwendung festzulegen. Sie können zwischen hellen und dunklen Themen wählen. |
| *filterRepoList* | Funktion | Nein |  | Sie können `filterRepoList` Callback-Funktion, die das Experience Manager-Repository aufruft und eine gefilterte Liste von Repositorys zurückgibt. |

## Beispiele zur Verwendung der Asset-Selektor-Eigenschaften {#usage-examples}

Sie können die Asset-Selektor-[Eigenschaften](#asset-selector-properties) in der Datei `index.html` definieren, um die Anzeige des Asset-Selektors in Ihrer Applikation anzupassen.

### Beispiel 1: Asset-Selektor in der Leistenansicht

![rail-view-example](assets/rail-view-example-vanilla.png)

Wenn der Wert des AssetSelector `rail` auf `false` oder in den Eigenschaften nicht erwähnt wird, wird die Asset-Auswahl standardmäßig in der Modal-Ansicht angezeigt. Die `acvConfig` -Eigenschaft ermöglicht einige tief greifende Konfigurationen, wie Drag-and-Drop. Besuch [Drag &amp; Drop aktivieren oder deaktivieren](#enable-disable-drag-and-drop) , um die Verwendung von `acvConfig` -Eigenschaft.

<!--
### Example 2: Use selectedAssets property in addition to the path property

Use the `path` property to define the folder name that displays automatically when the Asset Selector is rendered. In addition, use the `selectedAssets` property to define the IDs for the assets that you need to select within the folder. Moreover, when you want to display assets that are pre-defined within the folder, you can use selectedAssets property.

   ![selected-assets-example](assets/selected-assets-example-vanilla.png)
-->

### Beispiel 2: Metadaten-Popover

Verwenden Sie verschiedene Eigenschaften, um Metadaten eines Assets zu definieren, das Sie mit einem Informationssymbol anzeigen möchten. Das Info-Popover bietet die Sammlung von Informationen über das Asset oder den Ordner, einschließlich Titel, Abmessungen, Änderungsdatum, Speicherort und Beschreibung eines Assets. Im folgenden Beispiel werden verschiedene Eigenschaften verwendet, um Metadaten eines Assets anzuzeigen, z. B. gibt die Eigenschaft `repo:path` den Speicherort eines Assets an. <!--`repo` represents the repository from where the asset is showing, whereas, `path` represents the route from where the asset or folder is rendered.-->

![metadata-popover-example](assets/metadata-popover.png)

### Beispiel 3: Benutzerdefinierte Filtereigenschaft in der Leistenansicht

Zusätzlich zur Facettensuche können Sie mit dem Asset-Selektor verschiedene Attribute anpassen, um Ihre Suche von [!DNL Adobe Experience Manager] als eine [!DNL Cloud Service]-Anwendung zu verfeinern. Fügen Sie den folgenden Code hinzu, um benutzerdefinierte Suchfilter zu Ihrer Anwendung hinzuzufügen. Im folgenden Beispiel ist die `Type Filter`-Suche, die den Asset-Typ nach Bildern, Dokumenten oder Videos filtert, oder der Filtertyp, den Sie für die Suche hinzugefügt haben.

![custom-filter-example-vanilla](assets/custom-filter-example-vanilla.png)

<!--

## Customization after integrating Asset Selector 

### Custom metadata

Assets display panel shows the out of the box metadata that can be displayed in the info of the asset. In addition to this, [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application allows configuration of the asset selector by adding custom metadata that is shown in info panel of the asset.
-->

## Code-Snippets für die funktionale Einrichtung{#code-snippets}

Definieren Sie die Voraussetzungen in der `index.html` Datei oder einer ähnlichen Datei in Ihrer Anwendungsimplementierung, um die Authentifizierungsdetails für den Zugriff auf die [!DNL Experience Manager Assets] Repository. Danach können Sie Codefragmente gemäß Ihren Anforderungen hinzufügen.

### Anpassen des Filterbereichs {#customize-filter-panel}

Sie können das folgende Codefragment in `assetSelectorProps` -Objekt zum Anpassen des Filterbereichs:

```
filterSchema: [
    {
    header: 'File Type',
    groupKey: 'TopGroup',
    fields: [
    {
    element: 'checkbox',
    name: 'type',
    options: [
    {
    label: 'Images',
    value: '<comma separated mimetypes, without space, that denote all images, for e.g., image/>',
    },
    {
    label: 'Videos',
    value: '<comma separated mimetypes, without space, that denote all videos for e.g., video/,model/vnd.mts,application/mxf>'
    }
    ]
    }
    ]
    },
    {
    fields: [
    {
    element: 'checkbox',
    name: 'type',
    options: [
    { label: 'JPG', value: 'image/jpeg' },
    { label: 'PNG', value: 'image/png' },
    { label: 'TIFF', value: 'image/tiff' },
    { label: 'GIF', value: 'image/gif' },
    { label: 'MP4', value: 'video/mp4' }
    ],
    columns: 3,
    },
    ],
    header: 'Mime Types',
    groupKey: 'MimeTypeGroup',
    }},
    {
    fields: [
    {
    element: 'checkbox',
    name: 'property=metadata.application.xcm:keywords.value',
    options: [
    { label: 'Fruits', value: 'fruits' },
    { label: 'Vegetables', value: 'vegetables'}
    ],
    columns: 3,
    },
    ],
    header: 'Food Category',
    groupKey: 'FoodCategoryGroup',
    }
],
```

### Informationen in der modalen Ansicht anpassen {#customize-info-in-modal-view}

Sie können die Detailansicht eines Assets anpassen, wenn Sie auf die ![Infosymbol](assets/info-icon.svg) Symbol. Führen Sie den folgenden Code aus:

```
// Create an object infoPopoverMap and set the property `infoPopoverMap` with it in assetSelectorProps
const infoPopoverMap = (map) => {
// for example, to skip `path` from the info popover view
let defaultPopoverData = PureJSSelectors.getDefaultInfoPopoverData(map);
return defaultPopoverData.filter((i) => i.label !== 'Path'
};
assetSelectorProps.infoPopoverMap = infoPopoverMap;
```

### Drag &amp; Drop-Modus aktivieren oder deaktivieren {#enable-disable-drag-and-drop}

Fügen Sie die folgenden Eigenschaften zu `assetSelectorProp` , um den Drag-and-Drop-Modus zu aktivieren. Um Drag-and-Drop zu deaktivieren, ersetzen Sie die `true` Parameter mit `false`.

```
rail: true,
acvConfig: {
dragOptions: {
allowList: {
'*': true,
},
},
selectionType: 'multiple'
}

// the drop handler to be implemented
function drop(e) {
e.preventDefault();
// following helps you get the selected assets – an array of objects.
const data = JSON.parse(e.dataTransfer.getData('collectionviewdata'));
}
```

### Auswahl von Assets {#selection-of-assets}

Der ausgewählte Asset-Typ ist ein Array von Objekten, das die Asset-Informationen bei Verwendung der Funktionen `handleSelection`, `handleAssetSelection` und `onDrop` enthält.

Führen Sie die folgenden Schritte aus, um die Auswahl einzelner oder mehrerer Assets zu konfigurieren:

```
acvConfig: {
selectionType: 'multiple' // 'single' for single selection
}
// the `handleSelection` callback, always gets you the array of selected assets
```

**Schemasyntax**

```
interface SelectedAsset {
    'repo:id': string;
    'repo:name': string;
    'repo:path': string;
    'repo:size': number;
    'repo:createdBy': string;
    'repo:createDate': string;
    'repo:modifiedBy': string; 
    'repo:modifyDate': string; 
    'dc:format': string; 
    'tiff:imageWidth': number;
    'tiff:imageLength': number;
    'repo:state': string;
    computedMetadata: Record<string, any>;
    _links: {
        'http://ns.adobe.com/adobecloud/rel/rendition': Array<{
            href: string;
            type: string;
            'repo:size': number;
            width: number;
            height: number;
            [others: string]: any;
        }>;
    };
}
```

Die folgende Tabelle beschreibt einige der wichtigen Eigenschaften des ausgewählten Asset-Objekts.

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| *repo:repositoryId* | Zeichenfolge | Eindeutige Kennung für das Repository, in dem das Asset gespeichert ist. |
| *repo:id* | Zeichenfolge | Eindeutige Kennung für das Asset. |
| *repo:assetClass* | Zeichenfolge | Die Klassifizierung des Assets (z. B. Bild oder Video, Dokument). |
| *repo:name* | Zeichenfolge | Der Name des Assets, einschließlich der Dateierweiterung. |
| *repo:size* | Number (Zahl) | Die Größe des Assets in Bytes. |
| *repo:path* | Zeichenfolge | Der Speicherort des Assets im Repository. |
| *repo:ancestors* | `Array<string>` | Ein Array von Vorgängerelementen für das Asset im Repository. |
| *repo:state* | Zeichenfolge | Aktueller Status des Assets im Repository (z. B. aktiv, gelöscht). |
| *repo:createdBy* | Zeichenfolge | Die Person oder das System, welches das Asset erstellt hat. |
| *repo:createDate* | Zeichenfolge | Datum und Uhrzeit der Erstellung des Assets. |
| *repo:modifiedBy* | Zeichenfolge | Die Person oder das System, welches das Asset zuletzt geändert hat. |
| *repo:modifyDate* | Zeichenfolge | Datum und Uhrzeit der letzten Änderung des Assets. |
| *dc:format* | Zeichenfolge | Das Format des Assets, z. B. der Dateityp (z. B. JPEG, PNG usw.). |
| *tiff:imageWidth* | Number (Zahl) | Die Breite eines Assets. |
| *tiff:imageLength* | Number (Zahl) | Die Höhe eines Assets. |
| *computedMetadata* | `Record<string, any>` | Ein Objekt, das einen Behälter für alle Metadaten des Assets aller Art (Repository, Applikation oder eingebettete Metadaten) darstellt. |
| *_links* | `Record<string, any>` | Hypermedia-Links für das verknüpfte Asset. Enthält Links für Ressourcen wie Metadaten und Ausgabedarstellungen. |
| *_links.<http://ns.adobe.com/adobecloud/rel/rendition>* | `Array<Object>` | Array von Objekten, das Informationen zu Ausgabedarstellungen des Assets enthält. |
| *_links.<http://ns.adobe.com/adobecloud/rel/rendition[].href>* | Zeichenfolge | Der URI zur Ausgabedarstellung. |
| *_links.<http://ns.adobe.com/adobecloud/rel/rendition[].type>* | Zeichenfolge | Der MIME-Typ der Ausgabedarstellung. |
| *_links.<http://ns.adobe.com/adobecloud/rel/rendition[].'repo:size>&#39;* | Number (Zahl) | Die Größe der Ausgabedarstellung in Byte. |
| *_links.<http://ns.adobe.com/adobecloud/rel/rendition[].width>* | Number (Zahl) | Die Breite der Ausgabedarstellung. |
| *_links.<http://ns.adobe.com/adobecloud/rel/rendition[].height>* | Number (Zahl) | Die Höhe der Ausgabedarstellung. |

Eine vollständige Liste der Eigenschaften und ein ausführliches Beispiel finden Sie unter [Asset-Wähler-Code-Beispiel](https://github.com/adobe/aem-assets-selectors-mfe-examples).

## Umgang mit der Auswahl von Assets mithilfe des Objektschemas {#handling-selection}

Die `handleSelection`-Eigenschaft wird verwendet, um einzelne oder mehrere Auswahlen von Assets in dem Asset-Selektor zu verarbeiten. Das folgende Beispiel zeigt die Syntax der Verwendung von `handleSelection`.

![handle-selection](assets/handling-selection.png)

## Deaktivieren der Auswahl von Assets {#disable-selection}

Die Auswahl deaktivieren wird verwendet, um die Auswahl der Assets oder Ordner auszublenden oder zu deaktivieren. Dadurch wird das Kontrollkästchen &quot;Auswählen&quot;auf der Karte oder im Asset ausgeblendet, wodurch die Auswahl verhindert wird. Um diese Funktion zu verwenden, können Sie die Position eines Assets oder Ordners deklarieren, das Sie in einem Array deaktivieren möchten. Wenn Sie beispielsweise die Auswahl eines Ordners deaktivieren möchten, der an der ersten Position angezeigt wird, können Sie den folgenden Code hinzufügen:
`disableSelection: [0]:folder`

Sie können dem Array eine Liste von MIME-Typen (z. B. Bild, Ordner, Datei oder andere MIME-Typen, z. B. Bild/JPEG) bereitstellen, die Sie deaktivieren möchten. Die MIME-Typen, die Sie deklarieren, werden `data-card-type` und `data-card-mimetype` Attribute eines Assets.

Darüber hinaus können Assets mit deaktivierter Auswahl gezogen werden. Um das Ziehen und Ablegen eines bestimmten Asset-Typs zu deaktivieren, können Sie `dragOptions.allowList` -Eigenschaft.

Die Syntax der deaktivierten Auswahl lautet wie folgt:

```
(args)=> {
    return(
        <ASDialogWrapper
            {...args}
            disableSelection={args.disableSelection}
            handleAssetSelection={action('handleAssetSelection')}
            handleSelection={action('handleSelection')}
            selectionType={args.selectionType}
        />
    );
}
```

>[!NOTE]
>
> Bei einem Asset ist das Kontrollkästchen &quot;Auswählen&quot;ausgeblendet, während bei einem Ordner der Ordner nicht ausgewählt werden kann, aber die Navigation des genannten Ordners weiterhin angezeigt wird.

## Verwenden des Asset-Selektors {#using-asset-selector}

Sobald der Asset-Selektor eingerichtet ist und Sie für die Verwendung mit Ihrem [!DNL Adobe Experience Manager] als [!DNL Cloud Service]-Applikation authentifiziert sind, können Sie Assets auswählen oder verschiedene andere Vorgänge durchführen, um Ihre Assets im Repository zu suchen.

![using-asset-selector](assets/using-asset-selector.png)

* **A**: [Bedienfeld aus-/einblenden](#hide-show-panel)
* **B**: [Repository-Umschalter](#repository-switcher)
* **C**: [Assets](#repository)
* **D**: [Filter](#filters)
* **E**: [Suchleiste](#search-bar)
* **F**: [Sortierung](#sorting)
* **G**: [Sortierung nach auf- oder absteigender Reihenfolge](#sorting)
* **H**: [Ansicht](#types-of-view)

### Bedienfeld aus-/einblenden {#hide-show-panel}

Um Ordner im linken Navigationsbereich auszublenden, klicken Sie auf das Symbol **[!UICONTROL Ordner ausblenden]**. Um die Änderungen rückgängig zu machen, klicken Sie erneut auf das Symbol **[!UICONTROL Ordner ausblenden]**.

### Repository-Umschalter {#repository-switcher}

Mit dem Asset-Selektor können Sie auch Repositorys für die Asset-Auswahl wechseln. Sie können das gewünschte Repository aus der Dropdown-Liste im linken Bedienfeld auswählen. Die in der Dropdown-Liste verfügbaren Repository-Optionen basieren auf der `repositoryId`-Eigenschaft, die in der `index.html`-Datei definiert ist. Sie basiert auf der Umgebung der ausgewählten IMS-Organisation, auf die der angemeldete Benutzer zugreifen kann. Nutzerinnen und Nutzer können eine bevorzugte `repositoryID` übergeben. In diesem Fall stoppt der Asset-Selektor das Rendern des Repository-Umschalters und rendert Assets nur aus dem angegebenen Repository.
<!--
It is based on the `imsOrg` that is provided in the application. If you want to see the list of repositories, then `repositoryId` is required to view those specific repositories in your application.
-->

### Assets-Repository

Es handelt sich um eine Sammlung von Asset-Ordnern, mit denen Sie Vorgänge durchführen können.

### Vorkonfigurierte Filter {#filters}

Der Asset-Selektor bietet außerdem vordefinierte Filteroptionen, mit denen Sie Ihre Suchergebnisse verfeinern können. Die folgenden Filter sind verfügbar:

* `File type`: umfasst Ordner, Dateien, Bilder, Dokumente oder Videos
* `MIME type`: umfasst JPG, GIF, PPTX, PNG, MP4, DOCX, TIFF, PDF, XLSX
* `Image Size`: umfasst minimale/maximale Breite, minimale/maximale Höhe des Bildes

  ![rail-view-example](assets/filters-asset-selector.png)

### Benutzerdefinierte Suche

Neben der Volltextsuche ermöglicht der Asset-Selektor die Suche nach Assets innerhalb von Dateien mithilfe einer benutzerdefinierten Suche. Sie können benutzerdefinierte Suchfilter sowohl im Modal- als auch im Leistenansichtsmodus verwenden.

![custom-search](assets/custom-search1.png)

Sie können auch einen Standardsuchfilter erstellen, um die häufig gesuchten Felder zu speichern und sie später zu verwenden. Um eine benutzerdefinierte Suche für Ihre Assets zu erstellen, können Sie die `filterSchema`-Eigenschaft verwenden.

### Suchleiste {#search-bar}

Mit dem Asset-Selektor können Sie eine Volltextsuche nach Assets im ausgewählten Repository durchführen. Wenn Sie zum Beispiel den Suchbegriff `wave` in die Suchleiste eingeben, werden alle Assets angezeigt, die den Suchbegriff `wave` in einer der Metadateneigenschaften enthalten.

### Sortierung {#sorting}

Sie können Assets im Asset-Selektor nach Namen, Abmessungen oder Größe eines Assets sortieren. Sie können die Assets auch in auf- oder absteigender Reihenfolge sortieren.

### Ansichtstypen {#types-of-view}

Mit dem Asset-Selektor können Sie das Asset in vier verschiedenen Ansichten anzeigen:

* **![Listenansicht](assets/do-not-localize/list-view.png) [!UICONTROL Listenansicht]**: Die Listenansicht zeigt scrollbare Dateien und Ordner in einer Spalte an.
* **![Rasteransicht](assets/do-not-localize/grid-view.png) [!UICONTROL Rasteransicht]**: Die Rasteransicht zeigt scrollbare Dateien und Ordner in einem Raster aus Zeilen und Spalten an.
* **![Galerieansicht](assets/do-not-localize/gallery-view.png) [!UICONTROL Galerieansicht]**: Die Galerie-Ansicht zeigt Dateien oder Ordner in einer zentrierten horizontalen Liste an.
* **![Wasserfallansicht](assets/do-not-localize/waterfall-view.png) [!UICONTROL Wasserfallansicht]**: Die Wasserfallansicht zeigt Dateien oder Ordner in Form einer Brücke an.

<!--
### Modes to view Asset Selector

Asset Selector supports two types of out of the box views:

**  Modal view or Inline view:** The modal view or inline view is the default view of Asset Selector that represents Assets folders in the front area. The modal view allows users to view assets in a full screen to ease the selection of multiple assets for import. Use `<AssetSelector rail={false}>` to enable modal view.

    ![modal-view](assets/modal-view.png)

**  Rail view:** The rail view represents Assets folders in a left panel. The drag and drop of assets can be performed in this view. Use `<AssetSelector rail={true}>` to enable rail view.

    ![rail-view](assets/rail-view.png)
-->
<!--

### Application Integration

Asset Selector is flexible and can be integrated within your existing [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application. It is accessible and localized to add, search, and select assets in your application. With Asset Selector you can:
*   **Configure** You can configure the files/folders that you want to show at the upfront. The assets that are chosen to view can be of any supported formats, for example, JPEG. It lets you control the display of various text or symbols as per your choice.
*   **Perfect fit** Asset selector easily fits in your existing [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application and choose the way you want to view. The mode of view can be inline, rail, or modal view.
*   **Accessible** With Asset Selector, you can reach the desired asset in an easy manner.
*   **Localize** Assets can be availed for the various locales available as per Adobe's localization standards.
-->
<!--

### Support for multiple instances

The micro front-end design supports the display of multiple instances of Asset Selector on a single screen.

![multiple-instance](assets/multiple-instance.png)
-->

<!--

### Controlled selection with multi-select

You can make default multi-selection of assets by specifying the assets to the component using `selectedAssets` property. You should specify an array of asset IDs. For example, `[{id: 'urn:234}, {id: 'urn:555'}].`
-->
<!--

### Action buttons

When you customize your application with Asset Selector based on ReactJS, you are provided with the following action buttons to perform various actions:
*   **Open in media library** Lets you open the asset in media library.
*   **Upload** Lets you upload an asset directly.
*   **Download** Downloads the asset in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
-->
<!--

### Status of an asset

Asset Selector lets you know the status of your uploaded assets. The status can be `Approved`, `Rejected`, or `Expired` of the asset. 
-->
<!--

### Localization

The integration of Asset Selector with [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] allows localized content appear in your application.
-->



<!--Best Practice-->
<!--
+++**Control default selection of the filter**
You can make the selection of filter default by implementing the following code snippet:

```
"defaultValue": [
    "image/*",
    "application/*"
],

{
    "label": "Documents",
    "value": "application/*"
}
```

+++
-->
