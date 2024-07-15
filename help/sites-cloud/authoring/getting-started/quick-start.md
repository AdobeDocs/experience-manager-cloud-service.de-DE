---
title: Schnellstartanleitung zum Verfassen von Seiten (Authoring)
description: Ein kurzer, allgemeiner Leitfaden mit den ersten Schritten zur Seitenbearbeitung
exl-id: d37c9b61-7382-4bf6-8b90-59726b871264
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '1541'
ht-degree: 100%

---


# Schnellstartanleitung zum Verfassen von Seiten (Authoring) {#quick-guide-to-authoring-pages}

Dieses Dokument ist als allgemeine Schnellstartanleitung für die wichtigsten Aktionen zur Erstellung von Seiten in AEM gedacht. Dieses Dokument:

* stellt keine umfassende Erläuterung dar.
* enthält Links zur detaillierten Dokumentation.

Genauere Informationen zur Bearbeitung mit AEM finden Sie unter:

* [Konzepte der Bearbeitung (Authoring)](/help/sites-cloud/authoring/getting-started/concepts.md)
* [Grundlegende Handhabung](/help/sites-cloud/authoring/getting-started/basic-handling.md)

{{edge-delivery-authoring}}

## Tipps {#a-few-quick-hints}

Bevor Sie mit der Schnellstartanleitung beginnen, hier eine kleine Sammlung von allgemeinen Tipps und Hinweisen, die Sie beachten sollten, aufgeteilt in Bereiche des Authoring-Systems.

### In der Sites-Konsole {#sites-console}

* Schaltfläche „Erstellen“

   * Diese Schaltfläche ist in vielen Konsolen verfügbar. Die aufgeführten Optionen sind kontextsensitiv und können je nach Szenario variieren.

* Neuanordnen von Seiten

   * Dies kann in der [Listenansicht](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view) durchgeführt werden. Die Änderungen werden angewendet und sind in anderen Ansichten sichtbar.

### Bearbeiten von Seiten {#page-authoring}

* Navigieren per Links

   * **Links sind für die Navigation nicht verfügbar**, wenn Sie sich im Modus **Bearbeiten** befinden. Für die Navigation mithilfe von Links müssen Sie [die Seite in der Vorschau anzeigen](/help/sites-cloud/authoring/fundamentals/editing-content.md#previewing-pages), indem Sie eine der folgenden Optionen verwenden:

      * [Vorschaumodus](/help/sites-cloud/authoring/fundamentals/editing-content.md#preview-mode)
      * [Als veröffentlicht anzeigen](/help/sites-cloud/authoring/fundamentals/editing-content.md#view-as-published)

* Versionen werden nicht über den Seiteneditor gestartet/erstellt. Dies geschieht jetzt über die **Sites-Konsole** (entweder über **Erstellen** oder [Timeline](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) für eine ausgewählte Ressource).

>[!NOTE]
>
>Es gibt eine Reihe von Tastaturbefehlen, die die Bearbeitung vereinfachen.
>
>* [Tastaturbefehle bei der Seitenbearbeitung](/help/sites-cloud/authoring/fundamentals/keyboard-shortcuts.md)
>* [Tastaturbefehle für Konsolen](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md)

### Suchen nach Seiten {#finding-your-page}

Es gibt verschiedene Möglichkeiten, eine Seite zu finden: Sie können navigieren und/oder suchen:

1. Öffnen Sie die **Sites-Konsole** (über die Option **Sites** in der [Globalen Navigation](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) – dies wird ausgelöst (Dropdown), wenn Sie auf den Link „Adobe Experience Manager“ klicken.

1. Navigieren Sie in der Struktur nach unten, indem Sie auf die entsprechende Seite tippen/klicken. Wie die Seitenressourcen dargestellt werden, hängt von der verwendeten Ansicht ab – [Karte, Liste oder Spalte](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources):

   ![Anzeigen der Auswahl-Dropdown-Liste](/help/sites-cloud/authoring/assets/views.png)

1. Navigieren Sie in der Baumstruktur nach oben, indem Sie [den Breadcrumb in der Kopfzeile](/help/sites-cloud/authoring/getting-started/basic-handling.md#the-header) verwenden. Dies ermöglicht es Ihnen, zum ausgewählten Pfad zurückzukehren:

   ![Breadcrumb-Dropdown](/help/sites-cloud/authoring/assets/breadcrumb.png)

1. Sie können auch nach einer Seite [suchen](/help/sites-cloud/authoring/getting-started/search.md). Sie können Ihre Seite aus den angezeigten Ergebnissen auswählen.

   ![Suchfeld](/help/sites-cloud/authoring/assets/search.png)

### Erstellen einer neuen Seite {#creating-a-new-page}

So [erstellen Sie eine Seite](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page):

1. [Navigieren Sie zu der Position, an der Sie die neue Seite erstellen möchten.](#finding-your-page)
1. Verwenden Sie das Symbol **Erstellen** und wählen Sie dann **Seite** aus der Liste:

   ![Schaltfläche „Erstellen“](/help/sites-cloud/authoring/assets/create.png)

1. Dadurch wird der Assistent geöffnet, der Sie durch das Erfassen der benötigten Informationen führt, die Sie zum [Erstellen einer neuen Seite](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) brauchen. Befolgen Sie die Anweisungen auf dem Bildschirm.

### Auswählen Ihrer Seite für weitere Aktionen {#selecting-your-page-for-further-action}

Sie können eine Seite auswählen, um eine Aktion für sie durchzuführen. Wenn Sie eine Seite auswählen, wird die Symbolleiste automatisch aktualisiert, sodass die für diese Ressource relevanten Aktionen angezeigt werden.

Wie Sie eine Seite auswählen, hängt davon ab, welche Ansicht Sie in der Konsole verwenden:

1. Spaltenansicht:

   * Wählen Sie die Miniaturansicht für die gewünschte Ressource aus. Auf der Miniaturansicht wird die ausgewählte Ressource durch ein Häkchen gekennzeichnet.

1. Listenansicht:

   * Wählen Sie die Miniaturansicht für die gewünschte Ressource aus. Auf der Miniaturansicht wird die ausgewählte Ressource durch ein Häkchen gekennzeichnet.

1. Kartenansicht:

   * Wechseln Sie in den Auswahlmodus, indem Sie [die gewünschte Ressource auswählen](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources). Wie Sie dies durchführen, hängt von Ihrem Gerät ab:

      * Auf einem Mobilgerät: Wählen und halten Sie die Karte
      * Auf einem Desktop-Gerät: Verwenden Sie den durch das Häkchen-Symbol dargestellten [Schnellzugriff](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions):

   * Auf der Karte wird die ausgewählte Seite durch ein Häkchen gekennzeichnet.

   ![Beispielkarte](/help/sites-cloud/authoring/assets/card.png)

### Schnellaktionen (nur Kartenansicht/Desktop) {#quick-actions-card-view-desktop-only}

[Schnellaktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions) sind verfügbar:

1. [Navigieren Sie zu der Seite](#finding-your-page), für die Sie eine Aktion ausführen möchten.
1. Bewegen Sie den Mauszeiger über die Karte, die die gewünschte Ressource darstellt. Die Schnellaktionen werden angezeigt:

   ![Kartenaktionen](/help/sites-cloud/authoring/assets/card-actions.png)

### Bearbeiten des Seiteninhalts {#editing-your-page-content}

So bearbeiten Sie Ihre Seite:

1. [Navigieren Sie zu der Seite](#finding-your-page), die Sie bearbeiten möchten.
1. [Öffnen Sie die zu bearbeitende Seite](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#opening-a-page-for-editing) über das Symbol „Bearbeiten“ (Bleistift):

   ![Schaltfläche „Bearbeiten“](/help/sites-cloud/authoring/assets/edit.png)

   Darauf können Sie zugreifen, indem Sie wahlweise Folgendes verwenden:

   * [Schnellzugriffe (nur Kartenansicht/Desktop)](#quick-actions-card-view-desktop-only) für die jeweilige Ressource
   * Symbolleiste, wenn die [Seite ausgewählt wurde](#selecting-your-page-for-further-action)

1. Beim Öffnen des Editors haben Sie folgende Möglichkeiten:

   * [Fügen Sie der Seite eine neue Komponente hinzu](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component), indem Sie:

      * den Seitenbereich öffnen
      * die Komponentenregisterkarte (den [Komponenten-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser)) auswählen
      * die gewünschte Komponente auf Ihre Seite ziehen

     Der Seitenbereich kann mit folgendem Symbol geöffnet (und geschlossen) werden:

     ![Schaltfläche zum Umschalten des Seitenbereichs](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

   * [Den Inhalt einer vorhandenen Komponente](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-toolbar) auf der Seite bearbeiten:

      * Öffnen Sie die Komponenten-Symbolleiste mit einer der beiden Optionen. Öffnen Sie das Dialogfeld über das Symbol **Bearbeiten** (Bleistift).
      * Öffnen Sie den integrierten Editor für die Komponente entweder durch Auswählen und Halten oder durch einen langsamen Doppelklick. Die verfügbaren Aktionen werden angezeigt (bei einigen Komponenten ist dies eine eingeschränkte Auswahl).
      * Um alle verfügbaren Aktionen anzuzeigen, gehen Sie wie folgt in den Vollbildmodus:

        ![Schaltfläche „Vollbild“](/help/sites-cloud/authoring/assets/full-screen.png)

   * [Die Eigenschaften einer vorhandenen Komponente konfigurieren](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-edit-dialog)

      * Öffnen Sie die Komponenten-Symbolleiste mit einer der beiden Optionen. Verwenden Sie das Symbol **Konfigurieren** (Schraubenschlüssel), um den Dialog zu öffnen.

   * [Verschieben](/help/sites-cloud/authoring/fundamentals/editing-content.md#moving-a-component) Sie eine Komponente mit einem der folgenden Verfahren:

      * Ziehen Sie die gewünschte Komponente an die neue Position.
      * Öffnen Sie die Komponenten-Symbolleiste mit einer der beiden Optionen. Verwenden Sie die Symbole **Ausschneiden** und dann **Einfügen**, wo erforderlich.

   * Wenden Sie die Aktionen [Kopieren (und Einfügen)](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-toolbar) auf eine Komponente an:

      * Öffnen Sie die Komponenten-Symbolleiste mit einer der beiden Optionen. Verwenden Sie die Symbole **Ausschneiden** und dann **Einfügen**, wo erforderlich.

   >[!NOTE]
   >
   >Sie können Komponenten auf derselben oder einer anderen Seite **einfügen**. Wenn Sie Komponenten auf einer anderen Seite einfügen, die bereits vor dem Ausschneiden und Kopieren geöffnet war, muss diese Seite aktualisiert werden.

   * So [löschen](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-toolbar) Sie eine Komponente:

      * Öffnen Sie die Komponenten-Symbolleiste durch Tippen oder Klicken, und verwenden Sie das Symbol **Löschen**.

   * Fügen Sie der Seite [Anmerkungen](/help/sites-cloud/authoring/fundamentals/annotations.md#annotations) hinzu:

      * Wählen Sie den Modus **Anmerken** (Sprechblasensymbol). Fügen Sie Anmerkungen mit dem Symbol **Anmerkung hinzufügen** (Pluszeichen) hinzu. Beenden Sie den Anmerkungsmodus mit dem X oben rechts.

        ![Schaltfläche „Anmerkungen“](/help/sites-cloud/authoring/assets/annotations.png)

   * [Vorschau einer Seite](/help/sites-cloud/authoring/fundamentals/editing-content.md#preview-mode) (um ihre Darstellung in der Publishing-Umgebung anzuzeigen)

      * Wählen Sie in der Symbolleiste die Option **Vorschau**.

   * Kehren Sie in den Bearbeitungsmodus zurück (oder wählen Sie einen anderen Modus), indem Sie die Dropdown-Auswahl **Bearbeiten** verwenden.

   >[!NOTE]
   >
   >Verwenden Sie den [Vorschaumodus](/help/sites-cloud/authoring/fundamentals/editing-content.md#preview-mode), wenn Sie mithilfe von Links im Inhalt navigieren möchten.

### Bearbeiten der Seiteneigenschaften {#editing-the-page-properties}

Es gibt (im Wesentlichen) zwei Methoden für das [Bearbeiten von Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md):

* In der Konsole **Sites**:

   1. [Navigieren Sie zu der Seite](#finding-your-page), die Sie veröffentlichen möchten.
   1. Wählen Sie das Symbol **Eigenschaften** aus, indem Sie wahlweise Folgendes verwenden:

      * [Schnellzugriffe (nur Kartenansicht/Desktop)](#quick-actions-card-view-desktop-only) für die jeweilige Ressource
      * Symbolleiste, wenn die [Seite ausgewählt wurde](#selecting-your-page-for-further-action)

      ![Schaltfläche „Eigenschaften“](/help/sites-cloud/authoring/assets/properties.png)

   1. Die Seiteneigenschaften werden angezeigt. Sie können nach Bedarf Aktualisierungen vornehmen. Speichern Sie diese anschließend, um sie beizubehalten.

* Beim [Bearbeiten Ihrer Seite](#editing-your-page-content):

   1. Öffnen Sie das Menü **Seiteninformationen**.
   1. Wählen Sie **Eigenschaften öffnen**, um den Dialog zum Bearbeiten der Eigenschaften zu öffnen.

      ![Schaltfläche „Seiteninformationen“](/help/sites-cloud/authoring/assets/page-information.png)

### Veröffentlichen Ihrer Seite (oder Rückgängigmachen der Veröffentlichung) {#publishing-your-page-or-unpublishing}

Es gibt im Wesentlichen zwei Methoden zum [Veröffentlichen Ihrer Seite](/help/sites-cloud/authoring/fundamentals/publishing-pages.md) (und ebenso zum Rückgängigmachen der Veröffentlichung):

* In der Konsole **Sites**:

   1. [Navigieren Sie zu der Seite](#finding-your-page), die Sie veröffentlichen möchten.
   1. Wählen Sie das Symbol **Quick Publish** aus, indem Sie wahlweise Folgendes verwenden:

      * [Schnellzugriffe (nur Kartenansicht/Desktop)](#quick-actions-card-view-desktop-only) für die jeweilige Ressource
      * Symbolleiste, wenn die [Seite ausgewählt wurde](#selecting-your-page-for-further-action) (ermöglicht auch Zugriff auf [Später veröffentlichen](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)).

      ![Schaltfläche „Quick Publish“](/help/sites-cloud/authoring/assets/quick-publish.png)

* Beim [Bearbeiten Ihrer Seite](#editing-your-page-content):

   1. Öffnen Sie das Menü **Seiteninformationen**.
   1. Wählen Sie **Seite veröffentlichen**.

* Das Rückgängigmachen der Veröffentlichung einer Seite in der Konsole kann nur über die Option **Veröffentlichung verwalten** erfolgen, die nur in der Symbolleiste verfügbar ist (nicht über Schnellaktionen).

  ![Schaltfläche „Veröffentlichung verwalten“](/help/sites-cloud/authoring/assets/manage-publication.png)

  Die Option **Veröffentlichung der Seite aufheben** ist weiterhin über das Menü **Seiteninformationen** im Editor verfügbar.

  Weitere Informationen finden Sie unter [Veröffentlichen von Seiten](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#unpublishing-pages).

### Verschieben, Kopieren und Einfügen oder Löschen Ihrer Seite {#move-copy-and-paste-or-delete-your-page}

Diese Aktionen können alle wie folgt ausgelöst werden:

1. [Navigieren Sie zu der Seite](#finding-your-page), die Sie verschieben, kopieren und einfügen oder löschen möchten.
1. Wählen Sie das Symbol zum Kopieren (und dann Einfügen), Verschieben oder Löschen nach Bedarf aus, indem Sie eine der folgenden Aktionen durchführen:

   * [Schnellaktionen (nur Kartenansicht/Desktop)](#quick-actions-card-view-desktop-only) für die gewünschte Ressource.
   * Symbolleiste, wenn die [Seite ausgewählt wurde](#selecting-your-page-for-further-action)

   Anschließend abhängig von Ihrer Aktion:

   * [Kopieren](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#copying-and-pasting-a-page):

      * Navigieren Sie dann zum neuen Ort und fügen Sie die Seite ein.

   * [Verschieben](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#moving-or-renaming-a-page):

      * Der Assistent wird geöffnet, um die zum Verschieben der Seite erforderlichen Informationen zu sammeln. Befolgen Sie die Anweisungen auf dem Bildschirm.

   * [Löschen](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#deleting-a-page):

      * Sie werden aufgefordert, die Aktion zu bestätigen.

   >[!NOTE]
   >
   >Löschen ist nicht als Schnellaktion verfügbar.

### Sperren (und Entsperren) Ihrer Seite  {#locking-your-page-then-unlocking}

[Sperren einer Seite](/help/sites-cloud/authoring/fundamentals/editing-content.md#locking-a-page): Verhindert, dass andere Autoren daran arbeiten, während Sie dies tun. Das Symbol bzw. die Schaltfläche „Sperren“ (und „Entsperren“) ist verfügbar:

* Symbolleiste, wenn die [Seite ausgewählt wurde](#selecting-your-page-for-further-action)
* Dropdown-Menü [Seiteninformationen](#editing-the-page-properties) beim Bearbeiten einer Seite
* Seitensymbolleiste beim Bearbeiten einer Seite (wenn die Seite gesperrt ist)

Beispielsweise sieht das Schloss-Symbol folgendermaßen aus:

![Schaltfläche „Sperren“](/help/sites-cloud/authoring/assets/lock.png)

### Zugreifen auf Seitenverweise {#accessing-page-references}

[Schnellzugriff auf Verweise](/help/sites-cloud/authoring/fundamentals/environment-tools.md#references) von/zu einer Seite ist in der Verweisleiste verfügbar.

1. Wählen Sie die Option **Verweise** mithilfe des Symbolleistensymbols (vor oder nach dem [Auswählen Ihrer Seite](#selecting-your-page-for-further-action)):

   ![Ansichtsoption „Verweise“](/help/sites-cloud/authoring/assets/references.png)

   Ein Liste von Verweistypen wird angezeigt:

   ![Ansicht „Verweise“](/help/sites-cloud/authoring/assets/references-list.png)

1. Wählen Sie den gewünschten Verweistyp aus, um weitere Details anzuzeigen und (bei Bedarf) weitere Aktionen auszuführen.

### Erstellen einer Version Ihrer Seite {#creating-a-version-of-your-page}

So erstellen Sie eine [Version](/help/sites-cloud/authoring/features/page-versions.md) Ihrer Seite:

1. Wählen Sie zum Öffnen der Timeline-Leiste die Option **[Timeline](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)** mithilfe des Symbolleistensymbols (vor oder nach dem [Auswählen Ihrer Seite](#selecting-your-page-for-further-action)):

   ![Ansichtsoption „Timeline“](/help/sites-cloud/authoring/assets/timeline.png)

1. Wählen Sie unten rechts in der Spalte „Timeline“ die Auslassungspunkte aus, um weitere Schaltflächen einzublenden, darunter auch **Als Version speichern**.

   ![Ansicht „Timeline“](/help/sites-cloud/authoring/assets/timeline-view.png)

1. Wählen Sie **Als Version speichern**, gefolgt von **Erstellen**.

### Wiederherstellen/Vergleichen einer Seitenversion {#restoring-comparing-a-version-of-your-page}

Beim Wiederherstellen und/oder Vergleichen von Seitenversionen wird dasselbe grundlegende Verfahren eingesetzt:

1. Wählen Sie mithilfe des Symbolleistensymbols die Option **[Timeline](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)** (vor oder nach dem [Auswählen Ihrer Seite](#selecting-your-page-for-further-action)):

   ![Ansichtsoption „Timeline“](/help/sites-cloud/authoring/assets/timeline.png)

   Wenn bereits eine Version der Seite gespeichert wurde, wird diese in der Timeline aufgeführt.

1. Wählen Sie die Version aus, die Sie wiederherstellen möchten. Dadurch werden zusätzliche Aktionsschaltflächen angezeigt:

   * **Auf diese Version zurücksetzen**

      * Die Version wird wiederhergestellt.

   * **Unterschiede anzeigen**

      * Die Seite wird geöffnet und die Unterschiede (zwischen den beiden Versionen) werden hervorgehoben.
