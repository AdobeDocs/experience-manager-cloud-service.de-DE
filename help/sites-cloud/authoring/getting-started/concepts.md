---
title: Authoring-Konzepte
description: Erfahren Sie mehr über die Konzepte zum Authoring in AEM mit Autoren-, Vorschau- und Veröffentlichungsumgebungen.
exl-id: ee9e4952-e075-4398-b31f-d7886153efff
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: ht
source-wordcount: '394'
ht-degree: 100%

---


# Authoring-Konzepte {#authoring-concepts}

Eine AEM-Installation besteht im Allgemeinen aus mindestens zwei Umgebungen:

* Autor
* Veröffentlichung

Diese Umgebungen interagieren miteinander und bieten Ihnen die Möglichkeit, Inhalte auf Ihrer Website verfügbar zu machen, sodass Ihre Besucherinnen und Besucher darauf zuzugreifen können.

Die Autorenumgebung bietet die Mechanismen zum Erstellen, Aktualisieren und Überprüfen dieses Inhalts, bevor er tatsächlich veröffentlicht wird.

* Ein Autor erstellt und prüft den Inhalt. Der Inhalt kann viele verschiedene Arten aufweisen, darunter Seiten, Assets und Veröffentlichungen.
* Dieser Inhalt wird zu einem späteren Zeitpunkt auf Ihrer Website veröffentlicht.

![Abbildung von Autor, Publisher und Dispatchern](/help/sites-cloud/authoring/assets/author-publish.png)

In der Authoring-Umgebung wird die Funktionalität von AEM über die Benutzeroberfläche von AEM zur Verfügung gestellt. In der Publishing-Umgebung entwerfen Sie das Aussehen der Oberfläche, die Sie Ihren Benutzenden zur Verfügung stellen.

{{edge-delivery-authoring}}

## Authoring-Umgebung {#author-environment}

Die Autorin bzw. der Autor arbeitet in der sogenannten **Authoring-Umgebung**. Diese Umgebung bietet eine benutzerfreundliche Benutzeroberfläche (grafische Benutzeroberfläche (GUI oder UI)) zum Erstellen des Inhalts. Die Autorin bzw. der Autor muss sich mit einem Konto anmelden, dem die entsprechenden Zugriffsrechte zugewiesen wurden.

>[!NOTE]
>
>Ihr Konto muss über die entsprechenden Zugriffsrechte verfügen, um Inhalte zu erstellen, zu bearbeiten oder zu veröffentlichen.

Je nachdem, wie Ihre Instanz und Ihre persönlichen Zugriffsrechte konfiguriert sind, können Sie viele Aufgaben in Bezug auf Ihre Inhalte durchführen, unter anderem:

* Erstellen neuer Inhalte oder Bearbeiten vorhandener Inhalte auf einer Seite
* Verwenden vordefinierter Vorlagen zum Erstellen von Inhaltsseiten
* Erstellen, Bearbeiten und Verwalten Ihrer Assets und Sammlungen
* Verschieben, Kopieren und Löschen von Inhaltsseiten und Assets.
* Veröffentlichen (oder Rückgängigmachen der Veröffentlichung) von Seiten und Assets.

Außerdem gibt es administrative Aufgaben, die Sie beim Verwalten des Inhalts unterstützen:

* Workflows für die Verwaltung von Änderungen, beispielsweise das Anfordern einer Prüfung vor der Veröffentlichung
* Projekte zur Koordinierung einzelner Aufgaben

>[!NOTE]
>
>AEM wird ebenfalls über die Autorenumgebung verwaltet.

## Vorschau von Inhalten {#previewing-content}

AEM bietet den Sites-Vorschau-Service, der Entwicklungspersonen und Inhaltsautorinnen bzw -autoren die Vorschau des endgültigen Erlebnisses einer Website ermöglicht, bevor diese in die Publishing-Umgebung gelangt und öffentlich verfügbar ist.

Siehe [Vorschau von Inhalten](/help/sites-cloud/authoring/fundamentals/previewing-content.md) für weitere Informationen.

## Publishing-Umgebung {#publish-environment}

Wenn die Inhalte Ihrer Site fertig sind, werden sie in der **Veröffentlichungsumgebung** veröffentlicht. Hier werden die Seiten der Website in Übereinstimmung mit dem Aussehen der entworfenen Oberfläche der vorgesehenen Zielgruppe bereitgestellt.

Weitere Informationen zum Veröffentlichen und zum Rückgängigmachen der Veröffentlichung von Seiten finden Sie im Dokument zum [Veröffentlichen von Seiten](/help/sites-cloud/authoring/fundamentals/publishing-pages.md).

## Dispatcher {#dispatcher}

Um eine optimale Nutzung der Website durch Ihre Besucherinnen und Besucher zu gewährleisten, führt der **[Dispatcher](/help/implementing/dispatcher/overview.md)** Lastverteilung und Caching durch.
