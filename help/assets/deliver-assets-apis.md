---
title: Bereitstellungs-APIs
description: Erfahren Sie, wie Sie die Bereitstellungs-APIs verwenden.
role: User
exl-id: 806ca38f-2323-4335-bfd8-a6c79f6f15fb
source-git-commit: c36938e80d0b159c5f89d450aaa228c37c4f5276
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 94%

---

# Bereitstellungs-APIs {#delivery-apis}

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

Alle [genehmigten Assets](approve-assets.md), die im Experience Manager-Asset-Repository verfügbar sind, können [durchsucht](search-assets-api.md) werden und anschließend mithilfe einer Bereitstellungs-URL an integrierte nachgelagerte Anwendungen gesendet werden.

Alle Änderungen an genehmigten Assets in DAM, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden automatisch in die Bereitstellungs-URLs übernommen. Mit einem niedrigen Time-to-Live(TTL)-Wert von 10 Minuten für die Bereitstellung von Assets per CDN werden Aktualisierungen in weniger als 10 Minuten in allen Authoring- und Publishing-Oberflächen sichtbar.

Die folgende Abbildung zeigt die verfügbaren Bereitstellungs-URLs:

![Bereitstellungs-APIs](assets/delivery-url.png)

Die folgende Tabelle zeigt die Verwendung der verschiedenen verfügbaren Bereitstellungs-APIs:

| Bereitstellungs-API | Beschreibung |
|---|---|
| [Web-optimierte binäre Darstellung des Assets im angeforderten Ausgabeformat](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat) | Gibt die Web-optimierte binäre Darstellung des Assets im angeforderten Ausgabeformat basierend auf der in der Anfrage gesendeten Asset-ID zurück. Darüber hinaus können Sie verschiedene Bildmodifikatoren definieren, z. B. Breite, Höhe, Drehung, Spiegelung, Qualität, Zuschnitt, Format und [intelligenter Zuschnitt](/help/assets/dynamic-media/image-profiles.md). Informationen zu unterstützten Formaten und Bildmodifikatoren finden Sie unter [API-Details](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat).<br>Adobe empfiehlt die Verwendung dieser API für alle Bildformattypen. |
| [Web-optimierte binäre Darstellung des Assets](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAsset) | Praktische API, die die Standardeinstellungen auf eine Web-optimierte binäre Darstellung des in der Antwort zurückgegebenen Assets anwendet. Die Standardeinstellungen sehen ein standardmäßiges JPEG/WEBP-Format, einen Qualitätswert von 65 und einen Breitenwert von 1024 vor. |
| [Ursprünglich hochgeladene Binärdatei des Assets](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetOriginal) | Gibt die ursprünglich hochgeladenen Binärdateien für das Asset zurück. Adobe empfiehlt die Verwendung dieser API für Dokumentformattypen und SVG-Bilder. |
| [Vorgenerierte Ausgabedarstellung des Assets, das in der AEM Assets-Authoring-Umgebung verfügbar ist](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetRendition) | Gibt den in der AEM Assets-Authoring-Umgebung verfügbaren Bitstream der Asset-Ausgabedarstellung basierend auf der Asset-ID und dem Namen der Ausgabedarstellung zurück, die beide in der Anfrage gesendet wurden. |
| [Asset-Metadaten](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetMetadata) | Gibt die mit einem Asset verknüpften Eigenschaften zurück, z. B. Titel, Beschreibung, Erstelldatum, Änderungsdatum usw. |
| [Player-Container für das Video-Asset](https://adobe-aem-assets-delivery.redoc.ly/#operation/videoPlayerDelivery) | Gibt den Player-Container für das Video-Asset zurück. Sie können den Player in ein iFrame-HTML-Element einbetten und das Video abspielen. |
| [Wiedergabe-Manifeste im ausgewählten Ausgabeformat](https://adobe-aem-assets-delivery.redoc.ly/#operation/videoManifestDelivery) | Gibt die Wiedergabe-Manifestdatei für das angegebene Video-Asset im ausgewählten Ausgabeformat zurück. Sie müssen einen benutzerdefinierten Player erstellen, der adaptives Streaming über HLS- oder DASH-Protokolle ermöglicht, um die Wiedergabe-Manifestdatei abzurufen und das Video abzuspielen. |

Dynamic Media mit OpenAPI-Funktionen unterstützt auch Videos in langer Form. Die Videos unterstützen bis zu 50 GB und 2 Stunden.

Informationen zu den verfügbaren Dynamic Media-Angeboten und deren Funktionen finden Sie unter [Dynamic Media Prime und Ultimate](/help/assets/dynamic-media/dm-prime-ultimate.md).

## Bereitstellungs-API-Endpunkte {#delivery-apis-endpoint}

Die API-Endpunkte variieren je nach Bereitstellungs-API. Der API-Endpunkt für die API `Web-optimized binary representation of the asset in the requested output format` lautet beispielsweise:
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/{assetId}/as/{seoName}.{format}`

Die Bereitstellungs-Domain ähnelt der Struktur der Domain der Autorenumgebung von Experience Manager. Der einzige Unterschied ist das Ersetzen des Begriffs `author` durch `delivery`.

`pXXXX` bezeichnet die Programm-ID

`eYYYY` bezeichnet die Umgebungs-ID

Weitere Informationen finden Sie unter [API-Details](https://adobe-aem-assets-delivery.redoc.ly/#tag/Assets).

## Anfragemethode für Bereitstellungs-APIs {#delivery-api-request-method}

GET

## Header für Bereitstellungs-APIs {#deliver-assets-api-header}

Beim Definieren eines Headers müssen Sie die folgenden Details im Header der Bereitstellungs-APIs angeben:

```java
headers: {
      'If-None-Match': 'string',
      Authorization: 'Bearer <YOUR_JWT_HERE>'
    }
```

Zum Aufrufen der Bereitstellungs-APIs ist ein IMS-Token in den `Authorization`-Details erforderlich, um ein eingeschränktes Asset bereitzustellen. Das IMS-Token wird aus einem technischen Konto abgerufen. Informationen zum Erstellen eines neuen technischen Kontos finden Sie unter [Abrufen der Anmeldedaten für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=de#fetch-the-aem-as-a-cloud-service-credentials). Informationen zum Generieren des IMS-Tokens und zu seiner entsprechenden Verwendung im Anfrage-Header der Bereitstellungs-APIs finden Sie unter [Generieren des Zugriffs-Tokens](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=de#generating-the-access-token).


Informationen zum Anzeigen von Anfragebeispielen, Antwortbeispielen und Antwort-Codes finden Sie unter [Bereitstellungs-APIs](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat).
