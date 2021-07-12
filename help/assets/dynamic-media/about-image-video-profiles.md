---
title: Informationen zu Dynamic Media – Bild- und Videoprofile
description: Ein Bildprofil oder ein Videoprofil ist ein Rezept dafür, welche Optionen auf Assets angewendet werden sollen, die Sie in einen Ordner hochladen. Sie können beispielsweise angeben, welche Videokodierung auf hochgeladene Dynamic Media-Video-Assets angewendet werden soll. Alternativ können Sie angeben, welches Bildprofil auf Dynamic Media-Bild-Assets angewendet werden soll, damit sie passend zugeschnitten werden.
feature: Asset-Management, Bildprofile, Videoprofile
role: Admin,User
exl-id: 8c8f0a57-13f5-4903-8d76-bfb6ee83323c
source-git-commit: 24a4a43cef9a579f9f2992a41c582f4a6c775bf3
workflow-type: tm+mt
source-wordcount: '1270'
ht-degree: 75%

---

# Informationen zu Dynamic Media – Bild- und Videoprofile{#about-dm-image-video-profiles}

Ein Bildprofil oder ein Videoprofil ist ein Rezept dafür, welche Optionen auf Assets angewendet werden sollen, die Sie in einen Ordner hochladen. Sie können beispielsweise angeben, welche Videokodierung auf hochgeladene Dynamic Media-Video-Assets angewendet werden soll. Alternativ können Sie angeben, welches Bildprofil auf Dynamic Media-Bild-Assets angewendet werden soll, damit sie passend zugeschnitten werden.

In Dynamic Media können Sie zwei Arten von Profilen erstellen. Sie werden unter den folgenden Links detailliert vorgestellt:

* [Dynamic Media-Bildprofile](/help/assets/dynamic-media/image-profiles.md)
* [Dynamic Media-Videoprofile](/help/assets/dynamic-media/video-profiles.md)

Siehe auch [Metadaten-Profile](/help/assets/metadata-profiles.md).

Sie müssen über Administratorrechte verfügen, um Dynamic Media-Bildprofile oder Dynamic Media-Videoprofile zu erstellen, zu bearbeiten und zu löschen.

Nachdem Sie Ihr Bild- oder Videoprofil erstellt haben, weisen Sie es mindestens einem Ordner zu, den Sie für neu hochgeladene Dynamic Media-Assets verwenden.

Siehe auch [Best Practices zum Organisieren Ihrer digitalen Assets für die Verwendung von Bild- oder Videoprofilen](/help/assets/dynamic-media/best-practices-for-file-management.md).

>[!NOTE]
>
>Assets, die Sie von einem Ordner in einen anderen verschieben, werden nicht erneut verarbeitet. Angenommen, Sie verfügen über Ordner 1, dem das Profil A zugewiesen ist, und über Ordner 2, dem das Profil B zugewiesen ist. Wenn Sie die Assets aus Ordner 1 in Ordner 2 verschieben, behalten die verschobenen Assets ihre ursprüngliche Verarbeitung aus Ordner 1 bei.
>
>Dasselbe gilt auch, wenn Sie Assets zwischen zwei Ordnern verschieben, denen dasselbe Profil zugewiesen ist.

## Dynamic Media-Assets in einem Ordner erneut verarbeiten {#reprocessing-assets}

Sie können Assets in einem Ordner, der bereits über ein später von Ihnen geändertes Dynamic Media-Bildprofil oder ein Dynamic Media-Videoprofil verfügt, neu verarbeiten.

Angenommen, Sie haben ein Dynamic Media-Bildprofil erstellt und es einem Ordner zugewiesen. Bei allen Bild-Assets, die Sie in den Ordner hochgeladen haben, wurde automatisch das Bildprofil auf die Assets angewendet. Später entscheiden Sie sich jedoch, dem Profil ein neues Verhältnis für smartes Zuschneiden hinzuzufügen. Anstatt die Assets erneut auszuwählen und in den Ordner hochzuladen, führen Sie einfach den Workflow *Scene7: Assets erneut verarbeiten* aus.

Sie können den Neuverarbeitungs-Workflow für ein Asset ausführen, bei dem die Verarbeitung beim ersten Mal fehlgeschlagen ist. Selbst wenn Sie kein Bildprofil oder Videoprofil bearbeitet haben oder bereits ein Bildprofil oder ein Videoprofil angewendet haben, können Sie den Workflow zur erneuten Verarbeitung auch dann jederzeit für einen Asset-Ordner ausführen.

Sie können optional die Batch-Größe des Neuverarbeitungs-Workflows von 50 Assets bis zu 1000 Assets anpassen. Wenn Sie den Workflow _Scene7: Assets erneut verarbeiten_ für einen Ordner ausführen, werden die Assets in Batches gruppiert und zur Verarbeitung an den Dynamic Media-Server gesendet. Nach der Verarbeitung werden die Metadaten der einzelnen Assets im gesamten Batch-Satz auf [!DNL Adobe Experience Manager] aktualisiert. Wenn der Batch groß ist, kann es zu einer Verzögerung bei der Verarbeitung kommen. Wenn der Batch klein ist, kann dies zu vielen Umläufen zum Dynamic Media-Server führen.

Siehe [Anpassen der Batch-Größe des Neuverarbeitungs-Workflows](#adjusting-load).

>[!NOTE]
>
>Wenn Sie eine Massenmigration von Assets von Dynamic Media Classic zu [!DNL Experience Manager] durchführen, aktivieren Sie den Migrationsreplikationsagenten auf dem Dynamic Media-Server. Stellen Sie nach Abschluss der Migration sicher, dass Sie den Agenten deaktivieren.
>
>Der Migrationsveröffentlichungsagent muss auf dem Dynamic Media-Server deaktiviert werden, damit der Neuverarbeitungs-Workflow erwartungsgemäß funktioniert.

<!-- LEAVE IN PLACE, MAY BE USED IN THE FUTURE

Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media’s Image Production System) job. When you run the Scene7: Reprocess Assets workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job and so on until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. 

-->

**Dynamic Media-Assets in einem Ordner erneut verarbeiten:**

1. Navigieren Sie in [!DNL Experience Manager] von der Seite &quot;Assets&quot;zu einem Asset-Ordner, dem ein Bildprofil oder ein Videoprofil zugewiesen ist und für den Sie die Scene7 **anwenden möchten: Neuverarbeitung des Workflows Asset** .

   Bei Ordnern, denen ein Bildprofil oder ein Videoprofil zugewiesen ist, wird der Name des Profils in der Kartenansicht direkt unter dem Ordnernamen angezeigt.

1. Wählen Sie einen Ordner aus.

   * Der Workflow berücksichtigt rekursiv alle Dateien in dem ausgewählten Ordner.
   * Wenn sich im ausgewählten Hauptordner ein oder mehrere Unterordner mit Assets befinden, verarbeitet der Workflow jedes Asset in der Ordnerhierarchie neu.
   * Es empfiehlt sich, diesen Workflow nicht in einer Ordnerhierarchie mit mehr als 1.000 Assets auszuführen.

1. Wählen Sie links oben auf der Seite aus der Dropdownliste **[!UICONTROL Timeline]** aus.
1. Wählen Sie links unten auf der Seite rechts neben dem Feld [!UICONTROL Kommentar] das Karussymbol ( **^** ) aus.

   ![Workflow zur Neuverarbeitung von Assets 1](/help/assets/dynamic-media/assets/reprocess-assets1.png)

1. Wählen Sie **[!UICONTROL Workflow starten]** aus.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Workflow starten]** die Option **[!UICONTROL Scene7: Assets erneut verarbeiten]** aus.
1. (Optional) Geben Sie im Textfeld **Titel des Workflows eingeben** einen Namen für den Workflow ein. Sie können den Namen gegebenenfalls verwenden, um auf die Workflow-Instanz zu verweisen.

   ![Assets erneut verarbeiten 2](/help/assets/dynamic-media/assets/reprocess-assets2.png)

1. Wählen Sie **[!UICONTROL Start]** und dann **[!UICONTROL Bestätigen]** aus.

   Um den Workflow zu überwachen oder seinen Fortschritt zu überprüfen, wählen Sie auf der Hauptseite [!DNL Experience Manager] die Option **[!UICONTROL Tools > Workflow]** aus. Wählen Sie auf der Seite „Workflow-Instanzen“ einen Workflow aus. Wählen Sie in der Menüleiste **[!UICONTROL Offener Verlauf]** aus. Sie können einen ausgewählten Workflow auch auf derselben Seite „Workflow-Instanzen“ beenden, aussetzen oder umbenennen.

### Anpassen der Batch-Größe des Neuverarbeitungs-Workflows (optional) {#adjusting-load}

(Optional) Die standardmäßige Batch-Größe im Neuverarbeitungs-Workflow beträgt 50 Assets pro Auftrag. Diese optimale Batch-Größe wird durch die durchschnittliche Asset-Größe und die MIME-Typen der Assets bestimmt, bei denen die Neuverarbeitung ausgeführt wird. Ein höherer Wert bedeutet, dass ein Neuverarbeitungsauftrag viele Dateien enthalten wird. Das Verarbeitungsbanner bleibt also länger bei [!DNL Experience Manager]-Assets. Wenn die durchschnittliche Dateigröße jedoch kleiner als 1 MB oder kleiner ist, empfiehlt es sich, den Wert auf mehrere 100 zu erhöhen, jedoch nie mehr als 1000. Wenn die durchschnittliche Dateigröße Hunderte von Megabyte beträgt, empfiehlt Adobe, die Stapelgröße auf 10 zu verringern.

**Anpassen der Batch-Größe des Neuverarbeitungs-Workflows:**

1. Wählen Sie in [!DNL Experience Manager] **[!UICONTROL Adobe Experience Manager]** aus, um auf die globale Navigationskonsole zuzugreifen. Wählen Sie dann das Symbol **[!UICONTROL Tools]** (Hammer) > **[!UICONTROL Workflow > Modelle]** aus.
1. Wählen Sie auf der Seite „Workflow-Modelle“ in der Karten- oder Listenansicht **[!UICONTROL Scene7: Assets erneut verarbeiten]** aus.

   ![Seite „Workflow-Modelle“ mit „Scene7: Assets erneut verarbeiten“ in der Kartenansicht ausgewählt](/help/assets/dynamic-media/assets/reprocess-assets7.png)

1. Wählen Sie in der Symbolleiste **[!UICONTROL Bearbeiten]** aus. Eine neue Browser-Registerkarte öffnet die Workflow-Modellseite „Scene7: Assets erneut verarbeiten“.
1. Auf der Scene7: Workflow-Seite &quot;Assets erneut verarbeiten&quot;in der Nähe der oberen rechten Ecke wählen Sie **[!UICONTROL Bearbeiten]** aus, um den Workflow zu &quot;entsperren&quot;.
1. Wählen Sie im Workflow die Komponente Scene7 Batch-Upload aus, um die Symbolleiste zu öffnen, und wählen Sie dann **[!UICONTROL Konfigurieren]** in der Symbolleiste aus.

   ![Komponente „Massen-Upload in Scene7“](/help/assets/dynamic-media/assets/reprocess-assets8.png)

1. Legen Sie im Dialogfeld **[!UICONTROL Massen-Upload zu Scene7 – Schritt-Eigenschaften]** Folgendes fest:
   * Geben Sie in die Textfelder **[!UICONTROL Titel]** und **[!UICONTROL Beschreibung]** einen neuen Titel und eine neue Beschreibung für den Auftrag ein, falls gewünscht.
   * Wählen Sie **[!UICONTROL Handler-Modus]** aus, wenn der Handler mit dem nächsten Schritt fortfahren soll.
   * Geben Sie im Feld **[!UICONTROL Timeout]** den externen Prozess-Timeout (Sekunden) ein.
   * Geben Sie im Feld **[!UICONTROL Zeitraum]** ein Abrufintervall (Sekunden) ein, um zu testen, ob der externe Prozess abgeschlossen ist.
   * Geben Sie im Feld **[!UICONTROL Batch]** die maximale Anzahl von Assets (50-1.000) ein, die in einem Massen-Upload-Auftrag auf den Dynamic Media-Server verarbeitet werden sollen.
   * Wählen Sie **[!UICONTROL Bei Zeitüberschreitung fortsetzen]** aus, wenn Sie beim Erreichen des Zeitlimits fortfahren möchten. Entfernen Sie die Markierung, wenn Sie bei Erreichen der Zeitüberschreitung in den Posteingang wechseln möchten.

   ![Dialogfeld „Eigenschaften“](/help/assets/dynamic-media/assets/reprocess-assets3.png)

1. Wählen Sie oben rechts im Dialogfeld **[!UICONTROL Massen-Upload zu Scene7 - Schritteigenschaften]** die Option **[!UICONTROL Fertig]**.

1. In der oberen rechten Ecke der Scene7: Neuverarbeitung der Workflow-Modellseite für Assets, wählen Sie **[!UICONTROL Sync]** aus. Wenn Sie **[!UICONTROL Synchronisiert]** sehen, ist das Workflow-Laufzeitmodell erfolgreich synchronisiert und bereit, Assets in einem Ordner erneut zu verarbeiten.

   ![Synchronisieren des Workflow-Modells](/help/assets/dynamic-media/assets/reprocess-assets1.png)

1. Schließen Sie die Browser-Registerkarte, auf der „Scene7: Assets erneut verarbeiten“ angezeigt wird.

<!-- MAY BE NEEDED IN THE FUTURE

1. Return to the browser tab that has the open Workflow Models page, then press **Esc** to exit the selection.
1. In the upper-left corner of the page, select **[!UICONTROL Adobe Experience Manager]** to access the global navigation console, then select the **[!UICONTROL Tools]** (hammer) icon > **[!UICONTROL General > CRXDE Lite]**.
1. In the folder tree on the left side of the CRXDE Lite page, navigate to the following location:

   `/conf/global/settings/workflow/models/scene7_reprocess_assets/jcr:content/flow/reprocess/metaData`

   ![CRXDE Lite](/help/security/assets/workflow-models9.png)

1. On the right side of the CRXDE Lite page, in the lower portion, enter the following name, type, and value in its respective field:
    * **[!UICONTROL Name]**: `reprocess-batch-size`
    * **[!UICONTROL Type]**: `Long`
    * **[!UICONTROL Value]**: enter a default value (50-1000) for the batch size
1. In the lower-right corner, select **[!UICONTROL Add]**. The new property appears as the following:

    ![Saving the new property](/help/security/assets/workflow-models10.png)

1. On the menu bar of the CRXDE Lite page, select **[!UICONTROL Save All]**.
1. In the upper-left corner of the page, select **[!UICONTROL CRXDE Lite]** to return to the main Experience Manager console
1. Repeat steps 1-7 to re-synchronize the new batch size to the Scene7: Reprocess Assets workflow model.

-->
