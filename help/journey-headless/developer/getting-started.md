---
title: Erste Schritte mit AEM Headless als Cloud Service
description: In diesem Teil der AEM Headless-Entwickler-Journey erfahren Sie mehr über AEM Headless-Voraussetzungen.
source-git-commit: 8e96827f9353d6ffdf1e01645f2bc8bdaac2610f
workflow-type: tm+mt
source-wordcount: '3059'
ht-degree: 5%

---

# Erste Schritte mit AEM Headless als Cloud Service {#getting-started}

In diesem Teil der [AEM Headless-Entwickler-Journey,](overview.md) erfahren Sie, was erforderlich ist, um Ihr eigenes Projekt mit AEM Headless zu starten.

## Die Geschichte bisher {#story-so-far}

Im vorherigen Dokument der AEM Headless-Journey, [Informationen zur Headless-Entwicklung von CMS](learn-about.md) haben Sie die grundlegende Theorie gelernt, was ein Headless-CMS ist und sollten jetzt:

* Grundlegende Konzepte und Terminologie der Bereitstellung Headless Content
* Verstehen, warum und wann Headless erforderlich ist
* Erfahren Sie auf hoher Ebene, wie Headless-Konzepte verwendet werden und wie sie miteinander verknüpft sind

Dieser Artikel baut auf diesen Grundlagen auf, sodass Sie verstehen, wie Sie AEM verwenden können, um eine Headless-Lösung zu implementieren.

## Vorgabe {#objective}

Dieses Dokument hilft Ihnen, AEM Headless im Kontext Ihres eigenen Projekts zu verstehen. Nach dem Lesen sollten Sie:

* Machen Sie sich mit den Grundlagen AEM Headless-Funktionen vertraut.
* Machen Sie sich mit den Voraussetzungen für die Verwendung AEM Headless-Funktionen vertraut.
* Beachten Sie AEM Headless-Integrationsstufen.
* Sie können Ihr Projekt in Bezug auf den Umfang definieren.

## AEM Grundlagen {#aem-basics}

Bevor Sie Ihr Headless-Projekt in AEM definieren können, müssen Sie einige grundlegende AEM verstehen.

### Autoreninstanz {#author}

Am einfachsten besteht AEM aus einer Autoreninstanz und einer [Veröffentlichungsinstanz](#publish), die zusammenarbeiten, um Inhalte zu erstellen, zu verwalten und zu veröffentlichen.

Der Inhalt beginnt in der Autoreninstanz. Hier erstellen Ihre Inhaltsautoren ihren Inhalt. Die Autorenumgebung bietet verschiedene Tools für Autoren zum Erstellen, Organisieren und Wiederverwenden ihrer Inhalte.

### Veröffentlichungsinstanz {#publish}

Nachdem Inhalte in der Autoreninstanz erstellt wurden, müssen sie veröffentlicht werden, damit sie für andere Dienste verfügbar sind. Eine Veröffentlichungsinstanz enthält alle veröffentlichten Inhalte.

### Replikation {#replication}

Die Replikation ist der Vorgang der Übertragung von Inhalten von der Autoreninstanz auf die Veröffentlichungsinstanz. Dies erfolgt automatisch durch AEM, wenn ein Autor oder ein anderer Benutzer mit entsprechenden Berechtigungen Inhalte veröffentlicht.

### AEM Grundlagen Zusammenfassung {#aem-basics-summary}

Auf der einfachsten Ebene erfordert das Erstellen digitaler Erlebnisse in AEM die folgenden Schritte:

1. Ihre Inhaltsautoren erstellen Ihren Headless-Inhalt in der Autoreninstanz.
1. Wenn dieser Inhalt fertig ist, wird er auf die Veröffentlichungsinstanz repliziert.
1. Anschließend können APIs aufgerufen werden, um diesen Inhalt abzurufen.

AEM Headless baut auf dieser technischen Grundlage auf, indem leistungsstarke Tools zum Verwalten von Headless-Inhalten bereitgestellt werden, die im nächsten Abschnitt beschrieben werden.](#aem-headless-basics)[

## AEM Headless-Grundlagen {#aem-headless-basics}

Die Headless-Funktionen von AEM basieren auf einigen wichtigen Funktionen. Diese werden in späteren Teilen der Journey ausführlich erläutert. Es ist jetzt wichtig, nur die Grundlagen zu kennen, was sie tun und wie sie genannt werden.

### Inhaltsfragmentmodelle {#content-fragment-models}

Inhaltsfragmentmodelle definieren die Struktur der Daten und Inhalte, die Sie in AEM erstellen und verwalten. Sie dienen als Gerüst für Ihre Inhalte. Bei der Erstellung von Inhalten wählen Ihre Autoren aus den von Ihnen definierten Inhaltsfragmentmodellen aus, die sie bei der Erstellung von Inhalten anleiten.

### Inhaltsfragmente {#content-fragments}

Inhaltsfragmente ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Verwenden von seitenunabhängigen Inhalten. Außerdem können Sie Inhalte zur Verwendung an mehreren Orten und über mehrere Kanäle hinweg vorbereiten.

Inhaltsfragmente enthalten strukturierten Inhalt und können im JSON-Format bereitgestellt werden.

### GraphQL- und REST-APIs {#apis}

Um Inhalte Headless zu ändern, bietet AEM zwei robuste APIs.

* Mit der GraphQL-API können Sie Anfragen für den Zugriff auf und die Bereitstellung von Inhaltsfragmenten erstellen.
* Mit der Assets-REST-API können Sie Inhaltsfragmente (und andere Assets) erstellen und ändern.

Sie erfahren mehr über diese APIs und deren Verwendung in einem späteren Teil der Journey ohne Kopfzeilenfunktion AEM. Weitere Informationen finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) weiter unten.

## Headless-Integrationsstufen {#integration-levels}

AEM unterstützt sowohl den kompletten Headless- als auch den herkömmlichen Full Stack oder Headful-Modelle eines CMS. AEM bietet jedoch nicht nur diese beiden exklusiven Optionen, sondern auch die Möglichkeit, Hybridmodelle zu unterstützen, die die Vorteile beider Modelle kombinieren und Ihnen eine einzigartige Flexibilität für Ihr Headless-Projekt bieten.

Um Ihr Verständnis von Headless-Konzepten sicherzustellen, konzentriert sich dieses AEM Headless-Entwickler-Journey auf das reine Headless-Modell, um Sie so schnell wie möglich ohne Programmierung in AEM zum Laufen zu bringen.

Sie sollten sich jedoch der zusätzlichen Hybridmöglichkeiten bewusst sein, die Ihnen zur Verfügung stehen, sobald Sie AEM Headless-Funktionen verstehen. Wir legen diese Fälle für Ihr Bewusstsein weiter unten. Am Ende der Journey werden Sie detaillierter zu diesen Konzepten vorgestellt, falls eine solche Flexibilität für Ihr Projekt erforderlich ist.

### Sie verfügen bereits über einen externen Verbrauch von Headless-Inhalten, wie z. B. eine Einzelseitenanwendung (SPA). {#already-have-a-spa}

Nehmen wir einmal an, dass Ihre Grundanforderung mindestens darin besteht, Inhalte von AEM an einen bestehenden externen Dienst zu senden.

#### Ebene 1: Integration von Inhaltsfragmenten - Herkömmliches Headless-Modell {#level-1}

Diese Integrationsstufe ist das herkömmliche Headless-Modell und ermöglicht es Ihren Inhaltsautoren, Inhalte in AEM zu erstellen und diese mithilfe von GraphQL für eine beliebige Anzahl externer Dienste bereitzustellen oder mithilfe der Assets-API über externe Dienste zu bearbeiten. In AEM ist keine Kodierung erforderlich.

In diesem Modell wird AEM nur zum Erstellen und Bereitstellen des Inhalts mithilfe von AEM Inhaltsfragmenten verwendet. Rendering und Interaktion mit dem Inhalt werden an die nutzende externe Anwendung delegiert, häufig an eine Einzelseitenanwendung (SPA).

#### Ebene 2: Einbetten des SPA in AEM - Hybridmodell {#level-2}

Diese Integrationsstufe baut auf der ersten Ebene auf, ermöglicht jedoch auch die Einbettung der externen Anwendung (SPA) in AEM, sodass die Inhaltsautoren den Inhalt im Kontext der externen Anwendung in AEM anzeigen können. Die Anwendung kann auch eine eingeschränkte Bearbeitung der externen Anwendung in AEM unterstützen.

Diese Ebene bietet den Vorteil, dass Autoren von Inhalten Inhalte in AEM dynamisch erstellen können, wobei ihre Inhalte kontextbezogen mit einer eingebetteten externen SPA präsentiert werden, während sie die Inhalte dennoch Headless bereitstellen.

#### Ebene 3: Einbetten und vollständige Aktivierung von SPA in AEM - Hybridmodell {#level-3}

Diese Integrationsstufe baut auf Stufe zwei auf, indem die meisten Inhalte in der externen SPA innerhalb von AEM bearbeitbar sind.

### Sie haben noch keinen externen Benutzer des Headless-Inhalts, z. B. eine Single Page Application (SPA). {#do-not-have-a-spa}

Wenn Sie ein neues SPA erstellen möchten, das Inhalte von AEM nutzlos nutzt, können Sie Funktionen wie Inhaltsfragmente verwenden, um Ihre Headless-Inhalte zu verwalten, und auch eine SPA mit AEM Editor-Framework erstellen.

Mit dem SPA-Editor nutzt die SPA nicht nur Inhalte aus AEM, sondern ist auch AEM von Ihren Inhaltsautoren vollständig bearbeitbar, sodass Sie sowohl die Flexibilität der Headless-Bereitstellung als auch der kontextbezogenen Bearbeitung innerhalb AEM haben.

## Anforderungen und Voraussetzungen {#requirements-prerequisites}

Bevor Sie mit Ihrem Headless-AEM-Projekt beginnen, müssen Sie eine Reihe von Anforderungen erfüllen.

### Wissen {#knowledge}

* GraphQL
* Entwicklungs-Erlebnis beim Erstellen von SPA mit React- oder Angular-Frameworks
* Grundlegende AEM beim Erstellen von Inhaltsfragmenten und Verwenden des Editors

### Tools {#tools}

* Sandbox-Zugriff zum Testen der Bereitstellung Ihres Projekts
* Lokale Entwicklungsinstanz für Datenmodellierung und -tests
* Bestehende externe SPA oder andere Verbraucher Ihres Headless-AEM-Inhalts

## Definieren Ihres Projekts {#defining-your-project}

Für ein erfolgreiches Projekt ist es wichtig, nicht nur die Anforderungen des Projekts, sondern auch die Rollen und Verantwortlichkeiten klar zu definieren.

### Anwendungsbereich {#scope}

Es ist sehr wichtig, einen klar definierten Umfang für das Projekt zu haben. Der Umfang informiert über die Akzeptanzkriterien und ermöglicht es Ihnen, eine Definition des Erfüllten zu erstellen.

Die erste Frage, die Sie sich stellen müssen, lautet: &quot;Was versuche ich mit AEM Headless zu erreichen?&quot; Die Antwort sollte im Allgemeinen sein, dass Sie eine Erlebnisanwendung haben oder in Zukunft haben werden, die Sie mit Ihren eigenen Entwicklungs-Tools erstellt haben, nicht in Verbindung mit AEM. Bei dieser Erlebnisanwendung kann es sich um eine mobile App, eine Website oder eine andere Erlebnisanwendung für Endbenutzer handeln. Das Ziel der Verwendung von AEM Headless besteht darin, Ihre Erlebnisanwendung mit Inhalten zu versorgen, die in AEM erstellt, gespeichert und verwaltet werden, mit hochmodernen APIs, die AEM Headless aufrufen, um Inhalte oder sogar vollständig CRUD-Inhalte direkt aus Ihrer Erlebnisanwendung abzurufen. Wenn dies nicht das ist, was Sie tun möchten, sollten Sie [zurück zur AEM Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de) gehen und den Abschnitt finden, der besser zu dem passt, was Sie erreichen möchten.

### Rollen und Zuständigkeiten {#roles-responsibilities}

Die Rollen für jedes einzelne Projekt variieren, aber wichtige Aspekte, die im Inhalt AEM Headless-Entwicklung zu berücksichtigen sind, sind:

* [Administrator](#administrator)
* [Inhaltsautor](#content-author)
* [Inhaltsmodellierung](#content-modeler)
* [Entwickler](#developer)

#### Administrator {#administrator}

Der Administrator ist für die Basiseinrichtung und -konfiguration Ihres Systems verantwortlich. Beispielsweise richtet der Administrator Ihr Unternehmen im User Management-System der Adobe ein, auf das Identity Management System (IMS) verwiesen wird. Der Administrator ist der erste Benutzer des Unternehmens, der eine Einladung per E-Mail von Adobe erhält, sobald Ihre Organisation von Adobe in IMS erstellt wurde. Der Administrator kann sich bei IMS anmelden und Benutzer anderer Personen hinzufügen.

Sobald die Benutzer vom Administrator konfiguriert wurden, erhalten sie die Berechtigungen für den Zugriff auf alle AEM Ressourcen, um ihre Arbeit als Beitragende für die Bereitstellung der Erlebnisanwendung mit AEM Headless durchzuführen.

Der Administrator sollte der Benutzer sein, der AEM eingerichtet und die Laufzeitumgebung vorbereitet, damit [Inhaltsautoren](#content-author) Inhalte erstellen und aktualisieren können und [Entwickler](#developer) APIs verwenden können, die Inhalte für ihre Erlebnisanwendungen abrufen oder ändern.

#### Inhaltsautor {#content-author}

Inhaltsautoren erstellen und verwalten die Inhalte, die von AEM Headless bereitgestellt werden. Inhaltsautoren verwenden AEM Funktionen wie Inhaltsfragmente und die Konsole &quot;Assets&quot;, um ihren Inhalt zu verwalten.

Inhaltsautoren sollten die folgenden Best Practices beachten.

#### Lokalisierungsplan {#localization}

Planen Sie die Übersetzung und Lokalisierung am Anfang des Projekts. Betrachten Sie &quot;Internationalisierungs-Projektmanager&quot;als eine separate Person, deren Aufgabe es ist zu definieren, welche Inhalte übersetzt werden sollen und welche nicht und welche übersetzten Inhalte von regionalen oder lokalen Inhaltserstellern geändert werden können.

Erstellen Sie einen Plan zur benötigten Lokalisierung von Inhalten.

* Benötigen Sie nur verschiedene Sprachen oder auch Sprachen, um regionale Besonderheiten zu übernehmen?
* Benötigen Sie Rich-Media-Inhalte wie Bilder oder Videos, damit sie sich von Land zu Land unterscheiden?

Machen Sie sich mit Ihrem Inhaltsaktualisierungs-Workflow vertraut. Was ist der Genehmigungsprozess, den das System unterstützen muss? Können AEM Workflows genutzt werden, um diesen Prozess zu automatisieren?

Beachten Sie, dass Ihre [Inhaltshierarchie](#content-hierarchy) genutzt werden kann, um die Lokalisierung zu vereinfachen.

Weitere Informationen zu AEM Workflows und Lokalisierungs-Tools finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) .

##### Verwenden der Inhaltshierarchie {#content-hierarchy}

Die Ordnerhierarchie kann zwei wesentliche Probleme im Zusammenhang mit dem Content Management lösen:

* [Lokalisierung](#localization)  - AEM verwaltet die Lokalisierung von Inhalten, indem Kopien von Inhalten in gebietsschemaspezifischen Ordnern verwaltet werden.
* Organisation - Ordner werden verwendet, um eine Inhaltshierarchie zu definieren, die zur Unterstützung der Lokalisierungsanforderungen sowie zur logischen Verwaltung von Inhaltsfragmenten erforderlich ist.

AEM ermöglicht eine sehr flexible Inhaltsstruktur und eine Hierarchie kann beliebig groß sein. Es ist jedoch wichtig zu erkennen, dass Änderungen an der Ordnerstruktur unbeabsichtigte Folgen für bestehende Abfragen haben können, die [auf den Inhaltspfad angewiesen sind.](#developer) Daher kann eine klar definierte Hierarchie, die im Voraus festgelegt ist, für Ihre Inhaltsautoren äußerst hilfreich sein.

Ordner können auch darauf beschränkt werden, nur bestimmte Inhaltstypen zuzulassen (basierend auf Inhaltsfragmentmodellen). Es wird allgemein empfohlen, immer explizit anzugeben, welche Modelle für alle Ordner in der Hierarchie zulässig sind. Zulässige Inhalte für einen bestimmten Ordner angeben:

* Verhindert, dass Inhaltsautoren Inhalte erstellen, die nicht zum Ordner gehören.
* Optimiert den Inhaltserstellungsprozess, indem die Inhaltstypen gefiltert werden, die im Ordner während der Erstellung zulässig sind, sodass nur gültige Inhaltstypen angezeigt werden.

Durch die Erstellung einer geeigneten Inhaltsstruktur wird es einfacher, das Headless-Content-Authoring kanalübergreifend zu koordinieren, um die Wiederverwendung von Inhalten zu maximieren. Durch die Nutzung von Inhalten über mehrere Kanäle wird die Effizienz der Inhaltserstellung und das Änderungsmanagement erheblich verbessert.

##### Einrichten guter Benennungskonventionen {#naming-conventions}

Inhaltsfragmentnamen müssen für Inhaltsautoren beschreibend sein. AEM behandelt das Escapen und/oder Abschneiden der verwendeten IDs auf Repository-Ebene transparent. Daher sollten die von den Inhaltsautoren bereitgestellten logischen Namen immer lesbar sein und den Inhalt darstellen.

* Unangemessener Name: `cta_btn_1`
* Guten Namen: `Call To Action Button`

Weitere Informationen zu AEM Seitenbenennungskonventionen finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) .

##### Nicht überschreiben Inhalt verschachteln {#content-nesting}

[Inhaltsfragmente ](#content-fragments) werden in AEM verwendet, um Headless-Inhalte zu erstellen. AEM unterstützt bis zu zehn Verschachtelungsebenen von Inhalten für Inhaltsfragmente. Beachten Sie jedoch, dass AEM alle im übergeordneten Inhaltsfragment definierten Verweise iterativ auflösen und dann überprüfen müssen, ob in allen gleichrangigen Elementen untergeordnete Verweise vorhanden sind. Diese Vorgänge können sich schnell addieren und zu einem Leistungsproblem werden.

Als allgemeine Faustregel gilt, dass Inhaltsfragmentverweise nicht über fünf Ebenen verschachtelt werden sollten.

#### Inhaltsmodellierung {#content-modeler}

Inhaltsmodellierer analysieren die Anforderungen an die Daten, die Headless-Bereitstellung erfordern, und definieren die Struktur für diese Daten. Diese Strukturen werden in AEM [Inhaltsfragmentmodelle](#content-fragment-models) genannt. Inhaltsfragmentmodelle werden als Grundlage für die Inhaltsfragmente verwendet, die die Inhaltsautoren erstellen.

Ein nützlicher Ansatz bei der Definition von Inhaltsfragmentmodellen besteht darin, Modelle zu erstellen, die den UX-Komponenten der Anwendungen zugeordnet sind, die den Inhalt nutzen.

Da die Inhaltsautoren bei der Erstellung neuer Inhalte kontinuierlich mit den Modellen interagieren, hilft ihnen die Ausrichtung der Modelle an der UX dabei, das daraus resultierende digitale Erlebnis zu visualisieren. Wenn Sie diese Ausrichtung weiter vorantreiben, können Sie den Inhaltsfragmentmodellen, die das UX-Element darstellen, Symbole zuweisen, damit die Autoren anhand visueller Hinweise intuitiv das richtige Modell auswählen können.

#### Entwickler {#developer}

Entwickler sind dafür verantwortlich, die Inhalte, die direkt erstellt werden, AEM für den Verbraucher dieser Inhalte zusammenzuführen. Dabei kann es sich häufig um eine Einzelseiten-App (SPA), eine progressive Web-App (PWA), einen Webshop oder einen anderen AEM externen Dienst handeln.

GraphQL dient als &quot;Kleber&quot;zwischen AEM und den Verbrauchern von Headless Content. GraphQL ist die Sprache, in der Abfragen für den erforderlichen Inhalt AEM.

Entwickler sollten bei der Planung ihrer Abfragen einige grundlegende Empfehlungen beachten:

* Bei Abfragen sollte kein fester Pfad (`ByPath`) zum Abrufen von Inhaltsfragmenten verwendet werden.
   * [Inhaltsautoren haben vollständige Kontrolle über die ](#content-hierarchy) Hierarchie von Inhaltsfragmenten und können Änderungen vornehmen, die eine solche Abfrage unterbrechen würden.
   * Bei Abfragen sollten stattdessen Inhaltsfragmentmodellverweise mit dynamischen Abfrageparametern verwendet werden, um die Ergebnisse zu filtern und die gewünschte Payload zu generieren.
* Verwenden Sie für eine optimale Abfrageleistung immer persistente Abfragen in AEM. Diese werden später im Journey erläutert.
* GraphQL ist deklarativ und folgt dem Motto &quot;Fragen Sie genau, was Sie benötigen und erhalten Sie genau das.&quot; Dies bedeutet, dass Sie beim Erstellen von GraphQL-Abfragen immer `select *`-Abfragen vermeiden, die Sie möglicherweise in einer relationalen Datenbank erstellen.

Für eine [typische Headless-Implementierung mit AEM,](#level-1) benötigt der Entwickler keine Programmierkenntnisse zu AEM.

### Leistungsanforderungen {#performance-requirements}

Damit ein Projekt erfolgreich ist, muss die Leistung berücksichtigt werden, bevor Inhalte erstellt werden.

Sie müssen die Erwartungen Ihrer Benutzer/Besucher und deren Design verstehen. Legen Sie Service-Level-Ziele (SLOs) fest und messen Sie sie, um zu verstehen, ob Sie die Erwartungen Ihrer Benutzer erfüllen.

#### Traffic-Muster {#traffic-patterns}

Um Traffic- und Traffic-Muster zu verstehen, beginnen Sie damit, das zu erfassen, was Sie aus der Vergangenheit kennen, und projizieren Sie dann in den nächsten Jahren das erwartete Wachstum. Zu beachten sind einige der wichtigsten Variablen:

* Wie viele API-Aufrufe pro Stunde/Tag/Monat erwarten Sie und besteht ein Potenzial für Spitzen und Saisonabhängigkeit?
* Wie viele verschiedene Inhaltsautoren gibt es?
* Wie viele Inhaltsautoren erwarten Sie, dass sie gleichzeitig arbeiten?
* Wie häufig werden Inhaltsaktualisierungen vorgenommen?
* Wie viele Inhaltsmodelle werden benötigt?
* Wie viele Instanzen von Modellen werden benötigt?

#### Aktualisierungshäufigkeit {#update-frequency}

Oft gibt es bei verschiedenen Bereichen von Erlebnissen unterschiedliche Häufigkeit von Inhaltsaktualisierungen. Um CDN- und Cache-Konfigurationen optimieren zu können, ist es wichtig, dies zu verstehen. Dies ist auch für die [Inhaltsmodelle](#content-modeler) wichtig, da sie Modelle zur Darstellung Ihres Inhalts entwerfen. Beachten Sie:

* Müssen bestimmte Inhaltstypen nach einem bestimmten Zeitraum ablaufen?
* Gibt es Elemente, die benutzerspezifisch sind und daher nicht zwischengespeichert werden können?

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der AEM Headless-Entwickler-Journey abgeschlossen haben, sollten Sie:

* Machen Sie sich mit den Grundlagen AEM Headless-Funktionen vertraut.
* Machen Sie sich mit den Voraussetzungen für die Verwendung AEM Headless-Funktionen vertraut.
* Beachten Sie AEM Headless-Integrationsstufen.
* Sie können Ihr Projekt in Bezug auf den Umfang definieren.

Sie sollten Ihre AEM Headless-Journey fortsetzen, indem Sie sich das Dokument [Pfad zu Ihrem Erlebnis mit AEM Headless](path-to-first-experience.md) ansehen. Hier erfahren Sie, wie Sie die erforderlichen Tools einrichten und mit der Modellierung Ihrer Daten in AEM beginnen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, zum nächsten Teil der Headless-Development-Journey zu wechseln, indem Sie das Dokument [Pfad zu Ihrem ersten Erlebnis mit AEM Headless,](path-to-first-experience.md) lesen. Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige in diesem Dokument erwähnte Konzepte vertiefen. Sie müssen jedoch nicht mit der Headless-Journey weitermachen.

* [Einführung in die Architektur von Adobe Experience Manager as a Cloud Service](/help/core-concepts/architecture.md)  - Grundlegendes zur AEM als Cloud Service-Struktur
* [AEM Headless-Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de)  - Nutzen Sie diese praxisnahen Tutorials, um zu untersuchen, wie Sie die verschiedenen Optionen für die Bereitstellung von Inhalten an Headless-Endpunkte mit AEM nutzen können, und wählen Sie aus, was für Sie am besten geeignet ist.
* [Headless Content Management mit GraphQL-APIs](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses)  - In diesem Kurs erhalten Sie einen Überblick über die in AEM implementierte GraphQL-API. Eine Authentifizierung über Adobe ID ist erforderlich.
* [AEM Guides WKND - GraphQL](https://github.com/adobe/aem-guides-wknd-graphql)  - Dieses GitHub-Projekt enthält Beispielanwendungen, die AEM GraphQL-APIs hervorheben.
* [Authoring Konzepte](/help/sites-cloud/authoring/getting-started/concepts.md)  - Technische Dokumentation für die Authoring-Umgebung von AEM einschließlich Details zur Einrichtung von Autoren- und Veröffentlichungsinstanzen
* [Veröffentlichen von Seiten](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)  - Technische Dokumentation zur Veröffentlichung von Inhalten auf AEM
* [Namenskonventionen](/help/implementing/developing/introduction/naming-conventions.md)  - Technische Dokumentation zu den Seitenbenennungsbeschränkungen in AEM
* [Multi-Site-Manager und Übersetzung](/help/sites-cloud/administering/msm-and-translation.md)  - Technische Dokumentation zu AEM leistungsstarken Übersetzungsfunktionen
* [AEM Workflows](/help/sites-cloud/authoring/workflows/overview.md)  - Technische Dokumentation zur Automatisierung von Workflows in AEM
* [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md)  - Technische Dokumentation für Inhaltsfragmente.
* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)  - Technische Dokumentation für Inhaltsfragmentmodelle.
* [Technische Dokumentation zu GraphQL](https://graphql.org)  - Die GraphQL-Definition (externer Link)
* [GraphQL-API](/help/assets/content-fragments/graphql-api-content-fragments.md)  - Technische Dokumentation, in der erläutert wird, wie Anforderungen für den Zugriff auf und die Bereitstellung von Inhaltsfragmenten erstellt werden
* [Assets-REST-API](/help/assets/content-fragments/assets-api-content-fragments.md)  - Technische Dokumentation, in der erläutert wird, wie Inhaltsfragmente (und andere Assets) erstellt und geändert werden
* [Beständige Abfragen](/help/assets/content-fragments/graphql-api-content-fragments.md#persisted-queries-caching)  - Technische Dokumentation zu persistenten Abfragen in AEM
* [Headful und Headless in AEM](/help/implementing/developing/headful-headless.md)  - Eine vollständige Diskussion der Headless-Integration-Ebenen, die in AEM verfügbar sind
