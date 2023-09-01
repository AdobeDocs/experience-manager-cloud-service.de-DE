---
title: Optional - Erstellen von Einzelseiten-Apps (SPA) mit Adobe Experience Manager (AEM)
description: In dieser optionalen Fortsetzung der AEM Headless-Entwickler-Tour erfahren Sie, wie AEM Headless-Bereitstellungen mit herkömmlichen Full-Stack-CMS-Funktionen kombinieren kann und wie Sie mit dem SPA-Editor-Framework von AEM bearbeitbare SPAs erstellen können.
exl-id: d74848f2-683e-49e1-9374-32596ca5d7d7
source-git-commit: 7d09cafc4f8518fee185d3f9efc76c33ec20f9a3
workflow-type: tm+mt
source-wordcount: '1266'
ht-degree: 48%

---

# Erstellen von Single Page Applications (SPAs) mit AEM {#create-spa}

In dieser fakultativen Fortsetzung der [AEM Headless-Entwickler-Journey](overview.md)Erfahren Sie, wie AEM Headless-Bereitstellung mit herkömmlichen Full-Stack-CMS-Funktionen kombinieren kann. Außerdem erfahren Sie, wie Sie bearbeitbare SPA mit AEM Editor-Framework erstellen und externe SPA integrieren können, um Bearbeitungsfunktionen nach Bedarf zu ermöglichen.

## Die bisherige Entwicklung {#story-so-far}

An dieser Stelle sollten Sie die gesamte [AEM Headless-Entwickler-Tour](overview.md) abgeschlossen haben und die Grundlagen der Headless-Bereitstellung in AEM verstehen, einschließlich folgender Punkte:

* Unterschied zwischen Headless- und Headful-Inhaltsbereitstellung
* AEM Headless-Funktionen
* Organisieren eines AEM-Headless-Projekts
* Erstellen von Headless-Inhalten in AEM
* Abrufen und Aktualisieren von Headless-Inhalten in AEM
* Live-Schaltung mit einem AEM Headless-Projekt

Bisher sind Sie entweder mit Ihrem ersten AEM Headless-Projekt live gegangen oder verfügen über das entsprechende Wissen. Herzlichen Glückwunsch!

Warum lesen Sie also diese zusätzliche, optionale Fortsetzung der Journey? Sie erinnern sich daran in der [Erste Schritte](getting-started.md#integration-levels), wurde besprochen, wie AEM nicht nur Headless-Bereitstellung und traditionelle Full-Stack-Modelle unterstützt, sondern auch Hybridmodelle unterstützt, die die Vorteile beider Modelle kombinieren. Obwohl es sich hierbei nicht um das traditionelle Headless-Modell handelt, können derartige Hybridmodelle für bestimmten Projekte eine beispiellose Flexibilität bieten.

Dieser Artikel baut auf Ihren Kenntnissen von AEM Headless auf, indem Sie eingehend untersuchen, wie Sie Ihre eigenen Single-Page-Anwendungen (SPA) erstellen können, die in AEM bearbeitbar sind. Auf diese Weise können Sie Inhalte erstellen und direkt an einen SPA senden, dieser SPA bleibt jedoch in AEM bearbeitbar.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Single Page Applications mithilfe des AEM SPA Editor-Frameworks entwickelt werden. Nach dem Lesen dieses Dokuments sollten Sie Folgendes können:

* Verständnis der grundlegenden Funktion des SPA-Editors
* Kenntnis der Anforderungen zum Erstellen vollständig bearbeitbarer SPAs für AEM
* Kenntnis darüber, wie externe SPAs in AEM integriert werden können
* Erfahren Sie, wie serverseitiges Rendering implementiert werden kann oder nicht.

## Anforderungen und Vorbedingungen {#requirements-prerequisites}

Es gibt mehrere Anforderungen, bevor Sie mit der Arbeit mit SPA in AEM beginnen.

### Kenntnisse {#knowledge}

* Entwicklungserlebnis beim Erstellen von SPA mit React- oder Angular-Frameworks
* Grundlegende AEM-Kenntnisse zum Erstellen von Inhaltsfragmenten und Verwenden des Editors
* Überprüfen Sie unbedingt das Dokument. [Headless und Headless in AEM](/help/implementing/developing/headful-headless.md) damit Sie die verschiedenen Ebenen SPA Integration verstehen können.

### Tools {#tools}

* Sandbox-Zugriff zum Testen der Bereitstellung Ihres Projekts
* Lokale Entwicklungsinstanz für Datenmodellierung und -tests
* Vorhandene externe SPA (optional, je nach ausgewähltem Integrationsmodell)
* AEM-Projektarchetyp

## Was ist eine SPA? {#what-is-a-spa}

Eine Einzelseitenanwendung (SPA) unterscheidet sich von einer herkömmlichen Seite insofern, als sie Client-seitig gerendert wird und primär JavaScript-gesteuert ist. Dabei wird auf Ajax-Aufrufe zurückgegriffen, um Daten zu laden und die Seite dynamisch zu aktualisieren. Die meisten oder alle Inhalte werden einmal in einem einzelnen Seitenladevorgang abgerufen, wobei je nach Benutzerinteraktion mit der Seite asynchron zusätzliche Ressourcen geladen werden.

Diese Funktion reduziert den Bedarf an Seitenaktualisierungen und stellt dem Benutzer ein Erlebnis bereit, das nahtlos, schnell und eher wie ein natives App-Erlebnis ist.

Der AEM-SPA-Editor ermöglicht es Frontend-Entwicklern, SPAs zu erstellen, die sich in eine AEM-Site integrieren lassen, damit Inhaltsautoren SPA-Inhalte so einfach bearbeiten können wie andere AEM-Inhalte.

## Warum eine SPA? {#why-spa}

Da eine SPA schneller, flüssiger und eher wie eine native Anwendung ist, wird sie zu einem attraktiven Erlebnis. Es ist nicht nur für den Besucher der Webseite, sondern auch für Marketing-Experten und Entwickler aufgrund der Art und Weise, wie SPA funktionieren, gut.

Eine vollständige Beschreibung von SPAs sowie Gründe für ihre Verwendung finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Wie AEM SPAs verarbeitet

Bei der Entwicklung von Single Page Applications in AEM wird davon ausgegangen, dass sich der Frontend-Entwickler beim Erstellen einer SPA an die üblichen Best Practices hält. Wenn Sie als Frontend-Entwickler diese allgemeinen Best Practices und einige AEM-spezifische Prinzipien befolgen, wird Ihre SPA mit AEM und den Inhaltsbearbeitungsfunktionen funktionieren.

* **Portabilität**: Wie alle anderen Komponenten auch sollten die SPA-Komponenten so portabel wie möglich gestaltet werden. Die SPA sollte aus portablen und wiederverwendbaren Komponenten bestehen.
* **AEM verwaltet die Site-Struktur** - Der Frontend-Entwickler erstellt Komponenten und ist für ihre interne Struktur verantwortlich, verlässt sich jedoch bei der Definition der Inhaltsstruktur der Site auf AEM.
* **Dynamisches Rendering**: Alle Rendering-Vorgänge sollten dynamisch sein.
* **Dynamisches Routing**: Die SPA ist für das Routing verantwortlich; AEM lauscht darauf und ruft Inhalte auf dieser Basis ab. Jegliches Routing sollte ebenfalls dynamisch sein.

Eine vollständige Beschreibung, wie AEM SPAs verarbeitet, finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Der SPA-Editor von AEM {#aem-spa-editor}

Sites, die mit gängigen SPA-Frameworks wie React und Angular erstellt wurden, laden ihren Inhalt über dynamische JSON. Sie bieten nicht die HTML-Struktur, die erforderlich ist, damit der AEM Seiteneditor Bearbeitungssteuerelemente platzieren kann.

Um die Bearbeitung von SPA in AEM zu aktivieren, ist eine Zuordnung zwischen der JSON-Ausgabe des SPA und dem Inhaltsmodell im AEM Repository erforderlich, damit Sie Änderungen am Inhalt speichern können.

SPA Unterstützung in AEM führt eine dünne JavaScript-Ebene ein, die mit dem SPA JavaScript-Code interagiert, wenn diese im Seiteneditor geladen wird und mit denen Ereignisse gesendet werden können. Der Speicherort für die Bearbeitungssteuerelemente kann aktiviert werden, um eine kontextbezogene Bearbeitung zu ermöglichen. Diese Funktion baut auf dem Content Services API-Endpoint-Konzept auf, da der Inhalt aus dem SPA über Content Services geladen werden muss.

Eine vollständige Beschreibung des AEM-SPA-Editors finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Berücksichtigung vorhandener SPAs {#existing-spas}

Wenn Sie über eine vorhandene SPA verfügen, unterstützt AEM das Einbetten in AEM, damit diese für Ihre Inhaltsautoren im AEM Editor sichtbar ist. Mit dieser Funktion können Sie den Inhalt, den sie erstellen, mithilfe von Inhaltsfragmenten im Kontext der Endanwendung anzeigen, in der sie verwendet wird.

Außerdem können Sie mit nur kleinen Änderungen bestimmte Bearbeitungen für die externe SPA im AEM Editor aktivieren.

Die RemotePage-Komponente ermöglicht das Rendern externer SPAs in AEM.

Eine vollständige Beschreibung dazu, wie sich externe SPAs in AEM bearbeiten lassen, finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Wie geht es weiter {#what-is-next}

Lesen Sie die folgenden Dokumente, um mit der Entwicklung Ihrer eigenen SPAs für AEM zu beginnen:

* [SPA-WKND-Tutorial](/help/implementing/developing/hybrid/wknd-tutorial.md)
* [Erste Schritte mit React](/help/implementing/developing/hybrid/getting-started-react.md)
* [Erste Schritte mit Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Wenn Sie eine vorhandene SPA anpassen müssen, um sie in AEM zu verwenden, lesen Sie die folgenden Dokumente:

* [Die RemotePage-Komponente](/help/implementing/developing/hybrid/remote-page.md)
* [Bearbeiten einer externen SPA in AEM](/help/implementing/developing/hybrid/editing-external-spa.md)

Nachfolgend finden Sie [zusätzliche Ressourcen](#additional-resources) mit weiterführenden Informationen zu SPA-Themen in AEM.

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie einige zusätzliche Ressourcen, die näher auf einige der in diesem Dokument erwähnten Konzepte eingehen.

* [Headful und Headless in AEM](/help/implementing/developing/headful-headless.md) – eine Beschreibung der verschiedenen in AEM verfügbaren Bereitstellungsmodelle
* [SPA Einführung und exemplarische Vorgehensweise](/help/implementing/developing/hybrid/introduction.md) - Eine gute Einführung in SPA in AEM.
* [Entwickeln von SPAs für AEM](/help/implementing/developing/hybrid/developing.md) – Orientierungshilfe für die Entwicklung von SPAs für AEM
* [SPA-Editor – Überblick](/help/implementing/developing/hybrid/editor-overview.md) – Details zur Funktionsweise des SPA-Editors
* [Serverseitiges Rendering](/help/implementing/developing/hybrid/ssr.md) - So konfigurieren Sie SSR für AEM SPA
* [SPA](/help/implementing/developing/hybrid/reference-materials.md) - JavaScript-API-Referenzen und -Links zu den Open-Source-AEM SPA GitHub-Projekten
* [Arbeiten mit Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments) –Anleitung zur Erstellung von Inhaltsfragmenten
* Der [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) ist eine Maven-Vorlage, anhand derer ein minimales, auf Best Practices basierendes Adobe Experience Manager (AEM)-Projekt als Ausgangspunkt für Ihre Website erstellt wird.
