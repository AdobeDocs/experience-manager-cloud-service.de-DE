---
title: Verwalten von Produktkatalogseiten und -vorlagen
description: Erfahren Sie, wie Sie Produktkatalogseiten und -vorlagen verwalten
exl-id: 0d795d85-c865-40d5-941e-e02ee96fdd11
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 100%

---

# Verwalten von Produktkatalogseiten und -vorlagen {#product-catalog}

Hier erfahren Sie, wie Sie Produktkatalogseiten und -vorlagen verwalten.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der Journey für das AEM Content and Commerce-Authoring, [Einstieg in die Grundlagen des AEM-CIF-Authorings](getting-started.md), haben Sie die Grundlagen des CIF-Authorings kennengelernt.

Dieser Artikel baut auf diesen Grundlagen auf.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie Produktkatalogseiten und -vorlagen verwalten. Nach dem Lesen sollten Sie:

* die Konzepte von Katalogvorlagen verstehen
* die Funktionsweise generischer Vorlagen verstehen
* eine individuelle Vorlage erstellt haben

## Das Grundkonzept {#basic-concept}

Die Venia-Storefront verfügt über eine typische Produktkatalogoberfläche mit Navigation, Landingpage sowie Seiten für Kategorien (PLP) und Produktdetails (PDP).

Katalogseiten werden dynamisch mithilfe einer AEM-CIF-Katalogvorlage und Echtzeit-Produktdaten erstellt, die bei Bedarf vom Commerce-Endpunkt abgerufen werden. Jeder Katalog verfügt über eine generische Vorlage für Produkt- und Kategorieseiten.
![Katalogstruktur](assets/catalog-structure.png)

Die Navigationskomponente zeigt Inhalts- und Katalogseiten an. Es ist möglich, die Katalog-Landingpage oder die Kategorien der ersten Ebene in der Navigation anzuzeigen. Wenn Sie den Mauszeiger über eine Kategorie bewegen, werden Kategorien der zweiten Ebene als zweite Zeile angezeigt.
![Katalognavigation](assets/catalog-navigation.png)

Durch Klicken auf eine Kategorie wird die Kategorieseite (oder Produktlistenseite) geöffnet.

![PLP](assets/catalog-plp.png)

Durch Klicken auf ein Produkt wird die Produktdetailseite geöffnet.

![PLP](assets/catalog-pdp.png)

## Die Vorlagen {#templates}

### Generische Vorlagen {#generic}

Die generische Venia-Katalogvorlage verwendet die Produktlisten-Kernkomponente. Diese Komponente zeigt das Kategoriebild (sofern verfügbar) und Produkte aus der Kategorie an.
![Kategorievorlage](assets/category-template.png)

Die generische Venia-Produktvorlage verwendet die Produktdetails-Kernkomponente. Diese Komponente zeigt Produktinformationen für verschiedene Produktarten und die Aktion „In den Warenkorb“ an.
![Produktvorlage](assets/product-template.png)

### Bearbeiten von Vorlagen {#edit-templates}

Vorlagen können bearbeitet werden, indem Sie die Vorlagenseite direkt öffnen oder indem Sie beim Durchsuchen einer Produktkatalogseite in den Bearbeitungsmodus wechseln. Denken Sie daran, dass durch Ändern der Seite die Vorlage und nicht nur die spezifische Seite des Produkts/der Kategorie geändert wird.

### Kategorie- oder produktspezifische Vorlagen {#specific}

CIF unterstützt mehrere Vorlagen mit nur wenigen Klicks. Um eine andere Vorlage zu erstellen, wählen Sie die generische Vorlage aus der entsprechenden Kategorie aus und erstellen Sie eine neue Seite mithilfe der Aktion **Erstellen**.

![Erstellen einer Vorlagenseite](assets/create-template-page.png)

Wählen Sie die entsprechende Produkt- oder Kategorievorlage aus.

![Erstellen einer Vorlage: Auswählen ](assets/create-template-select.png)

Geben Sie den Titel ein und erstellen Sie die Seite.

![Erstellen einer Vorlage: Eingeben](assets/create-template-enter.png)

Beachten Sie, dass jetzt eine spezifische Vorlage unter der generischen Vorlage vorhanden ist.

![Erstellen der Vorlagenhierarchie](assets/create-template-hierachry.png)

Öffnen Sie die Vorlage. Sie sieht genau wie die generische Kategorievorlage aus.

![Neuerstellen einer Vorlage](assets/create-template-new.png)

Fügen Sie oben auf der Seite ein Bild hinzu.

![Vorlagenaktualisierung erstellen](assets/create-template-update.png)

Die Vorlage kann mit jeder Kategorie/jedem Produkt in der Vorschau angezeigt werden. Öffnen Sie **Seiteninformationen** und wählen Sie **Mit Kategorie/Produkt anzeigen**. Wählen Sie das Produkt/die Kategorie aus der Auswahl aus, um eine Vorschau mit diesem Produkt/dieser Kategorie zu erhalten. Wählen Sie die Kategorie **Den Look kaufen**, um eine Vorschau der aktualisierten Vorlage zu erhalten.

![Vorlage erstellen ](assets/create-template-picker.png)

Nun müssen Sie diese Vorlage der jeweiligen Kategorie zuweisen. Öffnen Sie „Eigenschaften“ im Menü **Seiteninformationen** und wechseln Sie zur Registerkarte „Commerce“. Klicken Sie in der Kategorieauswahl auf das Ordnersymbol, um die Kategorie **Shop the Look** auszuwählen. Es ist möglich, einer Vorlage mehrere Kategorien und auch Unterkategorien zuzuweisen, indem Sie das Kontrollkästchen aktivieren.

![Vorlagenzuordnung erstellen](assets/create-template-associate.png)

Navigieren Sie zurück zur Hauptseite und klicken Sie auf die Kategorie **Shop The Look**, um die spezifische Vorlage anzuzeigen. Alle anderen Kategorien verwenden weiterhin die generische Vorlage.

![Vorlagenergebnis erstellen](assets/create-template-result.png)

Derselbe Workflow kann angewendet werden, um individuelle Produktvorlagen zu erstellen.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der Tour abgeschlossen haben, sollten Sie:

* die Konzepte von Katalogvorlagen verstehen
* die Funktionsweise generischer Vorlagen verstehen
* eine individuelle Vorlage erstellt haben

Bauen Sie auf diesem Wissen auf und fahren Sie mit Ihrer Tour fort, indem Sie jetzt das Dokument [Verwalten von Erlebnissen im Staging-Produktkatalog](staged-catalog.md) durchgehen, in dem Sie erfahren, wie Sie mit Staging-Produktdaten und AEM-Launches arbeiten.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, zum nächsten Teil der Tour voranzuschreiten, indem Sie jetzt das Dokument [Verwalten von Erlebnissen im gestaffelten Produktkatalog](staged-catalog.md) durchgehen, Sie finden aber im Folgenden noch einige zusätzliche, optionale Ressourcen, die einige der in diesem Dokument erwähnten Konzepte vertiefen. Diese sind jedoch nicht zwingend erforderlich, um mit der Headless-Tour fortzufahren:

* [Erstellen mehrerer Kategorie- und Produktseiten](/help/commerce-cloud/authoring/multi-template-usage.md)
* [Migrationshandbuch für Experience Manager Cloud Service](/help/commerce-cloud/migration.md) – Migration von einer alten Version zum AEM Commerce Integration Framework (CIF)-Add-on
