---
title: Bereitstellungs-APIs
description: Erfahren Sie, wie Sie die Bereitstellungs-APIs verwenden.
role: User
source-git-commit: 6fdc44b93e11a20b6859419813fd7eadbefd95c1
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Bereitstellungs-APIs {#delivery-apis}

Alle [genehmigten Assets](approve-assets.md), die im Experience Manager-Asset-Repository verfügbar sind, können [durchsucht](search-assets-api.md) werden und dann mithilfe einer Bereitstellungs-URL an integrierte nachgelagerte Anwendungen gesendet werden.

Alle Änderungen an genehmigten Assets in DAM, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden automatisch in die Bereitstellungs-URLs übernommen. Mit einem kurzen TTL-Wert (Time-to-Live) von 10 Minuten, der für die Bereitstellung von Assets über CDN konfiguriert ist, werden Aktualisierungen in weniger als 10 Minuten auf allen Authoring- und veröffentlichten Schnittstellen sichtbar.

Die folgende Abbildung zeigt die verfügbaren Versand-URLs:

![Bereitstellungs-APIs](assets/delivery-url.png)

Die folgende Tabelle zeigt die Verwendung der verschiedenen verfügbaren Bereitstellungs-APIs:

| Bereitstellungs-API | Beschreibung |
|---|---|
| [Weboptimierte binäre Darstellung des Assets im angeforderten Ausgabeformat](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat) | Gibt die weboptimierte binäre Darstellung des Assets im angeforderten Ausgabeformat basierend auf der in der Anfrage gesendeten Asset-ID zurück. Darüber hinaus können Sie verschiedene Bildmodifikatoren definieren, z. B. Breite, Höhe, Rotation, Spiegeln, Qualität, Zuschneiden, Format und [smartes Zuschneiden](/help/assets/dynamic-media/image-profiles.md). Informationen zu unterstützten Formaten und Bild-Modifikatoren finden Sie unter [API-Details](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetSeoFormat) .<br>Adobe empfiehlt die Verwendung dieser API für alle Bildformat-Typen. |
| [Weboptimierte binäre Darstellung des Assets](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAsset) | Die bequeme API, die die Standardeinstellungen anwendet, verwendet eine weboptimierte binäre Darstellung des in der Antwort zurückgegebenen Assets. Die Standardeinstellungen umfassen ein standardmäßiges JPEG/WEBP-Format, Qualität => 65 und Breite => 1024. |
| [Ursprünglich hochgeladene Binärdatei des Assets](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetOriginal) | Gibt die ursprünglich hochgeladenen Binärdateien für das Asset zurück. Adobe empfiehlt die Verwendung dieser API für Dokumentformat-Typen und SVG-Bilder. |
| [Vorgenerierte Ausgabe des Assets, das in der AEM Assets-Authoring-Umgebung verfügbar ist](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetRendition) | Gibt den in der AEM Assets-Authoring-Umgebung verfügbaren Bitstream der Asset-Ausgabedarstellung basierend auf der Asset-ID und dem in der Anfrage gesendeten Ausgabedarstellungsnamen zurück. |
| [Asset-Metadaten](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetMetadata) | Gibt die mit einem Asset verknüpften Eigenschaften zurück, z. B. Titel, Beschreibung, CreateDate, ModifyDate usw. |
| [Player-Container für das Video-Asset](https://adobe-aem-assets-delivery.redoc.ly/#operation/videoPlayerDelivery) | Gibt den Player-Container für das Video-Asset zurück. Sie können den Player in ein iFrame-HTML-Element einbetten und das Video abspielen. |
| [Wiedergabe-Manifeste im ausgewählten Ausgabeformat](https://adobe-aem-assets-delivery.redoc.ly/#operation/videoManifestDelivery) | Gibt die Manifestdatei für die Wiedergabe des angegebenen Video-Assets im ausgewählten Ausgabeformat zurück. Sie müssen einen benutzerdefinierten Player erstellen, der das adaptive Streaming über HLS- oder DASH-Protokolle ermöglicht, um die Wiedergabemmanifestdatei abrufen und das Video abspielen zu können. |

## API-Endpunkte für Sendungen {#delivery-apis-endpoint}

Die API-Endpunkte variieren für jede Bereitstellungs-API. Der API-Endpunkt für die API `Web-optimized binary representation of the asset in the requested output format` lautet beispielsweise:
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/{assetId}/as/{seoName}.{format}`

Die Bereitstellungsdomäne ähnelt der Struktur der Domäne der Autorenumgebung des Experience Managers. Der einzige Unterschied besteht darin, den Begriff `author` durch `delivery` zu ersetzen.

`pXXXX` bezeichnet die Programm-ID

`eYYYY` bezeichnet die Umgebungs-ID

Weitere Informationen finden Sie unter [API-Details](https://adobe-aem-assets-delivery.redoc.ly/#tag/Assets) .

## Anfragemethode für Bereitstellungs-APIs {#delivery-api-request-method}

GET

## Kopfzeile der Bereitstellungs-APIs {#deliver-assets-api-header}

Sie müssen beim Definieren eines Headers in der Kopfzeile der Bereitstellungs-APIs die folgenden Details angeben:

```java
headers: {
      'If-None-Match': 'string',
      Authorization: 'Bearer <YOUR_JWT_HERE>'
    }
```

Um die Bereitstellungs-APIs aufzurufen, ist ein IMS-Token in den `Authorization` -Details erforderlich, um ein eingeschränktes Asset bereitzustellen. Das IMS-Token wird aus einem technischen Konto abgerufen. Siehe [Abrufen der AEM as a Cloud Service-Anmeldedaten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) , um ein neues technisches Konto zu erstellen. Siehe [Generieren des Zugriffs-Tokens](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) , um das IMS-Token zu generieren und es im Anforderungsheader der Bereitstellungs-APIs entsprechend zu verwenden.


Informationen zum Anzeigen von Anforderungsbeispielen, Antwortbeispielen und Antwortcodes finden Sie unter [Bereitstellungs-APIs](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat).