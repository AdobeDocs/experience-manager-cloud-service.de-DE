---
title: Seitenvorlagen
description: Seitenvorlagen werden bei der Erstellung einer Seite verwendet, die als Grundlage für die neue Seite verwendet wird
translation-type: tm+mt
source-git-commit: 69756d6831678151b0e8eb73db81113d49f17447
workflow-type: tm+mt
source-wordcount: '3228'
ht-degree: 62%

---


# Seitenvorlagen {#page-templates}

Beim Erstellen einer Seite müssen Sie eine Vorlage auswählen. Die Seitenvorlage wird als Grundlage für die neue Seite verwendet. Die Vorlage definiert die Struktur der Seite, anfängliche Inhalte und die Komponenten, die verwendet werden können (Designeigenschaften). Das hat mehrere Vorteile:

* Page Templates allow specialized authors to [create and edit templates](/help/sites-cloud/authoring/features/templates.md).
   * Diese spezialisierten Autoren werden als **Vorlagenautoren** bezeichnet.
   * Vorlagenautoren müssen Mitglieder der Gruppe `template-authors` sein.
* Seitenvorlagen behalten eine dynamische Verbindung zu allen Seiten bei, die mit ihnen erstellt wurden. Dadurch wird sichergestellt, dass alle Änderungen an der Vorlage auf den Seiten widergespiegelt werden.
* Seitenvorlagen machen die Seitenkomponente generischer, sodass die Hauptseitenkomponente ohne Anpassung verwendet werden kann.

Bei Seitenvorlagen werden die Elemente, die eine Seite bilden, innerhalb von Komponenten isoliert. Sie können die erforderlichen Komponentenkombinationen über eine Benutzeroberfläche konfigurieren. Damit entfällt die Notwendigkeit, für jede Seitenvariante eine neue Seitenkomponente zu entwickeln.

Dieses Dokument:

* Bietet einen Überblick über das Erstellen einer Seitenvorlage
* beschreibt die Administrator- bzw. Entwickleraufgaben, die zur Erstellung bearbeitbarer Vorlagen erforderlich sind.
* beschreibt die technischen Grundlagen bearbeitbarer Vorlagen.
* Beschreibt, wie AEM die Verfügbarkeit einer Vorlage bewertet

>[!NOTE]
>
>Bei den in diesem Dokument beschriebenen Schritten wird vorausgesetzt, dass Sie bereits mit dem Erstellen und Bearbeiten von Vorlagen vertraut sind. Weitere Informationen finden Sie im Dokument [Erstellen von Seitenvorlagen](/help/sites-cloud/authoring/features/templates.md) für Autoren, das detailliert beschreibt, welche Funktionen Vorlagenautoren mit bearbeitbaren Vorlagen zur Verfügung stehen.

>[!TIP]
>
>[Das WKND-Tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md) erläutert die Verwendung von Seitenvorlagen durch Implementierung eines Beispiels und ist sehr hilfreich, um zu verstehen, wie eine Vorlage in einem neuen Projekt eingerichtet wird

## Erstellen neuer Vorlagen {#creating-a-new-template}

Creating Page Templates is primarily done with the [template console and template editor](/help/sites-cloud/authoring/features/templates.md) by a template author. In diesem Abschnitt finden Sie einen Überblick über diesen Prozess, der anschließend aus technischer Perspektive beleuchtet wird.

Gehen Sie zum Erstellen einer neuen bearbeitbaren Vorlage wie folgt vor:

1. Erstellen Sie einen [Ordner für die Vorlagen](#template-folders). Dies ist zwar nicht unbedingt erforderlich, wird aber empfohlen.
1. Wählen Sie einen [Vorlagentyp](#template-type) aus. This is copied to create the [template definition](#template-definitions).

   >[!NOTE]
   >
   >Standardmäßig sind bereits diverse Vorlagen verfügbar. Bei Bedarf können Sie aber auch [eigene Site-spezifische Vorlagentypen](#creating-template-types) erstellen.

1. Konfigurieren Sie die Struktur, die Inhaltsrichtlinien, den anfänglichen Inhalt und das Layout der neuen Vorlage.

   **Struktur**

   * Die Struktur ermöglicht es Ihnen, Komponenten und Inhalte für Ihre Vorlage zu definieren.
   * Komponenten, die in der Vorlagenstruktur definiert sind, können auf resultierenden Seiten nicht verschoben oder gelöscht werden.
   * Wenn Seitenautoren die Möglichkeit haben sollen, Komponenten hinzuzufügen und zu entfernen, fügen Sie der Vorlage ein Absatzsystem hinzu.
   * Komponenten lassen sich entsperren und erneut sperren, damit Sie den anfänglichen Inhalt definieren können.

   Einzelheiten dazu, wie Vorlagenautoren Strukturen definieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-cloud/authoring/features/templates.md#editing-a-template-structure-template-author).

   Technische Details zu den Strukturen werden in diesem Dokument unter [Struktur](#structure) erläutert.

   **Richtlinien**

   * Die Richtlinien für Inhalte definieren die Designeigenschaften einer Komponente.

      * Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen.
   * Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

   Einzelheiten dazu, wie Vorlagenautoren Richtlinien definieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-cloud/authoring/features/templates.md#editing-a-template-structure-template-author).

   Technische Details zu den Richtlinien werden in diesem Dokument unter [Inhaltsrichtlinien](#content-policies) erläutert.

   **Anfänglicher Inhalt**

   * Der anfängliche Inhalt definiert Inhalt, der angezeigt wird, wenn eine Seite anfänglich auf Grundlage einer Vorlage erstellt wird.
   * Der anfängliche Inhalt kann dann von Seitenautoren bearbeitet werden.

   Einzelheiten dazu, wie Vorlagenautoren Strukturen definieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-cloud/authoring/features/templates.md#editing-a-template-initial-content-author).

   Technische Details zu den Richtlinien werden in diesem Dokument unter [Anfänglicher Inhalt](#initial-content) erläutert.

   **Layout**

   * Sie können das Vorlagen-Layout für verschiedene Geräte definieren.
   * Responsives Layout funktioniert für Vorlagen ebenso wie für die Seitenbearbeitung.

   Einzelheiten dazu, wie Vorlagenautoren Vorlagen-Layouts definieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-cloud/authoring/features/templates.md#editing-a-template-layout-template-author).

   Technische Details zu den Richtlinien werden in diesem Dokument unter [Layout](#layout) erläutert.

1. Aktivieren Sie die Vorlage und lassen Sie ihre Verwendung dann für bestimmte Inhaltsbäume zu.

   * Eine Vorlage kann aktiviert oder deaktiviert werden, um sie für Vorlagenautoren verfügbar bzw. nicht verfügbar zu machen.
   * Eine Vorlage kann für bestimmte Seitenverzweigungen verfügbar oder nicht verfügbar gemacht werden.

   Einzelheiten dazu, wie Vorlagenautoren Vorlagen aktivieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author).

   Technische Details zu den Richtlinien werden in diesem Dokument unter [Aktivieren und Zulassen von Vorlagen](#enabling-and-allowing-a-template-for-use) erläutert.

1. Verwenden Sie sie, um Inhaltsseiten zu erstellen.

   * Wenn Sie eine Vorlage zum Erstellen einer neuen Seite verwenden, ist kein Unterschied zwischen den statischen und bearbeitbaren Vorlagen ersichtlich.
   * Für die Seitenautoren ist der Prozess transparent.

   For details on how a page author uses templates to create a page, see [Creating and Organizing Pages](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#templates).

   Technische Details zu den Richtlinien werden in diesem Dokument unter [Resultierende Inhaltsseiten](#resultant-content-pages) erläutert.

>[!NOTE]
>
>The editor client library assumes the presence of the `cq.shared` namespace in content pages, and if it is absent the JavaScript error `Uncaught TypeError: Cannot read property 'shared' of undefined` will result.
>
>Alle Beispielinhaltsseiten enthalten `cq.shared`, sodass jeglicher darauf basierender Inhalt automatisch `cq.shared` umfasst. Wenn Sie sich jedoch ganz neue eigene Inhaltsseiten erstellen möchten, die nicht auf Beispielinhalt basieren, müssen Sie sicherstellen, dass Sie den `cq.shared`-Namespace einbinden.
>
>Weitere Informationen finden Sie unter [Verwendung clientseitiger Bibliotheken](/help/implementing/developing/introduction/clientlibs.md).

>[!CAUTION]
>
>Geben Sie in eine Vorlage nie Informationen ein, die internationalisiert werden müssen.

## Vorlagenordner {#template-folders}

Zum Organisieren Ihrer Vorlagen können Sie die folgenden Ordner verwenden:

* `global`
* Site-spezifisch

>[!NOTE]
>
>Obwohl Sie Ihre Ordner verschachteln können, werden sie den Benutzern in der **Vorlagenkonsole** als flache Struktur angezeigt.

In einer Standard-AEM-Instanz ist der Ordner `global` bereits in der Vorlagenkonsole vorhanden. Er enthält Standardvorlagen und dient als Ausweichlösung, wenn keine Richtlinien und/oder Vorlagentypen im aktuellen Ordner gefunden werden. Sie können Ihre Standardvorlagen entweder zu diesem Ordner hinzufügen oder aber einen neuen Ordner erstellen.

>[!NOTE]
>
>It is best practice to create a new folder to hold your customized templates and not to use the `global` folder.

>[!CAUTION]
>
>Folders must be created by a user with `admin` rights.

Arten von Vorlagen und Richtlinien werden gemäß der folgenden Rangordnung in allen Ordnern übernommen:

1. Der aktuelle Ordner
1. Übergeordnete(n) Elemente des aktuellen Ordners
1. `/conf/global`
1. `/apps`
1. `/libs`

Eine Liste aller zulässigen Einträge wird erstellt. If any configurations overlap ( `path`/ `label`), only the instance closest to the current folder is presented to the user.

Zum Erstellen eines neuen Ordners stehen Ihnen die folgenden Optionen zur Auswahl:

* Die programmgesteuerte Erstellung oder die Erstellung mit CRXDE Lite
* Using the [Configuration Browser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)

## Verwenden von CRXDE Lite {#using-crxde-lite}

1. Ein neuer Ordner (unter /conf) kann für Ihre Instanz entweder programmgesteuert oder mit CRXDE Lite erstellt werden.

   Nur die folgende Struktur darf verwendet werden:

   ```xml
   /conf
       <your-folder-name> [sling:Folder]
           settings [sling:Folder]
               wcm [cq:Page]
                   templates [cq:Page]
                   policies [cq:Page]
   ```

1. Sie können die folgenden Eigenschaften des Ordnerstammknotens definieren:

   `<your-folder-name> [sling:Folder]`

   * Name: `jcr:title`
   * Typ: `String`
   * Wert: Der Titel (für den Ordner), der Ihnen in der **Vorlagen**-Konsole angezeigt werden soll

1. Zusätzlich zu den standardmäßigen Autorenprivilegien und -berechtigungen (z. B. `content-authors`), müssen Sie jetzt eine oder mehrere Gruppen zuweisen und die erforderlichen Zugriffsrechte (ACLs) definieren, damit Ihre Autoren in der Lage sind, Vorlagen im neuen Ordner zu erstellen.

   Die Gruppe `template-authors` ist die Standardgruppe, die zugewiesen werden muss. See the section [ACLs and Groups](#acls-and-groups) for details.

   <!--See [Access Right Management](/help/sites-administering/user-group-ac-admin.md#access-right-management) for full details on managing and assigning access rights.-->

### Verwenden des Konfigurationsbrowsers {#using-the-configuration-browser}

1. Wechseln Sie zu **Globale Navigation** > **Tools** > [**Konfigurationsbrowser**.](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)

   The existing folders are listed to the left including the `global` folder.

1. Klicken Sie auf **Erstellen**.
1. In the **Create Configuration** dialog the following fields need to be configured:

   * **Titel**: Geben Sie einen Titel für den Konfigurationsordner ein.
   * **Bearbeitbare Vorlagen**: Aktivieren Sie dieses Kontrollkästchen, um bearbeitbare Vorlagen in diesem Ordner zuzulassen.

1. Klicken Sie auf **Erstellen**

>[!NOTE]
>
>In the [Configuration Browser,](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) you can edit the global folder and activate the **Editable Templates** option if you wish to create templates within this folder, however this is not recommended best practice.

### ACLs und Gruppen {#acls-and-groups}

Sobald Ihre Vorlagenordner erstellt sind (entweder über CRXDE oder mit dem Konfigurationsbrowser), müssen ACLs für die entsprechenden Gruppen für die Vorlagenordner definiert werden, um ein angemessenes Maß an Sicherheit zu gewährleisten.

The template folders for the [WKND tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md) can be used as an example.

#### Die Gruppe „template-authors“{#the-template-authors-group}

Die Gruppe `template-authors` ist die Gruppe zum Verwalten des Zugriffs auf Vorlagen und ist standardmäßig in AEM integriert, diese ist aber leer. Benutzer müssen der Gruppe für das Projekt bzw. die Site hinzugefügt werden.

>[!CAUTION]
>
>Die Gruppe `template-authors` ist nur für Benutzer, die die Möglichkeit haben müssen, neue Vorlagen zu erstellen.
>
>Die Bearbeitung von Vorlagen ist sehr leistungsstark und wenn nicht richtig ausgeführt, können vorhandene Vorlagen beschädigt werden. Daher sollte diese Rolle zielgerichtet und nur qualifizierten Benutzer zugewiesen werden.

In der folgenden Tabelle sind die erforderlichen Berechtigungen für die Bearbeitung von Vorlagen aufgeführt.

<table>
 <tbody>
  <tr>
   <th>Pfad          </th>
   <th>Rolle/Gruppe</th>
   <th>Berechtigungen<br /> </th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/templates</code></td>
   <td>Template Authors<br /> </td>
   <td>Lesen, Schreiben, Replizieren</td>
   <td>Vorlagenautoren, die Vorlagen im Site-spezifischen <code>/conf</code> Raum erstellen, lesen, aktualisieren, löschen und replizieren</td>
  </tr>
  <tr>
   <td>Anonymer Webbenutzer</td>
   <td>lesen</td>
   <td>Anonymer Webbenutzer muss Vorlagen beim Rendern einer Seite lesen</td>
  </tr>
  <tr>
   <td>Autoren von Inhalten</td>
   <td>replizieren</td>
   <td>replicateContent-Autoren müssen beim Aktivieren einer Seite die Vorlagen einer Seite aktivieren</td>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/policies</code></td>
   <td><code>Template Author</code></td>
   <td>Lesen, Schreiben, Replizieren</td>
   <td>Vorlagenautoren, die Vorlagen im Site-spezifischen <code>/conf</code> Raum erstellen, lesen, aktualisieren, löschen und replizieren</td>
  </tr>
  <tr>
   <td>Anonymer Webbenutzer</td>
   <td>lesen</td>
   <td>Anonymer Webbenutzer muss beim Rendern einer Seite Richtlinien lesen</td>
  </tr>
  <tr>
   <td>Autoren von Inhalten</td>
   <td>replizieren</td>
   <td>Inhaltsersteller müssen beim Aktivieren einer Seite die Richtlinien einer Vorlage aktivieren</td>
  </tr>
  <tr>
   <td rowspan="2"><code>/conf/&lt;site&gt;/settings/template-types</code></td>
   <td>Vorlagenautor</td>
   <td>lesen</td>
   <td>Der Vorlagenautor erstellt eine neue Vorlage basierend auf einem der vordefinierten Vorlagentypen.</td>
  </tr>
  <tr>
   <td>Anonymer Webbenutzer</td>
   <td>none</td>
   <td>Anonymer Webbenutzer darf nicht auf die Vorlagentypen zugreifen</td>
  </tr>
 </tbody>
</table>

This default `template-authors` group only covers the project setups, where all `template-authors` members are allowed to access and author all templates. Für komplexere Setups, bei denen mehrere Vorlagenautorengruppen benötigt werden, um einen getrennten Zugriff auf Vorlagen zu ermöglichen, müssen weitere benutzerdefinierte Vorlagenautorengruppen erstellt werden. Die Berechtigungen für die Vorlagenautorengruppen bleiben dabei jedoch dieselben.

## Vorlagentyp {#template-type}

Beim Erstellen einer neuen Vorlage müssen Sie einen Vorlagentyp angeben:

* Vorlagentypen stellen quasi Vorlagen für eine Vorlage bereit. Beim Erstellen einer neuen Vorlage wird die Struktur und der anfängliche Inhalt des gewählten Vorlagentyps verwendet, um die neue Vorlage zu erstellen.

   * Der Vorlagentyp wird zum Erstellen der Vorlage kopiert.
   * Nach Abschluss des Kopiervorgangs ist die einzige Verbindung zwischen der Vorlage und dem Vorlagentyp ein statischer Verweis zu Informationszwecken.

* Vorlagentypen ermöglichen es Ihnen, Folgendes zu definieren:

   * Den Ressourcentyp der Seitenkomponente.
   * Die Richtlinie des Stammknotens, die die im Vorlagen-Editor zulässigen Komponenten definiert.
   * Es wird empfohlen, die Haltepunkte für das responsive Raster und das Setup des Emulators für mobile Geräte über den Vorlagentyp zu definieren.

* AEM stellt einige vordefinierte Vorlagentypen wie HTML5-Seiten und Seiten mit adaptivem Formular bereit.

   * Weitere Beispiele finden Sie im [WKND-Tutorial.](/help/implementing/developing/introduction/develop-wknd-tutorial.md)

* Vorlagentypen werden in der Regel von Entwicklern definiert.

Die vordefinierten Vorlagentypen werden unter dem folgenden Pfad gespeichert:

* `/libs/settings/wcm/template-types`

>[!CAUTION]
>
>Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen. Dies liegt daran, dass der Inhalt von jederzeit durch ein Update zu AEM überschrieben werden kann. `/libs`

Ihre Site-spezifischen Vorlagentypen sollten an einer mit dem folgenden Pfad vergleichbaren Stelle gespeichert werden:

* `/apps/settings/wcm/template-types`

Definitions for your customized templates types should be stored in user-defined folders (recommended) or alternatively in `global`. Beispiel:

* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/template-types`
* `/conf/<my-folder>/settings/wcm/template-types`
* `/conf/global/settings/wcm/template-types`

>[!CAUTION]
>
>The template types have to respect the correct folder structure (i.e. `/settings/wcm/...`), otherwise the template types will not be found.

<!--
### Template Type and Mobile Device Groups {#template-type-and-mobile-device-groups-br}

The [device groups](/help/sites-developing/mobile.md#device-groups) used for an editable template (set as relative path of the property `cq:deviceGroups`) define which mobile devices are available as emulators in the [layout mode](/help/sites-authoring/responsive-layout.md) of page authoring. This value can be set in two places:

* On the editable template type
* On the editable template

When creating a new editable template, the value is copied from the template type to the individual template. If the value is not set on the type, it can be set on the template. Once a template is created, there is no inheritance from the type to the template.

>[!CAUTION]
>
>The value of `cq:deviceGroups` must be set as a relative path such as `mobile/groups/responsive` and not as an absolute path such as `/etc/mobile/groups/responsive`.

>[!NOTE]
>
>With static templates /help/sites-developing/page-templates-static.md, the value of `cq:deviceGroups` could be set at the root of the site.
>
>With editable templates, this value is now stored at the template level and is not supported at the page root level.
-->

### Erstellen von Vorlagentypen {#creating-template-types}

Wenn Sie eine Vorlage erstellt haben, die als Grundlage für andere Vorlagen dienen kann, können Sie diese Vorlage als Vorlagentyp kopieren.

1. Create a template as you would any Page Template [as documented here](/help/sites-cloud/authoring/features/templates.md#creating-a-new-template-template-author), which will serve as the basis of your template type.
1. Kopieren Sie mit CRXDE Lite die neu erstellte Vorlage aus dem Knoten `templates` in den Knoten `template-types` unter dem [Vorlagenordner](#template-folders).
1. Delete the template from the `templates` node under the [template folder](#template-folders).
1. In the copy of the template that is under the `template-types` node, delete all `cq:template` and `cq:templateType` `jcr:content` properties.

Sie können auch Ihren eigenen Vorlagentyp entwickeln, indem Sie eine bearbeitbare Beispielvorlage von GitHub als Grundlage verwenden.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub

* [Öffnen Sie das Projekt aem-sites-example-custom-template-type auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type/archive/master.zip) herunter

## Vorlagendefinitionen {#template-definitions}

Definitionen für bearbeitbare Vorlagen werden in [benutzerdefinierten Ordnern](#template-folders) (empfohlen) oder alternativ im Ordner `global` gespeichert. Beispiel:

* `/conf/<my-folder>/settings/wcm/templates`
* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/templates`
* `/conf/global/settings/wcm/templates`

Der Stammknoten der Vorlage weist den Typ `cq:Template` und das folgende Strukturgerüst auf:

```xml
<template-name>
  initial
    jcr:content
      root
        <component>
        ...
        <component>
  jcr:content
    @property status
  policies
    jcr:content
      root
        @property cq:policy
        <component>
          @property cq:policy
        ...
        <component>
          @property cq:policy
  structure
    jcr:content
      root
        <component>
        ...
        <component>
      cq:responsive
        breakpoints
  thumbnail.png
```

Die Hauptelemente sind:

* `<template-name>`

   * ` [initial](#initial-content)`
   * `jcr:content`
   * ` [structure](#structure)`
   * ` [policies](#policies)`
   * `thumbnail.png`

### jcr:content{#jcr-content} gespeichert 

Dieser Knoten enthält Eigenschaften für die Vorlage:

* **Name**: `jcr:title`
* **Name**: `status`
   * ``**Typ**: `String`
   * **Wert**: `draft`, `enabled` oder `disabled`

### Struktur {#structure}

Definiert die Struktur der resultierenden Seite:

* Is merged with the initial content ( `/initial`) when creating a new page.
* Änderungen an der Struktur werden auf allen mit der Vorlage erstellten Seiten berücksichtigt.
* The `root` ( `structure/jcr:content/root`) node defines the list of components that will be available in the resulting page.
   * Komponenten, die in der Vorlagenstruktur definiert sind, können auf resultierenden Seiten nicht verschoben oder gelöscht werden.
   * Sobald eine Komponente entsperrt ist, wird die Eigenschaft `editable` auf `true` festgelegt.
   * Sobald eine Komponente, die bereits Inhalt enthält, entsperrt ist, wird dieser Inhalt in die Verzweigung `initial` verschoben.

* The `cq:responsive` node holds definitions for the responsive layout.

### Anfänglicher Inhalt {#initial-content}

Definiert den anfänglichen Inhalt, den eine neue Seite bei Erstellung enthält:

* Er enthält einen Knoten `jcr:content`, der auf alle neue Seiten kopiert wird.
* Is merged with the structure ( `/structure`) when creating a new page.
* Vorhandene Seiten werden nicht aktualisiert, wenn der anfängliche Inhalt nach der Erstellung geändert wird.
* Der Knoten `root` enthält eine Liste von Komponenten, mit denen festgelegt wird, was auf der resultierenden Seite verfügbar sein soll.
* Wird einer Komponente im Strukturmodus Inhalt hinzugefügt und wird diese Komponente anschließend entsperrt (oder umgekehrt), so wird dieser Inhalt als anfänglicher Inhalt verwendet.

### Layout {#layout}

Beim [Bearbeiten einer Vorlage können Sie das Layout](/help/sites-cloud/authoring/features/templates.md)definieren. Dabei wird das [standardmäßige reaktionsfähige Layout](/help/sites-cloud/authoring/features/responsive-layout.md)verwendet.

<!-- that can also be [configured](/help/sites-administering/configuring-responsive-layout.md). -->

### Inhaltsrichtlinien {#content-policies}

Die Richtlinien für Inhalte definieren die Designeigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden). Inhaltsrichtlinien können mit dem Vorlagen-Editor erstellt und ausgewählt werden.

* The property `cq:policy`, on the `root` node
   `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/root`
Stellt einen relativen Verweis auf die Inhaltsrichtlinie für das Absatzsystem der Seite bereit.

* The property `cq:policy`, on the component-explicit nodes under `root`, provide links to the policies for the individual components.

* Die tatsächlichen Richtliniendefinitionen werden gespeichert unter:
   `/conf/<your-folder>/settings/wcm/policies/wcm/foundation/components`

>[!NOTE]
>
>Die Pfade der Richtliniendefinitionen sind vom Pfad der Komponente abhängig. `cq:policy` enthält einen relativen Verweis auf die Konfiguration selbst.

### Seitenrichtlinien {#page-policies}

Seitenrichtlinien ermöglichen es, die [Inhaltsrichtlinie](#content-policies) für die Seite (Hauptabsatzsystem) entweder in der Vorlage oder den resultierenden Seiten zu definieren.

### Aktivieren und Zulassen einer Vorlage {#enabling-and-allowing-a-template-for-use}

1. **Aktivieren Sie die Vorlage.**

   Bevor eine Vorlage verwendet werden kann, muss sie auf eine der folgenden Weisen aktiviert werden:

   * [Durch Aktivieren der Vorlage](/help/sites-cloud/authoring/features/templates.md) über die **Vorlagenkonsole**

   * Setting the status property on the `jcr:content` node.

      * Beispiel: on:
         `/conf/<your-folder>/settings/wcm/templates/<your-template>/jcr:content`

      * die Eigenschaft:

         * Name: status
         * Typ: String
         * Wert: `enabled`

1. **Zugelassene Vorlagen**

   * [Definieren Sie die Pfade zugelassener Vorlagen über die **Seiteneigenschaften**](/help/sites-cloud/authoring/features/templates.md#allowing-a-template-author) der entsprechenden Seite oder Stammseite einer Unterverzweigung.
   * Legen Sie die Eigenschaft fest:
      `cq:allowedTemplates`
Im 
`jcr:content` Knoten der erforderlichen Verzweigung.
   Beispielsweise mit dem Wert:

   `/conf/<your-folder>/settings/wcm/templates/.*`

## Resultierende Inhaltsseiten {#resultant-content-pages}

Für Seiten, die anhand bearbeitbarer Vorlagen erstellt wurden, gilt Folgendes:

* Sie werden mit einer Unterbaumstruktur erstellt, die aus `structure` und `initial` in der Vorlage zusammengeführt wird.

* Sie enthalten Verweise auf Informationen, die in der Vorlage und im Vorlagentyp enthalten sind. Dies wird mithilfe des Knotens `jcr:content` mit den folgenden Eigenschaften erreicht:

   * `cq:template` - Stellt den dynamischen Verweis auf die aktuelle Vorlage bereit und ermöglicht es, Änderungen an der Vorlage auf den aktuellen Seiten widerzuspiegeln.

   * `cq:templateType` - Enthält einen Verweis auf den Vorlagentyp.

![Zusammenhänge zwischen Vorlagen, Inhalten und Komponenten](assets/templates-content-components.png)

Das obige Diagramm veranschaulicht, wie Vorlagen, Inhalte und Komponenten zusammenhängen:

* Controller - `/content/<my-site>/<my-page>` - Die resultierende Seite, die auf die Vorlage verweist. Der Inhalt steuert den gesamten Prozess. Gemäß den Definitionen greift er auf die entsprechenden Vorlagen und Komponenten zu.
* Konfiguration - `/conf/<my-folder>/settings/wcm/templates/<my-template>` - Die [Vorlage und die zugehörigen Inhaltsrichtlinien](#template-definitions) definieren die Seitenkonfiguration.
* Model - OSGi bundles - The [OSGI bundles](/help/implementing/deploying/configuring-osgi.md) implement the functionality.
* View - `/apps/<my-site>/components` - On both the author and publish environments the content is rendered by components.

Beim Rendern einer Seite:

* **Vorlagen**:

   * The `cq:template` property of its `jcr:content` node will be referenced to access the template that corresponds to that page.

* **Komponenten**:

   * The page component will merge the `structure/jcr:content` tree of the template with the `jcr:content` tree of the page.
      * Die Seitenkomponente gestattet es dem Autor, nur die Knoten der Vorlagenstruktur zu bearbeiten, die als bearbeitbar gekennzeichnet sind (sowie jegliche untergeordneten Elemente).
      * Beim Rendern einer Komponente auf einer Seite wird der relative Pfad dieser Komponente vom Knoten `jcr:content` übernommen. Derselbe Pfad unter dem Knoten `policies/jcr:content` der Vorlage wird dann durchsucht.
         * The `cq:policy` property of this node points to the actual content policy (i.e. it holds the design configuration for that component).
            * Auf diese Weise können Sie mehrere Vorlagen verwenden, die dieselben Inhaltsrichtlinienkonfigurationen wiederverwenden.

### Verfügbarkeit der Vorlage {#template-availability}

Beim Erstellen einer neuen Seite in der Website-Admin-Oberfläche hängt die Liste der verfügbaren Vorlagen vom Speicherort der neuen Seite und den in den einzelnen Vorlagen angegebenen Platzierungsbeschränkungen ab.

Die folgenden Eigenschaften bestimmen, ob eine Vorlage `T` für eine neue Seite verwendet werden darf, die der Seite `P` untergeordnet platziert werden kann. Jede dieser Eigenschaften ist eine mehrwertige Zeichenfolge, welche null oder mehrere regulärere Ausdrücke enthält, die für die Übereinstimmung mit Pfaden verwendet werden:

* The `cq:allowedTemplates` property of the `jcr:content` subnode of `P` or an ancestor of `P`.

* Die `allowedPaths` Eigenschaft von `T`.

* Die `allowedParents` Eigenschaft von `T`.

* The `allowedChildren` property of the template of `P`.

Die Bewertung funktioniert wie folgt:

* The first non-empty `cq:allowedTemplates` property found while ascending the page hierarchy starting with `P` is matched against the path of `T`. Wenn keiner der Werte übereinstimmt, wird `T` abgelehnt.

* If `T` has a non-empty `allowedPaths` property, but none of the values match the path of `P`, `T` is rejected.

* If both of the above properties are either empty or non-existent, `T` is rejected unless it belongs to the same application as `P`. `T` gehört genau dann zurselben Anwendung wie `P`, wenn der Name der zweiten Ebene des Pfades von `T` mit dem Namen der zweiten Ebene des Pfades von `P` übereinstimmt. For example, the template `/apps/geometrixx/templates/foo` belongs to the same application as the page `/content/geometrixx`.

* If `T` has an non-empty `allowedParents` property, but none of the values match the path of `P`, `T` is rejected.

* If the template of `P` has a non-empty `allowedChildren` property, but none of the values match the path of `T`, `T` is rejected.

* In allen anderen Fällen ist `T` zulässig.

Das folgende Diagramm zeigt den Vorlagenauswertungsprozess:

![Vorlagenbewertungsverfahren](assets/template-evaluation.png)

>[!CAUTION]
>
>AEM Angeboten mehrere Eigenschaften, um die unter **Sites** zulässigen Vorlagen zu steuern. Eine Kombination dieser Regeln kann jedoch zu sehr komplexen Regeln führen, die sich nur schwer verfolgen und verwalten lassen.
>
>Daher empfiehlt Adobe, dass Sie einen einfachen Beginn durchführen, indem Sie Folgendes definieren:
>
>* Nur die `cq:allowedTemplates` Eigenschaft
   >
   >
* nur im Site-Stammordner
>
>
Ein Beispiel finden Sie im Inhalt des [WKND-Tutorials](/help/implementing/developing/introduction/develop-wknd-tutorial.md) : `/content/wknd/jcr:content`
>
>Die Eigenschaften `allowedPaths`, `allowedParents`und `allowedChildren` können auch auf den Vorlagen platziert werden, um komplexere Regeln zu definieren. Es ist jedoch nach Möglichkeit *viel* einfacher, weitere `cq:allowedTemplates` Eigenschaften in Unterabschnitten der Site zu definieren, wenn die zulässigen Vorlagen weiter eingeschränkt werden müssen.
>
>Ein weiterer Vorteil besteht darin, dass die `cq:allowedTemplates` Eigenschaften von einem Autor auf der Registerkarte &quot; **Erweitert** &quot;der **Seiteneigenschaften** aktualisiert werden können. Die anderen Vorlageneigenschaften können nicht über die (Standard-) Benutzeroberfläche aktualisiert werden. Daher benötigen Sie einen Entwickler, der die Regeln und eine Codebereitstellung für jede Änderung pflegt.

#### Einschränkende Vorlagen in untergeordneten Seiten {#limiting-templates-used-in-child-pages}

To limit what templates can be used to create child pages under a given page, use the `cq:allowedTemplates` property of `jcr:content` node of the page to specify the list of templates to be allowed as child pages. Each value in the list must be an absolute path to a template for an allowed child page, for example `/apps/wknd/templates/page-content`.

You can use the `cq:allowedTemplates` property on the template&#39;s  `jcr:content` node to have this configuration applied to all newly created pages that use this template.

Wenn Sie mehrere Einschränkungen hinzufügen möchten, z. B. bezüglich der Vorlagenhierarchie, können Sie die Eigenschaften `allowedParents/allowedChildren` auf der Vorlage verwenden. Sie können dann explizit angeben, dass Seiten, die aus einer Vorlage T erstellt wurden, übergeordnet/untergeordnet von Seiten sein müssen, die aus einer Vorlage T erstellt wurden.
