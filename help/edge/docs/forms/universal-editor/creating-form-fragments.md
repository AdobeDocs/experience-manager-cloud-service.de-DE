---
title: Erstellen von Formularfragmenten für das WYSIWYG-basierte Authoring
description: Erfahren Sie, wie Sie Formularfragmente im universellen Editor erstellen und zu Formularen hinzufügen können.
feature: Edge Delivery Services
role: Admin, User, Developer
hide: true
hidefromtoc: true
exl-id: 7b0d4c7f-f82f-407b-8e25-b725108f8455
source-git-commit: 615f4686fed0d17b7d7aa5cd86c545b11952d792
workflow-type: ht
source-wordcount: '1324'
ht-degree: 100%

---

# Erstellen und Verwenden von Edge Delivery Services-Formularfragmenten im universellen Editor

Formulare enthalten häufig allgemeine Abschnitte wie Kontaktinformationen, Identifizierungsangaben oder Einverständniserklärungen. Die Formularentwickelnden erstellen diese Abschnitte jedes Mal, wenn sie ein neues Formular erstellen, was monoton und zeitaufwändig ist.
Um diesen doppelten Aufwand zu vermeiden, bietet der universelle Editor eine Möglichkeit, wiederverwendbare Formularsegmente wie Panels oder Feldergruppen nur einmal zu erstellen und sie in verschiedenen Formularen wiederzuverwenden. Diese wiederverwendbaren, modularen und unabhängigen Segmente werden als Formularfragmente bezeichnet. Beispielsweise kann dasselbe Fragment für Notfallkontakte in verschiedenen Abschnitten eines Formulars verwendet werden, z. B. für Kontaktdetails von Mitarbeitenden und Vorgesetzten.

Am Ende des Artikels erfahren Sie, wie Sie mit dem universellen Editor Fragmente erstellen und in Formularen verwenden können.

## Funktionen von Edge Delivery Services-Formularfragmenten

* **Gewährleisten von Konsistenz mit Formularfragmenten**
Sie können Fragmente in verschiedene Formulare integrieren, wodurch Sie konsistente Layouts und standardisierte Inhalte beibehalten können. Mit dem Ansatz „Einmal ändern, überall widerspiegeln“ wird jede Aktualisierung eines Fragments automatisch auf alle Formulare angewendet.

* **Mehrfaches Hinzufügen von Formularfragmenten innerhalb eines Formulars**
Sie können ein Formularfragment mehrmals innerhalb eines Formulars hinzufügen und seine Datenbindungseigenschaften für Datenquellen oder Schemata konfigurieren.

* **Verwenden von Fragmenten in Fragmenten**
Sie können verschachtelte Formularfragmente erstellen, d. h. ein Fragment in einem anderen Fragment hinzufügen, um eine verschachtelte Fragmentstruktur zu erstellen.

  >[!NOTE]
  >
  > Ein Fragment kann nicht in sich selbst verschachtelt werden, da dies zu rekursiven Verweisen und unbeabsichtigtem Verhalten führen kann, was wiederum Fehler oder Rendering-Probleme verursacht.

## Überlegungen bei der Verwendung von Edge Delivery Services-Formularfragmenten

* Sie müssen in dem Fragment sowie in dem Formular, in dem Sie das Fragment verwenden möchten, dieselbe GitHub-URL hinzufügen.
* Ein Formularfragment, das als Verweis eingefügt wurde, kann nicht von einem Formular aus bearbeitet werden. Ändern Sie zum Bearbeiten das eigenständige Formularfragment.

## Voraussetzungen für das Erstellen von Edge Delivery Services-Formularfragmenten

* [Richten Sie Ihr GitHub-Repository so ein](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template), dass eine Verbindung zwischen Ihrer AEM-Umgebung und dem GitHub-Repository hergestellt wird.
* Wenn Sie bereits Edge Delivery Services verwenden, fügen Sie Ihrem GitHub-Repository die neueste Version des [adaptiven Formularblocks](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) hinzu.
* Die AEM Forms-Autoreninstanz enthält eine Vorlage, die auf Edge Delivery Services basiert. Stellen Sie sicher, dass die [neueste Version der Kernkomponenten](https://github.com/adobe/aem-core-forms-components) in Ihrer Umgebung installiert ist.
* Halten Sie die URL Ihrer AEM Forms as a Cloud Service-Autoreninstanz und Ihres GitHub-Repositorys bereit.

## Arbeiten mit Edge Delivery Services-Formularfragmenten

Sie können Edge Delivery Services-Formularfragmente im universellen Editor erstellen und die erstellten Fragmente zu Edge Delivery Services-Formularen hinzufügen. Sie können mit Edge Delivery Services-Formularfragmenten die folgenden Aktionen durchführen:

* [Erstellen von adaptiven Formularfragmenten](#creating-form-fragments)
* [Hinzufügen von Formularfragmenten zu einem Formular](#adding-form-fragments-to-a-form)
* [Verwalten von Formularfragmenten](#managing-form-fragments)

### Erstellen von adaptiven Formularfragmenten

Gehen Sie zum Erstellen eines Formularfragments im universellen Editor wie folgt vor:

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.
1. Klicken Sie auf **Erstellen > Adaptives Formularfragment**.

   ![Erstellen eines Fragments](/help/edge/docs/forms/universal-editor/assets/create-fragment.png)

   Der Assistent zum **Erstellen von adaptiven Formularfragmenten** wird angezeigt.
1. Wählen Sie auf der Registerkarte **Vorlage auswählen** die auf Edge Delivery Services basierende Vorlage aus und klicken Sie auf **[!UICONTROL Weiter]**.
   ![Auswählen einer Edge Delivery Services-Vorlage](/help/edge/docs/forms/universal-editor/assets/create-form-fragment.png)

1. Geben Sie Titel, Namen, Beschreibung und Tags für das Fragment an. Stellen Sie sicher, dass Sie einen eindeutigen Namen für das Fragment angeben. Wenn bereits ein anderes Fragment mit demselben Namen vorhanden ist, kann das Fragment nicht erstellt werden.
1. Geben Sie die **GitHub-URL** an. Wenn Ihr GitHub-Repository beispielsweise `edsforms` heißt und sich unter dem Konto `wkndforms` befindet, lautet die URL `https://github.com/wkndforms/edsforms`.

   ![Allgemeine Eigenschaften](/help/edge/docs/forms/universal-editor/assets/fragment-basic-properties.png)

1. (Optional) Klicken Sie auf die Registerkarte **Formularmodell**, um sie zu öffnen. Wählen Sie dann aus dem Dropdown-Menü **Auswählen** eines der folgenden Fragmentmodelle:

   ![Zeigt den Modelltyp auf der Registerkarte „Formularmodell“ an](/help/edge/docs/forms/universal-editor/assets/select-fdm-for-fragment.png)

   * **Formulardatenmodell (FDM)**: Zum Integrieren von Datenmodellobjekten und Diensten aus Datenquellen in Ihr Fragment. Wählen Sie „Formulardatenmodell (FDM)“, wenn Ihr Formular das Lesen und Schreiben von Daten aus mehreren Quellen erfordert.

   * **JSON-Schema**: Zum Integrieren Ihres Formulars in ein Backend-System, indem Sie ein JSON-Schema verknüpfen, das die Datenstruktur definiert. Damit können Sie dynamische Inhalte mithilfe der Schemaelemente hinzufügen.
   * **Keine**: Gibt an, dass das Fragment von Grund auf ohne Formularmodell erstellt werden soll.

   >[!NOTE]
   >
   > Um mehr über die Integration von Formularen oder Fragmenten mit einem Formulardatenmodell (FDM) im universellen Editor zur Verwendung verschiedener Backend-Datenquellen zu erfahren, [klicken Sie hier](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md).

1. (Optional) Geben Sie auf der Registerkarte **Erweitert** das **Veröffentlichungsdatum** oder das **Datum der Aufhebung der Veröffentlichung** für das Fragment an.

   ![Registerkarte „Erweitert“](/help/edge/docs/forms/universal-editor/assets/advanced-properties-fragment.png)
1. Klicken Sie auf **Erstellen**. Daraufhin wird ein Assistent angezeigt.

   ![Bearbeiten eines Fragments](/help/edge/docs/forms/universal-editor/assets/edit-fragment.png)

1. Klicken Sie auf **Bearbeiten**. Daraufhin wird das erstellte Fragment mit einer Standardvorlage im universellen Editor zwecks Authoring geöffnet.

   ![Fragment im universellen Editor zum Authoring](/help/edge/docs/forms/universal-editor/assets/fragment-in-ue.png)

   Im Bearbeitungsmodus können Sie dem Fragment eine beliebige Formularkomponente hinzufügen. Informationen zum Erstellen eines Fragments im universellen Editor finden Sie im Artikel [Erste Schritte mit Edge Delivery Services für AEM Forms mithilfe des universellen Editors](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg).

   Im folgenden Screenshot sehen Sie das im universellen Editor erstellte `contact fragment`.

   ![Kontaktfragment](/help/edge/docs/forms/universal-editor/assets/contact-fragment.png)

   Nachdem Sie das Fragment erstellt haben, können Sie [das erstellte Fragment in den Edge Delivery Services-Formularen hinzufügen](#adding-form-fragments-in-forms).

### Hinzufügen von Formularfragmenten zu einem Formular

Erstellen wir ein nun einfaches Formular `Employee Details`, das Informationen sowohl zu Mitarbeitenden als auch zu Verantwortlichen enthält. Sie können das Fragment `Contact Details` sowohl im Panel für Mitarbeitende als auch im Panel für Verantwortliche verwenden. Um das Formularfragment in Ihrem Formular zu verwenden, führen Sie die folgenden Schritte aus:

1. Öffnen Sie das Formular im Bearbeitungsmodus.
1. Fügen Sie die Komponente „Formularfragment“ dem Formular hinzu.
1. Öffnen Sie den Inhalts-Browser und navigieren Sie in der **Inhaltsstruktur** zur Komponente **[!UICONTROL Adaptives Formular]**.
1. Navigieren Sie zum Abschnitt, in dem ein Fragment hinzugefügt werden soll. Navigieren Sie beispielsweise zum Panel mit den **Mitarbeiterdetails**.

   ![Navigieren zum Abschnitt](/help/edge/docs/forms/universal-editor/assets/navigate-to-section.png)

1. Klicken Sie auf das Symbol **[!UICONTROL Hinzufügen]** und fügen Sie die Komponente **[!UICONTROL Formularfragment]** aus der Liste der **adaptiven Formularkomponenten** hinzu.
   ![Hinzufügen eines Formularfragments](/help/edge/docs/forms/universal-editor/assets/add-fragment.png)

   Wenn Sie die Komponente **[!UICONTROL Formularfragment]** auswählen, wird das Fragment zu Ihrem Formular hinzugefügt. Sie können die Eigenschaften des hinzugefügten Fragments konfigurieren, indem Sie dessen **Eigenschaften** öffnen. Blenden Sie beispielsweise den Titel des Fragments in seinen **Eigenschaften** aus.

   ![Konfigurieren der Fragmenteigenschaften](/help/edge/docs/forms/universal-editor/assets/fragment-properties.png)

1. Wählen Sie den **Fragmentverweis** auf der Registerkarte **Allgemein** aus. Je nach Formularmodell werden alle für Ihr Formular verfügbaren Fragmente angezeigt.

   Navigieren Sie beispielsweise zu `/content/forms/af` und wählen Sie das Fragment `Contact Details` aus:

   ![Auswählen eines Fragments](/help/edge/docs/forms/universal-editor/assets/select-fragment.png)

1. Klicken Sie auf **[!UICONTROL Auswählen]**.

   Das Formularfragment wird als Verweis in das Formular eingefügt und bleibt mit dem eigenständigen Formularfragment synchronisiert. Dies bedeutet, dass jegliche Änderungen am Fragment über alle Instanzen hinweg gespiegelt werden, in denen das Fragment in Formulare integriert ist.

   ![Fragment im Formular](/help/edge/docs/forms/universal-editor/assets/fragment-in-form.png)

   Sie können das Formular in einer Vorschau anzeigen, um zu sehen, wie das Formular im Modus **Vorschau** aussieht.

   ![Vorschau](/help/edge/docs/forms/universal-editor/assets/preview-form-with-fragment.png)

   Auf ähnliche Weise können Sie die Schritte 3 bis 7 wiederholen, um das Fragment `Contact Details` für das Panel `Supervisor Details` einzufügen.

   ![Formular „Mitarbeiterdetails“](/help/edge/docs/forms/universal-editor/assets/employee-detail-form-with-fragments.png)

### Verwalten von Formularfragmenten

Auf der Benutzeroberfläche von AEM Forms können Sie mehrere Aktionen für Formularfragmente ausführen.

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.

1. Wenn Sie ein Formularfragment auswählen, werden in der Symbolleiste die folgenden Vorgänge angezeigt, die Sie mit dem ausgewählten Fragment durchführen können.

   ![Verwalten von Fragmenten](/help/edge/docs/forms/universal-editor/assets/manage-fragment.png)

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
   <td><p> Bietet Optionen zum Kopieren des Formularfragments und zum Einfügen des Fragments an der gewünschten Position. <br /> <br /> </p> </td>
    </tr>
   <tr>
   <td><p>Vorschau</p> </td>
   <td><p>Bietet Optionen zum Anzeigen einer HTML-Vorschau des Fragments oder für eine benutzerdefinierte Vorschau des Fragments durch Zusammenführen von Daten aus einer XML-Datei mit dem Fragment. <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Herunterladen</p> </td>
   <td><p>Lädt das ausgewählte Fragment herunter.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Überprüfung starten/Überprüfung verwalten</p> </td>
   <td><p>Ermöglicht es, eine Überprüfung des ausgewählten Fragments zu initiieren und zu verwalten.<br /> <br /> </p> </td>
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
