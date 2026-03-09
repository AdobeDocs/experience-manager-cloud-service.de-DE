---
title: Integrieren des Inhaltsfragment-Selektors mit Nicht-Adobe- oder Drittanbieterprogrammen
description: Integrieren Sie den Inhaltsfragment-Selektor in verschiedene Adobe-, Nicht-Adobe- und Drittanbieteranwendungen.
role: Admin, User, Developer
source-git-commit: 3af1a89489af96bf9c9908aea7fb20883956517b
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 17%

---

# Integration in eine Adobe-fremde Anwendung {#integration-with-non-adobe-application}

Adobe Der Inhaltsfragment-Selektor ermöglicht die Integration in verschiedene Programme von Drittanbietern oder anderen Anbietern, damit sie nahtlos zusammenarbeiten können.

## Voraussetzungen {#prerequisites}

Verwenden Sie die folgenden Voraussetzungen, wenn Sie die Inhaltsfragmentauswahl in ein Nicht-Adobe-Programm integrieren:

* [Voraussetzungen](/help/headless/content-fragment-selector/overview.md#prerequisites)
* imsClientId
* imsScope
* redirectURL
* imsOrg
* apikey

Bei der Integration in ein Nicht-Adobe-Programm unterstützt der Inhaltsfragment-Selektor die Authentifizierung für das Adobe Experience Manager (AEM) as a Cloud Service-Repository mithilfe von Identity Management System (IMS)-Eigenschaften wie `imsScope` oder `imsClientID`.

## Konfigurieren des Inhaltsfragment-Selektors für ein Nicht-Adobe-Programm {#configure-content-fragment-selector-for-a-non-adobe-application}

Um den Inhaltsfragmentselektor für eine Nicht-Adobe-Anwendung zu konfigurieren, müssen Sie zunächst ein Support-Ticket für die Bereitstellung erstellen, bevor Sie mit den Integrationsschritten fortfahren.

### Einreichen eines Support-Tickets {#logging-a-support-ticket}

Schritte zum Einreichen eines Support-Tickets über die Admin Console:

1. Fügen Sie **Inhaltsfragmentauswahl mit AEM-Fragmenten** im Titel des Tickets hinzu.

1. Geben Sie in der Beschreibung die folgenden Details an:

   * Experience Manager as a Cloud Service-URL (Programm-ID und Umgebungs-ID).
   * Domain-Namen, auf denen die Nicht-Adobe-Web-Anwendung gehostet wird.

## Integrationsschritte {#integration-steps}

Verwenden Sie die folgende `index.html`-Beispieldatei für die Authentifizierung, wenn Sie den Inhaltsfragment-Selektor in eine Nicht-Adobe-Anwendung integrieren:

* Greifen Sie über das Tag `Script` auf das Paket zur Inhaltsfragmentauswahl zu.

* Definieren Sie die Eigenschaften des IMS-Flusses, z. B. `imsClientId`, `imsScope` und `redirectURL`.

   * Für die Funktion müssen Sie mindestens eine der `imsClientId`- und `imsScope` definieren.
   * Wenn Sie keinen Wert für `redirectURL` definieren, wird die registrierte Umleitungs-URL für die Client-ID verwendet.

* Da im Beispiel kein `imsToken` generiert wurde, verwenden Sie die Funktionen `registerFragmentsSelectorsAuthService` und `renderFragmentSelectorWithAuthFlow` .

   * Verwenden Sie die Funktion `registerFragmentsSelectorsAuthService` vor dem `renderFragmentSelectorWithAuthFlow`, um die `imsToken` mit dem Inhaltsfragment-Selektor zu registrieren.
   * Adobe empfiehlt, `registerFragmentsSelectorsAuthService` aufzurufen, wenn Sie die Komponente instanziieren.

* Definieren Sie die Authentifizierungsfragmente und andere as a Cloud Service-Zugriffseigenschaften im Abschnitt `const props` .
* Die globale Variable `PureJSContentFragmentSelectors` wird verwendet, um die Inhaltsfragmentauswahl im Webbrowser zu rendern.
* Der Inhaltsfragmentselektor wird für das `<div>` Container-Element gerendert. Im Beispiel wird ein Dialogfeld verwendet, um die Inhaltsfragmentauswahl anzuzeigen.

**Beispiel`ìndex.html`**

```html {line-numbers="true"}
<!doctype html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <link rel="icon" type="image/svg+xml" href="/vite.svg" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>testing-cf-mfe-integration-with-3rd-party-app</title>
        <script
            id="content-fragments-selector"
            src="https://experience.adobe.com/solutions/CQ-sites-content-fragment-selector/static-assets/resources/content-fragment-selector.js"
        ></script>
        <script>
            const imsProps = {
                imsClientId: '<IMS_CLIENT_ID>',
                imsScope:
                    'additional_info.projectedProductContext, AdobeID, openid, read_organizations',
                redirectUrl: window.location.href,
                onImsServiceInitialized: (service) => {
                    // invoked when the ims service is initialized and is ready
                    console.log('onImsServiceInitialized', service);
                },
                onAccessTokenReceived: (token) => {
                    console.log('onAccessTokenReceived', token);
                },
                onAccessTokenExpired: () => {
                    console.log('onAccessTokenError');
                    // re-trigger sign-in flow
                },
                onErrorReceived: (type, msg) => {
                    console.log('onErrorReceived', type, msg);
                },
            };

            function load() {
                const registeredTokenService =
                    PureJSContentFragmentSelectors.registerContentFragmentSelectorAuthService(
                        imsProps
                    );
                imsInstance = registeredTokenService;
            }

            // initialize the IMS flow before attempting to render the content fragment selector
            load();

            // function that will render the content fragment selector
            function renderContentFragmentSelectorWithAuthFlow() {
                const contentFragmentSelectorDialog = document.getElementById(
                    'content-fragment-selector-dialog'
                );

                const contentFragmentSelectorProps = {
                    inventoryViewToggleEnabled: true,
                    isOpen: true,
                    noWrap: false,
                    orgId: 'YOUR_ORG_ID@AdobeOrg',
                    // repoId: "author-p12345-e67890.adobeaemcloud.com", // if wanted to restrict to a specific repo
                    runningInUnifiedShell: false,
                    onDismiss: () => contentFragmentSelectorDialog.close(),
                    onSubmit: ({ contentFragments }) => {
                        const selectedContentFragment = contentFragments[0];
                        alert(selectedContentFragment.path);
                    },
                };
                // container element on which you want to render the ContentFragmentSelector component
                const container = document.getElementById('content-fragment-selector');

                /// Use the PureJSContentFragmentSelectors in globals to render the ContentFragmentSelector component
                PureJSContentFragmentSelectors.renderContentFragmentSelectorWithAuthFlow(
                    container,
                    contentFragmentSelectorProps,
                    () => contentFragmentSelectorDialog.showModal()
                );
            }
        </script>
    </head>
    <body>
        <div>
            <button onclick="renderContentFragmentSelectorWithAuthFlow()">
                Content Fragment Selector - Select Content Fragments with Ims Flow
            </button>
        </div>
        <dialog id="content-fragment-selector-dialog">
            <div
                id="content-fragment-selector"
                style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px"
            ></div>
        </dialog>
    </body>
</html>
```

## Zugriff auf das Bereitstellungs-Repository nicht möglich {#unable-to-access-delivery-repository}

Wenn Sie den Inhaltsfragmentselektor mithilfe des Workflows Anmelden integriert haben, aber immer noch nicht auf das Versand-Repository zugreifen können, stellen Sie sicher, dass Browser-Cookies gesäubert wurden.

Andernfalls wird möglicherweise der `invalid_credentials All session cookies are empty` in der Konsole angezeigt.
