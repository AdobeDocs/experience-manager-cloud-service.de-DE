---
title: Grundlagen zum Authoring
description: Erfahren Sie mehr über die Konzepte und Mechanismen sw Authoring für Ihr Headless-CMS mithilfe von Inhaltsfragmenten.
exl-id: 3eca973f-b210-41bb-98da-ecbd2bae9803
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 18c997a5644288e870c109a8d745b196349b923d
workflow-type: tm+mt
source-wordcount: '1733'
ht-degree: 98%

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

Eine AEM-Installation besteht im Allgemeinen aus drei Umgebungen:

* Autor
* Veröffentlichung
* Vorschau

Sie melden sich an und verwenden die Autorenumgebung, um Ihre Inhalte zu erzeugen. Wenn Sie fertig sind, veröffentlichen Sie Ihre Inhalte, damit sie allgemein verfügbar werden. Für Headless wäre dies für andere Anwendungen, für Web-Seiten wäre dies für Leser im Internet.

Weitere Informationen finden Sie unter „Authoring-Konzepte“.

Von der **Inhaltsfragmentkonsole** aus können Sie auch an den **Vorschau-Service** veröffentlichen, um vor der Veröffentlichung zu testen und eine Vorschau anzuzeigen. Siehe „Veröffentlichung und Vorschau eines Fragments“.

### Anmeldung {#signing-in}

Wie bei den meisten Systemen müssen Sie sich anmelden. Als Autorin bzw. Autor erhalten Sie Folgendes:

* Name des Benutzers (Konto)
* Passwort
* Link zum Zugriff auf den Anmeldebildschirm

Ihr Konto wurde mit den erforderlichen Berechtigungen konfiguriert. Sollten Sie Probleme haben, empfiehlt Adobe Ihnen, sich an Ihr internes Projektunterstützungs-Team zu wenden.

### Navigation {#navigation}

Wenn Sie sich zum ersten Mal anmelden, wird ein kleines Online-Tutorial einige der wichtigsten Funktionen der Benutzeroberfläche vorstellen.

Sie können dann über das Navigationsfenster auf wichtige Bereiche von AEM zugreifen. Für Inhaltsfragmente steht die **Inhaltsfragmentkonsole** zur Verfügung (für einige Aktionen können Sie auch die **Assets**-Konsole verwenden).

Das Navigationsfenster kann geöffnet werden, indem Sie links oben auf das Adobe-Symbol und dann auf das kleine Kompasssymbol klicken.

>[!NOTE]
>Inhaltsfragmente sind zwar eine Funktion von AEM **Sites**, sie werden jedoch als **Assets** gespeichert. Dies ist ein technisches Detail, das zwar keinen Einfluss auf Ihre Arbeitsweise hat, es könnte aber dennoch nützlich sein, es zu wissen.

In der Inhaltsfragmentkonsole können Sie im linken Bereich Ordner auswählen, um zu Ihrem Inhaltsfragment zu navigieren. Sie können auch danach filtern und/oder suchen.

![Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/assets/cf-managing-console-filter.png)

### Aktionen, Auswählen, Anzeigen {#actions-selecting-viewing}

In der **Inhaltsfragmentkonsole** stehen in der Symbolleiste mehrere Aktionen für Inhaltsfragmente zur Verfügung:

* **In Assets öffnen**
* **Erstellen**
* Die Spalte **Referenziert von** enthält auch einen direkten Link, der alle übergeordneten Verweise dieses Fragments anzeigt. einschließlich der Referenzierung von Inhaltsfragmenten, Experience Fragments und Seiten.
* Wenn Sie den Mauszeiger über einen Ordnernamen bewegen, wird der JCR-Pfad angezeigt.

Nach Auswahl des Fragments sind weitere Aktionen verfügbar (sofern zutreffend):

* **Öffnen**
* **Veröffentlichen** (und **Veröffentlichung rückgängig machen**)
* **Tags verwalten**
* **Kopieren**
* **Ersetzen**
* **Verschieben**
* **Umbenennen**
* **Löschen**

>[!NOTE]
>
>Aktionen wie Veröffentlichen, Veröffentlichung aufheben, Löschen, Verschieben, Umbenennen, Kopieren lösen einen asynchronen Vorgang aus. Der Fortschritt dieses Vorgangs kann über die AEM-Benutzeroberfläche für asynchrone Vorgänge überwacht werden.

## Erstellung von Inhaltsfragmenten {#authoring-content-fragments}

Das war also eine sehr kurze Einführung in die AEM-Benutzeroberfläche (UI), aber ich hoffe, Sie hatten bereits die Gelegenheit, sie auszuprobieren. Jetzt kommen wir zu Ihrem echten Interesse – Inhaltsfragmente für Headless.

Wir müssen die Dinge von Anfang bis Ende durchgehen, aber in Ihrer Instanz wurden möglicherweise bereits Ordner und/oder Fragmente erstellt, die sich an verschiedenen Stellen befinden. Die Prinzipien sind dieselben.

### Organisieren und Navigieren {#organizing-and-navigating}

Wenn Sie nicht gerade sehr wenige Inhaltsfragmente haben, werden Sie sie organisieren wollen – damit Sie (und andere) sie wiederfinden können.

#### Erstellen eines Ordners {#creating-folder}

Dazu können Sie im Bereich **Dateien** der **Assets**-Konsole Ordner erstellen. Wählen Sie die Option **Erstellen** (oben rechts), gefolgt von **Ordner**:

![Option „Ordner erstellen“](/help/journey-headless/author/assets/headless-journey-author-folder-01.png)

Daraufhin wird ein Dialogfeld geöffnet, in dem Sie die Details eingeben und dann mit **Erstellen** bestätigen können:

![Dialogfeld „Ordner erstellen“](/help/journey-headless/author/assets/headless-journey-author-folder-02.png)

#### Verwenden von Pfaden und Tags zur Beschränkung von Inhaltsfragmentmodellen, die im Ordner verfügbar sind {#tags-paths-for-models-in-folder}

Dieser Abschnitt ist etwas komplexer. Man braucht ihn nicht wirklich, wenn man gerade erst anfängt und Dinge ausprobiert, aber er ist *sehr* nützlich, wenn man viele Fragmente hat. Also ist es gut, ihn zu kennen – auch wenn man ihn noch nicht wirklich benutzt.

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

### Bearbeiten eines Fragments {#editing-fragment}

Sie können ein Fragment unmittelbar nach seiner Erstellung öffnen oder indem Sie es in der Inhaltsfragmente-Konsole (oder auch in der Assets-Konsole) auswählen.

>[!NOTE]
>
>Inhaltsfragmente sind eine Sites-Eigenschaft, werden jedoch als **Assets** gespeichert.
>
>Es gibt zwei Editoren für das Erstellen von Inhaltsfragmenten.
>
>* Der neue Editor, auf den hauptsächlich über die **Inhaltsfragmentkonsole** zugegriffen wird.
>* Der ursprüngliche Editor. Der Zugriff auf diesen erfolgt hauptsächlich über die **Assets**-Konsole.

Wenn der Editor zum ersten Mal geöffnet wird, sehen Sie Folgendes:

* obere Symbolleiste: für wichtige Informationen und Aktionen
   * ein Link zur Inhaltsfragmentkonsole (Startseiten-Symbol)
   * Informationen zum Modell und Ordner
   * Links zur Vorschau; wenn das URL-Standardmuster für die Vorschau für das Modell konfiguriert ist
   * die Aktionen „Veröffentlichen“ und „Veröffentlichung rückgängig machen“
   * eine Option zum Anzeigen aller **übergeordneten Verweise** (Link-Symbol)
   * der **Status** des Fragments und Informationen über die letzte Speicherung
   * ein Umschalter zum Umschalten auf den ursprünglichen (Assets-basierten) Editor
* linker Bereich: zeigt die **Varianten** für das Inhaltsfragment und dessen **Felder** an:
   * diese Links können verwendet werden, um in der Inhaltsfragmentstruktur zu navigieren
* rechter Bereich: enthält Registerkarten mit den Eigenschaften (Metadaten) und Tags, Informationen über den Versionsverlauf sowie Informationen zu Sprachkopien
   * auf der Registerkarte **Eigenschaften** können Sie den **Titel** und die **Beschreibung** für das Fragment oder die **Variante** aktualisieren
* zentraler Bereich: zeigt die tatsächlichen Felder und den Inhalt der ausgewählten Variante an
   * ermöglicht das Bearbeiten des Inhalts
   * wenn **Registerkartenplatzhalter**-Felder innerhalb des Modells definiert sind, werden sie hier angezeigt und können für die Navigation verwendet werden.

Für ein Fragment kann beispielsweise Folgendes gelten:

* Erfordert mehrere Informationen, einige mit einem bestimmten Typ. Für Headless-Inhalte sind Verweise von zentraler Bedeutung (Sie werden später in Ihrer Tour mehr darüber erfahren).

* Ermöglicht Ihnen das Schreiben eines langen Textabschnitts. Hier finden Sie zusätzliche Optionen zum Verwalten und Formatieren des Textes. Sie können die einzelnen Textfelder auch in einem Vollbild-Editor öffnen (mithilfe des kleinen bildschirmähnlichen Symbols auf der rechten Seite).

![Inhaltsfragmente-Editor – Alaska Spirits](/help/sites-cloud/administering/content-fragments/assets/cf-authoring-overview.png)

>[!NOTE]
>
>Möglicherweise ist eine projektspezifische Dokumentation erforderlich, um Autoren dabei zu helfen, einige Felder erfolgreich auszufüllen.
>
>Allgemeine Informationen finden Sie unter „Inhaltsfragmentmodelle – Datentypen und Eigenschaften“.

Bestätigen Sie Ihre Aktualisierungen mit **Speichern** oder **Speichern und schließen**.

>[!NOTE]
>
>Weitere Informationen finden Sie unter „Varianten – Authoring von Inhaltsfragmenten“.

#### Worüber Sie sich (wahrscheinlich) keine Sorgen machen müssen {#what-you-probably-do-not-need-to-worry-about}

OK, dieser Abschnitt mag etwas seltsam erscheinen, aber sobald Sie den Inhaltsfragment-Editor öffnen und mit der Erkundung beginnen, können Sie verschiedene Optionen sehen, die (wahrscheinlich) nicht für Ihre Headless-Inhaltsautoren-Tour relevant sind. Dies ist also nur ein kurzer Hinweis darauf, was man im Headless-Kontext ignorieren kann:

* **Inhaltsfragmentmodelle**

  Der Name des Inhaltsfragmentmodells wird im rechten Bereich des Editors angezeigt. Dies ist auch ein Link, über den Sie zum Modell-Editor gelangen.
Inhaltsfragmentmodelle sind für Ihre Inhaltsfragmente von entscheidender Bedeutung, da sie die zu verwendende Struktur definieren. Für die Erstellung und Bearbeitung ist jedoch (in der Regel) eine andere Rolle, der Inhaltsarchitekt, verantwortlich.

  >[!NOTE]
  >
  >Wenn Sie mehr darüber erfahren möchten, können Sie die Journey AEM Headless-Inhaltsarchitekten-Tour lesen.

### Veröffentlichung {#publishing}

<!-- needs more details -->

Nachdem Sie Ihr Fragment fertig gestellt haben, können Sie es **Veröffentlichen**, sodass es für die Headless-Anwendungen verfügbar ist.

Die Veröffentlichungsaktionen sind im Editor verfügbar:

![Inhaltsfragment-Editor – Mein Fragment](/help/journey-headless/author/assets/headless-journey-author-content-fragment-06.png)

>[!NOTE]
>
>Sie können Ihr Fragment auch über die **Assets**- oder **Inhaltsfragmente**-Konsole veröffentlichen.

## Wie geht es weiter {#whats-next}

Nachdem Sie nun die Grundlagen gelernt haben, lautet der nächste Schritt: [Erfahren Sie mehr über Verweise](references.md). Darin werden die verschiedenen verfügbaren Verweise vorgestellt und besprochen und die Erstellung von Strukturebenen mit den Fragmentverweisen beschrieben – ein wichtiger Bestandteil des Authoring für Headless.

## Zusätzliche Ressourcen {#additional-resources}

* [Authoring – Konzepte](/help/sites-cloud/authoring/author-publish.md)

* [Grundlegende Handhabung](/help/sites-cloud/authoring/basic-handling.md): Diese Seite basiert hauptsächlich auf der **Sites**-Konsole, aber viele / die meisten Funktionen sind auch für das Authoring von **Inhaltsfragmenten** unter der **Assets**-Konsole relevant.

   * [Navigationsfenster](/help/sites-cloud/authoring/basic-handling.md#navigation-panel)

   * [Die Kopfzeile](/help/sites-cloud/authoring/basic-handling.md#the-header)

   * [Aktionssymbolleiste](/help/sites-cloud/authoring/basic-handling.md#actions-toolbar)

   * [Schnellaktionen](/help/sites-cloud/authoring/basic-handling.md#quick-actions)

   * [Anzeigen und Auswählen von Ressourcen](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources)

   * [Schienenauswahl](/help/sites-cloud/authoring/basic-handling.md#rail-selector)

* [Arbeiten mit Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)

   * [Verwalten von Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/managing.md)

   * [Anwenden der Konfiguration auf Ihren Assets-Ordner](/help/sites-cloud/administering/content-fragments/setup.md#apply-the-configuration-to-your-folder)

   * [Erstellen eines Inhaltsfragments](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment)

   * [Erstellen von Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/authoring.md)

   * Veröffentlichung

      * Über den Editor oder die **Assets**-Konsole

         * [Quick Publish](/help/assets/manage-publication.md#quick-publish)

         * [Veröffentlichung verwalten](/help/assets/manage-publication.md#manage-publication)

      * Über die **Inhaltsfragmentkonsole**

         * [Veröffentlichung und Vorschau eines Inhaltsfragments](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment)

   * [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md)

      * [Inhaltsfragmentmodelle – Datentypen](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)

      * [Inhaltsfragmentmodelle – Eigenschaften](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#properties)

      * [Inhaltsfragmentmodelle – Zulassen von Inhaltsfragmentmodellen für Ihren Assets-Ordner](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#allowing-content-fragment-models-assets-folder)

* [Inhaltsfragmente – der ursprüngliche Editor aus der Assets-Konsole](/help/assets/content-fragments/content-fragments-variations.md)

* Anleitungen für den Einstieg
   * [Erstellen eines Setups für einen Asset-Ordner (Headless)](/help/headless/setup/create-assets-folder.md)

* AEM Headless-Inhaltsarchitekten-Tour

* AEM Headless-Übersetzungs-Tour
