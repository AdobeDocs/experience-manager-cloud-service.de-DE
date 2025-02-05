---
title: Konfigurieren von Layout-Container und Layout-Modus
description: Erfahren Sie, wie Sie Layout-Container und Layout-Modus konfigurieren, um responsive Layouts für Ihre Inhaltsautorinnen und Inhaltsautoren zu aktivieren.
exl-id: 469e8151-8231-4ccc-b7f6-855545f87440
solution: Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 96%

---

# Konfigurieren von Layout-Container und Layout-Modus {#configuring-layout-container-and-layout-mode}

Ein [responsives Layout](/help/sites-cloud/authoring/page-editor/responsive-layout.md) ist eine Methode, um ein [responsives Webdesign](https://de.wikipedia.org/wiki/Responsive_Webdesign) zu realisieren. Dadurch kann der Inhaltsautor Web-Seiten erstellen, deren Layout und Abmessungen von den Geräten abhängen, die ihre Benutzer verwenden.

Das responsive Layout für Ihre Seiten wird von AEM durch eine Kombination von Mechanismen ermöglicht:

* **[Layout-Container](/help/sites-cloud/authoring/page-editor/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode)**: Diese Komponente liefert ein Rasterabsatzsystem, mit dem Sie Komponenten in einem responsiven Raster hinzufügen und positionieren können.
   * Sie können sie als Standard-Absatzsystem für Ihre Seite nutzen und/oder sie anderen Autorinnen und Autoren im Komponenten-Browser zur Verfügung stellen.
   * Die standardmäßige **Layout-Container**-Komponente ist definiert unter `/libs/wcm/foundation/components/responsivegrid`.
   * Sie können Layout-Container definieren:
      * als Komponente, die Benutzerinnen und Benutzer einer Seite hinzufügen können.
      * als Standard-Absatzsystem für die Seite.
      * als Komponente und als Standard-Absatzsystem gleichzeitig.
         * Sie können den Layout-Container als Standard für die Seite festlegen und es den Benutzenden gleichzeitig erlauben, weitere Layout-Container darin hinzuzufügen, z. B. für die Spaltensteuerung.
* **[Layout-Modus](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector)**: Sobald der Layout-Container auf Ihrer Seite positioniert ist, können Sie den **Layout**-Modus verwenden, um Inhalte innerhalb des responsiven Rasters zu positionieren.
* **[Emulator](/help/sites-cloud/authoring/page-editor/responsive-layout.md#selecting-a-device-to-emulate)**: Auf diese Weise können Sie responsive Websites erstellen und bearbeiten, deren Layout sich durch interaktive Größenanpassung der Komponenten an die Geräte-/Fenstergröße anpasst. Die Benutzenden können dann mithilfe des Emulators sehen, wie der Inhalt gerendert wird.

Mit diesen responsiven Rastermechanismen können Sie:

* Breakpoints verwenden (die die Gerätegruppierung angeben), um je nach Geräte-Layout ein unterschiedliches Inhaltsverhalten zu definieren.
* Komponenten basierend auf Gerätegruppen ausblenden (d. h. definieren, an welchem Breakpoint eine Komponente ausgeblendet wird).
* Horizontales Einrasten am Raster verwenden (Komponenten im Raster platzieren, die Größe nach Bedarf ändern oder definieren, wann ein Reduzieren/Umfließen erfolgen soll, damit sie nebeneinander oder über-/untereinander angeordnet werden).
* Realisieren einer Spaltensteuerung.

>[!NOTE]
>
>Wenn Sie eine Site aus dem [Projekt-Archetyp](#addlink) oder aus der [Standard-Site-Vorlage](#addlink) erstellen, wird das responsive Layout generell konfiguriert. Andernfalls müssen Sie [die Layout-Container-Komponente für Ihre Seiten aktivieren](#enable-the-layout-container-component-for-page).

## Aktivieren des Emulators {#enabling-emulator}

Der [Projekt-Archetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) und die [Standard-Site-Vorlage](/help/sites-cloud/administering/site-creation/site-templates.md#standard-site-template) sind bereits für die Verwendung des Emulators aktiviert. Wenn Sie eigene Inhalte entwickelt haben, die nicht auf den Kernkomponenten oder dem Archetyp basieren, lesen Sie bitte das Dokument [Responsives Design](/help/implementing/developing/introduction/responsive-design.md), um zu erfahren, wie Sie Ihre Komponenten unter Nutzung dieser Funktionen entwickeln können.

## Aktivieren des Layout-Modus für die Website {#activate-layout-mode-for-your-site}

Der **Layout-Modus** ermöglicht es Ihnen, den Emulator zu verwenden, um das Layout Ihrer Inhalte für verschiedene Geräte anzupassen. Die WKND-Beispielseite ist bereits für den **Layout-Modus** aktiviert. Führen Sie diese Schritte aus, um Ihre eigene Site zu aktivieren.

### Konfigurieren von Breakpoints {#configure-breakpoints}

Breakpoints sind für responsives Design von entscheidender Bedeutung und definieren, wie und wann Inhalte an das Zielgerät angepasst werden. Seien Sie jedoch vorsichtig, da jeder von Ihnen eingeführte Breakpoint für Ihre Autorinnen und Autoren zusätzliche Arbeit zur Anpassung des Inhalts bedeutet. Oft können zwei Breakpoints ausreichend sein, einschließlich des standardmäßigen Breakpoints, der immer vorhanden ist. Adobe empfiehlt, nicht mehr als drei Breakpoints einschließlich des Standardwertes zu erstellen, d. h. nicht mehr als zwei Knoten unter `cq:responsive/breakpoint`.

* Breakpoints haben einen Titel und eine Breite:
   * Der Titel beschreibt die generische Gerätegruppierung, gegebenenfalls mit Ausrichtung.
      * Zum Beispiel `phone`, `tablet`
   * Die Breite definiert die maximale Breite in Pixel für diese generische Gerätegruppierung.
      * Wenn der Telefon-Breakpoint beispielsweise eine Breite von 768 hat, dann ist dies die maximale Breite des Layouts, das für ein Smartphone verwendet wird.
* Breakpoints können definiert werden:
   * auf der Seitenvorlage, von der aus die Einstellungen auf alle Seiten kopiert werden, die mit dieser Vorlage erstellt wurden
   * auf dem Seitenknoten, von dem aus die Einstellungen von allen untergeordneten Seiten übernommen werden.
* Breakpoints sind als Markierungen am oberen Rand des Seiten-Editors sichtbar, wenn Sie den Emulator verwenden.
* Breakpoints werden von der Hierarchie des übergeordneten Knotens übernommen und können beliebig überschrieben werden.
* Es gibt einen standardmäßigen (vorkonfigurierten) Breakpoint, der alles oberhalb des letzten konfigurierten Breakpoints abdeckt.
* Breakpoints können Sie mit CRXDE Lite oder XML definieren.

Breakpoints sollten sowohl für neue als auch für bestehende Projekte berücksichtigt werden.

* Wenn Sie ein neues Projekt einrichten, sollten Sie Breakpoints zu den Vorlagen hinzufügen.
* Wenn Sie ein vorhandenes Projekt (mit vorhandenen Inhalten) migrieren, müssen Sie:
   * Breakpoints zu Vorlagen hinzufügen.
   * Dieselben Breakpoints zu vorhandenen Seiten hinzufügen.

Aufgrund der Vererbung müssen Sie dies nur für die Stammseite Ihres Inhalts tun.

#### Konfigurieren von Breakpoints mithilfe von CRXDE Lite {#configuring-breakpoints-using-crxde-lite}

1. Navigieren Sie mit CRXDE Lite zu einem der folgenden:

   * Ihrer Vorlagendefinition.
   * dem Knoten `jcr:content` Ihrer Seite

1. Erstellen Sie unter `jcr:content` den Knoten:

   * Name: `cq:responsive`
   * Typ: `nt:unstructured`

1. Erstellen Sie darunter den Knoten:

   * Name: `breakpoints`
   * Typ: `nt:unstructured`

1. Unter dem Breakpoints-Knoten können Sie eine beliebige Anzahl von Breakpoints erstellen. Jede Definition ist ein einzelner Knoten mit den folgenden Eigenschaften:

   * Name: `<descriptive name>`
   * Typ: `nt:unstructured`
   * Titel: `String <descriptive title seen in Emulator>`
   * Breite: `Decimal <value of breakpoint>`

#### Konfigurieren von Haltepunkten mit XML {#configuring-breakpoints-using-xml}

Haltepunkte befinden sich im Abschnitt `<jcr:content>` der Datei `.context.html` im entsprechenden Vorlagenorder (bzw. Inhaltsordner).

Eine Beispieldefinition:

```xml
<cq:responsive jcr:primaryType="nt:unstructured">
  <breakpoints jcr:primaryType="nt:unstructured">
    <phone jcr:primaryType="nt:unstructured" title="{String}Phone" width="{Decimal}768"/>
    <tablet jcr:primaryType="nt:unstructured" title="{String}Tablet" width="{Decimal}1200"/>
  </breakpoints>
</cq:responsive>
```

## Aktivieren der Größenänderung von Komponenten für die Seite {#enable-component-resizing-for-the-page}

Die Größenanpassung von Komponenten im **Layout-Modus** ist ein wichtiger Bestandteil des responsiven Designs, das auf der WKND-Beispielseite verwendet werden kann. Führen Sie diese Schritte aus, um Ihre eigene Site zu aktivieren.

### Festlegen des Layout-Containers als Haupt-Absatzsystem {#set-layout-container-as-main-parsys}

Um festzulegen, dass das Haupt-Absatzsystem Ihrer Seite ein Layout-Container sein sollen, definieren Sie die Absatzsysteme wie folgt:

`wcm/foundation/components/responsivegrid`

In entweder der:

* Seitenkomponente
* Seitenvorlage (zur zukünftigen Verwendung)

Die folgenden beiden Beispiele veranschaulichen die Definition:

* **HTL:**

  ```xml
  <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
  ```

* **JSP:**

  ```xml
  <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
  ```

### Einschließen von responsivem CSS {#include-the-responsive-css}

#### CSS für Breakpoints mit LESS {#css-for-breakpoints-using-less}

AEM verwendet LESS, um Teile des erforderlichen CSS zu generieren. Diese müssen für Ihre Projekte einbezogen werden.

Sie müssen auch eine [Client-Bibliothek](/help/implementing/developing/introduction/clientlibs.md) erstellen, um zusätzliche Konfigurations- und Funktionsaufrufe bereitzustellen. Der folgende LESS-Extrakt ist ein Beispiel für das Minimum, das Sie zum Projekt hinzufügen müssen:

```java
@import (once) "/libs/wcm/foundation/clientlibs/grid/grid_base.less";

/* maximum amount of grid cells to be provided */
@max_col: 12;

/* default breakpoint */
.aem-Grid {
  .generate-grid(default, @max_col);
}

/* phone breakpoint */
@media (max-width: 768px) {
  .aem-Grid {
    .generate-grid(phone, @max_col);
  }
}

/* tablet breakpoint */
@media (min-width: 769px) and (max-width: 1200px) {
  .aem-Grid {
    .generate-grid(tablet, @max_col);
  }
}
```

Die Basisrasterdefinition finden Sie unter:

`/libs/wcm/foundation/clientlibs/grid/grid_base.less`

#### Überlegungen zur Gestaltung {#styling-considerations}

Die Größe von Komponenten in einem responsiven Container wird (zusammen mit den entsprechenden HTML-DOM-Elementen) entsprechend der Größe des responsiven Rasters geändert. Daher empfehlen wir in diesen Fällen, Definitionen von (enthaltenen) DOM-Elementen mit fester Breite zu vermeiden (oder zu aktualisieren).

Zum Beispiel:

* Vorher:

   * `width=100px`

* Nachher:

   * `max-width=100px`

#### Größenanpassung und adaptive Bildkompatibilität {#resizing-and-adaptive-image-compliance}

Jede Änderung der Größe einer Komponente innerhalb des Rasters löst mindestens einen der folgende Listener aus:

* `beforeedit`
* `beforechildedit`
* `afteredit`
* `afterchildedit`

Um die Größe eines adaptiven Bildes in einem responsiven Raster ordnungsgemäß zu ändern und die Inhalte des Bildes zu aktualisieren, müssen Sie den Listener `afterEdit`, dessen Wert auf `REFRESH_PAGE` festgelegt ist, zur `EditConfig`-Datei aller enthaltenen Komponenten hinzufügen.

Zum Beispiel:

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

Der Mechanismus für adaptive Bilder wird über ein Skript zur Verfügung gestellt, das die Auswahl des richtigen Bildes für die aktuelle Fenstergröße steuert. Es wird aktiviert, wenn das DOM bereit ist oder ein dediziertes Ereignis empfangen wird. Derzeit muss die Seite aktualisiert werden, um das Ergebnis der Benutzeraktion korrekt widerzuspiegeln.

>[!CAUTION]
>
>Benutzerdefinierte Stylesheet-ClientLibs müssen als Teil der Kopfzeile geladen werden, damit sie in der Autoren und der Veröffentlichungsumgebung ordnungsgemäß funktionieren.

## Aktivieren der Layout-Container-Komponente für die Seite {#enable-the-layout-container-component-for-page}

Für ein effizientes responsives Layout muss die Inhaltsautorin bzw. der Inhaltsautor Instanzen der Layout-Container-Komponente auf die Seite ziehen können. Dies ist für die WKND-Beispiel-Site bereits aktiviert. Führen Sie diese Schritte aus, um Ihre eigene Site zu aktivieren.

### Aktivieren der Layout-Container-Komponente für die Seitenbearbeitung {#enable-the-layout-container-component-for-page-editing}

Damit Autorinnen und Autoren weitere responsive Raster zu den Inhaltsseiten hinzufügen können, müssen Sie die Layout-Container-Komponente für Ihre Seite aktivieren. Möglich ist dies über folgende Optionen:

* **Über die Autorenumgebung**: [Bearbeiten Sie Ihre Seitenvorlagen](/help/sites-cloud/authoring/page-editor/templates.md), um den Layout-Container für eine Seite zu aktivieren.
* **Komponentendefinition**: Nutzen Sie beim Definieren der Komponente `allowedComponent` oder ein Static Include.

### Konfigurieren des Rasters des Layout-Containers {#configure-the-grid-of-the-layout-container}

Sie können die Anzahl der verfügbaren Spalten für jede spezifische Instanz des Layout-Containers konfigurieren [indem Sie Ihre Seitenvorlagen bearbeiten](/help/sites-cloud/authoring/page-editor/templates.md).
