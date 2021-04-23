---
title: Optional - Erstellen von Einzelseitenanwendungen (SPA) mit AEM
description: In dieser optionalen Fortsetzung der AEM Headless Developer-Journey erfahren Sie, wie AEM kopflosen Versand mit herkömmlichen CMS-Funktionen kombinieren und wie Sie bearbeitbare SPA mit AEM Editor-Framework erstellen können.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: 3fd695cbe77873fa57373d91249b71d8c4be8a08
workflow-type: tm+mt
source-wordcount: '1301'
ht-degree: 34%

---


# Erstellen von Einzelseitenanwendungen (SPA) mit AEM {#create-spa}

>[!CAUTION]
>
>ARBEITEN IN FORTSCHRITTEN - Die Schaffung dieses Dokuments ist im Gange und sollte nicht als vollständig oder endgültig betrachtet werden und auch nicht für Produktionszwecke verwendet werden.

In dieser optionalen Fortsetzung der [AEM Headless Developer-Journey erfahren Sie, wie AEM kopflosen Versand mit herkömmlichen CMS-Funktionen kombinieren können und wie Sie bearbeitbare SPA mit AEM Editor-Framework erstellen und externe SPA integrieren können, um die Bearbeitungsfunktionen nach Bedarf zu ermöglichen.](#overview.md)

## Die Meldung bisher {#story-so-far}

An dieser Stelle sollten Sie die gesamte AEM [Headless Developer-Journey](overview.md) abgeschlossen haben und die Grundlagen des Kopflosen Versands in AEM verstehen, einschließlich eines Verständnisses von:

* Der Unterschied zwischen dem Versand für kostenlose und kostenlose Inhalte.
* AEM Funktionen ohne Kopf.
* So organisieren und AEM Headless-Projekt.
* So erstellen Sie kostenlose Inhalte in AEM.
* So können Sie kostenlose Inhalte in AEM abrufen und aktualisieren.
* Wie man mit einem AEM Headless-Projekt live geht.

Sie sind jetzt entweder mit Ihrem ersten AEM Headless-Projekt live gegangen oder haben alle erforderlichen Kenntnisse, um dies zu tun. Herzlichen Glückwunsch!

Warum lesen Sie also diese zusätzliche, optionale Fortsetzung der Journey? Vielleicht erinnern Sie sich daran, dass wir in den [Erste Schritte](getting-started.md#integration-levels) kurz besprochen haben, wie AEM nicht nur kopflosen Versand und herkömmliche Vollstapelmodelle unterstützt, sondern auch Hybridmodelle unterstützen kann, die die Vorteile beider Modelle kombinieren. Auch wenn es sich nicht um das herkömmliche, kopflose Modell handelt, können solche Hybridmodelle für bestimmte Projekte eine beispiellose Flexibilität Angebot haben.

Dieser Artikel baut auf Ihren Kenntnissen von AEM Headless auf, indem Sie eingehend untersuchen, wie Sie Ihre eigenen einseitigen Anwendungen (SPA) erstellen können, die tatsächlich in AEM bearbeitet werden können. Auf diese Weise können Sie Inhalte erstellen und sie ohne weiteres in einen SPA Versand einfügen, aber dieser SPA bleibt in AEM bearbeitbar.

## Vorgabe {#objective}

In diesem Dokument erfahren Sie, wie Einzelseitenanwendungen mithilfe des AEM SPA Editor-Frameworks entwickelt werden. Nach dem Lesen dieses Dokuments sollten Sie:

* Machen Sie sich mit der grundlegenden Funktion des SPA-Editors vertraut.
* Machen Sie sich mit den Anforderungen für den Aufbau einer vollständig editierbaren SPA für AEM vertraut.
* Verstehen Sie, wie externe SPA in AEM integriert werden können.
* Verstehen Sie, wie serverseitiges Rendering implementiert werden sollte oder sollte.

## Anforderungen und Voraussetzungen {#requirements-prerequisites}

Es gibt eine Reihe von Anforderungen, bevor Sie mit SPA in AEM arbeiten.

### Wissen {#knowledge}

* Entwicklungs-Erfahrung beim Erstellen von SPA mit React- oder Angular-Frameworks
* Grundlegende AEM zum Erstellen von Inhaltsfragmenten und zum Verwenden des Editors
* Achten Sie darauf, das Dokument [Kopflos und Kopflos in AEM](/help/implementing/developing/headful-headless.md) zu überprüfen, um die verschiedenen Ebenen SPA Integration zu verstehen.

### Tools {#tools}

* Sandbox-Zugriff zum Testen der Bereitstellung Ihres Projekts
* Lokale Entwicklungsinstanz für Datenmodellierung und Tests
* Vorhandene externe SPA (optional, je nach ausgewähltem Integrationsmodell)
* AEM-Projektarchetyp

## Was ist eine SPA? {#what-is-a-spa}

Eine Single Page Application (SPA) unterscheidet sich von einer herkömmlichen Seite insofern, als sie Client-seitig gerendert wird und primär JavaScript-gesteuert ist. Dabei wird auf Ajax-Aufrufe zurückgegriffen, um Daten zu laden und die Seite dynamisch zu aktualisieren. Der Großteil der Inhalte oder alle Inhalte werden einmal in einem einzelnen Seiten-Load abgerufen, wobei je nach Benutzerinteraktion mit der Seite asynchron zusätzliche Ressourcen geladen werden.

So wird der Bedarf nach Seitenaktualisierungen reduziert und dem Benutzer ein Erlebnis präsentiert, das nahtlos und schnell ist und eher wie eine native App funktioniert.

Der AEM-SPA-Editor ermöglicht es Frontend-Entwicklern, SPAs zu erstellen, die sich in eine AEM-Site integrieren lassen, damit Inhaltsautoren SPA-Inhalte so einfach bearbeiten können wie andere AEM-Inhalte.

## Warum eine SPA? {#why-spa}

Da SPAs schneller, nahtloser und eher wie ein natives Programm sind, sind sie nicht nur für Besucher der Web-Seite, sondern auch für Marketing-Experten und Entwickler attraktiv. Das hängt mit der Art und Weise zusammen, wie SPAs funktionieren.

Eine vollständige Beschreibung der SPA und der Gründe für ihre Verwendung finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) für Links zu einer ausführlicheren Dokumentation.

## SPA AEM

Bei der Entwicklung von Single Page Applications in AEM wird davon ausgegangen, dass sich der Frontend-Entwickler beim Erstellen einer SPA an die üblichen Best Practices hält. Wenn Sie als Frontend-Entwickler diese allgemeinen Best Practices sowie einige AEM-spezifische Prinzipien befolgen, wird Ihre SPA mit AEM und seinen Inhaltsverfassungsfunktionen zusammenarbeiten.

* **Portabilität**  - Wie bei allen Komponenten sollten die SPA so tragbar wie möglich gebaut werden. Die SPA sollte aus portablen und wiederverwendbaren Komponenten bestehen.
* **AEM verwaltet die Site-Struktur**: Der Frontend-Entwickler erstellt Komponenten und ist für deren interne Struktur verantwortlich, verlässt sich bei der Definition der Inhaltsstruktur der Site jedoch auf AEM.
* **Dynamisches Rendering**: Alle Rendering-Vorgänge sollten dynamisch sein.
* **Dynamisches Routing**: Die SPA ist für das Routing verantwortlich; AEM lauscht darauf und ruft Inhalte auf dieser Basis ab. Jegliches Routing sollte ebenfalls dynamisch sein.

Eine vollständige Beschreibung der Handhabung von SPA finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) für Links zu einer ausführlicheren Dokumentation.

## Der AEM SPA-Editor {#aem-spa-editor}

Sites, die mit gängigen SPA-Frameworks wie React und Angular erstellt wurden, laden ihren Inhalt über dynamisches JSON und weisen nicht die HTML-Struktur auf, die für den Seiteneditor von AEM erforderlich ist, um Steuerelemente zur Bearbeitung platzieren zu können.

Um die Bearbeitung von SPAs innerhalb von AEM zu ermöglichen, ist eine Zuordnung zwischen der JSON-Ausgabe der SPA und dem Inhaltsmodell im AEM-Repository erforderlich, damit Änderungen am Inhalt gespeichert werden können.

Mit der SPA-Unterstützung wird in AEM ein JS-Thin Layer eingeführt. Dieses interagiert mit dem SPA-JS-Code, wenn es in den Seiten-Editor geladen wird, mit dem Ereignisse gesendet und der Speicherort für die Steuerelemente zur Bearbeitung aktiviert werden kann, um eine kontextbezogene Bearbeitung zu ermöglichen. Diese Funktion baut auf dem Content Services API Endpoint-Konzept auf, da die Inhalte aus der SPA über Content Services geladen werden müssen.

Eine vollständige Beschreibung des AEM-SPA-Editors finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) unter Links zu einer ausführlicheren Dokumentation.

## Bestehende SPA {#existing-spas} unterbringen

Wenn Sie über eine bestehende SPA verfügen, unterstützt AEM die Einbettung in AEM, damit diese für Ihre Inhaltsersteller im AEM-Editor sichtbar ist. Dies kann sehr hilfreich sein, um den Inhalt, den sie erstellen, über Inhaltsfragmente im Kontext der Endanwendung Ansicht, in der er verwendet wird.

Darüber hinaus können Sie mit nur kleinen Änderungen bestimmte Bearbeitungsmöglichkeiten für die externe SPA im AEM-Editor aktivieren.

Die RemotePage-Komponente ermöglicht die Wiedergabe einer externen SPA in AEM.

Eine vollständige Beschreibung, wie Sie eine externe SPA in AEM editierbar machen, finden Sie unter [Zusätzliche Ressourcen](#additional-resources) unter Links zu einer ausführlicheren Dokumentation.

## Wie geht es weiter {#what-is-next}

Lesen Sie die folgenden Dokumente, um Ihre eigenen SPA für AEM zu entwickeln:

* [SPA-WKND-Tutorial](/help/implementing/developing/hybrid/wknd-tutorial.md)
* [Erste Schritte mit React](/help/implementing/developing/hybrid/getting-started-react.md)
* [Erste Schritte mit Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Wenn Sie eine vorhandene SPA anpassen müssen, um sie in AEM zu verwenden, lesen Sie die folgenden Dokumente:

* [Die RemotePage-Komponente](/help/implementing/developing/hybrid/remote-page.md)
* [Bearbeiten einer externen SPA in AEM](/help/implementing/developing/hybrid/editing-external-spa.md)

Siehe unten für [weitere Ressourcen](#additional-resources), die Sie tiefer in SPA Themen in AEM einbinden können.

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie einige zusätzliche Ressourcen, die einen tieferen Einstieg in einige der in diesem Dokument erwähnten Konzepte ermöglichen.

* [Headful und Headless in AEM](/help/implementing/developing/headful-headless.md)  - Eine Beschreibung der verschiedenen Versand-Modelle in AEM
* [SPA-Einführung und exemplarische Vorgehensweise.](/help/implementing/developing/hybrid/introduction.md) - Eine gute Einführung in SPA in AEM
* [Entwicklung von SPA für AEM](/help/implementing/developing/hybrid/developing.md)  - Leitlinien für die Entwicklung von SPA für AEM
* [SPA Editor Übersicht](/help/implementing/developing/hybrid/editor-overview.md)  - Details zur Funktionsweise des SPA
* [Serverseitiges Rendering](/help/implementing/developing/hybrid/ssr.md)  - So konfigurieren Sie SSR für AEM SPA
* [SPA Referenz-Dokumente](/help/implementing/developing/hybrid/reference-materials.md)  - JavaScript-API-Verweise und Verknüpfungen zu Open-Source-AEM GitHub-Projekten
* [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md)  - Erstellen von Inhaltsfragmenten
* [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)  - Maven-Vorlage, die ein minimales, auf Best Practices basierendes Adobe Experience Manager-Projekt (AEM) als Ausgangspunkt für Ihre Website erstellt
