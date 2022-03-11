---
title: Verwalten von Produktkatalogseiten und Vorlagen
description: Erfahren Sie, wie Sie Produktkatalogseiten und -vorlagen verwalten
exl-id: 0d795d85-c865-40d5-941e-e02ee96fdd11
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 3%

---

# Verwalten von Produktkatalogseiten und Vorlagen {#product-catalog}

Hier erfahren Sie, wie Sie Produktkatalog-Seiten und -Vorlagen verwalten.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der Journey zur Inhaltserstellung und zum AEM Commerce [Erste Schritte mit AEM Grundlagen der CIF-Bearbeitung](getting-started.md), haben Sie die Grundlagen des CIF-Authoring gelernt.

Dieser Artikel baut auf diesen Grundlagen auf.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie Produktkatalogseiten und -vorlagen verwalten. Nach dem Lesen sollten Sie:

* Konzepte von Katalogvorlagen verstehen
* Funktionsweise generischer Vorlagen
* eine individuelle Vorlage erstellt haben

## Das Grundkonzept {#basic-concept}

Die Venia-Storefront verfügt über ein typisches Produktkatalog-Erlebnis mit Navigation, Landingpage, Kategorie (PLP) und Produktdetailseiten (PDP).

Katalogseiten werden dynamisch mithilfe einer AEM CIF-Katalogvorlage und Echtzeit-Produktdaten erstellt, die bei Bedarf vom Commerce-Endpunkt abgerufen werden. Jeder Katalog verfügt über eine generische Vorlage für Produkt- und Kategorieseiten.
![Katalogstruktur](assets/catalog-structure.png)

Die Navigationskomponente zeigt Inhalte und Katalogseiten an. Es ist möglich, entweder die Katalogeinstiegsseite oder die Kategorien der ersten Ebene in der Navigation anzuzeigen. Wenn Sie den Mauszeiger über eine Kategorie bewegen, werden Kategorien der zweiten Ebene als zweite Zeile angezeigt.
![Katalognavigation](assets/catalog-navigation.png)

Durch Klicken auf eine Kategorie wird die Kategorieseite (oder Produktlistenseite) geöffnet.

![PLP](assets/catalog-plp.png)

Durch Klicken auf ein Produkt wird die Produktdetailseite geöffnet.

![PLP](assets/catalog-pdp.png)

## Die Vorlagen {#templates}

### Allgemeine Vorlagen {#generic}

Die generische Venia-Katalogvorlage verwendet die Produktlisten-Kernkomponente. Diese Komponente zeigt das Kategoriebild (sofern verfügbar) und Produkte aus der Kategorie an.
![Kategorievorlage](assets/category-template.png)

Die generische Venia-Produktvorlage verwendet die Produktdetails-Kernkomponente. Diese Komponente zeigt Produktinformationen für verschiedene Produktarten und Aktionen zum Hinzufügen zum Warenkorb an.
![Produktvorlage](assets/product-template.png)

### Vorlagen bearbeiten {#edit-templates}

Vorlagen können bearbeitet werden, indem Sie entweder direkt die Vorlagenseite öffnen oder beim Durchsuchen einer Produktkatalogseite in den Bearbeitungsmodus wechseln. Denken Sie daran, dass durch Ändern der Seite die Vorlage und nicht nur die spezifische Seite des Produkts/der Kategorie geändert wird.

### Kategorie- oder produktspezifische Vorlagen {#specific}

CIF unterstützt mehrere Vorlagen mit nur wenigen Klicks. Um eine andere Vorlage zu erstellen, wählen Sie die generische Vorlage aus der entsprechenden Kategorie aus und erstellen Sie eine neue Seite mithilfe der **Erstellen** Aktion.

![Vorlagenseite erstellen](assets/create-template-page.png)

Wählen Sie die entsprechende Produkt- oder Kategorievorlage aus.

![Vorlagenauswahl erstellen](assets/create-template-select.png)

Geben Sie den Titel ein und erstellen Sie die Seite.

![Vorlagentyp erstellen](assets/create-template-enter.png)

Beachten Sie, dass Sie jetzt eine bestimmte Vorlage unter der generischen haben.

![Erstellen der Vorlagenhierarchie](assets/create-template-hierachry.png)

Öffnen Sie die Vorlage. Sie sieht genau wie die allgemeine Kategorievorlage aus.

![Vorlage neu erstellen](assets/create-template-new.png)

Fügen Sie oben auf der Seite ein Bild hinzu.

![Vorlagenaktualisierung erstellen](assets/create-template-update.png)

Die Vorlage kann mit jeder Kategorie/jedem Produkt in der Vorschau angezeigt werden. Öffnen **Seiteninformationen** und wählen Sie **Anzeigen mit Kategorie/Produkt**. Wählen Sie das Produkt/die Kategorie aus der Auswahl aus, um eine Vorschau mit diesem Produkt/dieser Kategorie zu erhalten. Auswählen **Look kaufen** -Kategorie, um eine Vorschau der aktualisierten Vorlage zu erhalten.

![Vorlage erstellen ](assets/create-template-picker.png)

Nun müssen wir diese Vorlage der jeweiligen Kategorie zuweisen. Öffnen Sie die Eigenschaften in **Seiteninformationen** und wechseln Sie zur Registerkarte &quot;Commerce&quot;. Klicken Sie auf das Ordnersymbol, um die **Look kaufen** aus der Kategorieauswahl. Es ist möglich, einer Vorlage mehrere Kategorien und auch Unterkategorien zuzuweisen, indem Sie das Kontrollkästchen aktivieren.

![Vorlagenzuordnung erstellen](assets/create-template-associate.png)

Gehen Sie zurück zur Hauptseite und klicken Sie auf **Look kaufen** -Kategorie, um die spezifische Vorlage anzuzeigen. Alle anderen Kategorien verwenden weiterhin die generische Vorlage.

![Vorlagenergebnis erstellen](assets/create-template-result.png)

Derselbe Workflow kann angewendet werden, um individuelle Produktvorlagen zu erstellen.

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil der Journey abgeschlossen haben, sollten Sie:

* Konzepte von Katalogvorlagen verstehen
* Funktionsweise generischer Vorlagen
* eine individuelle Vorlage erstellt haben

Machen Sie sich mit diesem Wissen vertraut und fahren Sie mit dem Journey fort, indem Sie das Dokument erneut überprüfen. [Erlebnisse im gestaffelten Produktkatalog verwalten](staged-catalog.md), wo Sie erfahren, wie Sie mit gestaffelten Produktdaten und AEM Launches arbeiten.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, zum nächsten Teil der Journey zu wechseln, indem Sie sich das Dokument ansehen. [Erlebnisse im gestaffelten Produktkatalog verwalten](staged-catalog.md)Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte ermöglichen, aber nicht auf der Headless-Journey weiterarbeiten müssen:

* [Erstellen mehrerer Kategorie- und Produktseiten](/help/commerce-cloud/authoring/multi-template-usage.md)
* [Migrationshandbuch für den Experience Manager Cloud Service](/help/commerce-cloud/migration.md) - Migration von einer alten Version zum AEM Commerce Integration Framework (CIF)-Add-on
