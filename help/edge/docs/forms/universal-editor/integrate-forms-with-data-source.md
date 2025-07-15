---
title: Wie lässt sich das Formulardatenmodell (FDM) für ein Formular im universellen Editor integrieren?
description: Erfahren Sie, wie Sie Formulare basierend auf einem Formulardatenmodell (FDM) zu erstellen. Erstellen und bearbeiten Sie Beispieldaten für Datenmodellobjekte im FDM.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
exl-id: 9ce51223-57d0-47d8-8868-84b37d4e8e3e
source-git-commit: e1ead9342fadbdf82815f082d7194c9cdf6d799d
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 94%

---

# Integrieren von Formularen mit dem Formulardatenmodell im universellen Editor

Durch das Integrieren von Formularen mit einem Formulardatenmodell (FDM) im universellen Editor können Sie verschiedene Backend-Datenquellen verwenden, um ein Formulardatenmodell (FDM) zu erstellen. Sie können das Formulardatenmodell (FDM) als Schema in verschiedenen Formular-Workflows verwenden. Konfigurieren Sie die Datenquellen und erstellen Sie ein Formulardatenmodell (FDM) basierend auf den Datenmodellobjekten und Diensten, die in den Datenquellen verfügbar sind. 

## Überlegungen

* Wenn das Symbol **Datenquellen** in der Benutzeroberfläche des universellen Editors oder die Eigenschaft **Bindungsverweis** im Panel „Eigenschaften“ auf der rechten Seite nicht angezeigt wird, aktivieren Sie die Erweiterung **Datenquelle** im **Extension Manager**.

  ![Screenshot der Extension Manager-Benutzeroberfläche des universellen Editors mit den verfügbaren Erweiterungen, einschließlich der Datenquellenerweiterung, die für die Formularintegration aktiviert werden kann](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

  Informationen zum Aktivieren und Deaktivieren von Erweiterungen im universellen Editor finden Sie im Artikel [Extension Manager – Highlights der Funktionen](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

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

   ![Screenshot des universellen Editors, der ein schemabasiertes Formular mit vorausgefüllten Formularfeldern und den Inhaltsbrowser mit verfügbaren Datenquellenelementen zeigt](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

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

   ![Screenshot, der den universellen Editor mit einem Nicht-Schemaformular zeigt, das durch Ziehen und Ablegen von Datenelementen von der Registerkarte „Data Source&quot; in die Formularstruktur erstellt wird](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png)

Sie können die Datenbindung in einem Formularfeld hinzufügen, indem Sie sie über die Eigenschaft **Bindungsverweis** auswählen. Fügen wir beispielsweise einen Datenbindungsverweis zum Textfeld **ID** hinzu, das bereits im Formular vorhanden ist.
Führen Sie die folgenden Schritte aus, um die Datenbindung für das Formularfeld über die Datenquellstruktur auszuwählen:

1. Öffnen Sie die Eigenschaften des Formularfelds, für das Sie den Datenbindungsverweis hinzufügen möchten.
1. Navigieren Sie zur Eigenschaft **Bindungsverweis** und klicken Sie auf das Symbol **Durchsuchen**.

   ![Manuelles Hinzufügen der Datenbindung für ein Formularfeld](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png)

1. Wählen Sie den Datenbindungsverweis aus der Datenquellenstruktur im Assistenten **Bindungsverweis auswählen** aus.

   ![Auswählen des Datenbindungsverweises](/help/edge/docs/forms/universal-editor/assets/select-bind-reference.png)

1. Wählen Sie das Datenelement in der Datenquellenstruktur aus, das Sie an das Formularfeld binden möchten, und klicken Sie auf **Auswählen**.

   ![Auswählen des Datenelements](/help/edge/docs/forms/universal-editor/assets/select-data-element.png)

   Das Formularfeld wird an das Datenelement gebunden und in der Eigenschaft **Bindungsverweis** angezeigt.

   ![Automatische Datenbindung](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

   Sie können die Eigenschaft **Bindungsverweis** für das Formularfeld auch manuell bearbeiten.

Sie können jetzt die [Übermittlungsaktion](/help/edge/docs/forms/universal-editor/submit-action.md) für Ihr Formular hinzufügen und konfigurieren.

## Siehe auch

{{universal-editor-see-also}}
