---
title: SPA-Editor – Überblick
description: Dieser Artikel gibt einen umfassenden Überblick über den SPA-Editor und seine Funktionsweise, einschließlich detaillierter Workflows der Interaktion des SPA-Editors innerhalb AEM.
translation-type: tm+mt
source-git-commit: 9b52d94b9f00be30c21dece9b34b0b56056dcbd6
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 55%

---


# SPA-Editor – Überblick {#spa-editor-overview}

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwickler möchten Sites mit SPA-Frameworks erstellen und Autoren möchten Inhalte in AEM nahtlos für eine Site bearbeiten, die mit diesen Frameworks erstellt wurde.

Der SPA-Editor bietet eine umfassende Lösung zur Unterstützung von SPAs in AEM. Auf dieser Seite finden Sie einen Überblick über die Unterstützung von SPA in AEM, die Funktionsweise des SPA-Editors und die Synchronisation des SPA-Frameworks und AEM.

## Einführung {#introduction}

Sites, die mit gängigen SPA-Frameworks wie React und Angular erstellt wurden, laden ihren Inhalt über dynamisches JSON und weisen nicht die HTML-Struktur auf, die für den Seiten-Editor von AEM erforderlich ist, um Steuerelemente zur Bearbeitung platzieren zu können.

Um die Bearbeitung von SPAs innerhalb von AEM zu ermöglichen, ist eine Zuordnung zwischen der JSON-Ausgabe der SPA und dem Inhaltsmodell im AEM-Repository erforderlich, damit Änderungen am Inhalt gespeichert werden können.

Mit der SPA-Unterstützung wird in AEM ein JS-Thin Layer eingeführt. Dieses interagiert mit dem SPA-JS-Code, wenn es in den Seiten-Editor geladen wird, mit dem Ereignisse gesendet und der Speicherort für die Steuerelemente zur Bearbeitung aktiviert werden kann, um eine kontextbezogene Bearbeitung zu ermöglichen. Diese Funktion baut auf dem Content Services API Endpoint-Konzept auf, da die Inhalte aus der SPA über Content Services geladen werden müssen.

Weitere Informationen zu SPAs in AEM finden Sie in den folgenden Dokumenten:

* [SPA-Blueprint](blueprint.md) für die technischen Anforderungen an SPAs
* [Erste Schritte mit SPAs in AEM mithilfe von React](getting-started-react.md) für eine schnelle Einführung in eine einfache BSG mit React
* [Erste Schritte mit SPAs in AEM Verwendung von Angular](getting-started-angular.md) für einen schnellen Überblick über eine einfache SPA mit Angular

## Design {#design}

Die Seitenkomponente für eine SPA stellt die HTML-Elemente ihrer untergeordneten Komponenten nicht über die JSP- oder HTL-Datei bereit. Dieser Vorgang wird an das SPA-Framework delegiert. Die Darstellung untergeordneter Komponenten oder Modelle wird als JSON-Datenstruktur aus der JCR-Datei abgerufen. Die SPA-Komponenten werden dann entsprechend dieser Struktur zur Seite hinzugefügt. Durch dieses Verhalten unterscheidet sich die anfängliche Hauptteilkomposition der Seitenkomponente von entsprechenden Kompositionen, bei denen es sich nicht um SPA-Komponenten handelt.

### Seitenmodellverwaltung {#page-model-management}

Die Auflösung und Verwaltung des Seitenmodells wird an eine bereitgestellte `PageModel`-Bibliothek delegiert. Die SPA muss die Seitenmodellbibliothek verwenden, um vom SPA-Editor initialisiert und verfasst zu werden. Die PageModel-Bibliothek wird der AEM-Seitenkomponente indirekt über den NPM `cq-react-editable-components` bereitgestellt. Das Seitenmodell fungiert als Interpreter zwischen AEM und der SPA und muss daher immer vorhanden sein. Bei der Erstellung der Seite muss eine zusätzliche Bibliothek `cq.authoring.pagemodel.messaging` hinzugefügt werden, um die Kommunikation mit dem Seiten-Editor zu ermöglichen.

Wenn die SPA-Seitenkomponente von der Seitenkernkomponente erbt, gibt es zwei Möglichkeiten, die Kategorie `cq.authoring.pagemodel.messaging` der Client-Bibliothek verfügbar zu machen:

* Wenn die Vorlage bearbeitbar ist, fügen Sie sie der Seitenrichtlinie hinzu.
* Oder fügen Sie die Kategorien mithilfe von `customfooterlibs.html`   hinzu.

Für jede Ressource im exportierten Modell ordnet die SPA eine tatsächliche Komponente zu, die das Rendern durchführt. Das als JSON dargestellte Modell wird dann mithilfe der Komponentenzuordnungen innerhalb eines Containers gerendert.

![Modell- und Komponentenzuordnung in SPA](assets/model-component-mapping.png)

>[!CAUTION]
>
>The inclusion of the `cq.authoring.pagemodel.messaging` category should be limited to the context of the SPA Editor.

### Kommunikationsdatentyp {#communication-data-type}

When the `cq.authoring.pagemodel.messaging` category is added to the page, it will send a message to the Page Editor to establish the JSON communication data type. Wenn der Kommunikationsdatentyp auf JSON festgelegt ist, kommunizieren die GET-Anfragen mit den Endpunkten des Sling-Modells einer Komponente. Nach einer Aktualisierung im Seiten-Editor wird die JSON-Repräsentation der aktualisierten Komponente an die PageModel-Bibliothek gesendet. Die PageModel-Bibliothek informiert dann die SPA über Aktualisierungen.

![SPA-Kommunikation](assets/communication.png)

## Workflow {#workflow}

Sie können den Fluss der Interaktion zwischen SPA und AEM verstehen, indem Sie den SPA-Editor als Vermittler zwischen den beiden betrachten.

* Die Kommunikation zwischen dem Seiten-Editor und der SPA erfolgt über JSON statt über HTML.
* Der Seiten-Editor stellt die neueste Version des Seitenmodells für die SPA über die iFrame- und Messaging-API bereit.
* Der Seitenmodell-Manager informiert den Editor, dass er zur Bearbeitung bereit ist, und übergibt das Seitenmodell als JSON-Struktur.
* Der Editor verändert weder die DOM-Struktur der zu erstellenden Seite, noch greift er darauf zu, sondern stellt vielmehr das neueste Seitenmodell bereit.

![SPA-Workflow](assets/workflow.png)

### Grundlegender SPA-Editor-Workflow {#basic-spa-editor-workflow}

Unter Berücksichtigung der Schlüsselelemente des SPA-Editors erscheint der allgemeine Arbeitsablauf zum Bearbeiten einer SPA in AEM dem Autor wie folgt:

![Animierter SPA-Workflow](assets/workflow.gif)

1. SPA-Editor wird geladen.
1. Die SPA wird in einem separaten Frame geladen.
1. SPA fordert JSON-Inhalte an und rendert Komponenten clientseitig.
1. SPA Editor erkennt gerenderte Komponenten und generiert Überlagerungen.
1. Autor klickt auf Überlagerung und zeigt die Bearbeitungssymbolleiste der Komponente an.
1. Der SPA-Editor bearbeitet weiterhin mit einer Serveranforderung für die POST.
1. SPA Editor fordert eine Aktualisierung von JSON an den SPA-Editor an, der mit einem DOM-Ereignis an die SPA gesendet wird.
1. SPA rendert die betreffende Komponente erneut und aktualisiert ihr DOM.

>[!NOTE]
>
>Beachten Sie:
>
>* Das SPA ist immer für seine Anzeige verantwortlich.
>* Der SPA-Editor ist vom SPA selbst isoliert.
>* In der Produktion (Veröffentlichung) wird der SPA-Editor nie geladen.


### Client-Server-Workflow zur Seitenbearbeitung {#client-server-page-editing-workflow}

Dies ist ein detaillierterer Überblick über die Interaktion zwischen Client und Server beim Bearbeiten einer SPA.

![Arbeitsablauf für die Client-Server-Bearbeitung](assets/client-server-editing.png)

1. Die SPA initialisiert sich selbst und fordert das Seitenmodell vom Sling Model Exporter an.
1. Der Sling Model Exporter fordert die Ressourcen, aus denen sich die Seite zusammensetzt, aus dem Repository an.
1. Das Repository gibt die Ressourcen zurück.
1. Der Sling Model Exporter gibt das Modell der Seite zurück.
1. Die SPA instanziiert ihre Komponenten auf Grundlage des Seitenmodells.
1. **6a** Der Inhalt teilt dem Editor mit, dass er für das Authoring bereit ist.

   **6b** Der Seiten-Editor fordert die Konfigurationen für das Komponenten-Authoring an.

   **6c** Der Seiten-Editor empfängt die Konfigurationen.
1. Wenn der Autor eine Komponente bearbeitet, sendet der Seiten-Editor eine Änderungsanforderung an das standardmäßige POST-Servlet.
1. Die Ressource wird im Repository aktualisiert.
1. Die aktualisierte Ressource wird für das POST-Servlet bereitgestellt.
1. Das standardmäßige POST-Servlet informiert den Seiten-Editor darüber, dass die Ressource aktualisiert wurde.
1. Der Seiten-Editor fordert das neue Seitenmodell an.
1. Die Ressourcen, aus denen sich die Seite zusammensetzt, werden vom Repository angefordert.
1. Die Ressourcen, aus denen sich die Seite zusammensetzt, werden vom Repository für den Sling Model Exporter bereitgestellt.
1. Das aktualisierte Seitenmodell wird an den Editor zurückgegeben.
1. Der Seiten-Editor aktualisiert die Seitenmodellreferenz der SPA.
1. Die SPA aktualisiert ihre Komponenten auf der Grundlage der neuen Seitenmodellreferenz.
1. Die Komponentenkonfigurationen der Seiten-Editoren werden aktualisiert.

   **17a** Die SPA signalisiert dem Seiten-Editor, dass der Inhalt bereit ist.

   **17b** Der Seiten-Editor stellt Komponentenkonfigurationen für die SPA bereit.

   **17c** Die SPA stellt aktualisierte Komponentenkonfigurationen bereit.

### Authoring-Workflow {#authoring-workflow}

Dies ist ein detaillierterer Überblick, der sich auf die Authoring-Erfahrung konzentriert.

![SPA-Authoring-Workflow](assets/authoring-workflow.png)

1. Die SPA ruft das Seitenmodell ab.
1. **2a** Das Seitenmodell stellt die für das Authoring notwendigen Daten für den Editor bereit.

   **2b** Wenn der Komponenten-Orchestrator benachrichtigt wird, aktualisiert er die Inhaltsstruktur der Seite.
1. Der Komponenten-Orchestrator fragt die Zuordnung zwischen einem AEM-Ressourcentyp und einer SPA-Komponente ab.
1. Der Komponenten-Orchestrator instanziiert die SPA-Komponente dynamisch anhand des Seitenmodells und der Komponentenzuordnung.
1. Der Seiten-Editor aktualisiert das Seitenmodell.
1. **6a** Das Seitenmodell stellt die aktualisierten Authoring-Daten für den Seiten-Editor bereit.

   **6b** Das Seitenmodell versendet Änderungen an den Komponenten-Orchestrator.
1. Der Komponenten-Orchestrator ruft die Komponentenzuordnung ab.
1. Der Komponenten-Orchestrator aktualisiert den Inhalt der Seite.
1. Wenn die SPA die Aktualisierung des Inhalts der Seite abgeschlossen hat, lädt der Seiten-Editor die Authoring-Umgebung.

## Anforderungen und Einschränkungen {#requirements-limitations}

Damit der Autor den Seiteneditor zum Bearbeiten des Inhalts einer SPA verwenden kann, muss Ihre SPA-Anwendung implementiert sein, um mit dem AEM SPA Editor SDK zu interagieren. Bitte lesen Sie das [Erste Schritte mit SPAs in AEM Verwenden von React](getting-started-react.md) Dokument für ein Minimum, das Sie wissen müssen, um Ihre Arbeit zu starten.

### Unterstützte Frameworks {#supported-frameworks}

Das SPA Editor SDK unterstützt die folgenden Mindestversionen:

* React 16.x und höher
* Angular 6.x und höher

Frühere Versionen dieser Frameworks können mit dem AEM SPA Editor SDK verwendet werden, werden jedoch nicht unterstützt.

### Zusätzliche Frameworks {#additional-frameworks}

Zusätzliche SPA-Frameworks können implementiert werden, um mit dem AEM SPA Editor SDK zu arbeiten. Im [SPA Blueprint](blueprint.md) -Dokument finden Sie Informationen zu den Anforderungen, die ein Framework erfüllen muss, um eine Framework-spezifische Ebene zu erstellen, die aus Modulen, Komponenten und Diensten besteht, die mit dem AEM SPA Editor verwendet werden können.

### Mehrere Selektoren verwenden {#multiple-selectors}

Zusätzliche benutzerdefinierte Selektoren können als Teil einer SPA definiert und verwendet werden, die für das AEM SPA SDK entwickelt wurde. Diese Unterstützung erfordert jedoch, dass der `model` Selektor der erste Selektor ist und die Erweiterung `.json` den Anforderungen des JSON-Exporteurs entspricht.

### Texteditoranforderungen {#text-editor-requirements}

Wenn Sie den In-Place-Editor einer in SPA erstellten Textkomponente verwenden möchten, ist eine zusätzliche Konfiguration erforderlich.

1. Legen Sie ein Attribut (das beliebig sein kann) für das Container-Wrapper-Element fest, das die Text-HTML enthält. Im Falle des WKND SPA-Projekts ist es ein `<div>` Element und der verwendete Selektor ist `data-rte-editelement`.
1. Legen Sie die Konfiguration `editElementQuery` auf der entsprechenden AEM Textkomponente fest, `cq:InplaceEditingConfig` die auf diese Auswahl verweist, z. B. `data-rte-editelement`. Dadurch wird der Editor wissen, welches HTML-Element den HTML-Text umschließt.

Weitere Informationen zur `editElementQuery` Eigenschaft und Konfiguration des Rich-Text-Editors finden Sie unter Rich-Text-Editor [konfigurieren.](/help/implementing/developing/extending/rich-text-editor.md)

### Beschränkungen {#limitations}

Das AEM SPA Editor SDK wird von der Adobe vollständig unterstützt und als neue Funktion wird es weiter erweitert und erweitert. Die folgenden AEM Funktionen werden vom SPA-Editor noch nicht unterstützt:

* Zielgruppe, Modus
* ContextHub
* Inline-Bildbearbeitung
* Bearbeiten Sie Konfigurationen (z. B. Listener)
* Stilsystem
* Rückgängig/Wiederholen
* Seitenwechsel und Zeitverzerrung
* Funktionen, die serverseitig HTML-Umschreibungen durchführen, wie Link Checker, CDN-Rewriter-Dienst, URL-Verkürzung usw.
* Entwicklermodus
* AEM
