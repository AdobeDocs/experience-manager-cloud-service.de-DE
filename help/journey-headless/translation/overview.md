---
title: AEM Headless-Übersetzungs-Tour
description: Beginnen Sie hier mit einer geführten Tour durch die Übersetzung Ihrer Headless-Inhalte mithilfe der leistungsstarken Übersetzungs-Tools von AEM.
exl-id: b677f691-5257-43c3-a4b9-c34932577b31
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1024'
ht-degree: 100%

---

# AEM Headless-Übersetzungs-Tour {#aem-headless-translation-journey}

Beginnen Sie hier mit einer geführten Tour durch die Übersetzung Ihrer Headless-Inhalte mithilfe der leistungsstarken Übersetzungs-Tools von AEM.

## Einführung {#introduction}

Die Headless-Implementierung wird immer wichtiger, wenn es darum geht, Erlebnisse für Ihre Zielgruppe überall und unabhängig von Kanal, Region oder Gebietsschema bereitzustellen.

Die Headless-Implementierung verzichtet auf das Seiten- und Komponenten-Management, wie es bei Full-Stack-Lösungen üblich ist, und konzentriert sich auf die Erstellung kanalneutraler, wiederverwendbarer Inhaltsfragmente und deren kanalübergreifende Bereitstellung. Mithilfe der leistungsstarken Übersetzungs-Tools in AEM können diese wiederverwendbaren Fragmente einfach übersetzt und für Ihre Zielgruppe bereitgestellt werden, wo immer sie sich befindet.

Dieser Leitfaden führt Sie durch die wichtigsten Themen der Headless-Übersetzung. Nach dem Abschluss der Lektüre sollten Sie:

* einen Überblick darüber haben, was die Bereitstellung von Headless-Inhalten ist.
* ein grundlegendes Verständnis der Headless-Funktionen von AEM haben.
* die Übersetzungsfunktionen von AEM verstehen und wissen, wie sie sich auf Headless-Inhalte beziehen.
* damit beginnen können, Ihre eigenen Headless-Inhalte zu übersetzen.

Ziel ist es, Ihnen ein breites Verständnis der Headless-Technologie sowie davon, wie AEM Headless-Inhalte bereitstellt und wie Sie es übersetzen können, zu vermitteln. Wenn Sie mit keinem dieser Themen vertraut sind, ist dies Ihr idealer Ausgangspunkt.

Wenn Sie bereits mit AEM, Headless und Übersetzung vertraut sind, verfügen Sie vielleicht schon über das Grundwissen aus dieser Tour. Ziehen Sie auch unsere technische Dokumentation zu Rate, die im [Abschnitt „Zusätzliche Ressourcen“ unten verlinkt ist](#additional-resources).

## AEM-Dokumentations-Touren {#documentation-journeys}

[Eine Dokumentations-Tour](/help/journey-documentation/documentation-journeys.md) verbindet viele verschiedene, komplizierte Themen und Funktionen durch eine Darstellung, die mit AEM nicht vertrauten Leserinnen und Lesern hilft, ein geschäftliches Problem von Anfang bis Ende zu verstehen und zu lösen, wobei nur minimale Vorkenntnisse zum Thema oder zu AEM vorausgesetzt werden.

Dokumentations-Touren werden auf der Grundlage von Best-Practice-Prinzipien entwickelt, die auf Informationen aus den neuesten Forschungsergebnissen von Adobe, bewährten Implementierungserfahrungen der Adobe-Berater und dem Feedback aus Kundenprojekten basieren.

Wenn Sie wissen möchten, wie Adobe empfiehlt, Headless-Geschäftsfälle mit AEM zu lösen, sollten Sie mit den [AEM Headless-Touren](/help/journey-documentation/documentation-journeys.md) beginnen.

## Zielgruppe {#audience}

Diese Tour richtet sich an die Perona des Übersetzungsspezialisten, oft auch als Übersetzungsprojektmanager oder TPM (Translation Project Manager) bezeichnet. In dieser Tour werden die Anforderungen, Schritte und Ansätze zur Übersetzung von Headless-Inhalten in AEM beschrieben. In der Tour können zusätzliche Personas definiert werden, mit denen der Übersetzungsspezialist interagieren muss, aber der Blickwinkel für die Tour ist der des Übersetzungsspezialisten.

Bei dieser Tour wird davon ausgegangen, dass der Leser Erfahrung mit der Übersetzung von Inhalten in einem großen CMS-System hat, aber keine Kenntnisse über Headless-Technologie oder AEM hat.

Im Folgenden finden Sie die Personas, die in dieser Tour interagieren.

| Persona | Beschreibung | Rolle in der Tour |
|---|---|---|
| Übersetzungsspezialist | Definiert, welche Inhalte übersetzt werden sollen, und verwaltet diese Workflows | Zielgruppe dieser Tour |
| Inhaltsautor | Erstellt und verwaltet Inhalte, die „headless“ bereitgestellt werden | Inhaltsautoren erstellen Inhalte, die der Übersetzungsspezialist übersetzen muss. |
| Administrator | Verwaltet die grundlegende Einrichtung und Konfiguration von AEM | Der Übersetzungsspezialist arbeitet mit dem Administrator zusammen, um die für die Übersetzung erforderlichen Konfigurationsänderungen vorzunehmen, z. B. die Installation eines Übersetzungs-Connectors. |
| Inhaltsarchitekt | Analysiert die Anforderungen an die Daten, die „headless“ bereitgetellt werden müssen, und definiert die Struktur für diese Daten. | Übersetzungsspezialisten arbeiten mit dem Inhaltsarchitekten zusammen, um die Organisation der Inhalte zu definieren, damit sie leicht übersetzt werden können. |

Die Informationen in dieser Tour können auch für andere Rollen nützlich sein, aber einige Informationen sind für bestimmte Rollen nicht relevant. Freuen Sie sich auf [neue Touren, mit denen wir künftig auf weitere Rollen eingehen](/help/journey-documentation/documentation-journeys.md#journeys).

## Headless-Übersetzungs-Tour {#the-journey}

Im Rahmen dieser Tour werden Sie sich mit zahlreichen Themen befassen. Die folgenden Artikel vermitteln Ihnen Grundkenntnisse über das Übersetzen von Headless-Inhalten in AEM und enthalten Links zu detaillierten technischen Dokumentationen.

Sie können direkt zu einem bestimmten Teil der Tour gehen. Beachten Sie jedoch, dass viele Konzepte auf denen der vorherigen Artikel aufbauen. Wenn für Sie Headless-Übersetzungen in AEM also neu sind, empfehlen wir Ihnen, am Anfang zu beginnen und schrittweise vorzugehen.

| Nummer | Artikel | Beschreibung |
|---|---|---|
| 0 | AEM Headless-Übersetzungs-Tour | Dieses Dokument |
| 1 | [Erfahren Sie mehr über Headless-Inhalte und wie Sie sie in AEM übersetzen können.](learn-about.md) | Lernen Sie die Headless-Konzepte, ihre Zuordnung zu AEM und die Theorie der Übersetzung in AEM kennen. |
| 2 | [Erste Schritte mit der Headless-Übersetzung in AEM](getting-started.md) | Erfahren Sie, wie Sie Ihre Headless-Inhalte organisieren und wie die Übersetzungs-Tools von AEM funktionieren. |
| 3 | [Konfigurieren der Übersetzungsintegration](configure-connector.md) | Erfahren Sie, wie Sie AEM mit einem Übersetzungs-Service verbinden. |
| 4 | [Übersetzen von Inhalten](translate-content.md) | Verwenden Sie die Übersetzungsintegration und -regeln, um Ihre Headless-Inhalte zu übersetzen. |
| 5 | [Veröffentlichen übersetzter Inhalte](publish-content.md) | Erfahren Sie, wie Sie Ihre übersetzten Inhalte veröffentlichen und die Übersetzung aktualisieren können, wenn sich die zugrunde liegenden Inhalte ändern. |

## So geht es weiter {#what-is-next}

Jetzt sind Sie bereit, mit Ihrer Adobe Headless-Übersetzungs-Tour zu beginnen. Wir empfehlen Ihnen, mit dem nächsten Teil der Tour fortzufahren und den Artikel [Erfahren Sie mehr über Headless-Inhalte und wie man sie in AEM übersetzt](learn-about.md) zu lesen.

## Zusätzliche Ressourcen {#additional-resources}

Dokumentations-Touren zeigen Ihnen, wie AEM ein Geschäftsproblem löst, indem es eine Erzählung bereitstellt, die Sie durch komplexe, miteinander verknüpfte Prozesse und Funktionen führt. Eine Tour veranschaulicht, wie mehrere Funktionen zusammenarbeiten, um eine einzige Geschäftsanforderung zu erfüllen.

Diese Touren sind so konzipiert, dass sie für sich allein stehen können. Einige davon können jedoch miteinander verbunden werden. In diesen zusätzlichen Touren finden Sie weitere Informationen darüber, wie die leistungsstarken Funktionen von AEM zusammenarbeiten.

* [Headless-Autoren-Tour](/help/journey-headless/author/overview.md) – Diese angeleitete Tour bietet Ihnen eine Einführung zu den leistungsstarken und flexiblen Headless-Funktionen von AEM und deren Möglichkeiten. Sie veranschaulicht, wie Sie bei Ihrem ersten Headless-Entwicklungsprojekt Inhalte modellieren können.
* [Headless-Architekten-Tour](/help/journey-headless/architect/overview.md) – Beginnen Sie hier mit einer Einführung in die leistungsstarken, flexiblen Headless-Funktionen von Adobe Experience Manager as a Cloud Service und erfahren Sie, wie Sie Inhalte für Ihr Projekt modellieren können.
* [AEM Headless-Entwickler-Tour](/help/journey-headless/developer/overview.md) – Diese angeleitete Tour bietet Ihnen eine Einführung zu den leistungsstarken und flexiblen Headless-Funktionen von AEM und deren Möglichkeiten. Sie veranschaulicht, wie Sie sie bei Ihrem ersten Headless-Entwicklungsprojekt nutzen können.
* [AEM as a Cloud Service – Technische Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de) – Wenn Sie bereits über ein solides Verständnis von AEM und Headless-Technologien verfügen, können Sie direkt unsere ausführlichen technischen Dokumente hinzuziehen.
   * [Einführung in AEM als Headless-CMS](/help/headless/introduction.md)
* [AEM-Entwicklerportal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
* [AEM Headless-Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de) – Wenn Sie es vorziehen, durch praktisches Arbeiten zu lernen, und technisch versiert sind, können Sie unsere nach API und Framework geordneten praktischen Tutorials nutzen, in denen die Erstellung und Verwendung von Anwendungen auf der Grundlage von AEM Headless behandelt wird.
