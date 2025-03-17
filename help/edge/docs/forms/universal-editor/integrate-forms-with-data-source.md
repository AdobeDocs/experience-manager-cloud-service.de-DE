---
title: Erstellen eines Formulardatenmodells (FDM) für ein Formular im universellen Editor
description: Erfahren Sie, wie Sie Formulare erstellen, die auf einem Formulardatenmodell (FDM) basieren. Erstellen und bearbeiten Sie Beispieldaten für Datenmodellobjekte im FDM.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
hide: true
hidefromtoc: true
source-git-commit: e2259e542df5a12748705af901d073e4486292c4
workflow-type: tm+mt
source-wordcount: '1036'
ht-degree: 11%

---


# Integrieren von Formularen mit dem Formulardatenmodell im universellen Editor

Durch die Integration von Formularen mit einem Formulardatenmodell (FDM) im universellen Editor können Sie verschiedene Backend-Datenquellen verwenden, um ein Formulardatenmodell (FDM) zu erstellen. Sie können das Formulardatenmodell (FDM) als Schema in verschiedenen Formular-Workflows verwenden. Konfigurieren Sie die Datenquellen und erstellen Sie ein Formulardatenmodell (FDM) basierend auf den in den Datenquellen verfügbaren Datenmodellobjekten und Services.

## Hinweis

* Der Vorbefüllungsdienst für Formulare im universellen Editor wird derzeit nicht unterstützt.

## Voraussetzungen

Bevor Sie Ihr Formular mit dem Formulardatenmodell im universellen Editor konfigurieren, stellen Sie sicher, dass Sie die folgenden Schritte ausgeführt haben:

* [Konfigurieren von Data Source](/help/forms/configure-data-sources.md): Richten Sie die Datenquelle ein, um Ihr Formular mit Backend-Daten zu verbinden.
* [Erstellen eines Formulardatenmodells (FDM)](/help/forms/create-form-data-models.md): Erstellen Sie ein Datenmodell mithilfe von Datenobjekten und Services aus der konfigurierten Datenquelle.
* [Konfigurieren von Datenmodellobjekten und Services](/help/forms/work-with-form-data-model.md): Ordnen Sie die Datenmodellobjekte und Services zu, um einen reibungslosen Datenfluss zwischen dem Formular und der Datenquelle sicherzustellen.

## Erstellen von Forms mit dem Formulardatenmodell im universellen Editor

Im universellen Editor können Sie Folgendes erstellen:
* [Schemabasiertes Formular](#schema-based-form): Ein schemabasiertes Formular verwendet eine Datenquelle, die während der Formularerstellung auf der Registerkarte **Daten** konfiguriert wurde, um Daten automatisch an Formularfelder zu binden.
* [Nicht schemabasiertes Formular](#non-schema-based-form): Bei einem nicht schemabasierten Formular müssen Sie manuell eine Datenquelle hinzufügen und jedes Feld aus der Inhaltsstruktur binden.

![Formulartypen im universellen Editor](/help/edge/docs/forms/universal-editor/assets/form-types.png){width="50%" align="center" height="50%"}

Diese Methoden bieten Ihnen die Flexibilität, Datenmodelle je nach Bedarf mit Formularen zu verbinden.

### Schemabasiertes Formular

Wenn Sie ein schemabasiertes Formular erstellen, wird es automatisch mit einer Datenquelle konfiguriert, und die Formularfelder sind bereits über Datenbindungen mit den Daten verknüpft. Um ein schemabasiertes Formular mit dem Assistenten für die Formularerstellung zu erstellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Autoreninstanz an. 
2. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein. Wenn Sie sich angemeldet haben, wählen Sie in der oberen linken Ecke **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.
3. Klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptives Formular]**. Der Assistent wird geöffnet. Wählen Sie auf der Registerkarte {**}Source eine Vorlage aus:**

   ![Edge Delivery Services-Vorlage](/help/edge/assets/create-eds-forms.png)

   Wenn Sie eine Edge Delivery Services-basierte Vorlage auswählen, ist **[!UICONTROL Schaltfläche]** aktiviert. Sie können zu den Registerkarten **[!UICONTROL Daten-Source]** oder **[!UICONTROL Übermittlung]** gehen, um eine Datenquelle oder eine Übermittlungsaktion auszuwählen.

4. Auf der **Daten**-Registerkarte können Sie eines der folgenden Datenmodelle auswählen:

   * **Formulardatenmodell (FDM)**: Integrieren Sie Datenmodellobjekte und Services aus Datenquellen in Ihr Formular. Wählen Sie Formulardatenmodell (FDM) , wenn Ihr Formular das Lesen und Schreiben von Daten aus mehreren Quellen erfordert.

   * **JSON-Schema**: Integrieren Sie Ihr Formular in ein Backend-System, indem Sie ein JSON-Schema verknüpfen, das die Datenstruktur definiert. Damit können Sie dynamische Inhalte mithilfe der Schemaelemente hinzufügen.

     Wählen Sie beispielsweise das erstellte Formulardatenmodell mit dem Namen PET-Formulardatenmodell aus.

     ![Formulardatenmodell auswählen](/help/edge/docs/forms/universal-editor/assets/select-petstore-form-data-model.png)


     Standardmäßig werden alle Felder des zugehörigen JSON-Schemas oder Formulardatenmodells (FDM) automatisch ausgewählt und in entsprechende Formularkomponenten konvertiert, was den Erstellungsprozess vereinfacht. Im Assistenten können Sie mithilfe von Kontrollkästchen auch selektiv auswählen, welche Felder in das Formular aufgenommen werden sollen.

5. Klicken Sie auf **[!UICONTROL Erstellen]**. Daraufhin wird der Assistent **Formular erstellen** angezeigt.
6. Geben Sie die **Name** und **Title** an.
7. Geben Sie die **GitHub-URL** an. Wenn sich Ihr GitHub-Repository beispielsweise `edsforms` heißt und sich unter der `wkndforms` befindet, lautet die URL:
   `https://github.com/wkndforms/edsforms`
8. Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![Erstellen eines schemabasierten Formulars](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form.png)

   Wenn Sie auf **[!UICONTROL Erstellen]** klicken, wird das Formular zwecks Erstellung im universellen Editor geöffnet.

   ![Formular erstellen](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

   Das Formular wird mithilfe der Datenelemente aus der zugehörigen Datenquelle erstellt, wobei die Formularfelder eine vorkonfigurierte Datenbindung aufweisen.

   ![Automatische Datenbindung](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

   Sie können jetzt die Übermittlungsaktion für [ Formular hinzufügen ](/help/edge/docs/forms/universal-editor/submit-action.md) konfigurieren .

### Nicht schemabasiertes Formular

Wenn Sie ein nicht schemabasiertes Formular erstellen, wird keine Datenquelle konfiguriert. Sie können die Formulareigenschaften später bearbeiten, um eine Datenquelle hinzuzufügen und Datenbindungen für Ihre Formularfelder manuell zu konfigurieren. Führen Sie die folgenden Schritte aus, um die Formulareigenschaften zu bearbeiten und eine Datenquelle hinzuzufügen:

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Autoreninstanz an. 
1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein. Wenn Sie sich angemeldet haben, wählen Sie in der oberen linken Ecke **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.
1. Wählen Sie das Formular aus, für das Sie eine Datenquelle hinzufügen möchten, und klicken Sie auf **[!UICONTROL Eigenschaften]**.
   ![Formulareigenschaften öffnen](/help/edge/docs/forms/universal-editor/assets/non-schema-based-edit-properties.png)

   Die Formulareigenschaften werden geöffnet.
1. Klicken Sie, um die Registerkarte **Formularmodell** zu öffnen, und wählen Sie **Dropdown-Menü** Auswählen aus“ aus. Sie können eine der folgenden Optionen auswählen:

   * **Formulardatenmodell (FDM)**: Erstellen Sie das Formular mithilfe eines Formulardatenmodells.
   * **Connector**: Erstellen Sie das Formular mithilfe der Adobe Marketo-Datenquelle.
   * **Schema**: Erstellen Sie das Formular mit einem JSON-Schema, das auf AEM Forms hochgeladen wurde.
   * **Keine**: Erstellen Sie das Formular von Grund auf neu, ohne ein Formularmodell zu verwenden.

     Wählen Sie beispielsweise das Formulardatenmodell (FDM)

     ![Registerkarte „Formularmodell auswählen“](/help/edge/docs/forms/universal-editor/assets/select-form-model.png)

1. Wählen Sie das erstellte Formulardatenmodell (FDM) aus der Dropdown-Liste aus. Wählen Sie beispielsweise das erstellte Formulardatenmodell mit dem Namen Haustier-Formulardatenmodell aus der Dropdown-Liste.

   ![FDM auswählen](/help/edge/docs/forms/universal-editor/assets/select-fdm.png)

   Wenn Sie das Formulardatenmodell (FDM) auswählen, wird das Warndialogfeld angezeigt. Klicken Sie **OK**, um das Dialogfeld zu schließen.

   ![Formularmodell-Assistent](/help/edge/docs/forms/universal-editor/assets/form-model-wizard.png)

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.
1. Öffnen Sie das Formular zur Bearbeitung. Das Formular wird im universellen Editor zum Erstellen geöffnet.

   ![Nicht schemabasiertes Formular-Authoring](/help/edge/docs/forms/universal-editor/assets/non-schema-form-authoring.png)

   Die Formularelemente, die im zugehörigen Formulardatenmodell (FDM) vorhanden sind, werden auf der Registerkarte **[!UICONTROL Datenquelle]** des **[!UICONTROL Inhaltsbrowsers]** im **Eigenschaftenbereich** angezeigt.

   ![Form Data Source](/help/edge/docs/forms/universal-editor/assets/non-schema-data-source.png)

1. Wählen Sie die Datenelemente auf der Registerkarte **[!UICONTROL Datenquelle]** aus und klicken Sie auf **[!UICONTROL Hinzufügen]**.

   ![Datenelemente hinzufügen](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-element.png)

   Sie können diese Elemente auch per Drag-and-Drop in das zu erstellende adaptive Formular ziehen. Wenn Sie auf **[!UICONTROL Hinzufügen]** klicken, werden die ausgewählten Elemente auf der Registerkarte **[!UICONTROL Datenquelle]** zu Ihrem Formular hinzugefügt, und vor den hinzugefügten Elementen wird ein Häkchen angezeigt.

   ![Formular erstellen](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png)

   Sie können die Datenbindung auch manuell zu einem Formularelement hinzufügen, indem Sie sie in den **Bindungsverweis**-Eigenschaften des Formularelements angeben.
Fügen wir beispielsweise einen Datenbindungsverweis auf das Textfeld **Haustiername** hinzu, das bereits im Formular vorhanden ist:

   ![Manuelles Hinzufügen der Datensuche für ein Formularfeld](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png)

   Sie können jetzt die Übermittlungsaktion für [ Formular hinzufügen ](/help/edge/docs/forms/universal-editor/submit-action.md) konfigurieren .

## Siehe auch

{{universal-editor-see-also}}
