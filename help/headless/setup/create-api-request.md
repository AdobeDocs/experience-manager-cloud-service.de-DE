---
title: Erstellen einer API-Anfrage – Headless-Einrichtung
description: Erfahren Sie, wie Sie die GraphQL-API für die Headless-Bereitstellung von Inhaltsfragmentinhalten und die Assets-REST-API von AEM zur Verwaltung von Inhaltsfragmenten verwenden.
exl-id: 2b72f222-2ba5-4a21-86e4-40c763679c32
source-git-commit: c0b48db0cbef6232f153dc59432ea7289b430538
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 86%

---

# Erstellen einer API-Anfrage – Headless-Einrichtung {#accessing-delivering-content-fragments}

Erfahren Sie, wie Sie die GraphQL-API für die Headless-Bereitstellung von Inhaltsfragmentinhalten und die Assets-REST-API von AEM zur Verwaltung von Inhaltsfragmenten verwenden.

## Was sind GraphQL- und Assets-REST-APIs? {#what-are-the-apis}

[Nachdem Sie einige Inhaltsfragmente erstellt haben,](create-content-fragment.md) können Sie die APIs von AEM verwenden, um sie headless bereitzustellen.

* Mit der [GraphQL-API](/help/headless/graphql-api/content-fragments.md) können Sie Anfragen für den Zugriff auf und die Bereitstellung von Inhaltsfragmenten erstellen. Diese API bietet die zuverlässigsten Funktionen zum Abfragen und Verwenden von Inhaltsfragmentinhalten.
   * Zur Verwendung [müssen Endpunkte in AEM definiert und aktiviert werden](/help/headless/graphql-api/graphql-endpoint.md) und, falls erforderlich, muss die [GraphiQL-Oberfläche installiert werden](/help/headless/graphql-api/graphiql-ide.md).
* Mit der [Assets-REST-API](/help/assets/content-fragments/assets-api-content-fragments.md) können Sie Inhaltsfragmente (und andere Assets) erstellen und ändern.

Der Rest dieses Handbuchs konzentriert sich auf den GraphQL-Zugriff und die Bereitstellung von Inhaltsfragmenten.

## Aktivieren eines GraphQL-Endpunkts {#enable-graphql-endpoint}

Bevor die GraphQL-APIs verwendet werden können, muss ein GraphQL-Endpunkt erstellt werden.

1. Navigieren Sie zu **Instrumente**, **Allgemein**, wählen Sie **GraphQL**.
1. Wählen Sie **Erstellen**.
1. Das Dialogfeld **Neuen GraphQL-Endpunkt erstellen** wird geöffnet. Hier können Sie Folgendes angeben:
   * **Name**: Name des Endpunkts; Sie können einen beliebigen Text eingeben.
   * **GraphQL-Schema verwenden, das bereitgestellt wurde von**: Verwenden Sie das Dropdown-Menü, um die gewünschte Konfiguration auszuwählen.
1. Bestätigen Sie mit **Erstellen**.
1. In der Konsole wird nun ein **Pfad** basierend auf der zuvor erstellten Konfiguration angezeigt. Dies ist der Pfad zum Ausführen von GraphQL-Abfragen.

   ```
   /content/cq:graphql/<configuration-name>/endpoint
   ```

Weitere Informationen zur Aktivierung von [GraphQL-Endpunkten finden Sie hier](/help/headless/graphql-api/graphql-endpoint.md).

## Abfragen von Inhalten unter Verwendung von GraphQL mit GraphiQL

Informationsarchitekten müssen Abfragen für ihre Kanalendpunkte entwerfen, um Inhalte bereitzustellen. Diese Abfragen müssen in der Regel nur einmal pro Endpunkt und Modell berücksichtigt werden. Für die Zwecke dieser ersten Schritte müssen wir nur eine erstellen.

GraphiQL ist eine IDE, die in Ihrer AEM-Umgebung enthalten ist. nach dem Öffnen [Endpunkte konfigurieren](#enable-graphql-endpoint).

1. Melden Sie sich bei AEM as a Cloud Service an und rufen Sie die GraphiQL-Oberfläche auf:

   Sie können auf den Abfrageeditor wie folgt zugreifen:

   * **Instrumente** -> **Allgemein** -> **GraphQL-Abfrage-Editor**
   * direkt; Beispiel: `http://localhost:4502/aem/graphiql.html`

1. Die GraphiQL-IDE ist ein In-Browser-Abfrage-Editor für GraphQL. Sie können sie verwenden, um Abfragen zum Abrufen von Inhaltsfragmenten zu erstellen, um sie Headless als JSON bereitzustellen.
   * In der Dropdown-Liste oben rechts können Sie den Endpunkt auswählen.
   * In einem Bereich ganz links werden die beibehaltenen Abfragen aufgelistet (sofern verfügbar)
   * Im mittleren linken Bereich können Sie Ihre Abfrage erstellen.
   * Die Ergebnisse werden im rechten mittleren Bereich angezeigt.
   * Der Abfrage-Editor bietet Code-Vervollständigung und Hotkeys, um die Abfrage einfach auszuführen.

   ![GraphiQL-Editor](../assets/graphiql.png)

1. Angenommen, das von uns erstellte Modell `person` wurde mit Feldern `firstName`, `lastName` und `position` aufgerufen. Wir können dann eine einfache Abfrage erstellen, um den Inhalt unseres Inhaltsfragments abzurufen.

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

1. Geben Sie die Abfrage in das linke Bedienfeld ein.
   ![GraphiQL-Abfrage](../assets/graphiql-query.png)

1. Klicken Sie auf die Schaltfläche **Abfrage ausführen** oder verwenden Sie den `Ctrl-Enter`-Hotkey. Die Ergebnisse werden als JSON im rechten Bedienfeld angezeigt.
   ![GraphiQL-Ergebnisse](../assets/graphiql-results.png)

1. Klicken Sie oben rechts auf der Seite auf den Link **Dokumente**, um eine kontextbezogene Dokumentation anzuzeigen, die Sie bei der Erstellung Ihrer Abfragen unterstützt und sich an Ihre eigenen Modelle anpasst.
   ![GraphiQL-Dokumentation](../assets/graphiql-documentation.png)

GraphQL ermöglicht strukturierte Abfragen, die nicht nur auf bestimmte Datensätze oder einzelne Datenobjekte abzielen, sondern auch bestimmte Elemente der Objekte und verschachtelte Ergebnisse bereitstellen, Unterstützung für Abfragevariablen bieten und vieles mehr.

GraphQL kann sowohl iterative API-Anfragen als auch Überbereitstellungen vermeiden und ermöglicht stattdessen eine Massenbereitstellung von genau dem, was zum Rendern als Antwort auf eine einzelne API-Abfrage benötigt wird. Das resultierende JSON kann verwendet werden, um Daten in anderen Sites oder Mobile Apps bereitzustellen.

## Nächste Schritte {#next-steps}

Das war´s! Sie haben nun ein grundlegendes Verständnis für das Headless-Content-Management in AEM. Natürlich gibt es viele weitere Ressourcen, mit deren Hilfe Sie sich ein umfassendes Verständnis der verfügbaren Funktionen aneignen können.

* **[Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/content-fragments.md)** – Weitere Informationen zum Erstellen und Verwalten von Inhaltsfragmenten
* **[Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md)** – Weitere Informationen zum direkten Zugriff auf AEM-Inhalte über die HTTP-API über CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren, Löschen)
* **[GraphQL-API](/help/headless/graphql-api/content-fragments.md)** – Weitere Informationen zum Headless-Bereitstellen von Inhaltsfragmenten
