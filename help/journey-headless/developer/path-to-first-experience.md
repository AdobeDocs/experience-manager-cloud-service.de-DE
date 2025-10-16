---
title: Gestalten Ihres ersten Erlebnisses mit AEM Headless
description: In diesem Teil der AEM Headless-Entwickler-Tour erfahren Sie, wie Sie Ihre ersten Headless-Erlebnisse in AEM implementieren, einschließlich Überlegungen zur Planung, und lernen Best Practices kennen, die für möglichst reibungslose Abläufe sorgen.
exl-id: 172ad8d8-5067-4452-bf91-1eea9a39a7bc
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 2ccca86a0e611b93c273e37abb6e0fd7870421d4
workflow-type: tm+mt
source-wordcount: '1881'
ht-degree: 96%

---

# Gestalten Ihres ersten Erlebnisses mit AEM Headless {#path-to-first-experience}

In diesem Teil der [AEM Headless-Entwickler-Tour](overview.md) erfahren Sie, wie Sie Ihre ersten Headless-Erlebnisse in AEM implementieren, einschließlich Planungsüberlegungen, und lernen Best Practices kennen, die für möglichst reibungslose Abläufe sorgen.

## Ihre bisherige Tour {#story-so-far}

Im vorherigen Dokument zur AEM Headless-Entwickler-Tour, [Erste Schritte mit AEM as a Cloud Service](getting-started.md), haben Sie sich mit den Grundlagen zu Headless-CMS-Lösungen vertraut gemacht. Nun verfügen Sie über folgenden Voraussetzungen:

* Grundlegendes Verständnis der AEM Headless-Funktionen
* die Voraussetzungen für die Verwendung der Headless-Funktionen von AEM kennen,
* sich der Headless-Integrationsebenen von AEM bewusst sein.
* in der Lage sein, Ihr Projekt in Bezug auf den Umfang zu definieren.

Dieser Artikel baut auf diesen Grundlagen auf, sodass Sie verstehen, wie Sie Ihr eigenes AEM Headless-Projekt vorbereiten.

## Ziel {#objective}

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

Stattdessen sollten Sie sich überlegen, wie Inhalte auf verschiedenen Oberflächen basierend auf Organisationsprinzipien wie Marken- und Produkthierarchien, Waren- oder Oberflächenkategorien oder Schritten in der Customer Journey zusammenhängen. Wenn Sie beispielsweise über eine Reihe von Oberflächen zur Betreuung einer bestimmten von Ihnen hergestellten Automarke verfügen, empfiehlt es sich, mit einem Inhaltsmodell für allgemeine Informationen zu beginnen, die für das gesamte Fahrzeug gelten, und dann zu spezifischeren Elemente überzugehen, beispielsweise Inhalte, die benötigt werden, wenn das Fahrzeug in Betrieb genommen wird oder in die Werkstatt muss. Mit einem solchen Modell wird eine Vererbung der allgemeinen Inhalte der Automarke erzwungen und gleichzeitig Verschiebungen basierend auf bestimmtem Kontext ermöglicht. Das Modell hilft auch bei der späteren Verwaltung von Aktualisierungen dieser Inhalte, da Sie die Kontrolle auf der Grundlage von Rollen durchsetzen können, wie z. B. dem übergeordneten Marketer oder Produkt-Manager für die gesamte Automarke im Vergleich zu dem Autor, der für das „Starterlebnis“ verantwortlich ist.

Sobald Sie über ein Inhaltsmodell und eine klare Übersicht über die verschiedenen Clients verfügen, auf denen die Inhalte angezeigt werden sollen, müssen Sie sicherstellen, dass die GraphQL-APIs, die dem Zugriff auf verschiedene Inhaltsmodelle entsprechen, für alle Clients veröffentlicht werden, die diese Inhalte benötigen. Es gibt verschiedene Optionen für den Zugriff auf bestimmte Inhalte. Sie können einen bestimmten Inhalt anfordern, der statisch ist, wodurch das Caching des Inhalts ermöglicht und die Performance verbessert wird. Sie können auch dynamisch generierte Inhalte anfordern, die eine aufwendigere Verarbeitung erfordern. Stellen Sie sicher, dass Kundinnen und Kunden die APIs verwenden, die für ihre geschäftlichen Anforderungen am effizientesten sind.

## Grundlegendes zu Ihren Umgebungen {#understanding-environments}

In AEM gibt es drei Arten von Umgebungen: Entwicklungs-, Staging- und Produktionsumgebungen.

Die Entwicklungsumgebungen (davon können Sie mehrere haben) sind ein sicherer Ort, um Ideen auszuprobieren und zu experimentieren. In der Anfangsphase eines Projekts empfiehlt Adobe die Verwendung der Entwicklungsumgebungen, um Variationen von Inhaltsmodellen auszuprobieren und zu sehen, welche die gewünschte Ausgabe für die Oberflächen liefern.

Die Staging-Umgebung für Headless-Projekte wird verwendet, um neue AEM-Produktversionen zu validieren, bevor sie in die Produktion übergehen. Halten Sie eine aktuelle Liste der Produktions-Inhaltsmodelle dort und eine Teilmenge der Inhalte vor, damit Sie JSON-Dateien zum Vergleich rendern lassen können, die immer noch dieselbe Ausgabe liefern, wenn Sie Änderungen vornehmen oder mit einer AEM-Version Änderungen eingeführt werden.

In der Produktion erstellen und verwalten Inhaltsautoren ihre eigentlichen Inhalte. Modelländerungen in der Produktion müssen umsichtig und unter Berücksichtigung der Abwärtskompatibilität durchgeführt werden.

In der Entwicklungsphase wird empfohlen, mit einer Entwicklungs- und Staging-Umgebung zu arbeiten. Wenn Sie zu den Performance-Tests übergehen, sollten Sie in die Produktionsumgebung wechseln.

### Zusammenarbeit von Entwicklern und Inhaltsautoren {#cooperation}

Entwickler benötigen eine AEM-Entwicklungsumgebung mit den ausgefüllten Inhaltsmodellen. Die Entwickler entwickeln den Client, der Inhalte von AEM Headless nutzt, während die Inhaltsautoren noch mit der Inhaltserstellung beschäftigt sind. Aus diesem Grund sind die API-Definitionen sehr wichtig. Mithilfe des AEM SDK können Entwickelnde einen Test-Hook erstellen. Damit lassen sich Client- und Unit-Tests entwickeln, um sicherzustellen, dass der Client die Inhalte ordnungsgemäß rendern kann.

Inhaltsautorinnen und Inhaltsautoren erstellen Inhalte auf Basis der Inhaltsmodelle, die in der Staging-Umgebung definiert wurden. Mit dem Authoring-Tool für Inhaltsfragmente erstellen Autorinnen und Autoren neue Inhaltsfragmente bzw. bearbeiten vorhandene. Vor der Veröffentlichung können Autoren eine Vorschau der Inhalte im Client anzeigen. Dazu müssen sie mit den Entwicklern zusammenarbeiten, um das Inhaltsmodell in die Entwicklungsumgebung zu übertragen oder eine spezielle Entwicklungsumgebung einzurichten, damit die Autoren in der Vorschau anzeigen können, wie die Inhalte im Client aussehen würden.

## Einrichtung {#setup}

Bevor Sie Headless-Technologie in AEM nutzen können, müssen Sie sicherstellen, dass alle erforderlichen Funktionen aktiviert sind. Diese werden nachfolgend beschrieben. Die einzelnen Schritte werden im Verlauf der [AEM Headless-Entwickler-Tour](#overview.md) näher erläutert.

Optional können Sie auch [zusätzliche Ressourcen](#additional-resources) für weitere Informationen zu den einzelnen Themen einsehen.

### Konfiguration {#configuration}

1. Aktivieren von Inhaltsfragmenten
1. Aktivieren von GraphQL
1. Einrichten des Headless-SDK

## Implementieren Ihres ersten AEM Headless-Programms

Hier finden Sie einen Überblick darüber, was zur Implementierung Ihres ersten Headless-Programms mit AEM zur Bereitstellung Ihrer Inhalte erforderlich ist. Wie diese Schritte auszuführen sind, wird in späteren Abschnitten der AEM Headless-Entwickler-Tour ausführlich beschrieben.

1. Erstellen von Inhaltsfragmentmodellen
1. Erstellen von Inhaltsfragmenten
1. Abfragen von Inhalten mit GraphQL

## Best Practices {#best-practices}

Der Erfolg eines Headless-Projekts hängt nicht nur von der implementierten Technologie ab, sondern auch von guter Planung und Projekt-Governance. Im Folgenden finden Sie eine Reihe von Best Practices, die sowohl von Inhaltsautorinnen bzw. Inhaltsautoren als auch von Entwickelnden bei der Planung Ihres Projekts beachtet werden sollten.

### Organisieren Ihrer Inhalte {#organizing-content}

* Bauen Sie Ihre Struktur gerade so komplex wie nötig auf, aber halten Sie sie dabei so einfach wie möglich. Einfachere Inhaltsstrukturen tragen zur Optimierung der Inhaltsverwaltung und der Verbesserung der Systemleistung bei.
* Priorisieren Sie in Ihrer Strategie die Wiederverwendung von Inhalten. Erstellen Sie Untermodelle und Inhaltsreferenzen, die über mehrere übergeordnete Modelle und Kanäle Ebene hinweg wiederverwendet werden können.
* Gestalten Sie Inhaltsstrukturen so selbsterklärend wie möglich, sodass Inhaltsautoren sich schnell zurechtfinden und auf Bearbeitungsaufgaben einstellen können.
* Wenn Zugriffsbeschränkungen bestehen, versuchen Sie, Ihr Inhaltsmodell auf die Zugriffsanforderungen abzustimmen.
* Falls Zugriffsanforderungen vorliegen, sollten diese Ihre Inhaltshierarchie bestimmen. Fassen Sie Inhalte in Gruppen zusammen, der von derselben Personengruppe bearbeitet werden.
* Gruppieren Sie ähnliche Inhalte in einem Ordner.
   * Mit großer Wahrscheinlichkeit kopieren Inhaltsautorinnen und Inhaltsautoren vorhandene Inhalte, um sie an anderer Stelle einzufügen und neue Inhalte zu erstellen. Daher ist es effizienter, wenn dies im selben Ordner erfolgt.
   * AEM ermöglicht es, zulässige Modelle pro Ordner festzulegen, sodass durch Klicken auf die Schaltfläche **Neu erstellen** nur die an diesem Speicherort unterstützten Modelle angezeigt werden.
* Die Erstellung neuer Inhaltsfragmente im Inline-Inhaltsfragment-Editor kann vereinfacht werden, wenn der Stammordner im Modell festgelegt ist. Dann müssen die Fachleute keinen Speicherort auswählen, sondern brauchen nur einen Namen anzugeben und können die neue Referenz bearbeiten.

### Inhaltserstellung {#authoring}

* Verwenden Sie für kanalspezifische Versionen Ihrer Inhalte Inhaltsfragmentvarianten. Varianten werden mit den übergeordneten Inhalten synchronisiert, um die Verwaltung von Inhaltsänderungen zu optimieren.
* Laden Sie andere Inhaltserstellerinnen und -ersteller ein, Inhalte zu überprüfen und Feedback zu geben.
* Verzichten Sie bei Ihren Abläufen möglichst auf obligatorische Elemente. Obligatorische Elemente können Workflows behindern.

### Erstellen von globalen Inhalten {#localization}

* Legen Sie Regeln und Richtlinien für die Inhaltsübersetzung fest. Um die Systembelastung zu verringern, richten Sie die Übersetzung als asynchronen Prozess ein, der in längeren Abständen ausgeführt werden kann. Planen Sie Zeit für die Qualitätskontrolle und Fehlerbehebung bei der Lokalisierung ein.
* Nutzen Sie alle Funktionen Ihres Übersetzungstechnologiesystems, die Sie in AEM integrieren können, etwa ein Translation Memory.
* Bringen Sie in Erfahrung, ob Rich-Media-Content wie Bilder und Videos lokalisiert werden müssen.

## So geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der AEM Headless-Entwickler-Tour abgeschlossen haben, sollten Sie über die folgenden Kenntnisse verfügen:

* Kenntnis der wichtigen Planungsanforderungen für die Gestaltung Ihrer Inhalte
* Verständnis der Schritte zur Implementierung von Headless-Technologie in AEM
* Kenntnis darüber, welche Tools und AEM-Konfigurationen erforderlich sind
* Kenntnis der Best Practices, mit denen Sie für reibungslose Headless-Abläufe sorgen, die Inhaltsgenerierung effizient gestalten und die schnelle Bereitstellung von Inhalten sicherstellen können

Wir möchten, dass Sie auf diesem grundlegenden Wissen aufbauen, um die Leistungsfähigkeit und Flexibilität von AEM Headless vollständig zu verstehen, damit Sie es für Ihre eigenen Projekte nutzen können.

Fahren Sie dazu mit der AEM Headless-Journey mit [Modellieren Ihres Inhalts als AEM-Inhaltsmodelle“ fort, &#x200B;](/help/journey-headless/developer/model-your-content.md) dem Sie lernen, wie Sie Ihre Inhaltsstruktur in AEM modellieren.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, mit dem nächsten Teil der Headless-Entwickler-Tour fortzufahren, indem Sie das Dokument [Modellieren Ihres Inhalts als AEM-Inhaltsmodelle](model-your-content.md) lesen. Im Folgenden finden Sie jedoch noch zusätzliche optionale Ressourcen, die einige der in diesem Dokument erwähnten Konzepte vertiefen, aber nicht erforderlich sind, um die Headless-Tour fortzusetzen.

Wenn Sie **praktische Erfahrungen** vorziehen, empfehlen wir Ihnen das praxisnahe Tutorial [Erste Schritte mit AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=de). Dort können Sie sich direkt mit der AEM Headless-Entwicklung vertraut machen, indem Sie ein einfaches Projekt implementieren, um AEM Headless-Inhalte bereitzustellen.

Weitere Ressourcen:

* [AEM Headless Übersetzungs-Tour](/help/journey-headless/translation/overview.md) – Diese Dokumentations-Tour vermittelt Ihnen ein umfassendes Verständnis der Headless-Technologie sowie davon, wie AEM Headless Inhalte bereitstellt und wie Sie sie übersetzen können.
* [Headless-Entwicklung für AEM Sites as a Cloud Service](/help/headless/introduction.md) – eine kurze Einführung in die erforderlichen Funktionen, die AEM Headless-Entwickelnden eine Orientierungshilfe bietet.
* [AEM-Entwicklerportal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
* [Headless-Content-Management mit GraphQL-APIs](https://experienceleague.adobe.com/?Solution=Experience+Manager&Solution=Experience+Manager+Sites&Solution=Experience+Manager+Forms&Solution=Experience+Manager+Screens&launch=ExperienceManager-D-1-2020.1.headless#courses): In diesem Kurs erhalten Sie einen Überblick über die in AEM implementierte GraphQL-API. Eine Authentifizierung über Adobe ID ist erforderlich.
* [AEM Guides WKND - GraphQL](https://github.com/adobe/aem-guides-wknd-graphql) – GitHub-Projekt mit Beispielprogrammen, die auf AEM-GraphQL-APIs eingehen
* [Einführung in die Architektur von Adobe Experience Manager as a Cloud Service](/help/overview/architecture.md) – kompletter Überblick über die AEM-Architektur
* [Einrichtung von Headless](/help/headless/introduction.md#getting-started) – kurze Einführung in die Headless-Funktionen von AEM für Anwender mit AEM-Vorkenntnissen
* [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md) – technische Dokumentation zu Inhaltsfragmentmodellen
* [Arbeiten mit Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments) – technische Dokumentation zu Inhaltsfragmenten
* [AEM-GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md) – technische Dokumentation zur GraphQL-API
