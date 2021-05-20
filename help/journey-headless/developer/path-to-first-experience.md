---
title: Pfad zu Ihrem ersten Erlebnis mit AEM Headless
description: In diesem Teil der AEM Headless-Entwickler-Journey erfahren Sie, wie Sie Ihre ersten Headless-Erlebnisse in AEM implementieren, einschließlich Planungsüberlegungen, und lernen Best Practices kennen, um Ihren Pfad so reibungslos wie möglich zu gestalten.
source-git-commit: ddd320ae703225584d4a2055d0f882d238d60987
workflow-type: tm+mt
source-wordcount: '1991'
ht-degree: 0%

---


# Pfad zu Ihrem ersten Erlebnis mit AEM Headless {#path-to-first-experience}

In diesem Teil der [AEM Headless-Entwickler-Journey,](overview.md) werden Sie die Schritte zur Implementierung Ihres ersten Headless-Erlebnisses in AEM verstehen, einschließlich Planungsüberlegungen und Best Practices lernen, um Ihren Pfad so reibungslos wie möglich zu gestalten.

## Die Geschichte bisher {#story-so-far}

Im vorherigen Dokument der AEM Headless-Journey, [Erste Schritte mit AEM Headless als Cloud Service](getting-started.md) haben Sie die grundlegende Theorie gelernt, was ein Headless-CMS ist und sollten jetzt:

* Machen Sie sich mit den Grundlagen AEM Headless-Funktionen vertraut.
* Machen Sie sich mit den Voraussetzungen für die Verwendung AEM Headless-Funktionen vertraut.
* Beachten Sie AEM Headless-Integrationsstufen.
* Sie können Ihr Projekt in Bezug auf den Umfang definieren.

Dieser Artikel baut auf diesen Grundlagen auf, sodass Sie verstehen, wie Sie Ihr eigenes AEM Headless-Projekt vorbereiten.

## Vorgabe {#objective}

In diesem Dokument erfahren Sie, welche Schritte zur Implementierung Ihres ersten Projekts erforderlich sind. Nach dem Lesen sollten Sie Folgendes tun:

* Machen Sie sich mit wichtigen Planungsanforderungen für die Erstellung Ihres Inhalts vertraut.
* Machen Sie sich mit den Schritten zur Implementierung von Headless in AEM vertraut.
* Sie müssen wissen, welche Tools und AEM benötigt werden.
* Machen Sie sich mit Best Practices vertraut, um die Headless-Journey reibungslos zu gestalten, die Inhaltsgenerierung effizient zu gestalten und sicherzustellen, dass Inhalte schnell bereitgestellt werden.

## Voraussetzungen {#requirements}

Bevor Sie mit diesem Dokument fortfahren, stellen Sie sicher, dass Sie das vorherige Dokument in der AEM Headless Developer-Journey, [Erste Schritte mit AEM Headless als Cloud Service](getting-started.md) überprüft haben, um sicherzustellen, dass Sie:

* Erfüllen Sie die aufgelisteten Anforderungen.
* Sie haben Ihre eigene Projektdefinition einschließlich Umfang, Rollen und Leistung in Erwägung gezogen.

## Planung für Erfolg {#planning-for-success}

Um Ihr erstes AEM Headless-Projekt zu starten, müssen Sie sicherstellen, dass Sie über ein Inhaltsmodell verfügen, das die Personalisierung und Aktualisierungen unterstützt, die Sie über alle Kanäle hinweg vornehmen möchten.

Zusätzlich zu AEM möchten Sie auch sicherstellen, dass Sie eine geeignete Entwicklungsumgebung eingerichtet haben, wenn Sie eine clientseitige Anwendung erstellen, damit Sie Ihren Client anhand von API-Aufrufen an AEM als Cloud Service testen können.

### Definieren von Inhaltsmodellen und APIs {#defining-models}

Sie möchten ein konsistentes Erlebnis schaffen und personalisierte Kampagnen kanalübergreifend verwalten, sodass Sie jeden einzelnen Kanal und jede einzelne Oberfläche als eigene Inhaltsstruktur betrachten können, die Sie bereitstellen können. Die Pflege jedes Kanals mit seinem eigenen Inhaltsmodell ist jedoch schwierig.

Stattdessen sollten Sie überlegen, wie Inhalte auf verschiedenen Oberflächen auf der Grundlage von Organisationsprinzipien wie Marken- und Produkthierarchien, Warenkategorien oder Oberflächen oder Schritte im Journey zugeordnet werden. Wenn Sie beispielsweise über eine Reihe von Oberflächen verfügen, die eine bestimmte Automarke unterstützen, die Sie herstellen, möchten Sie vielleicht mit einem Inhaltsmodell für allgemeine Informationen beginnen, die für das gesamte Auto gelten würden, und dann kontextspezifische Elemente wie Inhalte haben, die benötigt werden, wenn das Auto anfängt, wenn Serviceprobleme auftreten. Mit einem solchen Modell wird eine Vererbung des allgemeinen Markeninhalts von Kraftfahrzeugen erzwungen und gleichzeitig Verschiebungen basierend auf bestimmten Rahmenbedingungen ermöglicht. Es hilft auch bei der zukünftigen Verwaltung von Aktualisierungen dieses Inhalts, da Sie die Kontrolle anhand von Rollen erzwingen können, wie z. B. dem gesamten Marketing- oder Produktmanager für die gesamte Automarke im Vergleich zu einem Autor, der für das Erlebnis &quot;Startauto&quot;verantwortlich ist.

Sobald Sie über das Inhaltsmodell und eine klare Ansicht auf den verschiedenen Clients verfügen, auf denen der Inhalt angezeigt werden muss, müssen Sie sicherstellen, dass die GraphQL/APIs, die mit dem Zugriff auf verschiedene Inhaltsmodelle verknüpft sind, für alle Clients veröffentlicht werden, die diese Inhalte benötigen. Es gibt verschiedene Optionen für den Zugriff auf bestimmte Inhalte. Sie können ein bestimmtes Inhaltselement anfordern, das statisch ist und das das Zwischenspeichern des Inhalts und eine höhere Leistung ermöglicht. Sie können auch dynamisch generierte Inhalte anfordern, die mehr Verarbeitung erfordern. Stellen Sie sicher, dass Kunden die APIs nutzen, die für ihre geschäftlichen Anforderungen am effizientesten sind.

## Verstehen Ihrer Umgebungen {#understanding-environments}

AEM gibt es drei Arten von Umgebungen: Entwicklung, Staging und Produktion.

Die Entwicklungsumgebungen (Sie können mehrere davon haben) sind ein sicherer Ort, um Ideen auszuprobieren und auszuprobieren. In der Anfangsphase des Projekts empfiehlt Adobe die Verwendung der Entwicklungsumgebungen, um Variationen von Inhaltsmodellen auszuprobieren und zu sehen, welche die gewünschte Ausgabe für die Oberflächen liefern.

Die Staging-Umgebung für Headless-Projekte wird verwendet, um neue AEM Produktversionen zu validieren, bevor sie in die Produktion eingeführt werden. Halten Sie eine aktuelle Liste der Produktionsinhaltsmodelle dort und eine Untergruppe des Inhalts bereit, damit Sie JSON-Dateien zum Vergleich von ihnen rendern lassen können, die immer noch dieselbe Ausgabe liefern, wenn Sie Änderungen vornehmen oder die AEM Version Änderungen einführt.

In der Produktion erstellen und verwalten Inhaltsautoren ihre tatsächlichen Inhalte. Modelländerungen in der Produktion müssen mit Vorsicht und unter Berücksichtigung der Abwärtskompatibilität durchgeführt werden.

In der Entwicklungsphase wird empfohlen, mit einer Entwicklungs- und Staging-Umgebung zu arbeiten. Wenn Sie zum Leistungstest übergehen, sollten Sie in die Produktionsumgebung wechseln.

### Zusammenarbeit von Entwicklern und Inhaltsautoren {#cooperation}

Entwickler benötigen eine AEM Entwicklungsumgebung mit den ausgefüllten Inhaltsmodellen. Der Entwickler entwickelt den Client, der Inhalte von AEM Headless nutzt, da die Inhaltsautoren den Inhalt noch erstellen. Deshalb sind die API-Definitionen sehr wichtig. Mithilfe des AEM SDK kann der Entwickler einen Test-Hook erstellen, damit Client- und Unit-Tests erstellt werden können, um sicherzustellen, dass der Client den Inhalt ordnungsgemäß rendern kann.

Inhaltsautoren erstellen Inhalte auf der Grundlage der Inhaltsmodelle, die in der Staging-Umgebung definiert wurden. Mit dem Authoring-Tool für Inhaltsfragmente erstellt der Autor ein neues Inhaltsfragment oder bearbeitet ein vorhandenes Inhaltsfragment. Vor der Veröffentlichung kann der Autor eine Vorschau des Inhalts im Client anzeigen, indem er mit dem Entwickler zusammenarbeitet, um das Inhaltsmodell auf die Entwicklung zu pushen, oder eine Entwicklungsumgebung einrichten, damit Autoren eine Vorschau des Inhalts im Client anzeigen können.

## Einrichtung {#setup}

Bevor Sie mit Headless in AEM beginnen, müssen Sie sicherstellen, dass alle erforderlichen Funktionen aktiviert sind. In diesem Abschnitt wird beschrieben, was erforderlich ist. Die eigentlichen Schritte zum Erfüllen dieser Schritte werden weiter unten im Journey [AEM Headless Developer beschrieben.](#overview.md)

Optional können Sie auch die [zusätzlichen Ressourcen](#additional-resources) konsultieren, um weitere Informationen zu den einzelnen Themen zu erhalten.

### Konfiguration {#configuration}

1. Aktivieren von Inhaltsfragmenten
1. GraphQL aktivieren
1. Einrichten des Headless-SDK

## Implementieren der ersten AEM Headless App

Dies ist ein Überblick darüber, was zur Implementierung Ihrer ersten Headless App mit AEM zur Bereitstellung Ihrer Inhalte erforderlich ist. Wie diese Schritte ausgeführt werden, wird in späteren Teilen der Headless Developer Journey ausführlich beschrieben.

1. Erstellen von Inhaltsfragmentmodellen
1. Erstellen von Inhaltsfragmenten
1. Inhalt mit GraphQL abfragen

## Best Practices {#best-practices}

Ein Headless-Projekt ist nicht nur aufgrund der implementierten Technologie erfolgreich, sondern auch aufgrund guter Planung und Projektführung. Im Folgenden finden Sie eine Reihe von Best Practices, die sowohl für Inhaltsautoren als auch für Entwickler bei der Planung Ihres Projekts beachtet werden sollten.

### Organisieren Ihres Inhalts {#organizing-content}

* Bauen Sie Ihre Struktur so komplex wie nötig auf, aber halten Sie sie so einfach wie möglich. Einfachere Inhaltsstrukturen helfen bei der Optimierung der Inhaltsverwaltung und der Verbesserung der Systemleistung.
* Priorisieren Sie die Wiederverwendung von Inhalten in Ihrer Strategie. Erstellen Sie Untermodelle und Inhaltsreferenzen, die über mehrere Modelle und Kanäle auf höherer Ebene hinweg wiederverwendet werden können.
* Machen Sie Inhaltsstrukturen so selbsterklärend wie möglich, damit Inhaltsautoren lernen und sich schnell an Bearbeitungsaufgaben anpassen können.
* Wenn Sie Zugriffsbeschränkungen haben, versuchen Sie, Ihr Inhaltsmodell an die Zugriffsanforderungen anzupassen.
* Wenn Sie Zugriffsanforderungen haben, sollten diese Ihre Inhaltshierarchie voranbringen. Gruppieren Sie Inhalte, die von derselben Personengruppe bearbeitet werden.
* Gruppieren Sie ähnliche Inhalte in einem Ordner.
   * Wahrscheinlicher ist, dass ein Inhaltsautor vorhandenen Inhalt kopieren und einfügen wird, um neue Inhalte zu erstellen. Dadurch wird es effizienter, dies im selben Ordner zu tun.
   * AEM ermöglicht es, zulässige Modelle pro Ordner festzulegen, sodass die Schaltfläche **Neu erstellen** nur die Modelle anzeigt, die an diesem Speicherort unterstützt werden.
* Die Erstellung neuer Inhaltsfragmente im Inline-Inhaltsfragment-Editor kann vereinfacht werden, wenn der Stammordner im Modell festgelegt ist. Dann muss der Praktiker keinen Ort auswählen, sondern nur einen Namen angeben und die neue Referenz bearbeiten.

### Inhaltserstellung {#authoring}

* Verwenden Sie für kanalspezifische Versionen Ihres Inhalts Inhaltsfragmentvarianten. Varianten werden mit den Übergeordneten Inhalten synchronisiert, um die Verwaltung von Inhaltsänderungen zu optimieren.
* Laden Sie andere Inhaltsanbieter ein, Inhalte zu überprüfen und Feedback mit Anmerkungen und Kommentaren zu geben, die im Inhaltsfragment-Editor verfügbar sind und global über Fragmente in der Admin Console von Inhaltsfragmenten hinweg verfügbar sind.
* Lassen Sie die Dinge so wenig wie möglich mit obligatorischen Elementen in Bewegung. Obligatorische Elemente können den Workflow blockieren.

### Verfassen globaler Inhalte {#localization}

* Legen Sie Regeln und Richtlinien für die Übersetzung von Inhalten fest. Um die Systemlast zu verringern, richten Sie die Übersetzung als asynchronen Prozess ein, der in längeren Abständen ausgeführt werden kann. Lassen Sie Zeit für die Qualitätskontrolle und Fehlerbehebung bei der Lokalisierung.
* Nutzen Sie alle Funktionen Ihres Übersetzungstechnologiesystems, die Sie in AEM integrieren können, wie z. B. Translation Memory.
* Erfahren Sie, ob Rich-Media-Inhalte wie Bilder und Videos lokalisiert werden müssen.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der AEM Headless-Entwickler-Journey abgeschlossen haben, sollten Sie:

* Machen Sie sich mit wichtigen Planungsanforderungen für die Erstellung Ihres Inhalts vertraut.
* Machen Sie sich mit den Schritten zur Implementierung von Headless in AEM vertraut.
* Sie müssen wissen, welche Tools und AEM benötigt werden.
* Machen Sie sich mit Best Practices vertraut, um die Headless-Journey reibungslos zu gestalten, die Inhaltsgenerierung effizient zu gestalten und sicherzustellen, dass Inhalte schnell bereitgestellt werden.

Wir möchten, dass Sie auf diesem grundlegenden Wissen aufbauen, um die Macht und Flexibilität von AEM Headless zu verstehen, damit Sie es für Ihre eigenen Projekte nutzen können. Dazu haben Sie Optionen.

### Wählen Sie Ihr eigenes Abenteuer {#choose-your-path}

Egal, welcher Lernstil Sie haben: Adobe will, dass Sie erfolgreich sind, wenn Sie mit Ihrem AEM Headless-Projekt beginnen.

* Wenn Sie weiterhin **mehr über Headless-Konzepte und AEM Headless-Technologien** erfahren möchten, sollten Sie Ihre AEM Headless-Journey fortsetzen, indem Sie sich das Dokument [So modellieren Sie Ihren Inhalt als AEM Inhaltsmodelle](model-your-content.md) ansehen. Hier erfahren Sie, wie Sie Ihre Inhaltsstruktur in AEM modellieren.
* Wenn Sie **lernen möchten, indem Sie** ausführen, können Sie zum [Tutorial Erste Schritte mit AEM Headless-Hand-On-Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) springen, in dem Sie direkt in AEM Headless-Entwicklung springen, indem Sie ein einfaches Projekt implementieren, um AEM Headless-Inhalte anzuzeigen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, zum nächsten Teil der Headless-Development-Journey zu wechseln, indem Sie das Dokument [So modellieren Sie Ihre Inhalte als AEM Inhaltsmodelle ansehen.](model-your-content.md) Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige der in diesem Dokument erwähnten Konzepte genauer untersuchen. Sie müssen jedoch nicht mit dem Headless-Journey weitermachen.

* [Headless-Entwicklung für AEM Sites as a Cloud Service](/help/implementing/developing/headless/introduction.md)  - Eine schnelle Einführung, um den AEM Headless-Entwickler mit den erforderlichen Funktionen auszurichten
* [AEM Headless-Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de)  - Nutzen Sie diese praxisnahen Tutorials, um zu untersuchen, wie Sie die verschiedenen Optionen für die Bereitstellung von Inhalten an Headless-Endpunkte mit AEM nutzen können, und wählen Sie aus, was für Sie am besten geeignet ist.
* [Headless Content Management mit GraphQL-APIs](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses)  - In diesem Kurs erhalten Sie einen Überblick über die in AEM implementierte GraphQL-API. Eine Authentifizierung über Adobe ID ist erforderlich.
* [AEM Guides WKND - GraphQL](https://github.com/adobe/aem-guides-wknd-graphql)  - Dieses GitHub-Projekt enthält Beispielanwendungen, die AEM GraphQL-APIs hervorheben.
* [Einführung in die Architektur von Adobe Experience Manager as a Cloud Service](/help/core-concepts/architecture.md)  - Ein vollständiger Überblick über AEM Architektur
* [Headless Erste Schritte](/help/implementing/developing/headless/introduction.md#getting-started)  - Eine schnelle Einführung in AEM Headless-Funktionen für Benutzer, die bereits über AEM verfügen.
* [Erstellen von Inhaltsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md)  - Technische Dokumentation zu Inhaltsfragmentmodellen
* [Erstellen von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)  - Technische Dokumentation zu Inhaltsfragmenten
* [Abfrageinhalt mit GraphQL](/help/assets/content-fragments/graphql-api-content-fragments.md)  - Technische Dokumentation zur GraphQL-API
