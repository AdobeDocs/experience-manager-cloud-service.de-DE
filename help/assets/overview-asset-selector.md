---
title: Asset-Selektor für [!DNL Adobe Experience Manager] als ein [!DNL Cloud Service]
description: Verwenden Sie die Asset-Auswahl, um die Metadaten und Ausgabeformate von Assets in Ihrer Anwendung zu suchen, zu suchen und abzurufen.
role: Admin, User
exl-id: 62b0b857-068f-45b7-9018-9c59fde01dc3
source-git-commit: 575980320c1dbd32f799bf9c2fddf3d6773c838a
workflow-type: tm+mt
source-wordcount: '1295'
ht-degree: 69%

---

# Micro-Front-End-Asset-Selektor {#Overview}

Der Micro-Front-End-Asset-Selektor bietet eine Benutzeroberfläche, die sich problemlos in das [!DNL Experience Manager Assets]-Repository integrieren lässt, sodass Sie die im Repository verfügbaren digitalen Assets durchsuchen und für die Erstellung von Applikationen verwenden können.

Die Micro-Front-End-Benutzeroberfläche wird über das Asset-Selektor-Paket in Ihrer Applikation verfügbar gemacht. Alle Aktualisierungen des Pakets werden automatisch importiert, und der zuletzt bereitgestellte Asset-Selektor wird automatisch in Ihrer Applikation geladen.

![Übersicht](assets/overview.png)

Der Asset-Selektor bietet viele Vorteile, z. B.:

* Einfache Integration mit einer der Anwendungen [Adobe](/help/assets/integrate-asset-selector-adobe-app.md) oder [non-Adobe](/help/assets/integrate-asset-selector-non-adobe-app.md) unter Verwendung der Vanilla JavaScript-Bibliothek.
* Einfach zu verwalten, da Aktualisierungen des Assets-Wähler-Pakets automatisch für den Asset-Selektor bereitgestellt werden, der für Ihre Applikation verfügbar ist. Es sind keine Aktualisierungen innerhalb Ihrer Applikation erforderlich, um die neuesten Änderungen zu laden.
* Einfachere Anpassung, da Eigenschaften verfügbar sind, die die Anzeige des Asset-Selektors in Ihrer Applikation steuern.
* Volltextsuche, vordefinierte und benutzerdefinierte Filter, um schnell zu Assets zu navigieren, die für das Authoring-Erlebnis verwendet werden können.
* Möglichkeit, innerhalb einer IMS-Organisation zur Asset-Auswahl zwischen Repositorys zu wechseln.
* Möglichkeit, Assets nach Namen, Dimensionen und Größe zu sortieren und in der Listen-, Raster-, Galerie- oder Wasserfallansicht anzuzeigen.

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
* Die URL der Anwendung befindet sich in der Zulassungsliste der Umleitungs-URLs des IMS-Clients.
* Der IMS-Anmeldefluss wird mithilfe eines Popup-Fensters im Webbrowser konfiguriert und gerendert. Daher sollten Popup-Fenster im Ziel-Browser aktiviert oder zugelassen werden.

Verwenden Sie die oben genannten Voraussetzungen, wenn Sie den IMS-Authentifizierungs-Workflow der Asset-Auswahl benötigen. Wenn Sie bereits mit dem IMS-Workflow authentifiziert sind, können Sie stattdessen die IMS-Informationen hinzufügen.

**Mehr anzeigen**

* [Integrieren der Asset-Auswahl in eine Adobe-App](/help/assets/integrate-asset-selector-adobe-app.md)
* [Integrieren der Asset-Auswahl in eine Nicht-Adobe-App](/help/assets/integrate-asset-selector-non-adobe-app.md)
* [Integrieren von APIs zum Öffnen dynamischer Medien in Asset Selector](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)


>[!IMPORTANT]
>
> Dieses Repository dient als zusätzliche Dokumentation, die die verfügbaren APIs und Anwendungsbeispiele für die Integration des Asset-Wählers beschreibt. Bevor Sie versuchen, den Asset-Wähler zu installieren oder zu verwenden, stellen Sie sicher, dass Ihr Unternehmen Zugriff auf den Asset-Wähler im Experience Manager Assets as a Cloud Service-Profil erhalten hat. Wenn diese Komponenten noch nicht bereitgestellt wurden, können Sie sie weder integrieren noch verwenden. Um die Bereitstellung anzufordern, sollte Ihr Programmadministrator ein Support-Ticket erstellen, das von der Admin Console als P2 gekennzeichnet ist, und die folgenden Informationen einschließen:
>
>* Domain-Namen, auf denen die integrierende Anwendung gehostet wird.
>* Nach der Bereitstellung wird Ihrem Unternehmen entsprechend den angeforderten Umgebungen, die für die Konfiguration des Asset-Wählers erforderlich sind, `imsClientId`, `imsScope` und eine `redirectUrl` bereitgestellt. Ohne diese gültigen Eigenschaften können Sie die Installationsschritte nicht ausführen.

## Installation {#installation}

Der Asset-Wähler ist sowohl über die ESM CDN-Version (z. B. [esm.sh](https://esm.sh/)/[skypack](https://www.skypack.dev/)) als auch über die [UMD](https://github.com/umdjs/umd)-Version verfügbar.

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

Um Ordner im linken Navigationsbereich auszublenden, klicken Sie auf das Symbol **[!UICONTROL Ordner ausblenden]** . Um die Änderungen rückgängig zu machen, klicken Sie erneut auf das Symbol **[!UICONTROL Ordner ausblenden]**.

### Repository-Umschalter {#repository-switcher}

Mit dem Asset-Selektor können Sie auch Repositorys für die Asset-Auswahl wechseln. Sie können das gewünschte Repository aus der Dropdown-Liste im linken Bedienfeld auswählen. Die in der Dropdown-Liste verfügbaren Repository-Optionen basieren auf der `repositoryId`-Eigenschaft, die in der `index.html`-Datei definiert ist. Sie basiert auf der Umgebung der ausgewählten IMS-Organisation, auf die die angemeldeten Benutzenden zugreifen können. Nutzerinnen und Nutzer können eine bevorzugte `repositoryID` übergeben. In diesem Fall stoppt der Asset-Selektor das Rendern des Repository-Umschalters und rendert Assets nur aus dem angegebenen Repository.

### Assets-Repository

Es handelt sich um eine Sammlung von Asset-Ordnern, mit denen Sie Vorgänge durchführen können.

### Vorkonfigurierte Filter {#filters}

Der Asset-Selektor bietet außerdem vordefinierte Filteroptionen, mit denen Sie Ihre Suchergebnisse verfeinern können. Die folgenden Filter sind verfügbar:

* **[!UICONTROL Status]:** enthält den aktuellen Status des Assets, entweder `all`, `approved`, `rejected` oder `no status`.
* **[!UICONTROL Dateityp]:** enthält `folder`, `file`, `images`, `documents` oder `video`.
* **[!UICONTROL Ablaufstatus]:** erwähnt die Assets basierend auf ihrer Gültigkeitsdauer. Sie können entweder das Kontrollkästchen `[!UICONTROL Expired]` aktivieren, um abgelaufene Assets zu filtern, oder `[!UICONTROL Expiration Duration]` eines Assets so einstellen, dass Assets basierend auf ihrer Ablaufdauer angezeigt werden. Wenn ein Asset bereits abgelaufen ist oder kurz vor seinem Ablauf steht, wird dasselbe mit einem Abzeichen angezeigt. Darüber hinaus können Sie steuern, ob Sie die Verwendung (oder das Ziehen per Drag-and-Drop) eines abgelaufenen Assets zulassen möchten. Weitere Informationen zum [Anpassen abgelaufener Assets](/help/assets/asset-selector-customization.md#customize-expired-assets). Standardmäßig wird für Assets, die in den nächsten 30 Tagen ablaufen, das Zeichen &quot;**Bald ablaufen**&quot;angezeigt. Sie können die Gültigkeitsdauer jedoch mit der Eigenschaft `expirationDate` konfigurieren.

  >[!TIP]
  >
  > Wenn Sie Assets anhand ihres künftigen Ablaufdatums anzeigen oder filtern möchten, geben Sie den künftigen Datumsbereich im Feld `[!UICONTROL Expiration Duration]` an. Es werden die Assets mit dem Zeichen **Läuft bald ab** angezeigt.

* **[!UICONTROL MIME-Typ]:** enthält `JPG`, `GIF`, `PPTX`, `PNG`, `MP4`, `DOCX`, `TIFF`, `PDF`, `XLSX`.
* **[!UICONTROL Bildgröße]:**: umfasst minimale/maximale Breite, minimale/maximale Höhe des Bildes.

  ![rail-view-example](assets/filters-asset-selector.png)

### Benutzerdefinierte Suche

Neben der Volltextsuche ermöglicht der Asset-Selektor die Suche nach Assets innerhalb von Dateien mithilfe einer benutzerdefinierten Suche. Sie können benutzerdefinierte Suchfilter sowohl im Modal- als auch im Leistenansichtsmodus verwenden.

![custom-search](assets/custom-search1.png)

Sie können auch einen Standardsuchfilter erstellen, um die häufig gesuchten Felder zu speichern und sie später zu verwenden. Um eine benutzerdefinierte Suche für Ihre Assets zu erstellen, können Sie die `filterSchema`-Eigenschaft verwenden.

### Suchleiste {#search-bar}

Mit der Asset-Auswahl können Sie eine Volltextsuche nach Assets im ausgewählten Repository durchführen. Wenn Sie zum Beispiel den Suchbegriff `wave` in die Suchleiste eingeben, werden alle Assets angezeigt, die den Suchbegriff `wave` in einer der Metadateneigenschaften enthalten.

### Sortierung {#sorting}

Sie können Assets im Asset-Selektor nach Namen, Abmessungen oder Größe eines Assets sortieren. Sie können die Assets auch in auf- oder absteigender Reihenfolge sortieren.

### Ansichtstypen {#types-of-view}

Mit dem Asset-Selektor können Sie das Asset in vier verschiedenen Ansichten anzeigen:

* **![Listenansicht](assets/do-not-localize/list-view.png) [!UICONTROL Listenansicht]**: Die Listenansicht zeigt scrollbare Dateien und Ordner in einer Spalte an.
* **![Rasteransicht](assets/do-not-localize/grid-view.png) [!UICONTROL Rasteransicht]**: Die Rasteransicht zeigt scrollbare Dateien und Ordner in einem Raster aus Zeilen und Spalten an.
* **![Galerieansicht](assets/do-not-localize/gallery-view.png) [!UICONTROL Galerieansicht]**: Die Galerie-Ansicht zeigt Dateien oder Ordner in einer zentrierten, horizontalen Liste an.
* **![Wasserfallansicht](assets/do-not-localize/waterfall-view.png) [!UICONTROL Wasserfallansicht]**: Die Wasserfallansicht zeigt Dateien oder Ordner in Form einer Brücke an.

**Übersichtsgrafik**


## Weitere Informationen zu wichtigen Funktionen {#key-capabilities-asset-selector}

<table>
<tr>
    <td>
        <img src="assets/integrate-asset-selector.gif" width="70px" height="70px" alt="Grafik der Asset-Auswahl integrieren"><br/>
        <a href="integrate-asset-selector.md">Integrieren der Asset-Auswahl</a>
        <p>
        <em>Erfahren Sie mehr über verschiedene Funktionen zur Integration der Asset-Auswahl in mehrere Anwendungen.
        </p>
     </td>
    <td>
        <img src="assets/with-adobe-app.gif" width="70px" height="70px" alt="Integrieren des Asset-Selektors mit der Grafik Adobe-Apps"><br/>
        <a href="integrate-asset-selector.md">Integrieren der Asset-Auswahl in Adobe-Anwendungen</a>
        <p>
        <em>Erfahren Sie, wie Sie den Asset-Selektor mit verschiedenen Adobe-Applikationen integrieren.</em>
        </p>
    </td>
    <td>
        <img src="assets/third-party-app.gif" width="70px" height="70px" alt="Grafik der Asset-Auswahl integrieren"><br/>
        <a href="integrate-asset-selector.md">Integrieren der Asset-Auswahl in Anwendungen von Drittanbietern</a>
        <p>
        <em>Erweitern Sie die Funktionen zur Integration des Asset-Selektors in Nicht-Adobe-Anwendungen.</em>
        </p>
    </td>
    <td>
        <img src="assets/with-dynamic-media-open-api.gif" width="70px" height="70px" alt="Grafik der Asset-Auswahl integrieren"><br/>
        <a href="integrate-asset-selector.md">Integrieren der Asset-Auswahl in Dynamic Media Open APIs</a>
        <p>
        <em>Erfahren Sie, wie Sie den Asset-Selektor mit Dynamic Media Open APIs integrieren.</em>
        </p>
     </td>
</tr>
<tr>
    <td>
        <img src="assets/asset-selector-examples.gif" width="70px" height="70px" alt="Asset-Auswahleigenschaftsgrafik"><br/>
        <a href="asset-selector-customization.md">Asset-Wählereigenschaften</a>
        <p>
        <em>Erfahren Sie mehr über die Grundlagen zum Anpassen verschiedener Komponenten der Asset-Auswahl, wie Filter, Auswahl von Assets, abgelaufene Assets und vieles mehr. </em>
        </p>
    </td>
    <td>
        <img src="assets/asset-selector-properties.gif" width="70px" height="70px" alt="Abbildung der Asset-Auswahl-Beispiele"><br/>
        <a href="asset-selector-customization.md">Beispiele für Asset-Wähler</a>
        <p>
        <em>Verstehen Sie die Verwendung von Eigenschaften auf praktische Weise. </em>
        </p>
    </td>
    <td>
        <img src="assets/customize-asset-selector.gif" width="70px" height="70px" alt="Anpassen der Asset-Auswahl-Grafik"><br/>
        <a href="asset-selector-customization.md">Anpassungen der Asset-Auswahl</a>
        <p>
        <em>Konfigurieren und passen Sie die verschiedenen Komponenten der Asset-Auswahl basierend auf Ihrer Benutzerfreundlichkeit an. </em>
        </p>
    </td>
    <td>
        <img src="assets/asset-selector-upload.gif" width="70px" height="70px" alt="Asset-Auswahl-Upload-Grafik"><br/>
        <a href="asset-selector-upload.md">Anpassungen der Asset-Auswahl</a>
        <p>
        <em>Erfahren Sie, wie Sie Dateien oder Ordner aus Ihrem lokalen Dateisystem oder aus einem Drittanbietersystem in die Asset-Auswahl hochladen können. </em>
        </p>
    </td>
</tr>
</table>

>[!MORELIKETHIS]
>
>* [Asset-Selektor-Anpassungen](/help/assets/asset-selector-customization.md)
>* [Integrieren der Asset-Auswahl in verschiedene Anwendungen](/help/assets/integrate-asset-selector.md)
>* [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md)
>* [Integrieren der Asset-Auswahl in Dynamic Media mit OpenAPI-Funktionen](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
