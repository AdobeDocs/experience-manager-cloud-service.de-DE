---
title: Konfigurieren von ContextHub
description: Es wird beschrieben, wie Sie ContextHub konfigurieren.
translation-type: tm+mt
source-git-commit: 2a589ff554a5cced3d7ad45d981697debb73992f
workflow-type: tm+mt
source-wordcount: '1670'
ht-degree: 68%

---


# Konfigurieren von ContextHub {#configuring-contexthub}

ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten. For more detail on ContextHub, please see the [ContextHub developer overview](contexthub.md).

Sie können die ContextHub-Symbolleiste konfigurieren, um zu steuern, ob sie im Vorschau-Modus angezeigt wird, ContextHub-Stores zu erstellen und UI-Module hinzuzufügen.

## Ein- und Ausblenden der ContextHub-Benutzeroberfläche {#showing-and-hiding-the-contexthub-ui}

Konfigurieren Sie den Adobe Granite ContextHub-OSGi-Dienst, um die [ContextHub-Benutzeroberfläche](/help/sites-cloud/authoring/personalization/targeted-content.md) auf Ihren Seiten ein- oder auszublenden. The PID of this service is `com.adobe.granite.contexthub.impl.ContextHubImpl.`

To configure the service you can either use the [Web Console](/help/implementing/deploying/configuring-osgi.md) or use a JCR node in the repository:

* **Web-Konsole:** Aktivieren Sie die Eigenschaft „Show UI“, um die Benutzeroberfläche anzuzeigen. Verwenden Sie die Eigenschaft „Hide UI“, um die Benutzeroberfläche auszublenden.
* **JCR-Knoten:** Um die Benutzeroberfläche anzuzeigen, setzen Sie die boolesche `com.adobe.granite.contexthub.show_ui` Eigenschaft auf `true`. To hide the UI, set the property to `false`.

Wenn die ContextHub-Benutzeroberfläche angezeigt wird, erscheint sie nur auf den Seiten von AEM-Autoreninstanzen. Auf Seiten von Veröffentlichungsinstanzen wird die Benutzeroberfläche nicht angezeigt.

## Hinzufügen von ContextHub-UI-Modi und -Modulen {#adding-contexthub-ui-modes-and-modules}

Konfigurieren Sie die UI-Modi und -Module, die auf der ContextHub-Symbolleiste im Vorschaumodus angezeigt werden:

* UI-Modi: Gruppen mit verwandten Modulen
* Module: Widgets, die Kontextdaten eines Stores verfügbar machen und Autoren die Änderung des Kontexts ermöglichen

UI-Modi werden als Symbole auf der linken Seite der Symbolleiste angezeigt. Wenn die Option ausgewählt ist, erscheinen die Module eines UI-Modus auf der rechten Seite.

![ContextHub-Symbolleiste](assets/contexthub-toolbar.png)

Bei Symbolen handelt es sich um Verweise aus der [Coral-Bibliothek mit Benutzeroberflächensymbolen](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableIcons).

### Hinzufügen eines UI-Modus {#adding-a-ui-mode}

Fügen Sie einer Gruppe mit verwandten ContextHub-Modulen einen UI-Modus hinzu. Beim Erstellen des UI-Modus geben Sie den Titel und das Symbol an, der bzw. das in der ContextHub-Symbolleiste angezeigt werden soll.

1. Klicken oder tippen Sie auf der Experience Manager-Leiste auf „Tools“ > „Sites“ > „ContextHub“.
1. Klicken oder tippen Sie auf den standardmäßigen Konfigurations-Container.
1. Klicken oder tippen Sie auf die ContextHub-Konfiguration.
1. Klicken oder tippen Sie auf die Schaltfläche „Erstellen“ und dann auf „ContextHub-UI-Modus“.

   ![hinzufügen](assets/contexthub-ui-mode.png)

1. Geben Sie Werte für die folgenden Eigenschaften an:

   * UI-Modus Titel: Der Titel, der den UI-Modus identifiziert
   * Mode Icon: The selector for the [Coral UI icon](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableIcons) to use, for example `coral-Icon--user`
   * Aktiviert: Wählen Sie diese Option aus, um den UI-Modus in der ContextHub-Symbolleiste anzuzeigen.

1. Klicken oder tippen Sie auf „Speichern“.

### Hinzufügen eines UI-Moduls {#adding-a-ui-module}

Fügen Sie ein ContextHub-UI-Modul einem UI-Modus hinzu, damit es in der ContextHub-Symbolleiste zum Einblenden einer Vorschau für Seiteninhalte angezeigt wird. Beim Hinzufügen eines UI-Moduls erstellen Sie eine Instanz eines Modultyps, der für ContextHub registriert ist. Sie müssen den Namen des zugeordneten Modultyps kennen, um ein UI-Modul hinzufügen zu können.

AEM stellt einen grundlegenden UI-Modultyp und mehrere Beispiele für UI-Modultypen bereit, die Sie als Basis für ein UI-Modul verwenden können. Die folgende Tabelle enthält eine kurze Beschreibung der einzelnen Modultypen. Weitere Informationen zum Entwickeln eines benutzerdefinierten UI-Moduls finden Sie unter [Erstellen von ContextHub-UI-Modulen](extending-contexthub.md#creating-contexthub-ui-module-types).

Die Eigenschaften von UI-Modulen enthalten eine Detailkonfiguration, in der Sie Werte für modulspezifische Eigenschaften angeben können. Sie stellen die Detailkonfiguration im JSON-Format bereit. Die Spalte „Modultyp“ in der Tabelle enthält Links zu Informationen zum JSON-Code, der für die einzelnen UI-Modultypen erforderlich ist.

| Modultyp | Beschreibung | Speichern |
|---|---|---|
| [contexthub.base](sample-modules.md#contexthub-base-ui-module-type) | Ein generischer UI-Modultyp | In den Eigenschaften des UI-Moduls konfiguriert |
| [contexthub.browserinfo](sample-modules.md#contexthub-browserinfo-ui-module-type) | Zeigt Informationen zum Browser an | `surferinfo` |
| [contexthub.datetime](sample-modules.md#contexthub-datetime-ui-module-type) | Zeigt Informationen zu Datum und Uhrzeit an | `datetime` |
| [contexthub.device](sample-modules.md#contexthub-device-ui-module-type) | Client-Gerät anzeigen | `emulators` |
| [contexthub.location](sample-modules.md#contexthub-location-ui-module-type) | Zeigt den Breiten- und Längengrad des Clients sowie die Position auf einer Karte an. Sie können den Standort ändern. | `geolocation` |
| [contexthub.screen-orientation](sample-modules.md#contexthub-screen-orientation-ui-module-type) | Zeigt die Bildschirmausrichtung des Geräts (Querformat oder Hochformat) an | `emulators` |
| [contexthub.tagcloud](sample-modules.md#contexthub-tagcloud-ui-module-type) | Zeigt Statistiken zu Seiten-Tags an | `tagcloud` |
| [granite.Profil](sample-modules.md#granite-profile-ui-module-type) | Zeigt Informationen zum Profil des aktuellen Benutzers an, einschließlich `authorizableID`, `displayName` und `familyName`. You can change the value of `displayName` and `familyName`. | `profile` |

1. Klicken oder tippen Sie auf der Experience Manager-Leiste auf „Tools“ > „Sites“ > „ContextHub“.
1. Klicken oder tippen Sie auf den Konfigurations-Container, dem Sie ein UI-Modul hinzufügen möchten.
1. Klicken oder tippen Sie auf die ContextHub-Konfiguration, der Sie das UI-Modul hinzufügen möchten.
1. Klicken oder tippen Sie auf den UI-Modus, dem Sie das UI-Modul hinzufügen.
1. Klicken oder tippen Sie auf die Schaltfläche „Erstellen“ und dann auf „ContextHub-UI-Modul (generisch)“.

   ![ContextHub-UI-Modul](assets/contexthub-ui-module.png)

1. Geben Sie Werte für die folgenden Eigenschaften an:

   * UI-Modultitel: Ein Titel, mit dem das UI-Modul identifiziert wird.
   * Modultyp: Gibt den Modultyp an.
   * Aktiviert: Wählen Sie diese Option aus, um das UI-Modul in der ContextHub-Symbolleiste anzuzeigen.

1. (Optional) Geben Sie ein JSON-Objekt ein, um das UI-Modul zu konfigurieren und so die Standardkonfiguration für den Store außer Kraft zu setzen. 
1. Klicken oder tippen Sie auf „Speichern“.

## Erstellen eines ContextHub-Store {#creating-a-contexthub-store}

Erstellen Sie einen ContextHub-Store, in dem Benutzerdaten dauerhaft gespeichert werden können und bei Bedarf zugänglich sind. ContextHub-Stores basieren auf registrierten Store-Kandidaten. Beim Erstellen des Stores benötigen Sie den Wert von storeType, unter dem der Store-Kandidat registriert wurde. (Siehe [Erstellen von benutzerdefinierten Store-Kandidaten](extending-contexthub.md#creating-custom-store-candidates).)

### Store-Detailkonfiguration {#detailed-store-configuration}

Beim Konfigurieren eines Stores können Sie über die Eigenschaft „Detailkonfiguration“ Werte für Store-spezifische Eigenschaften angeben. Der Wert basiert auf dem Parameter `config` der Store-Funktion `init`. Es hängt daher vom Store ab, ob dieser Wert angegeben werden muss und welches Format der Wert haben muss.

Der Wert der Eigenschaft „Detailkonfiguration“ ist ein `config`-Objekt im JSON-Format.

### Beispiele für Store-Kandidaten {#sample-store-candidates}

In AEM werden die folgenden Beispiele für Store-Kandidaten bereitgestellt, die Sie als Basis für einen Store verwenden können.

| Filialtyp | Beschreibung |
|---|---|
| [aem.segmentation](sample-stores.md#aem-segmentation-sample-store-candidate) | Store für gelöste und ungelöste ContextHub-Segmente. Ruft automatisch Segmente aus dem ContextHub SegmentManager zurück |
| [aem.resolvedsegmente](sample-stores.md#aem-resolvedsegments-sample-store-candidate) | Speichert die aktuell gelösten Segmente. Hört auf den ContextHub SegmentManager-Dienst automatisch, um den Store automatisch zu aktualisieren |
| [contexthub.geolocation](sample-stores.md#contexthub-geolocation-sample-store-candidate) | Speichert den Breiten- und Längengrad des Browser-Speicherorts. |
| [contexthub.datetime](sample-stores.md#contexthub-datetime-sample-store-candidate) | Speichert das aktuelle Datum, die aktuelle Uhrzeit und die aktuelle Saison für den Browser-Standort |
| [granite.emulators](sample-stores.md#granite-emulators-sample-store-candidate) | Definiert Eigenschaften und Funktionen für eine Reihe von Geräten und erkennt das aktuelle Client-Gerät |
| [contexthub.generic-jsonp](sample-stores.md#contexthub-generic-jsonp-sample-store-candidate) | Ruft Daten von einem JSONP-Dienst ab und speichert sie |
| [granite.Profil](sample-stores.md#granite-profile-sample-store-candidate) | Speichert Profil-Daten für den aktuellen Benutzer |
| [contexthub.surferinfo](sample-stores.md#contexthub-surferinfo-sample-store-candidate) | Speichert Informationen zum Client, z. B. Geräteinformationen, Browsertyp und Fensterausrichtung |
| [contexthub.tagcloud](sample-stores.md#contexthub-tagcloud-sample-data-store) | Speichert Seiten-Tags und Tag-Zählungen |

1. Klicken oder tippen Sie auf der Experience Manager-Leiste auf „Tools“ > „Sites“ > „ContextHub“.
1. Klicken oder tippen Sie auf den standardmäßigen Konfigurations-Container.
1. Klicken oder tippen Sie auf „ContextHub-Konfiguration“.
1. Um einen Store hinzuzufügen, klicken oder tippen Sie auf das Symbol Erstellen und klicken Sie dann auf ContextHub Store-Konfiguration oder tippen Sie darauf.

   ![ContextHub Store-Konfiguration](assets/contexthub-store-configuration.png)

1. Geben Sie Werte für die grundlegenden Konfigurationseigenschaften an und klicken oder tippen Sie dann auf „Weiter“:

   * **Konfigurationstitel:** Der Titel, mit dem der Store identifiziert wird.
   * **Filialtyp:** Der Wert der Eigenschaft storeType des Store-Kandidaten, auf dem der Store basiert.
   * **Erforderlich:** Wählen Sie diese Option aus.
   * **Aktiviert:** Wählen Sie diese Option aus, um den Store zu aktivieren.

1. (Optional) Geben Sie im Feld „Detailkonfiguration (JSON)“ ein JSON-Objekt ein, um die Standardkonfiguration für den Store außer Kraft zu setzen.
1. Klicken oder tippen Sie auf „Speichern“.

## Beispiel: Verwenden eines JSONP-Diensts  {#example-using-a-jsonp-service}

In diesem Beispiel wird veranschaulicht, wie Sie einen Store konfigurieren und die Daten in einem UI-Modul anzeigen. In diesem Beispiel wird der MD5-Dienst der Website „jsontest.com“ als Datenquelle für einen Store verwendet. Der Dienst gibt den MD5-Hashcode einer bestimmten Zeichenfolge im JSON-Format zurück.

A contexthub.generic-jsonp store is configured so that it stores data for the service call `https://md5.jsontest.com/?text=%22text%20to%20md5%22`. Der Dienst gibt die folgenden Daten zurück, die in einem UI-Modul angezeigt werden:

```xml
{
   "md5": "919a56ab62b6d5e1219fe1d95248a2c5",
   "original": "\"text to md5\""
}
```

### Erstellen des Stores „contexthub.generic-jsonp“ {#creating-a-contexthub-generic-jsonp-store}

Mit dem Beispielspeicherkandidaten &quot;contexthub.generic-jsonp&quot;können Sie Daten von einem JSONP-Dienst oder einem Webdienst abrufen, der JSON-Daten zurückgibt. Verwenden Sie für diesen Store-Kandidaten die Store-Konfiguration, um Details zu dem JSONP-Dienst anzugeben, der genutzt werden soll.

The [init](contexthub-api.md#init-name-config) function of the `ContextHub.Store.JSONPStore` Javascript class defines a `config` object that initializes this store candidate. Das `config`-Objekt enthält ein `service`-Objekt mit Details zum JSONP-Dienst. Zum Konfigurieren des Stores geben Sie das `service`-Objekt im JSON-Format als Wert für die Eigenschaft „Detailkonfiguration“ an.

Verwenden Sie zum Speichern von Daten aus dem MD5-Dienst der Website „jsontest.com“ das Verfahren unter [Erstellen eines ContextHub-Store](#creating-a-contexthub-store) mit den folgenden Eigenschaften:

* **Konfigurationstitel:** md5
* **Store-Typ:** contexthub.generic-jsonp
* **Erforderlich:** Wählen Sie diese Option aus.
* **Aktiviert:** Auswählen
* **Detailkonfiguration (JSON):**

   ```xml
   {
    "service": {
    "jsonp": false,
    "timeout": 1000,
    "ttl": 1800000,
    "secure": false,
    "host": "md5.jsontest.com",
    "port": 80,
    "params":{
    "text":"text to md5"
        }
      }
    }
   ```

### Hinzufügen eines UI-Moduls für die md5-Daten {#adding-a-ui-module-for-the-md-data}

Fügen Sie der ContextHub-Symbolleiste ein UI-Modul hinzu, um die Daten anzuzeigen, die im md5-Beispiel-Store gespeichert sind. In diesem Beispiel wird das Modul &quot;contexthub.base&quot;verwendet, um das folgende UI-Modul zu erstellen:

![ContextHub MD5 Store](assets/contexthub-md5-store.png)

Use the procedure in [Adding a UI Module](#adding-a-ui-module) to add the UI module to an existing UI Mode, such as the sample Persona UI Mode. Verwenden Sie für das UI-Modul die folgenden Eigenschaftswerte:

* **UI-Modultitel:** MD5
* **Modultyp:** contexthub.base
* **Detailkonfiguration (JSON):**

   ```xml
   {
    "icon": "coral-Icon--data",
    "title": "MD5 Conversion",
    "storeMapping": { "md5": "md5" },
    "template": "<p> {{md5.original}}</p>;
                 <p>{{md5.md5}}</p>"
   }
   ```

## Debuggen von ContextHub {#debugging-contexthub}

Ein Debugmodus für ContextHub kann aktiviert werden, um die Fehlerbehebung zuzulassen. Der Debugmodus kann entweder über die ContextHub-Konfiguration oder per CRXDE aktiviert werden.

### Per Konfiguration {#via-the-configuration}

Edit the ContextHub&#39;s configuration and check the option **Debug**

1. Klicken oder tippen Sie in der Leiste auf **Tools > Sites > ContextHub**.
1. Klicken oder tippen Sie auf den standardmäßigen **Konfigurations-Container**.
1. Wählen Sie die **ContextHub-Konfiguration** aus und klicken oder tippen Sie auf **Ausgewähltes Element bearbeiten**.
1. Click or tap **Debug** and click or tap **Save**

### Per CRXDE {#via-crxde}

Use CRXDE Lite to set the property `debug` to **true** under:

* `/conf/global/settings/cloudsettings` oder
* `/conf/<site>/settings/cloudsettings`

### Unbeaufsichtigter Modus {#silent-mode}

Im unbeaufsichtigten Modus werden alle Debuginformationen unterdrückt. Im Gegensatz zur normalen Debug-Option, die für jede ContextHub-Konfiguration unabhängig festgelegt werden kann, ist der Silent-Modus eine globale Einstellung, die Vorrang vor allen Debug-Einstellungen auf ContextHub-Konfigurationsebene hat.

Dies ist nützlich für Ihre Veröffentlichungsinstanz, in der Sie keine Debugging-Informationen wünschen. Da es sich um eine globale Einstellung handelt, wird sie per OSGi aktiviert.

1. Open the **Adobe Experience Manager Web Console Configuration** at `http://<host>:<port>/system/console/configMgr`
1. Search for **Adobe Granite ContextHub**
1. Click the configuration **Adobe Granite ContextHub** to edit its properties
1. Aktivieren Sie die Option für den **unbeaufsichtigten Modus** (Silent Mode) und klicken Sie auf **Speichern**.

## Deaktivieren von ContextHub {#disabling-contexthub}

ContextHub kann deaktiviert werden, um das Laden von JS/CSS-Code und die Initialisierung zu verhindern. Sie haben zwei Optionen, um ContextHub zu deaktivieren:

* Bearbeiten Sie die Konfiguration von ContextHub und aktivieren Sie die Option **ContextHub deaktivieren**.

   1. Klicken oder tippen Sie in der Leiste auf **Tools > Sites > ContextHub**.
   1. Klicken oder tippen Sie auf den standardmäßigen **Konfigurations-Container**.
   1. Wählen Sie die **ContextHub-Konfiguration** aus und klicken oder tippen Sie auf **Ausgewähltes Element bearbeiten**.
   1. Klicken oder tippen Sie auf **ContextHub deaktivieren** und dann auf **Speichern**.

 oder

* Use CRXDE Lite to set the property `disabled` to **true** under `/conf/global/settings/cloudsettings/<configName>/contexthub`
