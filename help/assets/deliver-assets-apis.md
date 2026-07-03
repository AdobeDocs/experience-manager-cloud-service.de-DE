---
title: Bereitstellungs-APIs
description: Erfahren Sie, wie Sie die Bereitstellungs-APIs verwenden.
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
exl-id: 806ca38f-2323-4335-bfd8-a6c79f6f15fb
source-git-commit: fa93e2079ad5a2840b5e58c5b83cb288606bda97
workflow-type: tm+mt
source-wordcount: '1879'
ht-degree: 43%

---

# Bereitstellungs-APIs {#delivery-apis}

Alle [genehmigten Assets](approve-assets.md), die im Experience Manager-Asset-Repository verfügbar sind, können [durchsucht](search-assets-api.md) und anschließend mithilfe einer Bereitstellungs-URL an integrierte nachgelagerte Anwendungen gesendet werden.

Alle Änderungen an genehmigten Assets in DAM, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden automatisch in die Bereitstellungs-URLs übernommen. Mit einem niedrigen Time-to-Live(TTL)-Wert von 10 Minuten für die Bereitstellung von Assets per CDN werden Aktualisierungen in weniger als 10 Minuten in allen Authoring- und Publishing-Oberflächen sichtbar.

Die folgende Abbildung zeigt die verfügbaren Bereitstellungs-URLs:

![Bereitstellungs-APIs](assets/delivery-url.png)

Die folgende Tabelle zeigt die Verwendung der verschiedenen verfügbaren Bereitstellungs-APIs:

| Bereitstellungs-API | Beschreibung |
|---|---|
| [Web-optimierte binäre Darstellung des Assets im angeforderten Ausgabeformat](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat) | Gibt die Web-optimierte binäre Darstellung des Assets im angeforderten Ausgabeformat basierend auf der in der Anfrage gesendeten Asset-ID zurück. Darüber hinaus können Sie verschiedene Bildmodifikatoren definieren, z. B. Breite, Höhe, Drehung, Spiegelung, Qualität, Zuschnitt, Format und [intelligenter Zuschnitt](/help/assets/dynamic-media/image-profiles.md). Informationen zu unterstützten Formaten und Bildmodifikatoren finden Sie unter [API-Details](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat).<br>Adobe empfiehlt die Verwendung dieser API für alle Bildformattypen. |
| [Web-optimierte binäre Darstellung des Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAsset) | Convenience-API, die die Standardeinstellungen auf eine Web-optimierte binäre Darstellung des in der Antwort zurückgegebenen Assets anwendet. Die Standardeinstellungen sehen ein standardmäßiges JPEG/WEBP-Format, einen Qualitätswert von 65 und einen Breitenwert von 1024 vor. |
| [Ursprünglich hochgeladene Binärdatei des Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetOriginal) | Gibt die ursprünglich hochgeladenen Binärdateien für das Asset zurück. Adobe empfiehlt die Verwendung dieser API für Dokumentformattypen und SVG-Bilder. |
| [Vorgenerierte Ausgabedarstellung des Assets, das in der AEM Assets-Authoring-Umgebung verfügbar ist](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetRendition) | Gibt den in der AEM Assets-Authoring-Umgebung verfügbaren Bitstream der Asset-Ausgabedarstellung basierend auf der Asset-ID und dem Namen der Ausgabedarstellung zurück, die beide in der Anfrage gesendet wurden. |
| [Asset-Metadaten](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetMetadata) | Gibt die mit einem Asset verknüpften Eigenschaften zurück, z. B. Titel, Beschreibung, Erstellungsdatum, Änderungsdatum usw. |
| [Player-Container für das Video-Asset](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/videoPlayerDelivery) | Gibt den Player-Container für das Video-Asset zurück. Sie können den Player in ein iFrame-HTML-Element einbetten und das Video abspielen. |
| [Wiedergabe-Manifeste im ausgewählten Ausgabeformat](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/videoManifestDelivery) | Gibt die Wiedergabe-Manifestdatei für das angegebene Video-Asset im ausgewählten Ausgabeformat zurück. Sie müssen einen benutzerdefinierten Player erstellen, der adaptives Streaming über HLS- oder DASH-Protokolle ermöglicht, um die Wiedergabe-Manifestdatei abzurufen und das Video abzuspielen. |

>[!IMPORTANT]
>
>Sie können jeden Modifikator testen, der nicht allgemein über experimentelle APIs verfügbar ist. Zum Beispiel: Klicken Sie hier, um mehr über die Verwendung der [experimentellen APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/#experimental-apis) zu erfahren und die [vollständige Liste der Modifikatoren](https://developer.adobe.com/experience-cloud/experience-manager-apis/) anzuzeigen.

Dynamic Media mit OpenAPI-Funktionen unterstützt auch langformatige Videos. Es werden Videos mit bis zu 50 GB und einer Länge von bis zu 2 Stunden unterstützt.

Informationen zu den verfügbaren Dynamic Media-Angeboten und deren Funktionen finden Sie unter [Dynamic Media Prime und Ultimate](/help/assets/dynamic-media/dm-prime-ultimate.md).

>[!NOTE]
>
>Kundinnen und Kunden von DM Prime können grundlegende Bildmodifikatoren verwenden, einschließlich Drehen, Zuschneiden, Spiegeln, Höhe, Breite und Qualität. Die intelligente Bildbearbeitung unterstützt AVIF für Kundinnen und Kunden von DM Prime nicht.

## Bereitstellungs-API-Endpunkte {#delivery-apis-endpoint}

Die API-Endpunkte variieren je nach Bereitstellungs-API. Der API-Endpunkt für `Web-optimized binary representation of the asset in the requested output format` API lautet beispielsweise:

Die Bereitstellungs-Domain ähnelt der Struktur der Domain der Autorenumgebung von Experience Manager. Der einzige Unterschied ist das Ersetzen des Begriffs `author` durch `delivery`.

`pXXXX` bezeichnet die Programm-ID

`eYYYY` bezeichnet die Umgebungs-ID

Weitere Informationen finden Sie unter [API-Details](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#tag/Assets).

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

Zum Aufrufen der Bereitstellungs-APIs ist ein IMS-Token in den `Authorization`-Details erforderlich, um ein eingeschränktes Asset bereitzustellen. Das IMS-Token wird aus einem technischen Konto abgerufen. Informationen zum Erstellen eines neuen technischen Kontos finden Sie unter [Abrufen der Anmeldedaten für AEM as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis). Informationen zum Generieren des IMS-Tokens und zu seiner entsprechenden Verwendung im Anfrage-Header der Bereitstellungs-APIs finden Sie unter [Generieren des Zugriffs-Tokens](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis).


Informationen zum Anzeigen von Anfragebeispielen, Antwortbeispielen und Antwort-Codes finden Sie unter [Bereitstellungs-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat).

## Häufig gestellte Fragen {#delivery-apis-faqs}

### Was sind die Dynamic Media-APIs mit OpenAPI-Bereitstellungs-APIs und was aktivieren sie? {#delivery-apis-overview}

Die Dynamic Media-API mit OpenAPI-Bereitstellungs-APIs ermöglichen es, in Adobe Experience Manager Assets gespeicherte genehmigte Assets über eine Bereitstellungs-URL an integrierte nachgelagerte Anwendungen bereitzustellen. Es sind sieben verschiedene APIs verfügbar, die die Bildbereitstellung, die ursprüngliche Binärbereitstellung, die Bereitstellung vorgenerierter Ausgabedarstellungen, den Abruf von Asset-Metadaten, die Einbettung in den Video-Player und die Bereitstellung von Videowiedergabemanifesten abdecken. Alle Änderungen an genehmigten Assets in DAM, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden automatisch in den Bereitstellungs-URLs angezeigt, ohne dass die Assets erneut veröffentlicht oder manuell bearbeitet werden müssen.

### Wie schnell werden Asset-Aktualisierungen in Bereitstellungs-APIs nach Änderungen in AEM Assets angezeigt? {#delivery-api-ttl-updates}

Aktualisierungen genehmigter Assets in AEM Assets sind in weniger als 10 Minuten auf allen Authoring- und Veröffentlichungsoberflächen sichtbar. Dynamic Media mit OpenAPI-Bereitstellungs-APIs verwendet einen kurzen Time-to-Live-Wert von 10 Minuten, der für die Asset-Bereitstellung über CDN konfiguriert ist. Dies bedeutet, dass Versionsaktualisierungen, Metadatenänderungen und andere Änderungen an genehmigten Assets im DAM innerhalb von 10 Minuten automatisch an Bereitstellungs-URLs weitergegeben werden, ohne dass der Cache manuell invalidiert werden muss.

### Welche Bereitstellungs-API sollte ich für die Bereitstellung von Bild-Assets verwenden? {#delivery-api-image-recommendation}

Die Web-optimierte binäre Darstellung des Assets im angeforderten Ausgabeformat-API ist die empfohlene API für alle Bildformattypen. Diese API gibt die Web-optimierte Binärdarstellung des Assets im angeforderten Ausgabeformat basierend auf der in der Anfrage gesendeten Asset-ID zurück. Es unterstützt verschiedene Bildmodifikatoren wie Breite, Höhe, Drehen, Spiegeln, Qualität, Zuschneiden, Format und smartes Zuschneiden. Für Dokumentformattypen und SVG-Bilder wird stattdessen die ursprünglich hochgeladene Binärdatei der Asset-API empfohlen.

### Welche Bildmodifikatoren werden von der Web-optimierten Bereitstellungs-API für binäre Darstellungen unterstützt? {#delivery-api-image-modifiers}

Die Web-optimierte binäre Darstellung des Assets im angeforderten Ausgabeformat-API unterstützt Bildmodifikatoren wie Breite, Höhe, Drehen, Spiegeln, Qualität, Zuschneiden, Format und smartes Zuschneiden. Diese Modifikatoren können als Parameter in der Versand-URL-Anfrage definiert werden, um das Asset zum Zeitpunkt der Bereitstellung umzuwandeln, ohne das in AEM Assets gespeicherte Original-Asset zu ändern.

### Was gibt die praktische Web-optimierte Bereitstellungs-API für Binärdarstellungen standardmäßig zurück? {#delivery-api-defaults}

Die praktische, Web-optimierte Binärdarstellung der Asset-API gilt standardmäßig für das in der Antwort zurückgegebene Asset. Die Standardwerte sind das JPEG- oder WEBP-Format, eine Qualität von 65 und eine Breite von 1024 Pixel. Diese API ist geeignet, wenn kein bestimmtes Ausgabeformat oder keine Modifikatorsteuerung erforderlich ist und eine standardmäßige Web-optimierte Ausgabedarstellung für die nachgelagerte Anwendung ausreicht.

### Welche Bereitstellungs-API sollte ich für Dokumente und SVG-Bilder verwenden? {#delivery-api-documents-svg}

Die ursprünglich hochgeladene Binärdatei der Asset-API ist die empfohlene API für Dokumentformattypen und SVG-Bilder. Diese API gibt die ursprünglich hochgeladene Binärdatei für das Asset zurück, ohne Web-Optimierungstransformationen anzuwenden. Für alle anderen Bildformattypen wird die Web-optimierte binäre Darstellungs-API im angeforderten Ausgabeformat empfohlen.

### Wie rufe ich vorgenerierte Ausgabedarstellungen eines Assets mithilfe der Bereitstellungs-APIs ab? {#delivery-api-pre-generated-renditions}

Die vorgenerierte Ausgabedarstellung des Assets, die in der Authoring-Umgebungs-API von AEM Assets verfügbar ist, gibt den Bitstream einer bestimmten Ausgabedarstellung basierend auf der Asset-ID und dem Ausgabedarstellungsnamen zurück, die in der Anfrage gesendet wurden. Die Ausgabedarstellung muss bereits in der AEM Assets-Autorenumgebung vorhanden sein, bevor sie mit dieser API abgerufen werden kann. Diese API unterscheidet sich von der Web-optimierten binären API, die die Ausgabe bei Bedarf mithilfe von Bildmodifikatoren erzeugt.

### Wie bette ich ein Video-Asset ein und spiele es mit den Bereitstellungs-APIs ab? {#delivery-api-video-player}

Der Player-Container für die Video-Asset-API gibt einen Player-Container für ein Video-Asset zurück, das in ein iFrame-HTML-Element eingebettet werden kann, um die Wiedergabe von Videos auf der Seite zu aktivieren. Bei Szenarien, in denen benutzerdefinierte Player-Implementierungen mit adaptivem Streaming erforderlich sind, gibt das Wiedergabemanifest in der ausgewählten Ausgabeformat-API die Wiedergabemanifestdatei für das angegebene Video-Asset im HLS- oder DASH-Format zurück. Es muss ein benutzerdefinierter Player erstellt werden, der adaptives Streaming über HLS- oder DASH-Protokolle ermöglicht, um die Manifestdatei zu nutzen und das Video abzuspielen.

### Welche maximale Größe und Dauer von Videodateien wird von Dynamic Media mit OpenAPI-Bereitstellungs-APIs unterstützt? {#delivery-api-video-limits}

Dynamic Media mit OpenAPI-Bereitstellungs-APIs unterstützen Videos in Langform mit einer Dateigröße von bis zu 50 GB und einer Dauer von bis zu 2 Stunden. Diese Beschränkungen gelten für Video-Assets, die über den Player-Container und die Bereitstellungs-APIs für Wiedergabe-Manifeste bereitgestellt werden.

### Wie ist die URL des Bereitstellungs-API-Endpunkts strukturiert? {#delivery-api-endpoint-structure}

Die Bereitstellungs-API-Endpunkt-URL für die Web-optimierte Binärdarstellung im angeforderten Ausgabeformat folgt dieser Struktur: https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/{assetId}/as/{seoName}.{format}. Die Bereitstellungs-Domain ist ähnlich wie die Domain der AEM-Autorenumgebung strukturiert - der einzige Unterschied besteht darin, den Begriff „Autor“ durch „Versand“ zu ersetzen. In der URL bezieht sich pXXXX auf die Programm-ID und eJJJJ auf die Umgebungs-ID. Alle Bereitstellungs-APIs verwenden die HTTP-GET-Anfragemethode.

### Welche Authentifizierung ist erforderlich, um Dynamic Media mit OpenAPI-Bereitstellungs-APIs aufzurufen? {#delivery-api-authentication}

Der Aufruf von Dynamic Media mit OpenAPI-Bereitstellungs-APIs erfordert ein IMS-Token in der Autorisierungs-Kopfzeile, um eingeschränkte Assets bereitzustellen. Die Kopfzeile muss zwei Felder enthalten: Wenn-keine-Übereinstimmung als Zeichenfolgenwert und Autorisierung als Bearer-Token, das das IMS-Token enthält. Das IMS-Token wird aus einem technischen Konto abgerufen, das mithilfe des Workflows AEM as a Cloud Service-Anmeldeinformationen erstellt wurde. Das technische Konto muss eingerichtet und das Zugriffstoken muss generiert werden, bevor eine Bereitstellungs-API aufgerufen wird.

### Was sind experimentelle Bereitstellungs-APIs und wie greife ich auf sie zu? {#delivery-api-experimental}

Experimentelle Bereitstellungs-APIs ermöglichen das Testen von Bildmodifikatoren, die noch nicht allgemein verfügbar sind. Der Zugriff auf experimentelle APIs erfolgt über ein URL-Pfadformat, das den Modifikator und ein Ablaufdatum enthält - zum Beispiel: /adobe/experimental/advancemodifiers-expires-YYYMMDD/assets. Die vollständige Liste der verfügbaren experimentellen Modifikatoren ist in Adobe Developer Console dokumentiert. Experimentelle APIs dienen Testzwecken und können vor der allgemeinen Verfügbarkeit geändert werden.

### Welche Bildmodifikatorfunktionen sind für Kunden von Dynamic Media Prime im Vergleich zu Dynamic Media Ultimate verfügbar? {#delivery-api-prime-vs-ultimate-modifiers}

Kunden von Dynamic Media Prime können über die Bereitstellungs-APIs grundlegende Bildmodifikatoren wie Drehen, Zuschneiden, Spiegeln, Höhe, Breite und Qualität verwenden. Die intelligente Bildbearbeitung ist für Kunden von Dynamic Media Prime verfügbar, mit dem Unterschied, dass das AVIF-Format für die intelligente Bildbearbeitung in Dynamic Media Prime nicht unterstützt wird. Kunden von Dynamic Media Ultimate haben Zugriff auf alle Bildmodifikatoren und Funktionen der intelligenten Bildbearbeitung, einschließlich Unterstützung des AVIF-Formats.