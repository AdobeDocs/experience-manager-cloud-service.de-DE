---
title: Inhaltsmodellierung für WYSIWYG-Authoring-Projekte mit Edge Delivery Services
description: Erfahren Sie, wie die Inhaltsmodellierung für WYSIWYG-Authoring-Projekte mit Edge Delivery Services funktioniert und wie Sie eigene Inhalte modellieren.
exl-id: e68b09c5-4778-4932-8c40-84693db892fd
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 384f8a1301ea488e0b2aa493389d090896fe3b33
workflow-type: tm+mt
source-wordcount: '2195'
ht-degree: 100%

---


# Inhaltsmodellierung für WYSIWYG-Authoring-Projekte mit Edge Delivery Services {#content-modeling}

Erfahren Sie, wie die Inhaltsmodellierung für WYSIWYG-Authoring-Projekte mit Edge Delivery Services funktioniert und wie Sie eigene Inhalte modellieren.

## Voraussetzungen {#prerequisites}

Projekte, die WYSIWYG-Authoring mit Edge Delivery Services verwenden, erben den Großteil der Mechanismen anderer Edge Delivery Services-Projekte, und zwar unabhängig von der Inhaltsquelle oder [Authoring-Methode](/help/edge/wysiwyg-authoring/authoring.md).

Bevor Sie mit der Modellierung von Inhalten für Ihr Projekt beginnen, lesen Sie zunächst Folgendes:

* [Erste Schritte – Entwickler-Tutorial](/help/edge/developer/tutorial.md)
* [Markup, Abschnitte, Blöcke und automatische Blockerstellung](/help/edge/developer/markup-sections-blocks.md)
* [Blocksammlung](/help/edge/developer/block-collection.md)

Es ist wichtig, diese Konzepte zu verstehen, um ein überzeugendes Inhaltsmodell zu entwickeln, das unabhängig von Inhaltsquellen funktioniert. Dieses Dokument enthält Details zu den Mechanismen, die speziell für das WYSIWYG-Authoring implementiert wurden.

## Standardinhalt {#default-content}

**Standardinhalt** ist Inhalt, den eine Autorin oder ein Autor intuitiv auf eine Seite platzieren würde, ohne zusätzliche Semantik hinzuzufügen. Dazu gehören Text, Überschriften, Links und Bilder. Solche Inhalte sind in ihrer Funktion und ihrem Zweck selbsterklärend.

In AEM werden diese Inhalte als Komponenten mit sehr einfachen, vordefinierten Modellen implementiert, die alles enthalten, was in Markdown und HTML serialisiert werden kann.

* **Text**: Rich-Text (einschließlich Listenelementen und fett oder kursiv formatiertem Text)
* **Titel**: Text, Typ (h1-h6)
* **Bild**: Quelle, Beschreibung
* **Schaltfläche**: Text, Titel, URL, Typ (Standard, primär, sekundär)

Das Modell dieser Komponenten ist Teil der [Vorlage für das WYSIWYG-Authoring mit Edge Delivery Services](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json#L2-L112).

## Bausteine {#blocks}

Blöcke werden verwendet, um vielfältigere Inhalte mit bestimmten Stilen und Funktionen zu erstellen. Im Gegensatz zu Standardinhalten erfordern Bausteine keine zusätzliche Semantik.

Blöcke sind im Wesentlichen Inhaltselemente, die von JavaScript dekoriert und mit einem Stylesheet formatiert werden.

### Definition des Blockmodells {#model-definition}

Beim WYSIWYG-Authoring mit Edge Delivery Services muss der Inhalt der Bausteine explizit modelliert werden, damit der Autorin oder dem Autor die Benutzeroberfläche zur Inhaltserstellung zur Verfügung gestellt wird. Grundsätzlich müssen Sie ein Modell erstellen, damit die Authoring-Benutzeroberfläche weiß, welche Optionen der Autorin oder dem Autor basierend auf dem Block präsentiert werden sollen.

Die Datei [`component-models.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json) definiert das Blockmodell. Die im Komponentenmodell definierten Felder werden als Eigenschaften in AEM beibehalten und als Zellen in der Tabelle gerendert, aus der sich ein Block zusammensetzt.

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

Nicht jeder Block muss über ein Modell verfügen. Einige Blöcke sind einfach [Container](#container) für eine Liste von untergeordneten Elementen. Dabei hat jedes untergeordnete Element ein eigenes Modell.

Außerdem müssen Sie definieren, welche Blöcke vorhanden sind und mit dem universellen Editor zu einer Seite hinzugefügt werden können. Die Datei [`component-definitions.json`](/help/implementing/universal-editor/component-definition.md) listet die Komponenten so auf, wie sie vom universellen Editor zur Verfügung gestellt werden.

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

Es ist möglich, ein Modell für eine Vielzahl von Blöcken zu verwenden. Einige Blöcke können beispielsweise ein gemeinsames Modell haben, das einen Text und ein Bild definiert.

Für jeden Block gilt Folgendes:

* Die Entwicklerin oder der Entwickler muss den Ressourcentyp `core/franklin/components/block/v1/block` verwenden, die generische Implementierung der Blocklogik in AEM.
* Die Entwicklerin oder der Entwickler muss den Blocknamen definieren, der in der Tabellenüberschrift des Blocks gerendert wird.
   * Anhand des Blocknamens werden der richtige Stil und das richtige Skript zum Dekorieren des Blocks abgerufen.
* Die Entwicklerin oder der Entwickler kann eine [Modell-ID](/help/implementing/universal-editor/field-types.md#model-structure) definieren.
   * Die Modell-ID ist ein Verweis auf das Modell der Komponente, die die Felder definiert, die der Autorin bzw. dem Autor im Bedienfeld „Eigenschaften“ zur Verfügung stehen.
* Die Entwicklerin oder der Entwickler kann eine [Filter-ID](/help/implementing/universal-editor/filtering.md) definieren.
   * Die Filter-ID ist ein Verweis auf den Filter der Komponente, der es ermöglicht, das Authoring-Verhalten zu ändern, z. B. indem begrenzt wird, welche untergeordneten Elemente zum Block oder Abschnitt hinzugefügt werden können oder welche RTE-Funktionen aktiviert sind.

Alle diese Informationen werden in AEM gespeichert, wenn ein Block zu einer Seite hinzugefügt wird. Wenn der Ressourcentyp oder der Blockname fehlt, wird der Block nicht auf der Seite gerendert.

>[!WARNING]
>
>Es ist zwar möglich, benutzerdefinierte AEM-Komponenten zu implementieren, was jedoch weder erforderlich noch zu empfehlen ist. Die von AEM für Edge Delivery Services bereitgestellten Komponenten sind ausreichend und bieten bestimmte Mechanismen für eine einfachere Entwicklung.
>
>Sie rendern ein Markup, das beim Veröffentlichen in Edge Delivery Services von [helix-html2md](https://github.com/adobe/helix-html2md) und beim Laden einer Seite im universellen Editor von [aem.js](https://github.com/adobe/aem-boilerplate/blob/main/scripts/aem.js) genutzt werden kann. Das Markup ist der stabile Kontrakt zwischen AEM und den anderen Teilen des Systems und lässt keine Anpassungen zu. Aus diesem Grund dürfen Projekte die Komponenten nicht ändern und keine benutzerdefinierten Komponenten verwenden.

### Blockstruktur {#block-structure}

Die Eigenschaften von Blöcken sind [in den Komponentenmodellen definiert](#model-definition) und werden als solche in AEM beibehalten. Eigenschaften werden als Zellen in der tabellenähnlichen Struktur des Blocks gerendert.

#### Einfache Blöcke {#simple}

In der einfachsten Form rendert ein Block jede Eigenschaft in einer Zeile/Spalte in der Reihenfolge, in der die Eigenschaften im Modell definiert sind.

Im folgenden Beispiel wird zuerst das Bild im Modell und dann der Text definiert. An diese Reihenfolge wird sich auch beim Rendern gehalten.

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

>[!TAB Tabelle]

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

Sie stellen möglicherweise fest, dass einige Werttypen die Ableitung von Semantik im Markup zulassen und Eigenschaften in einzelnen Zellen kombiniert werden. Dieses Verhalten wird unter [Typableitung](#type-inference) beschrieben.

#### Schlüssel-Wert-Block {#key-value}

In vielen Fällen wird empfohlen, das gerenderte semantische Markup zu dekorieren, CSS-Klassennamen hinzuzufügen, neue Knoten hinzuzufügen oder sie im DOM zu verschieben und Stile anzuwenden.

In anderen Fällen wird der Block jedoch als eine Schlüssel-Wert-Paar-ähnliche Konfiguration gelesen.

Ein Beispiel hierfür sind die [Abschnittsmetadaten.](/help/edge/developer/markup-sections-blocks.md#sections) In diesem Anwendungsfall kann der Block so konfiguriert werden, dass er als Schlüssel-Wert-Paar-Tabelle gerendert wird. Weitere Informationen finden Sie unter [Abschnitte und Abschnittsmetadaten](#sections-metadata).

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

>[!TAB Tabelle]

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

Beide vorherigen Strukturen haben eine einzige Dimension: die Liste der Eigenschaften. Container-Blöcke ermöglichen das Hinzufügen von untergeordneten Elementen (normalerweise vom gleichen Typ oder Modell) und sind daher zweidimensional. Diese Blöcke unterstützen weiterhin ihre eigenen Eigenschaften, die zuerst als Zeilen mit einer Spalte gerendert werden. Sie ermöglichen jedoch auch das Hinzufügen von untergeordneten Elementen, für die jedes Element als Zeile und jede Eigenschaft als Spalte in dieser Zeile gerendert wird.

Im folgenden Beispiel akzeptiert ein Block eine Liste verknüpfter Symbole als untergeordnete Elemente. Dabei verfügt jedes verknüpfte Symbol über ein Bild und einen Link. Achten Sie auf die in den Daten des Blocks festgelegte [Filter-ID](/help/implementing/universal-editor/filtering.md). Darüber wird auf die Filterkonfiguration verwiesen.

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

>[!TAB Tabelle]

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

### Erstellen semantischer Inhaltsmodelle für Blöcke {#creating-content-models}

Auf Grundlage der [erläuterten Mechanismen der Blockstruktur](#block-structure) ist es nun möglich, ein Inhaltsmodell zu erstellen, das die in AEM gespeicherten Inhalte der Bereitstellungsebene eins zu eins zuordnet.

In der Frühphase jedes Projekts muss ein Inhaltsmodell für jeden Block sorgfältig überdacht werden. Es muss unabhängig von der Inhaltsquelle und dem Authoring-Erlebnis sein. Nur so können sie von Autorinnen und Autoren gewechselt oder kombiniert werden, bei Wiederverwendung von Blockimplementierungen und Stilen. Weitere Informationen und allgemeine Leitlinien finden Sie unter [Davids Modell (Take 2).](https://www.aem.live/docs/davidsmodel) Genauer gesagt, enthält die [Blocksammlung](/help/edge/developer/block-collection.md) einen umfangreichen Satz an Inhaltsmodellen für spezifische Anwendungsfälle gängiger Benutzeroberflächenmuster.

Beim WYSIWYG-Authoring mit Edge Delivery Services wirft dies die Frage auf, wie ein überzeugendes semantisches Inhaltsmodell bereitgestellt werden kann, wenn die Informationen mit aus mehreren Feldern bestehenden Formularen erstellt werden, anstatt semantisches Markup so wie Rich-Text kontextbezogen zu bearbeiten.

Zur Lösung dieses Problems gibt es drei Methoden, die die Erstellung eines überzeugenden Inhaltsmodells erleichtern:

* [Typableitung](#type-inference)
* [Ausblendung von Feldern](#field-collapse)
* [Elementgruppierung](#element-grouping)

>[!NOTE]
>
>Blockimplementierungen können den Inhalt dekonstruieren und den Block durch ein Client-seitig gerendertes DOM ersetzen. Dies ist zwar für Entwickelnde möglich und intuitiv, für Edge Delivery Services jedoch nicht die beste Vorgehensweise.

#### Typableitung {#type-inference}

Für einige Werte kann die semantische Bedeutung aus den Werten selbst abgeleitet werden. Zu solchen Werten zählen:

* **Bilder**: Wenn eine Referenz auf eine Ressource in AEM ein Asset mit einem MIME-Typ ist, der mit `image/` beginnt, wird die Referenz als `<picture><img src="${reference}"></picture>` gerendert.
* **Links**: Wenn eine Referenz in AEM vorhanden ist, die kein Bild ist, oder wenn der Wert mit `https?://` oder `#` beginnt, wird die Referenz als `<a href="${reference}">${reference}</a>` gerendert.
* **Rich-Text**: Wenn ein abgeschnittener Wert mit einem Absatz beginnt (`p`, `ul`, `ol`, `h1`-`h6` usw.), wird der Wert als Rich-Text gerendert.
* **Klassennamen**: Die `classes`-Eigenschaft wird als [Blockoptionen](/help/edge/developer/markup-sections-blocks.md#block-options) behandelt und in der Tabellenkopfzeile für [einfache Blöcke](#simple) bzw. als Werteliste für Elemente in einem [Container-Block gerendert.](#container) Sie ist nützlich, wenn Sie [einen Block anders gestalten](/help/edge/wysiwyg-authoring/create-block.md#block-options), aber keinen völlig neuen Block erstellen möchten.
* **Wertelisten**: Wenn es sich bei einem Wert um eine Eigenschaft mit mehreren Werten handelt und der erste Wert keiner der vorherigen ist, werden alle Werte als kommagetrennte Liste verkettet.

Alles andere wird als einfacher Text gerendert.

#### Ausblendung von Feldern {#field-collapse}

Beim Ausblenden von Feldern werden mehrere Feldwerte basierend auf einer Namenskonvention mithilfe der Suffixe `Title`, `Type`, `MimeType`, `Alt` und `Text` (unter Berücksichtigung der Groß- und Kleinschreibung) zu einem einzigen semantischen Element zusammengefasst. Jede Eigenschaft, die mit einem dieser Suffixe endet, wird nicht als Wert, sondern als Attribut einer anderen Eigenschaft betrachtet.

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

>[!TAB Tabelle]

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

Kein `linkType` oder `linkType=default`

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

>[!TAB Tabelle]

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

>[!TAB Tabelle]

```text
## Getting started
```

>[!ENDTABS]

#### Elementgruppierung {#element-grouping}

Bei der [Ausblendung von Feldern](#field-collapse) werden mehrere Eigenschaften zu einem einzigen semantischen Element kombiniert, wohingegen es bei der Elementgruppierung darum geht, mehrere semantische Elemente zu einer einzigen Zelle zu verketten. Dies ist besonders hilfreich in Anwendungsfällen, in denen die Autorin oder der Autor in Bezug auf Art und Anzahl der Elemente, die sie bzw. er erstellen kann, eingeschränkt werden soll.

Beispielsweise kann eine Teaser-Komponente der Autorin oder dem Autor erlauben, nur einen Untertitel, einen Titel und eine einzelne Absatzbeschreibung sowie maximal zwei Aktionsaufruf-Schaltflächen zu erstellen. Wenn Sie diese Elemente gruppieren, erhalten Sie ein semantisches Markup, das ohne weitere Maßnahmen formatiert werden kann.

Die Elementgruppierung verwendet eine Namenskonvention, bei der der Gruppenname durch einen Unterstrich von jeder Eigenschaft in der Gruppe getrennt wird. Die Ausblendung der Felder für die Eigenschaften in einer Gruppe funktioniert wie zuvor beschrieben.

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

>[!TAB Tabelle]

```text
+-------------------------------------------------+
| Teaser                                          |
+=================================================+
| ![A group of people sitting on a stage][image0] |
+-------------------------------------------------+
| Adobe Experience Cloud                          |
| ## Meet the Experts                             |
| Join us in this ask me everything session ...   |
| [More Details](https://link.to/more-details)    |
| [RSVP](https://link.to/sign-up)                 |
+-------------------------------------------------+
```

>[!ENDTABS]

## Abschnitte und Abschnittsmetadaten {#sections-metadata}

Entwickelnde können verschiedene Abschnitte auf die gleiche Weise definieren, auf die sie auch mehrere [Blöcke](#blocks) definieren und modellieren.

Das Inhaltsmodell von Edge Delivery Services lässt absichtlich nur eine einzige Verschachtelungsebene zu, d. h. jeder Standard-Content oder -block, der in einem Abschnitt enthalten ist. Um komplexere visuelle Komponenten zu erhalten, die andere Komponenten enthalten können, müssen diese daher als Abschnitte modelliert und mithilfe der Client-seitigen automatischen Blockerstellung kombiniert werden. Typische Beispiele hierfür sind Registerkarten und ausblendbare Abschnitte wie Akkordeons.

Ein Abschnitt kann auf die gleiche Weise wie ein Block definiert werden, jedoch mit dem Ressourcentyp `core/franklin/components/section/v1/section`. Abschnitte können einen Namen und eine [Filter-ID](/help/implementing/universal-editor/filtering.md) haben, die nur vom [universellen Editor](/help/implementing/universal-editor/introduction.md) verwendet wird, sowie eine [Modell-ID](/help/implementing/universal-editor/field-types.md#model-structure), die zum Rendern der Abschnittsmetadaten verwendet wird. Das Modell ist auf diese Weise das Modell des Bereichsmetadatenblocks, der automatisch als Schlüssel-Wert-Block an einen Abschnitt angehängt wird, wenn dieser nicht leer ist.

Die [Modell-ID](/help/implementing/universal-editor/field-types.md#model-structure) und [Filter-ID](/help/implementing/universal-editor/filtering.md) des Standardabschnitts ist `section`. Sie kann verwendet werden, um das Verhalten des Standardabschnitts zu ändern. Im folgenden Beispiel werden dem Abschnittsmetadatenmodell einige Stile und ein Hintergrundbild hinzugefügt.

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

Im folgenden Beispiel wird ein Registerkartenabschnitt definiert, der zum Erstellen eines Registerkartenblocks verwendet werden kann, indem aufeinander folgende Abschnitte mit einem Registerkartentitel-Datenattribut während der automatischen Blockerstellung in einen Registerkartenblock kombiniert werden.

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

Dokumente können eine Seite [Metadatenblock](https://www.aem.live/developer/block-collection/metadata) enthalten, mit der definiert wird, welche `<meta>`-Elemente im `<head>` einer Seite gerendert werden. Die Seiteneigenschaften von Seiten in AEM as a Cloud Service sind denen zugeordnet, die standardmäßig für Edge Delivery Services verfügbar sind, z. B. `title`, `description`, `keywords`.

Bevor Sie weitere Informationen zum Definieren Ihrer eigenen Metadaten erhalten, lesen Sie zunächst die folgenden Dokumente, um das Konzept der Seitenmetadaten zu verstehen.

* [Metadaten](https://www.aem.live/developer/block-collection/metadata)
* [Massenmetadaten](/help/edge/docs/bulk-metadata.md)

Es ist auch möglich, zusätzliche Seitenmetadaten auf zwei Arten zu definieren.

### Metadaten-Tabellen {#metadata-spreadsheets}

Es ist möglich, Metadaten in AEM as a Cloud Service anhand von Pfaden oder Pfadmustern auf tabellenähnliche Weise zu definieren. Es gibt eine Authoring-Benutzeroberfläche für tabellenähnliche Daten, die Excel- oder Google-Tabellen ähneln.

Weitere Informationen finden Sie im Dokument [Verwenden von Tabellen zur Verwaltung von Tabellendaten](/help/edge/wysiwyg-authoring/tabular-data.md).

### Seiteneigenschaften {#page-properties}

Viele der in AEM verfügbaren Standardseiteneigenschaften werden den entsprechenden Seitenmetadaten in einem Dokument zugeordnet. Das umfasst beispielsweise `title`, `description`, `robots`, `canonical url` oder `keywords`. Einige AEM-spezifische Eigenschaften sind ebenfalls verfügbar:

* `cq:lastModified` als `modified-time` im ISO8601-Format
* Zeitpunkt der letzten Veröffentlichung des Dokuments als `published-time` im ISO8601-Format
* `cq:tags` als `cq-tags` als kommagetrennte Liste der Tag-IDs.

Es ist auch möglich, ein Komponentenmodell für benutzerdefinierte Seitenmetadaten zu definieren, das der Autorin oder dem Autor im universellen Editor zur Verfügung gestellt wird.

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

## Nächste Schritte {#next-steps}

Nachdem Sie nun wissen, wie Sie Inhalte modellieren, können Sie Bausteine für Ihre eigenen Edge Delivery Service-Projekte mit WYSIWYG-Authoring erstellen.

Im Dokument [Erstellen von für den universellen Editor instrumentierten Bausteinen](/help/edge/wysiwyg-authoring/create-block.md) erfahren Sie, wie Sie Bausteine erstellen, die für die Verwendung mit dem universellen Editor in WYSIWYG-Authoring mit Edge Delivery Services-Projekten instrumentiert sind.

Wenn Sie bereits mit der Erstellung von Blöcken vertraut sind, lesen Sie bitte das [Erste-Schritte-Handbuch für Entwickelnde zum WYSIWYG-Authoring mit Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md), um Ihnen den Start mit einer neuen Adobe Experience Manager-Site zu erleichtern, wobei Sie Edge Delivery Services und den universellen Editor für die Erstellung von Inhalten verwenden.

>[!TIP]
>
>Eine durchgängige Anleitung zum Erstellen eines neuen Edge Delivery Services-Projekts, das für WYSIWYG-Authoring mit AEM as a Cloud Service als Inhaltsquelle aktiviert ist, finden Sie in [diesem AEM GEMs-Webinar](https://experienceleague.adobe.com/de/docs/events/experience-manager-gems-recordings/gems2024/wysiwyg-authoring-and-edge-delivery).

