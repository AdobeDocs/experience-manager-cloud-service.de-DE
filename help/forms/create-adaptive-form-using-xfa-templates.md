---
title: Wie erstelle ich ein adaptives Formular basierend auf Kernkomponenten mithilfe von XFA-Formularvorlagen?
description: Erfahren Sie, wie Sie ein adaptives Formular mit [!DNL Experience Manager Forms] mithilfe von XFA-Formularvorlagen oder XDP-Dateien erstellen.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
source-git-commit: 681c194f997ab66f93beedad4eea273614e6797d
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 20%

---


# Erstellen eines adaptiven Formulars (Kernkomponenten) basierend auf XFA-Formularvorlagen

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

AEM as a Cloud Service bietet Benutzern die Möglichkeit, adaptive Forms basierend auf Kernkomponenten mithilfe von XFA-Formularvorlagen (XML Forms Architecture) oder `*.XDP`-Dateien (XML-Datenpaket) zu erstellen. Mit dieser Funktion können Benutzer Zeit sparen, indem sie Felder aus XFA-Formularvorlagen oder XDP-Dateien direkt in Adaptive Forms migrieren.

Sie können Ihre XFA-Formularvorlage oder XDP-Dateiformularvorlagen erneut verwenden, um adaptive Forms basierend auf Kernkomponenten zu erstellen. Laden Sie zu diesem Zweck eine XFA-Formularvorlage oder XDP-Dateien hoch und verknüpfen Sie sie mit einem adaptiven Formular. Die Elemente der XFA-Formularvorlage oder XDP-Dateien werden beim Authoring adaptiver Formulare zur Verwendung in der Inhaltssuche verfügbar. Sie können die Formularvorlagenelemente per Drag-and-Drop aus der Inhaltssuche in das Formular ziehen.

## Vorteile beim Erstellen von Formularen basierend auf XFA-Formularvorlagen oder XDP-Dateien

Die folgenden Vorteile sind beim Erstellen von Formularen auf Basis von XFA-Formularvorlagen oder XDP-Dateien:

* **Zeitersparnis**: Sie können vorhandene XFA-Formularvorlagen (XDP-Dateien) schnell wiederverwenden, ohne die Formularstruktur neu erstellen zu müssen. So sparen Sie Zeit und Mühe während des Authoring-Prozesses.
* **Unkomplizierte Migration**: Wenn Sie bereits XFA-Formularvorlagen verwendet haben, bietet diese Option einen einfachen Migrationspfad zu Adaptive Forms, mit dem Sie die Vorteile moderner AEM Kernkomponenten nutzen können, ohne vorhandene Formulardaten und Logik zu verlieren.
* **Verbessertes Benutzererlebnis**: Adaptive Forms sind responsiver und anpassbarer als XFA-Formulare. Durch den Übergang zu Adaptive Forms können Sie für ein benutzerfreundlicheres Erlebnis auf verschiedenen Geräten und Bildschirmgrößen sorgen.
* **Verbesserte Integration**: Adaptive Forms lässt sich besser mit anderen Funktionen integrieren, wie z. B. Workflows, Datenbindung und Formularübermittlungen, sodass reibungslosere Workflows und eine bessere allgemeine Formularverwaltung möglich sind.

## Voraussetzungen

Sie benötigen Folgendes, um ein adaptives Formular basierend auf Kernkomponenten mithilfe von XFA-Formularvorlagen oder XDP-Dateien zu erstellen:

* [Aktivieren der Kernkomponenten adaptiver Formulare für Ihre Umgebung](enable-adaptive-forms-core-components.md).
* Es wird empfohlen, sich mit den folgenden Bereichen vertraut zu machen:
   * Erstellen eines adaptiven Formulars
   * XFA (XML Forms Architecture)

## Wie erstelle ich ein adaptives Formular mit XFA-Formularvorlagen oder XDP-Dateien?

Führen Sie die folgenden Schritte aus, um ein adaptives Formular mit XFA- oder XDP-Formularvorlagen zu erstellen:

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms] -Autoreninstanz an.
1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein. Wenn Sie sich angemeldet haben, wählen Sie in der oberen linken Ecke **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.

   ![Forms und Dokumente](/help/forms/assets/create-fdm.png)

1. Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptive Forms]** aus.

   ![Adaptives Formular erstellen](/help/forms/assets/create-af.png)

   Der Assistent zur Formularerstellung wird geöffnet.
1. Wählen Sie auf der Registerkarte **Source** eine Vorlage basierend auf Kernkomponenten aus.

   ![Auswählen der Vorlage](/help/forms/assets/select-template.png)

   Wenn Sie eine Vorlage auswählen, werden ein in der Vorlage angegebenes Design und eine in der Vorlage angegebene Übermittlungsaktion automatisch ausgewählt und die Schaltfläche **[!UICONTROL Erstellen]** ist aktiviert.

   ![Design auswählen](/help/forms/assets/select-form-theme.png)

1. Wählen Sie **[!UICONTROL Erstellen]**. Ein Dialogfeld zum Angeben von Titel, Name und Speicherort für das adaptive Formular wird angezeigt.
1. Geben Sie Titel, Namen und Speicherort an.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.
   ![Geben Sie den Namen und den Titel an](/help/forms/assets/create-form.png)

   Ein adaptives Formular wird erstellt und im Editor für adaptive Formulare geöffnet. Der Editor zeigt die in der Vorlage verfügbaren Inhalte an.
1. Wählen Sie ![Seiteninformationen](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Eigenschaften öffnen]** aus.

   ![Eigenschaften öffnen](/help/forms/assets/form-properties.png)

   Die Seite mit den Formulareigenschaften wird geöffnet.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Formularmodell]** die Option **Formularvorlagen** aus.
1. Wählen Sie die .xdp-Datei aus der Dropdown-Liste aus.

   ![XDP-Datei auswählen](/help/forms/assets/select-xdp-file.png)

   Auf dem Bildschirm wird ein Warndialogfeld angezeigt. Klicken Sie auf **OK** , um fortzufahren.

   ![Warndialog](/help/forms/assets/fdm-warning.png)

1. Klicken Sie zum Speichern der Eigenschaften auf **[!UICONTROL Speichern und schließen]**.

   >[!NOTE]
   >
   > Nach Auswahl von **Formularvorlagen** auf der Registerkarte **Formularmodell** kann das Modell nicht mehr geändert werden.


Ein adaptives Formular wird erstellt und im Editor für adaptive Formulare geöffnet. Der Editor zeigt die in der Vorlage verfügbaren Inhalte an.  Basierend auf dem Typ des adaptiven Formulars werden die Formularelemente, die in der zugehörigen XFA-Formularvorlage vorhanden sind, auf der Registerkarte **[!UICONTROL Datenmodellobjekte]** des **[!UICONTROL Inhaltsbrowsers]** in der Seitenleiste angezeigt. Sie können diese Elemente auch per Drag-and-Drop in das zu erstellende adaptive Formular ziehen.

>[!NOTE]
>
> Sie können Skripte für XDP-Formularfelder über die Symbolleiste des Bedienfelds des hinzugefügten Felds deaktivieren. Erstellen Sie mit dem [visuellen Regeleditor](/help/forms/rule-editor-core-components.md) Logiken für die hinzugefügten Felder.

## Siehe auch

{{see-also}}
* [Hinzufügen von dynamischem Verhalten zu Formularen mithilfe des Regeleditors](/help/forms/rule-editor-core-components.md)