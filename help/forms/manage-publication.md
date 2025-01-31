---
title: Wie werden Formulare in Vorschau- oder Veröffentlichungsinstanzen veröffentlicht bzw. deren Veröffentlichung rückgängig gemacht?
description: Erfahren Sie, wie Sie Formulare in der AEM-Autorenumgebung veröffentlichen oder die Veröffentlichung rückgängig machen können, um Instanzen in der Vorschau anzuzeigen oder zu veröffentlichen. Unabhängig davon, ob Sie Ihre Formulare in einer Staging-Umgebung testen oder für Endbenutzer live bereitstellen, bietet AEM optimierte Tools, um diesen Prozess effizient zu verwalten.
Keywords: Manage publication, Forms Manage publication, AF Manage publication, Adaptive Forms Manage publication, Cloud Manage publication
feature: Adaptive Forms
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
role: User, Developer
level: Intermediate
source-git-commit: d3c089dcca80255f53c0888d46ee1b4b6246741e
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 2%

---


# &#x200B;Veröffentlichung in Experience Manager Forms verwalten

Als Adobe Experience Manager Forms-Administrator können Sie Formulare von Ihrer Autoreninstanz in Experience Manager Forms veröffentlichen. Sie können die Veröffentlichung eines Formulars oder Ordners zu einem späteren Zeitpunkt planen. Nach der Veröffentlichung können Benutzer auf die Formulare zugreifen und sie ausfüllen.

In der Experience Manager Forms-Benutzeroberfläche können Sie ein Formular mit dem folgenden Befehl veröffentlichen:
* [Publish-Option](#publish-forms-using-the-publish-option)
* [Veröffentlichungsoption verwalten](#publish-forms-using-the-manage-publication-option)

Wenn Sie in Experience Manager Forms nachfolgende Änderungen an den Originalformularen oder -ordnern vornehmen, werden die Änderungen erst dann in der **Publish**-Instanz übernommen, wenn Sie von Experience Manager Forms aus erneut veröffentlichen. Dadurch wird sichergestellt, dass laufende Änderungen nicht in der **Publish-Instanz** sind. Nur von einem Administrator veröffentlichte Änderungen sind in der **Publish**-Instanz verfügbar.

## Publish Forms mit der Option &quot;Publish&quot;

Mit der Option **Publish** können Sie ein Formular sofort veröffentlichen. So veröffentlichen Sie ein Experience Manager-Formular mithilfe der Schaltfläche **Publish** in der Symbolleiste. So veröffentlichen Sie Formulare mit der Option Publish :

1. Navigieren Sie in der Experience Manager Forms-Konsole zum übergeordneten Ordner und wählen Sie ein Formular aus, das Sie veröffentlichen möchten.
1. Klicken Sie auf die Option **Publish** in der Symbolleiste, um sich alle Referenz-Assets anzusehen, die mit dem Formular veröffentlicht werden sollen.
1. Klicken Sie auf **[!UICONTROL Veröffentlichen]**.

   ![Publish und Formular zum Rückgängigmachen der Veröffentlichung](/help/edge/docs/forms/assets/publish-form-option.png)

   Nachdem das Formular und die zugehörigen Assets erfolgreich veröffentlicht wurden, wird **Dialogfeld** Erfolg“ angezeigt. Klicken Sie **Schließen**, um das Dialogfeld zu schließen.

   ![Dialogfeld „Erfolg“](/help/forms/assets/publish-success.png)

### Veröffentlichung des Formulars aufheben

Nach der erfolgreichen Veröffentlichung des Formulars mit der Option **Publish** und den zugehörigen Assets können Sie die Veröffentlichung sogar mit der Schaltfläche **[!UICONTROL Veröffentlichung rückgängig machen]** in der Symbolleiste aufheben. So heben Sie die Veröffentlichung eines Formulars auf:

1. Um die Veröffentlichung des Formulars und der zugehörigen Assets rückgängig zu machen, wählen Sie das Formular aus und klicken Sie auf **[!UICONTROL Veröffentlichung rückgängig machen]** auf der Symbolleiste

   Wenn Sie auf die Schaltfläche **[!UICONTROL Veröffentlichung rückgängig machen]** klicken, wird **Dialogfeld** Veröffentlichung rückgängig machen“ angezeigt.
1. Klicken Sie auf **[!UICONTROL Veröffentlichung aufheben]**, um den Prozess zum Aufheben der Veröffentlichung zu starten

   ![Dialogfeld „Veröffentlichung aufheben](/help/forms/assets/unpublish-asset.png)

   Nachdem die Veröffentlichung des Formulars und der zugehörigen Assets erfolgreich aufgehoben wurde, wird **Dialogfeld** Erfolg“ angezeigt. Klicken Sie **Schließen**, um das Dialogfeld zu schließen.

   ![Veröffentlichung erfolgreich aufgehoben](/help/forms/assets/unpublishing-start.png)

## Publish-Formulare mit der Option Veröffentlichung verwalten

Mit „Veröffentlichung verwalten“ können Sie Inhalte am ausgewählten Ziel veröffentlichen oder die Veröffentlichung rückgängig machen, Inhalte aus dem gesamten Ordner „Formulare und Dokumente“ zur Veröffentlichungsliste hinzufügen, Verweise zur Veröffentlichung auswählen und die Veröffentlichung für ein späteres Datum oder eine spätere Uhrzeit planen.  So veröffentlichen Sie Formulare mit der Option Veröffentlichung verwalten :

1. Navigieren Sie in der Experience Manager Forms-Konsole zum übergeordneten Ordner und wählen Sie ein Formular aus, das Sie veröffentlichen möchten.
1. Klicken Sie **[!UICONTROL der Symbolleiste auf]** Option Veröffentlichung verwalten .

   ![Option „Veröffentlichung verwalten“](/help/forms/assets/manage-publication-option.png)

   Die Benutzeroberfläche **Veröffentlichung verwalten** wird angezeigt:

   ![Veröffentlichung verwalten](/help/forms/assets/manage-publication.png)

   Die folgenden Optionen sind in der Benutzeroberfläche **Veröffentlichung verwalten** verfügbar:

   * **Aktionen**

      * **Publish**: Publish-Formulare für das ausgewählte Ziel
      * **Veröffentlichung aufheben**: Veröffentlichung von Formularen im Ziel aufheben

   * **Ziel**

      * **Publish**: Publish-Instanz von Publish Forms an Experience Manager Forms (AEM).
      * **Vorschau**: Vorschauinstanz von Publish Forms to Experience Manager Forms (AEM).

   * **Zeitplan**

      * **Jetzt**: Publish-Formulare sofort
      * **Später**: Publish-Formulare basierend auf dem **Aktivierungsdatum** oder der Uhrzeit

1. Klicken Sie **Weiter** um fortzufahren.
1. Verwenden **auf der Registerkarte** Umfang“ die Option [Inhalt hinzufügen](#add-content), um weitere Inhalte für die Veröffentlichung hinzuzufügen. Sie können beispielsweise weitere Forms- oder Datensatzdokumentdateien hinzufügen.
   ![Registerkarte „Umfang“](/help/forms/assets/scope-tab.png)
1. Klicken Sie auf **[!UICONTROL Publish]**, um die Formulare und zugehörigen Assets zu veröffentlichen. Daraufhin wird die Erfolgsmeldung angezeigt.
   ![Erfolgreiche Nachricht veröffentlichen](/help/forms/assets/publish-successful.png)

### Inhalt hinzufügen

Durch das Veröffentlichen in Experience Manager Forms können Sie der Veröffentlichungsliste weitere Inhalte (Formulare und Ordner) hinzufügen. Sie können der Liste aus dem `formsanddocuments` Ordner weitere Formulare oder Ordner hinzufügen. Sie können jedoch nicht Formulare aus mehreren Ordnern gleichzeitig hinzufügen. So fügen Sie weitere Formulare für die Veröffentlichung hinzu:

1. Klicken Sie auf **Schaltfläche** Inhalt hinzufügen“, um weitere Inhalte hinzuzufügen.

   ![Inhalt hinzufügen](/help/forms/assets/add-content.png)

1. Wählen Sie das Formular auf dem Bildschirm **Pfad**. Sie können mehrere Formulare aus einem Ordner hinzufügen oder mehrere Ordner gleichzeitig hinzufügen. Sie können jedoch nicht Formulare aus mehreren Ordnern gleichzeitig hinzufügen.

   ![Inhalt hinzufügen](/help/forms/assets/add-assets.png)

1. Um die Verweise zu konfigurieren, die für ein Formular veröffentlicht oder nicht veröffentlicht werden sollen, wählen Sie das Formular aus und klicken Sie auf **[!UICONTROL Veröffentlichte Verweise]**.

   ![Veröffentlichte Verweise](/help/forms/assets/published-references.png)

1. Deaktivieren Sie im Dialogfeld **Veröffentlichte**&quot; die Assets, die Sie nicht veröffentlichen möchten, und klicken Sie auf **[!UICONTROL Fertig]**.
   ![Dialogfeld „Veröffentlichte Verweise“](/help/forms/assets/published-references-dialog.png)

<!--
### Include Folder Settings
By default, publishing a folder to Experience Manager Forms publishes all the assets, subfolders, and their references. To filter the folder for publishing:

1. Click **[Include Folder Settings]** to filter the folder.

    ![Include folder](/help/forms/assets/include-folder.png)

    The **[UICONTROL Include Folder Settings]** dialog appears. 
    
    ![Include folder dialog](/help/forms/assets/include-folder-dialog.png)
    
    The **[UICONTROL Include Folder Settings]** includes following options:

    * **[!UICONTROL Include folder contents]** checkbox. 
        * If selected, all forms and assets in the chosen folder, its subfolders (including all forms and assets within them), and references are published.
        * If not selected, only the forms and assets in the selected folder are published, while subfolder forms and assets are not.

    * **[!UICONTROL Include only immediate folder contents]** checkbox
        Selecting the **[!UICONTROL Include folder contents]** checkbox enables the **[!UICONTROL Include only immediate folder contents]** checkbox for selection.

        * If you select both options, all the forms and assets of the selected folder, subfolders (empty), and references are published. The forms and assets of the subfolders are not published.
        * -->


### Publish oder Rückgängigmachen der Veröffentlichung eines Formulars

Mit der Option „Später veröffentlichen“ oder „Veröffentlichung aufheben“ können Sie Formulare nicht nur zu einem späteren Zeitpunkt veröffentlichen, sondern auch einen Workflow konfigurieren. Die Formulare werden nach Abschluss des Workflows veröffentlicht oder ihre Veröffentlichung wird rückgängig gemacht. So planen Sie die Veröffentlichung oder das Rückgängigmachen der Veröffentlichung eines Formulars:

1. Navigieren Sie in der Experience Manager Forms-Konsole zum übergeordneten Ordner und wählen Sie das Formular aus, für das Sie die Veröffentlichung planen möchten.
1. Klicken Sie **[!UICONTROL der Symbolleiste auf]** Option Veröffentlichung verwalten .

   ![Veröffentlichung verwalten](/help/forms/assets/manage-publication.png)

1. Klicken Sie auf **Publish** oder **Veröffentlichung aufheben** in **[!UICONTROL Action]** und wählen Sie dann das **[!UICONTROL Ziel]** aus, in dem Sie die Veröffentlichung des Inhalts durchführen oder aufheben möchten.
   * **Vorschau**: Verwenden Sie die Option **Vorschau** zum Veröffentlichen oder Rückgängigmachen der Veröffentlichung in einer Experience Manager Forms-Vorschauumgebung. Die Experience Manager Forms-Vorschauumgebungen werden zum Testen unter „Entwicklungsformulare“ verwendet.
   * **Publish**: Verwenden Sie die Option &quot;Experience Manager Forms Publish&quot;, um das Formular an die Experience Manager Forms-Veröffentlichungsumgebung zu senden, nachdem das Formular für die Verwendung in einer Produktionsumgebung bereit ist.

1. Wählen Sie **[!UICONTROL Später]** unter Planung aus.

   ![Veröffentlichung später verwalten](/help/forms/assets/manage-publication-later.png)

1. Wählen Sie ein **[!UICONTROL Aktivierungsdatum]** aus und geben Sie das Datum und die Uhrzeit an.
1. Klicken Sie **[!UICONTROL Weiter]**.
1. Klicken Sie auf der **Umfang** auf **[!UICONTROL Inhalt hinzufügen]** (falls erforderlich).
   ![Veröffentlichung verwalten - Inhalte später hinzufügen](/help/forms/assets/publish-later-add-content.png)
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. (Optional) Geben Sie auf der **Workflows** einen **[!UICONTROL Workflow-Titel]** an.
1. Klicken Sie auf **[!UICONTROL Publish Later]**.

   ![Verwalten des Veröffentlichungs-Workflows](/help/forms/assets/manage-publication-workflows.png)

## Bestimmen des Veröffentlichungsstatus

Es gibt mehrere Möglichkeiten, den Veröffentlichungsstatus zu bestimmen:

* Melden Sie sich bei der Zielinstanz an, um die veröffentlichten Formulare und anderen Assets zu überprüfen (je nach geplantem Datum oder Uhrzeit).

* Verwenden Sie die Zeitleisten -Ansicht, um den Veröffentlichungsstatus zu bestimmen.

* Verwenden Sie das Menü Seiteninformationen im Editor für adaptive Forms.
