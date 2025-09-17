---
title: Entwickler-Tour für AEM Headless CMS
description: Erfahren Sie mehr über die Headless-Entwicklung mit Adobe Experience Manager (AEM) als Headless-CMS. Erfahren Sie, wie Sie Funktionen wie Inhaltsmodelle, Inhaltsfragmente und eine GraphQL-API verwenden können, um die Bereitstellung von Headless-Inhalten zu ermöglichen.
landing-page-description: Gewinnen Sie ein Verständnis für die Bereitstellung und Implementierung von Headless-Inhalten. Erfahren Sie mehr über die Entwicklung einer Strategie für Ihr Unternehmen.
exl-id: d14a1e30-dd04-49a8-8cda-27c80a4bb0f5
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 20914cde3be3ff3061b061d930154bd72da45d11
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 100%

---

# Entwickler-Tour für AEM Headless CMS {#aem-headless-developer-journey}

Willkommen in der Dokumentation für Entwickler, die neu bei Adobe Experience Manager Headless CMS sind!

Erfahren Sie mehr über die leistungsstarken und flexiblen Headless-Funktionen, ihre Möglichkeiten und darüber, wie Sie sie in Ihrem ersten Headless-Entwicklungsprojekt einsetzen können. Im Rahmen dieser Tour erhalten Sie die gesamten Informationen, die Sie zur Entwicklung Ihrer ersten Headless-Anwendung benötigen.

>[!CONTEXTUALHELP]
>id="aemcloud_headless_developer_resources"
>title="AEM Headless-Entwicklungsressourcen und erweiterte Dokumentation"
>abstract="Alles, was Sie benötigen, um mehr über AEM Headless-CMS zu erfahren und bessere Anwendungen und schnellere Erlebnisse zu entwickeln und bereitzustellen."


## Einführung  {#introduction}

Die Headless-Implementierung von AEM verwendet Inhaltsfragmentmodelle und Inhaltsfragmente, um sich auf die Erstellung von strukturierten, kanalneutralen und wiederverwendbaren Inhaltsfragmenten und deren kanalübergreifende Bereitstellung zu konzentrieren. Um dies zu erreichen, wird auf die Seiten- und Komponentenverwaltung verzichtet, wie sie bei Full-Stack-Lösungen üblich ist. Es handelt sich um ein modernes und dynamisches Entwicklungsmuster zur Implementierung von digitalen Erlebnissen.

Dieses Handbuch führt Sie durch Themen der Headless-Implementierung in AEM, sodass Sie nach Abschluss über Folgendes verfügen:

* Umfassendes Verständnis davon, was die Headless-Bereitstellung von Inhalten ist und welche Vorteile sie bietet
* Kenntnisse der Headless-Funktionen von AEM und wie sie zusammenarbeiten, um Headless-Erlebnisse bereitzustellen
* Fähigkeit zur Durchführung der ersten Schritte zur Implementierung Ihres ersten AEM Headless-Projekts.

>[!TIP]
>
> Wenn Sie es vorziehen, **durch praktische Anwendungen zu lernen** und bereits über AEM-Kenntnisse verfügen, können Sie die Headless-Tutorials für AEM nutzen, die nach API und Framework geordnet sind und im Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments zur Verfügung stehen.

## Zielgruppe {#audience}

Diese Tour ist speziell für die Rolle des Entwicklers ausgelegt und legt die Anforderungen und Schritte sowie den Ansatz von AEM Headless-Projekten aus Entwicklersicht dar. Sie definiert weitere Rollen, mit denen Entwickler interagieren müssen, um zum Gelingen von Projekten beizutragen. Zugeschnitten ist die Tour jedoch auf Entwickler.

Im Folgenden finden Sie die Rollen, die in dieser Tour interagieren.

| Persona | Beschreibung | Rolle in dieser Tour |
|---|---|---|
| Entwickler (Zielgruppe) | Hat Erfahrung mit der Entwicklung von Headless-Anwendungen, die Inhalte aus verschiedenen Quellen nutzen | Zielgruppe dieser Tour |
| Inhaltsautor | Erstellt und verwaltet Inhalte, die „headless“ bereitgestellt werden. | Inhaltsautoren erstellen Inhalte, die der Entwickler „headless“ bereitstellt. |
| Administrator | Verwaltet die grundlegende Einrichtung und Konfiguration von AEM | Der Entwickler arbeitet mit dem Administrator zusammen, um für die Entwicklung erforderliche Konfigurationsänderungen vorzunehmen. |
| Inhaltsarchitekt | Analysiert die Anforderungen an die Daten, die „headless“ bereitgetellt werden müssen, und definiert die Struktur für diese Daten. | Die Entwickler arbeiten mit dem Inhaltsarchitekten zusammen, um die Struktur der Daten und die Anforderungen für die Headless-Bereitstellung der Daten zu verstehen. |

## Die Headless-Entwickler-Tour {#the-journey}

Wir werden auf dieser Tour viele Themen behandeln, die Ihnen das Grundwissen über Headless-Konzepte in AEM vermitteln.

Obwohl Sie direkt zu einem bestimmten Teil der Tour gehen können, sollten Sie beachten, dass viele Konzepte auf denen der vorherigen Artikel aufbauen. Adobe empfiehlt deswegen, am Anfang zu beginnen und schrittweise vorzugehen.

| Nummer | Artikel | Beschreibung |
|---|---|---|
| 0 | AEM Headless-Entwickler-Tour | Dieses Dokument |
| 1 | [Erfahren Sie mehr über die CMS-Headless-Entwicklung](learn-about.md) | Hier erfahren Sie mehr über Headless-Technologie und wann sie verwendet werden kann. |
| 2 | [Erste Schritte mit AEM Headless as a Cloud Service](getting-started.md) | Hier erfahren Sie mehr über die Voraussetzungen für AEM Headless. |
| 3 | [Gestalten Ihres ersten Erlebnisses mit AEM Headless ](path-to-first-experience.md) | Richten Sie Ihre Entwicklungsumgebung ein und erfahren Sie, wie Sie ein einfaches Programm mit AEM Headless integrieren. |
| 4 | [Erfahren Sie, wie Sie Ihre Inhalte modellieren](model-your-content.md) | Erfahren Sie, wie Sie Ihre Inhaltsstruktur modellieren. |
| 5 | [Zugreifen auf Ihre Inhalte über AEM-Bereitstellungs-APIs](access-your-content.md) | Hier erfahren Sie, wie Sie mit GraphQL-Abfragen auf Ihre Inhaltsfragmente zugreifen können. |
| 6 | [So aktualisieren Sie Ihre Inhalte über AEM Assets-APIs:](update-your-content.md) | Hier erfahren Sie, wie Sie mit einer REST-API Ihre Inhaltsfragmente aktualisieren können. |
| 7 | [So fügen Sie alles zusammen – Ihr Programm und Ihre Inhalte in AEM Headless](put-it-all-together.md) | Erfahren Sie, wie Sie mit dem AEM Headless-SDK Ihr AEM-Projekt für den Go-live vorbereiten können. |
| 8 | [Live-Schalten Ihres Headless-Programms](go-live.md) | Hier erfahren Sie, wie Sie Ihre Anwendung live bereitstellen, indem Sie Ihren lokalen Code von Git in den Cloud Manager-Git für die CI/CD-Pipeline verschieben. |
| 9 | [Optional – Erstellen von Single Page Applications (SPA) mit AEM](create-spa.md) | Erkunden Sie, wie Sie Headful- und Headleass-Bereitstellung kombinieren und lernen Sie, wie Sie mit dem SPA-Editor-Framework von AEM bearbeitbare SPAs erstellen können. |

{style="table-layout:auto"}

## So geht es weiter {#what-is-next}

Um zu beginnen, schauen Sie sich den nächsten Artikel an: [Erfahren Sie mehr über die Entwicklung von CMS Headless](learn-about.md).

### Wählen Sie Ihren eigenen Weg {#choose-your-path}

Lernen Sie lieber in Ihrem eigenen Tempo? Sehen Sie sich diese Optionen an:

* Wenn Sie darüber hinaus **mehr über Headless-Konzepte und -Technologien von AEM** erfahren möchten, sollten Sie Ihre AEM Headless-Tour wie empfohlen fortsetzen, indem Sie sich das Dokument [Modellieren Ihres Inhalts](model-your-content.md) ansehen. Hier erfahren Sie, wie Sie Ihre Content-Struktur in AEM modellieren.
* Wenn Sie **praktische Erfahrungen** vorziehen, empfehlen wir Ihnen das praxisnahe Tutorial [Erste Schritte mit AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=de). Dort können Sie sich direkt mit der AEM Headless-Entwicklung vertraut machen, indem Sie ein einfaches Projekt implementieren, um AEM Headless-Inhalte bereitzustellen.

## Zusätzliche Ressourcen {#additional-resources}

Dokumentations-Touren zeigen Ihnen, wie AEM ein Geschäftsproblem löst, indem sie Ihnen eine Erzählung bieten, die Sie durch miteinander verknüpfte Prozesse und Funktionen führt. Eine Tour veranschaulicht, wie mehrere Funktionen zusammenarbeiten, um eine einzige Geschäftsanforderung zu erfüllen.

In diesen zusätzlichen Touren finden Sie weitere Informationen darüber, wie die leistungsstarken Funktionen von AEM zusammenarbeiten.

* Das [AEM-Entwicklerportal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
* [AEM Headless-Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de): Wenn Sie es vorziehen, durch praktisches Arbeiten zu lernen, und technisch in AEM versiert sind, können Sie unsere nach API und Framework geordneten praktischen Tutorials nutzen, in denen die Erstellung und Verwendung von Anwendungen auf der Grundlage von AEM Headless behandelt wird.
* [AEM Headless Übersetzungs-Tour](/help/journey-headless/translation/overview.md) – Diese Dokumentations-Tour vermittelt Ihnen ein umfassendes Verständnis der Headless-Technologie sowie davon, wie AEM Headless Inhalte bereitstellt und wie Sie sie übersetzen können.
* [Headless-Autoren-Tour](/help/journey-headless/author/overview.md) – Diese angeleitete Tour bietet Ihnen eine Einführung zu den leistungsstarken und flexiblen Headless-Funktionen von AEM und deren Möglichkeiten. Sie veranschaulicht, wie Sie sie bei Ihrem ersten Headless-Projekt Inhalte modellieren können.
* [Headless-Architekten-Tour](/help/journey-headless/architect/overview.md) – Beginnen Sie hier mit einer Einführung in die leistungsstarken, flexiblen Headless-Funktionen von Adobe Experience Manager as a Cloud Service und erfahren Sie, wie Sie Inhalte für Ihr Projekt modellieren können.
* [Technische Dokumentation zu AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de) – Wenn Sie bereits über ein solides Verständnis von AEM und Headless-Technologien verfügen, können Sie direkt unsere ausführlichen technischen Dokumente hinzuziehen.
   * [Einführung in AEM als Headless-CMS](/help/headless/introduction.md)
