---
title: Erstellen von Seitenvorlagen
description: Eine Vorlage definiert die Struktur einer erstellten Seite und mit dem Vorlageneditor ist die Erstellung und Verwaltung von Vorlagen nicht mehr nur Entwicklern vorbehalten.
exl-id: 4c9dbf26-5852-45ab-b521-9f051c153b2e
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '4577'
ht-degree: 65%

---

# Erstellen von Seitenvorlagen {#creating-page-templates}

Beim Erstellen einer Seite müssen Sie eine Vorlage auswählen, die als Grundlage für die Erstellung der neuen Seite dient. Die Vorlage definiert die Struktur der resultierenden Seite, den anfänglichen Inhalt und die Komponenten, die verwendet werden können.

Mit dem **Vorlageneditor** ist das Erstellen und Verwalten von Vorlagen nicht mehr nur eine Aufgabe für Entwickler. Auch ein Power User, der als **Vorlagenautor** bezeichnet wird, kann einbezogen werden. Entwickler müssen weiterhin die Umgebung einrichten, Clientbibliotheken erstellen und die zu verwendenden Komponenten erstellen. Sobald diese Grundlagen vorhanden sind, hat der **Vorlagenautor** jedoch die Flexibilität, Vorlagen ohne Entwicklungsprojekt zu erstellen und zu konfigurieren.

Die **Vorlagenkonsole** ermöglicht es Vorlagenautoren,

* eine neue Vorlage erstellen oder eine vorhandene Vorlage kopieren
* den Lebenszyklus der Vorlage verwalten

Mit dem **Vorlageneditor** können Vorlagenautoren:

* Fügen Sie Komponenten zur Vorlage hinzu und positionieren Sie sie auf einem responsiven Raster.
* die Komponenten vorkonfigurieren
* Definieren Sie, welche Komponenten auf Seiten bearbeitet werden können, die mit der Vorlage erstellt wurden.

In diesem Dokument wird erklärt, wie ein **Vorlagenautor** die Vorlagenkonsole und den Vorlageneditor verwenden kann, um bearbeitbare Vorlagen zu erstellen und zu verwalten.

Ausführliche Informationen zur Funktionsweise von bearbeitbaren Vorlagen auf technischer Ebene finden Sie im Entwicklerdokument [Seitenvorlagen](/help/implementing/developing/components/templates.md) für weitere Informationen.

>[!NOTE]
>
>Der **Vorlageneditor** unterstützt kein Targeting direkt auf Vorlagenstufe. Seiten, die auf Grundlage einer bearbeitbaren Vorlage erstellt wurden, können zielgerichtet sein, die Vorlagen selbst müssen das jedoch nicht sein.

## Bevor Sie beginnen {#before-you-start}

>[!NOTE]
>
>Ein Admin muss im **Konfigurations-Browser** einen Vorlagenordner konfigurieren und entsprechende Berechtigungen anwenden, bevor ein Vorlagenautor eine Vorlage in diesem Ordner erstellen kann.

Bevor Sie anfangen, sollten Sie beachten, dass die Erstellung einer neuen Vorlage Zusammenarbeit erfordert. Aus diesem Grund wird für jede Aufgabe eine [Rolle](#roles) angezeigt. Dies hat keinen Einfluss auf die Art und Weise, wie Sie eine Seite mit einer Vorlage erstellen, sondern nur auf die Weise, wie eine Seite mit ihrer Vorlage in Beziehung steht.

### Rollen {#roles}

Für das Erstellen einer neuen Vorlage mithilfe der **Vorlagenkonsole** und des **Vorlageneditors** ist eine Zusammenarbeit zwischen folgenden Rollen erforderlich:

* **Admin**:
   * Erstellt neue Ordner für Vorlagen, wofür `admin`-Berechtigungen erforderlich sind.
   * Solche Aufgaben können oft auch von einem Entwickler durchgeführt werden
* **Entwickler**:
   * Konzentriert sich auf die technischen/internen Details
   * Muss Erfahrung mit der Entwicklungsumgebung haben.
   * Versorgt den Vorlagenautor mit den erforderlichen Informationen.
* **Vorlagenautor**:
   * Dies ist ein bestimmter Autor, der Mitglied der Gruppe `template-authors` ist.
      * Weist die erforderlichen Berechtigungen zu.
   * Kann die Verwendung von Komponenten und anderen Details auf hoher Ebene konfigurieren, was Folgendes erfordert:
      * Einige technische Kenntnisse
         * Verwenden Sie beispielsweise Muster beim Definieren von Pfaden.
      * Technische Informationen vom Entwickler.

Aufgrund der Art einiger Aufgaben wie der Erstellung eines Ordners ist eine Entwicklungsumgebung erforderlich, die Wissen/Erfahrung erfordert.

Die in diesem Dokument beschriebenen Aufgaben werden mit der Rolle aufgelistet, die für ihre Durchführung verantwortlich ist.

## Erstellen und Verwalten von Vorlagen {#creating-and-managing-templates}

Gehen Sie zum Erstellen einer neuen bearbeitbaren Vorlage wie folgt vor:

* Verwenden Sie die **Vorlagenkonsole**, die im Bereich **Allgemein** der Konsole **Tools** verfügbar ist.
   * Oder direkt unter: `https://<host>:<port>/libs/wcm/core/content/sites/templates.html/conf`
* Erstellen Sie bei Bedarf [einen Ordner für die Vorlagen](#creating-a-template-folder-admin).
* [Erstellen Sie eine neue Vorlage](#creating-a-new-template-template-author), die anfangs leer ist.
* [Zusätzliche Eigenschaften definieren](#defining-template-properties-template-author) für die Vorlage, falls erforderlich
* [Vorlage bearbeiten](#editing-templates-template-authors) um Folgendes zu definieren:
   * [Struktur](#editing-a-template-structure-template-author) – vordefinierter Inhalt, der auf Seiten, die mit der Vorlage erstellt werden, nicht geändert werden kann.
   * [Anfänglicher Inhalt](#editing-a-template-initial-content-author) – vordefinierter Inhalt, der auf den Seiten geändert werden kann, die mit der Vorlage erstellt werden.
   * [Layout](#editing-a-template-layout-template-author) – für eine Vielzahl von Geräten.
   * [Stile](/help/sites-cloud/authoring/features/style-system.md) – zum Definieren der Stile für die Vorlage und ihre Komponenten.
* [Vorlage aktivieren](#enabling-a-template-template-author) zur Verwendung beim Erstellen einer Seite
* [Vorlage zulassen](#allowing-a-template-author) für die gewünschte Seite oder den Zweig Ihrer Website
* [Vorlage veröffentlichen](#publishing-a-template-template-author) , um sie in der Veröffentlichungsumgebung verfügbar zu machen

>[!NOTE]
>
>Die **zugelassenen Vorlagen** werden häufig vordefiniert, wenn Sie Ihre Website erstmals einrichten.

>[!TIP]
>
>Geben Sie in eine Vorlage nie Informationen ein, die internationalisiert werden müssen. <!-- Never enter any information that needs to be [internationalized](/help/sites-developing/i18n.md) into a template.-->
>
>Verwenden Sie für Vorlagenelemente wie Kopf- und Fußzeilen, die lokalisiert werden müssen, den [Lokalisierungsfunktionen der Kernkomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html?lang=de)

### Erstellen eines Vorlagenordners – Administrator {#creating-a-template-folder-admin}

Für Ihr Projekt sollte ein Vorlagenordner für Ihre projektspezifischen Vorlagen erstellt werden. Dies ist eine Administratoraufgabe, die im Dokument [Seitenvorlagen](/help/implementing/developing/components/templates.md#template-folders) beschrieben wird.-->

### Erstellen einer neuen Vorlage – Vorlagenautor {#creating-a-new-template-template-author}

1. Öffnen Sie die **Vorlagenkonsole** (über **Tools >** **Allgemein**) und navigieren Sie zum gewünschten Ordner.

   >[!NOTE]
   >
   >In einer Standard-AEM-Instanz ist der Ordner **Global** bereits in der Vorlagenkonsole vorhanden. Er enthält Standardvorlagen und dient als Ausweichlösung, wenn keine Richtlinien und/oder Vorlagentypen im aktuellen Ordner gefunden werden.
   >
   >Es wird empfohlen, eine [Vorlagenordner, der für Ihr Projekt erstellt wurde](/help/implementing/developing/components/templates.md#template-folders).

1. Wählen Sie **Erstellen** und anschließend **Vorlage erstellen**, um den Assistenten zu öffnen.

1. Auswählen einer **Vorlagentyp**, wählen Sie **Nächste**.

   >[!NOTE]
   >
   >Vorlagenarten sind vordefinierte Vorlagen, die als Vorlagen für eine Vorlage betrachtet werden können. Diese werden von Entwicklern oder dem Systemadministrator vordefiniert. Weitere Informationen finden Sie im Entwicklerdokument [Seitenvorlagen](/help/implementing/developing/components/templates.md#template-type).-->

1. Führen Sie die **Vorlagendetails**:

   * **Vorlagenname**
   * **Beschreibung**

1. Wählen Sie **Erstellen**. Eine Bestätigung wird angezeigt, wählen Sie **Öffnen** , um mit der Bearbeitung der Vorlage zu beginnen, oder **Fertig** , um zur Vorlagenkonsole zurückzukehren.

   >[!NOTE]
   >
   >Wenn eine neue Vorlage erstellt wird, wird sie in der Konsole als **Entwurf** markiert, was bedeutet, dass sie noch nicht für Seitenautoren zur Verfügung steht.

>[!NOTE]
>
>Vorlagen sind leistungsstarke Tools zur Optimierung des Seitenerstellungs-Workflows. Allerdings können zu viele Vorlagen die Autoren überwältigen und das Erstellen von Seiten unübersichtlich machen. Eine gute Faustregel ist, die Anzahl der Vorlagen unter 100 zu halten.
>
>Adobe empfiehlt, aufgrund möglicher Leistungsauswirkungen nicht mehr als 1.000 Vorlagen zu verwenden.

### Definieren von Vorlageneigenschaften – Vorlagenautor {#defining-template-properties-template-author}

Eine Vorlage kann die folgenden Eigenschaften aufweisen:

* Bild
   * Bild, das als [Miniatur der Vorlage verwendet wird](#template-thumbnail-image), um die Auswahl zu vereinfachen, beispielsweise im Seitenerstellungsassistenten.
      * Kann hochgeladen werden
      * Kann basierend auf dem Vorlageninhalt generiert werden
* Titel
   * Ein Titel, der zur Identifizierung der Vorlage verwendet wird, z. B. im **Seite erstellen** Assistent.
* Beschreibung
   * Eine optionale Beschreibung mit weiteren Informationen zur Vorlage und deren Verwendung, die beispielsweise im **Seitenerstellungsassistenten** angezeigt werden können.

So zeigen Sie die Eigenschaften an bzw. bearbeiten sie:

1. Wählen Sie in der **Vorlagenkonsole** eine Vorlage aus.
1. Wählen Sie **Eigenschaften anzeigen** in der Symbolleiste oder in den Schnelloptionen aus, um das Dialogfeld zu öffnen.
1. Jetzt können Sie die Vorlageneigenschaften anzeigen oder bearbeiten.

>[!NOTE]
>
>Der Status einer Vorlage („Entwurf“, „Aktiviert“ oder „Deaktiviert“) wird in der Konsole angezeigt.

#### Vorlagenminiaturbild {#template-thumbnail-image}

So definieren Sie die Vorlagenminiatur:

1. Bearbeiten Sie die Vorlageneigenschaften.
1. Wählen Sie aus, ob Sie eine Miniaturansicht hochladen oder aus dem Vorlageninhalt generieren lassen möchten.
   * Wenn Sie eine Miniaturansicht hochladen möchten, klicken oder tippen Sie auf **Bild hochladen**
   * Wenn Sie eine Miniatur erzeugen möchten, klicken oder tippen Sie auf **Vorschau generieren**
1. Für beide Methoden wird eine Vorschau der Miniaturansicht angezeigt.
   * Wenn sie nicht zufriedenstellend ist, klicken oder tippen Sie auf **Löschen** , um ein anderes Bild hochzuladen oder die Miniaturansicht neu zu generieren.
1. Wenn Sie mit der Miniaturansicht zufrieden sind, klicken oder tippen Sie auf **Speichern und schließen**.

### Aktivieren und Zulassen einer Vorlage – Vorlagenautor {#enabling-and-allowing-a-template-template-author}

Um beim Erstellen einer Seite eine Vorlage zu verwenden, gehen Sie wie folgt vor:

* [Aktivieren Sie die Vorlage](#enabling-a-template-template-author), um sie verfügbar zu machen, wenn Seiten erstellt werden.
* [Lassen Sie die Vorlage zu](#allowing-a-template-author), um die Inhaltsverzweigungen anzugeben, in denen die Vorlage verwendet werden kann.

#### Aktivieren einer Vorlage – Vorlagenautor {#enabling-a-template-template-author}

Eine Vorlage kann aktiviert oder deaktiviert werden, um sie im **Seite erstellen** Assistent.

>[!CAUTION]
>
>Nachdem eine Vorlage aktiviert wurde, wird eine Warnung angezeigt, wenn ein Vorlagenautor beginnt, die Vorlage weiter zu aktualisieren. Diese dient dazu, den Benutzer zu informieren, dass die Vorlage referenziert wird und damit sämtliche Änderungen, die die Vorlage referenzierenden Seiten beeinträchtigen könnten.

1. Wählen Sie in der **Vorlagenkonsole** eine Vorlage aus.
1. Wählen Sie in der Symbolleiste die Option **Aktivieren** oder **Deaktivieren** und bestätigen Sie Ihre Wahl im Bestätigungsdialogfeld.
1. Jetzt können Sie Ihre Vorlage verwenden, wenn Sie [eine neue Seite erstellen](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page), bzw. [die Vorlage bearbeiten](#editing-templates-template-authors), um sie an Ihre Anforderungen anzupassen.

>[!NOTE]
>
>Der Status einer Vorlage („Entwurf“, „Aktiviert“ oder „Deaktiviert“) wird in der Konsole angezeigt.

#### Zulassen einer Vorlage – Autor {#allowing-a-template-author}

Eine Vorlage kann für bestimmte Seitenverzweigungen verfügbar oder nicht verfügbar gemacht werden.

1. Öffnen Sie die [Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md) für die Stammseite der Verzweigung, in der die Vorlage verfügbar sein soll.
1. Öffnen Sie die Registerkarte **Erweitert**.
1. Klicken Sie unter **Vorlageneinstellungen** auf **Feld hinzufügen**, um den Pfad/die Pfade zu Ihren Vorlagen anzugeben.

   Der Pfad kann explizit sein oder Muster verwenden. Ein Beispiel:

   `/conf/<your-folder>/settings/wcm/templates/.*`

   Die Reihenfolge der Pfade ist irrelevant. Alle Pfade werden gescannt und alle Vorlagen werden abgerufen.

   >[!NOTE]
   >
   >Wenn die Variable **Zulässige Vorlagen** leer ist, wird der Baum aufgerissen, bis ein Wert/eine Liste gefunden wird.
   >
   >
   >Weitere Informationen finden Sie unter [Vorlagenverfügbarkeit](/help/implementing/developing/components/templates.md#template-availability) – die Prinzipien für zugelassene Vorlagen bleiben gleich.

1. Klicken Sie auf **Speichern**, um die Änderungen an den Seiteneigenschaften zu speichern.

>[!NOTE]
>
>Häufig werden die zugelassenen Vorlagen für Ihre gesamte Site vordefiniert, wenn diese eingerichtet wird.

### Veröffentlichen einer Vorlage – Vorlagenautor {#publishing-a-template-template-author}

Da auf die Vorlage verwiesen wird, wenn eine Seite dargestellt wird, muss die voll konfigurierte Vorlage veröffentlicht werden, damit sie in der Veröffentlichungsumgebung verfügbar ist.

1. Wählen Sie in der **Vorlagenkonsole** eine Vorlage aus.
1. Wählen Sie **Veröffentlichen** in der Symbolleiste, um den Assistenten zu öffnen.
1. Wählen Sie die **Inhaltsrichtlinien**, die mit veröffentlicht werden sollen.
1. Wählen Sie **Veröffentlichen** in der Symbolleiste, um den Vorgang abzuschließen.

## Bearbeiten von Vorlagen   – Vorlagenautoren {#editing-templates-template-authors}

Beim Erstellen oder Bearbeiten einer Vorlage können verschiedene Aspekte definiert werden. Das Bearbeiten von Vorlagen ähnelt dem Bearbeiten von Seiten.

Mit der **Modus**-Auswahl in der Symbolleiste können Sie die jeweiligen Aspekte der Vorlage auswählen und bearbeiten:

* [Struktur](#editing-a-template-structure-template-author)
* [Anfänglicher Inhalt](#editing-a-template-initial-content-author)
* [Layout](#editing-a-template-layout-template-author)

![Modusauswahl im Vorlageneditor](/help/sites-cloud/authoring/assets/templates-mode.png)

Mit der Option **Seitenrichtlinie** im Menü **Seiteninformationen** können Sie [die erforderlichen Seitenrichtlinien auswählen](#page-policies):

![Seiteninformationen des Vorlageneditors](/help/sites-cloud/authoring/assets/templates-page-information.png)

>[!CAUTION]
>
>Wenn ein Autor beginnt, eine bereits aktivierte Vorlage zu bearbeiten, wird eine Warnung angezeigt. Diese dient dazu, den Benutzer zu informieren, dass die Vorlage referenziert wird und damit sämtliche Änderungen, die die Vorlage referenzierenden Seiten beeinträchtigen könnten.

### Vorlagenattribute {#template-attributes}

Die folgenden Attribute einer Vorlage können bearbeitet werden:

#### Struktur {#template-structure}

Komponenten, die zur [Struktur](#editing-a-template-structure-template-author) hinzugefügt werden, können von den Seitenautoren nicht von den resultierenden Seiten entfernt/verschoben werden. Wenn Seitenautoren in der Lage sein sollen, neue Komponenten zu resultierenden Seiten hinzuzufügen und daraus zu entfernen, müssen Sie der Vorlage ein Absatzsystem hinzufügen.

Wenn Komponenten gesperrt sind, können Sie Inhalte hinzufügen, die von Seitenautoren nicht bearbeitet werden können. Sie können Komponenten entsperren, damit Sie [Anfänglicher Inhalt](#editing-a-template-initial-content-author).

>[!NOTE]
>
>Im Strukturmodus können Komponenten, die einer entsperrten Komponente übergeordnet sind, nicht verschoben, ausgeschnitten oder gelöscht werden.

#### Anfänglicher Inhalt {#template-initial-content}

Wenn eine Komponente entsperrt wurde, können Sie die [anfänglicher Inhalt](#editing-a-template-initial-content-author) wird auf die resultierende(n) Seite(n) kopiert, die aus der Vorlage erstellt wird. Diese entsperrten Komponenten können auf den resultierenden Seiten bearbeitet werden.

>[!NOTE]
>
>In **Anfänglicher Inhalt** -Modus und auf den resultierenden Seiten können alle entsperrten Komponenten, die über ein barrierefreies übergeordnetes Element verfügen (d. h. Komponenten in einem Layout-Container), gelöscht werden.

#### Layout {#template-layout}

Mit dem [Layout](#editing-a-template-layout-template-author) können Sie das Vorlagen-Layout für die erforderlichen Geräteformate vordefinieren. Der Modus **Layout** für das Erstellen von Vorlagen bietet dieselben Funktionen wie der Modus [**Layout** für das Erstellen von Seiten](/help/sites-cloud/authoring/features/responsive-layout.md#defining-layouts-layout-mode).

#### Seitenrichtlinien {#template-page-policies}

Unter [Seitenrichtlinien](#page-policies) können Sie vordefinierte Seitenrichtlinien für die Seite verknüpfen. Diese Seitenrichtlinien definieren die verschiedenen Design-Konfigurationen.

#### Stile {#template-styles}

Das [Stilsystem](/help/sites-cloud/authoring/features/style-system.md) ermöglicht es einem Vorlagenautor, in der Inhaltsrichtlinie für Komponenten Stilklassen festzulegen, die ein Inhaltsautor später bei der Bearbeitung der Komponente auf einer Seite auswählen kann. Diese Stile können alternative visuelle Varianten einer Komponente sein, um das Verfahren flexibler zu gestalten.

Weitere Informationen finden Sie in der [Dokumentation für das Stilsystem](/help/sites-cloud/authoring/features/style-system.md).

### Bearbeiten einer Vorlage – Struktur – Vorlagenautor {#editing-a-template-structure-template-author}

Im **Strukturmodus** definieren Sie Komponenten und Inhalte für Ihre Vorlage sowie Richtlinien für die Vorlage und die zugehörigen Komponenten.

* Komponenten, die in der Vorlagenstruktur definiert sind, können nicht auf einer resultierenden Seite verschoben oder von den resultierenden Seiten gelöscht werden.
* Wenn Seitenautoren Komponenten hinzufügen und entfernen können sollen, fügen Sie der Vorlage ein Absatzsystem hinzu.
* Komponenten lassen sich entsperren und erneut sperren, damit Sie den [anfänglichen Inhalt](#editing-a-template-initial-content-author) definieren können.
* Die Design-Richtlinien für die Komponenten und die Seite werden definiert.

![Seitenstruktur des Vorlageneditors](/help/sites-cloud/authoring/assets/templates-page-structure.png)

Es gibt eine Reihe von Aktionen, die Sie im **Strukturmodus** des Vorlageneditors ausführen können, sowie eine Reihe von Funktionen, die Ihnen Unterstützung bieten:

#### Hinzufügen von Komponenten {#add-components}

Es gibt mehrere Möglichkeiten, Komponenten zur Vorlage hinzuzufügen:

* Aus dem **Komponenten** im Seitenbereich.
* über die Option **Komponente einfügen** in der Symbolleiste von Komponenten, die sich bereits in der Vorlage befinden, oder das Feld **Komponenten hierher ziehen**
* Durch Ziehen eines Assets (aus dem **Assets** -Browser im Seitenbereich) direkt auf die Vorlage klicken, um die entsprechende Komponente vor Ort zu generieren.

Nach dem Hinzufügen wird jede Komponente mit folgenden Elementen markiert:

* Rahmen
* Eine Markierung, die den Komponententyp anzeigt
* Eine Markierung, die anzeigt, wann die Komponente entsperrt wurde

>[!NOTE]
>
>Wenn Sie eine vordefinierte **Titelkomponente** zur Vorlage hinzufügen, enthält sie den Standardtext **Struktur**.
>
>Wenn Sie diesen ändern und Ihren eigenen Text hinzufügen, wird dieser aktualisierte Text verwendet, wenn eine Seite aus der Vorlage erstellt wird.
>
>Wenn Sie den Standardtext (Struktur) nicht ändern, wird der Titel standardmäßig mit dem Namen der nachfolgenden Seite benannt.

>[!NOTE]
>
>Das Hinzufügen von Komponenten und Assets zu einer Vorlage ist zwar nicht dasselbe wie das [Erstellen von Seiten](/help/sites-cloud/authoring/fundamentals/editing-content.md), es gibt aber durchaus einige Ähnlichkeiten.

#### Komponenten-Aktionen {#component-actions}

Nehmen Sie Aktionen für die Komponenten vor, nachdem sie der Vorlage hinzugefügt wurden. Jede einzelne Instanz verfügt über eine Symbolleiste, über die Sie auf die verfügbaren Aktionen zugreifen können. Die Symbolleiste hängt vom Komponententyp ab.

![Aktions-Symbolleiste einer Vorlagenkomponente](/help/sites-cloud/authoring/assets/templates-component-actions.png)

Sie kann auch von durchgeführten Aktionen abhängig sein. Wenn z. B. eine Richtlinie mit der Komponente verbunden wurde, ist das Design-Konfigurationssymbol verfügbar.

#### Bearbeiten und Konfigurieren {#edit-and-configure}

Mit diesen zwei Aktionen können Sie Inhalte zu Ihren Komponenten hinzufügen.

#### Rand für die Anzeige der Struktur {#border-to-indicate-structure}

Bei der Arbeit in **Struktur** -Modus zeigt ein orangefarbener Rahmen die aktuell ausgewählte Komponente an. Eine gepunktete Linie zeigt auch die übergeordnete Komponente an.

#### Richtlinien und Eigenschaften (Allgemein) {#policy-and-properties-general}

Die Inhalts- (oder Design-)Richtlinien definieren die Designeigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

Erstellen Sie für eine Komponente eine Inhaltsrichtlinie oder wählen Sie eine vorhandene.

![Schaltfläche „Inhaltsrichtlinie“](/help/sites-cloud/authoring/assets/templates-content-policy-button.png)

Damit können Sie die Design-Details definieren.

![Inhaltsrichtlinie](/help/sites-cloud/authoring/assets/template-content-policy.png)

Das Konfigurationsfenster ist in zwei Hälften geteilt.

* Auf der linken Seite des Dialogfelds können Sie unter **Richtlinie** eine vorhandene Richtlinie auswählen.
* Auf der rechten Seite des Dialogfelds können Sie unter **Eigenschaften** die für den Komponententyp spezifischen Eigenschaften festlegen.

Die verfügbaren Eigenschaften hängen von der ausgewählten Komponente ab. Beispielsweise definieren die Eigenschaften für eine Textkomponente die Optionen zum Kopieren und Einfügen, Formatierungsoptionen und den Absatzstil.

##### Richtlinie {#policy}

Die Inhalts- (oder Design-)Richtlinien definieren die Designeigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

Unter **Richtlinie** können Sie eine vorhandene Richtlinie auswählen, die über das Dropdown-Menü auf die Komponente angewendet wird.

![Richtlinie auswählen](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

Sie können eine neue Richtlinie hinzufügen, indem Sie auf die Schaltfläche „Hinzufügen“ klicken, die sich neben dem Dropdown-Menü **Richtlinie auswählen** befindet. Dann muss ein neuer Name in das Feld **Richtlinienname** eingegeben werden.

![Schaltfläche „Richtlinie hinzufügen“](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

Die im Dropdown-Menü **Richtlinie auswählen** ausgewählte vorhandene Richtlinie kann mithilfe der Schaltfläche „Kopieren“, die sich neben dem Dropdown-Menü befindet, kopiert werden. Dann muss ein neuer Name in das Feld **Richtlinienname** eingegeben werden. Standardmäßig erhält die kopierte Richtlinie den Namen **Kopie von X**, wobei X der Titel der kopierten Richtlinie ist.

![Schaltfläche „Richtlinie kopieren“](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

Eine Beschreibung der Richtlinie im Feld **Richtlinienbeschreibung** ist optional.

Im Abschnitt **Andere Vorlagen, die ebenfalls die ausgewählte Richtlinie verwenden** ist leicht ersichtlich, welche anderen Vorlagen die Richtlinie verwenden, die in der Dropdown-Liste **Richtlinie auswählen** ausgewählt wurde.

![Nutzung der vorhandenen Richtlinie](/help/sites-cloud/authoring/assets/templates-policy-use.png)

>[!NOTE]
>
>Wenn mehrere Komponenten des gleichen Typs als anfänglicher Inhalt hinzugefügt werden, gilt für alle Komponenten dieselbe Richtlinie.

##### Eigenschaften {#properties}

Unter dem **Eigenschaften** -Überschrift können Sie die Einstellungen der Komponente definieren. Die Überschrift hat zwei Registerkarten:

* Allgemein
* Funktionen

###### Allgemein {#main}

Auf der Registerkarte **Allgemein** sind die wichtigsten Einstellungen der Komponente definiert.

Beispielsweise können für eine Bildkomponente die zulässigen Breiten zusammen mit der Aktivierung von verzögertem Laden definiert werden.

Wenn eine Einstellung mehrere Konfigurationen zulässt, klicken oder tippen Sie auf die **Hinzufügen** -Schaltfläche, um eine weitere Konfiguration hinzuzufügen.

![Schaltfläche „Hinzufügen“](/help/sites-cloud/authoring/assets/templates-add-button.png)

Um eine Konfiguration zu entfernen, klicken oder tippen Sie auf die Schaltfläche **Löschen**, die sich rechts neben der Konfiguration befindet.

Um eine Konfiguration zu entfernen, klicken oder tippen Sie auf die Schaltfläche **Löschen**.

![Schaltfläche „Löschen“](/help/sites-cloud/authoring/assets/templates-delete-button.png)

###### Funktionen {#features}

Die **Funktionen** -Tab können Sie zusätzliche Funktionen der Komponente aktivieren oder deaktivieren.

Beispielsweise können Sie für eine Bildkomponente die Zuschneideproportionen, die zulässigen Bildausrichtungen und die Möglichkeit von Uploads definieren.

![Registerkarte „Funktionen“](/help/sites-cloud/authoring/assets/templates-features-tab.png)

>[!CAUTION]
>
>Beachten Sie, dass in AEM die Beschneidungsverhältnisse als **Höhe/Breite** definiert sind. Dies unterscheidet sich von der herkömmlichen Definition als Breite/Höhe und erfolgt aus Gründen der Legacy-Kompatibilität. Benutzer, die Seiten erstellen, bemerken keinen Unterschied, vorausgesetzt, dass Sie den **Namen** klar definieren, da dieser auf der Benutzeroberfläche angezeigt wird.

>[!NOTE]
>
>[Inhaltsrichtlinien für Komponenten, die den Rich-Text-Editor implementieren](/help/implementing/developing/extending/rich-text-editor.md), können nur für Optionen definiert werden, die vom RTE über die UI-Einstellungen bereitgestellt werden.  

#### Richtlinien und Eigenschaften (Layout-Container) {#policy-and-properties-layout-container}

Die Richtlinien- und Eigenschafteneinstellungen eines Layout-Containers ähneln der allgemeinen Verwendung, allerdings mit einigen Unterschieden.

>[!NOTE]
>
>Die Konfiguration einer Richtlinie ist für Container-Komponenten obligatorisch, da sie es Ihnen ermöglicht, Komponenten zu definieren, die im Container verfügbar sind.

Das Konfigurationsfenster ist in zwei Bereiche unterteilt, genau wie in der allgemeinen Nutzung des Fensters.

##### Richtlinie {#policy-layout}

Die Inhalts- (oder Design-)Richtlinien definieren die Designeigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

Unter **Richtlinie** können Sie eine vorhandene Richtlinie auswählen, die über das Dropdown-Menü auf die Komponente angewendet wird. Dies funktioniert ebenso wie bei der allgemeinen Verwendung des Fensters.

##### Eigenschaften {#properties-layout}

Unter dem **Eigenschaften** -Überschrift können Sie auswählen, welche Komponenten für den Layout-Container verfügbar sind, und ihre Einstellungen definieren. Die Überschrift hat drei Registerkarten:

* Zugelassene Komponenten
* Standardkomponenten
* Responsive Einstellungen

###### Zugelassene Komponenten {#allowed-components}

Im **Zugelassene Komponenten** definieren, legen Sie fest, welche Komponenten für den Layout-Container verfügbar sind.

* Die Komponenten werden nach Komponentengruppen gruppiert, die sich erweitern und reduzieren lassen.
* Es kann eine ganze Gruppe ausgewählt werden, indem der Gruppenname überprüft wird. Die Auswahl aller Gruppen kann durch Deaktivieren der Option aufgehoben werden.
* Ein Minuszeichen steht für mindestens ein Element, es werden jedoch nicht alle Elemente einer Gruppe ausgewählt.
* Es ist eine Suche verfügbar, um nach einer Komponente nach Namen zu filtern.
* Die rechts neben dem Komponentengruppen-Namen aufgelisteten Zahlen geben die Gesamtanzahl der ausgewählten Komponenten in diesen Gruppen an, unabhängig vom Filter.

![Registerkarte „Zugelassene Komponenten“](/help/sites-cloud/authoring/assets/templates-allowed-components-tab.png)

###### Standardkomponenten {#default-components}

Im **Standardkomponenten** -Registerkarte definieren, definieren Sie, welche Komponenten automatisch bestimmten Medientypen zugeordnet werden. Wenn ein Autor ein Asset aus dem Asset-Browser zieht, weiß AEM, mit welcher Komponente es verknüpft werden soll. Beachten Sie, dass für diese Konfiguration nur Komponenten mit Ablageflächen verfügbar sind.

Klicken oder tippen Sie auf **Zuordnung hinzufügen** , um eine völlig neue Komponente und MIME-Typzuordnung hinzuzufügen.

Wählen Sie eine Komponente in der Liste aus und tippen/klicken Sie auf **Typ hinzufügen**, um einer bereits zugeordneten Komponente einen zusätzlichen MIME-Typ hinzuzufügen. Klicken Sie auf das Symbol **Löschen**, um einen MIME-Typ zu entfernen.

![Registerkarte „Standardkomponenten“](/help/sites-cloud/authoring/assets/templates-default-components-tab.png)

###### Responsive Einstellungen {#responsive-settings}

Auf der Registerkarte **Responsive Einstellungen** können Sie die Anzahl der Spalten im resultierenden Raster des Layout-Containers konfigurieren.

#### Sperren und Entsperren von Komponenten {#unlock-and-lock-components}

Komponenten werden entsperrt/gesperrt, um festzulegen, ob der Inhalt im Modus **Anfänglicher Inhalt** geändert werden darf.

Wenn eine Komponente entsperrt wurde:

* Im Rahmen wird eine offene Vorhängeschlossanzeige angezeigt.
* Die Komponenten-Symbolleiste wird entsprechend angepasst.
* Bereits eingegebener Inhalt wird nicht mehr in **Struktur** -Modus.
   * Bereits eingegebener Inhalt wird als anfänglicher Inhalt betrachtet und ist nur im Modus **Anfänglicher Inhalt** sichtbar.
* Die Komponenten, die der entsperrten Komponente übergeordnet sind, können nicht verschoben, ausgeschnitten oder gelöscht werden.

![Schaltfläche „Komponente sperren“](/help/sites-cloud/authoring/assets/templates-unlock-component.png)

Dies umfasst das Entsperren von Containerkomponenten, sodass weitere Komponenten hinzugefügt werden können, entweder im **Ursprüngliche Inhalte** oder auf den daraus resultierenden Seiten. Wenn Sie dem Container bereits Komponenten/Inhalte hinzugefügt haben, bevor Sie ihn entsperren, werden diese nicht mehr angezeigt, wenn Sie **Struktur** -Modus, sie werden jedoch in **Anfänglicher Inhalt** -Modus. In **Strukturmodus**, wird nur die Container-Komponente selbst mit der zugehörigen Liste von **Zugelassene Komponenten**.

![Zugelassene Komponenten](/help/sites-cloud/authoring/assets/templates-allowed-components.png)

Der Layout-Container wächst nicht an, um die Liste der zulässigen Komponenten aufzunehmen. Auf diese Weise wird Speicherplatz gespart. Stattdessen wird der Container zu einer bildlauffähigen Liste.

Komponenten, die konfigurierbar sind, werden mit einem Symbol für **Richtlinien** angezeigt, auf das Sie tippen/klicken können, um die Richtlinie und Eigenschaften dieser Komponente zu bearbeiten.

![Symbol „Konfigurierbare Komponente“](/help/sites-cloud/authoring/assets/templates-configurable-component.png)

#### Beziehung zu vorhandenen Seiten {#relationship-to-existing-pages}

Auf diesen Seiten werden die Änderungen an der Vorlage widergespiegelt, wenn die Struktur aktualisiert wird, nachdem die Seiten auf der Grundlage der Vorlage erstellt wurden. In der Symbolleiste wird eine Warnung mit einem Bestätigungsdialog angezeigt, um Sie an diese Tatsache zu erinnern.

![Banner-Warnung, dass Vorlage bereits in Verwendung ist](/help/sites-cloud/authoring/assets/templates-in-use-banner.png)

### Bearbeiten einer Vorlage – Anfänglicher Inhalt – Autor {#editing-a-template-initial-content-author}

Der Modus **Anfänglicher Inhalt** wird für definierten Inhalt verwendet, der angezeigt wird, wenn eine Seite anfänglich auf der Grundlage einer Vorlage erstellt wird. Der anfängliche Inhalt kann dann von Seitenautoren bearbeitet werden.

Obwohl der gesamte Inhalt, der im Modus **Struktur** erstellt wird, im Modus **Anfänglicher Inhalt** sichtbar ist, können nur entsperrte Komponenten ausgewählt und bearbeitet werden.

>[!NOTE]
>
>Der Modus **Anfänglicher Inhalt** kann als Bearbeitungsmodus für Seiten betrachtet werden, die mit dieser Vorlage erstellt werden. Daher sind Richtlinien nicht im Modus **Anfänglicher Inhalt**, sondern im [**Strukturmodus** definiert](#editing-a-template-structure-template-author).

* Entsperrte Komponenten, die zur Bearbeitung verfügbar sind, sind markiert. Wenn ausgewählt, wird ein blauer Rahmen angezeigt:

  ![Modus „Anfänglicher Inhalt“](/help/sites-cloud/authoring/assets/templates-initial-content-mode.png)

* Entsperrte Komponenten haben eine Symbolleiste, mit der Sie den Inhalt bearbeiten und konfigurieren können:

  ![Entsperrte Komponente](/help/sites-cloud/authoring/assets/templates-unlocked-components.png)

* Wenn eine Container-Komponente (im Modus **Struktur**) entsperrt wurde, können Sie neue Komponenten zum Container hinzufügen (im Modus **Anfänglicher Inhalt**). Komponenten, die im Modus **Anfänglicher Inhalt** hinzugefügt werden, können auf resultierende Seiten verschoben oder von diesen gelöscht werden.

  Sie können Komponenten über den Bereich **Komponenten hierher ziehen** oder mithilfe der Option **Neue Komponente einfügen** in der Symbolleiste des jeweiligen Containers hinzufügen.

  ![Komponente hinzufügen](/help/sites-cloud/authoring/assets/templates-add-component.png)
  ![Komponente hinzufügen](/help/sites-cloud/authoring/assets/templates-add-component-dialog.png)

* Wenn der anfängliche Inhalt der Vorlage aktualisiert wird, nachdem Seiten auf der Grundlage der Vorlage erstellt wurden, wirken sich die Änderungen am anfänglichen Inhalt der Vorlage nicht auf diese Seiten aus.

>[!NOTE]
>
>Der ursprüngliche Inhalt dient zum Vorbereiten von Komponenten und dem Seitenlayout, die als Ausgangspunkt für die Erstellung des Inhalts dienen. Dies soll nicht der eigentliche Inhalt sein, der unverändert bleibt. Aus diesem Grund können anfängliche Inhalte nicht übersetzt werden.
>
>Wenn Sie in Ihre Vorlage übersetzbaren Text aufnehmen möchten, z. B. in Kopf- oder Fußzeilen, können Sie die [Lokalisierungsfunktionen der Hauptkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html?lang=de) verwenden.

### Bearbeiten einer Vorlage – Layout – Vorlagenautor {#editing-a-template-layout-template-author}

Sie können das Vorlagen-Layout für verschiedene Geräte definieren. [Responsives Layout](/help/sites-cloud/authoring/features/responsive-layout.md) funktioniert für Vorlagen ebenso wie für die Seitenbearbeitung.

>[!NOTE]
>
>Änderungen am Layout werden in **Anfänglicher Inhalt** -Modus, jedoch wird keine Änderung in **Struktur** -Modus.

![Vorlagen-Layout bearbeiten](/help/sites-cloud/authoring/assets/templates-edit-layout.png)

### Bearbeiten einer Vorlage – Seitenrichtlinie – Vorlagenautor/Entwickler {#editing-a-template-page-policy-template-author-developer}

Die Seitenrichtlinie einschließlich der erforderlichen Client-seitigen Bibliotheken wird unter der Option **Seitenrichtlinie** im Menü **Seiteninformationen** verwaltet.

So greifen Sie auf das Dialogfeld **Seitenrichtlinie** zu:

1. Wählen Sie im **Vorlageneditor** die Option **Seiteninformationen** aus der Symbolleiste und anschließend die Option **Seitenrichtlinie**, um das Dialogfeld zu öffnen.
1. Das Dialogfeld **Seitenrichtlinie** wird geöffnet. Es ist in zwei Abschnitte unterteilt:

   * Die linke Hälfte definiert die [Seitenrichtlinien](#page-policies).
   * Die rechte Hälfte definiert die [Seiteneigenschaften](#page-properties).

   ![Seiten-Design](/help/sites-cloud/authoring/assets/templates-page-design.png)

#### Seitenrichtlinien {#page-policies}

Sie können eine Inhaltsrichtlinie auf die Vorlage oder resultierende Seiten anwenden. So wird die Inhaltsrichtlinie für das Hauptabsatzsystem auf der Seite definiert.

![Seitenrichtlinie](/help/sites-cloud/authoring/assets/templates-page-policy.png)

* Sie können eine vorhandene Richtlinie für die Seite im Dropdown-Menü **Richtlinie auswählen** auswählen.

  ![Richtlinienauswahl](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

  Sie können eine neue Richtlinie hinzufügen, indem Sie auf die Schaltfläche „Hinzufügen“ klicken, die sich neben dem Dropdown-Menü **Richtlinie auswählen** befindet. Dann muss ein neuer Name in das Feld **Richtlinienname** eingegeben werden.

  ![Schaltfläche „Richtlinie hinzufügen“](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

  Die im Dropdown-Menü **Richtlinie auswählen** ausgewählte vorhandene Richtlinie kann mithilfe der Schaltfläche „Kopieren“, die sich neben dem Dropdown-Menü befindet, kopiert werden. Dann muss ein neuer Name in das Feld **Richtlinienname** eingegeben werden. Standardmäßig erhält die kopierte Richtlinie den Namen **Kopie von X**, wobei X der Titel der kopierten Richtlinie ist.

  ![Schaltfläche „Richtlinie kopieren“](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

* Geben Sie im Feld **Richtlinienname** einen Namen für die Richtlinie an. Eine Richtlinie muss einen Namen tragen, damit sie mühelos im Dropdown-Menü **Richtlinie auswählen** ausgewählt werden kann.

  ![Richtlinienname](/help/sites-cloud/authoring/assets/templates-policy-title.png)

* Eine Beschreibung der Richtlinie im Feld **Richtlinienbeschreibung** ist optional.
* Im Abschnitt **Andere Vorlagen, die ebenfalls die ausgewählte Richtlinie verwenden** ist leicht ersichtlich, welche anderen Vorlagen die Richtlinie verwenden, die in der Dropdown-Liste **Richtlinie auswählen** ausgewählt wurde.

  ![Richtlinienverwendung](/help/sites-cloud/authoring/assets/templates-policy-use.png)

#### Seiteneigenschaften {#page-properties}

Mithilfe der Seiteneigenschaften können Sie die erforderlichen Client-seitigen Bibliotheken definieren, indem Sie das Dialogfeld **Seiten-Design** verwenden. Diese Client-seitigen Bibliotheken enthalten Stylesheets und JavaScript, die zusammen mit der Vorlage und den mit der Vorlage erstellten Seiten geladen werden.

![Seiteneigenschaften](/help/sites-cloud/authoring/assets/templates-page-properties.png)

* Geben Sie die Client-seitigen Bibliotheken an, die auf die mit dieser Vorlage erstellten Seiten angewendet werden sollen. Eingabe des Namens einer Bibliothek in das Textfeld im Bereich **Client-Bibliotheken**.

  ![Client-seitige Bibliotheken](/help/sites-cloud/authoring/assets/templates-client-side-libraries.png)

* Wenn mehrere Bibliotheken erforderlich sind, klicken Sie auf die Schaltfläche „Hinzufügen“, um ein zusätzliches Textfeld für den Namen der Bibliothek hinzuzufügen.

  ![Schaltfläche „Hinzufügen“](/help/sites-cloud/authoring/assets/templates-add-button.png)

  Fügen Sie für Ihre Client-seitigen Bibliotheken so viele Textfelder wie nötig hinzu.

* Definieren Sie bei Bedarf die relative Position der Bibliotheken, indem Sie die Felder mithilfe des Ziehpunkts ziehen.

  ![Ziehpunkt](/help/sites-cloud/authoring/assets/templates-drag-handle.png)

>[!NOTE]
>
>Während der Vorlagenautor die Seitenrichtlinien in der Vorlage festlegt, benötigt er Angaben zu den jeweiligen Client-seitigen Bibliotheken vom Entwickler.

### Bearbeiten einer Vorlage – Anfängliche Seiteneigenschaften – Autor {#editing-a-template-initial-page-properties-author}

Mit der Option **Anfängliche Seiteneigenschaften** können Sie die anfänglichen [Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md) definieren, die bei der Erstellung einer neuen Seite gelten sollen.

1. Wählen Sie im Vorlageneditor **Seiteninformationen** aus der Symbolleiste und anschließend **Anfängliche Seiteneigenschaften**, um das Dialogfeld zu öffnen.

1. Im Dialogfeld können Sie Eigenschaften definieren, die für Seiten gelten sollen, die mit dieser Vorlage erstellt werden.

   ![Vorlagen für anfängliche Seiteneigenschaften](/help/sites-cloud/authoring/assets/templates-initial-properties.png)

1. Bestätigen Sie Ihre Definitionen mit **Fertig**.

## Best Practices {#best-practices}

Beachten Sie beim Erstellen von Vorlagen Folgendes:

1. Die Auswirkungen von Änderungen an der Vorlage, sobald Seiten aus dieser Vorlage erstellt wurden.

   Im Folgenden finden Sie eine Liste der verschiedenen Vorgänge, die für Vorlagen möglich sind, sowie deren Auswirkungen auf die daraus erstellten Seiten:

   * Änderungen an der Struktur:

      * Diese werden sofort auf die resultierenden Seiten angewendet.
      * Die geänderte Vorlage muss veröffentlicht werden, damit Besucher die Änderungen sehen können.

   * Änderungen an Inhaltsrichtlinien und Designkonfigurationen:

      * Diese gelten sofort für die resultierenden Seiten.
      * Die Änderungen müssen veröffentlicht werden, damit Besucher die Änderungen sehen können.

   * Änderungen am anfänglichen Inhalt:

      * Diese gelten nur für Seiten, die nach den Änderungen an der Vorlage erstellt wurden.

   * Änderungen am Layout hängen davon ab, ob die geänderte Komponente Teil von ist:

      * Nur Struktur - sofort angewendet
      * Ursprünglichen Inhalt enthalten - nur auf Seiten, die nach der Änderung erstellt wurden

   Besondere Vorsicht ist erforderlich bei:

   * Sperren oder Entsperren von Komponenten in aktivierten Vorlagen.
   * Dies kann Nebeneffekte haben, da die Komponenten bereits von vorhandenen Seiten verwendet werden können. In der Regel:

      * Das Entsperren von Komponenten (die gesperrt waren) fehlt auf vorhandenen Seiten.
      * Durch das Sperren von Komponenten (die bearbeitbar waren) wird der Inhalt vor der Anzeige auf den Seiten ausgeblendet.

   >[!NOTE]
   >
   >AEM gibt explizite Warnungen aus, wenn der Sperrstatus von Komponenten in Vorlagen geändert wird, bei denen es sich nicht mehr um Entwürfe handelt.

1. [Erstellen eigener Ordner](#creating-a-template-folder-admin) für Ihre Site-spezifischen Vorlagen.
1. [Vorlagen veröffentlichen](#publishing-a-template-template-author) von **Vorlagen** Konsole.
