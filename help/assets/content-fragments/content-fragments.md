---
title: Arbeiten mit Inhaltsfragmenten (Assets – Inhaltsfragmente)
description: Erfahren Sie, wie Sie mit Inhaltsfragmenten in Adobe Experience Manager (AEM) as a Cloud Service Seiteninhalte entwerfen, erstellen, kuratieren und verwenden können, die sich ideal für die Seitenbearbeitung und die Headless-Bereitstellung eignen. Auch wie sie zusammen mit MSM verwendet werden können.
exl-id: db17eff1-4252-48d5-bb67-5e476e93ef7e
source-git-commit: cc752e540fd08c2db5145316f57071c991d264b3
workflow-type: tm+mt
source-wordcount: '2229'
ht-degree: 63%

---

# Arbeiten mit Inhaltsfragmenten {#working-with-content-fragments}

Mit Adobe Experience Manager (AEM) as a Cloud Service können Sie Inhaltsfragmente entwerfen, erstellen, kuratieren und [seitenunabhängige Inhalte veröffentlichen](/help/sites-cloud/authoring/fundamentals/content-fragments.md). Sie ermöglichen es Ihnen, Inhalte für die Verwendung an mehreren Orten/über mehrere Kanäle vorzubereiten, die sich ideal für die Headless-Bereitstellung eignen. Sie können auch zusammen mit [Multi-Site-Management, um die Wiederverwendung Ihrer Inhalte zu ermöglichen](#reusing-content-fragments-with-msm-assets).

Inhaltsfragmente enthalten strukturierten Inhalt:

* Sie basieren auf einem [Inhaltsfragmentmodell](/help/assets/content-fragments/content-fragments-models.md), das eine Struktur für das daraus entstehende Fragment vordefiniert.
* Die Struktur kann variieren:
   * Einfach
      * Beispiel: ein einzelnes, mehrzeiliges Textfeld.
      * Sie kann zum Vorbereiten von unkomplizierten Inhalten für die Verwendung bei der Seitenbearbeitung verwendet werden.
   * Komplex
      * Eine Kombination aus vielen Feldern unterschiedlicher Datentypen, darunter Text, Zahl, boolescher Wert, Daten und Uhrzeit.
      * Es kann entweder zum Vorbereiten strukturierterer Inhalte für die Seitenbearbeitung oder zum Versand an Ihre Anwendung verwendet werden.
   * Verschachtelt
      * Mit den verfügbaren Referenzdatentypen können Sie Ihre Inhalte verschachteln.
      * Wird in der Regel für die Bereitstellung an Ihr Programm verwendet.

Mit der Sling Model (JSON)-Exportfunktion der AEM-Kernkomponenten können Inhaltsfragmente auch im JSON-Format bereitgestellt werden. Diese Form der Bereitstellung:

* bietet Ihnen die Möglichkeit, mithilfe der Komponente zu bestimmen, welche Fragmentelemente bereitgestellt werden sollen
* ermöglicht durch das Hinzufügen mehrerer Inhaltsfragment-Kernkomponenten auf der für die API-Bereitstellung verwendeten Seite eine Bereitstellung in größerem Umfang

>[!NOTE]
>
>Inhaltsfragmente sind eine Sites-Funktion, werden jedoch als **Assets**.
>
>Sie werden jetzt hauptsächlich mit der **[Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console)**-Konsole verwaltet, können jedoch weiterhin über die **Assets**-Konsole verwaltet werden. In diesem Abschnitt wird die Verwaltung über die **Assets**-Konsole beschrieben.
>
>Es gibt zwei Editoren für die Bearbeitung von Inhaltsfragmenten. In diesem Abschnitt wird der ursprüngliche Editor beschrieben, auf den Sie hauptsächlich über das **Assets** Konsole. Weitere Informationen finden Sie in der Sites-Dokumentation . [Inhaltsfragmente - Authoring](/help/sites-cloud/administering/content-fragments/authoring.md)für Details zum neuen Editor (hauptsächlich über die **Inhaltsfragmente** -Konsole). Beide Editoren verfügen in der oberen Symbolleiste über einen Umschalter, um einen schnellen Zugriff auf den anderen Editor zu ermöglichen.

Diese und die folgenden Seiten behandeln die Aufgaben zum Erstellen, Konfigurieren, Verwalten und Verwenden Ihrer Inhaltsfragmente:

* [Aktivieren der Funktionen für Inhaltsfragmente für Ihre Instanz](/help/assets/content-fragments/content-fragments-configuration-browser.md)
* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md) - Aktivieren, Erstellen und Definieren Ihrer Modelle
* [Verwalten von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-managing.md) - Erstellen Sie Ihre Inhaltsfragmente und bearbeiten, veröffentlichen und verweisen Sie dann auf
* [Varianten – Erstellen von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-variations.md) – Erstellen Sie das Inhaltsfragment und erstellen Sie Varianten der Vorlage
* [Markdown](/help/assets/content-fragments/content-fragments-markdown.md) – Verwendung der Markdown-Syntax für Ihr Fragment
* [Verwenden verknüpfter Inhalte](/help/assets/content-fragments/content-fragments-assoc-content.md) – Hinzufügen verknüpfter Inhalte
* [Metadaten – Fragmenteigenschaften](/help/assets/content-fragments/content-fragments-metadata.md) – Anzeigen und Bearbeiten der Fragmenteigenschaften
* Verwendung [Inhaltsfragmente, zusammen mit GraphQL, damit Sie Inhalte bereitstellen können](/help/assets/content-fragments/content-fragments-graphql.md) zur Verwendung in Ihren Anwendungen. Dabei kann es Ihnen helfen, die [JSON-Ausgabe](/help/assets/content-fragments/content-fragments-json-preview.md) in der Vorschau anzeigen.
* [Wiederverwenden von Inhaltsfragmenten mit MSM für Assets](#reusing-content-fragments-with-msm-assets)

>[!NOTE]
>
>Diese Seiten können wie folgt gelesen werden:
>
>* [Seitenbearbeitung mit Inhaltsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
>* [Anpassen und Erweitern von Inhaltsfragmenten](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [Inhaltsfragmente, die Komponenten für die Wiedergabe konfigurieren](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md)

Die Anzahl der Kommunikationskanäle nimmt jährlich zu. Typischerweise beziehen sich Kanäle auf den Bereitstellungsmechanismus, und zwar wie folgt:

* Physischer Kanal; z. B. Desktop, Mobilgerät.
* Form der Bereitstellung in einem physischen Kanal; z. B. die Produktdetailseite, die Produktkategorieseite für Desktops oder „mobiles Web“, „Mobile App“ für Mobilgeräte.

Sie möchten jedoch (wahrscheinlich) nicht denselben Inhalt für alle Kanäle verwenden - Sie müssen Ihren Inhalt entsprechend dem jeweiligen Kanal optimieren.

Inhaltsfragmente ermöglichen Ihnen Folgendes:

* Erwägen, wie sich Zielgruppen effizient kanalübergreifend erreichen lassen
* Kanalneutrale redaktionelle Inhalte erstellen und verwalten
* Inhaltspools für mehrere Kanäle erstellen
* Inhaltsvarianten für bestimmte Kanäle entwerfen
* Bilder durch Einfügen von Assets (Fragmente mit gemischten Medien) zu Texten hinzufügen
* Erstellen Sie verschachtelte Inhalte, die die Komplexität Ihrer Daten widerspiegeln.

Diese Inhaltsfragmente können dann zusammengestellt werden, um Erlebnisse über verschiedene Kanäle bereitzustellen.

>[!NOTE]
>
>**Inhaltsfragmente** und **[Experience Fragments](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)** sind unterschiedliche Funktionen in AEM:
>* **Inhaltsfragmente** sind redaktionelle Inhalte mit Definition und Struktur, aber ohne zusätzliches visuelles Design und/oder Layout. Sie können für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden.
>* **Experience Fragments** sind vollständig gestaltete Inhalte und stellen Teile von Web-Seiten dar.
>
>Experience Fragments können Inhalte in Form von Inhaltsfragmenten enthalten, aber nicht umgekehrt.
>
>Weitere Details finden Sie auch in den [Informationen zu Inhaltsfragmenten und Experience Fragments in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=de#content-fragments).

## Inhaltsfragmente und Content Services {#content-fragments-and-content-services}

Mit den AEM Content Services können die Beschreibung und Bereitstellung von Inhalten in/über AEM über einen Fokus auf Web-Seiten hinweg generalisiert werden.

Sie ermöglichen die Bereitstellung von Inhalten in Kanälen, die keine traditionellen AEM-Web-Seiten sind, und nutzen standardisierte Methoden, die von allen Clients genutzt werden können. Diese Kanäle können Folgendes sein:

* Single Page Applications (SPA)
* native Mobile Apps
* weitere AEM-externe Kanäle und Touchpoints

Der Versand erfolgt im JSON-Format mit dem JSON-Exporter.

AEM-Inhaltsfragmente können zur Beschreibung und Verwaltung strukturierter Inhalte verwendet werden. Strukturierte Inhalte werden in Modellen definiert, die verschiedene Inhaltstypen enthalten können, darunter Text, numerische Daten, boolesche Werte, Datum und Uhrzeit und mehr.

Zusammen mit der JSON-Exportfunktion der AEM-Kernkomponenten kann dieser strukturierte Inhalt dann zur Bereitstellung von AEM-Inhalten auf anderen Kanälen als AEM-Seiten verwendet werden.

>[!NOTE]
>
>Eine Einführung in die Headless-Entwicklung für AEM Sites as a Cloud Service finden Sie unter [Headless und AEM](/help/headless/introduction.md).

>[!NOTE]
>
>AEM unterstützt auch die Übersetzung von Fragmentinhalten. Weitere Informationen finden Sie unter [Übersetzen von Assets](/help/assets/translate-assets.md).

## Wiederverwenden von Inhaltsfragmenten mit MSM für Assets {#reusing-content-fragments-with-msm-assets}

Wenn der Zugriff über **Assets** -Konsole können Sie MSM verwenden und Live Copies für Ihre Fragmente erstellen.

Weitere Informationen finden Sie unter [Wiederverwenden von Inhaltsfragmenten mit MSM für Assets](/help/assets/reuse-assets-using-msm.md). Dies ermöglicht [Vererbung](/help/assets/content-fragments/content-fragments-variations.md#inheritance) für Varianten und einzelne Felder Ihrer Fragmente.

>[!CAUTION]
>
>Wenn Sie MSM verwenden wollen (welches Kopien von Inhaltsfragmenten erstellt), dann sollten alle **Eindeutig**-Einschränkungen aus allen Datentypen entfernt werden, die in den jeweiligen [Inhaltsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md) verwendet werden.

## Inhaltstyp {#content-type}

Inhaltsfragmente werden:

* als **Assets** gespeichert:

   * Inhaltsfragmente (und deren Varianten) können in der Konsole **Assets** erstellt und verwaltet werden.
   * Im Inhaltsfragment-Editor erstellt und bearbeitet.

* Wird im [Seiten-Editor durch die Inhaltsfragment-Komponente](/help/sites-cloud/authoring/fundamentals/content-fragments.md) (Verweiskomponente):

   * Die Komponente **Inhaltsfragment** steht für Seitenautoren zur Verfügung. Sie ermöglicht das Erstellen von Verweisen für sowie das Bereitstellen des erforderlichen Inhaltsfragments im HTML- oder JSON-Format.

* Abrufbar mit der [AEM-GraphQL-API](/help/headless/graphql-api/content-fragments.md).

Inhaltsfragmente sind eine Inhaltsstruktur mit folgenden Eigenschaften:

* Sie haben kein Layout oder Design (im Rich-Text-Modus ist eine Textformatierung möglich).
* mindestens einen [Bestandteile](#constituent-parts-of-a-content-fragment).
* [Bilder enthalten oder mit ihnen verbunden werden können](#fragments-with-visual-assets).
* Wird verwendet [Übergangsinhalte](#in-between-content-when-page-authoring-with-content-fragments) wenn auf einer Seite auf sie verwiesen wird.
* Sie sind unabhängig vom Bereitstellungsmechanismus (d. h. Seite, Kanal).

### Fragmente mit visuellen Assets {#fragments-with-visual-assets}

Um Autoren eine bessere Kontrolle über eigene Inhalte zu ermöglichen, können Bilder zu einem Inhaltsfragment hinzugefügt und/oder darin integriert werden.

Assets können auf verschiedene Weise mit einem Inhaltsfragment verwendet werden. Jede davon hat eigene Vorteile:

* In ein Fragment **eingefügte Assets** (Fragmente mit gemischten Medien)

   * Sie sind Teil des Fragments (siehe [Bestandteile von Inhaltsfragmenten](#constituent-parts-of-a-content-fragment)).
   * definieren die Position des Assets;
   * Weitere Informationen finden Sie unter [Einfügen von Assets in Fragmente](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) im Fragment-Editor.

  >[!NOTE]
  >
  >Die in das Inhaltsfragment eingefügten visuellen Assets werden mit dem vorangehenden Absatz verbunden. Wenn das Fragment zu einer Seite hinzugefügt wird, werden diese Assets in Bezug auf diesen Absatz verschoben, wenn Übergangsinhalte hinzugefügt werden.

* **Zugehörige Inhalte**

   * Verbunden mit einem Fragment, jedoch nicht mit einem festen Teil des Fragments (siehe [Bestandteile von Inhaltsfragmenten](#constituent-parts-of-a-content-fragment)).
   * Hat eine gewisse Flexibilität bei der Positionierung.
   * Einfache Verwendung (als Zwischeninhalt) bei der Verwendung des Fragments auf einer Seite.

  weitere Informationen finden Sie unter [Zugehörige Inhalte](/help/assets/content-fragments/content-fragments-assoc-content.md).

* Im Seiten-Editor verfügbare Assets im **Asset-Browser**

   * bieten vollständige Flexibilität bei der Asset-Auswahl;
   * Hat eine gewisse Flexibilität bei der Positionierung.
   * liefern nicht die Möglichkeit, für ein bestimmtes Fragment genehmigt zu werden;

  weitere Informationen finden Sie unter [Assets-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser).

### Bestandteile von Inhaltsfragmenten {#constituent-parts-of-a-content-fragment}

Inhaltsfragment-Assets setzen sich aus folgenden Teilen zusammen (entweder direkt oder indirekt):

* **Fragmentelementen**

   * Elemente korrelieren mit den Datenfeldern, die Inhalte enthalten.
   * Sie verwenden ein Inhaltsmodell, um das Inhaltsfragment zu erstellen. Die im Modell angegebenen Elemente (Felder) definieren die Struktur des Fragments. Diese Elemente (Felder) können verschiedene Datentypen aufweisen.

* **Fragmentabsätze**

   * Textblöcke, häufig mehrzeilig, die als einzelne Entitäten getrennt sind.

   * In den Modi [Rich-Text](/help/assets/content-fragments/content-fragments-variations.md#rich-text) und [Markdown](/help/assets/content-fragments/content-fragments-variations.md#markdown) kann ein Absatz als Kopfzeile formatiert werden. In diesem Fall gehören dieser und der folgende Absatz als eine Einheit zusammen.

   * Ermöglichen die Inhaltssteuerung während der Seitenbearbeitung

* **In ein Fragment eingefügte Assets (Fragmente mit gemischten Medien)**

   * Assets (Bilder), die in das eigentliche Fragment eingefügt und als interne Inhalte eines Fragments verwendet werden;
   * Im Absatzsystem des Fragments eingebettet.
   * können formatiert werden, wenn das [Fragment auf einer Seite verwendet/referenziert wird](/help/sites-cloud/authoring/fundamentals/content-fragments.md);
   * können nur über den Fragment-Editor einem Fragment hinzugefügt, daraus gelöscht oder darin verschoben werden; diese Aktionen können nicht im Seiten-Editor durchgeführt werden;
   * Kann nur zu einem Fragment hinzugefügt, daraus gelöscht oder darin verschoben werden, indem die Variable [Rich-Text-Format im Fragment-Editor](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
   * können nur zu mehrzeiligen Textelementen hinzugefügt werden (beliebiger Fragmenttyp);
   * werden mit dem vorangehenden Text (Absatz) verbunden;

     >[!CAUTION]
     >
     >Assets können (versehentlich) aus dem Fragment gelöscht werden, wenn in das Nur-Text-Format gewechselt wird.

     >[!NOTE]
     >
     >Assets können auch als [zusätzlicher (Übergangs) Inhalt](/help/sites-cloud/authoring/fundamentals/content-fragments.md#using-associated-content) hinzugefügt werden, wenn ein Fragment auf einer Seite verwendet wird (bei Nutzung von zugehörigen Inhalten oder Assets aus dem Assets-Browser).

* **Zugehörige Inhalte**

   * Hierbei handelt es sich um externen Inhalt für das Fragment, der jedoch von redaktioneller Relevanz ist. Normalerweise Bilder, Videos oder andere Fragmente.
   * Die einzelnen Assets innerhalb der Sammlung können mit dem Fragment im Seiten-Editor verwendet werden, wenn es einer Seite hinzugefügt wird. Zugehörige Inhalte sind also optional, abhängig von den Anforderungen des jeweiligen Kanals.
   * Die Assets sind [mit Fragmenten über Sammlungen verknüpft sind](/help/assets/content-fragments/content-fragments-assoc-content.md); verknüpfte Sammlungen ermöglichen es dem Autor, zu entscheiden, welche Assets beim Bearbeiten der Seite verwendet werden sollen.

      * Sammlungen können mit Fragmenten als Standardinhalt oder von Autoren während der Fragmentbearbeitung verbunden werden.
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

* **Vorlage**

   * Ein Teil des Fragments

      * Jedes Inhaltsfragment hat eine Vorlageninstanz.
      * Die Vorlage kann gelöscht werden.

   * Auf die primäre Vorlage kann über den Fragment-Editor unter **[Varianten](/help/assets/content-fragments/content-fragments-variations.md)** zugegriffen werden.
   * Die Vorlage ist keine Variante an sich, sondern die Grundlage aller Varianten.

* **Varianten**

   * Ausgabeformate von Fragmenttext, die für einen redaktionellen Zweck spezifisch sind. Sie können mit einem Kanal verbunden sein, sind jedoch nicht obligatorisch. Sie können auch für lokale Ad-hoc-Änderungen verwendet werden.
   * werden als Kopien von **Master**, können aber dann nach Bedarf bearbeitet werden. Es gibt Inhaltsüberschneidungen zwischen den Varianten selbst.
   * können beim Erstellen von Fragmenten definiert werden;
   * werden im Fragment gespeichert, um die Streuung von Inhaltskopien zu vermeiden;
   * können mit der Vorlage [synchronisiert](/help/assets/content-fragments/content-fragments-variations.md#synchronizing-with-master) werden, wenn der Vorlageninhalt aktualisiert wurde;
   * können [zusammengefasst](/help/assets/content-fragments/content-fragments-variations.md#summarizing-text) werden, um Text schnell auf eine vordefinierte Länge zu kürzen;
   * sind auf der Registerkarte [Varianten](/help/assets/content-fragments/content-fragments-variations.md) des Fragment-Editors verfügbar.

### Übergangsinhalte bei der Seitenerstellung mit Inhaltsfragmenten {#in-between-content-when-page-authoring-with-content-fragments}

Übergangsinhalte:

* Verfügbar für die Verwendung im Seiteneditor bei der Arbeit mit Inhaltsfragmenten.
* [Zusätzliche Inhalte, die im Fluss eines Fragments hinzugefügt werden](/help/sites-cloud/authoring/fundamentals/content-fragments.md#adding-in-between-content) , nachdem sie auf einer Seite verwendet oder referenziert wurde.
* Zur Verwendung in [Seiten-Editor beim Arbeiten mit Inhaltsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
* Übergangsinhalte können zu jedem beliebigen Fragment hinzugefügt werden, in dem nur ein Element sichtbar ist.
* Zugehörige Inhalte sowie Assets und/oder Komponenten des entsprechenden Browsers können eingesetzt werden.

>[!CAUTION]
>
>Bei Zwischeninhalten handelt es sich um Seiteninhalte. Sie werden nicht im Inhaltsfragment gespeichert.

### Voraussetzungen für Fragmente {#required-by-fragments}

Um Inhaltsfragmente zu erstellen, benötigen Sie:

* **Inhaltsmodelle**

   * werden [mithilfe des Konfigurations-Browsers aktiviert](/help/assets/content-fragments/content-fragments-configuration-browser.md).
   * werden [mithilfe von Tools erstellt](/help/assets/content-fragments/content-fragments-models.md).
   * Erforderlich zum [Erstellen eines Fragments](/help/assets/content-fragments/content-fragments-managing.md#creating-content-fragments).
   * Definiert die Struktur eines Fragments (Titel, Inhaltselemente, Tag-Definitionen).
   * Inhaltsmodelldefinitionen erfordern einen Titel und ein Datenelement. Alle weiteren Elemente sind optional.
   * Das Modell kann Standardinhalte definieren – sofern zutreffend.
   * Autoren können die definierte Struktur nicht ändern, wenn sie den Fragmentinhalt erstellen.
   * Änderungen, die nach dem Erstellen von abhängigen Inhaltsfragmenten an einem Modell vorgenommen wurden, können sich auf diese Inhaltsfragmente auswirken.

Um Ihre Inhaltsfragmente für die Seitenbearbeitung zu verwenden, benötigen Sie außerdem:

* **Inhaltsfragment-Komponente**

   * Instrumentiert, um das Fragment im HTML-Format, JSON-Format oder beides bereitzustellen.
   * Erforderlich zum [Referenzieren des Fragments auf einer Seite](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
   * Zuständig für das Layout und die Bereitstellung eines Fragments, d. h. Kanäle.
   * Fragmente benötigen eine oder mehrere dedizierte Komponenten, um das Layout zu definieren und einige oder alle Elemente/Varianten und zugehörigen Inhalte bereitzustellen.
   * Wenn Sie ein Fragment bei der Bearbeitung auf eine Seite ziehen, wird die erforderliche Komponente automatisch zugewiesen.

## Anwendungsbeispiel {#example-usage}

Ein Fragment samt seinen Elementen und Varianten kann zur Erstellung von kohärentem Inhalt für verschiedene Kanäle verwendet werden. Überlegen Sie beim Entwerfen Ihres Fragments, was verwendet wird und wo es verwendet wird.

### WKND-Beispiel {#wknd-sample}

Die Beispiele der [WKND-Site](/help/implementing/developing/introduction/develop-wknd-tutorial.md) helfen Ihnen dabei, mehr über AEM as a Cloud Service zu erfahren.

Das WKND-Projekt umfasst:

* Inhaltsfragmentmodelle verfügbar unter:
  `http://<hostname>:<port>/libs/dam/cfm/models/console/content/models.html/conf/wknd`

* Inhaltsfragmente (und anderere Inhalte) verfügbar unter:
  `http://<hostname>:<port>/assets.html/content/dam/wknd/en`
