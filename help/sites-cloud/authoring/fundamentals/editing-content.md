---
title: Bearbeiten des Seiteninhalts
description: Nachdem die Seite erstellt wurde, können Sie den Inhalt bearbeiten, um die erforderlichen Aktualisierungen vorzunehmen
exl-id: 8af0f621-14e8-4605-a51a-a3be21f19092
source-git-commit: e2505c0fec1da8395930f131bfc55e1e2ce05881
workflow-type: tm+mt
source-wordcount: '2975'
ht-degree: 93%

---


# Bearbeiten des Seiteninhalts{#editing-page-content}

Sobald Ihre Seite erstellt ist (neu oder im Rahmen eines Launch oder einer Live Copy), können Sie den Inhalt bearbeiten und die erforderlichen Aktualisierungen vornehmen.

Inhalte werden mithilfe von [Komponenten](/help/sites-cloud/authoring/features/components-console.md) hinzugefügt (entsprechend dem Inhaltstyp), die per Drag-and-Drop auf die Seite gezogen werden können. Dort können sie dann bearbeitet, verschoben oder gelöscht werden.

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

{{edge-delivery-authoring}}

## Seitensymbolleiste {#page-toolbar}

Die Seite-Symbolleiste bietet Zugriff auf die entsprechenden Funktionen, die von der Seitenkonfiguration abhängig sind.

![Seitensymbolleiste](/help/sites-cloud/authoring/assets/editing-page-toolbar.png)

Die Symbolleiste bietet Zugriff auf eine Vielzahl von Optionen. Je nach aktuellem Kontext und Ihrer Konfiguration sind einige Optionen möglicherweise nicht verfügbar.

* **Seitliches Bedienfeld ein/aus**

  Dadurch wird das seitliche Bedienfeld geöffnet/geschlossen, das den [Asset-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser), den [Komponenten-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) und die [Inhaltsstruktur](/help/sites-cloud/authoring/fundamentals/environment-tools.md#content-tree) enthält.

  ![Seitliches Bedienfeld ein/aus](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

* **Seiteninformationen**

  Ermöglicht den Zugriff auf das Menü [Seiteninformationen](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) mit Seitendetails und Aktionen, die auf der Seite durchgeführt werden können, einschließlich Anzeigen und Bearbeiten von Seiteninformationen, Anzeigen von Seiteneigenschaften und Veröffentlichen/Entfernen der Seite.

  ![Schaltfläche „Seiteninformationen“](/help/sites-cloud/authoring/assets/page-information-icon.png)

* **Emulator**

  Blendet die [Emulator-Symbolleiste](/help/sites-cloud/authoring/features/responsive-layout.md#selecting-a-device-to-emulate) ein bzw. aus, über die das Look-and-Feel der Seite auf einem anderen Gerät emuliert werden kann. Dies wird im Layout-Modus automatisch umgeschaltet.

  ![Schaltfläche „Emulator“](/help/sites-cloud/authoring/assets/emulator.png)

* **ContextHub**

  Öffnet den [ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md). Dieser ist nur im Vorschaumodus verfügbar.

  ![Schaltfläche „ContextHub“](/help/sites-cloud/authoring/assets/context-hub.png)

* **Seitentitel**

  Dient nur zu Informationszwecken.

  ![Seitentitel](/help/sites-cloud/authoring/assets/page-title.png)

* **Modusauswahl**

  Zeigt den aktuellen [mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) und ermöglicht die Auswahl eines anderen Modus wie Bearbeiten, Layout, Timewarp oder Targeting.

  ![Schaltfläche „Modusauswahl“](/help/sites-cloud/authoring/assets/mode-selector.png)

* **Vorschau**

  Aktiviert den [Vorschaumodus](#preview-mode). Dadurch wird die Seite so angezeigt, wie sie bei der Veröffentlichung erscheint.

  ![Schaltfläche „Vorschau“](/help/sites-cloud/authoring/assets/preview.png)

* **Anmerken**

  Ermöglicht das Hinzufügen von [Anmerkungen](/help/sites-cloud/authoring/fundamentals/annotations.md) auf der Seite, wenn Sie eine Seite überprüfen. Nach der ersten Anmerkung ändert sich das Symbol in eine Zahl, die die Anzahl der Anmerkungen auf der Seite anzeigt.

  ![Schaltfläche „Anmerkungen“](/help/sites-cloud/authoring/assets/annotations.png)

### Statusbenachrichtigung {#status-notification}

Wird eine Seite bearbeitet, die einem oder mehreren [Workflows](/help/sites-cloud/authoring/workflows/overview.md) unterliegt, wird oben im Bildschirm eine Benachrichtigungsleiste mit einem entsprechenden Hinweis angezeigt.

![Workflow-Benachrichtigung](/help/sites-cloud/authoring/assets/editing-workflow-notification.png)

>[!NOTE]
>
>Die Statusleiste ist nur für Benutzerkonten mit entsprechenden Berechtigungen sichtbar.

In der Benachrichtigung ist der Workflow aufgeführt, dem die Seite zugeordnet ist. Wenn Benutzende am aktuellen Workflow-Schritt beteiligt sind, sind zusätzlich auch Optionen verfügbar, die sich [auf den Workflow-Status auswirken](/help/sites-cloud/authoring/workflows/participating.md) und die weiteren Informationen zum Workflow liefern, darunter:

* **Abschließen**: Öffnet das Dialogfeld **Arbeitselement abschließen**.
* **Delegieren**: Öffnet das Dialogfeld **Arbeitselement abschließen**.
* **Details anzeigen**: Öffnet das Fenster **Details** des entsprechenden Workflows.

Das Fertigstellen und Delegieren von Workflow-Schritten über die Benachrichtigungsleiste erfolgt auf die gleiche Art und Weise wie beim [Teilnehmen an Workflows](/help/sites-cloud/authoring/workflows/participating.md) über den Benachrichtigungs-Posteingang.

Wenn die Seite mehreren Workflows unterliegt, werden in der Benachrichtigung rechts außen die Anzahl der Workflows sowie Pfeilschaltflächen angezeigt, über die Sie durch die einzelnen Workflows scrollen können.

![Mehrere Workflow-Benachrichtigungen](/help/sites-cloud/authoring/assets/editing-workflow-notification-multiple.png)

## Komponenten-Platzhalter {#component-placeholder}

Der Komponenten-Platzhalter zeigt an, wo eine Komponente platziert wird, wenn Sie sie per Drag-and-Drop ablegen – oberhalb der Komponente, über der sich der Mauszeiger gerade befindet:

* Beim Hinzufügen einer neuen Komponente zur Seite (Ziehen aus dem Komponenten-Browser per Drag-and-Drop):

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

   * Wählen Sie die Option **Komponente einfügen** (+) aus der Symbolleiste einer vorhandenen Komponente oder aus dem Feld **Komponenten hierherziehen**.

     ![Einfügen einer Komponente](/help/sites-cloud/authoring/assets/editing-insert-component.png)

   * Wenn Sie sich auf einem Desktop-Gerät befinden, können Sie auf das **Komponenten hierher ziehen** ankreuzen.

   * Die **Neue Komponente einfügen** -Dialogfeld geöffnet, in dem Sie die gewünschte Komponente auswählen können:

     ![Dialogfeld „Neue Komponente einfügen“](/help/sites-cloud/authoring/assets/editing-insert-component-selection.png)

1. Die ausgewählte Komponente wird unten auf der Seite hinzugefügt. [Bearbeiten](#edit-content) Sie bei Bedarf die Komponente.

### Einfügen einer Komponente mit dem Assets-Browser {#inserting-a-component-using-the-assets-browser}

Sie können der Seite auch eine neue Komponente hinzufügen, indem Sie ein Asset aus dem [Asset-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser) ziehen. Dadurch wird automatisch eine Komponente des entsprechenden Typs erstellt (und das Asset enthält).

Dieses Verhalten kann für Ihre Installation konfiguriert werden. Weitere Informationen finden Sie unter „Konfigurieren eines Absatzsystems zum Erstellen einer Komponenteninstanz infolge des Ziehens eines Assets“. <!--This behavior can be configured for your installation. See [Configuring a Paragraph System so that Dragging an Asset Creates a Component Instance](/help/sites-developing/developing-components.md#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance) for further details.-->

So erstellen Sie eine Komponente, indem Sie einen der obigen Asset-Typen ziehen:

1. Öffnen Sie die Seite im Modus [**Bearbeiten**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes).
1. Öffnen Sie den [Asset-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser).
1. Ziehen Sie die benötigte Komponente an die passende Position. Der [Komponenten-Platzhalter](#component-placeholder) zeigt an, wo die Komponente platziert wird.

   Eine für den Asset-Typ geeignete Komponente wird am erforderlichen Speicherort erstellt und enthält das ausgewählte Asset.

1. [Bearbeiten](#edit-content) Sie bei Bedarf die Komponente.

>[!NOTE]
>
>Auf Mobilgeräten nimmt der Asset-Browser den gesamten Bildschirm ein. Sobald Sie mit dem Ziehen eines Assets beginnen, wird der Browser geschlossen, um die Seite erneut anzuzeigen, damit Sie das Asset platzieren können.

Wenn Sie die Assets durchgehen und feststellen, dass Sie an einem der Assets eine Änderung vornehmen möchten, können Sie den [Asset-Editor](/help/assets/manage-digital-assets.md) direkt über den Browser starten. Klicken Sie dazu einfach auf das Bearbeitungssymbol neben dem Asset-Namen.

![Schaltfläche „Asset bearbeiten“](/help/sites-cloud/authoring/assets/asset-edit-button.png)

## Komponenten-Symbolleiste {#component-toolbar}

Wenn Sie eine Komponente auswählen, wird die Symbolleiste geöffnet. Dadurch erhalten Sie Zugriff auf verschiedene Aktionen, die für die Komponente ausgeführt werden können.

Die tatsächlichen für die Benutzenden verfügbaren Aktionen werden abhängig von der jeweiligen Situation angezeigt, sodass hier u. U. nicht alle möglichen Aktionen beschrieben werden.

![Komponentensymbolleiste](/help/sites-cloud/authoring/assets/editing-component-toolbar.png)

* **Bearbeiten**

  [Abhängig vom Komponententyp](/help/sites-cloud/authoring/fundamentals/components.md) können Sie hierüber den [Inhalt der Komponente bearbeiten](#edit-content). Häufig wird eine Symbolleiste bereitgestellt.

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

  Dadurch wird die Komponente von der Seite gelöscht, sofern Sie dies bestätigen.

  ![Schaltfläche „Löschen“](/help/sites-cloud/authoring/assets/editing-component-toolbar-delete.png)

* **Komponente einfügen**

  Dadurch wird das Dialogfeld für das [Hinzufügen einer neuen Komponente](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component-from-the-paragraph-system) geöffnet.

  ![Schaltfläche „Einfügen“](/help/sites-cloud/authoring/assets/editing-component-toolbar-insert.png)

* **Einfügen**

  Fügt die Komponente aus der Zwischenablage in die Seite ein. Ob das Original erhalten bleibt, hängt davon ab, ob Sie „Kopieren“ oder „Ausschneiden“ verwendet haben.

   * Sie können Komponenten auf derselben oder einer anderen Seite einfügen.
   * Das eingefügte Element wird über dem Element eingefügt, auf dem Sie die Einfügeaktion auswählen.
   * Die Aktion „Einfügen“ wird nur angezeigt, wenn sich Inhalt in der Zwischenablage befindet.

  ![Schaltfläche „Einfügen“](/help/sites-cloud/authoring/assets/editing-component-toolbar-paste.png)

  >[!NOTE]
  >
  >Wenn Sie etwas auf einer anderen Seite einfügen, die bereits vor dem Ausschneiden bzw. Kopieren geöffnet war, müssen Sie die Seite aktualisieren, damit der eingefügte Inhalt angezeigt wird.

* **Gruppe**

  Damit können Sie mehrere Komponenten gleichzeitig auswählen. Dasselbe kann auf einem Desktop-Gerät durch **Strg+Klicken** bzw. **Befehl+Klicken** erreicht werden.

  ![Schaltfläche „Gruppe“](/help/sites-cloud/authoring/assets/editing-component-toolbar-group.png)

* **Übergeordnet**

  Damit können Sie die übergeordnete Komponente der ausgewählten Komponente auswählen.

  ![Schaltfläche „Übergeordnet“](/help/sites-cloud/authoring/assets/editing-component-toolbar-parent.png)

* **Layout**

  Auf diese Weise können Sie die [layout](/help/sites-cloud/authoring/fundamentals/editing-content.md#edit-component-layout) der ausgewählten Komponente. Dies gilt nur für die ausgewählte Komponente und aktiviert nicht den [Layout-Modus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) für die gesamte Seite.

  ![Schaltfläche „Layout“](/help/sites-cloud/authoring/assets/editing-component-toolbar-layout.png)

* **In Experience Fragment-Variante umwandeln**

  Auf diese Weise können Sie eine [Experience Fragment](/help/sites-cloud/authoring/fundamentals/experience-fragments.md) aus der ausgewählten Komponente oder fügen Sie sie einem vorhandenen Experience Fragment hinzu.

  ![Schaltfläche „In Experience Fragment-Variante umwandeln“](/help/sites-cloud/authoring/assets/editing-component-toolbar-xf.png)

## Inhalt bearbeiten {#edit-content}

Für das Hinzufügen und/oder Bearbeiten von Inhalten in Komponenten sind zwei Verfahren verfügbar:

* Öffnen Sie das [Komponentendialogfeld für die Bearbeitung](#component-edit-dialog).
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

* Bildkomponente – Vollbild

  [Der Wechsel in den Vollbildmodus](#edit-content-full-screen-mode) für die Bildkomponente bietet mehr Platz zum Bearbeiten des Bildes und zeigt zusätzliche Bearbeitungsoptionen wie **Karte starten** und **Zoom zurücksetzen**. Außerdem können im Vollbildmodus Zuschnittvoreinstellungen ausgewählt werden.

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

1. Wählen Sie durch Tippen und Halten bzw. Klicken und Halten den Absatz aus, der verschoben werden soll.
1. Ziehen Sie den Absatz an die neue Position. AEM zeigt an, wo der Absatz abgelegt werden kann. Legen Sie ihn an der gewünschten Position ab.

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

1. Sobald die Layout-Aktion ausgewählt ist, sehen Sie Folgendes:

   * Die Größenänderungsgriffe für die Komponente werden angezeigt.
   * Oben im Bildschirm wird die Emulator-Symbolleiste angezeigt.
   * In der Komponenten-Symbolleiste werden Layout-Aktionen anstelle der standardmäßigen Bearbeitungsaktionen angezeigt.

   ![Komponente im Layout-Modus](/help/sites-cloud/authoring/assets/editing-layout-mode.png)

   Jetzt können Sie Änderungen am Layout der Komponente auf die gleiche Art und Weise vornehmen wie im [Layout-Modus](/help/sites-cloud/authoring/features/responsive-layout.md#defining-layouts-layout-mode).

1. Wenn Sie alle Änderungen wie gewünscht vorgenommen haben, klicken Sie im Aktionsmenü der Komponente auf die Schaltfläche **Schließen**, um die Layout-Anpassung zu beenden. In der Komponenten-Symbolleiste stehen nun wieder die Standard-Bearbeitungsfunktionen zur Verfügung.

   ![Komponenten-Symbolleiste einer Seitenkomponente](/help/sites-cloud/authoring/assets/editing-layout-exit.png)

>[!TIP]
>
>Die Layout-Aktion ist immer auf die jeweils ausgewählte Komponente beschränkt. Wenn Sie beispielsweise das Layout einer Komponente bearbeiten und dann auf eine andere Komponente klicken, wird die standardmäßige Bearbeitungssymbolleiste (nicht die Layout-Symbolleiste) für die neu ausgewählte Komponente und die Größenänderungsgriffe angezeigt und die Emulator-Symbolleiste wird ausgeblendet.
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

Mit dem [Seitenmodus „Live Copy-Status“](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) erhalten Sie einen schnellen Überblick über den Live Copy-Status und darüber, welche Komponenten übernommen bzw. nicht übernommen wurden:

* Grüner Rahmen: Vererbt
* Rosa Rahmen: Vererbung wurde abgebrochen

Beispiel:

![Beispiel für einen Live Copy-Status](/help/sites-cloud/authoring/assets/editing-live-copy-status.png)

## Hinzufügen von Anmerkungen {#adding-annotations}

[Anmerkungen](/help/sites-cloud/authoring/fundamentals/annotations.md) ermöglichen es Prüferinnen und Prüfern sowie anderen Autorinnen und Autoren, Feedback zu Ihrem Inhalt zu geben. Sie werden häufig zu Überprüfungs- und Validierungszwecken verwendet.

## Anzeigen einer Seitenvorschau {#previewing-pages}

Für die Anzeige einer Seitenvorschau stehen zwei Optionen zur Verfügung:

* [Vorschaumodus](#preview-mode) – für einen schnellen Blick auf die Seite im Kontext
* [Als veröffentlicht anzeigen](#view-as-published) – eine vollständige Vorschau, die die Seite auf einer neuen Registerkarte öffnet

>[!TIP]
>
>* Links im Inhalt sind sichtbar, können jedoch im Bearbeitungsmodus nicht aufgerufen werden.
>* Verwenden Sie eine der Vorschauoptionen, wenn Sie mithilfe von Links navigieren möchten.
>* Verwenden Sie den [Tastaturbefehl](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `Ctrl-Shift-M` (Strg+Umschalt+M), um zwischen der Vorschau und dem zuletzt ausgewählten Modus zu wechseln.

>[!NOTE]
>
>Das WCM-Modus-Cookie wird für beide Vorschauoptionen gesetzt.

### Vorschaumodus {#preview-mode}

Beim Bearbeiten von Inhalt können Sie mithilfe des [Vorschaumodus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) eine Vorschau der Seite anzeigen. Dieser Modus:

* Blendet diverse Bearbeitungsmechanismen aus, damit Sie einen schnellen Überblick darüber erhalten, wie die Seite veröffentlicht aussehen wird.
* Ermöglicht die Verwendung von Links zur Navigation.
* Aktualisiert **nicht** den Seiteninhalt.

Bei der Bearbeitung einer Seite können Sie den Vorschaumodus über das Symbol rechts oben im Seiteneditor aufrufen:

![Schaltfläche „Vorschau“](/help/sites-cloud/authoring/assets/preview.png)

### Als veröffentlicht anzeigen {#view-as-published}

Die Option **Als veröffentlicht anzeigen** ist über das Menü [Seiteninformationen](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) verfügbar. Dadurch wird die Seite in einer neuen Registerkarte geöffnet und der Inhalt aktualisiert, und die Seite wird genau so angezeigt, wie sie in der Publishing-Umgebung angezeigt wird.

## Sperren einer Seite   {#locking-a-page}

AEM bietet Ihnen die Möglichkeit, eine Seite zu sperren, sodass niemand außer Ihnen den Inhalt bearbeiten kann. Diese Sperre ist nützlich, wenn Sie zahlreiche Änderungen an einer bestimmten Seite vornehmen oder wenn Sie eine Seite für kurze Zeit einfrieren müssen.

Eine Seite kann wie folgt gesperrt werden:

* **Sites**-Konsole

   1. Wählen Sie die Seite mit dem [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) aus.
   1. Wählen Sie das Sperrsymbol aus.

      ![Schaltfläche „Sperren“](/help/sites-cloud/authoring/assets/lock.png)

* **Seiteneditor**

   1. Wählen Sie das Symbol **Seiteninformationen** aus, um das Auswahlmenü zu öffnen.
   1. Wählen Sie die Option **Seite sperren** aus.

Nach der Sperrung werden die Informationen der Konsolenansicht aktualisiert und beim Bearbeiten wird in der Symbolleiste ein Vorhängeschlosssymbol angezeigt.

![Beispiel für eine gesperrte Seite](/help/sites-cloud/authoring/assets/editing-locked-page.png)

>[!CAUTION]
>
>Wird stellvertretend für einen Benutzer agiert, ist es möglich, eine Seite zu sperren. Eine auf diese Weise gesperrte Seite kann jedoch nur (von Kunden) mit dem Benutzer entsperrt werden, für den stellvertretend agiert wurde.
>
>Seiten können nicht entsperrt werden, indem man sich als der Benutzer ausgibt, der die Seite gesperrt hat.
>
>Wenn die Benutzerin bzw. der Benutzer, die bzw. der die Seite gesperrt hat, nicht zum Entsperren der Seite verfügbar ist, wenden Sie sich an den Support, um sich über Optionen zum Entfernen der Sperrung zu informieren.

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
>Wenn die Benutzerin bzw. der Benutzer, die bzw. der die Seite gesperrt hat, nicht zum Entsperren der Seite verfügbar ist, wenden Sie sich an den Support, um sich über Optionen zum Entfernen der Sperrung zu informieren.

<!--
>[!CAUTION]
>
>Locking a page can be performed when impersonating a user. However a page locked in this way can only then be unlocked by the user who was impersonated, or by a user with admin rights (a member of AEM Administrator IMS profile).
>
>Pages cannot be unlocked by impersonating the user who locked the page.
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

Das Verhalten der Befehle „Rückgängig“ und „Wiederholen“ ähnelt dem in anderer Software. Verwenden Sie die Befehle zum Wiederherstellen des aktuellen Status Ihrer Web-Seite, wenn Sie Entscheidungen über Inhalte treffen. Wenn Sie beispielsweise einen Textabsatz an eine Stelle auf der Seite verschoben haben, können Sie ihn mithilfe des Befehls zum Rückgängigmachen wieder zurück an die ursprüngliche Stelle verschieben. Falls Sie dann entscheiden, dass die vorherige Position besser war, verwenden Sie den Befehl „Wiederherstellen“, um „das Rückgängigmachen rückgängig zu machen“.

Sie können beispielsweise:

* Sie können Aktionen wiederholen, solange Sie seit der Verwendung von „Rückgängig machen“ keine Seitenbearbeitungen durchgeführt haben.
* Sie können maximal 20 Bearbeitungsaktionen rückgängig machen (Standardeinstellung).
* Sie können zum Rückgängigmachen und Wiederholen auch [Tastaturbefehle](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) verwenden.

Sie können die folgenden Arten von Seitenänderungen rückgängig machen und wiederherstellen:

* Hinzufügen, Bearbeiten, Entfernen und Verschieben von Absätzen
* Bearbeitung von Absatzinhalten im Kontext
* Kopieren, Ausschneiden und Einfügen von Elementen auf einer Seite

>[!NOTE]
>
>* Spezielle Berechtigungen sind erforderlich, um Änderungen rückgängig zu machen bzw. wiederherzustellen, die an Dateien und Bildern vorgenommen wurden.
>* Änderungen an Dateien und Bildern können für einen Verlauf von mindestens zehn Stunden rückgängig gemacht werden. Bei länger zurückliegenden Änderungen ist dies unter Umständen nicht mehr möglich. Ihre Admins können die Standardzeit von zehn Stunden ändern.
>* Ihr Systemadministrator kann verschiedene Aspekte der Funktionen „Rückgängig“ und „Wiederholen“ den Anforderungen Ihrer Instanz entsprechend konfigurieren.
<!--* Your system administrator can [configure various aspects of the Undo/Redo features](/help/sites-administering/config-undo.md) according to the requirements for your instance.-->
