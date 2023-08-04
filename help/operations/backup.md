---
title: Backup und Wiederherstellung in AEM as a Cloud Service
description: Erfahren Sie mehr über Sicherung und Wiederherstellung in AEM as a Cloud Service
exl-id: 469fb1a1-7426-4379-9fe3-f5b0ebf64d74
source-git-commit: 8c73805b6ed1b7a03c65b4d21a4252c1412a5742
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 52%

---


# Backup und Wiederherstellung in AEM as a Cloud Service {#backup-aemaacs}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_backuprestore"
>title="Backup und Wiederherstellung"
>abstract="AEM as a Cloud Service kann die gesamte Anwendung eines Kunden (Code und Inhalte) zu bestimmten, vorher festgelegten Zeitpunkten in den letzten sieben Tagen wiederherstellen und dabei alles ersetzen, was sich in der Produktion befand. Die Funktion sollte nur verwendet werden, wenn schwerwiegende Probleme mit Code oder Inhalt aufgetreten sind. Die jüngsten Daten zwischen dem Zeitpunkt des wiederhergestellten Backups und dem aktuellen Zeitpunkt gehen verloren. Die Staging-Umgebung wird ebenfalls in der alten Version wiederhergestellt."

Sollte es zu Inhalts- oder Datenbeschädigungen kommen, kann AEM as a Cloud Service die vollständige Anwendung (Code und Inhalt) eines Kunden wiederherstellen. Es wird in den letzten sieben Tagen zu bestimmten, vorab festgelegten Zeiten wiederhergestellt und ersetzt das, was in der Produktion war.
Wenn die Implementierung eines Kunden beschädigt ist (d. h. der bereitgestellte Anwendungs-Code beschädigt oder fehlerhaft ist), sollten Sie sie beheben und zu einer neuen Version wechseln, anstatt die Implementierung aus dem Backup wiederherzustellen. Das Backup wird so durchgeführt, dass es keine Auswirkungen auf die Laufzeitleistung einer Anwendung hat.

>[!CAUTION]
>
>Die Funktion sollte nur verwendet werden, wenn schwerwiegende Probleme mit Code oder Inhalt aufgetreten sind. Die jüngsten Daten zwischen dem Zeitpunkt des wiederhergestellten Backups und dem aktuellen Zeitpunkt gehen verloren. Die Staging-Umgebung wird ebenfalls in der alten Version wiederhergestellt.

## Verwendung {#how-to-use}

Kunden sollten ein Support-Ticket mit einer Beschreibung des aufgetretenen Problems erstellen. Das Support-Ticket führt normalerweise zu einer Untersuchung durch den Support der Adobe, der dann feststellen kann, ob eine Wiederherstellung erforderlich ist.

AEM as a Cloud Service unterstützt:

* Sicherung und Wiederherstellung für Staging-, Produktions- und Entwicklungsumgebungen.
* 24-Stunden-Point-in-Time Recovery, d. h., das System kann in den letzten 24 Stunden zu einem beliebigen Zeitpunkt wiederhergestellt werden.
* Wiederherstellen anhand eines bestimmten, von der Adobe definierten Zeitstempels, der zweimal täglich für die letzten sieben Tage benötigt wird. Alle Replikationsmeldungen (Löschen, Aktualisieren, Erstellen) bleiben erhalten.

In allen Fällen wird die Version des benutzerdefinierten Codes von der letzten erfolgreichen Bereitstellung vor dem Wiederherstellungspunkt übernommen.

Das Recovery Time Objective (RTO) kann variieren, aber als allgemeine Richtlinie dauert die Wiederherstellungssequenz je nach verschiedenen Faktoren, z. B. der Repository-Größe, durchschnittlich 60 bis 90 Minuten. Die Vorschau von Umgebungen und Multiregion-Herausgebern kann das Ziel der Wiederherstellung verlängern.

Nach einer Wiederherstellung wird die AEM auf die neueste Version aktualisiert.

>[!CAUTION]
>
>Daten gelöschter Umgebungen sind dauerhaft verloren und können nicht wiederhergestellt werden.

## Offsite-Sicherung {#offsite-backup}

Während regelmäßige Backups das Risiko versehentlicher Löschungen oder technischer Fehler innerhalb von AEM Cloud Services abdecken, müssen auch die Risiken abgedeckt werden, die sich aus dem Ausfall einer Region ergeben können. Neben der Verfügbarkeit besteht das größte Risiko bei Ausfällen in solchen Datenregionen in erster Linie in Datenverlust.
AEM as a Cloud Service deckt dieses Risiko als Standard für alle AEM Produktionsumgebungen ab. Er kopiert kontinuierlich den gesamten AEM in einen Remote-Bereich und stellt ihn drei Monate lang zur Wiederherstellung bereit. Adobe ruft diese Funktion Offsite Backup auf.
Die Wiederherstellung von AEM Cloud Services für Staging- und Produktionsumgebungen wird von AEM Service Reliability Engineering durchgeführt, wenn Datenregionsausfälle auftreten.
