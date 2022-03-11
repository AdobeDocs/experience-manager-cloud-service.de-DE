---
title: Authoring – Konzepte
description: Konzepte der Bearbeitung (Authoring) in AEM
exl-id: ee9e4952-e075-4398-b31f-d7886153efff
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 100%

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
>Ihr Konto muss über die entsprechenden Zugriffsrechte verfügen, um Inhalt erstellen, bearbeiten oder veröffentlichen zu können.

Je nachdem, wie die jeweilige Instanz und die entsprechenden Benutzerrechte konfiguriert sind, können Autoren für Inhalte unter anderem die folgenden Aufgaben durchführen:

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

## Veröffentlichungsumgebung {#publish-environment}

Wenn die Inhalte Ihrer Site fertig sind, werden sie in der **Veröffentlichungsumgebung** veröffentlicht. Hier werden die Seiten der Website in Übereinstimmung mit dem Aussehen der entworfenen Oberfläche der vorgesehenen Zielgruppe bereitgestellt.

Weitere Informationen zum Veröffentlichen und Rückgängigmachen der Veröffentlichung von Seiten finden Sie im Dokument zum [Veröffentlichen von Seiten](/help/sites-cloud/authoring/fundamentals/publishing-pages.md).

## Dispatcher {#dispatcher}

Um eine optimale Nutzung der Website durch Ihre Besucher zu gewährleisten, führt der **[Dispatcher](/help/implementing/dispatcher/overview.md)** Lastverteilung und Caching durch.
