---
title: Erstellen von Formularfragmenten für das WYSIWYG-basierte Authoring
description: Erfahren Sie, wie Sie Formularfragmente im universellen Editor erstellen und zu Formularen hinzufügen.
feature: Edge Delivery Services
role: Admin, User, Developer
hide: true
hidefromtoc: true
source-git-commit: 62c58ceb2d2d659bad591b3eba1bfd924f2a848b
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 16%

---


# Erstellen und Verwenden von Edge Delivery Services-Formularfragmenten im universellen Editor

Forms enthält häufig allgemeine Abschnitte wie Kontaktinformationen, Identifizierungsdetails oder Einverständniserklärungen. Die Formularentwickler erstellen diese Abschnitte jedes Mal, wenn sie ein neues Formular erstellen, was sich wiederholt und zeitaufwendig ist.
Um diese Doppelarbeit zu vermeiden, bietet der universelle Editor eine Möglichkeit, wiederverwendbare Formularsegmente wie Bereiche oder Feldergruppen nur einmal zu erstellen und sie in verschiedenen Formularen wiederzuverwenden. Diese wiederverwendbaren, modularen und eigenständigen Segmente werden als Formularfragmente bezeichnet. Beispielsweise kann dasselbe Fragment für Notfallkontakte in verschiedenen Abschnitten eines Formulars verwendet werden, z. B. für Mitarbeiter- und Vorgesetzte-Kontaktdetails.

Am Ende des Artikels erfahren Sie, wie Sie mit dem universellen Editor Fragmente in Formularen erstellen und verwenden.

## Funktionen von Edge Delivery Services-Formularfragmenten

* **Konsistenz mit Formularfragmenten gewährleisten**
Sie können Fragmente in verschiedene Formulare integrieren, wodurch Sie konsistente Layouts und standardisierte Inhalte beibehalten können. Mit dem Ansatz „Einmal ändern, überall widerspiegeln“ wird jede Aktualisierung eines Fragments automatisch auf alle Formulare angewendet.

* **Mehrfaches Hinzufügen von Formularfragmenten innerhalb eines Formulars**
Sie können ein Formularfragment mehrmals innerhalb eines Formulars hinzufügen und seine Datenbindungseigenschaften für Datenquellen oder Schemata konfigurieren.

* **Verwenden von Fragmenten innerhalb von Fragmenten**
Sie können verschachtelte Formularfragmente erstellen, d. h. Sie können ein Fragment in einem anderen Fragment hinzufügen und eine verschachtelte Fragmentstruktur aufweisen.

  >[!NOTE]
  >
  > Ein Fragment kann nicht in sich selbst verschachtelt werden, da dies zu rekursiven Verweisen und unbeabsichtigtem Verhalten führen kann, was zu Fehlern oder Rendering-Problemen führen kann.

## Überlegungen bei der Verwendung von Edge Delivery Services-Formularfragmenten

* Sie müssen dieselbe GitHub-URL sowohl dem Fragment als auch dem Formular hinzufügen, in dem Sie das Fragment verwenden möchten.
* Sie können ein Formularfragment, das per Verweis eingefügt wurde, nicht aus einem Formular heraus bearbeiten. Um das eigenständige Formularfragment zu bearbeiten, ändern Sie es.

## Voraussetzungen für das Erstellen von Edge Delivery Services-Formularfragmenten

* [Richten Sie Ihr GitHub-Repository ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template), um eine Verbindung zwischen Ihrer AEM-Umgebung und dem GitHub-Repository herzustellen.
* Wenn Sie bereits Edge Delivery Services verwenden, fügen Sie Ihrem GitHub-Repository die neueste Version des [adaptiven Formularblocks](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) hinzu.
* Die AEM Forms-Autoreninstanz enthält eine Vorlage, die auf Edge Delivery Services basiert. Stellen Sie sicher, dass die [neueste Version der Kernkomponenten](https://github.com/adobe/aem-core-forms-components) in Ihrer Umgebung installiert ist.
* Halten Sie die URL Ihrer AEM Forms as a Cloud Service-Autoreninstanz und Ihres GitHub-Repositorys bereit.

## Arbeiten mit Edge Delivery Services-Formularfragmenten

Sie können Edge Delivery Services-Formularfragmente im universellen Editor erstellen und die erstellten Fragmente zu Edge Delivery Services-Formularen hinzufügen. Sie können die folgenden Aktionen mit Edge Delivery Services-Formularfragmenten durchführen:

* [Erstellen von Formularfragmenten](#creating-form-fragments)
* [Hinzufügen von Formularfragmenten zu einem Formular](#adding-form-fragments-to-a-form)
* [Verwalten von Formularfragmenten](#managing-form-fragments)

### Erstellen von Formularfragmenten

Um ein Formularfragment im universellen Editor zu erstellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.
1. Klicken Sie auf **Erstellen > Adaptives Formularfragment**.

   ![Fragment erstellen](/help/edge/docs/forms/universal-editor/assets/create-fragment.png)

   Der **Assistent „Adaptives Formularfragment erstellen** wird angezeigt.
1. Wählen Sie auf der Registerkarte **Vorlage auswählen“ die auf Edge Delivery Services basierende Vorlage** und klicken Sie auf **[!UICONTROL Weiter]**.
   ![Edge Delivery Services-Vorlage auswählen](/help/edge/docs/forms/universal-editor/assets/create-form-fragment.png)

1. Geben Sie Titel, Namen, Beschreibung und Tags für das Fragment an. Stellen Sie sicher, dass Sie einen eindeutigen Namen für das Fragment angeben. Wenn bereits ein anderes Fragment mit demselben Namen vorhanden ist, kann das Fragment nicht erstellt werden.
1. Geben Sie die **GitHub-URL** an. Wenn sich Ihr GitHub-Repository beispielsweise `edsforms` heißt und sich unter der `wkndforms` befindet, wird die URL `https://github.com/wkndforms/edsforms`.

   ![Grundlegende Eigenschaften](/help/edge/docs/forms/universal-editor/assets/fragment-basic-properties.png)

1. (Optional) Klicken Sie, um die Registerkarte **Formularmodell** zu öffnen. Wählen Sie dann **Dropdown-Menü** Auswählen aus“ eines der folgenden Fragmentmodelle aus:

   ![Zeigt den Modelltyp auf der Registerkarte „Formularmodell“ an](/help/edge/docs/forms/universal-editor/assets/select-fdm-for-fragment.png)

   * **Formulardatenmodell (FDM)**: Integrieren Sie Datenmodellobjekte und Services aus Datenquellen in Ihr Fragment. Wählen Sie Formulardatenmodell (FDM) , wenn Ihr Formular das Lesen und Schreiben von Daten aus mehreren Quellen erfordert.

   * **JSON-Schema**: Integrieren Sie Ihr Formular in ein Backend-System, indem Sie ein JSON-Schema verknüpfen, das die Datenstruktur definiert. Damit können Sie dynamische Inhalte mithilfe der Schemaelemente hinzufügen.
   * **Keine**: Gibt an, dass das Fragment von Grund auf ohne Formularmodell erstellt werden soll.

   >[!NOTE]
   >
   > Informationen zum Integrieren von Formularen oder Fragmenten in ein Formulardatenmodell (FDM) im universellen Editor zur Verwendung verschiedener Backend-Datenquellen finden Sie [hier](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md).

1. (Optional) Geben Sie auf der Registerkarte **Erweitert** das Veröffentlichungsdatum oder **Datum** Rückgängigmachen der Veröffentlichung **Fragments**.

   ![Registerkarte Erweitert](/help/edge/docs/forms/universal-editor/assets/advanced-properties-fragment.png)
1. Klicken Sie **Erstellen** und ein Assistent wird angezeigt.

   ![Fragment bearbeiten](/help/edge/docs/forms/universal-editor/assets/edit-fragment.png)

1. Klicken Sie **Bearbeiten** und das erstellte Fragment mit einer Standardvorlage wird im universellen Editor für das Authoring geöffnet.

   ![Fragment im universellen Editor für das Authoring](/help/edge/docs/forms/universal-editor/assets/fragment-in-ue.png)

   Im Bearbeitungsmodus können Sie dem Fragment beliebige Formularkomponenten hinzufügen. Informationen zum Erstellen eines Fragments im universellen Editor finden Sie im Artikel [Erste Schritte mit Edge Delivery Services für AEM Forms mit dem universellen Editor](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg).

   Im folgenden Screenshot sehen Sie die im universellen Editor erstellten `contact fragment`.

   ![Kontaktfragment](/help/edge/docs/forms/universal-editor/assets/contact-fragment.png)

   Nachdem Sie das Fragment erstellt haben, können Sie [das erstellte Fragment in der Edge Delivery Services Forms hinzufügen](#adding-form-fragments-in-forms).

### Hinzufügen von Formularfragmenten zu einem Formular

Erstellen wir ein einfaches `Employee Details` Formular, das sowohl Mitarbeiter- als auch Vorgesetzte-Informationen enthält. Sie können das `Contact Details` Fragment sowohl im Mitarbeiter- als auch im Supervisor-Bedienfeld verwenden. Um das Formularfragment in Ihrem Formular zu verwenden, führen Sie die folgenden Schritte aus:

1. Öffnen Sie das Formular im Bearbeitungsmodus.
1. Fügen Sie die Formularfragment -Komponente zum Formular hinzu.
1. Öffnen Sie den Inhalts-Browser und navigieren Sie in der **Inhaltsstruktur** zur Komponente **[!UICONTROL Adaptives Formular]**.
1. Navigieren Sie zum Abschnitt, in dem Sie ein Fragment hinzufügen möchten. Navigieren Sie beispielsweise zum Bedienfeld **Mitarbeiterdetails** .

   ![Navigieren Sie zum Abschnitt](/help/edge/docs/forms/universal-editor/assets/navigate-to-section.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen]** und fügen Sie die Komponente **[!UICONTROL Formularfragment]** aus der Liste **Adaptive Formularkomponenten** hinzu.
   ![Formularfragment hinzufügen](/help/edge/docs/forms/universal-editor/assets/add-fragment.png)

   Wenn Sie die Komponente **[!UICONTROL Formularfragment]** auswählen, wird das Fragment zu Ihrem Formular hinzugefügt. Sie können die Eigenschaften des hinzugefügten Fragments konfigurieren, indem Sie dessen **Eigenschaften** öffnen. Blenden Sie beispielsweise den Titel des Fragments in seinen **Eigenschaften** aus.

   ![Konfigurieren der Fragmenteigenschaften](/help/edge/docs/forms/universal-editor/assets/fragment-properties.png)

1. Wählen Sie den **Fragmentverweis** auf der Registerkarte **Allgemein** aus. Alle für Ihr Formular verfügbaren Fragmente werden je nach Formularmodell angezeigt.

   Navigieren Sie beispielsweise zu `/content/forms/af` und wählen Sie das `Contact Details` aus.

   ![Fragment auswählen](/help/edge/docs/forms/universal-editor/assets/select-fragment.png)

1. Klicken Sie **[!UICONTROL Auswählen]**.

   Das Formularfragment wird per Verweis auf das Formular hinzugefügt und bleibt mit dem eigenständigen Formularfragment synchronisiert. Dies bedeutet, dass alle am Fragment vorgenommenen Änderungen in allen Instanzen gespiegelt werden, in denen das Fragment in Formulare integriert ist.

   ![Fragment im Formular](/help/edge/docs/forms/universal-editor/assets/fragment-in-form.png)

   Sie können das Formular in der Vorschau anzeigen, um zu sehen, wie das Formular im **Vorschau**-Modus angezeigt wird.

   ![Vorschau](/help/edge/docs/forms/universal-editor/assets/preview-form-with-fragment.png)

   Auf ähnliche Weise können Sie die Schritte 3 bis 7 wiederholen, um das `Contact Details` für das `Supervisor Details` einzufügen.

   ![Formular „Mitarbeiterdetails“](/help/edge/docs/forms/universal-editor/assets/employee-detail-form-with-fragments.png)

### Verwalten von Formularfragmenten

Sie können über die Benutzeroberfläche von AEM Forms mehrere Vorgänge mit Formularfragmenten durchführen.

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.

1. Wenn Sie ein Formularfragment auswählen, werden in der Symbolleiste die folgenden Vorgänge angezeigt, die Sie mit dem ausgewählten Fragment durchführen können.

   ![Fragment verwalten](/help/edge/docs/forms/universal-editor/assets/manage-fragment.png)

   <table>
    <tbody>
    <tr>
   <td><p><strong>Vorgang</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
    </tr>
    <tr>
   <td><p>Bearbeiten</p> </td>
   <td><p>Öffnet das Formularfragment im Bearbeitungsmodus.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Eigenschaften</p> </td>
   <td><p>Bietet Optionen zum Ändern der Eigenschaften des Formularfragments.<br /> <br /> </p> </td>
    </tr>
    <td><p>Kopieren</p> </td>
   <td><p> Bietet Optionen zum Kopieren des Formularfragments und zum Einfügen an der gewünschten Position. <br /> <br /> </p> </td>
    </tr>
   <tr>
   <td><p>Vorschau</p> </td>
   <td><p>Bietet Optionen, um eine Vorschau des Fragments als HTML anzuzeigen oder eine benutzerdefinierte Vorschau durchzuführen, indem Daten aus einer XML-Datei mit dem Fragment zusammengeführt werden. <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Download</p> </td>
   <td><p>Lädt das ausgewählte Fragment herunter.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Review starten/verwalten</p> </td>
   <td><p>Initiieren und Verwalten einer Review des ausgewählten Fragments.<br /> <br /> </p> </td>
    </tr>
    <!--<tr>
   <td><p>Add Dictionary</p> </td>
   <td><p>Generates a dictionary for localizing the selected fragment. For more information, see <a>Localizing Adaptive Forms</a>.<br /> <br /> </p> </td>
    </tr>-->
    <tr>
   <td><p>Veröffentlichen/Veröffentlichung rückgängig machen</p> </td>
   <td><p>Veröffentlicht das ausgewählte Fragment bzw. macht die Veröffentlichung rückgängig.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Löschen</p> </td>
   <td><p>Löscht das ausgewählte Fragment.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Vergleichen</p> </td>
   <td><p>Vergleicht zwei verschiedene Formularfragmente zu Vorschauzwecken.<br /> <br /> </p> </td>
    </tr>
    </tbody>
    </table>

## Best Practices

* Stellen Sie sicher, dass der Fragmentname eindeutig ist. Wenn bereits ein anderes Fragment mit demselben Namen vorhanden ist, kann das Fragment nicht erstellt werden.
* Alle Ausdrücke, Skripte oder Stile in einem eigenständigen Formularfragment bleiben erhalten, wenn es als Verweis eingefügt oder in ein Formular eingebettet wird.
* Wenn Sie ein Formular veröffentlichen, werden die Formularfragmente, die als Verweis in das Formular eingefügt wurden, automatisch veröffentlicht.

## Siehe auch

{{universal-editor-see-also}}