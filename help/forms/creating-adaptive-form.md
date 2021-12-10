---
title: Erstellen eines adaptiven Formulars
description: 'Erfahren Sie, wie Sie ein adaptives Formular mit  [!DNL Experience Manager Forms] erstellen können. Adaptive Formulare sind responsive HTML5-Formulare, mit denen die Informationserfassung und -verarbeitung optimiert wird. Vertiefen Sie Ihre Kenntnisse über die Erstellung adaptiver Formulare auf der Grundlage eines Formulardatenmodells und eines XML- oder JSON-Schemas. '
feature: Adaptive Forms
role: User, Developer
level: Beginner
exl-id: 38ca5eea-793b-420b-ae60-3a0bd83caf00
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1500'
ht-degree: 100%

---

# Erstellen eines adaptiven Formulars {#creating-an-adaptive-form}

Adaptive Formulare bieten Ihnen die Möglichkeit, interaktive, responsive und dynamische adaptive Formulare zu erstellen. [!DNL AEM Forms] bietet eine intuitive Benutzeroberfläche sowie vordefinierte Komponenten zum Erstellen und Verarbeiten von adaptiven Formularen. Sie können adaptive Formulare auf der Basis eines Formularmodells oder Schemas oder ohne Formularmodell erstellen. Es ist wichtig, sorgfältig ein Formularmodell zu wählen, das nicht nur Ihren Verwendungszwecken entspricht, sondern auch Ihre bestehenden Infrastrukturinvestitionen und -Assets erweitert. Zum Erstellen eines adaptiven Formulars werden die folgenden Optionen bereitgestellt:

* **Verwendung eines Formulardatenmodell**
   [Datenintegration](data-integration.md) ermöglicht die Integration von Entitäten und Services aus unterschiedlichen Datenquellen in ein Formulardatenmodell, das Sie zum Erstellen adaptiver Formulare verwenden können. Wählen Sie das Formulardatenmodell, wenn Sie ein adaptives Formular erstellen, für das Daten aus mehreren Datenquellen abgerufen und in sie geschrieben werden sollen.

   <!--  * **Using an XDP Form Template**
   It is an ideal form model if you have investments in XFA-based or XDP forms. It provides a direct way to convert your XFA-based forms into Adaptive Forms. Any existing XFA rules are retained in the associated Adaptive Forms. The resulting Adaptive Forms support XFA constructs, such as validations, events, properties, and patterns. -->

* **Verwendung einer XML-Schemadefinition (XSD) oder eines JSON-Schemas** XML- und JSON-Schemas stellen die Struktur dar, in der Daten vom Back-End-System in Ihrem Unternehmen produziert oder genutzt werden. Sie können das Schema mit einem adaptiven Formular verknüpfen und dem Formular mithilfe der Elemente dieses Schemas dynamische Inhalte hinzufügen. Bei der Erstellung adaptiver Formulare sind die Elemente des Schemas für die Verwendung auf der Registerkarte „Datenmodellobjekte“ des Content-Browsers verfügbar.

* **Keines verwenden oder ohne Formularmodell** Bei dieser Option wird kein Formularmodell für die Erstellung adaptiver Formulare verwendet. Die XML-Datendatei, die aus diesen Formularen generiert wird, hat eine flache Struktur mit Feldern und entsprechenden Werten.

## Voraussetzungen

Zum Erstellen eines adaptiven Formulars benötigen Sie Folgendes:

* Eine Vorlage für ein adaptives Formular. Eine Vorlage liefert die Grundstruktur für ein adaptives Formular und definiert dessen Erscheinungsbild (Layouts und Stile). Es bietet vorformatierte Komponenten, die bestimmte Eigenschaften und Inhaltsstrukturen beinhalten. Sie können [eine neue Vorlage erstellen](template-editor.md), eine vorhandene Vorlage importieren oder [Beispielvorlagen](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:3f89abe1-0ece-492a-b5af-57c73badad52) herunterladen und importieren.
* Ein Design für ein adaptives Formular. Zu einem Design gehören Stildetails für die Komponenten und Bereiche. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegelt der angegebene Stil die entsprechenden Komponenten wider. Sie können [ein neues Design erstellen](themes.md), [ein vorhandenes Design importieren](import-export-forms-templates.md#uploading-a-theme) oder [Beispiel-Designs](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:2779f80e-16ba-4cd1-a96f-8e2b53f3be25) herunterladen und importieren.
* Fügen Sie Ihre Benutzer zu [!DNL forms-users] hinzu, um ihnen die notwendigen Berechtigungen zum Erstellen eines adaptiven Formulars zu erteilen. Eine detaillierte Liste der formularspezifischen Benutzergruppen finden Sie unter [Gruppen und Berechtigungen](forms-groups-privileges-tasks.md).

## Erstellen eines adaptiven Formulars {#strong-create-an-adaptive-form-strong}

Um ein adaptives Formular zu erstellen, gehen Sie wie folgt vor.

1. Öffnen Sie die [!DNL Experience Manager Forms]-Autoreninstanz. Dabei kann es sich um eine Cloud-Instanz oder eine lokale Entwicklungsinstanz handeln.

1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein.

   Wenn Sie sich angemeldet haben, tippen Sie in der oberen linken Ecke auf **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.

1. Tippen Sie auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Adaptives Formular]**. Wählen Sie eine Vorlage aus und klicken Sie auf **[!UICONTROL Weiter]**.
1. Eine Option **[!UICONTROL Eigenschaften hinzufügen]** wird angezeigt. Geben Sie die Werte für die folgenden Eigenschaftenfelder an. Die Felder „Titel“ und „Name“ sind obligatorisch.

   * **[!UICONTROL Titel:]** Gibt den Anzeigenamen des Formulars an. Der Titel erleichtert Ihnen die Identifizierung des Formulars in der Benutzeroberfläche von [!DNL Experience Manager Forms].
   * **[!UICONTROL Name:]** Gibt den Namen des Formulars an. Im Repository wird ein Knoten mit dem angegebenen Namen erstellt. Wenn Sie mit der Eingabe des Titels beginnen, wird automatisch ein Wert für das Feld „Name“ vorgeschlagen. Sie können den vorgeschlagenen Wert gegebenenfalls ändern. Im Feld „Name“ dürfen nur alphanumerische Zeichen, Bindestriche und Unterstriche eingegeben werden. Ungültige Eingaben werden durch Bindestriche ersetzt.
   * **[!UICONTROL Beschreibung:]** Gibt detaillierte Informationen zum Formular an.
   * **[!UICONTROL Tags:]** Gibt Tags an, die eine eindeutige Identifizierung des adaptiven Formulars ermöglichen. Tags erleichtern die Suche nach dem Formular. Um die Tags zu erstellen, geben Sie neue Tag-Namen in das Feld **[!UICONTROL Tags]** ein.

1. Sie können ein adaptives Formular erstellen, das auf den folgenden Formularmodellen basiert:

   * [Formulardatenmodell](#fdm)

   <!--* [XFA form template](#create-an-adaptive-form-based-on-an-xfa-form-template)-->
   * [XML- oder JSON-Schema](#create-an-adaptive-form-based-on-xml-or-json-schema)
   * Kein oder ohne Formularmodell

   Sie können diese auf der Registerkarte **[!UICONTROL Formularmodell]** konfigurieren. Sie befindet sich auf der Seite **[!UICONTROL Eigenschaften hinzufügen]**. Standardmäßig ist das Formularmodell **[!UICONTROL Ohne]** ausgewählt.

1. Tippen Sie auf **[!UICONTROL Erstellen]**. Ein adaptives Formular wird erstellt, und es wird ein Dialogfeld zum Öffnen des Formulars zur Bearbeitung angezeigt.

1. Tippen Sie auf **[!UICONTROL Öffnen]**, um das neu erstellte Formular in einer neuen Registerkarte zu öffnen. Das Formular wird zur Bearbeitung geöffnet und zeigt den Inhalt an, der in der Vorlage verfügbar ist. Es zeigt auch die Seitenleiste an, um das neu erstellte Formular entsprechend den Anforderungen anzupassen.

   Je nach Typ des adaptiven Formulars werden auf der Registerkarte **[!UICONTROL Datenmodellobjekte]** des **[!UICONTROL Content-Browsers]** in der Seitenleiste die Formularelemente angezeigt, die im zugewiesenen <!--XFA form template, -->XML-Schema oder JSON-Schema vorhanden sind. Sie können diese Elemente auch in das zu erstellende adaptive Formular ziehen.

## Erstellen eines adaptiven Formulars auf der Basis eines Formulardatenmodells {#fdm}

Durch die [Datenintegration](data-integration.md) können Sie mehrere Datenquellen integrieren, ihre Entitäten und Services zusammenführen und so ein Formulardatenmodell erstellen. Dabei handelt es sich um eine Erweiterung des JSON-Schemas. Sie können ein Formulardatenmodell verwenden, um ein adaptives Formular zu erstellen. Die Entitäten oder Datenmodellobjekte, die in einem Formulardatenmodell konfiguriert sind, sind als Datenmodellobjekte für die Formularerstellung verfügbar. Sie sind an die jeweiligen Datenquellen gebunden und werden verwendet, um ein Formular vorauszufüllen und die übermittelten Daten zurück in die entsprechenden Datenquellen zu schreiben. Sie können auch Services aufrufen, die in einem Formulardatenmodell mit Regeln für adaptive Formulare konfiguriert sind.

So verwenden Sie ein Formulardatenmodell zum Erstellen eines adaptiven Formulars:

1. Wählen Sie auf der Registerkarte „Formularmodell“ im Bildschirm „Eigenschaften hinzufügen“ **[!UICONTROL Formulardatenmodell]** aus der Dropdown-Liste **[!UICONTROL Auswählen]**.

   ![Erstellen eines adaptiven Formulars](assets/create-af-1-1.png)

1. Tippen Sie auf **[!UICONTROL Formulardatenmodell auswählen]**, um es zu erweitern. Sie sehen eine Liste aller verfügbaren Formulardatenmodelle. Wählen Sie ein Formulardatenmodell aus.

>[!NOTE]
>
>Das Formulardatenmodell für ein adaptives Formular können Sie auch ändern. Detaillierte Anweisungen hierfür finden Sie unter [Formularmodelleigenschaften eines adaptiven Formulars bearbeiten](#edit-form-model).

## Erstellen eines adaptiven Formulars auf der Basis eines XML- oder JSON-Schemas {#create-an-adaptive-form-based-on-xml-or-json-schema}

XML- und JSON-Schemas stellen die Struktur dar, in der Daten vom Back-End-System in Ihrer Organisation produziert oder genutzt werden. Sie können ein Schema mit einem adaptiven Formular verknüpfen und dem Formular mithilfe der Elemente aus dem Schema dynamische Inhalte hinzufügen. Die Elemente des Schemas stehen auf der Registerkarte „Datenmodellobjekt“ des Content-Browsers für das Erstellen von adaptiven Formularen zur Verfügung. Sie können die Schemaelemente zum Erstellen des Formulars ziehen und ablegen.

In den folgenden Dokumenten erfahren Sie, wie Sie ein XML- oder JSON-Schema für die Erstellung adaptiver Formulare entwickeln.

* [Erstellen adaptiver Formulare mithilfe eines XML-Schemas](adaptive-form-xml-schema-form-model.md)
* [Erstellen adaptiver Formulare mithilfe eines JSON-Schemas](adaptive-form-json-schema-form-model.md)

Führen Sie folgende Schritte aus, um ein XML- oder JSON-Schema als Formularmodell für ein adaptives Formular zu verwenden:

1. Tippen Sie auf der Seite zum Erstellen adaptiver Formulare beim Schritt **[!UICONTROL Eigenschaften hinzufügen]** auf die Registerkarte **[!UICONTROL Formularmodell]**.
1. Wählen Sie auf der Registerkarte „Formularmodell“ **[!UICONTROL Schema]** aus dem Dropdown-Feld **[!UICONTROL Auswählen]**.

1. Tippen Sie auf **[!UICONTROL Schema auswählen]** und führen Sie einen der folgenden Schritte aus:

   * **[!UICONTROL Von Datenträger hochladen]** – Wählen Sie diese Option und tippen Sie auf „Schemadefinition hochladen“, um ein XML- oder JSON-Schema in Ihrem Dateisystem zu suchen und hochzuladen. Die hochgeladene Schemadatei befindet sich innerhalb des Formulars und ist für andere adaptive Formulare nicht zugänglich.
   * **[!UICONTROL Im Repository suchen]** – Wählen Sie diese Option, um eine Auswahl aus der Liste der im Repository verfügbaren Schemadefinitionsdateien zu treffen. Wählen Sie die XML- oder JSON-Schemadatei als Formularmodell aus. Das ausgewählte Schema wird dem Formular per Verweis zugeordnet und kann für andere adaptive Formulare verwendet werden.

      Stellen Sie sicher, dass der Dateiname des JSON-Schemas mit **.schema.json** endet. Beispiel: mySchema.schema.json
   ![Auswählen eines XML- oder JSON-Schemas](assets/upload-schema.png)
   **Abbildung:** *Auswählen eines XML- oder JSON-Schemas*

1. (Nur für XML-Schema) Nachdem Sie ein XML-Schema ausgewählt oder hochgeladen haben, geben Sie ein Stammelement der ausgewählten XSD-Datei an, das dem adaptiven Formular zugewiesen werden soll.

   ![Auswählen eines XSD-Stammelements](assets/xsd-root-element.png)
   **Abbildung:** *XSD-Stammelement auswählen*

>[!NOTE]
>
>Sie können das Schema für ein adaptives Formular auch ändern. Detaillierte Anweisungen hierfür finden Sie unter [Formularmodelleigenschaften eines adaptiven Formulars bearbeiten](#edit-form-model).

## Bearbeiten der Formularmodelleigenschaften eines adaptiven Formulars {#edit-form-model}

Adaptive Formulare werden entweder ohne Formularmodell erstellt (mithilfe der Option „Ohne“ für Formularmodelle) oder mithilfe eines Formularmodells wie eines <!-- form template, -->XML- oder JSON-Schemas oder eines Formulardatenmodells. Sie können das Formularmodell für ein adaptives Formular von der Option „Ohne“ zu einem anderen Formularmodell ändern. Sie können für ein adaptives Formular, das auf einem Formularmodell basiert, ein anderes <!-- form template,--> XML-Schema, JSON-Schema oder Formulardatenmodell für dasselbe Formularmodell wählen. Sie können jedoch nicht zwischen Formularmodellen wechseln.

1. Wählen Sie das adaptive Formular aus und tippen Sie auf das Symbol **Eigenschaften**.
1. Öffnen Sie die Registerkarte **[!UICONTROL Formularmodell]** und wählen Sie eine der folgenden Vorgehensweisen.

   * Wenn das adaptive Formular nicht auf einem Formularmodell basiert, können Sie ein Formularmodell und ein entsprechendes XML- oder JSON-Schema oder ein Formulardatenmodell auswählen.<!-- a form template, -->
   * Bei einem adaptiven Formular, das auf einem Formularmodell basiert, können Sie ein anderes <!-- form template, --> XML-Schema, JSON-Schema oder Formulardatenmodell für dasselbe Formularmodell wählen.

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Eigenschaften zu speichern.
