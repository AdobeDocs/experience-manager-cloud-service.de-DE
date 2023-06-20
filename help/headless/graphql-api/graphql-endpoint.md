---
title: Verwalten von GraphQL-Endpunkten in AEM
description: Erfahren Sie, wie Sie GraphQL-Endpunkte in Adobe Experience Manager as a Cloud Service für die Bereitstellung von Headless-Inhalten verwalten.
feature: Content Fragments,GraphQL API
exl-id: f7164ae3-4074-4db7-8c43-a79cc2ef00b1
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 97%

---

# Verwalten von GraphQL-Endpunkten in AEM {#graphql-aem-endpoint}

Der Endpunkt ist der Pfad, der für den Zugriff auf GraphQL für AEM verwendet wird. Mit diesem Pfad können Sie (oder Ihr Programm):

* auf das GraphQL-Schema zugreifen,
* Ihre GraphQL-Abfragen senden,
* Antworten (auf Ihre GraphQL-Abfragen) empfangen.

Es gibt zwei Arten von Endpunkten in AEMٔ:

* Global
   * Verfügbar zur Verwendung durch alle Websites.
   * Dieser Endpunkt kann alle Inhaltsfragmentmodelle aus allen Sites-Konfigurationen verwenden (definiert im [Konfigurations-Browser](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)).
   * Wenn es Inhaltsfragmentmodelle gibt, die unter Sites-Konfigurationen freigegeben werden sollen, sollten diese unter den globalen Sites-Konfigurationen erstellt werden.
* Sites-Konfigurationen:
   * Entspricht einer Sites-Konfiguration, wie im [Konfigurations-Browser](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) definiert.
   * Spezifisch für eine bestimmte Website / ein bestimmtes Projekt.
   * Ein für die Sites-Konfiguration spezifischer Endpunkt verwendet die Inhaltsfragmentmodelle aus dieser spezifischen Sites-Konfiguration zusammen mit denen aus der globalen Sites-Konfiguration.

>[!CAUTION]
>
>Der Inhaltsfragment-Editor kann zulassen, dass ein Inhaltsfragment einer Sites-Konfiguration (über Richtlinien) auf ein Inhaltsfragment einer anderen Sites-Konfiguration verweist.
>
>In einem solchen Fall ist nicht der gesamte Inhalt mithilfe eines konfigurationsspezifischen Endpunkts für Sites abrufbar.
>
>Der Inhaltsautor sollte dieses Szenario steuern. Beispielsweise kann es nützlich sein, freigegebene Inhaltsfragmentmodelle unter die globale Sites-Konfiguration zu stellen.

Der Repository-Pfad des GraphQL für den globalen Endpunkt in AEM lautet:

`/content/cq:graphql/global/endpoint`

Ihr Programm kann den folgenden Pfad in der Anfrage-URL verwenden:

`/content/_cq_graphql/global/endpoint.json`

Um den GraphQL-Endpunkt für AEM zu aktivieren, gehen Sie folgendermaßen vor:

* [Aktivieren des GraphQL-Endpunkts](#enabling-graphql-endpoint)
* [Veröffentlichen des GraphQL-Endpunkts](#publishing-graphql-endpoint)

## Aktivieren des GraphQL-Endpunkts {#enabling-graphql-endpoint}

Um einen GraphQL-Endpunkt zu aktivieren, benötigen Sie zunächst eine entsprechende Konfiguration. Siehe [Inhaltsfragmente – Konfigurations-Browser](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md).

>[!CAUTION]
>
>Wenn die [Verwendung von Inhaltsfragmentmodellen nicht aktiviert wurde](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md), ist die Option **Erstellen** nicht verfügbar.

So aktivieren Sie den entsprechenden Endpunkt:

1. Gehen Sie zu **Tools**, **Allgemein** und wählen Sie **GraphQL** aus.
1. Wählen Sie **Erstellen**.
1. Das Dialogfeld **Neuen GraphQL-Endpunkt erstellen** wird geöffnet. Hier können Sie Folgendes angeben:
   * **Name**: Name des Endpunkts; Sie können einen beliebigen Text eingeben.
   * **GraphQL-Schema verwenden, das bereitgestellt wurde von**: Verwenden Sie das Dropdown-Menü, um die gewünschte Website / das gewünschte Projekt auszuwählen.

   >[!NOTE]
   >
   >Die folgende Warnung wird im Dialogfeld angezeigt:
   >
   >* *GraphQL-Endpunkte können Datensicherheits- und Leistungsprobleme hervorrufen, wenn sie nicht sorgfältig verwaltet werden. Stellen Sie sicher, dass nach dem Erstellen eines Endpunkts die entsprechenden Berechtigungen festgelegt werden.*

1. Bestätigen Sie mit **Erstellen**.
1. Das Dialogfeld **Nächste Schritte** stellt einen direkten Link zur Sicherheitskonsole bereit, sodass Sie sicherstellen können, dass der neu erstellte Endpunkt über geeignete Berechtigungen verfügt.

   >[!CAUTION]
   >
   >Der Endpunkt ist für jeden zugänglich. Dies kann – insbesondere bei Veröffentlichungsinstanzen – Sicherheitsbedenken aufwerfen, da GraphQL-Abfragen eine hohe Server-Belastung verursachen können.
   >
   >Sie können am Endpunkt geeignete ACLs für Ihr Programm einrichten.

## Veröffentlichen des GraphQL-Endpunkts {#publishing-graphql-endpoint}

Wählen Sie den neuen Endpunkt und **Veröffentlichen** aus, um ihn in allen Umgebungen vollständig verfügbar zu machen.

>[!CAUTION]
>
>Der Endpunkt ist für jeden zugänglich.
>
>Dies kann – insbesondere bei Veröffentlichungsinstanzen – Sicherheitsbedenken aufwerfen, da GraphQL-Abfragen eine hohe Server-Belastung verursachen können.
>
>Sie müssen am Endpunkt [für Ihren Anwendungsfall geeignete ACLs](/help/headless/security/permissions.md) einrichten.
