---
title: Erstellen eines adaptiven Formulars
description: Erfahren Sie, wie Sie ein adaptives Formular mit  [!DNL Experience Manager Forms] erstellen können. Adaptive Formulare sind responsive HTML5-Formulare, mit denen die Informationserfassung und -verarbeitung optimiert wird. Vertiefen Sie Ihre Kenntnisse über die Erstellung adaptiver Formulare auf der Grundlage eines Formulardatenmodells und eines XML- oder JSON-Schemas.
feature: Adaptive Forms
role: User, Developer
level: Beginner
exl-id: 38ca5eea-793b-420b-ae60-3a0bd83caf00
source-git-commit: 434071de17d6ff56ede561735f7214d96f98cfa0
workflow-type: tm+mt
source-wordcount: '1359'
ht-degree: 27%

---

# Erstellen eines adaptiven Formulars {#creating-an-adaptive-form}


Adaptive Formulare bieten Ihnen die Möglichkeit, interaktive, responsive und dynamische adaptive Formulare zu erstellen. AEM Forms bietet einen benutzerfreundlichen Assistenten für Unternehmen, mit dem sich Adaptive Forms schnell erstellen lässt. Der Assistent verfügt über eine schnelle Registerkartennavigation, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen.

<!-- 

You can choose to create an Adaptive Form based on a form model or schema or without a form model. It is important to carefully choose the form model that not only suits your requirements but extends your existing infrastructural investments and assets. You get to choose from the following options to create an Adaptive Form: 

-->

![Assistent zum Erstellen eines adaptiven Formulars](/help/release-notes/assets/wizard.png)

<!-- 

Adaptive Forms allow you to create forms that are engaging, responsive, dynamic, and adaptive. [!DNL AEM Forms] provides an intuitive wizard and out-of-the-box components to create Adaptive Forms. You can choose to create an Adaptive Form based on a form model or schema or without a form model. It is important to carefully choose the form model that not only suits your requirements but extends your existing infrastructural investments and assets. You get to choose from the following options to create an Adaptive Form:

* **Using a form data model**
  [Data integration](data-integration.md) lets you integrate entities and services from disparate data sources in to a Form Data Model that you can use to create Adaptive Forms. Choose Form Data Model if the Adaptive Form you are creating involves fetching and write data from and to multiple data source.

  <!--  * **Using an XDP Form Template**
   It is an ideal form model if you have investments in XFA-based or XDP forms. It provides a direct way to convert your XFA-based forms into Adaptive Forms. Any existing XFA rules are retained in the associated Adaptive Forms. The resulting Adaptive Forms support XFA constructs, such as validations, events, properties, and patterns. 

* **Using an XML Schema Definition (XSD) or a JSON Schema**
   XML and JSON schemas represent the structure in which data is produced or consumed by the back-end system in your organization. You can associate the schema to an Adaptive Form and use its elements to add dynamic content to the Adaptive Form. The elements of the schema will be available for use in the Data Model Objects tab of the Content browser when authoring Adaptive Forms.

* **Using none or without a form model**
   Adaptive Forms created with this option don’t use any form model. The data XML generated from such forms has flat structure with fields and corresponding values. -->

## Voraussetzungen

Zum Erstellen eines adaptiven Formulars benötigen Sie Folgendes:

* **Eine Vorlage für ein adaptives Formular**: Eine Vorlage bietet eine grundlegende Struktur und definiert das Erscheinungsbild (Layouts und Stile) eines adaptiven Formulars. Sie enthält vorformatierte Komponenten einschließlich bestimmter Eigenschaften und einer Struktur für Inhalte. Es bietet außerdem die Optionen zum Definieren eines Designs und einer Übermittlungsaktion. Das Design definiert das Erscheinungsbild und die Übermittlungsaktion definiert die Aktion, die bei der Übermittlung eines adaptiven Formulars ausgeführt werden soll. Senden der erfassten Daten an eine Datenquelle. Der Cloud-Dienst unterstützt zwei Arten von Vorlagen:

   * **Bearbeitbare Vorlage**: Sie können [eine neue](template-editor.md) oder [eine vorhandene bearbeitbare Vorlage importieren](migrate-to-forms-as-a-cloud-service.md). Sie können auch die [neuester Archetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#:~:text=The%20AEM%20Archetype%20is%20made%20up%20of%20modules%3A,and%20request%20filters.%20it.tests%3A%20are%20Java-basierte%20integration%20tests.) um einige bearbeitbare Beispielvorlagen zu erhalten.
   * **Statische Vorlage**: Hierbei handelt es sich um veraltete Vorlagen, die nur für Kunden empfohlen werden, die von Adobe Managed Services (AMS)- und On-Premise-AEM Forms-Installationen (AEM 6.5 Forms oder früher) migrieren. Damit können Sie Ihre bereits getätigten Investitionen in statische Vorlagen weiter nutzen. Wenn Sie ein neues adaptives Formular erstellen, wird empfohlen, eine bearbeitbare Vorlage zu verwenden.

* **Thema für adaptives Formular**: Ein Design enthält Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider. Sie können [Erstellen eines neuen Designs](themes.md) oder [ein vorhandenes Design importieren](import-export-forms-templates.md#uploading-a-theme). Sie können auch die [neuester Archetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html#create-project) für einige Beispielthemen.

* **Berechtigungen**: Benutzer hinzufügen zu [!DNL forms-users] , um ihnen Berechtigungen zum Erstellen eines adaptiven Formulars zu erteilen. Eine detaillierte Liste der formularspezifischen Benutzergruppen finden Sie unter [Gruppen und Berechtigungen](forms-groups-privileges-tasks.md).

1. Öffnen Sie die [!DNL Experience Manager Forms]-Autoreninstanz. Dabei kann es sich um eine Cloud-Instanz oder eine lokale Entwicklungsinstanz handeln.

1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein.

   Wenn Sie sich angemeldet haben, tippen Sie in der oberen linken Ecke auf **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.

1. Tippen **[!UICONTROL Erstellen]**  > **[!UICONTROL Adaptives Forms]**. Der Assistent wird geöffnet.
1. Wählen Sie im Tab Quelle eine Vorlage aus:

   * Wenn Sie eine bearbeitbare Vorlage auswählen, werden ein Design und eine Sendeaktion, die in der Vorlage angegeben sind, automatisch ausgewählt und die **[!UICONTROL Erstellen]** -Schaltfläche aktiviert ist. Sie können zum **[!UICONTROL Stil]** oder **[!UICONTROL Einsendung]** Registerkarten zur Auswahl eines anderen Designs oder einer anderen Übermittlungsaktion. Wenn in der ausgewählten bearbeitbaren Vorlage kein Design angegeben wird, bleibt die Schaltfläche &quot;Erstellen&quot;deaktiviert. Sie können zum **[!UICONTROL Stile]** Registerkarte, um ein Design manuell auszuwählen.

      >[!NOTE]
      >
      > Sie können auch [!UICONTROL Datensatzdokument] Vorlage mit einem Editor für adaptive Formulare verwenden. Weitere Informationen finden Sie unter [Unterstützung von Datensatzdokumenten im Editor für adaptive Formulare](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform).

   * Wenn Sie eine statische Vorlage auswählen, sind die Optionen für Daten, Stil, Übermittlung, Bereitstellung und Vorschau nicht verfügbar. Wenn Sie ein neues adaptives Formular erstellen, wird empfohlen, eine bearbeitbare Vorlage zu verwenden.

1. Wählen Sie auf der Registerkarte Stil ein Design aus:
   * Wenn die ausgewählte Vorlage ein Design angibt, wird das Design automatisch im Assistenten ausgewählt. Sie können auch auf der Registerkarte Stil ein anderes Design auswählen.
   * Wenn in der ausgewählten Vorlage kein Design angegeben ist, können Sie auf der Registerkarte Stil ein Design auswählen. Die **[!UICONTROL Erstellen]** -Schaltfläche nur aktiviert ist, nachdem ein Design ausgewählt wurde.
1. (Optional) Wählen Sie auf der Registerkarte &quot;Daten&quot;ein Datenmodell aus:
   * **Formulardatenmodell**: A [Formulardatenmodell](data-integration.md) ermöglicht Ihnen die Integration von Entitäten und Diensten aus unterschiedlichen Datenquellen in ein adaptives Formular. Wählen Sie das Formulardatenmodell aus, wenn das adaptive Formular, das Sie erstellen, das Abrufen und Schreiben von Daten aus und in mehrere Datenquellen umfasst.
   * **JSON-Schema**: [JSON-Schema](adaptive-form-json-schema-form-model.md) stellt die Struktur dar, in der Daten vom Back-End-System in Ihrem Unternehmen produziert oder genutzt werden. Sie können das Schema mit einem adaptiven Formular verknüpfen und dem Formular mithilfe der Elemente dieses Schemas dynamische Inhalte hinzufügen. Die Schemaelemente stehen beim Erstellen von Adaptive Forms auf der Registerkarte Datenmodellobjekte des Inhaltsbrowsers zur Verfügung und alle Felder werden auch zum neu erstellten adaptiven Formular hinzugefügt.

   Standardmäßig sind alle Felder des Datenmodells ausgewählt. Wenn Sie das adaptive Formular erstellen, werden alle ausgewählten Datenmodellfelder in entsprechende adaptive Formularkomponenten konvertiert. Mit den Kontrollkästchen des Assistenten können Sie nur die Felder auswählen, die im adaptiven Formular enthalten sein sollen.

   <!-- 
   
   If your JSON schema contains a fragment, the fragment is considered a single unit. You can select or deselect a complete fragment and all the fields of the fragment are selected or deselected accordingly. 
   
   -->

1. Wählen Sie im Tab Übermittlung eine Übermittlungsaktion aus:

   * Wenn Sie eine Vorlage auswählen, wird die in der Vorlage angegebene Sendeaktion automatisch ausgewählt. Sie können im Tab Übermittlung eine andere Sendeaktion auswählen. Die **[!UICONTROL Einsendung]** zeigt alle verfügbaren Sendeaktionen an.

   * Wenn die ausgewählte Vorlage keine Sendeaktion angibt, können Sie die **[!UICONTROL Einsendung]** Registerkarte zur Auswahl einer Sendeaktion

1. (Optional) Auf der Registerkarte Versand können Sie ein Veröffentlichungs- oder Veröffentlichungsdatum für ein adaptives Formular angeben.

1. Tippen Sie auf **[!UICONTROL Erstellen]**. Ein Dialogfeld zum Angeben von Titel, Name und Speicherort für das adaptive Formular wird angezeigt:

   * **[!UICONTROL Titel]** Gibt den Anzeigenamen des Formulars an. Der Titel erleichtert Ihnen die Identifizierung des Formulars in der Benutzeroberfläche von [!DNL Experience Manager Forms].
   * **[!UICONTROL Name:]** Gibt den Namen des Formulars an. Im Repository wird ein Knoten mit dem angegebenen Namen erstellt. Wenn Sie mit der Eingabe des Titels beginnen, wird automatisch ein Wert für das Feld „Name“ vorgeschlagen. Sie können den vorgeschlagenen Wert gegebenenfalls ändern. Im Feld „Name“ dürfen nur alphanumerische Zeichen, Bindestriche und Unterstriche eingegeben werden. Ungültige Eingaben werden durch Bindestriche ersetzt.
   * **[!UICONTROL Pfad:]** Gibt den Speicherort an, an dem das adaptive Formular gespeichert werden soll. Sie können das adaptive Formular direkt unter `/content/dam/formsanddocuments` oder erstellen Sie einen Ordner wie `/content/dam/formsanddocuments/adaptiveforms` , um ein adaptives Formular zu speichern. Stellen Sie sicher, dass Sie den Ordner erstellen, bevor Sie ihn im Pfad verwenden. Die **[!UICONTROL Pfad:]** -Feld erstellt keinen Ordner automatisch.

1. Tippen Sie auf **[!UICONTROL Erstellen]**. Ein adaptives Formular wird erstellt und im adaptiven Forms-Editor geöffnet. Der Editor zeigt die in der Vorlage verfügbaren Inhalte an. Es zeigt auch die Seitenleiste an, um das neu erstellte Formular entsprechend den Anforderungen anzupassen.

   Basierend auf dem Typ des adaptiven Formulars sind die Formularelemente im zugehörigen <!--XFA form template, XML schema or --> Das JSON-Schema oder das Formulardatenmodell wird im **[!UICONTROL Datenmodellobjekte]** des **[!UICONTROL Inhaltsbrowser]** in der Seitenleiste. Sie können diese Elemente auch in das zu erstellende adaptive Formular ziehen.

<!-- ## Create an Adaptive Form based on a Form Data Model {#fdm}

[Data integration](data-integration.md) lets you integrate multiple data sources and bring their entities and services together to create a form data model. It is an extension of JSON schema. You can use a Form Data Model to create an Adaptive Form. The entities or data model objects configured in a Form Data Model are available as data model objects for form authoring. They are bound to respective data sources and used to prefill a form and write submitted data back to the respective data sources. You can also call services configured in a Form Data Model using Adaptive Form rules.

To use a Form Data Model for creating an Adaptive Form:

1. In Form Model tab on Add Properties screen, select **[!UICONTROL Form Data Model]** in the **[!UICONTROL Select From]** drop-down list.

   ![Create an Adaptive Form](assets/create-af-1-1.png)

1. Tap to expand **[!UICONTROL Select Form Data Model]**. All available form data models are listed.Select a from data model.

>[!NOTE]
>
>You can also change the Form Data Model for an Adaptive Form. For detailed steps, see [Edit Form Model properties of an Adaptive Form](#edit-form-model).

## Create an Adaptive Form based on XML or JSON schema {#create-an-adaptive-form-based-on-xml-or-json-schema}

XML and JSON schemas represent the structure in which data is produced or consumed by the back-end system in your organization. You can associate a schema to an Adaptive Form and use its elements to add dynamic content to the Adaptive Form. The elements of the schema are available in the Data Model Object tab of the content browser for authoring Adaptive Forms. You can drag-drop the schema elements to build the form.

See the following documents to understand how to design XML or JSON schema for authoring Adaptive Forms.

* [Creating Adaptive Forms using XML schema](adaptive-form-xml-schema-form-model.md)
* [Creating Adaptive Forms using JSON schema](adaptive-form-json-schema-form-model.md)

Do the following to use XML or JSON schema as form model for an Adaptive Form:

1. On the **[!UICONTROL Add Properties]** step of Adaptive Form creation page, tap on the **[!UICONTROL Form Model]** tab.
1. In the Form Model tab, select **[!UICONTROL Schema]** from the **[!UICONTROL Select From]** drop-down field.

1. Tap **[!UICONTROL Select Schema]** and do one of the following:

    * **[!UICONTROL Upload from disk]** - Select this option and tap Upload Schema Definition to browse and upload an XML schema or JSON schema from your file system. The uploaded schema file resides with the form and is not accessible to other Adaptive Forms.
    * **[!UICONTROL Search in repository]** - Select this option to select from the list of schema definition files available in the repository. Select the XML or JSON schema file as form model. The selected schema is associated with the form by reference and is accessible for use in other Adaptive Forms.

      Ensure that the JSON schema filename ends with **.schema.json**. For example: mySchema.schema.json

   ![Selecting XML or JSON schema](assets/upload-schema.png)
**Figure:** *Selecting XML or JSON schema*

1. (For XML schema only) After you select or upload an XML Schema, specify a root element of the selected XSD file to map with the Adaptive Form.

   ![Selecting XSD root element](assets/xsd-root-element.png)
**Figure:** *Selecting XSD root element*

>[!NOTE]
>
>You can also change the schema for an Adaptive Form. For detailed steps, see [Edit Form Model properties of an Adaptive Form](#edit-form-model). -->

## Bearbeiten der Formularmodelleigenschaften eines adaptiven Formulars {#edit-form-model}

Sie können das Formularmodell für ein adaptives Formular (JSON-basiertes oder Formulardatenmodell) ändern. Sie können nicht von einem Formularmodell zum anderen wechseln.

1. Wählen Sie das adaptive Formular aus und tippen Sie auf das Symbol **Eigenschaften**.
1. Öffnen Sie die Registerkarte **[!UICONTROL Formularmodell]** und wählen Sie eine der folgenden Vorgehensweisen.

   * Wenn das adaptive Formular nicht auf einem Formularmodell basiert, können Sie ein Formularmodell und ein entsprechendes XML- oder JSON-Schema oder ein Formulardatenmodell auswählen.<!-- a form template, -->
   * Bei einem adaptiven Formular, das auf einem Formularmodell basiert, können Sie ein anderes <!-- form template, --> XML-Schema, JSON-Schema oder Formulardatenmodell für dasselbe Formularmodell wählen.

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Eigenschaften zu speichern.

Sie können die Eigenschaften des Formularmodells auch im Vorlagen-Editor für adaptive Formulare oder adaptive Formulare ändern.

1. Wählen Sie die **[!UICONTROL Container für adaptive Formulare (Stamm)]** -Komponente.
1. Klicken ![Symbol &quot;Konfigurieren&quot;](/help/forms/assets/configure-icon.svg) Symbol zum Öffnen **[!UICONTROL Eigenschaften]** des Containers für adaptive Formulare.
1. Wählen Sie die **[!UICONTROL Datenmodell]** und führen Sie einen der folgenden Schritte aus:

   * Wenn das adaptive Formular ohne Formularmodell ist, können Sie ein Formularmodell auswählen und dementsprechend <!-- a form template, --> XML- oder JSON-Schema oder Formulardatenmodell.
   * Wenn das adaptive Formular auf einem Formularmodell basiert, können Sie das Formularmodell nicht ändern. Sie können eine andere <!-- form template, --> XML- oder JSON-Schema oder Formulardatenmodell für dasselbe Formularmodell.
1. Tippen Sie auf ![Speichern](/help/forms/assets/check-button.png), um die Eigenschaften zu speichern.

![FDM-Schema-support](/help/forms/assets/fdmsupport.png)
