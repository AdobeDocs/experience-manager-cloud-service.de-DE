---
title: 'Herunterladen von Dropdown-Listenoptionen über eine URL oder ein anderes Blatt für Edge Delivery Services für AEM Forms as a Cloud Service:'
description: Die Dropdown-Listenoptionen sind in einer gesonderten Tabelle enthalten und werden dann über die angegebene URL in die primäre Tabelle importiert.
feature: Edge Delivery Services
exl-id: 5b0bc1b6-6e33-41f3-b7c1-4d997787b6cd
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 100%

---


# Optionen aus einer URL oder einem anderen Blatt für Edge Delivery Services für AEM Forms as a Cloud Service

Forms enthält häufig Dropdown-Menüs, aus denen Benutzende vordefinierte Optionen auswählen können. Diese Optionen werden normalerweise im Formular selbst definiert, aber die Verwaltung langer Listen kann umständlich sein. Dieses Handbuch beschreibt, wie Sie die Bearbeitung von Formularen verbessern können, indem Sie Dropdown-Optionen aus einer separaten Tabelle über eine URL laden.


Die Vorteile des Ladens von Dropdown-Optionen aus einer separaten Tabelle sind:

- Vereinfachte Verwaltung: Verwaltung von Dropdown-Optionen an einer zentralen Stelle, um Aktualisierungen und Ergänzungen zu erleichtern.
- Verbesserte Effizienz: Manuelles Hinzufügen langer Optionslisten innerhalb der Formulardefinition ist nicht erforderlich.

![Dropdown-Optionen](/help/forms/assets/drop-down-options.png)


Am Ende dieses Artikels werden Sie Folgendes gelernt haben:

- [Definieren von Optionen in einer separaten Tabelle](#define-options)
- [Hinzufügen einer URL, um Dropdown-Listenoptionen zu laden](#add-url)

## Definieren von Optionen auf einem separaten Blatt {#define-options}

Definieren von Optionen in einer separaten Kalkulationstabelle

1. Erstellen einer Kalkulationstabelle:
   1. Suchen Sie Ihren AEM-Projektordner in Microsoft® SharePoint oder Google Drive.
   1. Fügen Sie eine neue Tabelle hinzu. Zum Beispiel „shared-country“ (gemeisames Land).
1. Definieren Sie die Optionsspalten:
Fügen Sie zwei Spalten hinzu: „Option“ und „Wert“.
   - „Option“ definiert den im Dropdown-Menü angezeigten Text.
   - „Wert“ definiert den Wert, der übertragen wird, wenn die Option ausgewählt wird.

   >[!NOTE]
   >
   >Wenn sowohl Option als auch Wert identisch sind, ist nur die Spalte „Option“ erforderlich.

1. Füllen Sie die Kalkulationstabelle aus:
Geben Sie Ihre Länderoptionen in die Spalte „Option“ (und ggf. in die Spalte „Wert“) ein.

   Die Struktur finden Sie im folgenden Beispiel.

   ![Dropdown-Liste für Land](/help/forms/assets/drop-down-country-options.png)

1. Erstellen Sie eine Vorschau und veröffentlichen Sie das Blatt `shared-country` unter Verwendung von [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   Wenn das Repository Ihres Projekts beispielsweise „wefinance“ heißt, sich unter dem Konto „wkndform“ befindet und Sie die Verzweigung „main“ verwenden, wird in der URL das Blatt `shared-country` angezeigt:
   `https://main--wefinance--wkndform.aem.live/enquiry.json?sheet=country`
   <!--(https://main--wefinance--wkndform.aem.live/enquiry.json?sheet=country)  -->

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

Um die URL zum Laden der Dropdown-Listenoptionen hinzuzufügen, rufen Sie die [Abfragetabelle](/help/edge/assets/enquiry.xlsx) auf.

Nach der Integration der URL in die Formulardefinition zum Laden der Dropdown-Listenoptionen beginnen die Optionen für die Dropdown-Liste `Destination` aus der URL zu erscheinen.

Wenn das Repository Ihres Projekts beispielsweise „wefinance“ heißt, sich unter dem Konto „wkndform“ befindet und Sie die Verzweigung „main“ verwenden, zeigt die folgende URL das `enquiry`-Formular mit den in dem separaten Blatt gespeicherten Optionen an:

`https://main--wefinance--wkndform.aem.live/enquiry-form`



