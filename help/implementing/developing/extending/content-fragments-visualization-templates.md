---
title: Erstellen von Visualisierungsvorlagen für Inhaltsfragmente
description: Vorschau und Veröffentlichung von Inhaltsfragmenten mit Visualisierungsvorlagen. Erfahren Sie, wie Sie die Vorlagen erstellen und anpassen können.
feature: Developing, Content Fragments
role: Admin, Developer
source-git-commit: 5413e173ac159015f224845e238779c5dc997ee5
workflow-type: tm+mt
source-wordcount: '2141'
ht-degree: 3%

---

# Visuelle Inhaltsfragmente - Vorlagen {#visual-content-fragments-templates}

In Adobe Experience Manager (AEM) as a Cloud Service können HTML-Vorlagen verwendet werden, um Inhaltsfragmente zu visualisieren und im HTML-Format bereitzustellen.

<!-- CQDOC-23232 - remove when GA -->

>[!NOTE]
>
>Visuelle Inhaltsfragmente und der Auftrag „Figma zu visuellen Inhaltsfragmenten“ sind derzeit nur eingeschränkt verfügbar.
>
>Wenn Sie teilnehmen möchten, senden Sie bitte eine Anfrage von Ihrer offiziellen E-Mail-Adresse an [experience-production-agent@adobe.com](mailto:experience-production-agent@adobe.com).

Mit HTML-Vorlagen können Sie steuern, wie Ihre Inhaltsfragmente angezeigt werden. Sie können HTML-Vorlagen in Ihrem Codeeditor erstellen und diese dann hochladen und Inhaltsfragmentmodellen in AEM zuweisen.  Platzhalter für Inhalte mit Handlebars.js ermöglichen die Zuordnung der Vorlage zu Datentypen im Inhaltsfragmentmodell. Sobald eine Vorlage einem Modell zugewiesen wurde, kann sie mit jedem auf dem Modell basierenden Inhaltsfragment verwendet werden, um das Fragment zu visualisieren oder als modulares Erlebnis im HTML-Format für jeden Kanal bereitzustellen, z. B. Web, E-Mail, Mobile App oder andere.

In diesem Artikel wird erläutert, wie Sie benutzerdefinierte HTML-Vorlagen mit Handlebars-Syntax zum Rendern visueller Inhaltsfragmente erstellen.

Nach dem Erstellen der Vorlagen haben Sie folgende Möglichkeiten:

* [Verwenden von Vorlagen in AEM](#using-a-content-fragment-html-template-in-aem)

* Verwenden Sie die [Veröffentlichungs-URL Ihrer visuellen Inhaltsfragmente](#using-the-visual-content-fragment-publish-url)

>[!NOTE]
>
>Unter [Visuelle Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md) finden Sie Informationen zum Hochladen, Zuweisen und Verwenden Ihrer Vorlage in AEM.

>[!NOTE]
>
>Verwenden Sie den Auftrag [Figma to Visual Content Fragments](/help/ai-in-aem/agents/brand-experience/experience-production/figma-to-visual-content-fragments.md) um das Laden eines HTML-Designs zu automatisieren.

## Was Sie lernen werden {#what-you-will-learn}

Nach einer (sehr kurzen) Einführung in:

* Verwenden Ihrer Vorlagen in AEM
* Verwenden der Veröffentlichungs-URL

Auf dieser Seite wird Folgendes behandelt (detaillierter):

* Handlebars - die erforderlichen Grundlagen der Syntax
* Zugreifen auf Inhaltsfragmentdaten
* Arbeiten mit verschachtelten Inhaltsfragmenten
* Umgang mit Feldern mit mehreren Werten
* Erstellen von Schleifen und bedingter Logik
* Best Practices für den Vorlagenentwurf für Inhaltsfragmente

## Voraussetzungen {#prerequisites}

Um die hier behandelten Technologien zu verstehen und mit ihnen zu arbeiten, benötigen Sie Folgendes:

* Grundlegende Informationen zu HTML
* Vertrautheit mit AEM-Inhaltsfragmenten und Inhaltsfragmentmodellen
* Grundlegendes zu Ihren Inhaltsfragmentmodellen

## Verwenden einer HTML-Vorlage für Inhaltsfragmente {#using-a-content-fragment-html-template}

### Verwenden einer HTML-Vorlage für Inhaltsfragmente in AEM {#using-a-content-fragment-html-template-in-aem}

Weitere Informationen zur Verwendung Ihrer Vorlage in AEM finden Sie unter:

* [Visuelle Inhaltsfragmente - Hochladen und Zuweisen Ihrer Vorlagen](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md)
* [Vorschauaktion für ein ausgewähltes Fragment über die Konsole](/help/sites-cloud/administering/content-fragments/managing.md#actions-selected-content-fragment)
* [Vorschau Ihres Fragments - im Fragment-Editor](/help/sites-cloud/administering/content-fragments/authoring.md#preview-content-fragment)

### Verwenden der Veröffentlichungs-URL für visuelle Inhaltsfragmente {#using-the-visual-content-fragment-publish-url}

Nachdem Sie visuelle Inhaltsfragmente mithilfe der Vorlage erstellt haben, können Sie die [Veröffentlichungs-URL Ihrer visuellen Inhaltsfragmente“ ](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md).

## Handlebars - die (sehr) Grundlagen {#handlebars-the-very-basics}

Handlebars ist eine einfache Vorlagensprache, die geschweifte Klammern (`{{ }}`) verwendet, um dynamische Inhalte in HTML einzufügen.

### Grundlegende Syntax {#basic-syntax}

Ein Beispiel für die grundlegende Handlebars-Syntax:

```handlebars
<!-- Output a variable (HTML-escaped) -->
{{variableName}}

<!-- Output raw HTML (unescaped) -->
{{{htmlContent}}}

<!-- Comment (not rendered) -->
{{! This is a comment }}
```

### Wichtige Konzepte {#key-concepts}

Die wichtigsten Konzepte von Handlebars:

| Syntax | Beschreibung | Wann ist sie einzusetzen? |
|--- |--- |--- |
| `{{ }}` | Escape-Zeichen für HTML | Metadaten, Kennzeichnungen, Boolesche Werte |
| `{{{ }}}` | Gibt unformatierten HTML aus (ohne Escape-Zeichen) | Rich-Text- und Asset-Ausgabe |
| `{{! }}` | Nur-Handlebars-Kommentar | Vorlagendokumentation |

>[!IMPORTANT]
>
> Verwenden Sie dreifache Klammern (`{{{ }}}`) für Feldwerte, da Werte vorab in HTML gerendert werden.

## Kontextreferenz zur Vorlage {#template-context-reference}

Wenn die Vorlage gerendert wird, erhält sie ein Kontextobjekt, das alle Daten zu Ihrem Inhaltsfragment enthält. Dies umfasst Folgendes:

* Das ausgewählte Fragment
* Alle weiteren Fragmente, auf die von diesem ausgewählten Fragment verwiesen wird

  >[!NOTE]
  >
  >Fragmente können referenziert werden:
  >
  >* in der Benutzeroberfläche: bis zur maximalen Tiefe von 5
  >* Bei Verwendung der API: Die Tiefe kann konfiguriert werden, bis zur maximalen Tiefe von 10

### Inhaltsfragment {#content-fragment}

Die Struktur des Kontextobjekts für das (ausgewählte) Inhaltsfragment:

| Variable | Typ | Beschreibung |
|--- |--- |--- |
| `properties` | Map | Fragmentmetadaten (siehe [Eigenschaftenstruktur](#properties-structure-main-and-referenced-fragments)) |
| `fields` | Map | Direkter Zugriff auf Feldwerte nach Namen |
| `allFields` | Liste | Array von `{name, value}` für die Iteration |
| `hasFields` | Boolescher Wert | `true`, ob das Fragment Felder enthält |

### Eigenschaftenstruktur {#properties-structure}

Das `properties`-Objekt hat für das ausgewählte Fragment und für jedes referenzierte Fragment dieselbe Struktur.

| Eigenschaft | Typ | Beschreibung | Beispiel |
|--- |--- |--- |--- |
| `id` | Zeichenfolge | UUID des Fragments | |
| `title` | Zeichenfolge | Titel des Fragments | Radfahren Süd Utah |
| `description` | Zeichenfolge | Beschreibung des Fragments | Ein Abenteuer… |
| `path` | Zeichenfolge | JCR-Pfad zum Fragment | `/content/dam/...` |
| `hasDescription` | Boolescher Wert | True, wenn die Beschreibung nicht leer ist | `true` |
| `createdDate` | Zeichenfolge | ISO-8601 Erstellungsdatum | |
| `modifiedDate` | Zeichenfolge | ISO-8601 Änderungsdatum | |
| `publishedDate` | Zeichenfolge | ISO-8601 Veröffentlichungsdatum | |
| `status` | Zeichenfolge | Replikationsstatus für die Veröffentlichungsebene | `DRAFT` |
| `model` | Map | Enthält: `id`, `path`, `name`, `technicalName`, `description` | |
| `validationStatus` | Liste | Einträge wie `{property, message}` | |
| `previewReplicationStatus` | Zeichenfolge | Replikationsstatus für die Vorschauebene | |
| `tags` | Liste | Tags auf Fragmentebene. Jedes Element: `id`, `title`, `titlePath`, `name`, `path`, `description` | |
| `fieldTags` | Liste | Tags auf Feldebene. Gleiche Struktur wie `tags`. | |

Beispiele: Vorlagenzugriff

Für das (ausgewählte) Inhaltsfragment:

```handlebars
{{properties.title}}, {{properties.description}}, {{{fields.field_name}}} 
```

### Referenzierte Inhaltsfragmente {#referenced-content-fragments}

Die Struktur des Kontextobjekts für alle referenzierten Fragmente:

| Variable | Typ | Beschreibung |
|--- |--- |--- |
| `hasReferencedFragments` | Boolescher Wert | `true`, wenn Verweise vorhanden sind |
| `referencedFragments` | Liste | Array von referenzierten Fragmentobjekten |
| `referencesError` | Boolescher Wert | `true`, ob beim Laden von Verweisen ein Fehler aufgetreten ist |
| `referencesErrorMessage` | Zeichenfolge | Fehlermeldung, wenn `referencesError` `true` ist |

### Fragmentstruktur, auf die verwiesen wird {#referenced-fragment-structure}

Jedes Element in `referencedFragments` enthält:

| Eigenschaft | Typ | Beschreibung |
|--- |--- |--- |
| `anchorId` | Zeichenfolge | HTML-sichere Anker-ID (auf Fragmentebene, keine Inhaltsfragment-Eigenschaft) |
| `properties` | Map | Fragmentmetadaten (gleiche Struktur wie oben) |
| `hasFields` | Boolescher Wert | True, wenn das Fragment Felder enthält |
| `fields` | Map | Direkter Zugriff auf Felder in diesem Fragment |
| `allFields` | Liste | Array von `{name, value}` für die Iteration |

Beispiele: Vorlagenzugriff für das erste referenzierte Inhaltsfragment (erstes Element in der 0-indizierten Liste):

```handlebars
{{referencedFragments.[0].anchorId}}, {{referencedFragments.[0].properties.title}}, {{referencedFragments.[0].properties.description}}
```

Oder aus der Feldzuordnung:

```handlebars
{{{ fields.referenced_cf_field_name.properties.description }}}
```

## Grundlegender Feldzugriff {#basic-field-access}

Der direkte Feldzugriff wird empfohlen. Bei Bedarf können Sie alle Felder durchlaufen.

### Direkter Feldzugriff (empfohlen) {#direct-field-access-recommended}

Greifen Sie mithilfe der Feldzuordnung direkt nach Namen auf Felder zu:

```handlebars
<!DOCTYPE html>
<html>
<head>
  <title>{{properties.title}}</title>
</head>
<body>
  <article>
    <h1>{{{fields.title}}}</h1>
    <p class="subtitle">{{{fields.subtitle}}}</p>
    <div class="content">
      {{{fields.description}}}
    </div>
    <div class="image">
      {{{fields.primaryImage}}}
    </div>
  </article>
</body>
</html>
```

Denken Sie daran:

* Verwenden Sie dreifache Klammern `{{{ }}}` für Feldwerte, wenn sie vorab gerenderten HTML (Rich-Text) enthalten
* Feldnamen (Titel, Untertitel, Beschreibung, primaryImage) **müssen** genau mit Ihrem Inhaltsfragmentmodell **exakt**
* Fehlende Felder werden nicht gerendert - es werden keine Fehler ausgegeben und die Handlebars-Syntax bleibt im gerenderten HTML-Fragment vorhanden (und sichtbar)

### Iteration aller Felder {#iterate-through-all-fields}

Verwenden Sie `allFields`, wenn Sie die Feldnamen nicht im Voraus kennen:

```handlebars
<table>
  <thead>
    <tr>
      <th>Field Name</th>
      <th>Field Value</th>
    </tr>
  </thead>
  <tbody>
    {{#each allFields}}
    <tr>
      <td>{{name}}</td>
      <td>{{{value}}}</td>
    </tr>
    {{/each}}
  </tbody>
</table>
```

Denken Sie daran:

* `{{name}}` verwendet doppelte geschweifte Klammern (Nur-Text-Beschriftung)
* `{{{value}}}` verwendet dreifache geschweifte Klammern (vorab gerenderter HTML-Wert)

## Verschachtelte Inhaltsfragmente {#nested-content-fragments}

Wenn ein Inhaltsfragmentfeld auf ein anderes Inhaltsfragment verweist, können Sie Punktnotation verwenden, um direkt auf Felder im referenzierten Fragment zuzugreifen.

### Verschachtelung auf einer Ebene {#single-level-nesting}

Ein Beispiel für die Verschachtelung auf einer Ebene:

```handlebars
<article>
  <h1>{{{fields.title}}}</h1>

  <!-- Access author (a referenced Content Fragment) -->
  <div class="author-info">
    <h3>Author</h3>
    <p>Name: {{{fields.author.name}}}</p>
    <p>Email: {{{fields.author.email}}}</p>
    <p>Bio: {{{fields.author.bio}}}</p>
  </div>

  <div class="content">
    {{{fields.content}}}
  </div>
</article>
```

Muster: `fields.referenceFieldName.nestedFieldName`

### Verschachtelung mehrerer Ebenen {#multi-level-nesting}

Das System unterstützt eine unbegrenzte Verschachtelungstiefe:

```handlebars
<article>
  <h1>{{{fields.title}}}</h1>

  <div class="author-details">
    <!-- Level 1: Author -->
    <p>Author: {{{fields.author.name}}}</p>

    <!-- Level 2: Author's Organization -->
    <p>Organization: {{{fields.author.organization.name}}}</p>
    <p>Website: {{{fields.author.organization.website}}}</p>

    <!-- Level 3: Organization's Address -->
    <p>Located in: {{{fields.author.organization.address.city}}},
    {{{fields.author.organization.address.country}}}</p>
  </div>

  <div class="content">
    {{{fields.content}}}
  </div>
</article>
```

Muster: `fields.level1.level2.level3.fieldName` (begrenzte Tiefe; Standard ist 5, kann auf 10 erweitert werden, wenn die API verwendet wird)

### API-Parameteranforderung: Hydratation {#api-parameter-requirements}

Um den Zugriff auf verschachtelte Inhaltsfragmente zu aktivieren, müssen Sie den `hydration` Abfrageparameter in Ihren API-Aufruf einbeziehen:

So aktivieren Sie die Hydratation:

```http
# Enable hydration with depth=2 for 2 levels of nesting
GET /adobe/sites/cf/fragments/{id}/preview?hydration=%7B%22enabled%22%3Atrue%2C%22maxDepth%22%3A2%7D
```

| `maxDepth` | Was geladen wird |
|--- |--- |
| `1` | Hauptfragment + direkte Verweise |
| `2` | Hauptfragment + direkte Verweise + ihre Verweise |
| `3+` | Weiter bis zu 10 Ebenen |

## Felder mit mehreren Werten {#multi-valued-fields}

Es gibt mehrere Arten von Feldern mit mehreren Werten.

### Textfelder mit mehreren Werten {#multi-valued-text-fields}

Text, [Zahl](#multi-valued-number-fields), Datum und andere einfache Felder werden bei mehreren Werten zu Arrays:

```handlebars
<article>
  <h1>{{{fields.title}}}</h1>

  <!-- Access individual items by index (use dot before bracket) -->
  <div class="tags">
    <span class="tag">{{{fields.tags.[0]}}}</span>
    <span class="tag">{{{fields.tags.[1]}}}</span>
  </div>

  <!-- Better: Iterate through all tags -->
  <div class="tags">
    {{#each fields.tags}}
    <span class="tag">{{{this}}}</span>
    {{/each}}
  </div>
</article>
```

Denken Sie daran, beim Zugriff auf Array-Elemente nach Index in Handlebars:

* Verwenden Sie:
   * `.[0]` (Punkt vor Klammer)
* Nicht:
   * `[0]`

### Zahlenfelder mit mehreren Werten {#multi-valued-number-fields}

Zahlen werden zur [ in ](#multi-valued-text-fields) umgewandelt:

```handlebars
<div class="pricing">
  <h3>Available Prices:</h3>
  {{#each fields.prices}}
  <span class="price">${{{this}}}</span>
  {{/each}}
</div>
```

### Verweise auf Inhaltsfragmente mit mehreren Werten {#multi-valued-content-fragment-references}

Wenn ein Feld auf mehrere Inhaltsfragmente verweist:

```handlebars
<div class="authors">
  <h3>Authors:</h3>
  {{#each fields.authors}}
  <div class="author">
    <h4>{{{this.name}}}</h4>
    <p>Email: {{{this.email}}}</p>
    {{#if this.bio}}
    <p class="bio">{{{this.bio}}}</p>
    {{/if}}
  </div>
  {{/each}}
</div>
```

### Verweise auf Assets mit mehreren Werten {#multi-valued-asset-references}

[Inhaltsreferenz](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-reference) Felder, die für Inhaltstypen konfiguriert sind, bei denen es sich um Assets handelt (z. B. Bilder und Dokumente), werden vorab als HTML gerendert. Assets mit mehreren Werten werden zu Arrays:

```handlebars
<!-- Single asset -->
<div class="hero-image">
  {{{fields.heroImage}}}
</div>

<!-- Multi-valued: iterate through all images -->
<div class="gallery">
  {{#each fields.gallery}}
  <div class="image">{{{this}}}</div>
  {{/each}}
</div>
```

### Verschachtelte Verweise mit mehreren Werten {#nested-multi-valued-references}

Verweise mit mehreren Werten können Verweise mit mehreren Werten in jeder Tiefe enthalten:

```handlebars
{{#each fields.chapters}}
<div class="chapter">
  <h3>Chapter: {{{this.title}}}</h3>

  {{#each this.authors}}
  <p>Author: {{{this.name}}}</p>

  {{#each this.publications}}
  <p>Publication: {{{this.title}}}</p>
  {{/each}}
  {{/each}}
</div>
{{/each}}
```

## Schleifen und Iteration {#loops-and-iteration}

Handlebars stellt den `{{#each}}` Helper für die Iteration über Arrays und Objekte bereit.

### Iteration über Arrays {#iterating-over-arrays}

Beispiel für die Iteration über Arrays:

```handlebars
<!-- Simple array iteration -->
{{#each fields.tags}}
<span class="tag">{{{this}}}</span>
{{/each}}

<!-- Array of objects -->
{{#each fields.authors}}
<div class="author">
  <h4>{{{this.name}}}</h4>
  <p>{{{this.email}}}</p>
</div>
{{/each}}

<!-- With empty-state fallback -->
{{#each fields.tags}}
<span class="tag">{{{this}}}</span>
{{else}}
<p>No tags available.</p>
{{/each}}
```

### Spezielle Variablen in Schleifen {#special-variables-in-loops}

Innerhalb `{{#each}}` Blöcke stellt Handlebars spezielle Variablen bereit:

```handlebars
{{#each fields.items}}
<div class="item">
  <p>Index: {{@index}}</p>     <!-- 0-based index -->
  <p>Number: {{@number}}</p>   <!-- 1-based index -->
  <p>First: {{@first}}</p>     <!-- true for first item -->
  <p>Last: {{@last}}</p>       <!-- true for last item -->
  <p>Value: {{{this}}}</p>     <!-- current item -->
</div>
{{/each}}

<!-- Example: numbered steps with first/last CSS classes -->
<ul>
  {{#each fields.steps}}
  <li class="{{#if @first}}first{{/if}} {{#if @last}}last{{/if}}">
    Step {{@number}}: {{{this}}}
  </li>
  {{/each}}
</ul>
```

### Iteration über referenzierte Fragmente {#iterating-over-referenced-fragments}

Ein Beispiel für die Iteration über referenzierte Fragmente:

```handlebars
{{#if hasReferencedFragments}}
<section class="references">
  <h2>Related Content</h2>
  {{#each referencedFragments}}
  <article id="{{anchorId}}">
    <h3>{{title}}</h3>
    {{#if hasDescription}}
    <p>{{description}}</p>
    {{/if}}
    {{#if hasFields}}
    <ul>
      {{#each allFields}}
      <li><strong>{{name}}:</strong> {{{value}}}</li>
      {{/each}}
    </ul>
    {{/if}}
  </article>
  {{/each}}
</section>
{{/if}}
```

### Verschachtelte Schleifen {#nested-loops}

Beispiel für verschachtelte Schleifen:

```handlebars
{{#each fields.categories}}
<section class="category">
  <h2>{{{this.name}}}</h2>

  {{#each this.products}}
  <article class="product">
    <h3>{{{this.name}}}</h3>
    <p>{{{this.description}}}</p>
  </article>
  {{/each}}
</section>
{{/each}}
```

## Bedingtes Rendering {#conditional-rendering}

Verwenden Sie Bedingungen, um Inhalte je nach Verfügbarkeit der Daten ein- oder auszublenden.

### Basic IF/Else {#basic-if-else}

Beispiel für ein einfaches If-Else-Konstrukt:

```handlebars
{{#if hasMainDescription}}
<p class="description">{{properties.description}}</p>
{{else}}
<p class="no-description">No description available.</p>
{{/if}}

<!-- Check field existence before rendering -->
{{#if fields.author}}
<div class="author">
  <p>By {{{fields.author.name}}}</p>
</div>
{{/if}}

{{#if fields.publishDate}}
<time>{{{fields.publishDate}}}</time>
{{/if}}
```

### Außer (negativ bedingt) {#unless-negative-conditional}

Ein `unless` Helper:

```handlebars
<!-- Show author unless explicitly hidden -->
{{#unless fields.hideAuthor}}
<div class="author">{{{fields.author.name}}}</div>
{{/unless}}
```

### Verschachtelte Bedingungen {#nested-conditials}

Ein Beispiel für verschachtelte bedingte Regeln:

```handlebars
{{#if fields.author}}
<div class="author">
  <h3>{{{fields.author.name}}}</h3>

  {{#if fields.author.bio}}
  <p class="bio">{{{fields.author.bio}}}</p>
  {{/if}}

  {{#if fields.author.website}}
  <a href="{{{fields.author.website}}}">Visit Website</a>
  {{/if}}
</div>
{{/if}}
```

## Integrierte Handlebars-Helfer {#built-in-handlebars-helpers}

Handlebars umfasst mehrere integrierte Helper, die über `{{#if}}` und `{{#each}}` hinausgehen.

| Helfer | Beschreibung |
|--- |--- |
| `{{#if condition}}` | Rendert Inhalt, wenn die Bedingung wahr ist. Falsy-Werte: `false`, `undefined`, `null`, `0`, `""`, `[]` |
| `{{#unless condition}}` | Rendert den Inhalt, wenn die Bedingung fehlerhaft ist (Umkehrung von `#if`) |
| `{{#each array}}` | Wiederholt Inhalte für jedes Element; unterstützt `{{else}}` für leere Arrays |
| `{{#with object}}` | Erstellt einen neuen Bereich für ein verschachteltes Objekt, wodurch die Pfadwiederholung reduziert wird |
| `{{lookup this "key"}}` | Dynamisches Suchen einer Eigenschaft nach Namen |

### Mit Helper {#with-helper}

Erstellt einen neuen Bereich für verschachtelte Objekte, um Präfixe für sich wiederholende Pfade zu reduzieren:

```handlebars
{{#with fields.author}}
<div class="author">
  <h3>{{{name}}}</h3>     <!-- same as fields.author.name -->
  <p>{{{email}}}</p>      <!-- same as fields.author.email -->
  <p>{{{bio}}}</p>        <!-- same as fields.author.bio -->
</div>
{{/with}}

<!-- Useful for deeply nested objects -->
{{#with fields.author.organization}}
<div class="organization">
  <h4>{{{name}}}</h4>
  <p>{{{website}}}</p>
  {{#with address}}
  <address>
    {{{street}}}<br/>
    {{{city}}}, {{{country}}}
  </address>
  {{/with}}
</div>
{{/with}}
```

## Erweiterte Muster {#advanced-patterns}

Es folgen einige Beispiele für erweiterte Muster.

### Zugreifen auf den übergeordneten Kontext in verschachtelten Schleifen {#accessing-parent-context-in-nested-loops}

Verwenden Sie `../` , um innerhalb einer verschachtelten Schleife auf den übergeordneten Bereich zuzugreifen:

```handlebars
<h1>{{{fields.title}}}</h1>

{{#each fields.chapters}}
<section class="chapter">
  <h2>Chapter {{@number}}: {{{this.title}}}</h2>

  {{#each this.sections}}
  <article>
    <!-- Access parent chapter via ../ -->
    <p>Chapter: {{{../title}}}</p>

    <!-- Access root context via ../../ -->
    <p>Book: {{{../../fields.title}}}</p>

    <h3>{{{this.title}}}</h3>
    <div>{{{this.content}}}</div>
  </article>
  {{/each}}
</section>
{{/each}}
```

### Dynamische CSS-Klassen {#dynamic-css-classes}

Beispiel für dynamische CSS-Klassen:

```handlebars
<article class="content-fragment {{#if hasMainDescription}}with-description{{/if}} {{#if hasReferencedFragments}}has-refs{{/if}}">
  <h1>{{properties.title}}</h1>
</article>

<ul class="tag-list">
  {{#each fields.tags}}
  <li class="tag {{#if @first}}first{{/if}} {{#if @last}}last{{/if}}">
    {{{this}}}
  </li>
  {{/each}}
</ul>
```

## Vollständige Beispiele {#complete-examples}

Mehrere vollständige Beispiele sind als Referenz angegeben.

### Blogpost mit Autor

Ein Blogpost mit Autorendetails:

```handlebars
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>{{properties.title}}</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 40px; }
    .author-card { background: #f5f5f5; padding: 20px; border-radius: 8px; }
    .tags { display: flex; gap: 10px; }
    .tag { background: #007bff; color: white; padding: 5px 10px; border-radius: 4px; }
  </style>
</head>
<body>
  <article>
    <header>
      <h1>{{{fields.title}}}</h1>
      {{#if fields.publishDate}}
      <time datetime="{{{fields.publishDate}}}">{{{fields.publishDate}}}</time>
      {{/if}}
      {{#if fields.tags}}
      <div class="tags">
        {{#each fields.tags}}
        <span class="tag">{{{this}}}</span>
        {{/each}}
      </div>
      {{/if}}
    </header>

    {{#if fields.heroImage}}
    <figure>
      {{{fields.heroImage}}}
      {{#if fields.imageCaption}}
      <figcaption>{{{fields.imageCaption}}}</figcaption>
      {{/if}}
    </figure>
    {{/if}}

    <div class="content">
      {{{fields.content}}}
    </div>

    {{#if fields.author}}
    <aside class="author-card">
      <h3>About the Author</h3>
      <h4>{{{fields.author.name}}}</h4>
      {{#if fields.author.profilePicture}}
      <div class="author-image">{{{fields.author.profilePicture}}}</div>
      {{/if}}
      {{#if fields.author.bio}}
      <p>{{{fields.author.bio}}}</p>
      {{/if}}
      {{#if fields.author.email}}
      <p>Contact: <a href="mailto:{{{fields.author.email}}}">{{{fields.author.email}}}</a></p>
      {{/if}}
    </aside>
    {{/if}}
  </article>
</body>
</html>
```

Erforderlicher API-Aufruf:

```http
GET /adobe/sites/cf/fragments/{id}/preview?hydration=%7B%22enabled%22%3Atrue%2C%22maxDepth%22%3A1%7D
```

### Allgemeine Tabellenansicht (keine Vorkenntnisse in Feldern) {#generic-table-view-no-prior-knowledge-of-fields}

Eine allgemeine Tabellenansicht ohne inhärente Feldkenntnisse. Die ähnelt der **Generische Vorlage**:

```handlebars
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>{{properties.title}}</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 40px; }
    table { width: 100%; border-collapse: collapse; margin: 20px 0; }
    th, td { border: 1px solid #ddd; padding: 12px; text-align: left; }
    th { background-color: #f4f4f4; font-weight: bold; }
    .ref-section { background: #f9f9f9; padding: 20px; margin: 20px 0; border-radius: 8px; }
  </style>
</head>
<body>
  <header>
    <h1>{{properties.title}}</h1>
    {{#if properties.description}}<p>{{properties.description}}</p>{{/if}}
    <p><small>Path: {{properties.path}}</small></p>
  </header>

  {{#if hasFields}}
  <section>
    <h2>Fields</h2>
    <table>
      <thead>
        <tr><th>Field Name</th><th>Field Value</th></tr>
      </thead>
      <tbody>
        {{#each allFields}}
        <tr>
          <td><strong>{{name}}</strong></td>
          <td>{{{value}}}</td>
        </tr>
        {{/each}}
      </tbody>
    </table>
  </section>
  {{/if}}

  {{#if hasReferencedFragments}}
  <section class="ref-section">
    <h2>Referenced Content Fragments</h2>
    {{#each referencedFragments}}
    <article id="{{anchorId}}" style="margin-bottom: 30px;">
      <h3>{{title}}</h3>
      {{#if hasDescription}}<p>{{description}}</p>{{/if}}
      <p><small>Path: {{path}}</small></p>
      {{#if hasFields}}
      <table>
        <thead>
          <tr><th>Field Name</th><th>Field Value</th></tr>
        </thead>
        <tbody>
          {{#each allFields}}
          <tr>
            <td><strong>{{name}}</strong></td>
            <td>{{{value}}}</td>
          </tr>
          {{/each}}
        </tbody>
      </table>
      {{/if}}
    </article>
    {{/each}}
  </section>
  {{/if}}
</body>
</html>
```

## Best Practices {#best-practices}

Zu den Best Practices gehören:

1. Verwenden Sie immer dreifache Klammern für Feldwerte, die HTML-Markup-Inhalte enthalten.

   * Feldwerte werden in HTML vorab gerendert.

     >[!NOTE]
     >
     >Doppelte Klammern zeigen unformatierte HTML-Tags als Nur-Text-Text an.

   ```handlebars
   <!-- CORRECT -->
   {{{fields.description}}}
   
   <!-- WRONG - displays HTML tags as text -->
   {{fields.description}}
   ```

1. Prüfen Sie das Vorhandensein, bevor Sie auf verschachtelte Felder zugreifen.

   ```handlebars
   <!-- GOOD: check before accessing nested fields -->
   {{#if fields.author}}
   <p>By {{{fields.author.name}}}</p>
   {{/if}}
   
   <!-- RISKY: may render empty if author is not set -->
   <p>By {{{fields.author.name}}}</p>
   ```

1. Verwenden Sie nach Möglichkeit den direkten Feldzugriff.

   * Es ist leichter lesbar und verwaltbar als das Iterieren von `allFields` und Übereinstimmungen mit dem Namen.

1. Strukturvorlagen mit Abschnittskommentaren.

   ```handlebars
   {{! ===== HEADER SECTION ===== }}
   <header>
     <h1>{{properties.title}}</h1>
   </header>
   
   {{! ===== MAIN CONTENT ===== }}
   <main>
     {{#if hasFields}}
     <!-- fields rendering -->
     {{/if}}
   </main>
   
   {{! ===== REFERENCES ===== }}
   {{#if hasReferencedFragments}}
   <!-- references rendering -->
   {{/if}}
   ```

1. Verarbeiten Sie fehlende Daten mit Fallbacks.

   ```handlebars
   {{#if fields.title}}
   <h1>{{{fields.title}}}</h1>
   {{else}}
   <h1>Untitled</h1>
   {{/if}}
   ```

1. Verwenden Sie immer eine ordnungsgemäße HTML-Dokumentstruktur.

   ```handlebars
   <!DOCTYPE html>
   <html lang="en">
   <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1">
     <title>{{properties.title}}</title>
   </head>
   <body>
     <!-- your content here -->
   </body>
   </html>
   ```

1. Testen mit einer Vielzahl von Inhaltsszenarien:

   * Alle Felder vollständig ausgefüllt
   * Optionale Felder fehlen
   * Leere Felder mit mehreren Werten
   * Tiefe Verschachtelung (mehrere Ebenen)
   * Verweise, die nicht geladen werden können

1. Verwenden semantischer HTML-Elemente:

   * Verwenden Sie für eine bessere Barrierefreiheit `<article>`, `<header>`, `<main>`, `<footer>`, `<time>`, `<address>` oder Ähnliches.

1. Beibehalten von Stilen in CSS.

   * Verwenden Sie `<style>` Tags oder externe Stylesheets.
   * Inline-Stile sollten nach Möglichkeit vermieden werden.

1. Komplexe Logik von Dokumenten:

   * Verwenden Sie Handlebars-Kommentare `({{! }})`.
   * Verwenden Sie keine HTML-Kommentare, die in der gerenderten Ausgabe angezeigt werden.

## Fehlerbehebung {#troubleshooting}

Einige Hinweise zur Fehlerbehebung:

| Problem | Symptom | Lösung |
|--- |--- |--- |
| Feld zeigt HTML-Tags als Text an | `<p>Hello World</p>` wörtlich angezeigt | Verwendung dreier Klammern: `{{{fields.description}}}` |
| Verschachtelte Inhaltsfragmentfelder sind leer oder zeigen [Objekt] | `{{{fields.author.name}}}` ist leer | Aktivieren der Hydratation im API-Aufruf; Überprüfen der Schreibweise des Feldnamens; Überprüfen, ob die `maxDepth` tief genug ist |
| Feld mit mehreren Werten zeigt nur das erste Element an | Array mit fünf Elementen rendert nur ein Element | `{{#each fields.tags}}` verwenden, um alle Elemente zu iterieren |
| Zugriff auf Array-Index funktioniert nicht | `{{{fields.tags[0]}}}` wird leer dargestellt | Punktklammersyntax verwenden: `{{{fields.tags.[0]}}}` |
| Referenzierte Fragmente werden nicht angezeigt | `hasReferencedFragments` ist immer „false“ | Hydratation aktivieren: `?hydration=%7B%22enabled%22%3Atrue%7D;` auch `{{#if referencesError}}` überprüfen |
| Vorlage rendert nichts | Leere Seite oder leere Ausgabe | Auf nicht geschlossene `{{#if}}` oder `{{#each}}` prüfen; Diagnoseausgabe hinzufügen: `<pre>hasFields: {{hasFields}}`|`title: {{properties.title}}</pre>` |
| Kommentare werden auf der gerenderten Seite angezeigt | Für Endbenutzer sichtbarer HTML-Kommentartext | Verwenden von Handlebars-Kommentaren `{{! comment }}` anstelle von HTML `<!-- comment -->` |
| Bedingung wird immer als „true“ ausgewertet | `{{#if fields.enabled}}` ist immer wahr | Hinweis: Der `"false"` ist in Handlebars wahr. Nur tatsächliche `false`, `null`, `undefined`, `0`, `""` und `[]` sind falsch. |
| Sonderzeichen werden als Entitäten gerendert | `&lt;`, `&amp;` anstelle von `<` angezeigt, `&` | Verwenden Sie dreifache geschweifte Klammern für vorab gerenderte HTML-Inhalte: `{{{fields.content}}}` |
| Zugriff auf äußere Schleifenvariable über innere Schleife nicht möglich | Variable des übergeordneten `#each` ist nicht definiert | `../` für übergeordneten Bereich verwenden: `{{{../name}}}`; `../../` für übergeordnete Elemente verwenden |
| Leere Liste ohne Fallback-Nachricht | Feld mit mehreren Werten und null Elementen zeigt nichts an | `{{else}}` in `{{#each}}` verwenden: `{{#each fields.tags}}...{{else}}<p>No tags</p>{{/each}}` |

### Arbeiten mit Assets {#working-with-assets}

Assets, auf die von Inhaltsfragmenten verwiesen wird, wird von AEM vorab als HTML gerendert. Daher sind dreifache Klammern für alle Asset-Verweise obligatorisch.

| Asset-Typ | Gerendert als |
|--- |--- |
| Bilder | `<img src="..." alt="...">` |
| Videos | `<video>` |
| Dokumente | Link `<a href="...">` |

Denken Sie daran:

* Verwenden Sie immer dreifache Klammern für Asset-Felder.
Bei Verwendung doppelter Klammern wird das generierte HTML-Tag mit Escape-Zeichen versehen und als Rohtext angezeigt, anstatt das Bild, Video oder den Link zu rendern.

### Nutzung der Asset-Felder {#asset-field-usage}

Beispiel für die Verwendung von Asset-Feldern:

```handlebars
<!-- CORRECT - triple braces render the image -->
{{{fields.heroImage}}}
<!-- Output: <img src="path/to/image.jpg" alt="Hero"> -->

<!-- WRONG - double braces escape the tag, showing it as text -->
{{fields.heroImage}}
<!-- Output: &lt;img src="path/to/image.jpg" alt="Hero"&gt; -->
```

## Helper für benutzerdefinierte Vorlagen {#customer-template-helpers}

Das System stellt benutzerdefinierte Handlebars-Helper zum Generieren von HTML-Elementen mit benutzerdefinierten HTML-Attributen bereit. Diese Helper geben Ihnen die Kontrolle über das generierte Markup und bewältigen gleichzeitig die Komplexität des Extrahierens von Quell-URLs aus vorgerenderten Inhalten.

Verfügbare Helper:

1. `asset` - Generiert `<img>`-Tags mit benutzerdefinierten Attributen
1. `text` - Erzeugt `<span>` Tags, die Textinhalte mit benutzerdefinierten Attributen umschließen

### `asset` Helper {#asset-helper}

Syntax:

```handlebars
{{{asset fieldValue attribute1="value1" attribute2="value2"}}}
```

Denken Sie daran:

* Verwenden Sie mit dem Asset-Helper `{{{ }}}` dreifache Klammern, keine doppelten Klammern!

#### Vier grundlegende Beispiele {#four-basic-examples}

Vier grundlegende Beispiele sind:

```handlebars
<!-- Add a CSS class to an image -->
{{{asset fields.heroImage class="hero-image"}}}
<!-- Output: <img src="..." alt="..." class="hero-image"> -->

<!-- Add multiple CSS classes -->
{{{asset fields.productImage class="product-img responsive shadow"}}}

<!-- Add id and class -->
{{{asset fields.logo class="brand-logo" id="main-logo"}}}

<!-- Add data attributes -->
{{{asset fields.thumbnail class="thumb" data-category="product" data-id="123"}}}
```

#### Unterstützte Attribute {#supported-attributes}

Sie können jedes gültige HTML-Attribut hinzufügen:

| Attribut |  Beispiel |
|--- |--- |
| `class` | `class="my-class another-class"` |
| `id` | `id="unique-id"` |
| `alt` | `alt="Custom alt text" (overrides existing alt)` |
| `data-*` | `data-index="1" data-type="hero"` |
| `aria-*` | `aria-label="Description" aria-hidden="true"` |
| `width` | `width="300"` |
| `height` | `height="200"` |
| `loading` | `loading="lazy"` |
| `style` | `style="border-radius: 8px;"` |

#### Alt-Text überschreiben {#override-alt-text}

Das `alt`-Attribut aus dem Originalbild kann überschrieben werden:

```handlebars
{{{asset fields.photo alt="Custom description for accessibility"}}}
```

#### Komplexes Beispiel {#complex-example}

Ein komplexes Beispiel:

```handlebars
<article class="blog-post">
<header>
{{{asset fields.featuredImage 
class="featured-image responsive" 
id="post-hero"
loading="lazy"
data-post-id="12345"}}}
</header>
</article>
```

#### Verwenden von mit Schleifen {#using-with-loops}

Asset Helper in Schleifen:

```handlebars
{{#each fields.galleryImages}}
{{{asset this class="gallery-item" data-index=@index}}}
{{/each}}
```

### `text` Helper {#text-helper}

Der Text-Helper generiert einen `<span>` Tag, der Textinhalte mit benutzerdefinierten CSS-Klassen und HTML-Attributen umschließt. Nützlich für die Gestaltung einzelner Textfelder.

Syntax:

```handlebars
{{{text fieldValue attribute1="value1" attribute2="value2"}}}
```

Denken Sie daran:

* Verwenden Sie dreifache Klammern `{{{ }}}` mit dem Text Helper, keine doppelten Klammern!

#### Drei grundlegende Beispiele {#three-basic-examples}

Drei grundlegende Beispiele sind:

```handlebars
<!-- Add a CSS class to text -->
{{{text fields.title class="article-title"}}}
<!-- Output: <span class="article-title">The Title Text</span> -->

<!-- Add multiple attributes -->
{{{text fields.price class="price-tag" id="product-price" data-currency="USD"}}}

<!-- Style inline text -->
{{{text fields.highlightedText class="highlighted" style="background: yellow;"}}}
```

#### Häufige Anwendungsfälle {#common-use-cases}

Einige gängige Anwendungsfälle sind:

```handlebars
<!-- Styling article metadata -->
<article>
<header>
{{{text fields.category class="category-badge"}}}
<h1>{{{fields.title}}}</h1>
{{{text fields.author class="byline"}}}
{{{text fields.publishDate class="date"}}}
</header>
</article>

<!-- Creating styled labels -->
<div class="product-card">
{{{text fields.productName class="product-name"}}}
{{{text fields.brand class="brand-label" data-brand-id="abc"}}}
{{{text fields.price class="price" id="main-price"}}}
</div>

<!-- Accessibility enhancements -->
{{{text fields.importantNote class="alert" role="alert" aria-live="polite"}}}
```

#### Mit Schleifen {#with-loops}

Ein gängiges Anwendungsbeispiel für -Schleifen sind:

```handlebars
{{#each fields.tags}}
{{{text this class="tag-badge"}}}
{{/each}}
```

### Helper - Attributvalidierung {#helpers-attribute-validation}

Beide Helper validieren Attributnamen, bevor sie in die Ausgabe aufgenommen werden.

Gültige Attributnamen:

* Muss mit einem Buchstaben beginnen (a-z, A-Z)
* Darf nur Buchstaben, Ziffern, Bindestriche und Unterstriche enthalten; siehe [Namenskonventionen](/help/implementing/developing/introduction/naming-conventions.md)
* Ignorieren der Groß-/Kleinschreibung
* Beispiel:
   * Gültig:
      * `class`, `id`, `data-value`, `aria-label`, `my_attr`, `dataIndex1`
   * Ungültig:
      * `123-attr`, `-class`, `@special`, `$money`

Ungültige Attributnamen werden mit einer Warnung in den Protokollen im Hintergrund übersprungen:

```handlebars
{{{asset fields.image class="valid" 123-invalid="skipped" id="also-valid"}}}
<!-- Output: <img src="..." alt="..." class="valid" id="also-valid"> -->
<!-- 123-invalid is skipped because it starts with a number -->
```

Denken Sie daran:

* Überprüfen Sie die Serverprotokolle auf Warnungen zu „Blockierte ungültige Attributnamensformate“.

## Vergleichen der direkten Ausgabe mit Helfern {#comparing-direct-output-to-helpers}

Verwendung der `{{{fields.xxx}}}` für die direkte Ausgabe:

* Sie benötigen keinen benutzerdefinierten Stil
* Die Standardausgabe soll unverändert bleiben
* Das Feld enthält eine komplexe HTML, die Sie nicht ändern möchten

Wann Helper verwendet werden sollten:

* Sie müssen CSS-Klassen für die Formatierung hinzufügen
* Sie müssen benutzerdefinierte HTML-Attribute (`data-*`, `aria-*` und andere) hinzufügen
* Sie wünschen sich eine konsistente, kontrollierte HTML-Struktur

Vergleich:

```handlebars
<!-- Direct output - uses whatever HTML the system generates -->
{{{fields.heroImage}}}
<!-- Output: <img src="/path/image.jpg" alt="Hero Image"> -->

<!-- With asset helper - full control over attributes -->
{{{asset fields.heroImage class="hero responsive" id="main-hero" loading="lazy"}}}
<!-- Output: <img src="/path/image.jpg" alt="Hero Image" class="hero responsive" id="main-hero" loading="lazy"> -->
```

## Kurzübersicht {#quick-reference}

Einige Kurzanleitungen werden als Referenz bereitgestellt.

### Kontextvariablen {#context-variables}

Die Kontextvariablen:

```handlebars
{{properties}}                <!-- Main fragment metadata -->
{{fields}}                    <!-- Map keyed by field name to rendered values (such as strings, lists, nested maps for Content Fragment references, commerce maps, HTML, and others) -->
{{allFields}}                 <!-- List of { name, value } maps (uniform iteration) -->
{{hasFields}}.                <!-- Boolean -->
{{hasReferencedFragments}}.   <!-- Boolean -->
{{referencedFragments}}       <!-- List of referenced-fragment maps -->
```

### Feldzugriff {#field-access}

Zugriff auf Felder:

```handlebars
{{{fields.fieldName}}}                    <!-- Direct field -->
{{{fields.author.name}}}                  <!-- Nested Content Fragment field -->
{{{fields.author.org.address.city}}}      <!-- Multi-level nesting -->
{{{fields.tags.[0]}}}                     <!-- Array by index -->
{{#each fields.tags}}...{{/each}}         <!-- Array iteration -->
{{{fields.authors.[0].name}}}             <!-- Multi-valued Content Fragment reference -->
```

### Kontrollfluss {#control-flow}

Der Kontrollfluss:

```handlebars
{{#if condition}}...{{/if}}               <!-- Conditional -->
{{#if condition}}...{{else}}...{{/if}}    <!-- If/else -->
{{#unless condition}}...{{/unless}}       <!-- Negative conditional -->
{{#each array}}...{{/each}}               <!-- Iteration -->
{{#each array}}...{{else}}...{{/each}}    <!-- Iteration with fallback -->
{{#with object}}...{{/with}}              <!-- Change scope -->
```

### Schleifenvariablen {#loop-variables}

Die Schleifenvariablen:

```handlebars
{{@index}}        <!-- 0-based index -->
{{@number}}       <!-- 1-based index -->
{{@first}}        <!-- true for first item -->
{{@last}}         <!-- true for last item -->
{{@key}}          <!-- Object property name -->
{{this}}          <!-- Current item -->
{{../parent}}     <!-- Access parent scope -->
```

### Helper für benutzerdefinierte Vorlagen {#custom-template-helpers}

Die benutzerdefinierten Vorlagen-Helper:

```handlebars
{{{asset fields.image class="css-class"}}}                <!-- Image with class -->
{{{asset fields.image class="c1" id="my-id"}}}            <!-- Image with multiple attrs -->
{{{asset fields.image alt="Custom alt text"}}}            <!-- Override alt text -->
{{{asset fields.image loading="lazy" data-x="val"}}}      <!-- Custom attributes -->

{{{text fields.title class="title-class"}}}               <!-- Span with class -->
{{{text fields.price class="price" id="p1"}}}             <!-- Span with multiple attrs -->
{{{text this class="item" data-index=@index}}}            <!-- In loops -->
```

## Zusätzliche Ressourcen {#additional-resources}

Zusätzliche Ressourcen sind verfügbar:

* [Dokumentation zu Handlebars](https://handlebarsjs.com/)
* [Integrierte Handlebars-Helfer](https://handlebarsjs.com/guide/builtin-helpers.html)
* [Dokumentation zu AEM-Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)

