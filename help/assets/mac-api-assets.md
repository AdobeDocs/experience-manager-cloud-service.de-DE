---
title: Assets-HTTP-API
description: Erfahren Sie mehr über die Implementierung, Datenmodelle und Funktionen der Assets-HTTP-API. Verwenden Sie die Assets-HTTP-API, um verschiedene Aufgaben rund um Assets auszuführen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 7fe5761e14288349bbdce9d2c4e9e89e8d0a9e48

---


# Assets-HTTP-API {#assets-http-api}

## Übersicht {#overview}

Die Assets-HTTP-API ermöglicht CRUD-Vorgänge (Create-Read-Update-Delete, Erstellen/Lesen/Aktualisieren/Löschen) für Assets, einschließlich Binärdateien, Metadaten, Ausgabeformate und Kommentaren sowie strukturierten Inhalten mit AEM-Inhaltsfragmenten. Sie wird unter `/api/assets` bereitgestellt und als REST-API implementiert. Dazu gehört die [Unterstützung von Inhaltsfragmenten](assets-api-content-fragments.md).

So greifen Sie auf die API zu:

1. Öffnen Sie das Dokument zum API-Dienst unter `https://[hostname]:[port]/api.json`.
1. Folgen Sie dem Link zum Assets-Dienst, der zu `https://[hostname]:[server]/api/assets.json` führt.

Die API-Antwort ist eine JSON-Datei für einige MIME-Typen und ein Antwortcode für alle MIME-Typen. Die JSON-Antwort ist optional und kann zum Beispiel nicht für PDF-Dateien verfügbar sein. Verwenden Sie den Antwortcode für weitere Analysen oder Aktionen.

Nach der [!UICONTROL Ausschaltzeit] sind ein Asset und seine Ausgabeformate weder über die Assets-Web-Oberfläche noch über die HTTP-API verfügbar. Die API gibt die Fehlermeldung 404 zurück, wenn die [!UICONTROL Einschaltzeit] in der Zukunft oder die [!UICONTROL Ausschaltzeit] in der Vergangenheit liegt.

>[!NOTE]
>
>Alle API-Aufrufe zum Hochladen oder Aktualisieren von Assets oder Binärdateien im Allgemeinen (wie Ausgabeformate) werden für die Bereitstellung von AEM as a Cloud Service nicht mehr unterstützt. For uploading binaries, use [direct binary upload APIs](developer-reference-material-apis.md#asset-upload-technical) instead.

## Inhaltsfragmente {#content-fragments}

Ein [Inhaltsfragment](content-fragments/content-fragments.md) ist ein spezieller Asset-Typ. Er kann für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden. Da es einige Unterschiede zu `standard`-Assets (z. B. Bildern oder Dokumenten) gibt, gelten einige zusätzliche Regeln für die Verarbeitung von Inhaltsfragmenten.

Weitere Informationen finden Sie unter [Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API](assets-api-content-fragments.md).

## Datenmodell {#data-model}

Die Assets-HTTP-API stellt zwei wichtige Elemente bereit: Ordner und Assets (für Standard-Assets).

Außerdem stellt sie ausführlichere Elemente für die benutzerdefinierten Datenmodelle bereit, die strukturierte Inhalte in Inhaltsfragmenten beschreiben. Weitere Informationen finden Sie im Abschnitt [Datenmodelle für Inhaltsfragmente](assets-api-content-fragments.md#content-models-and-content-fragments).

### Ordner {#folders}

Ordner verhalten sich wie Verzeichnisse in traditionellen Dateisystemen. Sie stellen Container für andere Ordner oder Assets dar. Ordner enthalten folgende Komponenten:

**Entitäten**: Zu den Entitäten eines Ordners zählen die untergeordneten Elemente, z. B. die Ordner und Assets.

**Eigenschaften**:
* `name`: Name des Ordners. Dies entspricht dem letzten Segment im URL-Pfad ohne die Erweiterung
* `title`: Optionaler Titel des Ordners, der anstelle des Namens angezeigt werden kann

>[!NOTE]
>
>Einige Eigenschaften des Ordners oder Assets sind einem anderen Präfix zugeordnet. Das `jcr`-Präfix von `jcr:title`, `jcr:description` und `jcr:language` werden mit dem `dc`-Präfix ersetzt. Daher enthalten im zurückgegebenen JSON `dc:title` und `dc:description` die Werte aus `jcr:title` bzw. `jcr:description`.

**Links**-Ordner stellen drei Links bereit:
* `self`: Link zu sich selbst
* `parent`: Link zum übergeordneten Ordner
* `thumbnail`: (Optionaler) Link zu einem Ordnerminiaturbild

### Assets {#assets}

In AEM enthalten Assets die folgenden Elemente:

* Die Eigenschaften und Metadaten des Assets
* Mehrere Wiedergabeformate, z. B. das ursprüngliche Wiedergabeformat (das ursprünglich hochgeladene Asset), eine Miniaturansicht und viele andere Wiedergabeformate. Bei den zusätzlichen Wiedergabeformaten kann es sich um Bilder unterschiedlicher Größe, unterschiedliche Videokodierungen oder aus PDF- oder InDesign-Dateien extrahierte Seiten handeln.
* Optionale Kommentare

Weitere Informationen über Elemente in Inhaltsfragmenten finden Sie unter [Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API](assets-api-content-fragments.md).

In AEM enthält ein Ordner die folgenden Komponenten:

* Entitäten: Die untergeordneten Elemente von Assets sind die Ausgabeformate.
* Eigenschaften
* Links

Die Assets-HTTP-API bietet die folgenden Funktionen:

* Abrufen von Ordnerauflistungen
* Erstellen von Ordnern
* Erstellen von Assets   (veraltet)
* Aktualisieren der Asset-Binärdatei (veraltet)
* Aktualisieren der Asset-Metadaten
* Erstellen von Asset-Ausgabeformaten
* Aktualisieren von Asset-Ausgabeformaten
* Erstellen von Asset-Kommentaren
* Kopieren von Ordnern oder Assets
* Verschieben von Ordnern oder Assets
* Löschen von Ordnern, Assets oder Wiedergabeformaten

>[!NOTE]
>
>Zur besseren Lesbarkeit der folgenden Beispiele wird die vollständige cURL-Notation weggelassen. Tatsächlich korreliert die Notation mit [Resty](https://github.com/micha/resty), dem Skript-Wrapper für cURL.

<!-- TBD: The Console Manager is not available now. So how to configure the below? 

**Prerequisites**

* Go to `https://[aem_server]:[port]/system/console/configMgr`.
* Navigate to **Adobe Granite CSRF Filter**.
* Make sure the property **Filter Methods** includes: POST, PUT, DELETE.
-->

## Abrufen von Ordnerauflistungen {#retrieve-a-folder-listing}

Ruft eine Siren-Darstellung eines vorhandenen Ordners und seiner untergeordneten Entitäten ab (Unterordner oder Assets).

**Anforderung**

```
GET /api/assets/myFolder.json
```

**Antwort-Codes**

```
200 - OK - success
404 - NOT FOUND - folder does not exist or is not accessible
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

**Antwort**

Die Klasse der zurückgegebenen Entität ist Assets/Ordner.

Die Eigenschaften der enthaltenen Entitäten bilden eine Untergruppe der vollständigen Eigenschaften einer jeden Entität. Um eine vollständige Darstellung der Entität zu erreichen, sollten Kunden den Inhalt der URL abrufen, auf die der Link mit einem `rel` von `self` verweist.

## Erstellen von Ordnern {#create-a-folder}

Erstellt einen neuen Ordner `sling`: `OrderedFolder` im festgelegten Pfad. Wenn statt eines Knotennamens ein * angegeben wird, verwendet das Servlet den Parameternamen als Knotennamen. Akzeptiert als Anforderungsdaten wird entweder eine Siren-Darstellung des neuen Ordners oder ein Satz von Name-Wert-Paaren, kodiert als `application/www-form-urlencoded` oder `multipart`/ `form`- `data`. Dies ist dann sinnvoll, wenn Sie einen Ordner direkt aus einem HTML-Formular erstellen. Zusätzlich können die Eigenschaften des Ordners als URL-Abfrageparameter angegeben werden.

Wenn der übergeordnete Knoten des angegebenen Pfades nicht vorhanden ist, schlägt der Vorgang mit einem Antwort-Code `500` fehl. Wenn der Ordner bereits vorhanden ist, wird der Antwort-Code `409` zurückgegeben.

**Parameter**

* `name` - Ordnername

**Anforderung**

```
POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'
```

 oder

```
POST /api/assets/* -F"name=myfolder" -F"title=My Folder"
```

**Antwort-Codes**

```
201 - CREATED - on successful creation
409 - CONFLICT - if folder already exist
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Erstellen von Assets {#create-an-asset}

Informationen zum Erstellen eines Assets mit APIs finden Sie unter [Asset-Upload](developer-reference-material-apis.md). Das Erstellen eines Assets mit der HTTP-API wird nicht mehr unterstützt.

## Aktualisieren von Asset-Binärdateien {#update-asset-binary}

Informationen zum Aktualisieren von Asset-Binärdateien mithilfe von APIs finden Sie unter [Asset-Upload](developer-reference-material-apis.md). Das Aktualisieren einer Asset-Binärdatei mit der HTTP-API wird nicht mehr unterstützt.

## Aktualisieren von Metadaten eines Assets {#update-asset-metadata}

Aktualisiert die Asset-Metadateneigenschaften.

**Anforderung**

```
PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'
```

**Antwort-Codes**

```
200 - OK - if Asset has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Erstellen von Asset-Ausgabeformaten {#create-an-asset-rendition}

Erstellt ein neues Asset-Ausgabeformat für ein Asset. Wenn der Anforderungsparametername nicht angegeben wurde, wird der Dateiname als Ausgabeformatname verwendet.

**Parameter**

* `name` - Name des Ausgabeformats
* `file` - Dateiverweis

**Anforderung**

```
POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"
```

 oder

```
POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"
```

**Antwort-Codes**

```
201 - CREATED - if Rendition has been created successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Aktualisieren von Asset-Ausgabeformaten {#update-an-asset-rendition}

Aktualisiert bzw. ersetzt ein Asset-Wiedergabeformat durch die neuen Binärdaten.

**Anforderung**

```
PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png
```

**Antwort-Codes**

```
200 - OK - if Rendition has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Erstellen von Asset-Kommentaren {#create-an-asset-comment}

Erstellt einen neuen Asset-Kommentar.

**Parameter**

* `message` - Nachricht
* `annotationData` - Anmerkungsdaten (JSON)

**Anforderung**

```
POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"
```

**Antwort-Codes**

```
201 - CREATED - if Comment has been created successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Kopieren von Ordnern oder Assets {#copy-a-folder-or-asset}

Kopiert einen Ordner oder ein Asset in dem angegebenen Pfad in ein neues Ziel.

**Anforderungs-Header**

```
X-Destination - a new destination URI within the API solution scope to copy the resource to
X-Depth - either 'infinity' or '0'. The value '0' only copies the resource and its properties, no children.
X-Overwrite - 'F' to prevent overwriting an existing destination
```

**Anforderung**

```
COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"
```

**Antwort-Codes**

```
201 - CREATED - if folder/asset has been copied to a non-existing destination
204 - NO CONTENT - if the folder/asset has been copied to an existing destination
412 - PRECONDITION FAILED - if a request header is missing or
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Verschieben von Ordnern oder Assets {#move-a-folder-or-asset}

Verschiebt einen Ordner oder ein Asset in dem angegebenen Pfad in ein neues Ziel.

**Anforderungs-Header**

```
X-Destination - a new destination URI within the API solution scope to copy the resource to
X-Depth - either 'infinity' or '0'. The value '0' only copies the resource and its properties, no children.
X-Overwrite - either 'T' to force deletion of existing resources or 'F' to prevent overwriting an existing resource.
```

**Anforderung**

```
MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"
```

**Antwort-Codes**

```
201 - CREATED - if folder/asset has been copied to a non-existing destination
204 - NO CONTENT - if the folder/asset has been copied to an existing destination
412 - PRECONDITION FAILED - if a request header is missing or
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Löschen eines Ordners, eines Assets oder eines Ausgabeformats {#delete-a-folder-asset-or-rendition}

Löscht eine Ressource (Struktur) in dem angegebenen Pfad.

**Anforderung**

```
DELETE /api/assets/myFolder
```

 oder

```
DELETE /api/assets/myFolder/myAsset.png
```

 oder

```xml
DELETE /api/assets/myFolder/myAsset.png/renditions/original
```

**Antwort-Codes**

```
200 - OK - if folder has been deleted successfully
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

