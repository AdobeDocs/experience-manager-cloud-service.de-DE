---
title: Wie werden Formulare in Vorschau- oder Veröffentlichungsinstanzen veröffentlicht bzw. deren Veröffentlichung rückgängig gemacht?
description: Erfahren Sie, wie Sie Formulare in der AEM-Autorenumgebung veröffentlichen oder die Veröffentlichung rückgängig machen können, um Instanzen in der Vorschau anzuzeigen oder zu veröffentlichen. Unabhängig davon, ob Sie Ihre Formulare in einer Staging-Umgebung testen oder für Endbenutzer live bereitstellen, bietet AEM optimierte Tools, um diesen Prozess effizient zu verwalten.
Keywords: Manage publication, Forms Manage publication, AF Manage publication, Adaptive Forms Manage publication, Cloud Manage publication
feature: Adaptive Forms
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
role: User, Developer
level: Intermediate
exl-id: 6ade40f1-bad5-4f5e-aa0e-84b7c6a82e02
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 7%

---


# Verwalten der Veröffentlichung in Experience Manager Forms

Als Adobe Experience Manager (AEM) Forms-Administrator können Sie Formulare von Ihrer Autoreninstanz in Experience Manager Forms veröffentlichen. Sie haben außerdem die Möglichkeit, die Veröffentlichung eines Formulars oder Ordners für ein späteres Datum oder eine spätere Uhrzeit zu planen. Nach der Veröffentlichung können Benutzer auf die Formulare zugreifen und sie ausfüllen.

In Experience Manager Forms können Sie ein Formular mit einer der folgenden Methoden veröffentlichen:

* [Option Veröffentlichen](#publish-forms-using-the-publish-option)
* [Veröffentlichungsoption verwalten](#publish-forms-using-the-manage-publication-option)

## Zu beachtende Punkte

* Nur Mitglieder der `forms-users` können die Option **Veröffentlichung verwalten** verwenden, um die Formulare zu veröffentlichen.
* Änderungen an Formularen oder Ordnern in Experience Manager Forms werden erst dann in der **Veröffentlichungsinstanz** angezeigt, wenn sie erneut veröffentlicht wurden. Dadurch wird sichergestellt, dass laufende Aktualisierungen in der Veröffentlichungsinstanz nicht **werden**. Nur von einem Administrator explizit veröffentlichte Änderungen werden in der **Publish**-Instanz übernommen.

## Veröffentlichen von Formularen mit der Option Veröffentlichen

Mit **Option „Veröffentlichen** können Sie ein Formular sofort veröffentlichen. So veröffentlichen Sie ein Experience Manager-Formular mithilfe **Schaltfläche Veröffentlichen** der Symbolleiste. So veröffentlichen Sie Formulare mit der Option Veröffentlichen :

1. Navigieren Sie in der Experience Manager Forms-Konsole zum übergeordneten Ordner und wählen Sie ein Formular aus, das Sie veröffentlichen möchten.
1. Klicken Sie auf **Option** Veröffentlichen“ auf der Symbolleiste, um alle Referenz-Assets anzuzeigen, die mit dem Formular veröffentlicht werden sollen.
1. Klicken Sie auf **[!UICONTROL Veröffentlichen]**.

   ![Formular veröffentlichen und Veröffentlichung aufheben](/help/edge/docs/forms/assets/publish-form-option.png)

   Nachdem das Formular und die zugehörigen Assets erfolgreich veröffentlicht wurden, wird **Dialogfeld** Erfolg“ angezeigt.
1. Klicken Sie auf **Schließen**.

   ![Dialogfeld „Erfolg“](/help/forms/assets/publish-success1.png)

### Veröffentlichung des Formulars aufheben

Nach der erfolgreichen Veröffentlichung des Formulars mit der Option **Veröffentlichen** und den zugehörigen Assets können Sie die Veröffentlichung sogar aufheben, indem Sie die Schaltfläche **[!UICONTROL Veröffentlichung aufheben]** in der Symbolleiste verwenden. So heben Sie die Veröffentlichung eines Formulars auf:

1. Um die Veröffentlichung des Formulars und der zugehörigen Assets rückgängig zu machen, wählen Sie das Formular aus und klicken Sie auf **[!UICONTROL Veröffentlichung rückgängig machen]** auf der Symbolleiste

   Wenn Sie auf die Schaltfläche **[!UICONTROL Veröffentlichung rückgängig machen]** klicken, wird **Dialogfeld** Veröffentlichung rückgängig machen“ angezeigt.
1. Klicken Sie auf **[!UICONTROL Veröffentlichung aufheben]**, um den Prozess zum Aufheben der Veröffentlichung zu starten

   ![Dialogfeld „Veröffentlichung aufheben](/help/forms/assets/unpublish-asset.png)

   Nachdem die Veröffentlichung des Formulars und der zugehörigen Assets erfolgreich aufgehoben wurde, wird **Dialogfeld** Erfolg“ angezeigt.
1. Klicken Sie auf **Schließen**.

   ![Veröffentlichung erfolgreich aufgehoben](/help/forms/assets/unpublishing-start.png)

## Veröffentlichen von Formularen mit der Option Veröffentlichung verwalten

Mit Veröffentlichung verwalten können Sie Inhalte am ausgewählten Ziel veröffentlichen oder die Veröffentlichung rückgängig machen, Inhalte aus dem gesamten `forms&documents` Ordner zur Veröffentlichungsliste hinzufügen, Verweise zur Veröffentlichung auswählen und die Veröffentlichung für ein späteres Datum oder eine spätere Uhrzeit planen.  So veröffentlichen Sie Formulare mit der Option **Veröffentlichung verwalten**:

1. Navigieren Sie in der Experience Manager Forms-Konsole zum übergeordneten Ordner und wählen Sie ein Formular aus, das Sie veröffentlichen möchten.
1. Klicken Sie **[!UICONTROL der Symbolleiste auf]** Option Veröffentlichung verwalten .

   ![Option „Veröffentlichung verwalten“](/help/forms/assets/manage-publication-option.png)

   Die Benutzeroberfläche **Veröffentlichung verwalten** wird angezeigt:

   ![Veröffentlichung verwalten](/help/forms/assets/manage-publication.png)

   Die folgenden Optionen sind in der Benutzeroberfläche **Veröffentlichung verwalten** verfügbar:

   * **Aktionen**

      * **Veröffentlichen**: Veröffentlichen von Formularen im ausgewählten Ziel
      * **Veröffentlichung aufheben**: Veröffentlichung von Formularen im Ziel aufheben

   * **Ziel**

      * **Veröffentlichen**: Veröffentlichen von Formularen in der Veröffentlichungsinstanz von Experience Manager Forms (AEM).
      * **Vorschau**: Veröffentlichen von Formularen in der Vorschauinstanz von Experience Manager Forms (AEM).

   * **Zeitplan**

      * **Jetzt**: Formulare sofort veröffentlichen
      * **Später**: Veröffentlichen von Formularen basierend auf dem **Aktivierungsdatum** oder der Uhrzeit

1. Klicken Sie **Weiter** um fortzufahren.
1. (Optional) Verwenden Sie auf der Registerkarte **Umfang** die Option [Inhalt hinzufügen](#add-content), um weitere Inhalte für die Veröffentlichung hinzuzufügen. Sie können beispielsweise weitere Forms- oder Datensatzdokumentdateien hinzufügen.
   ![Registerkarte „Umfang“](/help/forms/assets/scope-tab.png)
1. Klicken Sie auf **[!UICONTROL Veröffentlichen]**, um die Formulare und zugehörigen Assets zu veröffentlichen. Daraufhin wird die Erfolgsmeldung angezeigt.
   ![Erfolgreiche Nachricht veröffentlichen](/help/forms/assets/publish-successful.png)

### Inhalt hinzufügen

Durch das Veröffentlichen in Experience Manager Forms können Sie der Veröffentlichungsliste weitere Inhalte (Formulare) hinzufügen.
So fügen Sie weitere Formulare für die Veröffentlichung hinzu:

1. Klicken Sie auf **Schaltfläche** Inhalt hinzufügen“, um weitere Inhalte hinzuzufügen.

   ![Inhalt hinzufügen](/help/forms/assets/add-content.png)

2. Wählen Sie das Formular auf dem Bildschirm **Pfad**.

   ![Inhalt hinzufügen](/help/forms/assets/add-assets.png)

   >[!NOTE]
   >
   > Sie können der Liste aus dem `formsanddocuments` Ordner weitere Formulare oder Ordner hinzufügen. Sie können jedoch nicht Formulare aus mehreren Ordnern gleichzeitig hinzufügen.

3. Um die Verweise zu konfigurieren, die für ein Formular veröffentlicht oder nicht veröffentlicht werden sollen, wählen Sie das Formular aus und klicken Sie auf **[!UICONTROL Veröffentlichte Verweise]**.

   ![Veröffentlichte Verweise](/help/forms/assets/published-references.png)

4. Deaktivieren Sie im Dialogfeld **Veröffentlichte**&quot; die Assets, die Sie nicht veröffentlichen möchten, und klicken Sie auf **[!UICONTROL Fertig]**.
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


### Späteres Veröffentlichen eines Formulars oder Rückgängigmachen der Veröffentlichung

Mit der Option „Später veröffentlichen“ oder „Veröffentlichung aufheben“ können Sie Formulare nicht nur zu einem späteren Zeitpunkt veröffentlichen, sondern auch einen Workflow konfigurieren. Die Formulare werden nach Abschluss des Workflows veröffentlicht oder ihre Veröffentlichung wird rückgängig gemacht.

So planen Sie die Veröffentlichung oder das Rückgängigmachen der Veröffentlichung eines Formulars:

1. Navigieren Sie in der Experience Manager Forms-Konsole zum übergeordneten Ordner und wählen Sie das Formular aus, für das Sie die Veröffentlichung planen möchten.
1. Klicken Sie **[!UICONTROL der Symbolleiste auf]** Option Veröffentlichung verwalten .

   ![Veröffentlichung verwalten](/help/forms/assets/manage-publication.png)

1. Klicken Sie **Veröffentlichen** oder **Veröffentlichung aufheben** in **[!UICONTROL Aktion]**.
1. Wählen Sie das **[!UICONTROL Ziel]** aus, in dem Sie die Veröffentlichung des Inhalts vornehmen oder aufheben möchten.
   * **Vorschau**: Verwenden Sie die Option **Vorschau** zum Veröffentlichen oder Rückgängigmachen der Veröffentlichung in einer Experience Manager Forms-Vorschauumgebung. Die Experience Manager Forms-Vorschauumgebungen werden zum Testen unter „Entwicklungsformulare“ verwendet.
   * **Veröffentlichen** **: Verwenden Sie die Option „Veröffentlichen** von Experience Manager Forms, um das Formular an die Experience Manager Forms-Veröffentlichungsumgebung zu senden, nachdem das Formular zur Verwendung in einer Produktionsumgebung bereit ist.

1. Wählen Sie **[!UICONTROL Später]** unter **Planung** aus.

   ![Veröffentlichung später verwalten](/help/forms/assets/manage-publication-later.png)

1. Wählen Sie ein **[!UICONTROL Aktivierungsdatum]** aus und geben Sie das Datum und die Uhrzeit an.
1. Klicken Sie **[!UICONTROL Weiter]**.
1. (Optional) Fügen Sie auf der Registerkarte **Umfang** Inhalte mithilfe von **[!UICONTROL Inhalt hinzufügen“]**.
   ![Veröffentlichung verwalten - Inhalte später hinzufügen](/help/forms/assets/publish-later-add-content.png)
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie auf **Registerkarte** einen **[!UICONTROL Workflow-Titel]** an.
1. Klicken Sie **[!UICONTROL Später veröffentlichen]**.

   ![Verwalten des Veröffentlichungs-Workflows](/help/forms/assets/manage-publication-workflows.png)

## Bestimmen des Veröffentlichungsstatus

Es gibt mehrere Möglichkeiten, den Veröffentlichungsstatus zu bestimmen:

* Melden Sie sich bei der Zielinstanz an, um die veröffentlichten Formulare und anderen Assets zu überprüfen (je nach geplantem Datum oder Uhrzeit).

* Verwenden Sie die Zeitleisten -Ansicht, um den Veröffentlichungsstatus zu bestimmen.

* Verwenden Sie das Menü Seiteninformationen im Editor für adaptive Forms.
