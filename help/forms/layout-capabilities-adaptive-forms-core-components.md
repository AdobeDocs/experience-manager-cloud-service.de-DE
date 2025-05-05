---
title: Welche Layout-Funktionen bietet adaptive Forms basierend auf Kernkomponenten?
description: Layout und Darstellung adaptiver Formulare auf verschiedenen Geräten werden von den Layouteinstellungen geregelt. Machen Sie sich mit den verschiedenen Layouts und ihrer Anwendung vertraut.
feature: Adaptive Forms, Core Components
keywords: Layout adaptiver Formulare basierend auf Kernkomponenten, Verschiedene Layouts für Formulare, Layouts für dynamische Formulare AEM, Layouts für AEM Cloud Service-Formulare, Formularlayouttypen in AEM-Kernkomponenten, Layouts adaptiver Formulare
role: User, Developer, Admin
exl-id: dcc01d84-0d39-4fa8-ac47-71a9aba91b1e
source-git-commit: 7cb963794ca0d7a12d8007564c9fd6e49b53d5c4
workflow-type: tm+mt
source-wordcount: '2104'
ht-degree: 7%

---

# Layout-Möglichkeiten für adaptive Forms basierend auf Kernkomponenten


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/layout-capabilities-adaptive-forms.html?lang=de) |
| AEM as a Cloud Service (Foundation-Komponenten) | [Hier klicken](/help/forms/layout-capabilities-adaptive-forms.md) |
| AEM as a Cloud Service (Kernkomponenten) | Dieser Artikel |

Adaptive Forms bietet erstklassige Komponenten zum effektiven Layout und Design der Formulare. Das Layout steuert, wie Komponenten in einem Formular angezeigt werden. Adaptive Forms unterstützt verschiedene Layouts: Bedienfeld, Assistent, Akkordeon, Registerkarten oben/horizontal und Registerkarten links/vertikal.

<!-- ![Types of Layout](/help/forms/assets/generic-layout-hero-image.png){align="center"}-->

## Voraussetzung

Bevor Sie die verschiedenen Funktionen eines Layouts untersuchen, stellen Sie sicher, dass Kernkomponenten für Ihre Umgebung aktiviert sind. Detaillierte Anweisungen zum Aktivieren von Kernkomponenten für Ihre Umgebung finden Sie [hier](/help/forms/enable-adaptive-forms-core-components.md).

## Layouttypen für adaptive Forms

Adaptive Formulare, die auf Kernkomponenten basieren, unterstützen die folgenden Layouttypen:
* **Bedienfeld-Layout**
* **Assistenten-Layout**
* **Vertikales Layout**
* **Horizontales Layout**
* **Akkordeon-Layout**

>[!BEGINTABS]

>[!TAB Bedienfeld-Layout]

Das Bereichslayout ist nützlich, um verwandte Felder so zu organisieren, dass die Navigation und das Auffinden entsprechender Inhalte erleichtert werden. Das Bereichslayout ordnet Formularkomponenten in separaten Bereichen oder Bereichen in einem adaptiven Formular an.

![Bedienfeld-Layout](/help/forms/assets/panel-layout.png)

Bedienfeldlayout

Sie können die [Bedienfeld-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) verwenden, um das Bedienfeld-Layout einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren verschiedener Eigenschaften der Bedienfeldkomponente finden Sie im Artikel [Bedienfeldkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) .

>[!TAB Assistentenlayout]

Das Assistenten-Layout vereinfacht ein komplexes Formular, indem es in verschiedene Schritte unterteilt wird. Jeder Schritt stellt einen anderen Teil des Prozesses dar, und Benutzende navigieren nacheinander durch die Schritte, häufig mit den Schaltflächen **Weiter** und **Zurück**. Sie können das Assistenten-Layout verwenden, um ein Formular zu erstellen, das mehrere Abschnitte oder Schritte umfasst.

![Assistentenlayout](/help/forms/assets/wizard-layout-compare.gif)

Assistenten-Layout

Sie können die Komponente [Assistent](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) verwenden, um das Assistenten-Layout einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Assistenten-Komponente finden Sie im Artikel [Assistenten-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) .

>[!TAB Layout für vertikale Registerkarten]

Das Layout Vertikale Registerkarten wird auch als Registerkarten im linken Layout bezeichnet. Mit dem Layout Vertikale Registerkarten werden Bedienfelder oder Abschnitte auf der linken Seite eines Formulars angeordnet. Dies ist ein gängiges Layout für Formulare, bei dem Bereiche/Abschnitte vertikal gestapelt sind, um die Lektüre und Navigation zu erleichtern.

![Vertikales Layout](/help/forms/assets/vertical-tab.gif)

Layout vertikaler Registerkarten

Sie können die Komponente [Vertikale Registerkarten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) verwenden, um das Layout Vertikale Registerkarten einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Komponente „Vertikale Registerkarten“ finden Sie im Artikel [Komponente „Vertikale Registerkarten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) .


>[!TAB Horizontales Registerkarten-Layout]

Das Layout „Horizontale Registerkarten“ wird auch als Layout „Registerkarten oben“ bezeichnet. Das Layout Horizontale Registerkarten ordnet Bedienfelder oder Abschnitte nebeneinander in einer Zeile an. Dieses Layout stellt die Formularabschnitte linear über die Breite des Formulars oder Bereichs dar.


![Horizontales Layout](/help/forms/assets/horizontal-layout.gif)

Layout horizontaler Registerkarten

Sie können die Komponente [Horizontale Registerkarten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs) verwenden, um das Layout Horizontale Registerkarten einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Komponente „Horizontale Registerkarten“ finden Sie im Artikel [Komponente „Horizontale Registerkarten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs) .


>[!TAB Akkordeon-Layout]

Das Akkordeon-Layout zeigt Inhalte in ausblendbaren Abschnitten oder Bereichen in einem adaptiven Formular an. Wenn ein Abschnitt erweitert wird, wird der Inhalt darin angezeigt, während andere Abschnitte reduziert bleiben. Dieses Layout ist ideal für die Anzeige großer Informationsmengen in kompakter Form.

![Akkordeon-Layout](/help/forms/assets/accordion-layout-compare.gif)

Akkordeon-Layout

Sie können die [Akkordeon-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) verwenden, um das Akkordeon-Layout in einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Akkordeon-Komponente finden Sie im Artikel [Akkordeon-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) .

>[!ENDTABS]

Informationen zum Einfügen eines Layouts und Hinzufügen von Formularkomponenten finden Sie im Abschnitt mit dem Titel [Wie füge ich ein Layout ein und füge Formularkomponenten hinzu?](#how-to-insert-a-layout-and-add-form-components-to-it)

### Wie wählt man das richtige adaptive Formular-Layout?

Es ist wichtig, das richtige Layout für adaptive Formulare auszuwählen, um das Benutzererlebnis und die Formularfunktionen zu optimieren. Die Tabelle hilft Ihnen, die verschiedenen verfügbaren Layout-Optionen zu verstehen, und führt Sie bei der Auswahl des am besten geeigneten Layouts basierend auf Ihren spezifischen Anforderungen und Anwendungsfällen:

| Funktion | Bedienfeldlayout | Assistenten-Layout | Registerkarten am oberen/vertikalen Registerkarten-Layout | Registerkarten links/horizontal Registerkarten-Layout | Akkordeon-Layout |
|--------------------------|-----------------------------------------------------|----------------------------------------------------|-----------------------------------------------------|--------------------------------------------------------|--------|
| **Zweck** | Gruppiert verwandte Inhalte in separate Abschnitte | Führt Benutzer durch einen mehrstufigen Prozess oder ein mehrstufiges Formular | Ermöglicht das Wechseln zwischen Abschnitten/Ansichten auf derselben Seite | Ähnlich wie obere Registerkarten, aber vertikal auf der linken Seite angeordnet | Organisiert Inhalte in ausblendbaren Abschnitten |
| **Struktur** | Unterschiedliche Abschnitte | Sequenzielle Schritte/Seiten | Horizontale Registerkarten oben | Vertikale Registerkarten links | Reduzierbare Bereiche/Abschnitte |
| **Navigation** | Klicken Sie auf die Panel-Kopfzeilen, um zu navigieren | - Vorwärts: „Weiter“-Taste<br>- Rückwärts: „Zurück“-Schaltfläche<br>- Optionale Schritte überspringen | Auf Registerkarten klicken, um Abschnitte zu wechseln | Auf Registerkarten klicken, um Abschnitte zu wechseln | Auf Kopfzeilen klicken, um Abschnitte zu erweitern/reduzieren |
| **Benutzererlebnis** | Organisiert große Inhaltsmengen auf überschaubare Weise | Schritt-für-Schritt-Anleitung zur Verringerung der Überlastung | Übersichtlicher, barrierefreier Wechsel zwischen Ansichten | Effiziente Nutzung von vertikalem Platz, immer sichtbare Registerkarten | Kompakte Ansicht mit erweiterten/reduzierten Abschnitten |
| **Nutzungsszenario** | Komplexe Formulare mit kategorisierten Abschnitten | Einrichtungsprozesse, komplexe Formulare | Organisieren von Einstellungen oder Inhaltskategorien | Dashboards, komplexe Datenansichten | Häufig gestellte Fragen, Einstellungsmenüs, detaillierte Inhaltsabschnitte |


## Einfügen eines Layouts und Hinzufügen von Formularkomponenten?

Im folgenden Diagramm werden die Schritte zum Einfügen eines Layouts in ein Formular und zum Hinzufügen von Formularkomponenten dargestellt:

![Workflow zum Hinzufügen von Layout- und Formularkomponenten](/help/forms/assets/workflow-to-add-component-to-a-layout.png)

Betrachten Sie das **IT-Anforderungsformular** das im Abschnitt [Adaptive Forms-Layouttypen](#adaptive-forms-layout-types) angezeigt wird. Das Formular sammelt Informationen von Mitarbeitern, die technische Probleme im Zusammenhang mit ihrem Netzwerk oder Laptop haben. Es umfasst drei Bereiche:

* **Mitarbeiterdetails**: Das Bedienfeld sammelt Informationen über den Mitarbeiter und enthält drei Textfelder mit der Bezeichnung Name, E-Mail-ID und Abteilung.

* **Problemdetails**: Das Bedienfeld erfasst Details zum Problem. Es enthält ein Kontrollkästchen für die Problemkategorie mit drei Optionen: Netzwerk, Computer oder Sonstige. Es enthält auch zwei Textfelder mit der Beschriftung Bitte und Anmerkungen.

* **Anlagen**: In diesem Bedienfeld können Benutzende unterstützende Dokumente hochladen, die mit dem Problem in Zusammenhang stehen.

Im Folgenden wird der schrittweise Prozess zum Einfügen eines Layouts und Hinzufügen von Komponenten erläutert. In diesem Beispiel wird ein horizontales Registerkarten-Layout in ein Formular eingefügt.

### 1. Einfügen einer Layout-Komponente in ein Formular

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Instanz an.
1. Wählen Sie oben links **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms und Dokumente]**.
1. Öffnen Sie ein vorhandenes adaptives Formular im Bearbeitungsmodus, wenn es bereits erstellt wurde.

   ![Öffnen eines adaptiven Formulars](/help/forms/assets/insert-layout.png)

   Alternativ können Sie auch [neues adaptives Formular erstellen](/help/forms/creating-adaptive-form-core-components.md).

1. Suchen Sie den Abschnitt im Formular-Editor, mit dem Sie ein Layout hinzufügen können.

   ![Formular-Editor](/help/forms/assets/form-editor.png)
1. Klicken Sie auf das Symbol **Hinzufügen**. Das Symbol ist ein Pluszeichen (+). Es steht für die Option zum Hinzufügen neuer Komponenten.

   ![Layout einfügen](/help/forms/assets/insert-layout-add-icon.png)

   Wenn Sie auf das Symbol **Hinzufügen** klicken, wird das Dialogfeld **Neue Komponente einfügen** angezeigt, in dem verschiedene Komponenten zum Einfügen angezeigt werden.

   >[!NOTE]
   >
   > Alternativ können Sie auch [die Layout-Komponente per Drag-and-Drop verschieben](#extra-bytes).

1. Durchsuchen Sie die verfügbaren Komponenten im Dialogfeld und wählen Sie das gewünschte Layout in der Liste aus. In unserem Fall wählen wir die Komponente Horizontale Registerkarten aus, um das Layout Horizontale Registerkarten einzufügen.

   ![Horizontale Registerkarten auswählen](/help/forms/assets/select-horizontal-tab.png)

   Wenn Sie die Komponente „Horizontale Registerkarten“ zum Formular hinzufügen, besteht es standardmäßig aus zwei leeren Bereichen, einem Element1 und einem Element2. Sie müssen diesen Bedienfeldern manuell Formularkomponenten hinzufügen.

   ![Horizontale Registerkarten](/help/forms/assets/insert-tabs-on-top.png)

1. Öffnen Sie die Eigenschaften der Komponente Horizontale Registerkarten und geben Sie den Namen für die Komponente an.
In diesem Fall fügen wir beispielsweise den Namen der horizontalen Registerkarten-Komponente als IT-Anfrageformular hinzu.

   ![Name für horizontale Registerkarten hinzufügen](/help/forms/assets/change-name-of-horizontal-tabs.png)

1. Klicken Sie auf **Fertig**.

   ![Horizontale Registerkarten](/help/forms/assets/tabs-on-top-rename-component.png)

Nachdem die Layout-Komponente zum Formular hinzugefügt wurde, ändern Sie die Anzahl der Bedienfelder entsprechend den Anforderungen.

### 2. Bedienfelder zum Layout hinzufügen

Hinzufügen eines neuen Bedienfelds zur horizontalen Registerkarten-Komponente:

1. Öffnen Sie die Komponenteneigenschaften der horizontalen Registerkarten und klicken Sie auf die Registerkarte **Elemente** .

   ![Elementregisterkarte für horizontale Registerkarten](/help/forms/assets/tabs-on-top-items-tab.png)

1. Klicken Sie auf **Hinzufügen**, um ein neues Bedienfeld hinzuzufügen.

   ![Neues Bedienfeld hinzufügen](/help/forms/assets/tabs-on-top-add-panel.png)

   Wenn Sie auf das Symbol **Hinzufügen** klicken, wird **Dialogfeld „Neue Komponente einfügen** angezeigt.

1. Wählen Sie die Bedienfeldkomponente aus.

   ![Neues Bedienfeld hinzufügen](/help/forms/assets/tabs-on-top-new-panel.png)

   Wenn Sie die Bedienfeldkomponente auswählen, wird das neue Bedienfeld im horizontalen Layout hinzugefügt.

   ![Neues Bedienfeld hinzufügen](/help/forms/assets/tabs-on-top-add-new-panel.png)

   Geben Sie einen Namen für das neue Bedienfeld ein. Andernfalls können Sie die Eigenschaften der horizontalen Registerkarten-Komponente nicht speichern.

1. Geben Sie die Namen der Bereiche an, wie in der folgenden Abbildung dargestellt:

   ![Bereichsnamen](/help/forms/assets/tabs-on-tops-panel-name.png)

1. Klicken Sie auf **Fertig**.

   Wenn Sie auf **Fertig** klicken, werden die drei Bedienfelder nebeneinander in einer Zeile angezeigt. Die Bereichsnamen werden als Überschriften für jedes Bedienfeld angezeigt, und Sie können jedem Bedienfeld Formularkomponenten hinzufügen.

   ![Bereichsnamen](/help/forms/assets/tabs-on-top-initial-view.png)

   Sie können die Eigenschaften der Bedienfeldkomponente konfigurieren. Beispielsweise enthält das IT-Anfrageformular keine Bereichstitel. Im Folgenden finden Sie die Schritte zum Konfigurieren der Eigenschaften einer Bereichskomponente.

1. Öffnen Sie die Eigenschaften des ersten Bedienfelds.

   ![Eigenschaften von Panel 1](/help/forms/assets/tabs-on-tops-panel1-properties.png)

1. Aktivieren Sie das Kontrollkästchen **Titel ausblenden** auf der Registerkarte **Allgemein**.

   ![Titel ausblenden](/help/forms/assets/tabs-on-top-hide-panel.png)

1. Klicken Sie auf **Fertig**.

Außerdem können Sie Titel für die beiden anderen Bedienfelder ausblenden. Anschließend können Sie jedem Bedienfeld Formularkomponenten hinzufügen.

### 3. Hinzufügen von Formularkomponenten zum Bedienfeld

<!-- You can employ one of the following method to add form components to the panel:
* [Add components to a layout's panel using the Add icon](#add-components-to-a-layouts-panel-using-the-add-icon)
* [Drag and drop components into a layout's panel](#drag-and-drop-components-into-a-layouts-panel) -->

1. Suchen Sie den Abschnitt innerhalb des Bedienfelds, in dem Sie Komponenten hinzufügen können.
1. Klicken Sie auf das Symbol **Hinzufügen**. Das Symbol ist ein Pluszeichen (+). Es steht für die Option zum Hinzufügen neuer Komponenten.
   ![Layout einfügen](/help/forms/assets/tabs-on-top-add-component.png)

   Wenn Sie auf das Symbol **Hinzufügen** klicken, wird das Dialogfeld **Neue Komponente einfügen** angezeigt, in dem verschiedene Komponenten zum Einfügen angezeigt werden.

   ![Dialogfeld „Neue Komponente einfügen“](/help/forms/assets/insert-new-component.png)

1. Durchsuchen Sie die verfügbaren Komponenten im angezeigten Dialogfeld und wählen Sie die gewünschte Komponente aus. Wählen Sie in unserem Fall die Komponente Textfeld aus.
1. Öffnen Sie die Eigenschaften der hinzugefügten Komponente und geben Sie ihren Namen an. Bearbeiten Sie die Eigenschaften der hinzugefügten Textfeld-Komponente und geben Sie deren Namen an.
   ![Layout einfügen](/help/forms/assets/tabs-on-top-textbox-component.png)
1. Fügen Sie auf ähnliche Weise zwei weitere Textfeld-Komponenten hinzu und benennen Sie die hinzugefügten Komponenten als E-Mail-ID und Abteilung.\
   ![Erstes Bedienfeld](/help/forms/assets/tabs-on-tops-first-panel.png)

   Nachdem die Komponenten im ersten Bedienfeld hinzugefügt wurden, können Sie mit dem Hinzufügen der Komponenten zum zweiten Bedienfeld fortfahren.

1. Um das Bedienfeld zu wechseln, klicken Sie **der Symbolleiste auf** Bedienfeld auswählen“.

   ![Schalttafel](/help/forms/assets/tabs-on-top-select-panel.png)

   Wenn Sie auf **Bedienfeld auswählen** klicken, wird die Liste der hinzugefügten Bedienfelder in der Komponente „Horizontale Registerkarten“ angezeigt.

   ![Schalttafel](/help/forms/assets/tabs-on-tops-panel2.png)

1. Wählen Sie **2 Panel** aus der Bereichsliste aus, und die Ansicht ändert sich vom ersten Bedienfeld zum zweiten Bedienfeld.

   ![Zweites Bedienfeld](/help/forms/assets/tabs-on-top-panel2-component.png)

1. Wiederholen Sie die Schritte von Schritt 2 bis Schritt 4, um die gewünschten Komponenten in Bedienfeld 2 hinzuzufügen, wie in der folgenden Abbildung dargestellt:

   ![Komponenten des zweiten Bedienfelds](/help/forms/assets/panel-2-components.png)

1. Wechseln Sie zum **3** Panel, indem Sie die in Schritt 6 und Schritt 7 beschriebenen Schritte ausführen.

1. Wiederholen Sie die Schritte von Schritt 2 bis Schritt 4, um die gewünschte Komponente in Bedienfeld 3 hinzuzufügen:

   ![Komponenten des dritten Bedienfelds](/help/forms/assets/panel-3-component.png)

1. Klicken Sie **[!UICONTROL Vorschau]** in der oberen rechten Ecke Ihrer Authoring-Umgebung.
   ![Horizontales Layout](/help/forms/assets/horizontal-layout.gif)

Sie können die [ auch ziehen und ablegen, ](#extra-bytes) die Formularkomponenten jedem Bedienfeld hinzuzufügen.


<!-- #### Drag and drop components into a layout's panel 

1. Locate the section within the panel that allows you to add components. 
2. Navigate to the left panel within your authoring environment and click **Components**.

    ![Component Panel](/help/forms/assets/add-new-component.png){width="200" align="center"}

    When you click the **Components** option, the list of the available components appears.   

    ![Component Panel](/help/forms/assets/add-new-component2.png){width="200" align="center"}

3. Browse the available components and select the Text Box component.

4. Drag the component by clicking and holding the selected component, then drag it over to the panel area to place it.

5. Drop the component into the panel by releasing the mouse. 

6. Open the properties of the added Text Box component and specify its name as Name.
    ![Insert layout](/help/forms/assets/tabs-on-top-textbox-component.png){width="200" align="center"}
7. Similarly, add two more Text Box components and name added the components as Email ID and Department.   
    ![First Panel](/help/forms/assets/tabs-on-tops-first-panel.png){width="200" align="center"}

    Now that the components in the first panel have been added, you can proceed with adding the components to the second panel. 

8. To switch the panel, click **Select Panel** from the toolbar. 

    ![Switch Panel](/help/forms/assets/tabs-on-top-select-panel.png){width="200" align="center"}

    When you click the **Select Panel**, the list of the added panels in the Horizontal Tabs component appears.

    ![Switch Panel](/help/forms/assets/tabs-on-tops-panel2.png){width="200" align="center"}

9. Select **2 Panel** from the panel list and the view changes from the first panel to the second panel.

    ![Second Panel](/help/forms/assets/tabs-on-top-panel2-component.png){width="200" align="center"}

10. Repeat the steps outlined from Step 2 to Step 6 for adding the desired components in panel 2 as shown in the below figure:   

     ![Second Panel components](/help/forms/assets/panel-2-components.png){width="200" align="center"}

11. Switch to the **3 Panel** by following the steps outlined in Step 8 and Step 9.

12. Repeat the steps outlined from Step 2 to Step 6 for adding the desired component in panel 3:

    ![Third Panel components](/help/forms/assets/panel-3-component.png){width="200" align="center"} 

    -->



Sie können eine Formularkomponente auch mithilfe des Symbols ![Löschen](/help/forms/assets/Smock_Delete_18_N.svg) aus dem Bedienfeld löschen.

![Löschen einer Komponente](/help/forms/assets/delete-component.png)

Sie können bei Bedarf auch die erforderlichen Validierungen für die Komponenten hinzufügen.

## Ersetzen eines vorhandenen Layouts durch ein neues Layout

Sie können ein Layout eines Formulars durch ein neues Layout ersetzen, wobei Sie die Art und Weise ändern müssen, wie Komponenten innerhalb eines Formulars angeordnet und angezeigt werden.

Führen Sie die folgenden Schritte aus, um das vorhandene Layout eines Formulars zu ersetzen:

1. Klicken Sie in der Symbolleiste der Layout-Komponente auf das Symbol „Ersetzen **[!UICONTROL und das Dialogfeld „Komponente]**&quot; wird angezeigt.

   ![Layout ersetzen](/help/forms/assets/replace-layout.png)

1. Wählen Sie das gewünschte Layout im Dialogfeld **[!UICONTROL Komponente ersetzen]** aus.

   ![Dialogfeld „Komponente ersetzen“](/help/forms/assets/replace-component.png)

   Nach Auswahl des Layouts ändert sich entsprechend die Anordnung der Komponenten innerhalb des Layouts. Wählen Sie beispielsweise die Komponente Vertikale Registerkarten im Dialogfeld **[!UICONTROL Komponente ersetzen]** aus. Die Anordnung des Bedienfelds ändert sich in Registerkarten auf der linken Seite:

   ![Vertikales Layout](/help/forms/assets/vertical-tab.gif)

## Zusätzliche Bytes

So ziehen Sie Komponenten per Drag-and-Drop in den Formulareditor:

1. Suchen Sie den Abschnitt, in dem Sie Komponenten hinzufügen können.
1. Navigieren Sie zum linken Bedienfeld in Ihrer Authoring-Umgebung und klicken Sie auf **Komponenten**.

   ![Bedienfeld „Komponente](/help/forms/assets/add-new-component.png)

   Wenn Sie auf die Option **Komponenten** klicken, wird die Liste der verfügbaren Komponenten angezeigt.

   ![Bedienfeld „Komponente](/help/forms/assets/add-new-component2.png)

1. Durchsuchen Sie die verfügbaren Komponenten und wählen Sie die gewünschte Komponente aus.

1. Ziehen Sie die Komponente, indem Sie die ausgewählte Komponente anklicken und gedrückt halten, und ziehen Sie sie dann in den Bereich des Bedienfelds, um sie zu platzieren.

1. Ziehen Sie die Komponente in das Bedienfeld, indem Sie die Maus loslassen.

## Nächste Schritte

Sobald Sie mit den verschiedenen Layout-Funktionen für ein adaptives Formular, das auf Kernkomponenten basiert, vertraut sind, können Sie mit den nächsten Schritten fortfahren:

* [Erstellen Ihres ersten adaptiven Formulars basierend auf Kernkomponenten](/help/forms/creating-adaptive-form-core-components.md)
* [Erstellen und Verwenden von Designs für adaptive Formulare](/help/forms/using-themes-in-core-components.md)



## Siehe auch

{{see-also}}
