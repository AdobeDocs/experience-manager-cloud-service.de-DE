---
title: Stilsystem
description: Das Stilsystem ermöglicht es einem Vorlagenautor, in der Inhaltsrichtlinie für Komponenten Stilklassen festzulegen, die ein Inhaltsautor später bei der Bearbeitung der Komponente auf einer Seite auswählen kann. Diese Stile können alternative visuelle Varianten einer Komponente sein, um das Verfahren flexibler zu gestalten.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Stilsystem {#style-system}

Das Stilsystem ermöglicht es einem Vorlagenautor, in der Inhaltsrichtlinie für Komponenten Stilklassen festzulegen, die ein Inhaltsautor später bei der Bearbeitung der Komponente auf einer Seite auswählen kann. Diese Stile können alternative visuelle Varianten einer Komponente sein, um das Verfahren flexibler zu gestalten.

So muss nicht eigens für jeden Stil eine benutzerdefinierte Komponente entwickelt oder der Komponentendialog angepasst werden, um eine derartige Stilfunktionalität zu ermöglichen. Das Resultat sind mehr wiederverwendbare Komponenten, die schnell und einfach an die Bedürfnisse von Inhaltsautoren angepasst werden können, ohne dass eine AEM-Back-End-Entwicklung erforderlich ist.

## Nutzungsszenario {#use-case}

Vorlagenautoren müssen nicht nur die Funktionsweise der Komponenten für die Inhaltsautoren konfigurieren können, sondern auch eine Reihe alternativer visueller Varianten einer Komponente.

Genauso müssen Inhaltsautoren ihre Inhalte nicht nur strukturieren und anordnen können. Sie müssen auch auswählen können, wie der Inhalt visuell präsentiert wird.

Das Stilsystem bietet eine einheitliche Lösung für die Anforderungen des Vorlagenautors und des Inhaltsautors:

* Vorlagenautoren können in den Inhaltsrichtlinien für Komponenten Stilklassen festlegen.
* Inhaltsautoren können diese Klassen später aus einem Dropdown-Menü auswählen, wenn sie die Komponente auf einer Seite bearbeiten, um die jeweiligen Stile darauf anzuwenden.

Die Stilklasse wird daraufhin in das Decoration-Wrapper-Element der Komponente eingefügt, sodass sich der Komponentenentwickler nicht mit der Handhabung der Stile über die Bereitstellung der CSS-Regeln hinaus befassen muss.

## Überblick {#overview}

Die allgemeine Verwendung des Stilsystems sieht wie folgt aus.

1. Der Webdesigner erstellt unterschiedliche visuelle Varianten einer Komponente.
1. Dem HTML-Entwickler werden die HTML-Ausgabe der Komponenten sowie die zu implementierenden visuellen Varianten zur Verfügung übermittelt.
1. Der HTML-Entwickler definiert die CSS-Klassen, die jeder visuellen Variante entsprechen und in das Element eingefügt werden sollen, das die Komponenten umschließt.
1. Der HTML-Entwickler implementiert den entsprechenden CSS-Code (und optional JS-Code) für jede visuelle Variation, sodass sie wie definiert aussehen.
1. Der AEM-Entwickler legt den bereitgestellten CSS-Code (und optional JS-Code) in einer Client-Bibliothek ab und stellt ihn bereit. <!--The AEM developer places the provided CSS (and optional JS) in a [Client Library](/help/sites-developing/clientlibs.md) and deploys it.-->
1. Der AEM-Entwickler oder Vorlagenautor konfiguriert die Seitenvorlagen und bearbeitet die Richtlinie jeder formatierten Komponente, fügt die definierten CSS-Klassen hinzu, gibt benutzerfreundliche Namen zu jedem Stil und gibt an, welche Stile kombiniert werden können.
1. Der AEM-Seitenautor kann die entworfenen Stile daraufhin über das Stilmenü in der Symbolleiste einer Komponente im Seiten-Editor auswählen.

Beachten Sie, dass nur die letzten drei Schritte direkt in AEM ausgeführt werden. Das bedeutet, dass die gesamte erforderliche CSS- und JavaScript-Entwicklung ohne AEM durchgeführt werden kann.

Für die eigentliche Implementierung der Stile ist nur die Bereitstellung in AEM sowie die Auswahl innerhalb der Komponenten der gewünschten Vorlagen erforderlich.

Das folgende Diagramm stellt die Architektur des Stilsystems dar.

![Stil-Systemarchitektur](/help/sites-cloud/authoring/assets/style-system-architecture.png)

## Verwenden Sie:{#use}

Um die Funktion zu demonstrieren, müssen Stile für eine Komponente erstellt werden. Die folgenden Abschnitte [Als Inhaltsautor](#as-a-content-author) und [als Vorlagenautor](#as-a-template-author) beschreiben, wie die Funktionalität des Stilsystems unter Verwendung des Stilsystems verwendet werden kann, vorausgesetzt, Ihre Komponenten haben bereits Stile konfiguriert.

Wenn Sie das Stilsystem für Ihre eigenen Komponenten verwenden möchten, gehen Sie wie folgt vor:

1. Installieren Sie den CSS-Code als Client-Bibliotheken, wie im Abschnitt [Überblick](#overview) erklärt.
1. Konfigurieren Sie die CSS-Klassen, die Sie Ihren Inhaltsautoren zur Verfügung stellen möchten, wie im Abschnitt [Als Vorlagenautor](#as-a-template-author) beschrieben.
1. Inhaltsautoren können die Stile daraufhin wie im Abschnitt [Als Inhaltsautor](#as-a-content-author) beschrieben verwenden.

### Als Inhaltsautor {#as-a-content-author}

1. Bearbeiten Sie eine Seite mit einer Komponente, für die ein Stil konfiguriert ist.
1. Wählen Sie eine Komponente mit konfiguriertem Stil, wie z. B. die **List** -Komponente.

   ![Authoring-Stile](/help/sites-cloud/authoring/assets/style-system-author.png)

1. Tippen oder klicken Sie auf die Schaltfläche **Stile** in der Symbolleiste der Komponente **Liste**, um das Stilmenü zu öffnen und das Erscheinungsbild der Komponente zu bearbeiten.

   ![Erstellen von Stilen durch Auswahl von](/help/sites-cloud/authoring/assets/style-system-author-select.png)

   >[!NOTE]
   >
   >In this example, the **Layout** styles (**Block** and **Grid**) are mutually exclusive, while the **Display** options (**Image** or **Date**) can be combined. Dies kann [in der Vorlage durch den Vorlagenautor konfiguriert werden](#as-a-template-author).

### Als Vorlagenautor {#as-a-template-author}

1. Bearbeiten Sie beim Bearbeiten einer Inhaltsseite, für die Sie Stile konfigurieren möchten, die Vorlage der Seite über **Seiteninformationen -> Vorlage** bearbeiten.

   ![Vorlage bearbeiten](/help/sites-cloud/authoring/assets/style-system-template.png)

1. Bearbeiten Sie die Richtlinie der Komponente, für die Sie die Stile wie die **List** -Komponente konfigurieren möchten, indem Sie auf die Schaltfläche **Policy** der Komponente tippen oder klicken.

   ![Vorlagenkomponentenrichtlinie](/help/sites-cloud/authoring/assets/style-system-template-policy.png)

1. Auf der Registerkarte „Stile“ in den Eigenschaften können Sie sehen, wie die Stile konfiguriert wurden.

   ![Registerkarte &quot;Stile&quot;des Eigenschaftenfensters](/help/sites-cloud/authoring/assets/style-system-template-styles.png)

   * **Gruppenname:** Stile können im Stilmenü gruppiert werden, das dem Inhaltsautor angezeigt wird, während er den Stil einer Komponente konfiguriert.
   * **Stile können kombiniert werden:** Legt fest, dass mehrere Stile innerhalb einer Gruppe gleichzeitig ausgewählt werden können.
   * **Stilname:** Die Beschreibung des Stils, der dem Inhaltsautor bei der Konfiguration des Stils der Komponente angezeigt wird.
   * **CSS-Klassen:** Der tatsächliche Name der dem Stil zugeordneten CSS-Klasse.
   Ordnen Sie die Gruppen und die Stile innerhalb der Gruppen mit den Ziehpunkten. Nutzen Sie die Symbole „Hinzufügen“ oder „Löschen“, um Gruppen bzw. Stile innerhalb der Gruppen hinzuzufügen oder zu entfernen.

>[!CAUTION]
>
>The CSS classes (as well as any necessary Javascript) configured as style properties of a component&#39;s policy must be deployed as Client Libraries in order to work. <!-- The CSS classes (as well as any necessary Javascript) configured as style properties of a component's policy must be deployed as [Client Libraries](/help/sites-developing/clientlibs.md) in order to work.-->

## Einrichtung {#setup}

>[!NOTE]
>
>Version 2 der Kernkomponenten kann das Stilsystem vollständig nutzen. Dafür ist keine zusätzliche Konfiguration erforderlich.
>
>Führen Sie die nächsten Schritte aus, um das Stilsystem für Ihre eigenen benutzerdefinierten Komponenten zu aktivieren oder die Hauptkomponenten von Version 1 zu erweitern und die Funktion zu nutzen.

Damit eine Komponente mit dem Stilsystem von AEM verwendet werden kann und die Registerkarte „Stil“ im Dialogfeld „Design“ angezeigt wird, muss der Komponentenentwickler diese Registerkarte mit den folgenden Einstellungen für die Komponente miteinbeziehen:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_design/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

Ist die Komponente entsprechend konfiguriert, fügt AEM die von den Seitenautoren festgelegten Stile automatisch in den Decoration-Element-Wrapper ein, der automatisch auf alle bearbeitbaren Komponenten angewendet wird. Dafür ist keine weitere Aktion der Komponente erforderlich.

### Stile mit Elementnamen {#styles-with-element-names}

Mit der String-Array-Eigenschaft `cq:styleElements` können Entwickler auch eine Liste der zulässigen Elementnamen für Stile in der Komponente konfigurieren. In der Registerkarte „Stile“ für die Richtlinie im Dialogfeld „Design“ kann der Vorlagenautor außerdem Elementnamen auswählen, die für die einzelnen Stile festgelegt werden sollen. Dadurch wird der Elementname des Wrapper-Elements definiert.

This property is set on the `cq:Component` node. Beispiel:

* `/apps/wknd/components/content/contentfragment@cq:styleElements=[div,section,span]`

>[!CAUTION]
>
>Definieren Sie keine Elementnamen für Stile, die kombiniert werden können. Wenn mehrere Elementnamen definiert werden, gilt die folgende Prioritätsreihenfolge:
>
>1. HTL hat Vorrang vor allem: `data-sly-resource="${'path/to/resource' @ decorationTagName='span'}`
>1. Danach wird unter mehreren aktiven Stilen der erste Stil in der Liste der in der Komponentenrichtlinie konfigurierten Stile ausgewählt.
>1. Finally, the component&#39;s `cq:htmlTag`/ `cq:tagName` will be considered as a fallback value.
>



Die Fähigkeit, Stilnamen zu definieren, ist bei sehr generischen Komponenten wie dem Layout-Container oder der Inhaltsfragmentkomponente hilfreich, um diesen eine zusätzliche Bedeutung zu verleihen.

For instance it allows a Layout Container to be given semantics like `<main>`, `<aside>`, `<nav>`, etc.
