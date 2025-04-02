---
title: Der Micro-Front-End-Inhaltsfragment-Selektor für Adobe Experience Manager as a Cloud Service
description: Verwenden Sie den Micro-Front-End-Inhaltsfragment-Selektor, um Inhaltsfragmente aus Ihrem Programm zu suchen, zu finden und abzurufen.
role: Admin, User
source-git-commit: 426e958444446174bf90a13ad831c8604fddecc4
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 11%

---


# Micro-Front-End-Inhaltsfragmentauswahl {#micro-frontend-content-fragment-selector}

Der Micro-Front-End-Inhaltsfragment-Selektor bietet eine Benutzeroberfläche, die sich einfach in das as a Cloud Service-Repository von Adobe Experience Manager (AEM) integrieren lässt. Auf der -Benutzeroberfläche können Sie Inhaltsfragmente im Repository durchsuchen und in Ihrer Anwendung verwenden.

Die Micro-Front-End-Benutzeroberfläche wird in Ihrem Programm mithilfe des Inhaltsfragment-Selektor-Pakets bereitgestellt. Alle Aktualisierungen des Pakets werden automatisch importiert und in Ihre Anwendung geladen.

![Micro-Front-End-Inhaltsfragmentauswahl - Übersicht](/help/headless/assets/content-fragment-selector-overview.png)

Der Inhaltsfragment-Selektor bietet viele Vorteile, z. B.:

* Einfache Integration in eine der Adobe-Anwendungen.
* Einfach zu verwalten, da Aktualisierungen des Inhaltsfragment-Selektor-Pakets automatisch für den Inhaltsfragment-Selektor bereitgestellt werden, der für Ihre Anwendung verfügbar ist. Das bedeutet, dass die Anwendung keine Maßnahmen ergreifen muss, um die neuesten Änderungen zu laden.
* Einfache Anpassung durch Verwendung von Eigenschaften, die die Anzeige des Inhaltsfragment-Selektors in Ihrer Anwendung steuern.
* Die Volltextsuche ermöglicht zusammen mit anpassbaren Filtern die schnelle Navigation von Inhaltsfragmenten in der Authoring-Oberfläche.
* Möglichkeit, innerhalb einer IMS-Organisation zur Auswahl von Inhaltsfragmenten zwischen Repositorys zu wechseln.
* Möglichkeit, Inhaltsfragmente zu sortieren und in der ausgewählten Ansicht anzuzeigen.

## Voraussetzungen {#prerequisites}

### IMS-Authentifizierung {#ims-authentication}

Wenn Sie den IMS-Authentifizierungs-Workflow benötigen, müssen Sie sicherstellen, dass:

* Die Anwendung wird auf `HTTPS` ausgeführt.
* Die URL der Anwendung befindet sich in der Liste der zulässigen Umleitungs-URLs für den IMS-Client.
* Der IMS-Anmeldefluss wird mithilfe eines Popup-Fensters im Webbrowser konfiguriert und gerendert. Daher sollten Popup-Fenster im Ziel-Browser aktiviert oder zugelassen werden.

Wenn Ihre Anwendung bereits über den IMS-Workflow authentifiziert ist, können Sie stattdessen die entsprechenden IMS-Informationen hinzufügen.

## Installation {#installation}

Verwenden Sie die `ContentFragmentSelector`. Es gibt mehrere Installationsoptionen:

1. NPM-Registrierung (private Adobe-Registrierung)

   * Fügen Sie Folgendes zu `.npmrc` hinzu:

     ```html
     @aem-sites:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-aem-sites-release/
     ```

   * Installieren Sie dann

     ```html
     npm install @aem-sites/content-fragment-selector
     ```

1. Git-Repository

   * Fügen Sie `package.json` Abhängigkeiten Folgendes hinzu:

     ```html
     "@aem-sites/content-fragment-selector": "git+https://github.com/adobe/<your-private-repo-url>.git#version"
     ```

## Verwenden des Inhaltsfragment-Selektors {#using-the-Content-Fragment-selector}

Nachdem der Inhaltsfragmentselektor für die Verwendung des Inhaltsfragmentselektors mit Ihrer AEM as a Cloud Service-Anwendung eingerichtet und authentifiziert wurde, können Sie Inhaltsfragmente auswählen oder verschiedene andere Vorgänge ausführen, um im Repository nach Ihren Fragmenten zu suchen:

![Der Inhaltsfragment-Selektor](/help/headless/assets/content-fragment-selector-using.png)

* Mit der **Repository**-Auswahl oben rechts können Sie das Repository auswählen, das Sie verwenden möchten
* Im Bereich ganz links haben Sie folgende Möglichkeiten:
   * Ordner aus dem ausgewählten Repository ausblenden oder anzeigen
   * Einen bestimmten Ordner auswählen, um Inhaltsfragmente in diesem Ordner anzuzeigen
* Im Hauptbedienfeld haben Sie folgende Möglichkeiten:
   * Inhaltsfragmente auswählen
   * Nach Inhaltsfragmenten suchen
   * Sortiert die aktuelle Liste nach verschiedenen Spalten (aufsteigend oder absteigend)
   * Anzeige des Anzeigeformats anzeigen
   * Filter anzeigen, ausblenden und angeben

### Bedienfeld aus-/einblenden {#hide-show-panel}

Um Ordner im linken Navigationsbereich auszublenden, klicken Sie auf das Symbol **Ordner ausblenden**. Um die Änderungen rückgängig zu machen, klicken Sie erneut auf das Symbol **Ordner ausblenden**.

### Repository-Umschalter {#repository-switcher}

Mit der Inhaltsfragmentauswahl können Sie ein Repository für die Fragmentauswahl auswählen.

Sie können das gewünschte Repository aus der Dropdown-Liste **Repository** auswählen, die oben im Hauptbedienfeld verfügbar ist.

![Der Inhaltsfragment-Selektor](/help/headless/assets/content-fragment-repository-selector.png)

Die in der Dropdown-Liste verfügbaren Repository-Optionen basieren auf der `repositoryId`-Eigenschaft, die in der `index.html`-Datei definiert ist. Diese Eigenschaft basiert auf der Umgebung der ausgewählten IMS-Organisation, auf die der aktuell angemeldete Benutzer zugreift.

Nutzerinnen und Nutzer können eine bevorzugte `repositoryID` übergeben, um Fragmente aus einem bestimmten Repository zu rendern, und das Rendern des Repository-Umschalters beenden.

### Ordner für Inhaltsfragmente {#content-fragments-folders}

Das Inhaltsfragment-Repository ist eine Sammlung von Inhaltsfragment-Ordnern, die Sie zum Ausführen von Vorgängen verwenden können.

### Filter {#filters}

Die Inhaltsfragmentauswahl bietet außerdem vordefinierte Filteroptionen, mit denen Sie Ihre Suchergebnisse verfeinern können. Es stehen verschiedene Filter zur Verfügung, darunter:

* **Fragmentmodell**
* **Lokalisierung**
* **Status**: der aktuelle Status des Fragments; `New`, `Draft`, `Published`, `Modified`, `Unpublished`
* Tags
* Benutzer
* Uhrzeit und Datum

![Filteroptionen](/help/headless/assets/content-selector-filters.png)

Sie können auch einen Standardsuchfilter erstellen, der für die zukünftige Verwendung gespeichert wird. Um benutzerdefinierte Suchfilter für Ihre Inhaltsfragmente zu erstellen, können Sie die `filterSchema`-Eigenschaft verwenden.

### Suchleiste {#search-bar}

Mit der Inhaltsfragmentauswahl können Sie eine Volltextsuche nach Fragmenten im ausgewählten Repository durchführen. Wenn Sie beispielsweise den `wave` in die Suchleiste eingeben, werden alle Fragmente angezeigt, die den `wave` in einer der Metadateneigenschaften enthalten.

### Sortierung {#sorting}

Sie können Fragmente im Inhaltsfragment-Selektor nach verschiedenen Eigenschaften sortieren. Sie können die Fragmente auch in auf- oder absteigender Reihenfolge sortieren.

### Ansichtstyp {#view-type}

Mit der Inhaltsfragment-Auswahl können Sie das Fragment in der Datei anzeigen:

* **Tabellenansicht**
