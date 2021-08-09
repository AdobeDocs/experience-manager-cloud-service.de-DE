---
title: Gestalten Ihres ersten Erlebnisses mit AEM Headless
description: In diesem Teil der AEM Headless-Entwickler-Tour erfahren Sie, wie Sie Ihre ersten Headless-Erlebnisse in AEM implementieren, einschließlich Planungsüberlegungen, und lernen Best Practices kennen, die für möglichst reibungslose Abläufe sorgen.
source-git-commit: ddd320ae703225584d4a2055d0f882d238d60987
workflow-type: ht
source-wordcount: '1991'
ht-degree: 100%

---


# Gestalten Ihres ersten Erlebnisses mit AEM Headless {#path-to-first-experience}

In diesem Teil der [AEM Headless-Entwickler-Tour](overview.md) erfahren Sie, wie Sie Ihre ersten Headless-Erlebnisse in AEM implementieren, einschließlich Planungsüberlegungen, und lernen Best Practices kennen, die für möglichst reibungslose Abläufe sorgen.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument zur AEM Headless-Entwickler-Tour, [Erste Schritte mit AEM as a Cloud Service](getting-started.md), haben Sie sich mit den Grundlagen zu Headless-CMS-Lösungen vertraut gemacht. Nun verfügen Sie über folgenden Voraussetzungen:

* Grundlegendes Verständnis der AEM Headless-Funktionen
* Kenntnis der Voraussetzungen für die Verwendung von AEM Headless-Funktionen
* Verständnis der AEM Headless-Integrationsebenen
* in der Lage sein, Ihr Projekt in Bezug auf den Umfang zu definieren.

Dieser Artikel baut auf diesen Grundlagen auf, sodass Sie verstehen, wie Sie Ihr eigenes AEM Headless-Projekt vorbereiten.

## Ziele {#objective}

In diesem Dokument erfahren Sie, welche Schritte zur Implementierung Ihres ersten Projekts erforderlich sind. Nach dem Lesen sollten Sie über folgende Voraussetzungen verfügen:

* Kenntnis der wichtigen Planungsanforderungen für die Gestaltung Ihrer Inhalte
* Verständnis der Schritte zur Implementierung von Headless-Technologie in AEM
* Kenntnis darüber, welche Tools und AEM-Konfigurationen erforderlich sind
* Kenntnis der Best Practices, mit denen Sie für reibungslose Headless-Abläufe sorgen, die Inhaltsgenerierung effizient gestalten und die schnelle Bereitstellung von Inhalten sicherstellen können

## Voraussetzungen {#requirements}

Bevor Sie mit diesem Dokument fortfahren, vergewissern Sie sich, dass Sie das vorherige Dokument zur AEM Headless-Entwickler-Tour, [Erste Schritte mit AEM as a Cloud Service](getting-started.md) gelesen haben. So stellen Sie Folgendes sicher:

* Sie erfüllen die aufgelisteten Anforderungen.
* Sie haben Ihre eigene Projektdefinition einschließlich Umfang, Rollen und Leistung berücksichtigt.

## Planen für den Erfolg {#planning-for-success}

Um Ihr erstes AEM Headless-Projekt zu starten, müssen Sie sicherstellen, dass Sie über ein Inhaltsmodell verfügen, das die Personalisierung und Aktualisierungen unterstützt, die Sie über alle Kanäle hinweg vornehmen möchten.

Unabhängig von AEM sollten Sie auch sicherstellen, dass Sie eine geeignete Entwicklungsumgebung eingerichtet haben, wenn Sie ein Client-seitiges Programm erstellen, damit Sie Ihren Client mit API-Aufrufen an AEM as a Cloud Service testen können.

### Definieren von Inhaltsmodellen und APIs {#defining-models}

Sie möchten konsistente Erlebnisse gestalten und personalisierte Kampagnen kanalübergreifend verwalten, sodass Sie jeden einzelnen Kanal und jede einzelne Oberfläche als eigene Inhaltsstruktur für die Bereitstellung betrachten können. Allerdings wäre es schwierig, für jeden Kanal ein eigenes Inhaltsmodell zu verwalten.

Stattdessen sollten Sie sich überlegen, wie Inhalte auf verschiedenen Oberflächen basierend auf Organisationsprinzipien wie Marken- und Produkthierarchien, Waren- oder Oberflächenkategorien oder Schritten in der Customer Journey zusammenhängen. Wenn Sie beispielsweise über eine Reihe von Oberflächen zur Betreuung einer bestimmten von Ihnen hergestellten Automarke verfügen, empfiehlt es sich, mit einem Inhaltsmodell für allgemeine Informationen zu beginnen, die für das gesamte Fahrzeug gelten, und dann zu kontextspezifischeren Elemente überzugehen, beispielsweise Inhalte, die benötigt werden, wenn das Fahrzeug in Betrieb genommen wird oder in die Werkstatt muss. Mit einem solchen Modell wird eine Vererbung der allgemeinen Markeninhalte erzwungen und gleichzeitig Verschiebungen basierend auf bestimmten Kontext ermöglicht. Das Modell hilft auch bei der späteren Verwaltung von Aktualisierungen dieser Inhalte, da Sie die Kontrolle auf der Grundlage von Rollen durchsetzen können, wie z. B. dem übergeordneten Marketer oder Produkt-Manager für die gesamte Automarke im Vergleich zu dem Autor, der für das „Starterlebnis“ verantwortlich ist.

Sobald Sie über ein Inhaltsmodell und eine klare Übersicht über die verschiedenen Clients verfügen, auf denen die Inhalte angezeigt werden sollen, müssen Sie sicherstellen, dass die GraphQL-APIs, die mit dem Zugriff auf verschiedene Inhaltsmodelle verbunden sind, für alle Clients veröffentlicht werden, die diese Inhalte benötigen. Es gibt verschiedene Optionen für den Zugriff auf bestimmte Inhalte. Sie können einen bestimmten Inhalt anfordern, der statisch ist, wodurch das Caching des Inhalts ermöglicht und die Performance verbessert wird. Sie können auch dynamisch generierte Inhalte anfordern, die eine aufwendigere Verarbeitung erfordern. Stellen Sie sicher, dass Kunden die APIs nutzen, die für ihre geschäftlichen Anforderungen am effizientesten sind.

## Grundlegendes zu Ihren Umgebungen {#understanding-environments}

In AEM gibt es drei Arten von Umgebungen: Entwicklungs-, Staging- und Produktionsumgebungen.

Die Entwicklungsumgebungen (davon können Sie mehrere haben) sind ein sicherer Ort, um Ideen auszuprobieren und zu experimentieren. In der Anfangsphase eines Projekts empfiehlt Adobe die Verwendung der Entwicklungsumgebungen, um Variationen von Inhaltsmodellen auszuprobieren und zu sehen, welche die gewünschte Ausgabe für die Oberflächen liefern.

Die Staging-Umgebung für Headless-Projekte wird verwendet, um neue AEM-Produktversionen zu validieren, bevor sie in die Produktion übergehen. Halten Sie eine aktuelle Liste der Produktions-Inhaltsmodelle dort und eine Untergruppe der Inhalte vor, damit Sie JSON-Dateien zum Vergleich rendern lassen können, die immer noch dieselbe Ausgabe liefern, wenn Sie Änderungen vornehmen oder mit einer AEM-Version Änderungen eingeführt werden.

In der Produktion erstellen und verwalten Inhaltsautoren ihre eigentlichen Inhalte. Modelländerungen in der Produktion müssen umsichtig und unter Berücksichtigung der Abwärtskompatibilität durchgeführt werden.

In der Entwicklungsphase wird empfohlen, mit einer Entwicklungs- und Staging-Umgebung zu arbeiten. Wenn Sie zu den Performance-Tests übergehen, sollten Sie in die Produktionsumgebung wechseln.

### Zusammenarbeit von Entwicklern und Inhaltsautoren {#cooperation}

Entwickler benötigen eine AEM-Entwicklungsumgebung mit den ausgefüllten Inhaltsmodellen. Die Entwickler entwickeln den Client, der Inhalte von AEM Headless nutzt, während die Inhaltsautoren noch mit der Inhaltserstellung beschäftigt sind. Aus diesem Grund sind die API-Definitionen sehr wichtig. Mithilfe des AEM-SDK können Entwickler einen Test-Hook erstellen. Damit lassen sich Client- und Unit-Tests entwickeln, um sicherzustellen, dass der Client die Inhalte ordnungsgemäß rendern kann.

Inhaltsautoren erstellen Inhalte auf Basis der Inhaltsmodelle, die in der Staging-Umgebung definiert wurden. Mit dem Authoring-Tool für Inhaltsfragmente erstellen Autoren neue Inhaltsfragmente bzw. bearbeiten vorhandene Inhaltsfragmente. Vor der Veröffentlichung können Autoren eine Vorschau der Inhalte im Client anzeigen. Dazu müssen sie mit den Entwicklern zusammenarbeiten, um das Inhaltsmodell in die Entwicklungsumgebung zu übertragen oder eine spezielle Entwicklungsumgebung einzurichten, damit die Autoren in der Vorschau anzeigen können, wie die Inhalte im Client aussehen würden.

## Einrichtung {#setup}

Bevor Sie Headless-Technologie in AEM nutzen können, müssen Sie sicherstellen, dass alle erforderlichen Funktionen aktiviert sind. Diese werden nachfolgend beschrieben. Die einzelnen Schritte werden im Verlauf der [AEM Headless-Entwickler-Tour](#overview.md) näher erläutert.

Optional können Sie auch die [zusätzlichen Ressourcen](#additional-resources) heranziehen, um weitere Informationen zu den jeweiligen Themen zu erhalten.

### Konfiguration {#configuration}

1. Aktivieren von Inhaltsfragmenten
1. Aktivieren von GraphQL
1. Einrichten des Headless-SDK

## Implementieren Ihres ersten AEM Headless-Programms

Hier finden Sie einen Überblick darüber, was zur Implementierung Ihres ersten Headless-Programms mit AEM zur Bereitstellung Ihrer Inhalte erforderlich ist. Wie diese Schritte auszuführen sind, wird in späteren Abschnitten der AEM Headless-Entwickler-Tour ausführlich beschrieben.

1. Erstellen eines Inhaltsfragmentmodells
1. Erstellen von Inhaltsfragmenten
1. Abfragen von Inhalten mit GraphQL

## Best Practices {#best-practices}

Der Erfolg eines Headless-Projekts hängt nicht nur von der implementierten Technologie ab, sondern auch von guter Planung und Projekt-Governance. Im Folgenden finden Sie eine Reihe von Best Practices, die sowohl von Inhaltsautoren als auch von Entwicklern bei der Planung Ihres Projekts beachtet werden sollten.

### Organisieren Ihrer Inhalte {#organizing-content}

* Bauen Sie Ihre Struktur gerade so komplex wie nötig auf, aber halten Sie sie dabei so einfach wie möglich. Einfachere Inhaltsstrukturen tragen zur Optimierung der Inhaltsverwaltung und der Verbesserung der Systemleistung bei.
* Priorisieren Sie in Ihrer Strategie die Wiederverwendung von Inhalten. Erstellen Sie Untermodelle und Inhaltsreferenzen, die über mehrere übergeordnete Modelle und Kanäle Ebene hinweg wiederverwendet werden können.
* Gestalten Sie Inhaltsstrukturen so selbsterklärend wie möglich, sodass Inhaltsautoren sich schnell zurechtfinden und auf Bearbeitungsaufgaben einstellen können.
* Wenn Zugriffsbeschränkungen bestehen, versuchen Sie, Ihr Inhaltsmodell auf die Zugriffsanforderungen abzustimmen.
* Falls Zugriffsanforderungen vorliegen, sollten diese Ihre Inhaltshierarchie bestimmen. Fassen Sie Inhalte in Gruppen zusammen, der von derselben Personengruppe bearbeitet werden.
* Gruppieren Sie ähnliche Inhalte in einem Ordner.
   * Mit großer Wahrscheinlichkeit kopieren Inhaltsautoren vorhandene Inhalte, um sie an anderer Stelle einzufügen und neue Inhalte zu erstellen. Daher ist es effizienter, wenn dies im selben Ordner erfolgt.
   * AEM ermöglicht es, zulässige Modelle pro Ordner festzulegen, sodass durch Klicken auf die Schaltfläche **Neu erstellen** nur die an diesem Speicherort unterstützten Modelle angezeigt werden.
* Die Erstellung neuer Inhaltsfragmente im Inline-Inhaltsfragment-Editor kann vereinfacht werden, wenn der Stammordner im Modell festgelegt ist. Dann müssen die Anwender keinen Speicherort auswählen, sondern nur einen Namen angeben und die neue Referenz bearbeiten.

### Inhaltserstellung {#authoring}

* Verwenden Sie für kanalspezifische Versionen Ihrer Inhalte Inhaltsfragmentvarianten. Varianten werden mit den übergeordneten Inhalten synchronisiert, um die Verwaltung von Inhaltsänderungen zu optimieren.
* Bitten Sie andere Inhaltsautoren, Inhalte zu überprüfen und Feedback mit Anmerkungen und Kommentaren zu geben, die im Inhaltsfragment-Editor verfügbar sind und global für alle Fragmente in der Admin Console für Inhaltsfragmente abgerufen werden können.
* Verzichten Sie bei Ihren Abläufen möglichst auf obligatorische Elemente. Obligatorische Elemente können Workflows behindern.

### Erstellen von globalen Inhalten {#localization}

* Legen Sie Regeln und Richtlinien für die Inhaltsübersetzung fest. Um die Systembelastung zu verringern, richten Sie die Übersetzung als asynchronen Prozess ein, der in längeren Abständen ausgeführt werden kann. Planen Sie Zeit für die Qualitätskontrolle und Fehlerbehebung bei der Lokalisierung ein.
* Nutzen Sie alle Funktionen Ihres Übersetzungstechnologiesystems, die Sie in AEM integrieren können, etwa ein Translation Memory.
* Bringen Sie in Erfahrung, ob Rich-Media-Content wie Bilder und Videos lokalisiert werden müssen.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der AEM Headless-Entwickler-Tour abgeschlossen haben, sollten Sie über die folgenden Kenntnisse verfügen:

* Kenntnis der wichtigen Planungsanforderungen für die Gestaltung Ihrer Inhalte
* Verständnis der Schritte zur Implementierung von Headless-Technologie in AEM
* Kenntnis darüber, welche Tools und AEM-Konfigurationen erforderlich sind
* Kenntnis der Best Practices, mit denen Sie für reibungslose Headless-Abläufe sorgen, die Inhaltsgenerierung effizient gestalten und die schnelle Bereitstellung von Inhalten sicherstellen können

Ziel ist es, dass Sie auf diesem grundlegenden Wissen aufbauen, um das Potenzial und die Flexibilität von AEM Headless zu verstehen, damit Sie es für Ihre eigenen Projekte nutzen können. Dazu stehen Ihnen unterschiedliche Möglichkeiten zur Verfügung.

### Wählen Sie Ihren eigenen Weg {#choose-your-path}

Egal, welcher Lernstil Ihnen liegt: Adobe möchte, dass Sie erfolgreich sind, wenn Sie mit Ihrem AEM Headless-Projekt beginnen.

* Wenn Sie darüber hinaus **mehr über Headless-Konzepte und -Technologien von AEM** erfahren möchten, sollten Sie Ihre AEM Headless-Entwickler-Tour fortsetzen, indem Sie sich das Dokument [Modellieren Ihres Inhalts](model-your-content.md) ansehen. Hier erfahren Sie, wie Sie Ihre Inhaltsstruktur in AEM modellieren.
* Wenn Sie **praktische Erfahrungen** vorziehen, empfehlen wir Ihnen das praxisnahe Tutorial [Erste Schritte mit AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=de). Dort können Sie sich direkt mit der AEM Headless-Entwicklung vertraut machen, indem Sie ein einfaches Projekt implementieren, um AEM Headless-Inhalte bereitzustellen.

## Zusätzliche Ressourcen {#additional-resources}

Sie können wie empfohlen mit dem nächsten Teil der AEM Headless-Entwickler-Tour fortfahren, indem Sie das Dokument [Modellieren Ihres Inhalts](model-your-content.md) lesen. Im Folgenden finden Sie jedoch noch zusätzliche optionale Ressourcen, die auf einige der in diesem Dokument erwähnten Konzepte eingehen. Diese sind jedoch nicht erforderlich, um mit Ihrer AEM Headless-Entwickler-Tour fortzufahren.

* [Headless-Entwicklung für AEM Sites as a Cloud Service](/help/implementing/developing/headless/introduction.md) – eine kurze Einführung in die erforderlichen Funktionen, die AEM Headless-Entwicklern eine Orientierungshilfe bietet.
* [AEM Headless-Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de) – praxisnahe Tutorials, mit denen Sie die verschiedenen Optionen für die Bereitstellung von Content an Headless-Endpunkten mit AEM nutzen erkunden, um die für die geeignete Konfiguration zu ermitteln.
* [Headless Content Management Using GraphQL APIs](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless?lang=de#courses) – Kurs mit einem Überblick über die in AEM implementiere GraphQL-API. Es ist eine Authentifizierung per Adobe ID erforderlich.
* [AEM Guides WKND - GraphQL](https://github.com/adobe/aem-guides-wknd-graphql) – GitHub-Projekt mit Beispielprogrammen, die auf AEM-GraphQL-APIs eingehen
* [Einführung in die Architektur von Adobe Experience Manager as a Cloud Service](/help/core-concepts/architecture.md) – kompletter Überblick über die AEM-Architektur
* [Headless-Entwicklung für AEM Sites as a Cloud Service](/help/implementing/developing/headless/introduction.md#getting-started) – kurze Einführung in die Headless-Funktionen von AEM für Anwender mit AEM-Vorkenntnissen
* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md) – technische Dokumentation zu Inhaltsfragmentmodellen
* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md) – technische Dokumentation zu Inhaltsfragmenten
* [AEM-GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/assets/content-fragments/graphql-api-content-fragments.md) – technische Dokumentation zur GraphQL-API
