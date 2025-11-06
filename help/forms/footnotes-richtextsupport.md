---
title: Hinzufügen von Fußnoten zu einem adaptiven Formular?
description: Verwenden Sie den Rich-Text-Editor (RTE) für Fußnoten in adaptiven Formularen.
feature: Adaptive Forms, Foundation Components
exl-id: f04dae84-daab-42f8-876f-02fe426f62be
role: User, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 100%

---

# Fußnotenkomponente {#footnotecomponent}

>[!NOTE]
>
> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für die Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/creating-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben.

Eine **[!UICONTROL Fußnote]** ist eine zusätzliche Information oder Anmerkung, die am Ende der Seite erscheint. Eine [!UICONTROL Fußnote] umfasst die Anmerkungen, auf die in Ihrem Text durch hochgestellte Zahlen verwiesen wird.

Fußnoten werden in der Reihenfolge nummeriert, in der sie auf der Seite angezeigt werden. Jede Fußnote hat eine eindeutige hochgestellte Nummer, die der Nummer am unteren Rand der Seite entspricht. Neben der Nummer erscheint die Zusatzinformation als Fußnotenbeschreibung.

![Fußnotenbeschreibung](/help/forms/assets/footnote_description.png)


## Verwendung einer Fußnote {#usesoffootnotes}

* Hilft bei der Bereitstellung von Zitaten.
* Bietet zusätzliche Informationen, die den normalen Fluss der Hauptinformationen unterbrechen würden.
* Enthält Informationen in Klammern oder Copyright-Genehmigungen.

In adaptiven Formularen wird eine [!UICONTROL Fußnote] verwendet, um Informationen zum Ausfüllen oder Verwenden des Formulars anzuzeigen. Informationen zum Erstellen eines adaptiven Formulars finden Sie unter [Erstellen eines adaptiven Formulars](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-an-adaptive-form/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html?lang=de).

## Fußnoten in adaptiven Formularen {#using-footnote-adaptiveforms}

Gehen Sie wie folgt vor, um Fußnoten in adaptiven Formularen hinzuzufügen:

1. Öffnen Sie ein adaptives Formular im **Bearbeitungsmodus**.
1. Ziehen Sie im Komponenten-Browser per Drag &amp; Drop die Komponente **[!UICONTROL Text]** auf das adaptive Formular.
1. Wählen Sie die hinzugefügte **[!UICONTROL Textkomponente]** und dann ![cmppr](assets/configure-icon.svg) aus, um ihre Eigenschaften zu bearbeiten.

   ![Fußnote in adaptiven Formularen](/help/forms/assets/footnote_rte.png)

1. Wählen Sie den Text aus, für den Sie eine Fußnotenbeschreibung hinzufügen möchten, und klicken Sie auf die  ![Stern](/help/forms/assets/asterisk.svg)-Schaltfläche, um die **[!UICONTROL Fußnoten]**-Komponente zu gestalten.

1. Klicken Sie auf den ![Haken](/help/forms/assets/save_icon.svg), um die Änderungen und Stile zu speichern.

   >[!NOTE]
   >
   >* Fußnoten werden automatisch nummeriert und erscheinen so, wie sie im adaptiven Formular erstellt werden.
   >* Wenn doppelte Fußnoten vorhanden sind, ist die Zählung für alle doppelten Fußnoten identisch.

1. Ziehen Sie im Komponenten-Browser mittels Drag &amp; Drop die Komponente **[!UICONTROL Fußnoten-Platzhalter]** auf das adaptive Formular.

   >[!NOTE]
   >
   >* In der Veröffentlichungsinstanz werden Fußnoten an der Position angezeigt, an der die Komponente **[!UICONTROL Fußnoten-Platzhalter]** auf dem adaptiven Formular platziert ist.
   >* Wenn Sie zwischen verschiedenen Bedienfeldern navigieren, erscheinen nur sichtbare Fußnoten im **[!UICONTROL Fußnoten-Platzhalter]**, die im navigierten Bedienfeld vorhanden sind.

1. Speichern Sie die Eigenschaften.

Zur Laufzeit erscheint die Nummer im Text als hochgestellte Zahl, und die entsprechende Beschreibung erscheint in der **[!UICONTROL Fußnoten]**-Komponente an der Stelle, an der der [!UICONTROL Fußnoten-Platzhalter] im adaptiven Formular platziert ist. Sie können direkt zur Beschreibung in Form der Fußnote navigieren, indem Sie auf die zugehörige Nummer der [!UICONTROL Fußnote] klicken.


## Siehe auch {#see-also}

{{see-also}}