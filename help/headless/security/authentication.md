---
title: Authentifizierung für AEM-GraphQL-Remote-Abfragen in Inhaltsfragmenten
description: Machen Sie sich mit der Authentifizierung vertraut, die für Adobe Experience Manager-GraphQL-Remote-Abfragen erforderlich ist, um die Bereitstellung von Headless-Inhalten zu sichern.
feature: Headless, Content Fragments,GraphQL API
exl-id: dfeae661-06a1-4001-af24-b52ae12d625f
role: Admin, Developer
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 100%

---

# Authentifizierung für AEM-GraphQL-Remote-Abfragen in Inhaltsfragmenten {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Ein primäres Anwendungsbeispiel für die [GraphQL-API von Adobe Experience Manager as a Cloud Service (AEM) für die Bereitstellung von Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md) ist das Annehmen von Remote-Abfragen von Drittanbieter-Programmen oder -Services. Diese Remote-Abfragen erfordern möglicherweise einen authentifizierten API-Zugriff, um die Bereitstellung von Headless-Inhalten zu sichern.

>[!NOTE]
>
>Für Tests und Entwicklung können Sie auch direkt über die [GraphiQL-Schnittstelle](/help/headless/graphql-api/graphiql-ide.md) auf die AEM GraphQL-API zugreifen.

Zur Authentifizierung muss der Drittanbieter-Service ein [Zugriffs-Token](#retrieving-access-token) abrufen, das dann [in der GraphQL-Anfrage](#use-access-token-in-graphql-request) verwendet werden kann.

## Abrufen eines Zugriffs-Tokens {#retrieving-access-token}

Ausführliche Informationen finden Sie unter [Generieren von Zugriffs-Token für Server-seitige APIs](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md).

## Verwenden des Zugriffs-Tokens in einer GraphQL-Anfrage {#use-access-token-in-graphql-request}

Damit ein Drittanbieter-Service eine Verbindung mit einer AEM-Instanz herstellen kann, benötigt er ein *Zugriffs-Token*. Der Service muss dieses Token dann der `Authorization`-Kopfzeile in der POST-Anfrage hinzufügen.

Ein Beispiel für eine GraphQL-Autorisierungskopfzeile:

```xml
Authorization: Bearer <access_token>
```

## Berechtigungsanforderungen {#permission-requirements}

Alle Anfragen, die mit dem Zugriffs-Token durchgeführt werden, werden *von dem Benutzerkonto ausgeführt, das das Token generiert hat*.

Dieses Benutzerkonto bedeutet, dass Sie überprüfen müssen, ob das Konto über die erforderlichen Berechtigungen zur Ausführung von GraphQL-Abfragen verfügt.

Sie können diese Berechtigungen mit GraphiQL auf der lokalen Instanz überprüfen. Weitere Informationen finden Sie unter [Überlegungen zu Berechtigungen für Headless-Inhalte](/help/headless/security/permissions.md).
