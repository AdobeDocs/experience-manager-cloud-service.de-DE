---
title: Erste Schritte mit AEM Headless as a Cloud Service
description: In diesem Teil der AEM Headless-Entwickler-Tour erfahren Sie mehr über die Voraussetzungen für AEM Headless.
exl-id: 9661e17b-fa9f-4689-900c-412b068e942c
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '3068'
ht-degree: 94%

---

# Erste Schritte mit AEM Headless as a Cloud Service {#getting-started}

In diesem Teil der [AEM Headless-Entwickler-Journey](overview.md) erfahren Sie, was erforderlich ist, um Ihr eigenes Projekt mit AEM Headless zu starten.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Headless-Tour, [Informationen zur CMS-Headless-Entwicklung](learn-about.md), haben Sie die grundlegende Theorie gelernt, was ein Headless-CMS ist, und sollten jetzt:

* die grundlegenden Konzepte und die Terminologie der Headless-Bereitstellung von Inhalten verstehen,
* verstehen, warum und wann Headless erforderlich ist,
* grundsätzlich wissen, wie Headless-Konzepte verwendet werden und wie sie miteinander zusammenhängen.

Dieser Artikel baut auf diesen Grundlagen auf, sodass Sie verstehen, wie Sie AEM verwenden können, um eine Headless-Lösung zu implementieren.

## Ziel {#objective}

Dieses Dokument hilft Ihnen, AEM Headless im Kontext Ihres eigenen Projekts zu verstehen. Nach dem Lesen sollten Sie:

* die Grundlagen der Headless-Funktionen von AEM verstehen,
* die Voraussetzungen für die Verwendung der Headless-Funktionen von AEM kennen,
* sich der Headless-Integrationsebenen von AEM bewusst sein.
* in der Lage sein, Ihr Projekt in Bezug auf den Umfang zu definieren.

## AEM-Grundlagen {#aem-basics}

Bevor Sie Ihr Headless-Projekt in AEM definieren können, müssen Sie einige grundlegende AEM-Konzepte verstehen.

### Autoreninstanz {#author}

In seiner einfachsten Form besteht AEM aus einer Autoreninstanz und einer [Veröffentlichungsinstanz](#publish), die zusammenarbeiten, um Ihre Inhalte zu erstellen, zu verwalten und zu veröffentlichen.

Inhalte haben ihren Anfang in der Autoreninstanz. Hier erstellen Inhaltsautoren ihre Inhalte. Die Autorenumgebung bietet verschiedene Tools für Autoren zum Erstellen, Organisieren und Wiederverwenden ihrer Inhalte.

### Veröffentlichungsinstanz {#publish}

Nachdem Inhalte in der Autoreninstanz erstellt wurden, müssen sie veröffentlicht werden, damit sie für andere Services verfügbar sind. Eine Veröffentlichungsinstanz enthält alle veröffentlichten Inhalte.

### Vorschau-Service {#preview}

Vor der Veröffentlichung in der Publishing-Instanz können Sie Ihr Inhaltsfragment auch im **Vorschau-Service** zum Testen und Überprüfen veröffentlichen. Dies geschieht über die **Inhaltsfragmentkonsole**.

### Replikation {#replication}

Die Replikation ist der Vorgang der Übertragung von Inhalten von der Autoreninstanz auf die Veröffentlichungsinstanz. Dies erfolgt automatisch durch AEM, wenn ein Autor oder ein anderer Benutzer mit entsprechenden Berechtigungen Inhalte veröffentlicht.

### AEM-Grundlagen – Zusammenfassung {#aem-basics-summary}

Auf der einfachsten Ebene erfordert das Erstellen digitaler Erlebnisse in AEM die folgenden Schritte:

1. Inhaltsautoren erstellen ihre Headless-Inhalte in der Autoreninstanz.
1. Wenn diese Inhalte fertig sind, werden sie auf die Veröffentlichungsinstanz repliziert.
1. Anschließend können APIs aufgerufen werden, um diese Inhalte abzurufen.

AEM Headless baut auf dieser technischen Grundlage auf, indem leistungsstarke Tools zum Verwalten von Headless-Inhalten bereitgestellt werden[ die im nächsten Abschnitt beschrieben ](#aem-headless-basics).

## AEM Headless-Grundlagen {#aem-headless-basics}

Die Headless-Funktionen von AEM basieren auf einigen wenigen wichtigen Funktionen. Diese werden in späteren Teilen der Tour ausführlich erläutert. Es ist jetzt nur wichtig, die Grundlagen zu kennen, was sie tun und wie sie heißen.

### Inhaltsfragmentmodelle {#content-fragment-models}

Inhaltsfragmentmodelle definieren die Struktur der Daten und Inhalte, die Sie in AEM erstellen und verwalten. Sie dienen als Gerüst für Ihre Inhalte. Bei der Erstellung von Inhalten wählen Autoren aus den von Ihnen definierten Inhaltsfragmentmodellen aus, die sie bei der Erstellung von Inhalten anleiten.

### Inhaltsfragmente {#content-fragments}

Inhaltsfragmente ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Verwenden von seitenunabhängigen Inhalten. Außerdem können Sie Inhalte zur Verwendung an mehreren Orten und über mehrere Kanäle hinweg vorbereiten.

Inhaltsfragmente enthalten strukturierten Inhalt und können im JSON-Format bereitgestellt werden.

### GraphQL- und REST-APIs {#apis}

Um Inhalte „headless“ zu ändern, bietet AEM zwei robuste APIs.

* Mit der GraphQL-API können Sie Anfragen für den Zugriff auf und die Bereitstellung von Inhaltsfragmenten erstellen.
* Mit der Assets-REST-API können Sie Inhaltsfragmente (und andere Assets) erstellen und ändern.

In einem späteren Teil der AEM-Headless-Tour erfahren Sie mehr über diese APIs und wie Sie sie verwenden können. Weitere Dokumentation finden Sie unten im Abschnitt [Zusätzliche Ressourcen](#additional-resources).

## Headless-Integrationsebenen {#integration-levels}

AEM unterstützt sowohl den vollständigen Headless- als auch den herkömmlichen Full-Stack oder Headful-Modelle eines CMS. AEM bietet jedoch nicht nur diese beiden exklusiven Optionen, sondern auch die Möglichkeit, Hybridmodelle zu unterstützen, die die Vorteile beider Modelle kombinieren und Ihnen eine einzigartige Flexibilität für Ihr Headless-Projekt bieten.

Um sicherzustellen, dass Sie die Headless-Konzepte verstehen, konzentriert sich diese AEM Headless-Entwickler-Tour auf das reine Headless-Modell, damit Sie so schnell wie möglich ohne Codieren in AEM starten können.

Sie sollten sich jedoch der zusätzlichen zur Verfügung stehenden Hybridmöglichkeiten bewusst sein, sobald Sie AEM Headless-Funktionen verstehen. Diese Fälle werden nachstehend zu Ihrer Information aufgeführt. Am Ende der Tour werden Sie mit diesen Konzepten näher vertraut gemacht, falls eine solche Flexibilität für Ihr Projekt erforderlich ist.

### Sie verfügen bereits über eine externe Nutzung von Headless-Inhalten, wie z. B. eine Single Page Application (SPA). {#already-have-a-spa}

Nehmen wir einmal an, dass Ihre Grundanforderung mindestens darin besteht, Inhalte von AEM an einen bestehenden externen Service zu senden.

#### Ebene 1: Integration von Inhaltsfragmenten – Herkömmliches Headless-Modell {#level-1}

Diese Integrationsebene ist das herkömmliche Headless-Modell und ermöglicht es Ihren Inhaltsautoren, Inhalte in AEM zu erstellen und diese mithilfe von GraphQL für eine beliebige Anzahl externer Services bereitzustellen oder mithilfe der Assets-API über externe Services zu bearbeiten. In AEM ist keine Programmierung erforderlich.

In diesem Modell wird AEM nur zum Erstellen und Bereitstellen der Inhalte mithilfe von AEM-Inhaltsfragmenten verwendet. Rendering und Interaktion mit dem Inhalt werden an die nutzende externe Anwendung delegiert, häufig eine Single Page Application (SPA).

#### Ebene 2: Einbetten der SPA in das AEM-Hybridmodell {#level-2}

Diese Integrationsebene baut auf der ersten Ebene auf, ermöglicht jedoch auch die Einbettung der externen Anwendung (SPA) in AEM, sodass die Inhaltsautoren die Inhalte im Kontext der externen Anwendung in AEM sehen können. Die Anwendung kann auch eine eingeschränkte Bearbeitung der externen Anwendung in AEM unterstützen.

Diese Ebene bietet den Vorteil, dass Inhaltsautoren Inhalte in AEM dynamisch erstellen können, wobei ihre Inhalte kontextbezogen mit einer eingebetteten externen SPA präsentiert werden, während sie die Inhalte dennoch „headless“ bereitstellen.

#### Ebene 3: Einbetten und vollständiges Aktivieren der SPA im AEM-Hybridmodell {#level-3}

Diese Integrationsebene baut auf Ebene zwei auf, indem die meisten Inhalte in der externen SPA innerhalb von AEM bearbeitbar sind.

### Sie haben noch keinen externen Benutzer der Headless-Inhalte, z. B. eine Single Page Application (SPA). {#do-not-have-a-spa}

Wenn Sie eine SPA erstellen möchten, die Inhalte von AEM „headless“ nutzt, können Sie Funktionen wie Inhaltsfragmente verwenden, um Ihre Headless-Inhalte zu verwalten, und auch eine SPA mithilfe des AEM SPA-Editor-Frameworks erstellen.

Mit dem SPA-Editor nutzt die SPA nicht nur Inhalte aus AEM, sondern kann auch innerhalb von AEM von Ihren Inhaltsautoren vollständig bearbeitet werden, sodass Sie sowohl die Flexibilität der Headless-Bereitstellung als auch der kontextbezogenen Bearbeitung innerhalb von AEM nutzen können.

## Anforderungen und Vorbedingungen {#requirements-prerequisites}

Bevor Sie mit Ihrem Headless-AEM-Projekt beginnen, müssen Sie verschiedene Anforderungen erfüllen.

### Kenntnisse {#knowledge}

* GraphQL
* Entwicklungserlebnis beim Erstellen von SPA mit React- oder Angular-Frameworks
* Grundlegende AEM-Kenntnisse zum Erstellen von Inhaltsfragmenten und Verwenden des Editors

### Tools {#tools}

* Sandbox-Zugriff zum Testen der Bereitstellung Ihres Projekts
* Lokale Entwicklungsinstanz für Datenmodellierung und -tests
* Bestehende externe SPA oder andere Nutzer Ihrer Headless-AEM-Inhalte

## Definieren Ihres Projekts {#defining-your-project}

Für ein erfolgreiches Projekt ist es wichtig, nicht nur die Anforderungen des Projekts, sondern auch die Rollen und Verantwortlichkeiten klar zu definieren.

### Umfang {#scope}

Es ist sehr wichtig, einen klar definierten Umfang für das Projekt zu haben. Der Umfang gibt Auskunft über die Akzeptanzkriterien und ermöglicht es Ihnen, eine Definition von „Fertig“ festzulegen.

Die erste Frage, die Sie sich stellen müssen, lautet: „Was versuche ich, mit AEM Headless zu erreichen?“ Die Antwort sollte im Allgemeinen sein, dass Sie eine Erlebnis-App haben oder in Zukunft haben werden, die Sie mit Ihren eigenen Entwicklungs-Tools und nicht mit AEM erstellt haben. Bei dieser Erlebnisanwendung kann es sich um eine mobile App, eine Website oder eine andere Erlebnisanwendung für Endverbraucher handeln. Das Ziel der Verwendung von AEM Headless besteht darin, Ihre Erlebnisanwendung mit Inhalten zu versorgen, die in AEM erstellt, gespeichert und verwaltet werden, mit hochmodernen APIs, die AEM Headless aufrufen, um Inhalte oder sogar vollständige CRUD-Inhalte direkt aus Ihrer Erlebnisanwendung abzurufen. Wenn dies nicht das ist, was Sie tun möchten, sollten Sie [zurück zur AEM-Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de) gehen und den Abschnitt finden, der besser zu dem passt, was Sie erreichen möchten.

### Rollen und Zuständigkeiten {#roles-responsibilities}

Die Rollen für jedes einzelne Projekt werden variieren, aber wichtige Rollen, die man im Kontext der AEM-Headless-Entwicklung berücksichtigen sollte, sind:

* [Administrator](#administrator)
* [Inhaltsautor](#content-author)
* [Inhaltsarchitekt](#content-architect)
* [Entwickler](#developer)

#### Administrator {#administrator}

Der Administrator ist für die grundlegende Einrichtung und Konfiguration Ihres Systems verantwortlich. Beispielsweise richtet der Administrator Ihre Organisation im User Management-System von Adobe ein, das auch Identity Management System (IMS) genannt wird. Der Administrator ist der erste Benutzer des Unternehmens, der per E-Mail eine Einladung von Adobe erhält, sobald Ihre Organisation von Adobe im IMS erstellt wurde. Der Administrator kann sich dann beim IMS anmelden und Benutzer oder andere Rollen hinzufügen.

Sobald die Benutzer vom Administrator konfiguriert wurden, erhalten sie die Berechtigungen für den Zugriff auf alle AEM-Ressourcen, um ihre Arbeit als Mitwirkende für die Bereitstellung der Erlebnis-App mit AEM Headless zu erledigen.

Der Administrator sollte der Benutzer sein, der AEM einrichtet und die Laufzeitumgebung vorbereitet, damit [Inhaltsautoren](#content-author) Inhalte erstellen und aktualisieren können und [Entwickler](#developer) APIs verwenden können, die Inhalte für ihre Erlebnisanwendungen abrufen oder ändern.

#### Inhaltsautor {#content-author}

Inhaltsautoren erstellen und verwalten die Inhalte, die von AEM Headless bereitgestellt werden. Inhaltsautorinnen und Inhaltsautoren verwenden AEM-Funktionen wie den Inhaltsfragmenteditor und verschiedene Konsolen zur Verwaltung ihrer Inhalte.

Inhaltsautoren sollten die folgenden Best Practices beachten.

#### Übersetzung planen {#translation}

Planen Sie die Übersetzung ganz am Anfang des Projekts. Betrachten Sie den Übersetzungsspezialisten als eine separate Rolle, dessen Aufgabe es ist zu definieren, welche Inhalte übersetzt werden sollen und welche nicht und welche übersetzten Inhalte von regionalen oder lokalen Inhaltserstellern geändert werden können.

Erstellen Sie einen Plan zur benötigten Übersetzung von Inhalten.

* Benötigen Sie nur verschiedene Sprachen oder auch Sprachvarianten zur Anpassung an regionale Besonderheiten?
* Müssen Rich-Media-Inhalte wie Bilder oder Videos für verschiedene Länder unterschiedlich sein?

Verschaffen Sie sich Klarheit über Ihren Workflow zur Aktualisierung von Inhalten. Wie sieht der Genehmigungsprozess aus, den das System unterstützen muss? Können AEM-Workflows genutzt werden, um diesen Prozess zu automatisieren?

Ihre [Inhaltshierarchie](#content-hierarchy) kann genutzt werden, um die Übersetzung zu erleichtern.

Im Abschnitt [Zusätzliche Ressourcen](#additional-resources) finden Sie zusätzliche Dokumentation zu AEM-Workflows und Übersetzungs-Tools sowie Links zur AEM Headless-Übersetzungs-Tour.

##### Verwenden der Inhaltshierarchie {#content-hierarchy}

Die Ordnerhierarchie kann zwei wesentliche Probleme im Zusammenhang mit dem Content-Management lösen:

* [Übersetzung](#translation): AEM verwaltet die Übersetzung von Inhalten, indem Kopien von Inhalten in gebietsschemaspezifischen Ordnern verwaltet werden.
* Organisation: Ordner werden verwendet, um eine Inhaltshierarchie zu definieren, die zur Unterstützung der Anforderungen an die Übersetzung sowie zur logischen Verwaltung von Inhaltsfragmenten erforderlich ist.

AEM ermöglicht eine sehr flexible Inhaltsstruktur und eine Hierarchie kann beliebig groß sein. Es ist jedoch wichtig zu verstehen, dass Änderungen an der Ordnerstruktur unbeabsichtigte Folgen für bestehende Abfragen haben können, die ([ auf den Inhaltspfad angewiesen) ](#developer). Daher kann eine klar definierte Hierarchie, die im Voraus festgelegt ist, für Inhaltsautoren äußerst hilfreich sein.

Ordner können auch darauf beschränkt werden, nur bestimmte Inhaltstypen zuzulassen (basierend auf Inhaltsfragmentmodellen). Es wird allgemein empfohlen, immer explizit anzugeben, welche Modelle für alle Ordner in der Hierarchie zulässig sind. Das Angeben von zulässigen Inhalten für einen bestimmten Ordner:

* verhindert, dass Inhaltsautoren Inhalte erstellen, die nicht zum Ordner gehören,
* optimiert den Inhaltserstellungsprozess, indem die Inhaltstypen gefiltert werden, die im Ordner während der Erstellung zulässig sind, sodass nur gültige Inhaltstypen angezeigt werden.

Durch das Schaffen einer geeigneten Inhaltsstruktur wird es einfacher, die Headless-Inhaltserstellung kanalübergreifend zu koordinieren, um die Wiederverwendung von Inhalten zu maximieren. Durch die Nutzung von Inhalten über mehrere Kanäle wird die Effizienz der Inhaltserstellung und das Änderungs-Management erheblich verbessert.

##### Einrichten guter Benennungskonventionen {#naming-conventions}

Inhaltsfragmentnamen müssen für Inhaltsautoren beschreibend sein. AEM behandelt das Maskieren und/oder Abschneiden der verwendeten IDs auf Repository-Ebene transparent. Daher sollten die von den Inhaltsautoren bereitgestellten logischen Namen immer lesbar sein und den Inhalt darstellen.

* Schlechter Name: `cta_btn_1`
* Guter Name: `Call To Action Button`

Weitere Informationen zu AEM-Seitennamenkonventionen finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources).

##### Verschachtelung von Inhalten nicht überstrapazieren {#content-nesting}

[Inhaltsfragmente](#content-fragments) werden in AEM verwendet, um Headless-Inhalte zu erstellen. AEM unterstützt bis zu zehn Verschachtelungsebenen von Inhalten für Inhaltsfragmente. Beachten Sie jedoch, dass AEM alle im übergeordneten Inhaltsfragment definierten Verweise iterativ auflösen und dann überprüfen muss, ob in allen gleichrangigen Elementen Verweise auf untergeordnete Elemente vorhanden sind. Diese Vorgänge können sich schnell summieren und zu einem Leistungsproblem werden.

Als allgemeine Faustregel gilt, dass Inhaltsfragmentverweise nicht über mehr als fünf Ebenen verschachtelt werden sollten.

#### Inhaltsarchitekt {#content-architect}

Inhaltsarchitekten analysieren die Anforderungen an die Daten, die „headless“ bereitgestellt werden müssen, und definieren die Struktur für diese Daten. Diese Strukturen werden in AEM [Inhaltsfragmentmodelle](#content-fragment-models) genannt. Inhaltsfragmentmodelle werden als Grundlage für die Inhaltsfragmente verwendet, die die Inhaltsautoren erstellen.

Ein nützlicher Ansatz bei der Definition von Inhaltsfragmentmodellen besteht darin, Modelle zu erstellen, die den Benutzererlebnis-Komponenten der Anwendungen zugeordnet sind, die die Inhalte nutzen.

Da die Inhaltsautoren bei der Erstellung neuer Inhalte kontinuierlich mit den Modellen interagieren, hilft ihnen die Ausrichtung der Modelle am Benutzererlebnis dabei, das daraus resultierende digitale Erlebnis zu visualisieren. Wenn Sie diese Ausrichtung weiter vorantreiben, können Sie den Inhaltsfragmentmodellen, die das Benutzererlebnis-Element darstellen, Symbole zuweisen, damit die Autoren anhand visueller Hinweise intuitiv das richtige Modell auswählen können.

#### Entwickler {#developer}

Entwickler sind dafür verantwortlich, die Inhalte, die „headless“ in AEM erstellt werden, mit dem Nutzer dieser Inhalte zusammenzuführen. Dabei kann es sich häufig um eine Single Page Application (SPA), eine Progressive Web App (PWA), einen Webshop oder einen anderen für AEM externen Service handeln.

GraphQL dient als „Kleber“ zwischen AEM und den Nutzern von Headless-Inhalten. GraphQL ist die Sprache, die AEM nach den erforderlichen Inhalten abfragt.

Entwickler sollten bei der Planung ihrer Abfragen einige grundlegende Empfehlungen beachten:

* Bei Abfragen sollte kein fester Pfad (`ByPath`) zum Abrufen von Inhaltsfragmenten verwendet werden.
   * [Inhaltsautoren haben vollständige Kontrolle über die Hierarchie von Inhaltsfragmenten](#content-hierarchy) und könnten Änderungen vornehmen, die eine solche Abfrage ungültig machen würden.
   * Bei Abfragen sollten stattdessen Verweise auf Inhaltsfragmentmodelle mit dynamischen Abfrageparametern verwendet werden, um die Ergebnisse zu filtern, sodass sie die gewünschte Payload generieren.
* Für eine optimale Abfrageleistung sollten Sie immer persistente Abfragen in AEM verwenden. Diese werden später in der Tour erläutert.
* GraphQL ist deklarativ und folgt dem Motto „Fragen Sie nach genau dem, was Sie brauchen, und erhalten Sie genau das.“ Dies bedeutet, dass Sie beim Erstellen von GraphQL-Abfragen immer `select *`-Abfragen vermeiden sollten, die Sie möglicherweise in einer relationalen Datenbank erstellen würden.

Für eine [typische Headless-Implementierung mit AEM](#level-1) benötigt der Entwickler keine Programmierkenntnisse für AEM.

### Leistungsanforderungen {#performance-requirements}

Damit ein Projekt erfolgreich ist, muss die Leistung berücksichtigt werden, bevor Inhalte erstellt werden.

Sie müssen die Erwartungen Ihrer Benutzer/Besucher verstehen und für diese entwickeln. Legen Sie Service-Level-Ziele (SLOs) fest und messen Sie sie, um zu verstehen, ob Sie die Erwartungen Ihrer Benutzer erfüllen.

#### Traffic-Muster {#traffic-patterns}

Um Traffic und Traffic-Muster zu verstehen, beginnen Sie mit dem Sammeln dessen, was Sie aus der Vergangenheit wissen, und projizieren Sie dann auf das erwartete Wachstum in den nächsten paar Jahren. Einige der wichtigsten Variablen, die zu berücksichtigen sind:

* Wie viele API-Aufrufe pro Stunde/Tag/Monat erwarten Sie und besteht ein Potenzial für Spitzen und eine Saisonabhängigkeit?
* Wie viele verschiedene Inhaltsautoren gibt es?
* Wie viele Inhaltsautoren werden voraussichtlich gleichzeitig arbeiten?
* Wie häufig werden Inhaltsaktualisierungen vorgenommen?
* Wie viele Inhaltsmodelle werden benötigt?
* Wie viele Instanzen von Modellen werden benötigt?

#### Aktualisierungshäufigkeit {#update-frequency}

Oft haben verschiedene Bereiche von Erlebnissen unterschiedliche Häufigkeiten von Inhaltsaktualisierungen. Es ist wichtig, dass Sie hierüber informiert sind, damit Sie CDN- und Cache-Konfigurationen optimieren können. Dies ist auch ein wichtiger Input für die [Inhaltsarchitekten](#content-architects), da sie Modelle zur Darstellung Ihrer Inhalte entwerfen. Ziehen Sie dies in Betracht:

* Müssen bestimmte Inhaltstypen nach einem bestimmten Zeitraum ablaufen?
* Gibt es Elemente, die benutzerspezifisch sind und daher nicht zwischengespeichert werden können?

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der AEM Headless-Entwickler-Tour abgeschlossen haben, sollten Sie über die folgenden Kenntnisse verfügen:

* die Grundlagen der Headless-Funktionen von AEM verstehen,
* die Voraussetzungen für die Verwendung der Headless-Funktionen von AEM kennen,
* sich der Headless-Integrationsebenen von AEM bewusst sein.
* in der Lage sein, Ihr Projekt in Bezug auf den Umfang zu definieren.

Sie sollten Ihre AEM-Headless-Tour fortsetzen, indem Sie als Nächstes das Dokument [Weg zu Ihrem ersten Erlebnis mit AEM Headless](path-to-first-experience.md) lesen, in dem Sie erfahren, wie Sie die erforderlichen Tools einrichten und wie Sie mit der Modellierung Ihrer Daten in AEM beginnen können.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, mit dem nächsten Teil der Headless-Entwicklungs-Journey fortzufahren, indem Sie das Dokument [Der Weg zu Ihrem ersten Erlebnis mit AEM Headless](path-to-first-experience.md) lesen, aber im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige der in diesem Dokument erwähnten Konzepte vertiefen, die aber nicht erforderlich sind, um mit der Headless-Journey fortzufahren.

* [AEM Headless Übersetzungs-Tour](/help/journey-headless/translation/overview.md) – Diese Dokumentations-Tour vermittelt Ihnen ein umfassendes Verständnis der Headless-Technologie sowie davon, wie AEM Headless Inhalte bereitstellt und wie Sie sie übersetzen können.
* [Einführung in die Architektur von Adobe Experience Manager as a Cloud Service](/help/overview/architecture.md) – Grundlegendes zur Struktur von AEM as a Cloud Service
* [Einführung in AEM als Headless-CMS](/help/headless/introduction.md)
* Das [AEM-Entwicklerportal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
* [AEM Headless-Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de) – Nutzen Sie diese praxisnahen Tutorials, um herauszufinden, wie Sie die verschiedenen Optionen für die Bereitstellung von Inhalten an Headless-Endpunkte mit AEM verwenden können, und wählen Sie aus, was für Sie am besten geeignet ist.
* [Headless Content Management mit GraphQL-APIs](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses): In diesem Kurs erhalten Sie einen Überblick über die in AEM implementierte GraphQL-API. Eine Authentifizierung über Adobe ID ist erforderlich.
* [AEM-Handbuch zu WKND – GraphQL](https://github.com/adobe/aem-guides-wknd-graphql): Dieses GitHub-Projekt enthält Beispielprogramme zu den AEM-GraphQL-APIs.
* [Authoring-Konzepte](/help/sites-cloud/authoring/author-publish.md): Technische Dokumentation für die Authoring-Umgebung von AEM einschließlich Details zur Einrichtung von Autoren- und Veröffentlichungsinstanzen.
* [Veröffentlichen von Seiten](/help/sites-cloud/authoring/sites-console/publishing-pages.md): Technische Dokumentation zur Veröffentlichung von Inhalten auf AEM.
* [Benennungskonventionen](/help/implementing/developing/introduction/naming-conventions.md): Technische Dokumentation zu den Seitenbenennungsbeschränkungen in AEM.
* [Multi Site Manager und Übersetzung](/help/sites-cloud/administering/msm-and-translation.md): Technische Dokumentation zu den leistungsstarken Übersetzungsfunktionen von AEM.
* [AEM-Workflows](/help/sites-cloud/authoring/workflows/overview.md): Technische Dokumentation zur Automatisierung von Workflows in AEM
* [Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/overview.md): Technische Dokumentation für Inhaltsfragmente.
* [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/content-fragment-models.md): Technische Dokumentation für Inhaltsfragmentmodelle.
* [Technische Dokumentation zu GraphQL](https://graphql.org): Die GraphQL-Definition (externer Link).
* [GraphQL-API](/help/headless/graphql-api/content-fragments.md): Technische Dokumentation, in der erläutert wird, wie Anfragen für den Zugriff auf und die Bereitstellung von Inhaltsfragmenten erstellt werden.
* [Assets-REST-API](/help/assets/content-fragments/assets-api-content-fragments.md): Technische Dokumentation, in der erläutert wird, wie Inhaltsfragmente (und andere Assets) erstellt und geändert werden.
* [Persistente Abfragen](/help/headless/graphql-api/persisted-queries.md): Technische Dokumentation zu persistenten Abfragen in AEM.
* [Headful und Headless in AEM](/help/implementing/developing/headful-headless.md): Eine vollständige Diskussion der Headless-Integrationsebenen, die in AEM verfügbar sind.
* Die [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md) sind ebenfalls verfügbar.
