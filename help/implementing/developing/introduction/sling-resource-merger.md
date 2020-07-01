---
title: Verwenden des Sling Resource Merger in Adobe Experience Manager als Cloud Service
description: Der Sling Resource Merger bietet Dienste für den Zugriff auf und das Zusammenführen von Ressourcen.
translation-type: tm+mt
source-git-commit: 8028682f19ba6ba7db6b60a2e5e5f5843f7ac11f
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 40%

---


# Verwenden des Sling Resource Merger in AEM as a Cloud Service {#using-the-sling-resource-merger-in-aem}

## Zweck {#purpose}

Der Sling Resource Merger bietet Dienste für den Zugriff auf und das Zusammenführen von Ressourcen. Er stellt Differenzierungsmechanismen bereit für:

* **[Überlagerungen](/help/implementing/developing/introduction/overlays.md)**von Ressourcen mithilfe der[Suchpfade](/help/implementing/developing/introduction/overlays.md#search-paths).

* **Überschreibungen** von Komponentendialogfeldern für die Touch-optimierte Benutzeroberfläche (`cq:dialog`) unter Verwendung der Ressourcentyphierarchie (anhand der Eigenschaft `sling:resourceSuperType`).

Mit dem Sling Resource Merger werden die Überlagerungs-/Überschreibungsressourcen bzw. -eigenschaften mit den ursprünglichen Ressourcen/Eigenschaften zusammengeführt:

* Der Inhalt der angepassten Definition hat eine höhere Priorität als der des Originals (d. h. er *überlagert* oder *überschreibt* ihn).

* Wo nötig, geben bei der Anpassung definierte [Eigenschaften](#properties) an, wie aus dem Original zusammengeführte Inhalte zu verwenden sind.

<!-- Still links to reference material in 6.5 -->

>[!CAUTION]
>
>Die Sling Resource Merger-Methode und die zugehörigen Methoden können nur mit der touchfähigen Benutzeroberfläche verwendet werden (der einzigen Benutzeroberfläche, die für AEM als Cloud Service verfügbar ist).

### Ziele für AEM {#goals-for-aem}

Die Ziele der Verwendung des Sling Resource Merger in AEM lauten wie folgt:

* ensure that customization changes are not made in `/libs`.
* reduce the structure that is replicated from `/libs`.

   When using the Sling Resource Merger it is not recommended to copy the entire structure from `/libs` as this would result in too much information being held in the customization (usually `/apps`). Das unnötige Duplizieren von Daten erhöht die Wahrscheinlichkeit von Problemen, wenn für das System ein Upgrade jedweder Art durchgeführt wird.

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen,
>
>Der Grund dafür ist, dass der Inhalt von `/libs` ggf. überschrieben werden kann, wenn Aktualisierungen auf Ihre Instanz angewendet werden.
>
>* Überlagerungen sind von [Suchpfaden](/help/implementing/developing/introduction/overlays.md#search-paths)abhängig.
   >
   >
* Überschreibungen hängen nicht von Suchpfaden ab, sie nutzen die Eigenschaft `sling:resourceSuperType` zur Herstellung der Verbindung.
   >  However, overrides are often defined under `/apps`, as best practice in AEM as a Cloud Service is to define customizations under `/apps`; this is because you must not change anything under `/libs`.


### Eigenschaften {#properties}

Der Resource Merger stellt die folgenden Eigenschaften zur Verfügung:

* `sling:hideProperties` ( `String` oder `String[]`)

   Gibt die Eigenschaft bzw. Liste der auszublendenden Eigenschaften an.

   The wildcard `*` hides all.

* `sling:hideResource` ( `Boolean`)

   Gibt an, ob die Ressourcen einschließlich der untergeordneten Elemente vollständig ausgeblendet werden sollen.

* `sling:hideChildren` ( `String` oder `String[]`)

   Enthält den untergeordneten Knoten oder die Liste der untergeordneten Knoten, die ausgeblendet werden sollen. Die Eigenschaften des Knotens werden beibehalten.

   The wildcard `*` hides all.

* `sling:orderBefore` ( `String`)

   Enthält den Namen des gleichrangigen Knotens, vor dem der aktuellen Knoten platziert werden soll.

These properties affect how the corresponding/original resources/properties (from `/libs`) are used by the overlay/override (often in `/apps`).

### Erstellen der Struktur {#creating-the-structure}

To create an overlay or override you need to recreate the original node, with the equivalent structure, under the destination (usually `/apps`). Beispiel:

* Überlagerung

   * Die Definition des Navigationseintrags für die Site-Konsole, wie in der Leiste dargestellt, wird wie folgt definiert:

      `/libs/cq/core/content/nav/sites/jcr:title`

   * Erstellen Sie zum Überlagern folgende Node:

      `/apps/cq/core/content/nav/sites`

      Aktualisieren Sie dann die Eigenschaft `jcr:title` nach Bedarf.

* Überschreibung

   * Die Definition des touchfähigen Dialoges für die Konsole &quot;Texte&quot;lautet wie folgt:

      `/libs/foundation/components/text/cq:dialog`

   * Um dies zu überschreiben, erstellen Sie den folgenden Knoten - z. B.:

      `/apps/the-project/components/text/cq:dialog`

Um eine dieser beiden Optionen zu erstellen, müssen Sie nur die Skelettstruktur neu erstellen. To simplify the recreation of the structure all intermediary nodes can be of type `nt:unstructured` (they do not have to reflect the original node type; for example, in `/libs`).

Somit werden im obigen Überlagerungsbeispiel die folgenden Knoten benötigt:

```shell
/apps
  /cq
    /core
      /content
        /nav
          /sites
```

>[!NOTE]
>
>When using the Sling Resource Merger (i.e. when dealing with the standard, touch-enabled UI) it is not recommended to copy the entire structure from `/libs` as it would result in too much information being held in `/apps`. Dies führt u. U. zu Problemen, wenn für das System ein Upgrade jedweder Art durchgeführt wird.

### Nutzungsszenarien {#use-cases}

Diese ermöglichen Ihnen zusammen mit den Standardfunktionen Folgendes:

* **Eigenschaft hinzufügen**

   The property does not exist in the `/libs` definition, but is required in the `/apps` overlay/override.

   1. Create the corresponding node within `/apps`
   1. Erstellen Sie die neue Eigenschaft auf diesem Knoten &quot;

* **Eigenschaft neu definieren (nicht automatisch erstellte Eigenschaften)**

   The property is defined in `/libs`, but a new value is required in the `/apps` overlay/override.

   1. Create the corresponding node within `/apps`
   1. Erstellen Sie die entsprechende Eigenschaft auf diesem Knoten (unter `apps`/).

      * Die Eigenschaft verfügt über eine Priorität, die auf der Konfiguration des Sling Resource Resolver basiert.
      * Das Ändern des Eigenschaftstyps wird unterstützt.

         If you use a property type different to the one used in `/libs`, then the property type you define will be used.
   >[!NOTE]
   >
   >Das Ändern des Eigenschaftstyps wird unterstützt.

* **Automatisch erstellte Eigenschaft neu definieren**

   By default, auto-created properties (such as `jcr:primaryType`) are not subject to an overlay/override to ensure that the node type currently under `/libs` is respected. To impose an overlay/override you have to recreate the node in `/apps`, explicitly hide the property and redefine it:

   1. Create the corresponding node under `/apps` with the desired `jcr:primaryType`
   1. Erstellen Sie die Eigenschaft `sling:hideProperties` auf diesem Knoten, wobei der Wert auf den Wert der automatisch erstellten Eigenschaft eingestellt ist. zum Beispiel `jcr:primaryType`

      Diese Eigenschaft, die unter `/apps`definiert wird, hat jetzt Vorrang vor der Eigenschaft, die unter `/libs`

* **Knoten und zugehörige untergeordnete Elemente neu definieren**

   The node and its children are defined in `/libs`, but a new configuration is required in the `/apps` overlay/override.

   1. Kombinieren Sie folgende Aktionen:

      1. Untergeordnete Elemente eines Knotens ausblenden (wobei die Eigenschaften des Knotens beibehalten werden)
      1. Eigenschaft(en) neu definieren

* **Eigenschaft ausblenden**

   The property is defined in `/libs`, but not required in the `/apps` overlay/override.

   1. Create the corresponding node within `/apps`
   1. Erstellen Sie eine Eigenschaft `sling:hideProperties` vom Typ `String` oder `String[]`. Geben Sie hiermit an, ob die Eigenschaften verborgen/ignoriert werden sollen. Platzhalter können auch verwendet werden. Beispiel:

      * `*`
      * `["*"]`
      * `jcr:title`
      * `["jcr:title", "jcr:description"]`

* **Knoten und zugehörige untergeordnete Elemente ausblenden**

   The node and its children are defined in `/libs`, but not required in the `/apps` overlay/override.

   1. Erstellen Sie den entsprechenden Knoten unter /apps.
   1. Create a property `sling:hideResource`

      * type: `Boolean`
      * value: `true`

* **Untergeordnete Elemente eines Knotens ausblenden (wobei die Eigenschaften des Knotens beibehalten werden)**

   The node, its properties and its children are defined in `/libs`. The node and its properties are required in the `/apps` overlay/override, but some or all of the child nodes are not required in the `/apps` overlay/override.

   1. Erstellen Sie den entsprechenden Knoten unter `/apps`
   1. Eigenschaft erstellen `sling:hideChildren`:

      * type: `String[]`
      * value: a list of the child nodes (as defined in `/libs`) to hide/ignore

      Der Platzhalter&amp;ast; können alle untergeordneten Knoten ausgeblendet/ignoriert werden.


* **Knoten neu anordnen**

   The node and its siblings are defined in `/libs`. A new position is required so the node is recreated in the `/apps` overlay/override, where the new position is defined in reference to the appropriate sibling node in `/libs`.

   * Use the `sling:orderBefore` property:

      1. Erstellen Sie den entsprechenden Knoten unter `/apps`
      1. Eigenschaft erstellen `sling:orderBefore`:

         Dies gibt den Knoten (wie in `/libs`) an, vor dem der aktuelle Knoten positioniert werden soll:

         * type: `String`
         * value: `<before-SiblingName>`

### Aufrufen des Sling Resource Merger aus dem Code {#invoking-the-sling-resource-merger-from-your-code}

Der Sling Resource Merger umfasst zwei benutzerdefinierte Ressourcenanbieter – einen für Überlagerungen und einen für Überschreibungen. Beide werden in Ihrem Code anhand eines Einhängepunkts abgerufen:

>[!NOTE]
>
>Beim Zugriff auf die Ressource sollten Sie den entsprechenden Einhängepunkt verwenden.
>
>This ensures that the Sling Resource Merger is invoked and the fully merged resource returned (reducing the structure that needs to be replicated from `/libs`).

* Überlagerung:

   * Zweck: Ressourcen anhand ihrer Suchpfade zusammenführen
   * mount point: `/mnt/overlay`
   * usage: `mount point + relative path`
   * Beispiel:

      * `getResource('/mnt/overlay' + '<relative-path-to-resource>');`

* Überschreibung:

   * Zweck: Ressourcen anhand ihrer Supertypen zusammenführen
   * mount point: `/mnt/overide`
   * usage: `mount point + absolute path`
   * Beispiel:

      * `getResource('/mnt/override' + '<absolute-path-to-resource>');`

<!--
### Example of Usage {#example-of-usage}

Some examples are covered:

* Overlay:

    * [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md)
    * [Customizing Page Authoring](/help/sites-developing/customizing-page-authoring-touch.md)

* Override:

    * [Configuring your Page Properties](/help/sites-developing/page-properties-views.md#configuring-your-page-properties)
-->
