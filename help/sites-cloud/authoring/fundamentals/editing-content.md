---
title: Bearbeiten des Seiteninhalts
description: Bearbeiten und ggf. Aktualisieren von Inhalten auf von Ihnen erstellten Seiten
exl-id: 8af0f621-14e8-4605-a51a-a3be21f19092
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '2974'
ht-degree: 100%

---

# Bearbeiten des Seiteninhalts{#editing-page-content}

Sobald Ihre Seite erstellt ist (neu oder im Rahmen eines Launch oder einer Live Copy), können Sie den Inhalt bearbeiten und die erforderlichen Aktualisierungen vornehmen.

Der Inhalt wird mit mithilfe von (zum Inhaltstyp passenden) [Komponenten](/help/sites-cloud/authoring/features/components-console.md) hinzugefügt, die auf die Seite gezogen werden können. Dort können sie dann bearbeitet, verschoben oder gelöscht werden.

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

Die Symbolleiste bietet Zugriff auf eine Vielzahl von Optionen. Je nachdem, in welchem Kontext Sie gerade arbeiten und welche Konfiguration Sie aktuell verwenden, stehen einige Optionen u. U. nicht zur Verfügung.

* **Seitliches Bedienfeld ein/aus**

   Damit wird das seitliche Bedienfeld geöffnet bzw. geschlossen, das den [Asset-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser), den [Komponenten-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) und die [Inhaltsstruktur](/help/sites-cloud/authoring/fundamentals/environment-tools.md#content-tree) enthält.

   ![Seitliches Bedienfeld ein/aus](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

* **Seiteninformationen**

   Hierüber wird das Menü [Seiteninformationen](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) aufgerufen, das Details zur Seite sowie Aktionen enthält, die auf der Seite ausgeführt werden können (z. B. das Anzeigen und Bearbeiten der Seiteninformationen oder die Veröffentlichung bzw. das Rückgängigmachen der Veröffentlichung der Seite).

   ![Schaltfläche „Seiteninformationen“](/help/sites-cloud/authoring/assets/page-information-icon.png)

* **Emulator**

   Blendet die [Emulator-Symbolleiste](/help/sites-cloud/authoring/features/responsive-layout.md#selecting-a-device-to-emulate) ein bzw. aus, über die das Look-and-Feel der Seite auf einem anderen Gerät emuliert werden kann. Im Layout-Modus wird sie automatisch eingeblendet.

   ![Schaltfläche „Emulator“](/help/sites-cloud/authoring/assets/emulator.png)

* **ContextHub**

   Öffnet den [ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md). Dieser ist nur im Vorschaumodus verfügbar.

   ![Schaltfläche „ContextHub“](/help/sites-cloud/authoring/assets/context-hub.png)

* **Seitentitel**

   Dient nur zu Informationszwecken.

   ![Seitentitel](/help/sites-cloud/authoring/assets/page-title.png)

* **Modusauswahl**

   Zeigt den aktuellen [Modus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) an und ermöglicht die Auswahl eines anderen Modus, z. B. Bearbeiten, Layout, Timewarp oder Targeting.

   ![Schaltfläche „Modusauswahl“](/help/sites-cloud/authoring/assets/mode-selector.png)

* **Vorschau**

   Aktiviert den [Vorschaumodus](#preview-mode). Mit diesem wird die Seite so angezeigt, wie sie bei der Veröffentlichung dargestellt wird.

   ![Schaltfläche „Vorschau“](/help/sites-cloud/authoring/assets/preview.png)

* **Anmerken**

   Hierüber können Sie die Seite mit [Anmerkungen](/help/sites-cloud/authoring/fundamentals/annotations.md) versehen (z. B. zu Prüfungszwecken). Nach der ersten Anmerkung wird anstelle des Symbols eine Zahl für die Anzahl der Anmerkungen auf der Seite angezeigt.

   ![Schaltfläche „Anmerkungen“](/help/sites-cloud/authoring/assets/annotations.png)

### Statusbenachrichtigung {#status-notification}

Wird eine Seite bearbeitet, die einem oder mehreren [Workflows](/help/sites-cloud/authoring/workflows/overview.md) unterliegt, wird oben im Bildschirm eine Benachrichtigungsleiste mit einem entsprechenden Hinweis angezeigt.

![Workflow-Benachrichtigung](/help/sites-cloud/authoring/assets/editing-workflow-notification.png)

>[!NOTE]
>
>Die Statusleiste wird nur für Benutzerkonten angezeigt, die über die entsprechenden Berechtigungen verfügen.

In der Benachrichtigung ist der Workflow aufgeführt, dem die Seite zugeordnet ist. Wenn der Benutzer am aktuellen Workflow-Schritt beteiligt ist, sind zusätzlich auch Optionen verfügbar, die sich [auf den Workflow-Status auswirken](/help/sites-cloud/authoring/workflows/participating.md) und die weitere Informationen zum Workflow liefern, darunter:

* **Abschließen**: Öffnet das Dialogfeld **Arbeitselement abschließen**.
* **Delegieren**: Öffnet das Dialogfeld **Arbeitselement abschließen**.
* **Details anzeigen**: Öffnet das Fenster **Details** des entsprechenden Workflows.

Das Fertigstellen und Delegieren von Workflow-Schritten über die Benachrichtigungsleiste erfolgt auf die gleiche Art und Weise wie beim [Teilnehmen an Workflows](/help/sites-cloud/authoring/workflows/participating.md) über den Benachrichtigungs-Posteingang.

Wenn die Seite mehreren Workflows unterliegt, werden in der Benachrichtigung rechts außen die Anzahl der Workflows sowie Pfeilschaltflächen angezeigt, über die Sie durch die einzelnen Workflows scrollen können.

![Mehrere Workflow-Benachrichtigungen](/help/sites-cloud/authoring/assets/editing-workflow-notification-multiple.png)

## Komponenten-Platzhalter {#component-placeholder}

Der Komponenten-Platzhalter zeigt an, wo eine Komponente platziert wird, wenn Sie sie per Drag-and-Drop ablegen – oberhalb der Komponente, über der sich der Mauszeiger gerade befindet:

* Wenn Sie eine neue Komponente zur Seite hinzufügen (die Sie aus dem Komponenten-Browser ziehen):

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
>Auf Mobilgeräten nimmt der Komponenten-Browser den gesamten Bildschirm ein. Sobald Sie eine Komponente per Drag-and-Drop auswählen, wird der Browser geschlossen, sodass Sie die Komponente auf der Seite ablegen können.

### Einfügen einer Komponente aus dem Absatzsystem {#inserting-a-component-from-the-paragraph-system}

Sie können eine neue Komponente über das Feld **Komponenten hierher ziehen** des Absatzsystems hinzufügen.

1. Öffnen Sie die Seite im Modus [**Bearbeiten**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes).
1. Neue Komponenten können auf zwei Arten aus dem Absatzsystem ausgewählt und hinzugefügt werden:

   * Wählen Sie die Option **Komponente einfügen** (+) in der Symbolleiste einer vorhandenen Komponente oder aus dem Feld **Komponenten hierher ziehen**.

      ![Einfügen einer Komponente](/help/sites-cloud/authoring/assets/editing-insert-component.png)

   * Wenn Sie ein Desktop-Gerät verwenden, können Sie die Aktion per Doppelklick auf das Feld **Komponenten hierher ziehen** durchführen.

   * Das Dialogfeld **Neue Komponente einfügen** wird geöffnet. Dort können Sie die erforderliche Komponente auswählen:

      ![Dialogfeld „Neue Komponente einfügen“](/help/sites-cloud/authoring/assets/editing-insert-component-selection.png)

1. Die ausgewählte Komponente wird am Ende der Seite hinzugefügt. [Bearbeiten](#edit-content) Sie die Komponente.

### Einfügen einer Komponente mit dem Assets-Browser  {#inserting-a-component-using-the-assets-browser}

Sie können eine neue Komponente zur Seite hinzufügen, indem Sie ein Asset aus dem [Asset-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser) ziehen. Dadurch wird automatisch eine neue Komponente des entsprechenden Typs erstellt, die das Asset enthält.

Dieses Verhalten kann für Ihre Installation konfiguriert werden. Weitere Informationen finden Sie unter „Konfigurieren eines Absatzsystems zum Erstellen einer Komponenteninstanz infolge des Ziehens eines Assets“. <!--This behavior can be configured for your installation. See [Configuring a Paragraph System so that Dragging an Asset Creates a Component Instance](/help/sites-developing/developing-components.md#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance) for further details.-->

So erstellen Sie eine Komponente, indem Sie einen der obigen Asset-Typen ziehen:

1. Öffnen Sie die Seite im Modus [**Bearbeiten**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes).
1. Öffnen Sie den [Asset-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser).
1. Ziehen Sie das benötigte Asset an die passende Position. Der [Komponenten-Platzhalter](#component-placeholder) zeigt an, wo die Komponente platziert wird.

   Am entsprechenden Ort wird eine zum Asset-Typ passende Komponente erstellt, die das ausgewählte Asset enthält.

1. [Bearbeiten](#edit-content) Sie die Komponente.

>[!NOTE]
>
>Auf Mobilgeräten nimmt der Asset-Browser den gesamten Bildschirm ein. Sobald Sie ein Asset per Drag-and-Drop auswählen, wird der Browser geschlossen, sodass Sie das Asset auf der Seite ablegen können.

Wenn Sie die Assets durchgehen und feststellen, dass Sie an einem der Assets eine Änderung vornehmen möchten, können Sie den [Asset-Editor](/help/assets/manage-digital-assets.md) direkt über den Browser starten. Klicken Sie dazu einfach auf das Bearbeitungssymbol neben dem Asset-Namen.

![Schaltfläche „Asset bearbeiten“](/help/sites-cloud/authoring/assets/asset-edit-button.png)

## Komponentensymbolleiste {#component-toolbar}

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

   Kopiert die Komponente in die Zwischenablage. Nach dem Einfügen bleibt die ursprüngliche Komponente weiter vorhanden.

   ![Schaltfläche „Kopieren“](/help/sites-cloud/authoring/assets/editing-component-toolbar-copy.png)

* **Ausschneiden**

   Kopiert die Komponente in die Zwischenablage. Nach dem Einfügen wird die ursprüngliche Komponente entfernt.

   ![Schaltfläche „Ausschneiden“](/help/sites-cloud/authoring/assets/editing-component-toolbar-cut.png)

* **Löschen**

   Löscht die Komponente von der Seite. Sie werden dazu aufgefordert, die Aktion zu bestätigen.

   ![Schaltfläche „Löschen“](/help/sites-cloud/authoring/assets/editing-component-toolbar-delete.png)

* **Komponente einfügen**

   Öffnet das Dialogfeld, in dem Sie eine [neue Komponente hinzufügen](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component-from-the-paragraph-system) können.

   ![Schaltfläche „Einfügen“](/help/sites-cloud/authoring/assets/editing-component-toolbar-insert.png)

* **Einfügen**

   Fügt die Komponente aus der Zwischenablage in die Seite ein. Ob das Original erhalten bleibt, hängt davon ab, ob sie es kopiert oder ausgeschnitten haben.

   * Sie können die Komponente sowohl in die aktuelle Seite als auch in eine andere Seite einfügen.
   * Das Element wird über dem Element eingefügt, auf dem Sie die Einfügen-Aktion durchführen.
   * Die Option zum Einfügen wird nur angezeigt, wenn sich Inhalt in der Zwischenablage befindet.

   ![Schaltfläche „Einfügen“](/help/sites-cloud/authoring/assets/editing-component-toolbar-paste.png)

   >[!NOTE]
   >
   >Wenn Sie eine Seite auf einer anderen Seite einfügen, die vor dem Ausschneiden/Kopieren geöffnet war, müssen Sie die Seite aktualisieren, damit der eingefügte Inhalt angezeigt wird.

* **Gruppe**

   Mit dieser Aktion können Sie mehrere Komponenten gleichzeitig auswählen. Auf einem Desktop-Gerät können Sie diese Aktion auch über die Tastenkombination **Strg+Mausklick** bzw. **Befehlstaste+Mausklick** durchführen.

   ![Schaltfläche „Gruppe“](/help/sites-cloud/authoring/assets/editing-component-toolbar-group.png)

* **Übergeordnet**

   Hierüber können Sie die Komponente auswählen, die der ausgewählten Komponente übergeordnet ist.

   ![Schaltfläche „Übergeordnet“](/help/sites-cloud/authoring/assets/editing-component-toolbar-parent.png)

* **Layout**

   Hierüber können Sie das [Layout](/help/sites-cloud/authoring/fundamentals/editing-content.md#edit-component-layout) der ausgewählten Komponente ändern. Diese Aktion wird nur auf die ausgewählte Komponente angewendet, der [Layout-Modus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes), mit dem das Layout der gesamten Seite bearbeitet wird, wird dabei nicht aktiviert.

   ![Schaltfläche „Layout“](/help/sites-cloud/authoring/assets/editing-component-toolbar-layout.png)

* **In Experience Fragment-Variante umwandeln**

   Hierüber können Sie ein neues [Experience Fragment](/help/sites-cloud/authoring/fundamentals/experience-fragments.md) aus der ausgewählten Komponente erstellen oder einem bestehenden Experience Fragment hinzufügen.

   ![Schaltfläche „In Experience Fragment-Variante umwandeln“](/help/sites-cloud/authoring/assets/editing-component-toolbar-xf.png)

## Inhalt bearbeiten {#edit-content}

Für das Hinzufügen und/oder Bearbeiten von Inhalten in Komponenten sind zwei Verfahren verfügbar:

* Öffnen Sie das Dialogfeld [Komponente](#component-edit-dialog) für die Bearbeitung.
* [Ziehen Sie ein Asset](#drag-and-drop-assets-into-component) aus dem Asset-Browser, um Inhalt direkt hinzuzufügen.

### Dialogfeld „Komponente bearbeiten“   {#component-edit-dialog}

Sie können eine Komponente öffnen, um den Inhalt zu bearbeiten, indem Sie das Symbol [„Bearbeiten“ (Stiftsymbol) der Komponenten-Symbolleiste](#component-toolbar) verwenden.

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

* Bildkomponente – Vollbild

   Wenn Sie den [Vollbildmodus](#edit-content-full-screen-mode) für die Bildkomponente aufrufen, haben Sie mehr Platz zum Bearbeiten des Bildes und erhalten zusätzliche Bearbeitungsoptionen wie **Map starten** und **Zoom zurücksetzen**. Außerdem können im Vollbildmodus Zuschnittvoreinstellungen ausgewählt werden.

   ![Vollbildmodus der Bildkomponente](/help/sites-cloud/authoring/assets/editing-image-component-full-screen.png)

* Bei Komponenten (aus mehreren grundlegenden Komponenten erstellt) müssen Sie zunächst die gewünschte Optionsgruppe wählen:

### Drag-and-Drop von Assets in Komponenten {#drag-and-drop-assets-into-component}

Bei bestimmten Komponententypen (z. B. Bildern) können Sie Assets aus dem Asset-Browser direkt in die Komponente ziehen und ablegen, um den Inhalt zu aktualisieren.

## Inhalt bearbeiten im Vollbildmodus {#edit-content-full-screen-mode}

Für alle Komponenten kann der Vollbildmodus über das folgende Symbol gestartet und beendet werden:

![Schaltfläche „Vollbild“](/help/sites-cloud/authoring/assets/editing-full-screen.png)

Z. B. die Komponente **Text**:

![Textkomponente im Vollbildmodus](/help/sites-cloud/authoring/assets/editing-text-full-screen.png)

>[!NOTE]
>
>Bei einigen Komponenten sind im Vollbildmodus mehr Optionen verfügbar als im integrierten Editor.

## Verschieben einer Komponente {#moving-a-component}

So verschieben Sie eine Absatzkomponente:

1. Wählen Sie den zu verschiebenden Absatz durch Tippen/Klicken und Halten aus:
1. Ziehen sie den Absatz an die neue Position. AEM zeigt an, wo der Absatz abgelegt werden kann. Legen Sie den Absatz an der gewünschten Stelle ab.

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

1. Durch das Auswählen der Layout-Aktion stehen folgende Funktionen zur Verfügung:

   * Auf der Komponente werden die Ziehpunkte für die Größenanpassung angezeigt.
   * Oben im Bildschirm wird die Emulator-Symbolleiste angezeigt.
   * In der Komponenten-Symbolleiste stehen statt der Standard-Bearbeitungsaktionen nun Layout-Aktionen zur Verfügung.

   ![Komponente im Layout-Modus](/help/sites-cloud/authoring/assets/editing-layout-mode.png)

   Jetzt können Sie Änderungen am Layout der Komponente auf die gleiche Art und Weise vornehmen wie im [Layout-Modus](/help/sites-cloud/authoring/features/responsive-layout.md#defining-layouts-layout-mode).

1. Wenn Sie alle Änderungen wie gewünscht vorgenommen haben, klicken Sie im Aktionsmenü der Komponente auf die Schaltfläche **Schließen**, um die Layout-Anpassung zu beenden. In der Komponenten-Symbolleiste stehen nun wieder die Standard-Bearbeitungsfunktionen zur Verfügung.

   ![Komponenten-Symbolleiste einer Seitenkomponente](/help/sites-cloud/authoring/assets/editing-layout-exit.png)

>[!TIP]
>
>Die Layout-Aktion ist immer auf die jeweils ausgewählte Komponente beschränkt. Wenn Sie etwa bei einer Komponente das Layout bearbeiten und dann auf eine andere Komponente klicken, werden auf der Symbolleiste für die Bearbeitung die Layout-Aktionen durch die Standardaktionen ersetzt und die Ziehpunkte für die Größenanpassung sowie die Emulator-Symbolleiste werden nicht mehr angezeigt.
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

Der [Seitenmodus „Live Copy-Status“](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) bietet einen schnellen Überblick über den Live Copy-Status und darüber, welche Komponenten vererbt oder nicht vererbt wurden.

* Grüner Rahmen: Vererbt
* Pinkfarbener Rahmen: Vererbung wurde abgebrochen

Beispiel:

![Beispiel für einen Live Copy-Status](/help/sites-cloud/authoring/assets/editing-live-copy-status.png)

## Hinzufügen von Anmerkungen {#adding-annotations}

[Anmerkungen](/help/sites-cloud/authoring/fundamentals/annotations.md) bieten Reviewern und anderen Autoren die Möglichkeit, Feedback zu Ihrem Inhalt zu erteilen. Dies wird häufig zu Korrektur- oder Überprüfungszwecken verwendet.

## Anzeigen einer Seitenvorschau   {#previewing-pages}

Für die Anzeige einer Seitenvorschau stehen zwei Optionen zur Verfügung:

* [Vorschaumodus](#preview-mode) – für einen schnellen Blick auf die Seite im Kontext
* [Als veröffentlicht anzeigen](#view-as-published) – eine Vorschau, bei der die Seite in einer neuen Registerkarte geöffnet wird

>[!TIP]
>
>* Verweise im Inhalt sind sichtbar, können im Bearbeitungsmodus jedoch nicht aufgerufen werden.
>* Verwenden Sie eine der Vorschauoptionen, wenn Sie mithilfe von Links navigieren möchten.
>* Verwenden Sie den [Tastaturbefehl](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `Ctrl-Shift-M` (Strg+Umschalt+M), um zwischen der Vorschau und dem zuletzt ausgewählten Modus zu wechseln.


>[!NOTE]
>
>Das WCM-Modus-Cookie wird für beide Vorschauoptionen gesetzt.

### Vorschaumodus {#preview-mode}

Beim Bearbeiten von Inhalt können Sie mithilfe des [Vorschaumodus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) eine Vorschau der Seite anzeigen. Dieser Modus:

* Blendet diverse Bearbeitungsmechanismen aus, damit Sie einen schnellen Überblick darüber erhalten, wie die Seite veröffentlicht aussehen wird.
* Ermöglicht es Ihnen, mit Links zu navigieren.
* Aktualisiert den Seiteninhalt **nicht**.

Bei der Bearbeitung einer Seite können Sie den Vorschaumodus über das Symbol rechts oben im Seiteneditor aufrufen:

![Schaltfläche „Vorschau“](/help/sites-cloud/authoring/assets/preview.png)

### Als veröffentlicht anzeigen {#view-as-published}

Die Option **Als veröffentlicht anzeigen** ist im Menü [Seiteninformationen](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) verfügbar. Mit dieser Option wird die Seite in einer neuen Registerkarte geöffnet, ihr Inhalt aktualisiert und die Seite so angezeigt, wie sie später in der Veröffentlichungsumgebung aussieht.

## Sperren einer Seite {#locking-a-page}

AEM bietet Ihnen die Möglichkeit, eine Seite zu sperren, sodass niemand außer Ihnen den Inhalt bearbeiten kann. Dies ist hilfreich, wenn Sie eine Vielzahl von Bearbeitungen an einer bestimmten Seite vornehmen oder wenn Sie eine Seite für eine kurze Zeit einfrieren möchten.

Eine Seite kann wie folgt gesperrt werden:

* **Sites-Konsole**

   1. Wählen Sie die Seite mit dem [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) aus.
   1. Wählen Sie das Sperrsymbol aus.

      ![Schaltfläche „Sperren“](/help/sites-cloud/authoring/assets/lock.png)

* **Seiteneditor**

   1. Wählen Sie das Symbol **Seiteninformationen** aus, um das Menü zu öffnen:
   1. Wählen Sie die Option **Seite sperren** aus.

Nach der Sperrung werden die Informationen der Konsolenansicht aktualisiert und beim Bearbeiten wird in der Symbolleiste ein Vorhängeschlosssymbol angezeigt.

![Beispiel für eine gesperrte Seite](/help/sites-cloud/authoring/assets/editing-locked-page.png)

>[!CAUTION]
>
>Wird stellvertretend für einen Benutzer agiert, ist es möglich, eine Seite zu sperren. Eine auf diese Weise gesperrte Seite kann nur von dem Benutzer, für den stellvertretend agiert wurde, oder von einem Benutzer mit Administratorrechten entsperrt werden.
>
>Seiten lassen sich nicht entsperren, indem stellvertretend für den Benutzer agiert wird, der die Seite gesperrt hat.
<!--
>Locking a page can be performed when [impersonating a user](/help/sites-administering/security.md#impersonating-another-user). However a page locked in this way can only then be unlocked by the user who was impersonated or by the admin user.
-->

## Entsperren einer Seite {#unlocking-a-page}

Das Entsperren einer Seite verläuft ähnlich wie das [Sperren der Seite](#locking-a-page) – nach dem Sperren der Seite werden die Sperroptionen durch Aktionen zum Entsperren ersetzt.

Im Menü „Seiteninformationen“ steht dann die Option **Entsperren** zur Verfügung und das Vorhängeschlosssymbol in der Sites-Konsole wird durch ein **Entsperren-Symbol** ersetzt.

![Schaltfläche „Entsperren“](/help/sites-cloud/authoring/assets/unlock.png)

>[!CAUTION]
>
>Wird stellvertretend für einen Benutzer agiert, ist es möglich, eine Seite zu sperren. Eine auf diese Weise gesperrte Seite kann nur von dem Benutzer, für den stellvertretend agiert wurde, oder von einem Benutzer mit Administratorrechten entsperrt werden.
>
>Seiten lassen sich nicht entsperren, indem stellvertretend für den Benutzer agiert wird, der die Seite gesperrt hat.
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

Das Verhalten der Befehle „Rückgängig“ und „Wiederholen“ ähnelt dem in anderer Software. Verwenden Sie die Befehle zum Wiederherstellen des aktuellen Status Ihrer Web-Seite, wenn Sie Entscheidungen über Inhalte treffen. Wenn Sie beispielsweise einen Textabsatz an eine Stelle auf der Seite verschoben haben, können Sie ihn mithilfe des Befehls zum Rückgängigmachen wieder zurück an die ursprüngliche Stelle verschieben. Wenn Sie den Absatz dann doch wieder an die zuletzt verwendete Stelle verschieben möchten, können Sie mit dem Befehl zum Wiederholen quasi das „Rückgängigmachen rückgängig machen“.

Sie können beispielsweise:

* Aktionen wiederholen, solange Sie seit dem letzten Rückgängigmachen einer Aktion keine Seitenbearbeitungen durchgeführt haben
* maximal 20 Bearbeitungsaktionen rückgängig machen (Standardeinstellung)
* für das Rückgängigmachen und Wiederholen auch [Tastaturbefehle](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) verwenden

Die können die folgenden Arten von Seitenbearbeitungen rückgängig machen bzw. wiederholen:

* Hinzufügen, Bearbeiten, Entfernen und Verschieben von Absätzen
* Bearbeitung von Absatzinhalten im Kontext
* Kopieren, Ausschneiden und Einfügen von Elementen innerhalb einer Seite

>[!NOTE]
>
>* Spezielle Berechtigungen sind erforderlich, um Änderungen rückgängig zu machen bzw. wiederherzustellen, die an Dateien und Bildern vorgenommen wurden.
>* Änderungen an Dateien und Bildern können für einen Verlauf von mindestens zehn Stunden rückgängig gemacht werden. Bei länger zurückliegenden Änderungen ist dies unter Umständen nicht mehr möglich. Ihr Administrator kann die Standarddauer von zehn Stunden ändern.
>* Ihr Systemadministrator kann verschiedene Aspekte der Funktionen „Rückgängig“ und „Wiederholen“ den Anforderungen Ihrer Instanz entsprechend konfigurieren.

<!--* Your system administrator can [configure various aspects of the Undo/Redo features](/help/sites-administering/config-undo.md) according to the requirements for your instance.-->
