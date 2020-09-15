---
title: Sicherung und Wiederherstellung in AEM als Cloud Service
description: 'Sicherung und Wiederherstellung in AEM als Cloud Service '
translation-type: tm+mt
source-git-commit: c3af507716ef60541ecca8dafb797651e8ece9d3
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---


# Sicherung und Wiederherstellung in AEM als Cloud Service

Sollte es zu Inhalts- oder Datenbeschädigungen kommen, AEM ein Cloud Service die vollständige Anwendung (Code und Inhalt) eines Kunden in den letzten sieben Tagen auf bestimmte, vordefinierte Zeiten zurücksetzen kann, wodurch die Produktion ersetzt wird.
Wenn die Bereitstellung eines Kunden (d. h. der bereitgestellte Anwendungscode ist beschädigt oder fehlerhaft), sollten Sie ihn lieber beheben und zu einer neuen Version weiterleiten, anstatt ihn aus der Sicherung wiederherzustellen. Die Sicherung wird auf eine Weise durchgeführt, die keine Auswirkungen auf die Laufzeit-Leistung einer Anwendung hat.

>[!CAUTION]
>
>Diese Funktion sollte nur verwendet werden, wenn schwerwiegende Probleme mit Code oder Inhalt auftreten. Die letzten Daten zwischen dem Zeitpunkt der wiederhergestellten Sicherung und dem Moment gehen verloren. Die Staging-Version wird ebenfalls wiederhergestellt.

## Verwendung

Kunden sollten ein Support-Ticket mit einer Beschreibung des aufgetretenen Problems einreichen. Dies führt zu einer Untersuchung durch die Adobe Support, die entscheiden, ob eine Wiederherstellung notwendig ist.

AEM als Cloud Service unterstützt:

* 24-Stunden-Recovery, d.h. das System kann in den letzten 24 Stunden zu einem beliebigen Zeitpunkt wiederhergestellt werden.
* Wiederherstellen anhand eines bestimmten Zeitstempels, der in den letzten 7 Adoben einmal täglich verwendet wurde.  Alle Replikationsmeldungen (Löschen, Aktualisieren, Erstellen) bleiben erhalten.

In allen Fällen wird die Version des benutzerdefinierten Codes von der letzten erfolgreichen Bereitstellung vor dem Wiederherstellungspunkt übernommen.

Das Ziel der Wiederherstellungszeit (RTO) variiert je nach Größe des Repositorys, aber als allgemeine Richtlinie, sobald die Wiederherstellungssequenz beginnt, sollte es ca. 30 Minuten dauern.

Nach einer Wiederherstellung wird die AEM auf die neueste Version aktualisiert.

**Die Daten gelöschter Umgebung gehen dauerhaft verloren und können nicht wiederhergestellt werden.**
