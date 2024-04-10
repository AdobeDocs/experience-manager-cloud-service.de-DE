---
title: Dropdown-Listenoptionen aus URL laden
description: Die Optionen der Dropdown-Liste sind in einer separaten Tabelle enthalten und werden dann über die bereitgestellte URL in die primäre Tabelle importiert.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: eadfc3d448bd2fadce08864ab65da273103a6212
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 2%

---


# Dropdown-Listenoptionen von URL laden

In Edge Delivery Services-Formularen haben Benutzende die Möglichkeit, einen Wert aus einem vordefinierten Satz von Optionen auszuwählen. Formularautoren verwenden die `select` -Element, das eine Liste von Auswahlmöglichkeiten bereitstellt.
Beispiel: `enquiry` Das Formular enthält ein Dropdown-Menü zur Auswahl von Ländern, aus dem die Benutzer eine Reihe vordefinierter Länder auswählen können. Sie können sehen, dass diese Liste eine lange Liste von Ländern enthält, die durch Kommas getrennt sind.

![Dropdown-Optionen](/help/forms/assets/drop-down-options.png)

Die Verwaltung langer Listen von Optionen für Dropdown-Menüs kann umständlich sein, wenn sie direkt zum Blatt mit der Formulardefinition hinzugefügt werden. Das Erstellen eines separaten Blatts zum Speichern dieser Dropdown-Optionen kann den Prozess vereinfachen und optimieren. Dieses Blatt dient als zentralisiertes Repository für alle Dropdown-Optionen, angeordnet in einem strukturierten Format. Jede Option wird in einer eigenen Zeile aufgelistet, was die Verwaltung und Aktualisierung erleichtert.

Im Folgenden wird beschrieben, wie der Prozess der Formularerstellung durch Laden der Optionsliste aus einer anderen Tabelle über eine URL verbessert werden kann.

Am Ende dieses Artikels werden Sie Folgendes gelernt haben:

* [Optionen in einer separaten Tabelle definieren](#define-options)
* [Dropdown-Listenoptionen zum Laden der URL hinzufügen](#add-url)

## Optionen in einem separaten Blatt definieren {#define-options}

Erstellen Sie eine Tabelle mit zwei Spalten:`Option` und `Value`, um die Optionen zu definieren:

1. Wechseln Sie zu Ihrem AEM-Projektordner in Microsoft® SharePoint oder dem Google Drive-Ordner.
2. Eine Tabelle mit dem Namen hinzufügen `shared-country` in der Microsoft® SharePoint-Site oder in Ihrem Google Drive-Ordner aus und fügen Sie Folgendes hinzu:

   * **Option**: Stellt die Anzeigewerte von Optionen im Dropdown-Menü dar.
   * **Wert**: Stellt den gesendeten Wert dar, wenn ein Benutzer die Option auswählt.

   >[!NOTE]
   >
   > Wenn der Wert und die Option für eine Dropdown-Option identisch sind, kann die Tabelle nur den **Option** Spalte.

   Fügen wir ein neues Blatt hinzu, [geteiltes Land](/help/forms/assets/enquiry-options.xlsx) für die in der `Destination` Dropdown-Liste im `enquiry` Formular.

   Siehe Abbildung unten, in der Folgendes dargestellt wird `shared-country` Kalkulationstabelle:

   ![Dropdown für Land](/help/forms/assets/drop-down-country-options.png)
3. Vorschau anzeigen und veröffentlichen `shared-country` Blatt mit [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   Verweisen Sie auf die URL, die `shared-country` Blatt: https://main--wefinance--wkndforms.hlx.live/enquiry.json?sheet=country

>[!NOTE]
>
> `?sheet=country` ist ein Abfrageparameter, der an die URL angehängt wird. Dieser Parameter gibt die JSON-Datei an, die anhand des `shared-country` Blatt. Sie werden zur JSON-Datei weitergeleitet, die Informationen zu verschiedenen Ländern enthält.

## Dropdown-Listenoptionen zum Laden der URL hinzufügen{#add-url}

Die `Options` Eigenschaft eines `select` akzeptiert eine URL. Die URL gibt ein JSON-Array zurück, das als Optionen für das `Destination` Dropdown-Liste. So fügen Sie die Dropdown-Listenoptionen URL zum Laden hinzu:

1. Wechseln Sie zum AEM-Projektordner in Microsoft® SharePoint oder Google Drive und öffnen Sie die Tabelle. Sie können auch eine neue Tabelle für ein Formular erstellen.
1. URL kopieren von `shared-country` Blatt und fügen Sie es in die `Options` Spalte für die `Destination` Feld.

   ![Abfragetabelle](/help/forms/assets/drop-down-enquiry.png)

1. Anzeigen einer Vorschau und Veröffentlichen des Arbeitsblatts mithilfe von [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).


   ![Dropdown für Land](/help/forms/assets/load-dropdown-options-form.png)

Weitere Informationen finden Sie im [Anfrage-Tabelle](/help/forms/assets/enquiry-options.xlsx) , um die Dropdown-Listenoptionen URL zum Laden hinzuzufügen.

Nach der Integration der URL in die Dropdown-Listenoptionen für die Formulardefinition zum Laden werden die Optionen für die `Destination` Dropdown-Liste, die von der URL aus angezeigt wird.

Siehe die unten stehende URL, die Folgendes anzeigt: `enquiry` Formular mit den in der separaten Tabelle gespeicherten Optionen:

https://main--wefinance--wkndforms.hlx.live/enquiry-form

## Siehe auch

{{see-more-forms-eds}}


