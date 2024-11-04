---
title: Welche Layoutfunktionen bietet Adaptive Forms basierend auf Kernkomponenten?
description: Layout und Darstellung adaptiver Formulare auf verschiedenen Geräten werden von den Layouteinstellungen geregelt. Machen Sie sich mit den verschiedenen Layouts und ihrer Anwendung vertraut.
feature: Adaptive Forms, Core Components
keywords: Layout des adaptiven Formulars basierend auf Kernkomponenten, verschiedene Layouts für Formulare, AEM für dynamische Formulare, AEM Cloud Service-Formularlayouts, Formularlayouttypen in AEM Kernkomponenten, Layouts für adaptive Formulare
role: User, Developer, Admin
exl-id: dcc01d84-0d39-4fa8-ac47-71a9aba91b1e
source-git-commit: 3ab7ff01201a7da790fe556bfe68c8c76aff9698
workflow-type: tm+mt
source-wordcount: '2107'
ht-degree: 4%

---

# Layout-Funktionen von Adaptive Forms basierend auf Kernkomponenten


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/layout-capabilities-adaptive-forms.html?lang=de) |
| AEM as a Cloud Service (Foundation-Komponenten) | [Hier klicken](/help/forms/layout-capabilities-adaptive-forms.md) |
| AEM as a Cloud Service (Kernkomponenten) | Dieser Artikel |

Adaptive Forms bietet erstklassige Komponenten für das effektive Layout und Design von Formularen. Das Layout steuert, wie Komponenten in einem Formular angezeigt werden. Adaptive Forms unterstützt verschiedene Layouts: Bedienfeld, Assistent, Akkordeon, Registerkarten oben/horizontal und Registerkarten auf linken/vertikalen Registerkarten.

![Layouttypen](/help/forms/assets/generic-layout-hero-image.png){align="center"}

## Voraussetzung

Bevor Sie die verschiedenen Funktionen eines Layouts erkunden, stellen Sie sicher, dass die Kernkomponenten für Ihre Umgebung aktiviert sind. Ausführliche Anweisungen zum Aktivieren von Kernkomponenten für Ihre Umgebung finden Sie [hier klicken](/help/forms/enable-adaptive-forms-core-components.md).

## Adaptive Forms-Layouttypen

Adaptive Formulare, die auf Kernkomponenten basieren, unterstützen die folgenden Layouttypen:
* **Bedienfeld-Layout**
* **Assistentenlayout**
* **Vertikales Layout**
* **Horizontales Layout**
* **Akkordeon-Layout**

>[!BEGINTABS]

>[!TAB Bedienfeldlayout]

Das Bedienfeldlayout ist nützlich, um verwandte Felder so zu organisieren, dass es einfacher ist, zu entsprechenden Inhalten zu navigieren und sie zu finden. Das Bedienfeldlayout ordnet Formularkomponenten innerhalb bestimmter Abschnitte oder Bereiche in einem adaptiven Formular an.

![Bedienfeldlayout](/help/forms/assets/panel-layout.png)

Bedienfeldlayout

Sie können die [Bedienfeldkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) verwenden, um das Bedienfeldlayout in einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren verschiedener Eigenschaften der Bedienfeldkomponente finden Sie im Artikel [Bedienfeldkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) .

>[!TAB Assistent-Layout]

Das Assistentenlayout erleichtert die Arbeit an komplexen Formularen, indem es in unterschiedliche Schritte unterteilt wird. Jeder Schritt stellt einen anderen Teil des Prozesses dar. Benutzer navigieren nacheinander durch die Schritte, oft mit den Schaltflächen **Weiter** und **Zurück**. Sie können das Layout des Assistenten verwenden, um ein Formular zu erstellen, das mehrere Abschnitte oder Schritte umfasst.

![Assistent-Layout](/help/forms/assets/wizard-layout-compare.gif)

Assistentenlayout

Sie können die [Assistentenkomponente](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) verwenden, um das Assistentenlayout in einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Assistentenkomponente finden Sie im Artikel [Assistentenkomponente](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) .

>[!TAB Vertikales Tabulatorlayout]

Das Layout der vertikalen Registerkarten wird auch als Registerkarten im linken Layout bezeichnet. Das Layout der vertikalen Registerkarten organisiert Bedienfelder oder Abschnitte auf der linken Seite eines Formulars. Dies ist ein gängiges Layout für Formulare, bei denen Bereiche/Abschnitte zur einfachen Lese- und Navigation vertikal gestapelt werden.

![Vertikales Layout](/help/forms/assets/vertical-tab.gif)

Layout mit vertikalen Registerkarten

Sie können die Komponente [Vertikale Registerkarten ](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) verwenden, um das Layout der vertikalen Registerkarten in einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Komponente für vertikale Registerkarten finden Sie im Artikel [Komponente für vertikale Registerkarten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) .


>[!TAB Horizontales Registerkarten-Layout]

Das horizontale Layout von Registerkarten wird auch als Registerkarten im oberen Layout bezeichnet. Das Layout der horizontalen Registerkarten ordnet Bedienfelder oder Abschnitte nebeneinander in einer Zeile an. Mit diesem Layout werden die Formularabschnitte über die gesamte Breite des Formulars oder Bedienfelds linear dargestellt.


![Horizontales Layout](/help/forms/assets/horizontal-layout.gif)

Horizontales Registerkartenlayout

Sie können die Komponente [Horizontale Registerkarten ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs) verwenden, um das horizontale Registerkartenlayout in einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Komponente &quot;Horizontale Registerkarten&quot;finden Sie im Artikel [Horizontale Registerkarten-Komponente](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs) .


>[!TAB Accordion-Layout]

Das Akkordeon-Layout zeigt Inhalte in ausblendbaren Abschnitten oder Bereichen in einem adaptiven Formular an. Wenn ein Abschnitt erweitert wird, wird der Inhalt in angezeigt, während andere Abschnitte ausgeblendet bleiben. Dieses Layout eignet sich ideal für die Darstellung großer Datenmengen in kompakter Form.

![Accordion-Layout](/help/forms/assets/accordion-layout-compare.gif)

Akkordeon-Layout

Sie können die [Accordion-Komponente](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) verwenden, um das Akkordeon-Layout in einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Accordion-Komponente finden Sie im Artikel [Accordion-Komponente](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) .

>[!ENDTABS]

Informationen zum Einfügen eines Layouts und zum Hinzufügen von Formularkomponenten finden Sie im Abschnitt [Wie fügt man ein Layout ein und fügt ihm Formularkomponenten hinzu?](#how-to-insert-a-layout-and-add-form-components-to-it)

### Wie wählt man das richtige adaptive Formularlayout aus?

Es ist wichtig, das richtige adaptive Formularlayout auszuwählen, um die Benutzerfreundlichkeit und die Formularfunktionen zu optimieren. Die Tabelle vermittelt Ihnen ein besseres Verständnis der verschiedenen verfügbaren Layoutoptionen und leitet Sie bei der Auswahl des am besten geeigneten Layouts entsprechend Ihren spezifischen Anforderungen und Anwendungsfällen:

| Funktion | Bedienfeldlayout | Assistentenlayout | Registerkarten im Layout der oberen/vertikalen Registerkarten | Layout mit Registerkarten links/Horizontal | Akkordeon-Layout |
|--------------------------|-----------------------------------------------------|----------------------------------------------------|-----------------------------------------------------|--------------------------------------------------------|--------|
| **Zweck** | Gruppiert verwandte Inhalte in verschiedene Abschnitte | Führt Benutzer durch einen mehrstufigen Prozess oder ein Formular | Ermöglicht den Wechsel zwischen Abschnitten/Ansichten auf derselben Seite | Ähnlich wie obere Registerkarten, aber vertikal auf der linken Seite angeordnet | Organisiert Inhalte in ausblendbare Abschnitte |
| **Struktur** | Unterschiedliche Abschnitte | Sequenzielle Schritte/Seiten | Horizontale Registerkarten oben | Vertikale Registerkarten links | Reduzierbare Bereiche/Abschnitte |
| **Navigation** | Klicken Sie auf die Bedienfeldkopfzeilen, um zu navigieren | - Vorwärts: Schaltfläche &quot;Weiter&quot;<br>- Rückwärts: Schaltfläche &quot;Zurück&quot;<br> - Optionale Schritte zum Überspringen | Klicken Sie auf Registerkarten, um Abschnitte zu wechseln | Klicken Sie auf Registerkarten, um Abschnitte zu wechseln | Klicken Sie auf Kopfzeilen zum Erweitern/Reduzieren von Abschnitten |
| **Benutzererlebnis** | Organisieren großer Inhaltsmengen auf verwaltbare Weise | Schrittweise Anleitung zur Reduzierung der Überlastung | Klare, barrierefreie Wechseln zwischen Ansichten | Effizienter Einsatz von vertikalem Raum, immer sichtbaren Registerkarten | Kompakte Ansicht mit erweiterten/reduzierten Abschnitten |
| **Nutzungsszenario** | Komplexe Formulare mit kategorisierten Abschnitten | Einrichten von Prozessen, komplexen Formularen | Organisieren von Einstellungen oder Inhaltskategorien | Dashboards, komplexe Datenansichten | FAQs, Einstellungsmenüs, detaillierte Inhaltsabschnitte |


## Wie fügt man ein Layout ein und fügt Formularkomponenten hinzu?

Das folgende Diagramm zeigt die Schritte zum Einfügen eines Layouts in ein Formular und zum Hinzufügen von Formularkomponenten:

![Workflow zum Hinzufügen eines Layouts und von Formularkomponenten](/help/forms/assets/workflow-to-add-component-to-a-layout.png)

Betrachten Sie das **IT-Anforderungsformular**, das im Abschnitt [Adaptive Forms-Layouttypen](#adaptive-forms-layout-types) angezeigt wird. Das Formular erfasst Informationen von Mitarbeitern, die technische Probleme mit ihrem Netzwerk oder Laptop haben. Er umfasst drei Bereiche:

* **Mitarbeiterdetails**: Das Bedienfeld erfasst Informationen zum Mitarbeiter und enthält drei Textfelder mit den Bezeichnungen Name, E-Mail-ID und Abteilung.

* **Problemdetails**: Das Bedienfeld erfasst Details zum Problem. Es enthält ein Kontrollkästchen für die Problemkategorie mit drei Optionen: Netzwerk, Computer oder Sonstige. Es enthält außerdem zwei Textfelder mit der Bezeichnung &quot;Bitte geben und Kommentare&quot;.

* **Anlagen**: Der Bereich ermöglicht Benutzern das Hochladen von unterstützenden Dokumenten zum Problem.

Im Folgenden wird der schrittweise Prozess zum Einfügen eines Layouts und zum Hinzufügen von Komponenten erläutert. In diesem Beispiel wird ein horizontales Tabulatorlayout in ein Formular eingefügt.

### 1. Fügen Sie eine Layout-Komponente in ein Formular ein

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Instanz an.
1. Wählen Sie oben links **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms &amp; Documents]** aus.
1. Öffnen Sie ein vorhandenes adaptives Formular in einem Bearbeitungsmodus, wenn es bereits erstellt wurde.

   ![Öffnen eines adaptiven Formulars](/help/forms/assets/insert-layout.png)

   Alternativ können Sie auch [ein neues adaptives Formular erstellen](/help/forms/creating-adaptive-form-core-components.md).

1. Suchen Sie den Abschnitt im Formular-Editor, in dem Sie ein Layout hinzufügen können.

   ![Formular-Editor](/help/forms/assets/form-editor.png)
1. Klicken Sie auf das Symbol **Hinzufügen** . Das Symbol ist ein Pluszeichen (+), das die Option zum Hinzufügen neuer Komponenten anzeigt.

   ![Layout einfügen](/help/forms/assets/insert-layout-add-icon.png)

   Wenn Sie auf das Symbol **Hinzufügen** klicken, wird das Dialogfeld **Neue Komponente einfügen** angezeigt, in dem verschiedene Komponenten zum Einfügen angezeigt werden.

   >[!NOTE]
   >
   > Alternativ können Sie auch [die Layout-Komponente ziehen und ablegen](#extra-bytes).

1. Durchsuchen Sie die verfügbaren Komponenten im Dialogfeld und wählen Sie das gewünschte Layout aus der Liste aus. In unserem Beispiel wählen wir die Komponente Horizontale Registerkarten aus, um das Layout der horizontalen Registerkarten einzufügen.

   ![Horizontale Registerkarten auswählen](/help/forms/assets/select-horizontal-tab.png)

   Wenn Sie die Komponente &quot;Horizontale Registerkarten&quot;zum Formular hinzufügen, besteht sie zunächst standardmäßig aus zwei leeren Bedienfeldern namens &quot;Item1&quot;und &quot;Item2&quot;. Sie müssen diesen Bedienfeldern manuell Formularkomponenten hinzufügen.

   ![Horizontale Registerkarten](/help/forms/assets/insert-tabs-on-top.png)

1. Öffnen Sie die Eigenschaften der Komponente &quot;Horizontale Registerkarten&quot;und geben Sie den Namen für die Komponente an.
In diesem Fall fügen wir beispielsweise den Namen der horizontalen Registerkarten-Komponente als IT-Anforderungsformular hinzu.

   ![Name für horizontale Registerkarten hinzufügen](/help/forms/assets/change-name-of-horizontal-tabs.png)

1. Klicken Sie auf **Fertig**.

   ![Horizontale Registerkarten](/help/forms/assets/tabs-on-top-rename-component.png)

Nachdem die Layout-Komponente im Formular hinzugefügt wurde, ändern Sie die Anzahl der Bedienfelder entsprechend den Anforderungen.

### 2. Bedienfelder zum Layout hinzufügen

Fügen Sie der Komponente Horizontale Registerkarten ein neues Bedienfeld hinzu:

1. Öffnen Sie die Eigenschaften der horizontalen Registerkarten-Komponenten und klicken Sie auf die Registerkarte **Elemente** .

   ![Registerkarte &quot;Element&quot;für horizontale Registerkarten](/help/forms/assets/tabs-on-top-items-tab.png)

1. Klicken Sie auf das Symbol **Hinzufügen** , um ein neues Bedienfeld hinzuzufügen.

   ![Neues Bedienfeld hinzufügen](/help/forms/assets/tabs-on-top-add-panel.png)

   Wenn Sie auf das Symbol **Hinzufügen** klicken, wird das Dialogfeld **Neue Komponente einfügen** angezeigt.

1. Wählen Sie die Bedienfeldkomponente aus.

   ![Neues Bedienfeld hinzufügen](/help/forms/assets/tabs-on-top-new-panel.png)

   Wenn Sie die Bedienfeldkomponente auswählen, wird das neue Bedienfeld im horizontalen Layout hinzugefügt.

   ![Neues Bedienfeld hinzufügen](/help/forms/assets/tabs-on-top-add-new-panel.png)

   Geben Sie einen Namen für das neue Bedienfeld ein. Andernfalls können Sie die Eigenschaften der Komponente für horizontale Registerkarten nicht speichern.

1. Geben Sie die Namen der Bedienfelder an, wie in der folgenden Abbildung dargestellt:

   ![Bereichsnamen](/help/forms/assets/tabs-on-tops-panel-name.png)

1. Klicken Sie auf **Fertig**.

   Wenn Sie auf **Fertig** klicken, werden die drei Bedienfelder nebeneinander in einer Zeile angezeigt. Die Bereichsnamen werden für jedes Bedienfeld als Überschriften angezeigt. Sie können jedem Bedienfeld Formularkomponenten hinzufügen.

   ![Bereichsnamen](/help/forms/assets/tabs-on-top-initial-view.png)

   Sie können die Eigenschaften der Bedienfeldkomponente konfigurieren. Beispielsweise enthält das IT-Anforderungsformular keine Bedienfeldtitel. Hier finden Sie die Schritte zum Konfigurieren der Eigenschaften der Bedienfeldkomponente.

1. Öffnen Sie die Eigenschaften des ersten Bedienfelds.

   ![Bedienfeld 1 - Eigenschaften](/help/forms/assets/tabs-on-tops-panel1-properties.png)

1. Aktivieren Sie das Kontrollkästchen **Titel ausblenden** auf der Registerkarte **Einfach** .

   ![Titel ausblenden](/help/forms/assets/tabs-on-top-hide-panel.png)

1. Klicken Sie auf **Fertig**.

Auf ähnliche Weise können Sie auch Titel für die anderen beiden Bedienfelder ausblenden. Anschließend können Sie mit dem Hinzufügen von Formularkomponenten zu jedem Bedienfeld fortfahren.

### 3. Hinzufügen von Formularkomponenten zum Bereich

<!-- You can employ one of the following method to add form components to the panel:
* [Add components to a layout's panel using the Add icon](#add-components-to-a-layouts-panel-using-the-add-icon)
* [Drag and drop components into a layout's panel](#drag-and-drop-components-into-a-layouts-panel) -->

1. Suchen Sie den Abschnitt innerhalb des Bereichs, in dem Sie Komponenten hinzufügen können.
1. Klicken Sie auf das Symbol **Hinzufügen** . Das Symbol ist ein Pluszeichen (+), das die Option zum Hinzufügen neuer Komponenten anzeigt.
   ![Layout einfügen](/help/forms/assets/tabs-on-top-add-component.png)

   Wenn Sie auf das Symbol **Hinzufügen** klicken, wird das Dialogfeld **Neue Komponente einfügen** angezeigt, in dem verschiedene Komponenten zum Einfügen angezeigt werden.

   ![Dialogfeld &quot;Neue Komponente einfügen&quot;](/help/forms/assets/insert-new-component.png)

1. Durchsuchen Sie die verfügbaren Komponenten im angezeigten Dialogfeld und wählen Sie die gewünschte Komponente aus. Wählen Sie in unserem Fall die Komponente Textfeld aus.
1. Öffnen Sie die Eigenschaften der hinzugefügten Komponente und geben Sie deren Namen an. Lassen Sie die Eigenschaften der hinzugefügten Textfeldkomponente bearbeiten und ihren Namen angeben.
   ![Layout einfügen](/help/forms/assets/tabs-on-top-textbox-component.png)
1. Fügen Sie auf ähnliche Weise zwei weitere Textfeldkomponenten hinzu und fügen Sie den Namen der Komponenten als E-Mail-ID und Abteilung hinzu.\
   ![Erstes Bedienfeld](/help/forms/assets/tabs-on-tops-first-panel.png)

   Nachdem die Komponenten im ersten Bereich hinzugefügt wurden, können Sie mit dem Hinzufügen der Komponenten zum zweiten Bereich fortfahren.

1. Um das Bedienfeld zu wechseln, klicken Sie in der Symbolleiste auf **Bedienfeld auswählen** .

   ![Bedienfeld wechseln](/help/forms/assets/tabs-on-top-select-panel.png)

   Wenn Sie auf das Feld **Bedienfeld auswählen** klicken, wird die Liste der hinzugefügten Bedienfelder in der Komponente &quot;Horizontale Registerkarten&quot;angezeigt.

   ![Bedienfeld wechseln](/help/forms/assets/tabs-on-tops-panel2.png)

1. Wählen Sie **2 Bedienfeld** aus der Bedienfeldliste aus und die Ansicht ändert sich vom ersten Bedienfeld zum zweiten Bedienfeld.

   ![Zweites Bedienfeld](/help/forms/assets/tabs-on-top-panel2-component.png)

1. Wiederholen Sie die Schritte aus Schritt 2 bis Schritt 4, um die gewünschten Komponenten in Bedienfeld 2 hinzuzufügen, wie in der folgenden Abbildung dargestellt:

   ![Zweite Bedienfeldkomponenten](/help/forms/assets/panel-2-components.png)

1. Wechseln Sie zum Bereich **3}**, indem Sie die in Schritt 6 und Schritt 7 beschriebenen Schritte ausführen.

1. Wiederholen Sie die Schritte aus Schritt 2 bis Schritt 4, um die gewünschte Komponente in Bedienfeld 3 hinzuzufügen:

   ![Komponenten des dritten Bedienfelds](/help/forms/assets/panel-3-component.png)

1. Klicken Sie oben rechts in Ihrer Authoring-Umgebung auf **[!UICONTROL Vorschau]** .
   ![Horizontales Layout](/help/forms/assets/horizontal-layout.gif)

Sie können auch [ die Komponenten per Drag &amp; Drop verschieben](#extra-bytes), um die Formularkomponenten zu jedem Bedienfeld hinzuzufügen.


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



Sie können die Formularkomponente auch über das Symbol ![Löschsymbol](/help/forms/assets/Smock_Delete_18_N.svg) aus dem Bedienfeld löschen.

![Löschen einer Komponente](/help/forms/assets/delete-component.png)

Sie können bei Bedarf auch die erforderlichen Überprüfungen für die Komponenten hinzufügen.

## Wie wird ein vorhandenes Layout durch ein neues Layout ersetzt?

Sie können ein Layout eines Formulars durch ein neues Layout ersetzen. Dazu gehört die Änderung der Anordnung und Anzeige von Komponenten in einem Formular.

Führen Sie die folgenden Schritte aus, um das vorhandene Layout eines Formulars zu ersetzen:

1. Klicken Sie in der Symbolleiste der Layout-Komponente auf das Symbol Ersetzen und das Dialogfeld **[!UICONTROL Komponente ersetzen]** wird angezeigt.

   ![Layout ersetzen](/help/forms/assets/replace-layout.png)

1. Wählen Sie das gewünschte Layout im Dialogfeld **[!UICONTROL Komponente ersetzen]** aus.

   ![Dialogfeld &quot;Komponente ersetzen&quot;](/help/forms/assets/replace-component.png)

   Nach Auswahl des Layouts ändert sich die Anordnung der Komponenten im Layout entsprechend. Wählen Sie beispielsweise die Komponente der vertikalen Registerkarten im Dialogfeld **[!UICONTROL Komponente ersetzen]** aus. Die Anordnung des Bedienfelds ändert sich in Registerkarten auf der linken Seite:

   ![Vertikales Layout](/help/forms/assets/vertical-tab.gif)

## Zusätzliche Byte

So ziehen Sie Komponenten per Drag-and-Drop in den Formular-Editor:

1. Suchen Sie den Abschnitt, in dem Sie Komponenten hinzufügen können.
1. Navigieren Sie zum linken Bereich in Ihrer Authoring-Umgebung und klicken Sie auf **Komponenten**.

   ![Komponentenbereich](/help/forms/assets/add-new-component.png)

   Wenn Sie auf die Option **Komponenten** klicken, wird die Liste der verfügbaren Komponenten angezeigt.

   ![Komponentenbereich](/help/forms/assets/add-new-component2.png)

1. Durchsuchen Sie die verfügbaren Komponenten und wählen Sie die gewünschte Komponente aus.

1. Ziehen Sie die Komponente, indem Sie auf die ausgewählte Komponente klicken und sie gedrückt halten, und ziehen Sie sie dann in den Bedienfeldbereich, um sie zu platzieren.

1. Ziehen Sie die Komponente in das Bedienfeld, indem Sie die Maus loslassen.

## Nächste Schritte

Sobald Sie die verschiedenen Layoutfunktionen für ein adaptives Formular kennen, das auf Kernkomponenten basiert, können Sie mit den nächsten Schritten fortfahren:

* [Erstellen Sie Ihr erstes adaptives Formular basierend auf Kernkomponenten](/help/forms/creating-adaptive-form-core-components.md)
* [Erstellen und Verwenden von Designs für adaptive Formulare](/help/forms/using-themes-in-core-components.md)



## Siehe auch

{{see-also}}
