---
title: Sicherung und Wiederherstellung in AEM als Cloud-Dienst
description: 'Sicherung und Wiederherstellung in AEM als Cloud-Dienst '
translation-type: tm+mt
source-git-commit: 8fba31951276d7e0de1f3bd079e42e431edaff4e

---


# Sicherung und Wiederherstellung in AEM als Cloud-Dienst

Sollte es zu Inhalts- oder Datenbeschädigungen kommen, kann AEM als Cloud-Dienst die vollständige Anwendung (Code und Inhalt) eines Kunden zu bestimmten, vordefinierten Zeiten in den letzten sieben Tagen wiederherstellen und die Produktion ersetzen.
Wenn die Bereitstellung eines Kunden (d. h. der bereitgestellte Anwendungscode ist beschädigt oder fehlerhaft), sollten Sie ihn lieber beheben und zu einer neuen Version weiterleiten, anstatt ihn aus der Sicherung wiederherzustellen.

>[!CAUTION]
>
>Diese Funktion sollte nur verwendet werden, wenn schwerwiegende Probleme mit Code oder Inhalt auftreten. Die letzten Daten zwischen dem Zeitpunkt der wiederhergestellten Sicherung und dem Moment gehen verloren. Die Staging-Version wird ebenfalls wiederhergestellt.

## Verwendung

Kunden sollten ein Support-Ticket mit einer Beschreibung des aufgetretenen Problems einreichen. Dies führt zu einer Untersuchung des Adobe-Supports, der feststellt, ob eine Wiederherstellung erforderlich ist.

AEM als Cloud-Dienst unterstützt:

* 24-Stunden-Recovery, d. h., das System kann in den letzten 24 Stunden zu einem beliebigen Zeitpunkt wiederhergestellt werden.
* Wiederherstellen eines bestimmten, von Adobe definierten Zeitstempels, der in den letzten 7 Tagen einmal täglich ausgeführt wurde.  Alle Replikationsmeldungen (Löschen, Aktualisieren, Erstellen) bleiben erhalten.

In allen Fällen wird die Version des benutzerdefinierten Codes von der letzten erfolgreichen Bereitstellung vor dem Wiederherstellungspunkt übernommen.

Das Ziel der Wiederherstellungszeit (RTO) variiert je nach Größe des Repositorys, aber als allgemeine Richtlinie, sobald die Wiederherstellungssequenz beginnt, sollte es ca. 30 Minuten dauern.

Nach einer Wiederherstellung wird die AEM-Version auf die neueste Version aktualisiert.

**Die Daten aus gelöschten Umgebungen gehen dauerhaft verloren und können nicht wiederhergestellt werden.**
