---
title: Prompting Guide for Experience Modernization Agent
description: Dieses Handbuch enthält Tipps für eine effektive Eingabeaufforderung an den Experience Modernization Agent und beschreibt, was dessen Fähigkeiten bewirken.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: e2a9c55644c0d9542f6a299f0df30a3dfd4a55de
workflow-type: tm+mt
source-wordcount: '2696'
ht-degree: 0%

---


# Prompting Guide for Experience Modernization Agent {#prompting-guide}

Der Experience Modernization Agent wählt automatisch die entsprechenden Kenntnisse auf der Grundlage von Anforderungen in natürlicher Sprache aus. Dieses Handbuch enthält Tipps für eine effektive Eingabeaufforderung und beschreibt, was die Fähigkeiten tun.

## Allgemeine Tipps {#general-tips}

### Einige Fähigkeiten hängen von Leistungen aus anderen Fähigkeiten ab. {#dependency}

* Da der Massenimport die von der Seitenmigration erstellte Importinfrastruktur benötigt, migrieren Sie mindestens eine Seite, bevor Sie den Massenimport ausführen.
* Da Block-CSS auf die globalen Design-Token verweist, vervollständigen Sie das Site-Wide-Design, bevor Sie einzelne Blöcke formatieren.

### Die KI folgt strukturierten Workflows und stellt bei Bedarf klärende Fragen. {#workflows}

* Vertrauen Sie dem Prozess und beantworten Sie diese qualifizierten Fragen, wenn sie auftauchen.
* Versuchen Sie nicht, in der ersten Eingabeaufforderung alle Anforderungen vorab zu laden.

### Erstellen Sie Markdown-Dateien im Projekt, um projektspezifische Regeln, Richtlinien, Design-Entscheidungen oder Begrenzungen zu dokumentieren. {#markdown-files}

* Diese Markdown-Dateien (z. B. INSTRUCTIONS.md, CONTEXT.md) können Dateibenennungskonventionen, Inhaltszuordnungsregeln oder Markenrichtlinien enthalten.
* Bitten Sie den Agenten beim Starten einer neuen Konversation, „sich durch Lesen der Projektdokumentation aufzuwärmen“, damit dieser Kontext geladen wird, bevor er mit Aufgaben fortfährt.

### Das Kontextfenster des Agenten ist nicht unendlich. {#limited-window}

* Bei langen Gesprächen können frühere Anweisungen komprimiert oder vergessen werden.
* Wenn der Agent den Kontext verloren zu haben scheint, erinnern Sie ihn entweder an die wichtigsten Punkte oder löschen Sie den Chat und beginnen Sie neu mit einer Warm-up-Aufforderung, um die Projektdokumentation zu lesen.

### Verwenden Sie iterative Eingabeaufforderungen, um die Ergebnisse zu verfeinern. {#iterate}

* Wenn etwas nicht richtig aussieht (z. B. eine falsche Hintergrundfarbe auf einem Block), fordern Sie den Support-Mitarbeiter auf, das spezifische Problem zu beheben, anstatt von vorne zu beginnen.

## Site-Erstellung und -Migration - Kenntnisse {#site-migration}

Der Site Modernization Agent bietet viele Fähigkeiten zum Erstellen neuer Edge Delivery Services-Sites und zum Migrieren vorhandener Websites. Jede neue Edge Delivery-Site oder jedes neue Migrationsprojekt sollte diese Fähigkeiten nutzen.

### Migrieren einer Site oder Seite zu AEM {#migrate-a-site}

Verwenden Sie diese Eingabeaufforderung, wenn Sie Inhalte von einer bestehenden Website zu Edge Delivery Services migrieren.

#### Beispiel-Eingabeaufforderungen {#example-migrate}

* „Migrieren Sie diese Seite: `https://example.com/about`
* „Migrieren dieser Seiten: URL1, URL2, URL3“

#### Was Sie wissen sollten {#wtk-migrate}

* Die Migration folgt einem siebenstufigen Workflow:
   1. Der Agent kratzt die Quellseite.
   1. Es identifiziert die Abschnittsstruktur.
   1. Es führt eine Authoring- und Analysefunktion durch.
   1. Dabei wird der Inhalt Blockvarianten zugeordnet.
   1. Er generiert einen Markdown.
   1. Es schafft eine Importinfrastruktur.
   1. Sie zeigt eine Vorschau des Ergebnisses an.
* Der Agent analysiert Seiten mithilfe einer zweistufigen Hierarchie:
   * Zuerst werden Abschnittsgrenzen (Hintergrundänderungen, Abstandsverschiebungen) identifiziert
   * Anschließend werden Inhaltssequenzen in jedem Abschnitt identifiziert.
* Die Erstellung der Analyse folgt [Davids Modell.](https://www.aem.live/docs/davidsmodel)
   * Für jede Inhaltssequenz wird zunächst überprüft: „Kann ein Autor dies durch normale Eingabe erstellen?“
   * Standardinhalte (Überschriften, Absätze, Listen, Inline-Bilder) werden gegenüber Blöcken bevorzugt.
* Der Agent versucht, vorhandene Blöcke aus der Blockbibliothek des Repositorys wiederzuverwenden, bevor neue erstellt werden.
   * Wenn Inhalte nicht einem vorhandenen Block zugeordnet werden können, werden neue Blockvarianten erstellt.
   * Sie können zu Änderungen auffordern, neue Varianten anfordern oder Zuordnungen interaktiv anpassen.
* Blockvarianten werden mit Metadaten verfolgt.
   * Bei der Migration mehrerer Seiten lädt der Agent zuerst vorhandene benutzerdefinierte Varianten und verwendet sie dann erneut, wenn die Formatierung übereinstimmt (70 % Ähnlichkeitsschwellenwert basierend auf Zweck, Farben, Typografie, Abstand, Layout).
* Kopf-, Navigations- und Fußzeile sind von der Seitenmigration ausgeschlossen. Diese werden von dedizierten Fähigkeiten gehandhabt.
* Bei jeder Migration wird eine Importinfrastruktur (Seitenvorlagen, Block-Parser, Transformatoren) für zukünftige Massenimporte erstellt.

### Massenimport {#bulk-import}

Verwenden Sie diese Eingabeaufforderung, um viele Seiten derselben Vorlage nach Abschluss einer [anfänglichen Einzelseitenmigration“ zu importieren](#migrate-a-site)

#### Beispiel-Eingabeaufforderungen {#example-prompts-bulk-import}

* „Führen Sie den Massenimport auf diesen Seiten aus: URL1, URL2, URL3.“
* „Führen Sie den Massenimport auf allen Produktseiten aus.“
* „Massenimport dieser Blog-Seiten: URL1, URL2.“

#### Was Sie wissen sollten {#wtk-bulk-import}

* Der Massenimport hängt von der Importinfrastruktur ab, die während einer vorherigen Einzelseitenmigration erstellt wurde.
   * Dazu gehören Seitenvorlagen (Abschnittsstruktur), Transformatoren (Site-Wide DOM Cleanup) und Parser (blockspezifische Konvertierung von HTML in Tabellen).
* Sie müssen mindestens eine repräsentative Seite pro Vorlage migrieren, bevor der Massenimport ausgeführt werden kann.
* Beim Massenimport werden die Struktur und die Zuordnungen wiederverwendet, die während der Einzelseitenmigration erstellt wurden.
   * Es leitet Vorlagen nicht von Grund auf ab.
* Transformatoren arbeiten auf dem gesamten DOM vor und nach dem Parsen. Parser arbeiten auf der Ebene der einzelnen Blöcke.
* Alle Parser werden validiert, bevor der Massenimport fortgesetzt werden kann.
* Eine Vorlage entspricht einer Massenimportkonfiguration.
   * Das Mischen von Vorlagen in einer einzigen Ausführung wird nicht unterstützt.

#### Typischer Workflow {#typical-workflow}

Der empfohlene Workflow ist iterativ: Validieren Sie ihn zuerst in kleinen Mengen und skalieren Sie dann die Anwendung.

1. **Führen Sie zuerst eine Migration auf einer einzelnen Seite aus.** : Migrieren Sie eine repräsentative Seite für die Vorlage, die Sie in großen Mengen importieren möchten.
   * Dadurch wird die erforderliche Importinfrastruktur erstellt.
1. **Führen Sie den Massenimport auf einer kleinen Gruppe von Seiten aus.** - Bitten Sie den Agenten, den Massenimport auszuführen, und geben Sie eine kurze Liste der URLs an, die derselben Vorlage folgen.
1. **Überprüfen und verfeinern Sie die Ergebnisse.** - Überprüfen Sie die importierten Seiten.
   * Wenn etwas falsch aussieht, bitten Sie den Agenten, Parser, Transformatoren oder Importlogik anzupassen.
1. **Hochskalieren.** - Wenn die Ergebnisse korrekt aussehen, geben Sie die vollständige Liste der URLs an.
   * Der Agent verwendet dieselbe Importlogik wieder und führt Massenimporte skaliert durch.

### Erstellen von Web-Seiten {#scraping-webpages}

Verwenden Sie diese Eingabeaufforderung, um Inhalte, Metadaten und Bilder aus einer Quell-URL für die Analyse oder Migration zu extrahieren.

#### Beispiel-Eingabeaufforderungen {#example-scraping}

* „Diese Seite für die Analyse kratzen: `https://example.com`&quot;
* „Extrahieren von Inhalten aus `https://example.com/product`&quot;

#### Was Sie wissen sollten {#wtk-scraping}

* Diese Eingabeaufforderung wird in der Regel automatisch als erster Schritt der Seitenmigration aufgerufen.
* Über CSS ausgeblendeter Inhalt wird ebenfalls erfasst, wenn er im DOM vorhanden ist.
* Lazy-Loading-Bilder und Client-seitig gerenderte Inhalte werden verarbeitet, indem Sie durch die Seite in Headless-Chromium scrollen und Skripte ausführen lassen.
* WebP/AVIF/SVG-Bilder werden aus Kompatibilitätsgründen in PNG konvertiert.
* Metadaten werden extrahiert, einschließlich Titel, Beschreibung, Open-Graph-Tags, JSON-LD-strukturierte Daten und kanonischer URL.
* Bilder im DOM sind unveränderlich.
   * background-image wird zu img konvertiert.
   * Bildelemente werden entpackt
   * srcset wird zu src aufgelöst
   * Relative URLs werden in absolute URLs konvertiert
   * Inline-SVG in werden in img-Dateien konvertiert.
* Bereinigte Dokumentpfade werden generiert (Kleinbuchstaben ohne `.html`).
* Folgende Ergebnisse werden erzeugt:
   * `screenshot.png`
   * `cleaned.html` (keine Scripts/Stile)
   * `metadata.json`
   * Ordner mit lokalen Kopien `images/`
* Benutzer können nach den Abmessungen des Screenshots fragen und bestimmte Gerätegrößen (Smartphone und Tablet) für die Inhaltsextraktion anfordern.
* Das Extrahieren von Inhalten an mehreren Haltepunkten verlängert die Verarbeitungszeit.

### Designmigration {#design-migration}

Verwenden Sie diese Eingabeaufforderung, um visuelles Design aus einer Quell-Site zu extrahieren und auf Edge Delivery Services anzuwenden.

#### Beispiel-Eingabeaufforderungen {#example-design}

* „Migrieren des Designs aus `https://example.com`&quot;
* „Design-Token extrahieren“
* „Den Heldenblock gestalten“

#### Was Sie wissen sollten {#wtk-design}

* Die Designmigration umfasst zwei Phasen:
   1. Phase 1 (standortweit) extrahiert Folgendes nach `styles/styles.css`:
      * Farbpalette und Akzentfarben weltweit
      * Typografie-System (Schriftarten, Größen, Gewichtungen)
      * Abstandssystem (Abstand, Ränder, Lücken)
      * Abschnittshintergründe (hell, dunkel, farbig)
      * Stile der Basiskomponenten (Schaltflächen, Links, Bilder)
      * Ausgaben an
   1. Phase 2 migriert einzelne Blockstile und erstellt blockspezifische CSS-Dateien in `/blocks/{name}/{name}.css`.
* Um die Blockformatierung (Phase 2) durchzuführen, muss zunächst das Site-Wide Design (Phase 1) abgeschlossen sein.
   * Das globale Designsystem stellt benutzerdefinierte CSS-Eigenschaften bereit, die Verweise blockieren.
* Geschätzte Zeit:
   * Phase 1: 5-10 Minuten
   * Phase 2: 10-15 Minuten
* Bei mehrdeutigen Anfragen wird die Migration standardmäßig abgeschlossen (beide Phasen).

### Blockkritik {#block-critique}

Verwenden Sie diese Eingabeaufforderung, um einzelne migrierte Blöcke zu validieren und zu verfeinern und die visuelle Genauigkeit mit der ursprünglichen Website sicherzustellen.

#### Beispiel-Eingabeaufforderungen {#example-block-critique}

* „Kritischer Heldenblock“
* „Benutzerdefinierte Block-Karten validieren“

#### Was Sie wissen sollten {#wtk-block-critique}

* Die Blockkritik vergleicht einen migrierten Block mit seiner ursprünglichen Quelle und wendet iterativ CSS-Korrekturen an, bis eine visuelle Ähnlichkeit von 85 % erreicht ist oder drei Iterationen abgeschlossen sind.
* Für die Kenntnis muss der Block zuerst durch Seitenmigration erstellt worden sein.
* Eine Blockkritik folgt einem sechsstufigen Workflow:
   1. Erfasst den ursprünglichen Block aus der Quellseite mithilfe einer XPath-Auswahl.
   1. Es initialisiert die Kritik-Sitzung.
   1. Es überprüft den Originalblock (Screenshots, Stile, HTML).
   1. Er überprüft den migrierten Block.
   1. Es vergleicht Elemente und generiert einen Ähnlichkeitswert mit CSS-Korrekturen.
   1. Es werden Fehlerbehebungen vorgenommen und die Prüfungen wiederholt, bis das 85-%-Ziel erreicht ist.
* Jede Iteration zeigt einen vollständigen Kritikbericht mit allen Unterschieden an, wendet alle CSS-Korrekturen an (priorisiert durch visuelle Auswirkungen), prüft in der Vorschau, überprüft erneut und zeigt Verbesserungsmetriken an.
* Verwenden Sie die Blockkritik, nachdem [Design-Migration](#design-migration) abgeschlossen ist.

### Seitenkritik {#page-critique}

Verwenden Sie diese Eingabeaufforderung, um die gesamte migrierte Seite im Hinblick auf ihre vollständige visuelle Wiedergabetreue mit der ursprünglichen Website zu überprüfen.

#### Beispiel-Eingabeaufforderungen {#example-page-critique}

* „Kritik an der Seite“
* „Validieren der migrierten Seite anhand von `https://example.com/about`&quot;

#### Was Sie wissen sollten {#wtk-page-critique}

* Die Seitenkritik führt einen ganzseitigen visuellen Vergleich zwischen der ursprünglichen und der migrierten Seite durch und iteriert, bis ein Ähnlichkeitsziel von 85 % erreicht ist oder drei Iterationen abgeschlossen sind.
* Eine Seitenkritik hat einen fünfstufigen Workflow:
   1. Es initialisiert eine Kritiksitzung.
   1. Es werden alle Elemente auf der Originalseite überprüft.
   1. Es werden alle Elemente auf der migrierten Seite überprüft.
   1. Er vergleicht und generiert einen Ähnlichkeitswert mit priorisierten CSS-Fehlerbehebungen.
   1. Es werden Fehlerbehebungen vorgenommen und die Prüfungen wiederholt, bis das 85-%-Ziel erreicht ist.
* Eine Seitenkritik benötigt die URL der Quellseite und den migrierten Pfad (z. B. &quot;/about„) als Eingabe.
* Verwenden Sie die Seitenkritik bei der Validierung der Gesamtseitentreue oder der gleichzeitigen Validierung mehrerer Blöcke.
* [Blockkritik verwenden](#block-critique) für fokussierte Validierung auf bestimmte Komponenten.
* Der folgende Workflow wird empfohlen:
   1. Migrieren einer Seite.
   1. Wenden Sie ein Design an.
   1. Blockkritik auf Schlüsselblöcke ausführen
   1. Führen Sie eine Seitenkritik zur vollständigen Validierung aus.

### FIGMA-Blockmigration {#figma-block-migration}

Verwenden Sie diese Eingabeaufforderung, um einen Baustein von Figma Design nach Edge Delivery Services zu migrieren.

Beachten Sie, dass Sie Ihre Figma-Details in [Experience Modernization Console](/help/ai-in-aem/agents/brand-experience/modernization/console.md) einrichten müssen, um diese Eingabeaufforderung zu verwenden.

#### Beispiel-Eingabeaufforderungen {#example-figma}

* „Migrieren des `https://figma.com/design/{fileKey}?node-id={nodeId}` nach Edge Delivery Services&quot;
* „Migrieren von `{blockName}` von `https://figma.com/file/{fileKey}` nach Edge Delivery Services&quot;

#### Was Sie wissen sollten {#wtk-figma}

* Diese Fähigkeit migriert einen Block nach dem anderen, nicht ganze Seiten oder vollständige Figma-Dateien.
* Für optimale Ergebnisse:
   * Wählen Sie den spezifischen Block aus, den Sie in Figma migrieren möchten, und kopieren Sie seinen Link (mit `node-id`) oder Namen.
   * Geben Sie in der URL den `node-id` an, um den genauen Block auszuwählen.
* Wenn Sie diese Fähigkeit ausführen, werden die folgenden Schritte automatisch in der gehosteten Umgebung ausgeführt:
   1. **Blockstrukturerkennung** - Der Agent liest den Figma-Knoten, um Ebenen und Komponenten zu verstehen.
   1. **Globale Stilextraktion** - Der Agent zieht Farben, Typografie und Abstände in `styles/styles.css` als benutzerdefinierte CSS-Eigenschaften (Design-Token) ein.
   1. **Blockspezifische Stilerstellung** - Der Agent erstellt zusätzliche benutzerdefinierte CSS-Eigenschaften, die für den migrierten Block spezifisch sind.
   1. **Zuordnung zu vorhandenen Blöcken** - Der Agent identifiziert den Block in der Blockbibliothek Ihres Projekts, der am ehesten damit übereinstimmt, und erstellt eine benutzerdefinierte Variante.
   1. **CSS-Generierung** - Der Agent schreibt Stile, die auf die extrahierten benutzerdefinierten CSS-Eigenschaften verweisen, und stellt so die Konsistenz des Designs sicher.
   1. **Asset-**: Der Agent speichert Bilder und Symbole aus Figma im Arbeitsbereich der gehosteten Umgebung.
   1. **Edge Delivery Services-Inhaltserstellung** - Der Agent erstellt die Markdown-Datei entsprechend der EDS-Blockstruktur
   1. **Ausgabevalidierung** - Der Agent zeigt eine Vorschau des Ergebnisses an und führt einen visuellen Vergleich mit dem ursprünglichen Figma-Design durch.
* Die Kenntnis liest zunächst Metadaten (Schritt 1), um die Struktur zu verstehen, und extrahiert dann einen detaillierten Design-Kontext (Schritte 2-5).
   * Dieser stufenweise Ansatz verhindert Probleme mit großen oder komplexen Figma-Dateien.
* Diese Fähigkeit verwendet einen Ansatz, bei dem Stile Vorrang haben.
   * Alle Stile werden als benutzerdefinierte CSS-Eigenschaften (Design-Token) extrahiert, bevor CSS geschrieben wird.
   * Dadurch wird sichergestellt, dass der migrierte Block konsistent mit Ihrem Design-System bleibt.
* Die Eingabeaufforderung erfordert die Figma-URL (mit `fileKey` und optionalem `node-id`) oder einen Figma-Dateischlüssel direkt als Eingabe.

### Navigations-Setup {#navigation-setup}

Verwenden Sie diese Eingabeaufforderung, um die Site-Navigation einzurichten oder zu migrieren.

#### Beispiel-Eingabeaufforderungen {#example-navigation}

* „Einrichten der Navigation von `https://example.com` aus“
* „Reparieren des Navigationsmenüs“

#### Was Sie wissen sollten {#wtk-navigation}

* Die Edge Delivery Services-Navigation erzwingt eine Struktur mit drei Abschnitten (erzwungen von `header.js`):
   1. **Marke** (Abschnitt 1): Logo und primärer Branding-Link
   1. **Abschnitte** (Abschnitt 2): Hauptnavigationsmenü mit optionalen Dropdown-Listen
   1. **Tools** (Abschnitt 3): Link zu Dienstprogrammen (abonnieren, anmelden, Warenkorb)
* Der Navigationsinhalt ist in `nav.md` im Stammverzeichnis vorhanden.
* Abschnitte werden durch (`---`) -Markierungen getrennt.
* Fett gedruckte Elemente (`**Text**`) mit verschachtelten Listen erstellen Dropdown-Listen.
* Links in der Navigation werden aufgrund des automatischen Umbruchs bei der Dokumenterstellung möglicherweise als Schaltflächen gerendert.
   * Der Kopfzeilenblock enthält Code zum Entfernen von Schaltflächenklassen von Navigations-Links.

## Blockentwicklungsfunktionen {#block-development-capabilities}

Diese Eingabeaufforderungen werden für die Erstellung und Weiterentwicklung von Blöcken verwendet, die einen kontinuierlichen Wert über die anfängliche Site-Erstellung oder -Migration hinaus bieten.

### Blockentwicklung {#block-development}

Verwenden Sie diese Eingabeaufforderung, um neue Blöcke zu erstellen oder vorhandene zu ändern.

#### Beispiel-Eingabeaufforderungen {#example-block-development}

* „Erstellen eines Blocks für Empfehlungen“
* „Dem Hero-Block eine Video-Hintergrundvariante hinzufügen“

#### Was Sie wissen sollten {#wtk-block-development}

* Der Agent folgt der Content-Driven Development (CDD), einem obligatorischen Prozess für die gesamte Edge Delivery Services-Entwicklung.
   * Vor dem Schreiben von Code werden Fragen zu Inhaltsmodellen gestellt und Inhalte getestet.
* Die Philosophie der CDD besteht darin, dass der Autor vor dem Entwickler kommen muss.
   * Inhaltsmodelle müssen für Autoren intuitiv sein, auch wenn dies komplexeren Dekorations-Code bedeutet.
* Das Erstellen von Testinhalten bietet zunächst:
   * Sofortige Testfunktion
   * PR-Validierungs-Links für PSI-Prüfungen
   * Living-Dokumentation für Autoren
   * Erkennung von Edge-Fällen, die bei Code-First-Ansätzen verpasst werden
* Der Agent sucht vor der Implementierung nach ähnlichen Blöcken in [Blocksammlung](https://www.aem.live/developer/block-collection) und [Blockpartei](https://www.aem.live/developer/block-party/), um Muster und wiederverwendbaren Code zu finden.
* Nur CDD für triviale CSS-basierte Anpassungen überspringen (aber dennoch Testinhalte für die Validierung identifizieren).

### Inhaltsmodellierung {#content-modeling}

Verwenden Sie diese Eingabeaufforderung, um die Tabellenstruktur zu entwerfen, mit der Autoren beim Erstellen von Blockinhalten arbeiten.

#### Beispiel-Eingabeaufforderungen {#example-modeling}

* „Gestalten eines Inhaltsmodells für einen Bericht-Block“
* „Was ist das beste Inhaltsmodell für dieses Karussell?“

#### Was Sie wissen sollten {#wtk-modeling}

* Edge Delivery Services verfügt über vier kanonische Modelltypen:
   * **Eigenständig:** Unterschiedliche visuelle/erzählerische Elemente (Held, Blockquote)
      * Einzelne Tabelle mit Blockinhalt
   * **Sammlung** Wiederholen von teilweise strukturierten Inhalten (Karten, Karussell)
      * Tabelle mit sich wiederholendem Zeilenmuster
   * **Konfiguration:** API-gesteuerte oder dynamische Inhalte, in denen Konfigurationssteuerelemente angezeigt werden (Blog-Auflistung, Suchergebnisse)
      * Tabelle mit Schlüssel-Wert-Konfigurationszeilen.
   * **Automatisch blockiert:** Komplexe Strukturen, die Autorinnen und Autoren als Abschnitte/Standardinhalte erstellen und dann transformiert werden (Registerkarten, YouTube-Einbettungen)
* Pro Zeile sind maximal vier Zellen zulässig.
   * Gruppieren verwandter Elemente in Zellen.
* Aus Gründen der Formatierungsunterschiede sollten Blockvarianten gegenüber Konfigurationszellen bevorzugt werden.
* [Befolgen Sie das Postel&#39;](https://en.wikipedia.org/wiki/Robustness_principle)-Gesetz: Seien Sie flexibel bei der Eingabestruktur.
   * Ein Hero-Block sollte unabhängig davon funktionieren, ob sich der Inhalt in einer Zelle, auf zwei Zellen oder in separaten Zeilen befindet.
* Diese Fähigkeit wird in der Regel automatisch durch die inhaltsgesteuerte Entwicklung während der Blockerstellung aufgerufen.

### Suchen nach Referenzblöcken {#reference-blocks}

Verwenden Sie diese Eingabeaufforderung, um nach vorhandenen Implementierungen zu suchen, die als Ausgangspunkte verwendet werden können.

#### Beispiel-Eingabeaufforderungen {#example-reference}

* „Suchen von Blöcken, die einer Preistabelle ähneln“
* „Welche Blöcke stehen für Testimonials zur Verfügung?“
* „Block-Party nach einer Registerkarten-Implementierung durchsuchen“

#### Was Sie wissen sollten {#wtk-reference}

* Die [Blocksammlung](https://www.aem.live/developer/block-collection) wird von Adobe gepflegt und auf Best Practices, hervorragende Inhaltsmodellierung, hohe Leistung und Barrierefreiheit hin überprüft.
   * Es ist auf häufig benötigte Blöcke beschränkt. Beginnen Sie hier.
* Die [Block Party](https://www.aem.live/developer/block-party/) ist gemeinschaftsorientiert und bietet eine größere Vielfalt einschließlich experimenteller Ansätze.
   * Es enthält auch Sidekick-Plug-ins, Build-Tools (webpack, Vite, Sass) und Integrationen.
   * Verwenden Sie diese Option, wenn die Blocksammlung nicht das enthält, was Sie benötigen.
* Denken Sie bei der Suche an alternative Namen.
   * FAQ = Akkordeon
   * Galerie = Karussell/Diashow
   * Navigation = Menü/Kopfzeile
* Die Blockpartei gibt nur genehmigte/kuratierte Einträge zurück.

### Dokumentation durchsuchen {#searching-documentation}

In dieser Eingabeaufforderung finden Sie Informationen zu Edge Delivery Services-Funktionen oder Implementierungshandbüchern.

#### Beispiel-Eingabeaufforderungen {#example-documentation}

* „Wie implementiere ich verzögertes Laden in Edge Delivery Services?“
* „Dokumente nach Abschnittsmetadaten durchsuchen“

#### Was Sie wissen sollten {#wtk-documentation}

* Es durchsucht speziell die [aem.live](https://aem.live)-Dokumentation (Dokumente und Blog-Posts).
* Verwenden Sie bestimmte Keywords („Blockdekoration“, „Sidekick-Plug-in“, „Metadaten„) anstelle von generischen Begriffen („aem“, „Website“, „Wie man erstellt„).
* Verwenden Sie für Code-Beispiele und Referenzimplementierungen stattdessen „Referenzblöcke suchen“.
* Die zehn wichtigsten Ergebnisse, die standardmäßig zurückgegeben werden.

### Testen {#testing}

Verwenden Sie diese Eingabeaufforderung, um Code-Änderungen zu validieren, bevor Sie eine Pull-Anfrage öffnen.

#### Beispiel-Eingabeaufforderungen {#example-testing}

* „Testen des neuen Kartenblocks“
* „Führen Sie die Tests durch, bevor ich einen PR öffne“

#### Was Sie wissen sollten {#wtk-testing}

* Tests folgen der Philosophie „Wert vs. Kosten“, nach der Sie Tests erstellen und verwalten, wenn ihr Wert die Kosten überschreitet.
   * **Keeper-Tests** (Unit-Tests) sind für logiklastige Dienstprogramme, Datenverarbeitung und API-Integrationen bestimmt. Diese sind schnell, einfach zu pflegen und erfassen Regressionen im wiederverwendeten Code.
   * **Wegwerftests** (Browser-Tests) dienen zur DOM-Transformation und visuellen Validierung. Verwenden Sie , um die Implementierung zu validieren, Screenshots zur PR-Überprüfung zu erfassen und dann zu verwerfen.
* Wegwerftests werden `test/tmp/` und Testinhalte in `drafts/tmp/` (beide werden ignoriert).
* Stellen Sie vor dem Öffnen eines PR Folgendes sicher:
   * Bestehende Tests erfolgreich
   * Modultests werden für neue Logik geschrieben
   * Browser-Validierung abgeschlossen
   * Alle Varianten werden getestet
   * Responsives Verhalten ist verifiziert
   * Linting Pässe

### Debugging {#debugging}

Verwenden Sie diese Eingabeaufforderung, um Probleme mit Blöcken, Bildern, CSS oder der Vorschau zu beheben.

#### Beispiel-Eingabeaufforderungen {#example-debugging}

* „Debuggen, warum Bilder als „about“ angezeigt :error&quot;
* „Beheben, dass der Hero-Block nicht gerendert wird“
* „Warum werden meine Änderungen nicht in der Vorschau angezeigt?“

#### Was Sie wissen sollten {#wtk-debugging}

* Häufige Probleme weisen bekannte Muster auf:
   * **Bilder mit „about:error&quot;**: Fehlt normalerweise `createOptimizedPicture` Aufruf in Block JS oder wird vor der DOM-Umstrukturierung aufgerufen
   * **Blöcke werden nicht gerendert**: Überprüfen Sie das Blocknamenformat im Markdown und stellen Sie sicher, dass der Block sowohl `.js`- als auch `.css`-Dateien in `blocks/` hat.
   * **CSS wird nicht geladen**: Überprüfen Sie die Dateipfade, ob die CSS-Datei vorhanden ist, und überprüfen Sie die Registerkarte „Netzwerk“ im Browser.
   * **Änderungen werden nicht angezeigt**: Die Codesynchronisierung dauert 3-5 Sekunden. Versuchen Sie, die Seite zu aktualisieren (Strg+Umschalt+R).
* Der Agent prüft jede Ebene systematisch:
   1. Source-Dateien
   1. Gerenderte Ausgabe
   1. Blockcode
   1. Browser-Konsole
* Der Agent hat die Möglichkeit, lokale Vorschauen auf `http://localhost:3000` zu überprüfen.
