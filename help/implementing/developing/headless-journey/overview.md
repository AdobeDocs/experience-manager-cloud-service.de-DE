---
title: AEM Developer Journey
description: Beginn hier für eine geführte Journey durch die leistungsstarken und flexiblen, kopflosen Funktionen von AEM, deren Fähigkeiten und wie man sie bei Ihrem ersten Entwicklungsprojekt einsetzt.
hide: true
hidefromtoc: true
index: false
exl-id: 4524c92a-8f19-497a-b4f2-c3e23f555d37
source-git-commit: a2588f420258522cc3a4b7b10f4ab52f2dd669d8
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 3%

---

# AEM Developer Journey {#aem-headless-developer-journey}

>[!CAUTION]
>
>ARBEITEN IN FORTSCHRITTEN - Die Schaffung dieses Dokuments ist im Gange und sollte nicht als vollständig oder endgültig betrachtet werden und auch nicht für Produktionszwecke verwendet werden.

Beginn hier für eine geführte Journey durch die leistungsstarken und flexiblen, kopflosen Funktionen von AEM, deren Fähigkeiten und wie man sie bei Ihrem ersten, kopflosen Entwicklungsprojekt einsetzt.

## Einführung {#introduction}

Die Implementierung ohne Kopf wird immer wichtiger, wenn Sie Erlebnisse für Ihre Audience bereitstellen möchten, egal wo sie sich befinden und unabhängig vom Kanal.

Bei der Implementierung ohne Kopfdaten wird das Seiten- und Komponentenmanagement verloren, wie es bei Vollstapellösungen üblich ist, und der Schwerpunkt liegt auf der Erstellung von Kanal-neutralen, wiederverwendbaren Inhaltsfragmenten und deren Cross-Kanal-Versand. Es handelt sich um ein modernes und dynamisches Entwicklungsmuster zur Implementierung von Web-Erlebnissen.

Dieser Leitfaden führt Sie durch die wichtigsten Themen, sodass Sie nach Abschluss des Projekts:

* Verstehen Sie, was Versand ohne Inhalt ist und welche Vorteile es bringt.
* Verstehen Sie AEM überflüssige Funktionen und wie sie zusammenarbeiten, um ein abwertendes Erlebnis zu bieten.
* Sie haben die Möglichkeit, die ersten Schritte zur Implementierung Ihres ersten AEM ohne Kopf durchzuführen.

## Audience {#audience}

Diese Journey wurde für die Entwickler-Persona konzipiert, um die Anforderungen, Schritte und den Ansatz eines AEM Headless-Projekts aus Entwicklersicht darzustellen. Die Journey definiert zusätzliche Personen, mit denen der Entwickler für ein erfolgreiches Projekt interagieren muss, aber die Ansicht für die Journey ist die des Entwicklers.

Informationen in dieser Journey können natürlich für andere Personen nützlich sein, aber einige Informationen werden für bestimmte Rollen überflüssig sein. Bleiben Sie dran für kommende Journey, die weitere Rollen übernehmen.

## Die Headless-Entwickler-Journey {#the-journey}

Sie werden viele Themen in dieser Journey untersuchen. Die folgenden Artikel vermitteln Ihnen grundlegende Kenntnisse über Kopfloses in AEM und verweisen auf eine detaillierte technische Dokumentation.

Obwohl Sie direkt zu einem bestimmten Teil der Journey wechseln können, basieren viele Konzepte auf denen in vorherigen Artikeln. Wenn Sie also neu in AEM sind, sollten Sie am Anfang und in der Folge Beginn machen.

| # | Artikel | Beschreibung |
|---|---|---|
| 0 | AEM Developer Journey | Dieses Dokument |
| 1 | [Weitere Informationen zur CMS-Headless-Entwicklung](learn-about.md) | Erfahren Sie mehr über die Headless-Technologie und wann sie verwendet werden soll. |
| 2 | [Erste Schritte mit AEM Headless als Cloud Service](getting-started.md) | Erfahren Sie mehr über AEM Voraussetzungen für das Überschreiben |
| 3 | [Pfad zum ersten Erlebnis mit AEM Kopflos](path-to-first-experience.md) | Einrichten Ihrer Entwicklungs-Umgebung und Erfahren Sie, wie Sie eine einfache App mit AEM Headless integrieren können |
| 4 | [So modellieren Sie Ihren Inhalt](model-your-content.md) | Erfahren Sie, wie Sie Ihre Inhaltsstruktur modellieren. Anschließend können Sie diese Struktur für Adobe Experience Manager (AEM) mithilfe von Inhaltsfragmentmodellen und Inhaltsfragmenten zur Wiederverwendung über mehrere Kanal hinweg nutzen. |
| 5 | [Zugriff auf Ihre Inhalte über AEM Versand-APIs](access-your-content.md) | Erfahren Sie, wie Sie mit GraphQL-Abfragen auf Ihre Inhaltsfragmente zugreifen können. |
| 6 | [Aktualisieren von Inhalten über AEM Assets-APIs](update-your-content.md) | Erfahren Sie, wie Sie mit der REST-API auf Ihre Inhalte für Inhaltsfragmente zugreifen und diese aktualisieren können. |
| 7 | [Wie Sie alles zusammenstellen - Ihre App und Ihr Inhalt in AEM Kopflos](put-it-all-together.md) | Erfahren Sie, wie Sie Ihr AEM Projekt, einschließlich Inhaltsfragmente, Ihre GraphQL-Aufrufe, Ihre REST API-Aufrufe und Ihre Anwendung, durchführen und es für den Live-Betrieb vorbereiten. |
| 8 | [Wie Sie mit Ihrem kostenlosen Programm live gehen](go-live.md) | Erfahren Sie, wie Sie die Anwendung live bereitstellen und Ihren lokalen Code in Git übernehmen und in die Cloud Manager Git for CI/CD-Pipeline verschieben. |
| 9 | [Optional - Erstellen von Einzelseitenanwendungen (SPA) mit AEM](create-spa.md) | Sobald Sie AEM Funktionen ohne Kopfdaten kennen, erfahren Sie, wie Sie mit dem kostenlosen und kostenlosen Versand kombinieren und wie Sie editierbare SPA mit AEM Editor-Framework erstellen könnenSPA. |

## Wie geht es weiter {#what-is-next}

Sie sind jetzt bereit, mit Ihrer Adobe Headless Journey zu beginnen. Wir empfehlen Ihnen, mit dem nächsten Teil der Journey fortzufahren und den Artikel [Weitere Informationen zu CMS Headless Development.](learn-about.md)

### Wählen Sie Ihr eigenes Abenteuer {#choose-your-path}

Die Adobe möchte jedoch, dass Sie beim Einstieg in Ihr AEM Headless-Projekt Erfolg haben, unabhängig von Ihrem Lernstil. Überlegen Sie daher bitte diese beiden Optionen.

* Wenn Sie weiterhin **mit den kostenlosen Konzepten und AEM kostenlosen Technologien** arbeiten möchten, sollten Sie Ihre AEM kopflosen Journey fortsetzen, wie empfohlen, indem Sie das Dokument [Wie Sie Ihren Inhalt als AEM Inhaltsmodelle modellieren](model-your-content.md) überprüfen, in dem Sie lernen, wie Sie Ihre Inhaltsstruktur in AEM modellieren.
* Wenn Sie lieber **lernen möchten, indem Sie** ausführen, können Sie zum [Erste Schritte mit AEM praxisnahen Lernprogramm ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) springen, in dem Sie direkt in AEM Headless-Entwicklung springen, indem Sie ein einfaches Projekt implementieren, um AEM kostenlose Inhalte bereitzustellen.
