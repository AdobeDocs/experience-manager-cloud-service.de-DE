---
title: Anpassen der Seitenbearbeitung
description: Erfahren Sie mehr über die Mechanismen, die AEM as a Cloud Service bietet, um die Seitenbearbeitungsfunktionen anzupassen.
exl-id: 98d3c7ab-46d2-4e8d-b0da-5c8a7b398135
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 100%

---

# Anpassen der Seitenbearbeitung {#customizing-page-authoring}

Adobe Experience Manager as a Cloud Service bietet verschiedene Mechanismen, mit denen Sie die Seitenbearbeitungsfunktion (und die [Konsolen](/help/implementing/developing/extending/consoles.md)) Ihrer Autoreninstanz anpassen können.

## Client-Bibliotheken {#clientlibs}

Mit Client-Bibliotheken können Sie die Standardimplementierung um neue Funktionen erweitern und gleichzeitig Standardfunktionen, -objekte und -methoden wiederverwenden.

Bei der Anpassung können Sie unter `/apps.` Ihre eigene Client-Bibliothek erstellen. Die neue Client-Bibliothek muss:

* die Authoring-Client-Bibliothek `cq.authoring.editor.sites.page` als Abhängigkeit aufweisen.
* der entsprechenden Kategorie in `cq.authoring.editor.sites.page.hook` angehören.

Siehe [Verwenden Client-seitiger Bibliotheken für AEM as a Cloud Service](/help/implementing/developing/introduction/clientlibs.md).

## Überlagerungen {#overlays}

Überlagerungen basieren auf Knotendefinitionen und ermöglichen es Ihnen, Standardfunktionen (in `/libs`) durch Ihre eigenen benutzerdefinierten Funktionen (in `/apps`) zu überlagern.

Wenn Sie eine Überlagerung erstellen, ist keine 1:1-Kopie des Originals erforderlich, da die [Sling-Ressourcenzusammenführung](/help/implementing/developing/introduction/sling-resource-merger.md) das Vererben zulässt.

Weitere Informationen finden Sie unter [JS-Dokumentationssatz](https://developer.adobe.com/experience-manager/reference-materials/6-5/jsdoc/ui-touch/editor-core/index.html).

Weitere Informationen zu Überlagerungen finden Sie unter [Überlagerungen für Adobe Experience Manager as a Cloud Service](/help/implementing/developing/introduction/overlays.md).

## Neue Ebene hinzufügen (Modus) {#add-new-layer-mode}

Beim Bearbeiten einer Seite sind verschiedene [Modi](/help/sites-cloud/authoring/page-editor/introduction.md#page-modes) verfügbar. Diese Modi werden mithilfe von [Ebenen](/help/implementing/developing/introduction/ui-structure.md#layer) implementiert. Diese ermöglichen den Zugriff auf verschiedene Funktionstypen für denselben Seiteninhalt. Zu den standardmäßigen AEM-Modi gehören Bearbeiten, Layout, Entwickler, Timewarp, Live Copy-Status und Targeting.

### Ebenenbeispiel: Live Copy-Status {#layer-example-live-copy-status}

Eine standardmäßige AEM-Instanz stellt die MSM-Ebene bereit. Diese greift auf Daten im Zusammenhang mit [Multisite-Management](/help/sites-cloud/administering/msm/overview.md) zu und hebt sie in der Ebene hervor.

Um sie im Einsatz zu sehen, können Sie jede Sprachkopie im [WKND-Beispielinhalt](/help/implementing/developing/introduction/develop-wknd-tutorial.md) bearbeiten und den **Live Copy-Status**-Modus auswählen.

Sie finden die MSM-Ebenendefinition (als Referenz) in:

`/libs/wcm/msm/content/touch-ui/authoring/editor/js/msm.Layer.js`

### Codebeispiel {#code-sample}

Dies ist ein Beispielpaket, das zeigt, wie eine Ebene (Modus) für die MSM-Ansicht erstellt wird.

Den Code dieser Seite finden Sie auf [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode).

## Hinzufügen einer neuen Auswahl-Kategorie zum Asset-Browser {#add-new-selection-category-to-asset-browser}

Der Asset-Browser zeigt Assets verschiedener Typen/Kategorien an (z. B. Bilder und Dokumente). Die Assets können auch anhand dieser Asset-Kategorien gefiltert werden.

### Codebeispiel {#code-sample-1}

`aem-authoring-extension-assetfinder-flickr` ist ein Beispielpaket, das das Hinzufügen einer Gruppe zur Asset-Suche demonstriert. Dieses Beispiel verbindet sich mit dem öffentlichen Stream von [Flickr](https://www.flickr.com) und zeigt ihn im Seitenbereich.

Den Code dieser Seite finden Sie auf [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr).

## Filtern von Ressourcen {#filtering-resources}

Beim Authoring von Seiten müssen Benutzende oft aus verschiedenen Ressourcen auswählen.

Um die Liste in einer angemessenen Größe und auch für den Anwendungsfall relevant zu halten, kann ein Filter in Form eines benutzerdefinierten Prädikats implementiert werden. Wenn z. B. die Benutzerin oder der Benutzer durch die `pathbrowser`-Granite-Komponente den Pfad zu einer bestimmten Ressource auswählen kann, können die gezeigten Pfade auf folgende Art gefiltert werden:

* Implementieren Sie das benutzerdefinierte Prädikat, indem Sie die Schnittstelle [`com.day.cq.commons.predicate.AbstractNodePredicate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/predicate/package-summary.html) implementieren.
* Geben Sie einen Namen für die Eigenschaft an und verwenden Sie diesen Namen, wenn Sie `pathbrowser` verwenden.

Weitere Details zum Erstellen einer benutzerdefinierten Eigenschaft finden Sie in [diesem Artikel](/help/implementing/developing/introduction/query-builder-custom-predicate.md).

## Hinzufügen einer neuen Aktion zu einer Komponenten-Symbolleiste {#add-new-action-to-a-component-toolbar}

Jede Komponente verfügt in der Regel über eine Symbolleiste, die Zugriff auf eine Reihe von Aktionen bietet, die für diese Komponente durchgeführt werden können.

### Codebeispiel {#code-sample-2}

`aem-authoring-extension-toolbar-screenshot` ist ein Beispielpaket, das die Erstellung einer benutzerdefinierten Symbolleistenaktion zum Rendern von Komponenten demonstriert.

Den Code dieser Seite finden Sie auf [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot).

## Hinzufügen eines neuen Editors für Bearbeitung im Kontext {#add-new-in-place-editor}

### Standardmäßiger Editor für Bearbeitung im Kontext {#standard-in-place-editor}

Bei der Standardinstallation von AEM:

1. `/libs/cq/gui/components/authoring/editors/clientlibs/core/js/editors/editorExample.js` enthält Definitionen der verschiedenen verfügbaren Editoren.

1. Es gibt eine Verknüpfung zwischen dem Editor und den einzelnen Ressourcenarten (wie Komponenten), die ihn verwenden können:

   * `cq:inplaceEditing`

     Beispiel:

      * `/libs/foundation/components/text/cq:editConfig`
      * `/libs/foundation/components/image/cq:editConfig`

         * property: `editorType`

           Definiert die Art des Inline-Editors, der verwendet wird, wenn die Bearbeitung im Kontext für diese Komponente ausgelöst wird, z. B. `text`, `textimage`, `image` und `title`.

1. Weitere Einstellungen des Editors können mit einem `config`-Knoten, der Konfigurationen enthält, sowie einem weiteren `plugin`-Knoten mit notwendigen Plug-in-Konfigurationsdetails konfiguriert werden.


Das folgende Beispiel zeigt die Definition von Seitenverhältnissen für das Bildbeschneidungs-Plug-in der Bildkomponente.

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
>Beschneidungsverhältnisse, die durch die Eigenschaft `ratio` definiert werden, sind in AEM als **Höhe/Breite** definiert. Dies unterscheidet sich von der herkömmlichen Definition als Breite/Höhe und erfolgt aus Gründen der Legacy-Kompatibilität. Die Benutzer, die die Seite erstellen, bemerken keinen Unterschied, vorausgesetzt, dass Sie die Eigenschaft `name` klar definieren, da diese auf der Benutzeroberfläche angezeigt wird.

#### Erstellen eines neuen Editors für Bearbeitung im Kontext {#creating-a-new-in-place-editor}

So erstellen Sie einen neuen Editor für Bearbeitung im Kontext (innerhalb Ihrer clientlib):

1. Implementierung:

   * `setUp`
   * `tearDown`

1. Registrieren Sie den Editor (einschließlich des Konstruktors):

   * `editor.register`

1. Geben Sie die Verknüpfung zwischen dem Editor und jedem Ressourcentyp an (wie in der Komponente), der ihn verwenden kann.

#### Codebeispiel zum Erstellen eines neuen Editors für Bearbeitung im Kontext {#code-sample-for-creating-a-new-in-place-editor}

`aem-authoring-extension-inplace-editor` ist ein Beispielpaket, das die Erstellung eines neuen Editors für die Bearbeitung im Kontext in AEM demonstriert.

Den Code dieser Seite finden Sie auf [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor).

## Hinzufügen einer neuen Seitenaktion {#add-a-new-page-action}

So fügen Sie der Seitensymbolleiste eine neue Seitenaktion hinzu, z. B. die Aktion **Zurück zu Sites** (Konsole).

### Codebeispiel {#code-sample-3}

`aem-authoring-extension-header-backtosites` ist ein Beispielpaket, das die Erstellung einer benutzerdefinierten Kopfzeilenleistenaktion demonstriert, mit der der Benutzer zurück zur Sites-Konsole springt.

Den Code dieser Seite finden Sie auf [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites).

## Anpassen des Aktivierungsanfrage-Workflows {#customizing-the-request-for-activation-workflow}

Der vorkonfigurierte Workflow, **Aktivierungsanfrage**:

* Wird automatisch im entsprechenden Menü angezeigt, wenn ein Inhaltsautor **nicht** über die entsprechenden Replikationsrechte verfügt, jedoch eine Mitgliedschaft von DAM-Benutzern und Autoren **hat**.

* Andernfalls wird nichts angezeigt, da die Replikationsrechte entfernt wurden.

Um das Verhalten bei dieser Aktivierung anzupassen, können Sie den **Aktivierungsanfrage**-Workflow überlagern:

1. Überlagern Sie in `/apps` den **Sites**-Assistenten `/libs/wcm/core/content/common/managepublicationwizard`

   * Dadurch wird die folgende gemeinsame Instanz überlagert `/libs/cq/gui/content/common/managepublicationwizard`.

1. Aktualisieren Sie das Workflow-Modell und je nach Bedarf relevante Konfigurationen/Skripte.
1. Entziehen Sie allen entsprechenden Benutzerinnen und Benutzern für alle relevanten Seiten das Recht zur `replicate`-Aktion, damit dieser Workflow standardmäßig ausgelöst wird, wenn Benutzende versuchen, eine Seite zu veröffentlichen (oder zu replizieren). 
