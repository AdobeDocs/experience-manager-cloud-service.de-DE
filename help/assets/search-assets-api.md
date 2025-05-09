---
title: API zum Durchsuchen von Assets
description: Erfahren Sie, wie Sie die API zum Durchsuchen von Assets verwenden.
role: User
exl-id: 0c52e793-4c33-4230-b4f2-27296dd9e4b3
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 94%

---

# API zum Durchsuchen von Assets {#search-assets-api}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

>[!AVAILABILITY]
>
>Das Handbuch zu Dynamic Media mit OpenAPI-Funktionen ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den KI-Assistenten von Adobe Acrobat, um Ihre Fragen zu beantworten.
>
>[!BADGE Handbuch zu Dynamic Media mit OpenAPI-Funktionen als PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Alle [genehmigten Assets](approve-assets.md), die im Experience Manager-Asset-Repository verfügbar sind, können durchsucht werden und anschließend mithilfe einer Bereitstellungs-URL an integrierte nachgelagerte Anwendungen gesendet werden.

Die Suche nach den richtigen genehmigten Assets im Experience Manager-Repository ist der erste Schritt bei der Bereitstellung von Assets mithilfe der Bereitstellungs-URL. Die Antwort auf die Suchanfrage umfasst ein Array von JSON-Dokumenten, die den Assets entsprechen, die die Suchkriterien erfüllt haben. Jedes JSON-Dokument wird mithilfe eines `id`-Feldes identifiziert, das zum Erstellen der Asset-Bereitstellungsanfrage verwendet wird.

![Überblick über das direkte binäre Upload-Protokoll](assets/search-assets-api-overview.png)

Sie können Eigenschaften in der Anfrage der API zum Durchsuchen von Assets definieren, um die folgenden Funktionen zu aktivieren:

* **Volltextsuche durchführen**: Verwenden Sie die `match`-Abfrage, um den zu suchenden Text zu definieren.  Sie können außerdem die Ergebnisse mithilfe von Operatoren innerhalb der `match`-Abfrage filtern.

* **Filter anwenden**: Verwenden Sie die `term`-Abfrage, um die Ergebnisse weiter zu filtern, indem Sie einen `key` und einen oder mehrere Werte definieren. `key` gibt das Feld an, dessen Wert abgeglichen werden muss, und `value` bestimmt, womit abgeglichen werden soll. Auf ähnliche Weise können Sie mit der `range`-Abfrage einen Bereich für ein Feld definieren, indem Sie die Eigenschaften „Größer als“ (gt), „Größer gleich“ (gte), „Kleiner als“ (lt) und „Kleiner gleich“ (lte) verwenden.

* **Ergebnisse sortieren**: Verwenden Sie die Eigenschaft `OrderBy`, um Suchergebnisse basierend auf einem oder mehreren Feldern zu sortieren. Sie können die Ergebnisse in auf- oder absteigender Reihenfolge sortieren.

* **Paginierung**: Verwenden Sie die Eigenschaften `limit` und `cursor`, um Paginierungseigenschaften in einer Such-API-Anfrage zu definieren. Die Eigenschaft `limit` definiert die maximale Anzahl von Elemente, die im Rahmen einer API-Antwort abgerufen werden soll. Die Eigenschaft `cursor` vereinfacht den Abruf des Startpunkts für den nächsten Satz von Assets, der in der Eigenschaft `limit` definiert ist. Wenn Sie beispielsweise `50` als Limit in der API-Anfrage definieren, können Sie mit der Eigenschaft `cursor` die nächsten 50 Elemente mit der nächsten API-Anfrage abrufen.

## Endpunkt bei der API zum Durchsuchen von Assets {#search-assets-api-endpoint}

Der Endpunkt in einer Anfrage der API zum Durchsuchen von Assets muss das folgende Format aufweisen:
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/search`

Die Bereitstellungs-Domain ähnelt der Struktur der Domain der Autorenumgebung von Experience Manager. Der einzige Unterschied ist das Ersetzen des Begriffs `author` durch `delivery`.

`pXXXX` bezeichnet die Programm-ID

`eYYYY` bezeichnet die Umgebungs-ID

## Anfragemethode der API zum Durchsuchen von Assets {#search-assets-api-request-method}

POST

## Header der API zum Durchsuchen von Assets {#search-assets-api-header}

Beim Definieren eines Headers in der API zum Durchsuchen von Assets müssen Sie die folgenden Details angeben:

```java
headers: {
      'Content-Type': 'application/json',
      'X-Adobe-Accept-Experimental': '1',
      Authorization: 'Bearer <YOUR_JWT_HERE>',
      'X-Api-Key': 'YOUR_API_KEY_HERE'
    },
```

Um die Such-API aufzurufen, ist ein IMS-Token erforderlich, das in den `Authorization`-Details definiert wird. Das IMS-Token wird aus einem technischen Konto abgerufen. Informationen zum Erstellen eines neuen technischen Kontos finden Sie unter [Abrufen der Anmeldedaten für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=de#fetch-the-aem-as-a-cloud-service-credentials). Informationen zum Generieren des IMS-Tokens und zu seiner entsprechenden Verwendung im Anfrage-Header der API zum Durchsuchen von Assets finden Sie unter [Generieren des Zugriffs-Tokens](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=de#generating-the-access-token).

Anfragebeispiele, Antwortbeispiele und Antwort-Codes finden Sie unter [API zum Durchsuchen von Assets](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/search).
