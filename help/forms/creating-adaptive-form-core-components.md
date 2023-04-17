---
title: Erstellen eines adaptiven Formulars
description: Erfahren Sie, wie Sie ein adaptives Formular mit  [!DNL Experience Manager Forms] erstellen können. Adaptive Formulare sind responsive HTML5-Formulare, mit denen die Informationserfassung und -verarbeitung optimiert wird. Vertiefen Sie Ihre Kenntnisse über die Erstellung adaptiver Formulare auf der Grundlage eines Formulardatenmodells und eines XML- oder JSON-Schemas.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
source-git-commit: a4fd268cb143c1356de3db9d55b16ccb58b67d4b
workflow-type: tm+mt
source-wordcount: '1496'
ht-degree: 96%

---


# Erstellen eines adaptiven Formulars (Kernkomponenten) {#creating-an-adaptive-form-core-components}

Adaptive Formulare bieten Ihnen die Möglichkeit, interaktive, responsive und dynamische adaptive Formulare zu erstellen. AEM Forms bietet eine benutzerfreundliche Assistenz für die schnelle Erstellung adaptiver Formulare. Der Assistent bietet eine schnelle Registerkartennavigation, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen.

Bevor Sie beginnen, erfahren Sie mehr über die Arten der Formular-Komponenten, die Ihnen zur Verfügung stehen:

* [Kernkomponenten adaptiver Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de): Dies sind standardisierte Datenerfassungskomponenten. Diese Komponenten bieten Anpassungsfunktionen, kürzere Entwicklungszeiten und niedrigere Wartungskosten für Ihre Erlebnisse bei der digitalen Registrierung. Entwickelnde können diese Komponenten einfach anpassen und gestalten. Adobe empfiehlt die Nutzung dieser modernen und erweiterbaren Komponenten zur Entwicklung von adaptiven Formularen.

* [Foundation-Komponenten adaptiver Formulare](creating-adaptive-form.md): Hierbei handelt es sich um klassische (alte) Datenerfassungskomponenten. Sie können diese weiterhin verwenden, um Ihre vorhandenen Foundation-Komponenten auf Grundlage des adaptiven Formulars zu bearbeiten. Wenn Sie neue Formulare erstellen, empfiehlt Adobe die Verwendung von  [Kernkomponenten von adaptiven Formularen](creating-adaptive-form-core-components.md), um ein adaptives Formular zu erstellen.

![Assistent zum Erstellen eines adaptiven Formulars](/help/release-notes/assets/wizard.png)


## Voraussetzungen

Zum Erstellen eines adaptiven Formulars benötigen Sie Folgendes:

* **Aktivieren der Kernkomponenten adaptiver Formulare für Ihre Umgebung**: Wenn Sie ein neues Programm erstellen, sind die Kernkomponenten adaptiver Formulare bereits für Ihre Umgebung aktiviert. Wenn Sie eine Forms as a Cloud Service-Umgebung basierend auf Archetyp 39 oder früher haben, [aktivieren Sie die Kernkomponenten adaptiver Formulare für Ihre Umgebung](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project). Sobald Sie die Kernkomponenten für Ihre Umgebung aktivieren, wird die Vorlage und das Arbeitsflächen-Design für **adaptive Formulare (Kernkomponente)** zu Ihrer Umgebung hinzugefügt. Wenn Ihre AEM SDK-Version älter als 2023.02.0 ist, [sicherstellen, dass Sie `prerelease` Markierung aktiviert in Ihrer Umgebung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=en#new-features) als Adaptive Forms-Kernkomponenten waren Teil der Vorabversion vor der Version 2023.02.0.

* **Eine adaptive Formularvorlage**: Eine Vorlage liefert eine Grundstruktur und definiert das Erscheinungsbild (Layouts und Stile) eines adaptiven Formulars. Es enthält vorformatierte Komponenten einschließlich bestimmter Eigenschaften und einer Struktur für Inhalte. Es bietet außerdem die Optionen zum Definieren eines Designs und einer Übermittlungsaktion. Das Design definiert den Look-and-Feel und die Übermittlungsaktion definiert die Aktion, die bei der Übermittlung eines adaptiven Formulars ausgeführt werden soll. Senden der erfassten Daten an eine Datenquelle. Der Cloud-Service bietet eine OOTB-Vorlage mit leerem Namen:

   * Die Vorlage `blank` ist in jedem neuen AEM Forms as a Cloud Service-Programm enthalten.
   * Sie können das Referenzpaket über Package Manager installieren, um die Vorlage `blank` zu Ihrem AEM Forms as a Cloud Service-Programm hinzuzufügen.
   * Daneben gibt es die Möglichkeit der von Grund auf neuen [Erstellung einer neuen Vorlage für adaptive Formulare (Kernkomponenten)](template-editor.md).

* **Ein adaptives Formular**: Ein Design enthält Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider.  Die Vorlage `Canvas` ist in jedem neuen AEM Forms as a Cloud Service-Programm enthalten.

   <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create a new Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **Berechtigungen**: Fügen Sie Ihre Benutzerinnen und Benutzer zur Gruppe [!DNL forms-users] hinzu. Die Mitglieder der [!DNL forms-users]-Gruppe sind berechtigt, ein adaptives Formular zu erstellen. Eine detaillierte Liste der formularspezifischen Benutzergruppen finden Sie unter [Gruppen und Berechtigungen](forms-groups-privileges-tasks.md).


## Erstellen eines adaptiven Formulars (Kernkomponenten) {#create-an-adaptive-form-core-components}

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz bei [!DNL Experience Manager Forms] an. Dabei kann es sich um eine Cloud-Instanz oder eine lokale Entwicklungsinstanz handeln.

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

   * **JSON-Schema**: [JSON-Schema](adaptive-form-json-schema-form-model.md) Unser auf Kernkomponenten basierendes adaptives Formular ermöglicht eine nahtlose Integration in das Backend-System Ihres Unternehmens, indem es die Möglichkeit bietet, ein JSON-Schema zu verknüpfen, das die Struktur der erzeugten oder verwendeten Daten darstellt. Diese Zuordnung ermöglicht es Autorinnen und Autoren, dem adaptiven Formular mithilfe der Elemente des Schemas dynamisch Inhalte hinzuzufügen. Die Elemente des Schemas sind auf der Registerkarte „Datenmodellobjekte“ des Inhaltsbrowsers während des Erstellungsprozesses leicht zugänglich, und alle Felder werden automatisch zu jedem neu erstellten adaptiven Formular hinzugefügt.

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

Jetzt können Sie die Kernkomponenten für adaptive Formulare per Drag &amp; Drop in den Container für adaptive Formulare ziehen, um das Formular zu entwerfen und zu erstellen.

## Verfügbare Kernkomponenten für adaptive Formulare

Kernkomponenten für adaptive Formulare sind standardisierte Datenerfassungskomponenten. Diese Komponenten bieten Anpassungsmöglichkeiten, verkürzen die Entwicklungszeit und senken die Wartungskosten für Ihre digitalen Anmeldesysteme. [Die Dokumentation zu den Kernkomponenten der adaptiven Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) enthält eine detaillierte Liste der verfügbaren Komponenten sowie detaillierte Informationen zu den Funktionen der einzelnen Komponenten. Sie können auch [https://aemcomponents.dev/](https://aemcomponents.dev/) besuchen, um die verfügbaren Kernkomponenten in Aktion zu sehen.

## Bearbeiten der Formularmodelleigenschaften eines adaptiven Formulars {#edit-form-model}

1. Wählen Sie das adaptive Formular aus und tippen Sie auf ![Seiteninformationen](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Eigenschaften öffnen]**. Die Seite mit den Formulareigenschaften wird geöffnet.

1. Navigieren Sie zur Registerkarte **[!UICONTROL Formularmodell]** und wählen Sie ein Formularmodell aus. Wenn das adaptive Formular ohne Formularmodell ist, können Sie entweder ein JSON-Schema oder ein Formulardatenmodell auswählen. Wenn das adaptive Formular jedoch bereits auf einem Formularmodell basiert, haben Sie die Möglichkeit, zu einem anderen Formularmodell desselben Typs zu wechseln. Wenn das Formular beispielsweise ein JSON-Schema verwendet, können Sie einfach zu einem anderen JSON-Schema wechseln. Wenn das Formular ein Formulardatenmodell verwendet, können Sie auch zu einem anderen Formulardatenmodell wechseln.

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Eigenschaften zu speichern.
