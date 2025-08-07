---
title: Wie erstelle ich ein adaptives Formular, das auf Kernkomponenten basiert, mithilfe von XFA-Formularvorlagen?
description: Erfahren Sie, wie Sie ein adaptives Formular mit XFA [!DNL Experience Manager Forms] Formularvorlagen oder XDP-Dateien erstellen.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
exl-id: f3c9b798-8b20-4674-9b96-a3a0b143d947
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 20%

---

# Erstellen eines adaptiven Formulars (Kernkomponenten) basierend auf XFA-Formularvorlagen

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

AEM as a Cloud Service bietet Benutzenden die Möglichkeit, adaptive Forms basierend auf Kernkomponenten mithilfe von XFA-Formularvorlagen (XML Forms Architecture) oder `*.XDP`-Dateien (XML Data Package) zu erstellen. Mit dieser Funktion können Benutzer Zeit sparen, indem sie Felder aus XFA-Formularvorlagen oder XDP-Dateien direkt in adaptive Forms migrieren.

Sie können Ihre XFA-Formularvorlage oder XDP-Dateiformularvorlagen wiederverwenden, um adaptive Forms basierend auf Kernkomponenten zu erstellen. Laden Sie zum erneuten Verwenden eine XFA-Formularvorlage oder XDP-Dateien hoch und verknüpfen Sie sie mit einem adaptiven Formular. Die Elemente der XFA-Formularvorlage oder XDP-Dateien werden für die Verwendung im Content Finder während der Erstellung des adaptiven Formulars verfügbar. Aus der Inhaltssuche können Sie die Elemente der Formularvorlage per Drag-and-Drop auf das Formular ziehen.

## Vorteile der Erstellung von Formularen, die auf XFA-Formularvorlagen oder XDP-Dateien basieren

Einige der Vorteile der Erstellung von Formularen, die auf XFA-Formularvorlagen oder XDP-Dateien basieren, sind:

* **Zeitersparnis**: Sie können vorhandene XFA-Formularvorlagen (XDP-Dateien) schnell wiederverwenden, ohne die Formularstruktur neu erstellen zu müssen, was Zeit und Aufwand während des Erstellungsprozesses spart.
* **Mühelose Migration**: Wenn Sie bereits XFA-Formularvorlagen verwenden, bietet diese Option einen einfachen Migrationspfad zu Adaptive Forms, sodass Sie die Vorteile moderner AEM-Kernkomponenten nutzen können, ohne die vorhandenen Formulardaten und die vorhandene Logik zu verlieren.
* **Verbessertes Benutzererlebnis**: Adaptive Forms sind responsiver und anpassbarer als XFA-Formulare. Durch den Wechsel zu Adaptive Forms können Sie ein benutzerfreundlicheres Erlebnis auf verschiedenen Geräten und Bildschirmgrößen sicherstellen.
* **Verbesserte Integration**: Adaptive Forms lässt sich besser mit anderen Funktionen wie Workflows, Datenbindung und Formularübermittlungen integrieren und ermöglicht so reibungslosere Workflows und eine bessere allgemeine Formularverwaltung.

## Voraussetzungen

Sie benötigen Folgendes, um ein adaptives Formular basierend auf Kernkomponenten mithilfe von XFA-Formularvorlagen oder XDP-Dateien zu erstellen:

* [Aktivieren der Kernkomponenten adaptiver Formulare für Ihre Umgebung](enable-adaptive-forms-core-components.md).
* Es wird empfohlen, sich mit den folgenden Bereichen vertraut zu machen:
   * Erstellen eines adaptiven Formulars
   * XFA (XML Forms Architecture)

## Erstellen eines adaptiven Formulars mit XFA-Formularvorlagen oder XDP-Dateien

Führen Sie die folgenden Schritte aus, um ein adaptives Formular mithilfe von XFA- oder XDP-Formularvorlagen zu erstellen:

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms] Autoreninstanz an.
1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein. Wenn Sie sich angemeldet haben, wählen Sie in der oberen linken Ecke **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.

   ![Forms und Dokumente](/help/forms/assets/create-fdm.png)

1. Wählen **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptive Forms]**.

   ![Erstellen eines adaptiven Formulars](/help/forms/assets/create-af.png)

   Der Assistent für die Formularerstellung wird geöffnet.
1. Wählen Sie auf der Registerkarte {**}Source eine Vorlage aus, die auf Kernkomponenten basiert.**

   ![Auswählen der Vorlage](/help/forms/assets/select-template.png)

   Wenn Sie eine Vorlage auswählen, werden ein Design und eine in der Vorlage angegebene Sendeaktion automatisch ausgewählt und die Schaltfläche **[!UICONTROL Erstellen]** wird aktiviert.

   ![Design auswählen](/help/forms/assets/select-form-theme.png)

1. Wählen Sie **[!UICONTROL Erstellen]**. Ein Dialogfeld zum Angeben von Titel, Name und Speicherort des adaptiven Formulars wird angezeigt.
1. Geben Sie Titel, Namen und Speicherort an.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.
   ![Name und Titel angeben](/help/forms/assets/create-form.png)

   Ein adaptives Formular wird erstellt und im Editor für adaptive Formulare geöffnet. Der Editor zeigt die in der Vorlage verfügbaren Inhalte an.
1. Wählen Sie ![Seiteninformationen](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Eigenschaften öffnen]** aus.

   ![Eigenschaften öffnen](/help/forms/assets/form-properties.png)

   Die Seite mit den Formulareigenschaften wird geöffnet.
1. Wechseln Sie zur Registerkarte **[!UICONTROL Formularmodell]** und wählen Sie **Formularvorlagen**.
1. Wählen Sie die XDP-Datei aus der Dropdown-Liste aus.

   ![XDP-Datei auswählen](/help/forms/assets/select-xdp-file.png)

   Auf dem Bildschirm wird ein Warndialogfeld angezeigt. Klicken Sie **OK**, um fortzufahren.

   ![Dialogfeld „Warnung](/help/forms/assets/fdm-warning.png)

1. Klicken Sie zum Speichern der Eigenschaften auf **[!UICONTROL Speichern und schließen]**.

   >[!NOTE]
   >
   > Nachdem Sie **Formularvorlagen** auf der Registerkarte **Modell** ausgewählt haben, kann sie nicht mehr geändert werden.


Ein adaptives Formular wird erstellt und im Editor für adaptive Formulare geöffnet. Der Editor zeigt die in der Vorlage verfügbaren Inhalte an.  Je nach Typ des adaptiven Formulars werden auf der Registerkarte **[!UICONTROL Datenmodellobjekte“ des Inhaltsbrowsers in der Seitenleiste]** Formularelemente **[!UICONTROL der zugeordneten XFA]** Formularvorlage. Sie können diese Elemente auch per Drag-and-Drop in das zu erstellende adaptive Formular ziehen.

>[!NOTE]
>
> Sie können Skripte für XDP-Formularfelder über die Bereichssymbolleiste des hinzugefügten Felds deaktivieren. Erstellen Sie mithilfe des visuellen Regeleditors Logiken für [ hinzugefügten Felder](/help/forms/rule-editor-core-components.md).

