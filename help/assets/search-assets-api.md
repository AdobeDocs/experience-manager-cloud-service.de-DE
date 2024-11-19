---
title: Assets-API durchsuchen
description: Erfahren Sie, wie Sie die Search Assets-API verwenden.
role: User
exl-id: 0c52e793-4c33-4230-b4f2-27296dd9e4b3
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 4%

---

# Assets-API durchsuchen {#search-assets-api}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!AVAILABILITY]
>
>Handbuch zu Dynamic Media mit OpenAPI-Funktionen ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den Adobe Acrobat AI-Assistenten, um Ihre Fragen zu beantworten.
>
>[!BADGE Handbuch für Dynamic Media mit OpenAPI-Funktionen PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Alle im Experience Manager-Asset-Repository verfügbaren [genehmigten Assets](approve-assets.md) können durchsucht und dann mithilfe einer Bereitstellungs-URL an integrierte nachgelagerte Anwendungen gesendet werden.

Die Suche nach den richtigen genehmigten Assets aus dem Experience Manager-Repository ist der erste Schritt zur Bereitstellung von Assets mithilfe der Bereitstellungs-URL. Die Antwort auf die Suchanfrage umfasst ein Array von JSON-Dokumenten, die den Assets entsprechen, die die Suchkriterien erfüllt haben. Jedes JSON-Dokument wird mithilfe eines `id` -Felds identifiziert, das zum Erstellen der Asset-Bereitstellungsanforderung verwendet wird.

![Überblick über das direkte binäre Upload-Protokoll](assets/search-assets-api-overview.png)

Sie können Eigenschaften in der Assets-API-Anfrage &quot;Suchen&quot;definieren, um die folgenden Funktionen zu aktivieren:

* **Volltextsuche**: Verwenden Sie die `match`-Abfrage, um den zu suchenden Text zu definieren.  Sie können auch Operatoren innerhalb der `match` -Abfrage verwenden, um die Ergebnisse zu filtern.

* **Filter anwenden**: Verwenden Sie die `term`-Abfrage, um die Ergebnisse weiter zu filtern, indem Sie einen `key` und einen oder mehrere Werte definieren. `key` gibt das Feld an, dessen Wert abgeglichen werden muss, und `value` gibt an, worauf abgestimmt werden soll. Auf ähnliche Weise können Sie mit der `range` -Abfrage einen Bereich für ein Feld definieren, indem Sie die Eigenschaften Größer als (gt), Größer als oder gleich (get), Kleiner als (lt) und Kleiner als oder gleich (lte) verwenden.

* **Ergebnisse sortieren**: Mit der Eigenschaft `OrderBy` können Sie Suchergebnisse basierend auf einem oder mehreren Feldern sortieren. Sie können die Ergebnisse in auf- oder absteigender Reihenfolge sortieren.

* **Paginierung**: Verwenden Sie die Eigenschaften `limit` und `cursor`, um Paginierungseigenschaften in einer Such-API-Anfrage zu definieren. `limit` -Eigenschaft definiert die maximalen Elemente, die in einer API-Antwort abgerufen werden sollen. Die Eigenschaft `cursor` erleichtert das Abrufen des Startpunkts für den nächsten Satz von Assets, der in der Eigenschaft `limit` definiert ist. Wenn Sie beispielsweise `50` als Grenze in der API-Anfrage definieren, können Sie mit der `cursor` -Eigenschaft die nächsten 50 Elemente mit der nächsten API-Anfrage starten und abrufen.

## Suchen nach Assets-API-Endpunkt {#search-assets-api-endpoint}

Der Endpunkt in einer Anfrage der API zur Suche nach Assets muss das folgende Format aufweisen:
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/search`

Die Bereitstellungsdomäne ähnelt der Struktur der Domäne der Autorenumgebung des Experience Managers. Der einzige Unterschied besteht darin, den Begriff `author` durch `delivery` zu ersetzen.

`pXXXX` bezeichnet die Programm-ID

`eYYYY` bezeichnet die Umgebungs-ID

## Anforderungsmethode der Asset-API {#search-assets-api-request-method}

POST

## Assets API-Kopfzeile durchsuchen {#search-assets-api-header}

Sie müssen beim Definieren eines Headers in der Such-Assets-API die folgenden Details angeben:

```java
headers: {
      'Content-Type': 'application/json',
      'X-Adobe-Accept-Experimental': '1',
      Authorization: 'Bearer <YOUR_JWT_HERE>',
      'X-Api-Key': 'YOUR_API_KEY_HERE'
    },
```

Um die Such-API aufzurufen, ist ein IMS-Token erforderlich, das in den `Authorization` -Details definiert wird. Das IMS-Token wird aus einem technischen Konto abgerufen. Siehe [Abrufen der AEM as a Cloud Service-Anmeldedaten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) , um ein neues technisches Konto zu erstellen. Siehe [Generieren des Zugriffs-Tokens](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) , um das IMS-Token zu generieren und es entsprechend im Anforderungsheader der Asset-API zu verwenden.

Informationen zum Anzeigen von Anforderungsbeispielen, Antwortbeispielen und Antwortcodes finden Sie unter [Assets-API durchsuchen](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/search).
