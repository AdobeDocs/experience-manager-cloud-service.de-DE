---
title: Micro-Frontend-Inhaltsfragment-Selektor für Adobe Experience Manager as a Cloud Service
description: Verwenden Sie den Micro-Frontend-Inhaltsfragment-Selektor, um Inhaltsfragmente in Ihrer Anwendung zu suchen, zu finden und abzurufen.
role: Admin, User
source-git-commit: 32e1b3cef768b420f32b70202ddadc80db2b74e8
workflow-type: ht
source-wordcount: '743'
ht-degree: 100%

---


# Micro-Frontend-Inhaltsfragment-Selektor {#micro-frontend-content-fragment-selector}

Der Micro-Frontend-Inhaltsfragment-Selektor bietet eine Benutzeroberfläche, die sich einfach mit dem Adobe Experience Manager (AEM) as a Cloud Service-Repository integrieren lässt. Über die Benutzeroberfläche können Sie Inhaltsfragmente im Repository durchsuchen bzw. suchen und in Ihrer Anwendung verwenden.

Die Micro-Frontend-Benutzeroberfläche wird über das Inhaltsfragment-Selektor-Paket in Ihrer Anwendung verfügbar gemacht. Alle Aktualisierungen am Paket werden automatisch importiert und in Ihre Anwendung geladen.

![Micro-Frontend-Inhaltsfragment-Selektor – Überblick](/help/headless/assets/content-fragment-selector-overview.png)

Der Inhaltsfragment-Selektor bietet viele Vorteile, z. B.:

* Einfache Integration mit allen Adobe-Anwendungen.
* Einfache Verwaltung, da Aktualisierungen des Inhaltsfragment-Selektor-Pakets automatisch für den Inhaltsfragment-Selektor bereitgestellt werden, der für Ihre Anwendung verfügbar ist. Das bedeutet, dass die Anwendung die neuesten Änderungen nicht aktiv laden muss.
* Einfache Anpassung durch Verwendung von Eigenschaften, die die Anzeige des Inhaltsfragment-Selektors in Ihrer Anwendung steuern.
* Schnelle Inhaltsfragmentnavigation in der Authoring-Oberfläche durch Volltextsuche und anpassbare Filter.
* Möglichkeit, zur Auswahl von Inhaltsfragmenten innerhalb einer IMS-Organisation zwischen Repositorys zu wechseln.
* Möglichkeit, Inhaltsfragmente zu sortieren und in der ausgewählten Ansicht anzuzeigen.

## Voraussetzungen {#prerequisites}

### IMS-Authentifizierung {#ims-authentication}

Wenn Sie den Workflow zur IMS-Authentifizierung benötigen, müssen Sie Folgendes sicherstellen:

* Die Anwendung wird unter `HTTPS` ausgeführt.
* Die URL der Anwendung befindet sich in der Liste der zulässigen Umleitungs-URLs für den IMS-Client.
* Der IMS-Anmeldefluss wird mithilfe eines Popup-Fensters im Webbrowser konfiguriert und gerendert. Daher sollten Popup-Fenster im Ziel-Browser aktiviert oder zugelassen werden.

Wenn Ihre Anwendung bereits mit dem IMS-Workflow authentifiziert ist, können Sie stattdessen auch die entsprechenden IMS-Informationen hinzufügen.

## Installation {#installation}

Verwenden Sie die Komponente `ContentFragmentSelector`. Es gibt verschiedene Installationsoptionen: 

1. NPM-Registrierung (private Adobe-Registrierung)

   * Fügen Sie Folgendes zu `.npmrc` hinzu:

     ```html
     @aem-sites:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-aem-sites-release/
     ```

   * Führen Sie dann die Installation durch:

     ```html
     npm install @aem-sites/content-fragment-selector
     ```

1. Git-Repository

   * Fügen Sie Folgendes zu den Abhängigkeiten in `package.json` hinzu:

     ```html
     "@aem-sites/content-fragment-selector": "git+https://github.com/adobe/<your-private-repo-url>.git#version"
     ```

## Verwenden des Inhaltsfragment-Selektors {#using-the-Content-Fragment-selector}

Sobald der Inhaltsfragment-Selektor zur Verwendung mit Ihrer AEM as a Cloud Service-Anwendung eingerichtet und authentifiziert wurde, können Sie Inhaltsfragmente auswählen oder verschiedene andere Vorgänge ausführen, um im Repository nach Ihren Fragmenten zu suchen:

![Der Inhaltsfragment-Selektor](/help/headless/assets/content-fragment-selector-using.png)

* Über den Selektor **Repository** oben rechts können Sie das zu verwendende Repository auswählen.
* Im Panel ganz links können Sie:
   * Ordner aus dem ausgewählten Repository aus- oder einblenden
   * einen bestimmten Ordner auswählen, um Inhaltsfragmente in diesem Ordner anzuzeigen
* Im Haupt-Panel können Sie:
   * Inhaltsfragmente auswählen
   * nach Inhaltsfragmenten suchen
   * die aktuelle Liste nach verschiedenen Spalten in auf- oder absteigender Reihenfolge sortieren
   * den Indikator für das Anzeigeformat sehen
   * Filter ein- bzw. ausblenden und festlegen

### Panel zum Aus-/Einblenden {#hide-show-panel}

Um Ordner im linken Navigationsbereich auszublenden, klicken Sie auf das Symbol **Ordner ausblenden**. Um die Änderungen rückgängig zu machen, klicken Sie erneut auf das Symbol **Ordner ausblenden**.

### Repository-Umschalter {#repository-switcher}

Mit dem Inhaltsfragment-Selektor können Sie ein Repository für die Fragmentauswahl auswählen.

Sie können das gewünschte Repository aus der Dropdown-Liste **Repository** auswählen, die oben im Haupt-Panel verfügbar ist.

![Der Inhaltsfragment-Selektor](/help/headless/assets/content-fragment-repository-selector.png)

Die in der Dropdown-Liste verfügbaren Repository-Optionen basieren auf der Eigenschaft `repositoryId`, die in der Datei `index.html` definiert ist. Diese Eigenschaft basiert auf der Umgebung der ausgewählten IMS-Organisation, auf die die aktuell angemeldete Person zugreift.

Nutzerinnen und Nutzer können eine bevorzugte `repositoryID` übergeben, um Fragmente aus einem bestimmten Repository zu rendern, und das Rendern des Repository-Umschalters beenden.

### Inhaltsfragmentordner {#content-fragments-folders}

Das Inhaltsfragment-Repository ist eine Sammlung von Inhaltsfragmentordnern, mit denen Sie Vorgänge durchführen können.

### Filter {#filters}

Der Inhaltsfragment-Selektor bietet außerdem vorkonfigurierte Filteroptionen, mit denen Sie Ihre Suchergebnisse verfeinern können. Es stehen verschiedene Filter zur Verfügung, darunter:

* **Fragmentmodell**
* **Lokalisierung**
* **Status**: der aktuelle Status des Fragments; `New`, `Draft`, `Published`, `Modified`, `Unpublished`
* Tags
* Benutzende
* Zeit und Datum

![Filteroptionen](/help/headless/assets/content-selector-filters.png)

Sie können auch einen Standardsuchfilter zur zukünftigen Verwendung erstellen und speichern. Um benutzerdefinierte Suchfilter für Ihre Inhaltsfragmente zu erstellen, können Sie die Eigenschaft `filterSchema` verwenden.

### Suchleiste {#search-bar}

Mit dem Inhaltsfragment-Selektor können Sie eine Volltextsuche nach Fragmenten im ausgewählten Repository durchführen. Wenn Sie zum Beispiel den Suchbegriff `wave` in die Suchleiste eingeben, werden alle Fragmente angezeigt, die den Suchbegriff `wave` in einer der Metadateneigenschaften aufweisen.

### Sortierung {#sorting}

Sie können Fragmente im Inhaltsfragment-Selektor nach verschiedenen Eigenschaften sortieren. Sie können die Fragmente auch in auf- oder absteigender Reihenfolge sortieren.

### Ansichtstyp {#view-type}

Mit dem Inhaltsfragment-Selektor können Sie das Fragment in der folgenden Ansicht anzeigen:

* **Tabellenansicht**
