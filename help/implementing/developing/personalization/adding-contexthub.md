---
title: Hinzufügen von ContextHub zu Seiten und Zugreifen auf Speicher
description: Fügen Sie Ihren Seiten ContextHub hinzu, um die ContextHub-Funktionen zu aktivieren und eine Verknüpfung mit den ContextHub-JavaScript-Bibliotheken herzustellen
exl-id: 8bfe2cff-3944-4e86-a95c-ebf1cb13913c
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 73%

---

# Hinzufügen von ContextHub zu Seiten und Zugreifen auf Speicher {#adding-contexthub-to-pages-and-accessing-stores}

Fügen Sie Ihren Seiten ContextHub hinzu, um die ContextHub-Funktionen zu aktivieren und eine Verknüpfung mit den ContextHub-JavaScript-Bibliotheken herzustellen.

Die ContextHub-JavaScript-API ermöglicht den Zugriff auf die von ContextHub verwalteten Kontextdaten. Diese Seite enthält einen kurzen Überblick über die wichtigsten Funktionen der API für den Zugriff auf Kontextdaten und deren Bearbeitung. Ausführlichere Informationen und Code-Beispiele finden Sie unter den Links zur API-Referenzdokumentation.

## Hinzufügen von ContextHub zu einer Seitenkomponente {#adding-contexthub-to-a-page-component}

Schließen Sie die `contexthub`-Komponente in den Bereich `head` Ihrer Seite ein, um die ContextHub-Funktionen zu aktivieren und eine Verknüpfung mit den ContextHub-JavaScript-Bibliotheken herzustellen. Der HTL-Code für Ihre Seitenkomponente sollte in etwa wie im folgenden Beispiel aussehen:

```xml
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

Beachten Sie, dass Sie auch konfigurieren müssen, ob die ContextHub-Symbolleiste im Vorschaumodus angezeigt wird. Siehe [Ein- und Ausblenden der ContextHub-Benutzeroberfläche](configuring-contexthub.md#showing-and-hiding-the-contexthub-ui).

## Informationen zu ContextHub-Speichern {#about-contexthub-stores}

Verwenden Sie ContextHub-Stores, um Kontextdaten beizubehalten. ContextHub bietet die folgenden Storetypen, die die Grundlage aller Storetypen bilden:

* [PersistedStore](contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](contexthub-api.md#contexthub-store-persistedstore)

Alle Speichertypen sind Erweiterungen der Klasse [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core). Informationen zum Erstellen eines neuen Storetyps finden Sie unter [Erstellen benutzerdefinierter Stores](extending-contexthub.md#creating-custom-store-candidates). Weitere Informationen zu Beispiel-Store-Typen finden Sie unter [Beispiele für ContextHub-Store-Kandidaten](sample-stores.md).

### Beibehaltungsmodi {#persistence-modes}

ContextHub-Stores verwenden einen der folgenden Persistenzmodi:

* **Lokal:** Verwendet HTML5 localStorage , um Daten beizubehalten. Lokaler Speicher wird sitzungsübergreifend im Browser beibehalten.
* **Sitzung:** Verwendet „sessionStorage“ (HTML5), um Daten beizubehalten. Sitzungsspeicher wird für die Dauer der Browser-Sitzung beibehalten und steht für alle Browser-Fenster zur Verfügung.
* **Cookie:** Verwendet die native Unterstützung von Cookies durch den Browser für die Datenspeicherung. Cookie-Daten werden in HTTP-Anfrage an den bzw. vom Server gesendet.
* **Window.name:** Verwendet die Eigenschaft „window.name“, um Daten beizubehalten.
* **Speicher:** Verwendet ein JavaScript-Objekt, um Daten beizubehalten.

Standardmäßig verwendet ContextHub den lokalen Persistenzmodus. Wenn der Browser HTML5 localStorage nicht unterstützt oder zulässt, wird die Sitzungspersistenz verwendet. Wenn der Browser HTML5 sessionStorage nicht unterstützt oder zulässt, wird die Persistenz Window.name verwendet.

### Store-Daten {#store-data}

Intern speichern Sie Daten in einer Baumstruktur, sodass Werte als primäre Typen oder komplexe Objekte hinzugefügt werden können. Wenn Sie komplexe Objekte zu Stores hinzufügen, bilden die Objekteigenschaften Zweige in der Datenstruktur. Im folgenden Beispiel wird das folgende komplexe Objekt einem leeren, als Store bezeichneten Ort hinzugefügt:

```javascript
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

Die Baumstruktur der Speicherdaten kann wie folgt gestaltet werden:

```text
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

Die Baumstruktur definiert Datenelemente im Speicher als Schlüssel-Wert-Paare. Im obigen Beispiel entspricht der Schlüssel `/number` dem Wert `321` und der Schlüssel `/data/country` dem Wert `Switzerland`.

### Bearbeiten von Objekten {#manipulating-objects}

Für die Bearbeitung von JavaScript-Objekten stellt ContextHub die Klasse [`ContextHub.Utils.JSON.tree`](contexthub-api.md#contexthub-utils-json-tree) bereit. Mithilfe der Funktionen dieser Klasse können Sie JavaScript-Objekte bearbeiten, bevor Sie sie einem Store hinzufügen oder nachdem Sie sie aus einem Store abgerufen haben.

Darüber hinaus bietet die Klasse [`ContextHub.Utils.JSON`](contexthub-api.md#contexthub-utils-json) Funktionen zum Serialisieren von Objekten zu Zeichenfolgen und zum Deserialisieren von Zeichenfolgen zu Objekten. Verwenden Sie diese Klasse zur Behandlung von JSON-Daten, um Browser zu unterstützen, die nativ nicht über die Funktionen `JSON.parse` und `JSON.stringify` verfügen.

## Interagieren mit ContextHub-Stores {#interacting-with-contexthub-stores}

Verwenden Sie das JavaScript-Objekt [`ContextHub`](contexthub-api.md#ui-event-constants), um einen Store als JavaScript-Objekt abzurufen. Nach dem Abrufen des Store-Objekts können Sie die darin enthaltenen Daten bearbeiten. Verwenden Sie zum Abrufen des Stores die Funktion [`getAllStores`](contexthub-api.md#getallstores) oder [`getStore`](contexthub-api.md#getstore-name).

### Zugreifen auf Store-Daten {#accessing-store-data}

Die JavaScript-Klasse [`ContexHub.Store.Core`](contexthub-api.md#contexthub-store-core) definiert mehrere Funktionen für die Interaktion mit Store-Daten. Die folgenden Funktionen ermöglichen das Speichern und Abrufen mehrerer in Objekten enthaltener Datenelemente:

* [addAllItems](contexthub-api.md#addallitems-tree-options)
* [getTree](contexthub-api.md#gettree-includeinternals)

Einzelne Datenelemente werden als Satz von Schlüssel/Wert-Paaren gespeichert. Um Werte zu speichern und abzurufen, geben Sie den entsprechenden Schlüssel an:

* [getItem](contexthub-api.md#getitem-key)
* [setItem](contexthub-api.md#setitem-key-value-options)

Beachten Sie, dass benutzerdefinierte Speicherkandidaten weitere Funktionen definieren können, die den Zugriff auf Speicherdaten ermöglichen.

>[!NOTE]
>
>ContextHub kennt nicht standardmäßig die aktuell angemeldeten Benutzer, die auf Veröffentlichungs-Servern verwendet werden, und diese Benutzer werden von ContextHub als &quot;Anonym&quot;betrachtet.
>
>Sie können ContextHub über angemeldete Benutzer informieren, indem Sie den Profil-Store laden. Den Beispiel-Code finden Sie [auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### ContextHub-Ereignisse {#contexthub-eventing}

ContextHub enthält ein Ereignis-Framework, das automatische Reaktionen auf Store-Ereignisse ermöglicht. Jedes Store-Objekt enthält ein Objekt vom Typ [`ContextHub.Utils.Eventing`](contexthub-api.md#contexthub-utils-eventing), das als Eigenschaft [`eventing`](contexthub-api.md#eventing) des Stores verfügbar ist. Verwenden Sie die Funktion [`on`](contexthub-api.md#on-name-handler-selector-triggerforpastevents) oder [`once`](contexthub-api.md#once-name-handler-selector-triggerforpastevents), um eine JavaScript-Funktion an ein Store-Ereignis zu binden.

## Bearbeiten von Cookies mithilfe von ContextHub {#using-context-hub-to-manipulate-cookies}

Die ContextHub JavaScript API bietet Browser-übergreifende Unterstützung für die Behandlung der Cookies von Browsern. Der Namespace [`ContextHub.Utils.Cookie`](contexthub-api.md#contexthub-utils-cookie) definiert eine Reihe von Funktionen zum Erstellen, Bearbeiten und Löschen von Cookies.

## Ermitteln aufgelöster ContextHub-Segmente {#determining-resolved-contexthub-segments}

Mit der ContextHub-Segment-Engine können Sie ermitteln, welche der registrierten Segmente im aktuellen Kontext aufgelöst werden. Verwenden Sie die Funktion „getResolvedSegments“ der Klasse [`ContextHub.SegmentEngine.SegmentManager`](contexthub-api.md#contexthub-segmentengine-segmentmanager), um aufgelöste Segmente abzurufen. Verwenden Sie anschließend die Funktion `getName` oder `getPath` der Klasse [`ContextHub.SegmentEngine.Segment`](contexthub-api.md#contexthub-segmentengine-segment), um auf ein Segment zu testen.

### ContextHub-Segmente {#contexthub-segments}

ContextHub-Segmente werden unter dem Knoten `/conf/<site>/settings/wcm/segments` installiert.

Die folgenden Segmente werden mit der [WKND-Tutorial-Site](/help/implementing/developing/introduction/develop-wknd-tutorial.md) installiert.

* summer
* winter

Die Regeln zur Auflösung dieser Segmente werden wie folgt zusammengefasst:

* Zunächst wird der [geolocation](sample-stores.md#contexthub-geolocation-sample-store-candidate)-Store zur Bestimmung des Breitengrads des Benutzers verwendet.
* Dann bestimmt das Datenelement für den Monat des [surferinfo](sample-stores.md#contexthub-surferinfo-sample-store-candidate)-Stores, in welcher Jahreszeit sich dieser Breitengrad befindet.

>[!WARNING]
>
>Die installierten Segmente werden als Referenzkonfigurationen bereitgestellt, um Ihnen bei der Erstellung einer eigenen dedizierten Konfiguration für Ihr Projekt zu helfen, und sollten daher nicht direkt verwendet werden.

## Debuggen von ContextHub {#debugging-contexthub}

Es gibt verschiedene Optionen zum Debugging von ContextHub, einschließlich der Erstellung von Protokollen. Weitere Informationen finden Sie unter [Konfigurieren von ContextHub](configuring-contexthub.md#logging-debug-messages-for-contexthub).

## Überblick über das ContextHub-Framework {#see-an-overview-of-the-contexthub-framework}

ContextHub bietet eine [Diagnoseseite](contexthub-diagnostics.md), auf der Sie einen Überblick über das ContextHub-Framework erhalten.
