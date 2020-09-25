---
title: Mustertypen von ContextHub-Benutzeroberflächenmodulen
description: ContextHub bietet mehrere Musterbenutzeroberflächenmodule, die Sie in Ihren Lösungen verwenden können
translation-type: tm+mt
source-git-commit: b8bc27b51eefcfcfa1c23407a4ac0e7ff068081e
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 66%

---


# Mustertypen von ContextHub-Benutzeroberflächenmodulen {#sample-contexthub-ui-module-types}

ContextHub bietet mehrere Musterbenutzeroberflächenmodule, die Sie in Ihren Lösungen verwenden können. Die folgenden Informationen werden bereitgestellt:

* Die Hauptfunktionen des Benutzeroberflächenmoduls.
* Gibt an, wo der Quellcode zu finden ist, damit Sie ihn zum Lernen öffnen können.
* So wird das Benutzeroberflächenmodul konfiguriert.

Informationen zum Hinzufügen von Benutzeroberflächenmodulen zu ContextHub finden Sie unter [Hinzufügen eines Benutzeroberflächenmoduls](configuring-contexthub.md#adding-a-ui-module). Informationen zum Entwickeln von Benutzeroberflächenmodulen finden Sie unter [Erstellen von ContextHub-Benutzeroberflächenmodultypen](extending-contexthub.md#creating-contexthub-ui-module-types).

## Benutzeroberflächenmodultyp contexthub.base {#contexthub-base-ui-module-type}

Der Benutzeroberflächenmodultyp contexthub.base ist der Basistyp für alle anderen Benutzeroberflächenmodultypen. Als solches stellt er allgemeine Funktionen zum Rendern von Storedaten bereit.

Die folgenden Eigenschaften sind verfügbar:

* **Titel und Symbol:** Geben Sie einen Titel für das Benutzeroberflächenmodul und ein Symbol an. Das Symbol kann über eine URL oder über die Coral-Benutzeroberflächensymbolbibliothek referenziert werden.
* **Storedaten:** Identifizieren Sie einen oder mehrere Stores, von denen Daten abgerufen werden sollen.
* **Inhalt:** Geben Sie den Inhalt an, der im Benutzeroberflächenmodul angezeigt wird, so wie er in der ContextHub-Symbolleiste angezeigt wird.
* **Popover-Inhalt:** Geben Sie den Inhalt an, der in einem Popover angezeigt wird, wenn auf das Benutzeroberflächenmodul geklickt oder getippt wird.
* **Vollbildmodus:** Kontrollieren Sie, ob der Vollbildmodus erlaubt ist.

Der Quellcode befindet sich unter `/libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js`.

### Konfiguration {#configuration}

Konfigurieren Sie das Benutzeroberflächenmodul contexthub.base mithilfe eines JavaScript-Objekts im JSON-Format. Fügen Sie eine der folgenden Eigenschaften zum Konfigurieren der Benutzeroberflächenmodulfunktionen hinzu:

* **image:** URL zu einem Bild, das als Symbol angezeigt werden soll.
* **Symbol:** Der Name einer [Coral UI-Symbolklasse](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html) . Wenn Sie einen Wert für das Symbol und die Bildeigenschaften angeben, wird das Bild verwendet.
* **title:** Ein Titel für das UI-Modul. Der Titel wird angezeigt, wenn der Mauszeiger auf dem Benutzeroberflächenmodulsymbol platziert wird.
* **fullscreen:** Ein boolescher Wert, der angibt, ob das UI-Modul den Vollbildmodus unterstützt. Use `true` to support fullscreen and `false` to prevent fullscreen mode.
* **template:** Eine [Handlebars-Vorlage](https://handlebarsjs.com/), die den Inhalt angibt, der in der ContextHub-Symbolleiste gerendert werden soll. Use at most two `<p>` tags.
* **storeMapping:** Ein Schlüssel-/Storediagramm. Verwenden Sie den Schlüssel in den Handlebar-Vorlagen, um auf die zugehörigen ContextHub-Speicherdaten zuzugreifen.
* **liste:** Ein Array von Elementen, die beim Klicken auf das UI-Modul als Liste in einem Popup angezeigt werden. Wenn Sie diesen Artikel einschließen, schließen Sie popoverTemplate nicht ein. Der Wert ist ein Array von Objekten mit folgenden Schlüsseln:
   * title: Der Text, der für diesen Artikel angezeigt werden soll
   * image: (optional) Eine URL zu einem Bild, das links angezeigt werden soll
   * icon: (optional) Eine CUI-Symbolklasse, die auf der linken Seite angezeigt werden soll. wird ignoriert, wenn ein Bild angegeben wird
   * selected: (optional) Ein boolescher Wert, der angibt, ob dieses Element als ausgewählt angezeigt werden soll (true=ausgewählt). Standardmäßig werden ausgewählte Elemente in Fettschrift angezeigt. Verwenden Sie eine `listType`-Eigenschaft, um andere Erscheinungen zu konfigurieren (siehe unten).
* **listType:** Der für Popover-Listenelemente zu verwendende Stil. Verwenden Sie einen der folgenden Werte:
   * checkmark
   * Kontrollkästchen 
   * radio
* **popoverTemplate:** Eine Handlebars-Vorlage, die den Inhalt angibt, der beim Klicken auf das UI-Modul im Popup wiedergegeben werden soll. Wenn Sie diesen Artikel einschließen, schließen Sie das `list`-Element nicht ein.

### Beispiel {#example}

The following example configures a c`ontexthub.base` UI module to display information from a [contexthub.emulators](sample-stores.md#granite-emulators-sample-store-candidate) store. Das `template`-Element veranschaulicht, wie Daten aus dem Store mithilfe des Schlüssels abgerufen werden, den das `storeMapping`-Element erstellt.

```javascript
{
   "icon": "coral-Icon--move",
    "title": "Screen Resolution",
    "storeMapping": {
      "emulator": "emulators"
    },
    "template": "<p>{{{ i18n \"Resolution\"}}}</p><p>{{{emulator.currentDevice.width}}} x {{{emulator.currentDevice.height}}}</p>"
}
```

![contexthub.base-Modul](assets/base-module.png)

## Benutzeroberflächenmodultyp contexthub.browserinfo {#contexthub-browserinfo-ui-module-type}

The `contexthub.browserinfo` UI module displays information about the client web browser and operating system. Informationen werden vom Store „surferinfo“ bezogen, der auf dem Storekandidaten [contexthub.surferinfo](sample-stores.md#contexthub-surferinfo-sample-store-candidate) basiert.

![contexthub.browserinfo-Modul](assets/browserinfo-module.png)

The source code for the UI module is located at `/libs/granite/contexthub/components/modules/browserinfo`. Although `contexthub.browserinfo` extends the `contexthub.base` UI module, it does not override or provide additional functions. Die Implementierung stellt eine Standardkonfiguration zum Rendern von Browserinformationen bereit.

### Konfiguration {#configuration-1}

Instanzen des Benutzeroberflächenmoduls contexthub.browserinfo benötigen keinen Wert für die Detailkonfiguration. Der folgende JSON-Text repräsentiert die Standardkonfiguration des Moduls.

```javascript
{
   "icon":"coral-Icon--globe",
   "title":"Browser/OS Information",
   "storeMapping":{"surferinfo":"surferinfo"},
   "template":"<p>{{surferinfo.browser.family}} {{surferinfo.browser.version}}</p><p>{{surferinfo.os.name}} {{surferinfo.os.version}}</p>"
}
```

## Benutzeroberflächenmodultyp contexthub.datetime  {#contexthub-datetime-ui-module-type}

The `contexthub.datetime` UI module displays the date and time that is stored in a store named datetime that is based on the `contexthub.datetime` store candidate.

![contexthub.datetime-Modul](assets/datetime-module.png)

Das Modul enthält ein Popover-Formular, mit dem Sie Datum und Uhrzeit im Store ändern können.

The source of the `contexthub.datetime` UI module is located at `/libs/granite/contexthub/components/modules/datetime`.

### Konfiguration {#configuration-2}

Instanzen des Benutzeroberflächenmoduls contexthub.datetime benötigen keinen Wert für die Detailkonfiguration. Der folgende JSON-Text repräsentiert die Standardkonfiguration des Moduls.

```javascript
{
   "icon":"coral-Icon--clock",
   "title":"DATE&TIME",
   "clickable":true,
   "storeMapping":{"d":"datetime"},
   "template":"<p class=\"contexthub-module-line1\">{{i18n \"Date&Time\"}}</p><p class=\"contexthub-module-line2\">{{d.formatted.locale.date}} {{d.formatted.locale.time}}</p>",
   "popoverTemplate":"<div class=\"datetime center\"><div class=\"coral-DatePicker-calendar\" data-init=\"datepicker\"><input class=\"coral-Textfield\" type=\"datetime\" value=\"{{d.formatted.iso}}\"><button class=\"coral-Button coral-Button--secondary coral-Button--square\" title=\"{{i18n \"Datetime picker\"}}\"><i class=\"coral-Icon coral-Icon--calendar coral-Icon--sizeS\"></i></button></div></div>"
}
```

## Benutzeroberflächenmodultyp contexthub.location {#contexthub-location-ui-module-type}

The `contexthub.location` UI module displays the longitude and latitude of the client. Das Modul bietet ein Popover mit einer Google-Karte, auf die Sie klicken können, um den aktuellen Standort zu ändern. Das Modul erhält Informationen von einem ContextHub-Store namens Geolocation, der auf dem Storekandidaten [contexthub.geolocation](sample-stores.md#contexthub-geolocation-sample-store-candidate) basiert.

![contexthub.location-Modul](assets/location-module.png)

The source of the UI module is located at `/etc/cloudsettings/default/contexthub/geolocation`.

### Konfiguration {#configuration-4}

Instanzen des Benutzeroberflächenmoduls contexthub.location erfordern keinen Wert für die Detailkonfiguration. Der folgende JSON-Text repräsentiert die Standardkonfiguration des Moduls.

```javascript
{
 "icon":"coral-Icon--compass",
 "title":"Location",
 "clickable":true,
 "editable":{"key":"/geolocation","disabled":[],"hidden":["/geolocation/generatedThumbnail","/geolocation/city","/geolocation/country"]},
 "fullscreen":true,
 "storeMapping":{"g":"geolocation"},
 "template":"<p>{{i18n \"Location\"}}</p><p>{{g.address.postalCode}} {{g.address.city}}{{#if g.address.city}}{{#if g.address.region}},{{/if}}{{/if}} {{g.address.region}}</p>",
 "list":[
  {"title":"Basel, Switzerland",
  "data":{"longitude":7.58929,"latitude":47.554746,"city":"Basel","country":"Switzerland"}},
  {"title":"Melbourne, Australia",
  "data":{"longitude":144.96328,"latitude":-37.814107,"city":"Melbourne","country":"Australia"}},
  {"title":"Beijing, China",
  "data":{"longitude":116.407526,"latitude":39.90403,"city":"Beijing","country":"China"}},
  {"title":"New York, NY, USA",
  "data":{"longitude":-74.005973,"latitude":40.714353,"city":"New York","country":"United States"}},
  {"title":"Paris, France",
  "data":{"longitude":2.352222,"latitude":48.856614,"city":"Paris","country":"France"}},
  {"title":"Rio de Janeiro, Brazil",
  "data":{"longitude":-43.20071,"latitude":-22.913395,"city":"Rio","country":"Brazil"}},
  {"title":"San Jose, CA, USA",
  "data":{"longitude":-121.894955,"latitude":37.339386,"city":"San Jose","country":"United States"}},
  {"title":"Tokyo, Japan",
  "data":{"longitude":139.691706,"latitude":35.689487,"city":"Shinjuku","country":"Japan"}}
 ],
 "listType":"checkmark"
}
```

## Benutzeroberflächenmodultyp contexthub.screen-orientation  {#contexthub-screen-orientation-ui-module-type}

The `contexthub.screen-orientation` UI module displays the current screen orientation of the client. Obwohl standardmäßig deaktiviert, bietet das Modul ein Popover, mit dem Sie eine Ausrichtung auswählen können. Das Modul erhält Informationen von einem ContextHub-Store namens Emulatoren, der auf dem Storekandidaten [granite.emulators](sample-stores.md#granite-emulators-sample-store-candidate) basiert.

![contexthub.screen-orientation-Modul](assets/screen-orientation-module.png)

The source of the UI module is located at `/libs/granite/contexthub/components/modules/screen-orientation`.

### Konfiguration {#configuration-5}

Instances of the `contexthub.screen-orientation` UI module do not require a value for the Detail Configuration. Der folgende JSON-Text repräsentiert die Standardkonfiguration des Moduls. Note that the `clickable` property is `false` by default. If you override the default configuration to set `clickable` to `true`, clicking the module reveals a popup where you can select the orientation.

```javascript
{
   "icon":"coral-Icon--rotateRight",
   "title":"Screen Orientation",
   "clickable":false,
   "storeMapping":{"emulator":"emulators"},
   "template":"<p>{{{ i18n \"Screen Orientation\" }}}</p><p>{{{ emulator.currentDevice.orientation }}}",
   "listReference":"/emulators/orientations",
   "listType":"checkmark"
}
```

## Benutzeroberflächenmodultyp contexthub.tagcloud {#contexthub-tagcloud-ui-module-type}

The `contexthub.tagcloud` UI module displays information about tags. Auf der Symbolleiste zeigt das UI-Modul die Anzahl der Tags an. Das Popupmenü zeigt eine Tagcloud und ein Textfeld zum Hinzufügen neuer Tags an. Das Benutzeroberflächenmodul ruft Informationen aus einem ContextHub-Store namens tagcloud ab, der auf dem der Storekandidat `contexthub.tagcloud` basiert.

![contexthub.tagcloud-Modul](assets/tagcloud-module.png)

The source of the UI module is located at `/libs/granite/contexthub/components/modules/tagcloud`.

### Konfiguration {#configuration-6}

Instances of the `contexthub.tagcloud` UI module do not require a value for the Detail Configuration. Der folgende JSON-Text repräsentiert die Standardkonfiguration des Moduls.

```javascript
{
   "icon":"coral-Icon--tag",
   "title":"TagCloud",
   "clickable":true,
   "storeMapping":{"t":"tagcloud"},
   "maxTags":20,
   "template":"<p class=\"contexthub-module-line1\">{{i18n \"TagCloud\"}}</p><p class=\"contexthub-module-line2\">{{stats.total}} {{i18n \"Tags\"}}</p>",
   "popoverTemplate":"<div class=\"contexthub-popover-content center\"><p class=\"stats\">{{stats.total}} {{i18n \"Tags\"}} | {{stats.hits}} {{i18n \"Hits\"}} | {{i18n \"Last tag\"}}: {{#if stats.recent}}{{stats.recent}}{{else}}{{i18n \"Unknown\"}}{{/if}}</p><p class=\"tagcloud\">{{#each tags}}<span class=\"tag{{this.weight}}\">{{this.name}}</span> {{/each}}</p><div class=\"coral-InputGroup\"><input type=\"text\" class=\"coral-InputGroup-input coral-Textfield tag-name\" placeholder=\"{{i18n \"Add a namespace:my/tag\"}}\" pattern=\"^[A-Za-z0-9_\\-]+(:[A-Za-z0-9_\\-\\/]+)?$\" title=\"{{i18n \"namespace:my/tag\"}}\"><span class=\"coral-InputGroup-button\"><button class=\"coral-Button coral-Button--secondary coral-Button--square contexthub-new-tag\" type=\"button\" title=\"{{i18n \"increment\"}}\"><i class=\"coral-Icon coral-Icon--sizeS coral-Icon--add\"></i></button></span></div></div>"
}
```

## Benutzeroberflächenmodultyp granite.profile  {#granite-profile-ui-module-type}

The `granite.profile` ContextHub UI module displays the display name of the current user. Das Popupmenü zeigt den Anmeldenamen des Benutzers auf, was Ihnen ermöglicht, den Wert der Anzeigename zu ändern. Das Benutzeroberflächenmodul erhält Informationen von einem ContextHub-Store namens Profile, der auf dem Storekandidaten [granite.profile](sample-stores.md#granite-profile-sample-store-candidate) basiert.

![granite.Profil-Modul](assets/profile-module.png)

The source of the UI module is at `/libs/granite/contexthub/components/modules/profile`.

### Konfiguration {#configuration-7}

Instances of the `granite.profile` UI module do not require a value for the Detail Configuration. Der folgende JSON-Text repräsentiert die Standardkonfiguration des Moduls.

```javascript
{
   "icon":"coral-Icon--user",
   "title":"Profile",
   "clickable":true,
   "editable":{
      "key":"/profile",
      "disabled":["/profile/authorizableId"],
      "hidden":["/profile/avatar","/profile/path"]},
   "storeMapping":{"p":"profile"},
   "template":"<p class=\"contexthub-module-line1\">{{i18n \"Persona\"}}</p><p class=\"contexthub-module-line2\">{{p.displayName}}</p>",
   "listType":"checkmark"
}
```
