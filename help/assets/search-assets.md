---
title: Suchen nach digitalen Assets und Bildern in AEM
description: Erfahren Sie, wie Sie die erforderlichen Assets in AEM mithilfe des Bedienfelds „Filter“ finden und wie Sie die Assets verwenden, die bei der Suche zurückgegeben werden.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 7317a5db6ed348f99b2290d72ddf6e540fae5456
workflow-type: tm+mt
source-wordcount: '4529'
ht-degree: 99%

---


# Suchen nach Assets in AEM     {#search-assets-in-aem}

Mit den benutzerfreundlichen Optionen zur Asset-Erkennung in Experience Manager können Sie Inhalte schneller finden. Ihre Teams können die Time-to-Market mit einem nahtlosen, intelligenten Sucherlebnis durch vordefinierte Funktionen und benutzerdefinierte Methoden verkürzen. Die Suche nach Assets spielt bei der Nutzung eines Digital-Asset-Management-Systems eine zentrale Rolle – sowohl für eine weitere Verwendung durch Kreativprofis als auch für eine robuste Verwaltung von Assets durch Geschäftsbenutzer und Marketing-Experten oder für die Verwaltung durch DAM-Administratoren. Einfache, erweiterte und benutzerdefinierte Suchen, die Sie über die Benutzeroberfläche von AEM Assets oder andere Apps und Oberflächen durchführen können, helfen beim Bewältigen dieser Anwendungsfälle.

AEM unterstützt folgende Anwendungsfälle und in diesem Artikel werden Verwendung, Konzepte, Konfigurationen, Einschränkungen und Fehlerbehebung für diese Fälle beschrieben.

| Suchen von Assets | Konfiguration und Verwaltung | Arbeiten mit Suchergebnissen |
|--- |--- |--- |
| [Einfache Suchvorgänge](#searchbasics) | [Suchindex](#searchindex) | [Ergebnisse sortieren](#sort) |
| [Benutzeroberfläche für Suchen](#searchui) |  | [Eigenschaften und Metadaten eines Assets überprüfen](#checkinfo) |
| [Suchvorschläge](#searchsuggestions) | [Obligatorische Metadaten](#mandatorymetadata) | [Download](#download) |
| [Suchergebnisse und -verhalten verstehen](#searchbehavior) | [Suchfacetten ändern](#searchfacets) | [Massenaktualisierung von Metadaten](#metadataupdates) |
| [Such-Ranking und -Optimierung](#searchrank) | [Textextraktion](#extracttextupload) | [Smart-Sammlungen](#collections) |
| [Erweiterte Suche: Filtern und Suchbereich](#scope) | [Benutzerdefinierte Prädikate](#custompredicates) | [Unerwartete Ergebnisse](#unexpectedresults) und [Fehlerbehebung](#troubleshoot) |
| [Suche über andere Lösungen und Apps](#beyondomnisearch): <br />     [Asset Link](#aal) <br />     [Desktop-Programm](#desktopapp) <br />     [Adobe Stock-Fotos](#adobestock) <br />     [Dynamic Media-Assets](#dynamicmedia) |  |  |
| [Asset-Wähler/Auswahl](#assetselector) |  |  |
| [Einschränkungen](#tips) und [Tipps](#limitations) |  |  |
| [Illustrierte Beispiele](#samples) |  |  |

Suchen Sie mithilfe des OmniSearch-Felds oben in der AEM-Web-Oberfläche nach Assets. Gehen Sie in AEM zu **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**, klicken Sie in der oberen Leiste auf ![search_icon](assets/do-not-localize/search_icon.png), geben Sie den Suchbegriff ein und drücken Sie die Eingabetaste. Alternativ können Sie die Suchbegriff-Tastenkombination `/` (Schrägstrich) verwenden, um das OmniSearch-Feld zu öffnen. `Location:Assets` ist vorausgewählt, um die Suche auf DAM-Assets zu begrenzen. Sie können erweiterte Suchen durchführen, um den [Suchbereich](#scope) zu vergrößern oder zu verkleinern.

Verwenden Sie das Bedienfeld **[!UICONTROL Filter]**, um nach Assets, Ordnern, Tags und Metadaten zu suchen. Sie können Suchergebnisse anhand der verschiedenen Optionen (Prädikate) filtern, z. B. Dateityp, Dateigröße, Datum der letzten Änderung, Status des Assets, Einblicke und Adobe Stock-Lizenzierung. Sie können das Bedienfeld „Filter“ anpassen und Suchprädikate über [Suchfacetten](/help/assets/search-facets.md) hinzufügen/entfernen.

Die AEM-Suchfunktionen erlauben die Suche nach Sammlungen sowie die Suche nach Assets in einer Sammlung. Siehe [Suchen nach Sammlungen](/help/assets/manage-collections.md).

## Suchoberfläche verstehen {#searchui}

Machen Sie sich mit der Suchoberfläche und den verfügbaren Aktionen vertraut.

![Bestandteile der Oberfläche für Assets-Suchergebnisse verstehen](assets/aem_search_results.png)
*Abbildung:* Bestandteile der Oberfläche für Assets-Suchergebnisse verstehen

**A.** Speichern Sie die Suche als Smart-Sammlung. **B.** Verwenden Sie Filter (Prädikate) zur Eingrenzung der Suchergebnisse. **C.** Zeigen Sie Dateien, Ordner oder beide in den Suchergebnissen an. **D.** Klicken Sie auf „Filter“, um die linke Leiste zu öffnen oder zu schließen. **E.** Die Suchposition ist DAM. **F.** OmniSearch-Feld mit benutzerdefiniertem Suchbegriff **G.** Kontrollkästchen zur Auswahl aller Suchergebnisse **H.** Anzahl der angezeigten Suchergebnisse aus der Gesamtanzahl der Suchergebnisse **I.** Schließen der Suche **J.** Wechseln zwischen Kartenansicht und Listenansicht

### Dynamische Suchfacetten {#dynamicfacets}

Sie können die gewünschten Assets schneller auf der Suchergebnisseite ausfindig machen, indem Sie die dynamisch aktualisierte Anzahl der erwarteten Suchergebnisse in den Suchfacetten verwenden. Die erwartete Anzahl an Assets wird noch vor Anwendung des Suchfilters aktualisiert. Durch Anzeige der erwarteten Anzahl im Filter können Sie schnell und effizient durch Suchergebnisse navigieren. Weitere Informationen finden Sie unter [Suche nach Assets in AEM](/help/assets/search-assets.md).

![Anzeigen der ungefähren Asset-Anzahl ohne Filterung der Suchergebnisse in Suchfacetten](assets/asset_search_results_in_facets_filters.png)

Anzeigen der ungefähren Asset-Anzahl ohne Filterung der Suchergebnisse in Suchfacetten

## Suchvorschläge bei der Eingabe {#searchsuggestions}

Wenn Sie mit der Eingabe eines Suchbegriffs beginnen, schlägt AEM mögliche Suchbegriffe oder -phrasen vor. Die Vorschläge basieren auf den Assets in AEM. AEM indiziert alle Metadatenfelder, um die Suche zu erleichtern. Zur Bereitstellung von Suchvorschlägen verwendet das System die Werte der folgenden Metadatenfelder. Um Suchvorschläge zu erhalten, können Sie die folgenden Felder mit geeigneten Suchbegriffen ausfüllen:

* Asset-Tags. (Zuordnung zu `jcr:content/metadata/cq:tags`)
* Asset-Titel. (Zuordnung zu `jcr:content/metadata/dc:title`)
* Asset-Beschreibung. (Zuordnung zu `jcr:content/metadata/dc:description`)
* Titel im JCR-Repository. Der Wert wird ggf. dem Asset-Titel zugeordnet. (Zuordnung zu `jcr:content/jcr:title`)
* Beschreibung im JCR-Repository. Der Wert wird ggf. der Asset-Beschreibung zugeordnet. (Zuordnung zu `jcr:content/jcr:description`)

## Suchergebnisse und -verhalten verstehen {#searchbehavior}

### Grundlegende Suchbegriffe und -ergebnisse {#searchbasics}

Sie können im OmniSearch-Feld mit Suchbegriffen suchen. Bei der Suche mit Suchbegriffen wird nicht zwischen Groß- und Kleinschreibung unterschieden und es handelt sich um eine Volltextsuche (über die gängigen Metadatenfelder hinweg). Wenn mehrere Suchbegriffe verwendet werden, ist `AND` der Standardoperator zwischen den Suchbegriffen. Die Ergebnisse werden nach Relevanz sortiert, beginnend mit den größten Übereinstimmungen. Bei mehreren Suchbegriffen sind Assets, die beide Begriffe in ihren Metadaten enthalten, relevanter. In Metadaten werden Suchbegriffe, die als Smart-Tags erscheinen, höher eingestuft als Suchbegriffe, die in anderen Metadatenfeldern auftauchen.

AEM bietet Ihnen die Möglichkeit, einem bestimmten Suchbegriff mehr Gewicht zu verleihen. Außerdem können Sie für bestimmte Suchbegriffe das Ranking einiger ausgewählter Assets erhöhen. AEM-Administratoren können diese Konfigurationen wie unten beschrieben vornehmen.

Zum schnellen Auffinden der benötigten Assets bietet die Rich-Oberfläche Filter-, Sortierungs- und Auswahlverfahren. Sie können Ergebnisse anhand mehrerer Kriterien filtern und für verschiedene Filter die Anzahl der durchsuchten Assets anzeigen. Alternativ können Sie die Suche erneut ausführen, indem Sie die Abfrage im OmniSearch-Feld ändern. Wenn Sie Suchbegriffe oder Filter ändern, bleiben die anderen Filter angewendet, um den Kontext Ihrer Suche zu wahren.

Manchmal werden in den Suchergebnissen auch unerwartete Assets angezeigt. Weitere Informationen dazu finden Sie unter [Unerwartete Ergebnisse](#unexpectedresults).

AEM kann viele Dateiformate suchen und die Suchfilter können an Ihre geschäftlichen Anforderungen angepasst werden. Wenden Sie sich an Ihre Administratoren, um zu erfahren, welche Suchoptionen für Ihr DAM-Repository zur Verfügung stehen und welche Einschränkungen Ihre Anmeldung haben kann.

<!-- 
### Results with and without Enhanced Smart Tags {#withsmarttags}

By default, AEM search combines the search terms with an AND clause. For example, consider searching for keywords woman running. Only the assets with both woman and running keywords in the metadata appear in the search results by default. The same behavior is retained when special characters (periods, underscores, or dashes) are used with the keywords. The following search queries return the same results:

* `woman running`
* `woman.running`
* `woman-running`

However, the query `woman -running` returns assets without `running` in their metadata.
Using smart tags adds an extra `OR` clause to find any of the search terms as the applied smart tags. An asset tagged with either `woman` or `running` using Smart Tags also appear in such a search query. So the search results are a combination of,

* Assets with `woman` and `running` keywords in the metadata (default behavior).

* Assets smart tagged with either of the keywords (Smart Tags behavior).
-->

### Such-Ranking und -Optimierung {#searchrank}

Die Suchergebnisse, die in Metadatenfeldern alle Suchbegriffe aufweisen, werden zuerst angezeigt. Danach folgen die Suchergebnisse, die einem oder mehr Suchbegriffen in den Smart-Tags entsprechen. Im obigen Beispiel werden die Suchergebnisse ungefähr in dieser Reihenfolge angezeigt:

1. Treffer von `woman running` in den verschiedenen Metadatenfeldern.
1. Treffer von `woman running` in den Smart-Tags.
1. Treffer von `woman` oder `running` in Smart-Tags.

Sie können die Relevanz von Suchbegriffen für bestimmte Assets verbessern, um die auf Suchbegriffen basierenden Suchen zu optimieren. D. h. die Bilder, für die Sie bestimmte Suchbegriffe festlegen, erscheinen bei der Suche nach diesen Suchbegriffen oben in den Suchergebnissen.

1. Öffnen Sie in der Assets-Benutzeroberfläche für das Asset die Seite „Eigenschaften“. Klicken Sie auf **[!UICONTROL Erweitert]** und klicken oder tippen Sie dann auf **[!UICONTROL Hinzufügen]** unter **[!UICONTROL Für Suchbegriffe erhöhen]**.
1. Geben Sie im Feld **[!UICONTROL Suche priorisieren]** einen Suchbegriff ein, für den Sie die Bildsuche optimieren möchten, und klicken oder tippen Sie anschließend auf **[!UICONTROL Hinzufügen]**. Sie können auf dieselbe Weise mehrere Suchbegriffe eingeben.
1. Klicken/tippen Sie auf **[!UICONTROL Speichern und schließen]**. Das Asset, das Sie für diesen Suchbegriff erhöht haben, befindet sich unter den obersten Suchergebnissen.

So können Sie das Ranking bestimmter Assets in den Suchergebnissen für den jeweiligen Suchbegriff erhöhen. Siehe Beispielvideo unten. Weitere Informationen finden Sie unter [Suchen in AEM](https://helpx.adobe.com/de/experience-manager/kt/help/assets/search-feature-video-use.html).

>[!VIDEO](https://video.tv.adobe.com/v/16766/?quality=6)

*Erfahren Sie, wie Suchergebnisse ihren Rang erhalten und wie der Rang beeinflusst werden kann.*

## Erweiterte Suche {#scope}

AEM bietet verschiedene Methoden wie Filter, die sich auf die durchsuchten Assets anwenden lassen, damit Sie gewünschte Assets schneller finden können. Nachfolgend werden einige häufig verwendete Methoden beschrieben. Im Folgenden werden einige [illustrierte Beispiele](#samples) vorgestellt.

**Nach Dateien oder Ordnern suchen**: In den Suchergebnissen sehen Sie entweder Dateien, Ordner oder beides. Wählen Sie im Bedienfeld **[!UICONTROL Filter]** die entsprechende Option aus. Siehe [Suchoberfläche](#searchui).

**In einem Ordner nach Assets suchen**: Sie können die Suche auf einen bestimmten Ordner beschränken. Fügen Sie im Bedienfeld **[!UICONTROL Filter]** den Pfad eines Ordners hinzu. Sie können immer nur einen Ordner auf einmal hinzufügen.

![Suchergebnisse durch Hinzufügen eines Ordnerpfads im Bedienfeld „Filter“ auf einen Ordner begrenzen](assets/search_folder_select.gif)

Suchergebnisse durch Hinzufügen eines Ordnerpfads im Bedienfeld „Filter“ auf einen Ordner begrenzen

<!--
### Find similar images {#visualsearch}

To find images that are visually similar to a user-selected image, click **[!UICONTROL Find Similar]** option from the card view of an image or from the toolbar. AEM displays the smart tagged images from the DAM repository that are similar to a user-selected image. See [how to configure similarity search](#configvisualsearch).

![Find similar images using the option in the card view](assets/search_find_similar.png)
*Figure: Find similar images using the option in the card view*
-->

### Adobe Stock-Fotos {#adobestock}

Benutzer können aus der AEM-Benutzeroberfläche heraus nach [Adobe Stock-Assets](/help/assets/aem-assets-adobe-stock.md) suchen und die erforderlichen Assets lizenzieren. Fügen Sie `Location: Adobe Stock` in der OmniSearch-Leiste hinzu. Sie können auch das Bedienfeld „Filter“ verwenden, um alle lizenzierten oder nicht lizenzierten Assets zu suchen bzw. mit der Adobe Stock-Dateinummer nach einem bestimmten Asset suchen.

### Dynamic Media-Assets {#dmassets}

Sie können nach Dynamic Media-Bildern filtern, indem Sie die Option **[!UICONTROL Dynamic Media > Sets]** im Bedienfeld **[!UICONTROL Filter]** auswählen. Dadurch werden Assets wie Bildsets, Karussells, gemischte Mediensets und Rotationssets gefiltert und angezeigt.

### Mit bestimmten Werten in Metadatenfeldern suchen {#gqlsearch}

Sie können anhand exakter Werte bestimmter Metadatenfelder wie Titel, Beschreibung und Autor nach Assets suchen. Die Volltextsuchfunktion GQL ruft nur jene Assets ab, deren Metadatenwert exakt mit Ihrer Suchanfrage übereinstimmt. Bei den Namen der Eigenschaften (z. B. Autor, Titel usw.) und Werten wird zwischen Groß- und Kleinschreibung unterschieden.

| Metadatenfeld | Facettenwert und Nutzung |
|---|---|
| Titel | title:John |
| Ersteller | creator:John |
| Standort | location:NA |
| Beschreibung | description:&quot;Sample Image&quot; |
| Erstellungswerkzeug | creatortool:&quot;Adobe Photoshop CC 2015&quot; |
| Urheberrechtsbesitzer | copyrightowner:&quot;Adobe Systems&quot; |
| Mitarbeiter | contributor:John |
| Nutzungsbedingungen | usageterms:„CopyRights Reserved“ |
| Erstellt | created:YYYY-MM-DDTHH |
| Ablaufdatum | expires:YYYY-MM-DDTHH |
| Einschaltzeit | ontime:YYYY-MM-DDTHH |
| Ausschaltzeit | offtime:YYYY-MM-DDTHH |
| Zeitraum (expires dateontime,offtime) | facet field : lowerbound..upperbound |
| Pfad | /content/dam/&lt;Ordnername> |
| PDF-Titel | pdftitle:„Adobe Document“ |
| Betreff | subject:„Training“ |
| Tags | tags:„Location And Travel“ |
| Typ | type:&quot;image\png&quot; |
| Bildbreite | width:lowerbound..upperbound |
| Bildhöhe | height:lowerbound..upperbound |
| Person | person:John |

Die Eigenschaften „path“, „limit“, „size“ und „orderby“ können nicht über OR mit einer anderen Eigenschaft verknüpft werden.

Der Suchbegriff für eine von einem Benutzer erstellte Eigenschaft ist ihre Feldbeschriftung im Eigenschafteneditor in Kleinbuchstaben und ohne Leerzeichen.

Im Folgenden finden Sie einige Beispiele für Suchformate für komplexe Abfragen:

* So zeigen Sie alle Assets mit mehreren Facettenfeldern an (wie: title=John Doe und creator tool = Adobe Photoshop):     `title:"John Doe" creatortool : Adobe*`
* So zeigen Sie alle Assets an, wenn der Facettenwert nicht ein einzelnes Wort, sondern ein Satz ist (wie: title=Scott Reynolds): `title:"Scott Reynolds"`
* So zeigen Sie alle Assets mit mehreren Werten für eine einzelne Eigenschaft an (wie: title=Scott Reynolds oder John Doe): `title:"Scott Reynolds" OR "John Doe"`
* So zeigen Sie Assets an, deren Eigenschaftswerte mit einer bestimmten Zeichenfolge beginnen (wie: title ist Scott Reynolds): `title:Scott*`
* So zeigen Sie Assets an, deren Eigenschaftswerte mit einer bestimmten Zeichenfolge enden (wie: title ist Scott Reynolds): `title:*Reynolds`
* So zeigen Sie Assets mit einem Eigenschaftswert an, der eine bestimmte Zeichenfolge enthält (wie: title=Basel Meeting Room): `title:*Meeting*`
* So zeigen Sie Assets an, die eine bestimmte Zeichenfolge enthalten und einen bestimmten Eigenschaftswert aufweisen (wie die Suche nach der Zeichenfolge „Adobe“ in Assets mit title=John Doe): `*Adobe* title:"John Doe"`

## Nach Assets über andere AEM-Produkte oder -Oberflächen suchen {#beyondomnisearch}

Adobe Experience Manager (AEM) verbindet das DAM-Repository mit verschiedenen anderen AEM-Lösungen, um den Zugriff auf digitale Assets zu erleichtern und die kreativen Arbeitsabläufe zu optimieren. Jede Asset-Erkennung beginnt mit dem Durchsuchen oder Suchen. Das Suchverhalten ist über die verschiedenen Oberflächen und Lösungen hinweg weitgehend gleich. Einige Suchmethoden ändern sich je nach Zielgruppe, Anwendungsfällen und Benutzeroberfläche der jeweiligen AEM-Lösung. Die genauen Methoden für die einzelnen Lösungen sind unter den unten stehenden Links dokumentiert. Die allgemein anwendbaren Tipps und Verhaltensweisen werden in diesem Artikel beschrieben.

### Nach Assets über das Bedienfeld „Adobe Asset Link“ suchen {#aal}

Mit Adobe Asset Link können Kreativprofis jetzt auf in AEM Assets gespeicherte Inhalte zugreifen, ohne die unterstützten Adobe Creative Cloud-Programme verlassen zu müssen. Kreative können mit dem In-App-Bedienfeld in folgenden Creative Cloud-Programmen Assets nahtlos suchen, durchsuchen sowie ein- und auschecken: Photoshop, Illustrator und InDesign. Asset Link ermöglicht es Benutzern auch, nach visuell ähnlichen Ergebnissen zu suchen. Die Ergebnisse der visuellen Suchanzeige basieren auf den maschinellen Lernalgorithmen von Adobe Sensei und helfen Benutzern dabei, optisch ähnliche Bilder zu finden. Siehe [Assets suchen und durchsuchen](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) mit Adobe Asset Link.

### Suchen nach Assets im AEM-Desktop-Programm {#desktopapp}

Kreativprofis verwenden das Desktop-Programm, um AEM-Assets auf ihrem lokalen Desktop (Windows oder Mac) bequem zu durchsuchen und verfügbar zu machen. Kreative können die gewünschten Assets in Mac Finder oder Windows Explorer leicht anzeigen, in Desktop-Programmen öffnen und lokal ändern. Die Änderungen werden dann wiederum unter einer neuen, im Repository erstellten Version in AEM gespeichert. Die Anwendung unterstützt grundlegende Suchvorgänge mit einem oder mehreren Suchbegriffen, den Platzhaltern „*“ und „?“ sowie dem AND-Operator. Siehe [Assets durchsuchen und suchen sowie Vorschau für Assets anzeigen](https://docs.adobe.com/content/help/de-DE/experience-manager-desktop-app/using/using.html#browse-search-preview-assets) im Desktop-Programm.

### Suchen von Assets in Brand Portal {#brandportal}

Geschäftsbenutzer und Marketing-Experten nutzen Brand Portal, um genehmigte digitale Assets effizient und sicher mit erweiterten internen Teams, Partnern und Wiederverkäufern zu teilen. Siehe [Suchen von Assets in Brand Portal](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/search-capabilities/brand-portal-searching.html).

### Suchen nach Adobe Stock-Fotos {#adobestock-1}

Benutzer können aus der AEM-Benutzeroberfläche heraus Adobe Stock-Assets suchen und die erforderlichen Assets lizenzieren. Fügen Sie `Location: Adobe Stock` im OmniSearch-Feld hinzu. Sie können auch das Bedienfeld **[!UICONTROL Filter]** verwenden, um alle lizenzierten oder nicht lizenzierten Assets zu suchen bzw. mit der Adobe Stock-Dateinummer ein bestimmtes Asset zu suchen. Siehe [Verwalten von Adobe Stock-Fotos in AEM](/help/assets/aem-assets-adobe-stock.md#usemanage).

### Suchen nach Dynamic Media-Assets {#dynamicmedia}

Sie können nach Dynamic Media-Bildern filtern, indem Sie die Option **[!UICONTROL Dynamic Media]** > **[!UICONTROL Sets]** im Bedienfeld **[!UICONTROL Filter]** auswählen. Dadurch werden Assets wie Bildsets, Karussells, gemischte Mediensets und Rotationssets gefiltert und angezeigt. Beim Erstellen von Web-Seiten können Autoren in der Inhaltssuche nach Sets suchen. Ein Filter für Sets ist in einem Popup-Menü verfügbar.

### Suchen nach Assets in der Inhaltssuche beim Erstellen von Web-Seiten {#contentfinder}

Autoren können mit der Inhaltssuche das DAM-Repository nach den relevanten Assets durchsuchen und die Assets auf den von ihnen erstellten Web-Seiten verwenden.

<!-- Authors can also use the Connected Assets functionality to search for assets that are available on a remote AEM deployment. Authors can then use these assets in web pages on a local AEM deployment. See [use remote assets](use-assets-across-connected-assets-instances.md#use-remote-assets).
-->

### Suchen nach Sammlungen {#collections}

Die AEM-Suchfunktionen erlauben die Suche nach Sammlungen sowie die Suche nach Assets in einer Sammlung. Siehe [Suchen nach Sammlungen](/help/assets/manage-collections.md).

## Asset-Wähler {#assetselector}

Mit dem Asset-Wähler können Sie DAM-Assets auf besondere Weise suchen, filtern und durchsuchen. Der Asset-Wähler ist verfügbar unter `https://[aem_server]:[port]/aem/assetpicker.html`. Sie können die Metadaten der Assets, die Sie über den Asset-Wähler auswählen, abrufen. Sie können ihn mit unterstützten Anfrageparametern wie dem Asset-Typ (Bild, Video, Text) und dem Auswahlmodus (eine oder mehrere Auswahlen) starten. Diese Parameter legen den Kontext des Asset-Wählers für eine bestimmte Suchinstanz fest und bleiben während der Auswahl intakt.

Der Asset-Wähler verwendet die HTML5-Meldung `Window.postMessage`, um Daten für das ausgewählte Asset an den Empfänger zu senden. Der Asset-Wähler basiert auf dem Vokabular der Foundation-Auswahl von Granite. Standardmäßig befindet sich der Asset-Wähler im Modus „Durchsuchen“. 

Sie können die folgenden Anforderungsparameter in einer URL übergeben, um den Asset-Wähler in einem bestimmten Kontext zu starten:

| Name | Werte | Beispiel | Zweck |
|---|---|---|---|
| resource suffix (B) | Ordnerpfad als Ressourcensuffix in der URL:[https://localhost:4502/aem/assetpicker.html/&lt;Ordnerpfad>](https://localhost:4502/aem/assetpicker.html) | Zum Starten des Asset-Wählers mit einem bestimmten Ordner, z. B. /content/dam/we-retail/en/activities, sollte die URL wie folgt aussehen: [https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images](https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images) | Wenn beim Starten des Asset-Wählers ein bestimmter Ordner ausgewählt sein soll, können Sie ihn als Ressourcensuffix übergeben. |
| mode | single, multiple | [https://localhost:4502/aem/assetpicker.html?mode=multiplehttps://localhost:4502/aem/assetpicker.html?mode=single](https://localhost:4502/aem/assetpicker.html?mode=multiplehttps://localhost:4502/aem/assetpicker.html?mode=single) | Im Modus „multiple“ können Sie mit dem Asset-Wähler mehrere Assets gleichzeitig auswählen. |
| mimetype | MIME-Typen (`/jcr:content/metadata/dc:format`) eines Assets (Platzhalter wird ebenfalls unterstützt) | <ul><li>[https://localhost:4502/aem/assetpicker.html?mimetype=image/png](https://localhost:4502/aem/assetpicker.html?mimetype=image/png)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*png](https://localhost:4502/aem/assetpicker.html?mimetype=*png)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*presentation](https://localhost:4502/aem/assetpicker.html?mimetype=*presentation)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*presentation&amp;mimetype=*png](https://localhost:4502/aem/assetpicker.html?mimetype=*presentation&amp;mimetype=*png)</li></ul> | Verwenden Sie diese Option zum Filtern von Assets anhand von MIME-Typen. |
| dialog | true, false | [https://localhost:4502/aem/assetpicker.html?dialog=true](https://localhost:4502/aem/assetpicker.html?dialog=true) | Verwenden Sie diese Parameter, um den Asset-Wähler als Granite-Dialogfeld zu öffnen. Diese Option ist nur relevant, wenn Sie den Asset-Wähler per Granite-Pfadfeld starten und als pickerSrc-URL konfigurieren. |
| assettype (S) | images, documents, multimedia, archives | <ul><li>[https://localhost:4502/aem/assetpicker.html?assettype=images](https://localhost:4502/aem/assetpicker.html?assettype=images)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=documents](https://localhost:4502/aem/assetpicker.html?assettype=documents)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=multimedia](https://localhost:4502/aem/assetpicker.html?assettype=multimedia)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=archives](https://localhost:4502/aem/assetpicker.html?assettype=archives)</li></ul> | Verwenden Sie diese Option, um die Asset-Typen basierend auf dem übergebenen Wert zu filtern. |
| root | &lt;Ordnerpfad> | [https://localhost:4502/aem/assetpicker.html?assettype=images&amp;root=/content/dam/we-retail/en/activities](https://localhost:4502/aem/assetpicker.html?assettype=images&amp;root=/content/dam/we-retail/en/activities) | Verwenden Sie diese Option, um den Stammordner für den Asset-Wähler anzugeben. In diesem Fall können Sie mit dem Asset-Wähler nur untergeordnete Assets (direkt/indirekt) unter dem Stammordner auswählen. |

Wechseln Sie für den Zugriff auf die Benutzeroberfläche des Asset-Wählers zu `https://[AEM server]:[port]/aem/assetpicker`. Navigieren Sie zum gewünschten Ordner und wählen Sie mindestens ein Asset aus. Alternativ können Sie im OmniSearch-Feld nach dem gewünschten Asset suchen, je nach Bedarf filtern und das Asset dann auswählen.

![Asset in der Asset-Auswahl suchen und auswählen](assets/assetpicker.png)

Asset in der Asset-Auswahl suchen und auswählen

## Beschränkungen {#limitations}

Die Suchfunktion in AEM Assets unterliegt folgenden Einschränkungen:

* Beginnen Sie die Suchanfrage nicht mit einem Leerzeichen, da die Suche sonst nicht funktioniert.
* AEM zeigt den Suchbegriff ggf. weiter an, nachdem Sie Eigenschaften eines Assets aus den Suchergebnissen ausgewählt und die Suche dann abgebrochen haben (CQ-4273540).
* Bei der Suche nach Ordnern bzw. Dateien und Ordnern können die Suchergebnisse mit keinem anderen Parameter sortiert werden.
* Wenn Sie die Eingabetaste drücken, ohne etwas in die OmniSearch-Leiste einzugeben, gibt AEM eine Liste mit nur Dateien ohne Ordner zurück. Wenn Sie gezielt nach Ordnern suchen, ohne einen Suchbegriff zu verwenden, gibt AEM keine Ergebnisse zurück.

Visuelle Suchen oder Ähnlichkeitssuchen weisen die folgenden Einschränkungen auf:

* Die visuelle Suche funktioniert am besten mit größeren Repositorys. Zwar ist keine Mindestanzahl von Bildern für gute Ergebnisse erforderlich, doch ist die Qualität der Treffer bei einigen Bildern möglicherweise nicht so hoch wie bei Treffern aus einem großen Repository.
* Sie können das Modell weder ändern noch AEM so trainieren, dass ähnliche Bilder gefunden werden. Das Hinzufügen oder Entfernen von Smart-Tags zu bzw. von einigen Assets verändert das Modell beispielsweise nicht. Die Assets werden aus den visuell ähnlichen Suchergebnissen ausgeschlossen.

## Suchtipps {#tips}

* Wenn Sie den Prüfungsstatus von Assets überwachen, verwenden Sie die entsprechende Option, um herauszufinden, welche Assets genehmigt wurden und für welche Assets die Genehmigung aussteht.
* Verwenden Sie das Prädikat „Einblicke“, um basierend auf den Nutzungsstatistiken diverser Creative Cloud-Programme nach unterstützten Assets zu suchen. Nutzungsdaten werden unter Nutzungsbewertung, Impressions, Klicks und Medienkanäle gruppiert, in denen die Assets anhand von Kategorien angezeigt werden.
* Aktivieren Sie Kontrollkästchen, um alle Suchergebnisse oder die gefilterten Suchergebnisse auszuwählen, die für die Auswahl verwendet werden sollen. Es werden alle gesuchten Assets ausgewählt, unabhängig davon, wie viele Assets in der aktuellen Benutzeransicht angezeigt werden. Sie können beispielsweise alle ausgewählten Assets herunterladen, Metadateneigenschaften für alle ausgewählten Assets stapelweise aktualisieren oder ausgewählte Assets einer Sammlung hinzufügen.
* Informationen zum Suchen nach Assets, die keine obligatorischen Metadaten enthalten, finden Sie unter [Obligatorische Metadaten](#mandatorymetadata).
* Die Suche nutzt alle Metadatenfelder. Eine allgemeine Suche, z. B. nach 12, gibt in der Regel viele Ergebnisse zurück. Für bessere Ergebnisse sollten Sie doppelte (nicht einfache) Anführungszeichen verwenden oder sicherstellen, dass die Zahl an ein Wort ohne Sonderzeichen angrenzt (z. B. *Schuh12*).
* Die Volltextsuche unterstützt Operatoren wie „-“, „^“ und andere. Um diese Buchstaben als alphabetische Zeichenfolgen zu suchen, setzen Sie den Suchausdruck in doppelte Anführungszeichen. Verwenden Sie z. B. „Notebook - Schönheit“ statt Notebook - Schönheit.
* Wenn es zu viele Suchergebnisse gibt, schränken Sie den [Suchbereich](#scope) ein, um die gewünschten Assets leichter finden zu können. Das funktioniert am besten, wenn Sie eine Ahnung davon haben, wie Sie besser nach den gewünschten Assets suchen können (z. B. nach einem bestimmten Dateityp, nach einem bestimmten Speicherort, nach bestimmten Metadaten usw.).

* **Tagging**: Mit Tags können Sie Assets kategorisieren, damit sie sich leichter durchsuchen und suchen lassen. Tagging hilft bei der Verbreitung der entsprechenden Taxonomie an andere Benutzer und Workflows. AEM bietet Methoden zum automatischen Taggen von Assets mit den KI-Diensten von Adobe Sensei, die beim Taggen von Assets durch Verwendung und Training immer besser werden. Bei der Suche nach Assets werden die Smart-Tags berücksichtigt, wenn die Funktion in Ihrem Konto aktiviert ist. Sie funktioniert zusammen mit der integrierten Suchfunktion. Siehe [Suchverhalten](#searchbehavior). Um die Reihenfolge zu optimieren, in der die Suchergebnisse angezeigt werden, können Sie für einige ausgewählte Assets das [Such-Ranking optimieren](#searchrank).

* **Indizierung**: In den Suchergebnissen werden nur indizierte Metadaten und Assets zurückgegeben. Um eine bessere Abdeckung und Leistung zu erzielen, stellen Sie eine ordnungsgemäße Indizierung sicher und befolgen Sie die Best Practices. Siehe [Indizierung](#searchindex).

## Einige Beispiele zur Illustration der Suche {#samples}

Verwenden Sie doppelte Anführungszeichen um Suchbegriffe, um Assets zu finden, die den genauen Wortlaut in der genauen vom Benutzer angegebenen Reihenfolge enthalten.

![Suchverhalten mit und ohne Anführungszeichen](assets/search_with_quotes.gif)

Suchverhalten mit und ohne Anführungszeichen

**Suche mit Sternchen als Platzhalter**: Wenn Sie die Suche erweitern möchten, verwenden Sie ein Sternchen vor oder nach dem Suchbegriff, um Treffer mit einer beliebigen Anzahl von Zeichen zu erhalten. Wenn Sie beispielsweise ohne Sternchen nach „run“ suchen, werden keine Assets zurückgegeben, die Varianten des Worts enthalten (auch in den Metadaten). Ein Sternchen ersetzt eine beliebige Anzahl von Zeichen. Beispiel:

* `run` gibt Assets mit dem genauen Suchbegriff „run“ zurück.
* `run*` gibt Assets mit „running“, „run“, „runaway“ usw. zurück.
* `*run` gibt „outrun“, „rerun“ usw. zurück.
* `*run*` gibt alle möglichen Kombinationen zurück.

![Illustration der Nutzung eines Sternchen-Platzhalters bei der Asset-Suche anhand eines Beispiels](assets/search_with_asterisk_run.gif)

Illustration der Nutzung eines Sternchen-Platzhalters bei der Asset-Suche anhand eines Beispiels

**Suchen mit Fragezeichen als Platzhalter**: Verwenden Sie zur Erweiterung der Suche ein oder mehrere Fragezeichen („?“), um Treffer mit der genauen Zeichenzahl zu erhalten. So gilt beispielsweise in der folgenden Illustration:

* Abfrage `run???` stimmt mit keinem Asset überein.

* Abfrage `run????` stimmt mit dem Wort `running` überein (vier Zeichen nach `run`).

* Abfrage `??run` stimmt mit dem Wort `rerun` überein (zwei Zeichen vor `run`).

![Illustration der Nutzung eines Fragezeichen-Platzhalters bei der Asset-Suche anhand eines Beispiels](assets/search_with_questionmark_run.gif)

Illustration der Nutzung eines Fragezeichen-Platzhalters bei der Asset-Suche anhand eines Beispiels

**Suchbegriff ausschließen**: Verwenden Sie einen Bindestrich, um nach Assets zu suchen, die einen Suchbegriff nicht enthalten. Beispielsweise gibt die Abfrage `running -shoe` Assets zurück, die `running`, aber nicht `shoe` enthalten. Gleichermaßen gibt die Abfrage `camp -night` Assets zurück, die `camp`, aber nicht `night` enthalten. Beachten Sie, dass die Abfrage `camp-night` Assets zurückgibt, die sowohl `camp` als auch `night` enthalten.

![Nutzung eines Bindestrichs zum Suchen nach Assets, die einen ausgeschlossenen Suchbegriff nicht enthalten](assets/search_dash_exclude_keyword.gif)
*Abbildung: Nutzung eines Bindestrichs zum Suchen nach Assets, die einen ausgeschlossenen Suchbegriff nicht enthalten*

<!--
## Configuration and administration tasks related to search functionality {#configadmin}

### Search index configurations {#searchindex}

Asset discovery relies on indexing of DAM contents, including the metadata. Faster and accurate asset discovery relies on optimized indexing and appropriate configurations. See [indexing](/help/operations/indexing.md).

<!--
### Visual or similarity search {#configvisualsearch}

Visual search uses smart tagging and requires AEM 6.5.2.0 or later. After configuring smart tagging functionality, follow these steps.

1. In AEM CRXDE, in `/oak:index/lucene` node, add the following properties and values and save the changes.

    * `costPerEntry` property of type `Double` with the value `10`.

    * `costPerExecution` property of type `Double` with the value `2`.

    * `refresh` property of type `Boolean` with the value `true`.

   This configuration allows searches from the appropriate index.

1. To create Lucene index, in CRXDE, at `/oak:index/damAssetLucene/indexRules/dam:Asset/properties`, create node named `imageFeatures` of type `nt-unstructured`. In `imageFeatures` node,

    * Add `name` property of type `String` with the value `jcr:content/metadata/imageFeatures/haystack0`.

    * Add `nodeScopeIndex` property of type `Boolean` with the value of `true`.

    * Add `propertyIndex` property of type `Boolean` with the value of `true`.

    * Add `useInSimilarity` property of type `Boolean` with the value `true`.

   Save the changes.

1. Access `/oak:index/damAssetLucene/indexRules/dam:Asset/properties/predictedTags` and add `similarityTags` property of type `Boolean` with the value of `true`.
1. Apply Smart Tags to the assets in your AEM repository. See [how to configure smart tags](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/smart-tags-technical-video-setup.html).
1. In CRXDE, in `/oak-index/damAssetLucene` node, set the `reindex` property to `true`. Save the changes.
1. (Optional) If you have customized search form then copy the `/libs/settings/dam/search/facets/assets/jcr%3Acontent/items/similaritysearch` node to `/conf/global/settings/dam/search/facets/assets/jcr:content/items`. Save all the changes.

For related information, see [understand smart tags in AEM](https://helpx.adobe.com/experience-manager/kt/help/assets/smart-tags-feature-video-understand.html) and [how to manage smart tags](/help/assets/smart-tags.md).

-->

<!--
### Mandatory metadata {#mandatorymetadata}

Business users, administrators, or DAM librarians can define some metadata as mandatory metadata that is a must for the business processes to work. For various reasons, some assets may be missing this metadata, such as legacy assets or assets migrated in bulk. Assets with missing or invalid metadata are detected and reported based on the indexed metadata property. To configure it, see [mandatory metadata](/help/assets/metadata-schemas.md#defining-mandatory-metadata).

### Modify search facets {#searchfacets}

To improve the speed of discovery, AEM Assets offers search facets using which you can filter the search results. The Filters panel includes a few standard facets by default. Administrators can customize the Filters panel to modify the default facets using the in-built predicates. AEM provides a good collection of in-built predicates and an editor to customize the facets. See [search facets](/help/assets/search-facets.md).

### Extract text when uploading assets {#extracttextupload}

You can configure AEM to extract the text from the assets when users upload assets, such as PSD or PDF files. AEM indexes the extracted text and helps users search these assets based on the extracted text. See [upload assets](/help/assets/manage-digital-assets.md#uploading-assets).

<!-- Check with gklebus if this customization is possible in Cloud Service now

### Custom predicates to filter search results {#custompredicates}

Predicates are used to create facets. Administrators can customize the search facets in the Filters panel using pre-configured predicates. These predicates can be customized using overlays. See [create custom predicates](/help/assets/searchx.md).

You can search for digital assets based on one or more of the following properties. Filters that apply on some of these properties are available by default and some other filters can be custom-created to apply on the other properties.

| Search field | Search property values |
|---|---|
| MIME Types | Images, Documents, Multimedia, Archives, or Other. |
| Last Modified | Hour, Day, Week, Month, or Year. |
| File Size | Small, Medium, or Large. |
| Publish Status | Published or Unpublished. |
| Approved Status | Approved or Rejected. |
| Orientation | Horizontal, Vertical, or Square. |
| Style | Color, or Black & White. |
| Video Height | Specified as a minimum and maximum value. Value is stored in the metadata of video renditions only. |
| Video Width | Specified as a minimum and maximum value. Value is stored in the metadata of video renditions only. |
| Video Format | DVI, Flash, MPEG4, MPEG, OGG Theora, QuickTime, Windows Media. Value is stored in the metadata of the source video and any renditions. |
| Video Codec | x264. Value is stored in the metadata of video renditions only. |
| Video Bitrate | Specified as a minimum and maximum value. Value is stored in the metadata of video renditions only. |
| Audio Codec | Libvorbis, Lame MP3, AAC Encoding. Value is stored in the metadata of video renditions only. |
| Audio Bitrate | Specified as a minimum and maximum value. Value is stored in the metadata of video renditions only. |

-->

## Arbeiten mit Asset-Suchergebnissen {#aftersearch}

Sobald Ihnen durchsuchte Assets angezeigt werden, die Ihren Kriterien entsprechen, können Sie folgende typische Aufgaben mit diesen Suchergebnissen ausführen oder die folgenden Aktionen vornehmen:

* Metadateneigenschaften und andere Informationen anzeigen.
* Ein oder mehrere Assets herunterladen.
* Desktop-Aktionen verwenden, um die Assets im Desktop-Programm zu öffnen.
* Smart-Sammlungen erstellen.

### Suchergebnisse sortieren {#sort}

Das Sortieren von Suchergebnissen hilft Ihnen, erforderliche Assets schneller zu finden. Das Sortieren von Suchergebnissen ist in der Listenansicht möglich und nur, wenn Sie die Option **[!UICONTROL [Dateien](#searchui)]**im Bedienfeld**[!UICONTROL  Filter ]**auswählen.[!DNL Assets]nutzt eine Server-seitige Sortierung, um alle Assets (wie viele auch immer) in einem Ordner oder den Ergebnissen einer Suchanfrage schnell zu sortieren. Server-seitige Sortierung liefert schnellere und genauere Ergebnisse als Client-seitige Sortierung.

In der Listenansicht lassen sich die Suchergebnisse genauso sortieren, wie Sie Assets in einem beliebigen Ordner sortieren. Die Sortierung funktioniert mit diesen Spalten: Name, Titel, Status, Dimensionen, Größe, Bewertung, Nutzung, (Datum) erstellt, (Datum) geändert, (Datum) Veröffentlicht, Workflow und Checked-out.

Mehr über Einschränkungen bei der Sortierfunktion finden Sie unter [Einschränkungen](#limitations).

### Überprüfen fon detaillierten Informationen zu einem Asset {#checkinfo}

Sie können auf der Suchergebnisseite genauere Informationen zu gefundenen Assets anzeigen.

Um alle Metadaten eines Assets anzuzeigen, wählen Sie das Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.

Um die Kommentare zu einem Asset oder den Versionsverlauf eines Assets zu überprüfen, klicken Sie auf das Asset, um eine große Vorschau zu öffnen. Öffnen Sie in der linken Leiste die Timeline und wählen Sie **[!UICONTROL Kommentare]** oder **[!UICONTROL Versionen]**. Sie können die Timeline-Aktivität genauso wie Kommentare oder Versionen auch in chronologischer Reihenfolge sortieren.

![Sortieren von Timeline-Einträgen für ein gesuchtes Asset](assets/sort_timeline_search_results.gif)

Sortieren von Timeline-Einträgen für ein gesuchtes Asset

### Herunterladen gesuchter Assets {#download}

Sie können die gesuchten Assets und ihre Ausgaben herunterladen, und zwar genauso wie normale Assets aus Ordnern. Wählen Sie in den Suchergebnissen mindestens ein Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Herunterladen]**.

### Massenaktualisierungen für Metadateneigenschaften {#metadataupdates}

Es lassen sich für die gängigen Metadatenfelder verschiedener Assets Massenaktualisierungen durchführen. Wählen Sie aus den Suchergebnissen ein oder mehrere Assets aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]** und aktualisieren Sie die Metadaten nach Bedarf. Klicken Sie abschließend auf **[!UICONTROL Speichern und schließen]**. Die zuvor vorhandenen Metadaten in den aktualisierten Feldern werden überschrieben.

Bei Assets, die in einem einzelnen Ordner oder einer Sammlung verfügbar sind, ist es einfacher, [die Metadaten stapelweise zu aktualisieren](/help/assets/manage-metadata.md#manage-assets-metadata). Bei Assets, die in verschiedenen Ordnern enthalten sind oder gemeinsamen Kriterien entsprechen, ist es schneller, durch Suchen eine Massenaktualisierung der Metadaten vorzunehmen.

### Smart-Sammlungen {#collections-1}

Eine Sammlung ist ein geordneter Satz von Assets, der Assets von verschiedenen Speicherorten enthalten kann, da Sammlungen lediglich Verweise auf diese Assets enthalten. Es gibt zwei Arten von Sammlungen:

* Eine statische Referenzliste mit Assets, Ordnern und anderen Sammlungen
* Eine dynamische Liste (Smart-Sammlung), die Assets in der Sammlung basierend auf einem Suchkriterium ausfüllt.

Sie können Smart-Sammlungen auf Grundlage der Suchkriterien erstellen. Wählen Sie im Bedienfeld **[!UICONTROL Filter]** die Option **[!UICONTROL Dateien]** und klicken Sie auf **[!UICONTROL Smart-Sammlung speichern]**. Siehe [Verwalten von Sammlungen](/help/assets/manage-collections.md).

## Unerwartete Suchergebnisse {#unexpectedresults}

**Suchen nach fehlenden Metadaten**: Bei der Suche nach Assets, denen die obligatorischen Metadaten fehlen, zeigt AEM möglicherweise einige Assets mit gültigen Metadaten an. Fehlende Metadaten werden anhand der Eigenschaft „Indizierte Metadaten“ erkannt und gemeldet. Selbst wenn die Asset-Metadaten korrigiert werden, werden sie bis zur Neuindizierung weiterhin als fehlende Metadaten angezeigt. Siehe [Obligatorische Metadaten](/help/assets/metadata-schemas.md#defining-mandatory-metadata).

**Zu viele Suchergebnisse**: Um zu viele Suchergebnisse zu vermeiden, sollten Sie die Suchergebnisse einschränken. Um beispielsweise in DAM nach Assets zu suchen, wählen Sie in der OmniSearch-Leiste `Location:Assets` aus. Weitere Suchfilter finden Sie unter [Suchbereich](#scope).

<!-- Another reason to get more than expected search results can be use of smarts tags. See [search behavior with smart tags](#withsmarttags). 
-->

<!--
**Partially related or unrelated search results**: AEM may display seemingly partially related or unrelated assets, alongside the desired assets in the search results. If you enable Enhanced Smart Tags, the search behavior changes slightly. See how it changes [after smart tagging](#withsmarttags).
-->

**Keine Vorschläge zur automatischen Vervollständigung bei neu hochgeladenen Assets**: Die Metadaten (Titel, Tags usw.) der kürzlich hochgeladenen Assets stehen nicht sofort als Vorschläge zur Verfügung, wenn Sie mit der Eingabe eines Suchbegriffs in die OmniSearch-Leiste beginnen. AEM Assets erstellt erst nach dem Ablauf eines Timeout-Zeitraums (standardmäßig eine Stunde) im Hintergrund einen Index der Metadaten für alle neu hochgeladenen oder aktualisierten Assets und fügt die Metadaten der Liste der Vorschläge hinzu.

**Keine Suchergebnisse**: Wenn AEM für eine Suchanfrage eine leere Seite anzeigt, kann dies folgende Gründe haben:

* Es sind keine Assets vorhanden, die Ihrer Abfrage entsprechen.
* Sie haben vor der Suchanfrage ein Leerzeichen eingegeben. Dabei handelt es sich um eine [bekannte Einschränkung](#limitations).

* Ein nicht unterstütztes Metadatenfeld enthält den Suchbegriff, nach dem Sie suchen. Nicht alle Metadatenfelder werden bei Suchvorgängen berücksichtigt. Siehe [Suchbereich](#scope).
* Die Ein- und Ausschaltzeit wurde für ein Asset konfiguriert und die Suche wurde während der Ausschaltzeit des Assets durchgeführt.

**Suchfilter/Prädikat ist nicht verfügbar**: Wenn in der Benutzeroberfläche keine erwartete Anpassung für Suchfilter verfügbar ist, wenden Sie sich an Ihren Administrator, um zu prüfen, ob die Anpassung für alle Autoren und auf dem Produktions-Server, den Sie verwenden, implementiert wurde. Möglicherweise war die Konfiguration falsch.

## Fehlerbehebung bei suchbezogenen Problemen {#troubleshoot}

Lernen Sie im Folgenden Probleme und mögliche Lösungen kennen:

* Wenden Sie sich an Ihren Administrator, wenn kein erwarteter Suchfilter/kein erwartetes Prädikat angezeigt wird.
* Bei der Suche nach visuell ähnlichen Bildern fehlt in den Suchergebnissen möglicherweise ein erwartetes Bild. Überprüfen Sie, ob die entsprechenden Assets indiziert und mit Smart-Tags versehen sind.
* Bei der Suche nach visuell ähnlichen Bildern kann gelegentlich auch ein scheinbar irrelevantes Bild in den Suchergebnissen angezeigt werden. AEM zeigt so viele potenziell passende Assets wie möglich an. Weniger relevante Bilder werden den Ergebnissen hinzugefügt, jedoch mit einem niedrigeren Such-Ranking. Die Qualität der Treffer und die Relevanz der gefundenen Assets nehmen ab, je weiter Sie nach unten scrollen.
