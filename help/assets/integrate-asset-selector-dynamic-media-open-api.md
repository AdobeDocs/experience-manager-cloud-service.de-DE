---
title: Integrieren des Asset-Wählers mit Dynamic Media-OpenAPIs
description: Integrieren Sie den Asset-Wähler in verschiedene Adobe-, Adobe-fremde- und Drittanbieter-Anwendungen.
role: Admin, User
exl-id: b01097f3-982f-4b2d-85e5-92efabe7094d
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: ht
source-wordcount: '936'
ht-degree: 100%

---

# Integrieren in Dynamic Media mit OpenAPI-Funktionen {#integrate-asset-selector-dynamic-media-open-apis}

Mit dem Asset-Wähler können Sie die Integration mit verschiedenen Adobe-Anwendungen durchführen, um eine nahtlose Zusammenarbeit zu ermöglichen.

## Voraussetzungen {#prereqs-polaris}

Wenden Sie die folgenden Voraussetzungen an, wenn Sie den Asset-Wähler in Dynamic Media mit OpenAPI-Funktionen integrieren:

* [Kommunikationsmethoden](/help/assets/overview-asset-selector.md#prereqs)
* Für den Zugriff auf Dynamic Media mit OpenAPI-Funktionen benötigen Sie folgende Lizenzen:
   * Assets-Repository (z. B. Experience Manager Assets as a Cloud Service)
   * AEM und Dynamic Media.
* Nur [genehmigte Assets](/help/assets/approve-assets.md) zur Verwendung verfügbar, um die Markenkonsistenz sicherzustellen.

## Integrieren in Dynamic Media mit OpenAPI-Funktionen {#adobe-app-integration-polaris}

Die Integration des Asset-Wählers mit dem OpenAPI-Prozess von Dynamic Media umfasst verschiedene Schritte, darunter die Erstellung einer benutzerdefinierten oder auswahlbereiten Dynamic Media-URL.

### Integrieren des Asset-Wählers in Dynamic Media mit OpenAPI-Funktionen {#integrate-dynamic-media}

Die Eigenschaften `rootPath` und `path` sollten nicht Teil von Dynamic Media mit OpenAPI-Funktionen sein. Stattdessen können Sie die Eigenschaft `aemTierType` konfigurieren. Die Syntax der Konfiguration ist wie folgt:

```
aemTierType:[1: "delivery"]
```

Mit dieser Konfiguration können Sie alle genehmigten Assets ohne Ordner oder als flache Struktur anzeigen. Weitere Informationen finden Sie im Abschnitt [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md) unter der Eigenschaft `aemTierType`.


### Erstellen einer dynamischen Bereitstellungs-URL aus genehmigten Assets {#create-dynamic-media-url}

Nachdem Sie den Asset-Wähler eingerichtet haben, wird ein Objektschema verwendet, um eine dynamische Bereitstellungs-URL anhand der genehmigten Assets zu erstellen.
Hier ist ein Beispiel für ein Schema eines Objekts aus einem Array von Objekten, das bei Auswahl eines Assets empfangen wird:

```
{
"dc:format": "image/jpeg",
"repo:assetId": "urn:aaid:aem:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
"repo:name": "image-7.jpg",
"repo:repositoryId": "delivery-pxxxx-exxxxxx.adobe.com",
...
}
```

Der Carrier für alle ausgewählten Assets ist die `handleSelection`-Funktion, die als JSON-Objekt fungiert. Beispiel: `JsonObj`. Die dynamische Versand-URL wird durch die Kombination der folgenden Carrier erstellt:

| Objekt | JSON |
|---|---|
| Host | `assetJsonObj["repo:repositoryId"]` |
| API-Stamm | `/adobe/assets` |
| asset-id | `assetJsonObj["repo:assetId"]` |
| seo-name | `assetJsonObj["repo:name"].split(".").slice(0,-1).join(".")` |
| format | `.jpg` |

#### API-Spezifikation für die Bereitstellung genehmigter Assets {#approved-assets-delivery-api-specification}

URL-Format:
`https://<delivery-api-host>/adobe/assets/<asset-id>/as/<seo-name>.<format>?<image-modification-query-parameters>`

Dabei gilt Folgendes:

* Der Host ist `https://delivery-pxxxxx-exxxxxx.adobe.com`
* Der API-Stamm lautet `"/adobe/assets"`
* `<asset-id>` ist die Asset-Kennung
* `as` ist der konstante Teil der OpenAPI-Spezifikation, der angibt, wie das Asset bezeichnet werden soll
* `<seo-name>` ist der Name eines Assets
* `<format>` ist das Ausgabeformat
* `<image modification query parameters>`, wie von der API-Spezifikation für die Bereitstellung genehmigter Assets unterstützt.

#### API für die Bereitstellung genehmigter Assets für die Original-Ausgabedarstellung {#approved-assets-delivery-api}

Die dynamische Versand-URL weist die folgende Syntax auf:
`https://<delivery-api-host>/adobe/assets/<asset-id>/original/as/<seo-name>`, wobei Folgendes gilt:

* Der Host ist `https://delivery-pxxxxx-exxxxxx.adobe.com`
* Der API-Stamm für die Bereitstellung der Original-Ausgabedarstellung lautet `"/adobe/assets"`
* `<asset-id>` ist die Asset-Kennung
* `/original/as` ist der konstante Teil der OpenAPI-Spezifikation, der angibt, wie die Original-Ausgabedarstellung bezeichnet werden soll
* `<seo-name>`ist der Name des Assets, das eine Erweiterung aufweisen kann

### Auswahlbereite dynamische Bereitstellungs-URL {#ready-to-pick-dynamic-delivery-url}

Der Carrier für alle ausgewählten Assets ist die `handleSelection`-Funktion, die als JSON-Objekt fungiert. Beispiel: `JsonObj`. Die dynamische Versand-URL wird durch die Kombination der folgenden Carrier erstellt:

| Objekt | JSON |
|---|---|
| Host | `assetJsonObj["repo:repositoryId"]` |
| API-Stamm | `/adobe/assets` |
| asset-id | `assetJsonObj["repo:assetId"]` |
| seo-name | `assetJsonObj["repo:name"]` |

Im Folgenden werden die beiden Möglichkeiten zum Durchlaufen des JSON-Objekts beschrieben:

![Dynamische Versand-URL](assets/dynamic-delivery-url.png)

* **Miniaturansicht:** Bei Miniaturansichten kann es sich um Bilder und Assets wie PDF, Videos usw. handeln. Sie können jedoch die Höhe- und Breitenattribute der Miniaturansicht eines Assets als Ausgabedarstellung für die dynamische Bereitstellung verwenden.
Der folgende Satz von Ausgabedarstellungen kann für Assets vom Typ PDF verwendet werden:
Sobald eine PDF-Datei im Sidekick ausgewählt ist, bietet der Auswahlkontext die folgenden Informationen. Nachstehend wird beschrieben, wie Sie das JSON-Objekt durchlaufen:

  <!--![Thumbnail dynamic delivery url](image-1.png)-->

  Im Screenshot oben finden Sie unter `selection[0].....selection[4]` den Link für das Array der Ausgabedarstellung. Die Haupteigenschaften einer der Miniaturausgabedarstellungen umfassen beispielsweise Folgendes:

  ```
  { 
      "height": 319, 
      "width": 319, 
      "href": "https://delivery-pxxxxx-exxxxx.adobeaemcloud.com/adobe/assets/urn:aaid:aem:8560f3a1-d9cf-429d-a8b8-d81084a42d41/as/algorithm design.jpg?width=319&height=319", 
      "type": "image/webp" 
  } 
  ```

Im obigen Screenshot muss die Versand-URL der Original-Ausgabedarstellung der PDF-Datei in das Zielerlebnis integriert werden, wenn eine PDF-Datei erforderlich ist und nicht ihre Miniaturansicht. Zum Beispiel: `https://delivery-pxxxxx-exxxxx.adobeaemcloud.com/adobe/assets/urn:aaid:aem:8560f3a1-d9cf-429d-a8b8-d81084a42d41/original/as/algorithm design.pdf`

* **Video:** Sie können die Video-Player-URL für die Assets vom Typ „Video“ verwenden, die einen eingebetteten iFrame verwenden. Sie können die folgenden Array-Ausgabedarstellungen im Zielerlebnis verwenden:
  <!--![Video dynamic delivery url](image.png)-->

  ```
  { 
      "height": 319, 
      "width": 319, 
      "href": "https://delivery-pxxxxx-exxxxx.adobeaemcloud.com/adobe/assets/urn:aaid:aem:2fdef732-a452-45a8-b58b-09df1a5173cd/as/DragDrop.2.jpg?width=319&height=319", 
      "type": "image/webp" 
  } 
  ```

  Im Screenshot oben finden Sie unter `selection[0].....selection[4]` den Link für das Array der Ausgabedarstellung. Die Haupteigenschaften einer der Miniaturausgabedarstellungen umfassen beispielsweise Folgendes:

  Das Code-Fragment im obigen Screenshot ist ein Beispiel für ein Video-Asset. Es enthält das Array der Ausgabedarstellungs-Links. `selection[5]` im Auszug ist das Beispiel für die Miniaturansicht eines Bildes, die als Platzhalter für die Miniaturansicht eines Videos im Zielerlebnis verwendet werden kann. `selection[5]` im Array der Ausgabedarstellungen ist für den Video-Player vorgesehen. Dies dient als HTML und kann als `src` des iFrames festgelegt werden. Es unterstützt das Streaming mit adaptiver Bitrate (die Web-optimierte Bereitstellung des Videos).

  Im obigen Beispiel lautet die URL des Video-Players wie folgt: `https://delivery-pxxxxx-exxxxx.adobeaemcloud.com/adobe/assets/urn:aaid:aem:2fdef732-a452-45a8-b58b-09df1a5173cd/play`

### Konfigurieren benutzerdefinierter Filter {#configure-custom-filters-dynamic-media-open-api}

Mit dem Asset-Wähler für Dynamic Media mit OpenAPI-Funktionen können Sie benutzerdefinierte Eigenschaften und die darauf basierenden Filter konfigurieren. Die Eigenschaft `filterSchema` wird zum Konfigurieren solcher Eigenschaften verwendet. Die Anpassung kann als `metadata.<metadata bucket>.<property name>.` verfügbar gemacht werden, womit die Filter konfiguriert werden können. Dabei gilt Folgendes:

* Bei `metadata` handelt es sich um die Informationen eines Assets
* Bei `embedded` handelt es sich um den statischen Parameter, der für die Konfiguration verwendet wird
* Bei `<propertyname>` handelt es sich um den Filternamen, den Sie konfigurieren

Für die Konfiguration werden die auf Ebene `jcr:content/metadata/` definierten Eigenschaften für die zu konfigurierenden Filter als `metadata.<metadata bucket>.<property name>.` verfügbar gemacht.

Beispielsweise wird im Asset-Wähler für Dynamic Media mit OpenAPI-Funktionen eine Eigenschaft unter `asset jcr:content/metadata/client_name:market` für die Filterkonfiguration in `metadata.embedded.client_name:market` umgewandelt.

Um den Namen abzurufen, muss eine einmalige Aktivität durchgeführt werden. Führen Sie einen Such-API-Aufruf für das Asset aus und rufen Sie den Eigenschaftsnamen (also den Bucket) ab.

### Benutzeroberfläche des Asset-Wählers für Dynamic Media mit OpenAPI-Funktionen {#interface-dynamic-media-open-api}

Nach der Integration mit dem Micro-Frontend-Asset-Wähler von Adobe können Sie die reine Asset-Struktur aller genehmigten Assets sehen, die im Experience Manager-Asset-Repository verfügbar sind.

![Benutzeroberfläche von Dynamic Media mit OpenAPI-Funktionen](assets/polaris-ui.png)

* **A**: Bedienfeld aus-/einblenden
* **B**: Assets
* **C**: Sortierung
* **D**: Filter
* **E**: Suchleiste
* **F**: Sortierung in auf- oder absteigender Reihenfolge
* **G**: Auswahl abbrechen
* **H**: Einzelne oder mehrere Assets auswählen

>[!NOTE]
>
>Ordner werden nur beim Herstellen einer Verbindung zum Autoren-Repository unterstützt, nicht aber zu Dynamic Media mit dem OpenAPI-Repository.

>[!MORELIKETHIS]
>
>* [Integrieren des Asset-Wählers in verschiedene Anwendungen](/help/assets/integrate-asset-selector.md)
>* [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md)
>* [Anpassungen des Asset-Wählers](/help/assets/asset-selector-customization.md)
