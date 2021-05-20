---
title: Assets-HTTP-API
description: Erstellen, lesen, aktualisieren, löschen, verwalten Sie digitale Assets mit der HTTP-API in  [!DNL Experience Manager Assets].
contentOwner: AG
feature: Assets-HTTP-API,APIs
role: Developer,Architect,Administrator
exl-id: a3b7374d-f24b-4d6f-b6db-b9c9c962bb8d
source-git-commit: b989833b7f1fa0c3de91f96e28a21859d97294cb
workflow-type: tm+mt
source-wordcount: '1519'
ht-degree: 69%

---

# [!DNL Adobe Experience Manager Assets]-HTTP-API {#assets-http-api}

## Überblick {#overview}

Die HTTP-API [!DNL Assets] ermöglicht CRUD-Vorgänge (Create-Read-Update-Delete, Erstellen/Lesen/Aktualisieren/Löschen) für digitale Assets, einschließlich Metadaten, Ausgabedarstellungen und Kommentaren sowie strukturierten Inhalten mit [!DNL Experience Manager] Inhaltsfragmenten. Sie wird unter `/api/assets` bereitgestellt und als REST-API implementiert. Dazu gehört die [Unterstützung von Inhaltsfragmenten](/help/assets/content-fragments/assets-api-content-fragments.md).

So greifen Sie auf die API zu:

1. Öffnen Sie das Dokument zum API-Service unter `https://[hostname]:[port]/api.json`.
1. Folgen Sie dem Dienstlink [!DNL Assets], der zu `https://[hostname]:[server]/api/assets.json` führt.

Die API antwortet mit einer JSON-Datei für einige MIME-Typen und einem Antwort-Code für alle MIME-Typen. Die JSON-Antwort ist optional und kann zum Beispiel nicht für PDF-Dateien verfügbar sein. Verwenden Sie den Antwort-Code für weitere Analysen oder Aktionen.

>[!NOTE]
>
>Alle API-Aufrufe zum Hochladen oder Aktualisieren von Assets oder Binärdateien im Allgemeinen (wie Ausgabedarstellungen) werden für [!DNL Experience Manager] als [!DNL Cloud Service]-Bereitstellung nicht mehr unterstützt. Verwenden Sie zum Hochladen von Binärdateien stattdessen [direkte binäre Upload-APIs](developer-reference-material-apis.md#asset-upload-technical).

## Inhaltsfragmente {#content-fragments}

Ein [Inhaltsfragment](/help/assets/content-fragments/content-fragments.md) ist ein spezieller Asset-Typ. Sie kann für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden. Da es einige Unterschiede zu `standard`-Assets (z. B. Bildern oder Dokumenten) gibt, gelten einige zusätzliche Regeln für die Verarbeitung von Inhaltsfragmenten.

Weitere Informationen finden Sie unter [Unterstützung von Inhaltsfragmenten in der  [!DNL Experience Manager Assets] HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md).

## Datenmodell {#data-model}

Die HTTP-API [!DNL Assets] stellt zwei wichtige Elemente, Ordner und Assets bereit (für Standard-Assets). Außerdem werden detailliertere Elemente für die benutzerdefinierten Datenmodelle bereitgestellt, die strukturierte Inhalte in Inhaltsfragmenten beschreiben. Weitere Informationen finden Sie unter [Inhaltsfragmentdatenmodelle](/help/assets/content-fragments/assets-api-content-fragments.md#content-models-and-content-fragments) .

### Ordner {#folders}

Ordner ähneln Verzeichnissen wie in herkömmlichen Dateisystemen. Ordner können nur Assets, nur Ordner oder Ordner und Assets enthalten. Ordner enthalten folgende Komponenten:

**Entitäten**: Zu den Entitäten eines Ordners zählen die untergeordneten Elemente, z. B. die Ordner und Assets.

**Eigenschaften**:

* `name` ist der Name des Ordners. Dies entspricht dem letzten Segment im URL-Pfad ohne die Erweiterung.
* `title` Ist ein optionaler Titel des Ordners, der anstelle des Namens angezeigt werden kann

>[!NOTE]
>
>Einige Eigenschaften des Ordners oder Assets sind einem anderen Präfix zugeordnet. Das `jcr`-Präfix von `jcr:title`, `jcr:description` und `jcr:language` werden mit dem `dc`-Präfix ersetzt. Daher enthalten im zurückgegebenen JSON `dc:title` und `dc:description` die Werte aus `jcr:title` bzw. `jcr:description`.

**Links**-Ordner stellen drei Links bereit:

* `self`: Link zu sich selbst.
* `parent`: Link zum übergeordneten Ordner.
* `thumbnail`: (Optionaler) Link zu einem Ordnerminiaturbild.

### Assets {#assets}

In [!DNL Experience Manager] enthalten Assets die folgenden Elemente:

* Die Eigenschaften und Metadaten des Assets.
* Ursprünglich wurde die Binärdatei des Assets hochgeladen.
* Mehrere Ausgabedarstellungen wie konfiguriert. Dabei kann es sich um Bilder unterschiedlicher Größe, Videos unterschiedlicher Kodierungen oder extrahierte Seiten aus PDF- oder [!DNL Adobe InDesign]-Dateien handeln.
* Optionale Kommentare.

Weitere Informationen über Elemente in Inhaltsfragmenten finden Sie unter [Unterstützung von Inhaltsfragmenten in der Experience Manager Assets-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md).

In [!DNL Experience Manager] enthält ein Ordner die folgenden Komponenten:

* Entitäten: Die untergeordneten Elemente von Assets sind die Ausgabedarstellungen.
* Eigenschaften.
* Links.

## Verfügbare Funktionen {#available-features}

Die HTTP-API [!DNL Assets] umfasst die folgenden Funktionen:

* [Abrufen von Ordnerauflistungen](#retrieve-a-folder-listing).
* [Erstellen eines Ordners](#create-a-folder).
* [Erstellen von Assets (veraltet)](#create-an-asset)
* [Aktualisieren der Asset-Binärdatei (veraltet)](#update-asset-binary).
* [Aktualisieren der Asset-Metadaten](#update-asset-metadata).
* [Erstellen von Asset-Ausgabedarstellungen](#create-an-asset-rendition).
* [Aktualisieren von Asset-Ausgabedarstellungen](#update-an-asset-rendition).
* [Erstellen von Asset-Kommentaren](#create-an-asset-comment).
* [Kopieren von Ordnern oder Assets](#copy-a-folder-or-asset).
* [Verschieben von Ordnern oder Assets](#move-a-folder-or-asset).
* [Löschen von Ordnern, Assets oder Ausgabedarstellungen](#delete-a-folder-asset-or-rendition).

>[!NOTE]
>
>Zur besseren Lesbarkeit werden in den folgenden Beispielen die vollständigen cURL-Anmerkungen weggelassen. Die -Notation korreliert mit [Resty](https://github.com/micha/resty) , dem Skript-Wrapper für cURL.

<!-- TBD: The Console Manager is not available now. So how to configure the below? 

**Prerequisites**

* Go to `https://[aem_server]:[port]/system/console/configMgr`.
* Navigate to **Adobe Granite CSRF Filter**.
* Make sure the property **Filter Methods** includes: POST, PUT, DELETE.
-->

## Abrufen von Ordnerauflistungen {#retrieve-a-folder-listing}

Ruft eine Siren-Darstellung eines vorhandenen Ordners und seiner untergeordneten Entitäten ab (Unterordner oder Assets).

**Anfrage**: `GET /api/assets/myFolder.json`

**Antwort-Codes**: Die Antwort-Codes sind:

* 200 – OK – Erfolg.
* 404 – NICHT GEFUNDEN – Ordner existiert nicht oder ist nicht zugänglich.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

**Antwort**: Die Klasse der zurückgegebenen Entität ist ein Asset oder ein Ordner. Die Eigenschaften der enthaltenen Entitäten bilden eine Teilmenge der vollständigen Eigenschaften jeder Entität. Um eine vollständige Darstellung der Entität zu erreichen, sollten Kunden den Inhalt der URL abrufen, auf die der Link mit einem `rel` von `self` verweist.

## Erstellen von Ordnern {#create-a-folder}

Erstellt eine `sling`: `OrderedFolder` am angegebenen Pfad. Wenn `*` anstelle eines Knotennamens angegeben wird, verwendet das Servlet den Parameternamen als Knotennamen. Die Anfrage akzeptiert eine der folgenden Optionen:

* Eine Siren-Darstellung des neuen Ordners
* Ein Satz von Name-Wert-Paaren, kodiert als `application/www-form-urlencoded` oder `multipart`/ `form`- `data`. Diese sind nützlich, um einen Ordner direkt aus einem HTML-Formular zu erstellen.

Außerdem können Eigenschaften des Ordners als URL-Abfrageparameter angegeben werden.

Wenn der übergeordnete Knoten des angegebenen Pfades nicht vorhanden ist, schlägt der API-Aufruf mit einem Antwort-Code `500` fehl. Ein Aufruf gibt einen Antwort-Code `409` zurück, wenn der Ordner vorhanden ist.

**Parameter**: `name` ist der Ordnername.

**Anfrage**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**Antwort-Codes**: Die Antwort-Codes sind:

* 201 – ERSTELLT – bei erfolgreicher Erstellung.
* 409 - KONFLIKT - wenn der Ordner vorhanden ist.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Erstellen von Assets {#create-an-asset}

Informationen zum Erstellen eines Assets finden Sie unter [Asset-Upload](developer-reference-material-apis.md) . Sie können ein Asset nicht mit der HTTP-API erstellen.

## Aktualisieren von Asset-Binärdateien {#update-asset-binary}

Informationen zum Aktualisieren von Asset-Binärdateien finden Sie unter [Asset-Upload](developer-reference-material-apis.md) . Sie können eine Asset-Binärdatei nicht mit der HTTP-API aktualisieren.

## Aktualisieren von Metadaten eines Assets {#update-asset-metadata}

Aktualisiert die Asset-Metadateneigenschaften. Wenn Sie eine Eigenschaft im `dc:`-Namespace aktualisieren, aktualisiert die API dieselbe Eigenschaft im `jcr`-Namespace. Die API synchronisiert die Eigenschaften unter den beiden Namespaces nicht.

**Anfrage**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'`

**Antwort-Codes**: Die Antwort-Codes sind:

* 200 – OK – wenn das Asset erfolgreich aktualisiert wurde.
* 404 – NICHT GEFUNDEN – wenn das Asset nicht gefunden oder unter dem angegebenen URI nicht aufgerufen werden konnte.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Erstellen von Asset-Ausgabedarstellungen {#create-an-asset-rendition}

Erstellen Sie eine Ausgabedarstellung für ein Asset. Wenn der Name nicht als Anfrageparameter angegeben wurde, wird der Dateiname als Ausgabedarstellungsname verwendet.

**Parameter**: Die Parameter sind `name` für den Namen der Ausgabedarstellung und `file` als ein Dateiverweis.

**Anfrage**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**Antwort-Codes**

* 201 – ERSTELLT - wenn die Ausgabedarstellung erfolgreich erstellt wurde.
* 404 – NICHT GEFUNDEN – wenn das Asset nicht gefunden oder unter dem angegebenen URI nicht aufgerufen werden konnte.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Aktualisieren von Asset-Ausgabedarstellungen {#update-an-asset-rendition}

Aktualisiert bzw. ersetzt eine Asset-Ausgabedarstellung durch die neuen Binärdaten.

**Anfrage**: `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**Antwort-Codes**: Die Antwort-Codes sind:

* 200 – OK – wenn die Ausgabedarstellung erfolgreich aktualisiert wurde.
* 404 – NICHT GEFUNDEN – wenn das Asset nicht gefunden oder unter dem angegebenen URI nicht aufgerufen werden konnte.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Hinzufügen eines Kommentars zu einem Asset {#create-an-asset-comment}

**Parameter**: Die Parameter sind  `message` für den Nachrichtentext des Kommentars und  `annotationData` für die Anmerkungsdaten im JSON-Format bestimmt.

**Anfrage**: `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**Antwort-Codes**: Die Antwort-Codes sind:

* 201 – ERSTELLT - wenn der Kommentar erfolgreich erstellt wurde.
* 404 – NICHT GEFUNDEN – wenn das Asset nicht gefunden oder unter dem angegebenen URI nicht aufgerufen werden konnte.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Kopieren von Ordnern oder Assets {#copy-a-folder-or-asset}

Kopiert einen Ordner oder ein Asset in dem angegebenen Pfad in ein neues Ziel.

**Anfrage-Header**: Die Parameter sind:

* `X-Destination` – ein neuer Ziel-URI im Bereich der API-Lösung, in den die Ressource kopiert werden soll.
* `X-Depth` – entweder `infinity` oder `0`. Mit `0` werden nur die Ressource und ihre Eigenschaften kopiert und nicht ihre untergeordneten Elemente.
* `X-Overwrite` – Verwenden Sie `F`, um ein Überschreiben eines Assets am vorhandenen Ziel zu verhindern.

**Anfrage**: `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**Antwort-Codes**: Die Antwort-Codes sind:

* 201 – ERSTELLT – wenn der Ordner/das Asset in ein nicht vorhandenes Ziel kopiert wurde.
* 204 – KEIN INHALT – wenn der Ordner/das Asset in ein vorhandenes Ziel kopiert wurde.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn ein Anfrage-Header fehlt.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Verschieben von Ordnern oder Assets {#move-a-folder-or-asset}

Verschiebt einen Ordner oder ein Asset in dem angegebenen Pfad in ein neues Ziel.

**Anfrage-Header**: Die Parameter sind:

* `X-Destination` – ein neuer Ziel-URI im Bereich der API-Lösung, in den die Ressource kopiert werden soll.
* `X-Depth` – entweder `infinity` oder `0`. Mit `0` werden nur die Ressource und ihre Eigenschaften kopiert und nicht ihre untergeordneten Elemente.
* `X-Overwrite` - Verwenden Sie entweder  `T` zum erzwungenen Löschen vorhandener Ressourcen oder  `F` um zu verhindern, dass eine vorhandene Ressource überschrieben wird.

**Anfrage**: `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

**Antwort-Codes**: Die Antwort-Codes sind:

* 201 – ERSTELLT – wenn der Ordner/das Asset in ein nicht vorhandenes Ziel kopiert wurde.
* 204 – KEIN INHALT – wenn der Ordner/das Asset in ein vorhandenes Ziel kopiert wurde.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn ein Anfrage-Header fehlt.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Löschen eines Ordners, eines Assets oder einer Ausgabedarstellung {#delete-a-folder-asset-or-rendition}

Löscht eine Ressource(nstruktur) im angegebenen Pfad.

**Anfrage**

* `DELETE /api/assets/myFolder`
* `DELETE /api/assets/myFolder/myAsset.png`
* `DELETE /api/assets/myFolder/myAsset.png/renditions/original`

**Antwort-Codes**: Die Antwort-Codes sind:

* 200 – OK – wenn der Ordner erfolgreich gelöscht wurde.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Tipps, Best Practices und Einschränkungen {#tips-limitations}

* Nach der [!UICONTROL Ausschaltzeit] sind ein Asset und seine Ausgabedarstellungen weder über die [!DNL Assets]-Web-Oberfläche noch über die HTTP-API verfügbar. Die API gibt die Fehlermeldung 404 zurück, wenn die [!UICONTROL Einschaltzeit] in der Zukunft oder die [!UICONTROL Ausschaltzeit] in der Vergangenheit liegt.

* Die Assets-HTTP-API gibt die vollständigen Metadaten nicht zurück. Die Namespaces sind fest codiert und nur diese Namespaces werden zurückgegeben. Vollständige Metadaten finden Sie im Asset-Pfad `/jcr_content/metadata.json`.

* Einige Eigenschaften des Ordners oder Assets werden einem anderen Präfix zugeordnet, wenn sie mit APIs aktualisiert werden. Das `jcr`-Präfix von `jcr:title`, `jcr:description` und `jcr:language` werden mit dem `dc`-Präfix ersetzt. Daher enthalten im zurückgegebenen JSON `dc:title` und `dc:description` die Werte aus `jcr:title` bzw. `jcr:description`.

>[!MORELIKETHIS]
>
>* [Referenzdokumente für Entwickler für  [!DNL Assets]](/help/assets/developer-reference-material-apis.md)

