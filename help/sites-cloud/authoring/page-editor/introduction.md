---
title: Der AEM Seiteneditor
description: Der AEM-Seiteneditor ist ein leistungsstarkes Tool für die Inhaltserstellung.
source-git-commit: f11635b799a9154ff3fcaac5faca429a12f7a62b
workflow-type: tm+mt
source-wordcount: '1400'
ht-degree: 43%

---


# Der AEM Seiteneditor {#editing-page-content}

Sobald Ihre Seite im **Sites** können Sie den Inhalt der Seite mit dem AEM Seiteneditor bearbeiten, einem leistungsstarken Tool zur Inhaltserstellung.

>[!NOTE]
>
>Ihr Konto muss über die entsprechenden Zugriffsrechte und Berechtigungen verfügen, um Seiten bearbeiten zu können. Wenden Sie sich an Ihren Systemadministrator, wenn Sie keine Berechtigungen haben.

## Ausrichtung {#orientation}

Der AEM Seiteneditor besteht in erster Linie aus drei Bereichen:

1. [Die Symbolleiste](#toolbar) - Über die Symbolleiste können Sie schnell auf den Seitenmodus wechseln und auf zusätzliche Seiteneinstellungen zugreifen.
1. [Seitenbereich](#side-panel) - Im Seitenbereich erhalten Sie Zugriff auf Seitenkomponenten und -Assets sowie auf andere Authoring-Tools.
1. [Der Editor](#editor) - Im Editor können Sie Änderungen an Ihrem Inhalt vornehmen und eine Vorschau davon anzeigen.

![Das Layout des Seiteneditors](assets/page-editor-layout.png)

Inhalte werden mithilfe von [Komponenten](/help/sites-cloud/authoring/components-console.md) hinzugefügt (entsprechend dem Inhaltstyp), die per Drag-and-Drop auf die Seite gezogen werden können. Dort können sie dann bearbeitet, verschoben oder gelöscht werden.

### Symbolleiste {#page-toolbar}

Die Seitensymbolleiste bietet Zugriff auf kontextbezogene Funktionen, abhängig von der Seitenkonfiguration.

![Symbolleiste des Seiteneditors](assets/page-editor-toolbar.png)

#### Seitenbereich {#side-panel-button}

Dadurch wird die [Seitenbereich,](/help/sites-cloud/authoring/page-editor/editor-side-panel.md) , der den Asset-Browser, den Komponenten-Browser und die Inhaltsstruktur enthält.

![Seitliches Bedienfeld ein/aus](assets/page-editor-side-panel-toggle.png)

#### Seiteninformationen {#page-information}

Dadurch erhalten Sie Zugriff auf detaillierte Seiteninformationen, einschließlich Seitendetails und Aktionen, die auf der Seite ausgeführt werden können, einschließlich Anzeigen und Bearbeiten von Seiteninformationen, Anzeigen von Seiteneigenschaften und Veröffentlichen/Rückgängigmachen der Veröffentlichung der Seite.

![Schaltfläche „Seiteninformationen“](assets/page-editor-page-information-icon.png)

**Seiteninformationen** öffnet ein Dropdown-Menü mit Details zur letzten Bearbeitung und zur letzten Veröffentlichung der ausgewählten Seite. Je nach den Eigenschaften der Seite, ihrer Site und Ihrer Instanz sind zusätzliche Aktionen verfügbar.

* [Eigenschaften öffnen](/help/sites-cloud/authoring/sites-console/page-properties.md)
* [Seiten-Rollout](/help/sites-cloud/administering/msm/overview.md#msm-from-the-ui)
* [Workflow starten](/help/sites-cloud/authoring/workflows/applying.md#starting-a-workflow-from-the-page-editor)
* [Sperren einer Seite](/help/sites-cloud/authoring/page-editor/introduction.md#locking-unlocking)
* [Seite veröffentlichen](/help/sites-cloud/authoring/sites-console/publishing-pages.md#publishing-pages-1)
* [Veröffentlichen einer Seite aufheben](/help/sites-cloud/authoring/sites-console/publishing-pages.md#unpublishing-pages)
* [Vorlage bearbeiten](/help/sites-cloud/authoring/sites-console/templates.md)
* [Als veröffentlicht anzeigen](/help/sites-cloud/authoring/page-editor/introduction.md#view-as-published)
* [In Admin anzeigen](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources)
* [Hilfe](/help/sites-cloud/authoring/basic-handling.md#accessing-help)
* [Launch bewerben](/help/sites-cloud/authoring/launches/promoting.md) (nur wenn die Seite ein Launch ist)

Darüber hinaus können über die **Seiteninformationen** ggf. auch Analysen und Empfehlungen aufgerufen werden.

#### Emulator {#emulator}

Dadurch wird die [Emulator-Symbolleiste](/help/sites-cloud/authoring/page-editor/responsive-layout.md#selecting-a-device-to-emulate), das verwendet wird, um das Erscheinungsbild der Seite auf einem anderen Gerät zu emulieren. Dies wird automatisch im Layout-Modus aktiviert.

![Schaltfläche „Emulator“](assets/page-editor-emulator.png)

#### ContextHub {#context-hub}

Dadurch wird die [ContextHub.](/help/sites-cloud/authoring/personalization/contexthub.md) Sie ist nur in verfügbar. **Vorschau** -Modus.

![Schaltfläche „ContextHub“](assets/page-editor-context-hub.png)

#### Seitentitel {#page-title}

Dies ist der Titel der Seite, der in Großbuchstaben als Information dargestellt wird.

![Seitentitel](assets/page-editor-page-title.png)

#### Modusauswahl {#mode-selector}

Die Modusauswahl zeigt die aktuelle [mode](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector) und ermöglicht die Auswahl eines anderen Modus wie Bearbeiten, Layout, Timewarp oder Targeting.

![Schaltfläche „Modusauswahl“](assets/page-editor-mode-selector.png)

Für die Bearbeitung von Seiten stehen verschiedene Modi zur Verfügung, über die jeweils unterschiedliche Aktionen durchgeführt werden können:

* [Bearbeiten](/help/sites-cloud/authoring/page-editor/edit-content.md) - Der beim Bearbeiten des Seiteninhalts zu verwendende Modus
* [Layout](/help/sites-cloud/authoring/page-editor/responsive-layout.md) - Hiermit können Sie Ihr responsives Layout geräteabhängig erstellen und bearbeiten (wenn die Seite auf einem Layout-Container basiert).
* [Targeting](/help/sites-cloud/authoring/personalization/targeted-content.md) - Verbessert die Inhaltsrelevanz durch Targeting und Messungen über alle Kanäle hinweg.
* [Timewarp](/help/sites-cloud/authoring/sites-console/page-versions.md#timewarp) - Anzeigen des Seitenstatus zu einem bestimmten Zeitpunkt
* [Live Copy-Status](/help/sites-cloud/authoring/page-editor/introduction.md#live-copy-status) - Ermöglicht einen schnellen Überblick über den Live Copy-Status und darüber, welche Komponenten übernommen werden/nicht
* [Entwicklermodus](/help/implementing/developing/tools/developer-mode.md)
* [Vorschau](/help/sites-cloud/authoring/page-editor/introduction.md#previewing-pages) - Zeigen Sie die Seite so an, wie sie in der Veröffentlichungsumgebung angezeigt wird, oder navigieren Sie mithilfe von Links im Inhalt.
* [Anmerken](/help/sites-cloud/authoring/page-editor/annotations.md) - Hinzufügen oder Anzeigen von Anmerkungen auf der Seite

>[!NOTE]
>
>* Je nach den Merkmalen der Seite sind einige Modi ggf. nicht verfügbar.
>* Für den Zugriff auf einige Modi sind die entsprechenden Berechtigungen erforderlich.
>* Aus Platzgründen steht der Entwicklermodus auf Mobilgeräten nicht zur Verfügung.
>* Mit dem [Tastaturbefehl](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md) `Ctrl-Shift-M` können Sie zwischen der **Vorschau** und dem aktuell ausgewählten Modus (z. B. **Bearbeiten**, **Layout**) wechseln.

#### Vorschau {#preview}

Die **Vorschau** Schaltfläche aktiviert [Vorschaumodus.](#preview-mode), wodurch die Seite so angezeigt wird, wie sie bei der Veröffentlichung erscheint.

![Schaltfläche „Vorschau“](assets/page-editor-preview.png)

#### Anmerken {#annotate}

**Anmerken** -Modus können Sie [Anmerkungen](/help/sites-cloud/authoring/page-editor/annotations.md) auf der Seite, wenn Sie eine Seite überprüfen. Nach der ersten Anmerkung ändert sich das Symbol in eine Zahl, die die Anzahl der Anmerkungen auf der Seite anzeigt.

![Schaltfläche „Anmerkungen“](assets/page-editor-annotations.png)

### Seitenbereich {#side-panel}

Im seitlichen Bedienfeld haben Sie Zugriff auf drei verschiedene Registerkarten.

* Komponenten-Browser zum Hinzufügen neuer Inhalte zu Ihrer Seite
* Asset-Browser zum Hinzufügen neuer Assets zu Ihrer Seite
* Die Inhaltsstruktur zum Durchsuchen der Struktur Ihrer Seite

![Seitenbereich des Seiteneditors](assets/page-editor-side-panel.png)

Lesen Sie das Dokument . [Seitenbereich des Seiteneditors](/help/sites-cloud/authoring/page-editor/editor-side-panel.md) für weitere Informationen.

### Bearbeiter {#editor}

Im Editor nehmen Sie Änderungen direkt am Seiteninhalt vor. Die Seite wird so gerendert, wie Sie sie sehen würden, und Sie können neue Inhalte mithilfe der Assets- oder Komponenten-Browser in das Seitenbedienfeld ziehen und dort Inhalt bearbeiten.

![Der Editor des Seiteneditors](assets/page-editor-editor.png)

## Bearbeiten von Inhalten {#editing-content}

Nachdem Sie nun den Seiteneditor kennen, können Sie Ihren Inhalt bearbeiten.

Lesen Sie das Dokument . [Bearbeiten von Inhalten mit dem AEM Seiteneditor](/help/sites-cloud/authoring/page-editor/edit-content.md) für weitere Informationen.

## Statusbenachrichtigung {#status-notification}

Wenn eine Seite Teil eines [Workflow](/help/sites-cloud/authoring/workflows/overview.md) Diese Informationen werden bei der Bearbeitung der Seite in einer Benachrichtigungsleiste unter der Symbolleiste angezeigt.

![Workflow-Benachrichtigung](assets/page-editor-editing-workflow-notification.png)

>[!NOTE]
>
>Die Statusleiste ist nur für Benutzerkonten mit entsprechenden Berechtigungen sichtbar.

In der Benachrichtigung ist der Workflow aufgeführt, dem die Seite zugeordnet ist. Wenn Benutzende am aktuellen Workflow-Schritt beteiligt sind, sind zusätzlich auch Optionen verfügbar, die sich [auf den Workflow-Status auswirken](/help/sites-cloud/authoring/workflows/participating.md) und die weiteren Informationen zum Workflow liefern, darunter:

* **Abschließen**: Öffnet das Dialogfeld **Arbeitselement abschließen**.
* **Delegieren**: Öffnet das Dialogfeld **Arbeitselement abschließen**.
* **Details anzeigen**: Öffnet das Fenster **Details** des entsprechenden Workflows.

Das Fertigstellen und Delegieren von Workflow-Schritten über die Benachrichtigungsleiste erfolgt auf die gleiche Art und Weise wie beim [Teilnehmen an Workflows](/help/sites-cloud/authoring/workflows/participating.md) über den Benachrichtigungs-Posteingang.

Wenn die Seite mehreren Workflows unterliegt, werden in der Benachrichtigung rechts außen die Anzahl der Workflows sowie Pfeilschaltflächen angezeigt, über die Sie durch die einzelnen Workflows scrollen können.

![Mehrere Workflow-Benachrichtigungen](assets/page-editor-editing-workflow-notification-multiple.png)

## Live Copy-Status {#live-copy-status}

Die **Live Copy-Status** Im Seitenmodus erhalten Sie einen schnellen Überblick über den Live Copy-Status und darüber, welche Komponenten übernommen werden/nicht:

* Grüner Rahmen: Vererbt
* Rosa Rahmen: Vererbung wurde abgebrochen

Beispiel:

![Beispiel für einen Live Copy-Status](assets/page-editor-editing-live-copy-status.png)

## Anzeigen einer Seitenvorschau {#previewing-pages}

Für die Anzeige einer Seitenvorschau stehen zwei Optionen zur Verfügung:

* [Vorschaumodus](#preview-mode) - Schnellere Vorschau an Ort und Stelle
* [Als veröffentlicht anzeigen](#view-as-published) - Eine vollständige Vorschau, die die Seite in einer neuen Registerkarte öffnet

>[!TIP]
>
>* Links im Inhalt sind sichtbar, können jedoch nicht in **Bearbeiten** -Modus.
>* Verwenden Sie eine der Vorschauoptionen, wenn Sie mithilfe von Links navigieren möchten.
>* Verwenden Sie den [Tastaturbefehl](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md) `Ctrl-Shift-M` (Strg+Umschalt+M), um zwischen der Vorschau und dem zuletzt ausgewählten Modus zu wechseln.

>[!NOTE]
>
>Das WCM-Modus-Cookie wird für beide Vorschauoptionen gesetzt.

### Vorschaumodus {#preview-mode}

Beim Bearbeiten von Inhalten können Sie mithilfe des Vorschaumodus eine Vorschau der Seite anzeigen. Dieser Modus:

* Blendet diverse Bearbeitungsmechanismen aus, damit Sie einen schnellen Überblick darüber erhalten, wie die Seite veröffentlicht aussehen wird.
* Ermöglicht die Verwendung von Links zur Navigation.
* Aktualisiert **nicht** den Seiteninhalt.

Beim Authoring ist der Vorschaumodus über das Symbol oben rechts im Seiteneditor verfügbar:

![Schaltfläche „Vorschau“](assets/page-editor-preview.png)

### Als veröffentlicht anzeigen {#view-as-published}

Die Option **Als veröffentlicht anzeigen** ist über das Menü [Seiteninformationen](#page-information) verfügbar. Dadurch wird die Seite in einer neuen Registerkarte geöffnet und der Inhalt aktualisiert, und die Seite wird genau so angezeigt, wie sie in der Publishing-Umgebung angezeigt wird.

## Sperren und Entsperren einer Seite {#locking-unlocking}

AEM ermöglicht das Sperren einer Seite, sodass niemand anders den Inhalt bearbeiten kann. Das Sperren ist nützlich, wenn Sie zahlreiche Bearbeitungen an einer bestimmten Seite vornehmen oder wenn Sie eine Seite für eine kurze Zeit einfrieren müssen.

1. Wählen Sie das Symbol **Seiteninformationen** aus, um das Auswahlmenü zu öffnen.
1. Wählen Sie die Option **Seite sperren** aus.

Nach der Sperrung wird in der Symbolleiste des Seiteneditors ein Sperrsymbol angezeigt.

![Beispiel für eine gesperrte Seite](assets/page-editor-editing-locked-page.png)

Das Entsperren einer Seite ähnelt sehr dem [Sperren der Seite](#locking-a-page). Sobald die Seite gesperrt ist, werden die Sperroptionen durch Aktionen zum Entsperren ersetzt.

>[!CAUTION]
>
>* Wird stellvertretend für andere Benutzende agiert, ist es möglich, eine Seite zu sperren. Eine auf diese Weise gesperrte Seite kann jedoch nur dann (von Kunden) entsperrt werden, wenn der Benutzer verwendet wird, für den stellvertretend agiert wurde.
>* Seiten können nicht entsperrt werden, indem man sich als der Benutzer ausgibt, der die Seite gesperrt hat.
>* Wenn die Benutzerin bzw. der Benutzer, die bzw. der die Seite gesperrt hat, nicht zum Entsperren der Seite verfügbar ist, wenden Sie sich an den Support, um sich über Optionen zum Entfernen der Sperrung zu informieren.

## Rückgängigmachen und Wiederholen von Seitenbearbeitungen {#undoing-and-redoing-page-edits}

Mit den folgenden Symbolen können Sie eine Aktion rückgängig machen oder wiederholen. Diese werden gegebenenfalls in der Symbolleiste angezeigt:

![Schaltflächen „Rückgängig“ und „Wiederholen“](assets/page-editor-redo.png)

>[!TIP]
>
>* Mit dem [Tastaturbefehl](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md) `Ctrl-Z` (Strg+Z) können Sie Bearbeitungen ebenfalls rückgängig machen.
>* Analog dazu können Sie zum Wiederholen von Bearbeitungen den Tastaturbefehl `Ctrl-Y` (Strg+Y) verwenden.

>[!NOTE]
>
>Lesen Sie das Dokument . [Einschränkungen beim Rückgängigmachen und Wiederherstellen](/help/sites-cloud/authoring/page-editor/undo-redo.md) für die vollständigen Details darüber, was beim Rückgängigmachen und Wiederholen von Seitenbearbeitungen möglich ist.
