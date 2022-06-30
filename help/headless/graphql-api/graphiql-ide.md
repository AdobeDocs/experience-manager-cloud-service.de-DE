---
title: Verwenden der GraphiQL-IDE in AEM
description: Erfahren Sie, wie Sie die GraphiQL IDE in Adobe Experience Manager verwenden.
feature: Content Fragments,GraphQL API
exl-id: be2ebd1b-e492-4d77-b6ef-ffdea9a9c775
source-git-commit: 6beef4cc3eaa7cb562366d35f936c9a2fc5edda3
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 3%

---

# Verwenden der GraphiQL-IDE {#graphiql-ide}

Implementierung des Standards [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) IDE ist für die Verwendung mit der GraphQL-API von Adobe Experience Manager (AEM) as a Cloud Service verfügbar.

>[!NOTE]
>
>GraphiQL ist in allen Umgebungen von AEM enthalten (kann jedoch nur bei der Konfiguration Ihrer Endpunkte aufgerufen/angezeigt werden).
>
>In früheren Versionen war ein Paket erforderlich, um die GraphiQL-IDE zu installieren. Wenn Sie diese installiert haben, kann sie jetzt entfernt werden.

>[!NOTE]
>Sie müssen [-Endpunkte konfiguriert haben](/help/headless/graphql-api/graphql-endpoint.md) im [Konfigurationsbrowser](/help/assets/content-fragments/content-fragments-configuration-browser.md) vor der Verwendung der GraphiQL IDE.


Die **GraphiQL** Mit können Sie Ihre GraphQL-Abfragen testen und debuggen, indem Sie:
* wählen Sie die **Endpunkt** passend zur Sites-Konfiguration, die Sie für Ihre Abfragen verwenden möchten
* direkt neue Abfragen eingeben
* Erstellen und Zugreifen auf **[Beständige Abfragen](/help/headless/graphql-api/persisted-queries.md)**
* Führen Sie Ihre Abfragen aus, um die Ergebnisse sofort anzuzeigen
* verwalten **Abfragevariablen**
* Speichern und verwalten **Beständige Abfragen**
* Veröffentlichung oder Rückgängigmachen der Veröffentlichung, **Beständige Abfragen** (z. B. nach/von `dev-publish`)
* sehen Sie die **Geschichte** der vorherigen Abfragen
* die **Dokumentation-Explorer** Zugriff auf die Dokumentation; hilft Ihnen zu lernen und zu verstehen, welche Methoden verfügbar sind.

Sie können auf den Abfrageeditor wie folgt zugreifen:

* **Instrumente** -> **Allgemein** -> **GraphQL-Abfrage-Editor**
* direkt; Beispiel: `http://localhost:4502/aem/graphiql.html`

![GraphiQL-Schnittstelle](assets/cfm-graphiql-interface.png "GraphiQL-Schnittstelle")

Sie können GraphiQL in Ihrem System verwenden, damit Abfragen von Ihrer Clientanwendung mithilfe von GET-Anfragen sowie zur Veröffentlichung von Abfragen angefordert werden können. Zur Verwendung in der Produktion können Sie dann [Ihre Abfragen in Ihre Produktionsumgebung verschieben](/help/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production). Zunächst zum Produktionsautor für die Validierung neu erstellter Inhalte mit den Abfragen und schließlich zur Produktionsveröffentlichung für den Live-Verbrauch.

## Endpunkt auswählen {#selecting-endpoint}

Als ersten Schritt müssen Sie die **[Endpunkt](/help/headless/graphql-api/graphql-endpoint.md)** die Sie für die Abfragen verwenden möchten. Der Endpunkt ist der Sites-Konfiguration angemessen, die Sie für Ihre Abfragen verwenden möchten.

Diese ist in der Dropdown-Liste oben rechts verfügbar.

## Neue Abfrage erstellen und beibehalten {#creating-new-query}

Sie können Ihre neue Abfrage im Editor eingeben, der sich in der Mitte links im Bedienfeld befindet, direkt unter dem GraphiQL-Logo.

>[!NOTE]
>
>Wenn Sie bereits eine persistente Abfrage ausgewählt und im Editor angezeigt haben, wählen Sie `+` (neben **Beständige Abfragen**), um den Editor für Ihre neue Abfrage zu leeren.

Beginnen Sie mit der Eingabe des Editors auch:

* verwendet den Mauszeiger, um zusätzliche Informationen zu Elementen anzuzeigen
* bietet Funktionen wie Syntaxhervorhebung, automatische Vervollständigung, automatische Empfehlung

>[!NOTE]
>
>GraphQL-Abfragen beginnen normalerweise mit einer `{` Zeichen.
>
>Zeilen, die mit einer `#` werden ignoriert.

Verwendung **Speichern unter** , um Ihre neue Abfrage beizubehalten.

## Persistente Abfrage aktualisieren {#updating-persisted-query}

Wählen Sie die zu aktualisierende Abfrage aus der Liste im **Beständige Abfragen** Bedienfeld (ganz links).

Die Abfrage wird im Editor angezeigt. Nehmen Sie die erforderlichen Änderungen vor und verwenden Sie dann **Speichern** , um Ihre Aktualisierungen in die persistente Abfrage zu übertragen.

## Ausführen von Abfragen {#running-queries}

Sie können eine neue Abfrage sofort ausführen oder eine persistente Abfrage laden und ausführen. Um eine persistente Abfrage zu laden, wählen Sie sie aus der Liste aus. Die Abfrage wird daraufhin im Editor angezeigt.

In beiden Fällen ist die im Editor angezeigte Abfrage die Abfrage, die ausgeführt wird, wenn Sie entweder:

* Klicken/tippen Sie auf die **Ausführen der Abfrage** icon
* Verwenden der Tastaturkombination `Control-Enter`

## Abfragevariablen {#query-variables}

<!-- more details needed here? -->

Mit der GraphiQL IDE können Sie auch Ihre [Abfragevariablen](/help/headless/graphql-api/content-fragments.md#graphql-variables).

Beispiel:

![GraphQL-Variablen](assets/cfm-graphqlapi-03.png "GraphQL-Variablen")

## Verwalten des Cache für die gespeicherten Abfragen {#managing-cache}

[Beständige Abfragen](/help/headless/graphql-api/persisted-queries.md) werden empfohlen, da sie auf den Dispatcher- und CDN-Ebenen zwischengespeichert werden können, was letztendlich die Leistung der anfragenden Client-Anwendung verbessert. Standardmäßig werden AEM den CDN-Cache (Content Delivery Network) basierend auf einer standardmäßigen Time to Live (TTL) ungültig.

Mit GraphQL können Sie die HTTP-Cache-Header konfigurieren, um diese Parameter für Ihre einzelne persistente Abfrage zu steuern.

1. Die **Kopfzeilen** -Option können Sie über die drei vertikalen Punkte rechts neben dem beibehaltenen Abfragenamen (ganz links) aufrufen:

   ![Persistente Abfrage-HTTP-Cache-Header](assets/cfm-graphqlapi-headers-01.png "Persistente Abfrage-HTTP-Cache-Header")

1. Wenn Sie diese Option auswählen, wird das **Cachekonfiguration** dialog:

   ![Einstellungen für beständige Abfrage-HTTP-Cache-Header](assets/cfm-graphqlapi-headers-02.png "Einstellungen für beständige Abfrage-HTTP-Cache-Header")

1. Wählen Sie den entsprechenden Parameter aus und passen Sie dann den Wert nach Bedarf an:

   * **cache-control** - **max-age**
Caches können diesen Inhalt für eine bestimmte Anzahl von Sekunden speichern. Normalerweise ist dies die TTL des Browsers (Time To Live).
   * **Ersatzsteuerung** - **s-maxage**
Entspricht maximalem Alter, gilt jedoch speziell für Proxy-Caches.
   * **Ersatzsteuerung** - **stale-while-revalidate**
Caches können eine zwischengespeicherte Antwort auch dann weiter bereitstellen, wenn sie bis zu der festgelegten Anzahl von Sekunden veraltet ist.
   * **Ersatzsteuerung** - **stale-if-error**
Caches können im Falle eines Ursprungs- oder Ursprungsfehlers bis zu einer festgelegten Anzahl von Sekunden weiterhin eine zwischengespeicherte Antwort bereitstellen.

1. Auswählen **Speichern** um die Änderungen beizubehalten.

## Persistente Abfragen veröffentlichen {#publishing-persisted-queries}

Nachdem Sie die beibehaltene Abfrage aus der Liste (linker Bereich) ausgewählt haben, können Sie die **Veröffentlichen** und **Veröffentlichung rückgängig machen** Aktionen. Dadurch werden sie in Ihrer Veröffentlichungsumgebung aktiviert (z. B. `dev-publish`) für den einfachen Zugriff Ihrer Anwendungen beim Testen.

>[!NOTE]
>
>Die Definition des Cache der gespeicherten Abfrage `Time To Live` {&quot;cache-control&quot;:&quot;parameter&quot;:value} hat einen Standardwert von 2 Stunden (7200 Sekunden).

## URL kopieren, um direkt auf die Abfrage zuzugreifen {#copy-url}

Die **URL kopieren** -Option können Sie eine Abfrage simulieren, indem Sie die URL kopieren, die zum direkten Zugriff auf die beibehaltene Abfrage verwendet wird, und die Ergebnisse anzeigen. Dies kann dann zum Testen verwendet werden. Beispielsweise durch Zugriff in einem Browser:

<!--
  >[!NOTE]
  >
  >The URL will need [encoding before using programmatically](/help/headless/graphql-api/persisted-queries.md#encoding-query-url).
  >
  >The target environment might need adjusting, depending on your requirements.
-->

Beispiel:

`http://localhost:4502/graphql/execute.json/global/article-list-01`

Durch die Verwendung dieser URL in einem Browser können Sie die Ergebnisse bestätigen:

![GraphiQL - URL kopieren](assets/cfm-graphiql-copy-url.png "GraphiQL - URL kopieren")

Die **URL kopieren** -Option können Sie über die drei vertikalen Punkte rechts neben dem beibehaltenen Abfragenamen (ganz links) aufrufen:

![GraphiQL - URL kopieren](assets/cfm-graphiql-persisted-query-options.png "GraphiQL - URL kopieren")

## Löschen persistenter Abfragen {#deleting-persisted-queries}

Die **Löschen** ist auch über die drei vertikalen Punkte rechts neben dem beibehaltenen Abfragenamen (ganz links) verfügbar.

<!-- what happens if you try to delete something that is still published? -->


## Installieren der beständigen Abfrage in der Produktion {#installing-persisted-query-production}

Nach dem Entwickeln und Testen Ihrer persistenten Abfrage mit GraphiQL besteht das Endziel darin, [Übertragen in die Produktionsumgebung](/help/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production) zur Verwendung durch Ihre Anwendungen.

## Tastaturbefehle {#keyboard-shortcuts}

Es gibt eine Auswahl von Tastaturbefehlen, die direkten Zugriff auf Aktionssymbole in der IDE bieten:

* Abfrage konfigurieren:  `Shift-Control-P`
* Zusammenführungsabfrage:  `Shift-Control-M`
* Ausführen der Abfrage:  `Control-Enter`
* Automatisch abschließen:  `Control-Space`

>[!NOTE]
>
>Auf einigen Tastaturen `Control` Schlüssel wird als `Ctrl`.
