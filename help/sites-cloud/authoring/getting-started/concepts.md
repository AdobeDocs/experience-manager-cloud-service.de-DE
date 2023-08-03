---
title: Authoring – Konzepte
description: Erfahren Sie mehr über die Konzepte des Authoring in AEM mithilfe der Autoren-, Vorschau- und Veröffentlichungsumgebungen.
exl-id: ee9e4952-e075-4398-b31f-d7886153efff
source-git-commit: 31e6ec8e9977c8787e14481ee3a94df767262aec
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 40%

---

# Authoring – Konzepte {#authoring-concepts}

Eine AEM-Installation besteht im Allgemeinen aus mindestens zwei Umgebungen:

* Autor
* Veröffentlichung

Diese Umgebungen interagieren, damit Sie Inhalte auf Ihrer Website verfügbar machen können, damit Ihre Besucher darauf zugreifen können.

Die Autorenumgebung bietet die Mechanismen zum Erstellen, Aktualisieren und Überprüfen dieses Inhalts, bevor er tatsächlich veröffentlicht wird.

* Ein Autor erstellt und prüft den Inhalt. Der Inhalt kann viele verschiedene Arten aufweisen, darunter Seiten, Assets und Veröffentlichungen.
* Dieser Inhalt wird zu einem späteren Zeitpunkt auf Ihrer Website veröffentlicht.

![Abbildung von Autor, Publisher und Dispatchern](/help/sites-cloud/authoring/assets/author-publish.png)

In der Autorenumgebung wird die Funktionalität von AEM über AEM Authoring-Benutzeroberfläche bereitgestellt. In der Veröffentlichungsumgebung entwerfen Sie das gesamte Erscheinungsbild der Benutzeroberfläche, die Ihren Benutzern zur Verfügung gestellt wird.

## Authoring-Umgebung {#author-environment}

Der Autor arbeitet in dem so genannten **Autorenumgebung**. Diese Umgebung bietet eine benutzerfreundliche Benutzeroberfläche (grafische Benutzeroberfläche (GUI oder UI)) zum Erstellen des Inhalts. Der Autor muss sich mit einem Konto anmelden, dem die entsprechenden Zugriffsrechte zugewiesen sind.

>[!NOTE]
>
>Ihr Konto muss über die entsprechenden Zugriffsrechte verfügen, um Inhalte zu erstellen, zu bearbeiten oder zu veröffentlichen.

Je nachdem, wie Ihre Instanz und Ihre persönlichen Zugriffsrechte konfiguriert sind, können Sie viele Aufgaben an Ihrem Inhalt ausführen, darunter (unter anderem):

* Erstellen neuer Inhalte oder Bearbeiten vorhandener Inhalte auf einer Seite
* Verwenden vordefinierter Vorlagen zum Erstellen von Inhaltsseiten
* Erstellen, Bearbeiten und Verwalten Ihrer Assets und Sammlungen
* Verschieben, Kopieren und Löschen von Inhaltsseiten und Assets.
* Veröffentlichen (oder Rückgängigmachen der Veröffentlichung) von Seiten und Assets

Außerdem gibt es administrative Aufgaben, die Ihnen bei der Verwaltung Ihrer Inhalte helfen:

* Workflows für die Verwaltung von Änderungen, beispielsweise das Anfordern einer Prüfung vor der Veröffentlichung
* Projekte zur Koordinierung einzelner Aufgaben

>[!NOTE]
>
>AEM wird ebenfalls über die Autorenumgebung verwaltet.

## Vorschau von Inhalten {#previewing-content}

AEM bietet außerdem einen Sites-Vorschaudienst, mit dem Entwickler und Inhaltsautoren eine Vorschau des finalen Erlebnisses einer Website anzeigen können, bevor diese in die Veröffentlichungsumgebung gelangt und öffentlich verfügbar ist.

Siehe [Vorschau von Inhalten](/help/sites-cloud/authoring/fundamentals/previewing-content.md) für weitere Informationen.

## Publishing-Umgebung {#publish-environment}

Wenn die Inhalte Ihrer Site fertig sind, werden sie in der **Veröffentlichungsumgebung** veröffentlicht. Hier werden die Seiten der Website in Übereinstimmung mit dem Aussehen der entworfenen Oberfläche der vorgesehenen Zielgruppe bereitgestellt.

Weitere Informationen zum Veröffentlichen und Rückgängigmachen der Veröffentlichung von Seiten finden Sie im Dokument zum [Veröffentlichen von Seiten](/help/sites-cloud/authoring/fundamentals/publishing-pages.md).

## Dispatcher {#dispatcher}

Um die Leistung für Besucher Ihrer Website zu optimieren, muss die Variable **[Dispatcher](/help/implementing/dispatcher/overview.md)** implementiert Lastenausgleich und Caching.
