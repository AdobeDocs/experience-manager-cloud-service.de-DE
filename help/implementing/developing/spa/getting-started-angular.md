---
title: Erste Schritte mit SPAs in AEM Verwenden von Angular
description: In diesem Artikel wird eine Beispielanwendung für die SPA vorgestellt, erklärt, wie sie zusammengestellt wird, und es wird Ihnen ermöglicht, mit dem Angular-Framework schnell eine eigene SPA-Anwendung einzurichten.
translation-type: tm+mt
source-git-commit: ccde1459090bb9f801d753cb7314e2bc7249f72e
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 27%

---


# Erste Schritte mit SPAs in AEM Verwenden von Angular {#getting-started-with-spas-in-aem-using-angular}

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwickler möchten in der Lage sein, Websites mithilfe von SPA-Frameworks zu erstellen, und Autoren möchten Inhalte innerhalb von AEM für eine Website, die mit SPA-Frameworks erstellt wurde, nahtlos bearbeiten.

Die SPA-Erstellungsfunktion bietet eine umfassende Lösung zur Unterstützung von SPAs in AEM. In diesem Artikel wird eine vereinfachte SPA-Anwendung für das Angular-Framework vorgestellt, die erklärt, wie sie zusammengestellt wird, sodass Sie sich schnell mit Ihrer eigenen SPA vertraut machen können.

>[!NOTE]
>
>Dieser Artikel basiert auf dem Angular-Framework. Das entsprechende Dokument für das React Framework finden Sie unter [Erste Schritte mit SPAs in AEM - Reaktion](getting-started-react.md).

## Einführung {#introduction}

Dieser Artikel fasst die grundlegenden Funktionen einer einfachen SPA und die Grundlagen zusammen, die Sie für deren Nutzung benötigen.

Weitere Informationen über die Funktionsweise von BSG in AEM finden Sie in den folgenden Dokumenten:

* [Einführung und exemplarische Vorgehensweisen zu SPA](introduction.md)
* [SPA-Editor – Überblick](editor-overview.md)
* [SPA-Blueprint](blueprint.md)

>[!NOTE]
>
>Um Inhalte innerhalb einer SPA erstellen zu können, müssen die Inhalte in AEM gespeichert und vom Inhaltsmodell bereitgestellt werden.
>
>Eine außerhalb von AEM entwickelte SPA ist nicht zulässig, wenn sie den Vertrag über das Inhaltsmodell nicht einhält.

In diesem Dokument wird die Struktur eines vereinfachten BSG erläutert, wie es funktioniert, sodass Sie dieses Verständnis auf Ihr eigenes BSG anwenden können.

## Abhängigkeiten, Konfiguration und Aufbau {#dependencies-configuration-and-building}

Zusätzlich zur erwarteten Angular-Abhängigkeit kann die Beispiel-SPA zusätzliche Bibliotheken nutzen, um die Erstellung der SPA effizienter zu gestalten.

### Abhängigkeiten {#dependencies}

Die `package.json` Datei definiert die Anforderungen des gesamten SPA-Pakets. Die erforderlichen AEM Abhängigkeiten sind hier aufgelistet.

```
"dependencies": {
  "@adobe/cq-angular-editable-components": "~1.0.3",
  "@adobe/cq-spa-component-mapping": "~1.0.3",
  "@adobe/cq-spa-page-model-manager": "~1.0.4"
}
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
    clientLibRoot: "./../content/jcr_root/apps/my-angular-app/clientlibs",

    libs: {
        name: "my-angular-app",
        allowProxy: true,
        categories: ["my-angular-app"],
        embed: ["my-angular-app.responsivegrid"],
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

`"build": "ng build --build-optimizer=false && clientlib",`

Sobald das Paket erstellt wurde, kann es in eine AEM-Instanz hochgeladen werden.

### AEM-Projektarchetyp {#aem-project-archetype}

Jedes AEM Projekt sollte den [AEM Project Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)nutzen, der SPA-Projekte mit React oder Angular unterstützt und das SPA-SDK nutzt.

## Anwendungsstruktur {#application-structure}

Wenn Sie die Abhängigkeiten einbeziehen und Ihre App wie oben beschrieben erstellen, erhalten Sie ein funktionierendes SPA-Paket, das Sie in Ihre AEM Instanz hochladen können.

Im nächsten Abschnitt dieses Dokuments erfahren Sie, wie eine SPA in AEM strukturiert ist, welche wichtigen Dateien die Anwendung antreiben und wie sie zusammenarbeiten.

Eine vereinfachte Bildkomponente wird als Beispiel verwendet, aber alle Komponenten der Anwendung basieren auf demselben Konzept.

### app.module.ts {#app-module-ts}

The entry point into the SPA is the `app.module.ts` file shown here simplified to focus on the important content.

```
// app.module.ts
import { BrowserModule, BrowserTransferStateModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { SpaAngularEditableComponentsModule } from '@adobe/cq-angular-editable-components';
import { AppRoutingModule } from './app-routing.module';

@NgModule({
  imports: [ BrowserModule.withServerTransition({ appId: 'my-angular-app' }),
    SpaAngularEditableComponentsModule,
    AppRoutingModule,
    BrowserTransferStateModule ],
  providers: ...,
  declarations: [ ... ],
  entryComponents: [ ... ],
  bootstrap: [ AppComponent ]
})
export class AppModule {}
```

Die `app.module.ts` Datei ist der Ausgangspunkt der App und enthält die anfängliche Projektkonfiguration und dient zum Bootstrapping der App `AppComponent` .

#### Statische Instanziierung {#static-instantiation}

Wenn die Komponente mit der Komponentenvorlage statisch instanziiert wird, muss der Wert vom Modell an die Eigenschaften der Komponente übergeben werden. Die Werte des Modells werden als Attribute übergeben, die später als Komponenteneigenschaften verfügbar sein sollen.

### app.component.ts {#app-component-ts}

Sobald `app.module.ts` Bootstraps `AppComponent`gestartet wurden, kann die App initialisiert werden, was hier in einer vereinfachten Version angezeigt wird, um sich auf wichtige Inhalte zu konzentrieren.

```
// app.component.ts
import { Component } from '@angular/core';
import { ModelManager } from '@adobe/cq-spa-page-model-manager';
import { Constants } from "@adobe/cq-angular-editable-components";

@Component({
  selector: 'app-root',
  template: `
    <router-outlet></router-outlet>
  `
})

export class AppComponent {
  items;
  itemsOrder;
  path;

  constructor() {
    ModelManager.initialize().then(this.updateData.bind(this));
  }

  private updateData(model) {
    this.path = model[Constants.PATH_PROP];
    this.items = model[Constants.ITEMS_PROP];
    this.itemsOrder = model[Constants.ITEMS_ORDER_PROP];
  }
}
```

### main-content.component.ts {#main-content-component-ts}

Durch die Verarbeitung der Seite werden hier `app.component.ts` aufgeführte Aufrufe in einer vereinfachten Version `main-content.component.ts` aufgerufen.

```
import { Component } from '@angular/core';
import { ModelManagerService }     from '../model-manager.service';
import { ActivatedRoute } from '@angular/router';
import { Constants } from "@adobe/cq-angular-editable-components";

@Component({
  selector: 'app-main',
  template: `
    <aem-page class="structure-page" [attr.data-cq-page-path]="path" [cqPath]="path" [cqItems]="items" [cqItemsOrder]="itemsOrder" ></aem-page>
  `
})

export class MainContentComponent {
  items;
  itemsOrder;
  path;

  constructor( private route: ActivatedRoute,
    private modelManagerService: ModelManagerService) {
    this.modelManagerService.getData({ path: this.route.snapshot.data.path }).then((data) => {
      this.path = data[Constants.PATH_PROP];
      this.items = data[Constants.ITEMS_PROP];
      this.itemsOrder = data[Constants.ITEMS_ORDER_PROP];
    });
  }
}
```

Der `MainComponent` nimmt die JSON-Repräsentation des Seitenmodells auf und verarbeitet den Inhalt, um jedes Element der Seite zu umhüllen/dekorieren. Weitere Details zum `Page` finden Sie im Dokument [SPA-Blueprint](blueprint.md).

### image.component.ts {#image-component-ts}

Das `Page` besteht aus Komponenten. Mit der Integration von JSON `Page` können diese Komponenten verarbeitet werden, wie hier `image.component.ts` dargestellt.

```
/// image.component.ts
import { Component, Input } from '@angular/core';

const ImageEditConfig = {

    emptyLabel: 'Image',

    isEmpty: function(cqModel) {
        return !cqModel || !cqModel.src || cqModel.src.trim().length < 1;
    }
};

@Component({
  selector: 'app-image',
  templateUrl: './image.component.html',
})

export class ImageComponent {
  @Input() src: string;
  @Input() alt: string;
  @Input() title: string;
}

MapTo('my-angular-app/components/image')(ImageComponent, ImageEditConfig);
```

Die zentrale Idee von SPAs in AEM ist die Idee, SPA-Komponenten auf AEM-Komponenten abzubilden und die Komponente zu aktualisieren, wenn der Inhalt geändert wird (und umgekehrt). See the document [SPA Editor Overview](editor-overview.md) for an summary of this communication model.

`MapTo('my-angular-app/components/image')(Image, ImageEditConfig);`

Die `MapTo`-Methode ordnet die SPA-Komponente der AEM-Komponente zu. Es unterstützt die Verwendung einer einzelnen Zeichenfolge oder eines Arrays von Zeichenfolgen.

`ImageEditConfig` ist ein Konfigurationsobjekt, das dazu beiträgt, die Authoring-Funktionen einer Komponente zu aktivieren, indem die erforderlichen Metadaten bereitgestellt werden, damit der Editor Platzhalter generieren kann

Wenn kein Inhalt vorhanden ist, werden Etiketten als Platzhalter bereitgestellt, um den leeren Inhalt darzustellen.

#### Dynamisch weitergegebene Eigenschaften {#dynamically-passed-properties}

Die vom Modell stammenden Daten werden dynamisch als Eigenschaften der Komponente übergeben.

### image.component.html {#image-component-html}

Schließlich kann das Bild gerendert werden `image.component.html`.

```
// image.component.html
<img [src]="src" [alt]="alt" [title]="title"/>
```

## Freigeben von Informationen zwischen SPA-Komponenten {#sharing-information-between-spa-components}

Es ist regelmäßig erforderlich, dass Komponenten in einer Einzelseitenanwendung Informationen austauschen. Es gibt mehrere empfohlene Methoden, um dies zu tun, wie folgt in steigender Reihenfolge der Komplexität aufgeführt.

* **Option 1:** Zentralisieren Sie die Logik und senden Sie sie an die erforderlichen Komponenten, indem Sie beispielsweise eine util-Klasse als reine objektorientierte Lösung verwenden.
* **Option 2:** Freigeben von Komponentenstatus mithilfe einer Statusbibliothek wie NgRx
* **Option 3:** Nutzen Sie die Objekthierarchie durch Anpassen und Erweitern der Container-Komponente.

## Nächste Schritte {#next-steps}

* [Die ersten Schritte mit SPAs in AEM mithilfe von React](getting-started-react.md) zeigen, wie ein grundlegendes SPA für die Arbeit mit dem SPA-Editor in AEM mithilfe von React erstellt wurde.
* [Der SPA Editor-Überblick](editor-overview.md) vertieft das Kommunikationsmodell zwischen AEM und SPA.
* [WKND SPA Project](wknd-tutorial.md) ist ein Schritt-für-Schritt-Tutorial zur Implementierung eines einfachen SPA-Projekts in AEM.
* [Die Zuordnung dynamischer Modelle zu Komponenten für SPAs](model-to-component-mapping.md) erläutert das dynamische Modell zur Komponentenzuordnung und seine Funktionsweise in SPAs in AEM.
* [SPA Blueprint](blueprint.md) Angebots bietet einen tiefen Einblick in die Funktionsweise des SPA SDK for AEM, falls Sie SPAs in AEM für ein anderes Framework als React oder Angular implementieren möchten oder einfach ein tieferes Verständnis wünschen.
