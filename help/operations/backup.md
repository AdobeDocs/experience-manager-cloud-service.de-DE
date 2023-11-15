---
title: Backup und Wiederherstellung in AEM as a Cloud Service
description: Erfahren Sie mehr über Sicherung und Wiederherstellung in AEM as a Cloud Service
exl-id: 469fb1a1-7426-4379-9fe3-f5b0ebf64d74
source-git-commit: 83b5d9a3ff0e9a3c69e36a97a3f733b05f827d3b
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 97%

---


# Backup und Wiederherstellung in AEM as a Cloud Service {#backup-aemaacs}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_backuprestore"
>title="Backup und Wiederherstellung"
>abstract="AEM as a Cloud Service kann die gesamte Anwendung eines Kunden (Code und Inhalte) zu bestimmten, vorher festgelegten Zeitpunkten in den letzten sieben Tagen wiederherstellen und dabei alles ersetzen, was sich in der Produktion befand. Die Funktion sollte nur verwendet werden, wenn schwerwiegende Probleme mit Code oder Inhalt aufgetreten sind. Die jüngsten Daten zwischen dem Zeitpunkt des wiederhergestellten Backups und dem aktuellen Zeitpunkt gehen dabei verloren. Die Staging-Umgebung wird ebenfalls in der alten Version wiederhergestellt."

Sollte es zu Inhalts- oder Datenbeschädigungen kommen, kann AEM as a Cloud Service die vollständige Anwendung (Code und Inhalt) einer Kundin bzw. eines Kunden wiederherstellen. Sie wird zu bestimmten, vorher festgelegten Zeitpunkten in den letzten sieben Tagen wiederhergestellt und ersetzt das, was in der Produktion war.
Wenn die Implementierung eines Kunden beschädigt ist (d. h. der bereitgestellte Anwendungs-Code beschädigt oder fehlerhaft ist), sollten Sie sie beheben und zu einer neuen Version wechseln, anstatt die Implementierung aus dem Backup wiederherzustellen. Das Backup wird so durchgeführt, dass es keine Auswirkungen auf die Laufzeitleistung einer Anwendung hat.

>[!CAUTION]
>
>Die Funktion sollte nur verwendet werden, wenn schwerwiegende Probleme mit Code oder Inhalt aufgetreten sind. Die jüngsten Daten zwischen dem Zeitpunkt des wiederhergestellten Backups und dem aktuellen Zeitpunkt gehen dabei verloren. Die Staging-Umgebung wird ebenfalls in der alten Version wiederhergestellt.

## Verwendung {#how-to-use}

Kunden sollten ein Support-Ticket mit einer Beschreibung des aufgetretenen Problems erstellen. Das Support-Ticket führt normalerweise zu einer Untersuchung durch den Adobe-Support, der dann feststellen kann, ob eine Wiederherstellung erforderlich ist.

AEM as a Cloud Service unterstützt:

* Backup und Wiederherstellung für Staging-, Produktions- und Entwicklungsumgebungen.
* 24-Stunden-Zeitpunkt-Wiederherstellung, d. h. das System kann mit einem beliebigen Zeitpunkt aus den letzten 24 Stunden wiederhergestellt werden.
* Wiederherstellung anhand eines bestimmten, von Adobe definierten Zeitstempels, der zweimal täglich für die letzten sieben Tage erstellt wird. Alle Replikationsmeldungen (Löschungen, Updates, Erstellungen) bleiben erhalten.

In jedem Fall wird die Version des benutzerdefinierten Codes von der letzten erfolgreichen Bereitstellung, die vor dem Wiederherstellungspunkt stattgefunden hat, übernommen.

Das Ziel für die Wiederherstellungszeit (Recovery Time Objective, RTO) kann variieren, aber als allgemeine Richtlinie lässt sich sagen, dass die Wiederherstellungssequenz im Durchschnitt zwischen 60 und 90 Minuten dauert, abhängig von verschiedenen Faktoren, wie z. B. der Größe des Repositorys. Die Vorschau von Umgebungen und Multiregion-Herausgebern kann das Ziel der Wiederherstellung verlängern.

Nach einer Wiederherstellung wird die AEM-Version auf die neueste Version aktualisiert.

>[!CAUTION]
>
>Daten gelöschter Umgebungen sind dauerhaft verloren und können nicht wiederhergestellt werden.

## Offsite-Sicherung {#offsite-backup}

Während regelmäßige Backups das Risiko versehentlicher Löschungen oder technischer Fehler innerhalb von AEM Cloud Services abdecken, müssen auch die Risiken abgedeckt werden, die sich aus dem Ausfall einer Region ergeben können. Neben der Verfügbarkeit besteht das größte Risiko bei Ausfällen in solchen Datenregionen in erster Linie in Datenverlust.
AEM as a Cloud Service deckt dieses Risiko standardmäßig für alle AEM-Produktionsumgebungen ab. Der gesamte AEM-Inhalt wird kontinuierlich in eine andere, entfernte Region kopiert und steht drei Monate lang zur Wiederherstellung zur Verfügung. Adobe nennt diese Funktion Offsite-Backup.
Die Wiederherstellung von AEM Cloud Services für Staging- und Produktionsumgebungen erfolgt durch AEM Service Reliability Engineering, wenn es zu Ausfällen von Datenregionen kommt.