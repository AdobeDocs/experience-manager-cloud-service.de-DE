---
title: Erstellen und Organisieren von Seiten
description: So erstellen und organisieren Sie Seiten mit AEM
exl-id: c57096ca-34fe-4b19-98e0-8f3cd43cf24e
source-git-commit: 635f4c990c27a7646d97ebd08b453c71133f01b3
workflow-type: tm+mt
source-wordcount: '2542'
ht-degree: 72%

---

# Erstellen und Organisieren von Seiten {#creating-and-organizing-pages}

In diesem Dokument wird beschrieben, wie Sie mit Adobe Experience Manager Cloud Service Seiten erstellen und verwalten können, um auf diesen Seiten [Inhalte zu erstellen](/help/sites-cloud/authoring/fundamentals/editing-content.md).

>[!NOTE]
>
>Ihr Konto muss über die erforderlichen Zugriffsrechte und Berechtigungen verfügen, damit Sie Aktionen auf Seiten durchführen können, beispielsweise das Erstellen, Kopieren, Verschieben, Bearbeiten und Löschen.
>
>Wenn Sie auf Probleme stoßen, empfehlen wir Ihnen, sich an den Systemadministrator zu wenden.

<!--
>Your account needs the [appropriate access rights](/help/sites-administering/security.md) and [permissions](/help/sites-administering/security.md#permissions) to take action on pages such as create, copy, move, edit, and delete.
-->

>[!TIP]
>
>Es steht eine Reihe von [Tastaturbefehlen](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) in der Websites-Konsole zur Verfügung, die eine effizientere Seitenorganisation ermöglichen.

## Website-Organisation {#organizing-your-website}

Als Autor müssen Sie Ihre Website in AEM organisieren. Dazu gehört die Erstellung und Benennung von Inhaltsseiten, sodass:

* Sie müssen leicht in der Authoring-Umgebung auffindbar sein.
* Besucher der Website müssen sie einfach in der Veröffentlichungsumgebung durchsuchen können.

Sie können Ihre Inhalte auch mithilfe von [Ordnern](#creating-a-new-folder) organisieren.

Die Struktur einer Website kann als Baumstruktur gesehen werden, die die Inhaltsseiten enthält. Die Namen dieser Inhaltsseiten werden zur Bildung der URLs verwendet. Die Titel werden zusammen mit dem Seiteninhalt angezeigt.

Im Folgenden sehen Sie als Beispiel die Site [WKND Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de), auf der ein Artikel über Skateparks ( `la-skateparks`) aufgerufen wird:

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
   * Benutzereingaben sind für dieses Feld optional. Wenn kein Name angegeben ist, wird der Name vom Titel abgeleitet. Weitere Informationen finden Sie unter [Seitennamen-Einschränkungen und Best Practices](#page-name-restrictions-and-best-practices).

#### Einschränkungen und Best Practices bei der Seitenbenennung {#page-name-restrictions-and-best-practices}

Der **Seitentitel** und der **Seitenname** können separat erstellt werden, sind aber verwandt:

* Beim Erstellen einer Seite ist nur das **Titelfeld** erforderlich. Wenn bei der Erstellung von Seiten kein **Name** angegeben wird, generiert AEM einen Namen aus den ersten 64 Zeichen des Titels (entsprechend der nachfolgenden Validierung). Nur die ersten 64 Zeichen werden verwendet, um die Best Practice für kurze Seitennamen zu unterstützen.
* Wenn ein Seitenname manuell vom Autor angegeben wird, gilt die Beschränkung von 64 Zeichen nicht, aber andere technische Einschränkungen gelten unter Umständen für die Länge des Seitennamens.

>[!TIP]
>
>Beim Definieren eines Seitennamens ist es sinnvoll, den Seitennamen so kurz wie möglich zu halten, aber so ausdruckstark und erinnerungsstark wie möglich, um ihn für den Leser verständlich zu machen. Weitere Informationen zum `title`-Element finden Sie im [W3C-Styleguide](https://www.w3.org/Provider/Style/TITLE.html).
>
>Denken Sie auch daran, dass einige Browser (z. B. ältere Versionen von IE) nur URLs bis zu einer bestimmten Länge akzeptieren, sodass auch technische Gründe für die Verwendung von kurzen Seitennamen bestehen.

Beim Erstellen einer neuen Seite [validiert AEM den Seitennamen entsprechend den AEM- und JCR-Konventionen](/help/implementing/developing/introduction/naming-conventions.md).

Mindestens zulässig sind die folgenden Zeichen:

* `a` bis `z`
* `A` bis `Z`
* `0` bis `9`
* `_` (Unterstrich)
* `-` (Bindestrich/Minus)

Umfassende Informationen zu allen zulässigen Zeichen finden Sie in den [Benennungskonventionen](/help/implementing/developing/introduction/naming-conventions.md).

>[!NOTE]
>
>Seitennamen sind auf 150 Zeichen begrenzt.

#### Titel {#title}

Wenn Sie für eine neu erstellte Seite nur den **Titel** angeben, leitet AEM den **Namen** für die Seite von dieser Zeichenfolge ab und [validiert den Namen entsprechend den Konventionen von AEM und JCR](/help/implementing/developing/introduction/naming-conventions.md).

A **Titel** -Feld mit ungültigen Zeichen wird akzeptiert, wobei die ungültigen Zeichen im abgeleiteten Namen jedoch ersetzt werden. Beispiel:

| Titel | Abgeleiteter Name |
|---|---|
| Schön | `schoen.html` |
| SC%&amp;&#42;ç+ | `sc---c-.html` |

#### Name {#name}

Wenn Sie beim Erstellen einer neuen Seite einen **Namen** für die Seite angeben, [validiert AEM den Namen gemäß den AEM- und JCR-Konventionen](/help/implementing/developing/introduction/naming-conventions.md). Die Eingabe von ungültigen Zeichen im Feld **Name** ist nicht zulässig. Wenn AEM ungültige Zeichen erkennt, wird das Feld durch eine erläuternde Meldung hervorgehoben.

![Beispiel für die Eingabe eines ungültigen Seitennamens](/help/sites-cloud/authoring/assets/organizing-invalid-name.png)

>[!TIP]
>
>Sie sollten es vermeiden, einen Zwei-Buchstaben-Code gemäß ISO-639-1 als Seitennamen zu verwenden, sofern es sich nicht um einen Sprachstamm handelt.
>
>Siehe [Vorbereiten von Inhalten für die Übersetzung](/help/sites-cloud/administering/translation/preparation.md) für weitere Informationen.

### Vorlagen {#templates}

In AEM gibt eine Vorlage einen speziellen Seitentyp an. Eine Vorlage wird als Grundlage für jede neue Seite verwendet, die erstellt wird.

Die Vorlage definiert die Seitenstruktur, u. a. eine Miniatur und andere Eigenschaften. Beispielsweise könnten Sie unterschiedliche Vorlagen für Produktseiten, Sitemaps und Kontaktangaben verwenden. Vorlagen bestehen aus [Komponenten](#components).

Im Lieferumfang von AEM sind diverse Vorlagen enthalten. Die verfügbaren Vorlagen hängen von der jeweiligen Website ab. Die wichtigsten Felder sind:

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

Nachdem Sie eine Seite erstellt und geöffnet haben, können Sie [Inhalt mithilfe der Komponenten hinzufügen](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component), die im Abschnitt [Komponenten-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).

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

   * Verwendung **Zurück** , um zur Vorlagenauswahl zurückzukehren.

   Die Schlüsselfelder sind:

   * **Titel**:

      * Dies wird dem Benutzer angezeigt und ist obligatorisch.

   * **Name**:

      * Mit diesem Wert wird der URI generiert. Wenn kein Name angegeben ist, wird der Name vom Titel abgeleitet.
      * Wenn Sie beim Erstellen einer neuen Seite einen **Namen** für die Seite angeben, [validiert AEM den Namen entsprechend den Konventionen von AEM und JCR](/help/implementing/developing/introduction/naming-conventions.md).
      * You **kann keine ungültigen Zeichen senden** im **Name** -Feld. Wenn AEM ungültige Zeichen erkennt, wird das Feld hervorgehoben und eine erläuternde Meldung angezeigt, die die Zeichen angibt, die entfernt/ersetzt werden müssen.

   >[!TIP]
   >
   >Siehe [Seitenbenennungskonventionen](#page-naming-conventions).

   Die zum Erstellen einer neuen Seite mindestens erforderlichen Informationen sind die **Titel**.

   ![Angeben des Seitentitels](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. Verwenden Sie **Erstellen**, um den Vorgang abzuschließen und die neue Seite zu erstellen. Im Bestätigungs-Dialogfeld werden Sie gefragt, ob Sie die Seite sofort **öffnen** oder zur Konsole zurückkehren möchten (**Fertig**):

   ![Erfolgreiche Seitenerstellung](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   >[!NOTE]
   >
   >Wenn Sie eine Seite erstellen und dabei einen in diesem Verzeichnis bereits vorhandenen Namen verwenden, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Beispiel: `beach` bereits vorhanden ist, wird eine neue Seite `beach1`.

1. Wenn Sie zur Konsole zurückkehren, wird die neue Seite angezeigt:

   ![Neu erstellte Seite](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!CAUTION]
>
>Nachdem eine Seite erstellt wurde, kann ihre Vorlage nicht mehr geändert werden – es sei denn, Sie [erstellen einen Launch mit einer neuen Vorlage](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template), wobei aber der gesamte bereits vorhandene Inhalt verloren geht.

### Öffnen einer Seite zur Bearbeitung {#opening-a-page-for-editing}

Wenn Sie eine Seite erstellt haben bzw. in der Konsole zu einer bereits vorhandenen Seite navigiert sind, können Sie diese zur Bearbeitung öffnen:

1. Öffnen Sie die **Sites** Konsole.
1. Navigieren Sie zu der Seite, die Sie bearbeiten möchten.
1. Wählen Sie Ihre Seite mit einer der folgenden Methoden aus:

   * [Schnellaktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) und Symbolleiste

   Wählen Sie anschließend das Symbol **Bearbeiten** aus:

   ![Schaltfläche „Bearbeiten“](/help/sites-cloud/authoring/assets/edit.png)

1. Die Seite wird geöffnet und Sie können [Bearbeiten der Seite](/help/sites-cloud/authoring/fundamentals/editing-content.md) nach Bedarf.

>[!NOTE]
>
>Das Navigieren zu anderen Seiten ist im Seiteneditor nur im Vorschaumodus möglich, da Links im Bearbeitungsmodus des Seiteneditors nicht aktiv sind.

### Kopieren und Einfügen einer Seite {#copying-and-pasting-a-page}

Sie können eine Seite und alle zugehörigen Unterseiten an einen neuen Speicherort kopieren:

1. Im **Sites** -Konsole, navigieren Sie zu der Seite, die Sie kopieren möchten.
1. Wählen Sie Ihre Seite mit einer der folgenden Optionen aus:

   * [Schnellaktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) und Symbolleiste

   Und dann **Kopieren** Seitensymbol:

   ![Kopieren](/help/sites-cloud/authoring/assets/copy.png)

1. Navigieren Sie zum Speicherort, an dem Sie die neue Kopie der Seite speichern möchten.
1. Tippen oder klicken Sie auf das Symbol **Einfügen**, das verfügbar wurde.

   ![Einfügen](/help/sites-cloud/authoring/assets/paste.png)

1. Das Dialogfeld „Einfügen“ bietet eine Zusammenfassung der Einfügeoperation und folgende Möglichkeiten:
   * **Neuer Website-Name:** Ändern des Namens der eingefügten Seite
   * **Ohne untergeordnete Seiten einfügen:** Auslassen der untergeordneten Seiten der ausgewählten Seite beim Einfügen (standardmäßig werden die untergeordneten Seiten eingefügt)

   ![Dialogfeld „Einfügen“](/help/sites-cloud/authoring/assets/paste-dialog.png)

1. Tippen oder klicken Sie auf die Schaltfläche **Einfügen**, um die Einfügeoperation zu bestätigen und die neue(n) Seite(n) zu erstellen.

>[!NOTE]
>
>Wenn Sie die Seite an einen Speicherort kopieren, an dem sich bereits eine Seite befindet, deren Name mit dem der ursprünglichen Seite übereinstimmt, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Beispiel: `beach` bereits vorhanden ist, eine neue Seite mit dem Namen `beach` wird `beach1`.

>[!NOTE]
>
>Wenn Sie die Einfügeoperation im Auswahlmodus beginnen, wird dieser automatisch beendet, sobald die Seite kopiert wird.

### Verschieben oder Umbenennen einer Seite {#moving-or-renaming-a-page}

Die Vorgehensweise beim Verschieben oder Umbenennen einer Seite ist im Großen und Ganzen gleich und beide Aktionen werden von demselben Assistenten unterstützt. Dieser Assistent hilft Ihnen bei den folgenden Aktionen:

* Umbenennen einer Seite, ohne sie zu verschieben
* Verschieben der Seite, ohne sie umzubenennen
* Verschieben und gleichzeitiges Umbenennen der Seite

AEM bietet die Möglichkeit, interne Links zu aktualisieren, die auf die Seite verweisen, die umbenannt/verschoben wird. Dies kann seitenweise erfolgen, um volle Flexibilität zu bieten.

1. Navigieren Sie zu der Seite, die Sie verschieben möchten.
1. Wählen Sie Ihre Seite mit einer der folgenden Optionen aus:

   * [Schnellaktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) und Symbolleiste

   Wählen Sie anschließend die **Verschieben** Seitensymbol:

   ![Schaltfläche „Verschieben“](/help/sites-cloud/authoring/assets/move.png)

   Dadurch wird der Assistent zum Verschieben von Seiten geöffnet.

1. Aus dem **Umbenennen** Schritt des Assistenten können Sie entweder:

   * Geben Sie den Namen an, den die Seite nach dem Verschieben aufweisen soll, und tippen/klicken Sie dann auf **Weiter**, um den Vorgang fortzusetzen.
   * Mit **Abbrechen** brechen Sie den Vorgang ab.

   ![Verschieben und Umbenennen einer Seite](/help/sites-cloud/authoring/assets/move-page-rename.png)

   Der Seitenname kann unverändert bleiben, wenn Sie nur die Seite verschieben.

   >[!NOTE]
   >
   >Wenn Sie die Seite an einen Speicherort verschieben, an dem sich bereits eine Seite befindet, deren Name mit dem der ursprünglichen Seite übereinstimmt, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn beispielsweise `beach` bereits vorhanden ist, eine neue Seite mit dem Namen `beach` wird `beach1`.

1. Aus dem **Ziel auswählen** Schritt des Assistenten können Sie entweder:

   * Verwenden Sie die [Spaltenansicht](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) , um zum neuen Speicherort für die Seite zu navigieren:

      * Wählen Sie das Ziel für die Seite aus, indem Sie auf die Miniatur des Ziels klicken.
      * Klicken Sie auf **Weiter**, um fortzufahren.

   * Verwendung **Zurück** , um zur Seitennamenspezifikation zurückzukehren.

   >[!NOTE]
   >
   >Standardmäßig wird das übergeordnete Element der Seite, die Sie verschieben oder umbenennen, als Ziel ausgewählt.

   ![Auswählen eines Seitenverschiebungsziels](/help/sites-cloud/authoring/assets/move-page-destination.png)

   >[!NOTE]
   >
   >Wenn Sie die Seite an einen Speicherort verschieben, an dem sich bereits eine Seite befindet, deren Name mit dem der ursprünglichen Seite übereinstimmt, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn beispielsweise `winter` bereits existiert, `winter` wird `winter1`.

1. Wenn die Seite verknüpft ist oder darauf verwiesen wird oder veröffentlicht wurde, werden die Details im **Anpassen/Erneutes Veröffentlichen** Schritt.

   Sie können angeben, welche Verweise ggf. angepasst und neu veröffentlicht werden sollen.

   >[!NOTE]
   >
   >Wenn die Seite weder verknüpft ist noch darauf verwiesen wurde, ist dieser Schritt nicht verfügbar.

   ![Erneutes Veröffentlichen einer Seite nach Verschiebung](/help/sites-cloud/authoring/assets/move-page-republish.png)

1. Auswählen **Verschieben** schließt den Prozess ab und verschiebt/umbenennt Ihre Seite nach Bedarf.

>[!NOTE]
>
>Wenn die Seite bereits veröffentlicht wurde, wird die Veröffentlichung durch Verschieben der Seite automatisch aufgehoben. Standardmäßig wird sie nach Abschluss des Verschiebevorgangs erneut veröffentlicht. Dies kann jedoch geändert werden, indem Sie die Option **Neu veröffentlichen** im Feld **Anpassen/Erneutes Veröffentlichen** Schritt.

>[!NOTE]
>
>Wenn auf die Seite in keiner Weise verwiesen wird, wird die **Anpassen/Erneutes Veröffentlichen** -Schritt übersprungen wird.

>[!NOTE]
>
>Das Umbenennen einer Seite unterliegt auch dem [Seitenbenennungskonventionen](#page-naming-conventions) beim Angeben des neuen Seitennamens.

>[!NOTE]
>
>Eine Seite kann nur an einen Ort verschoben werden, an dem die Vorlage, auf der die Seite basiert, zulässig ist. Weitere Informationen finden Sie unter [Formularverfügbarkeit](/help/implementing/developing/components/templates.md#template-availability).

#### Asynchrone Aktionen {#asynchronous-actions}

Normalerweise wird eine Aktion zum Verschieben oder Umbenennen von Seiten sofort ausgeführt. Dies gilt als synchrone Verarbeitung und weitere Aktionen in der Benutzeroberfläche werden blockiert, bis die Aktion abgeschlossen ist.

Wenn die Anzahl der betroffenen Seiten jedoch über einem definierten Limit liegt, wird die Aktion asynchron verarbeitet, sodass der Benutzer die Bearbeitung in der Benutzeroberfläche fortsetzen kann, ohne durch die Aktion zum Verschieben oder Umbenennen der Seite behindert zu werden.

* Wenn Sie im letzten Schritt oben auf **Verschieben** klicken, prüft AEM die konfigurierte Beschränkung.
* Wenn die Anzahl der betroffenen Seiten unter der Grenze liegt, wird ein synchroner Vorgang ausgeführt.
* Wenn die Anzahl der betroffenen Seiten über der Grenze liegt, wird ein asynchroner Vorgang ausgeführt.
   * Der Benutzer muss definieren, wann der asynchrone Vorgang ausgeführt werden soll.
      * **Jetzt** startet die Ausführung des asynchronen Auftrags sofort.
      * **Später** erlaubt es dem Benutzer zu definieren, wann der asynchrone Auftrag starten wird.

        ![Asynchrone Seitenverschiebung](/help/sites-cloud/authoring/assets/asynchronous-page-move.png)

Der Status asynchroner Aufträge kann im Dashboard [**Status asynchroner Aufträge**](/help/operations/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations) unter **Globale Navigation** > **Tools** > **Vorgänge** > **Aufträge** überprüft werden.

>[!NOTE]
>
>Weitere Informationen zur asynchronen Auftragsverarbeitung und zum Konfigurieren der Begrenzung für Seitenverschiebungs-/-umbenennungsaktionen finden Sie im Dokument [Asynchrone Aufträge](/help/operations/asynchronous-jobs.md) im Benutzerhandbuch für den Betrieb.

### Löschen einer Seite {#deleting-a-page}

1. Navigieren Sie zu der Seite, die Sie löschen möchten.
1. Wählen Sie mit dem [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) die gewünschte Seite aus, bevor Sie in der Symbolleiste die Option **Löschen** auswählen:

   ![Schaltfläche „Löschen“](/help/sites-cloud/authoring/assets/delete.png)

   >[!NOTE]
   >
   >Als Sicherheitsmaßnahme ist das Symbol **Löschen** nicht per Schnellzugriff verfügbar.

1. Ein Bestätigungsdialogfeld wird angezeigt.

   ![Dialogfeld „Löschen“](/help/sites-cloud/authoring/assets/delete-page.png)

   * **Möchten Sie Seiten vor dem Löschen archivieren?** - Wenn diese Option aktiviert ist, werden beim Löschen Versionen der zu löschenden Seiten erstellt.
      * [Versionen können zu einem späteren Zeitpunkt wiederhergestellt werden.](/help/sites-cloud/authoring/features/page-versions.md)
      * Seiten, die ohne vorherige Versionen gelöscht wurden, können nicht wiederhergestellt werden.
   * **Abbrechen** , um die Aktion abzubrechen
   * Mit **Löschen** bestätigen Sie die Aktion.

      * Wenn die Seite keine Verweise enthält, wird die Seite gelöscht.
      * Wenn die Seite Verweise enthält, werden Sie in einem Meldungsfeld darauf hingewiesen, dass **eine oder mehrere Seiten über einen Verweis verfügen**. Sie können **Löschen erzwingen** oder **Abbrechen** auswählen.

>[!NOTE]
>
>Wenn eine Seite bereits veröffentlicht ist, wird ihre Veröffentlichung vor dem Löschen automatisch rückgängig gemacht.

### Sperren einer Seite {#locking-a-page}

Sie können entweder in einer Konsole oder beim Bearbeiten einer Seite eine [Seite sperren/entsperren](/help/sites-cloud/authoring/fundamentals/editing-content.md#locking-a-page). Informationen darüber, ob eine Seite gesperrt ist, werden auch an beiden Stellen angezeigt.

![Schaltfläche „Sperren“](/help/sites-cloud/authoring/assets/lock.png) ![Schaltfläche „Entsperren“](/help/sites-cloud/authoring/assets/unlock.png)

### Erstellen eines neuen Ordners {#creating-a-new-folder}

Sie können Ordner erstellen, um Ihre Dateien und Seiten zu organisieren.

1. Öffnen Sie die **Sites** und navigieren Sie zum gewünschten Speicherort.
1. Um die Optionsliste zu öffnen, wählen Sie **Erstellen** über die Symbolleiste
1. Auswählen **Ordner** , um das Dialogfeld zu öffnen. Hier können Sie den **Namen** und den **Titel** eingeben:

   ![Ordner erstellen](/help/sites-cloud/authoring/assets/organizing-create-folder.png)

1. Wählen Sie **Erstellen**, um den Ordner zu erstellen.

>[!NOTE]
>
>Ordner unterliegen auch dem [Seitenbenennungskonventionen](#page-naming-conventions) beim Angeben des neuen Ordnernamen.

>[!CAUTION]
>
>* Ordner können nur direkt unter **Sites** oder unter anderen Ordnern. Sie können nicht unter einer Seite erstellt werden.
>* Für einen Ordner können folgende Standardaktionen ausgeführt werden: Verschieben, Kopieren, Einfügen, Löschen, Veröffentlichen, Rückgängigmachen der Veröffentlichung und Anzeigen/Bearbeiten von Eigenschaften.
>* Ordner sind in einer Live Copy nicht als Auswahl verfügbar.
