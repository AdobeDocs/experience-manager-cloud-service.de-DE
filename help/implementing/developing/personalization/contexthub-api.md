---
title: Referenz zur ContextHub-JavaScript-API
description: Die ContextHub-JavaScript-API ist für Ihre Skripte verfügbar, wenn die ContextHub-Komponente zur Seite hinzugefügt wurde
translation-type: tm+mt
source-git-commit: e361f24b943eff68982a37ac0dc2597f92450026
workflow-type: tm+mt
source-wordcount: '4621'
ht-degree: 73%

---


# Referenz zur ContextHub-JavaScript-API {#contexthub-javascript-api-reference}

Die ContextHub-JavaScript-API ist für Ihre Skripte verfügbar, wenn die [ContextHub-Komponente zur Seite hinzugefügt wurde](configuring-contexthub.md#adding-contexthub-to-a-page-component).

## ContextHub-Konstanten {#contexthub-constants}

Konstante Werte, die von der ContextHub-JavaScript-API definiert werden.

### Ereigniskonstanten {#event-constants}

In der folgenden Tabelle sind die Namen von Ereignissen aufgeführt, die bei ContextHub-Stores auftreten. Siehe auch [ContextHub.Utils.Eventing](contexthub-api.md#contexthub-utils-eventing)

| Konstante | Beschreibung | Wert |
|---|---|---|
| `ContextHub.Constants.EVENT_NAMESPACE` | ContextHub-Ereignis-Namensraum | `ch` |
| `ContextHub.Constants.EVENT_ALL_STORES_READY` | Gibt an, dass alle erforderlichen Stores registriert, initialisiert und einsatzbereit sind | `all-stores-ready` |
| `ContextHub.Constants.EVENT_STORES_PARTIALLY_READY` | Gibt an, dass nicht alle Stores innerhalb eines bestimmten Timeouts initialisiert wurden | `stores-partially-ready` |
| `ContextHub.Constants.EVENT_STORE_REGISTERED` | Wird ausgelöst, wenn ein Store registriert ist | `store-registered` |
| `ContextHub.Constants.EVENT_STORE_READY` | Gibt an, dass die Stores einsatzbereit sind. Wird sofort nach der Registrierung ausgelöst, außer bei JSONP-Stores, wo es ausgelöst wird, wenn Daten abgerufen werden. | `store-ready` |
| `ContextHub.Constants.EVENT_STORE_UPDATED` | Wird ausgelöst, wenn ein Store seine Persistenz aktualisiert | `store-updated` |
| `ContextHub.Constants.PERSISTENCE_CONTAINER_NAME` | Name des Persistent-Containers | `ContextHubPersistence` |
| `ContextHub.Constants.SERVICE_RAW_RESPONSE_KEY` | Speichert den spezifischen Namen des Persistenzschlüssels, in dem das unformatierte JSON-Ergebnis gespeichert wird | `/_/raw-response` |
| `ContextHub.Constants.SERVICE_RESPONSE_TIME_KEY` | Speichert einen bestimmten Zeitstempel, der angibt, wann JSON-Daten abgerufen wurden | `/_/response-time` |
| `ContextHub.Constants.SERVICE_LAST_URL_KEY` | Speichert spezifische URL des JSON-Dienstes, der während des letzten Aufrufs verwendet wird | `/_/url` |
| `ContextHub.Constants.IS_CONTAINER_EXPANDED` | Gibt an, ob die Benutzeroberfläche von ContextHub erweitert wird | `/_/container-expanded` |

### Benutzeroberflächen-Ereigniskonstanten {#ui-event-constants}

In der folgenden Tabelle sind die Namen der Ereignisse aufgeführt, die für die ContextHub-Benutzeroberfläche auftreten.

| **Konstante** | **Beschreibung** | **Wert** |
|---|---|---|
| `ContextHub.Constants.EVENT_UI_MODE_REGISTERED` | Wird ausgelöst, wenn ein Modus registriert ist | `ui-mode-registered` |
| `ContextHub.Constants.EVENT_UI_MODE_UNREGISTERED` | Wird ausgelöst, wenn ein Modus nicht registriert ist | `ui-mode-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODE_RENDERER_REGISTERED` | Wird ausgelöst, wenn ein Modus-Renderer registriert ist | `ui-mode-renderer-registered` |
| `ContextHub.Constants.EVENT_UI_MODE_RENDERER_UNREGISTERED` | Wird ausgelöst, wenn ein Modus-Renderer nicht registriert ist | `ui-mode-renderer-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODE_ADDED` | Wird ausgelöst, wenn ein neuer Modus hinzugefügt wird | `ui-mode-added` |
| `ContextHub.Constants.EVENT_UI_MODE_REMOVED` | Wird ausgelöst, wenn ein Modus entfernt wird | `ui-mode-removed` |
| `ContextHub.Constants.EVENT_UI_MODE_SELECTED` | Wird ausgelöst, wenn der Benutzer einen Modus auswählt | `ui-mode-selected` |
| `ContextHub.Constants.EVENT_UI_MODULE_REGISTERED` | Wird ausgelöst, wenn ein neues Modul registriert wird | `ui-module-registered` |
| `ContextHub.Constants.EVENT_UI_MODULE_UNREGISTERED` | Wird ausgelöst, wenn ein Modul nicht registriert ist | `ui-module-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODULE_RENDERER_REGISTERED` | Wird ausgelöst, wenn ein Modul-Renderer registriert ist | `ui-module-renderer-registered` |
| `ContextHub.Constants.EVENT_UI_MODULE_RENDERER_UNREGISTERED` | Wird ausgelöst, wenn ein Modul-Renderer nicht registriert ist | `ui-module-renderer-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODULE_ADDED` | Wird ausgelöst, wenn ein neues Modul hinzugefügt wird | `ui-module-added` |
| `ContextHub.Constants.EVENT_UI_MODULE_REMOVED` | Wird ausgelöst, wenn ein Modul entfernt wird | `ui-module-removed` |
| `ContextHub.Constants.EVENT_UI_CONTAINER_ADDED` | Wird ausgelöst, wenn der UI-Container der Seite hinzugefügt wird | `ui-container-added` |
| `ContextHub.Constants.EVENT_UI_CONTAINER_OPENED` | Wird ausgelöst, wenn die ContextHub-Benutzeroberfläche geöffnet wird | `ui-container-opened` |
| `ContextHub.Constants.EVENT_UI_CONTAINER_CLOSED` | Wird ausgelöst, wenn die ContextHub-Benutzeroberfläche reduziert wird | `ui-container-closed` |
| `ContextHub.Constants.EVENT_UI_PROPERTY_MODIFIED` | Wird ausgelöst, wenn eine Eigenschaft geändert wird | `ui-property-modified` |
| `ContextHub.Constants.EVENT_UI_RENDERED` | Wird jedes Mal ausgelöst, wenn die ContextHub-Benutzeroberfläche wiedergegeben wird (z. B. nach einer Eigenschaftenänderung) | `ui-rendered` |
| `ContextHub.Constants.EVENT_UI_INITIALIZED` | Wird ausgelöst, wenn UI-Container initialisiert wird | `ui-initialized` |
| `ContextHub.Constants.ACTIVE_UI_MODE` | Zeigt den aktiven UI-Modus an | `/_/active-ui-mode` |

## Referenz zur ContextHub-JavaScript-API {#contexthub-javascript-api-reference-2}

Das ContextHub-Objekt bietet Zugriff auf alle Stores.

### Funktionen (ContextHub) {#functions-contexthub}

#### getAllStores() {#getallstores}

Gibt alle registrierten ContextHub-Stores zurück.

Diese Funktion hat keine Parameter.

##### Rückgabe {#returns-}

Ein Objekt, das alle ContextHub-Stores enthält. Jeder Store ist ein Objekt, das denselben Namen wie der Store verwendet.

##### Beispiel {#example-}

Im folgenden Beispiel werden alle Stores und anschließend der Geolocation-Store abgerufen:

```javascript
var allStores = ContextHub.getAllStores();
var geoloc = allStores.geolocation
```

#### getStore(name) {#getstore-name}

Ruft einen Store als ein JavaScript-Objekt ab.

##### Parameter {#parameters-}

* **`name`:** Der Name, mit dem der Store registriert wurde.

##### Rückgabe {#returns-getstore-name}

Ein Objekt, das den Store darstellt.

##### Beispiel {#example-getstore-name}

Im folgenden Beispiel wird der Geolocation-Store abgerufen:

```javascript
var geoloc = ContextHub.getStore("geolocation");
```

## ContextHub.SegmentEngine.Segment {#contexthub-segmentengine-segment}

Stellt ein ContextHub-Segment dar. Use the `ContextHub.SegmentEngine.SegmentManager` to obtain segments.

### Funktionen (ContextHub.ContextEngine.Segment) {#functions-contexthub-contextengine-segment}

#### getName() {#getname}

Gibt den Namen des Segments als Stringwert zurück.

#### getPath() {#getpath}

Gibt den Repository-Pfad der Segmentdefinition als String-Wert zurück.

## ContextHub.SegmentEngine.SegmentManager {#contexthub-segmentengine-segmentmanager}

Bietet Zugriff auf ContextHub-Segmente.

### Funktionen (ContextHub.SegmentEngine.SegmentManager) {#functions-contexthub-segmentengine-segmentmanager}

#### getResolvedSegments() {#getresolvedsegments}

Gibt die Segmente zurück, die im aktuellen Kontext aufgelöst werden. Diese Funktion hat keine Parameter.

##### Rückgabe {#returns-getresolvedsegments}

An array of `ContextHub.SegmentEngine.Segment` objects.

## ContextHub.Store.Core {#contexthub-store-core}

Die Basisklasse für ContextHub-Stores.

### Eigenschaften (ContextHub.Store.Core) {#properties-contexthub-store-core}

#### Vielseitigkeit {#eventing}

Ein [`ContextHub.Utils.Eventing`](#contexthub-utils-eventing) Objekt. Verwenden Sie dieses Objekt zum Binden von Funktionen zum Speichern von Ereignissen. For information about the default value and initialization, see [`init(name,config)`](#init-name-config).

#### name {#name}

Der Name des Stores.

#### persistence {#persistence}

Ein `ContextHub.Utils.Persistence` Objekt. For information about the default value and initialization, see [`init(name,config)`](#init-name-config).

### Funktionen (ContextHub.Store.Core) {#functions-contexthub-store-core}

#### addAllItems(tree, options) {#addallitems-tree-options}

Führt ein Datenobjekt oder ein Array mit den Storedaten zusammen. Jedes Schlüssel/Wert-Paar im Objekt oder Array wird dem Store hinzugefügt (über die Funktion `setItem`):

* **Objekt:** Schlüssel sind die Eigenschaftsnamen.
* **Array:** Schlüssel sind die Array-Indizes.

Beachten Sie, dass Werte Objekte sein können.

##### Parameter {#parameters-addallitems}

* **`tree`:** (Objekt oder Array) Die Daten, die dem Store hinzugefügt werden sollen.
* **`options`:** (Objekt) Ein optionales Objekt von Optionen, das an die setItem-Funktion übergeben wird. For information, see the `options` parameter of [`setItem(key,value,options)`](#setitem-key-value-options).

##### Rückgabe {#returns-addallitems}

Ein `boolean` Wert:

* Der Wert `true` gibt an, dass das Datenobjekt gespeichert wurde.
* Der Wert `false` gibt an, dass der Datenstore unverändert ist.

#### addReference(key, anotherKey) {#addreference-key-anotherkey}

Erstellt eine Referenz von einem Schlüssel auf einem anderen Schlüssel. Ein Schlüssel kann sich nicht selbst referenzieren.

##### Parameter {#parameters-addreference}

* **`key`:** Der Schlüssel, auf den verwiesen wird `anotherKey`.

* **`anotherkey`:** Sie Schlüssel, auf den verwiesen wird `key`.

##### Rückgabe {#returns-addreference}

Ein `boolean` Wert:

* Der Wert `true` gibt an, dass die Referenz hinzugefügt wurde.
* Der Wert `false` gibt an, dass keine Referenz hinzugefügt wurde.

#### announceReadiness() {#announcereadiness}

Löst das `ready`-Ereignis für diesen Store aus. Diese Funktion hat keine Parameter und gibt keinen Wert zurück.

#### clean() {#clean}

Entfernt alle Daten aus dem Store. Die Funktion hat keine Parameter und keinen Rückgabewert.

#### getItem(key) {#getitem-key}

Gibt den Wert zurück, der einem Schlüssel zugeordnet ist.

##### Parameter {#parameters-getitem}

* **`key`:** (String) der Schlüssel, für den der Wert zurückgegeben werden soll.

##### Rückgabe {#returns-getitem}

Ein Objekt, das den Wert für den Schlüssel darstellt.

#### getKeys(includeInternals) {#getkeys-includeinternals}

Ruft die Schlüssel aus dem Store ab. Optional können Sie die Schlüssel abrufen, die intern vom ContextHub-Framework verwendet werden.

##### Parameter {#parameters-getkeys}

* **`includeInternals`:** Der Wert `true` schließt intern verwendete Schlüssel in die Ergebnisse ein. These keys begin with the underscore (`_`) character. Der Standardwert ist `false`.

##### Rückgabe {#returns-getkeys}

Ein Array von Schlüsselnamen (`string`-Werte).

#### getReferences() {#getreferences}

Ruft die Referenzen aus dem Store ab.

##### Rückgabe {#returns-getreferences}

Ein Array, das referenzierende Schlüssel als Indizes für die referenzierten Schlüssel verwendet:

* Referencing keys correspond with the `key` parameter of the `addReference` function.
* Referenced keys correspond with the `anotherKey` parameter of the `addReference` function.

#### getTree(includeInternals) {#gettree-includeinternals}

Ruft den Datenbaum vom Store ab. Optional können Sie die Schlüssel/Wert-Paare einschließen, die intern vom ContextHub-Framework verwendet werden.

##### Parameter {#parameters-gettree}

* `includeInternals:` Ein Wert von `true` enthält intern verwendete Schlüssel/Wert-Paare in den Ergebnissen. The keys of this data begin with the underscore (`_`) character. Der Standardwert ist `false`.

##### Rückgabe {#returns-gettree}

Ein Objekt, das die Datenstruktur darstellt. Die Schlüssel sind die Eigenschaftsnamen des Objekts.

#### init(name, config) {#init-name-config}

Initialisiert den Store.

* Setzt die Storedaten auf ein leeres Objekt.
* Setzt die Storereferenzen auf ein leeres Objekt.
* The `eventChannel` is `data:<name>`, where `<name>` is the store name.
* The `storeDataKey` is `/store/<name>`, where `<name>` is the store name.

##### Parameter {#parameters-init}

* **`name`:** Der Name des Stores.
* **`config`:** Ein Objekt, das Konfigurationseigenschaften enthält:
   * `eventDeferring`: Der Standardwert ist 32.
   * `eventing`: Das [ContextHub.Utils.Eventing](#contexthub-utils-eventing)-Objekt für diesen Store. The default value is the `ContextHub.eventing` object uses.
   * `persistence`: Das `ContextHub.Utils.Persistence` Objekt für diesen Store. Der Standardwert ist das `ContextHub.persistence`-Objekt.

#### isEventingPaused() {#iseventingpaused}

Ermittelt, ob das Eventing für diesen Store angehalten wurde.

##### Rückgabe {#returns-iseventingpaused}

Ein boolescher Wert:

* `true`: Eventing ist angehalten, sodass keine Ereignisse für diesen Store ausgelöst werden.
* `false`: Eventing ist nicht angehalten, sodass Ereignisse für diesen Store ausgelöst werden.

#### PauseEventing() {#pauseeventing}

Hält Eventing für den Store an, sodass keine Ereignisse ausgelöst werden. Diese Funktion erfordert keine Parameter und gibt keinen Wert zurück.

#### removeItem(key, options) {#removeitem-key-options}

Entfernt ein Schlüssel/Wert-Paar aus dem Store.

Wenn ein Schlüssel entfernt wird, löst die Funktion das `data`-Ereignis aus. Zu den Ereignis-Daten gehören der Name des Speichers, der Name des entfernten Schlüssels, der entfernte Wert, der neue Wert des Schlüssels (null) und der Aktionstyp &quot;remove&quot;.

Optional können Sie das Auslösen des Ereignisses `data` verhindern.

##### Parameter {#parameters-removeitem}

* **`key`:** (String) Der Name des zu entfernenden Schlüssels.
* **`options`:** (Objekt) Ein Objekt von Optionen. Die folgenden Objekteigenschaften sind gültig:
   * silent: Ein Wert `true` verhindert das Auslösen des `data`-Ereignisses. Der Standardwert ist `false`.

##### Rückgabe {#returns-removeitem}

Ein `boolean` Wert:

* A value of `true` indicates the key/value pair was removed.
* A value of `false` indicates that the data store is unchanged because the key was not found in the store.

#### removeReference(key) {#removereference-key}

Entfernt eine Referenz aus dem Store.

##### Parameter {#parameters-removereference}

* **`key`:** Die zu entfernende Schlüsselreferenz. This parameter corresponds with the `key` parameter of the `addReference` function.

##### Rückgabe {#returns-removereference}

Ein `boolean` Wert:

* A value of `true` indicates the reference was removed.
* A value of `false` indicates that the key was not valid and the store is unchanged.

#### reset(keepRemainingData) {#reset-keepremainingdata}

Setzt die Anfangswerte der persistenten Daten des Stores zurück. Optional können Sie alle anderen Daten aus dem Store entfernen. Eventing wird für diesen Store angehalten, während der Store zurückgesetzt wird. Diese Funktion gibt keinen Wert zurück.

Initial values are provided in the `initialValues` property of the config object that is used to instantiate the store object.

##### Parameter {#parameters-reset}

* **`keepRemainingData`**: (Boolesch) Ein Wert „true“ bewirkt, dass nicht-initial-Daten beibehalten werden. Der Wert „false“ bewirkt, dass alle Daten mit Ausnahme der Anfangswerte entfernt werden.

#### resolveReference(key, retry) {#resolvereference-key-retry}

Ruft einen referenzierten Schlüssel ab. Optional können Sie die Anzahl der Iterationen angeben, die zum Lösen der besten Übereinstimmung verwendet werden sollen.

##### Parameter {#parameters-resolvereference}

* **`key`:** (String) Der Schlüssel, für den die Referenz aufgelöst werden soll. This `key` parameter corresponds with the `key` parameter of the `addReference` function.
* **`retry`:** (Number) Die Anzahl der zu verwendenden Iterationen.

##### Rückgabe {#returns-resolvereference}

Ein `string`-Wert, der den referenzierten Schlüssel darstellt. Wenn keine Referenz aufgelöst wird, wird der Wert des `key`-Parameters zurückgegeben.

#### resumeEventing() {#resumeeventing}

Setzt Eventing für diesen Store fort, sodass Ereignisse ausgelöst werden. Diese Funktion definiert keine Parameter und gibt keinen Wert zurück.

#### setItem(key, value, options) {#setitem-key-value-options}

Fügt ein Schlüssel/Wert-Paar dem Store hinzu.

Löst das `data`-Ereignis nur aus, wenn der Wert für den Schlüssel sich von dem Wert unterscheidet, der aktuell für den Schlüssel gespeichert ist. Optional können Sie das Auslösen des `data`-Ereignisses verhindern.

Die Ereignisdaten umfassen den Storenamen, den Schlüssel, den vorherigen Wert, den neuen Wert und den Aktionstyp von `set`.

##### Parameter {#parameters-setitem}

* **`key`:** (String) Der Name des Schlüssels.
* **`options`:** (Objekt) Ein Objekt von Optionen. Die folgenden Objekteigenschaften sind gültig:
   * `silent`: Der Wert &quot; `true` verhindert das Auslösen des `data` Ereignisses. Der Standardwert ist `false`.
* **`value`:** (Object) Der Wert, der dem Schlüssel zugeordnet werden soll.

##### Rückgabe {#returns-setitem}

Ein `boolean` Wert:

* Der Wert `true` gibt an, dass das Datenobjekt gespeichert wurde.
* Der Wert `false` gibt an, dass der Datenstore unverändert ist.

## ContextHub.Store.JSONPStore {#contexthub-store-jsonpstore}

Ein Store, der JSON-Daten enthält. Die Daten werden von einem externen JSONP-Dienst oder optional von einem Dienst abgerufen, der JSON-Daten zurückgibt. Geben Sie die Details des Diensts mithilfe der [`init`](#init-name-config)-Funktion an, wenn Sie eine Instanz dieser Klasse erstellen.

Der Store verwendet die speicherinterne Persistenz (JavaScript-Variable). Storedaten sind nur während der Lebensdauer der Seite verfügbar.

ContextHub.Store.JSONPStore extends [ContextHub.Store.Core](#contexthub-store-core) and inherits the functions of that class.

### Funktionen (ContextHub.Store.JSONPStore) {#functions-contexthub-store-jsonpstore}

#### configureService(serviceConfig, override) {#configureservice-serviceconfig-override}

Konfiguriert die Details für die Verbindung mit dem JSONP-Dienst, den dieses Objekt verwendet. Sie können entweder die vorhandene Konfiguration aktualisieren oder ersetzen. Die Funktion gibt keinen Wert zurück.

##### Parameter {#parameters-configureservice}

* **`serviceConfig`:** Ein Objekt, das folgende Eigenschaften enthält:
   * `host`: (String) Servernamen oder IP-Adresse.
   * `jsonp`: (Boolesch) Ein Wert „true“ zeigt an, dass der Service ein JSONP-Service ist, andernfalls ist er „false“. Falls „true“, {callback: &quot;ContextHub.Callbacks.*Object.name*} Objekt wird dem service.params-Objekt hinzugefügt.
   * `params`: (Objekt) URL-Parameter, die als Objekteigenschaften dargestellt werden. Parameternamen sind Eigenschaftsnamen und Parameterwerte sind Eigenschaftswerte.
   * `path`: (String) Der Pfad zum Dienst.
   * `port`: (Number) Die Portnummer des Dienstes.
   * `secure`: (String oder Boolesch) Bestimmt das für die Service-URL zu verwendende Protokoll:
      * `auto`: //
      * `true`: https://
      * `false`: http://
* **override:** (Boolesch). A value of `true` causes the existing service configuration to be replaced by the properties of `serviceConfig`. A value of `false` causes the existing service configuration properties to be merged with the properties of `serviceConfig`.

#### getRawResponse() {#getrawresponse}

Gibt die unbearbeitete Antwort zurück, die seit dem letzten Aufruf des JSONP-Dienstes zwischengespeichert wurde. Die Funktion erfordert keine Parameter.

##### Rückgabe {#returns-getrawresponse}

Ein Objekt, das die unbearbeitete Antwort darstellt.

#### getServiceDetails() {#getservicedetails}

Ruft das Dienstobjekt für dieses ContextHub.Store.JSONPStore-Objekt ab. Das Dienstobjekt enthält alle Informationen, die zum Erstellen der Service-URL erforderlich sind.

##### Rückgabe {#returns-getservicedetails}

Ein Objekt mit den folgenden Eigenschaften:

* **`host`:** (String) Servernamen oder IP-Adresse.
* **`jsonp`:** (Boolesch) Ein Wert true zeigt an, dass der Dienst ein JSONP-Dienst ist, andernfalls ist er false. Falls „true“, {callback: &quot;ContextHub.Callbacks.*Object.name*} Objekt wird dem service.params-Objekt hinzugefügt.
* **`params`:** (Objekt) URL-Parameter, die als Objekteigenschaften dargestellt werden. Parameternamen sind Eigenschaftsnamen und Parameterwerte sind Eigenschaftswerte.
* **`path`:** (String) Der Pfad zum Dienst.
* **`port`:** (Number) Die Portnummer des Dienstes.
* **`secure`:** (String oder Boolesch) Bestimmt das für die Service-URL zu verwendende Protokoll:
   * `auto`: //
   * `true`: https://
   * `false`: http://

#### getServiceURL(resolve) {#getserviceurl-resolve}

Ruft die URL des JSONP-Dienstes ab.

##### Parameter {#parameters-getserviceurl}

* **`resolve`:** (Boolesch) Bestimmt, ob aufgelöste Parameter in die URL aufgenommen werden sollen. A value of `true` resolves parameters, and `false` does not.

##### Rückgabe {#returns-getserviceurl}

Ein `string`-Wert, der die Dienst-URL darstellt.

#### init(name, config) {#init-name-config-1}

initializes the `ContextHub.Store.JSONPStore` object.

##### Parameter {#parameters-init-1}

* **`name`:** (String) Der Name des Stores.
* **`config`:** (Object) Ein Objekt, das die Service-Eigenschaft enthält. Das JSONPStore-Objekt verwendet die Eigenschaften des `service`objekts, um die URL des JSONP-Service zu erstellen:
   * `eventDeferring`: 32.
   * `eventing`: Das ContextHub.Utils.Eventing-Objekt für diesen Store. Der Standardwert ist das `ContextHub.eventing`-Objekt.
   * `persistence`: Das ContextHub.Utils.Persistence-Objekt für diesen Store. Standardmäßig wird die Storepersistenz verwendet (JavaScript-Objekt).
   * `service`: (Object)
      * `host`: (String) Servernamen oder IP-Adresse.
      * `jsonp`: (Boolesch) Ein Wert „true“ zeigt an, dass der Service ein JSONP-Service ist, andernfalls ist er „false“. Wenn &quot;true&quot;, wird das `{callback: "ContextHub.Callbacks.*Object.name*}`Objekt `service.params`hinzugefügt.
      * `params`: (Objekt) URL-Parameter, die als Objekteigenschaften dargestellt werden. Parameternamen und Werte sind jeweils die Namen und Werte der Objekteigenschaften.
      * `path`: (String) Der Pfad zum Dienst.
      * `port`: (Number) Die Portnummer des Dienstes.
      * `secure`: (String oder Boolesch) Bestimmt das für die Service-URL zu verwendende Protokoll:
         * `auto`: //
         * `true`: https://
         * `false`: http://
      * `timeout`: (Number) Die Zeitspanne, die gewartet wird, bis der JSONP-Dienst vor Ablauf der Zeit reagiert (in Millisekunden).
         * `ttl`: Die Mindestdauer in Millisekunden, die zwischen Aufrufen an den JSONP-Dienst vergeht. (Siehe [queryService](#queryservice-reload) Funktion).

#### queryService(reload) {#queryservice-reload}

Fragt den Remote-JSONP-Dienst ab und speichert die Antwort zwischen. If the amount of time since the previous call to this function is less than the value of `config.service.ttl`, the service is not called and the cached response is not changed. Optional können Sie den Dienst erzwingen aufgerufen zu werden. Die Eigenschaft `config.service.ttl` wird festgelegt, wenn die [init](#init-name-config)-Funktion aufgerufen wird, um den Store zu initialisieren.

Löst das bereites Ereignis aus, wenn die Abfrage beendet ist. Wenn die JSONP-Service-URL nicht festgelegt ist, führt die Funktion nichts aus.

##### Parameter {#parameters-queryservice}

* **`reload`:** (Boolesch) Ein Wert „true“ entfernt die zwischengespeicherte Antwort und erzwingt den Aufruf des JSONP-Dienstes.

#### Zurücksetzen {#reset}

Setzt die Anfangswerte der persistenten Daten des Stores zurück und ruft dann den JSONP-Dienst auf. Optional können Sie alle anderen Daten aus dem Store entfernen. Eventing wird für diesen Store angehalten, während die Anfangswerte zurückgesetzt werden. Diese Funktion gibt keinen Wert zurück.

Anfangswerte werden in der initialValues-Eigenschaft des config-Objekts bereitgestellt, das zum Instanziieren des Storeobjekts verwendet wird.

##### Parameter {#parameters-reset-1}

* **`keepRemainingData`:** (Boolesch) Ein Wert „true“ bewirkt, dass nicht-initial-Daten beibehalten werden. Der Wert „false“ bewirkt, dass alle Daten mit Ausnahme der Anfangswerte entfernt werden.

#### resolveParameter(f) {#resolveparameter-f}

Löst den angegebenen Parameter auf.

## ContextHub.Store.PersistedJSONPStore {#contexthub-store-persistedjsonpstore}

`ContextHub.Store.PersistedJSONPStore` erweitert [ContextHub.Store.JSONPStore](#contexthub-store-jsonpstore) so, dass es alle Funktionen dieser Klasse übernimmt. Die Daten, die vom JSONP-Dienst abgerufen werden, bleiben jedoch gemäß der Konfiguration der ContextHub-Persistenz bestehen. (See [Persistence Modes:](configuring-contexthub.md#persistence-modes))

## ContextHub.Store.PersistedStore {#contexthub-store-persistedstore}

`ContextHub.Store.PersistedStore` erweitert [ContextHub.Store.Core](#contexthub-store-core) , sodass alle Funktionen dieser Klasse übernommen werden. Die Daten in diesem Store werden gemäß der Konfiguration der ContextHub-Persistenz beibehalten.

## ContextHub.Store.SessionStore {#contexthub-store-sessionstore}

`ContextHub.Store.SessionStore` erweitert [ContextHub.Store.Core](#contexthub-store-core) , sodass alle Funktionen dieser Klasse übernommen werden. Die Daten in diesem Store werden mithilfe der speicherinternen Persistenz beibehalten (JavaScript-Objekt).

## ContextHub.UI {#contexthub-ui}

Verwaltet Benutzeroberflächenmodule und Benutzeroberflächenmodulrenderer.

### Funktionen (ContextHub.UI) {#functions-contexthub-ui}

#### registerRenderer(moduleType, renderer, dontRender) {#registerrenderer-moduletype-renderer-dontrender}

Registriert einen Benutzeroberflächenmodulrenderer mit ContextHub. Nachdem der Renderer registriert ist, kann er verwendet werden, um [Benutzeroberflächenmodule zu erstellen](configuring-contexthub.md#adding-a-ui-module). Verwenden Sie diese Funktion, wenn Sie[ `ContextHub.UI.BaseModuleRenderer`](extending-contexthub.md#creating-contexthub-ui-module-types) erweitern, um einen benutzerdefinierten Benutzeroberflächenmodulrenderer zu erstellen.

##### Parameter {#parameters-registerrenderer}

* **`moduleType`:**(String) Die Kennung für den Benutzeroberflächenmodulrenderer. Wenn ein Renderer bereits mit dem angegebenen Wert registriert ist, wird der vorhandene Renderer nicht registriert, bevor dieser Renderer registriert wird.
* **`renderer`:** (String) Der Name der Klasse, die das UI-Modul rendert.
* **`dontRender`:** (Boolesch) Auf `true` gesetzt, um zu verhindern, dass die ContextHub-Benutzeroberfläche nach der Registrierung des Renderers gerendert wird. Der Standardwert ist `false`.

##### Beispiel {#example-registerrenderer}

The following example registers a renderer as the `contexthub.browserinfo` module type.

```javascript
ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());
```

## ContextHub.Utils.Cookie {#contexthub-utils-cookie}

Eine Dienstprogrammklasse für die Interaktion mit Cookies.

### Funktionen (ContextHub.Utils.Cookie) {#functions-contexthub-utils-cookie}

#### exists(key) {#exists-key}

Ermittelt, ob ein Cookie vorhanden ist.

##### Parameter {#parameters-exists}

* **`key`:** Ein `String`, der den Schlüssel des Cookies enthält, für das Sie testen.

##### Rückgabe {#returns-exists}

A `boolean` value of true indicates that the cookie exists.

##### Beispiel {#example-exists}

```javascript
if (ContextHub.Utils.Cookie.exists("name")) {
   // conditionally-executed code
}
```

#### getAllItems(filter) {#getallitems-filter}

Gibt alle Cookies zurück, deren Schlüssel einem Filter entsprechen.

##### Parameter {#parameters-getallitems}

* **`filter`:** (Optional) Kriterien für die Zuordnung von Cookie-Schlüsseln. Um alle Cookies zurückzugeben, geben Sie keinen Wert an. Die folgenden Typen werden unterstützt:
   * String: Der String wird mit dem Cookie-Schlüssel verglichen.
   * Array: Jedes Element im Array ist ein Filter.
   * Ein RegExp-Objekt: Die Testfunktion des Objekts wird verwendet, um Cookie-Schlüssel abzugleichen.
   * Eine Funktion: Eine Funktion, die einen Cookie-Schlüssel für eine Übereinstimmung testet. Die Funktion muss den Cookie-Schlüssel als Parameter nehmen und true zurückgeben, wenn der Test eine Übereinstimmung bestätigt.

##### Rückgabe {#returns-getallitems}

Ein Objekt von Cookies. Objekteigenschaften sind Cookie-Schlüssel und Schlüsselwerte sind Cookie-Werte.

##### Beispiel {#example-getallitems}

```javascript
ContextHub.Utils.Cookie.getAllItems([/^cq-authoring/, /^cq-editor/])
```

#### getItem(key) {#getitem-key-1}

Gibt einen Cookie-Wert zurück.

##### Parameter {#parameters-getitem-1}

* **`key`:** Der Schlüssel des Cookies, für das Sie einen Wert abrufen möchten.

##### Rückgabe {#returns-getitem-1}

Das Cookie-Wert oder `null`, wenn kein Cookie für den Schlüssel gefunden wurde.

##### Beispiel {#example-getitem-1}

```javascript
ContextHub.Utils.Cookie.getItem("name");
```

#### getKeys(filter) {#getkeys-filter}

Gibt ein Array der Schlüssel der vorhandenen Cookies zurück, die mit einem Filter übereinstimmen.

##### Parameter {#parameters-getkeys-1}

* **`filter`:** Kriterien für übereinstimmende Cookie-Schlüssel. Die folgenden Typen werden unterstützt:
   * String: Der String wird mit dem Cookie-Schlüssel verglichen.
   * Array: Jedes Element im Array ist ein Filter.
   * Ein RegExp-Objekt: Die Testfunktion des Objekts wird verwendet, um Cookie-Schlüssel abzugleichen.
   * Eine Funktion: Eine Funktion, die einen Cookie-Schlüssel für eine Übereinstimmung testet. The function must take the cookie key as a parameter and return `true` if the test confirms a match.

##### Rückgabe {#returns-getkeys-1}

Ein Array von Zeichenfolgen, wobei jede Zeichenfolge der Schlüssel eines Cookies ist, das dem Filter entspricht.

##### Beispiel {#example-getkeys-1}

```javascript
ContextHub.Utils.Cookie.getKeys([/^cq-authoring/, /^cq-editor/])
```

#### removeItem(key, options) {#removeitem-key-options-1}

Entfernt ein Cookie. Um das Cookie zu entfernen, wird der Wert auf eine leere Zeichenfolge festgelegt und das Ablaufdatum wird auf den Tag vor dem aktuellen Datum gesetzt.

##### Parameter {#parameters-removeitem-1}

* **`key`:** Ein `String`-Wert, der den Schlüssel des zu entfernenden Cookies darstellt.
* **`options`:** Ein Objekt, das Eigenschaftswerte zum Konfigurieren der Cookie-Attribute enthält. Siehe [`setItem`](#setitem-key-value-options) Funktion für Informationen. Die `expires`-Eigenschaft hat keine Auswirkungen.

##### Rückgabe {#returns-removeitem-1}

Diese Funktion gibt keinen Wert zurück.

##### Beispiel {#example-removeitem-1}

```javascript
ContextHub.Utils.Cookie.vanish([/^cq-authoring/, 'cq-scrollpos']);
```

#### setItem(key, value, options) {#setitem-key-value-options-1}

Erstellt ein Cookie mit dem angegebenen Schlüssel und Wert und fügt das Cookie zum aktuellen Dokument hinzu. Optional können Sie Optionen angeben, die die Attribute des Cookies konfigurieren.

##### Parameter {#parameters-setitem-1}

* **`key`:** Ein String, der den Schlüssel des Cookies enthält.
* **`value`:** Ein String, der den Cookie-Wert enthält.
* **`options`:** (Optional) Ein Objekt, das eine der folgenden Eigenschaften enthält, die die Cookie-Attribute konfigurieren:
   * `expires`: Ein `date` oder `number` -Wert, der angibt, wann das Cookie abläuft. Ein Datumswert gibt die absolute Verfallszeit an. Eine Zahl (in Tagen) legt die Verfallszeit auf die aktuelle Zeit plus die Zahl fest. Der Standardwert ist `undefined`.
   * `secure`: Ein `boolean` Wert, der das `Secure` Attribut des Cookies angibt. Der Standardwert ist `false`.
   * `path`: Ein `String` Wert, der als `Path` Attribut des Cookies verwendet wird. Der Standardwert ist `undefined`.

##### Rückgabe {#returns-setitem-1}

Das Cookie mit dem eingestellten Wert.

##### Beispiel {#example-setitem-1}

```javascript
ContextHub.Utils.Cookie.setItem("name", "mycookie", {
    expires: 3,
    domain: 'localhost',
    path: '/some/directory',
    secure: true
});
```

#### vanish(filter, options) {#vanish-filter-options}

Entfernt alle Cookies, die einem gegebenen Filter entsprechen. Cookies are matched using the `getKeys` function and removed using the `removeItem` function.

##### Parameter {#parameters-vanish}

* **`filter`:** Das `filter` Argument, das im Aufruf der [`getKeys`](#getkeys-filter) Funktion verwendet wird.
* **`options`:** Das `options` Argument, das im Aufruf der [`removeItem`](#removeitem-key-options) Funktion verwendet wird.

##### Rückgabe {#returns-vanish}

Diese Funktion gibt keinen Wert zurück.

## ContextHub.Utils.Eventing {#contexthub-utils-eventing}

Ermöglicht es Ihnen, Funktionen an ContextHub-Storeereignisse zu binden und zu lösen. Access `ContextHub.Utils.Eventing` objects for a store using the [eventing](#eventing) property of the store.

### Funktionen (ContextHub.Utils.Eventing) {#functions-contexthub-utils-eventing}

#### off(name, selector) {#off-name-selector}

Befreit eine Funktion aus einem Ereignis.

##### Parameter {#parameters-off}

* **`name`:** Der [Name des Ereignisses](#contexthub-utils-eventing) , für das Sie die Bindung der Funktion aufheben.
* **`selector`:** Der Selektor, der die Bindung identifiziert. (Siehe den `selector` Parameter für die [`on`](#on-name-handler-selector-triggerforpastevents) und [`once`](#once-name-handler-selector-triggerforpastevents) Funktionen).

##### Rückgabe {#returns-off}

Diese Funktion gibt keinen Wert zurück.

#### on(name, handler, selector, triggerForPastEvents) {#on-name-handler-selector-triggerforpastevents}

Bindet eine Funktion an ein Ereignis. Die Funktion wird jedes Mal aufgerufen, wenn das Ereignis eintritt. Optional kann die Funktion für Ereignisse aufgerufen werden, die in der Vergangenheit stattgefunden haben, bevor die Bindung eingerichtet wird.

##### Parameter {#parameters-on}

* **`name`:** (String) Der [Name des Ereignisses](#contexthub-utils-eventing), an das Sie die Funktion binden.
* **`handler`:** (Funktion) Die Funktion zum Binden an das Ereignis.
* **`selector`:** (String) Eine eindeutige Kennung für die Bindung. Sie benötigen den Selektor, um die Bindung zu identifizieren, wenn Sie die `off`-Funktion verwenden möchten, um die Bindung zu entfernen.
* **`triggerForPastEvents`:** (Boolesch) Gibt an, ob der Handler für Ereignisse ausgeführt werden soll, die in der Vergangenheit aufgetreten sind. Ein Wert `true` ruft den Handler für vergangene Ereignisse auf. A value of `false` calls the handler for future events. Der Standardwert ist `true`.

##### Rückgabe {#returns-on}

When the `triggerForPastEvents` argument is `true`, this function returns a `boolean` value that indicates whether the event occurred in the past:

* `true`: Das Ereignis ist in der Vergangenheit aufgetreten und der Handler wird aufgerufen.
* `false`: Das Ereignis ist nicht in der Vergangenheit aufgetreten.

If `triggerForPastEvents` is `false`, this function returns no value.

##### Beispiel {#example-on}

Im folgenden Beispiel wird eine Funktion an das Ereignis data des Geolocation Stores gebunden. Die Funktion füllt ein Element auf der Seite mit dem Wert für das Breitendatenelement des Speichers.

```html
<div class="location">
    <p>latitude: <span id="lat"></span></p>
</div>

<script>
    var geostore = ContextHub.getStore("geolocation");
    geostore.eventing.on(ContextHub.Constants.EVENT_DATA_UPDATE,getlat,"getlat");

    function getlat(){
       latitude = geostore.getItem("latitude");
       $("#lat").html(latitude);
    }
</script>
```

#### once(name, handler, selector, triggerForPastEvents) {#once-name-handler-selector-triggerforpastevents}

Bindet eine Funktion an ein Ereignis. Die Funktion wird nur einmal beim ersten Auftreten des Ereignisses aufgerufen. Optional kann die Funktion für das Ereignis aufgerufen werden, das in der Vergangenheit stattgefunden hat, bevor die Bindung hergestellt wird.

##### Parameter {#parameters-once}

* **`name`:** (String) Der [Name des Ereignisses](#contexthub-utils-eventing), an das Sie die Funktion binden.
* **`handler`:** (Funktion) Die Funktion zum Binden an das Ereignis.
* **`selector`:** (String) Eine eindeutige Kennung für die Bindung. Sie benötigen den Selektor, um die Bindung zu identifizieren, wenn Sie die `off`-Funktion verwenden möchten, um die Bindung zu entfernen.
* **`triggerForPastEvents`:** (Boolesch) Gibt an, ob der Handler für Ereignisse ausgeführt werden soll, die in der Vergangenheit aufgetreten sind. Ein Wert `true` ruft den Handler für vergangene Ereignisse auf. A value of `false` calls the handler for future events. Der Standardwert ist `true`.

##### Rückgabe {#returns-once}

When the `triggerForPastEvents` argument is `true`, this function returns a `boolean` value that indicates whether the event occurred in the past:

* `true`: Das Ereignis ist in der Vergangenheit aufgetreten und der Handler wird aufgerufen.
* `false`: Das Ereignis ist nicht in der Vergangenheit aufgetreten.

If `triggerForPastEvents` is `false`, this function returns no value.

## ContextHub.Utils.inheritance {#contexthub-utils-inheritance}

Eine Dienstprogrammklasse, mit der ein Objekt die Eigenschaften und Methoden eines anderen Objekts übernehmen kann.

### Funktionen (ContextHub.Utils.inheritance) {#functions-contexthub-utils-inheritance}

#### inherit(child, parent) {#inherit-child-parent}

Bewirkt, dass ein Objekt die Eigenschaften und Methoden eines anderen Objekts übernimmt.

##### Parameter {#parameters-inherit}

* **`child`:** (Object) Das Objekt, das übernimmt.
* **`parent`:** (Object) Das Objekt, das die übernommenen Eigenschaften und Methoden definiert.

## ContextHub.Utils.JSON {#contexthub-utils-json}

Stellt Funktionen zum Serialisieren von Objekten im JSON-Format und zum Deserialisieren von JSON-Strings in Objekten bereit.

### Funktionen (ContextHub.Utils.JSON) {#functions-contexthub-utils-json}

#### parse(data) {#parse-data}

Analysiert einen String als JSON und konvertiert ihn in ein JavaScript-Objekt.

##### Parameter {#parameters-parse}

* **`data`:** Ein Stringwert im JSON-Format.

##### Rückgabe {#returns-parse}

Ein JavaScript-Objekt

##### Beispiel {#example-parse}

Der Code:

```javascript
ContextHub.Utils.JSON.parse("{'city':'Basel','country':'Switzerland','population':'173330'}");
```

Gibt das folgende Objekt zurück:

```javascript
Object {
   city: "Basel",
   country: "Switzerland",
   population: 173330
}
```

#### stringify(data) {#stringify-data}

Serialisiert JavaScript-Werte und -Objekte in Stringwerte des JSON-Formats.

##### Parameter {#parameters-stringify}

* **`data`:** Der Wert oder das zu serialisierende Objekt. Diese Funktion unterstützt boolesche Werte, Array-, Zahlen-, String- und Datumswerte.

##### Rückgabe {#returns-stringify}

Der serialisierte Stringwert. When `data` is a R `egExp` value, this function returns an empty object. When `data` is a function, returns `undefined`.

##### Beispiel {#example-stringify}

Der folgende Code:

```javascript
ContextHub.Utils.JSON.stringify({
   city: "Basel",
   country: "Switzerland",
   population: 173330
});
```

Rückgabe:

```javascript
"{'city':'Basel','country':'Switzerland','population':'173330'}":
```

## ContextHub.Utils.JSON.tree {#contexthub-utils-json-tree}

Diese Klasse erleichtert die Manipulation von Datenobjekten, die gespeichert oder aus ContextHub-Stores abgerufen werden.

### Funktionen (ContextHub.Utils.JSON.tree) {#functions-contexthub-utils-json-tree}

#### addAllItems() {#addallitems}

Erstellt eine Kopie eines Datenobjekts und fügt die Datenstruktur aus einem zweiten Objekt hinzu. Die Funktion gibt die Kopie zurück und ändert keines der ursprünglichen Objekte. Wenn die Datenbäume der beiden Objekte identische Schlüssel enthalten, überschreibt der Wert des zweiten Objekts den Wert des ersten Objekts.

##### Parameter {#parameters-addallitems-1}

* **`tree`:** Das kopierte Objekt.
* **`secondTree`:** Das Objekt, das mit der Kopie des `tree` Objekts zusammengeführt wird.

##### Rückgabe {#returns-addallitems-1}

Ein Objekt, das die zusammengeführten Daten enthält.

#### cleanup() {#cleanup}

Erstellt eine Kopie eines Objekts, sucht und entfernt Elemente in der Datenstruktur, die keine Werte, Nullwerte oder undefinierten Werte enthalten, und gibt die Kopie zurück.

##### Parameter {#parameters-cleanup}

* **`tree`:** Das zu bereinigende Objekt.

##### Rückgabe {#returns-cleanup}

Eine Kopie der Struktur, die bereinigt wird.

#### getItem() {#getitem}

Ruft den Wert eines Objekts für den a-Schlüssel ab.

##### Parameter {#parameters-getitem-2}

* **`tree`:** Das data-Objekt.
* **`key`:** Der Schlüssel für den Wert, den Sie abrufen möchten.

##### Rückgabe {#returns-getitem-2}

Der Wert, der dem Schlüssel entspricht. Wenn der Schlüssel untergeordnete Schlüssel hat, gibt diese Funktion ein komplexes Objekt zurück. When the type of the value for the key is `undefined`, `null` is returned.

##### Beispiel {#example-getitem-2}

Betrachten Sie das folgende JavaScript-Objekt:

```javascript
myObject {
  user: {
    location: {
      city: "Basel",
        details: {
          population: 173330,
          elevation: 260
        }
      }
    }
  }
```

Der folgende Beispiel-Code gibt den Wert `260` zurück.

```javascript
ContextHub.Utils.JSON.tree.getItem(myObject, "/user/location/details/elevation");
```

Der folgende Beispiel-Code ruft den Wert für den Schlüssel zurück, der untergeordnete Schlüssel hat:

```javascript
ContextHub.Utils.JSON.tree.getItem(myObject, "/user");
```

Die Funktion gibt das folgende Objekt zurück:

```javascript
Object {
  location: {
    city: "Basel",
    details: {
      population: 173330,
      elevation: 260
    }
  }
}
```

#### getKeys() {#getkeys}

Ruft alle Schlüssel aus der Datenstruktur eines Objekts ab. Optional können Sie nur die Schlüssel der untergeordneten Elemente eines bestimmten Schlüssels abrufen. Sie können optional auch eine Sortierreihenfolge der abgerufenen Schlüssel angeben.

##### Parameter {#parameters-getkeys-2}

* **`tree`:** Das Objekt, von dem die Schlüssel des Datenbaums abgerufen werden.
* **`parent`:** (Optional) Der Schlüssel eines Elements im Datenbaum, für das Sie die Schlüssel der untergeordneten Elemente abrufen möchten.
* **`order`:** (Optional) Eine Funktion, die die Sortierreihenfolge der zurückgegebenen Schlüssel bestimmt. (Siehe [`Array.prototype.sort`](https://developer.mozilla.org/de-DE/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) im Mozilla Developer Network.)

##### Rückgabe {#returns-getkeys-2}

Ein Array von Schlüsseln.

##### Beispiel {#example-getkeys-2}

Betrachten Sie das folgende Objekt:

```javascript
myObject {
  location: {
    weather: {
      temperature: "28C",
      humidity: "77%",
      precipitation: "10%",
      wind: "8km/h"
    },
    city: "Basel",
    country: "Switzerland",
    longitude: 7.5925727,
    latitude: 47.557421
  }
}
```

The `ContextHub.Utils.JSON.tree.getKeys(myObject);` script returns the following array:

```javascript
["/location", "/location/city", "/location/country", "/location/latitude", "/location/longitude", "/location/weather", "/location/weather/humidity", "/location/weather/precipitation", "/location/weather/temperature", "/location/weather/wind"]
```

#### removeItem() {#removeitem}

Erstellt eine Kopie eines bestimmten Objekts, entfernt den angegebenen Zweig aus der Datenstruktur und gibt die geänderte Kopie zurück.

##### Parameter {#parameters-removeitem-2}

* **`tree`:** Ein Datenobjekt.
* **`key`:** Der zu entfernende Schlüssel.

##### Rückgabe {#returns-removeitem-2}

Eine Kopie des ursprünglichen Datenobjekts mit entferntem Schlüssel.

##### Beispiel {#example-removeitem-2}

Betrachten Sie das folgende Objekt:

```javascript
myObject {
  one: {
    foo: "bar",
    two: {
      three: {
        four: {
          five: 5,
          six: 6
        }
      }
    }
  }
}
```

Das folgende Beispielskript entfernt den Zweig /one/two/three/four aus dem Datenbaum:

```javascript
myObject = ContextHub.Utils.JSON.tree.removeItem(myObject, "/one/two/three/four");
```

Die Funktion gibt das folgende Objekt zurück:

```javascript
myObject {
  one: {
    foo: "bar"
  }
}
```

#### sanitizeKey(key) {#sanitizekey-key}

Bereinigt Stringwerte, um sie als Schlüssel nutzbar zu machen. Um einen String zu bereinigen, führt diese Funktion die folgenden Aktionen aus:

* Reduziert mehrere aufeinander folgende Schrägstriche zu einem Schrägstrich.
* Entfernt Leerzeichen am Anfang und am Ende des Strings.
* Teilt das Ergebnis in ein Array von Strings auf, die durch Schrägstriche abgegrenzt sind.

Verwenden Sie das resultierende Array, um einen verwendbaren Schlüssel zu erstellen.

##### Parameter {#parameters-sanitizekey}

* **`key`:** Die `string` zu sanitisieren.

##### Rückgabe {#returns-sanitizekey}

An array of `string` values where each string is the portion of the `key` that was demarcated by slashes. stellt den bereinigten Schlüssel dar. Wenn das bereinigte Array eine Länge von hat, gibt diese Funktion `null`null zurück.

##### Beispiel {#example-sanitizekey}

The following code sanitizes a string to produce the array `["this", "is", "a", "path"]`, and then generates the key `"/this/is/a/path"` from the array:

```javascript
var key = " / this////is/a/path ";
ContextHub.Utils.JSON.tree.sanitizeKey(key)
"/" + ContextHub.Utils.JSON.tree.sanitizeKey(key).join("/");
```

#### setItem(tree, key, value) {#setitem-tree-key-value}

Fügt dem Datenbaum einer Kopie eines Objekts ein Schlüssel/Wert-Paar hinzu. For information about data trees, see [Persistence.](contexthub.md#persistence)

##### Parameter {#parameters-setitem-2}

* **`tree`:** Ein Datenobjekt.
* **`key`:** Der Schlüssel, der mit dem hinzugefügten Wert verknüpft werden soll. Der Schlüssel ist der Pfad zum Element im Datenbaum. Diese Funktion ruft `ContextHub.Utils.JSON.tree.sanitize` auf, um den Schlüssel vor dem Hinzufügen zu bereinigen.
* **`value`:** Der Wert, der dem Datenbaum hinzugefügt werden soll.

##### Rückgabe {#returns-setitem-2}

A copy of the `tree` object that includes the `key`/ `value` pair.

##### Beispiel {#example-setitem-2}

Betrachten Sie den folgenden JavaScript-Code:

```javascript
var myObject = {
     user: {
        location: {
           city: "Basel"
           }
        }
     };

var myKey = "/user/location/details";

var myValue = {
      population: 173330,
      elevation: 260
     };

myObject = ContextHub.Utils.JSON.tree.setItem(myObject, myKey, myValue);
```

## ContextHub.Utils.storeCandidates {#contexthub-utils-storecandidates}

Ermöglicht es Ihnen, Storekandidaten zu registrieren und registrierte Storekandidaten zu erhalten.

### Funktionen (ContextHub.Utils.storeCandidates) {#functions-contexthub-utils-storecandidates}

#### getRegisteredCandidates(storeType) {#getregisteredcandidates-storetype}

Gibt die Storetypen zurück, die als Storekandidaten registriert sind. Rufen Sie entweder die registrierten Bewerber eines bestimmten Store-Typs oder aller Store-Typen ab.

##### Parameter {#parameters-getregisteredcandidates}

* **`storeType`:** (String) Der Name des Storetyps. See the `storeType` parameter of the [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#contexthub-utils-storecandidates) function.

##### Rückgabe {#returns-getregisteredcandidates}

Ein Objekt von Storetypen. Die Objekteigenschaften sind die Namen des Storetyps, und die Eigenschaftswerte sind ein Array von registrierten Storekandidaten.

#### getStoreFromCandidates(storeType) {#getstorefromcandidates-storetype}

Gibt einen Storetyp aus den registrierten Kandidaten zurück. Wenn mehrere Speichertypen mit demselben Namen registriert sind, gibt die Funktion den Speichertyp mit der höchsten Priorität zurück.

##### Parameter {#parameters-getstorefromcandidates}

* `storeType`: (String) Der Name des Storekandidaten. See the `storeType` parameter of the [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#registerstorecandidate-store-storetype-priority-applies) function.

##### Rückgabe {#returns-getstorefromcandidates}

Ein Objekt, das den registrierten Storekandidaten darstellt. Wenn der angeforderte Storetyp nicht registriert ist, wird ein Fehler ausgelöst.

#### getSupportedStoreTypes() {#getsupportedstoretypes}

Gibt die Namen der Storetypen zurück, die als Storekandidaten registriert sind. Diese Funktion erfordert keine Parameter.

##### Rückgabe {#returns-getsupportedstoretypes}

Ein Array von Stringwerten, wobei jeder String der Storetyp ist, mit dem ein Storekandidat registriert wurde. See the `storeType` parameter of the [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#contexthub-utils-storecandidates) function.

#### registerStoreCandidate(store, storeType, priority, applies) {#registerstorecandidate-store-storetype-priority-applies}

Registriert ein Storeobjekt als einen Storekandidaten unter Verwendung eines Namens und einer Priorität.

Die Priorität ist eine Zahl, die die Bedeutung der gleichnamigen Store angibt. Wenn ein Storekandidat unter Verwendung des gleichen Namens wie ein bereits registrierter Storekandidat registriert wird, wird der Kandidat mit der höheren Priorität verwendet. Bei der Registrierung eines Storekandidaten wird der Store nur registriert, wenn die Priorität höher ist als bei den gleichnamigen registrierten Storekandidaten.

##### Parameter {#parameters-registerstorecandidate}

* **`store`:** (Objekt) Das Storeobjekt, das als Storekandidat registriert werden soll.
* **`storeType`:** (String) Der Name des Storekandidaten. Dieser Wert wird beim Erstellen einer Instanz des Storekandidaten benötigt.
* **`priority`:** (Number) Die Priorität des Store-Kandidaten.
* **`applies`:** (Funktion) Die aufzurufende Funktion, die die Anwendbarkeit des Speichers in der aktuellen Umgebung auswertet. Die Funktion muss `true` zurückgeben, wenn der Store anwendbar ist, andernfalls `false`. The default value is a function that returns true: `function() {return true;}`

##### Beispiel {#example-registerstorecandidate}

```javascript
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandiate', 0);
```
