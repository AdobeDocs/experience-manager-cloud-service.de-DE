---
title: Authoring – Konzepte
description: Konzepte der Bearbeitung (Authoring) in AEM
exl-id: ee9e4952-e075-4398-b31f-d7886153efff
source-git-commit: b407765438086bb2f7fb720fb7f1dd05699cb48f
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 81%

---

# Authoring – Konzepte {#authoring-concepts}

Eine AEM-Installation besteht im Allgemeinen aus mindestens zwei Umgebungen:

* Autor
* Veröffentlichung

Diese interagieren miteinander und bieten Ihnen die Möglichkeit, Inhalt auf Ihrer Website verfügbar zu machen, sodass Ihre Besucher darauf zuzugreifen können.

Die Autorenumgebung bietet die Mechanismen zum Erstellen, Aktualisieren und Überprüfen dieses Inhalts, bevor er tatsächlich veröffentlicht wird.

* Ein Autor erstellt und prüft den Inhalt. Der Inhalt kann viele verschiedene Inhaltstypen umfassen, beispielsweise Seiten, Assets und Veröffentlichungen.
* Dieser Inhalt wird zu einem späteren Zeitpunkt auf Ihrer Website veröffentlicht.

![Abbildung von Autor, Publisher und Dispatchern](/help/sites-cloud/authoring/assets/author-publish.png)

In der Autorenumgebung werden die Funktionen von AEM über die Autorenbenutzeroberfläche von AEM bereitgestellt. In der Veröffentlichungsumgebung entwerfen Sie das Aussehen der Oberfläche, die Sie Ihren Benutzern zur Verfügung stellen.

## Autorenumgebung {#author-environment}

Der Autor arbeitet in der sogenannten **Autorenumgebung**. Diese bietet eine einfach zu verwendende Oberfläche (grafische Benutzeroberfläche (GUI oder UI)) zum Erstellen von Inhalt. Der Autor muss sich mit einem Konto anmelden, dem die entsprechenden Zugriffsrechte zugewiesen wurden.

>[!NOTE]
>
>Ihr Konto muss über die entsprechenden Zugriffsrechte verfügen, um Inhalte zu erstellen, zu bearbeiten oder zu veröffentlichen.

Je nachdem, wie Ihre Instanz und Ihre persönlichen Zugriffsrechte konfiguriert sind, können Sie viele Aufgaben an Ihrem Inhalt ausführen, darunter (unter anderem):

* Erstellen neuer Inhalte oder Bearbeiten vorhandener Inhalte auf einer Seite
* Verwenden vordefinierter Vorlagen zum Erstellen neuer Inhaltsseiten
* Erstellen, Bearbeiten und Verwalten Ihrer Assets und Sammlungen
* Verschieben, Kopieren und Löschen von Inhaltsseiten, Assets usw.
* Veröffentlichen (oder Aufheben der Veröffentlichung) von Seiten, Assets usw.

Außerdem gibt es administrative Aufgaben, die Sie beim Verwalten des Inhalts unterstützen:

* Workflows für die Verwaltung von Änderungen, beispielsweise das Anfordern einer Prüfung vor der Veröffentlichung
* Projekte zur Koordinierung einzelner Aufgaben

>[!NOTE]
>
>AEM wird ebenfalls über die Autorenumgebung verwaltet.

## Vorschau von Inhalten {#previewing-content}

AEM bietet außerdem einen Sites-Vorschaudienst, mit dem Entwickler und Inhaltsautoren eine Vorschau des finalen Erlebnisses einer Website anzeigen können, bevor diese in die Veröffentlichungsumgebung gelangt und öffentlich verfügbar ist.

Siehe [Vorschau des Inhalts](/help/sites-cloud/authoring/fundamentals/previewing-content.md) für weitere Informationen.

## Veröffentlichungsumgebung {#publish-environment}

Wenn die Inhalte Ihrer Site fertig sind, werden sie in der **Veröffentlichungsumgebung** veröffentlicht. Hier werden die Seiten der Website in Übereinstimmung mit dem Aussehen der entworfenen Oberfläche der vorgesehenen Zielgruppe bereitgestellt.

Weitere Informationen zum Veröffentlichen und Rückgängigmachen der Veröffentlichung von Seiten finden Sie im Dokument zum [Veröffentlichen von Seiten](/help/sites-cloud/authoring/fundamentals/publishing-pages.md).

## Dispatcher {#dispatcher}

Um eine optimale Nutzung der Website durch Ihre Besucher zu gewährleisten, führt der **[Dispatcher](/help/implementing/dispatcher/overview.md)** Lastverteilung und Caching durch.
