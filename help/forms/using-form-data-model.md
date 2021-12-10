---
title: Verwenden des Formulardatenmodells
description: Erfahren Sie, wie Sie adaptive Formulare und adaptive Formularfragmente auf Grundlage eines Formulardatenmodells erstellen. Finden Sie durch das Erzeugen und Bearbeiten von Beispieldaten für Datenmodellobjekte im Formulardatenmodell mehr heraus. Sie können diese Daten zur Vorschau und zum Testen adaptiver Formulare verwenden.
feature: Form Data Model
role: User
level: Beginner, Intermediate
exl-id: 827ce457-6585-46fb-8e28-1d970a40d949
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1010'
ht-degree: 100%

---

# Verwenden von Formulardatenmodellen {#use-form-data-model}

![data-integration](do-not-localize/data-integeration.png)

Mit der [!DNL Experience Manager Forms]-Datenintegration können Sie unterschiedliche Back-End-Datenquellen verwenden, um ein Formulardatenmodell zu erstellen, das Sie als Schema in verschiedenen Workflows für adaptive Formulare <!--and interactive communications--> verwenden können. Dafür ist das Konfigurieren von Datenquellen und das Erstellen von Formulardatenmodellen erforderlich, basierend auf Datenmodellobjekten sowie Services, die in den Datenquellen verfügbar sind. Weitere Informationen finden Sie in den folgenden Themen:

* [[!DNL Experience Manager Forms]-Datenintegration](data-integration.md)
* [Konfigurieren von Datenquellen](configure-data-sources.md)
* [Erstellen des Formulardatenmodells](create-form-data-models.md)
* [Arbeiten mit einem Formulardatenmodell](work-with-form-data-model.md)

Ein Formulardatenmodell ist eine Erweiterung des JSON-Schemas, die Sie verwenden können für:

* [Erstellen adaptiver Formulare und Fragmente](#create-af)

<!--* [Create interactive communications and building blocks like text, list, and condition fragments](#create-ic)-->
* [Vorschau mit Beispieldaten](#preview-ic)
* [den Formulardatenmodell-Service](#prefill)
* [Zurückschreiben von übermittelten adaptiven Formulardaten in Datenquellen](#write-af)
* [Aufrufen von Services über Regeln für adaptive Formulare](#invoke-services)

## Erstellen adaptiver Formulare und Fragmente {#create-af}

Sie können [adaptive Formulare](creating-adaptive-form.md) und adaptive Formularfragmente<!-- [Adaptive Form Fragments](adaptive-form-fragments.md) --> auf Grundlage eines Formulardatenmodells erstellen. Gehen Sie wie folgt vor, um ein Formulardatenmodell beim Erstellen eines adaptiven Formulars oder eines adaptiven Formularfragments zu verwenden:

1. Wählen Sie auf der Registerkarte „Formularmodell“ im Bildschirm „Eigenschaften hinzufügen“ **[!UICONTROL Formulardatenmodell]** aus der Dropdownliste **[!UICONTROL Auswählen aus]**.

   ![Create-af-1-1](assets/create-af-1-1.png)

1. Tippen Sie auf **[!UICONTROL Formulardatenmodell auswählen]**, um es zu erweitern. Alle verfügbaren Formulardatenmodelle werden aufgelistet.

   Wählen Sie ein Formulardatenmodell aus.

   ![Create-af-2-1](assets/create-af-2-1.png)

1. (**Nur adaptive Formularfragmente**) Sie können ein adaptives Formularfragment auf Grundlage eines einzelnen Datenmodellobjekts in einem Formulardatenmodell erstellen. Erweitern Sie die Dropdownliste **[!UICONTROL Definitionen für Formulardatenmodell]**. Hier sind sämtliche Datenmodellobjekte im angegebenen Formulardatenmodell aufgelistet. Wählen Sie ein Datenmodellobjekt aus der Liste aus.

   ![create-af-3](assets/create-af-3.png)

   Sobald das auf einem Formulardatenmodell basierende adaptive Formular oder Formularfragment erstellt ist, werden Formulardatenmodellobjekte auf der Registerkarte **[!UICONTROL Data Sources]** des Inhaltsbrowsers im Editor für adaptive Formulare angezeigt.

   >[!NOTE]
   >
   >Für adaptive Formularfragmente werden nur das beim Authoring gewählte Datenmodellobjekt und die mit diesem verknüpften Datenmodellobjekte auf der Registerkarte „Data Sources“ angezeigt.

   ![data-model-object-tab](assets/data-model-objects-tab.png)

   Indem Sie Datenmodellobjekte in das adaptive Formular oder Fragment ziehen und dort ablegen, können Sie Formularfelder hinzufügen. Für die hinzugefügten Formularfelder bleiben die Metadateneigenschaften und die Bindung der Datenmodellobjekteigenschaften erhalten. Die Bindung stellt sicher, dass die Feldwerte in den entsprechenden Datenquellen bei der Formularübermittlung aktualisiert und bei der Ausgabe des Formulars vorausgefüllt werden.

<!-- ## Create interactive communications {#create-ic}

You can create an interactive communication based on a Form Data Model that you can use to prefill interactive communication with data from configured data sources. In addition, the building blocks of an interactive communication, such as text, list, and condition document fragments can be based on a form data model.

You can choose a Form Data Model when creating an interactive communication or a document fragment. The following image shows the General tab of the Create Interactive Communication dialog.

![create-ic](assets/create-ic.png)

General tab of Create Interactive Communication dialog

For more information, see:

[Create an interactive communication](create-interactive-communication.md)

[Text in Interactive Communications](texts-interactive-communications.md)

[Conditions in Interactive Communications](conditions-interactive-communications.md)

[List fragments](lists.md) -->

## Vorschau mit Beispieldaten {#preview-ic}

Mit dem Formulardatenmodelleditor können Sie Beispieldaten für Datenmodellobjekte im Formulardatenmodell generieren und bearbeiten. Sie können diese Daten zur Vorschau und zum Testen adaptiver <!--interactive communications and-->-Formulare verwenden. Sie müssen die Beispieldaten vor der Vorschau generieren, wie beschrieben unter [Arbeiten mit einem Formulardatenmodell](work-with-form-data-model.md#sample).

<!--To preview an interactive communication with sample Form Data Model data:

1. On [!DNL  Experience Manager] author instance, navigate to **[!UICONTROL Forms > Forms & Documents]**.
1. Select an interactive communication and tap **[!UICONTROL Preview]** in the toolbar to select **[!UICONTROL Web Channel]**, **[!UICONTROL Print Channel]**, or **[!UICONTROL Both Channels]** to preview the interactive communication.
1. In the Preview [*channel*] dialog, ensure that **[!UICONTROL Test Data of Form Data Model]** is selected and tap **[!UICONTROL Preview]**.

The interactive communication opens with prefilled sample data.

![web-preview](assets/web-preview.png)-->

Um ein adaptives Formular mit Beispieldaten in der Vorschau anzuzeigen, öffnen Sie das Formular im Autorenmodus und tippen Sie auf **[!UICONTROL Vorschau]**.

## Vorbefüllen mit dem Formulardatenmodell-Service {#prefill}

[!DNL Experience Manager Forms] bietet einen standardmäßigen Vorbefüllungs-Service für Formulardatenmodelle, den Sie für adaptive Formulare <!--and interactive communications--> auf Grundlage eines Formulardatenmodells aktivieren können. Der Vorbefüllungs-Service fragt Datenquellen nach Datenmodellobjekten im adaptiven Formular <!--and interactive communication--> ab und befüllt dementsprechend Daten, während das Formular oder die Kommunikation gerendert wird.

Um den Vorbefüllungs-Service für ein adaptives Formular zu aktivieren, öffnen Sie die Eigenschaften des Containers für ein adaptives Formular und wählen Sie **[!UICONTROL Vorbefüllungs-Service für Formulardatenmodell]** aus der Dropdown-Liste **[!UICONTROL Vorbefüllungs-Service]** im Akkordeon „Standard“ aus. Speichern Sie anschließend die Eigenschaften.

![prefill-service](assets/prefill-service.png)

<!--To configure Form Data Model prefill service in an interactive communication, you can select Form Data Model Prefill Service in the Prefill Service drop-down while creating it or later by modifying the properties.

![edit-ic-props](assets/edit-ic-props.png)

Edit Properties dialog for an interactive communication-->

## Schreiben von übermittelten adaptiven Formulardaten in Datenquellen {#write-af}

Sie können ein auf einem Formulardatenmodell basierendes Formular so konfigurieren, dass die vom Benutzer im Formular übermittelten Daten für ein Datenmodellobjekt bei der Übermittlung in dessen Datenquellen geschrieben werden. Zu diesem Zweck stellen [!DNL Experience Manager Forms] die [Übermittlungsaktion für Formulardatenmodelle](configuring-submit-actions.md) zur Verfügung. Standardmäßig ist diese nur für adaptive Formulare verfügbar, die auf einem Formulardatenmodell basieren. Durch diese Aktion werden übermittelte Daten für ein Datenmodellobjekt in dessen Datenquelle geschrieben.

Um die Übermittlungsaktion für Formulardatenmodelle zu konfigurieren, öffnen Sie die Eigenschaften des Container für das adaptive Formular und wählen Sie **[!UICONTROL Mit Formulardatenmodell übermitteln]** aus der Dropdownliste „Übermittlungsaktion“ im Akkordeon „Übermittlung“ aus. Suchen Sie dann das gewünschte Datenmodellobjekt in der Dropdownliste **[!UICONTROL Name des zu übermittelnden Modellobjekts]** und wählen Sie es aus. Speichern Sie die Eigenschaften.

Bei Übermitteln des Formulars werden die Daten für das konfigurierte Datenmodellobjekt in die entsprechende Datenquelle geschrieben.

<!--![data-submission](assets/data-submission.png)-->

Mithilfe der Objekteigenschaft „Binärdatenmodell“ können Sie auch Formularanhänge an eine Datenquelle senden. Gehen Sie wie folgt vor, um Anhänge an eine JDBC-Datenquelle zu senden:

1. Fügen Sie dem Formulardatenmodell ein Datenmodellobjekt hinzu, das eine binäre Eigenschaft enthält.
1. Ziehen Sie im adaptiven Formular die Komponente **[!UICONTROL Dateianhang]** aus dem Komponentenbrowser auf das adaptive Formular.
1. Tippen Sie auf die hinzugefügte Komponente, um sie auszuwählen, und tippen Sie dann auf ![settings_icon](assets/configure-icon.svg), um den Eigenschaftenbrowser für die Komponente zu öffnen.
1. Tippen Sie im Feld „Bindungsverweis“ auf ![foldersearch_18](assets/folder-search-icon.svg), navigieren Sie zur binären Eigenschaft, die Sie im Formulardatenmodell hinzugefügt haben, und wählen Sie sie aus. Konfigurieren Sie weitere Eigenschaften entsprechend.

   Tippen Sie auf ![check-button](assets/save_icon.svg), um die Eigenschaften zu speichern. Damit ist das Anhangsfeld an die binäre Eigenschaft des Formulardatenmodells gebunden.

1. Aktivieren Sie im Abschnitt „Übermittlung“ der Eigenschaften des Containers für das adaptive Formular die Option **[!UICONTROL Formularanhänge einreichen]**. Dadurch wird der Anhang im Feld der binären Eigenschaft bei der Sendung des Formulars an die Datenquelle gesendet.

## Aufrufen von Services in adaptiven Formularen mithilfe von Regeln {#invoke-services}

In einem auf einem Formulardatenmodell basierenden adaptiven Formular können Sie [Regeln erstellen](rule-editor.md), um die im Formulardatenmodell konfigurierten Services aufzurufen. Für den Vorgang **[!UICONTROL Services aufrufen]** werden alle verfügbaren Services im Formulardatenmodell aufgelistet und Sie können die Ein- und Ausgabefelder für den Service auswählen. Sie können mit dem Regeltyp **[!UICONTROL Wert festlegen]** außerdem einen Formulardatenmodell-Service aufrufen und die vom Service zurückgegebene Ausgabe als Wert eines Feldes einstellen.

Beispielsweise ruft folgende Regel einen Get-Service auf, für den die Mitarbeiter-ID als Eingabe angegeben werden muss und der die entsprechenden Werte in den Feldern für die Angehörigen-ID, den Nachnamen, den Vornamen und das Geschlecht zurückgibt.

![invoke-service](assets/invoke-service.png)

Darüber hinaus können Sie mithilfe der `guidelib.dataIntegrationUtils.executeOperation`-API ein JavaScript im Codeeditor für den Regeleditor schreiben. <!-- For API details, see [API to invoke Form Data Model service](invoke-form-data-model-services.md).-->
