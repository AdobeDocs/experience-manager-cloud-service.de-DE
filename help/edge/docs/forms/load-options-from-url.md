---
title: Laden von Dropdown-Listenoptionen aus der URL
description: Die Dropdown-Listenoptionen sind in einer gesonderten Tabelle enthalten und werden dann über die angegebene URL in die primäre Tabelle importiert.
feature: Edge Delivery Services
source-git-commit: 2affe155b285986128487043fcc4f2938fc15842
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 59%

---


# Laden von Dropdown-Listenoptionen aus der URL

Forms enthält häufig Dropdown-Menüs, aus denen Benutzer vordefinierte Optionen auswählen können. Diese Optionen werden normalerweise im Formular selbst definiert, aber die Verwaltung langer Listen kann schwerfällig sein. In diesem Handbuch wird beschrieben, wie Sie die Formularbearbeitung verbessern können, indem Sie Dropdown-Optionen aus einer separaten Tabelle über eine URL laden.


Die Vorteile des Ladens von Dropdown-Optionen aus einer separaten Tabelle sind:

* Vereinfachte Verwaltung: Verwaltung von Dropdown-Optionen an einem zentralen Ort, um Aktualisierungen und Ergänzungen zu erleichtern.
* Verbesserte Effizienz: Manuelles Hinzufügen langer Optionslisten innerhalb der Formulardefinition ist nicht erforderlich.




![Dropdown-Optionen](/help/forms/assets/drop-down-options.png)


Am Ende dieses Artikels werden Sie Folgendes gelernt haben:

* [Definieren von Optionen in einer separaten Tabelle](#define-options)
* [Hinzufügen einer URL, um Dropdown-Listenoptionen zu laden](#add-url)

## Definieren von Optionen auf einem separaten Blatt {#define-options}

Definieren von Optionen in einer separaten Tabelle

1. Erstellen Sie eine Tabelle:
   1. Suchen Sie Ihren AEM Projektordner in Microsoft® SharePoint oder Google Drive.
   1. Fügen Sie ein neues Blatt hinzu. Beispiel: &quot;freigegebenes Land&quot;.
1. Definieren Sie Optionsspalten: Fügen Sie zwei Spalten hinzu: &quot;Option&quot;und &quot;Wert&quot;.
   * &quot;Option&quot; definiert den im Dropdown-Menü angezeigten Text.
   * &quot;Wert&quot;definiert den gesendeten Wert, wenn ein Benutzer die Option auswählt.

   >[!NOTE]
   >
   >Wenn sowohl Option als auch Wert identisch sind, ist nur die Spalte &quot;Option&quot;erforderlich.

1. Füllen Sie das Arbeitsblatt aus: Geben Sie in der Spalte &quot;Option&quot;(und ggf. &quot;Wert&quot;) die Länderoptionen ein.

   Die Struktur finden Sie im folgenden Beispiel.

   ![Dropdown-Liste für Land](/help/forms/assets/drop-down-country-options.png)

1. Erstellen Sie eine Vorschau und veröffentlichen Sie das Blatt `shared-country` unter Verwendung von [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   Die nachfolgende URL öffnet das Blatt `shared-country`: 
https://main--wefinance--wkndforms.hlx.live/enquiry.json?sheet=country

>[!NOTE]
>
> `?sheet=country` ist ein Abfrageparameter, der an die URL angehängt wird. Dieser Parameter gibt die auf dem Blatt `shared-country` basierende JSON-Datei an. Er leitet zur JSON-Datei um, die Informationen zu verschiedenen Ländern enthält.

## Hinzufügen einer URL, um Dropdown-Listenoptionen zu laden{#add-url}

Die `Options`-Eigenschaft eines `select`-Felds akzeptiert eine URL. Die URL gibt ein JSON-Array zurück, das als Optionen für die `Destination`-Dropdown-Liste verwendet wird. So fügen Sie die URL zum Laden der Dropdown-Listenoptionen hinzu:

1. Wechseln Sie in Microsoft® SharePoint oder Google Drive zu Ihrem AEM-Projektordner und öffnen Sie die Kalkulationstabelle. Sie können auch eine neue Kalkulationstabelle für ein Formular erstellen.
1. Kopieren Sie die URL des Blattes `shared-country` und fügen Sie sie in die Spalte `Options` für das Feld `Destination` ein.

   ![Abfragetabelle](/help/forms/assets/drop-down-enquiry.png)

1. Zeigen Sie eine Vorschau an und veröffentlichen Sie das Blatt mithilfe von [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).


   ![Dropdown-Liste für Land](/help/forms/assets/load-dropdown-options-form.png)

Um die URL zum Laden der Dropdown-Listenoptionen hinzuzufügen, rufen Sie die [Abfragetabelle](/help/forms/assets/enquiry-options.xlsx) auf.

Nach der Integration der URL in die Formulardefinition zum Laden der Dropdown-Listenoptionen beginnen die Optionen für die Dropdown-Liste `Destination` aus der URL zu erscheinen.

Unter der nachstehenden URL finden Sie das `enquiry`-Formular, in dem die in einem separaten Blatt gespeicherten Optionen angezeigt werden:

https://main--wefinance--wkndforms.hlx.live/enquiry-form

## Siehe auch

{{see-more-forms-eds}}


