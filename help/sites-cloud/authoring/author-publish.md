---
title: Authoring und Publishing-Konzepte
description: Erfahren Sie mehr über die Konzepte des Authoring in AEM mithilfe der Autoren-, Vorschau- und Veröffentlichungsumgebungen.
exl-id: ee9e4952-e075-4398-b31f-d7886153efff
source-git-commit: bbd845079cb688dc3e62e2cf6b1a63c49a92f6b4
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 30%

---


# Authoring und Publishing-Konzepte {#authoring-publishing}

Für einen Inhaltsautor kann eine AEM as a Cloud Service Installation als drei primäre Ebenen auf der grundlegendsten Ebene betrachtet werden

* Autorenebene
* Vorschauebene
* AEM Veröffentlichungsebene

Diese Ebenen interagieren, damit Sie Inhalte auf Ihrer Website verfügbar machen können, damit Ihre Besucher darauf zugreifen können. Der grundlegende Workflow lautet:

1. Inhaltsautoren erstellen ihren Inhalt mit der Autorenstufe.
1. Inhaltsautoren stellen ihren Inhalt für Prüfer zur Verfügung, um sie mithilfe der Vorschauebene in der Vorschau anzuzeigen.
1. Sobald der Inhalt für den öffentlichen Gebrauch bereit ist, veröffentlichen Autoren den Inhalt mit der Veröffentlichungsstufe.

Der Inhalt kann viele verschiedene Arten aufweisen, darunter Seiten, Assets und Veröffentlichungen. Die Vorschau von Inhalten kann nach Ermessen des Autors übersprungen werden.

![Abbildung von Autor, Publisher und Dispatchern](assets/author-publish.jpg)

Weitere Informationen zur technischen Architektur von AEM as a Cloud Service finden Sie im Dokument [Eine Einführung in die Architektur von Adobe Experience Manager as a Cloud Service.](/help/overview/architecture.md)

{{edge-delivery-authoring}}

## Inhaltserstellung {#author-environment}

Die Authoring-Umgebung der Autorenstufe bietet eine einfach zu verwendende grafische Benutzeroberfläche zum Erstellen von Inhalten. Die Autorin bzw. der Autor muss sich mit einem Konto anmelden, dem die entsprechenden Zugriffsrechte zugewiesen wurden.

Je nachdem, wie Ihre Instanz und Ihre persönlichen Zugriffsrechte konfiguriert sind, können Sie viele Aufgaben in Bezug auf Ihre Inhalte durchführen, unter anderem:

* Erstellen neuer Inhalte oder Bearbeiten vorhandener Inhalte auf einer Seite
* Verwenden vordefinierter Vorlagen zum Erstellen von Inhaltsseiten
* Erstellen, Bearbeiten und Verwalten Ihrer Assets und Sammlungen
* Verschieben, Kopieren und Löschen von Inhaltsseiten und Assets.
* Veröffentlichen (oder Rückgängigmachen der Veröffentlichung) von Seiten und Assets.

Außerdem gibt es administrative Aufgaben, die Sie beim Verwalten des Inhalts unterstützen:

* Workflows für die Verwaltung von Änderungen, beispielsweise das Anfordern einer Prüfung vor der Veröffentlichung
* Projekte zur Koordinierung einzelner Aufgaben

AEM wird ebenfalls über die Autorenumgebung verwaltet.

Lesen Sie das Dokument . [Schnellstartanleitung zum Authoring](/help/sites-cloud/authoring/quick-start.md) für einen Überblick über den Authoring-Prozess.

## Vorschau von Inhalten {#previewing-content}

AEM bietet außerdem einen Vorschaudienst, mit dem Entwickler und Inhaltsautoren eine Vorschau des endgültigen Erlebnisses einer Website anzeigen können, bevor diese in die Veröffentlichungsumgebung gelangt und öffentlich verfügbar ist.

Lesen Sie das Dokument . [Vorschau des Inhalts](/help/sites-cloud/authoring/sites-console/previewing-content.md) für weitere Informationen.

## Publishing-Umgebung {#publish-environment}

Wenn die Inhalte Ihrer Site fertig sind, werden sie in der Veröffentlichungsumgebung der Veröffentlichungsstufe veröffentlicht. Hier werden die Seiten der Website entsprechend dem Erscheinungsbild Ihrer Inhaltsvorlage der vorgesehenen Zielgruppe zur Verfügung gestellt.

Lesen Sie das Dokument . [Veröffentlichen von Seiten](/help/sites-cloud/authoring/sites-console/publishing-pages.md) für weitere Informationen zum Veröffentlichen und Rückgängigmachen der Veröffentlichung von Seiten.

## Dispatcher {#dispatcher}

Um die Leistung für Besucher Ihrer Website zu optimieren, muss die Variable **[Dispatcher](/help/implementing/dispatcher/overview.md)** implementiert Lastenausgleich und Caching für die Veröffentlichungs- und Vorschauschicht.
