---
title: Authoring-Konzepte
description: Konzepte der Bearbeitung (Authoring) in AEM
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Bearbeiten Konzepte {#authoring-concepts}

Eine AEM-Installation besteht im Allgemeinen aus mindestens zwei Umgebungen:

* Autor
* Veröffentlichen

Diese interagieren, damit Sie Inhalte auf Ihrer Website verfügbar machen können, damit Ihre Besucher darauf zugreifen können.

Die Autorenumgebung bietet die Mechanismen zum Erstellen, Aktualisieren und Überprüfen dieses Inhalts, bevor er tatsächlich veröffentlicht wird:

* Ein Autor erstellt und prüft den Inhalt. Der Inhalt kann sich auf verschiedene Arten beziehen, z. B. auf Seiten, Assets, Veröffentlichungen usw.
* Diese Inhalte werden zu einem bestimmten Zeitpunkt auf Ihrer Website veröffentlicht.

![Diagramm mit Autoren, Herausgebern und Dispatchern](/help/sites-cloud/authoring/assets/author-publish.png)

In der Autorenumgebung wird die Funktionalität von AEM über die Authoring-Benutzeroberfläche von AEM bereitgestellt. In der Veröffentlichungsumgebung entwerfen Sie das Aussehen der Oberfläche, die Sie Ihren Benutzern zur Verfügung stellen.

>[!NOTE]
>
>AEM selbst wird zum Veröffentlichen der AEM-Dokumentation verwendet.

## Autorenumgebung {#author-environment}

Der Autor arbeitet in der so genannten **Autorenumgebung**. Dies bietet eine benutzerfreundliche Oberfläche (grafische Benutzeroberfläche (GUI oder UI)) zum Erstellen des Inhalts. Der Autor muss sich mit einem Konto anmelden, dem die entsprechenden Zugriffsrechte zugewiesen wurden.

>[!NOTE]
>
>Ihr Konto muss über die entsprechenden Zugriffsrechte verfügen, um Inhalt erstellen, bearbeiten oder veröffentlichen zu können.

Je nachdem, wie die jeweilige Instanz und die entsprechenden Benutzerrechte konfiguriert sind, können Autoren für Inhalte unter anderem die folgenden Aufgaben durchführen:

* Erstellen neuer Inhalte oder Bearbeiten vorhandener Inhalte auf einer Seite
* Erstellen neuer Inhaltsseiten mit vordefinierten Vorlagen
* Erstellen, Bearbeiten und Verwalten von Assets und Sammlungen
* Verschieben, Kopieren und Löschen von Inhaltsseiten, Assets usw.
* Veröffentlichen (oder Aufheben der Veröffentlichung) von Seiten, Assets usw.

Außerdem gibt es administrative Aufgaben, die Sie beim Verwalten des Inhalts unterstützen:

* Arbeitsabläufe, die steuern, wie Änderungen verwaltet werden, z. B. Erzwingen einer Überprüfung vor der Veröffentlichung
* Projekte zur Koordinierung einzelner Aufgaben

>[!NOTE]
>
>AEM wird auch aus der Autorenumgebung verwaltet.

## Veröffentlichungsumgebung {#publish-environment}

When ready, your site&#39;s content is published to the **publish environment**. Hier werden die Seiten der Website in Übereinstimmung mit dem Aussehen der entworfenen Oberfläche der vorgesehenen Zielgruppe bereitgestellt.

Weitere Informationen zum Veröffentlichen und Rückgängigmachen der Veröffentlichung von Seiten finden Sie im Dokument [Veröffentlichen von Seiten.](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)

## Dispatcher {#dispatcher}

To optimize performance for visitors to your website, the **[dispatcher](/help/implementing/dispatcher/overview.md)**implements load balancing and caching.
