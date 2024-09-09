---
title: Asset-Selektor für [!DNL Adobe Experience Manager] als ein [!DNL Cloud Service]
description: Integrieren Sie die Asset-Auswahl in verschiedene Adobe-, Nicht-Adobe- und Drittanbieter-Anwendungen.
role: Admin, User
exl-id: 55848de0-aff2-42a0-b959-c771235d9425
source-git-commit: 575980320c1dbd32f799bf9c2fddf3d6773c838a
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 73%

---

# Integration mit einer Nicht-Adobe-Anwendung {#integrate-asset-selector-non-adobe-app}

Mit der Asset-Auswahl können Sie die Integration mit verschiedenen Anwendungen, die keine Adobe sind, oder Drittanbietern durchführen, um eine nahtlose Zusammenarbeit zu ermöglichen.

## Voraussetzungen {#prereqs-non-adobe-app}

Wenden Sie die folgenden Voraussetzungen an, wenn Sie den Asset-Wähler mit einer Nicht-Adobe-Anwendung integrieren:

* [Kommunikationsmethoden](/help/assets/overview-asset-selector.md#prereqs)
* imsClientId
* imsScope
* redirectURL
* imsOrg
* apikey

Der Asset-Wähler unterstützt die Authentifizierung für das [!DNL Experience Manager Assets]-Repository mit Eigenschaften des Identity Management System (IMS), z. B. `imsScope` oder `imsClientID`, wenn Sie es mit einer Nicht-Adobe-Anwendung integrieren.

## Konfigurieren des Asset-Selektors für eine Nicht-Adobe-Anwendung {#configure-non-adobe-app}

Um die Asset-Auswahl für eine Nicht-Adobe-Anwendung zu konfigurieren, müssen Sie zunächst ein Support-Ticket für die Bereitstellung und dann die Integrationsschritte protokollieren.

### Support-Ticket anmelden {#log-a-support-ticket}

Schritte zum Einreichen eines Support-Tickets über die Admin Console:

1. Fügen Sie **Asset-Wähler mit AEM Assets** zum Titel des Tickets hinzu.

1. Geben Sie in der Beschreibung die folgenden Details an:

   * [!DNL Experience Manager Assets] as a [!DNL Cloud Service]-URL (Programm-ID und Umgebungs-ID).
   * Domain-Namen, auf denen die Nicht-Adobe-Web-Anwendung gehostet wird.

## Integrationsschritte {#non-adobe-app-integration-steps}

Verwenden Sie diese Beispieldatei `index.html` zur Authentifizierung bei der Integration des Asset-Selektors in eine Nicht-Adobe-Anwendung.

Greifen Sie mithilfe des `Script`-Tags auf das Asset-Wählerpaket zu, wie in *Zeile 9* bis *Zeile 11* der `index.html`-Beispieldatei dargestellt.

In *Zeile 14* bis *Zeile 38* des Beispiels werden die Eigenschaften des IMS-Flusses beschrieben, z. B. `imsClientId`, `imsScope` und `redirectURL`. Die Funktion erfordert, dass Sie mindestens eine der Eigenschaften `imsClientId` und `imsScope` definieren. Wenn Sie keinen Wert für `redirectURL` definieren, wird die registrierte Umleitungs-URL für die Client-ID verwendet.

Da Sie kein `imsToken` generiert haben, verwenden Sie die Funktionen `registerAssetsSelectorsAuthService` und `renderAssetSelectorWithAuthFlow`, wie in den Zeilen 40 bis 50 der `index.html`-Beispieldatei dargestellt. Verwenden Sie die Funktion `registerAssetsSelectorsAuthService` vor `renderAssetSelectorWithAuthFlow`, um das `imsToken` mit dem Asset-Wähler zu registrieren. [!DNL Adobe] empfiehlt, `registerAssetsSelectorsAuthService` aufzurufen, wenn Sie die Komponente instanziieren.

Definieren Sie die Authentifizierung und andere Zugriffseigenschaften für Assets as a Cloud Service im Abschnitt `const props`, wie in *Zeile 54* bis *Zeile 60* der `index.html`-Beispieldatei dargestellt.

Die globale Variable `PureJSSelectors`, erwähnt in *Zeile 65*, wird zum Rendern des Asset-Wählers im Webbrowser verwendet.

Der Asset-Wähler wird im Container-Element `<div>` gerendert, wie in *Zeile 74* bis *Zeile 81* angegeben. Das Beispiel verwendet ein Dialogfeld zum Anzeigen des Asset-Wählers.

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

## Zugriff auf Bereitstellungs-Repository nicht möglich {#unable-to-access-delivery-repository}

>[!TIP]
>
>Wenn Sie den Asset-Wähler mithilfe des Workflows zum Registrieren und Anmelden integriert haben, aber trotzdem nicht auf das Bereitstellungs-Repository zugreifen können, stellen Sie sicher, dass die Browser-Cookies bereinigt wurden. Andernfalls tritt der Fehler `invalid_credentials All session cookies are empty` in der Konsole auf.

>[!MORELIKETHIS]
>
>* [Integrieren der Asset-Auswahl in verschiedene Anwendungen](/help/assets/integrate-asset-selector.md)
>* [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md)
>* [Integrieren der Asset-Auswahl in Dynamic Media mit OpenAPI-Funktionen](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
>* [Asset-Selektor-Anpassungen](/help/assets/asset-selector-customization.md)
