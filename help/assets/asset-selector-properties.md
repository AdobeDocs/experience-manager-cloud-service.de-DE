---
title: Asset-Selektor für [!DNL Adobe Experience Manager] als ein [!DNL Cloud Service]
description: Verwenden Sie den Asset-Selektor, um die Metadaten und Ausgabeformate von Assets in Ihrer Applikation zu suchen, zu finden und abzurufen.
role: Admin, User
exl-id: cd5ec1de-36b0-48a5-95c9-9bd22fac9719
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '1295'
ht-degree: 72%

---

# Eigenschaften des Asset-Wählers {#asset-selector-properties}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets-Entwicklerdokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Sie können die Asset-Wähler-Eigenschaften verwenden, um die Darstellung des Asset-Wählers anzupassen. In der folgenden Tabelle sind die Eigenschaften aufgeführt, mit denen Sie den Asset-Wähler anpassen und verwenden können.

| Eigenschaft | Typ | Erforderlich | Standard | Beschreibung |
|---|---|---|---|---|
| *Leiste* | Boolesch | Nein | False | Wenn als `true` markiert, wird der Asset-Wähler in der linken Leistenansicht gerendert. Wenn als `false` markiert, wird der Asset-Wähler in der modalen Ansicht gerendert. |
| *imsOrg* | Zeichenfolge | Ja | | Die Adobe Identity Management System (IMS)-ID, die bei der Bereitstellung von [!DNL Adobe Experience Manager] als [!DNL Cloud Service] für Ihre Organisation zugewiesen wird. Der `imsOrg`-Schlüssel ist erforderlich, damit authentifiziert wird, ob sich die Organisation, auf die Sie zugreifen, unter Adobe IMS befindet oder nicht. |
| *imsToken* | Zeichenfolge | Nein | | Für die Authentifizierung verwendeter IMS-Bearer-Token. Das `imsToken` ist erforderlich, wenn Sie eine [!DNL Adobe]-Anwendung für die Integration verwenden. |
| *apiKey* | Zeichenfolge | Nein | | API-Schlüssel, der für den Zugriff auf den AEM Discovery-Dienst verwendet wird. Der `apiKey` ist erforderlich, wenn Sie eine Integration mit einer [!DNL Adobe]-Anwendung verwenden. |
| *filterSchema* | Array | Nein | | Modell, das zum Konfigurieren von Filtereigenschaften verwendet wird. Dies ist nützlich, wenn Sie bestimmte Filteroptionen des Asset-Wählers einschränken möchten. |
| *filterFormProps* | Objekt | Nein | | Geben Sie die Filtereigenschaften an, die Sie zur Verfeinerung Ihrer Suche verwenden müssen. Beispiel: MIME-Typ JPG, PNG, GIF. |
| *selectedAssets* | Array `<Object>` | Nein |                 | Geben Sie ausgewählte Assets an, wenn der Asset-Wähler gerendert wird. Es ist ein Array von Objekten erforderlich, das eine ID-Eigenschaft der Assets enthält. Zum Beispiel: `[{id: 'urn:234}, {id: 'urn:555'}]` Ein Asset muss im aktuellen Verzeichnis verfügbar sein. Wenn Sie ein anderes Verzeichnis verwenden müssen, geben Sie auch einen Wert für die Eigenschaft `path` an. |
| *acvConfig* | Objekt | Nein | | Asset Collection View-Eigenschaft, die ein Objekt enthält, das eine benutzerdefinierte Konfiguration enthält, um Standardwerte zu überschreiben.  Diese Eigenschaft wird auch mit der Eigenschaft `rail` verwendet, um die Leistenansicht des Asset-Wählers zu aktivieren. |
| *i18nSymbols* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | Nein |                 | Wenn die vorkonfigurierten Übersetzungen für die Bedürfnisse Ihrer Anwendung unzureichend sind, können Sie eine Schnittstelle bereitstellen, über die Sie Ihre eigenen lokalisierten Werte durch die Eigenschaft `i18nSymbols` übergeben können. Wenn Sie über diese Schnittstelle einen Wert übergeben, werden die bereitgestellten Standardübersetzungen überschrieben und stattdessen Ihre eigenen verwendet. Um die Überschreibung vorzunehmen, müssen Sie ein gültiges [Message Descriptor](https://formatjs.io/docs/react-intl/api/#message-descriptor)-Objekt an den Schlüssel von `i18nSymbols` übergeben, den Sie überschreiben möchten. |
| *intl* | Objekt | Nein | | Der Asset-Wähler bietet standardmäßige, vorkonfigurierte Übersetzungen. Sie können die Übersetzungssprache auswählen, indem Sie eine gültige Gebietsschema-Zeichenfolge durch die `intl.locale`-Eigenschaft bereitstellen. Zum Beispiel: `intl={{ locale: "es-es" }}` </br></br> Die unterstützten Gebietsschema-Zeichenfolgen folgen den [ISO 639 – Codes](https://www.iso.org/iso-639-language-codes.html) für die Darstellung von Namen von Sprachen. </br></br> Liste der unterstützten Gebietsschemata: Englisch: „en-us“ (Standard), Spanisch: „es-es“, Deutsch: „de-de“, Französisch: „fr-fr“, Italienisch: „it-it“, Japanisch: „ja-jp“, Koreanisch: „ko-kr“, Portugiesisch: „pt-br“, Chinesisch (Vereinfacht): „zh-cn“, Chinesisch (Taiwan): „zh-tw“ |
| *repositoryId* | Zeichenfolge | Nein | &#39;&#39; | Repository, aus dem der Asset-Wähler den Inhalt lädt. |
| *additionalAemSolutions* | `Array<string>` | Nein | [ ] | Damit können Sie eine Liste mit zusätzlichen AEM-Repositorys hinzufügen. Wenn in dieser Eigenschaft keine Informationen bereitgestellt werden, werden nur die Medienbibliothek oder AEM Assets-Repositorys berücksichtigt. |
| *hideTreeNav* | Boolesch | Nein |  | Gibt an, ob die Navigationsseitenleiste der Asset-Baumstruktur ein- oder ausgeblendet werden soll. Sie wird nur in der modalen Ansicht verwendet und daher gibt es keine Auswirkung dieser Eigenschaft in der Leistenansicht. |
| *onDrop* | Funktion | Nein | | Die Eigenschaft ermöglicht die Ablagefunktion eines Assets. |
| *dropOptions* | `{allowList?: Object}` | Nein | | Konfiguriert Ablagefunktionen mithilfe der „Zulassungsliste“. |
| *colorScheme* | Zeichenfolge | Nein | | Design konfigurieren (`light` oder `dark`) für den Asset-Wähler. |
| *Design* | Zeichenfolge | Nein | Standard | Wenden Sie das Design auf die Asset-Auswahl-Anwendung zwischen `default` und `express` an. Es unterstützt auch `@react-spectrum/theme-express`. |
| *handleSelection* | Funktion | Nein | | Wird mit einem Array von Asset-Elementen aufgerufen, wenn Assets ausgewählt sind und die Schaltfläche `Select` im Modal angeklickt wird. Diese Funktion wird nur in der modalen Ansicht aufgerufen. Verwenden Sie für die Leistenansicht die Funktionen `handleAssetSelection` oder `onDrop`. Beispiel: <pre>handleSelection=(assets: Asset[])==> {...}</pre> Weitere Informationen finden Sie unter [Auswahl der Assets](/help/assets/asset-selector-customization.md#selection-of-assets) . |
| *handleAssetSelection* | Funktion | Nein | | Wird mit einem Array von Elementen aufgerufen, während die Assets ausgewählt oder deren Auswahl aufgehoben wird. Dies ist nützlich, wenn Sie auf Assets warten möchten, während die Benutzenden sie auswählen. Beispiel: <pre>handleSelection=(assets: Asset[])==> {...}</pre> Weitere Informationen finden Sie unter [Auswahl der Assets](/help/assets/asset-selector-customization.md#selection-of-assets) . |
| *onClose* | Funktion | Nein | | Wird aufgerufen, wenn die `Close`-Schaltfläche in der modalen Ansicht gedrückt wird. Dies wird nur in der `modal`-Ansicht aufgerufen und in der `rail`-Ansicht nicht beachtet. |
| *onFilterSubmit* | Funktion | Nein | | Wird mit Filterelementen aufgerufen, wenn Benutzende andere Filterkriterien ändern. |
| *selectionType* | Zeichenfolge | Nein | Einzeln | Konfiguration für `single`- oder `multiple`-Auswahl von Assets auf einmal. |
| *dragOptions.allowList* | Boolesch | Nein | | Die Eigenschaft wird verwendet, um das Drag-and-Drop von nicht auswählbaren Assets zuzulassen oder zu verweigern. |
| *aemTierType* | Zeichenfolge | Nein |  | Sie können damit festlegen, ob Assets aus der Bereitstellungsebene, der Autorenebene oder beiden Ebenen angezeigt werden sollen. <br><br> Syntax: `aemTierType:[0]: "author" 1: "delivery"` <br><br> Wenn zum Beispiel beide Ebenen `["author","delivery"]` verwendet werden, zeigt der Repository-Umschalter Optionen für Author und Bereitstellung an. |
| *handleNavigateToAsset* | Funktion | Nein | | Es handelt sich um eine Rückruffunktion, die die Auswahl eines Assets verarbeitet. |
| *noWrap* | Boolesch | Nein | | Die Eigenschaft *noWrap* hilft beim Rendern des Asset-Wählers im Bedienfeld der Seitenleiste. Wenn diese Eigenschaft nicht erwähnt wird, wird standardmäßig die *Dialogfeldansicht* gerendert. |
| *dialogSize* | Klein, mittelgroß, groß, Vollbild oder Vollbild-Übernahme | Zeichenfolge | Optional | Sie können das Layout kontrollieren, indem Sie dessen Größe mithilfe der angegebenen Optionen festlegen. |
| *colorScheme* | Hell oder dunkel | Nein | | Diese Eigenschaft wird verwendet, um das Design einer Asset-Wähler-Anwendung festzulegen. Sie können zwischen einem hellen und dunklen Design wählen. |
| *filterRepoList* | Funktion | Nein |  | Sie können die Rückruffunktion `filterRepoList` verwenden, die das Experience Manager-Repository aufruft und eine gefilterte Liste von Repositorys zurückgibt. |
| *expiryOptions* | Funktion | | | Sie können eine der beiden folgenden Eigenschaften verwenden: **getExpiryStatus**, was den Status eines abgelaufenen Assets angibt. Die Funktion gibt je nach dem Ablaufdatum eines von Ihnen angegebenen Assets `EXPIRED`, `EXPIRING_SOON` oder `NOT_EXPIRED` zurück. Siehe [Anpassen abgelaufener Assets](/help/assets/asset-selector-customization.md#customize-expired-assets). Darüber hinaus können Sie die Option **allowSelectionAndDrag** verwenden, in der der Wert der Funktion entweder `true` oder `false` sein kann. Wenn der Wert auf `false` festgelegt ist, kann das abgelaufene Asset weder ausgewählt noch auf die Arbeitsfläche gezogen werden. |
| *showToast* | | Nein | | Dadurch kann der Asset-Wähler eine benutzerdefinierte Popup-Meldung für das abgelaufene Asset anzeigen. |
| *metadataSchema* | Array | Nein | | Fügen Sie ein Array von Feldern hinzu, die Sie bereitstellen, um Metadaten vom Benutzer zu erfassen. Mit dieser Eigenschaft können Sie auch ausgeblendete Metadaten verwenden, die einem Asset automatisch zugewiesen, für den Benutzer jedoch nicht sichtbar sind. |
| *onMetadataFormChange* | Callback-Funktion | Nein | | Er besteht aus `property` und `value`. `Property` entspricht dem *mapToProperty* des Felds, das von dem *metadataSchema* übergeben wird, dessen Wert aktualisiert wird. Wohingegen `value` dem neuen Wert entspricht, wird als Eingabe bereitgestellt. |
| *targetUploadPath* | Zeichenfolge |  | `"/content/dam"` | Der Ziel-Upload-Pfad für die Dateien, der standardmäßig auf den Stamm des Assets-Repositorys festgelegt ist. |
| *hideUploadButton* | Boolesch | | False | Dadurch wird sichergestellt, dass die interne Schaltfläche zum Hochladen ausgeblendet wird. |
| *onUploadStart* | Funktion | Nein |  | Es handelt sich dabei um eine Callback-Funktion, mit der die Upload-Quelle zwischen Dropbox, OneDrive oder local weitergegeben wird. Die Syntax lautet `(uploadInfo: UploadInfo) => void` |
| *importSettings* | Funktion | | | Dadurch wird der Import von Assets aus Drittanbieterquellen unterstützt. `sourceTypes` verwendet ein Array der Importquellen, die Sie aktivieren möchten. Die unterstützten Quellen sind Onedrive und Dropbox. Die Syntax lautet `{ sourceTypes?: ImportSourceType[]; apiKey?: string; }` |
| *onUploadComplete* | Funktion | Nein | | Es handelt sich dabei um eine Rückruffunktion, mit der der Dateiupload-Status unter Erfolgreich, fehlgeschlagen oder dupliziert übergeben wird. Die Syntax lautet `(uploadStats: UploadStats) => void` |
| *onFilesChange* | Funktion | Nein | | Es handelt sich dabei um eine Rückruffunktion, die das Verhalten des Uploads beim Ändern einer Datei anzeigt. Es übergibt das neue Array der Dateien, die zum Hochladen ausstehen, und den Quelltyp des Uploads. Der Source-Typ kann im Fehlerfall null sein. Die Syntax lautet `(newFiles: File[], uploadType: UploadType) => void` |
| *uploadingPlaceholder* | Zeichenfolge | | | Es ist ein Platzhalterbild, das das Metadatenformular ersetzt, wenn ein Hochladen des Assets initiiert wird. Die Syntax lautet `{ href: string; alt: string; } ` |
| *uploadConfig* | Objekt | | | Es handelt sich um ein Objekt, das benutzerdefinierte Konfigurationen für den Upload enthält. |
| *featureSet* | Array | Zeichenfolge | | Die Eigenschaft `featureSet:[ ]` wird verwendet, um eine bestimmte Funktion in der Asset-Auswahl-Anwendung zu aktivieren oder zu deaktivieren. Um die Komponente oder eine Funktion zu aktivieren, können Sie einen Zeichenfolgenwert im Array übergeben oder das Array leer lassen, um diese Komponente zu deaktivieren. Wenn Sie beispielsweise die Upload-Funktion in der Asset-Auswahl aktivieren möchten, verwenden Sie die Syntax `featureSet:[0:"upload"]`. |

<!--
| *rootPath* | String | No | /content/dam/ | Folder path from which Asset Selector displays your assets. `rootPath` can also be used in the form of encapsulation. For example, given the following path, `/content/dam/marketing/subfolder/`, Asset Selector does not allow you to traverse through any parent folder, but only displays the children folders. |
| *path* | String | No | | Path that is used to navigate to a specific directory of assets when the Asset Selector is rendered. |
| *expirationDate* | Function | No | | This function is used to set the usability period of an asset. |
| *disableDefaultBehaviour* | Boolean | No | False | It is a function that is used to enable or disable the selection of an expired asset. You can customize the default behavior of an asset that is set to expire. See [customize expired assets](/help/assets/asset-selector-customization.md#customize-expired-assets). |
-->
