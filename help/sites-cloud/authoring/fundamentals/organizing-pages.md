---
title: Erstellen und Organisieren von Seiten
description: So erstellen und organisieren Sie Seiten mit AEM
translation-type: ht
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Erstellen und Organisieren von Seiten {#creating-and-organizing-pages}

In diesem Dokument wird beschrieben, wie Sie mit Adobe Experience Manager Cloud Service Seiten erstellen und verwalten können, um auf diesen Seiten [Inhalte zu erstellen](/help/sites-cloud/authoring/fundamentals/editing-content.md).

>[!NOTE]
>
>Ihr Konto muss über die erforderlichen Zugriffsrechte und Berechtigungen verfügen, damit Sie Aktionen auf Seiten durchführen können, beispielsweise Erstellen, Kopieren, Verschieben, Bearbeiten und Löschen.
>
>Wenn Sie auf Probleme stoßen, empfehlen wir Ihnen, sich an den Systemadministrator zu wenden.

<!--
>Your account needs the [appropriate access rights](/help/sites-administering/security.md) and [permissions](/help/sites-administering/security.md#permissions) to take action on pages such as create, copy, move, edit, and delete.
-->

>[!TIP]
>
>Es steht eine Reihe von [Tastaturbefehlen](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) in der Websites-Konsole zur Verfügung, die eine effizientere Seitenorganisation ermöglichen.

## Website-Organisation {#organizing-your-website}

Als Autor müssen Sie Ihre Website in AEM organisieren. Aus diesem Grund müssen Sie Ihre Inhaltsseiten entsprechend folgenden Richtlinien erstellen und benennen:

* Sie müssen leicht in der Autorenumgebung auffindbar sein.
* Besucher der Website müssen sie einfach in der Veröffentlichungsumgebung durchsuchen können.

Sie können Ihre Inhalte auch mithilfe von [Ordnern](#creating-a-new-folder) organisieren.

Die Struktur einer Website kann als Baumstruktur gesehen werden, die die Inhaltsseiten enthält. Die Namen dieser Inhaltsseiten werden zur Bildung der URLs verwendet. Die Titel werden zusammen mit dem Seiteninhalt angezeigt.

Im Folgenden sehen Sie als Beispiel die Site [WKND Tutorial](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html), auf der ein Artikel über Skateparks ( `la-skateparks`) aufgerufen wird:

`http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

```xml
 /content
 /wknd
  /en
   /music
    /...
   /sports
    /la-skateparks
    /five-gyms-la
    /mountain-bike-routes
   /shopping
    /...
   /art
    /...
   /...
```

Diese Struktur kann über die **Sites-Konsole** angezeigt werden. Von dort aus können Sie [durch die Seiten Ihrer Website navigieren](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) und Aktionen auf den Seiten durchführen. Sie können auch neue Sites und [neue Seiten](#creating-a-new-page) erstellen.

An jedem Punkt können Sie die Verzwigung nach oben in den Breadcrumbs in der Kopfzeilenleiste sehen:

![Navigieren mit Breadcrumbs](/help/sites-cloud/authoring/assets/organizing-breadcrumbs.png)

### Seitenbenennungskonventionen {#page-naming-conventions}

Beim Erstellen einer neuen Seite gibt es zwei Schlüsselfelder:

* **[Titel](#title)**:

   * Dieses Feld wird dem Benutzer bei der Bearbeitung im oberen Teil des Seiteninhalts in der Konsole angezeigt.
   * Dieses Feld ist obligatorisch.

* **[Name](#name)**:

   * Mit diesem Wert wird der URI generiert.
   * Benutzereingaben sind für dieses Feld optional. Wenn kein Name angegeben ist, wird er vom Titel abgeleitet. Weitere Informationen finden Sie unter [Seitennamen-Einschränkungen und Best Practices](#page-name-restrictions-and-best-practices). 

#### Seitennamen-Einschränkungen und Best Practices {#page-name-restrictions-and-best-practices}

Der **Seitentitel** und der **Seitenname** können separat erstellt werden, sind aber verwandt:

* Beim Erstellen einer Seite ist nur das **Titelfeld** erforderlich.  Wenn bei der Erstellung von Seiten kein **Name** angegeben wird, generiert AEM einen Namen aus den ersten 64 Zeichen des Titels (entsprechend der nachfolgenden Validierung).  Nur die ersten 64 Zeichen werden verwendet, um gängige Best Practices für kurze Seitennamen zu unterstützen.
* Wenn ein Seitenname manuell vom Autor angegeben wird, gilt die Beschränkung von 64 Zeichen nicht, aber andere technische Einschränkungen gelten unter Umständen für die Länge des Seitennamens.

>[!TIP]
>
>Beim Definieren eines Seitennamens ist es sinnvoll, den Seitennamen so kurz wie möglich zu halten, aber so ausdruckstark und erinnerungsstark wie möglich, um ihn für den Leser verständlich zu machen. Weitere Informationen zum `title`-Element finden Sie im [W3C-Styleguide](https://www.w3.org/Provider/Style/TITLE.html).
>
>Denken Sie auch daran, dass einige Browser (z. B. ältere Versionen von IE) nur URLs bis zu einer bestimmten Länge akzeptieren, sodass auch technisch Gründe für die Verwendung von kurzen Seitennamen bestehen.

Beim Erstellen einer neuen Seite validiert AEM den Seitennamen entsprechend den AEM- und JCR-Konventionen. <!--When creating a new page, AEM will [validate the page name according to the conventions](/help/sites-developing/naming-conventions.md) imposed by AEM and the JCR.-->

Mindestens zulässig sind die folgenden Zeichen:

* `a` bis `z`
* `A` bis `Z`
* `0` bis `9`
* `_` (Unterstrich)
* `-` (Bindestrich/Minus)

Umfassende Informationen zu allen zulässigen Zeichen finden Sie in den Benennungskonventionen. <!--Full details of all characters allowed can be found in [the naming conventions](/help/sites-developing/naming-conventions.md).-->

>[!NOTE]
>
>Seitennamen sind auf 150 Zeichen begrenzt.

#### Titel {#title}

Wenn Sie für eine neu erstellte Seite nur den **Titel** angeben, leitet AEM den **Namen** für die Seite von dieser Zeichenfolge ab und validiert den Namen entsprechend den Konventionen von AEM und JCR. <!--If you supply only a page **Title** when creating a new page, AEM will derive the page **Name** from this string and [validate the name according to the conventions](/help/sites-developing/naming-conventions.md) imposed by AEM and JCR.-->

Im Feld **Titel** werden ungültige Zeichen akzeptiert, wobei die ungültigen Zeichen im abgeleiteten Namen jedoch ersetzt werden. Beispiel:

| Titel | Abgeleiteter Name |
|---|---|
| Schön | `schoen.html` |
| SC%&amp;*ç+ | `sc---c-.html` |

#### Name {#name}

Wenn Sie beim Erstellen einer neuen Seite einen **Namen** für die Seite angeben, validiert AEM den Namen gemäß den AEM- und JCR-Konventionen. Eine Eingabe von ungültigen Zeichen im Feld **Name** ist nicht zulässig. Wenn AEM ungültige Zeichen erkennt, wird das Feld hervorgehoben. <!--When you supply a page **Name** when creating a new page, AEM will [validate the name according to the conventions](/help/sites-developing/naming-conventions.md) imposed by AEM and JCR. You cannot submit invalid characters in the **Name** field. When AEM detects invalid characters the field will be highlighted with an explanatory message.-->

![Beispiel für die Eingabe eines ungültigen Seitennamens](/help/sites-cloud/authoring/assets/organizing-invalid-name.png)

>[!TIP]
>
>Sie sollten es vermeiden, einen Zwei-Buchstaben-Code gemäß ISO-639-1 als Seitennamen zu verwenden, sofern es sich nicht um einen Sprachstamm handelt.
>
>Weitere Informationen finden Sie unter „Vorbereiten von Inhalten für die Übersetzung“.
<!--
>See [Preparing Content for Translation](/help/sites-administering/tc-prep.md) for more information.
-->

### Vorlagen {#templates}

In AEM sind bestimmte Seitentypen in Vorlagen gespeichert. Eine Vorlage wird als Basis für jede neue erstellte Seite verwendet.

Die Vorlage definiert die Seitenstruktur, u. a. eine Miniaturansicht und andere Eigenschaften. Beispielsweise könnten Sie unterschiedliche Vorlagen für Produktseiten, Sitemaps und Kontaktangaben verwenden. Vorlagen bestehen aus [Komponenten](#components).

Im Lieferumfang von AEM sind diverse Vorlagen enthalten. Welche Vorlagen verfügbar sind, hängt von der jeweiligen Website ab. Die wichtigsten Felder sind:

* **Titel**
Der Titel, der auf der resultierenden Web-Seite angezeigt wird.

* **Name**
Wird beim Benennen der Seite verwendet.

* **Vorlage**
Eine Liste von Vorlagen, die für das Erstellen neuer Seiten verwendet werden können.

>[!TIP]
>
>Sofern auf Ihrer Instanz konfiguriert, [können Vorlagenautoren Vorlagen mit dem Vorlageneditor erstellen](/help/sites-cloud/authoring/features/templates.md).

### Komponenten {#components}

Komponenten sind die Elemente, die von AEM bereitgestellt werden, damit Sie bestimmte Inhaltstypen hinzufügen können. AEM ist mit einsatzbereiten Komponenten ausgestattet, die umfangreiche Funktionen bieten, wie:

* Text
* Bild
* Titel
* Karussell
* Und viele weitere

Nachdem Sie eine Seite erstellt und geöffnet haben, können Sie mithilfe der im [Komponenten-Browser](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component) verfügbaren Komponenten [Inhalte hinzufügen](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).

>[!TIP]
>
>Die [Komponentenkonsole](/help/sites-cloud/authoring/features/components-console.md) bietet einen Überblick über die Komponenten in Ihrer Instanz.

## Verwalten von Seiten {#managing-pages}

### Erstellen einer neuen Seite {#creating-a-new-page}

Bevor Sie mit der Erstellung von Inhalten beginnen können, müssen Sie eine Seite erstellen, es sei denn, alle Seiten wurden bereits für Sie erstellt:

1. Öffnen Sie die Sites-Konsole (z. B. `https://<host>:<port>/sites.html/content`).
1. Navigieren Sie zu der Position, an der Sie die neue Seite erstellen möchten.
1. Öffnen Sie das Dropdown-Menü über **Erstellen** in der Symbolleiste und wählen Sie in der Liste **Seite** aus:

   ![Erstellen von Seiten](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. Im ersten Schritt des Assistenten haben Sie folgende Möglichkeiten:

   * Wählen Sie die Vorlage, die Sie zum Erstellen der neuen Seite verwenden möchten, und klicken/tippen Sie auf **Weiter**, um fortzufahren.

   * Mit **Abbrechen** brechen Sie den Vorgang ab.
   ![Auswählen einer Vorlage für eine neue Seite](/help/sites-cloud/authoring/assets/organizing-create-page-template.png)

1. Im letzten Schritt des Assistenten haben Sie folgende Möglichkeiten:

   * Geben Sie auf den drei Registerkarten die [Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md) ein, die Sie der neuen Seite zuweisen möchten, und klicken bzw. tippen Sie dann auf **Erstellen**, um die Seite zu erstellen.

   * Verwenden Sie **Zurück**, um zur Vorlagenauswahl zurückzukehren.
   Die Schlüsselfelder sind:

   * **Titel**:

      * Dieser wird dem Benutzer angezeigt und muss angegeben werden.
   * **Name**:

      * Mit diesem Wert wird der URI generiert. Wenn kein Name angegeben ist, wird er vom Titel abgeleitet.
      * Wenn Sie beim Erstellen einer neuen Seite einen **Namen** für die Seite angeben, validiert AEM den Namen entsprechend den Konventionen von AEM und JCR. <!--If you supply a page **Name** when creating a new page, AEM will [validate the name according to the conventions](/help/sites-developing/naming-conventions.md) imposed by AEM and JCR.-->
      * Die **Eingabe von ungültigen Zeichen** im Feld **Name** ist nicht zulässig. Wenn AEM ungültige Zeichen erkennt, wird das Feld markiert und eine erklärende Meldung angezeigt, die auf zu entfernende/ersetzende Zeichen verweist.
   >[!TIP]
   >
   >Weitere Informationen finden Sie unter [Benennungskonventionen für Seiten](#page-naming-conventions).

   Zum Erstellen einer neuen Seite muss zumindest der **Titel** angegeben werden.

   ![Angeben des Seitentitels](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. Verwenden Sie **Erstellen**, um den Vorgang abzuschließen und die neue Seite zu erstellen. Im Bestätigungs-Dialogfeld werden Sie gefragt, ob Sie die Seite sofort **öffnen** oder zur Konsole zurückkehren möchten (**Fertig**):

   ![Erfolgreiche Seitenerstellung](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   >[!NOTE]
   >
   >Wenn Sie eine Seite erstellen und dabei einen in diesem Verzeichnis bereits vorhandenen Namen verwenden, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn beispielsweise `beach` bereits vorhanden ist, wird eine neue Seite `beach1` genannt.

1. Wenn Sie zur Konsole zurückkehren, wird die neue Seite angezeigt:

   ![Neu erstellte Seite](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!CAUTION]
>
>Nachdem eine Seite erstellt wurde, kann ihre Vorlage nicht mehr geändert werden – es sei denn, Sie [erstellen einen Launch mit einer neuen Vorlage](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template), wobei aber der gesamte bereits vorhandene Inhalt verloren geht.

### Öffnen einer Seite zur Bearbeitung {#opening-a-page-for-editing}

Wenn Sie eine Seite erstellt haben bzw. in der Konsole zu einer bereits vorhandenen Seite navigiert sind, können Sie diese zur Bearbeitung öffnen:

1. Öffnen Sie die **Sites-Konsole**.
1. Navigieren Sie zu der Seite, die Sie bearbeiten möchten.
1. Wählen Sie die Seite aus, indem Sie wahlweise Folgendes verwenden:

   * [Schnellaktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) und Symbolleiste
   Wählen Sie anschließend das Symbol **Bearbeiten** aus:

   ![Schaltfläche „Bearbeiten“](/help/sites-cloud/authoring/assets/edit.png)

1. Die Seite wird geöffnet und Sie können [die Seite bearbeiten](/help/sites-cloud/authoring/fundamentals/editing-content.md).

>[!NOTE]
>
>Das Navigieren zu anderen Seiten ist im Seiten-Editor nur im Vorschaumodus möglich, da Links im Bearbeitungsmodus des Seiten-Editors nicht aktiv sind.

### Kopieren und Einfügen einer Seite   {#copying-and-pasting-a-page}

Sie können eine Seite und alle zugehörigen Unterseiten an einen neuen Speicherort kopieren:

1. Navigieren Sie in der **Sites-Konsole** zu der Seite, die Sie kopieren möchten.
1. Wählen Sie die Seite aus, indem Sie wahlweise Folgendes verwenden:

   * [Schnellaktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) und Symbolleiste
   Wählen Sie anschließend das Symbol **Seite kopieren** aus:

   ![Schaltfläche „Kopieren“](/help/sites-cloud/authoring/assets/copy.png)

   >[!NOTE]
   >
   >Wenn Sie sich im Auswahlmodus befinden, wird dieser automatisch beendet, sobald die Seite kopiert wird.

1. Navigieren Sie zum Speicherort, an dem Sie die neue Kopie der Seite speichern möchten.
1. Verwenden Sie das Symbol **Einfügen**:

   ![Schaltfläche „Einfügen“](/help/sites-cloud/authoring/assets/paste.png)

   In diesem Verzeichnis wird eine Kopie der ursprünglichen Seite und aller Unterseiten erstellt.

   >[!NOTE]
   >
   >Wenn Sie die Seite an einen Speicherort kopieren, an dem sich bereits eine Seite befindet, deren Name mit dem der ursprünglichen Seite übereinstimmt, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn `beach` zum Beispiel bereits vorhanden ist, wird eine neue Seite mit dem Namen `beach` zu `beach1`.

### Verschieben oder Umbenennen einer Seite {#moving-or-renaming-a-page}

Die Vorgehensweise beim Verschieben oder Umbenennen einer Seite ist im Großen und Ganzen gleich und wird von demselben Assistenten unterstützt. Dieser Assistent hilft Ihnen bei den folgenden Aktionen:

* Umbenennen einer Seite, ohne sie zu verschieben
* Verschieben der Seite, ohne sie umzubenennen
* Verschieben und gleichzeitiges Umbenennen der Seite

AEM bietet die Möglichkeit, interne Links zu aktualisieren, die auf die Seite verweisen, die umbenannt oder verschoben wird. Dies kann seitenweise erfolgen, um die volle Flexibilität zu ermöglichen.

1. Navigieren Sie zu der Seite, die Sie verschieben möchten.
1. Wählen Sie die Seite aus, indem Sie wahlweise Folgendes verwenden:

   * [Schnellaktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) und Symbolleiste
   Wählen Sie anschließend das Symbol **Verschieben** aus:

   ![Schaltfläche „Verschieben“](/help/sites-cloud/authoring/assets/move.png)

   Daraufhin wird der Assistent zum Verschieben von Seiten geöffnet.

1. Im Schritt des Assistenten für das **Umbenennen** haben Sie folgende Möglichkeiten:

   * Geben Sie den Namen an, den die Seite nach dem Verschieben aufweisen soll, und tippen/klicken Sie dann auf **Weiter**, um den Vorgang fortzusetzen.
   * Mit **Abbrechen** brechen Sie den Vorgang ab.
   ![Verschieben und Umbenennen einer Seite](/help/sites-cloud/authoring/assets/move-page-rename.png)

   Der Seitenname kann unverändert bleiben, wenn Sie die Seite nur verschieben.

   >[!NOTE]
   >
   >Wenn Sie die Seite an einen Speicherort verschieben, an dem sich bereits eine Seite befindet, deren Name mit dem der ursprünglichen Seite übereinstimmt, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn `beach` zum Beispiel bereits vorhanden ist, wird eine neue Seite mit dem Namen `beach` zu `beach1`.

1. Im Schritt **Ziel auswählen** des Assistenten können Sie entweder:

   * Die [Spaltenansicht](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) verwenden, um zum neuen Speicherort der Seite zu navigieren:

      * Wählen Sie das Ziel für die Seite aus, indem Sie auf die Miniaturansicht des Ziels klicken. 
      * Klicken Sie auf **Weiter**, um fortzufahren.
   * Mit **Zurück** zur Angabe des Asset-Namens zurückkehren.
   >[!NOTE]
   >
   >Standardmäßig wird das übergeordnete Element der Seite, die Sie verschieben/umbenennen, als Ziel ausgewählt.

   ![Auswählen eines Seitenverschiebungsziels](/help/sites-cloud/authoring/assets/move-page-destination.png)

   >[!NOTE]
   >
   >Wenn Sie die Seite an einen Speicherort verschieben, an dem sich bereits eine Seite befindet, deren Name mit dem der ursprünglichen Seite übereinstimmt, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn `winter` beispielsweise bereits existiert, wird `winter` zu `winter1`.

1. Wenn die Seite verknüpft ist oder darauf verwiesen wird, werden die Details im Schritt **Anpassen/Erneut veröffentlichen** aufgeführt.

   Sie können angeben, welche Verweise ggf. angepasst und neu veröffentlicht werden sollen.

   >[!NOTE]
   >
   >Wenn die Seite weder verknüpft ist noch darauf verwiesen wurde, ist dieser Schritt nicht verfügbar.

   ![Erneutes Veröffentlichen einer Seite nach Verschiebung](/help/sites-cloud/authoring/assets/move-page-republish.png)

1. Wenn Sie **Verschieben** auswählen, wird der Vorgang abgeschlossen und Ihre Seite verschoben oder umbenannt.

>[!NOTE]
>
>Wenn eine Seite bereits veröffentlicht wurde, wird ihre Veröffentlichung durch Verschieben der Seite automatisch rückgängig gemacht. Standardmäßig wird sie nach Abschluss des Verschiebevorgangs erneut veröffentlicht. Dies lässt sich jedoch ändern, indem Sie im Schritt **Anpassen/Erneut veröffentlichen** das Kontrollkästchen **Neu veröffentlichen** deaktivieren.

>[!NOTE]
>
>Wenn es keine Verweise auf die Seite gibt, wird der Schritt **Anpassen/Erneut veröffentlichen** übersprungen.

>[!NOTE]
>
>Beim Umbenennen einer Seite gelten ebenfalls die [Benennungskonventionen für Seiten](#page-naming-conventions), wenn der neue Seitenname angegeben wird.

>[!NOTE]
>
>Eine Seite kann nur an einen Speicherort verschoben werden, an dem die Vorlage zulässig ist, auf der die Seite basiert. Weitere Informationen finden Sie unter „Formularverfügbarkeit“.
<!--
>A page can only be moved to a location where the template upon which the page is based is allowed. See [Template Availability](/help/sites-developing/templates.md#template-availability) for more information.
-->

### Löschen einer Seite {#deleting-a-page}

1. Navigieren Sie zu der Seite, die Sie löschen möchten.
1. Wählen Sie mit dem [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) die gewünschte Seite aus, bevor Sie in der Symbolleiste die Option **Löschen** auswählen:

   ![Schaltfläche „Löschen“](/help/sites-cloud/authoring/assets/delete.png)

   >[!NOTE]
   >
   >Aus Sicherheitsgründen ist das Symbol **Löschen** nicht als Schnellaktion verfügbar.

1. Es wird ein Bestätigungsdialogfeld angezeigt.

   * Mit **Abbrechen** können Sie den Vorgang abbrechen.
   * **Löschen** bestätigen Sie die Aktion.

      * Wenn die Seite keine Referenzen aufweist, wird die Seite gelöscht.
      * Wenn die Seite Verweise enthält, werden Sie in einem Meldungsfeld darauf hingewiesen, dass **eine oder mehrere Seiten über einen Verweis verfügen**. Sie können **Löschen erzwingen** oder **Abbrechen** auswählen.

>[!NOTE]
>
>Wenn eine Seite bereits veröffentlicht ist, wird ihre Veröffentlichung vor dem Löschen automatisch rückgängig gemacht.

### Sperren einer Seite {#locking-a-page}

Sie können entweder in einer Konsole oder beim Bearbeiten einer Seite eine [Seite sperren/entsperren](/help/sites-cloud/authoring/fundamentals/editing-content.md#locking-a-page). Auch Angaben dazu, ob eine Seite gesperrt ist, werden in beiden Fällen angezeigt.

![Schaltfläche „Sperren“](/help/sites-cloud/authoring/assets/lock.png) ![Schaltfläche „Entsperren“](/help/sites-cloud/authoring/assets/unlock.png)

### Erstellen eines neuen Ordners {#creating-a-new-folder}

Sie können Ordner erstellen, um Ihre Dateien und Seiten zu organisieren.

1. Öffnen Sie die **Sites-Konsole** und navigieren Sie zum gewünschten Ort.
1. Um das Optionsmenü zu öffnen, wählen Sie **Erstellen** in der Symbolleiste.
1. Wählen Sie **Ordner**, um das Dialogfeld zu öffnen. Hier können Sie den **Namen** und den **Titel** eingeben:

   ![Ordner erstellen](/help/sites-cloud/authoring/assets/organizing-create-folder.png)

1. Wählen Sie **Erstellen**, um den Ordner zu erstellen.

>[!NOTE]
>
>Für Ordner gelten ebenfalls die [Benennungskonventionen für Seiten](#page-naming-conventions), wenn der neue Ordnername angegeben wird.

>[!CAUTION]
>
>* Ordner können nur direkt unter **Sites** oder unter anderen Ordnern erstellt werden. Sie können jedoch nicht unter einer Seite erstellt werden.
>* Für einen Ordner können folgende Standardaktionen ausgeführt werden: Verschieben, Kopieren, Einfügen, Löschen, Veröffentlichen, Rückgängigmachen der Veröffentlichung und Anzeigen/Bearbeiten von Eigenschaften.
>* Ordner sind in einer Live Copy nicht als Auswahl verfügbar.

