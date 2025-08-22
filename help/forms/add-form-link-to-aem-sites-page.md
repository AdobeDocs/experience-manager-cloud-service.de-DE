---
title: Wie werden Formular-Links auf der AEM Sites-Seite mit der Formularportal-Komponente „Link“ hinzugefügt?
description: Erfahren Sie, wie Sie Formular-Links zur AEM Sites-Seite hinzufügen können.
feature: Adaptive Forms, Core Components
role: User, Developer, Admin
exl-id: a55d0776-8827-46cc-9625-5d6f5f6bda3b
source-git-commit: 16b1e7ffa4e3812e9207bb283c63029939f7d14e
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 97%

---

# Hinzufügen von Formular-Links zu einer Sites-Seite

Im Szenario mit der Website einer Bank verbessert die Formularportal-Komponente **Link** die Navigation, indem Benutzende zu bestimmten Formularen in verschiedenen Abschnitten der Website geleitet werden. Sie stellt direkte Verweise auf Formulare bereit, z. B. Kreditanträge, Formulare zur Kontoeröffnung oder Feedback-Umfragen, die strategisch auf der gesamten Website platziert werden. Mit der Komponente **Link** werden Links eingefügt, die Benutzende auf der Sites-Seite zu bestimmten adaptiven Formularen weiterleiten. Beispielsweise können anonyme Personen auf der Website der Bank auf ein allgemeines Anfrageformular zugreifen, wohingegen angemeldete Benutzende direkten Zugriff auf sicherere Formulare wie Kreditanträge oder Formulare zu einer Transaktionsgenehmigung erhalten.

![Link-Symbol](/help/forms/assets/link-forms.png)

## Voraussetzung

Bevor Sie die verschiedenen Funktionen einer Formularportal-Komponente erkunden, stellen Sie sicher, dass Kernkomponenten für Ihre Umgebung aktiviert sind. Installieren Sie die neueste Version von , um adaptive Forms-Kernkomponenten für Ihre AEM Cloud Service-Umgebung zu aktivieren.

Nach der Bereitstellung der neuesten Kernkomponenten in Ihrer Umgebung können Sie auf die Formularportal-Komponenten in Ihrer Authoring-Umgebung zugreifen.

## Hinzufügen der Komponente „Link“ zu Ihrer Sites-Seite

Gehen Sie wie folgt für, um die Portal-Komponente **Link** zu Ihrer Sites-Seite hinzuzufügen:

1. Öffnen Sie die AEM Sites-Seite in einem **Bearbeitungsmodus**.
1. Navigieren Sie zu **[!UICONTROL Seiteninformationen]** > **[!UICONTROL Vorlage bearbeiten]**
   ![Richtlinie zum Bearbeiten von Vorlagen](/help/forms/assets/save-form-as-draft-edit-template.png)

1. Klicken Sie auf **[!UICONTROL Richtlinie]** und aktivieren Sie das Kontrollkästchen **[!UICONTROL Link]** unter **[AEM Archetyp-Projektname] – Formular- und Kommunikationsportal**.

   ![Auswählen von Richtlinien](/help/forms/assets/add-link.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**.
1. Öffnen Sie die AEM Sites-Seite nun im Authoring-Modus erneut.
1. Suchen Sie im Seiteneditor nach dem Abschnitt, in dem Sie die Formularportal-Komponente hinzufügen können.

1. Klicken Sie auf das Symbol **Hinzufügen**. Das Symbol ist ein Pluszeichen (+). Es steht für die Option zum Hinzufügen neuer Komponenten.

   Wenn Sie auf das Symbol **Hinzufügen** klicken, wird das Dialogfeld **Neue Komponente einfügen** angezeigt, in dem verschiedene Komponenten zum Einfügen angezeigt werden.

   >[!NOTE]
   >
   > Alternativ können Sie die Komponente auch per Drag-and-Drop hinzufügen.

1. Durchsuchen Sie die verfügbaren Komponenten im Dialogfeld und wählen Sie die gewünschte Komponente aus der Liste aus. Wählen Sie beispielsweise die Komponente **Link** aus der Liste aus, um die Formularportal-Komponente **Link** hinzuzufügen.

   ![Komponente „Link“](/help/forms/assets/add-link-in-sites.png)

Konfigurieren Sie jetzt die Eigenschaften der Komponente **Link**.

## Grundlegendes zu den Eigenschaften der Komponente „Link“

Sie können die Eigenschaften der Komponente **Link** einfach über das Dialogfeld „Konfigurieren“ anpassen, um für ein nahtloses Benutzererlebnis zu sorgen. Wählen Sie zum Konfigurieren die Komponente und dann das ![Symbol „Konfigurieren“](assets/configure_icon.png). Das Dialogfeld **[!UICONTROL Link]** wird geöffnet.

### Registerkarte „Anzeige“

![Registerkarte „Anzeige“](/help/forms/assets/link-asset-tab.png)

Geben Sie auf der Registerkarte **[!UICONTROL Anzeige]** die Link-Beschriftung und die QuickInfo ein, um die Identifizierung der durch diesen Link dargestellten Formulare zu erleichtern.

### Registerkarte „Asset-Info“

![Registerkarte „Asset-Info“](/help/forms/assets/link-asset-info.png)

Geben Sie auf der Registerkarte **[!UICONTROL Asset-Informationen]** den Repository-Pfad an, unter dem das Asset gespeichert ist.

### Registerkarte „Abfrageparameter“

![Registerkarte „Abfrageparameter“](/help/forms/assets/link-query-tab.png)

Geben Sie auf der Registerkarte **[!UICONTROL Abfrageparameter]** die zusätzlichen Parameter im Schlüssel-Wert-Paarformat an. Wenn auf den Link geklickt wird, werden diese zusätzlichen Parameter zusammen mit dem Formular übergeben.

## Anzeigen von Formular-Links auf der Sites-Seite mithilfe der Komponente „Link“

Zeigen Sie die Sites-Seite in der Vorschau an, um sich den Link zu einem adaptiven Formular anzusehen, der auf der Eigenschaften-Registerkarte **Assets-Info** der Komponente **Link** angegeben ist. Durch Klicken auf den Link wird das Formular auf dem Bildschirm für Benutzende angezeigt, die dann entsprechend der Berechtigungen darauf zugreifen können.

![Registerkarte „Abfrageparameter“](/help/forms/assets/link-forms.png)

## Verwandte Artikel

{{forms-portal-see-also}}

## Siehe auch {#see-also}

{{see-also}}
