---
title: Optional – Erstellen von Single Page Applications (SPAs) mit Adobe Experience Manager (AEM)
description: In dieser optionalen Fortsetzung der AEM Headless-Entwickler-Tour erfahren Sie, wie AEM Headless-Bereitstellungen mit herkömmlichen Full-Stack-CMS-Funktionen kombinieren kann und wie Sie mit dem SPA-Editor-Framework von AEM bearbeitbare SPAs erstellen können.
exl-id: d74848f2-683e-49e1-9374-32596ca5d7d7
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 100%

---

# Erstellen von Single Page Applications (SPAs) mit AEM {#create-spa}

In dieser optionalen Fortsetzung der [AEM Headless-Entwickler-Tour](overview.md) erfahren Sie, wie AEM die Headless-Bereitstellung mit herkömmlichen Full-Stack-CMS-Funktionen kombinieren kann. Außerdem erfahren Sie, wie Sie bearbeitbare SPAs mit dem SPA-Editor-Framework von AEM erstellen und externe SPAs integrieren können, um Bearbeitungsfunktionen nach Bedarf zu aktivieren.

## Die bisherige Entwicklung {#story-so-far}

An dieser Stelle sollten Sie die gesamte [AEM Headless-Entwickler-Tour](overview.md) abgeschlossen haben und die Grundlagen der Headless-Bereitstellung in AEM verstehen, einschließlich folgender Punkte:

* Unterschied zwischen Headless- und Headful-Inhaltsbereitstellung
* AEM Headless-Funktionen
* Organisieren eines AEM-Headless-Projekts
* Erstellen von Headless-Inhalten in AEM
* Abrufen und Aktualisieren von Headless-Inhalten in AEM
* Live-Schaltung mit einem AEM Headless-Projekt

Bisher sind Sie entweder mit Ihrem ersten AEM Headless-Projekt live gegangen oder verfügen zumindest über das entsprechende Wissen. Herzlichen Glückwunsch!

Warum lesen Sie also diese optionale Fortsetzung der Tour? Sie erinnern sich daran, dass wir in den [ersten Schritten](getting-started.md#integration-levels) besprochen haben, inwiefern AEM nicht nur die Headless-Bereitstellung und herkömmliche Full-Stack-Modelle unterstützt, sondern auch Hybridmodelle, die die Vorteile beider Welten kombinieren. Obwohl es sich hierbei nicht um das traditionelle Headless-Modell handelt, können derartige Hybridmodelle für bestimmten Projekte eine beispiellose Flexibilität bieten.

Dieser Artikel baut auf Ihren Kenntnissen über AEM Headless auf und erläutert eingehend, wie Sie Ihre eigenen SPAs (Single Page Applications) erstellen können, die in AEM bearbeitbar sind. Auf diese Weise können Sie Inhalte erstellen und „headless“ für eine SPA bereitstellen, wobei diese SPA gleichzeitig in AEM bearbeitbar bleibt.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Single Page Applications mithilfe des AEM SPA Editor-Frameworks entwickelt werden. Nach dem Lesen dieses Dokuments sollten Sie Folgendes können:

* Verständnis der grundlegenden Funktion des SPA-Editors
* Kenntnis der Anforderungen zum Erstellen vollständig bearbeitbarer SPAs für AEM
* Kenntnis darüber, wie externe SPAs in AEM integriert werden können
* Kenntnis darüber, wie Server-seitiges Rendering implementiert werden kann oder nicht.

## Anforderungen und Vorbedingungen {#requirements-prerequisites}

Bevor Sie in AEM mit SPAs arbeiten, müssen Sie einige Anforderungen erfüllen.

### Kenntnisse {#knowledge}

* Entwicklungserlebnis beim Erstellen von SPA mit React- oder Angular-Frameworks
* Grundlegende AEM-Kenntnisse zum Erstellen von Inhaltsfragmenten und Verwenden des Editors
* Lesen Sie das Dokument [Headful und Headless in AEM](/help/implementing/developing/headful-headless.md), um die verschiedenen möglichen Ebenen der SPA-Integration zu verstehen.

### Tools {#tools}

* Sandbox-Zugriff zum Testen der Bereitstellung Ihres Projekts
* Lokale Entwicklungsinstanz für Datenmodellierung und -tests
* Vorhandene externe SPA (optional, je nach ausgewähltem Integrationsmodell)
* AEM-Projektarchetyp

## Was ist eine SPA? {#what-is-a-spa}

Eine Single Page Application (SPA) unterscheidet sich von einer herkömmlichen Seite insofern, als sie Client-seitig gerendert wird und primär JavaScript-gesteuert ist. Dabei wird auf Ajax-Aufrufe zurückgegriffen, um Daten zu laden und die Seite dynamisch zu aktualisieren. Der Großteil der Inhalte (oder alle) werden einmalig beim Laden einer einzelnen Seite abgerufen, wobei je nach Benutzerinteraktion mit der Seite asynchron zusätzliche Ressourcen geladen werden.

Durch diese Funktionalität wird der Bedarf an Seitenaktualisierungen reduziert und den Benutzenden ein Erlebnis präsentiert, das nahtlos und schnell ist und ihnen eher wie eine native App vorkommt.

Der AEM-SPA-Editor ermöglicht es Frontend-Entwicklungspersonen, SPAs zu erstellen, die sich in eine AEM-Site integrieren lassen, damit Inhaltsautorinnen und -autoren SPA-Inhalte so einfach bearbeiten können wie alle anderen AEM-Inhalte.

## Warum eine SPA? {#why-spa}

Da eine SPA schneller, flüssiger und eher wie eine native Anwendung ist, wird sie zu einem ansprechenden Erlebnis. Aufgrund der Art und Weise, wie SPAs funktionieren, ist dies nicht nur gut für Menschen, die die Web-Seite besuchen, sondern auch für Marketing-Fachleute sowie Entwicklerinnen und Entwickler.

Eine vollständige Beschreibung von SPAs sowie Gründe für ihre Verwendung finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Wie AEM SPAs verarbeitet

Bei der Entwicklung von Single Page Applications in AEM wird davon ausgegangen, dass sich der Frontend-Entwickler beim Erstellen einer SPA an die üblichen Best Practices hält. Wenn Sie als Frontend-Entwicklungsperson diese allgemeinen Best Practices und einige AEM-spezifische Prinzipien befolgen, wird Ihre SPA mit AEM und den Inhaltsbearbeitungsfunktionen funktionieren.

* **Portabilität**: Wie alle anderen Komponenten auch sollten die SPA-Komponenten so portabel wie möglich gestaltet werden. Die SPA sollte aus portablen und wiederverwendbaren Komponenten bestehen.
* **AEM verwaltet die Site-Struktur**: Die Frontend-Entwicklungsperson erstellt Komponenten und ist für deren interne Struktur verantwortlich, verlässt sich für die Definition der Inhaltsstruktur der Site jedoch auf AEM.
* **Dynamisches Rendering**: Alle Rendering-Vorgänge sollten dynamisch sein.
* **Dynamisches Routing**: Die SPA ist für das Routing verantwortlich; AEM lauscht darauf und ruft Inhalte auf dieser Basis ab. Jegliches Routing sollte ebenfalls dynamisch sein.

Eine vollständige Beschreibung, wie AEM SPAs verarbeitet, finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Der SPA-Editor von AEM {#aem-spa-editor}

Sites, die mit gängigen SPA-Frameworks wie React und Angular erstellt wurden, laden ihren Inhalt über dynamisches JSON. Sie bieten nicht die HTML-Struktur, die erforderlich ist, damit der AEM-Seiteneditor Bearbeitungssteuerelemente platzieren kann.

Um die Bearbeitung von SPA in AEM zu aktivieren, ist eine Zuordnung zwischen der JSON-Ausgabe des SPA und dem Inhaltsmodell im AEM-Repository erforderlich, damit Sie Änderungen am Inhalt speichern können.

Die SPA-Unterstützung in AEM führt eine dünne JavaScript-Ebene ein, die mit dem SPA-JavaScript-Code interagiert, wenn dieser in den Seiteneditor geladen wird, und mit der Ereignisse gesendet werden können. Der Speicherort für die Bearbeitungssteuerelemente kann aktiviert werden, um eine kontextbezogene Bearbeitung zu ermöglichen. Diese Funktion baut auf dem Konzept des Content Services API-Endpunkts auf, da der Inhalt aus der SPA über Content Services geladen werden muss.

Eine vollständige Beschreibung des AEM-SPA-Editors finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Berücksichtigung vorhandener SPAs {#existing-spas}

Wenn Sie bereits über eine SPA verfügen, unterstützt AEM das Einbetten in AEM, damit diese für Ihre Inhaltsautorinnen und -autoren im AEM-Editor sichtbar ist. Diese Fähigkeit kann sehr nützlich sein, um die Inhalte anzuzeigen, die über Inhaltsfragmente im Kontext der Anwendung erstellt werden, in dem sie letztendlich verwendet werden.

Darüber hinaus können Sie im AEM-Editor mit nur kleinen Änderungen bestimmte Bearbeitungsmöglichkeiten für die externe SPA aktivieren.

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
* [SPA-Einführung und exemplarische Anleitung](/help/implementing/developing/hybrid/introduction.md): Eine gute Einführung in SPA in AEM.
* [Entwickeln von SPAs für AEM](/help/implementing/developing/hybrid/developing.md) – Orientierungshilfe für die Entwicklung von SPAs für AEM
* [SPA-Editor – Überblick](/help/implementing/developing/hybrid/editor-overview.md) – Details zur Funktionsweise des SPA-Editors
* [SPA-Referenzdokumente](/help/implementing/developing/hybrid/reference-materials.md): JavaScript-API-Referenzen und Links zu den Open-Source-AEM-SPA-GitHub-Projekten
* [Arbeiten mit Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments) –Anleitung zur Erstellung von Inhaltsfragmenten
* Der [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) ist eine Maven-Vorlage, anhand derer ein minimales, auf Best Practices basierendes Adobe Experience Manager (AEM)-Projekt als Ausgangspunkt für Ihre Website erstellt wird.
