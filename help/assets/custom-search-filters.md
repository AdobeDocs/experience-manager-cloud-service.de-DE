---
title: Benutzerdefinierte Suchfilter
description: Erfahren Sie mehr über das Anpassen von Suchfiltern in Formularen
role: User, Leader, Developer
exl-id: 383e8165-439e-447b-a19d-d5446238a13f
source-git-commit: 0484b8ac158f0590d5ada7536cf8b547c71ab686
workflow-type: tm+mt
source-wordcount: '1280'
ht-degree: 13%

---

# Suchfilter anpassen {#customize-search-filters}

Suchfilter ermöglichen es Ihnen, Suchergebnisse basierend auf verschiedenen Parametern wie Datum, Dateityp, Tags und Relevanz zu verfeinern, wodurch die Präzision von Suchabfragen verbessert wird. Durch die Anwendung von Filtern können Sie schnell und effizient die relevantesten Ergebnisse durchsuchen. Dies spart nicht nur Zeit, sondern verbessert auch das Gesamterlebnis bei der Suche, indem die Ergebnisse auf spezifische Voreinstellungen und Bedürfnisse zugeschnitten werden.
Weitere Informationen über [Suche](search-assets-view.md).

Benutzerdefinierte Suchfilter können nur Einträgen in Ihrem durchsuchbaren Eigenschaftsindex zugeordnet werden. Stellen Sie sicher, dass alle benutzerdefinierten Metadaten enthalten sind, bevor Sie Ihr benutzerdefiniertes Filtererlebnis konfigurieren. [!DNL Assets view] können Suchfilter angepasst werden, um den Suchvorgang zu optimieren. Um die Suchfiltervorlage anzupassen, führen Sie die folgenden Schritte aus:

1. Navigieren Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**.
1. Navigieren Sie zur Registerkarte **[!UICONTROL Suche]**. Klicken Sie **[!UICONTROL Anpassen]**, um Ihr Suchformular zu konfigurieren.

   ![Benutzerdefinierte Suchfiltereinstellungen](assets/custom-search-filter.png)

1. Das [!UICONTROL Filter konfigurieren] wird angezeigt. Stellen Sie sicher, dass Sie sich im Bearbeitungsmodus befinden, damit Sie Änderungen an der Vorlage vornehmen können. Sie können in den [!UICONTROL Vorschaumodus] wechseln, um die Vorschau eines vorhandenen Suchformulars anzuzeigen.
1. Legen Sie Filterelemente aus den [benutzerdefinierten Filtern](#available-custom-filters) auf der Arbeitsfläche ab. Sie können die Komponente bei Bedarf per Drag-and-Drop verschieben, um sie neu anzuordnen.

   >[!VIDEO](https://video.tv.adobe.com/v/3443080)

1. Klicken Sie **[!UICONTROL Vorschaumodus]**, um die Änderungen zu überprüfen.
1. Klicken Sie **[!UICONTROL Bestätigen]**, um zu speichern.

## Verfügbare benutzerdefinierte Filter {#available-custom-filters}

Die Assets-Ansicht bietet die folgenden benutzerdefinierten Filter, die je nach Anforderung rekonfigurierbar sind:

* [Filterelemente](#filter-elements)
* [Vorkonfigurierte Filter](#preconfigured-filters)

### Filterelemente {#filter-elements}

Sie können eine Sammlung von Filterelementen auf der Arbeitsfläche für benutzerdefinierte Suchfilter verwenden. Diese Elemente können basierend auf der Verwendbarkeit von Sucheigenschaftsattributen neu konfiguriert werden. Sie können jedoch die [Filtereigenschaften](#filter-properties) Ihren Anforderungen entsprechend anpassen. Die folgenden Filterelemente sind in [!DNL Assets view] verfügbar:

<table>
    <tr>
        <th>Filterelemente</th>
        <th>Beschreibung</th>
        <th>Eigenschaften</th>
    </tr>
    <tr>
        <td>Text</td>
        <td>Ein Textfeld ist ein Eingabebereich, in den Sie Informationen zum Filter eingeben können.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Werte
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Optionen</td>
        <td>Optionen beziehen sich auf die verfügbaren Alternativen zur Auswahl eines bevorzugten Elements aus einer Liste.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Werte
                <li>Optionen
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Boolesch</td>
        <td>Ein boolescher Wert stellt einen wahren Wert dar. Es kann dort verwendet werden, wo man spezifisch sein möchte, um eine Option unter anderen auszuwählen.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Zahl</td>
        <td>Verwenden Sie dieses Filterelement, um einen numerischen Wert darzustellen.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Auswahlart
                <li>Schrittweite
                <li>Schrittwert
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Dropdown</td>
        <td>Zur Auswahl zwischen verschiedenen Optionen, die in einer Optionsliste angezeigt werden.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Optionen
                <li>Werte
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Datum</td>
        <td>Dient zur Angabe des Datums.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Auswahlart
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Pfad-Browser</td>
        <td>Wird zum Navigieren durch Dateien oder Ordner im Experience Manager-Repository verwendet.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Pfad-Explorer
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Tags</td>
        <td>Wird verwendet, um Tags aus den verfügbaren Optionen auszuwählen. Tags bieten spezifischere Informationen über die Assets und verbessern ihre Auffindbarkeit. Auf die ausgewählten Assets bereits angewendete Tags werden im Bedienfeld <b>Eigenschaften</b> angezeigt. Wenn Sie Tags in einer benutzerdefinierten Metadateneigenschaft speichern und den Stammpfad verwenden, um ihn auf eine Hierarchie zu beschränken, können Sie dieselbe Konfiguration in Ihren Suchfiltern nutzen. Wenn Sie die entsprechenden Tags nicht finden können, erstellen Sie sie und weisen Sie sie den ausgewählten Assets zu. Weitere Informationen zum Erstellen und Zuweisen von Tags zu Assets finden Sie unter <a href = "tagging-management-assets-view.md"> Verwalten von Tags in der Assets-</a> .</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Tag-Auswahl
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>User</td>
        <td>Wird verwendet, um den Benutzertyp unter Administratoren, Standardbenutzenden und Privatkunden anzugeben.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Beschreibung
            </ul>
        </td>
    </tr>
</table>

### Vorkonfigurierte Filter {#preconfigured-filters}

Die vorkonfigurierten Filter sind Voreinstellungen, mit denen Sie sie direkt auf der Arbeitsfläche verwenden können. Sie können jedoch die [Filtereigenschaften](#filter-properties) Ihren Anforderungen entsprechend anpassen. Die folgenden Filter sind in [!DNL Assets view] vorkonfiguriert:

<table>
    <tr>
        <th>Vorkonfigurierte Filter</th>
        <th>Beschreibung</th>
        <th>Eigenschaften</th>
    </tr>
    <tr>
        <td>Dateityp</td>
        <td>Filtern Sie die Suchergebnisse nach den unterstützten Dateitypen: „Bilder“, „Dokumente“ und „Videos“.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Auswahlart
                <li>Optionen
                <li>Werte
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Dateiformat</td>
        <td>Assets View unterstützt alle binären Dateiformate mit grundlegenden Services wie Speichern, Hochladen, Kopieren, Verschieben, Löschen und Hinzufügen von Metadaten.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Auswahlart
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Bildgröße</td>
        <td>Geben Sie eine oder mehrere der minimalen und maximalen Abmessungen zum Filtern von Bildern an. Die Größe wird in Pixeln angegeben und ist nicht die Dateigröße der Bilder.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Auswahlart
                <li>Schrittweite
                <li>Schrittwert
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Bildbreite</td>
        <td>Vertikale Abmessungen eines Bildes.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Auswahlart
                <li>Schrittweite
                <li>Schrittwert
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Bildhöhe</td>
        <td>Horizontale Abmessungen eines Bildes.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Auswahlart
                <li>Schrittweite
                <li>Schrittwert
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Erstellungsdatum</td>
        <td>Datumsbereich, in dem die Assets erstellt wurden.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Auswahlart
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Änderungsdatum</td>
        <td>Datumsbereich, in dem Assets geändert wurden.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Auswahlart
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Asset-Status</td>
        <td>Mit der Assets-Ansicht können Sie den Status für im Repository verfügbare Assets festlegen. Legen Sie einen Asset-Status fest, um die nachgelagerte Nutzung digitaler Assets besser steuern und verwalten zu können. Wählen Sie zwischen <b>Genehmigt, Abgelehnt oder Kein Status</b>.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Auswahlart
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Smart-Tags</td>
        <td>Filtern Sie Assets mithilfe von Smart-Tags, die im Experience Manager-Repository hinzugefügt werden.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Auswahlart
                <li>Unterstützung von Trennzeichen
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Status von Dynamic Media</td>
        <td>Wählen Sie den Status eines Assets als veröffentlicht oder unveröffentlicht aus.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Auswahlart
                <li>Optionen
                <li>Werte
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Ablaufdatum</td>
        <td>Filtern Sie Assets und geben Sie einen Datumsbereich an, nach dem die Assets nicht mehr gültig oder erforderlich sind. </td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Auswahlart
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Tags (Taxonomie)</td>
        <td>Es handelt sich um ein System zur Organisation und Klassifizierung digitaler Assets mithilfe von Tags, bei dem im Wesentlichen eine hierarchische Struktur von Keywords erstellt wird, mit der Benutzende mühelos relevante Inhalte suchen und finden können, indem sie bestimmte Tags auf jedes Asset anwenden. </td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Tag-Auswahl
                <li>Beschreibung
            </ul>
        </td>
    </tr>
</table>

#### Filtern von Eigenschaften {#filter-properties}

Jedes Filterelement ist mit einer Reihe von Eigenschaften verknüpft. Die folgenden Eigenschaften werden im Filter und in den vorkonfigurierten Elementen verwendet:

<table>
    <tr>
        <th>Eigenschaften</th>
        <th>Werte</th>
        <th>Beschreibung</th>
    </tr>
    <tr>
        <td>Label</td>
        <td>Text</td>
        <td>Er ist eine Kennung des verwendeten Filters.</td>
    </tr>
    <tr>
        <td>Metadaten</td>
        <td>Dropdown</td>
        <td>Die Metadateneigenschaft wird verwendet, um genehmigte Metadaten aus dem Adobe Experience Manager Assets-Repository zuzuordnen. Sie können den Metadatenwert aus dem Dropdown-Menü auswählen, der dem Filterelement zugeordnet werden muss. </td>
    </tr>
    <tr>
        <td>Auswahlart</td> 
        <td>Einzel, Mehrere, Exakt oder Bereich </td>
        <td>
            <ul>
                <li><b>Einzelauswahl</b> ermöglicht die Auswahl eines Elements nach dem anderen, was sich ideal für unterschiedliche Auswahlmöglichkeiten eignet.
                <li><b>Mehrfachauswahl</b> ermöglicht die Auswahl mehrerer Elemente gleichzeitig, was für die Auswahl mehrerer Optionen nützlich ist. 
                <li><b>Exakte Auswahl</b> ermöglicht die Auswahl eines einzelnen Elements aus verschiedenen Optionen.
                <li><b>Bereichsauswahl</b> ermöglicht die Auswahl eines kontinuierlichen Satzes von Werten innerhalb eines definierten Bereichs, der für die Auswahl eines Datumsbereichs oder numerischer Werte nützlich ist.
            </ul>
        </td>   
    </tr>
    <tr>
        <td>Optionen</td>
        <td>Manueller JSON-Pfad oder CSV-Upload</td>
        <td>
            <ul>
                <li>Wählen Sie <b>Manuell</b> aus, wenn Sie Optionen manuell hinzufügen möchten. 
                <li>Wählen Sie <b>JSON-Pfad</b> aus, um Optionen aus der JSON-Datei hinzuzufügen. 
                <li>Wählen Sie <b>CSV-Upload</b>, um eine CSV-Datei zu importieren, die die in den Optionen hinzuzufügenden Werte enthält.
            </ul>
        </td>
    </tr>
    <tr>
       <td>Werte</td>
        <td>Hinzufügen oder bearbeiten</td>
        <td>
        <ul>
        <li>Klicken Sie <b>Hinzufügen</b>, um einen neuen Wert hinzuzufügen. 
        <li>Klicken Sie auf <span>✎</span>, um den Titel zu bearbeiten. 
        <li>Klicken Sie auf <span>??</span>, um den Optionswert zu löschen. 
        <li>Klicken Sie <b>Bearbeiten</b>, um die Bearbeitungsoptionen zu ändern. 
        <li>Sie können auch die Reihenfolge der Optionen ändern, indem Sie sie gedrückt halten.
        </td>
    </tr>
    <tr>
        <td>Unterstützung von Trennzeichen</td>
        <td>Aktivieren oder Deaktivieren</td>
        <td>Ein Trennzeichen ist ein Symbol zum Trennen verschiedener Elemente im Text. Beispiel: Kommas, Leerzeichen oder Semikolons.</td>
    </tr>
    <tr>
        <td>Schrittweite</td>
        <td>Wert</td>
        <td>Aktivieren Sie die Schaltfläche Schritt , um das Zahlenfeld zu ändern und den Wert bei jedem Klick zu erhöhen oder zu verringern. </td>
    </tr>
    <tr>
        <td>Schrittwert </td>
        <td>Zahl</td>
        <td>Sie zeigt den Wert zum Erhöhen/Verringern bei Verwendung der Schaltfläche „Schritt“ an. Es wird angezeigt, wenn „Schritte“ aktiviert ist.</td>
    </tr>
    <tr>
        <td>Beschreibung</td>
        <td>Text</td>
        <td>Fügen Sie eine detaillierte Erklärung hinzu, um zusätzliche Informationen über das Filterelement bereitzustellen.</td>
    </tr>
</table>


## Löschen eines Filterelements {#delete-a-filter-element}

Gehen Sie wie folgt vor, um einen Suchfilter zu löschen:

1. Navigieren Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**.
1. Navigieren Sie zur Registerkarte **[!UICONTROL Suche]**. Klicken Sie **[!UICONTROL Anpassen]**, um Ihr Suchformular zu konfigurieren.
1. Das [!UICONTROL Filter konfigurieren] wird angezeigt. Stellen Sie sicher, dass Sie sich im Bearbeitungsmodus befinden, damit Sie Änderungen an der Vorlage vornehmen können.
1. Wählen Sie das Filterelement aus, das Sie löschen möchten. Wählen Sie beispielsweise &quot;**[!UICONTROL &quot;]**.
1. Klicken Sie **[!UICONTROL Kategorie löschen]**, um das Filterelement zu löschen. Das **[!UICONTROL Bildhöhe]**-Element wird aus der Arbeitsfläche entfernt.
1. Klicken Sie **[!UICONTROL Bestätigen]**, um das Formular zu speichern.

## Verwenden benutzerdefinierter Suchfilter{#using-custom-search-filters}

Nachdem Sie die Suchfilter konfiguriert haben, können Sie sie für die Suche nach Assets im Repository verwenden.

![Verwenden benutzerdefinierter Suchfilter](assets/using-custom-search-filters.png)

>[!MORELIKETHIS]
>
>* [Suchen von Assets](search-assets-view.md)
