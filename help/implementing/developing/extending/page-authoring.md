---
title: Anpassung des Seiten-Authorings
description: Erfahren Sie mehr über die Mechanismen, die AEM as a Cloud Service bietet, um die Seitenbearbeitungsfunktionen anzupassen.
exl-id: 98d3c7ab-46d2-4e8d-b0da-5c8a7b398135
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 24%

---

# Anpassung des Seiten-Authorings {#customizing-page-authoring}

Adobe Experience Manager as a Cloud Service bietet Mechanismen, mit denen Sie die Seitenbearbeitungsfunktion (und die [Konsolen](/help/implementing/developing/extending/consoles.md)) Ihrer Authoring-Instanz.

## Clientbibliotheken {#clientlibs}

Mit Clientlibs können Sie die Standardimplementierung erweitern, um neue Funktionen zu aktivieren und gleichzeitig die Standardfunktionen, -objekte und -methoden wiederzuverwenden.

Bei der Anpassung können Sie unter `/apps.` Ihre eigene Clientbibliothek erstellen. Die neue Clientbibliothek muss:

* Von der Authoring-Client-Bibliothek abhängig `cq.authoring.editor.sites.page`.
* Teil der entsprechenden `cq.authoring.editor.sites.page.hook` Kategorie.

Siehe [Verwenden Client-seitiger Bibliotheken auf AEM as a Cloud Service](/help/implementing/developing/introduction/clientlibs.md).

## Überlagerungen {#overlays}

Überlagerungen basieren auf Knotendefinitionen und ermöglichen es Ihnen, die Standardfunktionen in `/libs` mit Ihrer eigenen benutzerdefinierten Funktionalität in `/apps`.

Beim Erstellen einer Überlagerung ist keine 1:1-Kopie des Originals erforderlich, da die [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) ermöglicht die Vererbung.

Weitere Informationen finden Sie unter [JS-Dokumentationssatz](https://developer.adobe.com/experience-manager/reference-materials/6-5/jsdoc/ui-touch/editor-core/index.html).

Weitere Informationen zu Überlagerungen finden Sie unter [Überlagerungen für Adobe Experience Manager as a Cloud Service](/help/implementing/developing/introduction/overlays.md).

## Neue Ebene hinzufügen (Modus) {#add-new-layer-mode}

Beim Bearbeiten einer Seite gibt es verschiedene [Modi](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) verfügbar. Diese Modi werden mithilfe von [Ebenen](/help/implementing/developing/introduction/ui-structure.md#layer). Diese ermöglichen den Zugriff auf verschiedene Funktionstypen für denselben Seiteninhalt. Zu den standardmäßigen AEM gehören Bearbeiten, Layout, Entwickler, Timewarp, Live Copy-Status und Targeting.

### Ebenenbeispiel: Live Copy-Status {#layer-example-live-copy-status}

Eine standardmäßige AEM-Instanz stellt die MSM-Ebene bereit. Auf Daten im Zusammenhang mit [Multisite-Management](/help/sites-cloud/administering/msm/overview.md) und hebt sie in der Ebene hervor.

Um es in Aktion zu sehen, können Sie jede Sprachkopie im [WKND-Beispielinhalt](/help/implementing/developing/introduction/develop-wknd-tutorial.md) und wählen Sie die **Live Copy-Status** -Modus.

Sie finden die MSM-Ebenendefinition (als Referenz) in:

`/libs/wcm/msm/content/touch-ui/authoring/editor/js/msm.Layer.js`

### Codebeispiel {#code-sample}

Dies ist ein Beispielpaket, das zeigt, wie eine Ebene (Modus) für die MSM-Ansicht erstellt wird.

Den Code dieser Seite finden Sie unter [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode)

## Neue Auswahlkategorie zum Asset-Browser hinzufügen {#add-new-selection-category-to-asset-browser}

Der Asset-Browser zeigt Assets verschiedener Typen/Kategorien an (z. B. Bilder und Dokumente). Die Assets können auch anhand dieser Asset-Kategorien gefiltert werden.

### Codebeispiel {#code-sample-1}

`aem-authoring-extension-assetfinder-flickr` ist ein Beispielpaket, das zeigt, wie eine Gruppe zur Asset-Suche hinzugefügt wird. Dieses Beispiel verbindet mit [Flickr](https://www.flickr.com)ist der öffentliche Stream und zeigt sie im Seitenbereich an.

Den Code dieser Seite finden Sie unter [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr)

## Ressourcen filtern {#filtering-resources}

Beim Erstellen von Seiten muss der Benutzer häufig aus den Ressourcen in einer Liste auswählen.

Um die Liste in einer angemessenen Größe und auch für den Anwendungsfall relevant zu halten, kann ein Filter in Form eines benutzerdefinierten Prädikats implementiert werden. Wenn beispielsweise die Variable `pathbrowser` Die Granite-Komponente wird verwendet, um dem Benutzer die Auswahl des Pfads zu einer bestimmten Ressource zu ermöglichen. Die angezeigten Pfade können wie folgt gefiltert werden:

* Implementieren Sie das benutzerdefinierte Prädikat, indem Sie die Schnittstelle [`com.day.cq.commons.predicate.AbstractNodePredicate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/predicate/package-summary.html) implementieren.
* Geben Sie einen Namen für die Eigenschaft an und verwenden Sie diesen Namen, wenn Sie `pathbrowser` verwenden.

Weitere Informationen zum Erstellen eines benutzerdefinierten Prädikats finden Sie unter [diesen Artikel.](/help/implementing/developing/introduction/query-builder-custom-predicate.md)

## Hinzufügen einer neuen Aktion zu einer Komponenten-Symbolleiste {#add-new-action-to-a-component-toolbar}

Jede Komponente verfügt in der Regel über eine Symbolleiste, die Zugriff auf eine Reihe von Aktionen bietet, die für diese Komponente durchgeführt werden können.

### Codebeispiel {#code-sample-2}

`aem-authoring-extension-toolbar-screenshot` ist ein Beispielpaket, das die Erstellung einer benutzerdefinierten Symbolleistenaktion zum Rendern von Komponenten demonstriert.

Den Code dieser Seite finden Sie unter [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot)

## Neuen Editor für Bearbeitung im Kontext hinzufügen {#add-new-in-place-editor}

### Standard-Editor für Bearbeitung im Kontext {#standard-in-place-editor}

Bei der Standardinstallation von AEM:

1. `/libs/cq/gui/components/authoring/editors/clientlibs/core/js/editors/editorExample.js` enthält Definitionen der verschiedenen verfügbaren Editoren.

1. Es besteht eine Verbindung zwischen dem Editor und jedem Ressourcentyp (wie in der Komponente), der ihn verwenden kann:

   * `cq:inplaceEditing`

     Beispiel:

      * `/libs/foundation/components/text/cq:editConfig`
      * `/libs/foundation/components/image/cq:editConfig`

         * property: `editorType`

           Definiert den Typ des Inline-Editors, der verwendet wird, wenn die Bearbeitung im Kontext für diese Komponente ausgelöst wird. Beispiel: `text`, `textimage`, `image`, `title`.

1. Zusätzliche Konfigurationsdetails des Editors können mit einer `config` Knoten, der Konfigurationen enthält, und ein `plugin` -Knoten, der die erforderlichen Details zur Plug-in-Konfiguration enthält.


Im Folgenden finden Sie ein Beispiel zum Definieren von Seitenverhältnissen für das Bildzuschnitt-Plug-in der Bildkomponente.

```xml
   <cq:inplaceEditing
           jcr:primaryType="cq:InplaceEditingConfig"
           active="{Boolean}true"
           editorType="image">
           <config jcr:primaryType="nt:unstructured">
               <plugins jcr:primaryType="nt:unstructured">
                   <crop jcr:primaryType="nt:unstructured">
                       <aspectRatios jcr:primaryType="nt:unstructured">
                           <_x0031_6-10
                               jcr:primaryType="nt:unstructured"
                               name="16 : 10"
                               ratio="0.625"/>
                       </aspectRatios>
                   </crop>
               </plugins>
           </config>
   </cq:inplaceEditing>
```

>[!NOTE]
>
>AEM Anbauverhältnisse, wie durch die `ratio` -Eigenschaft, definiert als **height/width**. Dies unterscheidet sich von der herkömmlichen Definition als Breite/Höhe und erfolgt aus Gründen der Legacy-Kompatibilität. Die Benutzer, die die Seite erstellen, bemerken keinen Unterschied, vorausgesetzt, dass Sie die Eigenschaft `name` klar definieren, da diese auf der Benutzeroberfläche angezeigt wird.

#### Erstellen eines neuen Editors für Bearbeitung im Kontext {#creating-a-new-in-place-editor}

So erstellen Sie einen neuen Editor für Bearbeitung im Kontext (innerhalb Ihrer clientlib):

1. Implementierung:

   * `setUp`
   * `tearDown`

1. Registrieren Sie den Editor (einschließlich des Konstruktors):

   * `editor.register`

1. Stellen Sie die Verbindung zwischen dem Editor und jedem Ressourcentyp (wie in der Komponente) bereit, der ihn verwenden kann.

#### Codebeispiel zum Erstellen eines neuen Editors für Bearbeitung im Kontext {#code-sample-for-creating-a-new-in-place-editor}

`aem-authoring-extension-inplace-editor` ist ein Beispielpaket, das zeigt, wie ein Editor für die Bearbeitung im Kontext in AEM erstellt wird.

Den Code dieser Seite finden Sie unter [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor)

## Hinzufügen einer neuen Seitenaktion {#add-a-new-page-action}

So fügen Sie der Seitensymbolleiste eine neue Seitenaktion hinzu, z. B. eine **Zurück zu Sites** Aktion (Konsole).

### Codebeispiel {#code-sample-3}

`aem-authoring-extension-header-backtosites` ist ein Beispielpaket, das die Erstellung einer benutzerdefinierten Kopfzeilenleistenaktion demonstriert, mit der der Benutzer zurück zur Sites-Konsole springt.

Den Code dieser Seite finden Sie unter [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites)

## Anpassen des Aktivierungsanfrage-Workflows {#customizing-the-request-for-activation-workflow}

Der vorkonfigurierte Workflow, **Aktivierungsanfrage**:

* Wird automatisch im entsprechenden Menü angezeigt, wenn ein Inhaltsautor **nicht** über die entsprechenden Replikationsrechte verfügt, jedoch eine Mitgliedschaft von DAM-Benutzern und Autoren **hat**.

* Andernfalls wird nichts angezeigt, da die Replikationsrechte entfernt wurden.

Um bei dieser Aktivierung ein benutzerdefiniertes Verhalten zu erzielen, können Sie die **Aktivierungsanfrage** workflow:

1. In `/apps` überlagern **Sites** Assistent `/libs/wcm/core/content/common/managepublicationwizard`

   * Dadurch wird die allgemeine Instanz von `/libs/cq/gui/content/common/managepublicationwizard`.

1. Aktualisieren Sie das Workflow-Modell und die zugehörigen Konfigurationen/Skripte nach Bedarf.
1. Entfernen Sie die Berechtigung zum `replicate` Aktion aller entsprechenden Benutzer für alle relevanten Seiten. Damit dieser Workflow als Standardaktion ausgelöst wird, wenn ein Benutzer eine Seite veröffentlicht (oder repliziert).
