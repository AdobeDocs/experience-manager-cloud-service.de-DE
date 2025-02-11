---
title: Assets-HTTP-API
description: Erstellen, lesen, aktualisieren, löschen, verwalten Sie digitale Assets mit der HTTP-API in [!DNL Experience Manager Assets].
contentOwner: AG
feature: Assets HTTP API
role: Developer, Architect, Admin
exl-id: a3b7374d-f24b-4d6f-b6db-b9c9c962bb8d
source-git-commit: 3143ca304ec7ff56d45502a3fd5e49b3b9ed6ce4
workflow-type: tm+mt
source-wordcount: '1709'
ht-degree: 81%

---

# Verwalten digitaler Assets mit der [!DNL Adobe Experience Manager Assets] HTTP-API{#assets-http-api}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/assets/extending/mac-api-assets.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

## Erste Schritte mit der AEM [!DNL Assets] der HTTP-API {#overview}

Die AEM [!DNL Assets] HTTP-API ermöglicht CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren und Löschen) für digitale Assets über eine REST-Schnittstelle unter /`api/assets`. Diese Vorgänge gelten für Asset-Metadaten, Ausgabedarstellungen und Kommentare. Dazu gehört die [Unterstützung für Inhaltsfragmente](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
> Eine modernisierte OpenAPI-Implementierung des API für die Verwaltung von Inhaltsfragmenten ist verfügbar. Eine vollständige Dokumentation finden Sie unter [API für die Verwaltung von Inhaltsfragmenten](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/?lang=de). Es wird empfohlen, die neue OpenAPI-Implementierung zu verwenden. Die vorhandene Verwendung des Assets-HTTP-API für Inhaltsfragmente sollte in des neuen OpenAPI für die Inhaltsfragmentverwaltung migriert werden.

So greifen Sie auf die API zu:

1. Öffnen Sie das Dokument zum API-Service unter `https://[hostname]:[port]/api.json`.
1. Folgen Sie dem Link zum [!DNL Assets]-Service, der zu `https://[hostname]:[server]/api/assets.json` führt.

Die API antwortet mit einer JSON-Datei für einige MIME-Typen und einem Antwort-Code für alle MIME-Typen. Die JSON-Antwort ist optional und kann zum Beispiel für PDF-Dateien nicht verfügbar sein. Verwenden Sie den Antwort-Code für weitere Analysen oder Aktionen.

>[!NOTE]
>
>Alle API-Aufrufe zum Hochladen oder Aktualisieren von Assets oder Binärdateien im Allgemeinen (wie Ausgabedarstellungen) werden für die Bereitstellung von [!DNL Experience Manager] as a [!DNL Cloud Service] nicht mehr unterstützt. Verwenden Sie zum Hochladen von Binärdateien stattdessen [direkte binäre Upload-APIs](developer-reference-material-apis.md#asset-upload).

## Verwalten von Inhaltsfragmenten {#content-fragments}

Ein [Inhaltsfragment](/help/assets/content-fragments/content-fragments.md) ist ein strukturiertes Asset, das Text, Zahlen und Daten speichert. Da es einige Unterschiede zu `standard`-Assets (z. B. Bildern oder Dokumenten) gibt, gelten einige zusätzliche Regeln für die Verarbeitung von Inhaltsfragmenten.

Weitere Informationen finden Sie unter [Unterstützung von Inhaltsfragmenten in der [!DNL Experience Manager Assets] HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
>Unter [AEM-APIs für die Bereitstellung und Verwaltung strukturierter Inhalte](/help/headless/apis-headless-and-content-fragments.md) finden Sie einen Überblick über die verschiedenen verfügbaren APIs und einen Vergleich einiger der damit verbundenen Konzepte.
>
>Die [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md) sind ebenfalls verfügbar.

## Prüfen des Datenmodells {#data-model}

Die [!DNL Assets]-HTTP-API stellt in erster Linie zwei Elemente bereit: Ordner und Standard-Assets. Sie enthält auch detaillierte Elemente für benutzerdefinierte Datenmodelle, die in Inhaltsfragmenten verwendet werden. Weitere Informationen finden Sie unter Inhaltsfragmentdatenmodelle. Weitere Informationen finden Sie im Abschnitt [Datenmodelle für Inhaltsfragmente](/help/assets/content-fragments/assets-api-content-fragments.md#content-models-and-content-fragments).

>[!NOTE]
>
>Die [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md) sind ebenfalls verfügbar.

### Ordner verwalten {#folders}

Ordner verhalten sich wie Verzeichnisse in traditionellen Dateisystemen. Ordner können Assets, Unterordner oder beides enthalten. Ordner enthalten folgende Komponenten:

**Entitäten**: Zu den Entitäten eines Ordners zählen die untergeordneten Elemente, z. B. die Ordner und Assets.

**Eigenschaften**:

* `name`: Der Name des Ordners (das letzte Segment des URL-Pfads, ohne Erweiterung).
* `title`: Ein optionaler Titel, der anstelle des Ordnernamens angezeigt wird.

>[!NOTE]
>
>Einige Eigenschaften des Ordners oder Assets sind einem anderen Präfix zugeordnet. Das `jcr`-Präfix von `jcr:title`, `jcr:description` und `jcr:language` werden mit dem `dc`-Präfix ersetzt. Daher enthalten im zurückgegebenen JSON `dc:title` und `dc:description` die Werte aus `jcr:title` bzw. `jcr:description`.

**Links**-Ordner stellen drei Links bereit:

* `self`: Ein Link zum Ordner selbst.
* `parent`: Ein Link zum übergeordneten Ordner.
* `thumbnail` (Optional): Ein Link zu einem Ordner-Miniaturbild.

### Verwalten von Assets {#assets}

In [!DNL Experience Manager] enthalten Assets die folgenden Elemente:

* **Eigenschaften und Metadaten** Beschreibende Informationen zum Asset.
* **Binärdatei:** die ursprünglich hochgeladene Datei.
* **Ausgabedarstellungen:** mehrere konfigurierte Ausgabedarstellungen (z. B. Bilder in verschiedenen Größen, verschiedene Videokodierungen oder extrahierte Seiten aus PDF-/Adobe InDesign-Dateien).
* **Kommentare (optional):** von Benutzern bereitgestellte Anmerkungen.

Weitere Informationen über Elemente in Inhaltsfragmenten finden Sie unter [Unterstützung von Inhaltsfragmenten in der Experience Manager Assets-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
>Die [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md) sind ebenfalls verfügbar.

In [!DNL Experience Manager] enthält ein Ordner die folgenden Komponenten:

* Entitäten: Die untergeordneten Elemente von Assets sind die Ausgabedarstellungen.
* Eigenschaften.
* Links.

## Verfügbare API-Vorgänge erkunden {#available-features}

Die [!DNL Assets]-HTTP-API bietet die folgenden Funktionen:

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
>Zur besseren Lesbarkeit der folgenden Beispiele wird die vollständige cURL-Notation weggelassen. Die Notation korreliert mit [Resty](https://github.com/micha/resty), einem Skript-Wrapper für cURL.

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

**Antwort**: Die Klasse der zurückgegebenen Entität ist ein Asset oder ein Ordner. Die Eigenschaften der enthaltenen Entitäten bilden eine Teilmenge der vollständigen Eigenschaften jeder Entität. Um eine vollständige Darstellung der Entität zu erreichen, sollten Kundinnen und Kunden den Inhalt der URL abrufen, auf die der Link mit einem `rel` von `self` verweist.

## Erstellen eines Ordners {#create-a-folder}

Erstellt einen `sling`: `OrderedFolder` im festgelegten Pfad. Wenn statt eines Knotennamens ein `*` angegeben wird, verwendet das Servlet den Parameternamen als Knotennamen. Die Anfrage akzeptiert eine der folgenden Optionen:

* Eine Siren-Darstellung des neuen Ordners
* Ein Satz von Name-Wert-Paaren, kodiert als `application/www-form-urlencoded` oder `multipart`/ `form` – `data`. Diese sind nützlich, um einen Ordner direkt aus einem HTML-Formular zu erstellen.

Zusätzlich können die Eigenschaften des Ordners als URL-Abfrageparameter angegeben werden.

Wenn der übergeordnete Knoten des angegebenen Pfades nicht vorhanden ist, schlägt der API-Aufruf mit einem Antwort-Code `500` fehl. Ein Aufruf gibt einen Antwort-Code `409` zurück, wenn der Ordner bereits vorhanden ist.

**Parameter**: `name` ist der Ordnername.

**Anfrage**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**Antwort-Codes**: Die Antwort-Codes sind:

* 201 – ERSTELLT – bei erfolgreicher Erstellung.
* 409 – KONFLIKT – wenn der Ordner vorhanden ist.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Erstellen von Assets {#create-an-asset}

Die Erstellung von Assets wird über diese HTTP-API nicht unterstützt. Verwenden Sie für die Asset-Erstellung die [Asset-Upload](developer-reference-material-apis.md)-API.

## Aktualisieren von Asset-Binärdateien {#update-asset-binary}

Informationen zum Aktualisieren von Asset-Binärdateien finden Sie unter [Asset-Upload](developer-reference-material-apis.md). Mit der HTTP-API kann keine Asset-Binärdatei aktualisiert werden.

## Aktualisieren von Metadaten eines Assets {#update-asset-metadata}

Dieser Vorgang aktualisiert die Metadaten des Assets. Beim Aktualisieren von Eigenschaften im `dc:`-Namespace wird die entsprechende `jcr:` aktualisiert. Die API synchronisiert jedoch nicht die Eigenschaften unter den beiden Namespaces.

**Anfrage**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'`

**Antwort-Codes**: Die Antwort-Codes sind:

* 200 – OK – wenn das Asset erfolgreich aktualisiert wurde.
* 404 – NICHT GEFUNDEN – wenn das Asset nicht gefunden oder unter dem angegebenen URI nicht aufgerufen werden konnte.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Erstellen von Asset-Ausgabeformaten {#create-an-asset-rendition}

Erstellt eine neue Ausgabedarstellung für ein Asset. Wenn der Name nicht als Anfrageparameter angegeben wurde, wird der Dateiname als Ausgabedarstellungsname verwendet.

**Parameter**: Die Parameter sind:

`name`: für den Namen der Ausgabedarstellung.
`file`: Die Binärdatei für die Ausgabedarstellung als Referenz.

**Anfrage**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**Antwort-Codes**

* 201 – ERSTELLT - wenn die Ausgabedarstellung erfolgreich erstellt wurde.
* 404 – NICHT GEFUNDEN – wenn das Asset nicht gefunden oder unter dem angegebenen URI nicht aufgerufen werden konnte.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Aktualisieren von Asset-Ausgabeformaten {#update-an-asset-rendition}

Aktualisiert bzw. ersetzt eine Asset-Ausgabedarstellung durch die neuen Binärdaten.

**Anfrage**: `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**Antwort-Codes**: Die Antwort-Codes sind:

* 200 – OK – wenn die Ausgabedarstellung erfolgreich aktualisiert wurde.
* 404 – NICHT GEFUNDEN – wenn das Asset nicht gefunden oder unter dem angegebenen URI nicht aufgerufen werden konnte.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Hinzufügen eines Kommentars zu einem Asset {#create-an-asset-comment}

**Parameter**: Die Parameter sind `message` für den Nachrichtentext des Kommentars und `annotationData` für die Anmerkungsdaten im JSON-Format.

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
* `X-Overwrite` – Verwenden Sie entweder `T`, um das Löschen einer vorhandenen Ressource zu erzwingen, oder `F`, um das Überschreiben einer vorhandenen Ressource zu verhindern.

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

## Befolgen Sie die Best Practices und beachten Sie Einschränkungen {#tips-limitations}

* Assets und die zugehörigen Ausgabedarstellungen sind nicht mehr über die [!DNL Assets]-Web-Oberfläche und die HTTP-API verfügbar, wenn die [!UICONTROL Ausschaltzeit] erreicht ist. Die API gibt einen 404-Fehler zurück, wenn die [!UICONTROL Einschaltzeit] in der Zukunft liegt oder [!UICONTROL Ausschaltzeit] in der Vergangenheit liegt.

* Die Assets-HTTP-API gibt nur eine Teilmenge von Metadaten zurück. Die Namespaces sind fest kodiert und nur diese Namespaces werden zurückgegeben. Vollständige Metadaten finden Sie im Asset-Pfad `/jcr_content/metadata.json`.

* Einige Eigenschaften des Ordners oder Assets werden einem anderen Präfix zugeordnet, wenn sie mit APIs aktualisiert wurden. Das `jcr`-Präfix von `jcr:title`, `jcr:description` und `jcr:language` werden mit dem `dc`-Präfix ersetzt. Daher enthalten im zurückgegebenen JSON `dc:title` und `dc:description` die Werte aus `jcr:title` bzw. `jcr:description`.

**Entdecken Sie verwandte Ressourcen**

* [Assets übersetzen](translate-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Referenzdokumente für Entwickelnde für [!DNL Assets]](/help/assets/developer-reference-material-apis.md)
