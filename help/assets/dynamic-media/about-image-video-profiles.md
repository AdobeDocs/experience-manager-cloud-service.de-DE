---
title: Informationen zu Dynamic Media – Bild- und Videoprofile
description: Ein Bildprofil oder ein Videoprofil ist ein Rezept dafür, welche Optionen auf Assets angewendet werden sollen, die Sie in einen Ordner hochladen. Sie können beispielsweise angeben, welche Videokodierung auf hochgeladene Dynamic Media-Video-Assets angewendet werden soll. Alternativ können Sie angeben, welches Bildprofil auf Dynamic Media-Bild-Assets angewendet werden soll, damit sie passend zugeschnitten werden.
feature: Asset-Management, Bildprofile, Videoprofile
role: Administrator,Business Practitioner
exl-id: 8c8f0a57-13f5-4903-8d76-bfb6ee83323c
source-git-commit: d3ee23917eba4a2e4ae1f2bd44f5476d2ff7dce1
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 68%

---

# Informationen zu Dynamic Media – Bild- und Videoprofile {#about-dm-image-video-profiles}

Ein Bildprofil oder ein Videoprofil ist ein Rezept dafür, welche Optionen auf Assets angewendet werden sollen, die Sie in einen Ordner hochladen. Sie können beispielsweise angeben, welche Videokodierung auf hochgeladene Dynamic Media-Video-Assets angewendet werden soll. Alternativ können Sie angeben, welches Bildprofil auf Dynamic Media-Bild-Assets angewendet werden soll, damit sie passend zugeschnitten werden.

In Dynamic Media können Sie zwei Arten von Profilen erstellen. Sie werden unter den folgenden Links detailliert vorgestellt:

* [Dynamic Media-Bildprofile](/help/assets/dynamic-media/image-profiles.md)
* [Dynamic Media-Videoprofile](/help/assets/dynamic-media/video-profiles.md)

Siehe auch [Metadaten-Profile](/help/assets/metadata-profiles.md).

Sie müssen über Administratorrechte verfügen, um Dynamic Media-Bildprofile oder Dynamic Media-Videoprofile zu erstellen, zu bearbeiten und zu löschen.

Nachdem Sie Ihr Bildprofil oder Videoprofil erstellt haben, weisen Sie es einem oder mehreren Ordnern zu, die Sie für neu hochgeladene Dynamic Media-Assets verwenden.

Siehe auch [Best Practices zum Organisieren Ihrer digitalen Assets für die Verwendung von Bild- oder Videoprofilen](/help/assets/dynamic-media/best-practices-for-file-management.md).

>[!NOTE]
>
>Assets, die Sie von einem Ordner in einen anderen verschieben, werden nicht erneut verarbeitet. Angenommen, Sie verfügen über Ordner 1, dem das Profil A zugewiesen ist, und über Ordner 2, dem das Profil B zugewiesen ist. Wenn Sie die Assets aus Ordner 1 in Ordner 2 verschieben, behalten die verschobenen Assets ihre ursprüngliche Verarbeitung aus Ordner 1 bei.
>
>Dasselbe gilt auch, wenn Sie Assets zwischen zwei Ordnern verschieben, denen dasselbe Profil zugewiesen ist.

## Erneutes Verarbeiten von Dynamic Media-Assets in einem Ordner {#reprocessing-assets}

Sie können Assets in einem Ordner, der bereits über ein später von Ihnen geändertes Dynamic Media-Bildprofil oder ein Dynamic Media-Videoprofil verfügt, neu verarbeiten.

Angenommen, Sie haben ein Dynamic Media-Bildprofil erstellt und es einem Ordner zugewiesen. Bei allen Bild-Assets, die Sie in den Ordner hochgeladen haben, wurde automatisch das Bildprofil auf die Assets angewendet. Später entscheiden Sie sich jedoch, dem Profil ein neues Verhältnis für smartes Zuschneiden hinzuzufügen. Anstatt die Assets erneut auszuwählen und in den Ordner hochzuladen, führen Sie einfach den Workflow *Scene7: Assets erneut verarbeiten* aus.

Sie können den Neuverarbeitungs-Workflow für ein Asset ausführen, bei dem die Verarbeitung beim ersten Mal fehlgeschlagen ist. Selbst wenn Sie kein Bild- oder Videoprofil bearbeitet haben oder bereits ein Bild- oder Videoprofil angewendet haben, können Sie den Neuverarbeitungs-Workflow jederzeit für einen Asset-Ordner ausführen.

Sie können optional die Batch-Größe des Neuverarbeitungs-Workflows von 50 Assets bis zu 1000 Assets anpassen. Wenn Sie _Scene7 ausführen: Neuverarbeitung des Workflows Assets_ für einen Ordner, Assets werden in Batches gruppiert und zur Verarbeitung an den Dynamic Media-Server gesendet. Nach der Verarbeitung werden die Metadaten der einzelnen Assets im gesamten Batch-Satz auf Adobe Experience Manager aktualisiert. Wenn die Batch-Größe groß ist, kann es zu einer Verzögerung bei der Verarbeitung kommen. Oder wenn die Batch-Größe zu klein ist, kann dies zu vielen Rundfahrten zum Dynamic Media-Server führen.

Siehe [Anpassen der Batch-Größe des Neuverarbeitungs-Workflows](#adjusting-load).

>[!NOTE]
>
>Wenn Sie eine Massenmigration von Assets von Dynamic Media Classic nach Experience Manager durchführen, aktivieren Sie den Migrationsreplikationsagenten auf dem Dynamic Media-Server. Stellen Sie nach Abschluss der Migration sicher, dass Sie den Agenten deaktivieren.
>
>Der Migrationsveröffentlichungsagent muss auf dem Dynamic Media-Server deaktiviert werden, damit der Neuverarbeitungs-Workflow erwartungsgemäß funktioniert.

<!-- LEAVE IN PLACE, MAY BE USED IN THE FUTURE

Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media’s Image Production System) job. When you run the Scene7: Reprocess Assets workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job and so on until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. 

-->

**Dynamic Media-Assets in einem Ordner erneut verarbeiten:**
1. Navigieren Sie in Experience Manager von der Seite &quot;Assets&quot;zu einem Asset-Ordner, dem ein Bildprofil oder ein Videoprofil zugewiesen ist und für den Sie die Scene7 **anwenden möchten: Neuverarbeitung des Workflows Asset** .

   Bei Ordnern, denen ein Bildprofil oder ein Videoprofil zugewiesen ist, wird der Name des Profils direkt unter dem Ordnernamen in der Kartenansicht angezeigt.

1. Wählen Sie einen Ordner aus.

   * Der Workflow berücksichtigt rekursiv alle Dateien in dem ausgewählten Ordner.
   * Wenn sich im ausgewählten Hauptordner ein oder mehrere Unterordner mit Assets befinden, verarbeitet der Workflow jedes Asset in der Ordnerhierarchie erneut.
   * Es empfiehlt sich, diesen Workflow nicht in einer Ordnerhierarchie mit mehr als 1000 Assets auszuführen.

1. Klicken Sie oben links auf der Seite in der Dropdown-Liste auf **[!UICONTROL Zeitleiste]**.
1. Tippen Sie unten links auf der Seite rechts neben dem Feld [!UICONTROL Kommentar] auf das Karussymbol ( **^** ).

   ![Workflow zur Neuverarbeitung von Assets 1](/help/assets/dynamic-media/assets/reprocess-assets1.png)

1. Klicken Sie auf **[!UICONTROL Workflow starten]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Workflow starten]** die Option **[!UICONTROL Scene7: Assets erneut verarbeiten]** aus.
1. (Optional) Geben Sie im Textfeld **Titel des Workflows eingeben** einen Namen für den Workflow ein. Sie können den Namen gegebenenfalls verwenden, um auf die Workflow-Instanz zu verweisen.

   ![Assets erneut verarbeiten 2](/help/assets/dynamic-media/assets/reprocess-assets2.png)

1. Klicken Sie auf **[!UICONTROL Starten]** und dann auf **[!UICONTROL Bestätigen]**.

   Klicken Sie auf der Hauptseite der Adobe Experience Manager-Konsole auf **[!UICONTROL Tools > Workflow]**, um den Workflow zu überwachen oder dessen Fortschritt zu überprüfen. Wählen Sie auf der Seite „Workflow-Instanzen“ einen Workflow aus. Klicken Sie in der Menüleiste auf **[!UICONTROL Offener Verlauf]**. Sie können einen ausgewählten Workflow auch auf derselben Seite „Workflow-Instanzen“ beenden, aussetzen oder umbenennen.

### Anpassen der Batch-Größe des Neuverarbeitungs-Workflows {#adjusting-load}

(Optional) Die standardmäßige Batch-Größe im Neuverarbeitungs-Workflow beträgt 50 Assets pro Auftrag. Diese optimale Batch-Größe wird durch die durchschnittliche Asset-Größe und die MIME-Typen von Assets bestimmt, für die die Neuverarbeitung ausgeführt wird. Ein höherer Wert bedeutet, dass ein Neuverarbeitungsauftrag viele Dateien enthält. Das Verarbeitungsbanner bleibt also länger auf Experience Manager-Assets. Wenn die durchschnittliche Dateigröße jedoch kleiner als 1 MB oder kleiner ist, empfiehlt es sich, den Wert auf mehrere 100 zu erhöhen, jedoch nie mehr als 1000. Wenn die durchschnittliche Dateigröße Hunderte von Megabyte beträgt, empfiehlt Adobe, die Stapelgröße auf 10 zu verringern.

**Anpassen der Batch-Größe des Neuverarbeitungs-Workflows:**

1. Tippen Sie in Experience Manager auf **[!UICONTROL Adobe Experience Manager]**, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie dann auf das Symbol **[!UICONTROL Tools]** (Hammer) > **[!UICONTROL Workflow > Modelle]**.
1. Wählen Sie auf der Seite „Workflow-Modelle“ in der Karten- oder Listenansicht **[!UICONTROL Scene7: Assets erneut verarbeiten]** aus.

   ![Seite „Workflow-Modelle“ mit „Scene7: Assets erneut verarbeiten“ in der Kartenansicht ausgewählt](/help/assets/dynamic-media/assets/reprocess-assets7.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**. Eine neue Browser-Registerkarte öffnet die Workflow-Modellseite „Scene7: Assets erneut verarbeiten“.
1. Tippen Sie oben rechts auf der Workflow-Seite „Scene7: Assets erneut verarbeiten“ auf **[!UICONTROL Bearbeiten]**, um den Workflow zu entsperren.
1. Wählen Sie im Workflow die Komponente Scene7 Batch-Upload aus, um die Symbolleiste zu öffnen, und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Konfigurieren]** .

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
