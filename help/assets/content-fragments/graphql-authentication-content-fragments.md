---
title: Authentifizierung für AEM GraphQL-Remote-Abfragen in Inhaltsfragmenten
description: Erfahren Sie mehr über die erforderliche Authentifizierung für AEM GraphQL-Remote-Abfragen.
translation-type: tm+mt
source-git-commit: 42ca0c70f7018a6e3c9be68ef13adefafc987864
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 100%

---


# Authentifizierung für AEM GraphQL-Remote-Abfragen in Inhaltsfragmenten {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Ein primäres Anwendungsbeispiel für die [GraphQL-API von Adobe Experience Manager as a Cloud Service (AEM) für die Bereitstellung von Inhaltsfragmenten](/help/assets/content-fragments/graphql-api-content-fragments.md) ist das Annehmen von Remote-Abfragen von Drittanbieter-Programmen oder -Services.  Für diese Remote-Abfragen ist möglicherweise ein authentifizierter API-Zugriff erforderlich.

>[!NOTE]
>
>Für Tests und Entwicklung können Sie auch direkt über die [GraphiQL-Schnittstelle](/help/assets/content-fragments/graphql-api-content-fragments.md#graphiql-interface) auf die AEM GraphQL-API zugreifen.

Zur Authentifizierung muss der Drittanbieter-Service ein [Zugriffs-Token](#access-token) verwenden, das dann [in der GraphQL-Anfrage](#use-access-token-in-graphql-request) verwendet werden kann.

## Abrufen eines Zugriffs-Tokens {#retrieving-access-token}

Ausführliche Informationen finden Sie unter [Generieren von Zugriffs-Token für Server-seitige APIs](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md).

## Verwenden des Zugriffs-Tokens in einer GraphQL-Anfrage {#use-access-token-in-graphql-request}

Damit ein Drittanbieter-Service eine Verbindung mit einer AEM-Instanz herstellen kann, benötigt er ein *Zugriffs-Token*. Der Service muss dieses Token dann der `Authorization`-Kopfzeile in der POST-Anfrage hinzufügen.

Ein Beispiel für eine GraphQL-Autorisierungskopfzeile:

```xml
Authorization: Bearer <access_token>
```

## Berechtigungsanforderungen {#permission-requirements}

Alle Anfragen, die mit dem Zugriffs-Token durchgeführt werden, werden tatsächlich *von dem Benutzerkonto ausgeführt, das das Token generiert hat*

Dies bedeutet, dass Sie überprüfen müssen, ob das Konto über die erforderlichen Berechtigungen zum Ausführen von GraphQL-Abfragen verfügt.

Sie können dies überprüfen, indem Sie GraphiQL auf der lokalen Instanz verwenden.
