---
title: Backup und Wiederherstellung in AEM as a Cloud Service
description: 'Backup und Wiederherstellung in AEM as a Cloud Service '
translation-type: tm+mt
source-git-commit: c3af507716ef60541ecca8dafb797651e8ece9d3
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 100%

---


# Backup und Wiederherstellung in AEM as a Cloud Service

Sollte es zu Inhalts- oder Datenbeschädigungen kommen, kann AEM as a Cloud Service die vollständige Anwendung eines Kunden (Code und Inhalt) auf bestimmte, vordefinierte Zeitpunkte in den letzten sieben Tagen zurücksetzen, wodurch Inhalte in der Produktion ersetzt werden.
Wenn die Implementierung eines Kunden beschädigt ist (d. h. der bereitgestellte Anwendungs-Code beschädigt oder fehlerhaft ist), sollten Sie sie beheben und zu einer neuen Version wechseln, anstatt die Implementierung aus dem Backup wiederherzustellen. Das Backup wird so durchgeführt, dass es keine Auswirkungen auf die Laufzeitleistung einer Anwendung hat.

>[!CAUTION]
>
>Die Funktion sollte nur verwendet werden, wenn schwerwiegende Probleme mit Code oder Inhalt aufgetreten sind. Die neuesten Daten zwischen dem Zeitpunkt des wiederhergestellten Backups und dem aktuellen Zeitpunkt gehen verloren. Die Staging-Umgebung wird ebenfalls in der alten Version wiederhergestellt.

## Verwendung

Kunden sollten ein Support-Ticket mit einer Beschreibung des aufgetretenen Problems erstellen. Dies führt zu einer Untersuchung durch das Adobe-Support-Team, das entscheiden wird, ob eine Wiederherstellung notwendig ist.

AEM as a Cloud Service unterstützt:

* 24-Stunden-Point-in-Time-Recovery, d. h. das System kann mit einem beliebigen Zeitpunkt aus den letzten 24 Stunden wiederhergestellt werden.
* Wiederherstellen anhand eines bestimmten Adobe-definierten Zeitstempels, der einmal täglich für die letzten 7 Tage erstellt wird.  Alle Replikationsmeldungen (Löschen, Aktualisieren, Erstellen) bleiben erhalten.

In jedem Fall wird die Version des benutzerdefinierten Codes von der letzten erfolgreichen Implementierung, die vor dem Wiederherstellungspunkt stattgefunden hat, übernommen.

Das Recovery Time Objective (RTO) variiert je nach Größe des Repositorys, im Allgemeinen sollte die Wiederherstellungssequenz aber ca. 30 Minuten in Anspruch nehmen.

Nach einer Wiederherstellung wird die AEM-Version auf die neueste Version aktualisiert.

**Daten gelöschter Umgebungen gehen dauerhaft verloren und können nicht wiederhergestellt werden.**
