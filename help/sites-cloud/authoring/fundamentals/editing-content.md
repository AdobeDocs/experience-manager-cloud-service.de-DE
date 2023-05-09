---
title: Bearbeiten des Seiteninhalts
description: Nachdem die Seite erstellt wurde, können Sie den Inhalt bearbeiten, um die erforderlichen Aktualisierungen vorzunehmen
exl-id: 8af0f621-14e8-4605-a51a-a3be21f19092
source-git-commit: 81d58f25af8b023774ce8653154597d92a7ac70b
workflow-type: tm+mt
source-wordcount: '3019'
ht-degree: 70%

---

# Bearbeiten des Seiteninhalts{#editing-page-content}

Sobald Ihre Seite erstellt ist (neu oder im Rahmen eines Launch oder einer Live Copy), können Sie den Inhalt bearbeiten und die erforderlichen Aktualisierungen vornehmen.

Inhalt wird hinzugefügt mit [Komponenten](/help/sites-cloud/authoring/features/components-console.md) (entsprechend dem Inhaltstyp), der auf die Seite gezogen werden kann. Dort können sie dann bearbeitet, verschoben oder gelöscht werden.

>[!NOTE]
>
>Damit Sie Seiten bearbeiten können, muss Ihr Konto über die entsprechenden Zugriffsrechte und Berechtigungen verfügen.
>
>Wenn Sie auf Probleme stoßen, empfehlen wir Ihnen, sich an den Systemadministrator zu wenden.
<!--
>Your account needs the [appropriate access rights](/help/sites-administering/security.md) and [permissions](/help/sites-administering/security.md#permissions) to edit pages.
-->

>[!NOTE]
>
>Wenn Ihre Seite und/oder Vorlage entsprechend eingerichtet ist, können Sie das [responsive Layout](/help/sites-cloud/authoring/features/responsive-layout.md) für die Bearbeitung verwenden.

>[!TIP]
>
>Im **Bearbeitungsmodus** werden Links in Ihrem Inhalt angezeigt, können jedoch **nicht aufgerufen werden**. Verwenden Sie den [Vorschaumodus](#previewing-pages), wenn Sie mithilfe von Links in Ihrem Inhalt navigieren möchten.

## Seitensymbolleiste {#page-toolbar}

Die Seite-Symbolleiste bietet Zugriff auf die entsprechenden Funktionen, die von der Seitenkonfiguration abhängig sind.

![Seitensymbolleiste](/help/sites-cloud/authoring/assets/editing-page-toolbar.png)

Die Symbolleiste bietet Zugriff auf eine Vielzahl von Optionen. Je nach aktuellem Kontext und Ihrer Konfiguration sind einige Optionen möglicherweise nicht verfügbar.

* **Seitliches Bedienfeld ein/aus**

   Dadurch wird das seitliche Bedienfeld geöffnet/geschlossen, das die [Asset-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser), [Komponenten-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser)und [Inhaltsstruktur](/help/sites-cloud/authoring/fundamentals/environment-tools.md#content-tree).

   ![Seitliches Bedienfeld ein/aus](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

* **Seiteninformationen**

   Bietet Zugriff auf [Seiteninformationen](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) -Menü mit Seitendetails und Aktionen, die auf der Seite ausgeführt werden können, einschließlich Anzeigen und Bearbeiten von Seiteninformationen, Anzeigen von Seiteneigenschaften und Veröffentlichen/Rückgängigmachen der Veröffentlichung der Seite.

   ![Schaltfläche „Seiteninformationen“](/help/sites-cloud/authoring/assets/page-information-icon.png)

* **Emulator**

   Blendet die [Emulator-Symbolleiste](/help/sites-cloud/authoring/features/responsive-layout.md#selecting-a-device-to-emulate) ein bzw. aus, über die das Look-and-Feel der Seite auf einem anderen Gerät emuliert werden kann. Dies wird automatisch im Layout-Modus umgeschaltet.

   ![Schaltfläche „Emulator“](/help/sites-cloud/authoring/assets/emulator.png)

* **ContextHub**

   Öffnet den [ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md). Dieser ist nur im Vorschaumodus verfügbar.

   ![Schaltfläche „ContextHub“](/help/sites-cloud/authoring/assets/context-hub.png)

* **Seitentitel**

   Das ist rein informativ.

   ![Seitentitel](/help/sites-cloud/authoring/assets/page-title.png)

* **Modusauswahl**

   Zeigt den aktuellen [mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) und ermöglicht Ihnen die Auswahl eines anderen Modus wie Bearbeiten, Layout, Timewarp oder Targeting.

   ![Schaltfläche „Modusauswahl“](/help/sites-cloud/authoring/assets/mode-selector.png)

* **Vorschau**

   Aktiviert den [Vorschaumodus](#preview-mode). Dadurch wird die Seite so angezeigt, wie sie bei der Veröffentlichung erscheint.

   ![Schaltfläche „Vorschau“](/help/sites-cloud/authoring/assets/preview.png)

* **Anmerken**

   Hierüber können Sie die Seite mit [Anmerkungen](/help/sites-cloud/authoring/fundamentals/annotations.md) versehen (z. B. zu Prüfungszwecken). Nach der ersten Anmerkung ändert sich das Symbol in eine Zahl, die die Anzahl der Anmerkungen auf der Seite angibt.

   ![Schaltfläche „Anmerkungen“](/help/sites-cloud/authoring/assets/annotations.png)

### Statusbenachrichtigung {#status-notification}

Wird eine Seite bearbeitet, die einem oder mehreren [Workflows](/help/sites-cloud/authoring/workflows/overview.md) unterliegt, wird oben im Bildschirm eine Benachrichtigungsleiste mit einem entsprechenden Hinweis angezeigt.

![Workflow-Benachrichtigung](/help/sites-cloud/authoring/assets/editing-workflow-notification.png)

>[!NOTE]
>
>Die Statusleiste ist nur für Benutzerkonten mit entsprechenden Berechtigungen sichtbar.

In der Benachrichtigung ist der Workflow aufgeführt, dem die Seite zugeordnet ist. Wenn der Benutzer am aktuellen Workflow-Schritt beteiligt ist, Optionen zum [auf den Workflow-Status](/help/sites-cloud/authoring/workflows/participating.md) und erhalten weitere Informationen zum Workflow, z. B.:

* **Abschließen**: Öffnet das Dialogfeld **Arbeitselement abschließen**.
* **Delegieren**: Öffnet das Dialogfeld **Arbeitselement abschließen**.
* **Details anzeigen**: Öffnet das Fenster **Details** des entsprechenden Workflows.

Das Fertigstellen und Delegieren von Workflow-Schritten über die Benachrichtigungsleiste erfolgt auf die gleiche Art und Weise wie beim [Teilnehmen an Workflows](/help/sites-cloud/authoring/workflows/participating.md) über den Benachrichtigungs-Posteingang.

Wenn die Seite mehreren Workflows unterliegt, werden in der Benachrichtigung rechts außen die Anzahl der Workflows sowie Pfeilschaltflächen angezeigt, über die Sie durch die einzelnen Workflows scrollen können.

![Mehrere Workflow-Benachrichtigungen](/help/sites-cloud/authoring/assets/editing-workflow-notification-multiple.png)

## Komponenten-Platzhalter {#component-placeholder}

Der Komponenten-Platzhalter zeigt an, wo eine Komponente platziert wird, wenn Sie sie per Drag-and-Drop ablegen – oberhalb der Komponente, über der sich der Mauszeiger gerade befindet:

* Beim Hinzufügen einer neuen Komponente zur Seite (Ziehen aus dem Komponenten-Browser):

   ![Platzhalter beim Hinzufügen einer neuen Komponente zu einer Seite](/help/sites-cloud/authoring/assets/editing-component-placeholder.png)

* Wenn Sie eine vorhandene Komponente verschieben:

   ![Platzhalter beim Verschieben einer vorhandenen Komponente auf einer Seite](/help/sites-cloud/authoring/assets/editing-component-placeholder-existing.png)

## Einfügen einer Komponente {#inserting-a-component}

### Einfügen einer Komponente aus dem Komponenten-Browser {#inserting-a-component-from-the-components-browser}

Sie können eine neue Komponente mit dem [Komponenten-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) hinzufügen. Der [Komponenten-Platzhalter](#component-placeholder) zeigt an, wo die Komponente platziert wird:

1. Öffnen Sie die Seite im Modus [**Bearbeiten**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes).
1. Öffnen Sie den [Komponenten-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).
1. Ziehen Sie die benötigte Komponente an die [passende Position](#component-placeholder).
1. [Bearbeiten](#edit-content) Sie die Komponente.

>[!NOTE]
>
>Auf Mobilgeräten nimmt der Komponenten-Browser den gesamten Bildschirm ein. Sobald Sie mit dem Ziehen einer Komponente beginnen, wird der Browser geschlossen, um die Seite erneut anzuzeigen, damit Sie die Komponente platzieren können.

### Einfügen einer Komponente aus dem Absatzsystem {#inserting-a-component-from-the-paragraph-system}

Sie können eine neue Komponente über das Feld **Komponenten hierher ziehen** des Absatzsystems hinzufügen.

1. Öffnen Sie die Seite im Modus [**Bearbeiten**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes).
1. Es gibt zwei Möglichkeiten, eine neue Komponente aus dem Absatzsystem auszuwählen und hinzuzufügen:

   * Wählen Sie die **Komponente einfügen** Option (+) in der Symbolleiste einer vorhandenen Komponente oder der **Komponenten hierher ziehen** ankreuzen.

      ![Einfügen einer Komponente](/help/sites-cloud/authoring/assets/editing-insert-component.png)

   * Wenn Sie ein Desktop-Gerät verwenden, können Sie die Aktion per Doppelklick auf das Feld **Komponenten hierher ziehen** durchführen.

   * Das Dialogfeld **Neue Komponente einfügen** wird geöffnet. Dort können Sie die erforderliche Komponente auswählen:

      ![Dialogfeld „Neue Komponente einfügen“](/help/sites-cloud/authoring/assets/editing-insert-component-selection.png)

1. Die ausgewählte Komponente wird unten auf der Seite hinzugefügt. [Bearbeiten](#edit-content) Sie bei Bedarf die Komponente.

### Einfügen einer Komponente mit dem Assets-Browser {#inserting-a-component-using-the-assets-browser}

Sie können auch eine neue Komponente zur Seite hinzufügen, indem Sie ein Asset aus dem [Asset-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser). Dadurch wird automatisch eine neue Komponente des entsprechenden Typs erstellt (und das Asset enthält).

Dieses Verhalten kann für Ihre Installation konfiguriert werden. Weitere Informationen finden Sie unter „Konfigurieren eines Absatzsystems zum Erstellen einer Komponenteninstanz infolge des Ziehens eines Assets“. <!--This behavior can be configured for your installation. See [Configuring a Paragraph System so that Dragging an Asset Creates a Component Instance](/help/sites-developing/developing-components.md#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance) for further details.-->

So erstellen Sie eine Komponente, indem Sie einen der obigen Asset-Typen ziehen:

1. Öffnen Sie die Seite im Modus [**Bearbeiten**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes).
1. Öffnen Sie die [Asset-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser).
1. Ziehen Sie das gewünschte Asset an die gewünschte Position. Der [Komponenten-Platzhalter](#component-placeholder) zeigt an, wo die Komponente platziert wird.

   Eine für den Asset-Typ geeignete Komponente wird am erforderlichen Speicherort erstellt und enthält das ausgewählte Asset.

1. [Bearbeiten](#edit-content) Sie bei Bedarf die Komponente.

>[!NOTE]
>
>Auf Mobilgeräten nimmt der Asset-Browser den gesamten Bildschirm ein. Sobald Sie mit dem Ziehen eines Assets beginnen, wird der Browser geschlossen, um die Seite erneut anzuzeigen, damit Sie das Asset platzieren können.

Wenn Sie beim Durchsuchen der Assets feststellen, dass Sie an einem Asset eine schnelle Änderung vornehmen müssen, können Sie die [Asset-Editor](/help/assets/manage-digital-assets.md) durch Klicken auf das Bearbeitungssymbol neben dem Asset-Namen direkt aus dem Browser heraus.

![Schaltfläche „Asset bearbeiten“](/help/sites-cloud/authoring/assets/asset-edit-button.png)

## Komponenten-Symbolleiste {#component-toolbar}

Wenn Sie eine Komponente auswählen, wird die Symbolleiste geöffnet. Dort haben Sie Zugriff auf verschiedene Aktionen, die Sie auf die Komponente anwenden können.

Die tatsächlichen für den Benutzer verfügbaren Aktionen werden abhängig von der jeweiligen Situation angezeigt, sodass hier u. U. nicht alle möglichen Aktionen beschrieben werden.

![Komponentensymbolleiste](/help/sites-cloud/authoring/assets/editing-component-toolbar.png)

* **Bearbeiten**

   [Abhängig vom Komponententyp](/help/sites-cloud/authoring/fundamentals/components.md) können Sie hierüber den [Inhalt der Komponente bearbeiten](#edit-content). Häufig wird eine Symbolleiste angezeigt.

   ![Schaltfläche „Bearbeiten“](/help/sites-cloud/authoring/assets/editing-component-toolbar-edit.png)

* **Konfigurieren**

   [Abhängig vom Komponententyp](/help/sites-cloud/authoring/fundamentals/components.md) können Sie hierüber die Eigenschaften der Komponente bearbeiten und konfigurieren. Häufig wird ein Dialogfeld geöffnet.

   ![Schaltfläche „Konfigurieren“](/help/sites-cloud/authoring/assets/editing-component-toolbar-configure.png)

* **Kopieren**

   Kopiert die Komponente in die Zwischenablage. Nach dem Einfügen bleibt die ursprüngliche Komponente erhalten.

   ![Schaltfläche „Kopieren“](/help/sites-cloud/authoring/assets/editing-component-toolbar-copy.png)

* **Ausschneiden**

   Kopiert die Komponente in die Zwischenablage. Nach dem Einfügen wird die ursprüngliche Komponente entfernt.

   ![Schaltfläche „Ausschneiden“](/help/sites-cloud/authoring/assets/editing-component-toolbar-cut.png)

* **Löschen**

   Dadurch wird die Komponente mit Ihrer Bestätigung von der Seite gelöscht.

   ![Schaltfläche „Löschen“](/help/sites-cloud/authoring/assets/editing-component-toolbar-delete.png)

* **Komponente einfügen**

   Dadurch wird das Dialogfeld geöffnet für [Hinzufügen einer neuen Komponente](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component-from-the-paragraph-system).

   ![Schaltfläche „Einfügen“](/help/sites-cloud/authoring/assets/editing-component-toolbar-insert.png)

* **Einfügen**

   Fügt die Komponente aus der Zwischenablage in die Seite ein. Ob das Original erhalten bleibt, hängt davon ab, ob Sie die Kopie oder den Schnitt verwendet haben.

   * Sie können auf derselben Seite oder auf einer anderen Seite einfügen.
   * Das eingefügte Element wird über dem Element eingefügt, in dem Sie die Einfügeaktion auswählen.
   * Die Aktion Pate wird nur angezeigt, wenn sich Inhalt in der Zwischenablage befindet.

   ![Schaltfläche „Einfügen“](/help/sites-cloud/authoring/assets/editing-component-toolbar-paste.png)

   >[!NOTE]
   >
   >Wenn Sie auf einer anderen Seite einfügen, die bereits vor dem Ausschneiden/Kopieren geöffnet war, müssen Sie die Seite aktualisieren, um den eingefügten Inhalt anzuzeigen.

* **Gruppe**

   Mit dieser Aktion können Sie mehrere Komponenten gleichzeitig auswählen. Dasselbe kann auf einem Desktop-Gerät durch ein **Strg+Klicken** oder **Befehl+Klicken**.

   ![Schaltfläche „Gruppe“](/help/sites-cloud/authoring/assets/editing-component-toolbar-group.png)

* **Übergeordnet**

   Hierüber können Sie die Komponente auswählen, die der ausgewählten Komponente übergeordnet ist.

   ![Schaltfläche „Übergeordnet“](/help/sites-cloud/authoring/assets/editing-component-toolbar-parent.png)

* **Layout**

   Hierüber können Sie das [Layout](/help/sites-cloud/authoring/fundamentals/editing-content.md#edit-component-layout) der ausgewählten Komponente ändern. Dies gilt nur für die ausgewählte Komponente, nicht aber für die [Layout-Modus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) für die gesamte Seite.

   ![Schaltfläche „Layout“](/help/sites-cloud/authoring/assets/editing-component-toolbar-layout.png)

* **In Experience Fragment-Variante umwandeln**

   Hierüber können Sie ein neues [Experience Fragment](/help/sites-cloud/authoring/fundamentals/experience-fragments.md) aus der ausgewählten Komponente erstellen oder einem bestehenden Experience Fragment hinzufügen.

   ![Schaltfläche „In Experience Fragment-Variante umwandeln“](/help/sites-cloud/authoring/assets/editing-component-toolbar-xf.png)

## Inhalt bearbeiten {#edit-content}

Für das Hinzufügen und/oder Bearbeiten von Inhalten in Komponenten sind zwei Verfahren verfügbar:

* Öffnen Sie die [Komponentendialogfeld für die Bearbeitung](#component-edit-dialog).
* [Ziehen Sie ein Asset](#drag-and-drop-assets-into-component) aus dem Asset-Browser, um Inhalt direkt hinzuzufügen.

### Dialogfeld „Komponente bearbeiten“ {#component-edit-dialog}

Sie können eine Komponente öffnen, um den Inhalt zu bearbeiten, indem Sie das Symbol [„Bearbeiten“ (Stiftsymbol) in der Komponenten-Symbolleiste](#component-toolbar) verwenden.

Welche Bearbeitungsoptionen verfügbar sind, hängt von der Komponente ab (und für einige Komponenten sind [alle Aktionen nur im Vollbildmodus verfügbar)](#edit-content-full-screen-mode). Beispiel:

* Textkomponente

   ![Symbolleiste der Textkomponente](/help/sites-cloud/authoring/assets/editing-text-component-toolbar.png)

* Bildkomponente

   ![Symbolleiste der Bildkomponente](/help/sites-cloud/authoring/assets/editing-image-component-toolbar.png)

   >[!NOTE]
   >
   >Die Bearbeitung funktioniert nicht bei leeren Bildkomponenten.
   >
   >Sie müssen ein Bild ziehen oder hochladen, bevor Sie die Bearbeitung starten können.

* Bildkomponente - Vollbild

   Wenn Sie den [Vollbildmodus](#edit-content-full-screen-mode) für die Bildkomponente aufrufen, haben Sie mehr Platz zum Bearbeiten des Bildes und erhalten zusätzliche Bearbeitungsoptionen wie **Map starten** und **Zoom zurücksetzen**. Außerdem können im Vollbildmodus Zuschnittvoreinstellungen ausgewählt werden.

   ![Vollbildmodus der Bildkomponente](/help/sites-cloud/authoring/assets/editing-image-component-full-screen.png)

* Bei Komponenten (aus mehreren grundlegenden Komponenten erstellt) müssen Sie zunächst die gewünschte Optionsgruppe wählen:

### Drag-and-Drop von Assets in Komponenten {#drag-and-drop-assets-into-component}

Bei bestimmten Komponententypen (z. B. Bildern) können Sie Assets aus dem Asset-Browser direkt in die Komponente ziehen und dort ablegen, um den Inhalt zu aktualisieren.

## Inhalt im Vollbildmodus bearbeiten {#edit-content-full-screen-mode}

Für alle Komponenten kann der Vollbildmodus über das folgende Symbol gestartet und beendet werden:

![Schaltfläche „Vollbild“](/help/sites-cloud/authoring/assets/editing-full-screen.png)

Z. B. die Komponente **Text**:

![Textkomponente im Vollbildmodus](/help/sites-cloud/authoring/assets/editing-text-full-screen.png)

>[!NOTE]
>
>Bei einigen Komponenten sind im Vollbildmodus mehr Optionen verfügbar als im integrierten Editor.

## Verschieben einer Komponente {#moving-a-component}

So verschieben Sie eine Absatzkomponente:

1. Wählen Sie den Absatz aus, der durch Tippen und Halten oder Klicken und Halten verschoben werden soll.
1. Ziehen Sie den Absatz an die neue Position. AEM gibt an, wo der Absatz hinterlegt werden kann. Legen Sie es an der gewünschten Position ab.

   ![Verschieben einer Komponente](/help/sites-cloud/authoring/assets/editing-moving-component.png)

1. Der Absatz wird verschoben.

>[!TIP]
>
>Sie können eine Komponente auch durch [Ausschneiden und Einfügen](#component-toolbar) verschieben.

## Bearbeiten des Komponenten-Layouts {#edit-component-layout}

Wenn Sie eine Komponente anpassen möchten, müssen Sie nicht ständig zwischen dem Bearbeitungs- und dem [Layout-Modus](/help/sites-cloud/authoring/features/responsive-layout.md) hin- und herwechseln. Mithilfe der **Layout**-Aktion können Sie das Layout einer Komponente ebenfalls ändern und dabei Zeit sparen, da Sie den Bearbeitungsmodus nicht verlassen müssen.

1. In der Sites-Konsole wird durch Auswählen einer Komponente im **Bearbeitungsmodus** die zugehörige Symbolleiste für die Komponente angezeigt.

   ![Komponenten-Symbolleiste einer Seitenkomponente](/help/sites-cloud/authoring/assets/editing-layout-toolbar.png)

   Klicken bzw. tippen Sie auf die **Layout**-Aktion, um das Layout der Komponente anzupassen.

   ![Schaltfläche „Layout“ der Komponenten-Symbolleiste](/help/sites-cloud/authoring/assets/editing-component-toolbar-layout.png)

1. Sobald die Aktion Layout ausgewählt ist:

   * Die Größenänderungsgriffe für die Komponentenanzeige.
   * Die Emulator-Symbolleiste wird oben im Bildschirm angezeigt.
   * In der Komponenten-Symbolleiste werden Layout-Aktionen anstelle der standardmäßigen Bearbeitungsaktionen angezeigt.

   ![Komponente im Layout-Modus](/help/sites-cloud/authoring/assets/editing-layout-mode.png)

   Jetzt können Sie Änderungen am Layout der Komponente auf die gleiche Art und Weise vornehmen wie im [Layout-Modus](/help/sites-cloud/authoring/features/responsive-layout.md#defining-layouts-layout-mode).

1. Wenn Sie alle Änderungen wie gewünscht vorgenommen haben, klicken Sie im Aktionsmenü der Komponente auf die Schaltfläche **Schließen**, um die Layout-Anpassung zu beenden. In der Komponenten-Symbolleiste stehen nun wieder die Standard-Bearbeitungsfunktionen zur Verfügung.

   ![Komponenten-Symbolleiste einer Seitenkomponente](/help/sites-cloud/authoring/assets/editing-layout-exit.png)

>[!TIP]
>
>Die Layout-Aktion ist immer auf die jeweils ausgewählte Komponente beschränkt. Wenn Sie etwa bei einer Komponente das Layout bearbeiten und dann auf eine andere Komponente klicken, werden in der Symbolleiste für die Bearbeitung die Layout-Aktionen durch die Standardaktionen ersetzt und die Ziehpunkte für die Größenanpassung sowie die Emulator-Symbolleiste werden nicht mehr angezeigt.
>
>Um das Layout für die gesamte Seite, d. h. über mehrere Komponenten hinweg, zu bearbeiten, wechseln Sie in den [Layout-Modus](/help/sites-cloud/authoring/features/responsive-layout.md).

## Vererbte Komponenten {#inherited-components}

Vererbung ist der Mechanismus, bei dem Inhalte automatisch von einer Komponente in eine andere verschoben werden können. Vererbte Komponenten können sich aus diversen Szenarien ergeben, wie:

* [Multi-Site-Management](/help/sites-cloud/administering/msm/overview.md)
* [Launch](/help/sites-cloud/authoring/launches/overview.md) (wenn auf einer Live Copy basierend).

Sie können die Vererbung deaktivieren (und dann wieder aktivieren). Je nach Komponente kann dies über die Komponenten-Symbolleiste erfolgen, wenn sich die Komponente auf einer Seite befindet, die Teil einer Live Copy oder eines Launch ist (wenn auf einer Live Copy basierend).

![Komponenten-Symbolleiste mit Vererbungsbeziehung](/help/sites-cloud/authoring/assets/editing-component-toolbar-inheritance.png)

Beispiel:

* Vererbung abbrechen

   ![Schaltfläche „Vererbung abbrechen“](/help/sites-cloud/authoring/assets/editing-cancel-inheritance.png)

* Vererbung wieder aktivieren (wenn die Vererbung bereits abgebrochen wurde)

   ![Schaltfläche „Vererbung wieder aktivieren“](/help/sites-cloud/authoring/assets/editing-reenable-inheritance.png)

* Die Rollout-Aktion steht auch in der Blueprint- oder Live Copy-Quelle zur Verfügung

   ![Schaltfläche „Rollout“](/help/sites-cloud/authoring/assets/editing-rollout.png)

## Bearbeiten der Seitenvorlage {#editing-the-page-template}

Sie können bequem zum [Vorlageneditor](/help/sites-cloud/authoring/features/templates.md#editing-templates-template-authors) wechseln, indem Sie die Option **Vorlage bearbeiten** im Menü [Seiteninformationen](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) auswählen.

Durch Auswählen der Seite in der [Spaltenansicht](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) oder [Listenansicht](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view) können Sie schnell und einfach feststellen, auf welcher Vorlage die Seite basiert.

## Live Copy-Status {#live-copy-status}

Die [Seitenmodus &quot;Live Copy-Status&quot;](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) bietet einen schnellen Überblick über den Live Copy-Status und darüber, welche Komponenten übernommen werden/nicht:

* Grüne Grenze: Übernommen
* Rosa Rahmen: Vererbung wurde abgebrochen

Beispiel:

![Beispiel für einen Live Copy-Status](/help/sites-cloud/authoring/assets/editing-live-copy-status.png)

## Hinzufügen von Anmerkungen {#adding-annotations}

[Anmerkungen](/help/sites-cloud/authoring/fundamentals/annotations.md) Reviewer und andere Autoren können Feedback zu Ihrem Inhalt geben. Sie werden häufig zu Überprüfungs- und Validierungszwecken verwendet.

## Anzeigen einer Seitenvorschau {#previewing-pages}

Für die Anzeige einer Seitenvorschau stehen zwei Optionen zur Verfügung:

* [Vorschaumodus](#preview-mode) – für einen schnellen Blick auf die Seite im Kontext
* [Als veröffentlicht anzeigen](#view-as-published) - eine vollständige Vorschau, die die Seite in einer neuen Registerkarte öffnet

>[!TIP]
>
>* Links im Inhalt sind sichtbar, können jedoch nicht im Bearbeitungsmodus aufgerufen werden.
>* Verwenden Sie eine der Vorschauoptionen, wenn Sie mithilfe von Links navigieren möchten.
>* Verwenden Sie den [Tastaturbefehl](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `Ctrl-Shift-M` (Strg+Umschalt+M), um zwischen der Vorschau und dem zuletzt ausgewählten Modus zu wechseln.


>[!NOTE]
>
>Das WCM-Modus-Cookie wird für beide Vorschauoptionen gesetzt.

### Vorschaumodus {#preview-mode}

Beim Bearbeiten von Inhalt können Sie mithilfe des [Vorschaumodus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) eine Vorschau der Seite anzeigen. Dieser Modus:

* Blendet diverse Bearbeitungsmechanismen aus, damit Sie einen schnellen Überblick darüber erhalten, wie die Seite veröffentlicht aussehen wird.
* Ermöglicht die Verwendung von Links zur Navigation.
* Does **not** den Seiteninhalt aktualisieren.

Bei der Bearbeitung einer Seite können Sie den Vorschaumodus über das Symbol rechts oben im Seiteneditor aufrufen:

![Schaltfläche „Vorschau“](/help/sites-cloud/authoring/assets/preview.png)

### Als veröffentlicht anzeigen {#view-as-published}

Die **Als veröffentlicht anzeigen** -Option verfügbar über [Seiteninformationen](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) Menü. Dadurch wird die Seite in einer neuen Registerkarte geöffnet, der Inhalt aktualisiert und die Seite wird genau so angezeigt, wie sie in der Veröffentlichungsumgebung angezeigt wird.

## Sperren einer Seite   {#locking-a-page}

AEM bietet Ihnen die Möglichkeit, eine Seite zu sperren, sodass niemand außer Ihnen den Inhalt bearbeiten kann. Dies ist hilfreich, wenn Sie eine Vielzahl von Bearbeitungen an einer bestimmten Seite vornehmen oder wenn Sie eine Seite für eine kurze Zeit einfrieren möchten.

Eine Seite kann gesperrt werden von:

* **Sites** console

   1. Wählen Sie die Seite mit [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
   1. Wählen Sie das Sperrsymbol aus.

      ![Schaltfläche „Sperren“](/help/sites-cloud/authoring/assets/lock.png)

* **Seiteneditor**

   1. Wählen Sie die **Seiteninformationen** -Symbol, um das Menü zu öffnen.
   1. Wählen Sie die **Seite sperren** -Option.

Nach der Sperrung werden die Informationen der Konsolenansicht aktualisiert und beim Bearbeiten wird in der Symbolleiste ein Vorhängeschlosssymbol angezeigt.

![Beispiel für eine gesperrte Seite](/help/sites-cloud/authoring/assets/editing-locked-page.png)

>[!CAUTION]
>
>Wird stellvertretend für einen Benutzer agiert, ist es möglich, eine Seite zu sperren. Eine auf diese Weise gesperrte Seite kann jedoch nur (von Kunden) mit dem Benutzer entsperrt werden, für den stellvertretend agiert wurde.
>
>Seiten können nicht entsperrt werden, indem man sich als der Benutzer ausgibt, der die Seite gesperrt hat.
>
>Wenn der Benutzer, der die Seite gesperrt hat, nicht zum Entsperren der Seite verfügbar ist, wenden Sie sich an den Support, um sich über Optionen zum Entfernen der Sperrung zu informieren.

## Entsperren einer Seite {#unlocking-a-page}

Das Entsperren einer Seite verläuft ähnlich wie das [Sperren der Seite](#locking-a-page) – nach dem Sperren der Seite werden die Sperroptionen durch Aktionen zum Entsperren ersetzt.

Im Menü „Seiteninformationen“ steht dann die Option **Entsperren** zur Verfügung und das Vorhängeschlosssymbol in der Sites-Konsole wird durch ein **Entsperren-Symbol** ersetzt.

![Schaltfläche „Entsperren“](/help/sites-cloud/authoring/assets/unlock.png)

>[!CAUTION]
>
>Wird stellvertretend für einen Benutzer agiert, ist es möglich, eine Seite zu sperren. Eine auf diese Weise gesperrte Seite kann jedoch nur dann (von Kunden) entsperrt werden, wenn der Benutzer verwendet wird, für den stellvertretend agiert wurde.
>
>Seiten können nicht entsperrt werden, indem man sich als der Benutzer ausgibt, der die Seite gesperrt hat.
>
>Wenn der Benutzer, der die Seite gesperrt hat, nicht zum Entsperren der Seite verfügbar ist, wenden Sie sich an den Support, um sich über Optionen zum Entfernen der Sperrung zu informieren.

<!--
>[!CAUTION]
>
>Locking a page can be performed when impersonating a user. However a page locked in this way can only then be unlocked by the user who was impersonated, or by a user with admin rights (a member of AEM Administrator IMS profile).
>
>Pages can not be unlocked by impersonating the user who locked the page.
-->

<!--
>Locking a page can be performed when [impersonating a user](/help/sites-administering/security.md#impersonating-another-user). However a page locked in this way can only then be unlocked by the user who was impersonated or by the admin user.
-->

## Rückgängigmachen und Wiederholen von Seitenbearbeitungen {#undoing-and-redoing-page-edits}

Mit den folgenden Symbolen können Sie eine Aktion rückgängig machen oder wiederholen. Diese werden gegebenenfalls in der Symbolleiste angezeigt:

![Schaltflächen „Rückgängig“ und „Wiederholen“](/help/sites-cloud/authoring/assets/redo.png)

>[!TIP]
>
>* Mit dem [Tastaturbefehl](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `Ctrl-Z` (Strg+Z) können Sie Bearbeitungen ebenfalls rückgängig machen.
>* Analog dazu können Sie zum Wiederholen von Bearbeitungen den Tastaturbefehl `Ctrl-Y` (Strg+Y) verwenden.


>[!NOTE]
>
>Siehe [Rückgängigmachen und Wiederholen von Seitenbearbeitungen - Die Theorie](#undoing-and-redoing-page-edits-the-theory); dort erfahren Sie, was beim Rückgängigmachen und Wiederholen von Seitenbearbeitungen möglich ist.

## Rückgängigmachen und Wiederholen von Seitenbearbeitungen - Die Theorie {#undoing-and-redoing-page-edits-the-theory}

AEM speichert einen Verlauf der Aktionen, die Sie ausführen, sowie die Reihenfolge der Ausführung. Sie können also mehrere Aktionen in der umgekehrten Reihenfolge ihrer Ausführung rückgängig machen und bei Bedarf die Aktionen wiederholen, wenn Sie eine oder mehrere davon erneut anwenden möchten.

Wenn ein Element auf der Inhaltsseite ausgewählt wird, gelten die Befehle „Rückgängig“ und „Wiederholen“ für das ausgewählte Element, also z. B. für eine Textkomponente.

Das Verhalten der Befehle „Rückgängig“ und „Wiederholen“ ähnelt dem in anderer Software. Verwenden Sie die Befehle zum Wiederherstellen des aktuellen Status Ihrer Web-Seite, wenn Sie Entscheidungen über Inhalte treffen. Wenn Sie beispielsweise einen Textabsatz an eine Stelle auf der Seite verschoben haben, können Sie ihn mithilfe des Befehls zum Rückgängigmachen wieder zurück an die ursprüngliche Stelle verschieben. Wenn Sie dann entscheiden, dass die vorherige Position besser war, verwenden Sie den Befehl &quot;Wiederholen&quot;, um &quot;Rückgängig rückgängig zu machen&quot;.

Sie können beispielsweise:

* Aktionen wiederholen, solange Sie seit dem Rückgängigmachen der Aktion keine Seitenbearbeitung vorgenommen haben.
* Rückgängigmachen von maximal 20 Bearbeitungsaktionen (Standardeinstellung).
* Auch verwenden [Tastaturbefehle](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) zum Rückgängigmachen und Wiederholen.

Sie können die folgenden Arten von Seitenänderungen rückgängig machen und wiederholen:

* Hinzufügen, Bearbeiten, Entfernen und Verschieben von Absätzen
* Bearbeitung im Kontext von Absatzinhalten
* Kopieren, Ausschneiden und Einfügen von Elementen auf einer Seite

>[!NOTE]
>
>* Spezielle Berechtigungen sind erforderlich, um Änderungen rückgängig zu machen bzw. wiederherzustellen, die an Dateien und Bildern vorgenommen wurden.
>* Änderungen an Dateien und Bildern können für einen Verlauf von mindestens zehn Stunden rückgängig gemacht werden. Bei länger zurückliegenden Änderungen ist dies unter Umständen nicht mehr möglich. Ihr Administrator kann die Standardzeit von zehn Stunden ändern.
>* Ihr Systemadministrator kann verschiedene Aspekte der Funktionen „Rückgängig“ und „Wiederholen“ den Anforderungen Ihrer Instanz entsprechend konfigurieren.
   <!--* Your system administrator can [configure various aspects of the Undo/Redo features](/help/sites-administering/config-undo.md) according to the requirements for your instance.-->

