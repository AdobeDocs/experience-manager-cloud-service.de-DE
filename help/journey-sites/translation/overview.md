---
title: AEM Sites Translation Journey
description: Beginnen Sie hier mit einer geführten Journey durch die Übersetzung Ihrer AEM Sites-Inhalte mit AEM leistungsstarken Übersetzungstools.
index: true
hide: false
hidefromtoc: false
exl-id: 3db2ff19-dc24-47b6-aa56-2ee2305fe045
source-git-commit: ada7c256de5d050724781e4cbad6d877c1562c7b
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 6%

---

# AEM Sites Translation Journey {#aem-sites-translation-journey}

Beginnen Sie hier mit einer geführten Journey durch die Übersetzung Ihrer AEM Sites-Inhalte mit AEM leistungsstarken Übersetzungstools.

## Einführung {#introduction}

AEM Sites ist ein leistungsstarkes Tool-Set zum Erstellen und Verwalten digitaler Erlebnisse. Autoren von Inhalten können mit dem Sites-Editor einfach digitale Erlebnisse erstellen und die Inhalte mithilfe der Sites-Konsole organisieren. Gleichzeitig können sie die Inhalte live sehen, wie sie von AEM an Ihre Zielgruppen kanalübergreifend bereitgestellt werden.

AEM bietet ebenso leistungsstarke Tools zur Übersetzung Ihrer Inhalte, mit denen Sie diese so schnell wie möglich für Ihre Zielgruppen in anderen Regionen oder Gebietsschemata bereitstellen können. Diese Journey führt Sie in die Authoring-Tools ein, damit Sie verstehen, wie Inhalte in AEM erstellt und verwaltet werden. Anschließend erfahren Sie, was Sie für die Verwaltung Ihres eigenen Übersetzungsprojekts wissen müssen.

Wenn Sie bereits mit AEM Sites und Ihren Übersetzungsanforderungen vertraut sind, verfügen Sie möglicherweise bereits über grundlegende Kenntnisse dieser Journey. Wenn ja, verweisen Sie auf unsere technische Dokumentation, die im Abschnitt [zusätzlichen Ressourcen weiter unten.](#additional-resources)

## Journey AEM Dokumentation {#documentation-journeys}

[Eine Journey der Dokumentation](/help/journey-documentation/documentation-journeys.md) verbindet viele verschiedene und vielleicht komplizierte Themen und Funktionen, indem eine Erzählung bereitgestellt wird, die dem Leser hilft, der neu zu AEM sein kann, ein Geschäftsproblem von Anfang bis Ende zu verstehen und zu lösen, während er von Anfang bis Ende nur ein minimales vorheriges Thema oder AEM Wissen angeht.

Die Journey der Dokumentation basieren auf Best-Practice-Prinzipien, die durch aktuelle Forschungsarbeiten der Adobe, bewährte Implementierungserfahrungen von Adobe-Beratern und Rückmeldungen von Kundenprojekten informiert werden.

Wenn Sie wissen möchten, wie Adobe empfiehlt, Sites-Geschäftsfälle mit AEM zu lösen, sollten AEM Sites-Journey beginnen.

## Zielgruppe {#audience}

Diese Journey ist für die Fachleute für Übersetzungen konzipiert, die häufig als Übersetzungsprojekt-Manager oder TPM bezeichnet werden. In dieser Journey werden die Anforderungen, Schritte und Ansätze zur Übersetzung von AEM Sites-Inhalten beschrieben. Die Journey kann zusätzliche Personas definieren, mit denen der Übersetzer interagieren muss, aber der Blickwinkel für die Journey ist der des Übersetzers.

Bei dieser Journey wird davon ausgegangen, dass der Leser über Erfahrung bei der Übersetzung von Inhalten in einem großen CMS-System verfügt, jedoch keine Kenntnisse über AEM hat.

Im Folgenden finden Sie die Rollen, die in dieser Journey interagieren.

| Rolle | Beschreibung | Rolle beim Journey |
|---|---|---|
| Übersetzungsspezialist | Definiert, welche Inhalte übersetzt werden sollen, und verwaltet diese Workflows | Zielgruppe dieser Journey |
| Inhaltsautor | Erstellt und verwaltet Inhalte, die als Sites bereitgestellt werden | Inhaltsautoren erstellen Inhalte, die der Übersetzer übersetzen muss. |
| Administrator | Verwalten der grundlegenden Einrichtung und Konfiguration von AEM | Der Übersetzungsspezialist arbeitet mit dem Administrator zusammen, um die für die Übersetzung erforderlichen Konfigurationsänderungen vorzunehmen, z. B. die Installation eines Übersetzungs-Connectors. |
| Inhaltsarchitektur | Analysiert die Anforderungen für die Daten, die als Sites bereitgestellt werden müssen, und definiert die Struktur für diese Daten | Übersetzungs-Spezialisten arbeiten mit dem Inhaltsarchitekten zusammen, um die Organisation des Inhalts zu definieren, damit er leicht übersetzt werden kann. |

Informationen in dieser Journey können natürlich für alle Personen nützlich sein, aber einige Informationen können für bestimmte Rollen überflüssig sein. Bleiben Sie dran für [bevorstehende Journey, in denen zusätzliche Rollen behandelt werden.](/help/journey-documentation/documentation-journeys.md#journeys)

## Die Sites-Übersetzungs-Journey {#the-journey}

Im Rahmen dieser Tour werden Sie sich mit zahlreichen Themen befassen. Die folgenden Artikel geben Ihnen grundlegende Kenntnisse über die Übersetzung von Site-Inhalten in AEM und verlinken Sie auf eine detaillierte technische Dokumentation.

Obwohl Sie direkt zu einem bestimmten Teil der Tour gehen können, beachten Sie, dass viele Konzepte auf denen der vorherigen Artikel aufbauen. Wenn Sie daher mit der Übersetzung in AEM noch nicht vertraut sind, empfehlen wir Ihnen, am Anfang zu beginnen und den Prozess sequenziell zu gestalten.

| Nummer | Artikel | Beschreibung |
|---|---|---|
| 0 | AEM Sites Translation Journey | Dieses Dokument |
| 1 | [Erfahren Sie mehr über Sites-Inhalte und wie Sie sie in AEM übersetzen können.](learn-about.md) | Lernen Sie Sites-Konzepte und die Theorie der AEM Übersetzung kennen. |
| 2 | [Erste Schritte mit der AEM Sites-Übersetzung](getting-started.md) | Lernen Sie, wie Sie Ihre Sites-Inhalte organisieren und wie AEM Übersetzungs-Tools funktionieren. |
| 3 | [Konfigurieren des Übersetzungs-Connectors](configure-connector.md) | Erfahren Sie, wie Sie AEM mit einem Übersetzungsdienst verbinden. |
| 4 | [Übersetzungsregeln konfigurieren](translation-rules.md) | Erfahren Sie, wie Sie Übersetzungsregeln definieren, um zu übersetzende Inhalte zu identifizieren. |
| 5 | [Inhalt übersetzen](translate-content.md) | Verwenden Sie den Übersetzungs-Connector und die Regeln, um Ihre Site-Inhalte zu übersetzen. |
| 6 | [Übersetzten Inhalt veröffentlichen](publish-content.md) | Erfahren Sie, wie Sie Ihre übersetzten Inhalte veröffentlichen und die Übersetzung aktualisieren können, wenn der zugrunde liegende Inhalt aktualisiert wird. |

## Wie geht es weiter {#what-is-next}

Sie sind jetzt bereit, mit der Journey-Übersetzung Ihrer Adobe Sites zu beginnen. Wir empfehlen Ihnen, mit dem nächsten Teil der Journey fortzufahren und den Artikel zu lesen [Erfahren Sie mehr über Sites-Inhalte und wie Sie sie in AEM übersetzen können.](learn-about.md)

## Zusätzliche Ressourcen {#additional-resources}

Sehen Sie sich diese zusätzlichen Ressourcen an, um mehr darüber zu erfahren, wie AEM leistungsstarken Funktionen zusammenarbeiten.

* [Headless-Authoring-Journey](/help/journey-headless/author/overview.md) - Beginnen Sie hier für eine geführte Journey durch die leistungsstarken und flexiblen Headless-Features von AEM, deren Funktionen und wie Sie Ihre Inhalte in Ihrem ersten Headless-Projekt modellieren können.
* [Headless Architect-Journey](/help/journey-headless/architect/overview.md) - Beginnen Sie hier mit einer Einführung in die leistungsstarken, flexiblen, Headless-Funktionen von Adobe Experience Manager as a Cloud Service und wie Sie Inhalte für Ihr Projekt modellieren können.
* [AEM Headless-Entwickler-Journey](/help/journey-headless/developer/overview.md) - Beginnen Sie hier für eine geführte Journey durch die leistungsstarken und flexiblen Headless-Features von AEM, deren Funktionen und wie Sie sie bei Ihrem ersten Entwicklungsprojekt nutzen können.
* [AEM as a Cloud Service technische Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de) - Wenn Sie bereits über ein festes Verständnis von AEM und Headless-Technologien verfügen, können Sie unsere ausführlichen technischen Dokumente direkt konsultieren.
* [AEM Headless-Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de) - Wenn Sie lieber lernen möchten, indem Sie tun und technisch geneigt sind, nehmen Sie unsere praxisorientierten Tutorials organisiert von API und Framework, die die Erstellung und Verwendung von Anwendungen, die auf AEM Headless aufbauen.
