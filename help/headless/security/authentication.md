---
title: Authentifizierung für AEM-GraphQL-Remote-Abfragen in Inhaltsfragmenten
description: Machen Sie sich mit der Authentifizierung vertraut, die für Remote Adobe Experience Manager GraphQL-Abfragen erforderlich ist, um die Bereitstellung Headless Content zu sichern.
feature: Content Fragments,GraphQL API
exl-id: dfeae661-06a1-4001-af24-b52ae12d625f
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 26%

---

# Authentifizierung für AEM-GraphQL-Remote-Abfragen in Inhaltsfragmenten {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Ein primärer Anwendungsfall für die [Adobe Experience Manager as a Cloud Service (AEM) GraphQL-API für die Bereitstellung von Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md) bedeutet, Remote-Abfragen von Drittanbieteranwendungen oder -diensten zu akzeptieren. Für diese Remote-Abfragen ist möglicherweise ein authentifizierter API-Zugriff erforderlich, um eine sichere, Headless-Content-Bereitstellung zu gewährleisten.

>[!NOTE]
>
>Zum Testen und Entwickeln können Sie auch direkt über die AEM GraphQL-API auf die [GraphiQL-Benutzeroberfläche](/help/headless/graphql-api/graphiql-ide.md).

Für die Authentifizierung muss der Drittanbieterdienst [Zugriffstoken abrufen](#retrieving-access-token) kann [in der GraphQL-Anforderung verwendet](#use-access-token-in-graphql-request).

## Abrufen eines Zugriffs-Tokens {#retrieving-access-token}

Siehe [Generieren von Zugriffstoken für serverseitige APIs](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) für ausführliche Informationen.

## Verwenden des Zugriffs-Tokens in einer GraphQL-Anfrage {#use-access-token-in-graphql-request}

Damit ein Drittanbieterdienst eine Verbindung mit einer AEM-Instanz herstellen kann, muss er über eine *Zugriffstoken*. Der Service muss dieses Token dann der `Authorization`-Kopfzeile in der POST-Anfrage hinzufügen.

Ein Beispiel für eine GraphQL-Autorisierungskopfzeile:

```xml
Authorization: Bearer <access_token>
```

## Berechtigungsanforderungen {#permission-requirements}

Alle Anfragen, die mithilfe des Zugriffstokens gestellt werden, werden ausgeführt *durch das Benutzerkonto, das das Token generiert hat*.

Dieses Benutzerkonto bedeutet, dass Sie überprüfen müssen, ob das Konto über die erforderlichen Berechtigungen zum Ausführen von GraphQL-Abfragen verfügt.

Sie können diese Berechtigungen mithilfe von GraphiQL in der lokalen Instanz überprüfen. Weitere Informationen über [Berechtigungen finden Sie hier](/help/headless/security/permissions.md).
