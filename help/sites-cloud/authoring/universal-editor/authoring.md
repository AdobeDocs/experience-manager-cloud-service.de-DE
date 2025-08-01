---
title: Inhaltserstellung mit dem universellen Editor
description: Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und -autoren ist, Inhalte mit dem universellen Editor zu erstellen.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 597315a7d569ebd62243322c543627b7a3535a6b
workflow-type: ht
source-wordcount: '2252'
ht-degree: 100%

---


# Inhaltserstellung mit dem universellen Editor {#authoring}

Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und -autoren ist, Inhalte mit dem universellen Editor zu erstellen.

## Einführung {#introduction}

Der universelle Editor ermöglicht die Bearbeitung beliebiger Aspekte von Inhalten in jeder Implementierung, um außergewöhnliche Erlebnisse bereitzustellen und die Inhaltsgeschwindigkeit zu erhöhen.

Zu diesem Zweck bietet der universelle Editor Inhaltsautorinnen und Inhaltsautoren eine intuitive Benutzeroberfläche, die nur eine minimale Schulung erfordert, damit sie gleich loslegen und mit der Bearbeitung von Inhalten beginnen können. In diesem Dokument wird das Authoring-Erlebnis mit dem universellen Editor beschrieben.

>[!NOTE]
>
>Bei den in diesem Dokument beschriebenen Schritten wird vorausgesetzt, dass Sie bereits damit vertraut sind, wie Sie auf den universellen Editor zugreifen und darin navigieren. Ist dies nicht der Fall, lesen Sie [Zugreifen auf den und Navigieren im universellen Editor](/help/sites-cloud/authoring/universal-editor/navigation.md).

>[!TIP]
>
>Eine detailliertere Einführung in den universellen Editor finden Sie im Dokument [Einführung in den universellen Editor](/help/implementing/universal-editor/introduction.md).

## Bearbeiten von Inhalten {#editing-content}

Die Bearbeitung von Inhalten ist einfach und intuitiv. Wenn Sie mit dem Mauszeiger über einen Inhalt im Editor fahren, werden bearbeitbare Inhalte mit einem dünnen blauen Umriss hervorgehoben.

![Bearbeitbare Inhalte werden durch ein blaues Feld hervorgehoben](assets/editable-content.png)

>[!TIP]
>
>Durch Tippen oder Klicken auf einen Inhalt wird dieser standardmäßig zur Bearbeitung ausgewählt. Wenn Sie durch das Folgen von Links in Ihren Inhalten navigieren möchten, wechseln Sie zum [Vorschaumodus](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode).

Je nach ausgewähltem Inhalt können Ihnen unterschiedliche Optionen zur Bearbeitung im Kontext zur Verfügung stehen. Außerdem sehen Sie möglicherweise zusätzliche Informationen und Optionen für den Inhalt im [Bedienfeld „Eigenschaften“](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail).

### Bearbeiten von einfachem Text {#edit-plain-text}

Sie können den Text direkt bearbeiten, indem Sie auf die Komponente doppelklicken oder doppeltippen.

![Bearbeiten von Inhalten](assets/editing-content.png)

Der dünne blaue Umriss wird zu einem dicken blauen Umriss, um die Auswahl anzuzeigen, und ein Cursor wird angezeigt. Nehmen Sie die gewünschten Änderungen vor und drücken Sie die Eingabetaste oder wählen Sie etwas außerhalb des Textfelds aus, um Ihre Änderungen zu speichern.

Wenn Sie die Textkomponente auswählen, werden ihre Details im [Bedienfeld „Eigenschaften“](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail) angezeigt. Sie können den Text auch im Bedienfeld bearbeiten.

![Bearbeiten von Text im Bedienfeld „Eigenschaften“](assets/ue-editing-text-component-rail.png)

Außerdem finden Sie im Bedienfeld „Eigenschaften“ weitere Details zu Ihrem Text. Änderungen werden automatisch gespeichert, sobald der Fokus das bearbeitete Feld im Bedienfeld „Eigenschaften“ verlässt.

### Bearbeiten von Rich-Text {#edit-rich-text}

Sie können den Text direkt bearbeiten, indem Sie auf die Komponente doppelklicken oder doppeltippen.

![Bearbeiten einer Rich-Text-Komponente](assets/rich-text-editing.png)

Zur Vereinfachung sind an zwei Stellen Formatierungsoptionen und Details zu Ihrem Text verfügbar.

#### Das Kontextmenü {#context-menu}

Das Kontextmenü wird oberhalb des Rich-Text-Blocks geöffnet und bietet grundlegende Formatierungsoptionen im Kontext. Aufgrund von Platzbeschränkungen kann es sein, dass einige Optionen hinter der Schaltfläche mit den Auslassungspunkten ausgeblendet werden.

![Kontextmenü für Rich-Text](assets/rich-text-context-menu.png)

Änderungen werden automatisch gespeichert, sobald das bearbeitete Feld nicht mehr den Eingabefokus hat.

#### Das Bedienfeld „Eigenschaften“ {#properties-rail}

Das [Bedienfeld „Eigenschaften“](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail) zeigt ein Element für den ausgewählten Text an. Tippen Sie auf den Eintrag, um ein Dialogfeld mit einer größeren Arbeitsfläche zu öffnen, mit der Sie den Text bearbeiten können.

![Dialogfeld für die Bearbeitung von Rich-Text](assets/rich-text-canvas.png)

Tippen oder klicken Sie auf **Fertig** oder **Abbrechen**, um die Änderungen zu speichern bzw. zu verwerfen.

### Bearbeiten von Medien {#edit-media}

Sie können die Details im [Bedienfeld „Eigenschaften“](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail) anzeigen.

![Bearbeiten von Medien](assets/ue-edit-media.png)

1. Tippen oder klicken Sie auf die Vorschau des ausgewählten Bildes im Bedienfeld „Eigenschaften“.
1. Das Fenster [Asset-Selektor](/help/assets/overview-asset-selector.md#using-asset-selector) wird geöffnet, in dem Sie ein Asset auswählen können.
1. Wählen Sie diese Option, um ein neues Asset auszuwählen.
1. Wählen Sie **Auswählen**, um zum Bedienfeld „Eigenschaften“ zurückzukehren, in dem das Asset ersetzt wurde.

Änderungen an Ihrem Inhalt werden automatisch gespeichert.

### Bearbeiten von Inhaltsfragmenten {#edit-content-fragment}

Wenn Sie ein [Inhaltsfragment](/help/sites-cloud/administering/content-fragments/overview.md) auswählen, können Sie dessen Details im [Bedienfeld „Eigenschaften“](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail) bearbeiten.

![Bearbeiten von Inhaltsfragmenten](assets/ue-edit-cf.png)

Die im Inhaltsmodell des ausgewählten Inhaltsfragments definierten Felder werden im Bedienfeld „Eigenschaften“ angezeigt und können dort bearbeitet werden.

Wenn Sie ein Feld auswählen, das mit einem Inhaltsfragment verknüpft ist, wird das Inhaltsfragment im Bedienfeld „Komponenten“ geladen und automatisch zu diesem Feld gescrollt.

Änderungen werden automatisch gespeichert, sobald der Fokus das bearbeitete Feld im Bedienfeld „Eigenschaften“ verlässt.

Wenn Sie Ihr Inhaltsfragment stattdessen im [Inhaltsfragmenteditor](/help/sites-cloud/administering/content-fragments/authoring.md) bearbeiten möchten, tippen oder klicken Sie im Bedienfeld „Eigenschaften“ auf die Schaltfläche [**Im CF-Editor öffnen**](/help/sites-cloud/authoring/universal-editor/navigation.md#edit).

>[!TIP]
>
>Verwenden Sie den Hotkey `e`, um das ausgewählte Inhaltsfragment im Inhaltsfragmenteditor zu bearbeiten.

Je nach den Anforderungen Ihres Workflows können Sie das Inhaltsfragment im universellen Editor oder direkt im Inhaltsfragmenteditor bearbeiten.

>[!NOTE]
>
>Der universelle Editor [validiert Inhaltsfragmentfelder anhand ihrer Modelle](/help/assets/content-fragments/content-fragments-models.md#validation). Dadurch können Sie Datenintegrationsregeln wie Regex-Muster und Eindeutigkeitsbeschränkungen erzwingen.
>
>So wird sichergestellt, dass Ihre Inhalte bestimmten Geschäftsanforderungen entsprechen, bevor sie veröffentlicht werden.

### Hinzufügen von Komponenten zu Containern {#adding-components}

1. Wählen Sie eine Container-Komponente in der [Inhaltsstruktur](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) oder im Editor aus.

   ![Auswählen einer Komponente zum Hinzufügen zu einem Container](assets/ue-add-component.png)

1. Wählen Sie dann das Symbol „Hinzufügen“ im Bedienfeld „Eigenschaften“ aus.

   ![Auswählen des Symbols „Hinzufügen“](assets/add-icon.png)

1. Wenn mehr als eine Komponente für den Container zulässig ist, wählen Sie aus der Dropdown-Liste die Komponente aus, die Sie einfügen möchten. Wenn nur eine Komponente zulässig ist, wird sie automatisch eingefügt.

Die Komponente wird in den Container eingefügt und kann im Editor bearbeitet werden.

>[!TIP]
>
>Verwenden Sie den Hotkey `a`, um dem ausgewählten Container eine Komponente hinzuzufügen.

### Duplizieren von Komponenten in Containern {#duplicating-components}

1. Wählen Sie eine Komponente in einem Container mithilfe der [Inhaltsstruktur](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) oder des Editors aus.
1. Wählen Sie dann das Symbol **Duplizieren** im Bedienfeld „Eigenschaften“ aus.

   ![Auswählen einer Komponente zum Hinzufügen zu einem Container](assets/ue-duplicate-component.png)
1. Die Komponente wird dupliziert und unterhalb der ausgewählten Komponente eingefügt.

Die Komponente wird in den Container eingefügt und kann im Editor bearbeitet werden.

### Löschen von Komponenten aus Containern {#deleting-components}

1. Wählen Sie eine Container-Komponente in der [Inhaltsstruktur](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) oder im Editor aus.
1. Wählen Sie das Pfeilsymbol des Containers aus, um seinen Inhalt in der Inhaltsstruktur zu erweitern.
1. Wählen Sie dann in der Inhaltsstruktur eine Komponente im Container aus.
1. Wählen Sie das Löschsymbol im Bedienfeld „Eigenschaften“ aus.

   ![Löschen einer Komponente](assets/ue-delete-component.png)

Die ausgewählte Komponente wird gelöscht.

>[!TIP]
>
>Verwenden Sie den Hotkey `Shift+Backspace`, um die ausgewählte Komponente aus ihrem Container zu löschen.

### Neuanordnen von Komponenten {#reordering-components}

1. Wechseln Sie in den [Inhaltsstruktur-Modus](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode), falls dieser nicht bereits aktiviert ist.
1. Wählen Sie eine Container-Komponente in der Inhaltsstruktur oder im Editor aus.
1. Wählen Sie das Pfeilsymbol des Containers aus, um seinen Inhalt in der Inhaltsstruktur zu erweitern.
1. Ziehpunkte neben den Komponenten im Container zeigen, dass Sie sie neu anordnen können. Ziehen Sie die Komponenten, um sie innerhalb des Containers neu anzuordnen.

   ![Neuanordnen von Komponenten](assets/ue-reordering-components.png)

1. Die gezogene Komponente wechselt in der Inhaltsstruktur zu Grau, während der Einfügepunkt durch eine blaue Linie dargestellt wird. Lassen Sie die Komponente an ihrer neuen Position los, um sie dort zu platzieren.

Die Komponenten werden sowohl in der Inhaltsstruktur als auch im Editor neu angeordnet.

>[!NOTE]
>
>Komponenten können nur dann zwischen Containern verschoben werden, wenn der [Komponentenfilter](/help/implementing/universal-editor/filtering.md) des Ziel-Containers die ausgewählte Komponente zulässt.

## Vorschau von Inhalten {#previewing-content}

Wenn Sie mit der Bearbeitung von Inhalten fertig sind, möchten Sie häufig durch diese navigieren, um zu sehen, wie sie im Inhalt anderer Seiten aussehen. Im [Vorschaumodus](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode) können Sie auf Links klicken, um genau wie eine Person, die Ihre Inhalte liest, durch diese zu navigieren. Der Inhalt wird im Editor so wiedergegeben, wie er veröffentlicht werden würde.

Beachten Sie, dass im Vorschaumodus beim Tippen oder Klicken auf den Inhalt die gleiche Reaktion erfolgt, wie es bei einer Person, die den Inhalt liest, der Fall wäre. Wenn Sie den Inhalt zum Bearbeiten auswählen möchten, verlassen Sie in den [Vorschaumodus](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode).

## Bearbeiten der Komponentenvererbung {#inheritance}

Vererbung ist der Mechanismus, durch den Inhalte so verknüpft werden können, dass Inhaltsänderungen automatisch übernommen werden. 

Mit dem universellen Editor können Sie die Vererbung für Inhalte abbrechen, indem Sie den Inhalt einfach aktualisieren. Der Editor deaktiviert automatisch die Vererbung für alle Änderungen, die von Autorinnen und Autoren auf dieser Seite vorgenommen werden. Dadurch wird sichergestellt, dass geänderte Inhalte beibehalten werden, wenn Aktualisierungen aus dem Blueprint synchronisiert werden.

Wenn die **AEM-Erweiterung für Multi-Site-Management (MSM)** für Ihr Programm aktiviert ist, verfügen Sie über [zusätzliche Symbolleistenoptionen](#inheritance-extension), um den Vererbungsstatus einer einzelnen Komponente im universellen Editor anzuzeigen und zu ändern.

Weitere Informationen zur Funktionsweise der Vererbung mit dem universellen Editor finden Sie im Dokument [Vererbung von Inhalten im universellen Editor](/help/sites-cloud/authoring/universal-editor/inheritance.md).

## Optionale Symbolleistenfunktionen {#toolbar-options}

Zusätzliche Funktionen sind als Erweiterungen des universellen Editors verfügbar, die Sie bei der weiteren Verwaltung Ihrer Seiten und Inhalte unterstützen. [Diese Erweiterungen müssen in Ihrem Programm von einer bzw. einem Admin aktiviert werden](/help/implementing/universal-editor/extending.md), bevor sie für Sie als Inhaltsautorin bzw. Inhaltsautor in der [Symbolleiste des universellen Editors](/help/sites-cloud/authoring/universal-editor/navigation.md#universal-editor-toolbar) sichtbar sind.

### Vererbung {#inheritance-extension}

Die **AEM-Erweiterung für Multi-Site-Management (MSM)** zeigt den aktuellen Vererbungsstatus der ausgewählten Komponente an und ermöglicht es Ihnen, die [Vererbung zu unterbrechen oder wiederherzustellen](/help/sites-cloud/authoring/universal-editor/inheritance.md).

Das Symbol **Vererbung installiert** in der Symbolleiste des universellen Editors zeigt an, dass die Vererbung für die ausgewählte Komponente weiterhin aktiv ist.

![Symbol „Vererbung installiert“](assets/inheritance-installed-icon.png)

Tippen oder klicken Sie auf das Symbol, um die Vererbung für die ausgewählte Komponente zu unterbrechen. Die Vererbung wird automatisch unterbrochen, wenn Sie die Komponente bearbeiten.

Das Symbol **Vererbung unterbrochen** zeigt an, dass die Vererbung für die ausgewählte Komponente unterbrochen wurde.

![Symbol „Vererbung unterbrochen“](assets/inheritance-broken-icon.png)

Tippen oder klicken Sie auf das Symbol, um die Vererbung für die ausgewählte Komponente wiederherzustellen. Sie müssen die Seite neu laden, um den Inhalt zu aktualisieren und die übernommenen Inhalte anzuzeigen.

Weitere Informationen zum Aktivieren dieser Erweiterung [finden Sie in der Dokumentation zu Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

>[!NOTE]
>
>Die Symbole **Vererbung installiert** und **Vererbung unterbrochen** werden nur angezeigt, wenn eine Komponente ausgewählt wurde und die Seite auf einer Blueprint basiert.

>[!NOTE]
>
>Die **AEM-Erweiterung für Multi-Site-Management (MSM)** funktioniert nur für Seiten, nicht für Inhaltsfragmente.

### Zugreifen auf Seiteneigenschaften {#page-properties}

Die **AEM-Erweiterung für Seiteneigenschaften** ermöglicht den schnellen Zugriff auf das [Fenster „Seiteneigenschaften“](/help/sites-cloud/authoring/sites-console/page-properties.md) für die aktuell in Bearbeitung befindliche Seite.

![Symbol „Seiteneigenschaften“](assets/page-properties-icon.png)

Tippen oder klicken Sie in der Symbolleiste des universellen Editors auf das Symbol **Seiteneigenschaften**, um die Seiteneigenschaften für die Seite in einem neuen Browser-Tab zu öffnen.

Weitere Informationen zum Aktivieren dieser Erweiterung [finden Sie in der Dokumentation zu Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

>[!NOTE]
>
>Die **AEM-Erweiterung für Seiteneigenschaften** funktioniert nur für Seiten, nicht für Inhaltsfragmente.

### Zugreifen auf die Sites-Konsole {#sites-console}

Die **AEM-Erweiterung für Site Admin** ermöglicht den schnellen Zugriff auf die Seite, die in der [Sites-Konsole von AEM bearbeitet wird](/help/sites-cloud/authoring/sites-console/introduction.md), und ermöglicht Ihnen die Navigation in der Site-Baumstruktur oder das Ausführen von Aktionen auf Seitenebene in der Konsole.

![Symbol „In Site Admin öffnen“](assets/open-in-site-admin-icon.png)

Tippen oder klicken Sie auf das Symbol, um die Sites-Konsole in einem neuen Browser-Tab zu öffnen, und navigieren Sie zu der Seite, die sich derzeit im Editor befindet.

Weitere Informationen zum Aktivieren dieser Erweiterung [finden Sie in der Dokumentation zu Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

### Sperren und Entsperren von Seiten {#locking-pages}

Die **AEM-Erweiterung für Seitensperren** zeigt den aktuellen Sperrstatus der Seite im Editor an und ermöglicht es Ihnen, die Seite zu [sperren oder zu entsperren](/help/sites-cloud/authoring/sites-console/managing-pages.md#locking-a-page).

Das Symbol **Entsperrt** in der Symbolleiste des universellen Editors zeigt an, dass die aktuell im Editor befindliche Seite nicht gesperrt ist.

![Symbol „Entsperrt“](assets/unlocked-icon.png)

Tippen oder klicken Sie auf das Symbol, um die Seite zu sperren.

Das Symbol **Gesperrt** in der Symbolleiste des universellen Editors zeigt an, dass die aktuell im Editor befindliche Seite gesperrt ist. Bewegen Sie den Mauszeiger über das Symbol für eine QuickInfo mit Angabe der Person, die die Seite gesperrt hat.

![Symbol „Gesperrt“](assets/locked-icon.png)

Tippen oder klicken Sie auf das Symbol, um die Seite zu entsperren, wenn Sie die Person sind, die sie gesperrt hat.

Weitere Informationen zum Aktivieren dieser Erweiterung [finden Sie in der Dokumentation zu Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

>[!NOTE]
>
>Die **AEM-Erweiterung für Seitensperren** funktioniert nur für Seiten, nicht für Inhaltsfragmente.

### Workflows {#workflows}

Die **AEM-Erweiterung für Workflows** ermöglicht das [Starten eines Workflows](/help/sites-cloud/authoring/workflows/overview.md) für die aktuell im Editor befindliche Seite.

![Symbol „Workflows“](assets/workflows-icon.png)

Tippen oder klicken Sie in der Symbolleiste des universellen Editors auf das Symbol **Workflows**, um das Modal **Workflow starten** zu öffnen. Im Fenster werden die möglichen Inhalte aufgelistet, auf die Sie einen Workflow anwenden können.

![Modal „Workflow starten“](assets/start-a-workflow.png)

1. Wählen Sie in der Dropdown-Liste **Workflow-Modell** den anzuwendenden Workflow aus.
1. Geben Sie im Feld **Name** eine Beschreibung für den Workflow an.
1. Legen Sie in der Liste **In den Workflow aufzunehmender Content** anhand der Kontrollkästchen fest, welche Inhalte in den Workflow aufgenommen werden sollen.
1. Tippen oder klicken Sie auf **Workflow starten**, um den Workflow zu starten, oder auf **Schließen**, um ihn abzubrechen.

Weitere Informationen zum Aktivieren dieser Erweiterung [finden Sie in der Dokumentation zu Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

### Anmeldung als Entwicklerin oder Entwickler {#developer-login}

Die **AEM-Erweiterung für die Anmeldung als Entwicklerin oder Entwickler beim universellen Editor** ist für Entwicklerinnen und Entwickler nützlich, die lokal entwickeln, und ermöglicht eine praktische Methode zur Authentifizierung bei einem lokalen AEM-SDK zu Testzwecken.

![Symbol „Anmeldung als Entwicklerin oder Entwickler“](assets/developer-login-icon.png)

Tippen oder klicken Sie in der Symbolleiste des universellen Editors auf das Symbol **Anmeldung als Entwicklerin oder Entwickler**, um Ihre lokalen Anmeldedaten für die Anmeldung bei Ihrem lokalen AEM-SDK anzugeben.

![Modal „Anmeldung als Entwicklerin oder Entwickler“](assets/developer-login.png)

Weitere Informationen zum Aktivieren dieser Erweiterung [finden Sie in der Dokumentation zu Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

## Optionale Funktionen des Panels „Eigenschaften“ {#properties-panel-options}

Zusätzliche Funktionen sind als Erweiterungen des universellen Editors verfügbar und unterstützen Sie bei der weiteren Verwaltung Ihrer Seiteninhalte. [Diese Erweiterungen müssen in Ihrem Programm von einer bzw. einem Admin aktiviert werden](/help/implementing/universal-editor/extending.md), bevor sie für Sie als Inhaltsautorin bzw. Inhaltsautor in der [Symbolleiste des universellen Editors](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail) sichtbar sind.

### Varianten generieren {#generate-variations}

Mit der Erweiterung **Varianten generieren** können Sie generative künstliche Intelligenz (KI) verwenden, um Varianten für Ihre Inhalte direkt im Panel „Eigenschaften“ zu erstellen.

![Symbol „Varianten generieren“](assets/generate-variations-icon.png)

Tippen oder klicken Sie in der Symbolleiste des universellen Editors auf das Symbol **Varianten generieren**, um Empfehlungen zu erhalten und Varianten zu erstellen. Weitere Informationen zum Generieren von Varianten finden Sie im Dokument [Varianten generieren – in AEM-Editoren integriert](/help/generative-ai/generate-variations-integrated-editor.md).

Weitere Informationen zum Aktivieren dieser Erweiterung [finden Sie in der Dokumentation zu Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

## Zusätzliche Ressourcen {#additional-resources}

Informationen zum Veröffentlichen von Inhalten mit dem universellen Editor finden Sie in diesem Dokument.

* [Veröffentlichen von Inhalten mit dem universellen Editor](publishing.md) – Erfahren Sie, wie mit dem universellen Editor Inhalte veröffentlicht werden und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.

Weitere Informationen zu den technischen Details zum universellen Editor finden Sie in diesen Entwicklerdokumenten.

* [Einführung in den universellen Editor](/help/implementing/universal-editor/introduction.md) – Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Aspekte von Inhalten in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen und die Inhaltsgeschwindigkeit zu erhöhen.
* [Erste Schritte mit dem universellen Editor in AEM](/help/implementing/universal-editor/getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](/help/implementing/universal-editor/architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](/help/implementing/universal-editor/attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Authentifizierung beim universellen Editor](/help/implementing/universal-editor/authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.
