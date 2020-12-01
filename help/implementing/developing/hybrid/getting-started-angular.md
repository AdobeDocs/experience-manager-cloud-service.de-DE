---
title: Erste Schritte mit SPAs in AEM unter Verwendung von Angular
description: In diesem Artikel wird ein Beispiel SPA Anwendung vorgestellt, erklärt, wie sie zusammengestellt wird, und es wird Ihnen ermöglicht, mit dem Angular-Framework schnell eine eigene SPA einzurichten.
translation-type: tm+mt
source-git-commit: cdd92032c627740c66de7b2f3836fa1dcd2ee2ca
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 43%

---


# Erste Schritte mit SPAs in AEM unter Verwendung von Angular {#getting-started-with-spas-in-aem-using-angular}

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwickler möchten in der Lage sein, Websites mithilfe von SPA-Frameworks zu erstellen, und Autoren möchten Inhalte innerhalb von AEM für eine Website, die mit SPA-Frameworks erstellt wurde, nahtlos bearbeiten.

Die SPA-Erstellungsfunktion bietet eine umfassende Lösung zur Unterstützung von SPAs in AEM. In diesem Artikel wird eine vereinfachte SPA Anwendung für das Angular-Framework vorgestellt, die erklärt, wie sie zusammengestellt wird, sodass Sie sich schnell mit Ihrer eigenen SPA vertraut machen können.

>[!NOTE]
>
>Dieser Artikel basiert auf dem Angular-Framework. Das entsprechende Dokument für das React Framework finden Sie unter [Erste Schritte mit SPA in AEM - React](getting-started-react.md).

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

Dieses Dokument durchläuft die Struktur eines vereinfachten SPA und zeigt, wie es funktioniert, sodass Sie dieses Verständnis auf Ihre eigenen SPA anwenden können.

## Abhängigkeiten, Konfiguration und Aufbau {#dependencies-configuration-and-building}

Zusätzlich zur erwarteten Angular-Abhängigkeit kann der SPA zusätzliche Bibliotheken nutzen, um die Erstellung der SPA effizienter zu gestalten.

### Abhängigkeiten {#dependencies}

Die `package.json`-Datei definiert die Anforderungen des gesamten SPA. Die erforderlichen AEM Abhängigkeiten sind hier aufgelistet.

```
"dependencies": {
  "@adobe/aem-angular-editable-components": "~1.0.3",
  "@adobe/aem-spa-component-mapping": "~1.0.5",
  "@adobe/aem-spa-page-model-manager": "~1.0.3"
}
```

Das `aem-clientlib-generator` wird genutzt, um die Erstellung von Client-Bibliotheken als Teil des Build-Prozesses automatisch zu gestalten.

`"aem-clientlib-generator": "^1.4.1",`

Weitere Details dazu können [hier auf GitHub](https://github.com/wcm-io-frontend/aem-clientlib-generator) gefunden werden.

`aem-clientlib-generator` wird wie folgt in der Datei `clientlib.config.js` konfiguriert:

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

Für jedes AEM-Projekt sollte der [AEM-Projektarchetyp](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/archetype/overview.html) genutzt werden, der SPA-Projekte mithilfe von React oder Angular unterstützt und das SPA SDK verwendet.

## Programmstruktur {#application-structure}

Wenn Sie die Abhängigkeiten einbeziehen und Ihre App wie oben beschrieben erstellen, erhalten Sie ein funktionierendes SPA, das Sie in Ihre AEM Instanz hochladen können.

Im nächsten Abschnitt dieses Dokuments erfahren Sie, wie eine SPA in AEM strukturiert ist, welche wichtigen Dateien die Anwendung antreiben und wie sie zusammenarbeiten.

Eine vereinfachte Bildkomponente wird als Beispiel verwendet, aber alle Komponenten der Anwendung basieren auf demselben Konzept.

### app.module.ts {#app-module-ts}

Der Einstiegspunkt in die SPA ist die `app.module.ts` Datei, die hier vereinfacht angezeigt wird, um sich auf den wichtigen Inhalt zu konzentrieren.

```
// app.module.ts
import { BrowserModule, BrowserTransferStateModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { SpaAngularEditableComponentsModule } from '@adobe/aem-angular-editable-components';
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

Die `app.module.ts`-Datei ist der Ausgangspunkt der App und enthält die anfängliche Projektkonfiguration und verwendet `AppComponent`, um die App zu bootstrapping durchzuführen.

#### Statische Instanziierung {#static-instantiation}

Wenn die Komponente mit der Komponentenvorlage statisch instanziiert wird, muss der Wert vom Modell an die Eigenschaften der Komponente übergeben werden. Die Werte des Modells werden als Attribute übergeben, die später als Komponenteneigenschaften verfügbar sein sollen.

### app.component.ts {#app-component-ts}

Sobald `app.module.ts` Bootstraps `AppComponent` gestartet wurde, kann die App initialisiert werden, was hier in einer vereinfachten Version angezeigt wird, um sich auf den wichtigen Inhalt zu konzentrieren.

```
// app.component.ts
import { Component } from '@angular/core';
import { ModelManager } from '@adobe/aem-spa-page-model-manager';
import { Constants } from "@adobe/aem-angular-editable-components";

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

Durch die Verarbeitung der Seite werden `app.component.ts`-Aufrufe `main-content.component.ts` hier in einer vereinfachten Version aufgelistet.

```
import { Component } from '@angular/core';
import { ModelManagerService }     from '../model-manager.service';
import { ActivatedRoute } from '@angular/router';
import { Constants } from "@adobe/aem-angular-editable-components";

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

Das `Page` besteht aus Komponenten. Wenn die JSON-Komponente ingested ist, kann die `Page` diese Komponenten wie `image.component.ts` wie hier gezeigt verarbeiten.

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

Die zentrale Idee von SPAs in AEM ist die Idee, SPA-Komponenten auf AEM-Komponenten abzubilden und die Komponente zu aktualisieren, wenn der Inhalt geändert wird (und umgekehrt). Eine Zusammenfassung dieses Kommunikationsmodells finden Sie im Dokument [SPA Editor Overview](editor-overview.md).

`MapTo('my-angular-app/components/image')(Image, ImageEditConfig);`

Die `MapTo`-Methode ordnet die SPA-Komponente der AEM-Komponente zu. Es unterstützt die Verwendung einer einzelnen Zeichenfolge oder eines Arrays von Zeichenfolgen.

`ImageEditConfig` ist ein Konfigurationsobjekt, das dazu beiträgt, die Authoring-Funktionen einer Komponente zu aktivieren, indem die erforderlichen Metadaten bereitgestellt werden, damit der Editor Platzhalter generieren kann

Wenn kein Inhalt vorhanden ist, werden Etiketten als Platzhalter bereitgestellt, um den leeren Inhalt darzustellen.

#### Dynamisch übergebene Eigenschaften {#dynamically-passed-properties}

Die vom Modell stammenden Daten werden dynamisch als Eigenschaften der Komponente übergeben.

### image.component.html {#image-component-html}

Schließlich kann das Bild in `image.component.html` gerendert werden.

```
// image.component.html
<img [src]="src" [alt]="alt" [title]="title"/>
```

## Freigeben von Informationen zwischen SPA Komponenten {#sharing-information-between-spa-components}

Es ist regelmäßig erforderlich, dass Komponenten in einer Einzelseitenanwendung Informationen austauschen. Es gibt mehrere empfohlene Methoden, um dies zu tun, wie folgt in steigender Reihenfolge der Komplexität aufgeführt.

* **Option 1:** Zentralisieren Sie die Logik und senden Sie sie an die erforderlichen Komponenten, indem Sie beispielsweise eine util-Klasse als reine objektorientierte Lösung verwenden.
* **Option 2: Komponentenstatus mithilfe einer Statusbibliothek wie NgRx** freigeben
* **Option 3:** Nutzen Sie die Objekthierarchie durch Anpassen und Erweitern der Container-Komponente.

## Nächste Schritte {#next-steps}

* [Erste Schritte mit SPAs in AEM unter Verwendung von React](getting-started-react.md) zeigt, wie unter Verwendung von React eine einfache SPA für die Zusammenarbeit mit dem SPA-Editor in AEM erstellt wird.
* [SPA-Editor – Überblick](editor-overview.md) liefert genauere Informationen zum Kommunikationsmodell zwischen AEM und der SPA.
* [WKND-SPA-Projekt](wknd-tutorial.md) ist ein Schritt-für-Schritt-Tutorial zur Implementierung eines einfachen SPA-Projekts in AEM.
* [Dynamisches Modell zur Komponentenzuordnung für SPAs](model-to-component-mapping.md) erläutert das dynamische Modell zur Komponentenzuordnung und die Funktionsweise innerhalb von SPAs in AEM.
* [SPA-Blueprint](blueprint.md) liefert gründlichere Informationen zur Funktionsweise des SPA SDK für AEM, falls Sie SPAs für ein anderes Framework als React oder Angular implementieren möchten oder einfach ein genaueres Verständnis wünschen.
