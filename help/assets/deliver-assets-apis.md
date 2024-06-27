---
title: Bereitstellungs-APIs
description: Erfahren Sie, wie Sie die Bereitstellungs-APIs verwenden.
role: User
source-git-commit: 3e2fe458460fe8ec4c1dd12152c1134bfb9ca62b
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# Bereitstellungs-APIs {#delivery-apis}

Alle [genehmigte Assets](approve-assets.md) im Experience Manager Assets-Repository verfügbar sein. [durchsucht](search-assets-api.md) und anschließend mithilfe einer Bereitstellungs-URL an integrierte nachgelagerte Anwendungen gesendet werden.

Alle Änderungen an genehmigten Assets in DAM, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden automatisch in die Bereitstellungs-URLs übernommen. Mit einem kurzen TTL-Wert (Time-to-Live) von 10 Minuten, der für die Bereitstellung von Assets über CDN konfiguriert ist, werden Aktualisierungen in weniger als 10 Minuten auf allen Authoring- und veröffentlichten Schnittstellen sichtbar.

Die folgende Abbildung zeigt die verfügbaren Versand-URLs:

![Bereitstellungs-APIs](assets/delivery-url.png)

Die folgende Tabelle zeigt die Verwendung der verschiedenen verfügbaren Bereitstellungs-APIs:

| Bereitstellungs-API | Beschreibung |
|---|---|
| [Weboptimierte binäre Darstellung des Assets im angeforderten Ausgabeformat](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetSeoFormat) | Gibt die weboptimierte binäre Darstellung des Assets im angeforderten Ausgabeformat basierend auf der in der Anfrage gesendeten Asset-ID zurück. Darüber hinaus können Sie verschiedene Bildmodifikatoren definieren, z. B. Breite, Höhe, Rotation, Spiegeln, Qualität, Zuschneiden, Format und [Smartes Zuschneiden](/help/assets/dynamic-media/image-profiles.md). Siehe [API-Details](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetSeoFormat) für unterstützte Formate und Bild-Modifikatoren.<br>Adobe empfiehlt die Verwendung dieser API für alle Bildformat-Typen. |
| [Weboptimierte binäre Darstellung des Assets](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAsset) | Die bequeme API, die die Standardeinstellungen anwendet, verwendet eine weboptimierte binäre Darstellung des in der Antwort zurückgegebenen Assets. Die Standardeinstellungen umfassen ein standardmäßiges JPEG/WEBP-Format, Qualität => 65 und Breite => 1024. |
| [Ursprünglich hochgeladene Binärdatei des Assets](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetOriginal) | Gibt die ursprünglich hochgeladenen Binärdateien für das Asset zurück. Adobe empfiehlt die Verwendung dieser API für Dokumentformat-Typen und SVG-Bilder. |
| [Vorgenerierte Ausgabe des Assets, das in der AEM Assets-Authoring-Umgebung verfügbar ist](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetRendition) | Gibt den in der AEM Assets-Authoring-Umgebung verfügbaren Bitstream der Asset-Ausgabedarstellung basierend auf der Asset-ID und dem in der Anfrage gesendeten Ausgabedarstellungsnamen zurück. |
| [Asset-Metadaten](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetMetadata) | Gibt die mit einem Asset verknüpften Eigenschaften zurück, z. B. Titel, Beschreibung, CreateDate, ModifyDate usw. |
| [Player-Container für das Video-Asset](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/videoPlayerDelivery) | Gibt den Player-Container für das Video-Asset zurück. Sie können den Player in ein iFrame-HTML-Element einbetten und das Video abspielen. |
| [Wiedergabe-Manifeste im ausgewählten Format](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/videoManifestDelivery) | Gibt die Manifestdatei für die Wiedergabe des angegebenen Video-Assets im ausgewählten Ausgabeformat zurück. Sie müssen einen benutzerdefinierten Player erstellen, der das adaptive Streaming über HLS- oder DASH-Protokolle ermöglicht, um die Wiedergabemmanifestdatei abrufen und das Video abspielen zu können. |

## API-Endpunkte für Sendungen {#delivery-apis-endpoint}

Die API-Endpunkte variieren für jede Bereitstellungs-API. Beispielsweise der API-Endpunkt für `Web-optimized binary representation of the asset in the requested output format` Die API lautet:
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/{assetId}/as/{seoName}.{format}`

Die Bereitstellungsdomäne ähnelt der Struktur der Domäne der Autorenumgebung des Experience Managers. Der einzige Unterschied besteht darin, den Begriff zu ersetzen `author` mit `delivery`.

`pXXXX` bezieht sich auf die Programm-ID

`eYYYY` bezieht sich auf die Umgebungs-ID

Siehe [API-Details](https://adobe-aem-assets-delivery-experimental.redoc.ly/#tag/Assets) für weitere Informationen.

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

Um die Bereitstellungs-APIs aufzurufen, ist ein IMS-Token im `Authorization` Details zum Bereitstellen eines eingeschränkten Assets. Das IMS-Token wird aus einem technischen Konto abgerufen. Siehe [Abrufen der AEM as a Cloud Service-Anmeldeinformationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) , um ein neues technisches Konto zu erstellen. Siehe [Zugriffstoken erstellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) , um das IMS-Token zu generieren und es in der Anfrage-Kopfzeile der Bereitstellungs-APIs entsprechend zu verwenden.

Informationen zum Anzeigen von Anforderungsbeispielen, Antwortbeispielen und Antwortcodes finden Sie unter [Bereitstellungs-APIs](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetSeoFormat).
