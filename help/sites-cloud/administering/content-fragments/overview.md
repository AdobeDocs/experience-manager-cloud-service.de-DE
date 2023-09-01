---
title: Eine Übersicht über die Arbeit mit Inhaltsfragmenten
description: Erfahren Sie, wie Sie mit Inhaltsfragmenten in Adobe Experience Manager (AEM) as a Cloud Service Seiteninhalte entwerfen, erstellen, kuratieren und verwenden können, die seitenunabhängig sind und sich ideal für Headless-Bereitstellung und Seitenbearbeitung eignen.
feature: Content Fragments
role: User, Developer, Architect
source-git-commit: 3d20f4bca566edcdb5f13eab581c33b7f3cf286d
workflow-type: tm+mt
source-wordcount: '1823'
ht-degree: 40%

---


# Eine Übersicht über die Arbeit mit Inhaltsfragmenten {#overview-working-with-content-fragments}

Mit Adobe Experience Manager (AEM) as a Cloud Service können Sie Inhaltsfragmente entwerfen, erstellen, kuratieren und [seitenunabhängige Inhalte veröffentlichen](/help/sites-cloud/authoring/fundamentals/content-fragments.md). Sie ermöglichen es Ihnen, Inhalte für die Verwendung an mehreren Orten und über mehrere Kanäle hinweg vorzubereiten, die sich ideal für die Headless-Bereitstellung und die Seitenbearbeitung eignen.

>[!IMPORTANT]
>
>Der Zugriff auf Inhaltsfragmente erfolgt über zwei Konsolen: **Inhaltsfragmente** und **Assets**.
>
>Es stehen auch zwei Editoren für Inhaltsfragmente zur Verfügung. (Auf beide Editoren kann von beiden Konsolen aus zugegriffen werden.)
>
>In diesem Abschnitt werden die **Inhaltsfragmente** und *new* Inhaltsfragment-Editor. Diese wurden für die Headless-Content-Bereitstellung entwickelt (obwohl sie für alle Szenarien verwendet werden können).
>
>Weitere Informationen finden Sie unter:
>
>* Verwendung der **Assets** Konsole für [Verwalten von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-managing.md)
>* Verwendung der [*original* Inhaltsfragmente-Editor](/help/assets/content-fragments/content-fragments-variations.md),
>* using [Inhaltsfragmente für die Seitenbearbeitung](/help/sites-cloud/authoring/fundamentals/content-fragments.md).


Inhaltsfragmente enthalten strukturierten Inhalt:

* Jedes Fragment basiert auf einer [Inhaltsfragmentmodell](/help/sites-cloud/administering/content-fragments/content-fragment-models.md).
   * Das Inhaltsfragmentmodell definiert die Struktur des resultierenden Fragments.
* Jedes Fragment besteht aus:
   * **[Main](#main-and-variations)** - ein integraler Bestandteil des Fragments, das den Kerninhalt enthält; immer vorhanden, kann nicht gelöscht werden
   * **[Varianten](#main-and-variations)** - eine oder mehrere vom Autor erstellte Permutationen des Inhalts
* Die Struktur kann variieren:
   * Einfach
      * Beispiel: ein einzelnes, mehrzeiliges Textfeld.
      * Kann verwendet werden, um einfache Inhalte für die Verwendung bei der Seitenerstellung vorzubereiten.
      * Kann auch für Headless-Sendungen an Ihre Anwendung verwendet werden.
   * Komplex
      * Eine Kombination aus vielen Feldern unterschiedlicher Datentypen, darunter Text, Zahl, boolescher Wert sowie Datum und Uhrzeit.
      * Kann entweder zur Vorbereitung strukturierterer Inhalte für die Seitenbearbeitung oder zur Headless-Bereitstellung an Ihre Anwendung verwendet werden.
   * Verschachtelt
      * Mit den verfügbaren Referenzdatentypen können Sie Ihre Inhalte verschachteln.
      * Wird für Headless-Versand an Ihre Anwendung verwendet.

Inhaltsfragmente können auch im JSON-Format bereitgestellt werden, indem die Sling Model (JSON)-Exportfunktionen AEM Kernkomponenten verwendet werden. Diese Form der Bereitstellung:

* bietet Ihnen die Möglichkeit, mithilfe der Komponente zu bestimmen, welche Fragmentelemente bereitgestellt werden sollen
* Ermöglicht die Massenbereitstellung durch Hinzufügen mehrerer [Inhaltsfragment-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=de) auf der für die API-Bereitstellung verwendeten Seite

Die Anzahl der Kommunikationskanäle nimmt jährlich zu. Typischerweise beziehen sich Kanäle auf den Bereitstellungsmechanismus, und zwar wie folgt:

* Physischer Kanal; z. B. Desktop, Mobilgerät.
* Form der Bereitstellung in einem physischen Kanal; z. B. die Produktdetailseite, die Produktkategorieseite für Desktops oder „mobiles Web“, „Mobile App“ für Mobilgeräte.

Sie (wahrscheinlich) möchten jedoch nicht die *exact* denselben Inhalt für alle Kanäle - Sie müssen Ihren Inhalt entsprechend dem jeweiligen Kanal optimieren.

Inhaltsfragmente ermöglichen Ihnen Folgendes:

* Erwägen, wie sich Zielgruppen effizient kanalübergreifend erreichen lassen
* Kanalneutrale redaktionelle Inhalte erstellen und verwalten
* Inhaltspools für mehrere Kanäle erstellen
* Inhaltsvarianten für bestimmte Kanäle entwerfen
* Fügen Sie Ihrem Text Bilder hinzu, indem Sie Assets einfügen.
* Erstellen Sie verschachtelte Inhalte, um die Komplexität Ihrer Daten widerzuspiegeln.

Diese Inhaltsfragmente können dann zusammengestellt werden, um Erlebnisse über verschiedene Kanäle bereitzustellen.

>[!NOTE]
>
>**Inhaltsfragmente** und **[Experience Fragments](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)** sind unterschiedliche Funktionen in AEM:
>* **Inhaltsfragmente** sind redaktionelle Inhalte mit Definition und Struktur, aber ohne zusätzliches visuelles Design und/oder Layout. Sie können für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden.
>* **Experience Fragments** sind vollständig gestaltete Inhalte und stellen Teile von Web-Seiten dar.
>
>Experience Fragments können Inhalte in Form von Inhaltsfragmenten enthalten, aber nicht umgekehrt.
>
>Weitere Informationen finden Sie unter [Grundlagen zu Inhaltsfragmenten und Experience Fragments in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=de#content-fragments).

Diese und die folgenden Seiten behandeln die Aufgaben zum Erstellen, Konfigurieren, Warten und Verwenden Ihrer Inhaltsfragmente:

* [Aktivieren der Funktionen für Inhaltsfragmente für Ihre Instanz](/help/sites-cloud/administering/content-fragments/setup.md)
* [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) - Aktivieren, Erstellen und Definieren Ihrer Modelle
* [Erstellen von Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment) (mithilfe der Inhaltsfragmentkonsole)

Nachdem die Fragmente erstellt wurden, haben Sie folgende Möglichkeiten:

* [Verwenden der Konsole &quot;Inhaltsfragmente&quot;](/help/sites-cloud/administering/content-fragments/managing.md) - für den Zugriff auf, die Veröffentlichung (für die Vorschau oder Produktion) und die Referenzierung Ihrer Fragmente
* [Verwenden des Inhaltsfragmente-Editors](/help/sites-cloud/administering/content-fragments/authoring.md) - zum Bearbeiten, Veröffentlichen (zur Vorschau oder Produktion) und Referenzieren Ihrer Fragmente
* [Analyse](/help/sites-cloud/administering/content-fragments/analysis.md)  die Struktur Ihres Inhaltsfragments mithilfe des Editors
* [Zugriff auf Fragmente mit GraphQL zur Headless-Bereitstellung für Ihre Anwendungen](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md).
* [Oder verwenden Sie Ihre Fragmente für die Seitenbearbeitung](/help/sites-cloud/authoring/fundamentals/content-fragments.md)

>[!NOTE]
>
>Diese Seiten können zusammen mit folgenden Elementen gelesen werden:
>
>* [Anpassen und Erweitern von Inhaltsfragmenten](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [Inhaltsfragmente, die Komponenten für die Wiedergabe konfigurieren](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md)
>* [Seitenbearbeitung mit Inhaltsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md).

## Haupt- und Varianten {#main-and-variations}

Varianten sind eine wichtige Funktion AEM Inhaltsfragmente. Sie ermöglichen es Ihnen, Kopien der **Main** Inhalte für die Verwendung in bestimmten Kanälen und Szenarien, wodurch die Headless Content-Bereitstellung und das Seiten-Authoring noch flexibler werden.

* **Allgemein**

   * **Main** ist keine Variante an sich, sondern die Grundlage aller Varianten.
   * Integraler Bestandteil des Fragments:

      * Jedes Inhaltsfragment verfügt über eine Instanz von **Main**.
      * **Main** kann nicht gelöscht werden.

   * **Main** ist im Fragmenteditor unter **[Varianten](/help/sites-cloud/administering/content-fragments/authoring.md#variations)**.

  >[!NOTE]
  >
  >Im Editor, der im **Assets** Konsole, **Main** als **Master**.

* **Varianten**

   * Ausgabedarstellungen von Fragmenttext, eigens zu redaktionellen Zwecken. Diese können mit einem Kanal verbunden sein, doch ist dies nicht obligatorisch; auch für lokale Ad-hoc-Änderungen geeignet;
   * werden als Kopien von **Main**, können dann aber nach Bedarf bearbeitet werden. Häufig kommt es zu einer Inhaltsüberlappung zwischen den Varianten.
   * Kann während der Fragmentbearbeitung definiert werden; über das linke Bedienfeld.
   * werden im Fragment gespeichert, um die Streuung von Inhaltskopien zu vermeiden;
   * Varianten können [vergleichen und synchronisieren](/help/sites-cloud/administering/content-fragments/authoring.md#compare-and-synchronize-rich-text) mit **Main**.
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

   * Inhaltsfragmente (und ihre Varianten) können über die [Konsole &quot;Inhaltsfragmente&quot;](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console).
   * Erstellt und bearbeitet im [Inhaltsfragment-Editor](/help/sites-cloud/administering/content-fragments/authoring.md).

* Für die Inhaltsbereitstellung mit der [GraphQL-API AEM](/help/headless/graphql-api/content-fragments.md).

* Verfügbar im [Seiten-Editor mithilfe der Inhaltsfragment-Komponente](/help/sites-cloud/authoring/fundamentals/content-fragments.md) (Verweiskomponente):

   * Die [Inhaltsfragment-Kernkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=de) ist für Seitenautoren verfügbar. Dadurch können sie das erforderliche Inhaltsfragment entweder im HTML- oder JSON-Format referenzieren und bereitstellen.

Inhaltsfragmente sind eine Inhaltsstruktur mit folgenden Eigenschaften:

* ohne Layout oder Design (Textformatierung ist für Textfelder möglich).
* Sie sind unabhängig vom Bereitstellungsmechanismus (z. B. Seite oder Kanal).
* Enthalten mindestens einen [Bestandteil](#constituent-parts-of-a-content-fragment).
* Kann Bilder [enthalten oder mit Bildern verbunden sein](#fragments-with-visual-assets).

### Fragmente mit visuellen Assets {#fragments-with-visual-assets}

Um Autoren eine bessere Kontrolle über ihren Inhalt zu ermöglichen, können Bilder zu einem Inhaltsfragment hinzugefügt und/oder darin integriert werden.

Assets können auf verschiedene Weise mit einem Inhaltsfragment verwendet werden. Jede davon hat eigene Vorteile:

* as a **Inhaltsreferenz**
* innerhalb einer **Mehrzeiliger Text** field

### Bestandteile von Inhaltsfragmenten {#constituent-parts-of-a-content-fragment}

Die Inhaltsfragment-Assets bestehen aus den folgenden Teilen (entweder direkt oder indirekt):

* **Fragmentelementen**

   * Elemente korrelieren mit den Datenfeldern, die Inhalte enthalten.
   * Sie verwenden eine [Inhaltsfragmentmodell](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) , um das Inhaltsfragment zu erstellen. Die im Modell angegebenen Elemente (Felder) definieren die Struktur des Fragments. Bei diesen Elementen (Feldern) gibt es verschiedene Datentypen.

* **Fragmentabsätze**

   * Textblöcke, häufig mehrzeilig, die als einzelne Entitäten getrennt sind.

   * Ermöglichen die Inhaltssteuerung während der Seitenbearbeitung

* **Fragmentmetadaten**

   * Verwendung der [Assets-Metadatenschemata](/help/assets/metadata-schemas.md)
   * Tag-Erstellung möglich:

      * Beim Erstellen und Bearbeiten des Fragments
      * Wenn Sie [Eigenschaften anzeigen oder bearbeiten](/help/sites-cloud/administering/content-fragments/authoring.md#view-properties-tags) im Fragment-Editor

  >[!CAUTION]
  >
  >Profile für die Metadatenverarbeitung sind nicht für Inhaltsfragmente geeignet.

  >[!CAUTION]
  >
  >Ein Inhaltsfragmentmodell kann häufig Datenfelder definieren, die **Titel** und **Beschreibung**. Wenn diese beiden Felder vorhanden sind, handelt es sich um benutzerdefinierte Felder, die im Inhaltsbereich des Editors aktualisiert werden können.
  >
  >Das Inhaltsfragment und seine Varianten verfügen auch über Metadaten- (Eigenschaften-)Felder namens **Titel** und **Beschreibung**. Diese beiden Metadatenfelder sind integraler Bestandteil jedes Inhaltsfragments und jeder Variante und werden beim Erstellen des Fragments ursprünglich definiert. Sie können im Bereich &quot;Eigenschaften/Metadaten&quot;des Editors aktualisiert werden.

* **[Allgemein](#main-and-variations)**
* **[Varianten](#main-and-variations)**

### Voraussetzungen für Fragmente {#required-by-fragments}

Zum Erstellen von Inhaltsfragmenten benötigen Sie Folgendes:

* **Inhaltsmodelle**

   * werden [mithilfe des Konfigurations-Browsers aktiviert](/help/sites-cloud/administering/content-fragments/setup.md).
   * werden [mithilfe von Tools erstellt](/help/sites-cloud/administering/content-fragments/content-fragment-models.md).
   * Erforderlich zum [Erstellen eines Fragments](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments).
   * Definiert die Struktur eines Fragments (Titel, Inhaltselemente, Tag-Definitionen).
   * Für Definitionen des Inhaltsfragmentmodells sind ein Titel und ein Datenelement erforderlich. Alle anderen Elemente sind optional.
   * Das Modell kann Standardinhalte definieren – sofern zutreffend.
   * Autoren können die definierte Struktur beim Bearbeiten von Fragmentinhalten nicht ändern. Sie können jedoch den Modell-Editor über den Fragment-Editor öffnen.
   * Änderungen, die nach dem Erstellen von abhängigen Inhaltsfragmenten an einem Modell vorgenommen werden, können sich auf diese Inhaltsfragmente auswirken.

Um Ihre Inhaltsfragmente für die Bereitstellung Headless Content zu verwenden, benötigen Sie außerdem:

* a [GraphQL-Abfrage](/help/headless/graphql-api/content-fragments.md) , um den erforderlichen Inhalt anzufordern
* Diese Inhalte können dann zur Entwicklung Ihrer eigenen SPA für AEM verwendet werden. Weitere Informationen finden Sie in den folgenden Dokumenten:

   * [SPA-WKND-Tutorial](/help/implementing/developing/hybrid/wknd-tutorial.md)
   * [Erste Schritte mit React](/help/implementing/developing/hybrid/getting-started-react.md)
   * [Erste Schritte mit Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Um Ihre Inhaltsfragmente zum Erstellen von Seiten zu verwenden, benötigen Sie außerdem Folgendes:

* A **Inhaltsfragment-Komponente**

   * Hilft bei der Bereitstellung des Fragments im HTML- und/oder JSON-Format.
   * Erforderlich zum [Referenzieren des Fragments auf einer Seite](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
   * Zuständig für das Layout und die Bereitstellung eines Fragments, z. B. Kanäle.
   * Fragmente benötigen eine oder mehrere dedizierte Komponenten zur Definition des Layouts sowie zur Bereitstellung einiger oder aller Elemente/Varianten und zugehörigen Inhalte.
   * Wenn Sie ein Fragment bei der Bearbeitung auf eine Seite ziehen, wird die erforderliche Komponente automatisch zugewiesen.
   * Siehe [Inhaltsfragment-Kernkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=de).

## Anwendungsbeispiel {#example-usage}

Ein Fragment samt seinen Elementen und Varianten kann zur Erstellung von kohärentem Inhalt für verschiedene Kanäle verwendet werden. Beim Entwerfen Ihres Fragments müssen Sie überlegen, was und wo verwendet werden soll.

### WKND-Beispiel {#wknd-sample}

Die [WKND-Site und WKND-Freigabe](/help/implementing/developing/introduction/develop-wknd-tutorial.md) Beispiele werden bereitgestellt, anhand derer Sie mehr über AEM as a Cloud Service erfahren können.

<!-- CHECK: which links can/should be used these days? -->

Das WKND-Projekt umfasst:

* Inhaltsfragmentmodelle verfügbar unter:

   * `.../libs/dam/cfm/models/console/content/models.html/conf/wknd`

   * `.../ui#/aem/libs/dam/cfm/models/console/content/models.html/conf/wknd-shared`

* Inhaltsfragmente (und anderere Inhalte) verfügbar unter:

   * `.../assets.html/content/dam/wknd/en`
