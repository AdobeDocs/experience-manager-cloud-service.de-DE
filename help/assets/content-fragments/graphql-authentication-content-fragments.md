---
title: Authentifizierung für AEM GraphQL-Remote-Abfragen in Inhaltsfragmenten
description: Verstehen Sie die erforderliche Authentifizierung für Remote AEM GraphQL-Abfragen, um Ihren kopflosen Content Versand zu sichern.
feature: Inhaltsfragmente, GraphQL-API
exl-id: dfeae661-06a1-4001-af24-b52ae12d625f
translation-type: tm+mt
source-git-commit: dab4c9393c26f5c3473e96fa96bf7ec51e81c6c5
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 75%

---

# Authentifizierung für AEM GraphQL-Remote-Abfragen in Inhaltsfragmenten {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Ein primäres Anwendungsbeispiel für die [GraphQL-API von Adobe Experience Manager as a Cloud Service (AEM) für die Bereitstellung von Inhaltsfragmenten](/help/assets/content-fragments/graphql-api-content-fragments.md) ist das Annehmen von Remote-Abfragen von Drittanbieter-Programmen oder -Services. Diese Remote-Abfragen erfordern möglicherweise einen authentifizierten API-Zugriff, um den Versand von kostenlosen Inhalten zu sichern.

>[!NOTE]
>
>Für Tests und Entwicklung können Sie auch direkt über die [GraphiQL-Schnittstelle](/help/assets/content-fragments/graphql-api-content-fragments.md#graphiql-interface) auf die AEM GraphQL-API zugreifen.

Zur Authentifizierung muss der Drittanbieter-Dienst [ein Zugriffstoken](#retrieving-access-token) abrufen, das dann [in der GraphQL-Anforderung](#use-access-token-in-graphql-request) verwendet werden kann.

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
