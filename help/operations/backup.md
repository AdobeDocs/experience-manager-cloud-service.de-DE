---
title: Backup und Wiederherstellung in AEM as a Cloud Service
description: Backup und Wiederherstellung in AEM as a Cloud Service
exl-id: 469fb1a1-7426-4379-9fe3-f5b0ebf64d74
source-git-commit: 7778430b409bdd6f30530d34f2e8cd10d63df153
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 100%

---

# Backup und Wiederherstellung in AEM as a Cloud Service {#backup-aemaacs}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_backuprestore"
>title="Backup und Wiederherstellung"
>abstract="AEM as a Cloud Service kann die gesamte Anwendung eines Kunden (Code und Inhalte) zu bestimmten, vorher festgelegten Zeitpunkten in den letzten sieben Tagen wiederherstellen und dabei alles ersetzen, was sich in der Produktion befand. Die Funktion sollte nur verwendet werden, wenn schwerwiegende Probleme mit Code oder Inhalt aufgetreten sind. Die neuesten Daten zwischen dem Zeitpunkt des wiederhergestellten Backups und dem aktuellen Zeitpunkt gehen verloren. Die Staging-Umgebung wird ebenfalls in der alten Version wiederhergestellt."

Sollte es zu Inhalts- oder Datenbeschädigungen kommen, kann AEM as a Cloud Service die vollständige Anwendung eines Kunden (Code und Inhalt) auf bestimmte, vordefinierte Zeitpunkte in den letzten sieben Tagen zurücksetzen, wodurch Inhalte in der Produktion ersetzt werden.
Wenn die Implementierung eines Kunden beschädigt ist (d. h. der bereitgestellte Anwendungs-Code beschädigt oder fehlerhaft ist), sollten Sie sie beheben und zu einer neuen Version wechseln, anstatt die Implementierung aus dem Backup wiederherzustellen. Das Backup wird so durchgeführt, dass es keine Auswirkungen auf die Laufzeitleistung einer Anwendung hat.

>[!CAUTION]
>
>Die Funktion sollte nur verwendet werden, wenn schwerwiegende Probleme mit Code oder Inhalt aufgetreten sind. Die neuesten Daten zwischen dem Zeitpunkt des wiederhergestellten Backups und dem aktuellen Zeitpunkt gehen verloren. Die Staging-Umgebung wird ebenfalls in der alten Version wiederhergestellt.

## Verwendung {#how-to-use}

Kunden sollten ein Support-Ticket mit einer Beschreibung des aufgetretenen Problems erstellen. Dies führt zu einer Untersuchung durch das Adobe-Support-Team, das entscheiden wird, ob eine Wiederherstellung notwendig ist.

AEM as a Cloud Service unterstützt:

* Sicherung und Wiederherstellung für Staging-, Produktions- und Entwicklungsumgebungen.
* 24-Stunden-Point-in-Time-Recovery, d. h. das System kann mit einem beliebigen Zeitpunkt aus den letzten 24 Stunden wiederhergestellt werden.
* Wiederherstellen anhand eines bestimmten, von Adobe definierten Zeitstempels, der zweimal täglich für die letzten 7 Tage erstellt wird.  Alle Replikationsmeldungen (Löschen, Aktualisieren, Erstellen) bleiben erhalten.

In jedem Fall wird die Version des benutzerdefinierten Codes von der letzten erfolgreichen Implementierung, die vor dem Wiederherstellungspunkt stattgefunden hat, übernommen.

Das Recovery Time Objective (RTO) variiert je nach Größe des Repositorys. Als allgemeine Richtlinie sollte die Wiederherstellungssequenz jedoch zwischen 30 Minuten und mehreren Stunden dauern.

Nach einer Wiederherstellung wird die AEM-Version auf die neueste Version aktualisiert.

>[!CAUTION]
>
>Daten gelöschter Umgebungen sind dauerhaft verloren und können nicht wiederhergestellt werden.

## Offsite-Sicherung {#offsite-backup}

Während regelmäßige Backups das Risiko versehentlicher Löschungen oder technischer Fehler innerhalb von AEM Cloud Services abdecken, müssen auch die Risiken abgedeckt werden, die sich aus dem Ausfall einer Region ergeben können. Neben der Verfügbarkeit besteht das größte Risiko bei Ausfällen in solchen Datenregionen in erster Linie in Datenverlust.
AEM as a Cloud Service deckt dieses Risiko als Standard für alle AEM Produktionsumgebungen ab, indem der gesamte AEM-Inhalt kontinuierlich in eine entfernte Region kopiert und für einen Zeitraum von 3 Monaten für die Wiederherstellung zur Verfügung gestellt wird. Wir nennen diese Funktion Offsite Backup.
Die Wiederherstellung von AEM Cloud Services für Staging- und Produktionsumgebungen erfolgt durch AEM Service Reliability Engineering im Fall von Ausfällen in der Datenregion.
