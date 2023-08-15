---
title: Grundlagen zum Authoring
description: Erfahren Sie mehr über die Konzepte und Mechanismen sw Authoring für Ihr Headless-CMS mithilfe von Inhaltsfragmenten.
exl-id: 3eca973f-b210-41bb-98da-ecbd2bae9803
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '1714'
ht-degree: 83%

---

# Grundlagen zum Authoring für Headless mit AEM {#author-headless-basics}

## Die bisherige Entwicklung {#story-so-far}

Zu Beginn der [AEM Headless-Inhaltsautoren-Tour](overview.md) wurden in der [Einführung](introduction.md) die grundlegenden Konzepte und die Terminologie für das Authoring für Headless behandelt.

Dieser Artikel baut auf diesen auf, damit Sie verstehen, wie Sie eigene Inhalte für Ihr AEM Headless-Projekt erstellen und bearbeiten können.

## Ziel {#objective}

* **Zielgruppe**: Anfänger
* **Ziel**: Einführung in die Grundlagen das Headless-CMS-Authoring:
   * Einführung in das Authoring mit AEMaaCS
   * Einführung in Inhaltsfragmente

## Grundlegende Handhabung {#basic-handling}

Bevor Sie mit Inhaltsfragmenten umgehen, hier eine (sehr) kurze Einführung in die Verwendung von AEM...aber nichts ersetzt das Erlebnis, sich anzumelden und zu versuchen, das System zu verwenden.

### Authoring, Vorschau und Veröffentlichung {#author-preview-publish}

Eine AEM Installation besteht im Allgemeinen aus drei Umgebungen:

* Autor
* Veröffentlichung
* Vorschau

Sie melden sich an und verwenden die Autorenumgebung, um Ihre Inhalte zu erzeugen. Wenn Sie fertig sind, veröffentlichen Sie Ihre Inhalte, damit sie allgemein verfügbar werden. Für Headless wäre dies für andere Anwendungen, für Web-Seiten wäre dies für Leser im Internet.

Weitere Informationen finden Sie unter „Authoring-Konzepte“.

Aus dem **Inhaltsfragmente** -Konsole können Sie auch in der **Vorschaufunktion**, zum Testen und zur Vorschau vor der Veröffentlichung. Siehe Veröffentlichen und Anzeigen einer Vorschau eines Fragments .

### Anmeldung {#signing-in}

Wie bei den meisten Systemen müssen Sie sich anmelden. Als Autor erhalten Sie Folgendes:

* Name des Benutzers (Konto)
* Passwort
* Link zum Zugriff auf den Anmeldebildschirm

Ihr Konto wurde mit den erforderlichen Berechtigungen konfiguriert. Wenn Sie Probleme haben, empfiehlt Adobe, sich an Ihr internes Projektunterstützungsteam zu wenden.

### Navigation {#navigation}

Wenn Sie sich zum ersten Mal anmelden, wird ein kleines Online-Tutorial einige der wichtigsten Funktionen der Benutzeroberfläche vorstellen.

Sie können dann über das Navigationsfenster auf wichtige Bereiche von AEM zugreifen. Für Inhaltsfragmente verwenden Sie die **Inhaltsfragmente** -Konsole (für einige Aktionen verwenden Sie auch die **Assets** -Konsole).

Das Navigationsfenster kann geöffnet werden, indem Sie links oben auf das Adobe-Symbol und dann auf das kleine Kompasssymbol klicken.

<!--
The Navigation Panel can be opened by selecting Adobe icon at the top left, followed by the small compass icon:

![Navigation panel](/help/journey-headless/author/assets/headless-journey-author-navigation-01.png)
-->

>[!NOTE]
>Inhaltsfragmente sind zwar eine Funktion von AEM **Sites**, sie werden jedoch als **Assets** gespeichert. Dies ist ein technisches Detail, das zwar keinen Einfluss auf Ihre Arbeitsweise hat, es könnte aber dennoch nützlich sein, es zu wissen.

In der Konsole können Sie im linken Bereich Ordner auswählen, um zu Ihrem Inhaltsfragment zu navigieren. Sie können auch danach filtern und/oder suchen.

![Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/assets/cfc-console-filter.png)

### Aktionen, Auswählen, Anzeigen {#actions-selecting-viewing}

In der **Inhaltsfragmentkonsole** stehen in der Symbolleiste mehrere Aktionen für Inhaltsfragmente zur Verfügung:

<!-- ![Console actions](assets/cfm-managing-cf-console-01.png) -->

* **In Assets öffnen**
* **Erstellen**
* Die Spalte **Referenziert von** enthält auch einen direkten Link, der alle übergeordneten Verweise dieses Fragments anzeigt. einschließlich der Referenzierung von Inhaltsfragmenten, Experience Fragments und Seiten.
* Wenn Sie den Mauszeiger über einen Ordnernamen bewegen, wird der JCR-Pfad angezeigt.

Nach der Auswahl eines Fragments werden alle passenden Aktionen angezeigt:

<!-- ![Console actions - fragment selected](assets/cfm-managing-cf-console-selected-01.png) -->

* **Öffnen**
* **Veröffentlichen** (und **Veröffentlichung rückgängig machen**)
* **Kopieren**
* **Verschieben**
* **Umbenennen**
* **Löschen**

>[!NOTE]
>
>Aktionen wie Veröffentlichen, Veröffentlichung aufheben, Löschen, Verschieben, Umbenennen, Kopieren lösen einen asynchronen Vorgang aus. Der Fortschritt dieses Vorgangs kann über die AEM-Benutzeroberfläche für asynchrone Vorgänge überwacht werden.

<!--
The **Assets** console has dedicated **Action Toolbars**, and **Quick Actions** that you can use after selecting a resource (for example, a folder or content fragment).

The Quick Actions are available for a single resource, see **Basel** in the example below:

![Quick Actions](/help/journey-headless/author/assets/headless-journey-author-navigation-05.png)

The Actions Toolbar provides access to the full range of actions - applicable for the current scenario. The actions available can change; for example, dependent on your location, or whether you have selected multiple resources:

![Action Toolbar](/help/journey-headless/author/assets/headless-journey-author-navigation-06.png)

You can select the format for viewing your resources with the View Selector:

![View Selector](/help/journey-headless/author/assets/headless-journey-author-navigation-03.png)

You can view additional information about items using the Rail Selector. This also gives access to additional actions.

![Left Rail](/help/journey-headless/author/assets/headless-journey-author-navigation-04.png)
-->

## Bearbeiten von Inhaltsfragmenten {#authoring-content-fragments}

Das war eine sehr schnelle Einführung in die AEM Benutzeroberfläche, aber hoffentlich hatten Sie die Möglichkeit, es auszuprobieren. Jetzt kommen wir zu Ihrem echten Interesse – Inhaltsfragmente für Headless.

Wir müssen die Dinge von Anfang bis Ende durchgehen, aber in Ihrer Instanz wurden möglicherweise bereits Ordner und/oder Fragmente erstellt, die sich an verschiedenen Stellen befinden. Die Prinzipien sind dieselben.

### Organisieren und Navigieren {#organizing-and-navigating}

Wenn Sie nicht gerade sehr wenige Inhaltsfragmente haben, werden Sie sie organisieren wollen – damit Sie (und andere) sie wiederfinden können.

#### Erstellen eines Ordners {#creating-folder}

Dazu können Sie im Bereich **Dateien** der **Assets**-Konsole Ordner erstellen. Wählen Sie die Option **Erstellen** (oben rechts), gefolgt von **Ordner**:

![Option „Ordner erstellen“](/help/journey-headless/author/assets/headless-journey-author-folder-01.png)

Daraufhin wird ein Dialogfeld geöffnet, in dem Sie die Details eingeben und dann mit **Erstellen** bestätigen können:

![Dialogfeld „Ordner erstellen“](/help/journey-headless/author/assets/headless-journey-author-folder-02.png)

#### Verwenden von Pfaden und Tags zur Beschränkung von Inhaltsfragmentmodellen, die im Ordner verfügbar sind {#tags-paths-for-models-in-folder}

Dieser Abschnitt ist etwas komplexer. Man braucht es nicht wirklich, wenn man gerade erst beginnt und Dinge ausprobiert, aber es ist *very* nützlich, wenn Sie viele Fragmente haben. Also ist es gut, darüber zu wissen - auch wenn Sie es noch nicht ganz verwenden.

Ihr Inhaltsarchitekt hat alle Inhaltsfragmentmodelle erstellt, die für Ihr aktuelles Projekt erforderlich sind, und möglicherweise auch für einige andere Projekte. Um Ihnen und anderen Autoren die Arbeit zu erleichtern, können Sie die Liste der für einen bestimmten Ordner verfügbaren Modelle einschränken.

Nach dem Erstellen des Ordners können Sie die **Eigenschaften** des Ordners öffnen. Hier finden Sie verschiedene Registerkarten mit Informationen und Konfigurationsdetails zum Ordner. Insbesondere für Inhaltsfragmente können Sie die Registerkarte **Richtlinien** verwenden, um bestimmte Pfade und/oder Tags für diesen Ordner zu definieren. Dadurch werden die für die Verwendung im Ordner verfügbaren Inhaltsfragmentmodelle eingeschränkt, da dies bedeutet, dass Inhaltsfragmentmodelle diese Anforderungen erfüllen müssen, bevor sie zum Erzeugen von Fragmenten in diesem Ordner verwendet werden können.

![Erstellen von Ordnereigenschaften – Richtlinien](/help/journey-headless/author/assets/headless-journey-author-folder-04.png)

>[!NOTE]
>
>Weitere Informationen finden Sie unter „Inhaltsfragmentmodelle – Zulassen von Inhaltsfragmentmodellen für Ihren Assets-Ordner“.

Navigieren Sie dann durch diese Ordner, um Ihre Inhaltsfragmente zu erstellen und zu bearbeiten.

#### Nur für den Fall – Konfiguration von Ordner-Cloud-Services {#cloud-services-folder}

Nur für den Fall...

Sie erhalten wahrscheinlich einen ersten Ordner, unter dem Sie Ihre Ordner erstellen können. Dies liegt daran, dass einige Konfigurationsdetails (normalerweise von einem Entwickler oder Systemadministrator) auf den Stammordner angewendet werden müssen. Dies wird Sie wahrscheinlich nicht interessieren, aber bei Bedarf können Sie die **Konfiguration** inn den **Cloud-Services** des Ordners **Eigenschaften** überprüfen:

![Erstellen von Ordnereigenschaften – Konfiguration](/help/journey-headless/author/assets/headless-journey-author-folder-03.png)

>[!NOTE]
>
>Weitere Informationen finden Sie unter „Anwenden der Konfiguration auf Ihren Assets-Ordner“.

### Erstellen eines Inhaltsfragments {#creating-fragment}

In der Konsole **Inhaltsfragmente** können Sie mit **Erstellen** das Dialogfeld **Neues Inhaltsfragment** öffnen:

![Inhaltsfragmente-Konsole – Erstellen eines neuen Fragments](/help/sites-cloud/administering/content-fragments/assets/cfc-console-create.png)

Geben Sie Folgendes an:

* **Speicherort**
* **Inhaltsfragmentmodell**
* **Titel**
* **Name**
* **Beschreibung**

Bestätigen Sie dann Ihre Angaben, indem Sie entweder auf **Erstellen** oder auf **Erstellen und öffnen** klicken.

<!--
Creating a Content Fragment is very similar - you just use the **Content Fragment** option instead:

![Create Content Fragment option](/help/journey-headless/author/assets/headless-journey-author-content-fragment-01.png)

This time a wizard opens. The first step is to select the Content Fragment Model that your fragment is based on:

![Create Content Fragment - select Model](/help/journey-headless/author/assets/headless-journey-author-content-fragment-02.png)

After continuing with **Next** you can supply the details (**Basic** and **Advanced**) for your fragment:

![Create Content Fragment - provide Name](/help/journey-headless/author/assets/headless-journey-author-content-fragment-03.png)

Confirm with **Create** and you can then **Open** your fragment in the editor.
-->

### Bearbeiten eines Fragments {#editing-fragment}

Sie können ein Fragment unmittelbar nach seiner Erstellung öffnen oder indem Sie es in der Inhaltsfragmente-Konsole (oder auch in der Assets-Konsole) auswählen.

Beim ersten Öffnen des Editors wird Folgendes angezeigt:

* Eine Liste von Symbolen auf der linken Seite – diese bietet Ihnen Zugriff auf verschiedene Funktionsbereiche. Der Editor öffnet sich auf der Registerkarte **Varianten**, auf der der größte Teil der Bearbeitung stattfindet. Vielleicht interessieren Sie sich auch für die Registerkarten **Anmerkungen** und **Metadaten**.

* Eine Kopfzeile mit Informationen zum Fragment und Zugriff auf verschiedene Aktionen.

* Hauptbearbeitungsbereich – dieser hängt von dem Modell ab, das zum Erstellen des Fragments verwendet wurde.

Beispiele:

* Ein Fragment, für das nur mehrere Informationen erforderlich sind, von denen einige einen bestimmten Typ aufweisen. Für Headless-Inhalte sind Verweise von zentraler Bedeutung (Sie werden später auf Ihrer Journey darüber erfahren).

  ![Inhaltsfragmente-Editor – Mein Fragment](/help/journey-headless/author/assets/headless-journey-author-content-fragment-04.png)

* Ein Fragment, mit dem Sie einen langen Abschnitt mit Text schreiben können. Hier finden Sie zusätzliche Optionen zum Verwalten und Formatieren des Textes. Sie können die einzelnen Textfelder auch in einem Vollbild-Editor öffnen (mithilfe des kleinen bildschirmähnlichen Symbols auf der rechten Seite).

  ![Inhaltsfragmente-Editor – Alaska Spirits](/help/journey-headless/author/assets/headless-journey-author-content-fragment-05.png)

>[!NOTE]
>
>Möglicherweise ist eine projektspezifische Dokumentation erforderlich, um Autoren dabei zu helfen, einige Felder erfolgreich auszufüllen.
>
>Allgemeine Informationen finden Sie unter „Inhaltsfragmentmodelle – Datentypen und Eigenschaften“.

Bestätigen Sie Ihre Aktualisierungen mit **Speichern** oder **Speichern und schließen**.

>[!NOTE]
>
>Weitere Informationen finden Sie unter „Varianten – Authoring von Inhaltsfragmenten“.

#### Was Sie (wahrscheinlich) nicht benötigen {#what-you-probably-do-not-need-to-worry-about}

OK, dies mag zwar etwas seltsam erscheinen, aber sobald Sie den Inhaltsfragment-Editor öffnen und mit der Untersuchung beginnen, können Sie verschiedene Optionen sehen, die (wahrscheinlich) nicht für Ihre Headless-Journey als Inhaltsautor gelten. Dies ist also nur ein kurzer Hinweis darauf, was man im Headless-Kontext ignorieren kann:

* **Inhaltsfragmentmodelle**

  Der Name des Inhaltsfragmentmodells wird oben im Editor angezeigt – direkt unter dem Namen des Fragments. Dies ist auch ein Link, über den Sie zum Modell-Editor gelangen.
Inhaltsfragmentmodelle sind für Ihre Inhaltsfragmente von entscheidender Bedeutung, da sie die zu verwendende Struktur definieren. Für die Erstellung und Bearbeitung ist jedoch (in der Regel) eine andere Rolle, der Inhaltsarchitekt, verantwortlich.

  >[!NOTE]
  >
  >Wenn Sie mehr darüber erfahren möchten, können Sie die Journey AEM Headless-Inhaltsarchitekten-Tour lesen.

* **Zugehörige Inhalte**

  Dies ist ziemlich offensichtlich, da es sich um eine Registerkarte im Editor handelt.

  Inhaltsfragmente sind in AEM seit einigen Versionen verfügbar. Ursprünglich wurden sie für die „traditionelle“ Verwendung beim Authoring von Seiten zur Verfügung gestellt...und werden weiterhin in diesem Zusammenhang verwendet. Dazu kann es gehören, Assets (z. B. Bilder) zuzuordnen, die zwar nicht in das Fragment eingebettet sind, aber für den Autor beim Erstellen und Bearbeiten einer Seite verfügbar sein müssen.

* **Vorschau**

  Dies ist eine weitere Registerkarte im Editor und bietet eine technische Ansicht, die hauptsächlich für Entwickler gedacht ist.

* **Seitenverweise aktualisieren**

  Diese Aktion ist im Abschnitt **...** (Ellipsen). Es ist für Headless-Autoren nicht interessant, da es sich auf die Seitenbearbeitung bezieht.

### Veröffentlichung {#publishing}

<!-- needs more details -->

Nachdem Sie Ihr Fragment fertig gestellt haben, können Sie es **Veröffentlichen**, sodass es für die Headless-Anwendungen verfügbar ist.

Die Veröffentlichungsaktionen sind im Editor verfügbar:

![Inhaltsfragmente-Editor – Mein Fragment](/help/journey-headless/author/assets/headless-journey-author-content-fragment-06.png)

>[!NOTE]
>
>Sie können Ihr Fragment auch über die **Assets** oder **Inhaltsfragmente** Konsole.

## Wie geht es weiter {#whats-next}

Nachdem Sie nun die Grundlagen gelernt haben, lautet der nächste Schritt: [Erfahren Sie mehr über Verweise](references.md). Darin werden die verschiedenen verfügbaren Verweise vorgestellt und besprochen und die Erstellung von Strukturebenen mit den Fragmentverweisen beschrieben – ein wichtiger Bestandteil des Authoring für Headless.

## Zusätzliche Ressourcen {#additional-resources}

* [Authoring – Konzepte](/help/sites-cloud/authoring/getting-started/concepts.md)

* [Grundlegende Handhabung](/help/sites-cloud/authoring/getting-started/basic-handling.md): Diese Seite basiert hauptsächlich auf der **Sites**-Konsole, aber viele / die meisten Funktionen sind auch für das Authoring von **Inhaltsfragmenten** unter der **Assets**-Konsole relevant.

   * [Navigationsfenster](/help/sites-cloud/authoring/getting-started/basic-handling.md#navigation-panel)

   * [Die Kopfzeile](/help/sites-cloud/authoring/getting-started/basic-handling.md#the-header)

   * [Aktionssymbolleiste](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar)

   * [Schnellaktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)

   * [Anzeigen und Auswählen von Ressourcen](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)

   * [Schienenauswahl](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector)

* [Arbeiten mit Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragments.md)

   * [Verwalten von Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md)

   * [Anwenden der Konfiguration auf Ihren Assets-Ordner](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md#apply-the-configuration-to-your-assets-folder)

   * [Erstellen eines Inhaltsfragments](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#creating-a-content-fragment)

   * [Varianten – Authoring von Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md)

   * Veröffentlichung

      * im Editor oder **Assets** console

         * [Quick Publish](/help/assets/manage-publication.md#quick-publish)

         * [Veröffentlichung verwalten](/help/assets/manage-publication.md#manage-publication)

      * Aus dem **Inhaltsfragmente** Konsole

         * [Veröffentlichen und Anzeigen der Vorschau eines Inhaltsfragments](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#publishing-and-previewing-a-fragment)

   * [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/content-fragments-models.md)

      * [Inhaltsfragmentmodelle – Datentypen](/help/sites-cloud/administering/content-fragments/content-fragments-models.md#data-types)

      * [Inhaltsfragmentmodelle – Eigenschaften](/help/sites-cloud/administering/content-fragments/content-fragments-models.md#properties)

      * [Inhaltsfragmentmodelle – Zulassen von Inhaltsfragmentmodellen für Ihren Assets-Ordner](/help/sites-cloud/administering/content-fragments/content-fragments-models.md#allowing-content-fragment-models-assets-folder)

* Anleitungen für den Einstieg
   * [Erstellen eines Setups für einen Asset-Ordner (Headless)](/help/headless/setup/create-assets-folder.md)

* AEM Headless-Inhaltsarchitekten-Tour

* AEM Headless-Übersetzungs-Tour
