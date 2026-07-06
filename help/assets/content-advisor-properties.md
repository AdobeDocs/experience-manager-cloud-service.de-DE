---
title: Eigenschaften von Content Advisor
description: Verwenden Sie Eigenschaften, um anzupassen, wie der Content Advisor gerendert wird, wenn Sie ihn in Ihr Programm integrieren.
role: Admin, User
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
exl-id: cd5ec1de-36b0-48a5-95c9-9bd22fac9719
source-git-commit: 230ca753bd5f3d5b26b30a962a526dc0edfc9bd4
workflow-type: tm+mt
source-wordcount: '2549'
ht-degree: 69%

---

# Installation und Eigenschaften von Content Advisor {#content-advisor-installation-properties}

Content Advisor ist auch für die Integration mit Anwendungen anderer Anbieter als Adobe verfügbar, wodurch die intelligente Asset-Erkennung über Adobe-Anwendungen hinaus erweitert werden kann. Derselbe umfangreiche Funktionssatz, einschließlich KI-gestützter Suche, kontextabhängiger Empfehlungen, kurzbasierter Erkennung in Campaign, Zugriff auf Dynamic Media-Ausgabedarstellungen, Erkennung von Inhaltsfragmenten, Filtern und Asset-Metadaten, wird in Integrationen von Drittanbietern unterstützt.

## Voraussetzungen{#prereqs}

Sie müssen die folgenden Kommunikationsmethoden sicherstellen:

* Die Host-Anwendung wird unter HTTPS ausgeführt.
* Sie können die Anwendung nicht auf `localhost` ausführen. Wenn Sie Content Advisor auf Ihrem lokalen Computer integrieren möchten, müssen Sie eine benutzerdefinierte Domain erstellen, z. B. `[https://<your_campany>.localhost.com:<port_number>]`, und diese benutzerdefinierte Domain dem `redirectUrl list` hinzufügen.
* Sie können die Client-ID konfigurieren und sie zur AEM Cloud Service-Umgebungsvariablen mit der entsprechenden `imsClientId` hinzufügen.
<!--
* You can configure and add `ADOBE_PROVIDED_CLIENT_ID` into the AEM Cloud Service environment variable with the respective `imsClientId`.
![Asset Selector IMS Client id environment](assets/asset-selector-ims-client-id-env.png)
-->
* Die Liste der IMS-Bereiche muss in der Umgebungskonfiguration definiert werden.
* Die URL der Anwendung befindet sich in der Zulassungsliste der Umleitungs-URLs des IMS-Clients.
* Der IMS-Anmeldefluss wird mithilfe eines Popup-Fensters im Webbrowser konfiguriert und gerendert. Daher sollten Popup-Fenster im Ziel-Browser aktiviert oder zugelassen werden.

Verwenden Sie die oben genannten Voraussetzungen, wenn Sie den IMS-Authentifizierungs-Workflow von Content Advisor benötigen. Wenn Sie bereits mit dem IMS-Workflow authentifiziert sind, können Sie stattdessen die IMS-Informationen hinzufügen.

>[!IMPORTANT]
>
> Dieses Repository dient als zusätzliche Dokumentation, in der die verfügbaren APIs und Nutzungsbeispiele für die Integration von Content Advisor beschrieben werden. Bevor Sie versuchen, Content Advisor zu installieren oder zu verwenden, stellen Sie sicher, dass Ihrem Unternehmen der Zugriff auf Content Advisor als Teil des Experience Manager Assets as a Cloud Service-Profils gewährt wurde. Wenn diese Komponenten noch nicht bereitgestellt wurden, können Sie sie weder integrieren noch verwenden. Um die Bereitstellung anzufordern, sollten Ihre Programm-Admins ein Support-Ticket erstellen, das von der Admin Console als P2 gekennzeichnet ist, und die folgenden Informationen einschließen:
>
>* Domain-Namen, auf denen die integrierende Anwendung gehostet wird.
>* Nach der Bereitstellung erhält Ihr Unternehmen `imsClientId`, `imsScope` und eine `redirectUrl`, die den angeforderten Umgebungen entspricht, die für die Konfiguration von Content Advisor erforderlich sind. Ohne diese gültigen Eigenschaften können Sie die Installationsschritte nicht ausführen.

## Installation {#content-advisor-installation}

Der Inhaltsratgeber ist sowohl über die ESM CDN-Version (z. B. [esm.sh](https://esm.sh/)/[skypack](https://www.skypack.dev/)) als auch über die [UMD](https://github.com/umdjs/umd)-Version verfügbar.

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

## Eigenschaften von Content Advisor {#content-advisor-propertiess}

Mit den Eigenschaften von Content Advisor können Sie anpassen, wie der Content Advisor gerendert wird. In der folgenden Tabelle sind die Eigenschaften aufgeführt, mit denen Sie Content Advisor anpassen und verwenden können.

| Eigenschaft | Typ | Erforderlich | Standard | Beschreibung |
|---|---|---|---|---|
| *Leiste* | Boolesch | Nein | False | Wenn als `true` markiert, wird der Inhaltsratgeber in der linken Leistenansicht gerendert. Wenn er als `false` markiert ist, wird der Content Advisor in der modalen Ansicht gerendert. |
| *imsOrg* | Zeichenfolge | Ja | | Die Adobe Identity Management System (IMS)-ID, die bei der Bereitstellung von [!DNL Adobe Experience Manager] als [!DNL Cloud Service] für Ihre Organisation zugewiesen wird. Der `imsOrg`-Schlüssel ist erforderlich, damit authentifiziert wird, ob sich die Organisation, auf die Sie zugreifen, unter Adobe IMS befindet oder nicht. |
| *imsToken* | Zeichenfolge | Nein | | Für die Authentifizierung verwendeter IMS-Bearer-Token. Das `imsToken` ist erforderlich, wenn Sie eine [!DNL Adobe]-Anwendung für die Integration verwenden. |
| *apiKey* | Zeichenfolge | Nein | | API-Schlüssel, der für den Zugriff auf den AEM Discovery-Dienst verwendet wird. Der `apiKey` ist erforderlich, wenn Sie eine Integration mit einer [!DNL Adobe]-Anwendung verwenden. |
| *externalBrief* | Zeichenfolge | Nein | | Ermöglicht den Upload eines Kampagnenübersichtsdokuments zur Ermittlung relevanter Assets, ohne dass Suchbegriffe manuell eingegeben werden müssen. Der Content Advisor analysiert die Informationen in der Kampagnenbeschreibung, um die Kampagnenzielsetzung zu verstehen, und empfiehlt relevante Assets, die in AEM Assets verfügbar sind. |
| *filterSchema* | Array | Nein | | Modell, das zum Konfigurieren von Filtereigenschaften verwendet wird. Dies ist nützlich, wenn Sie bestimmte Filteroptionen in Content Advisor einschränken möchten. |
| *filterFormProps* | Objekt | Nein | | Geben Sie die Filtereigenschaften an, die Sie zur Verfeinerung Ihrer Suche verwenden müssen. Beispiel: MIME-Typ JPG, PNG, GIF. |
| *selectedAssets* | Array `<Object>` | Nein |                 | Die ausgewählte Assets angeben, wenn der Content Advisor gerendert wird. Es ist ein Array von Objekten erforderlich, das eine ID-Eigenschaft der Assets enthält. Zum Beispiel: `[{id: 'urn:234}, {id: 'urn:555'}]` Ein Asset muss im aktuellen Verzeichnis verfügbar sein. Wenn Sie ein anderes Verzeichnis verwenden müssen, geben Sie auch einen Wert für die Eigenschaft `path` an. |
| *acvConfig* | Objekt | Nein | | Asset Collection View-Eigenschaft, die ein Objekt enthält, das eine benutzerdefinierte Konfiguration enthält, um Standardwerte zu überschreiben. Diese Eigenschaft wird auch mit der Eigenschaft `rail` verwendet, um die Leistenansicht des Asset-Wählers zu aktivieren. |
| *i18nSymbols* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | Nein |                 | Wenn die vorkonfigurierten Übersetzungen für die Bedürfnisse Ihrer Anwendung unzureichend sind, können Sie eine Schnittstelle bereitstellen, über die Sie Ihre eigenen lokalisierten Werte durch die Eigenschaft `i18nSymbols` übergeben können. Wenn Sie über diese Schnittstelle einen Wert übergeben, werden die bereitgestellten Standardübersetzungen überschrieben und stattdessen Ihre eigenen verwendet. Um die Überschreibung vorzunehmen, müssen Sie ein gültiges [Message Descriptor](https://formatjs.io/docs/react-intl/api/#message-descriptor)-Objekt an den Schlüssel von `i18nSymbols` übergeben, den Sie überschreiben möchten. |
| *intl* | Objekt | Nein | | Content Advisor bietet standardmäßige OOTB-Übersetzungen. Sie können die Übersetzungssprache auswählen, indem Sie eine gültige Gebietsschema-Zeichenfolge durch die `intl.locale`-Eigenschaft bereitstellen. Beispiel: `intl={{ locale: "es-es" }}` </br></br> Die unterstützten Gebietsschema-Zeichenfolgen folgen den [ISO 639 - Codes](https://www.iso.org/iso-639-language-codes.html) für die Darstellung von Namen von Sprachen. </br></br> Liste der unterstützten Gebietsschemata: Englisch: „en-us“ (Standard), Spanisch: „es-es“, Deutsch: „de-de“, Französisch: „fr-fr“, Italienisch: „it-it“, Japanisch: „ja-jp“, Koreanisch: „ko-kr“, Portugiesisch: „pt-br“, Chinesisch (Vereinfacht): „zh-cn“, Chinesisch (Taiwan): „zh-tw“ |
| *repositoryId* | Zeichenfolge | Nein | &#39;&#39; | Repository, aus dem der Content Advisor den Inhalt lädt. |
| *additionalAemSolutions* | `Array<string>` | Nein | [ ] | Damit können Sie eine Liste mit zusätzlichen AEM-Repositorys hinzufügen. Wenn in dieser Eigenschaft keine Informationen bereitgestellt werden, werden nur die Medienbibliothek oder AEM Assets-Repositorys berücksichtigt. |
| *hideTreeNav* | Boolesch | Nein |  | Gibt an, ob die Navigationsseitenleiste der Asset-Baumstruktur ein- oder ausgeblendet werden soll. Sie wird nur in der modalen Ansicht verwendet und daher gibt es keine Auswirkung dieser Eigenschaft in der Leistenansicht. |
| *onDrop* | Funktion | Nein | | Die Funktion „Beim Ablegen“ wird verwendet, um ein Asset per Drag-and-Drop auf einen festgelegten Ablagebereich zu ziehen. Es ermöglicht interaktive Benutzeroberflächen, über die Assets nahtlos verschoben und verarbeitet werden können. |
| *dropOptions* | `{allowList?: Object}` | Nein | | Konfiguriert Ablagefunktionen mithilfe der „Zulassungsliste“. |
| *theme* | Zeichenfolge | Nein | Standard | Wenden Sie zwischen `default` und `express` ein Design auf die Content Advisor-Anwendung an. Zudem wird `@react-spectrum/theme-express` unterstützt. |
| *handleSelection* | Funktion | Nein | | Wird mit einem Array von Asset-Elementen aufgerufen, wenn Assets ausgewählt sind und die Schaltfläche `Select` im Modal angeklickt wird. Diese Funktion wird nur in der modalen Ansicht aufgerufen. Verwenden Sie für die Leistenansicht die Funktionen `handleAssetSelection` oder `onDrop`. Zum Beispiel: <pre>handleSelection=(assets: Asset[])=> {...}</pre> Weitere Informationen finden Sie unter [Auswahl von Assets](/help/assets/content-advisor-customization.md#selection-of-assets). |
| *handleAssetSelection* | Funktion | Nein | | Wird mit einem Array von Elementen aufgerufen, während die Assets ausgewählt oder deren Auswahl aufgehoben wird. Dies ist nützlich, wenn Sie auf Assets warten möchten, während die Benutzenden sie auswählen. Zum Beispiel: <pre>handleAssetSelection=(assets: Asset[])=> {...}</pre> Weitere Informationen finden Sie unter [Auswahl von Assets](/help/assets/content-advisor-customization.md#selection-of-assets). |
| *onClose* | Funktion | Nein | | Wird aufgerufen, wenn die `Close`-Schaltfläche in der modalen Ansicht gedrückt wird. Dies wird nur in der `modal`-Ansicht aufgerufen und in der `rail`-Ansicht nicht beachtet. |
| *onFilterSubmit* | Funktion | Nein | | Wird mit Filterelementen aufgerufen, wenn Benutzende andere Filterkriterien ändern. |
| *selectionType* | Zeichenfolge | Nein | Einzeln | Konfiguration für `single`- oder `multiple`-Auswahl von Assets auf einmal. |
| *dragOptions.allowList* | Boolesch | Nein | | Die Eigenschaft wird verwendet, um das Ziehen von nicht auswählbaren Assets zuzulassen oder zu verweigern. Siehe [dragOptions-Eigenschaft](/help/assets/content-advisor-customization.md#drag-options-property). |
| *aemTierType* | Zeichenfolge | Nein |  | Damit können Sie auswählen, ob Assets aus der Bereitstellungsebene, der Autorenebene oder aus beiden angezeigt werden sollen. <br><br> Syntax: `aemTierType: "author"  "delivery"` <br><br> Wenn beispielsweise beide `["author","delivery"]` verwendet werden, zeigt der Repository-Umschalter Optionen für Autor und Versand an. |
| *handleNavigateToAsset* | Funktion | Nein | | Es handelt sich um eine Rückruffunktion, die die Auswahl eines Assets verarbeitet. |
| *noWrap* | Boolesch | Nein | | Die *noWrap*-Eigenschaft verhindert, dass der Content Advisor in einem Dialogfeld umschlossen wird. Wenn diese Eigenschaft nicht erwähnt wird, wird standardmäßig die *Dialogfeldansicht* gerendert. |
| *dialogSize* | S, M, L, Vollbild, Vollbildübernahme | Zeichenfolge | Optional | Sie können das Layout kontrollieren, indem Sie dessen Größe mithilfe der angegebenen Optionen festlegen. |
| *colorScheme* | Zeichenfolge (hell, dunkel) | Nein | | Diese Eigenschaft wird verwendet, um das Design einer Content Advisor-Anwendung festzulegen. Sie können zwischen einem hellen und dunklen Design wählen. |
| *filterRepoList* | Funktion | Nein | | Eine Funktion, die die Repository-Liste erhält und eine gefilterte Liste zurückgibt. |
| *expiryOptions* | Funktion | | | Sie können eine der beiden folgenden Eigenschaften verwenden: **getExpiryStatus**, was den Status eines abgelaufenen Assets angibt. Die Funktion gibt je nach dem Ablaufdatum eines von Ihnen angegebenen Assets `EXPIRED`, `EXPIRING_SOON` oder `NOT_EXPIRED` zurück. Siehe [Anpassen abgelaufener Assets](/help/assets/content-advisor-customization.md#customize-expired-assets). Darüber hinaus können Sie die Option **allowSelectionAndDrag** verwenden, in der der Wert der Funktion entweder `true` oder `false` sein kann. Wenn der Wert auf `false` festgelegt ist, kann das abgelaufene Asset weder ausgewählt noch auf die Arbeitsfläche gezogen werden. |
| *showToast* | | Nein | | Dadurch kann Content Advisor eine benutzerdefinierte Popup-Meldung für das abgelaufene Asset anzeigen. |
| *uploadConfig* | Objekt | | | Es handelt sich um ein Objekt, das benutzerdefinierte Konfigurationen für den Upload enthält. Informationen zur Verwendung finden Sie unter [Upload-Konfiguration](#content-advisor-customization.md#upload-config). |
| *uploadConfig* > *metadataSchema* | Array | Nein | | Diese Eigenschaft ist mit der Eigenschaft `uploadConfig` verschachtelt. Fügen Sie ein Array von Feldern hinzu, die Sie bereitstellen, um Metadaten von der Benutzerin oder dem Benutzer zu erfassen. Mit dieser Eigenschaft können Sie auch versteckte Metadaten verwenden, die einem Asset automatisch zugewiesen werden, für die Benutzerin bzw. den Benutzer jedoch nicht sichtbar sind. |
| *uploadConfig* > *onMetadataFormChange* | Rückruffunktion | Nein | | Diese Eigenschaft ist mit der Eigenschaft `uploadConfig` verschachtelt. Sie besteht aus `property` und `value`. `Property` entspricht der *mapToProperty* des Felds, das vom *metadataSchema* übergeben wird, dessen Wert aktualisiert wird. Dahingegen entspricht`value` dem neuen Wert und wird als Eingabe bereitgestellt. |
| *uploadConfig* > *targetUploadPath* | Zeichenfolge |  | `"/content/dam"` | Diese Eigenschaft ist mit der Eigenschaft `uploadConfig` verschachtelt. Der Ziel-Upload-Pfad für die Dateien, der standardmäßig auf den Stamm des Assets-Repositorys festgelegt ist. |
| *uploadConfig* > *hideUploadButton* | Boolesch | | False | Gibt an, ob die interne Schaltfläche „Hochladen“ ausgeblendet werden soll oder nicht. Diese Eigenschaft ist mit der Eigenschaft `uploadConfig` verschachtelt. |
| *uploadConfig* > *onUploadStart* | Funktion | Nein |  | Es handelt sich dabei um eine Rückruffunktion, mit der die Upload-Quelle zwischen Dropbox, OneDrive oder lokalem Verzeichnis weitergegeben wird. Die Syntax lautet `(uploadInfo: UploadInfo) => void`. Diese Eigenschaft ist mit der Eigenschaft `uploadConfig` verschachtelt. |
| *uploadConfig* > *importSettings* | Funktion | | | Ermöglicht die Unterstützung des Imports von Assets aus Drittanbieterquellen. `sourceTypes` verwendet ein Array der Importquellen, die Sie aktivieren möchten. Die unterstützten Quellen sind Onedrive und Dropbox. Die Syntax lautet `{ sourceTypes?: ImportSourceType[]; apiKey?: string; }`. Darüber hinaus ist diese Eigenschaft mit der Eigenschaft `uploadConfig` verschachtelt. |
| *uploadConfig* > *onUploadComplete* | Funktion | Nein | | Es handelt sich dabei um eine Rückruffunktion, mit der der Status des Uploads („Erfolgreich“, „Fehlgeschlagen“ oder „Duplikat“) weitergegeben wird. Die Syntax lautet `(uploadStats: UploadStats) => void`. Darüber hinaus ist diese Eigenschaft mit der Eigenschaft `uploadConfig` verschachtelt. |
| *uploadConfig* > *onFilesChange* | Funktion | Nein | | Diese Eigenschaft ist mit der Eigenschaft `uploadConfig` verschachtelt. Es handelt sich dabei um eine Rückruffunktion, mit der das Verhalten des Uploads angezeigt wird, wenn eine Datei geändert wird. Sie gibt das neue Array der Dateien, die zum Hochladen ausstehen, und den Quelltyp des Uploads weiter. Der Quelltyp kann im Fehlerfall null sein. Die Syntax lautet `(newFiles: File[], uploadType: UploadType) => void` |
| *uploadConfig* > *uploadPlaceholder* | Zeichenfolge | | | Es handelt sich dabei um ein Platzhalterbild, das das Metadatenformular ersetzt, wenn der Upload des Assets initiiert wird. Die Syntax ist `{ href: string; alt: string; }`. Darüber hinaus ist diese Eigenschaft mit der Eigenschaft `uploadConfig` verschachtelt. |
| *featureSet* | Array | Zeichenfolge | | Die `featureSet:[ ]`-Eigenschaft wird verwendet, um eine bestimmte Funktion in der Content Advisor-Anwendung zu aktivieren oder zu deaktivieren. Um die Komponente oder eine Funktion zu aktivieren, können Sie einen Zeichenfolgenwert im Array übergeben oder das Array leer lassen, um hinzugefügte Funktionen zu deaktivieren, und nur die Basisfunktion zu nutzen. Wenn Sie z. B. die Upload-Funktion im Content Advisor aktivieren möchten, verwenden Sie die `featureSet:["upload"]`. Ebenso können Sie `featureSet:["content-fragments"]` verwenden, um Inhaltsfragmente im Inhaltsratgeber zu aktivieren. Um mehrere Funktionen zusammen zu verwenden, lautet die Syntax featureSet:[„upload“, „content-fragments“]. |

<!--
| *selectedRendition* | Object | | | This property allows users to define and control which renditions of an asset are displayed when the panel is accessed. This customization enhances user experience by filtering out unnecessary renditions and showcasing only the most relevant renditions. For example, `CopyUrlHref` allows you to use Dynamic Media renditions in your Asset Selector application (delivery URL). |
| *featureSet* | Array | String | | The `featureSet:[ ]` property is used to enable or disable a particular functionaly in the Asset Selector application. To enable the component or a feature, you can pass a string value in the array or leave the array empty to disable that component. For example, you want to enable upload functionality in the Asset Selector, use the syntax `featureSet:[0:"upload"]`. Similarly, you can use `featureSet:[0:"collections"]` to enable collections in the Asset Selector. Addidionally, use `featureSet:[0:"detail-panel"]` to enable [details panel](overview-asset-selector.md#asset-details-and-metadata) of an asset. Also, `featureSet:[0:"dm-renditions"]` to show Dynamic Media renditions of an asset.|
| *rootPath* | String | No | /content/dam/ | Folder path from which Asset Selector displays your assets. `rootPath` can also be used in the form of encapsulation. For example, given the following path, `/content/dam/marketing/subfolder/`, Asset Selector does not allow you to traverse through any parent folder, but only displays the children folders. |
| *path* | String | No | | Path that is used to navigate to a specific directory of assets when the Asset Selector is rendered. |
| *expirationDate* | Function | No | | This function is used to set the usability period of an asset. |
| *disableDefaultBehaviour* | Boolean | No | False | It is a function that is used to enable or disable the selection of an expired asset. You can customize the default behavior of an asset that is set to expire. See [customize expired assets](/help/assets/asset-selector-customization.md#customize-expired-assets). |
-->

### ImsAuthProps {#ims-auth-props}

Die `ImsAuthProps` definieren die Authentifizierungsinformationen und den Fluss, den der Content Advisor zum Abrufen eines `imsToken` verwendet. Durch Festlegen dieser Eigenschaften können Sie steuern, wie sich der Authentifizierungsfluss verhält, und Listener für verschiedene Authentifizierungsereignisse registrieren.

| Eigenschaftsname | Beschreibung |
|---|---|
| `imsClientId` | Ein Zeichenfolgenwert, der die für Authentifizierungszwecke verwendete IMS-Client-ID darstellt. Dieser Wert wird von Adobe bereitgestellt und ist spezifisch für Ihre Adobe AEM CS-Organisation. |
| `imsScope` | Beschreibt die bei der Authentifizierung verwendeten Bereiche. Die Bereiche bestimmen den Umfang des Zugriffs, den die Anwendung auf die Ressourcen Ihrer Organisation hat. Mehrere Bereiche werden durch Kommas voneinander getrennt. |
| `redirectUrl` | Stellt die URL dar, an die Benutzende nach der Authentifizierung weitergeleitet werden. Dieser Wert wird normalerweise auf die aktuelle URL der Anwendung gesetzt. Wenn keine `redirectUrl` bereitgestellt wird, verwendet `ImsAuthService` die zum Registrieren der `imsClientId` verwendete redirectUrl |
| `modalMode` | Ein boolescher Wert, der angibt, ob der Authentifizierungsfluss in einem Modal (Popup-Fenster) angezeigt werden soll oder nicht. Wenn `true` festgelegt ist, wird der Authentifizierungsfluss in einem Popup-Fenster angezeigt. Wenn `false` festgelegt ist, wird der Authentifizierungsfluss bei vollständigem Neuladen der Seite angezeigt. Hinweis::_Für ein besseres Anwendererlebnis können Sie diesen Wert dynamisch steuern, wenn Popup-Fenster des Browsers deaktiviert sind. |
| `onImsServiceInitialized` | Eine Rückruffunktion, die aufgerufen wird, wenn der Adobe IMS-Authentifizierungsdienst initialisiert wird. Diese Funktion akzeptiert einen Parameter namens `service`, ein Objekt, das den Adobe IMS-Dienst darstellt. Siehe [`ImsAuthService`](#imsauthservice-ims-auth-service) für weitere Informationen. |
| `onAccessTokenReceived` | Eine Rückruffunktion, die aufgerufen wird, wenn ein `imsToken` vom Adobe IMS-Authentifizierungsdienst empfangen wird. Diese Funktion akzeptiert einen Parameter namens `imsToken`, eine Zeichenfolge, die das Zugriffstoken darstellt. |
| `onAccessTokenExpired` | Eine Rückruffunktion, die aufgerufen wird, wenn ein Zugriffstoken abgelaufen ist. Diese Funktion wird normalerweise verwendet, um einen neuen Authentifizierungsfluss auszulösen und so ein neues Zugriffstoken zu erhalten. |
| `onErrorReceived` | Eine Rückruffunktion, die aufgerufen wird, wenn während der Authentifizierung ein Fehler auftritt. Diese Funktion akzeptiert zwei Parameter: den Fehlertyp und die Fehlermeldung. Der Fehlertyp ist eine Zeichenfolge, die den Fehlertyp darstellt, und die Fehlermeldung ist eine Zeichenfolge, die die Fehlermeldung darstellt. |

### ImsAuthService {#ims-auth-service}

`ImsAuthService` Klasse verarbeitet den Authentifizierungsfluss für den Content Advisor. Sie ist für den Erhalt eines `imsToken` über den Adobe IMS-Authentifizierungsdienst verantwortlich. Das `imsToken` wird verwendet, um die Benutzerin oder den Benutzer zu authentifizieren und den Zugriff auf das [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Assets-Repository zu autorisieren. ImsAuthService verwendet die `ImsAuthProps`-Eigenschaften, um den Authentifizierungsfluss zu steuern und Listener für verschiedene Authentifizierungsereignisse zu registrieren. Sie können die praktische [`registerAssetsSelectorsAuthService`](#purejsselectorsregisterassetsselectorsauthservice) verwenden, um die Instanz _ImsAuthService_ beim Inhaltsratgeber zu registrieren. Die folgenden Funktionen sind in der `ImsAuthService`-Klasse verfügbar. Wenn Sie jedoch die Funktion _registerAssetsSelectorsAuthService_ verwenden, müssen Sie diese Funktionen nicht direkt aufrufen.

| Funktionsname | Beschreibung |
|---|---|
| `isSignedInUser` | Bestimmt, ob die Person derzeit beim Dienst angemeldet ist, und gibt entsprechend einen booleschen Wert zurück. |
| `getImsToken` | Ruft das Authentifizierungs-`imsToken` für die derzeit angemeldete Person ab, das zum Authentifizieren von Anforderungen für andere Dienste wie zum Beispiel zum Generieren von Asset-Ausgabedarstellungen verwendet werden kann. |
| `signIn` | Startet den Anmeldeprozess für die Person. Diese Funktion verwendet `ImsAuthProps`, um die Authentifizierung in einem Popup-Fenster oder beim vollständigem Neuladen einer Seite anzuzeigen |
| `signOut` | Meldet die Person vom Dienst ab, macht ihr Authentifizierungs-Token ungültig und fordert sie auf, sich erneut anzumelden, um auf geschützte Ressourcen zuzugreifen. Durch Aufrufen dieser Funktion wird die aktuelle Seite neu geladen. |
| `refreshToken` | Aktualisiert das Authentifizierungs-Token für die derzeit angemeldete Person, verhindert das Ablaufen des Tokens und stellt einen unterbrechungsfreien Zugriff auf geschützte Ressourcen sicher. Gibt ein neues Authentifizierungs-Token zurück, das für nachfolgende Anforderungen verwendet werden kann. |

### contentFragmentSelectorProps {#content-fragment-selector-properties}

Mit `contentFragmentSelectorProps` können Sie konfigurieren, wie der Zugriff auf und die Anzeige von Inhaltsfragmenten im Inhaltsratgeber erfolgt. Durch Aktivierung der Funktion für Inhaltsfragmente im `featureSet` und Bereitstellung der erforderlichen Konfiguration können Sie die Inhaltsfragmentauswahl nahtlos neben Assets integrieren. Dadurch können Benutzende Inhaltsfragmente in derselben einheitlichen Benutzeroberfläche durchsuchen, durchsuchen und auswählen, was eine konsistente Inhaltsauswahl für alle Assets und strukturierten Inhalte gewährleistet.

```
const assetSelectorProps = {
     featureSet: [
       'upload',            /* Include upload or other featureSet values to ensure no missing functionality */
       'content-fragments', /* Content Fragments pill will be shown */
     ],
     contentFragmentSelectorProps: {
       /* Configures the Content Fragments Pill experience */
       /* ...props @aem-sites/content-fragment-selector MFE supports */
    }
}

<AssetSelector {...assetSelectorProps} />
```

In `contentFragmentSelectorProps` können Sie auf jede der verfügbaren Eigenschaften verweisen (Eigenschaften [ Inhaltsfragmentauswahl](/help/headless/content-fragment-selector/properties.md).

Informationen zur Integration von Content Advisor in Angular-, React- und JavaScript-Anwendungen finden Sie unter [ für die Integration von Content Advisor](https://github.com/adobe/aem-assets-selectors-mfe-examples/tree/consolidate-docs-to-experience-league/examples).


**Siehe auch**

* [Assets übersetzen](/help/assets/translate-assets.md)
* [Assets-HTTP-API](/help/assets/mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](/help/assets/file-format-support.md)
* [Suchen von Assets](/help/assets/search-assets.md)
* [Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](/help/assets/asset-reports.md)
* [Metadatenschemata](/help/assets/metadata-schemas.md)
* [Herunterladen von Assets](/help/assets/download-assets-from-aem.md)
* [Verwalten von Metadaten](/help/assets/manage-metadata.md)
* [Verwalten von Dynamic Media-Vorlagen](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Verwalten von Berichten](/help/assets/manage-reports-assets-view.md)
* [Suchfacetten](/help/assets/search-facets.md)
* [Verwalten von Sammlungen](/help/assets/manage-collections.md)
* [Massenimport von Metadaten](/help/assets/metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
