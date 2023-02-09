---
title: Erstellen eines adaptiven Formulars
description: Erfahren Sie, wie Sie ein adaptives Formular mit  [!DNL Experience Manager Forms] erstellen können. Adaptive Formulare sind responsive HTML5-Formulare, mit denen die Informationserfassung und -verarbeitung optimiert wird. Vertiefen Sie Ihre Kenntnisse über die Erstellung adaptiver Formulare auf der Grundlage eines Formulardatenmodells und eines XML- oder JSON-Schemas.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
source-git-commit: 6f6cf5657bf745a2e392a8bfd02572aa864cc69c
workflow-type: tm+mt
source-wordcount: '1375'
ht-degree: 50%

---


# Erstellen eines adaptiven Formulars (Kernkomponenten) {#creating-an-adaptive-form-core-components}

Adaptive Formulare bieten Ihnen die Möglichkeit, interaktive, responsive und dynamische adaptive Formulare zu erstellen. AEM Forms bietet einen benutzerfreundlichen Assistenten für Unternehmen, mit dem Sie schnell Adaptive Forms erstellen können. Der Assistent bietet eine schnelle Registerkartennavigation, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen. Adaptive Forms bietet zwei Komponententypen:

* Adaptive Forms-Kernkomponenten sind standardisierte Datenerfassungskomponenten. Diese Komponenten bieten Anpassungsfunktionen, kürzere Entwicklungszeiten und niedrigere Wartungskosten für Ihre digitalen Registrierungserlebnisse. Entwickler können diese Komponenten einfach anpassen. Adobe empfiehlt die Nutzung dieser modernen und erweiterbaren Komponenten zur Entwicklung von Adaptive Forms.

* Adaptive Forms Foundation-Komponenten sind klassische (alte) Datenerfassungskomponenten.

In diesem Artikel wird ein neuester Ansatz zum Erstellen eines adaptiven Formulars beschrieben. Informationen zum Erstellen von Adaptive Forms basierend auf einem alten Ansatz finden Sie unter [Erstellen eines adaptiven Formulars (Foundation-Komponenten)](creating-adaptive-form.md)

![Assistent zum Erstellen eines adaptiven Formulars](/help/release-notes/assets/wizard.png)


## Voraussetzungen

Zum Erstellen eines adaptiven Formulars benötigen Sie Folgendes:

* **Eine adaptive Formularvorlage**: Eine Vorlage liefert eine Grundstruktur und definiert das Erscheinungsbild (Layouts und Stile) eines adaptiven Formulars. Es enthält vorformatierte Komponenten einschließlich bestimmter Eigenschaften und einer Struktur für Inhalte. Es bietet außerdem die Optionen zum Definieren eines Designs und einer Übermittlungsaktion. Das Design definiert den Look-and-Feel und die Übermittlungsaktion definiert die Aktion, die bei der Übermittlung eines adaptiven Formulars ausgeführt werden soll. Senden der erfassten Daten an eine Datenquelle. Der Cloud-Service bietet eine OOTB-Vorlage mit dem Namen leer:

   * Die `blank` -Vorlage ist in jedem neuen as a Cloud Service AEM Forms-Programm enthalten.
   * Sie können das Referenzpaket über Package Manager installieren, um die `blank` Vorlage für Ihr as a Cloud Service AEM Forms-Programm.
   * Sie können auch [eine neue adaptive Forms-Vorlage erstellen (Kernkomponenten)](template-editor.md) von Grund auf neu.

* **Ein adaptives Formular**: Ein Design enthält Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider.  Die `Canvas` -Vorlage ist in jedem neuen as a Cloud Service AEM Forms-Programm enthalten.

   <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create a new Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **Berechtigungen**: Benutzer hinzufügen zu [!DNL forms-users] hinzugefügt. Die Mitglieder der [!DNL forms-users] -Gruppe sind berechtigt, ein adaptives Formular zu erstellen. Eine detaillierte Liste der formularspezifischen Benutzergruppen finden Sie unter [Gruppen und Berechtigungen](forms-groups-privileges-tasks.md).


## Erstellen eines adaptiven Formulars (Kernkomponenten) {#create-an-adaptive-form-core-components}

1. Bei Ihrer [!DNL Experience Manager Forms] Autoreninstanz. Dabei kann es sich um eine Cloud-Instanz oder eine lokale Entwicklungsinstanz handeln.

1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein. Wenn Sie sich angemeldet haben, tippen Sie in der oberen linken Ecke auf **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.

1. Tippen Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptives Formular]**. Der Assistent wird geöffnet. Wählen Sie auf der Registerkarte „Quelle“ eine Vorlage aus:

   ![Kernkomponentenvorlage](/help/forms/assets/core-components-template.png)

   Wenn Sie eine Vorlage auswählen, werden ein Design und die Übermittlungsaktion, die in der Vorlage angegeben sind, automatisch ausgewählt und die **[!UICONTROL Erstellen]** -Schaltfläche aktiviert ist. Sie können zu den Registerkarten **[!UICONTROL Stil]** oder **[!UICONTROL Übermittlung]** gehen, um ein anderes Design oder eine andere Übermittlungsaktion auszuwählen. Wenn in der ausgewählten Vorlage kein Design angegeben wird, bleibt die Schaltfläche &quot;Erstellen&quot;deaktiviert. Sie können zur Registerkarte **[!UICONTROL Stile]** gehen, um ein Design manuell auszuwählen.

1. Im **[!UICONTROL Stil]** Registerkarte ein Design auswählen:

   * Wenn die ausgewählte Vorlage ein Design angibt, wird das Design automatisch im Assistenten ausgewählt. Sie können auch auf der Registerkarte „Stil“ ein anderes Design auswählen.

   * Wenn in der ausgewählten Vorlage kein Design angegeben ist, können Sie auf der Registerkarte „Stil“ ein Design auswählen. Die **[!UICONTROL Erstellen]**-Schaltfläche wird erst aktiviert, nachdem ein Design ausgewählt wurde.

1. (Optional) Wählen Sie auf der Registerkarte „Daten“ ein Datenmodell aus:

   * **Formulardatenmodell**: Ein [Formulardatenmodell](data-integration.md) ermöglicht Ihnen die Integration von Entitäten und Diensten aus unterschiedlichen Datenquellen in ein adaptives Formular. Wählen Sie das Formulardatenmodell, wenn Sie ein adaptives Formular erstellen, für das Daten aus mehreren Datenquellen abgerufen und in sie geschrieben werden sollen.

   * **JSON-Schema**: [JSON-Schema](adaptive-form-json-schema-form-model.md) Unser auf Kernkomponenten basierendes adaptives Formular ermöglicht eine nahtlose Integration in das Backend-System Ihres Unternehmens, indem es die Möglichkeit bietet, ein JSON-Schema zu verknüpfen, das die Struktur der erzeugten oder verwendeten Daten darstellt. Diese Zuordnung ermöglicht es Autoren, dem adaptiven Formular mithilfe der Elemente des Schemas dynamisch Inhalte hinzuzufügen. Die Elemente des Schemas sind während des Authoring-Prozesses auf der Registerkarte Datenmodellobjekte des Inhalts-Browsers leicht zugänglich. Alle Felder werden automatisch zu jedem neu erstellten adaptiven Formular hinzugefügt.

   Standardmäßig werden alle Felder des zugehörigen JSON-Schemas automatisch ausgewählt und in entsprechende adaptive Formularkomponenten konvertiert, was den Authoring-Prozess optimiert. Der Assistent bietet einen zusätzlichen Komfort, mit dem Sie mithilfe von Kontrollkästchen selektiv festlegen können, welche Felder in das adaptive Formular aufgenommen werden sollen.

1. Im **[!UICONTROL Einsendung]** eine Übermittlungsaktion auswählen:

   * Wenn Sie eine Vorlage auswählen, wird die in der Vorlage angegebene Übermittlungsaktion automatisch ausgewählt. Sie können auf der Registerkarte „Übermittlung“ eine andere Übermittlungsaktion auswählen. Auf der Registerkarte **[!UICONTROL Übermittlung]** werden alle verfügbaren Übermittlungsaktionen angezeigt.

   * Wenn die ausgewählte Vorlage keine Übermittlungsaktion angibt, können Sie auf der Registerkarte **[!UICONTROL Übermittlung]** eine Übermittlungsaktion auswählen

1. (Optional) Im **[!UICONTROL Versand]** können Sie ein Veröffentlichungs- oder Veröffentlichungsdatum für ein adaptives Formular angeben.

1. Tippen Sie auf **[!UICONTROL Erstellen]**. Es wird ein Dialogfeld angezeigt, in dem Sie den Titel, Namen und Speicherort des adaptiven Formulars angeben können:

   * **[!UICONTROL Titel:]** Gibt den Anzeigenamen des Formulars an. Der Titel erleichtert Ihnen die Identifizierung des Formulars in der Benutzeroberfläche von [!DNL Experience Manager Forms].
   * **[!UICONTROL Name:]** Gibt den Namen des Formulars an. Im Repository wird ein Knoten mit dem angegebenen Namen erstellt. Wenn Sie mit der Eingabe des Titels beginnen, wird automatisch ein Wert für das Feld „Name“ vorgeschlagen. Sie können den vorgeschlagenen Wert gegebenenfalls ändern. Im Feld „Name“ dürfen nur alphanumerische Zeichen, Bindestriche und Unterstriche eingegeben werden. Ungültige Eingaben werden durch Bindestriche ersetzt.
   * **[!UICONTROL Pfad:]** Gibt den Speicherort an, an dem das adaptive Formular gespeichert werden soll. Sie können das adaptive Formular direkt unter `/content/dam/formsanddocuments` erstellen oder einen Ordner wie `/content/dam/formsanddocuments/adaptiveforms` anlegen, um ein adaptives Formular zu speichern. Stellen Sie sicher, dass Sie den Ordner erstellen, bevor Sie ihn im Pfad verwenden. Die **[!UICONTROL Pfad]** -Feld erstellt keinen Ordner automatisch.

1. Tippen Sie auf **[!UICONTROL Erstellen]**. Ein adaptives Formular wird erstellt und im Editor für adaptive Formulare geöffnet. Der Editor zeigt die in der Vorlage verfügbaren Inhalte an.  Je nach Typ des adaptiven Formulars werden auf der Registerkarte **[!UICONTROL Datenmodellobjekte]** des **[!UICONTROL Content-Browsers]** in der Seitenleiste die Formularelemente angezeigt, die im zugewiesenen <!--XFA form template, XML schema or -->-JSON-Schema oder Formulardatenmodell vorhanden sind. Sie können diese Elemente auch per Drag-and-Drop in das zu erstellende adaptive Formular ziehen.

Jetzt können Sie den Container Adaptive Forms-Kernkomponenten per Drag &amp; Drop in den adaptiven Forms-Container ziehen, um das Formular zu entwerfen und zu erstellen.

## Verfügbare adaptive Forms-Kernkomponenten

Adaptive Forms-Kernkomponenten sind standardisierte Datenerfassungskomponenten. Diese Komponenten bieten Anpassungsfunktionen, kürzere Entwicklungszeiten und niedrigere Wartungskosten für Ihre digitalen Registrierungserlebnisse. Die folgenden Kernkomponenten sind standardmäßig verfügbar:

* Adaptives Forms-Akkordeon: Mit der Accordion-Funktion kann der Benutzer Abschnitte verwandter Inhalte in einem adaptiven Formular einblenden und verbergen.

* Schaltfläche &quot;Adaptives Forms&quot;
* Adaptive Forms-Kontrollkästchengruppe
* Adaptive Forms-Datumsauswahl
* Dropdown-Liste für adaptive Forms
* Adaptive Forms-E-Mail-Eingabe
* Adaptive Forms-Dateianlagen
* Horizontale Registerkarten für adaptive Forms
* Adaptives Forms-Bild
* Adaptive Forms-Zahleneingabe
* Adaptives Forms-Bedienfeld
* Optionsfeld &quot;Adaptives Forms&quot;
* Schaltfläche zum Zurücksetzen des adaptiven Forms
* Schaltfläche &quot;Adaptives Forms senden&quot;
* Adaptive Forms-Telefoneingabe
* Adaptiver Forms-Text
* Adaptives Forms-Textfeld
* Adaptiver Forms-Titel
* Layout des adaptiven Forms-Assistenten
* Kopfzeile
* den Namen Fußzeile zu

## Bearbeiten der Formularmodelleigenschaften eines adaptiven Formulars {#edit-form-model}

1. Wählen Sie das adaptive Formular aus und tippen Sie auf ![Seiteninformationen](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Eigenschaften öffnen]**. Die Seite &quot;Formulareigenschaften&quot;wird geöffnet.

1. Navigieren Sie zu **[!UICONTROL Formularmodell]** und wählen Sie ein Formularmodell aus. Wenn das adaptive Formular ohne Formularmodell ist, können Sie entweder ein JSON-Schema oder ein Formulardatenmodell auswählen. Wenn das adaptive Formular dagegen bereits auf einem Formularmodell basiert, können Sie zu einem anderen Formularmodell desselben Typs wechseln. Wenn das Formular beispielsweise ein JSON-Schema verwendet, können Sie einfach zu einem anderen JSON-Schema wechseln. Wenn das Formular ein Formulardatenmodell verwendet, können Sie auch zu einem anderen Formulardatenmodell wechseln.

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Eigenschaften zu speichern.
