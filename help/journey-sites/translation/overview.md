---
title: AEM Sites-Übersetzungs-Tour
description: Beginnen Sie hier mit einer geführten Tour durch die Übersetzung Ihrer AEM Sites-Inhalte mit den leistungsstarken Übersetzungs-Tools in AEM.
index: true
hide: false
hidefromtoc: false
exl-id: 3db2ff19-dc24-47b6-aa56-2ee2305fe045
solution: Experience Manager Sites
feature: Translation
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 98%

---

# AEM Sites-Übersetzungs-Tour {#aem-sites-translation-journey}

Beginnen Sie hier mit einer geführten Tour durch die Übersetzung Ihrer AEM Sites-Inhalte mit den leistungsstarken Übersetzungs-Tools in AEM.

## Einführung {#introduction}

AEM Sites ist ein leistungsstarkes Toolset zum Erstellen und Verwalten digitaler Erlebnisse. Inhaltsautorinnen und -autoren können mit dem Sites-Editor einfach digitale Erlebnisse erstellen und die Inhalte mithilfe der Sites-Konsole organisieren. Gleichzeitig können sie die Inhalte live so sehen, wie sie kanalübergreifend von AEM an Zielgruppen bereitgestellt werden.

AEM bietet ebenso leistungsstarke Tools zur Übersetzung Ihrer Inhalte, mit denen Sie diese so schnell wie möglich für Ihre Zielgruppen in anderen Regionen bereitstellen können. Diese Dokumentations-Tour führt Sie in die Authoring-Tools ein, damit Sie verstehen, wie Inhalte in AEM erstellt und verwaltet werden. Anschließend erfahren Sie, was Sie für die Verwaltung Ihres eigenen Übersetzungsprojekts wissen müssen.

Wenn Sie bereits mit AEM Sites und Ihren Übersetzungsanforderungen vertraut sind, verfügen Sie möglicherweise bereits über grundlegendes Wissen aus dieser Tour. Wenn ja, verweisen wir Sie auf unsere technische Dokumentation, die im Abschnitt [Zusätzliche Ressourcen unten“ verlinkt ](#additional-resources).

## AEM-Dokumentations-Touren {#documentation-journeys}

[Eine Dokumentations-Tour](/help/journey-documentation/documentation-journeys.md) verbindet viele verschiedene, komplizierte Themen und Funktionen durch eine Darstellung, die mit AEM nicht vertrauten Leserinnen und Lesern hilft, ein geschäftliches Problem von Anfang bis Ende zu verstehen und zu lösen, wobei nur minimale Vorkenntnisse zum Thema oder zu AEM vorausgesetzt werden.

Dokumentations-Touren werden auf der Grundlage von Best-Practice-Prinzipien entwickelt, die auf Informationen aus den neuesten Forschungsergebnissen von Adobe, bewährten Implementierungserfahrungen der Adobe-Berater und dem Feedback aus Kundenprojekten basieren.

Wenn Sie wissen möchten, wie Adobe empfiehlt, Geschäftsfälle für Websites mit AEM zu lösen, sollten Sie mit den AEM Sites-Touren beginnen.

## Zielgruppe {#audience}

Diese Tour richtet sich an die Rolle des Übersetzungsspezialisten, oft auch als Übersetzungsprojektmanager oder TPM (Translation Project Manager) bezeichnet. In dieser Tour werden die Anforderungen, Schritte und Ansätze zur Übersetzung von AEM Sites-Inhalten beschrieben. In der Tour können zusätzliche Rollen definiert werden, mit denen der Übersetzungsspezialist interagieren muss, aber der Blickwinkel für die Tour ist der des Übersetzungsspezialisten.

Bei dieser Tour wird davon ausgegangen, dass der Leser Erfahrung mit der Übersetzung von Inhalten in einem großen CMS-System hat, es werden jedoch keine Kenntnisse über AEM vorausgesetzt.

Im Folgenden finden Sie die Rollen, die in dieser Tour interagieren.

| Persona | Beschreibung | Rolle in der Tour |
|---|---|---|
| Übersetzungsspezialist | Definiert, welche Inhalte übersetzt werden sollen, und verwaltet diese Workflows | Zielgruppe dieser Tour |
| Inhaltsautor | Erstellt und verwaltet Inhalte, die als Sites bereitgestellt werden | Inhaltsautoren erstellen Inhalte, die der Übersetzungsspezialist übersetzen muss. |
| Administrator | Verwaltet die grundlegende Einrichtung und Konfiguration von AEM | Der Übersetzungsspezialist arbeitet mit dem Administrator zusammen, um die für die Übersetzung erforderlichen Konfigurationsänderungen vorzunehmen, z. B. die Installation eines Übersetzungs-Connectors. |
| Inhaltsarchitekt | Analysiert die Anforderungen für die Daten, die als Websites bereitgestellt werden müssen, und definiert die Struktur für diese Daten | Übersetzungsspezialisten arbeiten mit dem Inhaltsarchitekten zusammen, um die Organisation der Inhalte zu definieren, damit sie leicht übersetzt werden können. |

Die Informationen in dieser Tour können auch für andere Rollen nützlich sein, aber einige Informationen sind für bestimmte Rollen nicht relevant. Freuen Sie sich auf [neue Touren, mit denen wir künftig auf weitere Rollen eingehen](/help/journey-documentation/documentation-journeys.md#journeys).

## Die Sites-Übersetzungs-Tour {#the-journey}

Im Rahmen dieser Tour werden Sie sich mit zahlreichen Themen befassen. Die folgenden Artikel vermitteln Ihnen Grundkenntnisse über das Übersetzen von Website-Inhalten in AEM und enthalten Links zu detaillierten technischen Dokumentationen.

Sie können direkt zu einem bestimmten Teil der Tour gehen. Beachten Sie jedoch, dass viele Konzepte auf denen der vorherigen Artikel aufbauen. Wenn Übersetzungen in AEM für Sie also neu sind, empfehlen wir Ihnen, am Anfang zu beginnen und schrittweise vorzugehen.

| Nummer | Artikel | Beschreibung |
|---|---|---|
| 0 | AEM Sites-Übersetzungs-Tour | Dieses Dokument |
| 1 | [Erfahren Sie mehr über Site-Inhalte und wie Sie sie in AEM übersetzen können](learn-about.md) | Lernen Sie Site-Konzepte und die Theorie der AEM-Übersetzung kennen. |
| 2 | [Erste Schritte mit der AEM Sites-Übersetzung](getting-started.md) | Erfahren Sie, wie Sie Ihre Website-Inhalte organisieren und wie die Übersetzungs-Tools in AEM funktionieren. |
| 3 | [Konfigurieren des Übersetzungs-Connectors](configure-connector.md) | Erfahren Sie, wie Sie AEM mit einem Übersetzungs-Service verbinden. |
| 4 | [Konfigurieren von Übersetzungsregeln](translation-rules.md) | Erfahren Sie, wie Sie Übersetzungsregeln definieren, um zu übersetzende Inhalte zu identifizieren. |
| 5 | [Übersetzen von Inhalten](translate-content.md) | Verwenden Sie den Übersetzungs-Connector und die Regeln, um Ihre Website-Inhalte zu übersetzen. |
| 6 | [Veröffentlichen übersetzter Inhalte](publish-content.md) | Erfahren Sie, wie Sie Ihre übersetzten Inhalte veröffentlichen und die Übersetzung aktualisieren können, wenn sich die zugrunde liegenden Inhalte ändern. |

## Wie geht es weiter {#what-is-next}

Jetzt sind Sie bereit, mit Ihrer Adobe-Sites-Übersetzung-Tour zu beginnen. Wir empfehlen Ihnen, mit dem nächsten Teil der Tour fortzufahren und den Artikel [Erfahren Sie mehr über den Inhalt von Websites und wie man ihn in AEM übersetzt](learn-about.md) zu lesen.

## Zusätzliche Ressourcen {#additional-resources}

In diesen zusätzlichen Ressourcen finden Sie weitere Informationen darüber, wie die leistungsstarken Funktionen von AEM zusammenarbeiten.

* [Headless-Autoren-Tour](/help/journey-headless/author/overview.md) – Diese angeleitete Tour bietet Ihnen eine Einführung zu den leistungsstarken und flexiblen Headless-Funktionen von AEM und deren Möglichkeiten. Sie veranschaulicht, wie Sie bei Ihrem ersten Headless-Entwicklungsprojekt Inhalte modellieren können.
* [Headless-Architekten-Tour](/help/journey-headless/architect/overview.md) – Beginnen Sie hier mit einer Einführung in die leistungsstarken, flexiblen Headless-Funktionen von Adobe Experience Manager as a Cloud Service und erfahren Sie, wie Sie Inhalte für Ihr Projekt modellieren können.
* [AEM Headless-Entwickler-Tour](/help/journey-headless/developer/overview.md) – Diese angeleitete Tour bietet Ihnen eine Einführung zu den leistungsstarken und flexiblen Headless-Funktionen von AEM und deren Möglichkeiten. Sie veranschaulicht, wie Sie sie bei Ihrem ersten Headless-Entwicklungsprojekt nutzen können.
* [AEM as a Cloud Service – Technische Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de) – Wenn Sie bereits über ein solides Verständnis von AEM und Headless-Technologien verfügen, können Sie direkt unsere ausführlichen technischen Dokumente hinzuziehen.
* [AEM Headless-Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de) – Wenn Sie es vorziehen, durch praktisches Arbeiten zu lernen und technisch versiert sind, können Sie unsere nach API und Framework geordneten praktischen Tutorials nutzen, in denen die Erstellung und Verwendung von Programmen auf der Grundlage von AEM Headless behandelt wird.
