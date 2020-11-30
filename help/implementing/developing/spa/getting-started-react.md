---
title: Erste Schritte mit SPAs in AEM unter Verwendung von React
description: In diesem Artikel wird ein Beispiel SPA Anwendung vorgestellt, erklärt, wie sie zusammengestellt wird, und es wird Ihnen ermöglicht, mit dem React Framework schnell eine eigene SPA zu entwickeln.
translation-type: tm+mt
source-git-commit: 8bdb7bbe80a4e22bb2b750c0719c6db745133392
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 52%

---


# Erste Schritte mit SPAs in AEM unter Verwendung von React {#getting-started-with-spas-in-aem-using-react}

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwickler möchten in der Lage sein, Websites mithilfe von SPA-Frameworks zu erstellen, und Autoren möchten Inhalte innerhalb von AEM für eine Website, die mit SPA-Frameworks erstellt wurde, nahtlos bearbeiten.

Die SPA-Erstellungsfunktion bietet eine umfassende Lösung zur Unterstützung von SPAs in AEM. In diesem Artikel wird eine vereinfachte SPA Anwendung im React Framework vorgestellt, die erklärt, wie sie zusammengestellt wird, sodass Sie sich schnell mit Ihrer eigenen SPA vertraut machen können.

>[!NOTE]
>
>Dieser Artikel basiert auf dem React Framework. Das entsprechende Dokument für das Angular-Framework finden Sie unter [Erste Schritte mit SPA in AEM - Angular](getting-started-angular.md).

## Einführung {#introduction}

Dieser Artikel fasst die grundlegenden Funktionen einer einfachen SPA und die Grundlagen zusammen, die Sie für deren Nutzung benötigen.

Weitere Informationen zur Funktionsweise SPA in AEM finden Sie in den folgenden Dokumenten:

* [Einführung in SPAs und exemplarische Anleitung](introduction.md)
* [SPA-Editor – Überblick](editor-overview.md)
* [SPA-Blueprint](blueprint.md)

>[!NOTE]
>
>Um Inhalte innerhalb einer SPA erstellen zu können, müssen die Inhalte in AEM gespeichert und vom Inhaltsmodell bereitgestellt werden.
>
>Eine SPA, die außerhalb von AEM entwickelt wurde, kann nicht genehmigt werden, wenn sie den Content-Modell-Vertrag nicht einhält.

Dieses Dokument durchläuft die Struktur einer vereinfachten SPA, die mithilfe des React Frameworks erstellt wurde, und veranschaulicht, wie sie funktioniert, sodass Sie dieses Verständnis auf Ihre eigenen SPA anwenden können.

## Abhängigkeiten, Konfiguration und Aufbau {#dependencies-configuration-and-building}

Zusätzlich zur erwarteten React-Abhängigkeit kann die Beispiel-SPA zusätzliche Bibliotheken nutzen, um die Erstellung der SPA effizienter zu gestalten.

### Abhängigkeiten {#dependencies}

Die `package.json` Datei definiert die Anforderungen des gesamten SPA. Die AEM Abhängigkeiten für ein funktionierendes SPA sind hier aufgelistet.

```
  "dependencies": {
    "@adobe/aem-react-editable-components": "~1.0.4",
    "@adobe/aem-spa-component-mapping": "~1.0.5",
    "@adobe/aem-spa-page-model-manager": "~1.0.3"
  }
```

Da dieses Beispiel auf dem React-Framework basiert, gibt es zwei reaktionsspezifische Abhängigkeiten, die in der Datei `package.json` obligatorisch sind:

```
 react
 react-dom
```

The `aem-clientlib-generator` is leveraged to make the creation of client libraries automatic as part of the build process.

`"aem-clientlib-generator": "^1.4.1",`

Weitere Details dazu können [hier auf GitHub](https://github.com/wcm-io-frontend/aem-clientlib-generator) gefunden werden.

The `aem-clientlib-generator` is configured in the `clientlib.config.js` file as follows.

```
module.exports = {
    // default working directory (can be changed per 'cwd' in every asset option)
    context: __dirname,

    // path to the clientlib root folder (output)
    clientLibRoot: "./../content/jcr_root/apps/my-react-app/clientlibs",

    libs: {
        name: "my-react-app",
        allowProxy: true,
        categories: ["my-react-app"],
        embed: ["my-react-app.responsivegrid"],
        jsProcessor: ["min:gcc"],
        serializationFormat: "xml",
        assets: {
            js: [
                "dist/**/*.js"
            ],
            css: [
                "dist/**/*.css"
            ]
        }
    }
};
```

### Erstellung {#building}

Bei der Erstellung der App wird neben dem aem-clientlib-generator zur automatischen Client-Bibliothekserstellung auch [Webpack](https://webpack.js.org/) für die Übertragung verwendet. Daher ähnelt der Aufbaubefehl dem folgenden:

`"build": "webpack && clientlib --verbose"`

Sobald das Paket erstellt wurde, kann es in eine AEM-Instanz hochgeladen werden.

### AEM-Projektarchetyp {#aem-project-archetype}

Für jedes AEM-Projekt sollte der [AEM-Projektarchetyp](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/archetype/overview.html) genutzt werden, der SPA-Projekte mithilfe von React oder Angular unterstützt und das SPA SDK verwendet.

## Programmstruktur {#application-structure}

Wenn Sie die Abhängigkeiten einbeziehen und Ihre App wie oben beschrieben erstellen, erhalten Sie ein funktionierendes SPA, das Sie in Ihre AEM Instanz hochladen können.

Im nächsten Abschnitt dieses Dokuments erfahren Sie, wie eine SPA in AEM strukturiert ist, welche wichtigen Dateien die Anwendung antreiben und wie sie zusammenarbeiten.

Eine vereinfachte Bildkomponente wird als Beispiel verwendet, aber alle Komponenten der Anwendung basieren auf demselben Konzept.

### index.js {#index-js}

Der Einstiegspunkt in die SPA ist natürlich die hier gezeigte Datei `index.js`, die sich auf den wichtigen Inhalt konzentriert.

```
import ReactDOM from 'react-dom';
import App from './App';
import { ModelManager, Constants } from "@adobe/aem-spa-page-model-manager";

...

ModelManager.initialize().then((pageModel) => {
ReactDOM.render(
    <App cqChildren={pageModel[Constants.CHILDREN_PROP]} cqItems={pageModel[Constants.ITEMS_PROP]} cqItemsOrder={pageModel[Constants.ITEMS_ORDER_PROP]} cqPath={ModelManager.rootPath} locationPathname={ window.location.pathname }/>
, document.getElementById('page'));

});
```

Die Hauptfunktion von `index.js` ist die Verwendung der Funktion `ReactDOM.render`, um zu bestimmen, wo im DOM die Anwendung injiziert werden soll.

Dies ist eine Standardverwendung dieser Funktion, nicht nur für diese Beispielanwendung.

#### Statische Instanziierung {#static-instantiation}

Wenn die Komponente mit der Komponentenvorlage (z. B. JSX) statisch instanziiert wird, muss der Wert vom Modell an die Eigenschaften der Komponente übergeben werden.

### App.js {#app-js}

Beim Rendern der App ruft `index.js` `App.js` auf, die hier in einer vereinfachten Version angezeigt wird, um die Erläuterung auf den wesentlichen Inhalt zu reduzieren.

```
import {Page, withModel } from '@adobe/aem-react-editable-components';

...

class App extends Page {
...
}

export default withModel(App);
```

`App.js` dient in erster Linie dazu, die Stammkomponenten einzuschließen, aus denen die App erstellt wird. Der Einstiegspunkt einer App ist die Seite.

### Page.js {#page-js}

Durch Rendern der Seite werden `App.js` Aufrufe in einer vereinfachten Version `Page.js` angezeigt.

```
import {Page, MapTo, withComponentMappingContext } from "@adobe/aem-react-editable-components";

...

class AppPage extends Page {
...
}

MapTo('my-react-app/components/structure/page')(withComponentMappingContext(AppPage));
```

In diesem Beispiel erweitert sich die `AppPage` Klasse `Page`, die die Methoden des inneren Inhalts enthält, die dann verwendet werden können.

Der `Page` nimmt die JSON-Repräsentation des Seitenmodells auf und verarbeitet den Inhalt, um jedes Element der Seite zu umhüllen/dekorieren. Weitere Details zum `Page` finden Sie im Dokument [SPA-Blueprint.](blueprint.md)

### Image.js {#image-js}

Mit der gerenderten Seite können die Komponenten wie `Image.js` wie hier dargestellt gerendert werden.

```
import React, {Component} from 'react';
import {MapTo} from '@adobe/aem-react-editable-components';

require('./Image.css');

const ImageEditConfig = {

    emptyLabel: 'Image',

    isEmpty: function() {
        return !this.props || !this.props.src || this.props.src.trim().length < 1;
    }
};

class Image extends Component {

    render() {
        return (<img src={this.props.src}>);
    }
}

MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);
```

Die zentrale Idee von SPAs in AEM ist die Idee, SPA-Komponenten auf AEM-Komponenten abzubilden und die Komponente zu aktualisieren, wenn der Inhalt geändert wird (und umgekehrt). Eine Zusammenfassung dieses Kommunikationsmodells finden Sie unter Übersicht über das Dokument [SPA Editor](editor-overview.md) .

`MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);`

Die `MapTo`-Methode ordnet die SPA-Komponente der AEM-Komponente zu. Es unterstützt die Verwendung einer einzelnen Zeichenfolge oder eines Arrays von Zeichenfolgen.

`ImageEditConfig` ist ein Konfigurationsobjekt, das dazu beiträgt, die Authoring-Funktionen einer Komponente zu aktivieren, indem die erforderlichen Metadaten bereitgestellt werden, damit der Editor Platzhalter generieren kann

Wenn kein Inhalt vorhanden ist, werden Etiketten als Platzhalter bereitgestellt, um den leeren Inhalt darzustellen.

#### Dynamisch weitergegebene Eigenschaften {#dynamically-passed-properties}

Die vom Modell stammenden Daten werden dynamisch als Eigenschaften der Komponente übergeben.

## Exportieren bearbeitbarer Inhalte {#exporting-editable-content}

Sie können eine Komponente exportieren und bearbeitbar halten.

```
import React, { Component } from 'react';
import { MapTo } from '@adobe/aem-react-editable-components';

...

const EditConfig = {...}

class PageClass extends Component {...};

...

export default MapTo('my-react-app/react/components/structure/page')(PageClass, EditConfig);
```

The `MapTo` function returns a `Component` which is the result of a composition that extends the provided `PageClass` with the class names and attributes that enable the authoring. Diese Komponente kann exportiert werden, um später im Markup Ihrer Anwendung instanziiert zu werden.

When exported using the `MapTo` or `withModel` functions, the `Page` component, is wrapped with a `ModelProvider` component which provides standard components access to the latest version of the page model or a precise location in that page model.

Weitere Informationen finden Sie im Dokument [SPA-Blueprint](blueprint.md).

>[!NOTE]
>
>Standardmäßig erhalten Sie das gesamte Modell der Komponente, wenn Sie die Funktion `withModel` verwenden.

## Freigeben von Informationen zwischen SPA Komponenten {#sharing-information-between-spa-components}

Es ist regelmäßig erforderlich, dass Komponenten in einer Einzelseitenanwendung Informationen austauschen. Es gibt mehrere empfohlene Methoden, um dies zu tun, wie folgt in steigender Reihenfolge der Komplexität aufgeführt.

* **Option 1:** Zentralisieren Sie die Logik und senden Sie sie an die erforderlichen Komponenten, z. B. mithilfe von &quot;React Context&quot;.
* **Option 2:** Freigeben von Komponentenstatus mithilfe einer Statusbibliothek wie Redux
* **Option 3:** Nutzen Sie die Objekthierarchie durch Anpassen und Erweitern der Container-Komponente.

## Nächste Schritte {#next-steps}

* [Erste Schritte mit SPAs in AEM unter Verwendung von Angular](getting-started-angular.md) zeigt, wie unter Verwendung von Angular eine einfache SPA für die Zusammenarbeit mit dem SPA-Editor in AEM erstellt wird.
* [SPA-Editor – Überblick](editor-overview.md) liefert genauere Informationen zum Kommunikationsmodell zwischen AEM und der SPA.
* [WKND-SPA-Projekt](wknd-tutorial.md) ist ein Schritt-für-Schritt-Tutorial zur Implementierung eines einfachen SPA-Projekts in AEM.
* [Dynamisches Modell zur Komponentenzuordnung für SPAs](model-to-component-mapping.md) erläutert das dynamische Modell zur Komponentenzuordnung und die Funktionsweise innerhalb von SPAs in AEM.
* [SPA-Blueprint](blueprint.md) liefert gründlichere Informationen zur Funktionsweise des SPA SDK für AEM, falls Sie SPAs für ein anderes Framework als React oder Angular implementieren möchten oder einfach ein genaueres Verständnis wünschen.
