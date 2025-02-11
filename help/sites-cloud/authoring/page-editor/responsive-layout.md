---
title: Responsives Layout
description: Mit AEM können Sie ein responsives Layout für Ihre Seiten erstellen, indem Sie die Layout-Container -Komponente verwenden.
exl-id: 87202742-5bed-4e87-a427-456a1a0e72cc
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 70a35cfeb163967b0f627d3ac6495f112d922974
workflow-type: tm+mt
source-wordcount: '1789'
ht-degree: 92%

---


# Responsives Layout {#responsive-layout}

AEM ermöglicht das Erstellen eines responsiven Layouts für Ihre Seiten mithilfe der Komponente **Layout-Container**.

>[!TIP]
>
>Dieses Dokument bietet einen Überblick über die Funktionen des Layout-Containers, der für Inhaltsautorinnen und -autoren verfügbar ist. Zusätzliche Ressourcen sind verfügbar:
>
>* Für Site-Admins werden Informationen zum Konfigurieren des Layout-Containers für Ihre Sites im Dokument [Konfigurieren des Layout-Containers und des Layout-Modus“ beschrieben](/help/sites-cloud/administering/responsive-layout.md)
>* Für Entwicklerinnen und Entwickler werden Details zum Layout-Container und zum responsiven Raster im Dokument [Responsives Design“ beschrieben, das ](/help/implementing/developing/introduction/responsive-design.md) und Tipps zur Verwendung von Layout-Containern und responsivem Raster beim Entwerfen Ihrer Site enthält.

## Überblick {#overview}

Die **Layout-Container**-Komponente bietet ein Absatzsystem, mit dem Sie Komponenten in einem responsiven Raster positionieren können. Dieses Raster kann das Layout entsprechend der Geräte-/Fenstergröße und dem Format neu anordnen. Die Komponente wird zusammen mit dem [**Layout-Modus**](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector) verwendet, in dem Sie Ihr responsives Layout geräteabhängig erstellen und bearbeiten können.

Der Layout-Container:

* Bietet horizontale Ausrichtung am Raster sowie die Möglichkeit, Komponenten nebeneinander im Raster zu platzieren und zu definieren, wann sie reduziert werden/umfließen sollen.
* Verwendet vordefinierte Breakpoints (z. B. für Smartphones, Tablets usw.), mit denen Sie das erforderliche Verhalten von Inhalten für die Geräte/Ausrichtungen definieren können.
   * Sie können beispielsweise die Komponentengröße anpassen oder festlegen, ob die Komponente auf bestimmten Geräten angezeigt werden soll.
* Kann verschachtelt werden, um die Spaltensteuerung zuzulassen.

Die Benutzenden können dann mithilfe des Emulators sehen, wie der Inhalt für bestimmte Geräte gerendert wird.

Das responsive Layout für Ihre Seiten wird von AEM durch eine Kombination von Mechanismen ermöglicht:

* [**Layout-Container-Komponente**](#adding-a-layout-container-and-its-content-edit-mode)

  Diese Komponente ist im [Komponenten-Browser](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser) verfügbar. Sie bietet ein Raster-Absatzsystem, mit dem Sie Komponenten in einem responsiven Raster hinzufügen und positionieren können. Dieses kann auf Ihrer Seite auch als Standardabsatzsystem festgelegt werden.

* [**Layout-Modus**](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector)

  Sobald der Layout-Container auf der Seite positioniert ist, können Sie im **Layout**-Modus Inhalte im responsiven Raster positionieren.

* [**Emulator**](#selecting-a-device-to-emulate)
Auf diese Weise können Sie responsive Websites erstellen und bearbeiten, deren Layout sich durch interaktive Größenanpassung der Komponenten an die Geräte-/Fenstergröße anpasst. Die Benutzenden können dann mithilfe des Emulators sehen, wie der Inhalt gerendert wird.

Mit diesen responsiven Rastermechanismen können Sie:

* Breakpoints verwenden, um verschiedene Inhalts-Layouts basierend auf der Gerätebreite (bezogen auf Gerätetyp und Ausrichtung) zu definieren.
* Verwendung derselben Breakpoints und Inhaltslayouts, um sicherzustellen, dass Ihr Inhalt an die Größe des Browser-Fensters auf dem Desktop angepasst wird.
* Mit der horizontalen Ausrichtung am Raster können Sie Komponenten im Raster platzieren, die Größe anpassen und definieren, wann ein Reduzieren/Umfließen daneben oder drüber/darunter erfolgen soll.
* Ausblenden von Komponenten für bestimmte Gerätelayouts.
* Realisieren einer Spaltensteuerung.

Je nach Projekt kann der Layout-Container als standardmäßiges Absatzsystem für Ihre Seiten oder als Komponente verwendet werden, die über den Komponenten-Browser zu Ihrer Seite hinzugefügt werden kann (oder beides).

>[!NOTE]
>
>Die Verwendung des obigen Mechanismus wird durch die Konfiguration der Vorlage aktiviert. Weitere Informationen finden Sie im Dokument [Konfigurieren des responsiven Layouts](/help/sites-cloud/administering/responsive-layout.md).

## Layout-Definitionen, Geräteemulation und Breakpoints {#layout-definitions-device-emulation-and-breakpoints}

Wenn Sie den Inhalt Ihrer Website erstellen, möchten Sie sicherstellen, dass Ihr Inhalt auf dem für die Anzeige verwendeten Gerät angemessen angezeigt wird.

AEM ermöglicht die Definition von Layouts, die von der Breite des Geräts abhängig sind:

* Mit dem Emulator können Sie diese Layouts auf einer Reihe von Geräten emulieren. Abgesehen vom Gerätetyp kann sich auch die durch die Option **Gerät drehen** ausgewählte Ausrichtung auf den ausgewählten Breakpoint auswirken, da sich die Breite ändert.
* Breakpoints sind Punkte, die die Layout-Definitionen trennen.
   * Sie definieren die maximale Breite (in Pixel) der Geräte, die ein bestimmtes Layout verwenden.
   * Breakpoints gelten in der Regel für eine Auswahl an Geräten und hängen von der Breite der Displays ab.
   * Ein Breakpoint reicht nach links bis zum nächsten Breakpoint.
   * Sie können den Breakpoint nicht spezifisch auswählen - durch die Auswahl eines Geräts und einer Ausrichtung wird der entsprechende Breakpoint automatisch ausgewählt.

Das Gerät **Desktop**, das keine bestimmte Breite aufweist und sich auf den Standard-Breakpoint bezieht (d. h. auf alles über dem letzten konfigurierten Breakpoint).

>[!NOTE]
>
>Es wäre möglich, Breakpoints für jedes einzelne Gerät zu definieren. Dies würde jedoch den Aufwand für die Layout-Definition und die Wartung deutlich erhöhen.

Wenn Sie den Emulator verwenden, wählen Sie ein bestimmtes Gerät für die Emulation und Layout-Definition aus und der zugehörige Breakpoint wird ebenfalls hervorgehoben. Alle von Ihnen vorgenommenen Layout-Änderungen können für andere Geräte angewendet werden, für die der Breakpoint gilt. Also für alle Geräte, die links neben der aktiven Breakpoint-Markierung, aber vor der nächsten Breakpoint-Markierung positioniert sind.

Wenn Sie z. B. das Gerät **iPhone 6 Plus** für die Emulation und das Layout auswählen (das mit einer Breite von 540 Pixel definiert ist), wird auch der Breakpoint **Telefon** (definiert mit 768 Pixel) aktiviert. Alle Änderungen am Layout, die Sie für das **iPhone 6** durchführen, gelten auch für die anderen Geräte unter dem Breakpoint **Telefone**, wie das **iPhone 5** (mit 320 Pixel definiert).

![Emulatoren](/help/sites-cloud/authoring/assets/responsive-layout-emulators.png)

## Auswahl eines zu emulierenden Geräts {#selecting-a-device-to-emulate}

1. Öffnen Sie die gewünschte Seite zur Bearbeitung. Zum Beispiel:

   `http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

1. Wählen Sie in der oberen Symbolleiste das Symbol **Emulator** aus:

   ![Schaltfläche „Emulator“](/help/sites-cloud/authoring/assets/emulator.png)

1. Die Emulator-Symbolleiste wird geöffnet.

   ![Emulator-Symbolleiste](/help/sites-cloud/authoring/assets/responsive-layout-emulator-toolbar.png)

   In der Emulator-Symbolleiste werden zusätzliche Layout-Optionen angezeigt:

   * **Gerät drehen**: Ermöglicht es Ihnen, die vertikale Ausrichtung (Hochformat) eines Geräts in eine horizontale Ausrichtung (Querformat) zu ändern und umgekehrt.

   ![Schaltfläche zum Drehen des Geräts in das Querformat](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-landscape-button.png)
   ![Schaltfläche zum Drehen des Geräts in das Hochformat](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-portrait-button.png)

   * **Gerät auswählen** – Ermöglicht es Ihnen, ein bestimmtes Gerät anzugeben, das aus einer Liste emuliert werden soll (Einzelheiten dazu werden im nächsten Schritt beschrieben).

   ![Schaltfläche „Gerät auswählen“](/help/sites-cloud/authoring/assets/responsive-layout-select-device-button.png)

1. Um ein bestimmtes zu emulierendes Gerät auszuwählen, haben Sie folgende Möglichkeiten:

   * Verwenden Sie das Symbol „Gerät auswählen“ und wählen Sie aus einer Dropdown-Auswahl aus.
   * Wählen Sie auf der Emulator-Symbolleiste das Gerätezeichen aus.

   ![Dropdown zum Auswählen des Geräts](/help/sites-cloud/authoring/assets/responsive-layout-select-device-dropdown.png)

1. Nachdem Sie ein bestimmtes Gerät ausgewählt haben, sind folgende Möglichkeiten verfügbar:

   * Sie können die aktive Markierung für das ausgewählte Gerät anzeigen, z. B. **iPad**.
   * Sie können die aktive Markierung für den entsprechenden [Breakpoint](#layout-definitions-device-emulation-and-breakpoints) anzeigen, z. B. **Tablet**.
   * Die gepunktete blaue Linie stellt den *Falz* für das ausgewählte Gerät dar (in diesem Fall ein **iPhone 6 Plus** im Querformat).

   ![Der Falz](/help/sites-cloud/authoring/assets/responsive-layout-fold.png)

   * Der Falz kann auch als Seitenumbruch für den Inhalt betrachtet werden (nicht zu verwechseln mit den [Breakpoints](#layout-definitions-device-emulation-and-breakpoints)). Dies wird zur Vereinfachung angezeigt, um zu veranschaulichen, welchen Teil des Inhalts die Benutzenden auf dem Gerät sehen werden, bevor sie scrollen.
   * Die Linie für den Falz wird nicht angezeigt, wenn die Höhe des zu emulierenden Geräts die Bildschirmgröße überschreitet.
   * Der Falz wird aus Komfortgründen für Autorinnen und Autoren angezeigt, aber nicht auf der veröffentlichten Seite.

## Hinzufügen eines Layout-Containers und seiner Inhalte (Bearbeitungsmodus) {#adding-a-layout-container-and-its-content-edit-mode}

Ein **Layout-Container** ist ein Absatzsystem mit folgenden Eigenschaften:

* Enthält andere Komponenten.
* Definiert das Layout.
* Reagiert auf Änderungen.

>[!NOTE]
>
>Falls er noch nicht verfügbar ist **muss der** Layout-Container[ explizit für ein Absatzsystem/eine Seite aktiviert ](/help/sites-cloud/administering/responsive-layout.md).

1. Der **Layout-Container** ist als Standardkomponente im [Komponenten-Browser](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser) verfügbar. Von hier können Sie ihn an die gewünschte Position auf der Seite ziehen. Anschließend wird der Platzhalter **Komponenten hierher ziehen** angezeigt.
1. Anschließend können Sie dem Layout-Container Komponenten hinzufügen. Diese Komponenten enthalten den tatsächlichen Inhalt:

   ![Layout-Container](/help/sites-cloud/authoring/assets/responsive-layout-add-to-layout-container.png)

## Auswählen und Bearbeiten eines Layout-Containers (Bearbeitungsmodus) {#selecting-and-taking-action-on-a-layout-container-edit-mode}

Sie können einen Layout-Container wie andere Komponenten im **Bearbeitungsmodus** auswählen und anschließend bearbeiten (ausschneiden, kopieren, löschen):

>[!CAUTION]
>
>Da ein Layout-Container ein Absatzsystem ist, werden beim Löschen der Komponente sowohl das Layout-Raster als auch alle Komponenten (und deren Inhalt) gelöscht, die sich im Container befinden.

1. Wenn Sie den Mauszeiger über den Rasterplatzhalter bewegen oder ihn auswählen, wird das Aktionsmenü angezeigt.

   ![Zum Layout-Container hinzufügen](/help/sites-cloud/authoring/assets/responsive-layout-container.png)

   Wählen Sie daraufhin die Option **Übergeordnetes Element** aus.

   ![Schaltfläche „Übergeordnet“](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

1. Wenn die Layout-Komponente verschachtelt ist, bietet die Auswahl der Option **Übergeordnet** eine Dropdown-Auswahl, über die Sie den verschachtelten Layout-Container oder dessen übergeordnete Elemente auswählen können.

   Wenn Sie den Mauszeiger im Dropdown-Menü über die Container-Namen halten, wird ihre Gliederung auf der Seite angezeigt.

   * Der am wenigsten verschachtelte Layout-Container ist blau dargestellt.
   * Alle folgenden Container sind in jeweils helleren Blautönen dargestellt.

   ![Verschachtelte Container](/help/sites-cloud/authoring/assets/responsive-layout-nested.png)

1. Das gesamte Raster wird mit seinem Inhalt hervorgehoben. Die Aktionssymbolleiste wird angezeigt, über die Sie eine Aktion auswählen können, z. B. **Löschen**.

## Definieren von Layouts (Layout-Modus) {#defining-layouts-layout-mode}

>[!NOTE]
>
>Sie können für jeden [Breakpoint](#layout-definitions-device-emulation-and-breakpoints) (der durch den emulierten Gerätetyp und die Ausrichtung bestimmt wird) ein eigenes Layout definieren.

Das Layout eines mit dem Layout-Container implementierten responsiven Rasters muss im **Layout**-Modus konfiguriert werden.

Der **Layout**-Modus kann auf zwei Arten aktiviert werden.

* Durch Verwenden des [Modusmenüs in der Symbolleiste](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector) und Auswählen des **Layout**-Modus
   * Wählen Sie den **Layout**-Modus so aus, wie Sie den Modus **Bearbeiten** oder **Targeting** auswählen.
   * Der **Layout**-Modus wird zunächst automatisch beibehalten. Sie können den **Layout**-Modus nur beenden, indem Sie über die Modusauswahl einen anderen Modus auswählen.
* Beim [Bearbeiten einer einzelnen Komponente](/help/sites-cloud/authoring/page-editor/edit-content.md#editing-component-layout).
   * Durch Verwendung der Option **Layout** im Schnellaktionsmenü der Komponente können Sie in den **Layout**-Modus wechseln.
   * Der **Layout**-Modus bleibt während der Bearbeitung der Komponente bestehen und kehrt in den Modus **Bearbeiten** zurück, sobald der Fokus zu einer anderen Komponente wechselt.

Im Layout-Modus können Sie verschiedene Aktionen für ein Raster ausführen:

* Ändern Sie die Größe der Inhaltskomponenten mithilfe der blauen Punkte. Die Größenanpassung wird immer am Raster ausgerichtet. Während der Größenanpassung wird im Hintergrund das Raster angezeigt, was die Ausrichtung erleichtert:

  ![Größe von Komponenten anpassen](/help/sites-cloud/authoring/assets/responsive-layout-resizing.png)

  >[!NOTE]
  >
  >Wenn Sie die Größe von Komponenten wie **Bildern** ändern, bleiben die Proportionen und Seitenverhältnisse erhalten.

* Wählen Sie eine Inhaltskomponente aus. Über die Symbolleiste haben Sie folgende Möglichkeiten:
   * **Übergeordnetes Element**: Ermöglicht die Auswahl der gesamten Layout-Container-Komponente, um diese insgesamt zu bearbeiten.
   * **In neue Zeile verschieben**: Die Komponente wird abhängig von dem innerhalb des Rasters verfügbaren Platz in eine neue Zeile verschoben.
   * **Komponente ausblenden**: Die Komponente wird unsichtbar (sie kann über die Symbolleiste des Layout-Containers wiederhergestellt werden).

  ![Komponente ausblenden](/help/sites-cloud/authoring/assets/responsive-layout-hide.png)

* Im **Layout-Modus** können Sie **Komponenten hierher ziehen** auswählen, um die gesamte Komponente auszuwählen. Für diesen Modus wird die Symbolleiste angezeigt.

  Die Symbolleiste bietet je nach Status der Layout-Komponente und der zugehörigen Komponenten unterschiedliche Optionen. Zum Beispiel:

   * **Übergeordnetes Element**: Wählt die übergeordnete Komponente aus.

     ![Schaltfläche „Übergeordnet“](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

   * **Ausgeblendete Komponenten anzeigen**: Blendet alle oder einzelne Komponenten ein. Die Zahl gibt an, wie viele ausgeblendete Komponenten es derzeit gibt. Der Zähler zeigt an, wie viele Komponenten ausgeblendet sind.

     ![Schaltfläche „Verborgene Komponenten einblenden“](/help/sites-cloud/authoring/assets/responsive-layout-show-button.png)

   * **Breakpoint-Layout zurücksetzen**: Stellt das Standard-Layout wieder her. Es wird kein benutzerdefiniertes Layout festgelegt.

     ![Schaltfläche „Breakpoint-Layout zurücksetzen“](/help/sites-cloud/authoring/assets/responsive-layout-revert-button.png)

   * **In neue Zeile verschieben**: Verschiebt die Komponente um eine Position nach oben, wenn der Leerraum dies erlaubt.

     ![Schaltfläche „In neue Zeile verschieben“](/help/sites-cloud/authoring/assets/responsive-layout-float-button.png)

   * **Komponente ausblenden**: Blendet die aktuelle Komponente aus.

     ![Schaltfläche „Komponente ausblenden“](/help/sites-cloud/authoring/assets/responsive-layout-hide-button.png)

  >[!NOTE]
  >
  >Im obigen Beispiel sind die Aktionen zum Verschieben und Ausblenden verfügbar, weil dieser Layout-Container in einem übergeordneten Layout-Container verschachtelt ist.

   * **Komponenten einblenden**: Ermöglicht das Auswählen der übergeordneten Komponenten, um die Aktionssymbolleiste mit der Option **Verborgene Komponenten einblenden** anzuzeigen. In diesem Beispiel gibt es zwei ausgeblendete Komponenten.

     ![Komponenten einblenden](/help/sites-cloud/authoring/assets/responsive-layout-unhide.png)

  Bei Auswahl der Option **Verborgene Komponenten einblenden** werden die jeweils ausgeblendeten Komponenten in Blau an ihren ursprünglichen Positionen angezeigt.

  ![Schaltfläche „Alle wiederherstellen“](/help/sites-cloud/authoring/assets/responsive-layout-restore-all.png)

  Bei Auswahl der Option **Alle wiederherstellen** werden alle verborgenen Komponenten eingeblendet.
