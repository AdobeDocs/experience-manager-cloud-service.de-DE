---
title: Inhaltserstellung mit dem universellen Editor
description: Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und -autoren ist, Inhalte mit dem universellen Editor zu erstellen.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 3922375b52ae64d08cdc64d475a95e8bd240a587
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 80%

---


# Inhaltserstellung mit dem universellen Editor {#authoring}

Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und -autoren ist, Inhalte mit dem universellen Editor zu erstellen.

## Einführung {#introduction}

Der universelle Editor ermöglicht die Bearbeitung beliebiger Inhalte in jeder Implementierung, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.

Zu diesem Zweck bietet der universelle Editor Inhaltsautorinnen und Inhaltsautoren eine intuitive Benutzeroberfläche, die nur eine minimale Schulung erfordert, damit sie gleich loslegen und mit der Bearbeitung von Inhalten beginnen können. In diesem Dokument wird das Authoring-Erlebnis mit dem universellen Editor beschrieben.

>[!NOTE]
>
>In diesem Dokument wird davon ausgegangen, dass Sie bereits mit dem Zugriff auf den universellen Editor und dessen Navigation vertraut sind. Ist dies nicht der Fall, lesen Sie das Dokument [Zugriff auf den universellen Editor und Navigation](/help/sites-cloud/authoring/universal-editor/navigation.md) .

>[!TIP]
>
>Eine detailliertere Einführung in den universellen Editor finden Sie im Dokument [Einführung in den universellen Editor](/help/implementing/universal-editor/introduction.md).

## Bearbeiten von Inhalten {#editing-content}

Die Bearbeitung von Inhalten ist einfach und intuitiv. Wenn Sie mit dem Mauszeiger über einen Inhalt im Editor fahren, werden bearbeitbare Inhalte mit einem blauen Feld hervorgehoben.

![Bearbeitbare Inhalte werden durch ein blaues Feld hervorgehoben](assets/editable-content.png)

>[!TIP]
>
>Durch Tippen oder Klicken auf einen Inhalt wird dieser standardmäßig zur Bearbeitung ausgewählt. Wenn Sie durch das Folgen von Links in Ihren Inhalten navigieren möchten, wechseln Sie zum [Vorschaumodus.](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode)

Je nach ausgewähltem Inhalt können Ihnen unterschiedliche Optionen zur Bearbeitung im Kontext zur Verfügung stehen. Außerdem sehen Sie möglicherweise zusätzliche Informationen und Optionen für den Inhalt in der [Eigenschaftenleiste](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail).

### Bearbeiten von einfachem Text {#edit-plain-text}

Sie können den Text direkt bearbeiten, indem Sie auf die Komponente doppelklicken oder doppeltippen.

![Bearbeiten von Inhalten](assets/editing-content.png)

Drücken Sie die Eingabetaste oder wählen Sie etwas außerhalb des Textfelds aus, um Ihre Änderungen zu speichern.

Wenn Sie die Textkomponente auswählen, werden deren Details in der Eigenschaftenleiste von [angezeigt.](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail) Sie können den Text auch in der Leiste bearbeiten.

![Bearbeiten von Text in der Eigenschaftenleiste](assets/ue-editing-text-component-rail.png)

Details zu Ihrem Text sind auch in der Eigenschaftenleiste verfügbar. Änderungen werden automatisch gespeichert, sobald das bearbeitete Feld in der Eigenschaftenleiste nicht mehr im Fokus ist.

### Bearbeiten von Rich-Text {#edit-rich-text}

Sie können den Text direkt bearbeiten, indem Sie auf die Komponente doppelklicken oder doppeltippen.

![Bearbeiten einer Rich-Text-Komponente](assets/rich-text-editing.png)

Zur Vereinfachung sind an zwei Stellen Formatierungsoptionen und Details zu Ihrem Text verfügbar.

* Das **Kontextmenü** wird oberhalb des Rich-Text-Blocks geöffnet und bietet grundlegende Formatierungsoptionen im Kontext. Aufgrund von Platzbeschränkungen kann es sein, dass einige Optionen hinter der Schaltfläche mit den Auslassungspunkten ausgeblendet werden.
* Die **[Eigenschaftenleiste](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail)** zeigt alle verfügbaren Formatierungsoptionen zusammen mit dem Text an.

Änderungen werden automatisch gespeichert, sobald das bearbeitete Feld nicht mehr im Fokus ist.

### Bearbeiten von Medien {#edit-media}

Sie können die Details in der Leiste [Eigenschaften} anzeigen.](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail)

![Bearbeiten von Medien](assets/ue-edit-media.png)

1. Tippen oder klicken Sie in der Eigenschaftenleiste auf die Vorschau des ausgewählten Bildes.
1. Das Fenster [Asset-Selektor](/help/assets/asset-selector.md#using-asset-selector) wird geöffnet, in dem Sie ein Asset auswählen können.
1. Wählen Sie diese Option, um ein neues Asset auszuwählen.
1. Wählen Sie die Option **Auswählen** aus, um zur Eigenschaftenleiste zurückzukehren, in der das Asset ersetzt wurde.

Änderungen an Ihrem Inhalt werden automatisch gespeichert.

### Bearbeiten von Inhaltsfragmenten {#edit-content-fragment}

Wenn Sie ein [Inhaltsfragment](/help/sites-cloud/administering/content-fragments/overview.md) auswählen, können Sie dessen Details in der Leiste [ &quot;Eigenschaften&quot;bearbeiten.](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail)

![Bearbeiten von Inhaltsfragmenten](assets/ue-edit-cf.png)

Die im Inhaltsmodell des ausgewählten Inhaltsfragments definierten Felder werden in der Eigenschaftenleiste angezeigt und können bearbeitet werden.

Wenn Sie ein Feld auswählen, das sich auf ein Inhaltsfragment bezieht, wird das Inhaltsfragment in der Komponentenleiste geladen und automatisch zu diesem Feld gescrollt.

Änderungen werden automatisch gespeichert, sobald das bearbeitete Feld in der Eigenschaftenleiste nicht mehr im Fokus ist.

Wenn Sie Ihr Inhaltsfragment stattdessen im [Inhaltsfragment-Editor](/help/sites-cloud/administering/content-fragments/authoring.md) bearbeiten möchten, klicken Sie in der Eigenschaftenleiste auf die Schaltfläche [Bearbeiten](/help/sites-cloud/authoring/universal-editor/navigation.md#edit) .

Abhängig von den Anforderungen Ihres Workflows können Sie das Inhaltsfragment im universellen Editor oder direkt im Inhaltsfragmenteditor bearbeiten.

### Hinzufügen von Komponenten zu Containern {#adding-components}

1. Wählen Sie eine Container-Komponente im [Inhaltsbaum](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) oder im Editor aus.
1. Wählen Sie dann das Symbol „Hinzufügen“ in der Eigenschaftenleiste aus.

   ![Auswählen einer Komponente zum Hinzufügen zu einem Container](assets/ue-add-component.png)

Die Komponente wird in den Container eingefügt und kann im Editor bearbeitet werden.

>[!TIP]
>
>Verwenden Sie den Hotkey `A`, um dem ausgewählten Container eine Komponente hinzuzufügen.

### Löschen von Komponenten aus Containern {#deleting-components}

1. Wählen Sie eine Container-Komponente im [Inhaltsbaum](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) oder im Editor aus.
1. Wählen Sie das Pfeilsymbol des Containers aus, um seinen Inhalt in der Inhaltsstruktur zu erweitern.
1. Wählen Sie dann in der Inhaltsstruktur eine Komponente im Container aus.
1. Wählen Sie das Symbol „Löschen“ in der Eigenschaftenleiste aus.

   ![Löschen einer Komponente](assets/ue-delete-component.png)

Die ausgewählte Komponente wird gelöscht.

>[!TIP]
>
>Verwenden Sie den Hotkey `Shift+Backspace`, um die ausgewählte Komponente aus ihrem Container zu löschen.

### Neuanordnen von Komponenten in Containern {#reordering-components}

1. Wechseln Sie in den [Inhaltsstruktur-Modus](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode), wenn dieser nicht bereits aktiviert ist.
1. Wählen Sie eine Container-Komponente in der Inhaltsstruktur oder im Editor aus.
1. Wählen Sie das Pfeilsymbol des Containers aus, um seinen Inhalt in der Inhaltsstruktur zu erweitern.
1. Ziehpunkte neben den Komponenten im Container zeigen, dass Sie sie neu anordnen können. Ziehen Sie die Komponenten, um sie innerhalb des Containers neu anzuordnen.

   ![Neuanordnen von Komponenten](assets/ue-reordering-components.png)

1. Die gezogene Komponente wird in der Inhaltsstruktur grau dargestellt, während der Einfügepunkt durch eine blaue Linie dargestellt wird. Lassen Sie die Komponente los, um sie an ihrer neuen Position zu platzieren.

Die Komponenten werden sowohl in der Inhaltsstruktur als auch im Editor neu angeordnet.

## Vorschau von Inhalten {#previewing-content}

Wenn Sie mit der Bearbeitung von Inhalten fertig sind, möchten Sie häufig durch diese navigieren, um zu sehen, wie sie im Inhalt anderer Seiten aussehen. Im [Vorschaumodus](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode) können Sie auf Links klicken, um genau wie eine Person, die Ihre Inhalte liest, durch diese zu navigieren. Der Inhalt wird im Editor so wiedergegeben, wie er veröffentlicht werden würde.

Beachten Sie, dass im Vorschaumodus beim Tippen oder Klicken auf den Inhalt die gleiche Reaktion erfolgt, wie es bei einer Person, die den Inhalt liest, der Fall wäre. Wenn Sie den Inhalt zum Bearbeiten auswählen möchten, wechseln Sie in den [Vorschaumodus.](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode)

## Zusätzliche Ressourcen {#additional-resources}

Informationen zum Veröffentlichen von Inhalten mit dem universellen Editor finden Sie in diesem Dokument.

* [Veröffentlichen von Inhalten mit dem universellen Editor](publishing.md) – Erfahren Sie, wie mit dem universellen Editor Inhalte veröffentlicht werden und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.

Weitere Informationen zu den technischen Details zum universellen Editor finden Sie in diesen Entwicklerdokumenten.

* [Einführung in den universellen Editor](/help/implementing/universal-editor/introduction.md) – Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Erste Schritte mit dem universellen Editor in AEM](/help/implementing/universal-editor/getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](/help/implementing/universal-editor/architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](/help/implementing/universal-editor/attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Authentifizierung beim universellen Editor](/help/implementing/universal-editor/authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.

## Bearbeiten der Komponentenvererbung {#inheritance}

Vererbung ist der Mechanismus, bei dem Inhalte so verknüpft werden können, dass sich durch eine Änderung automatisch der andere verändert.

Mit dem universellen Editor können Sie die Vererbung für Inhalte abbrechen, indem Sie den Inhalt einfach aktualisieren. Der Editor deaktiviert automatisch die Vererbung für alle Änderungen, die von Autoren auf dieser Seite vorgenommen werden. Dadurch wird sichergestellt, dass geänderte Inhalte beibehalten werden, wenn Aktualisierungen aus dem Blueprint synchronisiert werden.

Weitere Informationen zur Funktionsweise der Vererbung mit dem universellen Editor finden Sie im Dokument [Inhaltsvererbung im universellen Editor](/help/sites-cloud/authoring/universal-editor/inheritance.md) .
