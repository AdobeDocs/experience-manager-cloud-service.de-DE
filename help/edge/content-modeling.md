---
title: Inhaltsmodellierung für AEM Authoring mit Edge Delivery Services-Projekten
description: Erfahren Sie, wie die Inhaltsmodellierung für AEM Authoring mit Edge Delivery Services-Projekten funktioniert und wie Sie Ihre eigenen Inhalte modellieren.
exl-id: e68b09c5-4778-4932-8c40-84693db892fd
source-git-commit: 22a631d394de1c0fb934d9703e966c8287aef391
workflow-type: tm+mt
source-wordcount: '2095'
ht-degree: 1%

---

# Inhaltsmodellierung für AEM Authoring mit Edge Delivery Services-Projekten {#content-modeling}

Erfahren Sie, wie die Inhaltsmodellierung für AEM Authoring mit Edge Delivery Services-Projekten funktioniert und wie Sie Ihre eigenen Inhalte modellieren.

{{aem-authoring-edge-early-access}}

## Voraussetzungen {#prerequisites}

Projekte, die AEM Authoring mit Edge Delivery Services verwenden, erben den Großteil der Mechanismen anderer Edge Delivery Services-Projekte, unabhängig von der Inhaltsquelle oder [Authoring-Methode.](/help/edge/authoring.md)

Bevor Sie mit der Modellierung von Inhalten für Ihr Projekt beginnen, lesen Sie zunächst die folgende Dokumentation.

* [Erste Schritte – Entwicklertutorial](/help/edge/developer/tutorial.md)
* [Markup, Abschnitte, Blöcke und automatische Blockerstellung](/help/edge/developer/markup-sections-blocks.md)
* [Blocksammlung](/help/edge/developer/block-collection.md)

Es ist wichtig, diese Konzepte zu verstehen, um ein überzeugendes Inhaltsmodell zu entwickeln, das auf inhaltsquellenunabhängige Weise funktioniert. Dieses Dokument enthält Details zu den Mechanismen, die speziell für AEM Authoring implementiert wurden.

## Standardinhalt {#default-content}

**Standardinhalt** ist Inhalt, den ein Autor intuitiv auf eine Seite platzieren würde, ohne zusätzliche Semantik hinzuzufügen. Dazu gehören Text, Überschriften, Links und Bilder. Solche Inhalte sind in ihrer Funktion und ihrem Zweck selbsterklärend.

In AEM wird dieser Inhalt als Komponenten mit sehr einfachen, vordefinierten Modellen implementiert, die alles enthalten, was in Markdown und HTML serialisiert werden kann.

* **Text**: Rich-Text (einschließlich Listenelementen und starker oder kursiver Text)
* **Titel**: Text, Typ (h1-h6)
* **Bild**: Quelle, Beschreibung
* **Schaltfläche**: Text, Titel, URL, Typ (Standard, primär, sekundär)

Das Modell dieser Komponenten ist Teil der [Vorlage für AEM Authoring mit Edge Delivery Services.](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json#L2-L112)

## Bausteine {#blocks}

Blöcke werden verwendet, um reichhaltigere Inhalte mit bestimmten Stilen und Funktionen zu erstellen. Im Gegensatz zu Standardinhalten erfordern Blöcke keine zusätzliche Semantik. Blöcke können mit [Komponenten im AEM Seiteneditor.](/help/implementing/developing/components/overview.md)

Blöcke sind im Wesentlichen Inhaltselemente, die von JavaScript dekoriert und mit einem Stylesheet formatiert werden.

### Definition des Blockmodells {#model-definition}

Bei Verwendung AEM Authoring mit Edge Delivery Services muss der Inhalt der Bausteine explizit modelliert werden, damit der Autor die Benutzeroberfläche zum Erstellen von Inhalten zur Verfügung stellt. Grundsätzlich müssen Sie ein Modell erstellen, damit die Authoring-Benutzeroberfläche weiß, welche Optionen dem Autor basierend auf dem Block präsentiert werden sollen.

Die [`component-models.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json) -Datei definiert das Blockmodell. Die im Komponentenmodell definierten Felder werden als Eigenschaften in AEM beibehalten und als Zellen in der Tabelle gerendert, aus der sich ein Block zusammensetzt.

```json
{
  "id": "hero",
  "fields": [
    {
      "component": "reference",
      "valueType": "string",
      "name": "image",
      "label": "Image",
      "multi": false
    },
    {
      "component": "text-input",
      "valueType": "string",
      "name": "imageAlt",
      "label": "Alt",
      "value": ""
    },
    {
      "component": "text-area",
      "name": "text",
      "value": "",
      "label": "Text",
      "valueType": "string"
    }
  ]
}
```

Beachten Sie, dass nicht jeder Block über ein Modell verfügen muss. Einige Blöcke sind einfach [container](#container) für eine Liste von untergeordneten Elementen, wobei jedes Kind über ein eigenes Modell verfügt.

Außerdem müssen Sie definieren, welche Blöcke vorhanden sind und mit dem universellen Editor zu einer Seite hinzugefügt werden können. Die [`component-definitions.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-definition.json) -Datei listet die Komponenten so auf, wie sie vom universellen Editor zur Verfügung gestellt werden.

```json
{
  "title": "Hero",
  "id": "hero",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/block/v1/block",
        "template": {
          "name": "Hero",
          "model": "hero"
        }
      }
    }
  }
}
```

Es ist möglich, ein Modell für viele Blöcke zu verwenden. Einige Blöcke können beispielsweise ein Modell verwenden, das einen Text und ein Bild definiert.

Für jeden Baustein hat der Entwickler folgende Möglichkeiten:

* Muss die `core/franklin/components/block/v1/block` Ressourcentyp, die generische Implementierung der Blocklogik in AEM.
* Muss den Blocknamen definieren, der in der Tabellenüberschrift des Blocks wiedergegeben wird.
   * Der Blockname wird verwendet, um den richtigen Stil und das richtige Skript zum Dekorieren des Blocks abzurufen.
* Kann eine [Modell-ID.](/help/implementing/universal-editor/field-types.md#model-structure)
   * Die Modell-ID ist ein Verweis auf das Modell der Komponente, das die Felder definiert, die dem Autor in der Eigenschaftenleiste zur Verfügung stehen.
* Kann eine [Filter-ID.](/help/implementing/universal-editor/customizing.md#filtering-components)
   * Die Filter-ID ist ein Verweis auf den Filter der Komponente, der es ermöglicht, das Authoring-Verhalten zu ändern, z. B. indem begrenzt wird, welche untergeordneten Elemente zum Block oder Abschnitt hinzugefügt werden können oder welche RTE-Funktionen aktiviert sind.

Alle diese Informationen werden in AEM gespeichert, wenn ein Block zu einer Seite hinzugefügt wird. Wenn der Ressourcentyp oder der Blockname fehlt, wird der Block nicht auf der Seite gerendert.

>[!WARNING]
>
>Es ist zwar möglich, benutzerdefinierte AEM-Komponenten zu implementieren, ist jedoch weder erforderlich noch zu empfehlen. Die Komponenten für die von AEM bereitgestellten Edge Delivery Services sind ausreichend und bieten bestimmte Schutzschienen, um die Entwicklung zu erleichtern.
>
>Die von AEM bereitgestellten Komponenten rendern ein Markup, das von [helix-html2md](https://github.com/adobe/helix-html2md) beim Veröffentlichen in Edge Delivery Services und durch [aem.js](https://github.com/adobe/aem-boilerplate/blob/main/scripts/aem.js) beim Laden einer Seite im Universal Editor. Das Markup ist der stabile Vertrag zwischen AEM und den anderen Teilen des Systems und ermöglicht keine Anpassungen. Aus diesem Grund dürfen Projekte die Komponenten nicht ändern und keine benutzerdefinierten Komponenten verwenden.

### Blockstruktur {#block-structure}

Die Eigenschaften von Blöcken sind [definiert in den Komponentenmodellen](#model-definition) und als solche in AEM beibehalten. Eigenschaften werden als Zellen in der tabellenähnlichen Struktur des Blocks gerendert.

#### Einfache Blöcke {#simple}

Im einfachsten Formular rendert ein Block jede Eigenschaft in einer einzelnen Zeile/Spalte in der Reihenfolge, in der die Eigenschaften im Modell definiert sind.

Im folgenden Beispiel wird das Bild zuerst im Modell und dann in der Textzeile definiert. Sie werden also mit dem Bild zuerst und Text danach gerendert.

>[!BEGINTABS]

>[!TAB Daten]

```json
{
  "name": "Hero",
  "model": "hero",
  "image": "/content/dam/image.png",
  "imageAlt": "Helix - a shape like a corkscrew",
  "text": "<h1>Welcome to AEM</h1>"
}
```

>[!TAB Markup]

```html
<div class="hero">
  <div>
    <div>
      <picture>
        <img src="/content/dam/image.png" alt="Helix - a shape like a corkscrew">
      </picture>
    </div>
  </div>
  <div>
    <div>
      <h1>Welcome to AEM</h1>
    </div>
  </div>
</div>
```

>[!TAB Verzeichnis]

```text
+---------------------------------------------+
| Hero                                        |
+=============================================+
| ![Helix - a shape like a corkscrew][image0] |
+---------------------------------------------+
| # Welcome to AEM                            |
+---------------------------------------------+
```

>[!ENDTABS]

Sie werden feststellen, dass einige Werttypen im Markup die Ableitung von Semantik zulassen und Eigenschaften in einzelnen Zellen kombiniert werden. Dieses Verhalten wird im Abschnitt beschrieben [Geben Sie Inference ein.](#type-inference)

#### Schlüssel-Wert-Block {#key-value}

In vielen Fällen wird empfohlen, das gerenderte semantische Markup zu dekorieren, CSS-Klassennamen hinzuzufügen, neue Knoten hinzuzufügen oder sie im DOM zu verschieben und Stile anzuwenden.

In anderen Fällen wird der Block jedoch als eine Schlüssel-Wert-Paar-ähnliche Konfiguration gelesen.

Ein Beispiel hierfür ist die [Abschnitt-Metadaten.](/help/edge/developer/markup-sections-blocks.md#sections) In diesem Anwendungsfall kann der Block so konfiguriert werden, dass er als Schlüssel-Wert-Paar-Tabelle dargestellt wird. Siehe Abschnitt . [Abschnitte und Abschnittsmetadaten](#sections-metadata) für weitere Informationen.

>[!BEGINTABS]

>[!TAB Daten]

```json
{
  "name": "Featured Articles",
  "model": "spreadsheet-input",
  "key-value": true,
  "source": "/content/site/articles.json",
  "keywords": ['Developer','Courses'],
  "limit": 4
}
```

>[!TAB Markup]

```html
<div class="featured-articles">
  <div>
    <div>source</div>
    <div><a href="/content/site/articles.json">/content/site/articles.json</a></div>
  </div>
  <div>
    <div>keywords</div>
    <div>Developer,Courses</div>
  <div>
  <div>
    <div>limit</div>
    <div>4</div>
  </div>
</div>
```

>[!TAB Verzeichnis]

```text
+-----------------------------------------------------------------------+
| Featured Articles                                                     |
+=======================================================================+
| source   | [/content/site/articles.json](/content/site/articles.json) |
+-----------------------------------------------------------------------+
| keywords | Developer,Courses                                          |
+-----------------------------------------------------------------------+
| limit    | 4                                                          |
+-----------------------------------------------------------------------+
```

>[!ENDTABS]

#### Container-Blöcke {#container}

Beide vorherigen Strukturen haben eine einzige Dimension: die Liste der Eigenschaften. Container-Blöcke ermöglichen das Hinzufügen von untergeordneten Elementen (normalerweise vom gleichen Typ oder Modell) und sind daher zweidimensional. Diese Blöcke unterstützen weiterhin ihre eigenen Eigenschaften, die zuerst als Zeilen mit einer einzelnen Spalte gerendert werden. Sie ermöglichen jedoch auch das Hinzufügen von untergeordneten Elementen, für die jedes Element als Zeile und jede Eigenschaft als Spalte in dieser Zeile gerendert wird.

Im folgenden Beispiel akzeptiert ein Block eine Liste verknüpfter Symbole als untergeordnete Elemente, wobei jedes verknüpfte Symbol über ein Bild und einen Link verfügt. Beachten Sie die [Filter-ID](/help/implementing/universal-editor/customizing.md#filtering-components) in den Daten des Blocks eingestellt werden, um auf die Filterkonfiguration zu verweisen.

>[!BEGINTABS]

>[!TAB Daten]

```json
{
  "name": "Our Partners",
  "model": "text-only",
  "filter": "our-partners",
  "text": "<p>Our community of partners is ...</p>",
  "item_0": {
    "model": "linked-icon",
    "image": "/content/dam/partners/foo.png",
    "imageAlt": "Icon of Foo",
    "link": "https://foo.com/"
  },
  "item_1": {
    "model": "linked-icon"
    "image": "/content/dam/partners/bar.png",
    "imageAlt": "Icon of Bar",
    "link": "https://bar.com"
  }
}
```

>[!TAB Markup]

```html
<div class="our-partners">
  <div>
    <div>
        Our community of partners is ...
    </div>
  </div>
  <div>
    <div>
      <picture>
         <img src="/content/dam/partners/foo.png" alt="Icon of Foo">
      </picture>
    </div>
    <div>
      <a href="https://foo.com">https://foo.com</a>
    </div>
  </div>
  <div>
    <div>
      <picture>
         <img src="/content/dam/partners/bar.png" alt="Icon of Bar">
      </picture>
    </div>
    <div>
      <a href="https://bar.com">https://bar.com</a>
    </div>
  </div>
</div>
```

>[!TAB Verzeichnis]

```text
+------------------------------------------------------------ +
| Our Partners                                                |
+=============================================================+
| Our community of partners is ...                            |
+-------------------------------------------------------------+
| ![Icon of Foo][image0] | [https://foo.com](https://foo.com) |
+-------------------------------------------------------------+
| ![Icon of Bar][image1] | [https://bar.com](https://bar.com) |
+-------------------------------------------------------------+
```

>[!ENDTABS]

### Erstellen Semantischer Inhaltsmodelle für Blöcke {#creating-content-models}

Mit dem [erläuterte Funktionsweise der Blockstruktur,](#block-structure) Es ist möglich, ein Inhaltsmodell zu erstellen, das die in AEM 1:1 gespeicherten Inhalte der Bereitstellungsebene zuordnet.

Zu Beginn jedes Projekts muss ein Inhaltsmodell für jeden Block sorgfältig überdacht werden. Sie muss unabhängig von der Inhaltsquelle und dem Authoring-Erlebnis sein, damit Autoren sie wechseln oder kombinieren können, während Blockimplementierungen und -stile wiederverwendet werden. Weitere Informationen und allgemeine Leitlinien finden Sie unter [David&#39;s Model (nimm 2).](https://www.aem.live/docs/davidsmodel) Genauer gesagt, wird die [Blocksammlung](/help/edge/developer/block-collection.md) enthält einen umfangreichen Satz an Inhaltsmodellen für spezifische Anwendungsfälle gängiger Benutzeroberflächenmuster.

AEM Authoring mit Edge Delivery Services wirft dies die Frage auf, wie ein überzeugendes semantisches Inhaltsmodell bereitgestellt werden kann, wenn die Informationen mit Formularen erstellt werden, die aus mehreren Feldern bestehen, anstatt semantisches Markup im Kontext wie Rich Text zu bearbeiten.

Zur Lösung dieses Problems gibt es drei Methoden, die die Erstellung eines überzeugenden Inhaltsmodells erleichtern:

* [Typeinsicht](#type-inference)
* [Feldausblendung](#field-collapse)
* [Elementgruppierung](#element-grouping)

>[!NOTE]
>
>Blockimplementierungen können den Inhalt dekonstruieren und den Block durch ein clientseitig gerendertes DOM ersetzen. Dies ist zwar für Entwickler möglich und intuitiv, für Edge Delivery Services jedoch nicht die beste Vorgehensweise.

#### Typeinsicht {#type-inference}

Für einige Werte können wir die semantische Bedeutung aus den Werten selbst ableiten. Zu diesen Werten gehören:

* **Bilder** - Wenn ein Verweis auf eine Ressource in AEM ein Asset mit einem MIME-Typ ist, der mit `image/`, wird der Verweis als `<picture><img src="${reference}"></picture>`.
* **Links** - Wenn eine Referenz in AEM vorhanden ist und kein Bild ist oder wenn der Wert mit `https?://`  oder `#`, wird der Verweis als `<a href="${reference}">${reference}</a>` .
* **Rich-Text** - Wenn ein abgeschnittener Wert mit einem Absatz beginnt (`p`, `ul`, `ol`, `h1`-`h6`usw.), wird der Wert als Rich-Text gerendert.
* **Klassennamen** - die `classes` -Eigenschaft wird als Blockoptionen behandelt und in der Tabellenüberschrift für [einfache Blöcke,](#simple) oder als Werteliste für Elemente in einer [Container-Block.](#container)
* **Wertlisten** - Wenn ein Wert eine Eigenschaft mit mehreren Werten ist und der erste Wert keiner der vorherigen ist, werden alle Werte als kommagetrennte Liste verkettet.

Alles andere wird als Text gerendert.

#### Feldausblendung {#field-collapse}

Beim Ausblenden von Feldern werden mehrere Feldwerte basierend auf einer Namenskonvention mithilfe der Suffixe zu einem einzigen semantischen Element zusammengefasst. `Title`, `Type`, `MimeType`, `Alt`, und `Text` (Groß-/Kleinschreibung beachten). Jede Eigenschaft, die mit einem dieser Suffixe endet, gilt nicht als Wert, sondern als Attribut einer anderen Eigenschaft.

##### Bilder {#image-collapse}

>[!BEGINTABS]

>[!TAB Daten]

```json
{
  "image": "/content/dam/red-car.png",
  "imageAlt: "A red card on a road"
}
```

>[!TAB Markup]

```html
<picture>
  <img src="/content/dam/red-car.png" alt="A red car on a road">
</picture>
```

>[!TAB Verzeichnis]

```text
![A red car on a road][image0]
```

>[!ENDTABS]

##### Links und Schaltflächen {#links-buttons-collapse}

>[!BEGINTABS]

>[!TAB Daten]

```json
{
  "link": "https://www.adobe.com",
  "linkTitle": "Navigate to adobe.com",
  "linkText": "adobe.com",
  "linkType": "primary"
}
```

>[!TAB Markup]

Nein `linkType`oder `linkType=default`

```html
<a href="https://www.adobe.com" title="Navigate to adobe.com">adobe.com</a>
```

`linkType=primary`

```html
<strong>
  <a href="https://www.adobe.com" title="Navigate to adobe.com">adobe.com</a>
</strong>
```

`linkType=secondary`

```html
<em>
  <a href="https://www.adobe.com" title="Navigate to adobe.com">adobe.com</a>
</em>
```

>[!TAB Verzeichnis]

```text
[adobe.com](https://www.adobe.com "Navigate to adobe.com")
**[adobe.com](https://www.adobe.com "Navigate to adobe.com")**
_[adobe.com](https://www.adobe.com "Navigate to adobe.com")_
```

>[!ENDTABS]

##### Überschriften {#headings-collapse}

>[!BEGINTABS]

>[!TAB Daten]

```json
{
  "heading": "Getting started",
  "headingType": "h2"
}
```

>[!TAB Markup]

```html
<h2>Getting started</h2>
```

>[!TAB Verzeichnis]

```text
## Getting started
```

>[!ENDTABS]

#### Elementgruppierung {#element-grouping}

while [Feldausfall](#field-collapse) Bei der Elementgruppierung geht es darum, mehrere Eigenschaften zu einem einzigen semantischen Element zu kombinieren. Dabei geht es darum, mehrere semantische Elemente zu einer einzigen Zelle zu verketten. Dies ist besonders hilfreich in Anwendungsfällen, in denen der Autor in der Art und Anzahl der Elemente, die er erstellen kann, eingeschränkt werden sollte.

Beispielsweise kann eine Teaser-Komponente dem Autor erlauben, nur einen Untertitel, einen Titel und eine einzelne Absatzbeschreibung sowie maximal zwei Aktionsaufruf-Schaltflächen zu erstellen. Wenn Sie diese Elemente gruppieren, erhalten Sie ein semantisches Markup, das ohne weitere Maßnahmen formatiert werden kann.

Die Elementgruppierung verwendet eine Benennungsregel, bei der der Gruppenname durch einen Unterstrich von jeder Eigenschaft in der Gruppe getrennt wird. Das Reduzieren der Eigenschaften in einer Gruppe funktioniert wie zuvor beschrieben.

>[!BEGINTABS]

>[!TAB Daten]

```json
{
  "name": "teaser",
  "model": "teaser",
  "image": "/content/dam/teaser-background.png",
  "imageAlt": "A group of people sitting on a stage",
  "teaserText_subtitle": "Adobe Experience Cloud"
  "teaserText_title": "Meet the Experts"
  "teaserText_titleType": "h2"
  "teaserText_description": "<p>Join us in this ask me everything session...</p>"
  "teaserText_cta1": "https://link.to/more-details",
  "teaserText_cta1Text": "More Details"
  "teaserText_cta2": "https://link.to/sign-up",
  "teaserText_cta2Text": "RSVP",
  "teaserText_cta2Type": "primary"
}
```

>[!TAB Markup]

```html
<div class="teaser">
  <div>
    <div>
      <picture>
        <img src="/content/dam/teaser-background.png" alt="A group of people sitting on a stage">
      </picture>
    </div>
  </div>
  <div>
    <div>
      <p>Adobe Experience Cloud</p>
      <h2>Meet the Experts</h2>
      <p>Join us in this ask me everything session ...</p>
      <p><a href="https://link.to/more-details">More Details</a></p>
      <p><strong><a href="https://link.to/sign-up">RSVP</a></strong></p>
    </div>
  </div>
</div>
```

>[!TAB Verzeichnis]

```text
+-------------------------------------------------+
| Teaser                                          |
+=================================================+
| ![A group of people sitting on a stage][image0] |
+-------------------------------------------------+
| Adobe Experience Cloud                          |
| ## Welcome to AEM                               |
| Join us in this ask me everything session ...   |
| [More Details](https://link.to/more-details)    |
| [RSVP](https://link.to/sign-up)                 |
+-------------------------------------------------+
```

>[!ENDTABS]

## Abschnitte und Abschnittsmetadaten {#sections-metadata}

Auf die gleiche Weise wie Entwickler mehrere [Blöcke,](#blocks) Sie können verschiedene Abschnitte definieren.

Das Inhaltsmodell von Edge Delivery Services lässt absichtlich nur eine Verschachtelungsebene zu, d. h. alle Standardinhalte oder -bausteine, die in einem Abschnitt enthalten sind. Um komplexere visuelle Komponenten zu erhalten, die andere Komponenten enthalten können, müssen sie daher als Abschnitte modelliert und mithilfe der clientseitigen automatischen Blockierung kombiniert werden. Typische Beispiele hierfür sind Tabulatoren und ausblendbare Abschnitte wie Akkordeons.

Ein Abschnitt kann auf die gleiche Weise wie ein Block definiert werden, jedoch mit dem Ressourcentyp von `core/franklin/components/section/v1/section`. Abschnitte können einen Namen und eine [Filter-ID,](/help/implementing/universal-editor/customizing.md#filtering-components) die von der [Universal Editor](/help/implementing/universal-editor/introduction.md) nur sowie eine [Modell-ID,](/help/implementing/universal-editor/field-types.md#model-structure) wird zum Rendern der Abschnittsmetadaten verwendet. Das Modell ist auf diese Weise das Modell des Bereichs-Metadatenblocks, der automatisch als Schlüssel-Wert-Block an einen Abschnitt angehängt wird, wenn dieser nicht leer ist.

Die [model-ID](/help/implementing/universal-editor/field-types.md#model-structure) und [Filter-ID](/help/implementing/universal-editor/customizing.md#filtering-components) des Standardabschnitts `section`. Sie kann verwendet werden, um das Verhalten des Standardabschnitts zu ändern. Im folgenden Beispiel werden dem Abschnitt-Metadatenmodell einige Stile und ein Hintergrundbild hinzugefügt.

```json
{
  "id": "section",
  "fields": [
    {
      "component": "multiselect",
      "name": "style",
      "value": "",
      "label": "Style",
      "valueType": "string",
      "options": [
        {
          "name": "Fade in Background",
          "value": "fade-in"
        },
        {
          "name": "Highlight",
          "value": "highlight"
        }
      ]
    },
    {
      "component": "reference",
      "valueType": "string",
      "name": "background",
      "label": "Image",
      "multi": false
    }
  ]
}
```

Im folgenden Beispiel wird ein Registerkartenabschnitt definiert, der zum Erstellen eines Tabulatorblocks verwendet werden kann, indem aufeinander folgende Abschnitte mit einem Tab-Titel-Datenattribut während der automatischen Blockierung in einen Tabulatorblock kombiniert werden.

```json
{
  "title": "Tab",
  "id": "tab",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/section/v1/section",
        "template": {
          "name": "Tab",
          "model": "tab",
          "filter": "section"
        }
      }
    }
  }
}
```

## Seitenmetadaten {#page-metadata}

Dokumente können eine Seite enthalten [Metadatenblock,](/help/edge/authoring.md#metadata--seo) , mit dem definiert wird, welche `<meta>` -Elemente werden im `<head>` einer Seite. Die Seiteneigenschaften von Seiten in AEM as a Cloud Service sind denen zugeordnet, die standardmäßig für Edge Delivery Services verfügbar sind, z. B. `title`, `description`, `keywords`, usw.

Bevor Sie weitere Informationen zum Definieren Ihrer eigenen Metadaten erhalten, lesen Sie zunächst die folgenden Dokumente, um das Konzept der Seitenmetadaten zu verstehen.

* [Metadaten](https://www.aem.live/developer/block-collection/metadata)
* [Massenmetadaten](/help/edge/docs/bulk-metadata.md)

Es ist auch möglich, zusätzliche Seitenmetadaten auf zwei Arten zu definieren.

### Metadaten-Tabellen {#metadata-spreadsheets}

Es ist möglich, Metadaten anhand von Pfaden oder Pfadmustern in AEM as a Cloud Service tabellenähnlicher Weise zu definieren. Es gibt eine Authoring-Benutzeroberfläche für tabellenähnliche Daten, die Excel oder Google Tabellen ähneln.

Um eine solche Tabelle zu erstellen, erstellen Sie eine Seite und verwenden Sie die Metadatenvorlage in der Sites-Konsole.

Definieren Sie in den Seiteneigenschaften des Arbeitsblatts die benötigten Metadatenfelder zusammen mit der URL. Fügen Sie dann Metadaten pro Seitenpfad oder Seitenpfadmuster hinzu.

Stellen Sie sicher, dass das Arbeitsblatt Ihrer Pfadzuordnung hinzugefügt wird, bevor Sie es veröffentlichen.

```json
{
  "mappings": [
    "/content/site/:/",
    "/content/site/metadata:/metadata.json"
  ]
}
```

### Seiteneigenschaften {#page-properties}

Viele der in AEM verfügbaren Standardseiteneigenschaften werden den entsprechenden Seitenmetadaten in einem Dokument zugeordnet. Das umfasst beispielsweise `title`, `description`, `robots`, `canonical url` oder `keywords`. Einige AEM-spezifische Eigenschaften sind ebenfalls verfügbar:

* `cq:lastModified` as `modified-time` im ISO8601-Format
* Der Zeitpunkt der letzten Veröffentlichung des Dokuments als `published-time` im ISO8601-Format
* `cq:tags` as `cq-tags` als kommagetrennte Liste der Tag-IDs.

Es ist auch möglich, ein Komponentenmodell für benutzerdefinierte Seitenmetadaten zu definieren, das dem Autor als Registerkarte des Dialogfelds &quot;Seiteneigenschaften&quot;von AEM Sites zur Verfügung gestellt wird.

Erstellen Sie dazu ein Komponentenmodell mit der ID `page-metadata`.

```json
{
  "id": "page-metadata",
  "fields": [
    {
      "component": "text",
      "name": "theme",
      "label": "Theme"
    }
  ]
}
```
