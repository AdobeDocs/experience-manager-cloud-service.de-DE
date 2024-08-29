---
title: Wie können Sie mit der Komponente "Forms Portal verknüpfen"Links zu Formularen auf der AEM Sites-Seite hinzufügen?
description: Erfahren Sie, wie Sie der AEM Sites-Seite Links für Formulare hinzufügen.
feature: Adaptive Forms, Core Components
role: User, Developer, Admin
source-git-commit: 31f18027d856cbd161457c4a01d6c7c17d1c2b89
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 16%

---


# Hinzufügen von Formular-Links zur Seite &quot;Sites&quot;

Im Szenario mit der Bankwebsite verbessert die Komponente **Link** Forms Portal die Navigation, indem Benutzer zu bestimmten Formularen in verschiedenen Abschnitten der Website geleitet werden. Es bietet direkte Verweise auf Formulare wie Kreditanträge, Formulare zur Kontoeröffnung oder Feedback-Umfragen, die strategisch auf der gesamten Website platziert werden. Die Komponente **Link** fügt Links ein, die Benutzer auf der Seite &quot;Sites&quot;zu einer bestimmten adaptiven Forms weiterleiten. Anonyme Benutzer können beispielsweise auf der Website der Bank auf ein allgemeines Anfrageformular zugreifen, angemeldete Benutzer hingegen können direkt auf sicherere Formulare wie Kreditanträge oder Transaktionsgenehmigungsformulare zugreifen.

![Link-Symbol](/help/forms/assets/link-forms.png)

## Voraussetzung

Bevor Sie die verschiedenen Funktionen einer Forms Portal-Komponente kennenlernen, stellen Sie sicher, dass Kernkomponenten für Ihre Umgebung aktiviert sind. Ausführliche Anweisungen zum Aktivieren von Kernkomponenten für Ihre Umgebung finden Sie [hier klicken](/help/forms/enable-adaptive-forms-core-components.md).

Nach der Bereitstellung der neuesten Kernkomponenten in Ihrer Umgebung können Sie auf die Forms Portal-Komponenten in Ihrer Authoring-Umgebung zugreifen.

## Fügen Sie die Komponente Link zu Ihrer Sites-Seite hinzu

So fügen Sie die Portalkomponente **Link** zu Ihrer Sites-Seite hinzu:

1. Öffnen Sie die AEM Sites-Seite im Modus **Bearbeiten** .
1. Navigieren Sie zu **[!UICONTROL Seiteninformationen]** => **[!UICONTROL Vorlage bearbeiten]**
   ![Vorlagenrichtlinie bearbeiten](/help/forms/assets/save-form-as-draft-edit-template.png)

1. Klicken Sie auf die **[!UICONTROL Richtlinie]** und aktivieren Sie das Kontrollkästchen **[!UICONTROL Link]** unter dem AEM **[Archetyp Projektname] - Forms und Kommunikationsportal**.

   ![Richtlinienauswahl](/help/forms/assets/add-link.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**.
1. Öffnen Sie nun die AEM Sites-Seite im Authoring-Modus erneut.
1. Suchen Sie den Abschnitt im Seiteneditor, in dem Sie die Forms Portal-Komponente hinzufügen können.

1. Klicken Sie auf das Symbol **Hinzufügen** . Das Symbol ist ein Pluszeichen (+), das die Option zum Hinzufügen neuer Komponenten anzeigt.

   Wenn Sie auf das Symbol **Hinzufügen** klicken, wird das Dialogfeld **Neue Komponente einfügen** angezeigt, in dem verschiedene Komponenten zum Einfügen angezeigt werden.

   >[!NOTE]
   >
   > Alternativ können Sie die Komponente auch per Drag-and-Drop verschieben.

1. Durchsuchen Sie die verfügbaren Komponenten im Dialogfeld und wählen Sie die gewünschte Komponente aus der Liste aus. Wählen Sie beispielsweise die Komponente **Link** aus der Liste aus, um die Komponente **Link** Forms Portal hinzuzufügen.

   ![Komponente &quot;Link&quot;](/help/forms/assets/add-link-in-sites.png)

Konfigurieren Sie jetzt die Eigenschaften der Komponente **Link** .

## Eigenschaften der Komponente &quot;Link&quot;

Sie können die Komponenteneigenschaften von **Link** einfach über das Dialogfeld &quot;Konfigurieren&quot;anpassen, um ein nahtloses Benutzererlebnis zu gewährleisten. Wählen Sie zum Konfigurieren die Komponente und dann das ![Symbol „Konfigurieren“](assets/configure_icon.png). Das Dialogfeld **[!UICONTROL Link]** wird geöffnet.

### Registerkarte &quot;Anzeigen&quot;

![Registerkarte &quot;Anzeige&quot;](/help/forms/assets/link-asset-tab.png)

Geben Sie auf der Registerkarte **[!UICONTROL Anzeige]** die Link-Beschriftung und die QuickInfo ein, um die Identifizierung der durch diesen Link dargestellten Formulare zu erleichtern.

### Registerkarte &quot;Asset Info&quot;

![Registerkarte &quot;Assets Info&quot;](/help/forms/assets/link-asset-info.png)

Geben Sie auf der Registerkarte **[!UICONTROL Asset-Informationen]** den Repository-Pfad an, unter dem das Asset gespeichert ist.

### Registerkarte &quot;Abfrageparameter&quot;

![Registerkarte &quot;Abfrageparameter&quot;](/help/forms/assets/link-query-tab.png)

Geben Sie auf der Registerkarte **[!UICONTROL Abfrageparameter]** die zusätzlichen Parameter im Schlüssel-Wert-Paarformat an. Wenn auf den Link geklickt wird, werden diese zusätzlichen Parameter zusammen mit dem Formular übergeben.

## Anzeigen von Formular-Links auf der Seite &quot;Sites&quot;mithilfe der Komponente &quot;Link&quot;

Zeigen Sie eine Vorschau der Seite &quot;Sites&quot;an, um den Link zu einem adaptiven Formular anzuzeigen, der auf der Registerkarte **Assets Info** Eigenschaften der Komponente **Link** angegeben ist. Durch Klicken auf den Link wird das Formular auf dem Bildschirm für Benutzer angezeigt, die dann anhand der Berechtigungen darauf zugreifen können.

![Registerkarte &quot;Abfrageparameter&quot;](/help/forms/assets/link-forms.png)

## Verwandte Artikel

{{forms-portal-see-also}}

## Siehe auch {#see-also}

{{see-also}}
