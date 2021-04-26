---
title: Erste Schritte mit AEM Headless als Cloud Service
description: Lernen Sie in diesem Teil der AEM Headless Developer-Journey die AEM Voraussetzungen ohne Kopfdaten kennen.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: 9fb18dbe60121f46dba1e11d4133e5264a6d538d
workflow-type: tm+mt
source-wordcount: '3087'
ht-degree: 4%

---


# Erste Schritte mit AEM Headless als Cloud Service {#getting-started}

>[!CAUTION]
>
>ARBEITEN IN FORTSCHRITTEN - Die Schaffung dieses Dokuments ist im Gange und sollte nicht als vollständig oder endgültig betrachtet werden und auch nicht für Produktionszwecke verwendet werden.

In diesem Teil der [AEM Headless Developer-Journey erfahren Sie, was erforderlich ist, um Ihr eigenes Projekt mit AEM Headless zu starten.](overview.md)

## Die Meldung bisher {#story-so-far}

Im vorherigen Dokument der AEM kopless-Journey, [Informationen zu CMS Headless Development](learn-about.md) haben Sie die Grundtheorie gelernt, was ein Headless-CMS ist und sollten Sie jetzt:

* Grundlegende Konzepte und Terminologie von Versand ohne Inhalt verstehen
* Verstehen Sie, warum und wann Kopflosigkeit erforderlich ist
* Auf hoher Ebene wissen, wie Headless-Konzepte verwendet werden und wie sie miteinander verknüpft werden

Dieser Artikel basiert auf diesen Grundlagen, damit Sie verstehen, wie Sie AEM verwenden können, um eine kopflose Lösung zu implementieren.

## Vorgabe {#objective}

Dieses Dokument hilft Ihnen, AEM Headless im Kontext Ihres eigenen Projekts zu verstehen. Nach dem Lesen sollten Sie:

* Machen Sie sich mit den Grundlagen AEM kostenlosen Funktionen vertraut.
* Erkennen Sie die Voraussetzungen für die Verwendung AEM kostenlosen Funktionen.
* Achten Sie auf AEM Ebene der kostenlosen Integration.
* Sie können Ihr Projekt in Bezug auf den Umfang definieren.

## AEM Grundlagen {#aem-basics}

Bevor Sie Ihr kopfloses Projekt in AEM definieren können, sollten Sie einige grundlegende AEM Konzepte verstehen.

### Autoreninstanz {#author}

Am einfachsten besteht AEM aus einer Autoreninstanz und einer [Veröffentlichungsinstanz](#publish), die zusammenarbeiten, um Ihre Inhalte zu erstellen, zu verwalten und zu veröffentlichen.

Der Inhalt beginnt in der Autoreninstanz. Hier erstellen Sie die Inhalte von Autoren. Die Authoring-Umgebung stellt Autoren verschiedene Tools zum Erstellen, Organisieren und Wiederverwenden ihrer Inhalte zur Verfügung.

### Instanz im Veröffentlichungsmodus {#publish}

Nachdem Inhalte in der Autoreninstanz erstellt wurden, müssen sie veröffentlicht werden, damit sie für andere Dienste verfügbar sind, um sie zu nutzen. Eine Veröffentlichungsinstanz enthält alle veröffentlichten Inhalte.

### Replikation {#replication}

Replizierung ist der Vorgang der Übertragung von Inhalten von der Autoreninstanz auf die Veröffentlichungsinstanz. Dies erfolgt automatisch durch AEM, wenn ein Autor oder ein anderer Benutzer mit entsprechenden Rechten Inhalte veröffentlicht.

### AEM Zusammenfassung {#aem-basics-summary}

Um digitale Erlebnisse in AEM auf der einfachsten Ebene zu erstellen, müssen die folgenden Schritte ausgeführt werden:

1. Ihre Inhaltsersteller erstellen Ihren kopflosen Inhalt in der Autoreninstanz.
1. Wenn dieser Inhalt fertig ist, wird er in die Veröffentlichungsinstanz repliziert. Anschließend können APIs aufgerufen werden, um diesen Inhalt abzurufen.

AEM Headless baut diese technische Grundlage auf, indem es leistungsstarke Tools zur Verwaltung von kostenlosen Inhalten anbietet, die im nächsten Abschnitt [beschrieben werden.](#aem-headless-basics)

## AEM Grundlagen ohne Kopfdaten {#aem-headless-basics}

Die nutzlosen Funktionen von AEM basieren auf einigen wichtigen Funktionen. Diese werden in späteren Abschnitten der Journey ausführlich erläutert. Es ist jetzt wichtig, nur die Grundlagen dessen zu kennen, was sie tun und was sie genannt werden.

### Inhaltsfragmentmodelle {#content-fragment-models}

Inhaltsfragmentmodelle definieren die Struktur der Daten und Inhalte, die Sie in AEM erstellen und verwalten. Sie dienen als Gerüst für Ihre Inhalte. Bei der Erstellung von Inhalten wählen Ihre Autoren aus den von Ihnen definierten Inhaltsfragmentmodellen aus, die sie bei der Erstellung von Inhalten anleiten.

### Inhaltsfragmente {#content-fragments}

Inhaltsfragmente ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Verwenden von seitenunabhängigen Inhalten. Außerdem können Sie Inhalte zur Verwendung an mehreren Orten und über mehrere Kanäle hinweg vorbereiten.

Inhaltsfragmente enthalten strukturierten Inhalt und können im JSON-Format bereitgestellt werden.

### GraphQL- und REST-APIs {#apis}

Um Ihre Inhalte ohne Probleme zu ändern, AEM Angebot zwei robuste APIs.

* Mit der GraphQL-API können Sie Anfragen für den Zugriff auf und die Bereitstellung von Inhaltsfragmenten erstellen.
* Mit der Assets-REST-API können Sie Inhaltsfragmente (und andere Assets) erstellen und ändern.

Sie erfahren mehr über diese APIs und wie sie in einem späteren Teil der Journey ohne AEM verwendet werden. Weitere Dokumentation finden Sie im Abschnitt [Weitere Ressourcen](#additional-resources) weiter unten.

## Headless-Integrationsstufen {#integration-levels}

AEM unterstützt sowohl den kompletten Headless- als auch den traditionellen Vollstapel- oder Headful-Modellen eines CMS. AEM Angebote jedoch nicht nur diese beiden exklusiven Optionen, sondern auch die Möglichkeit, Hybridmodelle zu unterstützen, die die Vorteile beider Modelle kombinieren und Ihnen eine einzigartige Flexibilität für Ihr Headless-Projekt bieten.

Um Ihr Verständnis von Headless-Konzepten sicherzustellen, konzentriert sich diese AEM Headless Developer-Journey auf das reine Headless-Modell, um Sie so schnell wie möglich ohne Programmierung in AEM in die Laufbahn zu bringen.

Sie sollten sich jedoch der zusätzlichen Hybrid-Möglichkeiten bewusst sein, die Ihnen zur Verfügung stehen, sobald Sie AEM Kopfloses verstehen. Wir legen diese Fälle unten für Ihr Bewusstsein dar. Am Ende der Journey werden Sie detaillierter in diese Konzepte aufgenommen, falls eine solche Flexibilität für Ihr Projekt erforderlich ist.

### Sie haben bereits einen externen Konsum von kostenlosen Inhalten, wie z. B. eine Einzelseitenanwendung (SPA). {#already-have-a-spa}

Gehen wir davon aus, dass Ihre grundlegende Anforderung mindestens darin besteht, Inhalte von AEM an einen vorhandenen externen Dienst bereitzustellen.

#### Ebene 1: Integration von Inhaltsfragmenten - Traditionelles Headless-Modell {#level-1}

Diese Integrationsstufe ist das herkömmliche, kopflose Modell und ermöglicht es Ihren Inhaltserstellern, Inhalte in AEM zu erstellen und diese mit GraphQL problemlos an eine beliebige Anzahl externer Dienste zu senden oder mithilfe der Assets API aus externen Diensten zu bearbeiten. In AEM ist keine Kodierung erforderlich.

In diesem Modell wird AEM nur zum Erstellen und Bereitstellen von Inhalten mithilfe von AEM Inhaltsfragmenten verwendet. Rendering und Interaktion mit dem Inhalt werden an die anspruchsvolle externe Anwendung delegiert, häufig an eine einseitige Anwendung (SPA).

#### Ebene 2: SPA in AEM - Hybridmodell {#level-2} einbetten

Diese Integrationsstufe baut auf der ersten Ebene auf, ermöglicht aber auch die Einbettung der externen Anwendung (SPA) in AEM, sodass die Inhaltsersteller den Inhalt im Kontext der externen Anwendung innerhalb AEM Ansicht können. Die Anwendung kann auch eine eingeschränkte Bearbeitung der externen Anwendung innerhalb von AEM unterstützen.

Diese Ebene hat den Vorteil, dass Autoren Inhalte auf kostenlose Weise flexibel AEM erstellen können, wobei ihre Inhalte im Kontext mit einer eingebetteten externen SPA dargestellt werden, ohne dass die Inhalte kopfüber bereitgestellt werden.

#### Ebene 3: SPA in AEM einbetten und vollständig aktivieren - Hybridmodell {#level-3}

Diese Integrationsstufe baut auf Stufe zwei auf, indem die meisten Inhalte in der externen SPA innerhalb AEM bearbeitet werden können.

### Sie haben noch keinen externen Benutzer des kostenlosen Inhalts, z. B. eine Einzelseitenanwendung (SPA). {#do-not-have-a-spa}

Wenn Ihr Ziel darin besteht, eine neue SPA zu erstellen, die Inhalte aus AEM nutzlos verbraucht, können Sie Funktionen wie Inhaltsfragmente verwenden, um Ihre kostenlosen Inhalte zu verwalten, und auch eine SPA mit SPA Editor-Framework erstellen.

Mit dem SPA-Editor nutzt die SPA nicht nur Inhalte aus AEM, sondern kann auch innerhalb AEM von Autoren vollständig bearbeitet werden, sodass Sie sowohl die Flexibilität von kostenlosem Versand als auch die Bearbeitung im Kontext innerhalb AEM haben.

## Anforderungen und Voraussetzungen {#requirements-prerequisites}

Bevor Sie mit Ihrem kopflosen AEM Projekt beginnen, müssen Sie eine Reihe von Anforderungen erfüllen.

### Wissen {#knowledge}

* GraphQL
* Entwicklungs-Erfahrung beim Erstellen von SPA mit React- oder Angular-Frameworks
* Grundlegende AEM zum Erstellen von Inhaltsfragmenten und zum Verwenden des Editors

### Tools {#tools}

* Sandbox-Zugriff zum Testen der Bereitstellung Ihres Projekts
* Lokale Entwicklungsinstanz für Datenmodellierung und Tests
* Bestehende externe SPA oder andere Verbraucher Ihrer kostenlosen AEM

## Definieren Ihres Projekts {#defining-your-project}

Für jedes erfolgreiche Projekt ist es wichtig, nicht nur die Anforderungen des Projekts, sondern auch die Rollen und Verantwortlichkeiten klar zu definieren.

### Anwendungsbereich {#scope}

Es ist sehr wichtig, einen klar definierten Anwendungsbereich für das Projekt zu haben. Scope informiert über die Akzeptanzkriterien und ermöglicht es Ihnen, eine Definition von done festzulegen.

Die erste Frage, die Sie sich stellen müssen, ist: &quot;Was versuche ich mit AEM Kopflos zu erreichen?&quot; Die Antwort sollte im Allgemeinen sein, dass Sie über eine Erlebnisanwendung verfügen oder in Zukunft verfügen werden, die Sie mit Ihren eigenen Entwicklungstools erstellt haben, nicht mit AEM. Bei dieser Erlebnisanwendung kann es sich um eine mobile App, eine Website oder eine andere Erlebnisanwendung für Endbenutzer handeln. Das Ziel der Verwendung AEM Headless besteht darin, Ihrer Erlebnisanwendung Inhalte zuzuführen, die in AEM mit den neuesten APIs erstellt, gespeichert und verwaltet werden, die AEM Headless aufrufen, um Inhalte oder sogar vollständig CRUD-Inhalte direkt aus Ihrer Erlebnisanwendung abzurufen. Wenn dies nicht der Fall ist, sollten Sie [zurück zur AEM Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de) gehen und den Abschnitt finden, der besser zu dem passt, was Sie erreichen möchten.

### Rollen und Zuständigkeiten {#roles-responsibilities}

Die Rollen für jedes einzelne Projekt werden unterschiedlich sein, aber wichtige Aspekte, die im Inhalt AEM kostenlosen Entwicklung zu berücksichtigen sind, sind:

* [Administrator](#administrator)
* [Inhaltsautor](#content-author)
* [Content-Modeler](#content-modeler)
* [Entwickler](#developer)

#### Administrator {#administrator}

Der Administrator ist für die Basiskonfiguration und -konfiguration Ihres Systems verantwortlich. Der Administrator richtet beispielsweise Ihr Unternehmen im Benutzerverwaltungssystem der Adobe ein, das auf Identity Management System (IMS) verwiesen wird. Der Administrator ist der erste Benutzer des Unternehmens, der eine E-Mail-Einladung von der Adobe erhält, sobald Ihr Unternehmen von der Adobe innerhalb des IMS erstellt wurde. Der Administrator kann sich bei IMS anmelden und Benutzer anderer Personen hinzufügen.

Sobald die Benutzer vom Administrator konfiguriert wurden, erhalten sie Zugriff auf alle AEM Ressourcen, um ihre Arbeit als Mitarbeiter für die Bereitstellung der Erlebnisanwendung mit AEM Headless zu erledigen.

Der Administrator sollte der Benutzer sein, der AEM einrichtet und die Laufzeit-Umgebung vorbereitet, damit [Inhaltsersteller](#content-author) Inhalte erstellen und aktualisieren können und [Entwickler](#developer) APIs verwenden können, die Inhalte für ihre Experience-Anwendungen abrufen oder ändern.

#### Inhaltsautor {#content-author}

Inhaltsersteller erstellen und verwalten die Inhalte, die von der AEM kopfüber bereitgestellt werden. Inhaltsautoren verwenden AEM Funktionen wie Inhaltsfragmente und die Asset-Konsole, um ihre Inhalte zu verwalten.

Autoren von Inhalten sollten die folgenden Best Practices beachten.

#### Plan für die Lokale Anpassung {#localization}

Planung der Übersetzung und lokale Anpassung zu Beginn des Projektes. Betrachten Sie &quot;Internationalisierungs-Projektmanager&quot;als eine separate Person, deren Aufgabe es ist, zu definieren, welche Inhalte übersetzt werden sollen und welche nicht und welche übersetzten Inhalte von regionalen oder lokalen Inhaltsproduzenten geändert werden können.

Erstellen Sie einen Plan für die gewünschte Content-lokale Anpassung.

* Benötigen Sie nur verschiedene Sprachen oder auch eine Sprache, um regionale Besonderheiten zu berücksichtigen?
* Benötigen Sie Rich-Media-Inhalte wie Bilder oder Videos, um für verschiedene Gebietsschemata unterschiedlich zu sein?

Achten Sie auf einen klaren Arbeitsablauf für Inhaltsaktualisierungen. Welchen Genehmigungsprozess muss das System unterstützen? Kann AEM genutzt Workflows werden, um diesen Prozess zu automatisieren?

Beachten Sie, dass Ihre [Inhaltshierarchie](#content-hierarchy) genutzt werden kann, um die lokale Anpassung zu vereinfachen.

Weitere Informationen zu AEM Tools für Workflows und lokale Anpassung finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources).

##### Nutzen Sie die Inhaltshierarchie {#content-hierarchy}

Die Ordnerhierarchie kann zwei wichtige Probleme in Bezug auf Content-Management lösen:

* [lokale Anpassung](#localization) : AEM verwaltet die lokale Anpassung von Inhalten durch Beibehaltung von Inhaltskopien in Gebietsschema-spezifischen Ordnern.
* Unternehmen - Ordner werden verwendet, um eine Inhaltshierarchie zu definieren, die zur Unterstützung der lokale Anpassung und zur logischen Verwaltung von Inhaltsfragmenten erforderlich ist.

AEM ermöglicht eine sehr flexible Inhaltsstruktur und eine Hierarchie kann beliebig groß sein. Es ist jedoch wichtig zu erkennen, dass Änderungen in der Ordnerstruktur unbeabsichtigte Folgen für bestehende Abfragen haben können, die [auf den Inhaltspfad angewiesen sind.](#developer) Daher kann eine klar definierte Hierarchie, die im Voraus klar festgelegt ist, für Ihre Autoren sehr hilfreich sein.

Ordner können auch darauf beschränkt werden, nur bestimmte Inhaltstypen zuzulassen (basierend auf Inhaltsfragmentmodellen). Es wird generell empfohlen, immer explizit anzugeben, welche Modelle für alle Ordner in der Hierarchie zulässig sind. Zulässige Inhalte für einen bestimmten Ordner angeben:

* Verhindert, dass Inhaltsersteller Inhalte erstellen, die nicht in den Ordner gehören.
* Optimiert den Inhaltserstellungsprozess durch Filtern der Inhaltstypen, die im Ordner während der Erstellung zulässig sind, sodass nur gültige Inhaltstypen angezeigt werden.

Durch die Erstellung einer geeigneten Inhaltsstruktur wird es einfacher, das Erstellen von kostenlosen Inhalten über Kanal hinweg zu koordinieren, um die Wiederverwendung von Inhalten zu maximieren. Die Nutzung von Inhalten über mehrere Kanal hinweg verbessert die Effizienz der Inhaltsproduktion und das Änderungsmanagement erheblich.

##### Gute Benennungskonventionen {#naming-conventions} einrichten

Inhaltsfragmentnamen müssen für Inhaltsersteller beschreibend sein. AEM behandelt das Escape- und/oder Abschneiden der verwendeten IDs auf Repository-Ebene transparent. Daher sollten die von den Autoren bereitgestellten logischen Namen immer lesbar sein und den Inhalt darstellen.

* Ungültiger Name: `cta_btn_1`
* Guten Namen: `Call To Action Button`

Weitere Dokumentation zu AEM Seitenbenennungskonventionen finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources).

##### Inhaltsverschachtelung nicht überschreiben {#content-nesting}

[Inhaltsfragmente ](#content-fragments) werden in AEM verwendet, um kopflosen Inhalt zu erstellen. AEM unterstützt bis zu zehn Ebenen der Verschachtelung von Inhalten für Inhaltsfragmente. Es ist jedoch wichtig zu beachten, dass AEM jeden im übergeordneten Inhaltsfragment definierten Verweis iterativ auflösen und dann prüfen müssen, ob in allen Geschwistern untergeordnete Verweise vorhanden sind. Diese Vorgänge können sich schnell ergänzen und zu einem Leistungsproblem werden.

Als allgemeine Faustregel sollten Inhaltsfragmentverweise nicht über fünf Ebenen verschachtelt werden.

#### Content Modeler {#content-modeler}

Inhaltsmodellierer analysieren die Anforderungen für die Daten, die ohne Überschneidung bereitgestellt werden müssen, und definieren die Struktur für diese Daten. Diese Strukturen werden in AEM als [Inhaltsfragmentmodelle](#content-fragment-models) bezeichnet. Inhaltsfragmentmodelle werden als Grundlage für die Inhaltsfragmente verwendet, die die Inhaltsersteller erstellen.

Ein nützlicher Ansatz beim Definieren von Inhaltsfragmentmodellen besteht darin, Modelle zu erstellen, die den UX-Komponenten der Anwendung(en) zugeordnet sind, die den Inhalt verbrauchen.

Da die Inhaltsersteller bei der Erstellung neuer Inhalte kontinuierlich mit den Modellen interagieren, hilft ihnen die Ausrichtung der Modelle an der UX dabei, die daraus resultierende digitale Erfahrung zu visualisieren. Wenn Sie diese Ausrichtung einen Schritt weiter vorantreiben, können Sie den Inhaltsfragmentmodellen Symbole zuweisen, die das UX-Element darstellen, damit die Autoren intuitiv das richtige Modell anhand visueller Hinweise auswählen können.

#### Entwickler {#developer}

Entwickler sind dafür verantwortlich, die Inhalte, die kopfüber erstellt werden, in AEM für den Verbraucher zusammenzuführen, was oft eine einseitige Anwendung (SPA), progressive Web-App (PWA), ein Webshop oder ein anderer Dienst außerhalb von AEM sein kann.

GraphQL dient als &quot;Kleber&quot; zwischen AEM und den Konsumenten von Kopflosen Inhalt. GraphQL ist die Sprache, die Abfragen für den erforderlichen Inhalt AEM.

Entwickler sollten bei der Planung ihrer Abfragen einige grundlegende Empfehlungen beachten:

* Abfragen sollten sich nicht auf einen festen Pfad (`ByPath`) zum Abrufen von Inhaltsfragmenten verlassen.
   * [Inhaltsersteller haben vollständige Kontrolle über die ](#content-hierarchy) Hierarchie von Inhaltsfragmenten und können Änderungen vornehmen, die eine solche Abfrage unterbrechen würden.
   * Abfragen sollten stattdessen auf Inhaltsfragmentmodellverweise mit dynamischen Abfragen zurückgreifen, um die Ergebnisse zu filtern und die gewünschte Nutzlast zu generieren.
* Verwenden Sie für eine optimale Abfrage stets die beibehaltenen Abfragen in AEM. Diese werden später im Journey diskutiert.
* GraphQL ist deklarativ nach dem Motto &quot;Fragen Sie genau, was Sie brauchen, und bekommen Sie genau das.&quot; Das bedeutet, dass Sie beim Erstellen von GraphQL-Abfragen immer `select *`-Abfragen vermeiden müssen, die Sie eventuell in einer relationalen Datenbank erstellen.

Bei einer [typischen Implementierung ohne Kopfdaten mit AEM benötigt der Entwickler keine Programmierkenntnisse zu AEM.](#level-1)

### Leistungsanforderungen {#performance-requirements}

Damit ein Projekt erfolgreich sein kann, muss die Leistung vor der Erstellung von Inhalten berücksichtigt werden.

Sie müssen die Erwartungen Ihrer Benutzer/Besucher und deren Design verstehen. Legen Sie Ziele auf Dienstebene (SLOs) fest und messen Sie diese, um zu verstehen, ob Sie die Erwartungen Ihrer Benutzer erfüllen.

#### Traffic-Muster {#traffic-patterns}

Um Traffic- und Traffic-Muster zu verstehen, Beginn mit dem Sammeln, was Sie aus der Vergangenheit kennen, und dann Projektieren Sie das erwartete Wachstum in den nächsten Jahren. Einige der wichtigsten Variablen, die zu berücksichtigen sind:

* Wie viele API-Aufrufe pro Stunde/Tag/Monat erwarten Sie und besteht Potenzial für Spitzen und Saisonabhängigkeit?
* Wie viele verschiedene Inhaltsersteller gibt es?
* Wie viele Autoren von Inhalten werden voraussichtlich gleichzeitig arbeiten?
* Wie oft werden Inhaltsaktualisierungen vorgenommen?
* Wie viele Inhaltsmodelle sind erforderlich?
* Wie viele Instanzen von Modellen werden benötigt?

#### Aktualisierungsfrequenz {#update-frequency}

Oft gibt es verschiedene Abschnitte mit unterschiedlichen Häufigkeit von Inhaltsaktualisierungen. Um CDN- und Cache-Konfigurationen genau abstimmen zu können, ist es wichtig, dies zu verstehen. Dies ist auch für die [Inhaltsmodelle](#content-modeler) wichtig, da sie Modelle zur Darstellung Ihres Inhalts entwerfen. Betrachten Sie Folgendes:

* Müssen einige Inhaltstypen nach einem bestimmten Zeitraum ablaufen?
* Gibt es Elemente, die benutzerspezifisch sind und daher nicht zwischengespeichert werden können?

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun die AEM Journey zum kostenlosen Entwickler abgeschlossen haben, sollten Sie:

* Machen Sie sich mit den Grundlagen AEM kostenlosen Funktionen vertraut.
* Erkennen Sie die Voraussetzungen für die Verwendung AEM kostenlosen Funktionen.
* Achten Sie auf AEM Ebene der kostenlosen Integration.
* Sie können Ihr Projekt in Bezug auf den Umfang definieren.

Sie sollten Ihre AEM kopflosen Journey fortsetzen, indem Sie sich das Dokument [Pfad zu Ihrem Erlebnis mit AEM Headless](path-to-first-experience.md) ansehen, in dem Sie erfahren, wie Sie die erforderlichen Tools einrichten und wie Sie beginnen, über die Modellierung Ihrer Daten in AEM nachzudenken.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, zum nächsten Teil der Journey für die Entwicklung ohne Kopfdaten zu wechseln, indem Sie das Dokument [Pfad zu Ihrem ersten Erlebnis mit AEM Headless überprüfen. Es folgen jedoch einige zusätzliche optionale Ressourcen, die einen tieferen Einstieg in einige der in diesem Dokument erwähnten Konzepte ermöglichen, die jedoch nicht weiter auf der Journey ohne Kopfdaten ausgeführt werden müssen.](path-to-first-experience.md)

* [Eine Einführung in die Architektur von Adobe Experience Manager als Cloud Service](/help/core-concepts/architecture.md)  - Verstehen AEM als Struktur eines Cloud Service
* [AEM Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de)  ohne Kopf - Nutzen Sie diese praktischen Übungen, um zu untersuchen, wie Sie die verschiedenen Optionen für die Bereitstellung von Inhalten an kopflosen Endpunkten mit AEM nutzen können, und zu entscheiden, was für Sie am besten geeignet ist.
* [Headless-Content-Management mit GraphQL-APIs](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses)  - In diesem Kurs erhalten Sie einen Überblick über die in AEM implementierte GraphQL-API. Die Authentifizierung über AdobeID ist erforderlich.
* [AEM Guides WKND - GraphQL](https://github.com/adobe/aem-guides-wknd-graphql)  - Dieses GitHub-Projekt enthält Beispielanwendungen, die AEM GraphQL APIs hervorheben.
* [Authoring-Konzepte](/help/sites-cloud/authoring/getting-started/concepts.md)  - Technische Dokumentation für die Authoring-Umgebung von AEM, einschließlich Informationen zum Einrichten der Autoren-Veröffentlichung
* [Veröffentlichungsseiten](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)  - Technische Dokumentation für die Veröffentlichung von Inhalten auf AEM
* [Namenskonventionen](/help/implementing/developing/introduction/naming-conventions.md)  - Technische Dokumentation der Seitenbenennungsbeschränkungen in AEM
* [Multi-Site-Manager und Übersetzung](/help/sites-cloud/administering/msm-and-translation.md)  - Technische Dokumentation zu AEM leistungsstarken Übersetzungsfunktionen
* [AEM Workflows](/help/sites-cloud/authoring/workflows/overview.md)  - Technische Dokumentation zur Automatisierung von Workflows in AEM
* [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md)  - Technische Dokumentation für Inhaltsfragmente.
* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)  - Technische Dokumentation für Inhaltsfragmentmodelle.
* [GraphQL Technische Dokumentation](https://graphql.org)  - Die GraphQL-Definition (externer Link)
* [GraphQL API](/help/assets/content-fragments/graphql-api-content-fragments.md)  - Technische Dokumentation, die erklärt, wie Anforderungen für den Zugriff auf und die Bereitstellung von Inhaltsfragmenten erstellt werden
* [Assets REST API](/help/assets/content-fragments/assets-api-content-fragments.md)  - Technische Dokumentation, in der das Erstellen und Ändern von Inhaltsfragmenten (und anderen Assets) erläutert wird
* [Beständige Abfragen](/help/assets/content-fragments/graphql-api-content-fragments.md#persisted-queries-caching)  - Technische Dokumentation zu beständigen Abfragen in AEM
* [Headful and Headless in AEM](/help/implementing/developing/headful-headless.md)  - Eine vollständige Diskussion über die in AEMverfügbaren Stufen der Integration ohne Kopf
