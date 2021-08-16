---
title: AEM Headless Translation Journey
description: Beginnen Sie hier für eine geführte Journey durch die Übersetzung Ihrer Headless Content mit AEM leistungsstarken Übersetzungstools.
index: false
hide: true
hidefromtoc: true
source-git-commit: 142c49b6b98dc78c3d36964dada1cfb900afee66
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 8%

---

# AEM Headless Translation Journey {#aem-headless-translation-journey}

Beginnen Sie hier für eine geführte Journey durch die Übersetzung Ihrer Headless Content mit AEM leistungsstarken Übersetzungstools.

## Einführung {#introduction}

Die Implementierung ohne Headless wird immer wichtiger für die Bereitstellung von Erlebnissen für Ihre Zielgruppe, unabhängig von Kanal, Region oder Gebietsschema.

Die Headless-Implementierung verzichtet auf das Seiten- und Komponenten-Management, wie es bei Full-Stack-Lösungen üblich ist, und konzentriert sich auf die Erstellung kanalneutraler, wiederverwendbarer Inhaltsfragmente und deren kanalübergreifende Bereitstellung. Mithilfe AEM leistungsstarken Übersetzungs-Tools können diese wiederverwendbaren Fragmente einfach übersetzt und an Ihre Audience geliefert werden, wo immer sie sich befinden.

Dieser Leitfaden führt Sie durch die wichtigsten Headless-Übersetzungsthemen, sodass Sie nach Abschluss:

* Verschaffen Sie sich einen Überblick darüber, was die Headless Content-Bereitstellung ist.
* Sie verfügen über ein grundlegendes Verständnis AEM Headless-Features.
* Verstehen Sie AEM Übersetzungsfunktionen und deren Zusammenhang mit Headless Content.
* Sie haben die Möglichkeit, Ihre eigenen Headless Content zu übersetzen.

Ziel ist es, Ihnen ein breites Verständnis der Headless-Technologie zu vermitteln, wie AEM Headless Content bereitstellt und wie Sie es übersetzen können. Wenn Sie mit keinem dieser Themen vertraut sind, ist dies Ihr idealer Ausgangspunkt.

Wenn Sie bereits mit AEM, Headless und Übersetzung vertraut sind, können Sie bereits über die Grundkenntnisse dieser Journey verfügen. Beachten Sie, dass Sie unten im Abschnitt [Zusätzliche Ressourcen auf unsere technische Dokumentation verweisen.](#additional-resources)

## Journey AEM Dokumentation {#documentation-journeys}

[Eine Dokumentation ](/help/journey-documentation/home.md) Journeys verbindet viele verschiedene und möglicherweise komplizierte Themen und Funktionen, indem sie eine Erzählung bereitstellt, die dem Leser hilft, der neu zu AEM sein kann, ein Geschäftsproblem von Anfang bis Ende versteht und löst, während er von einem minimalen vorherigen Thema oder AEM Wissen ausgeht.

Die Journey der Dokumentation basieren auf Best-Practice-Prinzipien, die durch aktuelle Forschungsarbeiten der Adobe, bewährte Implementierungserfahrungen von Adobe-Beratern und Rückmeldungen von Kundenprojekten informiert werden.

Wenn Sie wissen möchten, wie Adobe empfiehlt, Headless-Geschäftsfälle mit AEM zu lösen, AEM Headless-Journey beginnen.

## Zielgruppe {#audience}

Diese Journey ist für die Fachleute für Übersetzungen konzipiert, die häufig als Übersetzungsprojekt-Manager oder TPM bezeichnet werden. In dieser Journey werden die Anforderungen, Schritte und Ansätze zur Übersetzung von Headless Content in AEM beschrieben. Die Journey kann zusätzliche Personas definieren, mit denen der Übersetzer interagieren muss, aber der Blickwinkel für die Journey ist der des Übersetzers.

Diese Journey geht davon aus, dass der Leser Erfahrung mit der Übersetzung von Inhalten in einem großen CMS-System hat, jedoch keine Kenntnisse über Headless-Technologie oder AEM hat.

Im Folgenden finden Sie die Rollen, die in dieser Journey interagieren.

| Rolle | Beschreibung | Rolle beim Journey |
|---|---|---|
| Übersetzungsspezialist | Definiert, welche Inhalte übersetzt werden sollen, und verwaltet diese Workflows | Zielgruppe dieser Journey |
| Inhaltsautor | Erstellt und verwaltet Headless-Inhalte | Inhaltsautoren erstellen Inhalte, die der Übersetzer übersetzen muss. |
| Administrator | Verwalten der grundlegenden Einrichtung und Konfiguration von AEM | Der Übersetzungsspezialist arbeitet mit dem Administrator zusammen, um die für die Übersetzung erforderlichen Konfigurationsänderungen vorzunehmen, z. B. die Installation eines Übersetzungs-Connectors. |
| Inhaltsarchitektur | Analysiert die Anforderungen an die Daten, die Headless-Implementierung erfolgen muss, und definiert die Struktur für diese Daten | Übersetzungs-Spezialisten arbeiten mit dem Inhaltsarchitekten zusammen, um die Organisation des Inhalts zu definieren, damit er leicht übersetzt werden kann. |

Informationen in dieser Journey können natürlich für alle Personen nützlich sein, aber einige Informationen können für bestimmte Rollen überflüssig sein. Halten Sie sich für [bevorstehende Journey bereit, die zusätzliche Rollen behandeln.](/help/journey-documentation/home.md#journeys)

## Headless Translation Journey {#the-journey}

Im Rahmen dieser Tour werden Sie sich mit zahlreichen Themen befassen. Die folgenden Artikel geben Ihnen grundlegende Kenntnisse über die Übersetzung von Headless Content in AEM und verlinken Sie zu detaillierten technischen Dokumentationen.

Obwohl Sie direkt zu einem bestimmten Teil der Tour gehen können, beachten Sie, dass viele Konzepte auf denen der vorherigen Artikel aufbauen. Wenn Sie daher mit der Headless-Übersetzung in AEM noch nicht vertraut sind, empfehlen wir Ihnen, am Anfang zu beginnen und schrittweise voranzukommen.

| Nummer | Artikel | Beschreibung |
|---|---|---|
| 0 | AEM Headless Translation Journey | Dieses Dokument |
| 1 | [Erfahren Sie mehr über Headless Content und wie Sie ihn in AEM übersetzen können.](learn-about.md) | Lernen Sie Headless-Konzepte kennen, wie sie AEM zugeordnet sind und die Theorie AEM Übersetzung. |
| 2 | [Erste Schritte mit AEM Headless-Übersetzung](getting-started.md) | Lernen Sie, wie Sie Ihre Headless Content organisieren und wie AEM Übersetzungs-Tools funktionieren. |
| 3 | [Konfigurieren des Übersetzungs-Connectors](configure-connector.md) | Erfahren Sie, wie Sie AEM mit einem Übersetzungsdienst verbinden. |
| 4 | [Übersetzungsregeln konfigurieren](translation-rules.md) | Erfahren Sie, wie Sie Übersetzungsregeln definieren, um zu übersetzende Inhalte zu identifizieren. |
| 5 | [Inhalt übersetzen](translate-content.md) | Verwenden Sie den Übersetzungs-Connector und die Regeln, um Ihre Headless-Inhalte zu übersetzen. |
| 6 | [Übersetzten Inhalt veröffentlichen](publish-content.md) | Erfahren Sie, wie Sie Ihre übersetzten Inhalte veröffentlichen und die Übersetzung aktualisieren können, wenn der zugrunde liegende Inhalt aktualisiert wird. |

## Wie geht es weiter {#what-is-next}

Jetzt können Sie mit dem Headless-Übersetzungs-Journey auf Ihrer Adobe beginnen. Wir empfehlen Ihnen, mit dem nächsten Teil der Journey fortzufahren und den Artikel [Erfahren Sie mehr über Headless Content und wie Sie ihn in AEM](learn-about.md) übersetzen können.

## Zusätzliche Ressourcen {#additional-resources}

Die Journey der Dokumentation zeigen Ihnen, wie AEM ein Geschäftsproblem löst, indem sie eine Erzählung bereitstellen, die Sie durch komplexe, miteinander verknüpfte Prozesse und Funktionen führt. Eine Journey veranschaulicht, wie mehrere Funktionen zusammenarbeiten, um eine einzige Geschäftsanforderung zu erfüllen.

Journey sind so konzipiert, dass sie auf sich allein gestellt stehen. Einige davon können jedoch miteinander verbunden werden. Weitere Informationen dazu, wie AEM leistungsstarken Funktionen zusammenarbeiten, finden Sie in diesen zusätzlichen Journey .

* [AEM Headless-Entwickler-Journey](/help/journey-headless/developer/overview.md)  - Beginnen Sie hier für eine geführte Journey durch die leistungsstarken und flexiblen Headless-Features von AEM, deren Funktionen und wie Sie sie bei Ihrem ersten Entwicklungsprojekt nutzen können.
* [AEM als Cloud Service technische Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de)  - Wenn Sie bereits über fundierte Kenntnisse in AEM und Headless-Technologien verfügen, sollten Sie unsere ausführlichen technischen Dokumente direkt konsultieren.
