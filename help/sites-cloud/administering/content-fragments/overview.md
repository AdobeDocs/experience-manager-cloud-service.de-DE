---
title: Ein Überblick über das Arbeiten mit Inhaltsfragmenten
description: Erfahren Sie, wie Sie mit Inhaltsfragmenten in Adobe Experience Manager (AEM) as a Cloud Service strukturierte Inhalte erstellen und verwenden können – ideal für Headless-Bereitstellung und Seitenerstellung.
feature: Content Fragments
role: User, Developer, Architect
exl-id: ce9cb811-57d2-4a57-a360-f56e07df1b1a
solution: Experience Manager Sites
source-git-commit: 86a2c5f35d82010c84b74b6b5f0da09fd87c2b7a
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 100%

---

# Ein Überblick über das Arbeiten mit Inhaltsfragmenten {#overview-working-with-content-fragments}

In Adobe Experience Manager (AEM) as a Cloud Service können Sie mit Inhaltsfragmenten seitenunabhängige Inhalte entwerfen, erstellen, kuratieren und veröffentlichen. Sie ermöglichen es Ihnen, Inhalte so vorzubereiten, dass sie an mehreren Orten und über mehrere Kanäle verwendet werden können, ideal für die [Headless-Bereitstellung](/help/headless/what-is-headless.md) und die [Seitenerstellung](/help/sites-cloud/authoring/fragments/content-fragments.md).

>[!IMPORTANT]
>
>Auf Inhaltsfragmente können Sie über zwei Konsolen zugreifen: **Inhaltsfragmente** und **Assets**.
>
>Es gibt auch zwei Editoren für die Erstellung von Inhaltsfragmenten. Auch wenn die grundlegende Funktionalität gleich ist, gibt es einige Unterschiede. Auf beide Editoren kann von beiden Konsolen aus zugegriffen werden.
>
>Dieser Abschnitt befasst sich mit der **Inhaltsfragmentekonsole** und dem *neuen* Inhaltsfragmenteditor. Diese wurden für die Bereitstellung von Headless-Inhalten entwickelt (obwohl sie für alle Szenarien verwendet werden können)
>
>Weitere Informationen finden Sie unter:
>
>* Verwendung der **Assets**-Konsole für die [Verwaltung von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-managing.md),
>* Verwendung des [*originalen* Inhaltsfragmenteditors](/help/assets/content-fragments/content-fragments-variations.md),
>* Verwendung von [Inhaltsfragmenten für die Seitenerstellung](/help/sites-cloud/authoring/fragments/content-fragments.md).


Inhaltsfragmente enthalten strukturierte Inhalte:

* Jedes Fragment basiert auf einem [Inhaltsfragmentmodell](/help/sites-cloud/administering/content-fragments/content-fragment-models.md).
   * Das Inhaltsfragmentmodell definiert die Struktur des resultierenden Fragments.
* Jedes Fragment besteht aus:
   * **[Hauptteil](#main-and-variations)**: Ein integraler Bestandteil des Fragments, der den Kerninhalt enthält; immer vorhanden, kann nicht gelöscht werden
   * **[Varianten](#main-and-variations)**: Eine oder mehrere von der Autorin bzw. vom Autor erstellte Permutationen des Inhalts
* Die Struktur kann variieren:
   * Einfach
      * Beispiel: ein einzelnes, mehrzeiliges Textfeld.
      * Kann verwendet werden, um einfache Inhalte für die Verwendung bei der Seitenerstellung vorzubereiten.
      * Kann auch für die Headless-Bereitstellung an Ihre Anwendung verwendet werden.
   * Komplex
      * Eine Kombination aus vielen Feldern mit unterschiedlichen Datentypen, darunter Text, Zahlen, boolesche Werte, Datum und Uhrzeit, um nur einige zu nennen.
      * Kann entweder zur Vorbereitung von strukturierteren Inhalten für die Seitenerstellung oder zur Headless-Bereitstellung für Ihr Programm verwendet werden.
   * Verschachtelt
      * Mit den verfügbaren Referenzdatentypen können Sie Ihre Inhalte verschachteln.
      * Wird in der Regel für die Headless-Bereitstellung an Ihre Anwendung verwendet.

Mit der Sling Model (JSON)-Exportfunktion der AEM-Kernkomponenten können Inhaltsfragmente auch im JSON-Format bereitgestellt werden. Diese Form der Bereitstellung:

* bietet Ihnen die Möglichkeit, mithilfe der Komponente zu bestimmen, welche Fragmentelemente bereitgestellt werden sollen
* ermöglicht durch das Hinzufügen mehrerer [Inhaltsfragment-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=de) auf der für die API-Bereitstellung verwendeten Seite eine Bereitstellung in größerem Umfang

Die Anzahl der Kommunikationskanäle nimmt jährlich zu. Typischerweise beziehen sich Kanäle auf den Bereitstellungsmechanismus, und zwar wie folgt:

* Physischer Kanal; z. B. Desktop, Mobilgerät.
* Form der Bereitstellung in einem physischen Kanal; z. B. die Produktdetailseite, die Produktkategorieseite für Desktops oder „mobiles Web“, „Mobile App“ für Mobilgeräte.

Sie möchten jedoch (wahrscheinlich) nicht den *exakt* gleichen Inhalt für alle Kanäle verwenden – Sie müssen Ihre Inhalte entsprechend dem jeweiligen Kanal optimieren.

Inhaltsfragmente ermöglichen Ihnen Folgendes:

* Erwägen, wie sich Zielgruppen effizient kanalübergreifend erreichen lassen.
* Kanalneutrale redaktionelle Inhalte erstellen und verwalten.
* Inhaltspools für mehrere Kanäle erstellen.
* Inhaltsvarianten für bestimmte Kanäle entwerfen.
* Hinzufügen von Bildern durch Einfügen von Assets zu Texten.
* Erstellen Sie verschachtelte Inhalte, um die Komplexität Ihrer Daten widerzuspiegeln.

Diese Inhaltsfragmente können dann zusammengestellt werden, um Erlebnisse über verschiedene Kanäle bereitzustellen.

>[!NOTE]
>
>**Inhaltsfragmente** und **[Experience Fragments](/help/sites-cloud/authoring/fragments/content-fragments.md)** sind unterschiedliche Funktionen in AEM:
>* **Inhaltsfragmente** sind redaktionelle Inhalte mit Definition und Struktur, aber ohne zusätzliches visuelles Design und/oder Layout. Sie können unter anderem für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Datumsangaben verwendet werden.
>* **Experience Fragments** sind vollständig gestaltete Inhalte und stellen Teile von Web-Seiten dar.
>
>Experience Fragments können Inhalte in Form von Inhaltsfragmenten enthalten, aber nicht umgekehrt.
>
>Weitere Details finden Sie unter [Informationen zu Inhaltsfragmenten und Experience Fragments in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=de#content-fragments).

Hier und auf den folgenden Seiten werden die Aufgaben zum Erstellen, Konfigurieren, Verwalten und Verwenden von Inhaltsfragmenten beschrieben:

* [Aktivieren der Funktionen für Inhaltsfragmente für Ihre Instanz](/help/sites-cloud/administering/content-fragments/setup.md)
* [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/content-fragment-models.md): Aktivieren, Erstellen und Definieren Ihrer Modelle
* [Erstellen von Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment) (mithilfe der Inhaltsfragmentkonsole)

Nachdem das Fragment erstellt wurde, können Sie Folgendes tun:

* [Verwenden der Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/managing.md): Um auf Ihre Fragmente zuzugreifen, sie zu veröffentlichen (als Vorschau oder in der Produktion) und auf sie zu verweisen
* [Verwenden des Inhaltsfragmenteditors](/help/sites-cloud/administering/content-fragments/authoring.md): Um Ihre Fragmente zu bearbeiten, sie zu veröffentlichen (als Vorschau oder in der Produktion) und auf sie zu verweisen
* [Analysieren](/help/sites-cloud/administering/content-fragments/analysis.md) der Struktur Ihres Inhaltsfragments mithilfe des Editors
* [Zugreifen auf Ihre Fragmente mit GraphQL, für eine Headless-Bereitstellung an Ihre Anwendungen](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md).
* [Oder Verwenden Ihrer Fragmente für die Seitenerstellung](/help/sites-cloud/authoring/fragments/content-fragments.md)

>[!NOTE]
>
>Diese Seiten können eusammen mit Folgendem gelesen werden:
>
>* [Anpassen und Erweitern von Inhaltsfragmenten](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [Inhaltsfragmente, die Komponenten für die Wiedergabe konfigurieren](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md)
>* [Seitenbearbeitung mit Inhaltsfragmenten](/help/sites-cloud/authoring/fragments/content-fragments.md).
>* Die [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md) sind ebenfalls verfügbar.


## Hauptteil und Varianten {#main-and-variations}

Varianten sind eine wichtige Funktion von AEM-Inhaltsfragmenten. Sie können damit Kopien des **Haupt-Inhalts** erstellen und bearbeiten, um sie in bestimmten Kanälen und Szenarien zu verwenden. Dadurch wird die Bereitstellung von Headless-Inhalten und die Seitenbearbeitung noch flexibler.

* **Allgemein**

   * Der **Hauptteil** ist keine Variante an sich, sondern die Grundlage aller Varianten.
   * Integraler Bestandteil des Fragments:

      * Jedes Inhaltsfragment hat eine **Hauptteil**-Instanz.
      * Der **Hauptteil** kann nicht gelöscht werden.

   * Der **Hauptteil** ist im Fragmenteditor unter **[Varianten](/help/sites-cloud/administering/content-fragments/authoring.md#variations)** zugänglich.

  >[!NOTE]
  >
  >Im Editor, der über die **Assets**-Konsole verfügbar ist, ist der **Hauptteil** als **Primär** gekennzeichnet.

* **Varianten**

   * Ausgabedarstellungen von Fragmenttext, eigens zu redaktionellen Zwecken. Diese können mit einem Kanal verbunden sein, doch ist dies nicht obligatorisch; auch für lokale Ad-hoc-Änderungen geeignet;
   * Werden als Kopien des **Hauptteils** erstellt, können dann aber nach Bedarf bearbeitet werden, wobei es oft inhaltliche Überschneidungen zwischen den Varianten selbst gibt.
   * Können während der Erstellung von Fragmenten über das linke Bedienfeld definiert werden.
   * Werden im Fragment gespeichert, um zu vermeiden, dass Inhaltskopien verstreut werden.
   * Varianten können mit dem **Hauptteil** [verglichen und synchronisiert](/help/sites-cloud/administering/content-fragments/authoring.md#compare-and-synchronize-rich-text) werden.
  <!--
  * Can be [Summarized](/help/sites-cloud/administering/content-fragments/authoring.md#summarizing-text) to quickly truncate the text to a predefined length.
  -->

## Inhaltsfragmente und Content Services {#content-fragments-and-content-services}

Mit den AEM Content Services können die Beschreibung und Bereitstellung von Inhalten in/über AEM über einen Fokus auf Web-Seiten hinweg generalisiert werden.

Sie ermöglichen die Bereitstellung von Inhalten in Kanälen, die keine traditionellen AEM-Web-Seiten sind, und nutzen standardisierte Methoden, die von allen Clients genutzt werden können. Diese Kanäle können Folgendes sein:

* Single Page Applications (SPA)
* native Mobile Apps
* weitere AEM-externe Kanäle und Touchpoints

Der Versand erfolgt im JSON-Format mit dem JSON-Exporter.

AEM-Inhaltsfragmente können zur Beschreibung und Verwaltung strukturierter Inhalte verwendet werden. Strukturierter Inhalt wird in Modellen definiert, die eine Vielzahl von Inhaltstypen enthalten können, darunter Text, numerische Daten, boolesche Ausdrücke, Datum und Uhrzeit und mehr.

Zusammen mit der JSON-Exportfunktion der AEM-Kernkomponenten kann dieser strukturierte Inhalt dann zur Bereitstellung von AEM-Inhalten auf anderen Kanälen als AEM-Seiten verwendet werden.

>[!NOTE]
>
>Eine Einführung in die Headless-Entwicklung für AEM Sites as a Cloud Service finden Sie unter [Headless und AEM](/help/headless/introduction.md).

>[!NOTE]
>
>AEM unterstützt auch die Übersetzung von Fragmentinhalten. Weitere Informationen finden Sie unter [Übersetzen von Assets](/help/assets/translate-assets.md).

## Inhaltstyp {#content-type}

Inhaltsfragmente werden:

* eine **Sites**-Funktion.

* als **Assets** gespeichert:

   * Inhaltsfragmente (und deren Varianten) können in der [Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) erstellt und verwaltet werden.
   * Erstellt und bearbeitet im [Inhaltsfragmenteditor](/help/sites-cloud/administering/content-fragments/authoring.md).

* Zugänglich für die Bereitstellung von Inhalten über die [AEM GraphQL-API](/help/headless/graphql-api/content-fragments.md).

* Verfügbar im [Seiteneditor unter Verwendung der Inhaltsfragmentkomponente](/help/sites-cloud/authoring/fragments/content-fragments.md) (Verweiskomponente):

   * Die [Inhaltsfragment-Kernkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=de) steht für Autorinnen und Autoren der Seite zur Verfügung. Sie ermöglicht das Erstellen von Verweisen für sowie das Bereitstellen des erforderlichen Inhaltsfragments im HTML- oder JSON-Format.

Inhaltsfragmente sind eine Inhaltsstruktur mit folgenden Eigenschaften:

* Sie weisen kein Layout oder Design auf (Textformatierung ist in Textfeldern möglich).
* Sie sind unabhängig vom Bereitstellungsmechanismus (z. B. Seite oder Kanal).
* Enthalten mindestens einen [Bestandteil](#constituent-parts-of-a-content-fragment).
* Kann Bilder [enthalten oder mit Bildern verbunden sein](#fragments-with-visual-assets).

### Fragmente mit visuellen Assets {#fragments-with-visual-assets}

Um Autorinnen und Autoren eine bessere Kontrolle über eigene Inhalte zu ermöglichen, können zu einem Inhaltsfragment Bilder hinzugefügt und/oder darin integriert werden.

Assets können auf verschiedene Weise mit einem Inhaltsfragment verwendet werden, mit jeweiligen Vorteilen:

* als **Inhaltsverweis**
* innerhalb eines **mehrzeiligen Textfelds**

### Bestandteile von Inhaltsfragmenten {#constituent-parts-of-a-content-fragment}

Inhaltsfragment-Assets setzen sich aus folgenden Teilen zusammen (entweder direkt oder indirekt):

* **Fragmentelementen**

   * Elemente korrelieren mit den Datenfeldern, die Inhalte enthalten.
   * Verwenden Sie ein [Inhaltsfragmentmodell](/help/sites-cloud/administering/content-fragments/content-fragment-models.md), um das Inhaltsfragment zu erstellen. Die im Modell angegebenen Elemente (Felder) definieren die Struktur des Fragments. Bei diesen Elementen (Feldern) gibt es verschiedene Datentypen.

* **Fragmentabsätze**

   * Textblöcke, häufig mehrzeilig, die als einzelne Entitäten getrennt sind.

   * Aktivieren Sie die Inhaltskontrolle während der Seitenerstellung.

* **Fragmentmetadaten**

   * Verwendung der [Assets-Metadatenschemata](/help/assets/metadata-schemas.md).
   * Tag-Erstellung möglich:

      * Beim Erstellen und Bearbeiten des Fragments
      * Oder später, wenn Sie im Fragmenteditor [die Eigenschaften anzeigen oder bearbeiten](/help/sites-cloud/administering/content-fragments/authoring.md#view-properties-tags)

  >[!CAUTION]
  >
  >Profile für die Metadatenverarbeitung sind nicht für Inhaltsfragmente geeignet.

  >[!CAUTION]
  >
  >In einem Inhaltsfragmentmodell werden häufig Datenfelder mit den Namen **Titel** und **Beschreibung** definiert. Wenn diese beiden Felder vorhanden sind, handelt es sich um benutzerdefinierte Felder, die im Inhaltsbereich des Editors aktualisiert werden können.
  >
  >Das Inhaltsfragment und seine Variationen verfügen auch über Metadatenfelder (Eigenschaftsfelder) namens **Titel** und **Beschreibung**. Diese beiden Metadatenfelder sind integraler Bestandteil jedes Inhaltsfragments und jeder Variation und werden bei der Erstellung des Fragments definiert. Sie können im Bereich „Eigenschaften/Metadaten“ des Editors aktualisiert werden.

* **[Allgemein](#main-and-variations)**
* **[Varianten](#main-and-variations)**

### Voraussetzungen für Fragmente {#required-by-fragments}

Um Inhaltsfragmente zu erstellen, benötigen Sie:

* **Inhaltsmodelle**

   * Werden [mithilfe des Konfigurations-Browsers aktiviert](/help/sites-cloud/administering/content-fragments/setup.md).
   * Werden [mithilfe von Tools erstellt](/help/sites-cloud/administering/content-fragments/content-fragment-models.md).
   * Erforderlich zum [Erstellen eines Fragments](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments).
   * Definiert die Struktur eines Fragments (Titel, Inhaltselemente, Tag-Definitionen).
   * Definitionen von Inhaltsfragmentmodellen erfordern einen Titel und ein Datenelement. Alle weiteren Elemente sind optional.
   * Das Modell kann Standardinhalte definieren, sofern anwendbar.
   * Autorinnen und Autoren können die definierte Struktur beim Bearbeiten von Fragmentinhalten nicht ändern. Sie können jedoch den Modelleditor über den Fragmenteditor öffnen.
   * Änderungen, die nach dem Erstellen von abhängigen Inhaltsfragmenten an einem Modell vorgenommen wurden, können sich auf diese Inhaltsfragmente auswirken.

Um Ihre Inhaltsfragmente für die Bereitstellung von Headless-Inhalten zu verwenden, benötigen Sie außerdem:

* Eine [GraphQL-Abfrage](/help/headless/graphql-api/content-fragments.md) zur Abfrage des gewünschten Inhalts
* Diese Inhalte können dann zur Entwicklung Ihrer eigenen SPA für AEM verwendet werden. Weitere Informationen finden Sie in den folgenden Dokumenten:

   * [SPA-WKND-Tutorial](/help/implementing/developing/hybrid/wknd-tutorial.md)
   * [Erste Schritte mit React](/help/implementing/developing/hybrid/getting-started-react.md)
   * [Erste Schritte mit Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Um Ihre Inhaltsfragmente zum Erstellen von Seiten zu verwenden, benötigen Sie außerdem Folgendes:

* Eine **Inhaltsfragmentkomponente**

   * Hilft bei der Bereitstellung des Fragments im HTML- und/oder JSON-Format.
   * Erforderlich zum [Referenzieren des Fragments auf einer Seite](/help/sites-cloud/authoring/fragments/content-fragments.md).
   * Zuständig für das Layout und die Bereitstellung eines Fragments, z. B. Kanäle.
   * Fragmente benötigen eine oder mehrere dedizierte Komponenten zur Definition des Layouts sowie zur Bereitstellung einiger oder aller Elemente/Varianten und zugehörigen Inhalte.
   * Durch Ziehen eines Fragments auf eine Seite während der Bearbeitung wird die erforderliche Komponente automatisch zugewiesen.
   * Siehe [Inhaltsfragment-Kernkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=de).

## Anwendungsbeispiel {#example-usage}

Ein Fragment samt seinen Elementen und Varianten kann zur Erstellung von kohärentem Inhalt für verschiedene Kanäle verwendet werden. Beim Entwurf eines Fragments muss berücksichtigt werden, welche Elemente wo verwendet werden.

### WKND-Beispiel {#wknd-sample}

Die Beispiele der [WKND-Site und WKND Shared](/help/implementing/developing/introduction/develop-wknd-tutorial.md) helfen Ihnen dabei, mehr über AEM as a Cloud Service zu erfahren.

<!-- CHECK: which links can/should be used these days? -->

Das WKND-Projekt umfasst:

* Inhaltsfragmentmodelle verfügbar unter:

   * `.../libs/dam/cfm/models/console/content/models.html/conf/wknd`

   * `.../ui#/aem/libs/dam/cfm/models/console/content/models.html/conf/wknd-shared`

* Inhaltsfragmente (und anderere Inhalte) verfügbar unter:

   * `.../assets.html/content/dam/wknd/en`
