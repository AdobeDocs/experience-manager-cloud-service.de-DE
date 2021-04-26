---
title: Pfad zu Ihrem ersten Erlebnis mit AEM Kopflos
description: In diesem Teil der AEM Headless Developer-Journey erfahren Sie, wie Sie Ihre ersten praktischen Erfahrungen in der AEM implementieren, einschließlich Planungsüberlegungen, und lernen Best Practices kennen, um Ihren Weg so reibungslos wie möglich zu gestalten.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: 9fb18dbe60121f46dba1e11d4133e5264a6d538d
workflow-type: tm+mt
source-wordcount: '1899'
ht-degree: 0%

---


# Pfad zu Ihrem ersten Erlebnis mit AEM Headless {#path-to-first-experience}

>[!CAUTION]
>
>ARBEITEN IN FORTSCHRITTEN - Die Schaffung dieses Dokuments ist im Gange und sollte nicht als vollständig oder endgültig betrachtet werden und auch nicht für Produktionszwecke verwendet werden.

In diesem Teil der [AEM Headless Developer-Journey,](overview.md) werden Sie die Schritte zur Implementierung Ihrer ersten nutzlosen Erfahrung in AEM einschließlich Planungshinweise verstehen und außerdem Best Practices lernen, um Ihren Pfad so reibungslos wie möglich zu gestalten.

## Die Meldung bisher {#story-so-far}

Im vorherigen Dokument der AEM Journey [Erste Schritte mit AEM Headless als Cloud Service](getting-started.md) haben Sie die Grundtheorie gelernt, was ein kopless-CMS ist und sollten Sie jetzt:

* Machen Sie sich mit den Grundlagen AEM kostenlosen Funktionen vertraut.
* Erkennen Sie die Voraussetzungen für die Verwendung AEM kostenlosen Funktionen.
* Achten Sie auf AEM Ebene der kostenlosen Integration.
* Sie können Ihr Projekt in Bezug auf den Umfang definieren.

Dieser Artikel baut auf diesen Grundlagen auf, damit Sie verstehen, wie Sie Ihr eigenes AEM kopfloses Projekt vorbereiten.

## Vorgabe {#objective}

In diesem Dokument erfahren Sie, welche Schritte zur Implementierung des ersten Projekts erforderlich sind. Nach dem Lesen sollten Sie:

* Machen Sie sich mit wichtigen Planungshinweisen zum Entwerfen Ihrer Inhalte vertraut.
* Machen Sie sich mit den Schritten vertraut, die Sie zur Implementierung in AEM durchführen möchten.
* Erkennen Sie die erforderlichen Werkzeuge und AEM Konfigurationen.
* Machen Sie sich mit Best Practices vertraut, um die Journey ohne Kopf zu glätten, die Inhaltserstellung effizient zu gestalten und sicherzustellen, dass Inhalte schnell bereitgestellt werden.

## Voraussetzungen {#requirements}

Bevor Sie mit diesem Dokument fortfahren, stellen Sie sicher, dass Sie das vorherige Dokument in der AEM Headless Developer Journey, [Erste Schritte mit AEM Headless als Cloud Service](getting-started.md) überprüft haben.

* Erfüllen Sie die aufgelisteten Anforderungen.
* Überlegen Sie Ihre eigene Projektdefinition, einschließlich Umfang, Rollen und Leistung.

## Planung für Erfolg {#planning-for-success}

Um Ihr erstes AEM Projekt ohne Kopfdaten Beginn, müssen Sie sicherstellen, dass Sie über ein Inhaltsmodell verfügen, das die Personalisierung und die Aktualisierungen unterstützt, die Sie auf all Ihren Kanälen vornehmen möchten.

Neben AEM sollten Sie auch sicherstellen, dass beim Erstellen einer clientseitigen Umgebung eine ordnungsgemäße Entwicklungsanwendung eingerichtet ist, damit Sie den Client gegen API-Aufrufe testen können, die als Cloud Service AEM werden.

### Definieren von Inhaltsmodellen und APIs {#defining-models}

Sie möchten ein konsistentes Erlebnis fördern und personalisierte Kampagnen über Kanal hinweg verwalten, damit Sie jeden einzelnen Kanal und jede Oberfläche als eigene Inhaltsstruktur betrachten können, die Sie bereitstellen können. Es ist jedoch schwierig, jeden Kanal über ein eigenes Inhaltsmodell zu verfügen.

Stattdessen sollten Sie sich überlegen, wie Inhalte auf verschiedenen Oberflächen auf der Grundlage von Organisationsprinzipien wie Marken- und Produkthierarchien, Kategorien von Waren oder Oberflächen oder Stufen der Journey bezogen werden. Wenn Sie beispielsweise eine Reihe von Oberflächen haben, die eine bestimmte Automarke unterstützen, sollten Sie mit einem Inhaltsmodell für allgemeine Informationen, die für das gesamte Fahrzeug gelten, Beginn machen und dann kontextspezifische Elemente wie z. B. Inhalte haben, die benötigt werden, wenn das Auto anfängt, bis zu Serviceproblemen. Ein solches Modell wird eine Vererbung des allgemeinen Markeninhalts erzwingen, während Änderungen je nach dem jeweiligen Kontext möglich sind. Es hilft auch bei der zukünftigen Verwaltung von Aktualisierungen dieses Inhalts, da Sie die Kontrolle auf der Grundlage von Rollen wie dem Marketingmitarbeiter oder Produktmanager für die gesamte Automarke gegenüber einem Autor, der für das Erlebnis &quot;Startwagen&quot;verantwortlich ist, erzwingen können.

Sobald Sie über das Inhaltsmodell und eine klare Ansicht auf den verschiedenen Clients verfügen, auf die der Inhalt angezeigt werden soll, müssen Sie sicherstellen, dass die GraphQL/APIs, die mit dem Zugriff auf verschiedene Inhaltsmodelle verknüpft sind, für alle Clients veröffentlicht werden, die diese Inhalte benötigen. Es gibt verschiedene Optionen für den Zugriff auf bestimmte Inhalte. Sie können eine Anforderung für ein bestimmtes Inhaltselement anfordern, das statisch ist und die Zwischenspeicherung des Inhalts und eine höhere Leistung ermöglicht. Sie können auch Inhalte anfordern, die dynamisch generiert werden und mehr Verarbeitung erfordern. Stellen Sie sicher, dass Kunden die APIs nutzen, die für ihre geschäftlichen Anforderungen am effizientesten sind.

## Grundlegendes zu Ihren Umgebung {#understanding-environments}

Innerhalb AEM gibt es drei Arten von Umgebung: Entwicklung, Staging und Produktion.

Die Entwicklungs-Umgebung (mehrere) sind ein sicherer Ort zum Experimentieren und Ausprobieren von Ideen. Während der Anfangsphase des Projektes empfiehlt Adobe die Verwendung der Umgebung zur Entwicklung von Varianten der Inhaltsmodelle und zu prüfen, welche die gewünschte Ausgabe für die Oberflächen bereitstellen.

Die Staging-Umgebung für kostenlose Projekte dient zur Validierung neuer AEM Produktversionen, bevor sie in die Produktion eingeführt werden. Behalten Sie eine aktuelle Liste der Produktions-Inhaltsmodelle und eine Untergruppe des Inhalts bei, damit Sie JSON-Dateien zum Vergleich gerendert haben, die immer noch dieselbe Ausgabe bereitstellen, wenn Sie Änderungen vornehmen oder die AEM Version Änderungen einführt

In der Produktion erstellen und verwalten Inhaltsersteller ihre tatsächlichen Inhalte. Modelländerungen in der Produktion müssen sorgfältig und mit Rückwärtskompatibilität durchgeführt werden.

Während der Entwicklungsphase wird empfohlen, mit einer Entwicklungs- und Staging-Umgebung zu arbeiten. Wenn Sie zu Leistungstests übergehen, sollten Sie zur Produktions-Umgebung wechseln.

### Zusammenarbeit von Entwicklern und Inhaltserstellern {#cooperation}

Entwickler benötigen eine AEM Umgebung zur Entwicklung mit den ausgefüllten Inhaltsmodellen. Der Entwickler entwickelt den Client, der Inhalte aus AEM kopflosen nutzt, da die Inhaltsersteller den Inhalt noch erstellen. Deshalb sind die API-Definitionen wirklich wichtig. Durch die Nutzung des AEM SDK kann der Entwickler einen Test-Haken erstellen, damit Client- und Komponententests erstellt werden können, um sicherzustellen, dass der Client den Inhalt ordnungsgemäß wiedergeben kann.

Inhaltsersteller erstellen Inhalte auf der Grundlage der Inhaltsmodelle, die auf der Staging-Umgebung definiert wurden. Mithilfe des Authoring-Tools für Inhaltsfragmente erstellt der Autor ein neues Inhaltsfragment oder bearbeitet ein vorhandenes Inhaltsfragment. Vor der Veröffentlichung kann der Autor Vorschauen darüber vornehmen, wie das Inhaltsmodell im Client aussehen wird, indem er mit dem Entwickler zusammenarbeitet, um das Inhaltsmodell in die Entwicklung zu verschieben, oder eine Entwickler-Umgebung einrichten, damit Autoren die Vorschau erhalten, wie es im Client aussehen würde.

## Einrichtung {#setup}

Bevor Sie mit dem Kopflosen in AEM beginnen, müssen Sie sicherstellen, dass alle erforderlichen Funktionen aktiviert sind. Dieser Abschnitt beschreibt die erforderlichen Schritte. Die eigentlichen Schritte zur Erfüllung dieser Schritte werden weiter unten im Journey [AEM Headless Developer beschrieben.](#overview.md)

Optional können Sie auch auf die [zusätzlichen Ressourcen](#additional-resources) verweisen, um weitere Informationen zu den einzelnen Themen zu erhalten.

### Konfiguration {#configuration}

1. Inhaltsfragmente aktivieren
1. GraphQL aktivieren
1. Einrichten des Headless SDK

## Implementierung der ersten AEM Headless-App

Dies ist ein Überblick darüber, was für die Implementierung der ersten kopflosen App mit AEM zur Bereitstellung Ihrer Inhalte erforderlich ist. Wie Sie diese Schritte durchführen, wird in späteren Teilen der Headless Developer Journey ausführlich beschrieben.

1. Erstellen von Inhaltsfragmentmodellen
1. Inhaltsfragmente erstellen
1. Abfrage von Inhalten mit GraphQL

## Best Practices {#best-practices}

Ein übersichtliches Projekt ist nicht nur erfolgreich, weil die Technologie implementiert ist, sondern auch dank guter Planung und Projektverwaltung. Im Folgenden finden Sie eine Reihe bewährter Verfahren, die sowohl Autoren als auch Entwickler bei der Planung Ihres Projekts berücksichtigen sollten.

### Organisieren Ihres Inhalts {#organizing-content}

* Machen Sie Ihre Struktur so komplex wie nötig, aber halten Sie sie so einfach wie möglich. Einfachere Inhaltsstrukturen helfen, die Verwaltung von Inhalten zu optimieren und die Systemleistung zu verbessern.
* Priorisieren Sie die Wiederverwendung von Inhalten in Ihrer Strategie. Erstellen Sie Untermodelle und Inhaltsreferenzen, die über mehrere Modelle und Kanal auf höherer Ebene hinweg wiederverwendet werden können.
* Machen Sie Inhaltsstrukturen so selbsterklärend wie möglich, damit Inhaltsersteller schnell lernen und sich an Authoring-Aufgaben anpassen können.
* Wenn Sie Zugriffsbeschränkungen haben, versuchen Sie, Ihr Inhaltsmodell an die Zugriffsanforderungen anzupassen.
* Wenn Sie Zugriffsanforderungen haben, sollten diese Ihre Inhaltshierarchie fördern. Gruppieren Sie Inhalte zusammen, die von derselben Personengruppe bearbeitet werden.
* Gruppieren Sie ähnliche Inhalte in einem Ordner.
   * Es ist wahrscheinlicher, dass ein Inhaltsautor vorhandene Inhalte kopieren und einfügen wird, um neue Inhalte zu erstellen. Dadurch, dass dies im selben Ordner erfolgt, wird es effizienter.
   * AEM erlaubt das Festlegen erlaubter Modelle pro Ordner, sodass die Schaltfläche **Neu erstellen** nur die Modelle anzeigt, die an diesem Speicherort unterstützt werden.
* Die Erstellung neuer Inhaltsfragmente im Inline-Inhaltsfragment-Editor kann vereinfacht werden, wenn der Stammordner im Modell festgelegt ist. Dann muss der Praktiker keinen Ort auswählen, sondern nur einen Namen angeben und den neuen Verweis bearbeiten können.

### Erstellen von Inhalten {#authoring}

* Bei Kanal-spezifischen Inhaltsversionen sollten Sie Inhaltsfragmentvarianten verwenden. Variationen werden mit dem Übergeordnet Inhalt synchronisiert, um die Verwaltung von Inhaltsänderungen zu optimieren.
* Laden Sie andere Inhaltshersteller ein, Inhalte zu überprüfen und Feedback mit Anmerkungen und Kommentaren zu geben, die im Inhaltsfragmenteditor verfügbar sind und global über Fragmente in Inhaltsfragmenten in der Admin-Konsole verfügbar sind.
* Lassen Sie die Dinge mit so wenigen obligatorischen Elementen wie möglich in Bewegung. Obligatorische Elemente können den Workflow blockieren.

### Authoring globaler Inhalte {#localization}

* Regeln und Verwaltung für die Übersetzung von Inhalten festlegen. Um die Systembelastung zu verringern, müssen Sie die Übersetzung als asynchronen Prozess einrichten, der in längeren Abständen ausgeführt werden kann. Lassen Sie sich Zeit für die Qualitätssicherung und Fehlerbehebung der lokale Anpassung.
* Nutzen Sie alle Funktionen Ihres Übersetzungstechnologiesystems, die Sie in AEM wie Translation Memory integrieren können.
* Verstehen Sie, ob Rich-Media-Inhalte wie Bilder und Videos lokale Anpassung benötigen.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun die AEM Journey zum kostenlosen Entwickler abgeschlossen haben, sollten Sie:

* Machen Sie sich mit wichtigen Planungshinweisen zum Entwerfen Ihrer Inhalte vertraut.
* Machen Sie sich mit den Schritten vertraut, die Sie zur Implementierung in AEM durchführen möchten.
* Erkennen Sie die erforderlichen Werkzeuge und AEM Konfigurationen.
* Machen Sie sich mit Best Practices vertraut, um die Journey ohne Kopf zu glätten, die Inhaltserstellung effizient zu gestalten und sicherzustellen, dass Inhalte schnell bereitgestellt werden.

Sie sollten Ihre AEM Journey ohne Kopfdaten fortsetzen, indem Sie das Dokument [Wie Sie Ihren Inhalt als AEM Inhaltsmodelle](model-your-content.md) modellieren, in dem Sie lernen, wie Sie Ihre Inhaltsstruktur in AEM modellieren.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, mit dem nächsten Teil der Journey zur kostenlosen Entwicklung fortzufahren, indem Sie das Dokument [Wie Sie Ihre Inhalte als AEM Content-Modelle modellieren, überprüfen. Die folgenden sind jedoch einige zusätzliche optionale Ressourcen, die einen tieferen Einstieg in einige der in diesem Dokument erwähnten Konzepte ermöglichen, aber sie müssen nicht mit der kopflosen Journey fortfahren.](model-your-content.md)

* [Headless Development for AEM Sites als Cloud Service](/help/implementing/developing/headless/introduction.md)  - Eine schnelle Einführung in die Ausrichtung des AEM Headless-Entwicklers mit den erforderlichen Funktionen
* [AEM Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de)  ohne Kopf - Nutzen Sie diese praktischen Übungen, um zu untersuchen, wie Sie die verschiedenen Optionen für die Bereitstellung von Inhalten an kopflosen Endpunkten mit AEM nutzen können, und zu entscheiden, was für Sie am besten geeignet ist.
* [Headless-Content-Management mit GraphQL-APIs](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses)  - In diesem Kurs erhalten Sie einen Überblick über die in AEM implementierte GraphQL-API. Die Authentifizierung über AdobeID ist erforderlich.
* [AEM Guides WKND - GraphQL](https://github.com/adobe/aem-guides-wknd-graphql)  - Dieses GitHub-Projekt enthält Beispielanwendungen, die AEM GraphQL APIs hervorheben.
* [Einführung in die Architektur von Adobe Experience Manager als Cloud Service](/help/core-concepts/architecture.md)  - Ein vollständiger Überblick über AEM Architektur
* [Kopfloses Handbuch](/help/implementing/developing/headless/introduction.md#getting-started)  für erste Schritte - Eine schnelle Einführung in AEM kostenlose Funktionen für Benutzer, die bereits AEM wissen.
* [Erstellen von Inhaltsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md)  - Technische Dokumentation zu Inhaltsfragmentmodellen
* [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md)  erstellen - Technische Dokumentation zu Inhaltsfragmenten
* [Abfrage mit GraphQL](/help/assets/content-fragments/graphql-api-content-fragments.md)  - Technische Dokumentation zur GraphQL API
