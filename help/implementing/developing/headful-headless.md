---
title: Kopflos und Kopflos in AEM
description: AEM Projekte können in einem schlagkräftigen und kopflosen Modell implementiert werden, aber die Wahl ist nicht binär. AEM Angebote haben die Flexibilität, die Vorteile beider Modelle in einem Projekt zu nutzen.
translation-type: tm+mt
source-git-commit: 772717b7ad3baa17a58e251c128663035eb89931
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 0%

---


# Kopflos und Kopflos in AEM {#headful-headless}

Adobe Experience Manager-Projekte können sowohl in Headful- als auch in Headless-Modellen implementiert werden, aber die Wahl ist nicht binär. AEM Angebote haben die Flexibilität, die Vorteile beider Modelle in einem Projekt zu nutzen. Dieses Dokument bietet einen Überblick über die verschiedenen Modelle und beschreibt die Stufen SPA Integration.

## Überblick {#overview}

AEM Angeboten leistungsstarke Tools zur Verwaltung der Inhaltserstellung und des Versands auf einer Plattform. Dies ist ein traditionelles &quot;schlagkräftiges&quot;Content-Management-Modell, bei dem Autoren und Entwickler von Inhalten auf derselben Plattform arbeiten, um die Erlebnisse für die Nutzer bereitzustellen.

AEM können auch zur einfachen Verwaltung von Inhalten verwendet werden, sodass Präsentation und Versand der Inhalte von einer anderen Plattform verwaltet werden können. Dies ist das &quot;Headless&quot;-Modell des Content-Managements, bei dem Autoren und Entwickler von Inhalten auf verschiedenen Plattformen arbeiten, um den Nutzern von Inhalten ein Erlebnis zu bieten.

Aber das muss keine binäre Entscheidung sein. AEM Angebot haben eine beispiellose Flexibilität, sodass Sie die Vorteile beider Modelle für Ihr Projekt nutzen können.

![AEM-Implementierungsmodelle](headless/assets/aem-implementation-models.png)

In einem schlagkräftigen oder vollständigen Stapelmodell wird der Inhalt im AEM Repository und AEM Komponenten auf der Grundlage von Java, HTL usw. verwaltet. werden verwendet, um den Inhalt für die Benutzererfahrung wiederzugeben. In diesem Modell erfolgt die Erstellung des Inhalts, die Formatierung, Präsentation und Bereitstellung des Inhalts in AEM.

Bei einem kopflosen Modell wird der Inhalt im AEM Repository verwaltet, jedoch über APIs wie REST und GraphQL an ein anderes System gesendet, um den Inhalt für die Benutzererfahrung wiederzugeben. In diesem Modell werden Inhalte in AEM erstellt, aber die Formatierung, Präsentation und Bereitstellung erfolgt auf einer anderen Plattform.

Einzelseitenanwendungen (SPA) sind häufig das Ziel für Inhalte, die von AEM ohne Kopfhörer bereitgestellt werden. Diese SPA müssen jedoch nicht völlig extern zu AEM sein. AEM ermöglicht Ihnen zu entscheiden, in welchem Ausmaß Ihre SPA in AEM integriert sind. Nehmen wir ein Beispiel.

## Webshop-Beispiel {#web-shop-example}

Nehmen wir an, Sie haben einen Webshop für Ihre Firma als SPA. Darin haben Sie alle Produktdetails und Bilder. Anschließend stellen Sie AEM vor, um Ihre Marketingbemühungen wie Werbe-Sites, Blogs und Kampagnen-Inhalte zu unterstützen. Wie integrieren Sie die beiden? AEM bietet eine Reihe von Optionen:

* **Die Systeme können unabhängig betrieben werden.**
* **Bieten Sie den Webshop mit eingeschränktem Inhalt von AEM über GraphQL an.** Inhalte können von Autoren in AEM erstellt werden, jedoch nur über den Webshop SPA.
* **Betten Sie den Webshop SPA in AEM ein.** Inhalte können von Autoren in AEM erstellt und im Kontext des Webshops AEM angezeigt werden, jedoch nicht manipuliert.
* **Betten Sie den Webshop SPA in AEM ein und aktivieren Sie bearbeitbare Punkte.** Inhalte können von Autoren in AEM erstellt und im Kontext des Webshops AEM angezeigt werden, und die Autoren haben nur begrenzte Möglichkeiten, den Inhalt des Webshops SPA innerhalb AEM zu manipulieren.
* **Betten Sie den Webshop SPA in AEM ein und aktivieren Sie ganze Zonen für die Bearbeitung.** Inhalte können von Autoren in AEM erstellt und im Kontext des Webshops AEM angezeigt werden, und die Autoren haben nur begrenzte Möglichkeiten, den Inhalt des Webshops SPA innerhalb AEM zu manipulieren.

Im nächsten Abschnitt werden diese Integrationsstufen genauer untersucht.

>[!NOTE]
>
>Natürlich können Sie auch die Web-Shop-SPA als voll funktionierende AEM SPA [mit dem AEM SPA Editor-Framework neu implementieren.](/help/implementing/developing/hybrid/introduction.md) Wenn Sie bereits AEM haben und einen neuen Webshop oder andere SPA erstellen möchten, ist dies die empfohlene Methode, die jedoch nicht in den Anwendungsbereich dieses Dokuments fällt.

## SPA Integrationsstufen {#integration-levels}

SPA Integration fällt in AEM auf vier Ebenen.

* **Ebene 0: Keine Integration**
   * Die SPA und AEM existieren getrennt und tauschen keine Informationen aus.
   * Inhalte werden in zwei separaten Systemen erstellt, verwaltet und bereitgestellt.
* **Ebene 1: Integration von Inhaltsfragmenten**
   * [Inhaltsfragmente ](/help/assets/content-fragments/content-fragments.md) werden in AEM verwendet, um eingeschränkte Inhalte für die SPA zu erstellen und zu verwalten.
   * Die SPA ruft diesen Inhalt über AEM [GraphQL API ab.](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * Einige Inhalte werden in AEM und andere in einem externen System verwaltet.
   * Inhalte können nur im SPA angezeigt werden.
* **Ebene 2: SPA in AEM einbetten**
   * [Inhaltsfragmente ](/help/assets/content-fragments/content-fragments.md) werden in AEM verwendet, um Inhalte für die SPA zu erstellen und zu verwalten.
   * Die SPA ruft diesen Inhalt über AEM [GraphQL API ab.](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * Einige Inhalte werden in AEM und andere in einem externen System verwaltet.
   * Inhalte können im Kontext innerhalb von AEM angezeigt werden.
   * Eingeschränkte Inhalte können innerhalb von AEM bearbeitet werden.
* **Ebene 3: SPA in AEM einbetten und vollständig aktivieren**
   * [Inhaltsfragmente ](/help/assets/content-fragments/content-fragments.md) werden in AEM verwendet, um Inhalte für die SPA zu erstellen und zu verwalten.
   * Die SPA ruft diesen Inhalt über AEM [GraphQL API ab.](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * Inhalte können im Kontext innerhalb von AEM angezeigt werden.
   * Die meisten Inhalte können innerhalb von AEM bearbeitet werden.

Stufe 1 ist ein Beispiel für eine typische Implementierung ohne Kopfdaten. Inhaltsersteller können ihre Inhalte jedoch nur im Kontext innerhalb der SPA Ansichten. AEM ist nur ein Authoring-Tool.

Der Vorteil und die Flexibilität der AEM werden mit den Stufen 2 und 3 deutlich, während die Vorteile der SPA erhalten bleiben. Autoren können ihre Inhalte in AEM erstellen, sie sehen sie aber auch im Kontext innerhalb von AEM. Die SPA erhalten die Fähigkeit, in AEM verfasst zu werden, aber dennoch als SPA geliefert werden.

## Implementieren der Integrationsstufen {#implementing}

Es stehen verschiedene Tools in AEM zur Verfügung, je nachdem, welche Integrationsstufe Sie wählen. Jede Ebene baut auf den zuvor verwendeten Werkzeugen auf. In der folgenden Liste finden Sie Links zu den entsprechenden Ressourcen.

* **Ebene 1:** Inhaltsfragmente und der  [AEM ](/help/implementing/developing/headless/introduction.md) Rahmen ohne Kopfdaten können verwendet werden, um AEM Inhalte für die SPA bereitzustellen.
* **Ebene 2:** Zusätzlich zu Stufe 1:
   * [Die RemotePage-](/help/implementing/developing/hybrid/remote-page.md) Komponente kann verwendet werden, um die externe SPA in AEM einzubetten, wo AEM Inhalt im Kontext angezeigt werden kann.
   * Bestimmte Punkte auf der SPA können auch auf [Eingeschränkte Bearbeitung in AEM zulassen aktiviert werden.](/help/implementing/developing/hybrid/editing-external-spa.md)
* **Ebene 3:** Zusätzlich zu Stufe 2:
   * Ganze Bereiche des SPA können aktiviert werden, um eine umfassende Bearbeitung in AEM zu ermöglichen.
