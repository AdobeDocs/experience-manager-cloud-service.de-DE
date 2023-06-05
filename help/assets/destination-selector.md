---
title: Zielauswahl für AEM as a Cloud Service
description: Verwenden Sie die AEM Ziel-Auswahl, um Assets anzuzeigen und auszuwählen, die Sie als Kopie des ursprünglichen Assets verwenden können.
contentOwner: Adobe
feature: destination selector
role: Admin,User
source-git-commit: fc156b95ebbdb0546f9fb334b0cb6f599f5f2692
workflow-type: tm+mt
source-wordcount: '1907'
ht-degree: 3%

---


# Zielauswahl für MikroFrontend {#Overview}

Der Micro-Frontend-Zielselektor bietet eine Benutzeroberfläche innerhalb Ihrer Anwendung, die einfach in die [!DNL Experience Manager Assets as a Cloud Service] Repository. Sie können den entsprechenden Ordner im [!DNL Experience Manager Assets as a Cloud Service] Repository erstellen und Assets aus Ihrer Anwendung hochladen.

Die Micro-Frontend-Benutzeroberfläche wird in Ihrem Anwendungserlebnis mithilfe des Destination Selector-Pakets zur Verfügung gestellt. Alle Aktualisierungen des Pakets werden automatisch importiert und die zuletzt bereitgestellte Zielauswahl wird automatisch in Ihre Anwendung geladen.

![Übersicht](assets/overview-destination-selector.png)

Die Zielauswahl bietet viele Vorteile, z. B.:

* Einfache Integration in Adobe- oder Nicht-Adobe-Apps mit der Vanilla JavaScript-Bibliothek.
* Einfach zu verwalten, da Aktualisierungen des Destination Selector-Pakets automatisch in der Zielauswahl bereitgestellt werden, die für Ihre Anwendung verfügbar ist. Es sind keine Aktualisierungen innerhalb Ihrer Anwendung erforderlich, um die neuesten Änderungen zu laden.
* Einfachere Anpassung, da Eigenschaften verfügbar sind, die die Anzeige der Zielauswahl in Ihrer Anwendung steuern.
* Volltextsuche, um schnell zu Ordnern zu navigieren, um Assets aus Ihrer Anwendung hochzuladen.
* Möglichkeit, Ordner zu erstellen, Ordner in auf- oder absteigender Reihenfolge zu sortieren und sie in der Ansicht &quot;Liste&quot;, &quot;Raster&quot;, &quot;Galerie&quot;oder &quot;Wasserfall&quot;anzuzeigen.

In diesem Artikel wird gezeigt, wie der Ziel-Selektor mit einer [!DNL Adobe] unter Unified Shell oder wenn Sie bereits ein imsToken zur Authentifizierung generiert haben. Diese Workflows werden in diesem Artikel als Nicht-SUSI-Fluss bezeichnet.

Führen Sie die folgenden Aufgaben aus, um die Zielauswahl in Ihre [!DNL Experience Manager Assets as a Cloud Service] repository:

* [Integration der Zielauswahl mit Vanilla JS](#integration-with-vanilla-js)
* [Anzeigeeigenschaften des Ziel-Selektors definieren](#destination-selector-properties)
* [Verwenden der Zielauswahl](#using-destination-selector)

## Integration der Zielauswahl mit Vanilla JS {#integration-with-vanilla-js}

Sie können jede [!DNL Adobe] oder Nicht-Adobe-Anwendung mit [!DNL Experience Manager Assets] as a [!DNL Cloud Service] Repository erstellen und Assets aus der Anwendung auswählen.

Die Integration erfolgt durch Importieren des Destination Selector-Pakets und Verbinden mit den as a Cloud Service Assets mithilfe der Vanilla JavaScript-Bibliothek. Sie müssen eine `index.html` oder einer entsprechenden Datei in Ihrer Anwendung auf -
* Authentifizierungsdetails definieren
* Zugriff auf das as a Cloud Service Asset-Repository
* Konfigurieren der Eigenschaften der Anzeige der Zielauswahl

Sie können eine Authentifizierung durchführen, ohne einige der IMS-Eigenschaften zu definieren, wenn:

* Sie integrieren eine [!DNL Adobe] Anwendung auf [Unified Shell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=en).
* Für die Authentifizierung wurde bereits ein IMS-Token generiert.

## Voraussetzungen {#prerequisites}

Definieren Sie die Voraussetzungen in der `index.html` Datei oder einer ähnlichen Datei in Ihrer Anwendungsimplementierung, um die Authentifizierungsdetails für den Zugriff auf die [!DNL Experience Manager Assets] as a [!DNL Cloud Service] Repository. Zu den Voraussetzungen gehören:
* imsOrg
* imsToken
* apikey

## Installation {#installation}

Der Zielselektor ist über beide ESM-CDN verfügbar (z. B. [esm.sh](https://esm.sh/)/[Skypack](https://www.skypack.dev/)) und [UMD](https://github.com/umdjs/umd) -Version.

In Browsern mit **UMD-Version** (empfohlen):

```
<script src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/assets-selectors.js"></script>

<script>
  const { renderDestinationSelector } = PureJSSelectors;
</script>
```

In Browsern mit `import maps` Support verwenden **ESM CDN-Version**:

```
<script type="module">
  import { DestinationSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/@assets/selectors/index.js'
</script>
```

In der Deno/Webpack Module Federation mit **ESM CDN-Version**:

```
import { DestinationSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/@assets/selectors/index.js'
```

### Ausgewähltes Ziel {#selected-destination}

Zielauswahl empfängt einen Rückruf von `onItemSelect`, `onTreeToggleItem`oder `onTreeSelectionChange` durch den ausgewählten Ordner, der das Objekt enthält (Verzeichnis, Bild usw.).

**Schemasyntax**

```
interface SelectedDestination {
  id: string;
  children: SelectedDestination[];
  'repo:repositoryId': string;
  'dc:format': string;
  'repo:assetClass': string;
  'storage:directoryType': string;
  'storage:region': string;
  'repo:name': string;
  'repo:path': string;
  'repo:ancestors': string[];
  'repo:createDate': string;
  'storage:assignee':

  { type: string; id: string; }
  ;
  'repo:assetId': string;
  'aem:published': boolean;
  'repo:createdBy': string;
  'repo:state': string;
  'repo:id': string;
  'repo:modifyDate': string;
  _page:

  { orderBy: string; count: number; };
}
```

In der folgenden Tabelle werden einige der wichtigen Eigenschaften des ausgewählten Ziels beschrieben.

| Eigenschaft | Typ | Erklärung |
|---|---|---|
| *repo:repositoryId* | Zeichenfolge | Eindeutige Kennung für das Repository, in dem das Asset gespeichert ist. |
| *repo:id* | Zeichenfolge | Eindeutige Kennung für das Asset. |
| *repo:assetClass* | Zeichenfolge | Die Classification des Assets (z. B. Bild oder Video, Dokument). |
| *repo:name* | Zeichenfolge | Der Name des Assets, einschließlich der Dateierweiterung. |
| *repo:size* | Number (Zahl) | Die Größe des Assets in Bytes. |
| *repo:path* | Zeichenfolge | Der Speicherort des Assets im Repository. |
| *repo:ancestors* | `Array<string>` | Ein Array von Vorgängerelementen für das Asset im Repository. |
| *repo:state* | Zeichenfolge | Aktueller Status des Assets im Repository (z. B. aktiv, gelöscht usw.). |
| *repo:createdBy* | Zeichenfolge | Der Benutzer oder das System, der bzw. das das Asset erstellt hat. |
| *repo:createDate* | Zeichenfolge | Datum und Uhrzeit der Erstellung des Assets. |
| *repo:modifiedBy* | Zeichenfolge | Der Benutzer oder das System, der bzw. das das Asset zuletzt geändert hat. |
| *repo:modifyDate* | Zeichenfolge | Datum und Uhrzeit der letzten Änderung des Assets. |
| *dc:format* | Zeichenfolge | Das Format des Assets. |
| *_Seite* | orderBy: Zeichenfolge; count: Nummer; | Umfasst die Seitenzahl des Dokuments. |

Eine vollständige Liste der Eigenschaften und ein detailliertes Beispiel finden Sie unter [Codebeispiel für Zielauswahl](https://github.com/adobe/aem-assets-selectors-mfe-examples).

### Beispiel für Nicht-SUSI-Fluss {#non-ims-vanilla}

In diesem Beispiel wird gezeigt, wie beim Ausführen eines [!DNL Adobe] Anwendung unter Unified Shell oder wenn Sie bereits `imsToken` zur Authentifizierung generiert wurde.

Schließen Sie das Ziel-Selektor-Paket in Ihren Code ein, indem Sie die `script` Tag, wie in _Zeilen 6 bis 15_ des unten stehenden Beispiels. Sobald das Skript geladen wurde, wird die `PureJSSelectors` Die globale Variable ist verfügbar. Definieren der Zielauswahl [properties](#destination-selector-properties) wie in _Zeilen 16 bis 23_. Die `imsOrg` und `imsToken` -Eigenschaften sind beide für die Authentifizierung im Nicht-SUSI-Fluss erforderlich. Die `handleSelection` -Eigenschaft wird verwendet, um die ausgewählten Assets zu verarbeiten. Rufen Sie zum Rendern der Zielauswahl die `renderDestinationSelector` -Funktion gemäß _Zeile 17_. Die Zielauswahl wird im `<div>` Container-Element, wie in _Zeilen 21 und 22_.

Wenn Sie diese Schritte ausführen, können Sie die Zielauswahl mit einem Nicht-SUSI-Fluss in Ihrer [!DNL Adobe] Anwendung.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>
<head>
    <title>Destination Selector</title>
    <script src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/assets-selectors.js"></script>
    <script>
        // get the container element in which we want to render the DestinationSelector component
        const container = document.getElementById('destination-selector-container');
        // imsOrg and imsToken are required for authentication in non-SUSI flow
        const destinationSelectorProps = {
            imsOrg: 'example-ims@AdobeOrg',
            imsToken: "example-imsToken",
            apiKey: "example-apiKey-associated-with-imsOrg",
            handleSelection: (assets: SelectedAssetType[]) => {},
        };
        // Call the `renderDestinationSelector` available in PureJSSelectors globals to render DestinationSelector
        PureJSSelectors.renderDestinationSelector(container, destinationselectorprops);
    </script>
</head>

<body>
    <div id="destination-selector-container" style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px;">
    </div>
</body>

</html>
```

Ein detailliertes Beispiel finden Sie unter [Codebeispiel für Zielauswahl](https://github.com/adobe/aem-assets-selectors-mfe-examples).

## Verwenden der Eigenschaften der Zielauswahl {#destination-selector-properties}

Sie können die Eigenschaften der Zielauswahl verwenden, um die Darstellung der Zielauswahl anzupassen. In der folgenden Tabelle sind die Eigenschaften aufgeführt, die Sie zum Anpassen und Verwenden der Zielauswahl verwenden können:

| Eigenschaft | Typ | Erforderlich | Standard | Beschreibung |
|---|---|---|---|---|
| *imsOrg* | Zeichenfolge | Ja |  | Adobe Identity Management System (IMS)-ID, die bei der Bereitstellung zugewiesen wird [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] für Ihre Organisation. Die `imsOrg` -Schlüssel ist erforderlich, um zu authentifizieren, ob sich die Organisation, auf die Sie zugreifen, unter Adobe IMS befindet oder nicht. |
| *imsToken* | Zeichenfolge | Nein |  | Für die Authentifizierung verwendetes IMS-Trägertoken. `imsToken` ist nicht erforderlich, wenn Sie den SUSI-Fluss verwenden. Sie ist jedoch erforderlich, wenn Sie den Nicht-SUSI-Fluss verwenden. |
| *apiKey* | Zeichenfolge | Nein |  | API-Schlüssel, der für den Zugriff auf den AEM Discovery-Dienst verwendet wird. `apiKey` ist nicht erforderlich, wenn Sie den SUSI-Fluss verwenden. Sie ist jedoch im Nicht-SUSI-Fluss erforderlich. |
| *rootPath* | Zeichenfolge | Nein | /content/dam/ | Ordnerpfad, über den die Ziel-Auswahl Ihre Assets anzeigt. `rootPath` kann auch in Form von Kapselung verwendet werden. Beispiel: Unter dem folgenden Pfad: `/content/dam/marketing/subfolder/`, ermöglicht die Zielauswahl nicht, durch einen übergeordneten Ordner zu navigieren, sondern zeigt nur die untergeordneten Ordner an. |
| *hasMore* | Boolean (Boolesch) | Nein |  | Wenn die Anwendung mehr Inhalt anzeigen muss, können Sie diese Eigenschaft verwenden, um einen Lader hinzuzufügen, der den Inhalt lädt, damit er in der Anwendung sichtbar wird. Es handelt sich um einen Indikator, der angibt, dass das Laden von Inhalten noch läuft. |
| *orgName* | Boolean (Boolesch) | Nein |  | Es ist der Name der Organisation (wahrscheinlich orgID), die mit AEM verknüpft ist. |
| *initRepoID* | Zeichenfolge | Nein |  | Dies ist der Pfad des Assets-Repositorys, den Sie in einer standardmäßigen ersten Ansicht verwenden möchten |
| *onCreateFolder* | Zeichenfolge | Nein |  | Die `onCreateFolder` -Eigenschaft können Sie ein Symbol hinzufügen, mit dem ein neuer Ordner in der Anwendung hinzugefügt wird. |
| *onConfirm* | Zeichenfolge | Nein |  | Dies ist ein Rückruf, wenn Sie auf die Schaltfläche Bestätigen klicken. |
| *confirmDisabled* | Zeichenfolge | Nein |  | Diese Eigenschaft steuert den Umschalter der Schaltfläche &quot;Bestätigen&quot;. |
| *viewType* | Zeichenfolge | Nein |  | Die `viewType` -Eigenschaft wird verwendet, um die Ansichten anzugeben, die Sie zum Anzeigen von Assets verwenden. |
| *viewTypeOptions* | Zeichenfolge | Nein |  | Diese Eigenschaft ist mit `viewType` -Eigenschaft. Sie können eine oder mehrere Ansichten angeben, um Assets anzuzeigen. Verfügbare viewTypeOptions sind: Listenansicht, Rasteransicht, Galerie-Ansicht, Wasserfallansicht und Baumansicht. |
| *itemNameFormatter* | Zeichenfolge | Nein |  | Mit dieser Eigenschaft können Sie den Elementnamen formatieren |
| *i18nSymbols* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | Nein |  | Wenn die OOTB-Übersetzungen nicht ausreichen, um die Anforderungen Ihrer Anwendung zu erfüllen, können Sie eine Benutzeroberfläche bereitstellen, über die Sie Ihre eigenen lokalisierten Werte über die `i18nSymbols` prop. Wenn Sie über diese Schnittstelle einen Wert übergeben, werden die bereitgestellten Standardübersetzungen überschrieben und stattdessen Ihre eigenen verwendet.  Um die Überschreibung durchzuführen, müssen Sie eine gültige [Nachrichtendeskriptor](https://formatjs.io/docs/react-intl/api/#message-descriptor) -Objekt auf den Schlüssel von `i18nSymbols` die Sie überschreiben möchten. |
| *inlineAlertSetup* | Zeichenfolge | Nein |  | Es wird eine Warnmeldung hinzugefügt, die Sie in der Anwendung übermitteln möchten. Fügen Sie beispielsweise eine Warnmeldung hinzu, dass Sie keine Berechtigung für den Zugriff auf diesen Ordner haben. |
| *intl* | Objekt | Nein |  | Die Zielauswahl bietet standardmäßige OOTB-Übersetzungen. Sie können die Übersetzungssprache auswählen, indem Sie eine gültige Gebietsschemazeichenfolge über die `intl.locale` prop. Beispiel: `intl={{ locale: "es-es" }}` </br></br> Die unterstützten Gebietsschema-Zeichenfolgen folgen dem [ISO 639 - Codes](https://www.iso.org/iso-639-language-codes.html) für die Darstellung der Namen von Sprachstandards. </br></br> Liste der unterstützten Gebietsschemata: Englisch - &#39;en-us&#39; (Standard) Spanisch - &#39;es-es&#39; Deutsch - &#39;de-de&#39; Französisch - &#39;fr-fr&#39; Italienisch - &#39;it-it&#39; Japanisch - &#39;ja-jp&#39; Koreanisch - &#39;ko-kr&#39; Portugiesisch - &#39;pt-br&#39; Chinesisch (traditionell) - &#39;zh-cn&#39; Chinesisch (Taiwan) - &#39;zh-tw&#39; |

## Beispiele zur Verwendung der Eigenschaften der Zielauswahl {#usage-examples}

Sie können die Zielauswahl definieren [properties](#destination-selector-properties) im `index.html` -Datei, um die Zielauswahl-Anzeige in Ihrer Anwendung anzupassen.

### Beispiel 1: Erstellen eines Ordners in der Zielauswahl

Mit der Zielauswahl können Sie einen neuen Ordner erstellen, in den Sie Assets an einem bestimmten Speicherort hochladen, verschieben oder kopieren können.

![create-folder-destination-selector](assets/create-folder-destination-selector.png)

### Beispiel 2: Ansichtstyp der Zielauswahl festlegen

Die Zielauswahl zeigt ein breites Spektrum an Assets in vier verschiedenen Ansichten an, einschließlich Listenansicht, Rasteransicht, Galerie-Ansicht und Wasserfallansicht. Um den standardmäßigen Ansichtstyp festzulegen, können Sie `viewType` -Eigenschaft. Die `viewTypeOptions` -Eigenschaft zusammen mit `viewType` -Eigenschaft, um andere Ansichtstypen festzulegen, sodass andere Ansichtstypen in einer Dropdown-Liste angezeigt werden können. Es kann ein einzelnes Argument verwendet werden, wenn nur eine Option angezeigt werden soll.

![viewtype-destination-selector](assets/viewtype-destination-selector.png)

### Beispiel 3: Pfad des Asset-Ordners initialisieren

Verwenden Sie die `path` -Eigenschaft zum Definieren des Ordnernamens, der automatisch beim Rendern der Zielauswahl angezeigt wird.

![initialize-folder-path](assets/initialize-folder-path.png)

## Verwenden der Zielauswahl {#using-destination-selector}

Sobald die Zielauswahl eingerichtet ist und Sie authentifiziert sind, um die Zielauswahl mit Ihrem [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] -Anwendung können Sie Assets auswählen oder verschiedene andere Vorgänge ausführen, um im Repository nach Assets zu suchen.

![using-destination-selector](assets/using-destination-selector.png)

* **A**: [Suchleiste](#search-bar)
* **B**: [Sortierung](#sorting)
* **C**: [Assets](#assets-repo)
* **D**: [Suffix oder Präfix hinzufügen](#add-suffix-or-prefix)
* **E**: [Neuen Ordner erstellen](#create-new-folder)
* **F**: [Ansicht](#types-of-view)
* **G**: [Info](#info)
* **H**: [Ordner auswählen](#select-folder)

### Suchleiste {#search-bar}

Mit der Zielauswahl können Sie eine Volltextsuche nach Assets im ausgewählten Repository durchführen. Wenn Sie beispielsweise den Suchbegriff `wave` in der Suchleiste alle Assets mit der `wave` -Keyword, das in einer der Metadateneigenschaften erwähnt wird, wird angezeigt.

### Sortierung {#sorting}

Sie können Assets in der Zielauswahl nach Name, Dimension oder Größe eines Assets sortieren. Sie können die Assets auch in auf- oder absteigender Reihenfolge sortieren.

### Assets-Repository {#assets-repo}

Mit der Zielauswahl können Sie auch Daten des Repositorys Ihrer Wahl anzeigen, das in der AEM Anwendung verfügbar ist. Sie können `repositoryID` -Eigenschaft, um den Pfad des Zielordners zu initialisieren, den Sie in der ersten Instanz der Zielauswahl anzeigen möchten.

### Suffix oder Präfix hinzufügen {#add-suffix-or-prefix}

Dies ist ein Beispiel für die `optionsFormSetup` -Eigenschaft. Sie können dies verwenden, um die Auswahl zu bestätigen. Sie wird an die `onConfirm` -Ereignis.

### Neuen Ordner erstellen {#create-new-folder}

Damit können Sie einen neuen Ordner im Zielordner Ihrer [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].

### Ansichtstypen {#types-of-view}

Mit der Zielauswahl können Sie das Asset in vier verschiedenen Ansichten anzeigen:

* **![Listenansicht](assets/do-not-localize/list-view.png) [!UICONTROL Listenansicht]**: Die Listenansicht zeigt bildlauffähige Dateien und Ordner in einer Spalte an.
* **![Rasteransicht](assets/do-not-localize/grid-view.png) [!UICONTROL Rasteransicht]**: Die Rasteransicht zeigt bildlauffähige Dateien und Ordner in einem Raster aus Zeilen und Spalten an.
* **![Galerie-Ansicht](assets/do-not-localize/gallery-view.png) [!UICONTROL Galerie-Ansicht]**: Die Galerie-Ansicht zeigt Dateien oder Ordner in einer zentrierten horizontalen Liste an.
* **![Wasserfallansicht](assets/do-not-localize/waterfall-view.png) [!UICONTROL Wasserfallansicht]**: Die Wasserfallansicht zeigt Dateien oder Ordner in Form von Bridge an.

### Info {#info}

Über das Informations- oder Informationssymbol können Sie die Metadaten des ausgewählten Assets anzeigen. Sie enthält verschiedene Details wie Dimensionen, Größe, Beschreibung, Pfad, Änderungsdatum und Erstellungsdatum. Die Metadateninformationen werden beim Hochladen, Kopieren oder Erstellen eines neuen Assets bereitgestellt.

### Ordner auswählen {#select-folder}

Mit der Schaltfläche Ordner auswählen können Sie Assets für verschiedene Vorgänge auswählen, die mit [properties](#destination-selector-properties) in der Zielauswahl.