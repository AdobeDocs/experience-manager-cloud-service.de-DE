---
title: Assets-API durchsuchen
description: Erfahren Sie, wie Sie die Search Assets-API verwenden.
role: User
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 1%

---

# Assets-API durchsuchen {#search-assets-api}

Alle [genehmigte Assets](approved-assets.md) , die im Experience Manager-Assets-Repository verfügbar sind, können durchsucht und dann mithilfe einer Bereitstellungs-URL an integrierte nachgelagerte Anwendungen gesendet werden.

Die Suche nach den richtigen genehmigten Assets aus dem Experience Manager-Repository ist der erste Schritt zur Bereitstellung von Assets mithilfe der Bereitstellungs-URL. Die Antwort auf die Suchanfrage umfasst ein Array von JSON-Dokumenten, die den Assets entsprechen, die die Suchkriterien erfüllt haben. Jedes JSON-Dokument wird mithilfe eines `id` -Feld, das zum Erstellen der Asset-Bereitstellungsanforderung verwendet wird.

![Überblick über das direkte binäre Upload-Protokoll](assets/search-assets-api-overview.png)

Sie können Eigenschaften in der Anfrage der Search Assets API definieren, um die folgenden Funktionen zu aktivieren:

* **Volltextsuche**: Verwenden Sie die `match` abfragen, um den zu suchenden Text zu definieren.  Sie können auch Operatoren innerhalb der `match` Abfrage zum Filtern der Ergebnisse.

* **Filter anwenden**: Verwenden Sie die `term` Abfrage zum Filtern der Ergebnisse durch Definition einer `key` und einen oder mehrere Werte. `key` gibt das Feld an, dessen Wert übereinstimmen muss, und `value` steht für die Übereinstimmung. Auf ähnliche Weise können Sie die `range` Abfrage zum Definieren eines Bereichs für ein Feld mithilfe der Eigenschaften Größer als (gt), Größer als oder gleich (get), Kleiner als (lt) und Kleiner als oder Gleich (lte).

* **Ergebnisse sortieren**: Verwenden Sie die `OrderBy` -Eigenschaft zum Sortieren der Suchergebnisse anhand eines oder mehrerer Felder. Sie können die Ergebnisse in auf- oder absteigender Reihenfolge sortieren.

* **Paginierung**: Verwenden Sie die `limit` und `cursor` Eigenschaften zum Definieren von Paginierungseigenschaften in einer Such-API-Anfrage. `limit` -Eigenschaft definiert die maximalen Elemente, die in einer API-Antwort abgerufen werden sollen. `cursor` -Eigenschaft ermöglicht das Abrufen des Startpunkts für den nächsten Satz von Assets, der in der `limit` -Eigenschaft. Wenn Sie beispielsweise `50` als Begrenzung in der API-Anfrage verwenden, können Sie die `cursor` -Eigenschaft zum Starten und Abrufen der nächsten 50 Elemente mithilfe der nächsten API-Anfrage.

## Suchen nach Assets-API-Endpunkt {#search-assets-api-endpoint}

Der Endpunkt in einer Anfrage der API zur Suche nach Assets muss das folgende Format aufweisen:
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/search`

Die Bereitstellungsdomäne ähnelt der Struktur der Domäne der Autorenumgebung des Experience Managers. Der einzige Unterschied besteht darin, den Begriff zu ersetzen `author` mit `delivery`.

`pXXXX` bezieht sich auf die Programm-ID

`eYYYY` bezieht sich auf die Umgebungs-ID

## Anforderungsmethode der Asset-API {#search-assets-api-request-method}

POST

## API-Kopfzeile für die Suche nach Assets {#search-assets-api-header}

Sie müssen beim Definieren eines Headers in der Such-Assets-API die folgenden Details angeben:

```java
headers: {
      'Content-Type': 'application/json',
      'X-Adobe-Accept-Experimental': '1',
      Authorization: 'Bearer <YOUR_JWT_HERE>',
      'X-Api-Key': 'YOUR_API_KEY_HERE'
    },
```

Um die Such-API aufzurufen, ist ein IMS-Token erforderlich, das im `Authorization` Details. Das IMS-Token wird aus einem technischen Konto abgerufen. Siehe [Abrufen der AEM as a Cloud Service Anmeldedaten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) , um ein neues technisches Konto zu erstellen. Siehe [Zugriffstoken erstellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) , um das IMS-Token zu generieren und es in der Anforderungsheader der API für die Suche nach Assets entsprechend zu verwenden.

Informationen zum Anzeigen von Anforderungsbeispielen, Antwortbeispielen und Antwortcodes finden Sie unter [Assets-API durchsuchen](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/search).

