---
title: Verwalten digitaler Assets
description: Verschieben, Löschen, Kopieren, Umbenennen, Aktualisieren und Versionieren von Assets in  [!DNL Assets view].
role: User,Leader
contentOwner: AG
exl-id: 2459d482-828b-4410-810c-ac55ef0a2119
source-git-commit: f7d3e356e4e43d5838a6319f5ead750c149a9b3b
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 95%

---

# Verwalten von Assets {#manage-assets}

Mithilfe der benutzerfreundlichen Oberfläche von [!DNL Assets view] können Sie mühelos verschiedene Aufgaben des Digital Asset Management (DAM) ausführen. Nachdem Sie die Assets hinzugefügt haben, können Sie sie suchen, herunterladen, verschieben, kopieren, umbenennen, löschen, aktualisieren und bearbeiten.

Verwenden Sie [!DNL Assets view], um die folgenden Asset-Management-Aufgaben auszuführen. Wenn Sie ein Asset auswählen, werden die folgenden Optionen in der Symbolleiste oben angezeigt.

![Symbolleistenoptionen bei der Auswahl eines Assets](assets/toolbar-image-selected.png)

*Abbildung: In der Symbolleiste verfügbare Optionen für ein ausgewähltes Bild.*

* ![deselect icon](assets/do-not-localize/close-icon.png) Deaktivieren der Auswahl.
* ![details icon](assets/do-not-localize/edit-in-icon.png) Anklicken, um ein Asset in der Vorschau anzuzeigen und die detaillierten Metadaten anzuzeigen. Aus der Vorschau heraus können Sie die Versionen anzeigen und ein Bild bearbeiten.
* ![download icon](assets/do-not-localize/download-icon.png) Lädt das ausgewählte Asset in Ihr lokales Dateisystem herunter.
* ![delete icon](assets/do-not-localize/delete-icon.png) Löscht das ausgewählte Asset oder den ausgewählten Ordner.
* ![checkout icon](assets/do-not-localize/checkout-icon.png) Checkt das ausgewählte Asset aus.
* ![copy icon](assets/do-not-localize/copy-icon.png) Kopiert die ausgewählte Datei oder den ausgewählten Ordner.
* ![move icon](assets/do-not-localize/move-icon.png) Verschiebt das ausgewählte Asset oder den ausgewählten Ordner an einen anderen Speicherort in der Repository-Hierarchie.
* ![rename icon](assets/do-not-localize/rename-icon.png) Benennt das ausgewählte Asset oder den ausgewählten Ordner um. Verwenden Sie einen eindeutigen Namen, sonst schlägt die Umbenennung mit einer Warnung fehl. Sie können es mit einem neuen Namen erneut versuchen.
Außerdem können Sie auf den Titel eines Assets oder Ordners klicken, um es umzubenennen. Erwähnen Sie den neuen Text im **Asset umbenennen** Textfeld und klicken Sie auf **Speichern**. Diese Funktion ist in den Ansichten &quot;Raster&quot;, &quot;Galerie&quot;, &quot;Wasserfall&quot;und &quot;Liste&quot;verfügbar. <!--in-place rename-->
* ![assign task icon](assets/do-not-localize/review-delegate-icon.png) Weist anderen Benutzern Aufgaben zu, damit sie an einem Asset zusammenarbeiten können.

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

### Anzeigen von Versionen eines Assets {#view-versions}

Beim Hochladen eines Duplikats oder einer geänderten Kopie eines Assets können Sie dessen Versionen erstellen. Mit der Versionierung können Sie historische Assets überprüfen und bei Bedarf zu einer früheren Version zurückkehren.

Um Versionen anzuzeigen, öffnen Sie die Vorschau eines Assets und klicken Sie in der rechten Seitenleiste auf **[!UICONTROL Versionen]** ![Versions icon](assets/do-not-localize/versions-clock-icon.png). Um eine bestimmte Version in der Vorschau anzuzeigen, wählen Sie sie aus. Um zu ihr zurückzukehren, klicken Sie auf **[!UICONTROL Neueste erstellen]**.

Sie können Versionen auch aus der Versions-Zeitleiste erstellen. Wählen Sie die neueste Version aus, klicken Sie auf **[!UICONTROL Neue Version]** und laden Sie eine neue Kopie des Assets aus Ihrem lokalen Dateisystem hoch.

![Anzeigen von Versionen eines Assets](assets/view-asset-versions1.png)

*Abbildung: Zeigen Sie Versionen eines Assets an, kehren Sie zu einer früheren Version zurück oder laden Sie eine andere neue Version hoch.*

## Verwalten des Asset-Status {#manage-asset-status}

**Erforderliche Berechtigungen:**  `Can Edit`, `Owner` oder Administratorrechte für ein Asset.

In der Assets-Ansicht können Sie den Status der im Repository verfügbaren Assets festlegen. Legen Sie einen Asset-Status fest, um die nachgelagerte Nutzung digitaler Assets besser steuern und verwalten zu können.

Sie können die folgenden Status für Assets festlegen:

* Genehmigt

* Abgelehnt

* Kein Status

### Festlegen eines Asset-Status {#set-asset-status}

Festlegen eines Asset-Status

1. Wählen Sie das Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Details]**.

1. Wählen Sie in der Registerkarte **[!UICONTROL Allgemein]** den Asset-Status aus der Dropdown-Liste **[!UICONTROL Status]** aus. Zu den zulässigen Werten gehören „Genehmigt“, „Abgelehnt“ und „Kein Status“ (Standard).

   >[!VIDEO](https://video.tv.adobe.com/v/342495)


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

* [Sehen Sie sich ein Video zum Verwalten von Assets in der Assets-Ansicht an](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/basics/managing.html?lang=de)

* Geben Sie Produkt-Feedback über die Option [!UICONTROL Feedback] in der Benutzeroberfläche der Assets-Ansicht

* Geben Sie Feedback zur Dokumentation durch ![Bearbeiten der Seite](assets/do-not-localize/edit-page.png) über die Option [!UICONTROL Diese Seite bearbeiten] oder durch ![Erstellen eines GitHub-Themas](assets/do-not-localize/github-issue.png) über die Option [!UICONTROL Problem protokollieren] in der rechten Seitenleiste

* Kontaktieren Sie die [Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=General&amp;lang=de#support)

