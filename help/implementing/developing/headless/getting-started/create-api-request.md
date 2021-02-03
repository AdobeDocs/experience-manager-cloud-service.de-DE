---
title: Zugriff und Bereitstellung von Inhaltsfragmenten - Kurzanleitung ohne Beginn
description: Die Assets REST API ermöglicht die Verwaltung von Inhaltsfragmenten und die GraphQL API ermöglicht einen einfachen, kopflosen Versand von Inhaltsfragmentinhalten.
translation-type: tm+mt
source-git-commit: 472f691cf8b2ec502611ee88bc4abdcabb6d8412
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 1%

---


# Zugriff auf und Bereitstellung von Inhaltsfragmenten - Kurzanleitung {#accessing-delivering-content-fragments} ohne Beginn

Die Assets REST API ermöglicht die Verwaltung von Inhaltsfragmenten und die GraphQL API ermöglicht einen einfachen, kopflosen Versand von Inhaltsfragmentinhalten.

## Was sind GraphQL und Assets REST APIs? {#what-are-the-apis}

[Nachdem Sie jetzt einige Inhaltsfragmente erstellt haben, können ](create-content-fragment.md) Sie AEM APIs verwenden, um sie kopfüber bereitzustellen.

* [Mit der GraphQL-](/help/assets/content-fragments/graphql-api-content-fragments.md) API können Sie Anforderungen für den Zugriff auf und die Bereitstellung von Inhaltsfragmenten erstellen.
* [Mit der REST-](/help/assets/content-fragments/assets-api-content-fragments.md) API für Assets können Sie Inhaltsfragmente (und andere Assets) erstellen und ändern.

Der Rest dieses Handbuchs konzentriert sich auf GraphQL-Zugriff und Content Fragment Versand.

## Bereitstellen eines Inhaltsfragments mit GraphQL {#how-to-deliver-a-content-fragment}

Informationsarchitekten müssen Abfragen für ihre Kanal-Endpunkte entwerfen, um Inhalte bereitstellen zu können. Diese Abfragen müssen in der Regel nur einmal pro Endpunkt pro Modell berücksichtigt werden. Für die Zwecke dieses Beginns-Leitfadens müssen wir nur einen erstellen.

<!-- Not in the UI yet - will need updating when it is -->
<!--
1. Log into AEM as a Cloud Service and from the main menu select **Tools -&gt; Assets -&gt; GraphQL** 
   * Alternatively open the page directly at `https://<host>:<port>/content/graphiql.html`.
-->

1. Melden Sie sich bei AEM als Cloud Service an und greifen Sie auf die GraphiQL-Oberfläche zu:
   * Beispiel: `https://<host>:<port>/content/graphiql.html`.

1. GraphiQL ist ein In-Browser-Abfrage-Editor für GraphQL. Sie können damit Abfragen zum Abrufen von Inhaltsfragmenten erstellen, um diese als JSON-Datei direkt bereitzustellen.
   * Im linken Bereich können Sie Ihre Abfrage erstellen.
   * Im rechten Bereich werden die Ergebnisse angezeigt.
   * Der Abfrage-Editor bietet Codevervollständigung und Hotkeys, um die Abfrage einfach auszuführen.
      ![GraphiQL-Editor](../assets/graphiql.png)

1. Unter der Annahme, dass das von uns erstellte Modell mit den Feldern `person`, `lastName` und `position` mit den Feldern `firstName` und  benannt wurde, können wir eine einfache Abfrage erstellen, um den Inhalt unseres Inhaltsfragments abzurufen.

   ```text
   query 
   {
     personList {
       items {
         _path
         firstName
         lastName
         position
       }
     }
   }
   ```

1. Geben Sie die Abfrage in den linken Bereich ein.
   ![GraphiQL-Abfrage](../assets/graphiql-query.png)

1. Klicken Sie auf die Schaltfläche **Abfrage ausführen** oder verwenden Sie den `Ctrl-Enter`-Hotkey, und die Ergebnisse werden als JSON im rechten Bereich angezeigt.
   ![GraphiQL-Ergebnisse](../assets/graphiql-results.png)

1. Klicken Sie auf den Link **Docs** oben rechts auf der Seite, um eine kontextbezogene Dokumentation anzuzeigen, die Ihnen beim Aufbau Ihrer Abfragen hilft, die sich an Ihre eigenen Modelle anpassen.
   ![GraphiQL-Dokumentation](../assets/graphiql-documentation.png)

GraphQL ermöglicht strukturierte Abfragen, mit denen nicht nur bestimmte Datensätze oder einzelne Datenobjekte Zielgruppe werden können, sondern auch bestimmte Elemente der Objekte, verschachtelte Ergebnisse, Angebot-Unterstützung für Abfragen und vieles mehr bereitgestellt werden können.

GraphQL kann sowohl iterative API-Anfragen als auch Überlastung von Versänden vermeiden und ermöglicht stattdessen den Versand von Massen genau dem, was als Antwort auf eine einzige API-Abfrage für die Wiedergabe benötigt wird. Das resultierende JSON kann verwendet werden, um Daten an andere Sites oder Apps zu senden.

## Nächste Schritte {#next-steps}

Das war´s! Sie haben jetzt ein grundlegendes Verständnis für das kopflose Content-Management in AEM. Natürlich gibt es noch viele weitere Ressourcen, in denen Sie tiefer tauchen können, um ein umfassendes Verständnis der verfügbaren Features zu erhalten.

* **Konfigurationsbrowser**  - Weitere Informationen zum AEM Konfigurationsbrowser
* **[Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md)**  - Weitere Informationen zum Erstellen und Verwalten von Inhaltsfragmenten
* **[Unterstützung von Inhaltsfragmenten in der AEM Assets HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md)**  - Weitere Informationen zum Zugriff auf AEM Inhalte über die HTTP-API über CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren, Löschen)
* **[GraphQL-API](/help/assets/content-fragments/graphql-api-content-fragments.md)**  - Weitere Informationen zum Übermitteln von Inhaltsfragmenten per Kopf
