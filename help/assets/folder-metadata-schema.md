---
title: Ordner-Metadatenschema
description: Erfahren Sie, wie Sie ein Metadatenschema für Asset-Ordner in  [!DNL Experience Manager Assets] erstellen.
contentOwner: AG
feature: 'Metadaten  '
role: Geschäftspraktiker, Administrator
translation-type: tm+mt
source-git-commit: 8093f6cec446223af58515fd8c91afa5940f9402
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 100%

---


# Ordner-Metadatenschema {#folder-metadata-schema}

Mit [!DNL Adobe Experience Manager Assets] können Sie Metadatenschemata für Asset-Ordner erstellen, die die auf Seiten mit Ordnereigenschaften angezeigten Layouts und Metadaten definieren.

## Hinzufügen von Ordner-Metadatenschema-Formularen  {#add-a-folder-metadata-schema-form}

Verwenden Sie den Editor für Metadatenschema-Formulare, um Metadatenschemata für Ordner zu erstellen und zu bearbeiten.

1. Tippen/klicken Sie auf das [!DNL Experience Manager]-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Ordner-Metadatenschemata]**.
1. Tippen/klicken Sie auf der Seite „Ordner-Metadatenschema-Formulare“ auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Namen für das Formular an und tippen/klicken Sie auf **[!UICONTROL Erstellen]**. Das neue Schemaformular wird auf der Seite „Schemaformulare“ aufgeführt.

## Bearbeiten von Ordner-Metadatenschema-Formularen   {#edit-folder-metadata-schema-forms}

Sie können neu erstellte oder bestehende Metadatenschema-Formulare bearbeiten. Hierzu zählen folgende Elemente:

* Registerkarten
* Formularelemente innerhalb von Registerkarten

Sie können diese Formularelemente einem Feld innerhalb eines Metdatenknotens im CRX-Repository zuordnen bzw. dafür konfigurieren. Sie können dem Metadatenschema-Formular neue Registerkarten oder Formularelemente hinzufügen.

1. Wählen Sie auf der Seite „Schemaformulare“ das erstellte Formular aus und tippen/klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Bearbeiten]**.
1. Tippen/klicken Sie auf der Seite „Ordner-Metadatenschema-Editor“ auf das Symbol **[!UICONTROL +]**, um eine Registerkarte zum Formular hinzuzufügen. Um die Registerkarte umzubenennen, tippen/klicken Sie auf den Standardnamen und geben Sie unter **[!UICONTROL Einstellungen]** den neuen Namen an.

   ![custom_tab](assets/custom_tab.png)

   Um weitere Registerkarten hinzuzufügen, tippen/klicken Sie erneut auf das Symbol **[!UICONTROL +]**. Tippen/klicken Sie auf **[!UICONTROL X]**, um eine Registerkarte zu löschen.

1. Fügen Sie in der aktiven Registerkarte eine oder mehrere Komponenten von der Registerkarte **[!UICONTROL Formular erstellen]** hinzu.

   ![adding_components](assets/adding_components.png)

   Wenn Sie mehrere Registerkarten erstellen, tippen/klicken Sie auf eine Registerkarte, um Komponenten hinzuzufügen.

1. Um eine Komponente zu konfigurieren, wählen Sie diese aus und ändern Sie ihre Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**.

   Löschen Sie ggf. eine Komponente über die Registerkarte **[!UICONTROL Einstellungen]**.

   ![configure_properties](assets/configure_properties.png)

1. Tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

### Komponenten zum Erstellen von Formularen   {#components-to-build-forms}

Die Registerkarte **[!UICONTROL Formular erstellen]** enthält Formularelemente, die Sie im Ordner-Metadatenschema-Formular verwenden. Die Registerkarte **[!UICONTROL Einstellungen]** enthält die Attribute für jedes Element, das Sie auf der Registerkarte **[!UICONTROL Formular erstellen]** auswählen. Im Folgenden finden Sie eine Liste der auf der Registerkarte **[!UICONTROL Formular erstellen]** verfügbaren Elemente:

<table>
 <tbody>
  <tr>
   <td><p><strong>Komponentenname</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>Bereichs-Kopfzeile</p> </td>
   <td><p> Fügen Sie eine Abschnittsüberschrift für eine Liste allgemeiner Komponenten hinzu.</p> </td>
  </tr>
  <tr>
   <td><p>Einzelzeilentext</p> </td>
   <td><p> Fügen Sie eine einzeilige Texteigenschaft hinzu. Diese wird als Zeichenfolge gespeichert.</p> </td>
  </tr>
  <tr>
   <td><p>Mehrwerttext</p> </td>
   <td><p> Fügen Sie eine Texteigenschaft mit mehreren Werten hinzu. Diese wird als Zeichenfolgen-Array gespeichert.</p> </td>
  </tr>
  <tr>
   <td><p>Zahl</p> </td>
   <td><p> Fügen Sie eine Zahlenkomponente hinzu.</p> </td>
  </tr>
  <tr>
   <td><p>Datum</p> </td>
   <td><p> Fügen Sie eine Datumskomponente hinzu.</p> </td>
  </tr>
  <tr>
   <td><p>Dropdown</p> </td>
   <td><p> Fügen Sie eine Dropdown-Liste hinzu.</p> </td>
  </tr>
  <tr>
   <td><p>Standard-Tags</p> </td>
   <td><p> Fügen Sie ein Tag hinzu. </p> </td>
  </tr>
  <tr>
   <td><p>Ausgeblendetes Feld</p> </td>
   <td><p> Fügen Sie ein ausgeblendetes Feld hinzu. Dieses wird beim Speichern des Assets als POST-Parameter gesendet.</p> </td>
  </tr>
 </tbody>
</table>

### Bearbeiten von Formularelementen   {#editing-form-items}

Um die Eigenschaften von Formularelementen zu bearbeiten, tippen/klicken Sie auf die Komponente und bearbeiten Sie folgende Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**.

**[!UICONTROL Feldbezeichnung]**: Der Name der Metadateneigenschaft, der auf der Eigenschaftenseite des Assets angezeigt wird.

**[!UICONTROL Zu Eigenschaft zuordnen]**: Diese Eigenschaft gibt den relativen Pfad des Ordnerknotens im CRX-Repository an, wo das Element gespeichert ist. Sie beginnt mit „**./**“. Dies zeigt an, dass sich der Pfad unter dem Knoten des Ordners befindet.

Im Folgenden finden Sie die gültigen Werte für diese Eigenschaft:

* `./jcr:content/metadata/dc:title`: Speichert den Wert im Metadatenknoten des Ordners als Eigenschaft `dc:title`.

* `./jcr:created`: Speichert das Erstellungsdatum und die Erstellungsuhrzeit eines Assets. Dies ist eine geschützte Eigenschaft. Wenn Sie diese Eigenschaften konfigurieren, empfiehlt Adobe, dass Sie sie mit [!UICONTROL Bearbeitung deaktivieren] markieren.

Um zu gewährleisten, dass die Komponente ordnungsgemäß im Metadatenschema-Formular angezeigt wird, fügen Sie dem Eigenschaftenpfad keine Leerzeichen hinzu.

**[!UICONTROL JSON-Pfad]**: Verwenden Sie diese Eigenschaft, um den Pfad der JSON-Datei anzugeben, in der Sie Schlüssel-Wert-Paare für Optionen speichern.

**[!UICONTROL Platzhalter]**: Geben Sie mit dieser Eigenschaft relevanten Platzhaltertext zur Metadateneigenschaft an.

**[!UICONTROL Wahlen]**: Mit dieser Eigenschaft legen Sie Optionen in einer Liste fest.

**[!UICONTROL Beschreibung]**: Mit dieser Eigenschaft können Sie eine kurze Beschreibung für die Metadatenkomponente hinzufügen.

**[!UICONTROL Klasse]**: Objektklasse, der die Eigenschaft zugeordnet ist.

## Löschen von Ordner-Metadatenschema-Formularen   {#delete-folder-metadata-schema-forms}

Sie können Ordner-Metadatenschema-Formulare über die Seite „Ordner-Metadatenschema-Formulare“ löschen. Um ein Formular zu löschen, wählen Sie es aus und tippen/klicken Sie in der Symbolleiste auf das Löschsymbol.

![delete_form](assets/delete_form.png)

## Zuordnen eines Ordner-Metadatenschemas {#assign-a-folder-metadata-schema}

Sie können ein Ordner-Metadatenschema über die Seite „Ordner-Metadatenschema-Formulare“ oder bei der Ordnererstellung einem Ordner zuordnen.

Wenn Sie ein Metadatenschema für einen Ordner konfigurieren, wird der Pfad in der Eigenschaft `folderMetadataSchema` des Ordnerknotens unter */jcr:content* gespeichert.

### Zuweisen eines Schemas über die Seite „Ordner-Metadatenschema“   {#assign-to-a-schema-from-the-folder-metadata-schema-page}

1. Tippen/klicken Sie auf das [!DNL Experience Manager]-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Ordner-Metadatenschemata]**.
1. Wählen Sie auf der Seite „Ordner-Metadatenschema-Formulare“ das Schemaformular aus, das Sie auf einen Ordner anwenden möchten.
1. Tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL Auf Ordner anwenden]**.

1. Wählen Sie den Ordner aus, auf den Sie das Schema anwenden möchten, und klicken/tippen Sie auf **[!UICONTROL Anwenden]**. Wenn bereits ein Metadatenschema auf den Ordner angewendet wurde, wird eine Warnung dazu angezeigt, dass das bestehende Schema überschrieben wird. Tippen/klicken Sie auf **[!UICONTROL Überschreiben]**.
1. Öffnen Sie die Metadateneigenschaften für den Ordner, auf den Sie das Schema angewendet haben.

   ![Ordnereigenschaften](assets/folder_properties.png)

   Um die Felder der Ordnermetadaten anzuzeigen, tippen/klicken Sie auf die Registerkarte **[!UICONTROL Ordnermetadaten]**.

   ![folder_metadata_properties](assets/folder_metadata_properties.png)

### Zuweisen eines Schemas bei der Ordnererstellung {#assign-a-schema-when-creating-a-folder}

Sie können Ordner-Metadatenschemata auch beim Erstellen eines Ordners zuweisen. Wenn bereits mindestens ein Ordner-Metadatenschema im System vorhanden ist, wird eine zusätzliche Liste im Dialogfeld **[!UICONTROL Ordner erstellen]** angezeigt. Sie können das gewünschte Schema auswählen. Standardmäßig ist kein Schema ausgewählt.

1. Tippen/klicken Sie in der Symbolleiste der [!DNL Experience Manager Assets]-Benutzeroberfläche auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Titel und einen Namen für den Ordner an.
1. Wählen Sie in der Liste „Ordner-Metadatenschema“ das gewünschte Schema aus. Tippen/klicken Sie anschließend auf **[!UICONTROL Erstellen]**.

   ![select_schema](assets/select_schema.png)

1. Öffnen Sie die Metadateneigenschaften für den Ordner, auf den Sie das Schema angewendet haben.
1. Um die Felder der Ordnermetadaten anzuzeigen, tippen/klicken Sie auf die Registerkarte **[!UICONTROL Ordnermetadaten]**.

## Verwenden des Ordner-Metadatenschemas {#use-the-folder-metadata-schema}

Öffnen Sie die Eigenschaften für einen Ordner, der mit einem Ordner-Metadatenschema konfiguriert wurde. Hierdurch wird die Registerkarte **[!UICONTROL Ordnermetadaten]** auf der Seite mit den Ordnereigenschaften angezeigt. Um das Ordner-Metadatenschema-Formular anzuzeigen, wählen Sie diese Registerkarte aus.

Geben Sie Metadatenwerte in die verschiedenen Felder ein und tippen/klicken Sie auf **[!UICONTROL Speichern]**, um die Werte zu speichern. Die angegebenen Werte werden im Ordnerknoten im CRX-Repository gespeichert.

![folder_metadata_properties-1](assets/folder_metadata_properties-1.png)
