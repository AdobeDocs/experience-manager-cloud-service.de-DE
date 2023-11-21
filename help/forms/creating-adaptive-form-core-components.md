---
title: Wie erstelle ich ein adaptives Formular basierend auf Kernkomponenten?
description: Erfahren Sie, wie Sie ein adaptives Formular mit  [!DNL Experience Manager Forms] erstellen können. Adaptive Formulare sind responsive HTML5-Formulare, mit denen die Informationserfassung und -verarbeitung optimiert wird. Vertiefen Sie Ihre Kenntnisse über die Erstellung adaptiver Formulare auf der Grundlage eines Formulardatenmodells und eines XML- oder JSON-Schemas.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
exl-id: 1e812d93-4ba5-4589-b59b-2f564d754b0f
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '2301'
ht-degree: 74%

---

# Erstellen eines adaptiven Formulars {#creating-an-adaptive-form-core-components}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/create-an-adaptive-form-core-components.html) |
| AEM as a Cloud Service | Dieser Artikel |


Mit Adaptive Forms können Sie Formulare erstellen, die ansprechend, reaktionsfähig, dynamisch und anpassungsfähig sind. AEM Forms bietet einen benutzerfreundlichen Assistenten für Unternehmen, mit dem Sie schnell Adaptive Forms erstellen können. Der Assistent bietet eine schnelle Registerkartennavigation, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen.

Bevor Sie beginnen, erfahren Sie mehr über die Arten der Formular-Komponenten, die Ihnen zur Verfügung stehen:

* [Kernkomponenten adaptiver Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de): Dies sind standardisierte Datenerfassungskomponenten. Diese Komponenten bieten Anpassungsfunktionen, kürzere Entwicklungszeiten und niedrigere Wartungskosten für Ihre Erlebnisse bei der digitalen Registrierung. Entwickelnde können diese Komponenten einfach anpassen und gestalten. Adobe empfiehlt die Verwendung dieser modernen und erweiterbaren Komponenten zur Entwicklung von Adaptive Forms.

* [Foundation-Komponenten adaptiver Formulare](creating-adaptive-form.md): Hierbei handelt es sich um klassische (alte) Datenerfassungskomponenten. Sie können diese weiterhin verwenden, um Ihre vorhandenen Foundation-Komponenten auf Grundlage des adaptiven Formulars zu bearbeiten. Wenn Sie neue Formulare erstellen, empfiehlt Adobe die Verwendung von  [Kernkomponenten von adaptiven Formularen](creating-adaptive-form-core-components.md), um ein adaptives Formular zu erstellen.

![Assistent zum Erstellen eines adaptiven Formulars](/help/release-notes/assets/wizard.png)


## Voraussetzungen

Zum Erstellen eines adaptiven Formulars benötigen Sie Folgendes:

* **Aktivieren der adaptiven Forms-Kernkomponenten für Ihre Umgebung**: Wenn Sie ein Programm erstellen, sind die adaptiven Forms-Kernkomponenten bereits für Ihre Umgebung aktiviert. Wenn Sie eine as a Cloud Service Forms-Umgebung basierend auf Archetyp 39 oder früher haben, [Aktivieren der adaptiven Forms-Kernkomponenten für Ihre Umgebung](enable-adaptive-forms-core-components.md). Sobald Sie die Kernkomponenten für Ihre Umgebung aktivieren, werden die Vorlage und das Arbeitsflächen-Design für **adaptive Formulare (Kernkomponente)** zu Ihrer Umgebung hinzugefügt. Wenn Ihre AEM SDK-Version älter als 2023.02.0 ist, [stellen Sie sicher, dass das `prerelease`-Flag in Ihrer Umgebung aktiviert ist](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features), da Kernkomponenten für adaptive Formulare Teil der Vorabversion vor der Version 2023.02.0 waren.

* **Eine adaptive Formularvorlage**: Eine Vorlage liefert eine Grundstruktur und definiert das Erscheinungsbild (Layouts und Stile) eines adaptiven Formulars. Es enthält vorformatierte Komponenten einschließlich bestimmter Eigenschaften und einer Struktur für Inhalte. Es bietet außerdem die Optionen zum Definieren eines Designs und einer Übermittlungsaktion. Das Design definiert den Look-and-Feel und die Übermittlungsaktion definiert die Aktion, die bei der Übermittlung eines adaptiven Formulars ausgeführt werden soll. Senden der erfassten Daten an eine Datenquelle. Der Cloud-Service bietet eine OOTB-Vorlage mit leerem Namen:

   * Die Vorlage `blank` ist in jedem neuen AEM Forms as a Cloud Service-Programm enthalten.
   * Sie können das Referenzpaket über Package Manager installieren, um die Vorlage `blank` zu Ihrem AEM Forms as a Cloud Service-Programm hinzuzufügen.
   * Sie können auch [Erstellen einer adaptiven Forms-Vorlage (Kernkomponenten)](/help/forms/template-editor-core-components.md) von Grund auf neu.
   * Sie können auch [Beispielvorlagen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) in Ihre Umgebung. Auf diese Weise können Sie Formulare schnell erstellen.

* **Ein adaptives Formular**: Ein Design enthält Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider.  Die Vorlage `Canvas` ist in jedem neuen AEM Forms as a Cloud Service-Programm enthalten. Sie können auch [Beispieldesigns](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) in Ihre Umgebung. Diese helfen Ihnen dabei, mit der Formatierung Ihrer Formulare zu beginnen und eine Basisstruktur bereitzustellen, mit der Sie ein Design gemäß Ihren Geschäftsanforderungen erstellen oder anpassen können.

  <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create an Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **Berechtigungen**: Fügen Sie Ihre Benutzerinnen und Benutzer zur Gruppe [!DNL forms-users] hinzu. Die Mitglieder der [!DNL forms-users]-Gruppe sind berechtigt, ein adaptives Formular zu erstellen. Eine detaillierte Liste formularspezifischer Benutzergruppen finden Sie unter [Gruppen und Berechtigungen](forms-groups-privileges-tasks.md).

<!--
>[!NOTE]
>
>
> In addition to the given themes and templates when you enable Core Components, you can also deploy the latest out-of-the box [sample themes and templates](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) to your AEM environment for use in Core Components based Adaptive Forms.
-->

## Erstellen eines adaptiven Formulars  {#create-an-adaptive-form-core-components}

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms] Autoreninstanz. Dabei kann es sich um eine Cloud-Instanz oder eine lokale Entwicklungsinstanz handeln.

1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein. Wenn Sie sich angemeldet haben, tippen Sie in der oberen linken Ecke auf **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.

1. Tippen Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptives Formular]**. Der Assistent wird geöffnet. Wählen Sie auf der Registerkarte „Quelle“ eine Vorlage aus:

   ![Kernkomponentenvorlage](/help/forms/assets/core-components-template.png)

   Wenn Sie eine Vorlage auswählen, werden ein Design und eine in der Vorlage angegebene Sendeaktion automatisch ausgewählt und die Schaltfläche **[!UICONTROL Erstellen]** wird aktiviert. Sie können zu den Registerkarten **[!UICONTROL Stil]** oder **[!UICONTROL Übermittlung]** gehen, um ein anderes Design oder eine andere Übermittlungsaktion auszuwählen. Wenn in der ausgewählten Vorlage kein Design angegeben wird, bleibt die Schaltfläche „Erstellen“ deaktiviert. Sie können zur Registerkarte **[!UICONTROL Stile]** gehen, um ein Design manuell auszuwählen.

   >[!NOTE]
   >
   >
   > Wenn Sie über keine Vorlage für **adaptive Formulare (Kernkomponente)** in Ihrer Umgebung verfügen, [aktivieren Sie die Kernkomponenten für adaptive Formulare für Ihre Umgebung](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project). Sobald Sie die Kernkomponenten für Ihre Umgebung aktivieren, wird die Vorlage für **adaptive Formulare (Kernkomponente)** zu Ihrer Umgebung hinzugefügt.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Stil]** ein Design aus:

   * Wenn die ausgewählte Vorlage ein Design angibt, wird das Design automatisch im Assistenten ausgewählt. Sie können auch auf der Registerkarte „Stil“ ein anderes Design auswählen.

   * Wenn in der ausgewählten Vorlage kein Design angegeben ist, können Sie auf der Registerkarte „Stil“ ein Design auswählen. Die **[!UICONTROL Erstellen]**-Schaltfläche wird erst aktiviert, nachdem ein Design ausgewählt wurde.

1. (Optional) Wählen Sie auf der Registerkarte „Daten“ ein Datenmodell aus:

   * **Formulardatenmodell**: Ein [Formulardatenmodell](data-integration.md) ermöglicht Ihnen die Integration von Entitäten und Diensten aus unterschiedlichen Datenquellen in ein adaptives Formular. Wählen Sie das Formulardatenmodell, wenn Sie ein adaptives Formular erstellen, für das Daten aus mehreren Datenquellen abgerufen und in sie geschrieben werden sollen.

   * **JSON-Schema**: [JSON-Schema](adaptive-form-json-schema-form-model.md) Unser auf Kernkomponenten basierendes adaptives Formular ermöglicht eine nahtlose Integration in das Backend-System Ihres Unternehmens, indem es die Möglichkeit bietet, ein JSON-Schema zu verknüpfen, das die Struktur der erzeugten oder verwendeten Daten darstellt. Diese Zuordnung ermöglicht es Autorinnen und Autoren, dem adaptiven Formular mithilfe der Elemente des Schemas dynamisch Inhalte hinzuzufügen. Die Elemente des Schemas sind während des Authoring-Prozesses auf der Registerkarte Datenmodellobjekte des Inhalts-Browsers leicht zugänglich. Alle Felder werden automatisch zu jedem erstellten adaptiven Formular hinzugefügt.

   Standardmäßig werden alle Felder des zugehörigen JSON-Schemas automatisch ausgewählt und in entsprechende adaptive Formularkomponenten konvertiert, was den Erstellungsprozess vereinfacht. Der Assistent bietet einen zusätzlichen Komfort, mit dem Sie mithilfe von Kontrollkästchen selektiv festlegen können, welche Felder in das adaptive Formular aufgenommen werden sollen.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Übermittlung]** eine Übermittlungsaktion aus:

   * Wenn Sie eine Vorlage auswählen, wird die in der Vorlage angegebene Übermittlungsaktion automatisch ausgewählt. Sie können auf der Registerkarte „Übermittlung“ eine andere Übermittlungsaktion auswählen. Auf der Registerkarte **[!UICONTROL Übermittlung]** werden alle verfügbaren Übermittlungsaktionen angezeigt.

   * Wenn die ausgewählte Vorlage keine Übermittlungsaktion angibt, können Sie auf der Registerkarte **[!UICONTROL Übermittlung]** eine Übermittlungsaktion auswählen

1. (Optional) Auf der Registerkarte **[!UICONTROL Versand]** können Sie ein Datum für die Veröffentlichung oder das Rückgängigmachen der Veröffentlichung eines adaptiven Formulars angeben.

1. Tippen Sie auf **[!UICONTROL Erstellen]**. Es wird ein Dialogfeld angezeigt, in dem Sie den Titel, Namen und Speicherort des adaptiven Formulars angeben können:

   * **[!UICONTROL Titel:]** Gibt den Anzeigenamen des Formulars an. Der Titel erleichtert Ihnen die Identifizierung des Formulars in der Benutzeroberfläche von [!DNL Experience Manager Forms].
   * **[!UICONTROL Name:]** Gibt den Namen des Formulars an. Im Repository wird ein Knoten mit dem angegebenen Namen erstellt. Wenn Sie mit der Eingabe des Titels beginnen, wird automatisch ein Wert für das Feld „Name“ vorgeschlagen. Sie können den vorgeschlagenen Wert gegebenenfalls ändern. Im Feld „Name“ dürfen nur alphanumerische Zeichen, Bindestriche und Unterstriche eingegeben werden. Alle ungültigen Eingaben werden durch Bindestriche ersetzt.
   * **[!UICONTROL Pfad:]** Gibt den Speicherort an, an dem das adaptive Formular gespeichert werden soll. Sie können das adaptive Formular direkt unter `/content/dam/formsanddocuments` erstellen oder einen Ordner wie `/content/dam/formsanddocuments/adaptiveforms` anlegen, um ein adaptives Formular zu speichern. Stellen Sie sicher, dass Sie den Ordner erstellen, bevor Sie ihn im Pfad verwenden. Das Feld **[!UICONTROL Pfad]** erstellt nicht automatisch einen Ordner.

1. Tippen Sie auf **[!UICONTROL Erstellen]**. Ein adaptives Formular wird erstellt und im Editor für adaptive Formulare geöffnet. Der Editor zeigt die in der Vorlage verfügbaren Inhalte an.  Je nach Typ des adaptiven Formulars werden auf der Registerkarte **[!UICONTROL Datenmodellobjekte]** des **[!UICONTROL Content-Browsers]** in der Seitenleiste die Formularelemente angezeigt, die im zugewiesenen <!--XFA form template, XML schema or -->-JSON-Schema oder Formulardatenmodell vorhanden sind. Sie können diese Elemente auch per Drag-and-Drop in das zu erstellende adaptive Formular ziehen.

Jetzt können Sie die [Adaptive Forms-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) in den adaptiven Forms-Container, um das Formular zu entwerfen und zu erstellen. Sie können auch [https://aemcomponents.dev/](https://aemcomponents.dev/) besuchen, um die verfügbaren Kernkomponenten in Aktion zu sehen.

## Konfigurieren der Sendeaktion für ein adaptives Formular {#configure-submit-action-for-form}

Mit einer Übermittlungsaktion können Sie das Ziel der Daten auswählen, die über ein adaptives Formular erfasst werden. Eine Übermittlungsaktion wird ausgelöst, wenn eine Benutzerin bzw. ein Benutzer in einem adaptiven Formular auf die Schaltfläche „Senden“ klickt. Adaptive Formulare enthalten einige vordefinierte Sendeaktionen. Sie können außerdem die standardmäßigen Sendeaktionen erweitern, um Ihre eigene benutzerdefinierte Sendeaktion zu erstellen. So konfigurieren Sie eine Sendeaktion für Ihr Formular:

1. Öffnen Sie den Inhaltsbrowser und wählen Sie die **[!UICONTROL Guide Container]** -Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf die Guide Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare wird geöffnet.

1. Klicken Sie auf  **[!UICONTROL Einsendung]** Registerkarte.

   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptive Formulare zu öffnen und eine Sendeaktion zu konfigurieren.](/help/forms/assets/adaptive-forms-submit-message.png)

1. Auswählen und Konfigurieren eines **[!UICONTROL Übermittlungsaktion]**, basierend auf Ihren Anforderungen. Detaillierte Informationen zu Sendeaktionen finden Sie unter [Sendeaktion für adaptive Formulare](/help/forms/configuring-submit-actions.md)

<!--
    
    ![Click the Wrench icon to open Adaptive Form Container dialog box to configure Data Models for the Adaptive Form Container component](/help/forms/assets/adaptive-forms-container.png)

-->

## Leiten Sie bei der Formularübermittlung die Benutzenden auf eine Seite um oder zeigen Sie eine Dankesnachricht an

Beim Senden eines Formulars können Sie die Benutzenden zu einer anderen Web-Seite oder Nachricht umleiten. So leiten Sie die Benutzenden um oder konfigurieren die Dankesnachricht:

1. Öffnen Sie den Inhaltsbrowser und wählen Sie die **[!UICONTROL Guide Container]** -Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf die Guide Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Übermittlung]**.

   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptives Formular zu öffnen, um eine Umleitungsseite oder Dankesnachricht zu konfigurieren.](/help/forms/assets/adaptive-forms-redirect-message.png)

   * Um eine Umleitungs-URL zu konfigurieren, wählen Sie für die Option &quot;Beim Senden&quot;die Option **[!UICONTROL Zu URL umleiten]** und eine AEM Sites-Seite durchsuchen und auswählen oder die URL einer externen Seite angeben.

   * Um eine benutzerdefinierte Nachricht oder Dankesnachricht zu konfigurieren, wählen Sie für die Option &quot;Senden&quot;die Option **[!UICONTROL Nachricht anzeigen]** und geben Sie eine Nachricht im **[!UICONTROL Nachrichteninhalt]** ankreuzen. Es handelt sich um ein Rich-Text-Feld. Sie können die Vollbildoption verwenden, um alle verfügbaren Rich-Text-Elemente anzuzeigen.

## Schema oder Formulardatenmodell für ein adaptives Formular konfigurieren{#configure-schema-or-data-model-for-form}

Sie können das Formulardatenmodell verwenden, um ein Formular mit einer Datenquelle zu verbinden und Daten basierend auf Benutzeraktionen zu senden und zu empfangen. Sie können auch ein Formular mit einem JSON-Schema verbinden, um die gesendeten Daten in einem vordefinierten Format zu empfangen. Verbinden Sie basierend auf der Anforderung Ihr Formular mit einem JSON-Schema oder Formulardatenmodell:

* [Erstellen Sie ein JSON-Schema und laden Sie es in Ihre Umgebung hoch](/help/forms/adaptive-form-json-schema-form-model.md)
* [Erstellen Sie ein Formulardatenmodell](/help/forms/create-form-data-models.md)

### JSON-Schema oder Formulardatenmodell für Ihr Formular konfigurieren

So konfigurieren Sie ein JSON-Schema oder ein Formulardatenmodell für Ihr Formular:

1. Öffnen Sie den Inhaltsbrowser und wählen Sie die **[!UICONTROL Guide Container]** -Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf die Guide Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare wird geöffnet.
1. Öffnen Sie die **[!UICONTROL Datenmodell]** Registerkarte.

   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptives Formular zu öffnen, um ein JSON-Schema oder Formulardatenmodell zu konfigurieren.](/help/forms/assets/adaptive-forms-select-form-data-model-or-json-schema.png)

1. Wählen Sie ein JSON-Schema oder ein Formulardatenmodell aus und konfigurieren Sie es entsprechend Ihren Anforderungen:

   * Wenn Sie die Option **[!UICONTROL Formularmodell]** wählen, können Sie mit der Option **[!UICONTROL Formulardatenmodell auswählen]** ein vorkonfiguriertes Formulardatenmodell auswählen.
   * Wenn Sie die Option **[!UICONTROL Schema]** wählen, verwenden Sie die Option **[!UICONTROL Schema]**, um ein JSON-Schema für Ihr Formular auszuwählen.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Konfigurieren eines Vorbefüllungs-Dienstes  {#configure-prefill-service-for-form}

Sie können den Vorbefüllungsdienst verwenden, um Felder eines adaptiven Formulars automatisch mit vorhandenen Daten auszufüllen. Wenn eine Benutzerin oder ein Benutzer ein Formular öffnet, sind die Werte für diese Felder schon vorbefüllt. Sie haben folgende Möglichkeiten:

* [Erstellen eines benutzerdefinierten Vorbefüllungsdienstes](/help/forms/prepopulate-adaptive-form-fields.md)
* [Verwenden des Vorbefüllungsdienstes für Formulardatenmodelle](#fdm-prefill-service)

### Verwenden Sie den Vorbefüllungs-Dienst für Formulardatenmodelle, um Felder eines adaptiven Formulars im Voraus auszufüllen. {#fdm-prefill-service}

Sie können den Vorbefüllungs-Dienst für Formulardatenmodelle verwenden, um Felder eines adaptiven Formulars mit einem Formulardatenmodell oder einem benutzerdefinierten Vorbefüllungs-Dienst im Voraus auszufüllen. Der Vorbefüllungsdienst für das Formulardatenmodell verwendet den [Get-Dienst des konfigurierten Formulardatenmodells](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) zum Abrufen von Daten. So verwenden Sie für ein adaptives Formular den Vorbefüllungsdienst für Formulardatenmodelle:

1. Öffnen Sie den Inhaltsbrowser und wählen Sie die **[!UICONTROL Guide Container]** -Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf die Guide Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare wird geöffnet.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld der Container für adaptive Formulare zum Konfigurieren von Datenmodellen wird geöffnet.
   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptives Formular zu öffnen, um eine Umleitungsseite oder Dankesnachricht zu konfigurieren.](/help/forms/assets/adaptive-forms-container-prefill-service.png)
1. Wählen Sie ein Formulardatenmodell aus. Öffnen Sie die Registerkarte **[!UICONTROL Allgemein]**. Wählen Sie im Vorbefüllungsdienst die Option **[!UICONTROL Vorbefüllungsdienst für Formulardatenmodell]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**. Ihr adaptives Formular ist jetzt so konfiguriert, dass es die Vorbefüllung für Formulardatenmodelle verwendet. Sie können nun den [Regeleditor](rule-editor.md) verwenden, um Regeln zu erstellen, nach denen Felder des Formulars vorausgefüllt werden.

## Bearbeiten der Formularmodelleigenschaften eines adaptiven Formulars {#edit-form-model}

1. Wählen Sie das adaptive Formular aus und tippen Sie auf ![Seiteninformationen](/help/forms/assets/Smock_Properties_18_N.svg) => **[!UICONTROL Eigenschaften öffnen]**. Die Seite mit den Formulareigenschaften wird geöffnet.

1. Navigieren Sie zur Registerkarte **[!UICONTROL Formularmodell]** und wählen Sie ein Formularmodell aus. Wenn das adaptive Formular ohne Formularmodell ist, können Sie entweder ein JSON-Schema oder ein Formulardatenmodell auswählen. Wenn das adaptive Formular jedoch bereits auf einem Formularmodell basiert, haben Sie die Möglichkeit, zu einem anderen Formularmodell desselben Typs zu wechseln. Wenn das Formular beispielsweise ein JSON-Schema verwendet, können Sie einfach zu einem anderen JSON-Schema wechseln. Wenn das Formular ein Formulardatenmodell verwendet, können Sie auch zu einem anderen Formulardatenmodell wechseln.

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Eigenschaften zu speichern.


<!--

## See next

* [Create style or themes for your forms](using-themes-in-core-components.md)
* [Add dynamic behavior to forms using the rule editor](rule-editor.md)
* [Set layout of forms for different screen sizes and device types](/help/sites-cloud/authoring/features/responsive-layout.md)
* [Sample themes templates and form data models](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)

-->

## Siehe auch {#see-also}

{{see-also}}
* [Hinzufügen von dynamischem Verhalten zu Formularen mithilfe des Regeleditors](rule-editor.md)
* [Festlegen des Layouts von Formularen für verschiedene Bildschirmgrößen und Gerätetypen](/help/sites-cloud/authoring/features/responsive-layout.md)

