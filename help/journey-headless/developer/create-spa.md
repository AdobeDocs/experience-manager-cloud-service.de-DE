---
title: Optional - Erstellen von Einzelseiten-Apps (SPA) mit AEM
description: In dieser optionalen Fortsetzung der AEM Headless-Entwickler-Journey erfahren Sie, wie AEM Headless-Bereitstellung mit herkömmlichen Full-Stack-CMS-Funktionen kombinieren und wie Sie bearbeitbare SPA mit AEM Editor-Framework erstellen können.
source-git-commit: ddd320ae703225584d4a2055d0f882d238d60987
workflow-type: tm+mt
source-wordcount: '1273'
ht-degree: 35%

---


# Erstellen von Einzelseiten-Apps (SPA) mit AEM {#create-spa}

In dieser optionalen Fortsetzung der [AEM Headless-Entwickler-Journey,](overview.md) erfahren Sie, wie AEM Headless-Bereitstellung mit herkömmlichen Full-Stack-CMS-Funktionen kombinieren und wie Sie bearbeitbare SPA mit AEM Editor-Framework erstellen sowie externe SPA integrieren können, um Bearbeitungsfunktionen nach Bedarf zu ermöglichen.

## Die Geschichte bisher {#story-so-far}

An dieser Stelle sollten Sie die gesamte [AEM Headless-Entwickler-Journey](overview.md) abgeschlossen haben und die Grundlagen der Headless-Bereitstellung in AEM verstehen, einschließlich folgender Punkte:

* Der Unterschied zwischen Headless- und Headful-Content-Bereitstellung.
* AEM Headless-Funktionen.
* Organisieren und AEM des Headless-Projekts.
* So erstellen Sie Headless-Inhalte in AEM.
* So rufen Sie Headless-Inhalte in AEM ab und aktualisieren sie.
* Wie man mit einem AEM Headless-Projekt live geht.

Sie sind jetzt entweder mit Ihrem ersten AEM Headless-Projekt live gegangen oder verfügen über alle erforderlichen Kenntnisse. Herzlichen Glückwunsch!

Warum lesen Sie also diese zusätzliche, optionale Fortsetzung der Journey? Wahrscheinlich erinnern Sie sich daran, dass wir in [Erste Schritte](getting-started.md#integration-levels) kurz besprochen haben, wie AEM nicht nur Headless-Bereitstellung und herkömmliche Full-Stack-Modelle unterstützt, sondern auch Hybridmodelle unterstützen kann, die die Vorteile beider Modelle kombinieren. Obwohl dies nicht das traditionelle Headless-Modell ist, können derartige Hybridmodelle bestimmten Projekten eine beispiellose Flexibilität bieten.

Dieser Artikel baut auf Ihren Kenntnissen von AEM Headless auf, indem Sie eingehend untersuchen, wie Sie Ihre eigenen Single-Page-Anwendungen (SPA) erstellen können, die in AEM tatsächlich bearbeitbar sind. Auf diese Weise können Sie Inhalte erstellen und an einen SPA senden, dieser SPA bleibt jedoch in AEM bearbeitbar.

## Vorgabe {#objective}

In diesem Dokument erfahren Sie, wie Single Page Applications mithilfe des AEM SPA Editor-Frameworks entwickelt werden. Nach Lesen dieses Dokuments sollten Sie Folgendes tun:

* Machen Sie sich mit der grundlegenden Funktion des SPA-Editors vertraut.
* Machen Sie sich mit den Anforderungen zum Erstellen einer vollständig bearbeitbaren SPA für AEM vertraut.
* Erfahren Sie, wie externe SPA in AEM integriert werden können.
* Erfahren Sie, wie das serverseitige Rendering implementiert werden sollte oder nicht.

## Anforderungen und Voraussetzungen {#requirements-prerequisites}

Bevor Sie in AEM mit SPA arbeiten, müssen Sie eine Reihe von Anforderungen erfüllen.

### Wissen {#knowledge}

* Entwicklungs-Erlebnis beim Erstellen von SPA mit React- oder Angular-Frameworks
* Grundlegende AEM beim Erstellen von Inhaltsfragmenten und Verwenden des Editors
* Sehen Sie sich das Dokument [Headful und Headless in AEM](/help/implementing/developing/headful-headless.md) an, um die verschiedenen Ebenen SPA Integration zu verstehen.

### Tools {#tools}

* Sandbox-Zugriff zum Testen der Bereitstellung Ihres Projekts
* Lokale Entwicklungsinstanz für Datenmodellierung und -tests
* Vorhandene externe SPA (optional, je nach ausgewähltem Integrationsmodell)
* AEM-Projektarchetyp

## Was ist eine SPA? {#what-is-a-spa}

Eine Single Page Application (SPA) unterscheidet sich von einer herkömmlichen Seite insofern, als sie Client-seitig gerendert wird und primär JavaScript-gesteuert ist. Dabei wird auf Ajax-Aufrufe zurückgegriffen, um Daten zu laden und die Seite dynamisch zu aktualisieren. Der Großteil der Inhalte oder alle Inhalte werden einmal in einem einzelnen Seiten-Load abgerufen, wobei je nach Benutzerinteraktion mit der Seite asynchron zusätzliche Ressourcen geladen werden.

So wird der Bedarf nach Seitenaktualisierungen reduziert und dem Benutzer ein Erlebnis präsentiert, das nahtlos und schnell ist und eher wie eine native App funktioniert.

Der AEM-SPA-Editor ermöglicht es Frontend-Entwicklern, SPAs zu erstellen, die sich in eine AEM-Site integrieren lassen, damit Inhaltsautoren SPA-Inhalte so einfach bearbeiten können wie andere AEM-Inhalte.

## Warum eine SPA? {#why-spa}

Da SPAs schneller, nahtloser und eher wie ein natives Programm sind, sind sie nicht nur für Besucher der Web-Seite, sondern auch für Marketing-Experten und Entwickler attraktiv. Das hängt mit der Art und Weise zusammen, wie SPAs funktionieren.

Eine vollständige Beschreibung der SPA und deren Verwendung finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) , wo Sie Links zu einer ausführlicheren Dokumentation finden.

## Umgang AEM mit SPA

Bei der Entwicklung von Single Page Applications in AEM wird davon ausgegangen, dass sich der Frontend-Entwickler beim Erstellen einer SPA an die üblichen Best Practices hält. Wenn Sie als Frontend-Entwickler diese allgemeinen Best Practices sowie einige AEM-spezifische Prinzipien befolgen, wird Ihre SPA mit AEM und seinen Inhaltsverfassungsfunktionen zusammenarbeiten.

* **Portabilität**  - Wie bei allen Komponenten sollten die SPA so portabel wie möglich gestaltet werden. Die SPA sollte aus portablen und wiederverwendbaren Komponenten bestehen.
* **AEM verwaltet die Site-Struktur**: Der Frontend-Entwickler erstellt Komponenten und ist für deren interne Struktur verantwortlich, verlässt sich bei der Definition der Inhaltsstruktur der Site jedoch auf AEM.
* **Dynamisches Rendering**: Alle Rendering-Vorgänge sollten dynamisch sein.
* **Dynamisches Routing**: Die SPA ist für das Routing verantwortlich; AEM lauscht darauf und ruft Inhalte auf dieser Basis ab. Jegliches Routing sollte ebenfalls dynamisch sein.

Eine vollständige Beschreibung der Verarbeitung von SPA durch AEM finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) für Links zu ausführlicheren Dokumentationen.

## Der AEM SPA-Editor {#aem-spa-editor}

Sites, die mit gängigen SPA-Frameworks wie React und Angular erstellt wurden, laden ihren Inhalt über dynamisches JSON und weisen nicht die HTML-Struktur auf, die für den Seiteneditor von AEM erforderlich ist, um Steuerelemente zur Bearbeitung platzieren zu können.

Um die Bearbeitung von SPAs innerhalb von AEM zu ermöglichen, ist eine Zuordnung zwischen der JSON-Ausgabe der SPA und dem Inhaltsmodell im AEM-Repository erforderlich, damit Änderungen am Inhalt gespeichert werden können.

Mit der SPA-Unterstützung wird in AEM ein JS-Thin Layer eingeführt. Dieses interagiert mit dem SPA-JS-Code, wenn es in den Seiten-Editor geladen wird, mit dem Ereignisse gesendet und der Speicherort für die Steuerelemente zur Bearbeitung aktiviert werden kann, um eine kontextbezogene Bearbeitung zu ermöglichen. Diese Funktion baut auf dem Content Services API Endpoint-Konzept auf, da die Inhalte aus der SPA über Content Services geladen werden müssen.

Eine vollständige Beschreibung des AEM-SPA-Editors finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) für Links zu ausführlicheren Dokumentationen.

## Unterbringen bestehender SPA {#existing-spas}

Wenn Sie über eine vorhandene SPA verfügen, unterstützt AEM das Einbetten in AEM, damit diese für Ihre Inhaltsautoren im AEM Editor sichtbar ist. Dies kann sehr nützlich sein, um die Inhalte anzuzeigen, die über Inhaltsfragmente im Kontext der Endanwendung erstellt werden, in der sie verwendet werden.

Darüber hinaus können Sie mit nur kleinen Änderungen bestimmte Bearbeitungsmöglichkeiten für die externe SPA im AEM-Editor aktivieren.

Die RemotePage-Komponente ermöglicht die Wiedergabe eines externen SPA in AEM.

Eine vollständige Beschreibung, wie Sie eine externe SPA in AEM bearbeiten können, finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) für Links zu ausführlicheren Dokumentationen.

## Wie geht es weiter {#what-is-next}

Lesen Sie die folgenden Dokumente, um mit der Entwicklung Ihrer eigenen SPA für AEM zu beginnen:

* [SPA-WKND-Tutorial](/help/implementing/developing/hybrid/wknd-tutorial.md)
* [Erste Schritte mit React](/help/implementing/developing/hybrid/getting-started-react.md)
* [Erste Schritte mit Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Wenn Sie eine vorhandene SPA anpassen müssen, um sie in AEM zu verwenden, lesen Sie die folgenden Dokumente:

* [Die RemotePage-Komponente](/help/implementing/developing/hybrid/remote-page.md)
* [Bearbeiten einer externen SPA in AEM](/help/implementing/developing/hybrid/editing-external-spa.md)

Unten finden Sie [zusätzliche Ressourcen](#additional-resources), die Sie tiefer in SPA Themen in AEM bringen können.

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie einige zusätzliche Ressourcen, die einen tieferen Einblick in einige in diesem Dokument erwähnte Konzepte ermöglichen.

* [Headful und Headless in AEM](/help/implementing/developing/headful-headless.md)  - Eine Beschreibung der verschiedenen in AEM verfügbaren Versandmodelle
* [SPA-Einführung und exemplarische Vorgehensweise.](/help/implementing/developing/hybrid/introduction.md) - Eine gute Einführung in SPA in AEM
* [Entwicklung von SPA für AEM](/help/implementing/developing/hybrid/developing.md)  - Leitlinien für die Entwicklung von SPA für AEM
* [SPA Editor - Übersicht](/help/implementing/developing/hybrid/editor-overview.md)  - Details zur Funktionsweise des SPA-Editors
* [Server-seitiges Rendering](/help/implementing/developing/hybrid/ssr.md)  - So konfigurieren Sie SSR für AEM SPA
* [SPA Referenzdokumente](/help/implementing/developing/hybrid/reference-materials.md)  - JavaScript-API-Referenzen und -Links zu den Open-Source-AEM SPA GitHub-Projekten
* [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md)  - Erstellen von Inhaltsfragmenten
* [AEM Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)  - Maven-Vorlage, die ein minimales, auf Best Practices basierendes Adobe Experience Manager-Projekt (AEM) als Ausgangspunkt für Ihre Website erstellt
