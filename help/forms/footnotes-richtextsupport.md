---
title: Unterstützung von Fußnoten
description: RTE-Unterstützung für Fußnoten.
source-git-commit: 6f6cf5657bf745a2e392a8bfd02572aa864cc69c
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Fußzeilenkomponente {#footnotecomponent}

**[!UICONTROL Fußnote]** ist das zusätzliche Bit an Informationen oder Notizen, die am Ende der Seite angezeigt werden. [!UICONTROL Fußnote] enthält die Notizen, die in Ihrem Text mit Zahlen als Hochgestellt angegeben sind.

Fußnoten werden in der Reihenfolge nummeriert, in der sie auf der Seite erscheinen. Jede Fußnote hat eine eindeutige Nummer als Hochgestellt, die der Nummer entspricht, die am Ende der Seite platziert wird. Neben der Nummer erscheinen die Zusatzinformationen als Fußnote-Beschreibung.

![Fußnote](/help/forms/assets/footnote_description.png)


## Verwendung der Fußnote {#usesoffootnotes}

* Hilft bei der Bereitstellung von Zitaten.
* Bietet zusätzliche Informationen, die den normalen Fluss der Hauptinformationen unterbrechen können.
* Bietet Klammerinformationen oder Copyright-Berechtigungen.

In Adaptive Forms [!UICONTROL Fußnote] wird verwendet, um Informationen zum Ausfüllen oder Verwenden des Formulars anzuzeigen. Informationen zum Erstellen eines adaptiven Forms finden Sie unter [Erstellen eines adaptiven Formulars](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-an-adaptive-form/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html).

## Fußnote in Adaptive Forms {#using-footnote-adaptiveforms}

Gehen Sie wie folgt vor, um Fußnoten in Adaptive Forms hinzuzufügen:
1. Öffnen Sie ein adaptives Formular in **Bearbeiten** -Modus.
1. Ziehen Sie aus dem Komponenten-Browser die **[!UICONTROL Text]** auf das adaptive Formular.
1. Wählen Sie die **[!UICONTROL Text]** Komponente, die Sie hinzugefügt haben, und tippen Sie auf ![cmppr](assets/configure-icon.svg) , um die Eigenschaften zu bearbeiten.

   ![Fußnote in Adaptive Forms](/help/forms/assets/footnote_rte.png)

1. Wählen Sie den Text aus, für den Sie eine Fußnotenbeschreibung hinzufügen möchten, und klicken Sie auf  ![star](/help/forms/assets/asterisk.svg) Schaltfläche zum Formatieren **[!UICONTROL Fußnote]** -Komponente.

1. Klicken ![check](/help/forms/assets/save_icon.svg) , um die Änderungen und Stile zu speichern.

   >[!NOTE]
   >
   >* Fußnoten werden automatisch nummeriert und erscheinen so, wie sie im adaptiven Formular erstellt werden.
   >* Wenn doppelte Fußnoten vorhanden sind, ist die Zählung für alle doppelten Fußnoten identisch.


1. Ziehen Sie aus dem Komponenten-Browser die **[!UICONTROL Fußnoten-Platzhalter]** auf das adaptive Formular.
   >[!NOTE]
   >
   >* In der Veröffentlichungsinstanz werden Fußnoten an der Position angezeigt, an der **[!UICONTROL Fußnoten-Platzhalter]** wird im adaptiven Formular platziert.
   >* Wenn Sie zwischen verschiedenen Bedienfeldern navigieren, werden in der **[!UICONTROL Fußnoten-Platzhalter]** , die im Bedienfeld für die Navigation vorhanden sind.


1. Speichern Sie die Eigenschaften.

Zur Laufzeit wird eine Zahl auf dem Text als hochgestellt angezeigt und die zugehörige Beschreibung wird im **[!UICONTROL Fußnote]** Komponente an der Position, an der [!UICONTROL Fußnoten-Platzhalter] wird im adaptiven Formular platziert. Sie können direkt zur Beschreibung der Fußnote navigieren, indem Sie auf die zugehörige Nummer im [!UICONTROL Fußnote].