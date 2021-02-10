---
title: Informationen zu Dynamic Media – Bild- und Videoprofile
description: Ein Bildprofil oder ein Videoprofil ist ein Rezept dafür, welche Optionen auf Assets angewendet werden sollen, die Sie in einen Ordner hochladen. Sie können beispielsweise angeben, welche Videokodierung auf hochgeladene Dynamic Media-Video-Assets angewendet werden soll. Alternativ können Sie angeben, welches Bildprofil auf Dynamic Media-Bild-Assets angewendet werden soll, damit sie passend zugeschnitten werden.
translation-type: tm+mt
source-git-commit: dfaaafce8e9a7f0d90e4c3d6967c8236d48e6e40
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 76%

---


# Informationen zu Dynamic Media – Bild- und Videoprofile {#about-dm-image-video-profiles}

Ein Bildprofil oder ein Videoprofil ist ein Rezept dafür, welche Optionen auf Assets angewendet werden sollen, die Sie in einen Ordner hochladen. Sie können beispielsweise angeben, welche Videokodierung auf hochgeladene Dynamic Media-Video-Assets angewendet werden soll. Alternativ können Sie angeben, welches Bildprofil auf Dynamic Media-Bild-Assets angewendet werden soll, damit sie passend zugeschnitten werden.

In Dynamic Media können Sie zwei Arten von Profilen erstellen. Sie werden unter den folgenden Links detailliert vorgestellt:

* [Dynamic Media-Bildprofile](/help/assets/dynamic-media/image-profiles.md)
* [Dynamic Media-Videoprofile](/help/assets/dynamic-media/video-profiles.md)

Siehe auch [Metadaten-Profile](/help/assets/metadata-profiles.md).

Sie müssen über Administratorrechte verfügen, um Dynamic Media-Bildprofile oder Dynamic Media-Videoprofile zu erstellen, zu bearbeiten und zu löschen.

Nachdem Sie Ihr Image-Profil oder Video-Profil erstellt haben, weisen Sie es einem oder mehreren Ordnern zu, die Sie für neu hochgeladene Dynamic Media-Assets verwenden.

Siehe auch [Best Practices zum Organisieren Ihrer digitalen Assets für die Verwendung von Bild- oder Videoprofilen](/help/assets/dynamic-media/best-practices-for-file-management.md).

>[!NOTE]
>
>Assets, die Sie von einem Ordner in einen anderen verschieben, werden nicht erneut verarbeitet. Angenommen, Sie verfügen über Ordner 1, dem das Profil A zugewiesen ist, und über Ordner 2, dem das Profil B zugewiesen ist. Wenn Sie die Assets aus Ordner 1 in Ordner 2 verschieben, behalten die verschobenen Assets ihre ursprüngliche Verarbeitung aus Ordner 1 bei.
>
>Dasselbe gilt auch, wenn Sie Assets zwischen zwei Ordnern verschieben, denen dasselbe Profil zugewiesen ist.

## Erneutes Verarbeiten von Dynamic Media-Assets in einem Ordner {#reprocessing-assets}

Sie können Assets in einem Ordner, der bereits über ein später von Ihnen geändertes Dynamic Media-Bildprofil oder ein Dynamic Media-Videoprofil verfügt, neu verarbeiten.

Angenommen, Sie haben ein Dynamic Media-Bildprofil erstellt und es einem Ordner zugewiesen. Bei allen Bild-Assets, die Sie in den Ordner hochgeladen haben, wurde automatisch das Bildprofil auf die Assets angewendet. Später entscheiden Sie sich jedoch, dem Profil ein neues Verhältnis für smartes Zuschneiden hinzuzufügen. Anstatt die Assets erneut auszuwählen und in den Ordner hochzuladen, führen Sie einfach den Workflow *Scene7: Assets erneut verarbeiten* aus.

Sie können den Neuverarbeitungs-Workflow für ein Asset ausführen, bei dem die Verarbeitung beim ersten Mal fehlgeschlagen ist. Auch wenn Sie kein Image-Profil oder Video-Profil bearbeitet haben oder bereits ein Image-Profil oder Video-Profil angewendet haben, können Sie den Arbeitsablauf für die Neuverarbeitung jederzeit für einen Asset-Ordner ausführen.

Sie können optional die Batch-Größe des Neuverarbeitungs-Workflows von 50 Assets bis zu 1000 Assets anpassen. Wenn Sie das Scene7 _ausführen: Assets in einem Ordner neu verarbeiten, werden Assets in Stapeln gruppiert und zur Verarbeitung an den Dynamic Media-Server gesendet._ Nach der Verarbeitung werden die Metadaten der einzelnen Assets im gesamten Batch auf AEM aktualisiert. Wenn die Stapelgröße groß ist, kann es zu einer Verzögerung bei der Verarbeitung kommen. Oder wenn die Stapelgröße zu klein ist, kann dies zu vielen Rundungen zum Dynamic Media-Server führen.

Siehe [Anpassen der Batch-Größe des Neuverarbeitungs-Workflows](#adjusting-load).

>[!NOTE]
>
>Wenn Sie eine Massenmigration von Assets von Dynamic Media Classic zu Experience Manager durchführen, aktivieren Sie den Migrationsreplikationsagenten auf dem Dynamic Media-Server. Stellen Sie nach Abschluss der Migration sicher, dass Sie den Agenten deaktivieren.
>
>Der Migrationsveröffentlichungsagent muss auf dem Dynamic Media-Server deaktiviert werden, damit der Neuverarbeitungs-Workflow erwartungsgemäß funktioniert.

<!-- LEAVE IN PLACE, MAY BE USED IN THE FUTURE

Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media’s Image Production System) job. When you run the Scene7: Reprocess Assets workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job and so on until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. 

-->

**Dynamic Media-Assets in einem Ordner erneut verarbeiten**:
1. Navigieren Sie in Adobe Experience Manager auf der Seite „Assets“ zu einem Ordner mit Dynamic Media-Assets, dem ein Bildprofil oder ein Videoprofil zugewiesen ist und für den Sie den Workflow **Scene7: Assets erneut verarbeiten** anwenden möchten.

   Bei Ordnern, denen ein Image-Profil oder ein Video-Profil zugewiesen ist, wird der Name des Profils direkt unter dem Ordnernamen in der Card-Ansicht angezeigt.

1. Wählen Sie einen Ordner aus.

   * Der Workflow berücksichtigt rekursiv alle Dateien in dem ausgewählten Ordner.
   * Wenn sich im ausgewählten Hauptordner ein oder mehrere Unterordner mit Assets befinden, verarbeitet der Workflow jedes Asset in der Ordnerhierarchie neu.
   * Es empfiehlt sich, diesen Workflow nicht auf einer Ordnerhierarchie auszuführen, die mehr als 1000 Assets enthält.

1. Klicken Sie oben links auf der Seite in der Dropdown-Liste auf **[!UICONTROL Zeitleiste]**.
1. Tippen Sie in der linken unteren Ecke der Seite rechts neben dem Feld [!UICONTROL Kommentar] auf das Karussymbol ( **^** ).

   ![Workflow zur Neuverarbeitung von Assets 1](/help/assets/dynamic-media/assets/reprocess-assets1.png)

1. Klicken Sie auf **[!UICONTROL Workflow starten]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Workflow starten]** die Option **[!UICONTROL Scene7: Assets erneut verarbeiten]** aus.
1. (Optional) Geben Sie im Textfeld **Titel des Workflows eingeben** einen Namen für den Workflow ein. Sie können den Namen gegebenenfalls verwenden, um auf die Workflow-Instanz zu verweisen.

   ![Assets erneut verarbeiten 2](/help/assets/dynamic-media/assets/reprocess-assets2.png)

1. Klicken Sie auf **[!UICONTROL Starten]** und dann auf **[!UICONTROL Bestätigen]**.

   Klicken Sie auf der Hauptseite der Adobe Experience Manager-Konsole auf **[!UICONTROL Tools > Workflow]**, um den Workflow zu überwachen oder dessen Fortschritt zu überprüfen. Wählen Sie auf der Seite „Workflow-Instanzen“ einen Workflow aus. Klicken Sie in der Menüleiste auf **[!UICONTROL Offener Verlauf]**. Sie können einen ausgewählten Workflow auch auf derselben Seite „Workflow-Instanzen“ beenden, aussetzen oder umbenennen.

### Anpassen der Batch-Größe des Neuverarbeitungs-Workflows {#adjusting-load}

(Optional) Die standardmäßige Batch-Größe im Neuverarbeitungs-Workflow beträgt 50 Assets pro Auftrag. Diese optimale Stapelgröße wird durch die durchschnittliche Asset-Größe und die MIME-Typen von Assets bestimmt, auf denen die Neuverarbeitung ausgeführt wird. Ein höherer Wert bedeutet, dass Sie viele Dateien in einem einzigen Wiederaufbereitungsauftrag haben. Das Verarbeitungsbanner bleibt also länger auf den Assets des Experience Managers. Wenn die durchschnittliche Dateigröße jedoch nur 1 MB oder weniger beträgt, empfiehlt Adobe, den Wert auf mehrere Hundert, aber niemals mehr als 1.000 zu erhöhen. Wenn die durchschnittliche Dateigröße Hunderte von Megabyte beträgt, empfiehlt Adobe, die Batch-Größe auf bis zu 10 zu reduzieren.

**Anpassen der Batch-Größe des Neuverarbeitungs-Workflows**:

1. Tippen Sie in Experience Manager auf **[!UICONTROL Adobe Experience Manager]**, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie dann auf das Symbol **[!UICONTROL Tools]** (Hammer) > **[!UICONTROL Workflow > Modelle]**.
1. Wählen Sie auf der Seite „Workflow-Modelle“ in der Karten- oder Listenansicht **[!UICONTROL Scene7: Assets erneut verarbeiten]** aus.

   ![Seite „Workflow-Modelle“ mit „Scene7: Assets erneut verarbeiten“ in der Kartenansicht ausgewählt](/help/assets/dynamic-media/assets/reprocess-assets7.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**. Eine neue Browser-Registerkarte öffnet die Workflow-Modellseite „Scene7: Assets erneut verarbeiten“.
1. Tippen Sie oben rechts auf der Workflow-Seite „Scene7: Assets erneut verarbeiten“ auf **[!UICONTROL Bearbeiten]**, um den Workflow zu entsperren.
1. Wählen Sie im Workflow die Komponente Scene7 Batch Upload aus, um die Symbolleiste zu öffnen, und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Configure]**.

   ![Komponente „Massen-Upload in Scene7“](/help/assets/dynamic-media/assets/reprocess-assets8.png)

1. Legen Sie im Dialogfeld **[!UICONTROL Massen-Upload zu Scene7 – Schritt-Eigenschaften]** Folgendes fest:
   * Geben Sie in die Textfelder **[!UICONTROL Titel]** und **[!UICONTROL Beschreibung]** einen neuen Titel und eine neue Beschreibung für den Auftrag ein, falls gewünscht.
   * Wählen Sie **[!UICONTROL Handler-Modus]** aus, wenn der Handler mit dem nächsten Schritt fortfahren soll.
   * Geben Sie im Feld **[!UICONTROL Timeout]** den externen Prozess-Timeout (Sekunden) ein.
   * Geben Sie im Feld **[!UICONTROL Zeitraum]** ein Abrufintervall (Sekunden) ein, um zu testen, ob der externe Prozess abgeschlossen ist.
   * Geben Sie im Feld **[!UICONTROL Batch]** die maximale Anzahl von Assets (50-1.000) ein, die in einem Massen-Upload-Auftrag auf den Dynamic Media-Server verarbeitet werden sollen.
   * Wählen Sie **[!UICONTROL Bei Zeitüberschreitung fortsetzen]** aus, wenn Sie beim Erreichen des Zeitlimits fortfahren möchten. Entfernen Sie die Markierung, wenn Sie bei Erreichen der Zeitüberschreitung in den Posteingang wechseln möchten.

   ![Dialogfeld „Eigenschaften“](/help/assets/dynamic-media/assets/reprocess-assets3.png)

1. Tippen Sie oben rechts im Dialogfeld **[!UICONTROL Batch-Upload zu Scene7 - Schritt-Eigenschaften]** auf **[!UICONTROL Fertig]**.

1. Tippen Sie oben rechts auf der Workflow-Modellseite „Scene7: Assets erneut verarbeiten“ auf **[!UICONTROL Synchronisieren]**. Wenn Sie **[!UICONTROL Synchronisiert]** sehen, ist das Workflow-Laufzeitmodell erfolgreich synchronisiert und bereit, Assets in einem Ordner erneut zu verarbeiten.

   ![Synchronisieren des Workflow-Modells](/help/assets/dynamic-media/assets/reprocess-assets1.png)

1. Schließen Sie die Browser-Registerkarte, auf der „Scene7: Assets erneut verarbeiten“ angezeigt wird.

<!-- MAY BE NEEDED IN THE FUTURE

1. Return to the browser tab that has the open Workflow Models page, then press **Esc** to exit the selection.
1. In the upper-left corner of the page, tap **[!UICONTROL Adobe Experience Manager]** to access the global navigation console, then tap the **[!UICONTROL Tools]** (hammer) icon > **[!UICONTROL General > CRXDE Lite]**.
1. In the folder tree on the left side of the CRXDE Lite page, navigate to the following location:

   `/conf/global/settings/workflow/models/scene7_reprocess_assets/jcr:content/flow/reprocess/metaData`

   ![CRXDE Lite](/help/security/assets/workflow-models9.png)

1. On the right side of the CRXDE Lite page, in the lower portion, enter the following name, type, and value in its respective field:
    * **[!UICONTROL Name]**: `reprocess-batch-size`
    * **[!UICONTROL Type]**: `Long`
    * **[!UICONTROL Value]**: enter a default value (50-1000) for the batch size
1. In the lower-right corner, tap **[!UICONTROL Add]**. The new property appears as the following:

    ![Saving the new property](/help/security/assets/workflow-models10.png)

1. On the menu bar of the CRXDE Lite page, tap **[!UICONTROL Save All]**.
1. In the upper-left corner of the page, tap **[!UICONTROL CRXDE Lite]** to return to the main Experience Manager console
1. Repeat steps 1-7 to re-synchronize the new batch size to the Scene7: Reprocess Assets workflow model.

-->
