---
title: Verwenden des Sling Resource Merger in Adobe Experience Manager as a Cloud Service
description: Der Sling Resource Merger bietet Dienste für den Zugriff auf Ressourcen und für das Zusammenführen von Ressourcen.
exl-id: 5b6e5cb5-4c6c-4246-ba67-6b9f752867f5
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 95%

---

# Verwenden des Sling Resource Merger in AEM   as a Cloud Service {#using-the-sling-resource-merger-in-aem}

## Zweck {#purpose}

Der Sling Resource Merger bietet Dienste für den Zugriff auf und das Zusammenführen von Ressourcen. Er stellt Differenzierungsmechanismen bereit für:

* **[Überlagerungen](/help/implementing/developing/introduction/overlays.md)** von Ressourcen unter Verwendung der [Suchpfade](/help/implementing/developing/introduction/overlays.md#search-paths).

* **Überschreibungen** von Komponentendialogfeldern für die Touch-optimierte Benutzeroberfläche (`cq:dialog`) unter Verwendung der Ressourcentyphierarchie (anhand der Eigenschaft `sling:resourceSuperType`).

Mit dem Sling Resource Merger werden die Überlagerungs-/Überschreibungsressourcen bzw. -eigenschaften mit den ursprünglichen Ressourcen/Eigenschaften zusammengeführt:

* Der Inhalt der angepassten Definition hat eine höhere Priorität als der des Originals (d. h. er *überlagert* oder *überschreibt* dieses).

* Wo nötig, geben bei der Anpassung definierte [Eigenschaften](#properties) an, wie aus dem Original zusammengeführte Inhalte zu verwenden sind.

>[!CAUTION]
>
>Die Sling Resource Merger-Methode und verwandte Methoden können nur mit der Touch-optimierten Benutzeroberfläche verwendet werden (der einzigen Benutzeroberfläche, die für AEM as a Cloud Service verfügbar ist).

### Ziele für AEM {#goals-for-aem}

Die Ziele der Verwendung des Sling Resource Merger in AEM lauten wie folgt:

* Sicherstellen, dass Anpassungsänderungen nicht in `/libs` vorgenommen werden
* Die Struktur reduzieren, die von `/libs` repliziert wird

  Bei Verwendung des Sling Resource Merger wird nicht empfohlen, die gesamte Struktur aus `/libs` zu kopieren, da so zu viele Informationen in der Anpassung (im Allgemeinen `/apps`) gespeichert werden würden. Das unnötige Duplizieren von Daten erhöht die Wahrscheinlichkeit von Problemen, wenn für das System ein Upgrade jedweder Art durchgeführt wird.

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen.
>
>Der Grund dafür ist, dass der Inhalt von `/libs` ggf. überschrieben werden kann, wenn Upgrades auf Ihre Instanz angewendet werden.
>
>* Überlagerungen sind von [Suchpfaden](/help/implementing/developing/introduction/overlays.md#search-paths) abhängig.
>
>* Überschreibungen hängen nicht von Suchpfaden ab, sie nutzen die Eigenschaft `sling:resourceSuperType` zur Herstellung der Verbindung.
>
>Trotzdem werden Überschreibungen oft unter `/apps` definiert, denn die Best Practice in AEM as a Cloud Service besteht in der Definition von Anpassungen unter `/apps`, weil Sie unter `/libs` keine Änderungen vornehmen dürfen.

### Eigenschaften {#properties}

Der Resource Merger stellt die folgenden Eigenschaften zur Verfügung:

* `sling:hideProperties` ( `String` oder `String[]`)

  Gibt die Eigenschaft bzw. Liste der Eigenschaften an, die ausgeblendet werden sollen.

  Der Platzhalter `*` blendet alles aus.

* `sling:hideResource` ( `Boolean`)

  Gibt an, ob die Ressourcen vollständig ausgeblendet werden sollen, einschließlich ihrer untergeordneten Elemente.

* `sling:hideChildren` ( `String` oder `String[]`)

  Enthält den untergeordneten Knoten bzw. die Liste der untergeordneten Knoten, die ausgeblendet werden sollen. Die Eigenschaften des Knotens werden beibehalten.

  Der Platzhalter `*` blendet alles aus.

* `sling:orderBefore` ( `String`)

  Enthält den Namen des gleichrangigen Knotens, vor dem der aktuelle Knoten platziert werden soll.

Diese Eigenschaften beeinflussen, wie die entsprechenden/ursprünglichen Ressourcen/Eigenschaften (aus `/libs`) von den Überlagerungen/Überschreibungen (häufig in `/apps`) verwendet werden.

### Erstellen der Struktur {#creating-the-structure}

Zum Erstellen einer Überlagerung oder Überschreibung müssen Sie den ursprünglichen Knoten mit der äquivalenten Struktur unterhalb des Ziels (häufig `/apps`) neu erstellen. Beispiel:

* Überlagerung

   * Die Definition des Navigationseintrags für die Sites-Konsole, wie sie in der Leiste angezeigt ist, wird definiert unter:

     `/libs/cq/core/content/nav/sites/jcr:title`

   * Erstellen Sie zum Überlagern folgenden Knoten:

     `/apps/cq/core/content/nav/sites`

     Aktualisieren Sie dann die Eigenschaft `jcr:title` nach Bedarf.

* Überschreibung

   * Die Definition des Touch-fähigen Dialogfelds für die Textkonsole ist definiert unter:

     `/libs/foundation/components/text/cq:dialog`

   * Um dies zu überschreiben, erstellen Sie den folgenden Knoten, z. B.:

     `/apps/the-project/components/text/cq:dialog`

Um eine dieser beiden Optionen zu erstellen, müssen Sie nur die Skelettstruktur neu erstellen. Zum Vereinfachen der Neuerstellung der Struktur können alle dazwischenliegenden Knoten vom Typ `nt:unstructured` sein (sie müssen nicht dem ursprünglichen Knotentyp entsprechen, z. B. in `/libs`).

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
>Bei Verwendung des Sling Resource Merger (d. h. bei Verwendung der standardmäßigen, Touch-optimierten Benutzeroberfläche) ist es nicht empfehlenswert, die gesamte Struktur aus `/libs` zu kopieren, da so zu viele Informationen in `/apps` gespeichert würden. Dies führt u. U. zu Problemen, wenn für das System ein Upgrade jedweder Art durchgeführt wird.

### Anwendungsfälle {#use-cases}

Diese ermöglichen Ihnen zusammen mit den Standardfunktionen Folgendes:

* **Eigenschaft hinzufügen**

  Die Eigenschaft ist nicht in der `/libs`-Definition vorhanden, ist in der `/apps`-Überlagerung/-Überschreibung aber erforderlich.

   1. Erstellen Sie den entsprechenden Knoten in `/apps`.
   1. Erstellen Sie die neue Eigenschaft auf diesem Knoten.

* **Eigenschaft neu definieren (nicht automatisch erstellte Eigenschaften)**

  Die Eigenschaft ist in `/libs` definiert, aber für die `/apps`-Überlagerung/-Überschreibung ist ein neuer Wert erforderlich.

   1. Erstellen Sie den entsprechenden Knoten in `/apps`.
   1. Erstellen Sie die entsprechende Eigenschaft auf diesem Knoten (unter /`apps`).

      * Die Eigenschaft verfügt über eine Priorität, die auf der Konfiguration des Sling Resource Resolver basiert.
      * Das Ändern des Eigenschaftstyps wird unterstützt.

        Wenn Sie einen Eigenschaftstyp verwenden, der sich von dem in `/libs` verwendeten unterscheidet, wird der von Ihnen definierte Eigenschaftstyp verwendet.

  >[!NOTE]
  >
  >Das Ändern des Eigenschaftstyps wird unterstützt.

* **Automatisch erstellte Eigenschaft neu definieren**

  Standardmäßig unterliegen automatisch erstellte Eigenschaften (z. B. `jcr:primaryType`) keinen Überlagerungen/Überschreibungen, um sicherzustellen, dass der aktuell unter `/libs` befindliche Knotentyp respektiert wird. Um eine Überschreibung/Überlagerung vorzuschreiben, müssen Sie den Knoten in `/apps` neu erstellen, die Eigenschaft ausdrücklich ausblenden und neu definieren:

   1. Erstellen Sie den entsprechenden Knoten unter `/apps` mit dem gewünschten `jcr:primaryType`.
   1. Erstellen Sie die Eigenschaft `sling:hideProperties` auf diesem Knoten, wobei der Wert auf den Wert der automatisch erstellten Eigenschaft eingestellt ist, zum Beispiel `jcr:primaryType`.

      Diese Eigenschaft, die unter `/apps` definiert wird, hat jetzt Vorrang vor der Eigenschaft, die unter `/libs` definiert wurde.

* **Knoten und zugehörige untergeordnete Elemente neu definieren**

  Der Knoten und seine untergeordneten Elemente sind in `/libs` definiert, aber in der `/apps`-Überlagerung/Überschreibung wird eine neue Konfiguration benötigt.

   1. Kombinieren Sie folgende Aktionen:

      1. Untergeordnete Elemente eines Knotens ausblenden (wobei die Eigenschaften des Knotens beibehalten werden)
      1. Eigenschaft(en) neu definieren

* **Eigenschaft ausblenden**

  Die Eigenschaft ist in `/libs` definiert, ist aber für die `/apps`-Überlagerung/-Überschreibung nicht erforderlich.

   1. Erstellen Sie den entsprechenden Knoten in `/apps`.
   1. Erstellen Sie eine Eigenschaft `sling:hideProperties` vom Typ `String` oder `String[]`. Geben Sie hiermit an, ob die Eigenschaften verborgen/ignoriert werden sollen. Platzhalter können auch verwendet werden. Beispiel:

      * `*`
      * `["*"]`
      * `jcr:title`
      * `["jcr:title", "jcr:description"]`

* **Knoten und zugehörige untergeordnete Elemente ausblenden**

  Der Knoten und seine untergeordneten Elemente sind in `/libs` definiert, aber für die `/apps`-Überlagerung/-Überschreibung nicht erforderlich.

   1. Erstellen Sie den entsprechenden Knoten unter /apps.
   1. Erstellen Sie eine Eigenschaft `sling:hideResource`.

      * Typ: `Boolean`
      * Wert: `true`

* **Untergeordnete Elemente eines Knotens ausblenden (wobei die Eigenschaften des Knotens beibehalten werden)**

  Der Knoten, seine Eigenschaften und seine untergeordneten Elemente sind in `/libs` definiert. Der Knoten und seine Eigenschaften sind in der `/apps` -Überlagerung/-Überschreibung, aber einige oder alle untergeordneten Knoten sind im `/apps` Überlagerung/Überschreibung.

   1. Erstellen Sie den entsprechenden Knoten unter `/apps`
   1. Erstellen Sie die Eigenschaft `sling:hideChildren`:

      * Typ: `String[]`
      * Wert: eine Liste der auszublendenden/zu ignorierenden untergeordneten Knoten (wie definiert in `/libs`)

      Mit dem Platzhalter &amp;ast; können Sie alle untergeordneten Knoten ausblenden/ignorieren.

* **Knoten neu anordnen**

  Der Knoten und die ihm gleichrangigen Elemente sind in `/libs` definiert. Eine neue Position ist erforderlich, damit der Knoten in der `/apps`-Überlagerung/-Überschreibung neu erstellt wird, wobei die neue Position als Verweis auf den entsprechenden gleichrangigen Knoten in `/libs` definiert ist.

   * Verwenden Sie die Eigenschaft `sling:orderBefore`:

      1. Erstellen Sie den entsprechenden Knoten unter `/apps`
      1. Erstellen Sie die Eigenschaft `sling:orderBefore`:

         Dies gibt den Knoten (wie in `/libs`) an, vor dem der aktuelle Knoten positioniert werden soll:

         * Typ: `String`
         * Wert: `<before-SiblingName>`

### Aufrufen des Sling Resource Merger aus dem Code {#invoking-the-sling-resource-merger-from-your-code}

Der Sling Resource Merger umfasst zwei benutzerdefinierte Ressourcenanbieter – einen für Überlagerungen und einen für Überschreibungen. Beide werden in Ihrem Code anhand eines Einhängepunkts abgerufen:

>[!NOTE]
>
>Beim Zugriff auf die Ressource sollten Sie den entsprechenden Einhängepunkt verwenden.
>
>Dadurch wird sichergestellt, dass der Sling Resource Merger aufgerufen und die vollständig zusammengeführte Ressource zurückgegeben wird (was die Struktur reduziert, die repliziert werden muss von `/libs`).

* Überlagerung:

   * Zweck: Ressourcen anhand ihrer Suchpfade zusammenführen
   * Einhängepunkt: `/mnt/overlay`
   * Anwendung: `mount point + relative path`
   * Beispiel:

      * `getResource('/mnt/overlay' + '<relative-path-to-resource>');`

* Überschreibung:

   * Zweck: Ressourcen anhand ihrer Supertypen zusammenführen
   * Einhängepunkt: `/mnt/overide`
   * Anwendung: `mount point + absolute path`
   * Beispiel:

      * `getResource('/mnt/override' + '<absolute-path-to-resource>');`

