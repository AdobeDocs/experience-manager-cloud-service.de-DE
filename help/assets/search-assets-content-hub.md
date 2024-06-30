---
title: Suchen nach Assets in Content Hub
description: Erfahren Sie, wie Sie Assets in suchen [!DNL Content Hub]
role: User
source-git-commit: 5a968440c8841abe7af2c81c4af12258b7e4547f
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---


# Assets suchen in [!DNL Content Hub] {#search-assets}

![Asset-Bannerbild freigeben](assets/search.png)

Wenn Sie eine große Anzahl von Assets in Ihrem Repository haben, ist die Suche nach dem richtigen Asset zeitaufwendig. [!DNL The Content Hub] Die Suche bietet Ihnen die Möglichkeit, nach den genehmigten Assets zu suchen, damit Sie zusätzliche Aktionen daran durchführen können, z. B. Sammlungen herunterladen, freigeben oder erstellen können. Sie können verschiedene Funktionen nutzen, um Ihre Suchergebnisse einzugrenzen, z. B. die textbasierte Suche, die Verwendung von Filtern, die Durchführung von Tags oder die Suche nach Smart-Tags, die Suche nach einem bestimmten Dateiformat usw.

## Voraussetzungen {#prerequisites}

[Content Hub-Benutzer](deploy-content-hub.md#onboard-content-hub-users) kann die in diesem Artikel erwähnten Aktionen ausführen.

## Was Sie suchen können  {#what-you-can-search}

Die [!DNL Content Hub] Die Suche liefert Ergebnisse basierend auf:

* **Abgleichtext:** Die [!DNL Content Hub] Mit der Suche können Sie anhand des Namens oder der Beschreibung nach einem Asset suchen. Sie können eine schlüsselwortbasierte Suche durchführen, bei der der Suchbegriff mit dem in den Eigenschaften eines Assets verfügbaren Text verglichen wird.

* **Übereinstimmungskontext:** [!DNL Content Hub] Die Liste der Suchergebnisse enthält ungefähre Ergebnisse von Assets, die Sie basierend auf dem entsprechenden Kontext erhalten. Wenn Sie beispielsweise `cool` in der Suchleiste die Assets, die sich auf `winter`, `snow`, `cold surroundings`, in der Suchliste angezeigt.

* **Asset-Informationen (Titel, Tags oder Smart-Tags):** [!DNL Content Hub] verwendet intelligente Suchalgorithmen, um Suchergebnisse präzise und so relevant wie möglich zu ordnen. [Metadaten](#asset-properties.md) ist die Sammlung aller für ein Asset verfügbaren Daten, die jedoch nicht unbedingt in diesem Asset enthalten sein müssen. [Dies hilft Ihnen bei der weiteren Kategorisierung von Assets und ist hilfreich, wenn die Menge digitaler Informationen zunimmt](/help/assets/configure-content-hub-ui-options.md##configure-metadata-search-content-hub).

* **Datum der letzten Änderung:** Die kürzlich geänderten Assets werden oben in der Liste der Suchergebnisse angezeigt. Sie können den Datumsbereich auch nach Bedarf filtern.

* **Verwendung:** Die häufig verwendeten Assets werden oben in der Suchliste angezeigt.

* **Suchverlauf:** Klicken Sie in das Suchfeld, ohne ein Zeichen einzugeben, um Ihren Suchverlauf abzurufen. Sie können auch einen bestimmten Suchbegriff aus dem Verlauf entfernen. Der Suchverlauf wird im Cache-Speicher eines Webbrowsers gespeichert, d. h. wenn Sie auf die [!DNL Content Hub] in einem anderen Browser suchen oder den Cache-Speicher des Browsers leeren, können Sie den Suchverlauf nicht mehr anzeigen.

* **Suchen Sie bei der Eingabe:** Die [!DNL Content Hub] Die Suche verbessert Ihr Sucherlebnis, indem Sie beim Eingeben Vorschläge zur automatischen Vervollständigung machen.

## Einfache Suche {#basic-search}

So führen Sie eine einfache Suche durch [!DNL the Content Hub], navigieren Sie zur Suchleiste und geben Sie den Suchbegriff an, den Sie suchen möchten. Navigieren Sie zu den im linken Bereich verfügbaren Filtern und wenden Sie sie an, um Ihre Suchergebnisse einzugrenzen.

Suchen Sie beispielsweise nach allen **[!UICONTROL JPEG]** Bilder mit Keyword `architect` und die im letzten Jahr geändert wird. Führen Sie die folgenden Schritte aus, um dieses Szenario auszuführen:

1. Angeben `architect` als Suchbegriff.

1. Navigieren Sie zum Filterbereich > **[!UICONTROL Format]** > Auswählen **[!UICONTROL JPEG]**.

1. Navigieren Sie zu **[!UICONTROL Geändert]** > geben Sie den Datumsbereich an.

   ![Grundlegende Suche](assets/basic-search.png)

## Schränken Sie Ihre Suchergebnisse mithilfe von Filtern ein. {#narrow-down-search-results}

Verwenden Sie das Bedienfeld Filter , um basierend auf Metadaten nach Assets zu suchen. Sie können Suchergebnisse anhand verschiedener Sucheigenschaften filtern. Sie können alle geeigneten Eigenschaften auswählen, um Ihre Suchergebnisse zu minimieren oder einzuschränken. Wenn Sie mehrere Optionen in einem Filter auswählen, zeigt Content Hub die Assets an, die mit einer der in einem Filter ausgewählten Optionen übereinstimmen. Wenn Sie jedoch mehrere Optionen über Filter hinweg auswählen, zeigt Content Hub nur die Assets an, die mit allen über Filter hinweg ausgewählten Optionen übereinstimmen, um Ihre Suchergebnisse einzugrenzen.

Die Standardfilter enthalten das Dateiformat, das Datum der Genehmigung, das Datum der Genehmigung, abgelaufene und nicht abgelaufene Assets sowie das Ablaufdatum. Administratoren können auch die Filter konfigurieren, die in der Filterliste angezeigt werden. Weitere Informationen finden Sie unter [Benutzeroberfläche von Content Hub konfigurieren](configure-content-hub-ui-options.md#configure-filters-content-hub).

<!--

<table>
    <tbody>
     <tr>
      <th><strong>Search Predicate</strong></th>
      <th><strong>Description</strong></th>
      <th><strong>Properties</strong></th>
     </tr>
     <tr>
      <td> Campaigns </td>
      <td> Allows you to search using planned activity performed to take any particular action. For example, advertisement campaign run on Ferrari to know the understand the interests of people using number of clicks people perform.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Channels </td>
      <td> Helps you to understand the path from where the asset is coming from. For example, web, social media, books, catalog, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Region </td>
      <td> Helps you to understand the location where the asset is created. For example, Japan, EMEA, Worldwide, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Keywords </td>
      <td> Keyword helps you search using terms or the words that you enter based on the topic. For example, images, low-resolution, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Timeframe </td>
      <td> Helps you search assets using timeline. For example, search by year 2024, Q3 2023, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td>File format</td>
      <td>Composition of an asset. The supported assets include image, document, video, printable media, and so on.</td>
      <td>
        <ul>
            <li>[!UICONTROL JPEG]</li> 
            <li>[!UICONTROL Quicktime]</li> 
            <li>[!UICONTROL PNG]</li> 
            <li>[!UICONTROL WebP]</li> 
            <li>[!UICONTROL MP4]</li> 
            <li>[!UICONTROL Plain]</li> 
            <li>[!UICONTROL PDF]</li>
            <li>[!UICONTROL SVG + XML]</li>
        </ul>
      </td>
     </tr>
     <tr>
      <td>Tags</td>
      <td>Tags help you categorize assets that can be browsed and searched more efficiently based on hierarchical taxonomies.</td>
      <td>
        <ul>
            <li>Field label</li>
            <li>Property name</li>
            <li>Path</li>
            <li>Description</li>
        </ul>
      </td>
     </tr>
     <!--<tr>
      <td>Subject</td>
      <td>Classification of assets based on their theme. For example, colorful, hiking, outdoors.</td>
      <td>NA</td>
     </tr>
          <tr>
      <td>Last modified</td>
      <td>Search assets based on their last modification. Specify the date range using the Start date and End date fields.</td>
      <td>
        <ul>
            <li>Range text (From)</li> 
            <li>Range text (To) </li>
        </ul>
      </td>
     </tr>    
     <!--<tr>
      <td>Asset ID</td>
      <td>Unique number that identifies the asset.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Colors </td>
      <td> Helps you search assets using colors that are automatically identified in an asset using Adobe's Sensei AI capabilities.</td>
      <td>NA</td>
     </tr>  
    </tbody>
   </table>

-->

## Weitere Informationen zur Suche {#do-more-with-search}

[!DNL The Content Hub] ist nicht auf die Suche beschränkt, sondern ermöglicht Ihnen, zusätzliche Aktionen durchzuführen, z. B. [herunterladen](download-assets-content-hub.md), [share](share-assets-content-hub.md), und [Assets zur Sammlung hinzufügen](collections-content-hub.md), direkt über die Such- oder Vorschaufunktion. Wählen Sie die Assets auf der Suchergebnisseite aus, um diese Optionen anzuzeigen.
