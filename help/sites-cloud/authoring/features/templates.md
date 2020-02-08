---
title: Erstellen von Seitenvorlagen
description: Eine Vorlage definiert die Struktur einer erstellten Seite und mit dem Vorlagen-Editor ist die Erstellung und Verwaltung von Vorlagen nicht mehr nur Entwicklern vorbehalten.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Erstellen von Seitenvorlagen {#creating-page-templates}

Wenn Sie eine Seite erstellen, müssen Sie eine Vorlage auswählen. Diese wird als Grundlage für die Erstellung der neuen Seite verwendet. Die Vorlage definiert die Struktur der Seite, anfängliche Inhalte und die Komponenten, die verwendet werden können.

Mit dem **Vorlagen-Editor** ist die Erstellung und Verwaltung von Vorlagen nicht mehr nur Entwicklern vorbehalten. Ein erfahrener Benutzer, ein so genannter **Vorlagenautor**, kann hinzugezogen werden. Entwickler werden weiterhin benötigt, um die Umgebung zu installieren und Client-Bibliotheken und die zu verwendenden Komponenten zu erstellen. Sobald dies jedoch erledigt ist, hat der **Vorlagenautor** die Möglichkeit, Vorlagen ohne ein Entwicklungsprojekt zu erstellen und zu konfigurieren.

Mit der **Vorlagenkonsole** können Vorlagenautoren:

* eine neue Vorlage erstellen oder eine vorhandene Vorlage kopieren 
* Verwalten Sie den Lebenszyklus der Vorlage.

Mit dem **Vorlagen-Editor** können Vorlagenautoren:

* Komponenten zur Vorlage hinzufügen und sie auf einem responsiven Raster positionieren
* die Komponenten vorkonfigurieren 
* definieren, welche Komponenten auf den Seiten bearbeitet werden können, die mit der Vorlage erstellt wurden

In diesem Dokument wird erklärt, wie ein **Vorlagenautor** die Vorlagenkonsole und den Vorlagen-Editor verwenden kann, um bearbeitbare Vorlagen zu erstellen und zu verwalten.

Ausführliche Informationen zur Funktionsweise von bearbeitbaren Vorlagen auf technischer Ebene finden Sie im Entwicklerdokument Bearbeitbare Seitenvorlagen. <!-- For detailed information about how editable templates work at a technical level, please see the developer document [Page Templates - Editable](/help/sites-developing/page-templates-editable.md) for more information.-->

>[!NOTE]
>
>Der **Vorlagen-Editor** unterstützt das Targeting nicht direkt auf der Vorlagenebene. Seiten, die auf der Grundlage einer bearbeitbaren Vorlage erstellt wurden, können als Ziel angegeben werden, aber die Vorlagen selbst nicht.

## Bevor Sie beginnen {#before-you-start}

>[!NOTE]
>
>Ein Administrator muss einen Vorlagenordner im **Konfigurationsbrowser** konfigurieren und entsprechende Berechtigungen anwenden, bevor ein Vorlagenautor eine Vorlage in diesem Ordner erstellen kann.

Bevor Sie beginnen, sollten Sie bedenken, dass die Erstellung einer neuen Vorlage Zusammenarbeit erfordert. Aus diesem Grunde wird für jede Aufgabe eine [Rolle](#roles) angezeigt. Dies hat keinen Einfluss darauf, wie Sie eine Vorlage tatsächlich zum Erstellen einer Seite verwenden, aber es hat auch Auswirkungen darauf, wie eine Seite mit der Vorlage verknüpft ist.

### Rollen {#roles}

Das Erstellen einer neuen Vorlage mit der **Vorlagenkonsole** und dem **Vorlagen-Editor** erfordert die Zusammenarbeit zwischen den folgenden Rollen:

* **Admin**:
   * Creates a new folder for templates requires `admin` rights.
   * Solche Aufgaben können oft von einem Entwickler übernommen werden.
* **Entwickler**:
   * Konzentriert sich auf technische/interne Details.
   * Muss Erfahrung mit der Entwicklungsumgebung haben. 
   * Versorgt den Vorlagenautor mit den erforderlichen Informationen. 
* **Vorlagenautor**:
   * This is a specific author who is member of the group `template-authors`
      * Weist die erforderlichen Berechtigungen zu. 
   * Kann die Verwendung von Komponenten und andere wichtige Einzelheiten konfigurieren, was Folgendes erfordert:
      * Einige technische Kenntnisse
         * Zum Beispiel bei der Verwendung von Mustern, wenn Pfade definiert werden.
      * Technische Informationen vom Entwickler.

Aufgrund der Natur einiger Aufgaben (etwa dem Erstellen eines Ordners) ist eine Entwicklungsumgebung erforderlich, für die wiederum Wissen/Erfahrung benötigt wird.

Die im vorliegenden Dokument beschriebenen Aufgaben sind zusammen mit der Rolle der Person aufgeführt, die für die Ausführung der Aufgaben verantwortlich ist.

## Erstellen und Verwalten von Vorlagen {#creating-and-managing-templates}

Gehen Sie zum Erstellen einer neuen bearbeitbaren Vorlage wie folgt vor:

* Verwenden Sie die **Vorlagenkonsole**, die im Bereich **Allgemein** der Konsole **Werkzeuge** verfügbar ist.
   * Oder direkt unter: `https://<host>:<port>/libs/wcm/core/content/sites/templates.html/conf`
* Can [create a folder for the templates](#creating-a-template-folder-admin) if necessary
* [Erstellen Sie eine neue Vorlage](#creating-a-new-template-template-author), die anfangs leer ist. 
* [Definieren Sie bei Bedarf weitere Eigenschaften](#defining-template-properties-template-author) für die Vorlage.
* [Bearbeiten Sie die Vorlage](#editing-templates-template-authors), um Folgendes zu definieren:
   * [Struktur](#editing-a-template-structure-template-author) : Vordefinierter Inhalt, der auf Seiten, die mit der Vorlage erstellt wurden, nicht geändert werden kann.
   * [Anfänglicher Inhalt](#editing-a-template-initial-content-author) - Vordefinierter Inhalt, der auf mit der Vorlage erstellten Seiten geändert werden kann.
   * [Layout](#editing-a-template-layout-template-author) - Für eine Reihe von Geräten.
   * [Stile](/help/sites-cloud/authoring/features/style-system.md) – zum Definieren der Stile für die Vorlage und ihre Komponenten.
* [Aktivieren Sie die Vorlage](#enabling-a-template-template-author) zur Verwendung, wenn Sie eine Seite erstellen.
* [Lassen die Vorlage zu](#allowing-a-template-author), damit sie für die erforderliche Seite oder die Verzweigung Ihrer Website verwendet werden kann.
* [Veröffentlichen Sie die Vorlage](#publishing-a-template-template-author), um sie in der Veröffentlichungsumgebung bereitzustellen.

>[!NOTE]
>
>Die **zugelassenen Vorlagen** werden häufig vordefiniert, wenn Ihre Website erstmals eingerichtet wird.

>[!CAUTION]
>
>Geben Sie in eine Vorlage nie Informationen ein, die internationalisiert werden müssen. <!-- Never enter any information that needs to be [internationalized](/help/sites-developing/i18n.md) into a template.-->
>
>Bei Vorlagenelementen wie Kopf- und Fußzeilen, die lokalisiert werden müssen, sollten Sie die [Lokalisierungsfunktionen der Hauptkomponenten nutzen.](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/localization.html)

### Erstellen eines Vorlagenordners – Administrator {#creating-a-template-folder-admin}

Für Ihr Projekt sollte ein Vorlagenordner für Ihre projektspezifischen Vorlagen erstellt werden. Dies ist eine Administratoraufgabe, die im Dokument Bearbeitbare Seitenvorlagen<!-- A template folder should be created for your project to hold your project-specific templates. This is an admin task and is described in the document [Page Templates - Editable](/help/sites-developing/page-templates-editable.md#template-folders).--> beschrieben wird. 

### Erstellen einer neuen Vorlage – Vorlagenautor {#creating-a-new-template-template-author}

1. Open the **Templates Console** (via **Tools ->** **General**) then navigate to the required folder.

   >[!NOTE]
   >
   >In einer Standard-AEM-Instanz ist der Ordner **Global** bereits in der Vorlagen-Konsole vorhanden. Er enthält Standardvorlagen und dient als Ausweichlösung, wenn keine Richtlinien und/oder Vorlagentypen im aktuellen Ordner gefunden werden.
   >
   >Es wird das bewährte Verfahren empfohlen, einen für Ihr Projekt erstellten Vorlagenordner zu verwenden. <!-- It is recommended best practice to use a [template folder created for your project](/help/sites-developing/page-templates-editable.md#template-folders).-->

1. Wählen Sie **Erstellen** und anschließend **Vorlage erstellen**, um den Assistenten zu öffnen.

1. Wählen Sie eine **Vorlagenart** aus und klicken Sie dann auf **Weiter**.

   >[!NOTE]
   >
   >Vorlagenarten sind vordefinierte Vorlagen, die als Vorlagen für eine Vorlage betrachtet werden können. Sie werden von Entwicklern oder vom Systemadministrator vordefiniert. Weitere Informationen finden Sie im Entwicklerdokument Seitenvorlagen – Bearbeitbar. <!-- More information can be found in the developer document [Page Templates - Editable](/help/sites-developing/page-templates-editable.md#template-type).-->

1. Stellen Sie die **Vorlagendetails** fertig:

   * **Vorlagenname**
   * **Beschreibung**

1. Wählen Sie **Erstellen**. Eine Bestätigung wird angezeigt. Wählen Sie **Öffnen**, um die Vorlage zu bearbeiten oder **Fertig**, um zur Vorlagen-Konsole zurückzukehren.

   >[!NOTE]
   >
   >Wenn eine neue Vorlage erstellt wird, wird sie in der Konsole als **Entwurf** markiert, was bedeutet, dass sie noch nicht für Seitenautoren zur Verfügung steht.

### Definieren von Vorlageneigenschaften – Vorlagenautor {#defining-template-properties-template-author}

Eine Vorlage kann die folgenden Eigenschaften haben:

* Bild
   * Bild, das als [Miniaturansicht der Vorlage verwendet wird](#template-thumbnail-image), um die Auswahl zu vereinfachen, beispielsweise im Seitenerstellungsassistenten.
      * Kann hochgeladen werden
      * Kann auf der Grundlage des Vorlageninhalts generiert werden
* Titel
   * Ein Titel zum Identifizieren der Vorlage, beispielsweise im **Seitenerstellungsassistenten**.
* Beschreibung
   * An optional description to provide more information about the template and its use, which can be seen for example in the **Create Page** wizard.

So zeigen Sie die Eigenschaften an bzw. bearbeiten sie:

1. In the **Templates Console**, select the template.
1. Wählen Sie **Eigenschaften anzeigen** in der Symbolleiste oder in den Schnelloptionen aus, um das Dialogfeld zu öffnen.
1. Jetzt können Sie die Vorlageneigenschaften anzeigen oder bearbeiten.

>[!NOTE]
>
>Der Status einer Vorlage („Entwurf“, „Aktiviert“ oder „Deaktiviert“), wird in der Konsole angezeigt. 

#### Vorlagenminiaturbild {#template-thumbnail-image}

So definieren Sie eine Vorlagenminiatur:

1. Bearbeiten Sie die Vorlageneigenschaften.
1. Wählen Sie, ob Sie eine Miniatur hochladen oder aus dem Vorlageninhalt erstellen möchten.
   * Wenn Sie eine Miniatur hochladen möchten, klicken oder tippen Sie auf **Bild hochladen**
   * Wenn Sie eine Miniatur erzeugen möchten, klicken oder tippen Sie auf **Vorschau generieren** 
1. Bei beiden Methoden wird eine Vorschau der Miniatur angezeigt.
   * Wenn Sie mit dem Ergebnis nicht zufrieden sind, klicken oder tippen Sie auf **Löschen**, um ein anderes Bild hochzuladen oder die Miniatur neu zu erzeugen.
1. Wenn Sie mit der Miniatur zufrieden sind, klicken oder tippen Sie auf **Speichern und schließen**.

### Aktivieren und Zulassen einer Vorlage – Vorlagenautor {#enabling-and-allowing-a-template-template-author}

Um beim Erstellen einer Seite eine Vorlage zu verwenden, gehen Sie wie folgt vor:

* [Aktivieren Sie die Vorlage](#enabling-a-template-template-author) , damit sie beim Erstellen von Seiten zur Verfügung steht.
* [Zulassen, dass die Vorlage](#allowing-a-template-author) die Inhaltsverzweigungen angibt, in denen die Vorlage verwendet werden kann.

#### Aktivieren einer Vorlage – Vorlagenautor {#enabling-a-template-template-author}

Eine Vorlage kann aktiviert oder deaktiviert werden, um sie im Assistenten **Seite erstellen** verfügbar bzw. nicht verfügbar zu machen.

>[!CAUTION]
>
>Sobald eine Vorlage aktiviert ist, wird eine Warnmeldung angezeigt, wenn ein Autor beginnt, die Vorlage weiter zu aktualisieren. Diese dient dazu, den Benutzer zu informieren, dass die Vorlage referenziert wird und damit sämtliche Änderungen die die Vorlage referenzierenden Seiten beeinträchtigen könnten.

1. In the **Templates Console**, select the template.
1. Select **Enable** or **Disable** from the toolbar, and again in the confirmation dialog.
1. Sie können Ihre Vorlage jetzt verwenden, wenn Sie [eine neue Seite erstellen](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page), oder [die Vorlage bearbeiten](#editing-templates-template-authors), um sie an Ihre Anforderungen anzupassen.

>[!NOTE]
>
>Der Status einer Vorlage („Entwurf“, „Aktiviert“ oder „Deaktiviert“), wird in der Konsole angezeigt. 

#### Zulassen einer Vorlage – Autor {#allowing-a-template-author}

Eine Vorlage kann für bestimmte Seitenverzweigungen verfügbar oder nicht verfügbar gemacht werden.

1. Öffnen Sie die [Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md) für die Stammseite der Verzweigung, in der die Vorlage verfügbar sein soll.
1. Öffnen Sie die Registerkarte **Erweitert**.
1. Under **Template Settings** use **Add field** to specify the path(s) to your template(s).

   Der Pfad kann explizit sein oder Muster verwenden. Ein Beispiel:

   `/conf/<your-folder>/settings/wcm/templates/.*`

   Die Reihenfolge der Pfade ist irrelevant, da sämtliche Pfade überprüft und alle Vorlagen abgerufen werden.

   >[!NOTE]
   >
   >Wenn die Liste **Zugelassene Vorlagen** leer ist, wird die Struktur weiter durchsucht, bis ein Wert/eine Liste gefunden wird.
   >
   >
   >See Template Availability - the principles for allowed templates remain the same. <!--See [Template Availability](/help/sites-developing/templates.md#template-availability) - the principles for allowed templates remain the same.-->

1. Klicken Sie auf **Speichern**, um die Änderungen an den Seiteneigenschaften zu speichern.

>[!NOTE]
>
>Häufig werden die zugelassenen Vorlagen für Ihre gesamte Site vordefiniert, wenn sie eingerichtet ist.

### Veröffentlichen einer Vorlage – Vorlagenautor {#publishing-a-template-template-author}

Da die Vorlage referenziert wird, wenn eine Seite dargestellt wird, muss die voll konfigurierte Vorlage veröffentlicht werden, damit sie in der Veröffentlichungsumgebung verfügbar ist.

1. In the **Templates Console**, select the template.
1. Wählen Sie **Veröffentlichen** in der Symbolleiste, um den Assistenten zu öffnen.
1. Wählen Sie die **Inhaltsrichtlinien**, die mitveröffentlicht werden sollen.
1. Wählen Sie **Veröffentlichen** in der Symbolleiste, um den Vorgang abzuschließen.

## Bearbeiten von Vorlagen  – Vorlagenautoren {#editing-templates-template-authors}

Beim Erstellen oder Bearbeiten einer Vorlage können Sie diverse Aspekte definieren. Das Bearbeiten von Vorlagen ähnelt dem Erstellen von Seiten.

Mit der Auswahl **Modus** in der Symbolleiste können Sie die jeweiligen Aspekte der Vorlage auswählen und bearbeiten:

* [Struktur](#editing-a-template-structure-template-author)
* [Anfänglicher Inhalt](#editing-a-template-initial-content-author)
* [Layout](#editing-a-template-layout-template-author)

![Vorlageneditormodus-Auswahl](/help/sites-cloud/authoring/assets/templates-mode.png)

Mit der Option **Seitenrichtlinie** im Menü **Seiteninformationen** können Sie [die erforderlichen Seitenrichtlinien auswählen](#page-policies):

![Seiteninformationen zum Vorlageneditor](/help/sites-cloud/authoring/assets/templates-page-information.png)

>[!CAUTION]
>
>Wenn ein Autor beginnt, eine bereits aktivierte Vorlage zu bearbeiten, wird eine Warnmeldung angezeigt. Diese dient dazu, den Benutzer zu informieren, dass die Vorlage referenziert wird und damit sämtliche Änderungen die die Vorlage referenzierenden Seiten beeinträchtigen könnten.

### Vorlagenattribute {#template-attributes}

Die folgenden Attribute einer Vorlage können bearbeitet werden:

#### Struktur {#template-structure}

Components added to the [structure](#editing-a-template-structure-template-author) cannot be moved/removed from resultant pages by the page authors. Wenn Seitenautoren in der Lage sein sollen, neue Komponenten zu resultierenden Seiten hinzuzufügen und daraus zu entfernen, müssen Sie der Vorlage ein Absatzsystem hinzufügen.

Wenn Komponenten gesperrt sind, können Sie Inhalte hinzufügen, die nicht von den Seitenautoren bearbeitet werden können. Sie können Komponenten entsperren, damit Sie [anfänglichen Inhalt](#editing-a-template-initial-content-author) definieren können.

>[!NOTE]
>
>Im Strukturmodus können Komponenten, die einer nicht gesperrten Komponente übergeordnet sind, nicht verschoben, ausgeschnitten oder gelöscht werden.

#### Anfänglicher Inhalt {#template-initial-content}

When a component has been unlocked you can define the [initial content](#editing-a-template-initial-content-author) that will be copied to the resultant page(s), created from the template. Diese entsperrten Komponenten können auf den resultierenden Seiten bearbeitet werden.

>[!NOTE]
>
>Im Modus **Anfänglicher Inhalt** und auf den resultierenden Seiten können alle entsperrten Komponenten, bei denen übergeordnete Elemente verfügbar sind (z. B. Komponenten in einem Layout-Container), gelöscht werden.

#### Layout {#template-layout}

With the [layout](#editing-a-template-layout-template-author) you can predefine the template layout for the required device formats. Der Modus **Layout** für das Erstellen von Vorlagen bietet dieselben Funktionen wie der Modus [**Layout **für das Erstellen von Seiten](/help/sites-cloud/authoring/features/responsive-layout.md#defining-layouts-layout-mode).

#### Seitenrichtlinien {#template-page-policies}

[Seitenrichtlinien](#page-policies) können vordefinierte Seitenrichtlinien mit der Seite verbinden. Diese Seitenrichtlinien definieren die verschiedenen Designkonfigurationen.

#### Stile {#template-styles}

The [Style System](/help/sites-cloud/authoring/features/style-system.md) allows a template author to define style classes in the content policy of a component so that a content author is able to select them when editing the component on a page. Diese Stile können alternative visuelle Varianten einer Komponente sein, um das Verfahren flexibler zu gestalten.

Weitere Informationen finden Sie in der [Dokumentation für das Stilsystem](/help/sites-cloud/authoring/features/style-system.md).

### Bearbeiten einer Vorlage – Struktur – Vorlagenautor {#editing-a-template-structure-template-author}

In **Structure** mode you define components and content for your template and define policy for the template and its components.

* Komponenten, die in der Vorlagenstruktur definiert sind, können auf resultierenden Seiten nicht verschoben oder gelöscht werden.
* Wenn Seitenautoren die Möglichkeit haben sollen, Komponenten hinzuzufügen und zu entfernen, fügen Sie der Vorlage ein Absatzsystem hinzu.
* Komponenten können entsperrt und erneut gesperrt werden, damit Sie den [anfänglichen Inhalt](#editing-a-template-initial-content-author) definieren können.
* Die Designrichtlinien für die Komponenten und die Seite werden definiert.

![Seitenstruktur des Vorlageneditors](/help/sites-cloud/authoring/assets/templates-page-structure.png)

Es gibt eine Reihe von Aktionen, die Sie im **Strukturierungsmodus** des Vorlageneditors ausführen können, sowie eine Reihe von Funktionen, die Sie unterstützen:

#### Add Components {#add-components}

Es gibt verschiedene Möglichkeiten, Komponenten zur Vorlage hinzuzufügen:

* aus dem **Komponenten**-Browser im Seitenbereich
* By using the **Insert Component** option available on the toolbar of components already on the template or the **Drag components here** box.
* durch das Ziehen eines Assets (aus dem **Assets**-Browser im Seitenbereich) direkt auf die Vorlage, um die entsprechende Komponente dort zu generieren

Sobald sie hinzugefügt wurde, wird jede Komponente markiert mit:

* einem Rand
* einer Markierung, die den Komponententyp zeigt
* einer Markierung, die anzeigt, ob die Komponente entsperrt ist

>[!NOTE]
>
>When you add an out-of-the-box **Title** component to the template it will contain the default text **structure**.
>
>Wenn Sie diesen ändern und Ihren eigenen Text einfügen, wird dieser aktualisierte Text verwendet, wenn eine Seite aus der Vorlage erstellt wird.
>
>Wenn Sie den Standardtext (Struktur) nicht ändern, wird der Titel standardmäßig mit dem Namen der nachfolgenden Seite benannt.

>[!NOTE]
>
>Although not identical, adding components and assets to a template has many similarities to similar actions when [page authoring](/help/sites-cloud/authoring/fundamentals/editing-content.md).

#### Komponenten-Aktionen{#component-actions} 

Arbeiten Sie mit den Komponenten, nachdem sie zur Vorlage hinzugefügt wurden. Jede einzelne Instanz enthält eine Symbolleiste, mit der Sie auf die verfügbaren Aktionen zugreifen können. Die Symbolleiste ist abhängig von der Art der Komponente.

![Aktionsleiste einer Vorlagenkomponente](/help/sites-cloud/authoring/assets/templates-component-actions.png)

Sie kann auch von durchgeführten Aktionen abhängig sein. Wenn z. B. eine Richtlinie mit der Komponente verbunden wurde, ist das Designkonfigurationssymbol verfügbar.

#### Bearbeiten und Konfigurieren {#edit-and-configure}

Mit diesen zwei Aktionen können Sie Inhalte zu Ihren Komponenten hinzufügen.

#### Border to Indicate Structure {#border-to-indicate-structure}

Wenn Sie im Modus **Struktur** arbeiten, zeigt ein orangefarbener Rand die derzeit ausgewählte Komponente an. Außerdem zeigt eine gepunktete Linie die übergeordnete Komponente an.

#### Richtlinie und Eigenschaften (Allgemein) {#policy-and-properties-general}

Die Richtlinien für Inhalt (oder Design) definieren die Entwurfseigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

Erstellen Sie für eine Komponente eine Inhaltsrichtlinie oder wählen Sie eine vorhandene.

![Schaltfläche &quot;Inhaltsrichtlinie&quot;](/help/sites-cloud/authoring/assets/templates-content-policy-button.png)

Damit können Sie die Designdetails definieren.

![Inhaltsrichtlinie](/help/sites-cloud/authoring/assets/template-content-policy.png)

Das Konfigurationsfenster ist in zwei Hälften geteilt.

* In the left side of the dialogue under **Policy**, you have the ability to select an existing policy or select an existing one.
* In the right side of the dialogue under **Properties**, you can set the properties specific to the component type.

Die verfügbaren Eigenschaften sind von der ausgewählten Komponente abhängig. Beispielsweise definieren die Eigenschaften bei einer Textkomponente u. a. die Optionen „Kopieren“ und „Einfügen“, Formatierungsoptionen und das Absatzformat.

##### Richtlinie {#policy}

Die Richtlinien für Inhalt (oder Design) definieren die Entwurfseigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

Under **Policy** you can select an existing policy to apply to the component via the drop-down.

![Richtlinie auswählen](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

Sie können eine neue Richtlinie hinzufügen, indem Sie auf die Schaltfläche „Hinzufügen“ klicken, die sich neben dem Dropdown-Menü **Richtlinie auswählen** befindet. A new title should then be given in the **Policy Title** field.

![Schaltfläche &quot;Richtlinie hinzufügen&quot;](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

Die im Dropdown-Menü **Richtlinie auswählen** ausgewählte vorhandene Richtlinie kann mithilfe der Schaltfläche „Kopieren“, die sich neben dem Dropdown-Menü befindet, kopiert werden. A new title should then be given in the **Policy Title** field. By default the copied policy will be titled **Copy of X**, where X is the title of the copied policy.

![Schaltfläche &quot;Richtlinie kopieren&quot;](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

Eine Beschreibung der Richtlinie im Feld **Richtlinienbeschreibung** ist optional.

In the **Other templates also using the selected policy** section, you can easily see which other templates use the policy selected in the **Select policy** dropdown.

![Nutzung der vorhandenen Richtlinie](/help/sites-cloud/authoring/assets/templates-policy-use.png)

>[!NOTE]
>
>Wenn mehrere Komponenten des gleichen Typs als anfänglicher Inhalt hinzugefügt werden, gilt für alle Komponenten dieselbe Richtlinie.

##### Eigenschaften {#properties}

Unter der Überschrift **Eigenschaften** können Sie die Einstellungen der Komponente definieren. Die Überschrift hat zwei Registerkarten:

* Haupt
* Funktionen

###### Haupt {#main}

Auf der Registerkarte **Haupt** sind die wichtigsten Einstellungen der Komponente definiert.

Beispielsweise kann die zulässige Breite für eine Bildkomponente zusammen mit der Aktivierung des „Lazy Loading“ (Langsames Laden) definiert werden.

Wenn eine Einstellung mehrere Konfigurationen erlaubt, klicken oder tippen Sie auf die Schaltfläche **Hinzufügen**, um eine weitere Konfiguration hinzuzufügen.

![Schaltfläche &quot;Hinzufügen&quot;](/help/sites-cloud/authoring/assets/templates-add-button.png)

Um eine Konfiguration zu entfernen, klicken oder tippen Sie auf die Schaltfläche **Löschen**, die sich rechts neben der Konfiguration befindet.

Um eine Konfiguration zu entfernen, klicken oder tippen Sie auf die Schaltfläche **Löschen**.

![Schaltfläche „Löschen“](/help/sites-cloud/authoring/assets/templates-delete-button.png)

###### Funktionen {#features}

Die Registerkarte **Funktionen** erlaubt es Ihnen, zusätzliche Funktionen der Komponente zu aktivieren oder zu deaktivieren.

Sie können zum Beispiel für eine Bildkomponente die Beschneidungsproportionen, die erlaubten Bildausrichtungen und die erlaubten Uploads definieren.

![Registerkarte &quot;Funktionen&quot;](/help/sites-cloud/authoring/assets/templates-features-tab.png)

>[!CAUTION]
>
>Note that in AEM crop ratios are defined as **height/width**. Dies unterscheidet sich von der herkömmlichen Definition als Breite/Höhe und erfolgt aus Gründen der Legacy-Kompatibilität. Die Benutzer, die die Seite erstellen, bemerken keinen Unterschied, vorausgesetzt, dass Sie den **Namen** klar definieren, da dieser auf der Benutzeroberfläche angezeigt wird.

>[!NOTE]
>
>Inhalt-Richtlinien für Komponenten, die den Rich-Text-Editor implementieren, können nur für Optionen definiert werden, die vom RTE über die UI-Einstellungen bereitgestellt werden. <!--[Content policies for components implementing the rich text editor](/help/sites-administering/rich-text-editor.md#main-pars-header-206036638) can only be defined for options made available by the RTE through its UI settings.-->

#### Policy and Properties (Layout Container) {#policy-and-properties-layout-container}

Die Richtlinien und Eigenschafteneinstellungen eines Layout-Containers sind der allgemeinen Verwendung ähnlich, es gibt aber einige Abweichungen.

>[!NOTE]
>
>Das Konfigurieren einer Richtlinie ist für Container-Komponenten obligatorisch, da Sie dadurch die Komponenten definieren können, die im Container zur Verfügung stehen.

Das Konfigurationsfenster ist in zwei Hälften geteilt, ebenso wie bei der allgemeinen Verwendung des Fensters.

##### Richtlinie {#policy-layout}

Die Richtlinien für Inhalt (oder Design) definieren die Entwurfseigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

Under **Policy** you can select an existing policy to apply to the component via the drop-down. Dies funktioniert ebenso wie bei der allgemeinen Verwendung des Fensters.

##### Eigenschaften {#properties-layout}

Unter der Überschrift **Eigenschaften** können Sie auswählen, welche Komponenten für den Layout-Container verfügbar sein sollen, und Sie können die Einstellungen der Komponenten definieren. Die Überschrift hat drei Registerkarten:

* Zugelassene Komponenten
* Standardkomponenten
* Responsive Einstellungen

###### Zugelassene Komponenten {#allowed-components}

Auf der Registerkarte **Zugelassene Komponenten** definieren Sie, welche Komponenten für den Layout-Container verfügbar sein sollen.

* Die Komponenten werden anhand ihrer Komponentengruppen gruppiert, die sich ein- und ausblenden lassen.
* Eine gesamte Gruppe kann durch Aktivieren des Gruppennamens ausgewählt werden und die Auswahl kann durch Deaktivieren aufgehoben werden.
* Ein Minuszeichen zeigt an, dass mindestens eines, aber nicht alle Elemente in einer Gruppe ausgewählt sind.
* Eine Suche zum Filtern einer Komponente nach Name ist verfügbar.
* Die rechts neben dem Namen der Komponentengruppe aufgelisteten Werte stellen die Gesamtanzahl der ausgewählten Komponenten in diesen Gruppen dar (unabhängig vom Filter).

![Zulässige Komponenten, Registerkarte](/help/sites-cloud/authoring/assets/templates-allowed-components-tab.png)

###### Standardkomponenten {#default-components}

Auf der Registerkarte **Standardkomponenten** definieren Sie, welche Komponenten automatisch bestimmten Medientypen zugeordnet werden sollen, damit AEM weiß, welche Komponente zuzuordnen ist, wenn ein Autor ein Asset aus dem Asset-Browser zieht. Beachten Sie, dass nur Komponenten mit Ablagebereichen für eine solche Konfiguration verfügbar sind.

Klicken oder tippen Sie auf **Zuordnung hinzufügen**, um eine völlig neue Komponente und MIME-Typ-Zuordnung hinzuzufügen.

Wählen Sie in der Liste eine Komponente aus und klicken oder tippen Sie auf **Typ hinzufügen**, um einen zusätzlichen MIME-Typ einer bereits zugeordneten Komponente hinzuzufügen. Click the **Delete** icon to remove a MIME type.

![Registerkarte &quot;Standardkomponenten&quot;](/help/sites-cloud/authoring/assets/templates-default-components-tab.png)

###### Responsive Einstellungen {#responsive-settings}

Auf der Registerkarte **Responsive Einstellungen** können Sie die Anzahl der Spalten im resultierenden Raster des Layout-Containers konfigurieren.

#### Komponenten entsperren und sperren {#unlock-and-lock-components}

Komponenten werden entsperrt/gesperrt, um festzulegen, ob der Inhalt im Modus **anfänglicher Inhalt** geändert werden darf.

Wenn eine Komponente entsperrt wurde:

* wird am Rand ein offenes Vorhängeschloss angezeigt
* wird die Symbolleiste der Komponente entsprechend angepasst
* Bereits eingegebener Inhalt wird nicht mehr im **Strukturmodus** angezeigt.
   * Already entered content is considered initial content and is only visible in **Initial Content** mode.
* Die Komponenten, die der entsperrten Komponente übergeordnet sind, können nicht verschoben, ausgeschnitten oder gelöscht werden.

![Schaltfläche &quot;Komponente sperren&quot;](/help/sites-cloud/authoring/assets/templates-unlock-component.png)

Das gilt auch für das Entsperren von Container-Komponenten, damit weitere Komponenten hinzugefügt werden können, entweder im Modus **Anfänglicher Inhalt** oder auf resultierenden Seiten. Wenn Sie bereits Komponenten/Inhalte zum Container hinzugefügt haben, bevor Sie ihn entsperrt haben, werden diese nicht mehr im **Strukturmodus** angezeigt, aber sie werden im Modus **Anfänglicher Inhalt** angezeigt. Im **Strukturmodus** wird nur die Container-Komponente selbst und die zugehörige Liste der **zugelassenen Komponenten** angezeigt. 

![Zugelassene Komponenten](/help/sites-cloud/authoring/assets/templates-allowed-components.png)

Um Platz zu sparen, wird der Layout-Container nicht an die Liste der zulässigen Komponenten angepasst. Stattdessen wird der Container zu einer bildlauffähigen Liste.

Konfigurierbare Komponenten werden mit einem **Richtliniensymbol** angezeigt, auf das getippt oder geklickt werden kann, um die Richtlinie und die Eigenschaften der Komponente zu bearbeiten.

![Symbol &quot;Konfigurierbare Komponente&quot;](/help/sites-cloud/authoring/assets/templates-configurable-component.png)

#### Beziehung zu vorhandenen Seiten {#relationship-to-existing-pages}

Auf diesen Seiten werden die Änderungen an der Vorlage widergespiegelt, wenn die Struktur aktualisiert wird, nachdem die Seiten auf der Grundlage der Vorlage erstellt wurden. In der Symbolleiste wird eine Warnung mit einem Bestätigungsdialog angezeigt, um Sie an diese Tatsache zu erinnern. 

![Bannerwarnung, dass die Vorlage verwendet wird](/help/sites-cloud/authoring/assets/templates-in-use-banner.png)

### Bearbeiten einer Vorlage – Anfänglicher Inhalt – Autor {#editing-a-template-initial-content-author}

Der Modus **Anfänglicher Inhalt** wird für definierten Inhalt verwendet, der angezeigt wird, wenn eine Seite anfänglich auf der Grundlage einer Vorlage erstellt wird. Der anfängliche Inhalt kann dann von Seitenautoren bearbeitet werden.

Obwohl der gesamte Inhalt, der im Modus **Struktur** erstellt wird, im Modus **Anfänglicher Inhalt** sichtbar ist, können nur entsperrte Komponenten ausgewählt und bearbeitet werden.

>[!NOTE]
>
>Der Modus **Anfänglicher Inhalt** kann als Bearbeitungsmodus für Seiten betrachtet werden, die mit dieser Vorlage erstellt werden. Daher sind Richtlinien nicht im Modus **Anfänglicher Inhalt**, sondern im [**Strukturmodus **definiert](#editing-a-template-structure-template-author).

* Entsperrte Komponenten, die bearbeitet werden können, werden hervorgehoben. Werden sie ausgewählt, erhalten sie einen blauen Rand:

   ![Anfänglicher Inhaltsmodus](/help/sites-cloud/authoring/assets/templates-initial-content-mode.png)

* Entsperrte Komponenten haben eine Symbolleiste, mit der Sie den Inhalt bearbeiten und konfigurieren können:

   ![Ungesperrte Komponente](/help/sites-cloud/authoring/assets/templates-unlocked-components.png)

* Wenn eine Container-Komponente (im Modus **Struktur**) entsperrt wurde, können Sie neue Komponenten zum Container hinzufügen (im Modus **Anfänglicher Inhalt).** Komponenten, die im Modus **Anfänglicher Inhalt** hinzugefügt werden, können auf resultierende Seiten verschoben oder von diesen gelöscht werden.

   Sie können Komponenten über den Bereich **Komponenten hierher ziehen** oder mithilfe der Option **Neue Komponente einfügen** in der Symbolleiste des jeweiligen Containers hinzufügen.

   ![Komponente hinzufügen](/help/sites-cloud/authoring/assets/templates-add-component.png)
   ![Komponente hinzufügen](/help/sites-cloud/authoring/assets/templates-add-component-dialog.png)

* Wenn der anfängliche Inhalt der Vorlage aktualisiert wird, nachdem Seiten auf der Grundlage der Vorlage erstellt wurden, wirken sich die Änderungen am anfänglichen Inhalt der Vorlage nicht auf diese Seiten aus. 

>[!NOTE]
>
>Der ursprüngliche Inhalt dient zum Vorbereiten von Komponenten und dem Seitenlayout, die als Ausgangspunkt für die Erstellung des Inhalts dienen. Dies soll nicht der eigentliche Inhalt sein, der unverändert bleibt. Aus diesem Grund kann der anfängliche Inhalt nicht übersetzt werden.
>
>Wenn Sie übersetzbaren Text in Ihre Vorlage aufnehmen müssen, z. B. in Kopf- oder Fußzeilen, können Sie die [Lokalisierungsfunktionen der Hauptkomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/localization.html)verwenden.

### Bearbeiten einer Vorlage – Layout – Vorlagenautor {#editing-a-template-layout-template-author}

Sie können das Vorlagenlayout für verschiedene Geräte definieren. [Responsives Layout funktioniert für Vorlagen ebenso wie für die Seitenbearbeitung.](/help/sites-cloud/authoring/features/responsive-layout.md)

>[!NOTE]
>
>Änderungen am Layout werden im Modus **Anfänglicher Inhalt** widergespiegelt, doch im **Strukturmodus** sind keine Änderungen zu sehen.

![Bearbeiten des Vorlagenlayouts](/help/sites-cloud/authoring/assets/templates-edit-layout.png)

### Editing a Template - Page Policy - Template Author/Developer {#editing-a-template-page-policy-template-author-developer}

Die Seitenrichtlinie einschließlich der erforderlichen clientseitigen Bibliotheken wird unter der Option **Seitenrichtlinie** im Menü **Seiteninformationen** beibehalten.

To access the **Page Policy** dialog:

1. From the **Template Editor**, select **Page Information** from the toolbar, then **Page Policy** to open the dialog.
1. The **Page Policy** dialog opens and is divided into two sections:

   * Die linke Hälfte definiert die [Seitenrichtlinien](#page-policies). 
   * Die rechte Hälfte definiert die [Seiteneigenschaften](#page-properties). 
   ![Seitenentwurf](/help/sites-cloud/authoring/assets/templates-page-design.png)

#### Seitenrichtlinien {#page-policies}

Sie können eine Inhaltsrichtlinie auf die Vorlage oder resultierende Seiten anwenden. So wird die Inhaltsrichtlinie für das Hauptabsatzsystem auf der Seite definiert.

![Seitenrichtlinie](/help/sites-cloud/authoring/assets/templates-page-policy.png)

* Sie können eine vorhandene Richtlinie für die Seite im Dropdown-Menü **Richtlinie auswählen** auswählen.

   ![Richtlinienselektor](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

   Sie können eine neue Richtlinie hinzufügen, indem Sie auf die Schaltfläche „Hinzufügen“ klicken, die sich neben dem Dropdown-Menü **Richtlinie auswählen** befindet. A new title should then be given in the **Policy Title** field.

   ![Schaltfläche &quot;Richtlinie hinzufügen&quot;](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

   Die im Dropdown-Menü **Richtlinie auswählen** ausgewählte vorhandene Richtlinie kann mithilfe der Schaltfläche „Kopieren“, die sich neben dem Dropdown-Menü befindet, kopiert werden. A new title should then be given in the **Policy Title** field. By default the copied policy will be titled **Copy of X**, where X is the title of the copied policy.

   ![Schaltfläche &quot;Richtlinie kopieren&quot;](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

* Geben Sie im Feld **Richtlinienname** einen Namen für die Richtlinie an. Eine Richtlinie muss einen Namen haben, damit sie mühelos im Dropdown-Menü **Richtlinie auswählen** ausgewählt werden kann. 

   ![Richtlinientitel](/help/sites-cloud/authoring/assets/templates-policy-title.png)

* Eine Beschreibung der Richtlinie im Feld **Richtlinienbeschreibung** ist optional.
* In the **Other templates also using the selected policy** section, you can easily see which other templates use the policy selected in the **Select policy** dropdown.

   ![Richtlinienverwendung](/help/sites-cloud/authoring/assets/templates-policy-use.png)

#### Seiteneigenschaften {#page-properties}

Using page properties, you can define the required client-side libraries by using the **Page Design** dialog. Diese clientseitigen Bibliotheken enthalten Stylesheets und JavaScript, die zusammen mit der Vorlage und den mit der Vorlage erstellten Seiten geladen werden. 

![Seiteneigenschaften](/help/sites-cloud/authoring/assets/templates-page-properties.png)

* Geben Sie die clientseitigen Bibliotheken an, die auf die mit dieser Vorlage erstellten Seiten angewendet werden sollen. Eingabe des Namens einer Bibliothek in das Textfeld im Bereich **Clientseitige Bibliotheken**.

   ![Clientseitige Bibliotheken](/help/sites-cloud/authoring/assets/templates-client-side-libraries.png)

* Wenn mehrere Bibliotheken erforderlich sind, klicken Sie auf die Schaltfläche „Hinzufügen“, um ein zusätzliches Textfeld für den Namen der Bibliothek hinzuzufügen.

   ![Schaltfläche &quot;Hinzufügen&quot;](/help/sites-cloud/authoring/assets/templates-add-button.png)

   Fügen Sie für Ihre clientseitigen Bibliotheken so viele Textfelder wie nötig hinzu.

* Definieren Sie bei Bedarf die relative Position der Bibliotheken, indem Sie die Felder mithilfe des Ziehpunkts ziehen. 

   ![Ziehpunkt](/help/sites-cloud/authoring/assets/templates-drag-handle.png)

>[!NOTE]
>
>Während der Vorlagenautor die Seitenrichtlinien in der Vorlage festlegt, benötigt er Angaben zu den jeweiligen clientseitigen Bibliotheken vom Entwickler.

### Bearbeiten einer Vorlage – Anfängliche Seiteneigenschaften – Autor {#editing-a-template-initial-page-properties-author}

Mit der Option **Anfängliche Seiteneigenschaften** können Sie die anfänglichen [Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md) definieren, die bei der Erstellung einer neuen Seite gelten sollen.

1. Wählen Sie im Vorlagen-Editor **Seiteninformationen** in der Symbolleiste und anschließend **Anfängliche Seiteneigenschaften**, um das Dialogfeld zu öffnen.

1. Im Dialogfeld können Sie Eigenschaften definieren, die für Seiten gelten sollen, die mit dieser Vorlage erstellt werden.

   ![Vorlageneigenschaften der ersten Seite](/help/sites-cloud/authoring/assets/templates-initial-properties.png)

1. Bestätigen Sie Ihre Definitionen mit **Fertig**.

## Best Practices {#best-practices}

Beim Erstellen von Vorlagen sollten Sie Folgendes berücksichtigen:

1. die Auswirkungen von Änderungen an der Vorlage, nachdem Seiten mit dieser Vorlage erstellt wurden

   Im Folgenden finden Sie eine Liste der verschiedenen Vorgänge für Vorlagen sowie deren Auswirkungen auf die Seiten, die aus den Vorlagen erstellt werden:

   * Änderungen an der Struktur:

      * Diese werden sofort auf die resultierenden Seiten angewendet.
      * Die geänderte Vorlage muss veröffentlicht werden, damit Besucher die Änderungen sehen.
   * Änderungen an Inhaltsrichtlinien und Design-Konfigurationen:

      * Diese werden direkt auf die resultierenden Seiten angewendet.
      * Die Änderungen müssen veröffentlicht werden, damit Besucher die Änderungen sehen.
   * Änderungen am anfänglichen Inhalt:

      * Diese werden nur auf Seiten angewendet, die nach den Änderungen an der Vorlage erstellt werden.
   * Änderungen am Layout sind davon abhängig, ob für die geänderte Komponente Folgendes gilt:

      * Nur Struktur – werden sofort übernommen
      * Anfängliche Inhalte enthalten – werden nur auf Seiten übernommen, die nach der Änderung erstellt werden
   Lassen Sie bei folgenden Vorgängen besondere Vorsicht walten:

   * Sperren oder Entsperren von Komponenten in aktivierten Vorlagen.
   * Dies kann Nebeneffekte haben, da die Komponenten bereits von vorhandenen Seiten verwendet werden können. In der Regel gilt:

      * Wenn Komponenten (die gesperrt waren) entsperrt werden, fehlen sie auf vorhandenen Seiten.
      * Wenn Komponenten (die bearbeitbar waren) gesperrt werden, wird der entsprechende Inhalt auf den Seiten ausgeblendet.
   >[!NOTE]
   >
   >AEM warnt ausdrücklich davor, den Sperrstatus von Komponenten in Vorlagen zu ändern, die keine Entwürfe mehr sind.

1. [Erstellen Sie Ihre eigenen Ordner](#creating-a-template-folder-admin) für Ihre sitespezifischen Vorlagen.
1. [Veröffentlichen Sie Ihre Vorlagen](#publishing-a-template-template-author) über die **Vorlagenkonsole**.
