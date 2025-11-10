---
title: Benutzerdefinierte Suchfilter
description: Erfahren Sie mehr über das Anpassen von Suchfiltern in Formularen
role: User, Leader, Developer
exl-id: 383e8165-439e-447b-a19d-d5446238a13f
source-git-commit: 836805b4eac5ab940dff5c66ec0dcf1ca8652837
workflow-type: tm+mt
source-wordcount: '1425'
ht-degree: 85%

---


# Anpassen von Suchfiltern {#customize-search-filters}

Suchfilter ermöglichen es Ihnen, Suchergebnisse basierend auf verschiedenen Parametern wie Datum, Dateityp, Tags und Relevanz zu optimieren, wodurch die Präzision von Suchabfragen verbessert wird. Durch das Anwenden von Filtern können Sie schnell und effizient die relevantesten Ergebnisse durchsuchen. Dies spart nicht nur Zeit, sondern verbessert auch das Gesamterlebnis bei der Suche, indem die Ergebnisse auf konkrete Vorlieben und Bedürfnisse zugeschnitten werden.
Weitere Informationen über die [Suche](search-assets-view.md).

Angepasste Suchfilter in AEM Assets können nur Einträgen in Ihrem durchsuchbaren Eigenschaftsindex zugeordnet werden. Stellen Sie sicher, dass alle benutzerdefinierten Metadaten enthalten sind, bevor Sie Ihr benutzerdefiniertes Filtererlebnis konfigurieren. Mit [!DNL Assets view] können Suchfilter angepasst werden, um den Suchvorgang zu optimieren. Um die benutzerdefinierten Suchfilter von AEM Assets anzupassen, führen Sie die folgenden Schritte aus:

1. Navigieren Sie **[!UICONTROL Einstellungen]** > **[!UICONTROL Allgemeine Einstellungen]** > **[!UICONTROL Suche]**.

   <!--1. Go to the **[!UICONTROL Search]** tab. Click **[!UICONTROL Customize]** to configure your search form.-->

   ![Einstellungen für benutzerdefinierte Suchfilter](assets/custom-search-filter.png)

1. Im Abschnitt **[!UICONTROL Filter]** können Sie Folgendes konfigurieren:

   * **[!UICONTROL Dateien]:** Das Konfigurieren von Dateien umfasst Dateitypen, Dateiformate, den Status von Assets, die Dateigröße, Bildabmessungen, das Erstellungsdatum, das Änderungsdatum usw.
   * **[!UICONTROL Ordner]:** Konfigurieren von Ordnern umfasst das Erstellungsdatum, das Datum, das verworfen wurde, das verworfen wurde usw.
   * **[!UICONTROL Sammlungen]:** Konfigurieren von Sammlungen umfasst die Sichtbarkeit der Sammlung, den Sammlungstyp, das Erstellungsdatum usw.

1. Sie können eine Vorschau des Standardformulars **[!UICONTROL Vorgabenfilter]** anzeigen, das für Dateien, Ordner oder Sammlungen verfügbar ist. Sie können dieses bereits vorhandene Formular jedoch nicht anpassen oder löschen. Alternativ können Sie ein benutzerdefiniertes Filterformular erstellen, indem Sie auf **[!UICONTROL Neues Formular hinzufügen]** klicken.

   >[!NOTE]
   >
   >Pro Kategorie (Datei, Ordner oder Sammlung) kann nur ein benutzerdefiniertes Filterformular erstellt werden.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

## Aktionen in einem konfigurierten Formular {#Actions-on-configured-form}

Sie können die folgenden Aktionen in einem konfigurierten Formularfilterformular verwenden:

* **[!UICONTROL Anpassen]:** Klicken Sie, um das Formular hinzuzufügen oder zu ändern. Sie können Filterelemente aus den [benutzerdefinierten Filtern](#available-custom-filters) auf der Arbeitsfläche ablegen oder bei Bedarf neu anordnen.

* **[!UICONTROL Vorschau]:** Klicken Sie, um die Änderungen zu überprüfen.

* **[!UICONTROL Als Standard festlegen]:** Klicken, um das ausgewählte Formular als Standard festzulegen.

* **[!UICONTROL Formular löschen]:** Klicken Sie auf Weitere Optionen ![weitere Optionen](assets/do-not-localize/more-icon.svg) und wählen Sie **[!UICONTROL Formular löschen]**, um die ausgewählten Formularfilter zu löschen.

* **[!UICONTROL Formularbeschriftungen bearbeiten]:** Klicken Sie auf Weitere Optionen ![weitere Optionen](assets/do-not-localize/more-icon.svg) und fügen Sie Ihrem benutzerdefinierten Formularfilter eine neue Beschriftung und Beschreibung hinzu.

  ![Bearbeiten von Formularbeschriftungen](assets/edit-form-labels.png)

## Verfügbare benutzerdefinierte Filter {#available-custom-filters}

Die Assets-Ansicht bietet die folgenden benutzerdefinierten Filter, die je nach Anforderung neu konfigurierbar sind:

* [Filterelemente](#filter-elements)
* [Vorkonfigurierte Filter](#preconfigured-filters)

### Filterelemente {#filter-elements}

Benutzerdefinierte Filter in AEM Assets ermöglichen Ihnen die Verwendung einer Sammlung von Filterelementen auf der Arbeitsfläche für benutzerdefinierte Suchfilter. Diese Elemente können basierend auf der Verwendbarkeit von Sucheigenschaftsattributen neu konfiguriert werden. Sie können jedoch die [Filtereigenschaften](#filter-properties) Ihren Anforderungen entsprechend anpassen. Die folgenden Filterelemente sind in [!DNL Assets view] verfügbar:

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
        <td>Boolescher Wert</td>
        <td>Ein boolescher Wert stellt einen wahren Wert dar. Er kann dort verwendet werden, wo Sie konkret eine Option unter mehreren auswählen möchten.</td>
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
                <li>Schritte
                <li>Schrittwert
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Dropdown</td>
        <td>Zur Auswahl zwischen verschiedenen Optionen, die in einer Liste mit Optionen angezeigt werden.</td>
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
        <td>Wird zur Angabe des Datums verwendet.</td>
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
        <td>Wird verwendet, um Tags aus den verfügbaren Optionen auszuwählen. Tags bieten genauere Informationen über die Assets und verbessern ihre Auffindbarkeit. Bereits auf die ausgewählten Assets angewendete Tags werden im Panel <b>Eigenschaften</b> angezeigt. Wenn Sie Tags in einer benutzerdefinierten Metadateneigenschaft speichern und den Stammpfad verwenden, um ihn auf eine Hierarchie zu beschränken, können Sie dieselbe Konfiguration in Ihren Suchfiltern nutzen. Wenn Sie die entsprechenden Tags nicht finden können, erstellen Sie sie und weisen Sie sie den ausgewählten Assets zu. Weitere Informationen zum Erstellen von Tags und Zuweisen von diesen zu Assets finden Sie unter <a href = "tagging-management-assets-view.md">Verwalten von Tags in der Asset-Ansicht</a>.</td>
        <td>
            <ul>
                <li>Label
                <li>Metadaten
                <li>Tag-Wähler
                <li>Beschreibung
            </ul>
        </td>
    </tr>
    <tr>
        <td>Benutzerin bzw. Benutzer</td>
        <td>Wird verwendet, um den Benutzertyp unter Admins, Standardbenutzenden und Verbrauchenden anzugeben.</td>
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

Die vorkonfigurierten Filter sind Voreinstellungen, die direkt auf der Arbeitsfläche verwendet werden können. Sie können jedoch die [Filtereigenschaften](#filter-properties) Ihren Anforderungen entsprechend anpassen. Die folgenden Filter sind in [!DNL Assets view] vorkonfiguriert:

<table>
    <tr>
        <th>Vorkonfigurierte Filter</th>
        <th>Beschreibung</th>
        <th>Eigenschaften</th>
    </tr>
    <tr>
        <td>Dateityp</td>
        <td>Filtern Sie die Suchergebnisse nach den unterstützten Dateitypen „Bilder“, „Dokumente“ und „Videos“.</td>
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
        <td>Die Assets-Ansicht unterstützt alle binären Dateiformate mit grundlegenden Services wie Speichern, Hochladen, Kopieren, Verschieben, Löschen und Hinzufügen von Metadaten.</td>
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
                <li>Schritte
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
                <li>Schritte
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
                <li>Schritte
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
        <td>In der Assets-Ansicht können Sie den Status der im Repository verfügbaren Assets festlegen. Legen Sie einen Asset-Status fest, um die nachgelagerte Nutzung digitaler Assets besser steuern und verwalten zu können. Wählen Sie zwischen <b>„Genehmigt“, „Abgelehnt“ oder „Kein Status“</b>.</td>
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
        <td>Dynamic Media-Status</td>
        <td>Wählen Sie beim Status eines Assets zwischen „Veröffentlicht“ und „Unveröffentlicht“.</td>
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
        <td>Filtern Sie Assets und geben Sie einen Datumsbereich an, nach dem die Assets nicht mehr gültig sind oder benötigt werden. </td>
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
                <li>Tag-Wähler
                <li>Beschreibung
            </ul>
        </td>
    </tr>
</table>

#### Filtereigenschaften {#filter-properties}

Jedes Filterelement ist mit einer Reihe von Eigenschaften verknüpft. AEM Assets passt Suchfilter an und verwendet die folgenden Eigenschaften in den Filtern und vorkonfigurierten Elementen:

<table>
    <tr>
        <th>Eigenschaften</th>
        <th>Werte</th>
        <th>Beschreibung</th>
    </tr>
    <tr>
        <td>Label</td>
        <td>Text</td>
        <td>Eine Kennung des verwendeten Filters.</td>
    </tr>
    <tr>
        <td>Metadaten</td>
        <td>Dropdown</td>
        <td>Die Metadateneigenschaft wird verwendet, um genehmigte Metadaten aus dem Adobe Experience Manager Assets-Repository zuzuordnen. Sie können aus dem Dropdown-Menü den Metadatenwert auswählen, der dem Filterelement zugeordnet werden muss. </td>
    </tr>
    <tr>
        <td>Auswahlart</td> 
        <td>Einzel, Mehrfach, Exakt oder Bereich </td>
        <td>
            <ul>
                <li>Die <b>Einzelauswahl</b> ermöglicht die Auswahl eines Elements nach dem anderen und eignet sich ideal für unterschiedliche Auswahlmöglichkeiten.
                <li>Die <b>Mehrfachauswahl</b> ermöglicht die Auswahl mehrerer Elemente gleichzeitig und ist bei der Auswahl mehrerer Optionen nützlich. 
                <li>Die <b>exakte Auswahl</b> ermöglicht die Auswahl eines einzelnen Elements aus verschiedenen Optionen.
                <li>Die <b>Bereichsauswahl</b> ermöglicht die Auswahl eines kontinuierlichen Satzes von Werten innerhalb eines definierten Bereichs und ist für die Auswahl eines Datumsbereichs oder numerischer Werte nützlich.
            </ul>
        </td>   
    </tr>
    <tr>
        <td>Optionen</td>
        <td>Manuell, JSON-Pfad oder CSV-Upload</td>
        <td>
            <ul>
                <li>Wählen Sie <b>Manuell</b> aus, wenn Sie Optionen manuell hinzufügen möchten. 
                <li>Wählen Sie <b>JSON-Pfad</b> aus, um Optionen aus der JSON-Datei hinzuzufügen. 
                <li>Wählen Sie <b>CSV-Upload</b>, um eine CSV-Datei mit den in den Optionen hinzuzufügenden Werten zu importieren.
            </ul>
        </td>
    </tr>
    <tr>
       <td>Werte</td>
        <td>Hinzufügen oder Bearbeiten</td>
        <td>
        <ul>
        <li>Klicken Sie auf <b>Hinzufügen</b>, um einen neuen Wert hinzuzufügen. 
        <li>Klicken Sie auf <span>✎</span>, um das Label zu bearbeiten. 
        <li>Klicken Sie auf <span>??</span>, um den Optionswert zu löschen. 
        <li>Klicken Sie <b>Bearbeiten</b>, um die Bearbeitungsoptionen zu ändern. 
        <li>Sie können auch die Sequenz der Optionen ändern, indem Sie sie gedrückt halten.
        </td>
    </tr>
    <tr>
        <td>Unterstützung von Trennzeichen</td>
        <td>Aktivieren oder Deaktivieren</td>
        <td>Ein Trennzeichen ist ein Symbol zum Trennen verschiedener Elemente im Text. Beispielsweise Kommas, Leerzeichen oder Semikolons.</td>
    </tr>
    <tr>
        <td>Schritte</td>
        <td>Wert</td>
        <td>Aktivieren Sie die Schrittschaltflächen im Zahlenfeld, um den Wert beim Klicken zu erhöhen oder zu verringern. </td>
    </tr>
    <tr>
        <td>Schrittwert </td>
        <td>Zahl</td>
        <td>Gibt bei Verwendung der Schrittschaltfläche den Inkrement-/Dekrementwert an. Wird angezeigt, wenn Schritte aktiviert sind.</td>
    </tr>
    <tr>
        <td>Beschreibung</td>
        <td>Text</td>
        <td>Fügen Sie eine detaillierte Erklärung hinzu, um zusätzliche Informationen zum Filterelement bereitzustellen.</td>
    </tr>
</table>

>[!VIDEO](https://video.tv.adobe.com/v/3443080)

## Löschen eines Filterelements {#delete-a-filter-element}

Um einen Suchfilter zu löschen, führen Sie die folgenden Schritte aus:

1. Navigieren Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**.
1. Navigieren Sie zur Registerkarte **[!UICONTROL Suchen]**. Klicken Sie auf **[!UICONTROL Anpassen]**, um Ihr Suchformular zu konfigurieren.
1. Das Formular [!UICONTROL Filter konfigurieren] wird angezeigt. Stellen Sie sicher, dass Sie sich im Bearbeitungsmodus befinden, damit Sie Änderungen an der Vorlage vornehmen können.
1. Wählen Sie das Filterelement aus, das Sie löschen möchten. Wählen Sie beispielsweise **[!UICONTROL Bildhöhe]** aus.
1. Klicken Sie auf **[!UICONTROL Kategorie löschen]**, um das Filterelement zu löschen. Das Element **[!UICONTROL Bildhöhe]** wird von der Arbeitsfläche entfernt.
1. Klicken Sie auf **[!UICONTROL Bestätigen]**, um das Formular zu speichern.

## Verwenden benutzerdefinierter Suchfilter{#using-custom-search-filters}

Nachdem Sie die Suchfilter konfiguriert haben, können Sie sie für die Suche nach Assets im Repository verwenden.

![Verwenden benutzerdefinierter Suchfilter](assets/using-custom-search-filters.png)

>[!MORELIKETHIS]
>
>* [Suchen von Assets](search-assets-view.md)
