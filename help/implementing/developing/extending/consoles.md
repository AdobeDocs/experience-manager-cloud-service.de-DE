---
title: Anpassen von Konsolen
description: Erfahren Sie mehr über die verschiedenen Optionen, die AEM zum Anpassen der Konsolen Ihrer Autoreninstanz bereitstellt.
exl-id: 832f9a86-07c4-4229-a0dc-8ad50a8195b0
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 96%

---

# Anpassen von Konsolen {#customizing-consoles}

AEM bietet Optionen zum Anpassen der Konsolen (und der [Seitenbearbeitungsfunktionen](/help/implementing/developing/extending/page-authoring.md)) Ihrer Autoreninstanz.

## Client-Bibliotheken {#clientlibs}

Mit Client-Bibliotheken können Sie die Standardimplementierung um neue Funktionen erweitern und gleichzeitig Standardfunktionen, -objekte und -methoden wiederverwenden. Bei der Anpassung mit Client-Bibliotheken können Sie unter `/apps.` Ihre eigene Client-Bibliothek erstellen. Beispielsweise kann sie den Code enthalten, der für Ihre benutzerdefinierte Komponente erforderlich ist.

Siehe [Verwenden Client-seitiger Bibliotheken für AEM as a Cloud Service](/help/implementing/developing/introduction/clientlibs.md)

## Überlagerungen {#overlays}

Überlagerungen basieren auf Knotendefinitionen und ermöglichen es Ihnen, Standardfunktionen (in `/libs`) durch Ihre eigenen benutzerdefinierten Funktionen (in `/apps`) zu überlagern. Beim Erstellen einer Überlagerung ist keine 1:1-Kopie des Originals erforderlich, da [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) das Vererben zulässt.

Überlagerungen können auf viele Arten zum Erweitern Ihrer AEM-Konsolen verwendet werden. In den folgenden Abschnitten werden verschieden Beispiele beschrieben.

Siehe auch [Überlagerungen für Adobe Experience Manager as a Cloud Service](/help/implementing/developing/introduction/overlays.md).

>[!TIP]
>
>Wenn Sie an Optionen zur Anpassung des Authoring-Erlebnisses interessiert sind, lesen Sie [Anpassen der Seitenbearbeitung](/help/implementing/developing/extending/page-authoring.md).

## Anpassen der Standardansicht für eine Konsole {#customizing-the-default-view-for-a-console}

Sie können die Standardansicht (Spalte, Karte, Liste) für eine Konsole anpassen:

* Sie können die Ansichten neu anordnen, indem Sie den erforderlichen Eintrag unter folgendem Pfad überschreiben:

   * `/libs/wcm/core/content/sites/jcr:content/views`

   * Der erste Eintrag ist die Standardeinstellung.

   * Die verfügbaren Knoten entsprechen den verfügbaren Anzeigeoptionen:

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

Sie können Ihre eigenen Komponenten einschließlich der entsprechenden Client-Bibliotheken für benutzerdefinierte Aktionen erstellen.

* Erstellen Sie beispielsweise eine Aktion **Weiterleiten an Social Media** unter:

   * `/apps/wcm/core/clientlibs/sites/js/socialmedia.js`

   * Diese kann mit einem Symbolleistenelement in Ihrer Konsole verbunden sein:

   * `/apps/<yourProject>/admin/ext/launches`

   * Beispielsweise im Auswahlmodus:

   * `content/jcr:content/body/content/header/items/selection/items/socialmedia`

### Beschränken einer Symbolleisten-Aktion auf eine bestimmte Gruppe {#restrict-a-toolbar-action-to-a-specific-group}

Sie können die Standardaktion mit einer benutzerdefinierten Render-Bedingung überlagern und bestimmte Bedingungen festlegen, die vor dem Rendern erfüllt sein müssen.

Erstellen Sie beispielsweise eine Komponente zum Steuern der Render-Bedingungen nach Gruppe:

* `/apps/myapp/components/renderconditions/group`

So wenden Sie diese auf die Aktion **Site erstellen** in der Site-Konsole an:

* `/libs/wcm/core/content/sites`

1. Erstellen Sie die Überlagerung:

   * `/apps/wcm/core/content/sites`

1. Fügen Sie dann die Render-Bedingung für die Aktion hinzu:

   * `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

Mithilfe der Eigenschaften auf diesem Knoten können Sie die `groups` definieren, die die spezifische Aktion ausführen dürfen, beispielsweise `administrators`.

### Anpassen von Spalten in der Listenansicht {#customizing-columns-in-list-view}

So passen Sie die Spalten in der Listenansicht an:

1. Überlagern Sie die Liste der verfügbaren Spalten.

   * Auf dem Knoten:

     `/apps/wcm/core/content/common/availablecolumns`

1. Fügen Sie die neuen Spalten hinzu oder entfernen Sie vorhandene.

Falls Sie zusätzliche Daten hinzufügen möchten, müssen Sie einen [PageInfoProvider](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageInfoProvider.html) mit einer Eigenschaft `pageInfoProviderType` schreiben.

>[!NOTE]
>
>Diese Funktion ist für Spalten von Textfeldern optimiert. Bei anderen Datentypen ist es möglich, `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` in `/apps` zu überlagern.

### Filtern von Ressourcen {#filtering-resources}

Bei Verwendung einer Konsole müssen Benutzende häufig aus Ressourcen wie Seiten, Komponenten oder Assets auswählen. Dabei kann eine Liste verwendet werden, aus der die Autorin bzw. der Autor ein Element auswählen muss.

Um die Liste in einer angemessenen Größe und auch für den Anwendungsfall relevant zu halten, kann ein Filter in Form eines benutzerdefinierten Prädikats implementiert werden. Weitere Details finden Sie unter [Anpassen der Seitenbearbeitung](/help/implementing/developing/extending/page-authoring.md#filtering-resources).
