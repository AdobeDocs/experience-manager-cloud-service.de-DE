---
title: Verwalten von Asset-Sammlungen
description: Lernen Sie das Konzept von Sammlungen in AEM Assets kennen. Erfahren Sie, wie Sie Sammlungen verwalten, bearbeiten und mit anderen Benutzern teilen können.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 7141e42f53c556c0ac21def6085182ef400f5a71

---


# Verwalten von Sammlungen {#manage-collections}

Eine Sammlung ist ein Satz von Assets innerhalb von AEM- (Adobe Experience Manager-) Assets. Anhand von Sammlungen können Assets von mehreren Benutzern gemeinsam verwendet werden.

* Eine Sammlung kann Assets aus verschiedenen Speicherorten enthalten.
* Sie können Sammlungen für mehrere Benutzer mit unterschiedlichen Berechtigungsstufen, wie Anzeigen, Bearbeiten usw., freigeben.

Sie können mehrere Sammlungen für einen Benutzer freigeben. Jede Sammlung enthält Referenzen zu Assets. Die referenzielle Integrität von Assets wird sammlungsübergreifend aufrechterhalten.

Sammlungen sind von den folgenden Typen, und zwar auf Grundlage, wie sie Assets sortieren:

* Eine Sammlung, die eine statische Referenzliste mit Assets, Ordnern und anderen Sammlungen enthält.

* Eine intelligente Sammlung, die basierend auf Suchkriterien dynamisch Elemente enthält.

## Navigate the collections console {#navigate-the-collections-console}

So öffnen Sie die Konsole **[!UICONTROL Sammlungen]**:

1. Tippen oder klicken Sie auf das AEM-Logo.
1. From the Navigation page, go to **[!UICONTROL Assets]** > **[!UICONTROL Collections]**. Die Konsole **[!UICONTROL Sammlungen]** wird angezeigt.

## Sammlung erstellen {#create-a-collection}

You can create a collection either with [static references](#create-a-collection-with-static-references) or based on a [search criteria-based filter](#create-a-smart-collection). Sie können eine Sammlung auch über eine Lightbox erstellen.

### Create a collection with static references {#create-a-collection-with-static-references}

Sie können eine Sammlung mit statischen Referenzen erstellen, wie eine Sammlung mit Referenzen zu Assets, Ordnern, Sammlungen, Rotationssets und Bildsets.

1. Navigieren Sie zur Konsole **[!UICONTROL Sammlungen]**.
1. From the toolbar, tap/click **[!UICONTROL Create]**.
1. Geben Sie auf der Seite **[!UICONTROL Sammlung erstellen]** einen Titel und eine optionale Beschreibung für die Sammlung ein.
1. Fügen Sie der Sammlung Mitglieder hinzu und weisen Sie die jeweiligen Berechtigungen zu. Wählen Sie alternativ **[!UICONTROL Öffentliche Sammlung]** aus, damit alle Benutzer auf die Sammlung zugreifen können.

   >[!NOTE]
   >
   >Um es Mitgliedern zu ermöglichen, Sammlungen mit anderen Benutzern zu teilen, gewähren Sie der Gruppe `dam-users` Leseberechtigungen für den Pfad `home/users`. Give permission to the users at `/content/dam/collections` location to allow the users to view the Collections in pop up lists. Alternativ dazu können Sie Benutzer auch in die Gruppe `dam-users` aufnehmen.

1. (Optional) Fügen Sie eine Miniaturansicht für die Sammlung hinzu.
1. Tap/click **[!UICONTROL Create]**, and then tap/click **[!UICONTROL OK]** to close the dialog. In der Konsole „Sammlungen“ wird eine Sammlung mit dem angegebenen Titel und den Eigenschaften geöffnet.

   >[!NOTE]
   >
   >Mit AEM Assets können Sie Prüfungsaufgaben für eine Sammlung auf ähnliche Weise wie Prüfungsaufgaben für einen Assets-Ordner erstellen.

   Um Assets zur Sammlung hinzuzufügen, navigieren Sie zur Assets-Benutzeroberfläche. For details, see [Add assets to a collection](#add-assets-to-a-collection).

### Erstellen von Sammlungen mithilfe der Dropzone {#create-collections-using-dropzone}

Sie können Assets aus der Assets-Benutzeroberfläche ziehen und in einer Sammlung ablegen. Sie können auch eine Kopie einer Sammlung erstellen und Assets dort hinziehen.

1. Wählen Sie in der Assets-Benutzeroberfläche die Assets aus, die Sie zu einer Sammlung hinzufügen möchten.
1. Drag the assets to the **[!UICONTROL Drop in Collection]** zone. Tippen oder klicken Sie alternativ in der Symbolleiste auf das Symbol **[!UICONTROL Zu Sammlung]**.
1. In the **[!UICONTROL Add To Collection]** page, tap/click the **[!UICONTROL Create Collection]** icon from the toolbar. Wenn Sie die Assets einer vorhandenen Sammlung hinzufügen möchten, wählen Sie diese auf der Seite aus und tippen oder klicken Sie auf **[!UICONTROL Hinzufügen]**. Standardmäßig ist die zuletzt aktualisierte Sammlung ausgewählt.
1. Geben Sie im Dialogfeld **[!UICONTROL Neue Sammlung erstellen]** einen Namen für die Sammlung an. Wenn die Sammlung für alle Benutzer verfügbar sein soll, wählen Sie **[!UICONTROL Öffentliche Sammlung]** aus.
1. Tap/click **[!UICONTROL Continue]** to create the collection.

### Erstellen einer intelligenten Sammlung {#create-a-smart-collection}

Eine Smart-Sammlung verwendet Suchkriterien, um Assets dynamisch zu füllen. Sie können eine Smart-Sammlung erstellen, indem Sie Dateien und Ordner oder nur Dateien nutzen.

1. Navigate to the Assets UI, and tap/click the **[!UICONTROL Search]** icon.
1. Geben Sie im OmniSearch-Feld den Suchbegriff ein und drücken Sie die Eingabetaste. Tippen/Klicken Sie auf das GlobalNav-Symbol, um das Bedienfeld „Filter“ anzuzeigen, und wenden Sie einen Suchfilter aus dem Suchbereich an.
1. Wählen Sie aus der Liste **[!UICONTROL Dateien und Ordner]** die Option **[!UICONTROL Dateien]** aus.
1. Tippen oder klicken Sie auf **[!UICONTROL Smart-Sammlung speichern]**.
1. Geben Sie einen Namen für die Sammlung an. Aktivieren Sie **[!UICONTROL Öffentlich]**, um die DAM-Benutzergruppe mit der Rolle „Betrachter“ zur Smart-Sammlung hinzuzufügen.

   >[!NOTE]
   >
   >If you select **[!UICONTROL Public]**, the smart collection becomes available to everyone with the Owner role after you create it. Wenn Sie die Option **[!UICONTROL Öffentlich]** deaktivieren, ist die DAM-Benutzergruppe nicht mehr mit der Smart-Sammlung verknüpft.

1. Tap/click **[!UICONTROL Save]** to create the smart collection, and then close the message box to complete the process. The new smart collection is also added to the **[!UICONTROL Saved Searches]** list.
The label of the **[!UICONTROL Create Smart Selection]** button changes to **[!UICONTROL Edit Smart Selection]**. To edit the settings of the smart collection, select **[!UICONTROL Files]** from the **[!UICONTROL Files &amp; Folders]** list. Then, tap/click the **[!UICONTROL Edit Smart Selection]** button.

## Add assets to a collection {#add-assets-to-a-collection}

Sie können einer Sammlung mit einer Liste referenzierter Assets oder Ordner Assets hinzufügen.

>[!NOTE]
>
>Smart-Sammlungen füllen Assets anhand einer Suchabfrage. Daher sind statische Referenzen zu Assets und Ordnern für sie nicht anwendbar.

1. Navigieren Sie in Assets-Benutzeroberfläche zum Speicherort des Assets, das Sie zu einer Sammlung hinzufügen möchten.
1. Wählen Sie das Asset aus und tippen oder klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Zu Sammlung.]** Alternatively, you can drag the asset to the **[!UICONTROL Drop in Collection]** zone. Release the mouse button when the drop zone becomes active and its label changes to **[!UICONTROL Drop to Add]**.
1. In the **[!UICONTROL Add To Collection]** page, select the collection to which you want to add the asset.
1. Tippen oder klicken Sie auf **[!UICONTROL Hinzufügen]** und schließen Sie die Bestätigungsnachricht. Das Asset wird zur Sammlung hinzugefügt.

## Bearbeiten einer intelligenten Sammlung {#edit-a-smart-collection}

Smart collections are built by saving a search so you can alter their content by modifying the search parameters of the [saved search](#saved-searches).

1. In the Assets user interface, tap/click the **[!UICONTROL Search]** icon from the toolbar.
1. Drücken Sie mit dem Cursor in das Feld Omniture Search die Eingabetaste.
1. Tippen oder klicken Sie auf das GlobalNav-Symbol, um den Filterbereich anzuzeigen.
1. Wählen Sie in der Liste **[!UICONTROL Gespeicherte Suchen]** die Smart-Sammlung aus, die Sie ändern möchten. Im Suchbereich werden die für die gespeicherte Suche konfigurierten Filter angezeigt.
1. Wählen Sie aus der Liste **[!UICONTROL Dateien und Ordner]** die Option **[!UICONTROL Dateien]** aus.
1. Ändern Sie den bzw. die Filter nach Bedarf. Tap/click **[!UICONTROL Edit Smart Collection]**. Sie können auch den Namen der Smart-Sammlung ändern.
1. Tippen oder klicken Sie auf **[!UICONTROL Speichern]**. Das Dialogfeld **[!UICONTROL Smart-Sammlung bearbeiten]** wird angezeigt.
1. Tippen oder klicken Sie auf **[!UICONTROL Überschreiben]**, um die ursprüngliche Smart-Sammlung durch die bearbeitete Sammlung zu ersetzen. Wählen Sie alternativ **[!UICONTROL Speichern unter]** aus, um die bearbeitete Sammlung separat zu speichern.
1. Tippen oder klicken Sie im Bestätigungsdialogfeld auf **[!UICONTROL Speichern]**, um den Vorgang abzuschließen.

## View and edit collection metadata {#view-and-edit-collection-metadata}

Sammlungsmetadaten umfassen die Daten zur Sammlung, einschließlich aller hinzugefügten Tags.

1. From the Collections console, select a collection and tap/click the **[!UICONTROL Properties]** icon from the toolbar.
1. In the **[!UICONTROL Collection Metadata]** page, view the collection metadata from the **[!UICONTROL Basic]** and **Advanced** tabs.
1. Modify the metadata, as necessary, and then tap/click **[!UICONTROL Save &amp; Close]** from the toolbar to save the changes.

### Edit collection metadata in bulk {#edit-collection-metadata-in-bulk}

Sie können die Metadaten von mehreren Sammlungen gleichzeitig bearbeiten. Mit dieser Funktion können Sie schnell allgemeine Metadaten in mehreren Sammlungen replizieren.

1. Wählen Sie in der Konsole „Sammlungen“ zwei oder mehr Sammlungen aus, für die Sie Metadaten bearbeiten möchten.
1. From the toolbar, tap/click the **[!UICONTROL Properties]** icon.
1. In the **[!UICONTROL Collection Metadata]** page, edit the metadata under the **[!UICONTROL Basic]** and **[!UICONTROL Advanced]** tabs, as necessary.
1. Tap/click **[!UICONTROL Save &amp; Close]** from the toolbar, and then close the confirmation dialog to complete the process.
1. Um die neuen Metadaten an die vorhandenen Metadaten anzuhängen, wählen Sie **[!UICONTROL Anlagenmodus]** aus. Wenn Sie diese Option nicht auswählen, ersetzen die neuen Metadaten die vorhandenen Metadaten in den Feldern. Tap/click **[!UICONTROL Submit]**.

   >[!NOTE]
   >
   >Der Anlagenmodus funktioniert nur für Felder, die mehrere Werte enthalten können. Für Felder, die nur einen einzigen Wert enthalten können, werden neue Metadaten nicht an den vorhandenen Wert im Feld angehängt, selbst wenn Sie den **[!UICONTROL Anhängen-Modus]** auswählen.

## Suche{#searching}

The Search feature within Collections supports both [Search for collections](#search-collections) and [Search for assets within a Collection](#search-within-collections).

### Sammlungen durchsuchen {#search-collections}

Sie können mit der Konsole „Sammlungen“ nach Sammlungen suchen. Wenn Sie die Suche mit Schlüsselwörtern im Suchfeld durchführen, sucht AEM Assets nach Sammlungsnamen, Sammlungsmetadaten und den Tags, die zu den Sammlungen hinzugefügt wurden.

Wenn Sie auf der obersten Ebene nach Sammlungen suchen, werden nur die einzelnen Sammlungen in den Suchergebnissen zurückgegeben. Assets oder Ordner in den Sammlungen werden ausgeschlossen. In allen anderen Fällen (z. B. innerhalb einer individuellen Sammlung oder in einer Ordnerhierarchie) werden alle relevanten Assets, Ordner und Sammlungen zurückgegeben.

### In Sammlungen suchen {#search-within-collections}

Tippen/klicken Sie in der Sammlungskonsole auf eine Sammlung, um sie zu öffnen.

Innerhalb einer Sammlung ist die Suche von AEM Assets auf Assets (sowie deren Tags und Metadaten) in der angezeigten Sammlung begrenzt. Wenn Sie in einem Ordner suchen, werden alle passenden Assets und untergeordneten Ordner innerhalb des aktuellen Ordners zurückgegeben. Wenn Sie in einer Sammlung suchen, werden nur übereinstimmende Assets, Ordner und andere Sammlungen zurückgegeben, die direkt zur Sammlung gehören.

## Sammlungseinstellungen bearbeiten {#edit-collection-settings}

Sie können Sammlungseinstellungen, wie z. B. Titel und Beschreibung, bearbeiten oder Mitglieder zu einer Sammlung hinzufügen.

1. Select a collection, and tap/click the **[!UICONTROL Settings]** icon in the toolbar. Verwenden Sie alternativ die Schnellaktion **[!UICONTROL Einstellungen]** über die Miniaturansicht der Sammlung.
1. Modify the collection settings in the **[!UICONTROL Collection Settings]** page. For example, modify the collection title, descriptions, members, and permissions as discussed in [Add collections](#create-a-collection).
1. Tap/click **[!UICONTROL Save]** to save the changes.

## Eine Sammlung löschen {#delete-a-collection}

1. Wählen Sie in der Sammlungskonsole eine oder mehrere Sammlungen aus und tippen/klicken Sie auf das Löschsymbol in der Symbolleiste.
1. In the dialog, tap/click **[!UICONTROL Delete]** to confirm the delete action.

   >[!NOTE]
   >
   >You can also delete Smart collections by [delete saved searches](#saved-searches).

## Sammlung herunterladen {#download-a-collection}

Wenn Sie eine Sammlung herunterladen, wird die gesamte Hierarchie der Assets in der Sammlung heruntergeladen, einschließlich der Ordner und untergeordneten Sammlungen.

1. Wählen Sie in der Konsole „Sammlungen“ eine oder mehrere Sammlungen für den Download aus.
1. Tippen bzw. klicken Sie in der Symbolleiste auf das Symbol Herunterladen.
1. Tippen oder klicken Sie im Dialogfeld **[!UICONTROL Herunterladen]** auf **[!UICONTROL Herunterladen]**. Wählen Sie **[!UICONTROL Ausgabeformate]** aus, wenn Sie die Ausgabeformate des Assets in der Sammlung herunterladen möchten. Wählen Sie die Option **[!UICONTROL E-Mail]** aus, um eine E-Mail-Benachrichtigung an den Eigentümer der Sammlung zu senden.

   Bei Auswahl einer Sammlung für den Download wird die gesamte Ordnerstruktur unter dieser Sammlung heruntergeladen. To include each collection you download (including assets in child collections nested under the parent collection) in an individual folder, select **[!UICONTROL Create separate folder for each asset]**.

## Edit metadata properties of multiple collections {#editing-metadata-properties-of-multiple-collections}

Mit Adobe Enterprise Manager (AEM)-Assets können Sie die Metadaten vieler Sammlungen stapelweise bearbeiten. Auf der Seite &quot; [!UICONTROL Eigenschaften] &quot;können Sie Metadatenänderungen an mehreren Sammlungen durchführen, beispielsweise Metadateneigenschaften zu einem allgemeinen Wert ändern oder Tags hinzufügen oder ändern.

To customize the metadata [!UICONTROL Properties] page, including adding, modifying, deleting metadata properties, use the Schema editor.

>[!NOTE]
>
>Die Massenbearbeitungsmethoden arbeiten für Assets, die in einer Sammlung verfügbar sind. Für Assets, die in verschiedenen Ordnern enthalten sind oder gemeinsamen Kriterien entsprechen, können die [Metadaten nach einer Suche stapelweise aktualisiert werden](/help/assets/search-assets.md#metadataupdates).

1. Wählen Sie in der Sammlungskonsole die zu bearbeitenden Sammlungen aus.
1. From the toolbar, tap/click **[!UICONTROL Properties]** to open the [!UICONTROL Properties] page for the selected collections.
1. Ändern Sie die Metadateneigenschaften für ausgewählte Sammlungen auf den verschiedenen Registerkarten.

   >[!NOTE]
   >
   >Die Metadaten, die Sie für die ausgewählten Sammlungen hinzufügen, überschreiben die vorherigen Metadaten für diese Sammlungen, außer für Tags. Any tags you add in the **[!UICONTROL Tags]** field, are appended to the existing list of tags in the metadata.

1. Heben Sie die Auswahl der anderen Sammlungen in der Sammlungsliste auf, um die Metadateneigenschaften für eine bestimmte Sammlung anzuzeigen. Die Metadateneditorfelder werden mit den Metadaten für die bestimmte Sammlung gefüllt.

   >[!NOTE]
   >
   >* Auf der Sammlungseigenschaftenseite können Sie Sammlungen aus der Liste der Sammlungen entfernen, indem Sie die Auswahl aufheben. In der Sammlungsliste sind alle Sammlungen standardmäßig ausgewählt. Die Metadaten für Sammlungen, die Sie entfernen, werden nicht aktualisiert.
   >* At the top of the list, select the check box near **[!UICONTROL Title]** to toggle between selecting the collections and clearing the list.


1. Speichern Sie die Änderungen.

## Erstellen verschachtelter Sammlungen {#create-nested-collections}

Sie können eine Sammlung zu einer anderen Sammlung hinzufügen und so eine verschachtelte Sammlung erstellen.

1. From the Collections console, select the desired collection or group of collections, and tap or click the **[!UICONTROL To Collection]** icon in the toolbar.
1. Wählen Sie auf der Seite **[!UICONTROL Zu Sammlung hinzufügen]** die Sammlung aus, zu der die Sammlung hinzugefügt werden soll.

   >[!NOTE]
   >
   >The most recently updated collection is selected by default in the **[!UICONTROL Add To Collection]** page.

1. Tippen oder klicken Sie auf **[!UICONTROL Hinzufügen]**. Eine Meldung bestätigt, dass die Sammlung zur Zielsammlung auf der Seite **[!UICONTROL Ziel auswählen]** hinzugefügt wird. Schließen Sie die Meldung, um den Vorgang abzuschließen.

>[!NOTE]
>
>Smart-Sammlungen können nicht verschachtelt werden. Das heißt, Smart-Sammlungen können keine anderen Sammlungen enthalten.

## Gespeicherte Suchvorgänge {#saved-searches}

In der Benutzeroberfläche &quot;Assets&quot;können Sie Assets nach bestimmten Regeln, Suchkriterien oder benutzerdefinierten Suchfacetten suchen oder filtern. If you save these as **[!UICONTROL Saved Searches]**, you can access them later from the **[!UICONTROL Saved Searches]** list in the Filter panel. Beim Erstellen einer gespeicherten Suche wird auch eine Smart-Sammlung erstellt.

Gespeicherte Suchen werden erstellt, wenn Sie eine intelligente Sammlung erstellen. Intelligente Sammlungen werden automatisch der Liste **[!UICONTROL Gespeicherte Suchen]** hinzugefügt. The Saved Searches query for the collection is saved in the `dam:query` property in CRX at the relative location `/content/dam/collections/`.

>[!NOTE]
>
>Sie können Smart-Sammlungen auf gleiche Weise wie statische Sammlungen freigeben.

Gespeicherte Suchen werden genauso wie Smart-Sammlungen bearbeitet. For details, see [Edit a smart collection](#edit-a-smart-collection).

Gehen Sie wie folgt vor, um gespeicherte Suchen zu löschen:

1. Navigate to the Assets user interface, and tap/click **[!UICONTROL Search]** on the toolbar.
1. Drücken Sie mit dem Cursor in das Feld Omniture Search die Eingabetaste.
1. Klicken oder tippen Sie auf das GlobalNav-Symbol, um das Bedienfeld „Filter“ anzuzeigen.
1. From the **[!UICONTROL Saved Searches]** list, tap/click **[!UICONTROL Delete]** next to the smart collection you want to delete.
1. In the dialog, tap/click **[!UICONTROL Delete]** to delete the saved search.

## Run a workflow on a collection {#run-a-workflow-on-a-collection}

Sie können einen Workflow für die Assets in einer Sammlung ausführen. Wenn die Sammlung verschachtelte Sammlungen enthält, wird der Workflow auch für die Assets in den verschachtelten Sammlungen ausgeführt. Wenn jedoch die Sammlung und die verschachtelte Sammlung doppelte Assets enthalten, wird der Workflow nur einmal für solche Assets ausgeführt.

1. Wählen Sie in der Konsole „Sammlungen“ eine Sammlung aus, für die Sie einen Workflow ausführen möchten.
1. Tap/click the GlobalNav icon, and choose **Timeline** from the list.
1. Tippen oder klicken Sie in der Timeline unten auf das Caret-Zeichen und anschließend auf **Workflow starten**.
1. Wählen Sie im Abschnitt **Workflow starten** ein Workflow-Modell aus der Liste aus. Wählen Sie beispielsweise das Modell **DAM-Update-Asset** aus.
1. Geben Sie einen Titel für den Workflow ein und tippen oder klicken Sie auf **Start**.
1. Tippen oder klicken Sie im Dialogfeld auf **Fortfahren**. Der Workflow wird für alle Assets in der Sammlung ausgeführt.

>[!MORELIKETHIS]
>
>* [Erstellen einer Prüfungsaufgabe für Sammlungen](/help/assets/bulk-approval.md)

