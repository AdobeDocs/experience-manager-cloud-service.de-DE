---
title: Verwalten digitaler Assets
description: Verschieben, Löschen, Kopieren, Umbenennen, Aktualisieren und Versionieren von Assets in [!DNL Assets view].
role: User, Leader
contentOwner: AG
exl-id: 2459d482-828b-4410-810c-ac55ef0a2119
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: 89c47db38bf26f8c5984278e49ad7727a8ec03e5
workflow-type: ht
source-wordcount: '1700'
ht-degree: 100%

---

# Verwalten von Assets {#manage-assets}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

Mithilfe der benutzerfreundlichen Oberfläche von [!DNL Assets view] können Sie mühelos verschiedene Aufgaben des Digital Asset Management (DAM) ausführen. Nachdem Sie die Assets hinzugefügt haben, können Sie sie suchen, herunterladen, verschieben, kopieren, umbenennen, löschen, aktualisieren und bearbeiten.

Verwenden Sie [!DNL Assets view], um die folgenden Asset-Management-Aufgaben auszuführen. Wenn Sie ein Asset auswählen, werden die folgenden Optionen in der Symbolleiste oben angezeigt.

![Symbolleistenoptionen bei der Auswahl eines Assets](assets/toolbar-image-selected.png)

*Abbildung: In der Symbolleiste verfügbare Optionen für ein ausgewähltes Bild.*

* ![Symbol zum Aufheben der Auswahl](assets/do-not-localize/close-icon.png) Aufheben der Auswahl.

* ![Symbol „Ähnliche suchen“](assets/do-not-localize/find-similar.svg) Suchen Sie anhand der Metadaten und Smart Tags nach ähnlichen Bild-Assets in der Assets-Benutzeroberfläche.

* ![details icon](assets/do-not-localize/edit-in-icon.png) Anklicken, um ein Asset in der Vorschau anzuzeigen und die detaillierten Metadaten anzuzeigen. Aus der Vorschau heraus können Sie die Versionen anzeigen und ein Bild bearbeiten.

* ![download icon](assets/do-not-localize/download-icon.png) Lädt das ausgewählte Asset in Ihr lokales Dateisystem herunter.

* ![Symbol „Zu Sammlung hinzufügen“](assets/do-not-localize/add-collection.svg) Fügt das ausgewählte Asset zu einer Sammlung hinzu.

* ![Symbol „Assets anheften“](assets/do-not-localize/pin-quick-access.svg) Heftet ein Asset an, um bei späterem Bedarf schneller darauf zugreifen zu können. Alle angehefteten Elemente werden im Dashboard „Mein Arbeitsbereich“ im Abschnitt **Schnellzugriff** angezeigt.

* ![Symbol „In Express bearbeiten“](assets/do-not-localize/edit-e.svg) Bearbeiten eines Bildes in der integrierten Adobe Express-Anwending in Adobe Experience Manager Assets.

* ![Symbol „Asset bearbeiten“](assets/do-not-localize/edit-e.svg) Bearbeiten des Bildes mit Adobe Express.

* ![Symbol „Asset-Link freigeben“](assets/do-not-localize/share-link.svg) für Assets mit anderen Benutzenden, damit diese darauf zugreifen und die Assets herunterladen können.

* ![delete icon](assets/do-not-localize/delete-icon.png) Löscht das ausgewählte Asset oder den ausgewählten Ordner.

* ![copy icon](assets/do-not-localize/copy-icon.png) Kopiert die ausgewählte Datei oder den ausgewählten Ordner.

* ![move icon](assets/do-not-localize/move-icon.png) Verschiebt das ausgewählte Asset oder den ausgewählten Ordner an einen anderen Speicherort in der Repository-Hierarchie.

* ![rename icon](assets/do-not-localize/rename-icon.png) Benennt das ausgewählte Asset oder den ausgewählten Ordner um. Verwenden Sie einen eindeutigen Namen, sonst schlägt die Umbenennung mit einer Warnung fehl. Sie können es mit einem anderen Namen erneut versuchen.
Außerdem können Sie auf den Titel eines Assets oder eines Ordners klicken, um ihn umzubenennen. Geben Sie den neuen Text in das Textfeld **Asset umbenennen** ein und klicken Sie auf **Speichern**. Diese Funktion ist in den Ansichten „Raster“, „Galerie“, „Wasserfall“ und „Liste“ verfügbar.

* ![Symbol „Wasserfallansicht“](assets/do-not-localize/waterfall-view.png) [!UICONTROL Wasserfallansicht].

* ![Symbol „Bibliothek kopieren“](assets/do-not-localize/copy-icon.png) Fügt ein Asset zur Bibliothek hinzu.

* ![Symbol „Aufgabe zuweisen“](assets/do-not-localize/review-delegate-icon.png) Weist anderen Benutzenden Aufgaben zu, damit sie an einem Asset zusammenarbeiten können.

* ![Symbol „Aufgabe zuweisen“](assets/do-not-localize/watch-asset.svg) Überwachen der an einem Asset ausgeführten Vorgänge.

Sie können die gleichen Optionen bei den Miniaturansichten der Assets anzeigen.

![Optionen für die Asset-Miniaturansicht zum Verwalten eines Assets](assets/options-on-thumbnail.png)

[!DNL Assets view] zeigt nur die relevanten Optionen in der Symbolleiste an, die vom Typ des ausgewählten Assets abhängen.

![Symbolleistenoptionen bei der Auswahl eines Assets](assets/toolbar-folder-selected.png)

*Abbildung: In der Symbolleiste verfügbare Optionen für einen ausgewählten Ordner.*

![Symbolleistenoptionen bei der Auswahl eines Assets](assets/toolbar-pdf-selected.png)

*Abbildung: In der Symbolleiste verfügbare Optionen für eine ausgewählte PDF-Datei.*

## Herunterladen und Verteilen von Assets {#download}

Sie können ein oder mehrere Assets oder Ordner oder eine Kombination aus beiden auswählen und die Auswahl in Ihr lokales Dateisystem herunterladen. Sie können die Assets bearbeiten und erneut hochladen oder die Assets außerhalb von [!DNL Assets view] verteilen. Sie können auch [die Ausgabedarstellungen eines Assets herunterladen](/help/assets/add-delete-assets-view.md#renditions).

## Asset-Versionierung {#versions-of-assets}

<!-- 
TBD: query for engineering: How many versions are maintained. What happens when we reach that limit? Are old versions automatically removed? -->

[!DNL Assets view] versioniert die Assets, wenn die Assets, die aktualisiert oder bearbeitet werden, erneut hochgeladen werden. Sie können den Versionsverlauf und frühere Versionen anzeigen und eine frühere Version von Assets als neueste Version wiederherstellen, die bei Bedarf auf eine frühere Version zurückgesetzt wird. Asset-Versionen werden in den folgenden Szenarien erstellt:

* Ein neues Asset wird mit demselben Dateinamen wie ein vorhandenes Asset und in denselben Ordner wie das vorhandene Asset hochgeladen. [!DNL Assets view] fordert dazu auf, entweder das vorherige Asset zu überschreiben oder das neue Asset als Version zu speichern. Siehe [Hochladen von Asset-Duplikaten](/help/assets/add-delete-assets-view.md).

  ![Erstellen von Versionen beim Hochladen](assets/uploads-manage-duplicates.png)

  *Abbildung: Beim Hochladen eines Assets mit dem Namen eines vorhandenen Assets können Sie eine Version des Assets erstellen.*

* Bearbeiten Sie ein Bild und klicken Sie auf **[!UICONTROL Als Version speichern]**. Siehe [Bearbeiten von Bildern](/help/assets/edit-images-assets-view.md).

  ![Bearbeitetes Bild als Version speichern](assets/edit-image2.png)

  *Abbildung: Speichern Sie das bearbeitete Bild als Version.*

* Öffnen Sie die Versionen eines vorhandenen Assets. Klicken Sie auf **[!UICONTROL Neue Version]** und laden Sie eine neuere Version des Assets in das Repository hoch.

  ![Option zum Hochladen einer neuen Version eines Assets aus dem Versionsverlauf](assets/view-asset-versions2.png)

### Anzeigen und Vergleichen von Versionen eines Assets {#view-and-compare-versions}

Laden Sie ein Duplikat oder eine geänderte Kopie eines Assets hoch, um dessen Versionen zu erstellen. Mit der Versionierung können Sie die Änderungen an einem Asset im Laufe der Zeit verfolgen und bei Bedarf zu einer früheren Version zurückkehren.

Anzeigen und Vergleichen von Versionen:

1. Navigieren Sie zur Seite mit den Asset-Details.
1. Klicken Sie im rechten Bereich auf ![Versionen](/help/assets/assets/Clock.svg), um das Panel **[!UICONTROL Versionen]** anzuzeigen. In diesem Panel werden die Miniaturen des ursprünglichen Assets und seiner hochgeladenen Versionen angezeigt.
1. Wählen Sie eine Version im Panel aus, um sie im Vorschaubereich in der Vorschau anzuzeigen.
1. Wählen Sie eine andere Version als die neueste aus und klicken Sie auf **[!UICONTROL Als Neuestes festlegen]**, um sie als neueste Version festzulegen.
1. Ziehen Sie den Regler in der Vorschau nach links und rechts, um die ausgewählte Version eines Bildes und dessen neueste Version in einer einzigen Vorschau zu sehen. Auf diese Weise können Sie die ausgewählte Version des Bildes schnell mit der neuesten Version vergleichen.

   >[!NOTE]
   >
   > Der Versionsvergleich ist nur für Bild-Assets aktiviert.

   ![Vergleichen von Asset-Versionen](/help/assets/assets/version-compare2.png)

<!-- old content
To view versions, open an asset's preview and click **[!UICONTROL Versions]** ![Versions icon](assets/do-not-localize/versions-clock-icon.png) from the right sidebar. To preview a specific version, select it. To revert to it, click **[!UICONTROL Make Latest]**. 
-->

Wählen Sie die neueste Version aus und klicken Sie auf **[!UICONTROL Neue Version]**, um eine neue Kopie des Assets aus Ihrem lokalen Dateisystem hochzuladen und eine Asset-Version zu erstellen.

<!-- old content
You can also create versions from the versions timeline. Select the latest version, click **[!UICONTROL New Version]**, and upload a new copy of the asset from your local file system.

![View versions of an asset](assets/view-asset-versions1.png)

*Figure: View versions of an asset, revert to a previous version, or upload another new version.* 
-->

## Verwalten des Asset-Status {#manage-asset-status}

**Erforderliche Berechtigungen:**  `Can Edit`, `Owner` oder Administratorrechte für ein Asset.

In der Assets-Ansicht können Sie den Status der im Repository verfügbaren Assets festlegen. Legen Sie einen Asset-Status fest, um die nachgelagerte Nutzung digitaler Assets besser steuern und verwalten zu können.

Sie können die folgenden Status für Assets festlegen:

* Genehmigt

* Abgelehnt

* Kein Status

### Festlegen eines Asset-Status {#set-asset-status}

Um einen Asstet-Status festzulegen:

1. Wählen Sie das Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Details]**.

1. Wählen Sie in der Registerkarte **[!UICONTROL Allgemein]** den Asset-Status aus der Dropdown-Liste **[!UICONTROL Status]** aus. Zu den zulässigen Werten gehören „Genehmigt“, „Abgelehnt“ und „Kein Status“ (Standard).
Wenn Sie Dynamic Media mit OpenAPI-Funktionen für Ihre Umgebung bereitgestellt haben, generiert Experience Manager Assets eine öffentliche URL, sobald Sie das Asset als `Approved` markieren.

   >[!VIDEO](https://video.tv.adobe.com/v/342495)



### Festlegen des Genehmigungsziels {#set-approval-target}

Mit der Assets-Ansicht können Sie genehmigte Assets in Dynamic Media veröffentlichen, wobei OpenAPI-Funktionen, Content Hub oder beides auf dem Wert basieren, den Sie im Feld **Genehmigungsziel** auf der Seite „Asset-Details“ festgelegt haben.

So legen Sie das Genehmigungsziel fest:

1. Wählen Sie das Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Details]**.

1. Wählen Sie in der Registerkarte **[!UICONTROL Allgemein]** den Asset-Status aus der Dropdown-Liste **[!UICONTROL Status]** aus. Zu den zulässigen Werten gehören „Genehmigt“, „Abgelehnt“ und „Kein Status“ (Standard).

1. Wenn Sie in Schritt 2 **Genehmigt** auswählen, wählen Sie ein Genehmigungsziel aus. Zu den möglichen Werten gehören „Bereitstellung“ und „Content Hub“.

   * **Bereitstellung** ist die im Dropdown-Menü ausgewählte Standardoption. Das Asset wird sowohl in [Dynamic Media mit OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) als auch in [Content Hub](/help/assets/product-overview.md) veröffentlicht, sofern beide für Experience Manager Assets aktiviert sind.

   * Bei Auswahl von **Content Hub** wird das Asset nur in Content Hub veröffentlicht. Content Hub wird nur dann als Option angezeigt, wenn es für Experience Manager Assets aktiviert ist.

   * Wenn Sie keine Option aus der Dropdown-Liste auswählen, wird automatisch die für Ihre AEM as a Cloud Service-Umgebung aktivierte Standardoption auf das Asset angewendet.


   Weitere Informationen zu den verfügbaren Optionen finden Sie unter [Standardmäßige Genehmigungsziele und Veröffentlichungsziele für genehmigte Assets](#default-approval-target-options-publish-destinations).

   ![Genehmigungsstatus](/help/assets/assets/approval-status-delivery.png)

1. Geben Sie andere Asset-Eigenschaften an und klicken Sie auf **[!UICONTROL Speichern]**.

Weitere zu beachtende Punkte sind:

* Wenn Sie nicht das Standard-Metadatenformular verwenden und das Feld **[!UICONTROL Genehmigungsziel]** nicht sehen können, [bearbeiten Sie Ihr Metadatenformular](/help/assets/metadata-assets-view.md#metadata-forms), indem Sie das Feld **[!UICONTROL Genehmigung für]** aus den verfügbaren Komponenten in Ihr Metadatenformular ziehen, und klicken Sie auf **[!UICONTROL Speichern]**.

* Wenn Sie das Genehmigungsziel mithilfe der Assets-Ansicht als `Content Hub` auswählen, werden die Assets in Content Hub für die Benutzenden bereitgestellt, die derselben Organisation angehören.

#### Standardmäßige Genehmigungsziele und Veröffentlichungsziele für genehmigte Assets {#default-approval-target-options-publish-destinations}

Die folgende Tabelle zeigt die Voraussetzungen für die Anzeige der Dropdown-Liste `Approval Target` und des standardmäßigen Validierungsziels, basierend auf der Aktivierung von DM mit OpenAPI und Content Hub in Ihrer AEM as a Cloud Service-Umgebung:

| Dynamic Media mit OpenAPI | Content Hub | Wird die Dropdown-Liste „Genehmigungsziel“ angezeigt? | Standardmäßiges Genehmigungsziel für genehmigte Assets | Veröffentlichungsziel |
| --- | --- | --- | --- |---|
| Aktiviert | Aktiviert | Ja | Bereitstellung | Dynamic Media mit OpenAPI und Content Hub |
| Nicht aktiviert | Aktiviert | Ja | Content Hub | Content Hub |
| Aktiviert | Nicht aktiviert | Ja | Bereitstellung | Dynamic Media mit OpenAPI |
| Nicht aktiviert | Nicht aktiviert | Nein | Nicht zutreffend | Nicht zutreffend |

### Festlegen des Ablaufdatums eines Assets {#set-asset-expiration-date}

In der Assets-Ansicht können Sie auch das Ablaufdatum für die im Repository verfügbaren Assets festlegen. Sie können dann die [Suchergebnisse filtern](search-assets-view.md#refine-search-results), auf der Grundlage des Asset-Status `Expired`. Darüber hinaus können Sie einen Zeitraum für das Ablaufdatum für Assets angeben, um Ihre Suchergebnisse weiter zu filtern.

So legen Sie das Ablaufdatum eines Assets fest:

1. Wählen Sie das Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Details]**.

1. Legen Sie auf der Registerkarte **[!UICONTROL Standard]** im Feld **[!UICONTROL Ablaufdatum]** das Ablaufdatum für das Asset fest.

Das Kennzeichen `Expired` der Asset-Karte hat Vorrang vor dem Kennzeichen `Approved` oder `Rejected`, das für ein Asset festgelegt wurde.

Sie können Assets auch nach einem Asset-Status filtern. Weitere Informationen finden Sie unter [Suchen nach Assets in der Assets-Ansicht](search-assets-view.md).

## Anpassen von Metadatenformularen zur Aufnahme eines Asset-Statusfeldes {#customize-asset-status-metadata-form}

**Erforderliche Berechtigungen:** Administrator

Die Assets-Ansicht bietet standardmäßig viele Standard-Metadatenfelder. Unternehmen haben zusätzliche Metadatenanforderungen und benötigen mehr Metadatenfelder, um geschäftsspezifische Metadaten hinzuzufügen. Mit Metadatenformularen können Unternehmen benutzerdefinierte Metadatenfelder zur Seite [!UICONTROL Details] eines Assets hinzufügen. Die geschäftsspezifischen Metadaten verbessern die Verwaltung und Erkennung der Assets.

Weitere Informationen zum Hinzufügen zusätzlicher Metadatenfelder zum Metadatenformular finden Sie unter [Metadaten-Formulare](metadata-assets-view.md#metadata-forms).

**Hinzufügen des Metadatenfelds „Asset-Status“ zum Formular**

Um das Metadatenfeld „Asset-Status“ zum Formular hinzuzufügen, ziehen Sie die Komponente **[!UICONTROL Asset-Status]** von der linken Leiste in das Formular. Die Zuordnungseigenschaft wird automatisch vorausgefüllt. Speichern Sie das Formular, um die Änderungen zu bestätigen.

**Hinzufügen des Metadatenfelds „Ablaufdatum“ zum Formular**

Um das Metadatenfeld „Ablaufdatum“ zum Formular hinzuzufügen, ziehen Sie die Komponente **[!UICONTROL Datum]** aus der linken Leiste in das Formular. Geben Sie **Ablaufdatum** als Bezeichnung und `pur:expirationDate` als Zuordnungseigenschaft an. Speichern Sie das Formular, um die Änderungen zu bestätigen.

## Nächste Schritte {#next-steps}

* [Sehen Sie sich ein Video zum Verwalten von Assets in der Assets-Ansicht an](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets-essentials/basics/managing)

* Geben Sie Produkt-Feedback über die Option [!UICONTROL Feedback] in der Benutzeroberfläche der Assets-Ansicht

* Geben Sie Feedback zur Dokumentation durch ![Bearbeiten der Seite](assets/do-not-localize/edit-page.png) über die Option [!UICONTROL Diese Seite bearbeiten] oder durch ![Erstellen eines GitHub-Themas](assets/do-not-localize/github-issue.png) über die Option [!UICONTROL Problem protokollieren] in der rechten Seitenleiste

* Kontaktieren Sie die [Kundenunterstützung](https://experienceleague.adobe.com/de?support-solution=General#support)

