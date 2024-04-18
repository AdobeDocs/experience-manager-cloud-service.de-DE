---
title: Dropdown-Listenoptionen aus URL laden
description: Die Optionen der Dropdown-Liste sind in einer gesonderten Tabelle enthalten und werden dann über die angegebene URL in die primäre Tabelle importiert.
feature: Edge Delivery Services
source-git-commit: 2affe155b285986128487043fcc4f2938fc15842
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 3%

---


# Dropdown-Listenoptionen aus URL laden

Forms enthält häufig Dropdown-Menüs, aus denen Benutzer vordefinierte Optionen auswählen können. Diese Optionen werden normalerweise im Formular selbst definiert, aber die Verwaltung langer Listen kann schwerfällig sein. In diesem Handbuch wird beschrieben, wie Sie die Formularbearbeitung verbessern können, indem Sie Dropdown-Optionen aus einer separaten Tabelle über eine URL laden.


Die Vorteile des Ladens von Dropdown-Optionen aus einer separaten Tabelle sind:

* Vereinfachte Verwaltung: Verwaltung von Dropdown-Optionen an einem zentralen Ort, um Aktualisierungen und Ergänzungen zu erleichtern.
* Verbesserte Effizienz: Manuelles Hinzufügen langer Optionslisten innerhalb der Formulardefinition ist nicht erforderlich.




![Dropdown-Optionen](/help/forms/assets/drop-down-options.png)


Am Ende dieses Artikels werden Sie Folgendes gelernt haben:

* [Optionen in einer separaten Tabelle definieren](#define-options)
* [URL hinzufügen, um Dropdown-Listenoptionen zu laden](#add-url)

## Optionen in einem separaten Blatt definieren {#define-options}

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

1. Vorschau erstellen und veröffentlichen `shared-country` Tabellenblatt verwenden [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   Siehe URL, die die `shared-country` sheet: https://main—wefinance—wkndforms.hlx.live/inquiry.json?sheet=country

>[!NOTE]
>
> `?sheet=country` ist ein Abfrageparameter, der an die URL angehängt wird. Dieser Parameter gibt die JSON an, die basierend auf der `shared-country` Blatt. Es wird zur JSON-Datei umgeleitet, die Informationen zu verschiedenen Ländern enthält.

## URL hinzufügen, um Dropdown-Listenoptionen zu laden{#add-url}

Die `Options` -Eigenschaft eines `select` -Feld akzeptiert eine URL. Die URL gibt ein JSON-Array zurück, das als Optionen für die `Destination` Dropdown-Liste. So fügen Sie die URL zum Laden der Dropdown-Listenoptionen hinzu:

1. Wechseln Sie zu Ihrem AEM-Projektordner auf Microsoft® SharePoint oder Google Drive und öffnen Sie die Tabelle. Sie können auch eine neue Tabelle für ein Formular erstellen.
1. URL kopieren von `shared-country` und fügen Sie es in das `Options` Spalte für die `Destination` -Feld.

   ![Abfragetabelle](/help/forms/assets/drop-down-enquiry.png)

1. Erstellen Sie eine Vorschau und veröffentlichen Sie das Blatt mit [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).


   ![Dropdown-Liste für Land](/help/forms/assets/load-dropdown-options-form.png)

Weitere Informationen finden Sie unter [Fragenübersicht](/help/forms/assets/enquiry-options.xlsx) , um die URL zum Laden der Dropdown-Listenoptionen hinzuzufügen.

Nach der Integration der URL in die Formulardefinition zum Laden der Dropdown-Listenoptionen werden die Optionen für die `Destination` Dropdown-Liste beginnen, die über die URL angezeigt wird.

Siehe URL unten, in der die Variable `enquiry` Formular mit den im separaten Blatt gespeicherten Optionen:

https://main--wefinance--wkndforms.hlx.live/enquiry-form

## Siehe auch

{{see-more-forms-eds}}


