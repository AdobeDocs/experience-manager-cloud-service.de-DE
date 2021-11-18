---
title: Erste Schritte mit CIF Authoring
description: Erste Schritte mit CIF Authoring
source-git-commit: e497b5b4439cf91ec7ea698d9bedcb4210802414
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 1%

---

# Erste Schritte mit AEM CIF Authoring {#getting-started}

Erfahren Sie mehr über AEM CIF-Authoring.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument dieser AEM Journey zu Inhalt und Handel [Informationen zu AEM Content und Commerce](/help/commerce-cloud/introduction.md), haben Sie die grundlegende Theorie gelernt, was ein Headless-CMS ist, und sollten jetzt die grundlegenden Konzepte von AEM Content und Commerce verstehen.

Dieser Artikel baut auf diesen Grundlagen auf.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie CIF für Content und Commerce-spezifisches Authoring verwenden. Nach dem Lesen sollten Sie:

* Grundlegendes zu den Konzepten des CIF-Authoring mit dem universellen Editor
* Zugriff auf Produktkatalogdaten in AEM mithilfe von Produkt- und Kategorieauswahlen
* Zugriff auf Inhalts- und Commerce-Daten mithilfe des Produkt-Cockpits und AEM Omnisearch

## CIF-Bearbeitung im universellen Editor {#cif-authoring}

CIF erweitert den Universal Editor mit Funktionen, um auf die Echtzeit-Produktdaten zuzugreifen, ohne den Kontext zu verlassen:

Öffnen Sie das seitliche Bedienfeld und wählen Sie &quot;Produkte&quot;aus der Dropdown-Liste aus.
![Produkttyp auswählen](assets/asset-finder-overview.png)

Sie können den Produktkatalog durchsuchen oder das Feld für die Volltextsuche verwenden, um Produkte zu finden.
![Produkttyp](assets/asset-finder-search.png)

Produkte können auf Komponenten, die Produktrückgänge unterstützen (z. B. Produkt-Teaser, Produktkarussell) direkt auf der Seite abgelegt werden, auf der automatisch eine Produkt-Teaser-Komponente erstellt wird.

## Produkt- und Kategorieauswahlen {#pickers}

Wenn Produkt- und Kategoriedaten in Commerce-Komponenten oder AEM Back-Office-Dialogfeldern erforderlich sind, können AEM Autoren Auswahl verwenden, die Benutzeroberflächenelemente sind, um Produktkatalogdaten bequem zu suchen und auszuwählen.

### Produktauswahl

Durch Klicken auf das Ordnersymbol wird die modale Benutzeroberfläche der Auswahl geöffnet (z. B. Produkt-Teaser).
![Produktauswahl](assets/product-picker-open.png)

Produkte können entweder durch die Katalogstruktur auf der linken Seite oder durch die Suche gefunden werden. Die Volltextsuche berücksichtigt die ausgewählte Kategorie und beschränkt die Suchergebnisse auf diese Kategorie.
![Produktauswahlordner](assets/product-picker-folders.png)

Produkte mit Varianten werden mit einem Ordnersymbol gekennzeichnet, auf das Sie klicken können, um alle Varianten anzuzeigen.
![Produktauswahlvarianten](assets/product-picker-variants.png)
![Produktauswahlvarianten geöffnet](assets/product-picker-variants-open.png)

### Kategorieauswahl

Funktioniert wie eine Produktauswahl. Durch Klicken auf das Ordnersymbol wird die modale Benutzeroberfläche der Auswahl geöffnet (z. B. Kategoriekarussell).
![Kategorieauswahl](assets/category-picker-open.png)

Durchsuchen Sie die Katalogstruktur auf der linken Seite und wählen Sie die Kategorie aus.
![Kategorieauswahl](assets/category-picker-folders.png)

## Produkt-Cockpit {#cockpit}

Das Produkt-Cockpit ist ein zentraler Ort, um schnell auf den Produktkatalog mit all seinen angereicherten Inhalten zuzugreifen. In einem der nächsten Module erfahren Sie, wie Sie Produktdaten mit Inhalten anreichern. Zunächst sollten wir uns auf den Zugriff auf Produktdaten konzentrieren.

Klicken Sie im Hauptmenü auf Commerce , um eine Liste aller angehängten Produktkataloge anzuzeigen.
![Commerce-Menüelement](assets/commerce-menu-item.png)

Hier wird eine Liste aller Produktkataloge zum Verbinden angezeigt.
![integrierte Cockpit-Kataloge](assets/cockpit-Integrated-catalogs.png)

Der Produktkatalog zeigt standardmäßig alle Kategorien der ersten Ebene mit allen Produkten an. Wenn Sie auf eine Kategorie klicken, wird diese Kategorie mit allen zugehörigen Produkten und Unterkategorien einschließlich ihrer Produkte geöffnet.
![Cockpit-Produktkatalog](assets/cockpit-product-catalog.png)

Sie können die Produkteigenschaften öffnen, indem Sie auf das Eigenschaftssymbol klicken. Das Symbol wird angezeigt, indem Sie den Mauszeiger über eine Produktkachel bewegen.
![Cockpit-Produkteigenschaften](assets/cockpit-properties.png)

Alle Produkteigenschaften sind schreibgeschützt, da die Daten vom verbundenen Backend in Echtzeit geladen werden. Das Ändern der Produkteigenschaften muss im Backend-System vorgenommen werden, das das Aufzeichnungssystem ist. Die Registerkarte **Varianten** wird nur angezeigt, wenn das Produkt Varianten aufweist. Durch Klicken auf die Registerkarte werden alle Varianten mit ihren Attributen angezeigt.
![Cockpit-Produktvarianten](assets/cockpit-properties-variants.png)

Die übrigen Registerkarten zeigen alle AEM Inhalte an, die mit dem Produkt verknüpft sind. Wir werden diese Tabs in einem der nächsten Module besprechen.

## AEM Omnisearch {#omnisearch}

Die Verwendung von Omnisearch ist eine einfache Möglichkeit, AEM Inhalt mithilfe der Volltextsuche zu finden. CIF erweitert Omnisearch mit der Volltextsuche von Produktkatalogen mit den zugehörigen AEM.
![Commerce-Menüelement](assets/omnisearch.png)

Omnisearch führt eine Volltextsuche im Commerce-Backend durch, um alle verwandten Produkte zu finden. Das Ergebnis wird unter **Alle Produkte anzeigen**. Omnisearch sucht auch AEM nach Inhalten, die mit dem gesuchten Produkt verknüpft sind. Die Ergebnisse werden in den jeweiligen AEM aufgelistet. In diesem Beispiel ist ein Inhaltsfragment mit dem Produkt verknüpft.

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil des Journey abgeschlossen haben, sollten Sie:

* Grundlegendes zu den Konzepten des CIF-Authoring mit dem universellen Editor
* Zugriff auf den Produktkatalog in AEM mithilfe von Produkt- und Kategorieauswahlen
* Zugriff auf Inhalts- und Commerce-Daten mithilfe des Produkt-Cockpits und AEM Omnisearch

Machen Sie sich mit diesem Wissen vertraut und fahren Sie mit dem Journey fort, indem Sie das Dokument erneut überprüfen. [Verwalten von Produktkatalogseiten und -vorlagen](catalog-templates.md), wo Sie erfahren, wie Sie Ihr erstes Produktkatalog-Erlebnis erstellen und anpassen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, zum nächsten Teil der Journey zu wechseln, indem Sie sich das Dokument ansehen. [Verwalten von Produktkatalogseiten und -vorlagen](catalog-templates.md)Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte ermöglichen, aber nicht auf dem Journey weiterarbeiten müssen.

* [Konfigurieren von Stores und Katalogen](/help/commerce-cloud/getting-started.md#catalog)
