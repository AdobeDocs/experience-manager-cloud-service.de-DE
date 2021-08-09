---
title: AEM Headless-Entwickler-Tour
description: Beginnen Sie hier Ihre geführte Tour durch die leistungsstarken und flexiblen Headless-Funktionen von AEM und ihre Möglichkeiten und erfahren Sie, wie Sie diese in Ihrem ersten Entwicklungsprojekt nutzen können.
source-git-commit: bec1e901e19abc9ae99dbf95878e51c9b000a5ee
workflow-type: ht
source-wordcount: '736'
ht-degree: 100%

---


# AEM Headless-Entwickler-Tour {#aem-headless-developer-journey}

Beginnen Sie hier Ihre geführte Tour durch die leistungsstarken und flexiblen Headless-Funktionen von AEM und ihre Möglichkeiten und erfahren Sie, wie Sie diese in Ihrem ersten Headless-Entwicklungsprojekt nutzen können.

## Einführung {#introduction}

Die Headless-Implementierung wird immer wichtiger, wenn es darum geht, Erlebnisse für Ihr Zielgruppe überall und unabhängig vom Kanal bereitzustellen.

Die Headless-Implementierung verzichtet auf das Seiten- und Komponenten-Management, wie es bei Full-Stack-Lösungen üblich ist, und konzentriert sich auf die Erstellung kanalneutraler, wiederverwendbarer Inhaltsfragmente und deren kanalübergreifende Bereitstellung. Es handelt sich um ein modernes und dynamisches Entwicklungsmuster zur Implementierung von digitalen Erlebnissen.

Dieser Leitfaden führt Sie durch die wichtigsten Themen, sodass Sie nach Abschluss:

* ein umfassendes Verständnis davon haben werden, was die Headless-Inhaltsbereitstellung ist und welche Vorteile sie hat,
* die AEM Headless-Funktionen und die Art, wie sie zusammenarbeiten, um ein Headless-Erlebnis bereitzustellen, verstehen,
* die ersten Schritte zur Implementierung Ihres ersten AEM Headless-Projekts ausführen können.

## Zielgruppe {#audience}

Diese Tour ist für die Entwickler-Persona konzipiert. Sie legt die Anforderungen, Schritte und den Ansatz eines AEM Headless-Projekts aus Entwicklersicht dar. In der Tour werden weitere Personas definiert, mit denen der Entwickler für ein erfolgreiches Projekt interagieren muss, aber die Sichtweise in die Tour ist die des Entwicklers.

Die Informationen in dieser Tour können natürlich auch für andere Personas nützlich sein, doch einige Informationen werden für bestimmte Rollen überflüssig sein. Warten Sie auf die nächsten Touren, die weitere Rollen behandeln werden.

## Die Headless-Entwickler-Tour {#the-journey}

In dieser Tour werden Sie viele Themen kennenlernen. Die folgenden Artikel vermitteln Ihnen Grundlagenwissen zu Headless in AEM und verlinken auf detaillierte technische Dokumentationen.

Obwohl Sie direkt zu einem bestimmten Teil der Tour gehen können, beachten Sie, dass viele Konzepte auf denen der vorherigen Artikel aufbauen. Wenn Sie also neu bei Headless in AEM sind, empfehlen wir Ihnen, am Anfang zu beginnen und nach und nach voranzuschreiten.

| # | Artikel | Beschreibung |
|---|---|---|
| 0 | AEM Headless-Entwickler-Tour | Dieses Dokument |
| 1 | [Informationen zur CMS-Headless-Entwicklung](learn-about.md) | Erfahren Sie mehr über die Headless-Technologie und wann sie verwendet werden sollte. |
| 2 | [Erste Schritte mit AEM Headless as a Cloud Service](getting-started.md) | Erfahren Sie mehr über die Voraussetzungen für AEM Headless |
| 3 | [Der Weg zu Ihrem ersten Erlebnis mit AEM Headless](path-to-first-experience.md) | Einrichten der Entwicklungsumgebung und Lernen, wie man ein einfaches Programm mit AEM Headless integriert |
| 4 | [Erfahren Sie, wie Sie Ihre Inhalte modellieren](model-your-content.md) | Erfahren Sie, wie Sie Ihre Inhaltsstruktur modellieren. Setzen Sie dann diese Struktur für Adobe Experience Manager (AEM) mithilfe von Inhaltsfragmentmodellen und Inhaltsfragmenten um, um sie kanalübergreifend wiederzuverwenden. |
| 5 | [Zugriff auf Ihre Inhalte über AEM-Bereitstellungs-APIs](access-your-content.md) | Erfahren Sie, wie Sie mit GraphQL-Abfragen auf die Inhalte Ihrer Inhaltsfragmente zugreifen können. |
| 6 | [Aktualisieren Ihres Inhalts über AEM Assets-APIs](update-your-content.md) | Erfahren Sie, wie Sie mit der REST-API auf die Inhalte Ihrer Inhaltsfragmente zugreifen und diese aktualisieren können. |
| 7 | [So fügen Sie alles zusammen – Ihr Programm und Ihre Inhalte in AEM Headless](put-it-all-together.md) | Erfahren Sie, wie Sie mit dem AEM Headless-SDK Ihr AEM-Projekt für den Go-live vorbereiten können. |
| 8 | [So gehen Sie mit Ihrer Headless-Anwendung live](go-live.md) | Erfahren Sie, wie Sie eine Anwendung live bereitstellen und Ihren lokalen Code in Git für die CI/CD-Pipeline in das Cloud Manager Git verschieben. |
| 9 | [Optional – So erstellen Sie Single Page Applications (SPA) mit AEM](create-spa.md) | Sobald Sie die Headless-Funktionen von AEM verstanden haben, erfahren Sie, wie Sie Headful- und Headless-Bereitstellung kombinieren können, und Sie lernen, wie Sie mit dem SPA-Editor-Framework von AEM bearbeitbare SPA erstellen können. |

## Wie geht es weiter {#what-is-next}

Sie sind jetzt bereit, Ihre Adobe Headless-Tour zu beginnen. Wir empfehlen Ihnen, mit dem nächsten Teil der Tour fortzufahren und den Artikel [Weitere Infos zur CMS-Headless-Entwicklung](learn-about.md) zu lesen.

### Wählen Sie Ihr eigenes Abenteuer {#choose-your-path}

Adobe möchte jedoch, dass Sie Erfolg haben, wenn Sie mit Ihrem AEM Headless-Projekt beginnen, unabhängig von Ihrem Lernstil. Ziehen Sie also bitte diese beiden Optionen in Betracht:

* Wenn Sie sich weiter mit **Headless-Konzepten und den Headless-Technologien von AEM beschäftigen möchten**, sollten Sie als Nächstes das Dokument [So modellieren Sie Ihre Inhalte als AEM-Inhaltsmodelle](model-your-content.md) lesen, in dem Sie lernen, wie Sie Ihre Inhaltsstruktur in AEM modellieren.
* Wenn Sie es vorziehen, durch **praktische Übungen** zu lernen, können Sie zum [praktischen Tutorial Erste Schritte mit AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=de) wechseln, in dem Sie direkt in die AEM Headless-Entwicklung einsteigen, indem Sie ein einfaches Projekt implementieren, um AEM Headless-Inhalte darzustellen.
