---
title: Anpassen und Erweitern von Inhaltsfragmenten
description: Ein Inhaltsfragment erweitert ein Standard-Asset.
translation-type: ht
source-git-commit: a5d6a072dfd8df887309f56ad4a61b6b38b32fa7
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---


# Anpassen und Erweitern von Inhaltsfragmenten{#customizing-and-extending-content-fragments}

In Adobe Experience Manager as a Cloud Service erweitert ein Inhaltsfragment ein Standard-Asset. Siehe:

* [Erstellen und Verwalten von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md) und [Seitenbearbeitung mit Inhaltsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md).

* Weitere Informationen zu Standard-Assets finden Sie unter [Verwalten von Assets](/help/assets/manage-digital-assets.md) und [Anpassen und Erweitern des Asset-Editors](/help/assets/extend-asset-editor.md).

## Architektur {#architecture}

Ein Inhaltsfragment umfasst die folgenden grundlegenden [Bestandteile](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment):

* Ein *Inhaltsfragment*,
* das ein oder mehrere *Inhaltselemente* enthält,
* und eine oder mehrere *Inhaltsvarianten* aufweisen kann.

Je nach Fragmenttyp werden außerdem Modelle oder die Vorlagen für **einfache Fragmente** verwendet:

>[!CAUTION]
>
>Es werden derzeit [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md) zum Erstellen aller Fragmente empfohlen.
>
>Inhaltsfragmentmodelle werden für alle Beispiele in WKND verwendet.

* Inhaltsfragmentmodelle:

   * werden zum Definieren von Inhaltsfragmenten verwendet, die strukturierte Inhalte enthalten.
   * Inhaltsfragmentmodelle definieren die Struktur eines Inhaltsfragments, wenn dieses erstellt wird.
   * Ein Fragment verweist auf das Modell. Änderungen am Modell können sich daher auf alle abhängigen Fragmente auswirken.
   * Modelle werden anhand von Datentypen erstellt.
   * Funktionen zum Hinzufügen neuer Varianten und dergleichen müssen das Fragment entsprechend aktualisieren.
   >[!NOTE]
   >
   >Damit Sie ein Inhaltsfragment anzeigen/rendern können, muss Ihr Konto über `read`-Rechte für das Modell verfügen.

   >[!CAUTION]
   >
   >Alle Änderungen an einem vorhandenen Inhaltsfragmentmodell können sich auf abhängige Fragmente auswirken. Daher kann es zu verwaisten Eigenschaften in diesen Fragmenten kommen.

* Inhaltsfragmentvorlage – **Einfaches Fragment**:

   * wird zum Definieren von einfachen Inhaltsfragmenten verwendet.

   * Diese Vorlage definiert die (grundlegende, rein textbasierte) Struktur eines Inhaltsfragments, wenn dieses erstellt wird.

   * Die Vorlage wird beim Erstellen in das Fragment kopiert.

   * Funktionen zum Hinzufügen neuer Varianten und dergleichen müssen das Fragment entsprechend aktualisieren.

   * Die Inhaltsfragmentvorlage (**Einfaches Fragment**) arbeitet anders als die anderen Vorlagen in der AEM-Umgebung (z. B. Seitenvorlagen usw.). Daher sollte sie separat berücksichtigt werden.

   * Bei der Verwendung der Vorlage **Einfaches Fragment** wird der MIME-Typ des Inhalts anhand des tatsächlichen Inhalts verwaltet. Dies bedeutet, dass jedes Element und jede Variante einen anderen MIME-Typ haben kann.

### Integration von Sites mit Assets {#integration-of-sites-with-assets}

Die Inhaltsfragmentverwaltung (Content Fragment Management, CFM) ist Teil von AEM Assets:

* Inhaltsfragmente sind Assets.
* Sie verwenden vorhandene Assets-Funktionen.
* Sie sind vollständig mit Assets integriert (Admin-Konsole usw.).

Inhaltsfragmente werden als Sites-Funktion betrachtet, da:

* sie beim Authoring von Seiten verwendet werden.

#### Zuordnen von strukturierten Inhaltsfragmenten zu Assets {#mapping-structured-content-fragments-to-assets}

![Zuordnung von Inhaltsfragment zum Asset – strukturiert](assets/content-fragment-to-assets-structured.png)

Inhaltsfragmente mit strukturierten Inhalten (d. h. basierend auf einem Inhaltsfragmentmodell) werden einem einzelnen Asset zugeordnet:

* Alle Inhalte werden im Knoten `jcr:content/data` des Assets gespeichert:

   * Die Elementdaten werden im Master-Unterknoten gespeichert:
      `jcr:content/data/master`

   * Varianten werden in einem Unterknoten gespeichert, der den Namen der Variante hat:
z. B. `jcr:content/data/myvariation`

   * Die Daten der einzelnen Elemente werden im entsprechenden Unterknoten als Eigenschaft mit dem Elementnamen gespeichert: Das Inhaltselement `text` wird beispielsweise mit der Eigenschaft `text` in `jcr:content/data/master` gespeichert.

* Metadaten und verknüpfte Inhalte werden unter `jcr:content/metadata` gespeichert. Eine Ausnahme bilden der Titel und die Beschreibung, die nicht als Metadaten im herkömmlichen Sinne gelten und in `jcr:content` gespeichert werden.

#### Zuordnen von einfachen Inhaltsfragmenten zu Assets {#mapping-simple-content-fragments-to-assets}

![Zuordnung von Inhaltsfragment zum Asset – einfach](assets/content-fragment-to-assets-simple.png)

Einfache Inhaltsfragmente (basierend auf der Vorlage **Einfaches Fragment**) werden einem Verbund (Composite) aus Haupt-Asset und (optionalen) Unter-Assets zugeordnet:

* Alle nicht inhaltsbezogenen Daten in einem Fragment (wie Titel, Beschreibung, Metadaten, Struktur) werden nur im Haupt-Asset verwaltet.
* Der Inhalt des ersten Elements eines Fragments wird dem ursprünglichen Ausgabeformat des Haupt-Assets zugeordnet.

   * Die Varianten (falls vorhanden) des ersten Elements werden anderen Ausgabeformaten des Haupt-Assets zugeordnet.

* Zusätzliche Elemente (falls vorhanden) werden Unter-Assets des Haupt-Assets zugeordnet.

   * Der Hauptinhalt dieser zusätzlichen Elemente wird dem ursprünglichen Ausgabeformat des jeweiligen Unter-Assets zugeordnet.
   * Andere Varianten (falls zutreffend) zusätzlicher Elemente werden anderen Ausgabeformaten der jeweiligen Unter-Assets zugeordnet.

#### Asset-Speicherort     {#asset-location}

Wie bei Standard-Assets wird das Inhaltsfragment gespeichert in:

`/content/dam`

#### Asset-Berechtigungen {#asset-permissions}

Weitere Informationen finden Sie unter [Inhaltsfragmente – Überlegungen zum Löschen](/help/assets/content-fragments/content-fragments-delete.md).

#### Funktionsintegration {#feature-integration}

Integration mit dem Assets-Kern:

* Die Funktion „Inhaltsfragmentverwaltung“ (Content Fragment Management, CFM) baut auf dem Asset-Kern auf.

* CFM stellt eigene Implementierungen für Elemente in der Karten-, Spalten- und Listenansicht bereit. Diese sind mit den Ausgabeformatimplementierungen vorhandener Asset-Inhalte verknüpft.

* Einige Asset-Komponenten wurden für Inhaltsfragmente erweitert.

### Verwenden von Inhaltsfragmenten in Seiten {#using-content-fragments-in-pages}

>[!CAUTION]
>
>Die [Inhaltsfragment-Komponente als Teil der Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/content-fragment-component.html). Weitere Informationen finden Sie unter [Entwickeln von Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/developing.html).

AEM-Seiten können auf Inhaltsfragmente verweisen, ähnlich wie bei allen anderen Asset-Typen. AEM stellt die Kernkomponente für **[Inhaltsfragmente](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/content-fragment-component.html)**bereit, eine[Komponente, mit der Sie Inhaltsfragmente in Seiten einfügen können](/help/sites-cloud/authoring/fundamentals/content-fragments.md#adding-a-content-fragment-to-your-page). Sie können die Kernkomponente für**[Inhaltsfragmente](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/developing.html)** auch erweitern.

* Die Komponente verwendet die `fragmentPath`-Eigenschaft für Verweise auf das tatsächliche Inhaltsfragment. Die `fragmentPath`-Eigenschaft wird wie ähnliche Eigenschaften anderer Asset-Typen gehandhabt, beispielsweise wenn das Inhaltsfragment zu einem anderen Speicherort verschoben wird.

* Mit der Komponente können Sie die Variante auswählen, die angezeigt werden soll.

* Außerdem kann eine Reihe von Absätzen ausgewählt werden, um die Ausgabe zu beschränken, z. B. für die Ausgabe in mehreren Spalten.

* Die Komponente lässt auch Zwischeninhalte zu:

   * Die Komponente ermöglicht es Ihnen, andere Assets (Bilder usw.) zwischen den Absätzen des Fragments zu platzieren, auf das verwiesen wird.

   * Bei Zwischeninhalten müssen Sie:

      * beachten, dass Verweise möglicherweise instabil sind. Bei der Seitenbearbeitung hinzugefügte Zwischeninhalte haben keine feste Beziehung zu dem Absatz, neben dem sie platziert werden; es wird ein neuer Absatz (im Inhaltsfragment-Editor) eingefügt, bevor der Zwischeninhalt die relative Position verlieren kann.

      * die zusätzlichen Parameter (wie Varianten- und Absatzfilter) berücksichtigen, um zu konfigurieren, was auf der Seite dargestellt wird.

>[!NOTE]
>
>**Inhaltsfragmentmodell:**
>
>Bei Verwendung eines auf einem Inhaltsfragmentmodell basierenden Inhaltsfragments auf einer Seite wird auf das Modell verwiesen. Falls das Modell also zum Zeitpunkt der Seitenveröffentlichung nicht veröffentlicht wurde, wird dies gekennzeichnet und das Modell zu den Ressourcen hinzugefügt, die mit der Seite veröffentlicht werden sollen.
>
>**Inhaltsfragmentvorlage – Einfaches Fragment:**
>
>Bei Verwendung eines auf der Inhaltsfragmentvorlage **Einfaches Fragment** basierten Inhaltsfragments auf einer Seite erfolgt kein Verweis, da die Vorlage beim Erstellen des Fragments kopiert wurde.

### Integration mit anderen Frameworks {#integration-with-other-frameworks}

Inhaltsfragmente können mit folgenden Frameworks integriert werden:

* **Übersetzungen**

   Inhaltsfragmente sind vollständig mit dem AEM-Übersetzungs-Workflow integriert. Auf Architekturebene bedeutet dies:

   * Die einzelnen Übersetzungen eines Inhaltsfragments sind separate Fragmente, z. B.:

      * sie befinden sich unter verschiedenen Sprachstämmen, verwenden aber genau denselben relativen Pfad unterhalb des entsprechenden Sprachstamms:

         `/content/dam/<path>/en/<to>/<fragment>`

         im Vergleich zu

         `/content/dam/<path>/de/<to>/<fragment>`
   * Außer den regelbasierten Pfaden besteht keinerlei Verbindung zwischen den unterschiedlichen Sprachversionen von Inhaltsfragmenten. Sie werden als zwei separate Fragmente behandelt, obwohl die Benutzeroberfläche Funktionen zum Navigieren zwischen den Sprachvarianten beinhaltet.
   >[!NOTE]
   >
   >Der AEM-Übersetzungs-Workflow arbeitet mit `/content`:
   >
   >* Da sich die Inhaltsfragmentmodelle in `/conf` befinden, sind sie nicht in diesen Übersetzungen beinhaltet. Sie können die Strings der Benutzeroberfläche internationalisieren.


* **Metadatenschemata**

   * Inhaltsfragmente verwenden [Metadatenschemata](/help/assets/metadata-schemas.md) (wieder), die mit Standard-Assets definiert werden können.

   * CFM bietet ein eigenes, spezifisches Schema:

      `/libs/dam/content/schemaeditors/forms/contentfragment`

      dieses kann bei Bedarf erweitert werden.

   * Das entsprechende Schemaformular ist mit dem Fragment-Editor integriert.

## Server-seitige API für die Inhaltsfragmentverwaltung     {#the-content-fragment-management-api-server-side}

Sie können die serverseitige API für den Zugriff auf Inhaltsfragmente verwenden, siehe:

[com.adobe.cq.dam.cfm](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/ref/javadoc/com/adobe/cq/dam/cfm/package-frame.html)

>[!CAUTION]
>
>Es wird dringend empfohlen, die serverseitige API zu verwenden, anstatt direkt auf die Inhaltsstruktur zuzugreifen.

### Hauptschnittstellen     {#key-interfaces}

Die folgenden drei Schnittstellen können als Einstiegspunkte dienen:

* **Inhaltsfragment** ([ContentFragment](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/ref/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html))

   In dieser Schnittstelle können Sie abstrakt mit einem Inhaltsfragment arbeiten.

   Die Schnittstelle bietet folgende Möglichkeiten:

   * Verwalten grundlegender Daten (z. B. Abrufen von Namen, Abrufen/Festlegen von Titel, Beschreibung)
   * Zugriff auf Metadaten
   * Zugriff auf Elemente:

      * Auflisten von Elementen
      * Abrufen von Elementen nach Name
      * Erstellen neuer Elemente (siehe [Einschränkungen](#caveats))

      * Zugriff auf Elementdaten (siehe `ContentElement`)
   * Auflisten der für das Fragment definierten Varianten
   * Globales Erstellen neuer Varianten
   * Verwalten zugeordneter Inhalte:

      * Auflisten von Sammlungen
      * Hinzufügen von Sammlungen
      * Entfernen von Sammlungen
   * Zugriff auf das Modell oder die Vorlage des Fragments
   Folgende Schnittstellen stehen für die Hauptelemente eines Fragments:

   * **Inhaltselement** ([ContentElement](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/ref/javadoc/com/adobe/cq/dam/cfm/ContentElement.html))

      * Abrufen grundlegender Daten (Name, Titel, Beschreibung)
      * Abrufen/Festlegen von Inhalten
      * Zugriff auf Varianten eines Elements:

         * Auflisten von Varianten
         * Abrufen von Varianten nach Name
         * Erstellen neuer Varianten (siehe [Einschränkungen](#caveats))
         * Entfernen von Varianten (siehe [Einschränkungen](#caveats))
         * Zugriff auf Variantendaten (siehe `ContentVariation`)
      * Tastaturbefehl zum Auflösen von Varianten (Anwenden zusätzlicher implementierungsspezifischer Ausweich-Logik, falls die angegebene Variante für ein Element nicht verfügbar ist)
   * **Inhaltsvariante** ([ContentVariation](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/ref/javadoc/com/adobe/cq/dam/cfm/ContentVariation.html))

      * Abrufen grundlegender Daten (Name, Titel, Beschreibung)
      * Abrufen/Festlegen von Inhalten
      * Einfache Synchronisierung basierend auf den zuletzt geänderten Informationen
   Alle drei Schnittstellen (`ContentFragment`, `ContentElement`, `ContentVariation`) erweitern die `Versionable`-Schnittstelle durch zusätzliche, für Inhaltsfragmente erforderliche Versionierungsfunktionen:

   * Erstellen neuer Versionen des Elements
   * Auflisten der Versionen des Elements
   * Abrufen des Inhalts einer spezifischen Version des versionierten Elements







### Anpassen mit adaptTo()     {#adapting-using-adaptto}

Folgendes kann angepasst werden:

* `ContentFragment` kann angepasst werden an:

   * `Resource`: die zugrunde liegende Sling-Ressource. Um die zugrunde liegende `Resource` direkt zu aktualisieren, muss das `ContentFragment`-Objekt neu erstellt werden.

   * `Asset`: die DAM-`Asset`-Abstrahierung, die für das Inhaltsfragment steht. Um das zugrunde liegende `Asset` direkt zu aktualisieren, muss das `ContentFragment`-Objekt neu erstellt werden.

* `ContentElement` kann angepasst werden an:

   * `ElementTemplate` – für den Zugriff auf die Strukturdaten des Elements.

* `Resource` kann angepasst werden an:

   * `ContentFragment`

### Einschränkungen {#caveats}

Beachten Sie Folgendes:

* Die gesamte API ist so konzipiert, dass Änderungen **nicht** automatisch persistent gespeichert werden (es sei denn, dies ist anders in der Java-Dokumentation der API angegeben). Daher müssen Sie immer den Ressourcenkonfliktlöser der entsprechenden Anfrage (oder den tatsächlich verwendeten Konfliktlöser) festlegen.

* Aufgaben, für die möglicherweise zusätzliche Arbeitsschritte erforderlich sind:

   * Erstellen Sie neue Varianten von `ContentFragment`, um die Datenstruktur zu aktualisieren.

   * Durch das Entfernen vorhandener Varianten eines Elements mithilfe von `ContentElement.removeVariation()` werden die der Variante zugewiesenen globalen Datenstrukturen nicht aktualisiert. Verwenden Sie stattdessen `ContentFragment.removeVariation()`, um sicherzustellen, dass diese Datenstrukturen synchron bleiben, wodurch eine Variante global entfernt wird.

## Client-seitige API für die Inhaltsfragmentverwaltung     {#the-content-fragment-management-api-client-side}

>[!CAUTION]
>
>Die Client-seitige API ist intern.

### Zusätzliche Informationen {#additional-information}

Beachten Sie Folgendes:

* `filter.xml`

   `filter.xml` für die Inhaltsfragmentverwaltung ist so konfiguriert, dass es sich nicht mit dem Hauptinhaltspaket für Assets überschneidet.

## Bearbeitungssitzungen {#edit-sessions}

>[!CAUTION]
>
>Beachten Sie diese Hintergrundinformationen. Sie sollten hier nichts ändern (da dies im Repository als *privater Bereich* gekennzeichnet ist). Es kann aber in einigen Fällen hilfreich sein, die internen Prozesses zu verstehen.

Das Bearbeiten eines Inhaltsfragments, das mehrere Ansichten (d. h. HTML-Seiten) umspannen kann, ist atomisch. Da die atomischen Bearbeitungsfunktionen für mehrere Ansichten kein typisches AEM-Konzept sind, verwenden Inhaltsfragmente eine sogenannte *Bearbeitungssitzung*.

Eine Bearbeitungssitzung wird gestartet, wenn der Benutzer ein Inhaltsfragment im Editor öffnet. Die Bearbeitungssitzung ist beendet, wenn der Benutzer den Editor durch Auswählen von **Speichern** oder **Abbrechen** verlässt.

Technisch gesehen werden alle Änderungen an *Live*-Inhalten wie bei allen anderen AEM-Bearbeitungen vorgenommen. Beim Starten der Bearbeitungssitzung wird eine Version des aktuellen, nicht bearbeiteten Status erstellt. Wenn ein Benutzer eine Bearbeitung abbricht, wird diese Version wiederhergestellt. Wenn der Benutzer auf **Speichern** klickt, wird nichts Bestimmtes ausgeführt, da die Bearbeitung an *Live*-Inhalten ausgeführt wurde. Daher bleiben alle Änderungen bereits erhalten. Durch Klicken auf **Speichern** wird auch eine Hintergrundverarbeitung ausgelöst (z. B. das Erstellen von Volltextsuchinformationen und/oder das Bearbeiten von gemischten Medien-Assets).

Es gibt einige Sicherheitsmaßnahmen für Randfälle, beispielsweise, wenn der Benutzer versucht, den Editor zu verlassen, ohne die Bearbeitungssitzung zu speichern oder abzubrechen. Außerdem ist eine regelmäßige automatische Speicherung verfügbar, um Datenverluste zu vermeiden.
Beachten Sie, dass zwei Benutzer möglicherweise dasselbe Inhaltsfragment gleichzeitig bearbeiten und daher gegenseitig die Änderungen überschreiben können. Um dies zu verhindern, muss das Inhaltsfragment gesperrt werden, indem die *Checkout*-Aktion der DAM-Verwaltung auf das Fragment angewendet wird.

## Beispiele {#examples}

### Beispiel: Zugreifen auf ein vorhandenes Inhaltsfragment {#example-accessing-an-existing-content-fragment}

Dazu können Sie die Ressource, die für die API steht, wie folgt anpassen:

`com.adobe.cq.dam.cfm.ContentFragment`

Beispiel:

```java
// first, get the resource
Resource fragmentResource = resourceResolver.getResource("/content/dam/fragments/my-fragment");
// then adapt it
if (fragmentResource != null) {
    ContentFragment fragment = fragmentResource.adaptTo(ContentFragment.class);
    // the resource is now accessible through the API
}
```

### Beispiel: Erstellen eines neuen Inhaltsfragments     {#example-creating-a-new-content-fragment}

Um ein neues Inhaltsfragment zu programmieren, verwenden Sie eine `FragmentTemplate`, die von einem Modell oder einer Vorlagenressource angepasst wurde.

Beispiel:

```java
Resource templateOrModelRsc = resourceResolver.getResource("...");
FragmentTemplate tpl = templateOrModelRsc.adaptTo(FragmentTemplate.class);
ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
```

### Beispiel: Angeben des Intervalls für das automatische Speichern     {#example-specifying-the-auto-save-interval}

Das [Intervall für das automatische Speichern](/help/assets/content-fragments/content-fragments-managing.md#save-cancel-and-versions) (gemessen in Sekunden) kann mit dem Konfigurations-Manager (ConfMgr) definiert werden:

* Knoten: `<conf-root>/settings/dam/cfm/jcr:content`
* Eigenschaftsname: `autoSaveInterval`
* Typ: `Long`

* Standard: `600` (10 Minuten); wird definiert in `/libs/settings/dam/cfm/jcr:content`

Wenn Sie ein Intervall von 5 Minuten für das automatische Speichern festlegen möchten, müssen Sie die Eigenschaft auf dem Knoten definieren. Beispiel:

* Knoten: `/conf/global/settings/dam/cfm/jcr:content`
* Eigenschaftsname: `autoSaveInterval`

* Typ: `Long`

* Wert: `300` (5 Minuten entsprechen 300 Sekunden)

## Komponenten für die Seitenbearbeitung {#components-for-page-authoring}

Weitere Informationen finden Sie unter

* [Kernkomponenten – Inhaltsfragmentkomponente](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/content-fragment-component.html) (empfohlen)
