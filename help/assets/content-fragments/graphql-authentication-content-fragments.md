---
title: Authentifizierung für Remote AEM GraphQL-Abfragen in Inhaltsfragmenten
description: Erfahren Sie mehr über die erforderliche Authentifizierung für Remote AEM GraphQL-Abfragen.
translation-type: tm+mt
source-git-commit: 42ca0c70f7018a6e3c9be68ef13adefafc987864
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---


# Authentifizierung für Remote AEM GraphQL-Abfragen in Inhaltsfragmenten {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Ein primäres Anwendungsbeispiel für die Grafik-QL-API von [Adobe Experience Manager als Cloud Service (AEM) für Content Fragment Versand](/help/assets/content-fragments/graphql-api-content-fragments.md) ist das Akzeptieren von Remote-Abfragen von Drittanbieteranwendungen oder -diensten.  Für diese Remote-Abfragen ist möglicherweise ein authentifizierter API-Zugriff erforderlich.

>[!NOTE]
>
>Für Tests und Entwicklung können Sie auch direkt über die [GraphiQL Schnittstelle](/help/assets/content-fragments/graphql-api-content-fragments.md#graphiql-interface) auf die AEM GraphQL API zugreifen.

Zur Authentifizierung muss der Drittanbieter-Dienst ein [Zugriffstoken](#access-token) verwenden, das dann [in der GraphQL-Anforderung](#use-access-token-in-graphql-request) verwendet werden kann.

## Abrufen eines Zugriffstokens {#retrieving-access-token}

Ausführliche Informationen finden Sie unter [Generieren von Zugriffstoken für serverseitige APIs](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md).

## Verwenden des Zugriffstokens in einer GraphQL-Anforderung {#use-access-token-in-graphql-request}

Damit ein Drittanbieter-Dienst eine Verbindung mit einer AEM herstellen kann, muss er über ein *Zugriffstoken* verfügen. Der Dienst muss dieses Token dann der `Authorization`-Kopfzeile in der POST-Anforderung hinzufügen.

Beispiel: GraphQL-Autorisierungskopfzeile:

```xml
Authorization: Bearer <access_token>
```

## Berechtigungsanforderungen {#permission-requirements}

Alle Anfragen, die mit dem Zugriffstoken durchgeführt wurden, werden tatsächlich von dem Benutzerkonto ausgeführt, das das Token *generiert hat.*

Dies bedeutet, dass Sie überprüfen müssen, ob das Konto über die erforderlichen Berechtigungen zum Ausführen von GraphQL-Abfragen verfügt.

Sie können dies überprüfen, indem Sie GraphiQL auf der lokalen Instanz verwenden.
