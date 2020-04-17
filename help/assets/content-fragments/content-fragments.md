---
title: 'Arbeiten mit Inhaltsfragmenten '
description: Erfahren Sie, wie Sie mit Inhaltsfragmenten seitenunabhängige Inhalte entwerfen, erstellen, kuratieren und verwenden können.
translation-type: ht
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Arbeiten mit Inhaltsfragmenten {#working-with-content-fragments}

Inhaltsfragmente in Adobe Experience Manager (AEM) ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und [Verwenden von seitenunabhängigen Inhalten](/help/sites-cloud/authoring/fundamentals/content-fragments.md). Außerdem können Sie Inhalte zur Verwendung an mehreren Orten/über mehrere Kanäle hinweg vorbereiten. 

Mit der Sling Model (JSON)-Exportfunktion der AEM-Kernkomponenten können Inhaltsfragmente auch im JSON-Format bereitgestellt werden. Diese Form der Bereitstellung:

* bietet Ihnen die Möglichkeit, mithilfe der Komponente zu bestimmen, welche Fragmentelemente bereitgestellt werden sollen
* ermöglicht durch das Hinzufügen mehrerer Inhaltsfragment-Kernkomponenten auf der für die API-Bereitstellung verwendeten Seite eine Bereitstellung in größerem Umfang

Hier und auf den folgenden Seiten werden die Aufgaben zum Erstellen, Konfigurieren und Pflegen von Inhaltsfragmenten beschrieben: 

* [Verwalten von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-managing.md)     – Erstellen Sie Ihre Inhaltsfragmente; anschließend können Sie sie bearbeiten, veröffentlichen und Verweise erstellen
* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md) – Aktivieren, Erstellen und Definieren Ihrer Modelle
* [Varianten – Erstellen von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-variations.md) – Erstellen Sie das Inhaltsfragment und erstellen Sie Varianten der Master-Version
* [Markdown](/help/assets/content-fragments/content-fragments-markdown.md) – Verwendung der Markdown-Syntax für Ihr Fragment
* [Verwenden verknüpfter Inhalte](/help/assets/content-fragments/content-fragments-assoc-content.md) – Hinzufügen verknüpfter Inhalte
* [Metadaten – Fragmenteigenschaften](/help/assets/content-fragments/content-fragments-metadata.md) – Anzeigen und Bearbeiten der Fragmenteigenschaften

>[!NOTE]
>
>Diese Seiten sollten in Verbindung mit dem Thema [Seitenbearbeitung mit Inhaltsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md) gelesen werden. 

Die Anzahl der Kommunikationskanäle nimmt jährlich zu. Typischerweise beziehen sich Kanäle auf den Bereitstellungsmechanismus, und zwar wie folgt:

* Physische Kanäle, z. B. Desktop, Mobilgerät
* Bereitstellung in einem physischen Kanal, z. B. als „Produktdetailseite“ oder „Produktkategorieseite“ für Desktops bzw. als „mobiles Internet“ oder „mobile App“ für mobile Geräte 

Wahrscheinlich möchten Sie jedoch nicht dieselben Inhalte für alle Kanäle verwenden. Daher müssen Sie Ihre Inhalte je nach Kanal optimieren.

Inhaltsfragmente ermöglichen Ihnen Folgendes: 

* Erwägen, wie sich Zielgruppen effizient kanalübergreifend erreichen lassen 
* Kanalneutrale redaktionelle Inhalte erstellen und verwalten 
* Inhaltspools für mehrere Kanäle erstellen 
* Inhaltsvarianten für bestimmte Kanäle entwerfen 
* Bilder durch Einfügen von Assets (Fragmente mit gemischten Medien) zu Texten hinzufügen 

Diese Inhaltsfragmente können dann zusammengestellt werden, um Erlebnisse über verschiedene Kanäle bereitzustellen. 

## Inhaltsfragmente und Content Services   {#content-fragments-and-content-services}

Mit den AEM Content Services können die Beschreibung und Bereitstellung von Inhalten in/über AEM über einen Fokus auf Webseiten hinweg generalisiert werden.

Sie ermöglichen die Bereitstellung von Inhalten in Kanälen, die keine traditionellen AEM-Webseiten sind, und nutzen standardisierte Methoden, die von allen Clients genutzt werden können. Diese Kanäle können Folgendes sein:

* Einzelseiten-Webanwendungen
* native Mobile Apps
* weitere AEM-externe Kanäle und Touchpoints

Die Bereitstellung erfolgt im JSON-Format.

AEM-Inhaltsfragmente können zur Beschreibung und Verwaltung strukturierter Inhalte verwendet werden. Strukturierter Inhalt wird in Modellen definiert, die eine Vielzahl von Inhaltstypen enthalten können, darunter Text, numerische Daten, boolesche Ausdrücke, Datum und Uhrzeit und mehr.

Zusammen mit der JSON-Exportfunktion der AEM-Kernkomponenten kann dieser strukturierte Inhalt dann zur Bereitstellung von AEM-Inhalten auf anderen Kanälen als AEM-Seiten verwendet werden.

>[!NOTE]
>
>**Inhaltsfragmente** und **[Experience Fragments](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)**sind unterschiedliche Funktionen in AEM:
>* **Inhaltsfragmente** sind redaktionelle Inhalte, vor allem Text und zugehörige Bilder. Dabei handelt es sich um reinen Inhalt ohne Design und Layout.
>* **Experience Fragments** sind vollständig gestaltete Inhalte und stellen Teile von Web-Seiten dar.
>
>
Experience Fragments können Inhalte in Form von Inhaltsfragmenten enthalten, aber nicht umgekehrt.
>
>Weitere Details finden Sie in den [Informationen zu Inhaltsfragmenten und Experience Fragments in AEM](https://helpx.adobe.com/de/experience-manager/kt/platform-repository/using/content-fragments-experience-fragments-article-understand.html).

>[!CAUTION]
>
>Inhaltsfragmente stehen über die klassische Benutzeroberfläche nicht zur Verfügung. 
>
>Die Inhaltsfragmente-Komponente kann im Sidekick der klassischen Benutzeroberfläche angezeigt werden. Es stehen jedoch keine weiteren Funktionen zur Verfügung. 

>[!NOTE]
>
>AEM unterstützt auch die Übersetzung von Fragmentinhalten.  Weitere Informationen finden Sie unter „Erstellen von Übersetzungsprojekten für Inhaltsfragmente“.

<!--
>[!NOTE]
>
>AEM also supports the translation of fragment content. See [Creating Translation Projects for Content Fragments](/help/assets/creating-translation-projects-for-content-fragments.md) for further information.
-->

## Arten von Inhaltsfragmenten {#types-of-content-fragment}

Es gibt folgende Arten von Inhaltsfragmenten:

* Einfache Fragmente. Diese haben keine vordefinierte Struktur. Sie enthalten lediglich Text und Bilder.
Diese basieren auf der Vorlage für einfache Fragmente.

* Fragmente, die strukturierte Inhalte enthalten. Diese basieren auf einem [Inhaltsfragmentmodell](/help/assets/content-fragments/content-fragments-models.md), das eine Struktur für das daraus entstehende Fragment vordefiniert.
Diese können außerdem verwendet werden, um Content Services über den JSON Exporter bereitzustellen.

## Inhaltstyp {#content-type}

Inhaltsfragmente werden:

* als **Assets** gespeichert:

   * Inhaltsfragmente (und deren Varianten) können in der Konsole **Assets** erstellt und verwaltet werden.
   * Im Inhaltsfragment-Editor erstellt und bearbeitet.

* im [Seiteneditor anhand der Komponente Inhaltsfragment verwendet](/help/sites-cloud/authoring/fundamentals/content-fragments.md) (Verweiskomponente):

   * Die Komponente **Inhaltsfragment** steht für Seitenautoren zur Verfügung. Sie ermöglicht das Erstellen von Verweisen für sowie das Bereitstellen des erforderlichen Inhaltsfragments im HTML- oder JSON-Format.

Inhaltsfragmente sind eine Inhaltsstruktur mit folgenden Eigenschaften:

* Sie weisen kein Layout oder Design auf (gewisse Textformatierung ist im Rich-Text-Modus möglich).
* Enthalten mindestens einen [Bestandteil](#constituent-parts-of-a-content-fragment).
* Kann Bilder [enthalten oder mit Bildern verbunden sein](#fragments-with-visual-assets).
* Bei Referenzierung auf einer Seite können [Übergangsinhalte](#in-between-content-when-page-authoring-with-content-fragments) verwendet werden. 

* Sie sind unabhängig vom Bereitstellungsmechanismus (d. h. Seite, Kanal).

### Fragmente mit visuellen Assets {#fragments-with-visual-assets}

Um Autoren eine bessere Kontrolle über eigene Inhalte zu ermöglichen, können Bilder zu einem Inhaltsfragment hinzugefügt und/oder darin integriert werden.

Assets können auf verschiedene Weise mit einem Inhaltsfragment verwendet werden – mit jeweiligen Vorteilen: 

* In ein Fragment **eingefügte Assets** (Fragmente mit gemischten Medien)

   * sind ein integraler Bestandteil des Fragments (siehe [Bestandteile von Inhaltsfragmenten](#constituent-parts-of-a-content-fragment)); 
   * definieren die Position des Assets; 
   * Weitere Informationen finden Sie unter [Einfügen von Assets in Fragmente](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) im Fragment-Editor.
   >[!NOTE]
   >
   >Die in das Inhaltsfragment eingefügten visuellen Assets werden mit dem vorangehenden Absatz verbunden. Beim Hinzufügen des Fragments zu einer Seite werden diese Assets in Beziehung zu diesem Absatz verschoben, wenn Übergangsinhalte hinzugefügt werden. 

* **Zugehörige Inhalte**

   * sind zwar mit einem Fragment verbunden, stellen aber keinen festen Bestandteil des Fragments dar (siehe [Bestandteile von Inhaltsfragmenten](#constituent-parts-of-a-content-fragment)); 
   * ermöglichen eine gewisse Flexibilität bei der Positionierung; 
   * sind problemlos verfügbar (als Übergangsinhalte), wenn das Fragment auf einer Seite verwendet wird; 
   * weitere Informationen finden Sie unter [Zugehörige Inhalte](/help/assets/content-fragments/content-fragments-assoc-content.md). 

* Über den **Assets-Browser** des Seiten-Editors verfügbare Assets 

   * bieten vollständige Flexibilität bei der Asset-Auswahl; 
   * ermöglichen eine gewisse Flexibilität bei der Positionierung; 
   * liefern nicht die Möglichkeit, für ein bestimmtes Fragment genehmigt zu werden;
   * weitere Informationen finden Sie unter [Assets-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser). 

### Bestandteile von Inhaltsfragmenten {#constituent-parts-of-a-content-fragment}

Inhaltsfragment-Assets setzen sich aus folgenden Teilen zusammen (entweder direkt oder indirekt): 

* **Fragmentelementen**

   * Elemente korrelieren mit den Datenfeldern, die Inhalte enthalten.
   * Verwenden Sie bei Fragmenten mit strukturiertem Inhalt ein Inhaltsmodell, um das Inhaltsfragment zu erstellen. Die im Modell angegebenen Elemente (Felder) definieren die Struktur des Fragments. Bei diesen Elementen (Feldern) gibt es verschiedene Datentypen.
   * Bei einfachen Fragmenten:

      * Der Inhalt befindet sich in einem (oder mehreren) mehrzeiligen Textfeld(ern) oder Element(en).
      * Die Elemente werden in der Fragmentvorlage definiert (es ist nicht möglich, sie bei der Fragmenterstellung zu definieren; siehe „Inhaltsfragmentvorlagen“). <!--    * The elements are defined in the fragment template (cannot be defined when authoring the fragment, see [Content Fragment Templates](/help/sites-developing/content-fragment-templates.md)). -->

* **Fragmentabsätze**

   * Textblöcke, die:

      * durch vertikale Abstände (Zeilenschaltung) getrennt sind 
      * sich in mehrzeiligen Textelementen befinden, entweder in einfachen oder in strukturierten Fragmenten
   * Im [Rich-Text](/help/assets/content-fragments/content-fragments-variations.md#rich-text)- und [Markdown](/help/assets/content-fragments/content-fragments-variations.md#markdown)-Modus kann ein Absatz als Kopfzeile formatiert sein, wobei dieser sowie der nachfolgende Absatz als eine Einheit fungieren.

   * Ermöglichen die Inhaltssteuerung während der Seitenbearbeitung  


* **In ein Fragment eingefügte Assets (Fragmente mit gemischten Medien)** 

   * Assets (Bilder), die in das eigentliche Fragment eingefügt und als interne Inhalte eines Fragments verwendet werden;
   * sind in das Absatzsystem des Fragments eingebettet; 
   * können formatiert werden, wenn das [Fragment auf einer Seite verwendet/referenziert wird](/help/sites-cloud/authoring/fundamentals/content-fragments.md); 
   * können nur über den Fragment-Editor einem Fragment hinzugefügt, daraus gelöscht oder darin verschoben werden;  diese Aktionen können nicht im Seiten-Editor durchgeführt werden; 
   * können nur durch das [Rich-Text-Format im Fragment-Editor](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) einem Fragment hinzugefügt, daraus gelöscht oder darin verschoben werden; 
   * können nur zu mehrzeiligen Textelementen hinzugefügt werden (beliebiger Fragmenttyp);
   * werden mit dem vorangehenden Text (Absatz) verbunden; 
   >[!CAUTION]
   >
   >Ein (versehentliches) Löschen aus dem Fragment ist möglich, wenn in das Nur-Text-Format gewechselt wird. 

   >[!NOTE]
   >
   >Assets können auch als [zusätzlicher (Übergangs) Inhalt](/help/sites-cloud/authoring/fundamentals/content-fragments.md#using-associated-content) hinzugefügt werden, wenn ein Fragment auf einer Seite verwendet wird (bei Nutzung von zugehörigen Inhalten oder Assets aus dem Assets-Browser). 

* **Zugehörige Inhalte**

   * Hierbei handelt es sich um externen Inhalt für das Fragment, der jedoch von redaktioneller Relevanz ist. In der Regel sind dies Bilder, Videos oder andere Fragmente.
   * Die einzelnen Assets innerhalb der Sammlung können mit dem Fragment im Seiten-Editor verwendet werden, wenn es einer Seite hinzugefügt wird.  Zugehörige Inhalte sind also optional, abhängig von den Anforderungen des jeweiligen Kanals. 
   * Die Assets sind [mit Fragmenten über Sammlungen verknüpft](/help/assets/content-fragments/content-fragments-assoc-content.md). Mithilfe verknüpfter Sammlungen kann der Autor entscheiden, welche Assets beim Bearbeiten einer Seite verwendet werden sollen.

      * Sammlungen können mit Fragmenten anhand von Vorlagen als Standardinhalt oder von Autoren während der Fragmentbearbeitung verbunden werden.
      * [Asset (DAM)-Sammlungen](/help/assets/manage-collections.md) sind die Basis für die zugehörigen Inhalte von Fragmenten. 
   * Sie können auch das eigentliche Fragment zu einer Sammlung hinzufügen und so die Nachverfolgung unterstützen. 

* **Fragmentmetadaten**

   * Verwendung der [Assets-Metadatenschemata](/help/assets/metadata-schemas.md)
   * Tag-Erstellung möglich: 

      * Beim Erstellen und Bearbeiten des Fragments 
      * Oder später: 

         * Durch Anzeigen/Bearbeiten der **Fragmenteigenschaften** über die Konsole
         * Durch Bearbeiten der **Metadaten** im Fragment-Editor 
   >[!CAUTION]
   >
   >Profile für die Metadatenverarbeitung sind nicht für Inhaltsfragmente geeignet.

* **Master**

   * Integraler Bestandteil des Fragments: 

      * Jedes Inhaltsfragment hat eine Masterinstanz.
      * Der Master kann gelöscht werden. 
   * Auf den Master kann über den Fragment-Editor unter **[Varianten](/help/assets/content-fragments/content-fragments-variations.md)**zugegriffen werden.
   * Der Master ist keine Variante an sich, sondern die Grundlage aller Varianten.


* **Varianten**

   * Ausgabeformate von Fragmenttext, eigens zu redaktionellen Zwecken. Diese können mit einem Kanal verbunden sein, doch ist dies nicht obligatorisch; auch für lokale Ad-hoc-Änderungen geeignet;
   * werden als Kopien vom **Master** erstellt, können dann aber nach Bedarf bearbeitet werden; gewöhnlich kommt es zu einer Inhaltsüberlappung zwischen den Varianten;
   * können während der Fragmentbearbeitung definiert oder in Fragment-Vorlagen vordefiniert werden;
   * werden im Fragment gespeichert, um die Streuung von Inhaltskopien zu vermeiden;
   * können mit dem Master [synchronisiert](/help/assets/content-fragments/content-fragments-variations.md#synchronizing-with-master) werden, wenn der Masterinhalt aktualisiert wurde; 
   * können [zusammengefasst](/help/assets/content-fragments/content-fragments-variations.md#summarizing-text) werden, um Text schnell auf eine vordefinierte Länge zu kürzen;
   * sind auf der Registerkarte [Varianten](/help/assets/content-fragments/content-fragments-variations.md) des Fragment-Editors verfügbar.

### Übergangsinhalte bei der Seitenerstellung mit Inhaltsfragmenten {#in-between-content-when-page-authoring-with-content-fragments}

Übergangsinhalte:

* Sind für die Verwendung im Seiteneditor bei der Arbeit mit Inhaltsfragmenten verfügbar.
* Hierbei handelt es sich um [zusätzlichen Inhalt, der im Fluss eines Fragments hinzugefügt wird](/help/sites-cloud/authoring/fundamentals/content-fragments.md#adding-in-between-content), sobald dieses auf einer Seite verwendet/referenziert wird.
* Sind für die Verwendung im [Seiteneditor bei der Arbeit mit Inhaltsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md) verfügbar.
* Übergangsinhalte können zu jedem beliebigen Fragment hinzugefügt werden, in dem nur ein Element sichtbar ist.
* Zugehörige Inhalte sowie Assets und/oder Komponenten des entsprechenden Browsers können eingesetzt werden. 

>[!CAUTION]
>
>Bei Übergangsinhalten handelt es sich um Seiteninhalte. Sie werden nicht im Inhaltsfragment gespeichert.

### Voraussetzungen für Fragmente {#required-by-fragments}

Zum Erstellen, Bearbeiten und Verwenden von Inhaltsfragmenten ist zudem Folgendes erforderlich: 

* **Inhaltsmodell**

   * Wird [mithilfe von Tools aktiviert und erstellt](/help/assets/content-fragments/content-fragments-models.md).
   * Erforderlich für das [Erstellen eines strukturierten Fragments](/help/assets/content-fragments/content-fragments-managing.md#creating-content-fragments).
   * Definiert die Struktur eines Fragments (Titel, Inhaltselemente, Tag-Definitionen).
   * Inhaltsmodelldefinitionen erfordern einen Titel und ein Datenelement. Alle weiteren Elemente sind optional. Das Modell definiert einen minimalen Gültigkeitsbereich für das Fragment und ggf. den Standardinhalt. Autoren können die definierte Struktur ändern, wenn sie den Fragmentinhalt erstellen.

* **Fragmentvorlage**

   * Erforderlich für das [Erstellen eines einfachen Fragments](/help/assets/content-fragments/content-fragments-managing.md#creating-content-fragments).
   * In der Regel während der Projektimplementierung entwickelt; kann nicht während des Erstellens entwickelt werden.<!--  * Usually [developed during project implementation](/help/sites-developing/content-fragment-templates.md); cannot be created when authoring. -->
   * Definiert die grundlegenden Eigenschaften eines einfachen Fragments (Titel, Anzahl der Textelemente, Tag-Definitionen).
   * Vorlagendefinitionen erfordern einen Titel und ein Textelement. Alle weiteren Elemente sind optional. Die Vorlage definiert einen minimalen Gültigkeitsbereich für das Fragment und ggf. den Standardinhalt. Autoren können zu einem späteren Zeitpunkt die Definition eines Fragments über die Angaben in der Vorlage hinaus erweitern.

* **Inhaltsfragment-Komponente**

   * Hilft bei der Bereitstellung des Fragments im HTML- und/oder JSON-Format.
   * Erforderlich zum [Referenzieren des Fragments auf einer Seite](/help/sites-cloud/authoring/fundamentals/content-fragments.md). 
   * Zuständig für das Layout und die Bereitstellung eines Fragments, d. h. Kanäle.
   * Fragmente benötigen eine oder mehrere dedizierte Komponenten zur Definition des Layouts sowie zur Bereitstellung einiger oder aller Elemente/Varianten und zugehörigen Inhalte.
   * Durch Ziehen eines Fragments auf eine Seite während der Bearbeitung wird die erforderliche Komponente automatisch zugewiesen.

## Anwendungsbeispiel    {#example-usage}

Ein Fragment samt seinen Elementen und Varianten kann zur Erstellung von kohärentem Inhalt für verschiedene Kanäle verwendet werden. Beim Entwurf eines Fragments muss berücksichtigt werden, welche Elemente wo verwendet werden.

### WKND-Beispiel {#wknd-sample}

Die Beispiele der [WKND Site](/help/implementing/developing/introduction/develop-wknd-tutorial.md) helfen Ihnen dabei, mehr über AEM as a Cloud Service zu erfahren. Darin sind Musterfragmente enthalten, die Sie unter folgender Adresse sehen können:

`hhttp://<host>:<port>/assets.html/content/dam/wknd/en/adventures`
