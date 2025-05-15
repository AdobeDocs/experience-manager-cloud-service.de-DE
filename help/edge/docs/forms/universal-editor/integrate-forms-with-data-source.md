---
title: Wie lässt sich das Formulardatenmodell (FDM) für ein Formular im universellen Editor integrieren?
description: Erfahren Sie, wie Sie Formulare basierend auf einem Formulardatenmodell (FDM) zu erstellen. Erstellen und bearbeiten Sie Beispieldaten für Datenmodellobjekte im FDM.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
exl-id: 9ce51223-57d0-47d8-8868-84b37d4e8e3e
source-git-commit: 95998daf04ae579ca11896953903852e6140c3a4
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 82%

---

# Integrieren von Formularen mit dem Formulardatenmodell im universellen Editor

Durch das Integrieren von Formularen mit einem Formulardatenmodell (FDM) im universellen Editor können Sie verschiedene Backend-Datenquellen verwenden, um ein Formulardatenmodell (FDM) zu erstellen. Sie können das Formulardatenmodell (FDM) als Schema in verschiedenen Formular-Workflows verwenden. Konfigurieren Sie die Datenquellen und erstellen Sie ein Formulardatenmodell (FDM) basierend auf den Datenmodellobjekten und Diensten, die in den Datenquellen verfügbar sind. 

## Überlegungen

* Wenn das Symbol **Datenquellen** in der Benutzeroberfläche des universellen Editors oder die Eigenschaft **Bindungsverweis** im rechten Eigenschaftenbereich nicht angezeigt wird, aktivieren Sie die Erweiterung **Datenquelle** in der **Extension Manager**.

  ![Erweiterungs-Manager](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

  Informationen zum Aktivieren und Deaktivieren von Erweiterungen im universellen Editor ](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) Sie im Artikel [Extension Manager-Feature-Highlights .

* Der Vorbefüllungsdienst für Formulare im universellen Editor wird derzeit nicht unterstützt.

## Voraussetzungen

Vor dem Konfigurieren des Formulardatenmodells im universellen Editor müssen Sie die folgenden Schritte ausgeführt haben:

* [Konfigurieren der Datenquelle](/help/forms/configure-data-sources.md): Richten Sie die Datenquelle so ein, dass Ihr Formular mit Backend-Daten verbunden wird.
* [Erstellen eines Formulardatenmodells (FDM)](/help/forms/create-form-data-models.md): Erstellen Sie ein Datenmodell mithilfe von Datenobjekten und Diensten aus der konfigurierten Datenquelle.
* [Konfigurieren von Datenmodellobjekten und Diensten](/help/forms/work-with-form-data-model.md): Ordnen Sie die Datenmodellobjekte und Dienste zu, um einen reibungslosen Datenfluss zwischen dem Formular und der Datenquelle sicherzustellen.

## Erstellen von Formularen mit dem Formulardatenmodell im universellen Editor

Im universellen Editor können Sie Folgendes erstellen:

* [Schemabasiertes Formular](#schema-based-form): Ein schemabasiertes Formular verwendet eine Datenquelle, die während der Formularerstellung auf der Registerkarte **Daten** konfiguriert wurde, um Daten automatisch an Formularfelder zu binden.
* [Nicht schemabasiertes Formular](#non-schema-based-form): Bei einem nicht schemabasierten Formular müssen Sie manuell eine Datenquelle hinzufügen und jedes Feld aus der Inhaltsstruktur binden.

![Formulartypen im universellen Editor](/help/edge/docs/forms/universal-editor/assets/form-types.png){width="50%" align="center" height="50%"}

Diese Methoden bieten Ihnen die Flexibilität, Datenmodelle je nach Bedarf mit Formularen zu verbinden.

### Schemabasiertes Formular

Wenn Sie ein schemabasiertes Formular erstellen, wird es automatisch mit einer Datenquelle konfiguriert, wobei die Formularfelder bereits über Datenbindungen mit den Daten verknüpft sind. Um ein schemabasiertes Formular mithilfe des Assistenten für die Formularerstellung zu erstellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Autoreninstanz an.
1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein. Wenn Sie sich angemeldet haben, wählen Sie in der oberen linken Ecke **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.
1. Klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptives Formular]**. Der Assistent wird geöffnet. Wählen Sie auf der Registerkarte **Quelle** eine Vorlage aus:

   ![Vorlage von Edge Delivery Services](/help/edge/assets/create-eds-forms.png)

   Wenn Sie eine auf Edge Delivery Services basierende Vorlage auswählen, ist die Schaltfläche **[!UICONTROL Erstellen]** aktiviert. Sie können die Registerkarte **[!UICONTROL Datenquelle]** oder **[!UICONTROL Übermittlung]** verwenden, um eine Datenquelle oder eine Übermittlungsaktion auszuwählen.

1. Auf der Registerkarte **Daten** können Sie eines der folgenden Datenmodelle auswählen:

   * **Formulardatenmodell (FDM)**: Zum Integrieren von Datenmodellobjekten und Diensten aus Datenquellen in Ihr Formular. Wählen Sie „Formulardatenmodell (FDM)“, wenn Ihr Formular das Lesen und Schreiben von Daten aus mehreren Quellen erfordert.

   * **JSON-Schema**: Zum Integrieren Ihres Formulars in ein Backend-System, indem Sie ein JSON-Schema verknüpfen, das die Datenstruktur definiert. Damit können Sie dynamische Inhalte mithilfe der Schemaelemente hinzufügen.

     Wählen Sie beispielsweise das erstellte Formulardatenmodell mit dem Namen „Haustier-Formulardatenmodell“ aus.

     ![Auswählen des Formulardatenmodells](/help/edge/docs/forms/universal-editor/assets/select-petstore-form-data-model.png)


     Standardmäßig werden alle Felder des zugehörigen JSON-Schemas oder Formdatenmodells (FDM) automatisch ausgewählt und in entsprechende Formularkomponenten konvertiert, was den Erstellungsprozess vereinfacht. Im Assistenten können Sie mithilfe von Kontrollkästchen auch selektiv auswählen, welche Felder in das Formular aufgenommen werden sollen.

1. Klicken Sie auf **[!UICONTROL Erstellen]**. Daraufhin wird der Assistent **Formular erstellen** angezeigt.
1. Geben Sie den **Namen** und den **Titel** an.
1. Geben Sie die **GitHub-URL** an. Wenn Ihr GitHub-Repository beispielsweise `edsforms` heißt und sich unter dem Konto `wkndforms` befindet, lautet die URL wie folgt:
   `https://github.com/wkndforms/edsforms`
1. Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![Erstellen eines schemabasierten Formulars](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form.png)

   Wenn Sie auf **[!UICONTROL Erstellen]** klicken, wird das Formular zwecks Erstellung im universellen Editor geöffnet.

   ![Erstellen des Formulars](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

   Das Formular wird mithilfe der Datenelemente aus der zugehörigen Datenquelle erstellt, wobei die Formularfelder eine vorkonfigurierte Datenbindung aufweisen.

   ![Automatische Datenbindung](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

   Sie können jetzt die [Übermittlungsaktion](/help/edge/docs/forms/universal-editor/submit-action.md) für Ihr Formular hinzufügen und konfigurieren.

### Nicht schemabasiertes Formular

Wenn Sie ein nicht schemabasiertes Formular erstellen, wird keine Datenquelle konfiguriert. Sie können die Formulareigenschaften später bearbeiten, um eine Datenquelle hinzuzufügen und Datenbindungen für Ihre Formularfelder manuell zu konfigurieren. Führen Sie die folgenden Schritte aus, um die Formulareigenschaften zu bearbeiten und eine Datenquelle hinzuzufügen:

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Autoreninstanz an.
1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein. Wenn Sie sich angemeldet haben, wählen Sie in der oberen linken Ecke **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.
1. Wählen Sie das Formular aus, dem Sie eine Datenquelle hinzufügen möchten, und klicken Sie auf **[!UICONTROL Eigenschaften]**.
   ![Öffnen der Formulareigenschaften](/help/edge/docs/forms/universal-editor/assets/non-schema-based-edit-properties.png)

   Die Formulareigenschaften werden geöffnet.
1. Klicken Sie, um die Registerkarte **Formularmodell** zu öffnen, und wählen Sie aus dem Dropdown-Menü **Auswählen aus** das Passende aus. Sie können eine der folgenden Optionen auswählen:

   * **Formulardatenmodell (FDM)**: Zum Erstellen des Formulars mit einem Formulardatenmodell.
   * **Connector**: Zum Erstellen des Formulars mit der Adobe Marketo-Datenquelle.
   * **Schema**: Zum Erstellen des Formulars mit einem JSON-Schema, das auf AEM Forms hochgeladen wurde.
   * **Keine**: Zum Erstellen des Formulars von Grund auf ohne Formularmodell.

     Wählen Sie beispielsweise das Formulardatenmodell (FDM) aus

     ![Registerkarte „Formularmodell auswählen“](/help/edge/docs/forms/universal-editor/assets/select-form-model.png)

1. Wählen Sie das erstellte Formulardatenmodell (FDM) aus der Dropdown-Liste aus. Wählen Sie beispielsweise das erstellte Formulardatenmodell mit dem Namen „Haustier-Formulardatenmodell“ aus der Dropdown-Liste aus.

   ![Auswählen des FDM](/help/edge/docs/forms/universal-editor/assets/select-fdm.png)

   Wenn Sie das Formulardatenmodell (FDM) auswählen, wird das Warndialogfeld angezeigt. Klicken Sie auf **OK**, um das Dialogfeld zu schließen.

   ![Assistent für das Formularmodell](/help/edge/docs/forms/universal-editor/assets/form-model-wizard.png)

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.
1. Öffnen Sie Ihr Formular zum Bearbeiten. Das Formular wird im universellen Editor zum Erstellen geöffnet.

   ![Erstellen nicht schemabasierter Formulare](/help/edge/docs/forms/universal-editor/assets/non-schema-form-authoring.png)

   Die Formularelemente, die im zugehörigen Formulardatenmodell (FDM) vorhanden sind, werden auf der Registerkarte **[!UICONTROL Datenquelle]** des **[!UICONTROL Inhalts-Browsers]** im **Bedienfeld „Eigenschaften“** angezeigt.

   ![Formulardatenquelle](/help/edge/docs/forms/universal-editor/assets/non-schema-data-source.png)

1. Wählen Sie die Datenelemente auf der Registerkarte **[!UICONTROL Datenquelle]** aus und klicken Sie auf **[!UICONTROL Hinzufügen]**.

   ![Hinzufügen von Datenelementen](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-element.png)

   Sie können diese Elemente auch per Drag-and-Drop in das zu erstellende adaptive Formular ziehen. Wenn Sie auf **[!UICONTROL Hinzufügen]** klicken, werden die ausgewählten Elemente auf der Registerkarte **[!UICONTROL Datenquelle]** zu Ihrem Formular hinzugefügt, und vor den hinzugefügten Elementen wird ein Häkchen angezeigt.

   ![Erstellen eines Formulars](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png)

Sie können einem Formularfeld Datenbindung hinzufügen, indem Sie es aus der Eigenschaft &quot;**&quot;**. Fügen wir beispielsweise einen Datenbindungsverweis auf das Textfeld **id** hinzu, das bereits im Formular vorhanden ist.
Um die Datenbindung für das Formularfeld aus der Datenquellenstruktur auszuwählen, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die Eigenschaften des Formularfelds, für das Sie den Datenbindungsverweis hinzufügen möchten.
1. Wechseln Sie zur Eigenschaft **Bindungsverweis** und klicken Sie auf das Symbol **Durchsuchen**.

   ![Manuelles Hinzufügen der Datenbindung für ein Formularfeld](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png)

1. Wählen Sie die Datenbindungsreferenz aus der Datenquellenstruktur im **Bindungsverweis auswählen** .

   ![Datenbindungsverweis auswählen](/help/edge/docs/forms/universal-editor/assets/select-bind-reference.png)

1. Wählen Sie das Datenelement in der Datenquellenstruktur aus, das Sie an das Formularfeld binden möchten, und klicken Sie auf **Auswählen**.

   ![Datenelement auswählen](/help/edge/docs/forms/universal-editor/assets/select-data-element.png)

   Das Formularfeld wird an das Datenelement gebunden und in der Eigenschaft &quot;**&quot;**.

   ![Automatische Datenbindung](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

   Sie können die Eigenschaft **Bindungsverweis** für das Formularfeld auch manuell bearbeiten.

Sie können jetzt die [Übermittlungsaktion](/help/edge/docs/forms/universal-editor/submit-action.md) für Ihr Formular hinzufügen und konfigurieren.

## Siehe auch

{{universal-editor-see-also}}
