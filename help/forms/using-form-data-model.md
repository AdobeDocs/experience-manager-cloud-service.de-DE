---
title: Wie können wir ein Formulardatenmodell (FDM) für ein adaptives Formular erstellen?
description: Erfahren Sie, wie Sie adaptive Formulare und adaptive Formularfragmente auf Grundlage eines Formulardatenmodells (FDM) erstellen. Erstellen und bearbeiten Sie Beispieldaten für Datenmodellobjekte im FDM.
feature: Adaptive Forms, Form Data Model
role: Admin, User
level: Beginner, Intermediate
exl-id: 827ce457-6585-46fb-8e28-1d970a40d949
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 59%

---

# Formulardatenmodell (FDM) verwenden {#use-form-data-model}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/using-form-data-model.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |


![data-integration](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] Mit der Datenintegration können Sie unterschiedliche Backend-Datenquellen verwenden, um ein Formulardatenmodell (FDM) zu erstellen, das Sie als Schema in verschiedenen adaptiven Forms verwenden können. <!--and interactive communications--> Workflows. Dazu müssen Datenquellen konfiguriert und Formulardatenmodell (FDM) basierend auf Datenmodellobjekten und Diensten erstellt werden, die in Datenquellen verfügbar sind. Weitere Informationen finden Sie in den folgenden Themen:

* [[!DNL Experience Manager Forms]-Datenintegration](data-integration.md)
* [Konfigurieren von Datenquellen](configure-data-sources.md)
* [Formulardatenmodell (FDM) erstellen](create-form-data-models.md)
* [Arbeiten mit dem Formulardatenmodell (FDM)](work-with-form-data-model.md)

Ein Formulardatenmodell (FDM) ist eine Erweiterung des JSON-Schemas, die Sie für Folgendes verwenden können:

* [Erstellen adaptiver Formulare und Fragmente](#create-af)
  <!--* [Create interactive communications and building blocks like text, list, and condition fragments](#create-ic)-->
* [Vorschau mit Beispieldaten](#preview-ic)
* [den Formulardatenmodell-Service](#prefill)
* [Zurückschreiben von übermittelten adaptiven Formulardaten in Datenquellen](#write-af)
* [Aufrufen von Services über Regeln für adaptive Formulare](#invoke-services)

## Erstellen adaptiver Formulare und Fragmente {#create-af}

Sie können [Adaptives Forms](creating-adaptive-form.md) und adaptive Formularfragmente <!-- [Adaptive Form Fragments](adaptive-form-fragments.md) --> basierend auf einem Formulardatenmodell (FDM). Gehen Sie wie folgt vor, um ein Formulardatenmodell (FDM) beim Erstellen eines adaptiven Formulars oder adaptiven Formularfragments zu verwenden:

1. Wählen Sie auf der Registerkarte „Formularmodell“ im Bildschirm „Eigenschaften hinzufügen“ **[!UICONTROL Formulardatenmodell]** aus der Dropdownliste **[!UICONTROL Auswählen aus]**.

   ![Create-af-1-1](assets/create-af-1-1.png)

2. Wählen Sie zum Erweitern **[!UICONTROL Formulardatenmodell auswählen]** aus. Alle verfügbaren Formulardatenmodelle (FDM) werden aufgelistet.

   Wählen Sie ein Formulardatenmodell aus.

   ![Create-af-2-1](assets/create-af-2-1.png)

3. (**Nur adaptive Formularfragmente**) Sie können ein adaptives Formularfragment erstellen, das auf nur einem Datenmodellobjekt in einem Formulardatenmodell (FDM) basiert. Erweitern Sie die Dropdown-Liste mit den **[!UICONTROL Definitionen für Formulardatenmodelle]**. Es listet alle Datenmodellobjekte im angegebenen Formulardatenmodell (FDM) auf. Wählen Sie ein Datenmodellobjekt aus der Liste aus.

   ![create-af-3](assets/create-af-3.png)

   Nachdem das auf einem Formulardatenmodell (FDM) basierende adaptive Formular- oder Formularfragment erstellt wurde, werden Formulardatenmodellobjekte in der Variablen **[!UICONTROL Data Sources]** Registerkarte des Inhalts-Browsers im Editor für adaptive Formulare.

   >[!NOTE]
   >
   >Für adaptive Formularfragmente werden nur das beim Authoring gewählte Datenmodellobjekt und die mit diesem verknüpften Datenmodellobjekte auf der Registerkarte „Data Sources“ angezeigt.

   ![data-model-object-tab](assets/data-model-objects-tab.png)

   Indem Sie Datenmodellobjekte in das adaptive Formular oder Fragment ziehen und dort ablegen, können Sie Formularfelder hinzufügen. Die hinzugefügten Formularfelder behalten die Metadateneigenschaften und die Bindung mit den Datenmodellobjekteigenschaften bei. Durch die Bindung wird sichergestellt, dass die Feldwerte bei der Formularübermittlung in den entsprechenden Datenquellen aktualisiert und vorausgefüllt werden, wenn das Formular gerendert wird.

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

Mit dem Formulardatenmodell-Editor können Sie Beispieldaten für Datenmodellobjekte im Formulardatenmodell (FDM) generieren und bearbeiten. Sie können diese Daten zur Vorschau und zum Testen adaptiver <!--interactive communications and-->-Formulare verwenden. Sie müssen die Beispieldaten vor der Vorschau generieren, wie beschrieben unter [Arbeiten mit einem Formulardatenmodell](work-with-form-data-model.md#sample).

<!--To preview an interactive communication with sample Form Data Model data:

1. On [!DNL  Experience Manager] author instance, navigate to **[!UICONTROL Forms > Forms & Documents]**.
1. Select an interactive communication and select **[!UICONTROL Preview]** in the toolbar to select **[!UICONTROL Web Channel]**, **[!UICONTROL Print Channel]**, or **[!UICONTROL Both Channels]** to preview the interactive communication.
1. In the Preview [*channel*] dialog, ensure that **[!UICONTROL Test Data of Form Data Model]** is selected and select **[!UICONTROL Preview]**.

The interactive communication opens with prefilled sample data.

![web-preview](assets/web-preview.png)-->

Um ein adaptives Formular mit Beispieldaten in der Vorschau anzuzeigen, öffnen Sie das Formular im Autorenmodus und wählen Sie **[!UICONTROL Vorschau]**.

## Vorbefüllen mit dem Formulardatenmodell-Service {#prefill}

[!DNL Experience Manager Forms] bietet einen vordefinierten Vorbefüllungs-Dienst für Formulardatenmodelle, den Sie für die adaptive Forms aktivieren können <!--and interactive communications--> basierend auf dem Formulardatenmodell (FDM). Der Vorbefüllungs-Service fragt Datenquellen nach Datenmodellobjekten im adaptiven Formular <!--and interactive communication--> ab und befüllt dementsprechend Daten, während das Formular oder die Kommunikation gerendert wird.

Um den Vorbefüllungs-Service für ein adaptives Formular zu aktivieren, öffnen Sie die Eigenschaften des Containers für ein adaptives Formular und wählen Sie **[!UICONTROL Vorbefüllungs-Service für Formulardatenmodell]** aus der Dropdown-Liste **[!UICONTROL Vorbefüllungs-Service]** im Akkordeon „Standard“ aus. Speichern Sie anschließend die Eigenschaften.

![prefill-service](assets/prefill-service.png)

<!--To configure Form Data Model prefill service in an interactive communication, you can select Form Data Model Prefill Service in the Prefill Service drop-down while creating it or later by modifying the properties.

![edit-ic-props](assets/edit-ic-props.png)

Edit Properties dialog for an interactive communication-->

## Schreiben von übermittelten adaptiven Formulardaten in Datenquellen {#write-af}

Wenn ein Benutzer ein Formular sendet, das auf einem Formulardatenmodell (FDM) basiert, können Sie das Formular so konfigurieren, dass gesendete Daten für ein Datenmodellobjekt in dessen Datenquellen geschrieben werden. Um diesen Anwendungsfall zu erreichen, [!DNL Experience Manager Forms] bereitstellen [Übermittlungsaktion für Formulardatenmodell](configuring-submit-actions.md), die standardmäßig nur für adaptive Forms auf der Basis eines Formulardatenmodells (FDM) verfügbar sind. Durch diese Aktion werden übermittelte Daten für ein Datenmodellobjekt in dessen Datenquelle geschrieben.

So konfigurieren Sie die Übermittlungsaktion für das Formulardatenmodell:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Wählen Sie aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** die Option **[!UICONTROL Mit Formulardatenmodell absenden]**.

   ![Aktionskonfiguration](/help/forms/assets/configure-submit-action-invoke-fdm.png)

1. Geben Sie das **[!UICONTROL Datenmodell an, das übermittelt werden soll]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

Beim Senden des Formulars werden die Daten für das konfigurierte Datenmodellobjekt in die entsprechende Datenquelle geschrieben. Darüber hinaus können Sie einen Formularanhang mit einem Formulardatenmodell (FDM) und einem Datensatzdokument (DoR) an die Datenquelle senden. Weitere Informationen zum Formulardatenmodell (FDM) finden Sie unter [[!DNL AEM Forms] Datenintegration](data-integration.md).

<!--![data-submission](assets/data-submission.png)-->

>[!NOTE]
>
> AEM as a Cloud Service bietet verschiedene vordefinierte Übermittlungsaktionen für die Verarbeitung von Formularübermittlungen. Weitere Informationen zu diesen Optionen finden Sie im Artikel [Übermittlungsaktion für adaptive Formulare](/help/forms/configure-submit-actions-core-components.md).

Sie können auch Formularanhänge mit der Objekteigenschaft des binären Datenmodells an eine Datenquelle senden. Führen Sie folgende Schritte aus, um Anlagen an eine JDBC-Datenquelle zu senden:

1. Fügen Sie dem Formulardatenmodell (FDM) ein Datenmodellobjekt hinzu, das eine binäre Eigenschaft enthält.
1. Ziehen Sie im adaptiven Formular die Komponente **[!UICONTROL Dateianhang]** aus dem Komponentenbrowser auf das adaptive Formular.
1. Wählen Sie die hinzugefügte Komponente und wählen Sie dann ![settings_icon](assets/configure-icon.svg), um den Eigenschaften-Browser für die Komponente zu öffnen.
1. Wählen Sie im Feld &quot;Bindungsverweis&quot;die Option ![folderSearch_18](assets/folder-search-icon.svg) und navigieren Sie zu der binären Eigenschaft, die Sie im Formulardatenmodell (FDM) hinzugefügt haben. Konfigurieren Sie weitere Eigenschaften entsprechend.

   Wählen Sie ![check-button](assets/save_icon.svg) aus, um die Eigenschaften zu speichern. Das Anlagenfeld ist jetzt an die binäre Eigenschaft des Formulardatenmodells (FDM) gebunden.

1. Aktivieren Sie im Übermittlungsabschnitt der Eigenschaften des Containers für adaptive Formulare die Option **[!UICONTROL Formularanhänge einreichen]**. Dies sendet den Anhang im Feld der binären Eigenschaft bei der Formularübermittlung an die Datenquelle.

## Aufrufen von Services in adaptiven Formularen mithilfe von Regeln {#invoke-services}

In einem adaptiven Formular, das auf einem Formulardatenmodell (FDM) basiert, können Sie [Regeln erstellen](rule-editor.md) zum Aufrufen von Diensten, die im Formulardatenmodell (FDM) konfiguriert sind. Die **[!UICONTROL Dienste aufrufen]** -Vorgang in einer Regel listet alle verfügbaren Dienste im Formulardatenmodell (FDM) auf und ermöglicht es Ihnen, Eingabe- und Ausgabefelder für den Dienst auszuwählen. Sie können mit dem Regeltyp **[!UICONTROL Wert festlegen]** außerdem einen Formulardatenmodell-Service aufrufen und die vom Service zurückgegebene Ausgabe als Wert eines Feldes einstellen.

Beispielsweise ruft folgende Regel einen Get-Service auf, für den die Mitarbeiter-ID als Eingabe angegeben werden muss und der die entsprechenden Werte in den Feldern für die Angehörigen-ID, den Nachnamen, den Vornamen und das Geschlecht zurückgibt.

![invoke-service](assets/invoke-service.png)

Darüber hinaus können Sie mithilfe der `guidelib.dataIntegrationUtils.executeOperation`-API ein JavaScript im Codeeditor für den Regeleditor schreiben. <!-- For API details, see [API to invoke Form Data Model service](invoke-form-data-model-services.md).-->

### Aufrufen eines Formulardatenmodells (FDM) mithilfe benutzerdefinierter Funktionen {#invoke-form-data-model-using-custom-functions}

Sie können [ein Formulardatenmodell aus dem Regeleditor mithilfe benutzerdefinierter Funktionen aufrufen](/help/forms/rule-editor.md#custom-functions-in-rule-editor-custom-functions). Um das Formulardatenmodell (FDM) aufzurufen, fügen Sie der Zulassungsliste ein Formulardatenmodell hinzu. So fügen Sie ein Formulardatenmodell zu einer Zulassungsliste hinzu:

1. Navigieren Sie zur Experience Manager-Web-Konsole unter `https://server:host/system/console/configMgr`.
1. Suchen Sie das **[!UICONTROL Whitelisting des Formulardatenmodells für den Dienstaufruf auf adaptiver Formularebene – Konfigurations-Factory]**.
1. Klicken Sie auf das ![Plus-Symbol](/help/forms/assets/Smock_Add_18_N.svg), um die Konfiguration hinzuzufügen.
1. Fügen Sie ein **[!UICONTROL Inhaltspfadmuster]** hinzu, um den Speicherort Ihrer adaptiven Formulare anzugeben.  Standardmäßig lautet der Wert `/content/forms/af/(.*)`, was alle adaptiven Formulare umfasst. Sie können auch den Pfad für ein bestimmtes adaptives Formular angeben.
1. Hinzufügen **[!UICONTROL Pfadmuster des Formulardatenmodells]** um den Speicherort des Formulardatenmodells (FDM) anzugeben. Standardmäßig lautet der Wert `/content/dams/formsanddocuments-fdm/(.*)` , das das gesamte Formulardatenmodell (FDM) umfasst. Sie können auch den Pfad für ein bestimmtes Formulardatenmodell (FDM) angeben.
1. Speichern Sie die Einstellungen.

Die hinzugefügte Konfiguration wird unter der Option **[!UICONTROL Whitelisting des Formulardatenmodells für den Dienstaufruf auf adaptiver Formularebene – Konfigurations-Factory]** gespeichert.

>[!VIDEO](https://video.tv.adobe.com/v/3423977/adaptive-forms-custom-function-rule-editor)

>[!NOTE]
>
> So rufen Sie ein Formulardatenmodell (FDM) über ein AEM Archetypprojekt über benutzerdefinierte Funktionen im Regeleditor auf:
>
>1. [Eine Konfigurationsdatei erstellen](https://github.com/adobe/aem-core-forms-components/blob/master/it/config/src/main/content/jcr_root/apps/system/config/com.adobe.aemds.guide.factory.impl.AdaptiveFormFDMConfigurationFactoryImpl~core-components-it.cfg.json).
>1. Legen Sie Eigenschaften von getContentPathPattern und getFormDataModelPathPattern fest.
>1. Stellen Sie das Projekt bereit.

## Ähnliche Artikel

{{af-submit-action}}

