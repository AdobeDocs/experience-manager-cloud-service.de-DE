---
title: Erste Schritte mit CIF-Authoring
description: Erste Schritte mit CIF-Authoring.
exl-id: 0bef4d8c-0ad3-4ec8-ab08-8c83203b3b68
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 100%

---

# Erste Schritte mit AEM-CIF-Authoring {#getting-started}

Lernen Sie Adobe Experience Manager (AEM) CIF-Authoring kennen.

## Ihre bisherige Tour {#story-so-far}

Im vorherigen Dokument dieser AEM-Tour zu Content and Commerce, [Informationen zu AEM Content and Commerce](/help/commerce-cloud/introduction.md), haben Sie die grundlegende Theorie und die Konzepte von Headless CMS und AEM Content and Commerce kennengelernt.

Dieser Artikel baut auf diesen Grundlagen auf.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie CIF für das Authoring in Content and Commerce verwenden. Nach dem Lesen sollten Sie Folgendes können:

* Verstehen der Konzepte des CIF-Authorings mit dem Seiteneditor in AEM
* Zugreifen auf Produktkatalogdaten in AEM mithilfe von Produkt- und Kategorieauswahlelementen
* Zugreifen auf Inhalts- und Commerce-Daten mithilfe des Produkt-Cockpits und AEM Omnisearch

## CIF-Authoring im AEM-Seiteneditor {#cif-authoring}

CIF erweitert den Seiteneditor in AEM um Funktionen, um auf die Echtzeit-Produktdaten zuzugreifen, ohne den Kontext zu verlassen:

Öffnen Sie das seitliche Bedienfeld und wählen Sie „Produkte“ aus der Dropdown-Liste aus.
![Produkttyp auswählen](assets/asset-finder-overview.png)

Sie können den Produktkatalog durchsuchen oder das Feld für die Volltextsuche verwenden, um Produkte zu finden.
![Produkttyp](assets/asset-finder-search.png)

Produkte können auf Komponenten, die dies unterstützen (z. B. Produkt-Teaser, Produktkarussell), direkt auf der Seite abgelegt werden. Dadurch wird automatisch eine Produkt-Teaser-Komponente erstellt.

## Produkt- und Kategorieauswahl {#pickers}

Wenn Produkt- und Kategoriedaten in Commerce-Komponenten oder AEM-Back-Office-Dialogfeldern erforderlich sind, können AEM-Autoren Auswahlelemente verwenden. Dies sind Benutzeroberflächenelemente, mit den Produktkatalogdaten bequem gesucht und ausgewählt werden können.

### Produktauswahl

Durch Klicken auf das Ordnersymbol wird die modale Benutzeroberfläche der Auswahl geöffnet (z. B. Produkt-Teaser).
![Produktauswahl](assets/product-picker-open.png)

Produkte können über die Katalogstruktur auf der linken Seite oder über die Suche gefunden werden. Die Volltextsuche berücksichtigt die ausgewählte Kategorie und beschränkt die Suchergebnisse auf diese Kategorie.
![Produktauswahlordner](assets/product-picker-folders.png)

Produkte mit Varianten werden mit einem Ordnersymbol gekennzeichnet, auf das Sie klicken können, um alle Varianten anzuzeigen.
![Produktauswahl – Varianten](assets/product-picker-variants.png)
![Produktauswahl – Varianten geöffnet](assets/product-picker-variants-open.png)

### Kategorieauswahl

Funktioniert wie eine Produktauswahl. Durch Klicken auf das Ordnersymbol wird die modale Benutzeroberfläche der Auswahl geöffnet (z. B. Kategoriekarussell).
![Kategorieauswahl](assets/category-picker-open.png)

Durchsuchen Sie die Katalogstruktur auf der linken Seite und wählen Sie die Kategorie aus.
![Kategorieauswahl](assets/category-picker-folders.png)

## Produkt-Cockpit {#cockpit}

Das Produkt-Cockpit ist ein zentraler Ort, um schnell auf den Produktkatalog mit allen angereicherten Inhalten zuzugreifen. In einem der nächsten Module erfahren Sie, wie Sie Produktdaten mit Inhalten anreichern. Zunächst konzentrieren wir uns auf den Zugriff auf Produktdaten.

Klicken Sie im Hauptmenü auf „Commerce“, um eine Liste aller angehängten Produktkataloge anzuzeigen.
![Commerce-Menüelement](assets/commerce-menu-item.png)

Hier wird eine Liste aller verbundenen Produktkataloge angezeigt.
![Cockpit – Integrierte Kataloge](assets/cockpit-Integrated-catalogs.png)

Der Produktkatalog zeigt standardmäßig alle Kategorien der ersten Ebene mit allen Produkten an. Durch Klicken auf eine Kategorie wird diese Kategorie mit allen zugehörigen Produkten und Unterkategorien einschließlich ihrer Produkte geöffnet.
![Cockpit – Produktkatalog](assets/cockpit-product-catalog.png)

Sie können die Produkteigenschaften öffnen, indem Sie auf das Eigenschaftssymbol klicken. Das Symbol wird angezeigt, wenn Sie den Mauszeiger über eine Produktkachel bewegen.
![Cockpit – Produkteigenschaften](assets/cockpit-properties.png)

Alle Produkteigenschaften sind schreibgeschützt, da die Daten in Echtzeit vom verbundenen Backend geladen werden. Das Ändern der Produkteigenschaften muss im Backend-System vorgenommen werden, das als Aufzeichnungssystem dient. Die Registerkarte **Varianten** wird nur angezeigt, wenn das Produkt Varianten aufweist. Durch Klicken auf die Registerkarte werden alle Varianten mit ihren Attributen angezeigt.
![Cockpit – Produktvarianten](assets/cockpit-properties-variants.png)

Die übrigen Registerkarten zeigen alle AEM-Inhalte an, die mit dem Produkt verknüpft sind. Diese Registerkarten werden in einem der nächsten Module beschrieben.

## AEM Omnisearch {#omnisearch}

Die Verwendung von Omnisearch ist eine einfache Möglichkeit, AEM-Inhalte mithilfe der Volltextsuche zu finden. CIF erweitert Omnisearch um die Volltextsuche in Produktkatalogen mit den zugehörigen AEM-Inhalten.
![Commerce-Menüelement](assets/omnisearch.png)

Omnisearch führt eine Volltextsuche im Commerce-Backend durch, um alle zugehörigen Produkte zu finden. Das Ergebnis wird unter **Alle Produkte anzeigen** aufgeführt. Omnisearch durchsucht auch AEM nach Inhalten, die mit dem gesuchten Produkt verknüpft sind. Die Ergebnisse werden in den jeweiligen AEM-Kategorien aufgelistet. In diesem Beispiel ist ein Inhaltsfragment mit dem Produkt verknüpft.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der Tour abgeschlossen haben, sollten Sie:

* die Konzepte des CIF-Authorings mit dem Seiteneditor verstehen
* Zugreifen auf den Produktkatalog in AEM mithilfe von Produkt- und Kategorieauswahlelementen
* Zugreifen auf Inhalts- und Commerce-Daten mithilfe des Produkt-Cockpits und AEM Omnisearch

Nutzen Sie dieses Wissen und fahren Sie mit Ihrer Tour fort, indem Sie das Dokument [Verwalten von Produktkatalogseiten und -vorlagen](catalog-templates.md) lesen. Hier erfahren Sie, wie Sie Ihr erstes Produktkatalogerlebnis erstellen und anpassen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, mit dem nächsten Teil der Tour –[Verwalten von Produktkatalogseiten und -vorlagen](catalog-templates.md) – fortzufahren. Es folgen einige optionale Ressourcen, die einen tieferen Einblick in einige der hier erwähnten Konzepte bieten. Diese optionalen Ressourcen sind jedoch nicht erforderlich, um die Tour fortzusetzen.

* [Konfigurieren von Stores und Katalogen](/help/commerce-cloud/getting-started.md#catalog)
