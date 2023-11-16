---
title: Anpassen von Konsolen
description: Erfahren Sie mehr über die verschiedenen Optionen, die AEM bietet, um die Konsolen Ihrer Authoring-Instanz anzupassen.
exl-id: 832f9a86-07c4-4229-a0dc-8ad50a8195b0
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 10%

---

# Anpassen von Konsolen {#customizing-consoles}

AEM bietet Optionen zum Anpassen der Konsolen (und der [Seitenbearbeitungsfunktionen](/help/implementing/developing/extending/page-authoring.md)) Ihrer Authoring-Instanz.

## Clientbibliotheken {#clientlibs}

Clientlibs ermöglichen es Ihnen, die Standardimplementierung zu erweitern, um neue Funktionen anzubieten und gleichzeitig Standardfunktionen, -objekte und -methoden wiederzuverwenden. Beim Anpassen mit clientlibs können Sie Ihre eigene clientlib unter erstellen. `/apps.` Beispielsweise kann er den Code enthalten, der für Ihre benutzerdefinierte Komponente erforderlich ist.

Weitere Informationen zu clientlibs finden Sie im Dokument . [Verwenden Client-seitiger Bibliotheken auf AEM as a Cloud Service.](/help/implementing/developing/introduction/clientlibs.md)

## Überlagerungen {#overlays}

Überlagerungen basieren auf Knotendefinitionen und ermöglichen es Ihnen, die unter `/libs` mit Ihrer eigenen benutzerdefinierten Funktionalität unter `/apps`. Beim Erstellen einer Überlagerung ist keine 1:1-Kopie des Originals erforderlich, da [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) ermöglicht die Vererbung.

Überlagerungen können auf viele Arten verwendet werden, um Ihre AEM Konsolen zu erweitern. In den folgenden Abschnitten finden Sie verschiedene Beispiele.

Weitere Informationen zu Überlagerungen finden Sie im Dokument [Überlagerungen für Adobe Experience Manager as a Cloud Service.](/help/implementing/developing/introduction/overlays.md)

>[!TIP]
>
>Informationen zu den Optionen zum Anpassen des Authoring-Erlebnisses finden Sie im Dokument . [Anpassen der Seitenbearbeitung.](/help/implementing/developing/extending/page-authoring.md)

## Anpassen der Standardansicht für eine Konsole {#customizing-the-default-view-for-a-console}

Sie können die Standardansicht (Spalte, Karte, Liste) für eine Konsole anpassen:

* Sie können die Ansichten neu anordnen, indem Sie den erforderlichen Eintrag unter folgendem Pfad überschreiben:

   * `/libs/wcm/core/content/sites/jcr:content/views`

   * Der erste Eintrag ist der Standardwert.

   * Die verfügbaren Knoten korrelieren mit den verfügbaren Anzeigeoptionen:

      * `column`
      * `card`
      * `list`

* Beispiel: In einer Überlagerung für eine Liste:

   * `/apps/wcm/core/content/sites/jcr:content/views/list`

   * Definieren Sie folgende Eigenschaften:

      * **Name**: `sling:orderBefore`
      * **Typ**: `String`
      * **Wert**: `column`

### Hinzufügen einer neuen Aktion zur Symbolleiste {#add-a-new-action-to-the-toolbar}

Sie können eigene Komponenten erstellen und die entsprechenden Client-Bibliotheken für benutzerdefinierte Aktionen einschließen.

* Sie können beispielsweise eine **Weiterleiten an Social Media** Aktion unter:

   * `/apps/wcm/core/clientlibs/sites/js/socialmedia.js`

   * Diese kann mit einem Symbolleistenelement in Ihrer Konsole verbunden sein:

   * `/apps/<yourProject>/admin/ext/launches`

   * Beispielsweise im Auswahlmodus:

   * `content/jcr:content/body/content/header/items/selection/items/socialmedia`

### Beschränken einer Symbolleistenaktion auf eine bestimmte Gruppe {#restrict-a-toolbar-action-to-a-specific-group}

Sie können eine benutzerdefinierte Rendering-Bedingung verwenden, um die Standardaktion zu überlagern und bestimmte Bedingungen vorzuschreiben, die erfüllt sein müssen, bevor sie gerendert wird.

Sie können beispielsweise eine Komponente erstellen, um die Renderbedingungen einer Gruppe entsprechend zu steuern:

* `/apps/myapp/components/renderconditions/group`

So wenden Sie diese auf die **Site erstellen** Aktion in der Sites-Konsole:

* `/libs/wcm/core/content/sites`

1. Erstellen Sie die Überlagerung:

   * `/apps/wcm/core/content/sites`

1. Fügen Sie dann die Rendering-Bedingung für die Aktion hinzu:

   * `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

Mithilfe von Eigenschaften auf diesem Knoten können Sie die `groups` definieren, die die spezifische Aktion ausführen dürfen, beispielsweise `administrators`.

### Anpassen von Spalten in der Listenansicht {#customizing-columns-in-list-view}

So passen Sie die Spalten in der Listenansicht an:

1. Liste der verfügbaren Spalten überlagern

   * Auf dem Knoten:

     `/apps/wcm/core/content/common/availablecolumns`

1. Fügen Sie Ihre neuen Spalten hinzu oder entfernen Sie vorhandene.

Wenn Sie zusätzliche Daten einfügen möchten, müssen Sie eine [PageInfoProvider](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageInfoProvider.html) mit `pageInfoProviderType` -Eigenschaft.

>[!NOTE]
>
>Diese Funktion ist für Spalten von Textfeldern optimiert. Bei anderen Datentypen ist es möglich, Überlagerungen vorzunehmen `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` in `/apps`.

### Ressourcen filtern {#filtering-resources}

Bei Verwendung einer Konsole muss ein Benutzer häufig aus Ressourcen wie Seiten, Komponenten oder Assets auswählen. Dies kann in Form einer Liste erfolgen, aus der der Autor ein Element auswählen muss.

Um die Liste in einer angemessenen Größe und auch für den Anwendungsfall relevant zu halten, kann ein Filter in Form eines benutzerdefinierten Prädikats implementiert werden. Lesen Sie das Dokument .[Anpassen der Seitenbearbeitung](/help/implementing/developing/extending/page-authoring.md#filtering-resources) für Details.
