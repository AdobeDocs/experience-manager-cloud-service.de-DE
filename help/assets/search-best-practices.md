---
title: Best Practices für die Suche [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]
description: Best Practices zum Suchen, Suchen und Abrufen von Asset-Metadaten in Ihrer Anwendung.
contentOwner: KK
exl-id: 446692de-5cea-4dbd-a98e-ec5177c7017e
source-git-commit: 6638298056f2dae027db4df8c31c3fd59812a56b
workflow-type: tm+mt
source-wordcount: '2544'
ht-degree: 11%

---

# Best Practices für die AEM

[!DNL Adobe Experience Manager Assets] bietet stabile Suchmethoden für Assets, mit denen Sie eine höhere Inhaltsgeschwindigkeit erzielen können. Manchmal kann das Auffinden des richtigen Assets mühsam und zeitaufwendig sein. Daher können Sie Assets suchen in [!DNL Adobe Experience Manager Assets] ist von zentraler Bedeutung für die Nutzung eines digitalen Asset-Managementsystems - sei es für die weitere Verwendung durch Kreative, für eine robuste Verwaltung von Assets durch Geschäftsbenutzer und Marketing-Experten oder für die Verwaltung durch DAM-Administratoren.

Dieses Hilfedokument enthält Best Practices für AEM Suche mithilfe verschiedener Szenarien, damit AEM Benutzer eine einfache bis erweiterte Suche durchführen können.

## Zugriff auf die Experience Manager-Suche {#access-experience-manager-search}

Im Folgenden werden die wichtigsten Schritte beschrieben, die in Experience Manager durchgeführt werden müssen, bevor Sie mit der Suche beginnen:

* Im **Admin-Ansicht**, navigieren Sie zu Assets > Dateien in Experience Manager und klicken Sie auf das Suchsymbol in der oberen Leiste. Alternativ können Sie einen Schrägstrich (/) verwenden, um das Omni-Suchfeld zu öffnen.
Im **Asset-Ansicht**, ist die Suchleiste oben sichtbar und kann direkt aufgerufen werden.
* `Location:Assets` und `Path:/content/dam` sind vorausgewählt, um den Suchbereich auf Ihr Experience Manager Assets-Repository zu beschränken. Wenn Sie zu einem anderen Ordner navigieren, `Path:/content/dam/<folder name>` wird im Omni-Suchfeld angezeigt, um den Suchbereich auf den aktuellen Ordner zu beschränken.

## Grundlegende Suche {#basic-search}

**Szenario 1: Grundlegende Suche mithilfe einer `classic car` als Suchbegriff.**

Bei der Keyword-Suche wird nicht zwischen Groß- und Kleinschreibung unterschieden und es handelt sich um eine Volltextsuche über die Metadatenfelder, die im Asset enthalten sind *Volltextsuche* index (konfigurierbar in der Indexdefinition). Wenn mehrere Keywords verwendet werden, **UND ist der Standardoperator zwischen den Keywords, daher wird eine Suche nach &quot;klassischem Auto&quot;als &quot;klassisches UND Auto&quot;betrachtet**.

Die Suchergebnisse, die in Metadatenfeldern alle Suchbegriffe aufweisen, werden zuerst angezeigt. Danach folgen die Suchergebnisse, die einem oder mehr Suchbegriffen in den Smart-Tags entsprechen. Die ungefähre Reihenfolge der Anzeige von Suchergebnissen lautet:

1. Treffer von `Classic Car` in den verschiedenen Metadatenfeldern.
2. Treffer von `Classic Car` in den Smart-Tags.
3. Treffer von `Classic` oder `Car` in Smart-Tags.

Angeben `classic car` als Suchbegriff ein und klicken Sie auf &quot;Suchen&quot;. Sie können die Suchvorschläge bei der Eingabe des Suchbegriffs in einer Dropdown-Liste anzeigen. Die Suchvorschläge basieren auf dem Inhalt des Suchindex in Ihrer Experience Manager-Implementierung. Wenn Sie die entsprechenden Assets nicht im Dropdown-Menü anzeigen können, drücken Sie die Eingabetaste , um die Ergebnisliste anzuzeigen. Die Ergebnisse werden nach Relevanz sortiert, beginnend mit den nächsten Treffern.

![Grundlegende Suchmethode 1](assets/simple-search-1.png)

Sie können die Suche spezifischer gestalten, indem Sie Ihren Suchbegriff in doppelte Anführungszeichen setzen (&quot;&quot;&quot;). Diese Suche umfasst nur Assets, die die angegebenen Begriffe zusammen enthalten. Die Suchkriterien sehen wie folgt aus: `"classic car"`. Daher enthält die Suche beide Begriffe `classic` und `car` angezeigt.

![Suche nach exakter Übereinstimmung](assets/simple-search-2.png)

Die Suche zeigt ähnliche Ergebnisse an, wenn Sie in der **[!UICONTROL Asset-Ansicht]** sowie.

>[!VIDEO](https://video.tv.adobe.com/v/3425489)

## Dateien und Ordner {#files-folders}

**Szenario 2: Suche nach allen Dateien, die die `classic car` Suchbegriff in `automobile` Ordner.**

Der Filter &quot;Dateien und Ordner&quot;hilft Ihnen bei der Eingrenzung Ihrer Suche. Verwenden Sie je nach Bedarf die in der Dropdownliste verfügbaren Optionen Dateien, Ordner oder Dateien und Ordner . Die Option zur Auswahl zwischen Dateien, Ordnern oder Dateien und Ordnern ist im **[!UICONTROL Admin-Ansicht]** nur. Im **[!UICONTROL Asset-Ansicht]**, gehen Sie zu [!UICONTROL Pfad] und durchsuchen Sie den Ordner, in dem Sie eine Suche durchführen möchten.

* Verwenden Sie die **[!UICONTROL Dateien]** -Option, wenn Sie speziell nach Dateien in einem bestimmten Pfad innerhalb des Repositorys suchen müssen. Sie müssen nicht nach Ordnern im definierten Pfad suchen.
* Verwenden Sie die **[!UICONTROL Ordner]** -Option, wenn Sie die Suche auf Ordner in einem bestimmten Pfad beschränken müssen.
* Verwenden Sie die **[!UICONTROL Dateien und Ordner]** -Option, wenn Sie alle Assets durchsuchen müssen, die im angegebenen Pfad im Repository verfügbar sind.

Führen Sie die folgenden Schritte aus, um dieses Szenario zu erreichen:

1. Angeben `classic car` als Suchbegriff ein und klicken Sie auf &quot;Suchen&quot;.
2. Klicken Sie auf Filter und definieren Sie den Ordnerpfad für die `automobile` Ordner. Beispiel: `/content/dam/multiple-assets/automobile`
Wählen Sie den Ordner aus dem Pfad aus und navigieren Sie zum gewünschten Ordner, wenn Sie innerhalb des bestimmten Ordners suchen möchten.
3. Wählen Sie Dateien aus der Dropdownliste aus, um alle Dateien mit dem Schlüsselwort anzuzeigen `classic car`.

![Suchen mit Dateien und Ordnern](assets/files-folders.png)

>[!VIDEO](https://video.tv.adobe.com/v/3425487)

## Operatoren  {#operators}

**Szenario 3: Suchen Sie nach `Classic Car` oder `Car` Suchbegriffe, die verschiedene Operatorkombinationen verwenden, um Ihre Suche einzugrenzen.**

So führen Sie das obige Szenario aus: **[!UICONTROL Admin-Ansicht]** können Sie eine Kombination verschiedener Operatoren verwenden, um Ihre Sucherfahrung zu verbessern. Folgende Operatoren werden unterstützt:

### AND-Operator {#and-operator}

Der UND -Operator ist der Standardoperator zwischen zwei Suchbegriffen in der Omni-Suche. Wenn Sie beispielsweise `classic car` in der Suchleiste die Ergebnisse mit `classic` und `car` Suchbegriffe werden standardmäßig in Ihren Suchergebnissen angezeigt.

![Suchen mithilfe des AND-Operators](assets/simple-search-1.png)

### ODER-Operator {#or-operator}

Wenn Sie mit den Suchergebnissen spezifisch sein möchten und eine Option in den Suchergebnissen wünschen, können Sie den Operator ODER verwenden. Beispiel: die `classic OR car` -Keyword bietet Suchergebnisse mit einem der Keywords in den Metadaten.

![Suchen mithilfe des ODER-Operators](assets/or-operator.png)

### NOT-Operator {#not-operator}

Wenn Sie Ergebnisse ohne einige Suchbegriffe abrufen möchten, können Sie den Operator NOT verwenden. Der Operator NOT verwendet das Bindestrich-Symbol (-), um AEM Suche dahingehend zu leiten, was aus den Suchergebnissen ausgeschlossen werden soll. Beispiel: die `car - classic` Suchabfrage, die Metadaten angibt, die `car` aber ausschließt `classic`.

![Suche mithilfe des NOT-Operators](assets/not-operator.png)

Auf ähnliche Weise können Sie nach allen Autos suchen, aber nicht nach Jeep. Die Abfrage sieht wie folgt aus: `car - jeep`. Es werden alle Assets mit Metadaten angezeigt `car` schließt jedoch Assets mit Metadaten aus `jeep`.

![Suche mithilfe des NOT-Operators](assets/images-jeep.png)

**[!UICONTROL Asset-Ansicht]** unterstützt die Verwendung von Operatoren nicht.

## Platzhalter  {#wildcards}

Platzhalter werden verwendet, um ein oder mehrere Zeichen in der Suche zu ersetzen. So führen Sie das obige Szenario aus: **[!UICONTROL Admin-Ansicht]** können Sie eine Kombination aus verschiedenen Platzhaltern verwenden, um Ihr Sucherlebnis zu verbessern. Es werden zwei Platzhalter verwendet, um die Suche durchzuführen: Fragezeichen (?) und Sternchen (*). Das Fragezeichen-Symbol wird verwendet, um ein einzelnes Zeichen zu durchsuchen, während das Sternchen-Symbol für die Suche nach mehreren Zeichen verwendet wird.

### Fragezeichen (?) {#question-mark}

Das Fragezeichen-Symbol kann als bedingter Operator verwendet werden, um die Suche in Experience Manager zu erleichtern.

* `car?` -Abfrage entspricht dem Wort mit einem Zeichen nach dem Auto. Zum Beispiel Warenkorb.
* `?car` -Abfrage entspricht dem Wort mit einem Zeichen vor dem Auto. Beispiel: Narbe.
* `car????` -Abfrage entspricht dem Wort mit vier Zeichen nach dem Auto. Beispiel: Kartusche.

### Sternchen (*) {#asterisk}

Ein Sternchen ist ein Platzhalter-Operator, der verwendet wird, um Ihre Suche durch Eingabe von weniger Zeichen zu erweitern. Wenn Sie die Startzeichen des Assets kennen, nach dem Sie suchen, den Rest jedoch nicht kennen, können Sie den Sternchen-Operator bei Ihrer Suche verwenden. Beispiel: die `*car` -Abfrage gibt alle Assets mit dem Postfix-Auto zurück, das in den Metadaten verfügbar ist. Die Ergebnisse können klassische Autos, Sportwagen, Klassiker und Sportwagen usw. sein. Im Folgenden finden Sie einige Beispiele für die Verwendung des Sternchen-Operators:

* `*car*` gibt alle möglichen Kombinationen zurück.
* `car*` gibt Assets mit CarWasch, Träger, Transport usw. zurück.
* `*car` gibt Assets mit modernen Autos, Sportwagen usw. zurück.

>[!VIDEO](https://video.tv.adobe.com/v/3425488)

**[!UICONTROL Asset-Ansicht]** unterstützt die Verwendung von Platzhaltern nicht.

## Filter {#filters}

Adobe Experience Manager bietet verschiedene Suchfilter, mit denen Sie Ihre Suche mithilfe einer Scoped-Abfrage verfeinern und segmentieren können. Wenn Sie sich bezüglich des Titels oder der Meta-Beschreibung eines Assets nicht sicher sind, können Sie verschiedene Suchfilter verwenden, um Ihre Suche relevanter zu gestalten. Sie können Suchfilter mit oder ohne Eingabe eines Suchbegriffs verwenden. So öffnen Sie das Filterbedienfeld im **[!UICONTROL Admin-Ansicht]**, klicken Sie auf die **GlobalNav** Symbol und wählen Sie **[!UICONTROL Filter]**. Zum Öffnen des Filterbereichs in **[!UICONTROL Asset-Ansicht]** klicken [!UICONTROL Filter] neben der Suchleiste.

![Filterbereich](assets/filters.png)

Sie können einzelne oder mehrere Filter auswählen, um Ihre Suche in Adobe Experience Manager zu verfeinern.
<!--The following filters are available out of the box for all the users of Experience Manager:

* File Type Search Filters  
* File Size Search Filters 
* Date of Creation 
* Created by 
* Last Modified date 
* Last Modified by 
* Search by Language 
* Search by Status 
* Search based on Orientation 
* Search by Style 
* Search based on insights 
* Search by Adobe Stock 
* Color specific Asset search 
* Content fragment model 
 -->

<!--**Scenario 5: Search for an Asset named 'classic car' in Black color which has either meta description or a similar asset in Japanese language.**  
 
To perform a search on such a requirement, type 'classic car' in the search bar.  Navigate to the filters panel and expand the language search filter drop-down. Type "ja-jp", which represents the Japanese language. Expand the 'Asset Color' filter and select black color or add the hexadecimal code for the black color (#000000).

![Filter example 1](assets/filter-1.png)
-->

**Szenario 4: Suchen Sie nach nicht veröffentlichten PDF-Dateitypdokumenten mit der `classic car` enthalten.**

Führen Sie die folgenden Schritte aus unter **[!UICONTROL Admin-Ansicht]**:

1. Typ `classic car` in der Suchleiste.
1. Navigieren Sie zu Filter. under [!UICONTROL Dateityp], erweitern [!UICONTROL Dokumente]weitere Erweiterung [!UICONTROL Word-Verarbeitung].
1. Auswählen [!UICONTROL PDF].
1. Navigieren Sie zu [!UICONTROL Status] > [!UICONTROL Veröffentlichen] > [!UICONTROL Veröffentlichung rückgängig gemacht].

![Filterbeispiel 2](assets/filter-2.png)

Führen Sie die folgenden Schritte aus unter **[!UICONTROL Asset-Ansicht]**:

1. Typ `classic car` in der Suchleiste.
1. Navigieren Sie zu Filter. under [!UICONTROL MIME-Typ]auswählen [!UICONTROL PDF].
1. Navigieren Sie zu [!UICONTROL Asset-Status]auswählen [!UICONTROL Alle] , um alle veröffentlichten und nicht veröffentlichten Assets einzuschließen.

**Szenario 5: Suche nach allen Bildern außer PNG**

Wenn Sie sich bezüglich des Titels oder der Meta-Beschreibung eines Assets nicht sicher sind, können Sie verschiedene Suchfilter verwenden, um Ihre Suche relevanter zu gestalten. So suchen Sie beispielsweise Assets in **[!UICONTROL Admin-Ansicht]** führen Sie die folgenden Schritte aus:

1. Navigieren Sie zu Suchfiltern.
1. Navigieren Sie zu Filter. under [!UICONTROL Dateityp], erweitern [!UICONTROL Bilder] und wählen [!UICONTROL Web aktiviert]
1. Deaktivieren Sie PNG.

![Alle Bilder außer Jeep durchsuchen](assets/images-png.png)

So suchen Sie nach Assets mithilfe des erwähnten Szenarios in **[!UICONTROL Asset-Ansicht]** führen Sie die folgenden Schritte aus:

1. Navigieren Sie zu Suchfiltern.
1. Navigieren Sie zu Filter. under [!UICONTROL MIME-Typ], wählen Sie alle angegebenen MIME-Typen aus, deaktivieren Sie jedoch PNG.

>[!VIDEO](https://video.tv.adobe.com/v/3425486)

## Erweiterte Suche {#advanced-search}

AEM Suche ermöglicht es Ihnen, komplexe Suchabfragen mit geringerem Aufwand zu erstellen. Im Folgenden finden Sie verschiedene Beispiele, die Ihnen bei der Erstellung komplexer Suchabfragen helfen:

**Szenario 6: Suche nach allen Dokumenten im Experience Manager-Repository mit `classic car` in ihren Metadaten. Der Inhalt des Dokuments muss `classic car` enthalten.**

Mit Adobe Experience Manager können Sie mehrere Kriterien zu Ihrer Suche hinzufügen. Sie können eine Kombination aus Suchbegriffen, Operatoren und Filtern verwenden, um Ihre Suchergebnisse einzugrenzen.

So suchen Sie nach Szenario 6:

1. Geben Sie die `classic car` Suchbegriff in der Suchleiste.
2. Navigieren Sie zum Filterbedienfeld und wählen Sie unter &quot;Dateityp&quot;die Option Dokumente aus.
3. Verfeinern Sie Ihre Suche mithilfe des Sternchen-Platzhalters. Typ `"classic car"` , um alle Assets zu durchsuchen, die `classic car` Keyword.

![Szenario 6](assets/scenario-6.png)

Szenario 6 kann nicht in **[!UICONTROL Asset-Ansicht]** da es die Verwendung von Platzhaltern nicht unterstützt.

**Szenario 7: Suche nach allen Dokumenten im Experience Manager-Repository, in die der Dokumentinhalt eingefügt werden muss `car` aber ausschließen `classic`. Dasselbe gilt für Metadaten eines Assets.**

So suchen Sie nach Szenario 7:

Geben Sie die `car - classic` Suchbegriff in der Suchleiste. Navigieren Sie zum Filterbedienfeld und wählen Sie unter &quot;Dateityp&quot;die Option Dokumente aus. Die Prioritätsreihenfolge der Suche basiert auf Folgendem: Priorität 1: Metadatenpriorität 2: Smart-Tags

![Szenario 7](assets/scenario-7.png)

Szenario 7 ist nicht möglich in **[!UICONTROL Asset-Ansicht]** da es die Verwendung von Platzhaltern nicht unterstützt.

<!--
**Scenario 9: Search for all images except PNG**

When you are unsure about the title or meta description of an asset, you can use various search filters to make your search more relevant. Follow the steps below:

1. Go to search filters. 
1. Under [!UICONTROL File Type], expand [!UICONTROL Images] and select [!UICONTROL Web enabled]
1. Deselect PNG.

**Method 1:** Go to search bar and type `images - PNG`. All the images appear excluding PNG.

**Method 2:** Go to search filters. Under [!UICONTROL File Type], expand [!UICONTROL Images] > select [!UICONTROL Web enabled] > deselect PNG.

![Search all images except jeep](assets/images-jeep.png)
-->

**Szenario 8: Suche nach Metadaten-Tags mit Metadaten-Jeep**

Sie können ein bestimmtes Kriterium mithilfe verschiedener Suchfilter erfassen. Tag ist ein Schlüsselwort, das einem Asset zugewiesen wird, damit es von einer großen Anzahl von Assets identifiziert werden kann. Suchen Sie in diesem Szenario beispielsweise nach Assets mit *jeep* Tags darin. Geben Sie dazu `tags:jeep` in der Suchleiste. In den Suchergebnissen werden nur Assets aufgelistet, die diese Kriterien erfüllen.

![Suchen anhand von Tags](assets/search-tags.png)

Die Suche zeigt ähnliche Ergebnisse an, wenn Sie in der **[!UICONTROL Asset-Ansicht]** sowie.

>[!VIDEO](https://video.tv.adobe.com/v/3425490)

**Szenario 9: Ähnliche Übereinstimmung für roten Farbwagen suchen**

Bei der Suche nach AEM können Sie Ihre Ergebnisse filtern, indem Sie den ausgewählten Assets ähnliche Assets anzeigen. Sie können die **Ähnliche suchen** -Option, um die Suche auf die exakte oder ähnliche Übereinstimmung des gesuchten Assets einzuschränken. Dies hilft beim Suchen nach Assets, die ähnliche Smart-Tags wie das ausgewählte Asset haben. Wenn Sie beispielsweise nach gleichen Assets suchen möchten, führen Sie die folgenden Schritte aus:

1. Durchsuchen Sie das Asset gemäß Ihren Anforderungen.
1. Bewegen Sie den Mauszeiger über das Asset, klicken Sie auf das Auslassungszeichen und wählen Sie [!UICONTROL Ähnliche suchen].
oder Wählen Sie das Asset aus, navigieren Sie zu den Auslassungspunkten oben rechts und wählen Sie [!UICONTROL Ähnliche suchen].

   ![Ähnliches finden](assets/find-similar.png)

1. Beachten Sie die Suchleiste. Die Miniaturansicht des ausgewählten Assets wird in der Suchleiste angezeigt und gibt Ihre Suchanforderung an. Daher werden Assets mit ähnlichen Smart-Tags zurückgegeben.

**[!UICONTROL Asset-Ansicht]** unterstützt nicht die [!UICONTROL Ähnliche suchen] -Option.

## Benutzerdefinierte Suchfacetten {#custom-search-facets}

Mit Suchfacetten in Adobe Experience Manager können Sie auf mehrere Arten nach Assets suchen, anstatt in einer einzigen, vorab festgelegten oder taxonomischen Reihenfolge. Sie können Suchfacetten anpassen und Prädikate gemäß Ihren Anforderungen hinzufügen. Lesen [Suchfacetten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/search-facets.html?lang=de#) für die schrittweise Anleitung zum Hinzufügen eines benutzerdefinierten Prädikats.

<!--**Scenario 10: Search assets based on Sku ID**
to be added later
-->

**Szenario 10: Suche nach bestimmten Assets basierend auf ihrem letzten Änderungsdatum oder Ablaufdatum**

Mit Datumsbeschränkungen können Sie Ihre benutzerdefinierte Suche auf einen bestimmten Zeitraum einschränken, z. B. mithilfe der Zeitraumsuchfilter. Um nach der obigen Anforderung zu suchen, geben Sie `classic car` in der Suchleiste. Wählen Sie den Datumsbereich im [!UICONTROL Erstellungsdatum] und [!UICONTROL Zuletzt geändert] Datumsfilter.

![Datumsfilter](assets/date-filters.png)

Die Suche zeigt ähnliche Ergebnisse an, wenn Sie in der [!UICONTROL Asset-Ansicht] sowie.

## Steigerung der Relevanz von Keywords {#boosting-keywords}

Sie können die Relevanz von Keywords für bestimmte Assets verbessern, um die auf Keywords basierenden Suchen zu optimieren. D. h. die Bilder, für die Sie bestimmte Keywords festlegen, erscheinen bei der Suche nach diesen Keywords oben in den Suchergebnissen.

1. Öffnen Sie in der Assets-Benutzeroberfläche für das Asset die Seite „Eigenschaften“. Klicken Sie auf [!UICONTROL Erweitert] und klicken Sie dann auf [!UICONTROL Hinzufügen] unter [!UICONTROL Für Keywords erhöhen].
2. Geben Sie im Feld Suche priorisieren ein Keyword ein, für den Sie die Bildsuche optimieren möchten, und klicken Sie anschließend auf [!UICONTROL Hinzufügen]. Sie können auf dieselbe Weise mehrere Keywords eingeben.
3. Klicken Sie auf [!UICONTROL Speichern und schließen]. Das Asset, das Sie für dieses Keyword erhöht haben, befindet sich unter den obersten Suchergebnissen.

## Wesentliche Dinge bei der Durchführung einer Suche in Experience Manager {#notable-things}

* Geben Sie Metadateninformationen zum Asset an, um das Asset vorzubereiten, das vom Omni-Suchalgorithmus durchsuchbar ist. Stellen Sie sicher, dass die Metadateninformationen des Assets aktualisiert wurden.
* Verwenden Sie doppelte Anführungszeichen (&quot;&quot;&quot;), um Ihre Suche genau und bis zum Punkt zu machen.
* Überprüfen Sie den Pfad, den Sie untersuchen. Wählen Sie die entsprechende Option aus Ordner, Datei oder Datei und Ordner aus, um Ihre Suchabfrage an der entsprechenden Stelle auszuführen.
* Sie können die Filter, die Sie auf Ihre Suche anwenden, in der Omni-Suchleiste überprüfen.
* Falls Sie keine Ergebnisse erhalten, überprüfen Sie den Pfad, den Sie untersuchen. Überprüfen Sie auch den Ordner, aus dem Sie Ihre Suche durchführen. Wenn Sie beispielsweise eine Suche im Ordner &quot;Automobile&quot;durchführen, der von Ihnen verwendete Suchbegriff jedoch mit &quot;Apparels&quot;verknüpft ist, sind die Suchergebnisse unangemessen.
* Aktivieren Sie diese Option, wenn Sie vor dem Suchbegriff, nach dem Sie suchen, Leerzeichen hinzugefügt haben.
* Die Verwendung einer Mischung aus Keywords, Operatoren und Filtern kann Ihr Sucherlebnis vereinfachen und einfacher gestalten.

<!--
* Use stemming search approach while searching for the asset. It means using an exact keyword that you are looking for.
* Specify Smart tags to the asset properties to boost the ranking of the search results.
The newly added assets are not indexed.
-->

## Unterschiede zwischen [!UICONTROL Admin-Ansicht] und [!UICONTROL Asset-Ansicht] Suche {#differences-asset-and-admin-view}

<table>
    <tr>
        <th> Parameter </th>
        <th> Admin-Ansicht </th>
        <th> Assets-Ansicht </th>
    </tr>
    <tr>
        <td> Benutzerdefinierte Facetten </td>
        <td> Sie können <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/search-facets.html?lang=de">benutzerdefinierte Suchfacetten gemäß den Anforderungen.</td>
        <td> Die benutzerdefinierten Facetten werden teilweise in der Asset-Ansicht unterstützt. Folgende Facetten werden unterstützt:
            <ul>
            <li> Vorhergesagte Tags
            <li> Name
            <li> Vertraulichkeit prognostizierter Tags
            <li> Asset-Größe
            <li> Titel
            </ul>
        </td>
    </tr>
    <tr>
        <td> Operatoren  </td>
        <td> Unterstützt AND, OR und NOT </td>
        <td> Nicht unterstützt </td>
    </tr>
    <tr>
        <td> Platzhalter  </td>
        <td> Unterstützt Fragezeichen (?) und Sternchen (*).</td>
        <td> Nicht unterstützt </td>
    </tr>
    <tr>
        <td> Suchergebnisse steigern </td>
        <td> Unterstützt </td>
        <td> Nicht unterstützt </td>
    </tr>
     <tr>
        <td> Alle Filter gleichzeitig löschen </td>
        <td> Nicht unterstützt </td>
        <td> Unterstützt</td>
    </tr>
     <tr>
        <td> Dateien/Ordner/Dateien und Ordner </td>
        <td> Unterstützt </td>
        <td> Eine Option zur Auswahl eines Ordners ist unter "Dateityp"verfügbar </td>
    </tr>
     <tr>
        <td> Asset-Status </td>
        <td> 
            Unterstützte Optionen sind:
            <ul>
            <li> Veröffentlichen
            <li> Veröffentlichungsdatum
            <li> Zuletzt veröffentlicht von
            <li> Genehmigung 
            <li> Checkout
            <li> Ablauf
            <li> Dynamic Media
            </ul>
        </td>
        <td>
        Unterstützte Optionen sind:
            <ul>
            <li> Alle
            <li> Genehmigt
            <li> Abgelehnt
            <li> Kein Status
            </ul> 
        </td>
    </tr>
     <tr>
        <td> Dateityp </td>
        <td>
        Unterstützte Optionen sind:
            <ul>
            <li> Bilder
            <li> Dokumente
            <li> Multimedia
            <li> Archive 
            </ul>
            Diese haben weitere hierarchische Optionen.
        </td>
        <td>
        Unterstützte Optionen sind:
            <ul>
            <li> Bilder
            <li> Dokumente
            <li> Video 
            <li> Ordner 
            </ul> 
        Weitere Optionen sind unter MIME-Typ aufgeführt.
        </td>
    </tr>
     <tr>
        <td> Dateigröße </td>
        <td>
        Unterstützte Optionen sind:
            <ul>
            <li> Von - nach
            <li> Größe (Bytes, KB, MB, GB)
            </ul> 
        </td>
        <td> Nicht unterstützt </td>
    </tr>
     <tr>
        <td> Sonstige Filter </td>
        <td>
            <ul>
            <li> Sprache
            <li> Status
            <li> Ausrichtung
            <li> Stil 
            <li> Insights
            <li> Stock
            <li> Asset-Farbe
            <li> Inhaltsfragmentmodell
            </ul> 
        </td>
        <td> Nicht unterstützt </td>
    </tr>
     <tr>
        <td> Ähnliches finden </td>
        <td> Unterstützt </td>
        <td> Nicht unterstützt </td>
    </tr>
</table>

>[!MORELIKETHIS]
>
>* [Suchen von Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/search-assets.html?lang=de)
>* [Suchfacetten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/search-facets.html?lang=de)
