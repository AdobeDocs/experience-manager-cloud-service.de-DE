---
title: Adobe Analytics-Integration mit AEM Screens
seo-title: Adobe Analytics Integration with AEM Screens
description: Folgen Sie dieser Seite, um mehr über die vorkonfigurierte Integration von AEM Screens mit Adobe Analytics zu erfahren und einen Wiedergabenachweis zu erhalten.
seo-description: Follow this page to learn about out of the box integration of AEM Screens with Adobe Analytics and provides you with a proof of play.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: trushton
content-type: reference
products: SG_EXPERIENCEMANAGER/Cloud/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
role: Admin, Developer
level: Intermediate
source-git-commit: bf0a841a5cd5eb278fd3d59484c84d1cee172b4e
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 95%

---

# Adobe Analytics-Integration mit AEM Screens {#adobe-analytics-integration-with-aem-screens}

In diesem Abschnitt werden folgende Themen behandelt:

* **Überblick**
* **Architekturdetails**

## Überblick {#overview}

***AEM Screens*** nutzt Adobe Analytics, um etwas Einzigartiges auf dem Markt erreichen: kanalübergreifende Analysen, die die Korrelation von lokal angezeigten Inhalten mit anderen Datenquellen ermöglichen.

AEM Screens bietet eine vorkonfigurierte Integration mit Adobe Analytics und liefert Ihnen einen Wiedergabenachweis.

In diesem Abschnitt werden folgende Funktionen beschrieben, die beim Verbinden eines AEM Screens-Projekts mit Adobe Analytics genutzt werden:

* Berichte zum Nachweis der Wiedergabe nach Gerät
* Berichte zum Nachweis der Wiedergabe nach Asset
* Sicherstellung, dass alle Player-Ereignisse erfasst und mit einem Zeitstempel versehen werden
* Sicherstellung, dass alle Player-Ereignisse lokal gespeichert werden, wenn die Wiedergabe nicht mit einem Netzwerk verbunden ist
* Erstellung von Feedback-Schleifen zur Verfolgung von Wiedergabeereignissen im Zeitverlauf
* Ändern von Inhalten und Layouts anhand von Erfolgskriterien, die vom Inhaltsautor definiert wurden

Eine Integration von Adobe Analytics mit AEM Screens hat somit folgende *Ziele*:

* Fördern des ROI bei der Implementierung von Digital Signage
* Integrieren von Analytics als Grundlage für die künftige Erfassung und Analyse von Nutzungsdaten

## Architekturdetails {#architectural-details}

Ein AEM Screens-Kunde möchte wissen, welche Inhalte wann wie lange angezeigt wurden (aggregiert). Dies ist eine gebräuchliche Funktion einer Signage-Lösung. Statt eigene Analysen zu erstellen, nutzt AEM Screens Adobe Analytics, um etwas branchenweit Einzigartiges zu ermöglichen: kanalübergreifende Analysen, die dabei helfen, lokale angezeigte Inhalte mit anderen Datenquellen zu korrelieren.

Im folgenden Architekturdiagramm wird die Integration von Adobe Analytics mit AEM Screens veranschaulicht:

![Integration mit Adobe Analytics](/help/screens-cloud/assets/analytics-architecture.png)

## Aktivieren von Adobe Analytics in AEM Screens Cloud {#enabling-adobe-analytics-in-aem-screens-cloud}

Wenden Sie sich an Ihren Adobe Relationship Manager, um Adobe-Analysen in Screens Cloud zu aktivieren.

## Screens Analytics: Aktivierungsablauf {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>Wenden Sie sich vor der Konfiguration der Eigenschaften an Ihren Adobe Relationship Manager, damit dieser ein Ticket erstellt und Sie einen **Analytics-API-Schlüssel** sowie ein **Analytics-Projekt** zur Verwendung mit AEM Screens erhalten.

## Verwenden des Adobe Analytics-Service in AEM Screens {#using-adobe-analytics-service-in-aem-screens}

In diesem Szenario wird die Analytics-API über REST-Aufrufe aus einem Analytics-Service in den Screens-Kernkomponenten „Firmware“ und „Instrumente“ aufgerufen, um explizit Ereignisse zu erstellen und zu senden, die für ein bestimmtes Nutzungsszenario spezifisch sind. Gleichzeitig ist eine Erweiterung möglich, bei der sich benutzerdefinierte Nachrichten von einem benutzerdefinierten Kanal an Analytics senden lassen.

Analytics-Ereignisse werden in indexedDB offline gespeichert und später aufgeteilt und an die Cloud gesendet.
