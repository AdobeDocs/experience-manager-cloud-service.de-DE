---
title: Suchen nach Assets in Content Hub
description: Informationen zum Suchen nach Assets in [!DNL Content Hub]
role: User
exl-id: 8578d7d0-32b9-4e5c-80ef-3827e358ac6c
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: ht
source-wordcount: '630'
ht-degree: 100%

---

# Suchen nach Assets in [!DNL Content Hub] {#search-assets}

Wenn Sie über eine große Anzahl von Assets in Ihrem Repository verfügen, kann die Suche nach dem richtigen Asset zeitaufwendig sein. Mit der Suche in [!DNL The Content Hub] können Sie nach den genehmigten Assets suchen, damit Sie zusätzliche Aktionen für sie ausführen können, z. B. Sammlungen herunterladen, freigeben oder erstellen. Sie können verschiedene Funktionen nutzen, um Ihre Suchergebnisse einzugrenzen, z. B. die textbasierte Suche, die Verwendung von Filtern, die Durchführung von Tag- oder Smart-Tag-spezifischen Suchen sowie die Suche nach einem bestimmten Dateiformat.

## Voraussetzungen {#prerequisites}

[Content Hub-Benutzende](deploy-content-hub.md#onboard-content-hub-users) können die in diesem Artikel genannten Aktionen ausführen.

## Sie können nach Folgendem suchen  {#what-you-can-search}

Die Suche in [!DNL Content Hub] bietet Ergebnisse basierend auf Folgendem:

* **Übereinstimmender Text:** Mit der Suche in [!DNL Content Hub] können Sie anhand des Namens oder der Beschreibung nach einem Asset suchen. Sie können eine auf einem Suchbegriff basierende Suche durchführen, bei der der Suchbegriff mit dem in den Eigenschaften eines Assets verfügbaren Text verglichen wird.

* **Übereinstimmender Kontext:**: Die Ergebnisliste der Suche in [!DNL Content Hub] enthält ungefähre Ergebnisse von Assets, die Sie basierend auf dem übereinstimmenden Kontext erhalten. Wenn Sie beispielsweise `cool` in die Suchleiste eingeben, werden die mit `winter`, `snow`, `cold surroundings` verbundenen Assets in der Suchliste angezeigt.

* **Asset-Informationen (Titel, Tags oder Smart-Tags):** [!DNL Content Hub] verwendet einen intelligenten Suchalgorithmus, um die Suchergebnisse präzise und so relevant wie möglich hierarchisch zu sortieren. [Metadaten](#asset-properties.md) stellen die Sammlung aller für ein Asset verfügbaren Daten dar, sind aber nicht unbedingt im Asset selbst enthalten. [Sie helfen Ihnen dabei, Assets genauer einzuteilen. Außerdem erweisen sie sich als nützlich, wenn die Menge digitaler Informationen ansteigt](/help/assets/configure-content-hub-ui-options.md##configure-metadata-search-content-hub).

* **Datum der letzten Änderung:** Die zuletzt geänderten Assets werden oben in der Liste der Suchergebnisse angezeigt. Sie können den Datumsbereich auch nach Bedarf filtern.

* **Nutzung:** Die häufig verwendeten Assets werden oben in der Suchliste angezeigt.

* **Suchverlauf:** Klicken Sie in das Suchfeld, ohne ein Zeichen einzugeben, um Ihren Suchverlauf abzurufen. Sie können auch einen bestimmten Suchbegriff aus dem Verlauf entfernen. Der Suchverlauf wird im Cache-Speicher eines Webbrowsers gespeichert. Das bedeutet, dass Sie den Suchverlauf nicht mehr anzeigen können, wenn Sie in einem anderen Browser auf die Suche in [!DNL Content Hub] zugreifen oder den Cache-Speicher des Browsers leeren.

* **Suche während der Eingabe:** Die Suche in [!DNL Content Hub] verbessert Ihr Sucherlebnis, indem mit Beginn Ihrer Eingabe Vorschläge für die automatische Vervollständigung angezeigt werden.

## Einfache Suche {#basic-search}

Um eine einfache Suche in [!DNL the Content Hub] durchzuführen, navigieren Sie zur Suchleiste und geben Sie den Suchbegriff an, nach dem Sie suchen müssen. Navigieren Sie zu den im linken Bereich verfügbaren Filtern und wenden Sie sie an, um Ihre Suchergebnisse einzugrenzen.

Suchen Sie beispielsweise nach allen **[!UICONTROL JPEG]**-Bildern mit dem Suchbegriff `architect` darin, der im letzten Jahr geändert wurde. Gehen Sie für die Durchführung dieses Szenarios wie folgt vor:

1. Geben Sie `architect` als Suchbegriff an.

1. Navigieren Sie zum Bedienfeld „Filter“ > **[!UICONTROL Format]** und wählen Sie **[!UICONTROL JPEG]** aus.

1. Navigieren Sie zu **[!UICONTROL Geändert]** > und geben Sie den Datumsbereich an.

   ![Einfache Suche](assets/basic-search.png)

## Eingrenzen Ihrer Suchergebnisse mithilfe von Filtern {#narrow-down-search-results}

Verwenden Sie das Bedienfeld „Filter“, um nach auf Metadaten basierenden Assets zu suchen. Sie können Suchergebnisse anhand verschiedener Suchprädikate filtern. Sie können alle passenden Eigenschaften auswählen, um Ihre Suchergebnisse zu minimieren oder einzugrenzen. Wenn Sie mehrere Optionen in einem Filter auswählen, zeigt Content Hub die Assets an, die mit einer der in einem Filter ausgewählten Optionen übereinstimmen. Wenn Sie jedoch mehrere Optionen in verschiedenen Filtern auswählen, zeigt Content Hub nur die Assets an, die mit allen Optionen übereinstimmen, die in allen Filtern ausgewählt wurden, um Ihre Suchergebnisse einzugrenzen.

Zu den Standardfiltern gehören „Dateiformat“, „Genehmigt von“, „Datum der Genehmigung“, „Abgelaufene Assets“, „Nicht abgelaufene Assets“ sowie „Ablaufdatum“. Admins können auch die Filter konfigurieren, die in der Filterliste angezeigt werden. Weitere Informationen finden Sie unter [Konfigurieren der Benutzeroberfläche von Content Hub](configure-content-hub-ui-options.md#configure-filters-content-hub).

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

## Weitere Aktionen bei der Suche {#do-more-with-search}

[!DNL The Content Hub] ist nicht auf die Suche beschränkt, sondern Sie können direkt über die Benutzeroberfläche der Suche oder der Vorschau auch zusätzliche Aktionen ausführen, wie z. B. [Herunterladen](download-assets-content-hub.md), [Freigeben](share-assets-content-hub.md) und [Assets zur Sammlung hinzufügen](collections-content-hub.md). Wählen Sie die Assets auf der Seite mit den Suchergebnissen aus, um diese Optionen anzuzeigen.
