---
title: Responsives Layout
description: AEM ermöglicht Ihnen die Erstellung eines responsiven Layouts für Ihre Seiten
exl-id: 87202742-5bed-4e87-a427-456a1a0e72cc
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1748'
ht-degree: 56%

---

# Responsives Layout {#responsive-layout}

AEM ermöglicht Ihnen ein responsives Layout für Ihre Seiten mithilfe der **Layout-Container** -Komponente.

Dies bietet ein Absatzsystem, mit dem Sie Komponenten in einem responsiven Raster positionieren können. Dieses Raster kann das Layout entsprechend der Geräte-/Fenstergröße und dem Format neu anordnen. Die Komponente wird zusammen mit dem [**Layout**-Modus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) verwendet, in dem Sie Ihr responsives Layout geräteabhängig erstellen und bearbeiten können.

Der Layout-Container:

* Bietet horizontale Ausrichtung am Raster sowie die Möglichkeit, Komponenten nebeneinander im Raster zu platzieren und zu definieren, wann sie reduziert/umfließen sollen.
* Verwendet vordefinierte Breakpoints (z. B. für Smartphone, Tablet usw.), mit denen Sie das erforderliche Verhalten von Inhalten für verwandte Geräte/Ausrichtungen definieren können.
   * Sie können beispielsweise die Komponentengröße anpassen oder festlegen, ob die Komponente auf bestimmten Geräten angezeigt werden soll.
* Kann verschachtelt werden, um die Spaltensteuerung zuzulassen.

Der Benutzer kann dann sehen, wie der Inhalt mithilfe des Emulators für bestimmte Geräte gerendert wird.

Das responsive Layout für Ihre Seiten wird von AEM mithilfe einer Kombination von Mechanismen ermöglicht:

* [**Layout-Container-Komponente**](#adding-a-layout-container-and-its-content-edit-mode)

  Diese Komponente ist im [Komponenten-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) verfügbar. Sie bietet ein Raster-Absatzsystem, mit dem Sie Komponenten in einem responsiven Raster hinzufügen und positionieren können. Dieses kann auf Ihrer Seite auch als Standardabsatzsystem festgelegt werden.

* [**Layout-Modus**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes)

  Sobald der Layout-Container auf der Seite positioniert ist, können Sie im **Layout**-Modus Inhalte im responsiven Raster positionieren.

* [**Emulator**](#selecting-a-device-to-emulate)
Auf diese Weise können Sie responsive Websites erstellen und bearbeiten, die das Layout durch interaktive Größenanpassung der Komponenten an die Geräte-/Fenstergröße anpassen. Der Benutzer kann dann sehen, wie der Inhalt mithilfe des Emulators wiedergegeben wird.

Mit diesen responsiven Rastermechanismen können Sie:

* Verwenden Sie Haltepunkte, um verschiedene Inhaltslayouts basierend auf der Gerätebreite (bezogen auf Gerätetyp und Ausrichtung) zu definieren.
* Verwendung derselben Breakpoints und Inhaltslayouts, um sicherzustellen, dass Ihr Inhalt an die Größe des Browser-Fensters auf dem Desktop angepasst wird.
* Mit der horizontalen Ausrichtung am Raster können Sie Komponenten im Raster platzieren, die Größe anpassen und definieren, wann ein Reduzieren/Umfließen daneben oder drüber/darunter erfolgen soll.
* Ausblenden von Komponenten für bestimmte Gerätelayouts.
* Realisieren einer Spaltensteuerung.

Je nach Projekt kann der Layout-Container als standardmäßiges Absatzsystem für Ihre Seiten oder als Komponente verwendet werden, die über den Komponenten-Browser zu Ihrer Seite hinzugefügt werden kann (oder beides).

>[!TIP]
>
>Adobe stellt eine [GitHub-Dokumentation](https://adobe-marketing-cloud.github.io/aem-responsivegrid/) zum responsiven Layout als Referenz bereit. Diese kann Frontend-Entwicklern zur Verfügung gestellt werden, damit sie das AEM-Raster außerhalb von AEM verwenden können, um beispielsweise statische HTML-Modelle für künftige AEM Sites zu erstellen.

>[!NOTE]
>
>Die Verwendung des obigen Mechanismus wird durch die Konfiguration der Vorlage aktiviert. Weitere Informationen finden Sie unter „Konfigurieren des responsiven Layouts“. <!-- Use of the above mechanisms is enabled by configuration on the template. See [Configuring Responsive Layout](/help/sites-administering/configuring-responsive-layout.md) for further information.-->

## Layout-Definitionen, Geräteemulation und Breakpoints {#layout-definitions-device-emulation-and-breakpoints}

Wenn Sie den Inhalt Ihrer Website erstellen, möchten Sie sicherstellen, dass Ihr Inhalt auf dem für die Anzeige verwendeten Gerät angemessen angezeigt wird.

Mit AEM können Sie Layouts definieren, die von der Breite des Geräts abhängen:

* Mit dem Emulator können Sie diese Layouts auf einer Reihe von Geräten emulieren. Abgesehen vom Gerätetyp kann sich auch die durch die Option **Gerät drehen** ausgewählte Ausrichtung auf den ausgewählten Breakpoint auswirken, da sich die Breite ändert.
* Breakpoints sind Punkte, die die Layout-Definitionen trennen.
   * Sie definieren die maximale Breite (in Pixel) der Geräte, die ein bestimmtes Layout verwenden.
   * Breakpoints gelten in der Regel für eine Auswahl an Geräten und hängen von der Breite der Displays ab.
   * Ein Breakpoint reicht nach links bis zum nächsten Breakpoint.
   * Sie können den Breakpoint nicht spezifisch auswählen - durch die Auswahl eines Geräts und einer Ausrichtung wird der entsprechende Breakpoint automatisch ausgewählt.

Das Gerät **Desktop**, die keine bestimmte Breite hat, bezieht sich auf den Standard-Breakpoint (d. h. alles über dem letzten konfigurierten Breakpoint).

>[!NOTE]
>
>Es wäre möglich, Breakpoints für jedes einzelne Gerät zu definieren. Dies würde jedoch den Aufwand für die Layout-Definition und die Wartung deutlich erhöhen.

Wenn Sie den Emulator verwenden, wählen Sie ein bestimmtes Gerät für die Emulation und Layoutdefinition aus und der zugehörige Breakpoint wird ebenfalls hervorgehoben. Alle von Ihnen vorgenommenen Layoutänderungen gelten für andere Geräte, für die der Breakpoint gilt. d. h. alle Geräte, die links neben der aktiven Breakpoint-Markierung, aber vor der nächsten Breakpoint-Markierung positioniert sind.

Wenn Sie beispielsweise das Gerät auswählen **iPhone 6 Plus** (definiert mit einer Breite von 540 Pixel) für Emulation und Layout, der Breakpoint **Telefon** (definiert als 768 Pixel) wird ebenfalls aktiviert. Alle Layoutänderungen, die Sie für die **iPhone 6** auf andere Geräte im Rahmen der **Telefon** Breakpoint, z. B. **iPhone 5** (definiert als 320 Pixel).

![Emulatoren](/help/sites-cloud/authoring/assets/responsive-layout-emulators.png)

## Auswahl eines zu emulierenden Geräts {#selecting-a-device-to-emulate}

1. Öffnen Sie die gewünschte Seite zur Bearbeitung. Beispiel:

   `http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

1. Wählen Sie in der oberen Symbolleiste das Symbol **Emulator** aus:

   ![Schaltfläche „Emulator“](/help/sites-cloud/authoring/assets/emulator.png)

1. Die Emulator-Symbolleiste wird geöffnet.

   ![Emulator-Symbolleiste](/help/sites-cloud/authoring/assets/responsive-layout-emulator-toolbar.png)

   In der Emulator-Symbolleiste werden zusätzliche Layout-Optionen angezeigt:

   * **Gerät drehen** – Ermöglicht es Ihnen, die vertikale Ausrichtung (Hochformat) eines Geräts in eine horizontale Ausrichtung (Querformat) zu ändern und umgekehrt.

   ![Schaltfläche zum Drehen des Geräts in das Querformat](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-landscape-button.png)
   ![Schaltfläche zum Drehen des Geräts in das Hochformat](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-portrait-button.png)

   * **Gerät auswählen** – Ermöglicht es Ihnen, ein bestimmtes Gerät anzugeben, das aus einer Liste emuliert werden soll (Einzelheiten dazu werden im nächsten Schritt beschrieben).

   ![Schaltfläche „Gerät auswählen“](/help/sites-cloud/authoring/assets/responsive-layout-select-device-button.png)

1. Um ein bestimmtes zu emulierendes Gerät auszuwählen, haben Sie folgende Möglichkeiten:

   * Verwenden Sie das Symbol Gerät auswählen und wählen Sie aus einer Dropdown-Auswahl aus.
   * Tippen/klicken Sie auf der Emulator-Symbolleiste auf das Gerätezeichen.

   ![Dropdown zum Auswählen des Geräts](/help/sites-cloud/authoring/assets/responsive-layout-select-device-dropdown.png)

1. Nachdem Sie ein bestimmtes Gerät ausgewählt haben, sind folgende Möglichkeiten verfügbar:

   * Sie können die aktive Markierung für das ausgewählte Gerät anzeigen, z. B. **iPad**.
   * Sie können die aktive Markierung für den entsprechenden [Breakpoint](#layout-definitions-device-emulation-and-breakpoints) anzeigen, z. B. **Tablet**.
   * Die gepunktete blaue Linie stellt den *Falz* für das ausgewählte Gerät dar (in diesem Fall ein **iPhone 6 Plus** im Querformat).

   ![Der Falz](/help/sites-cloud/authoring/assets/responsive-layout-fold.png)

   * Die Kante kann auch als Seitenzeilenumbruch betrachtet werden (nicht zu verwechseln mit der [Breakpoints](#layout-definitions-device-emulation-and-breakpoints)) für den Inhalt. Diese wird angezeigt, um zu veranschaulichen, welchen Teil des Inhalts der Benutzer vor dem Scrollen auf dem Gerät sehen wird.
   * Die Linie für die Kante wird nicht angezeigt, wenn die Höhe des zu emulierenden Geräts größer als die Bildschirmgröße ist.
   * Der Falz wird aus Komfortgründen für Autoren, aber nicht auf der veröffentlichten Seite angezeigt.

## Hinzufügen eines Layout-Containers und seiner Inhalte (Bearbeitungsmodus) {#adding-a-layout-container-and-its-content-edit-mode}

Ein **Layout-Container** ist ein Absatzsystem mit folgenden Eigenschaften:

* Enthält andere Komponenten.
* Definiert das Layout.
* Reagiert auf Änderungen.

>[!NOTE]
>
>Falls er noch nicht verfügbar ist, muss der **Layout-Container** explizit für ein Absatzsystem/eine Seite aktiviert werden. <!-- If not already available, the **Layout Container** must be explicitly [activated for a paragraph system/page](/help/sites-administering/configuring-responsive-layout.md).-->

1. Der **Layout-Container** ist als Standardkomponente im [Komponentenbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) verfügbar. Von hier können Sie ihn an die gewünschte Position auf der Seite ziehen, nach der der Platzhalter **Komponenten hierher ziehen** angezeigt wird.
1. Anschließend können Sie dem Layout-Container Komponenten hinzufügen. Diese Komponenten enthalten den tatsächlichen Inhalt:

   ![Layout-Container](/help/sites-cloud/authoring/assets/responsive-layout-add-to-layout-container.png)

## Auswählen und Bearbeiten eines Layout-Containers (Bearbeitungsmodus) {#selecting-and-taking-action-on-a-layout-container-edit-mode}

Einen Layout-Container können Sie wie andere Komponenten im **Bearbeitungsmodus** auswählen und anschließend bearbeiten (ausschneiden, kopieren, löschen):

>[!CAUTION]
>
>Da ein Layout-Container ein Absatzsystem ist, werden beim Löschen der Komponente sowohl das Layout-Raster als auch alle Komponenten (und deren Inhalt) gelöscht, die sich im Container befinden.

1. Wenn Sie den Mauszeiger über den Rasterplatzhalter bewegen oder darauf tippen, wird das Aktionsmenü angezeigt.

   ![Zum Layout-Container hinzufügen](/help/sites-cloud/authoring/assets/responsive-layout-container.png)

   Wählen Sie daraufhin die Option **Übergeordnetes Element** aus.

   ![Schaltfläche „Übergeordnet“](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

1. Wenn die Layout-Komponente verschachtelt ist, wählen Sie die **Übergeordnet** bietet eine Dropdown-Auswahl, über die Sie den verschachtelten Layout-Container oder dessen übergeordnete Elemente auswählen können.

   Wenn Sie den Mauszeiger über die Namen der Container in der Dropdown-Liste bewegen, werden deren Konturen auf der Seite angezeigt.

   * Der am wenigsten verschachtelte Layout-Container ist blau dargestellt.
   * Jeder aufeinander folgende Container wird in einem helleren Blau dargestellt.

   ![Verschachtelte Behälter](/help/sites-cloud/authoring/assets/responsive-layout-nested.png)

1. Das gesamte Raster wird mit seinem Inhalt hervorgehoben. Die Aktionssymbolleiste wird angezeigt, über die Sie eine Aktion auswählen können, z. B. **Löschen.**

## Definieren von Layouts (Layout-Modus) {#defining-layouts-layout-mode}

>[!NOTE]
>
>Sie können für jeden [Breakpoint](#layout-definitions-device-emulation-and-breakpoints) (der durch den emulierten Gerätetyp und die Ausrichtung bestimmt wird) ein eigenes Layout definieren.

Das Layout eines mit dem Layout-Container implementierten responsiven Rasters muss im **Layout**-Modus konfiguriert werden.

Der **Layout**-Modus kann auf zwei Arten aktiviert werden.

* Durch Verwenden des [Modusmenüs in der Symbolleiste](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) und Auswählen des **Layout**-Modus
   * Wählen Sie den **Layout**-Modus so aus, wie Sie den Modus **Bearbeiten** oder **Targeting** auswählen.
   * Der **Layout**-Modus wird zunächst automatisch beibehalten. Sie können den **Layout**-Modus nur beenden, indem Sie über die Modusauswahl einen anderen Modus auswählen.
* Wann [Bearbeiten einer einzelnen Komponente](/help/sites-cloud/authoring/fundamentals/editing-content.md#edit-component-layout).
   * Durch Verwendung der Variablen **Layout** im Schnellaktionsmenü der Komponente können Sie zu **Layout** -Modus.
   * **Layout** -Modus bleibt beim Bearbeiten der Komponente bestehen und wird auf **Bearbeiten** Modus, sobald der Fokus auf eine andere Komponente wechselt.

Im Layout-Modus können Sie verschiedene Aktionen für ein Raster ausführen:

* Ändern Sie die Größe der Inhaltskomponenten mithilfe der blauen Punkte. Die Größenanpassung erfolgt immer am Raster. Bei der Größenanpassung wird das Hintergrundraster angezeigt, um die Ausrichtung zu erleichtern:

  ![Größe von Komponenten anpassen](/help/sites-cloud/authoring/assets/responsive-layout-resizing.png)

  >[!NOTE]
  >
  >Proportionen und Verhältnisse werden beibehalten, wenn Komponenten wie **Bilder** die Größe ändern.

* Wenn Sie auf eine Inhaltskomponente klicken/tippen, bietet Ihnen die Symbolleiste folgende Möglichkeiten:
   * **Übergeordnetes Element**: Ermöglicht die Auswahl der gesamten Layout-Container-Komponente, um diese insgesamt zu bearbeiten.
   * **In neue Zeile verschieben** - Die Komponente wird in eine neue Zeile verschoben, abhängig vom im Raster verfügbaren Platz.
   * **Komponente ausblenden** - Die Komponente wird unsichtbar (sie kann über die Symbolleiste des Layout-Containers wiederhergestellt werden).

  ![Komponente ausblenden](/help/sites-cloud/authoring/assets/responsive-layout-hide.png)

* Im **Layout**-Modus können Sie auf **Komponenten hierher ziehen** tippen/klicken, um die gesamte Komponente auszuwählen. Für diesen Modus wird die Symbolleiste angezeigt.

  Die Symbolleiste bietet je nach Status der Layout-Komponente und der zugehörigen Komponenten unterschiedliche Optionen. Beispiel:

   * **Übergeordnetes Element**: Wählt die übergeordnete Komponente aus.

     ![Schaltfläche „Übergeordnet“](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

   * **Verborgene Komponenten einblenden**: Ermöglicht das Einblenden aller oder einzelner Komponenten. Die Zahl gibt an, wie viele verborgene Komponenten es jeweils gibt. Der Zähler zeigt an, wie viele Komponenten ausgeblendet sind.

     ![Schaltfläche „Verborgene Komponenten einblenden“](/help/sites-cloud/authoring/assets/responsive-layout-show-button.png)

   * **Breakpoint-Layout zurücksetzen** - Wiederherstellen des Standardlayouts. Es wird kein benutzerdefiniertes Layout festgelegt.

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
