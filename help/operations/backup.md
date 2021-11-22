---
title: Backup und Wiederherstellung in AEM as a Cloud Service
description: Backup und Wiederherstellung in AEM as a Cloud Service
exl-id: 469fb1a1-7426-4379-9fe3-f5b0ebf64d74
source-git-commit: cac25668240a87ecbf86c4f71881310b3c3d17d2
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 93%

---

# Backup und Wiederherstellung in AEM as a Cloud Service

>[!CONTEXTUALHELP]
>id="aemcloud_golive_backuprestore"
>title="Backup und Wiederherstellung"
>abstract="AEM as a Cloud Service kann die gesamte Anwendung eines Kunden (Code und Inhalte) zu bestimmten, vorher festgelegten Zeitpunkten in den letzten sieben Tagen wiederherstellen und dabei alles ersetzen, was sich in der Produktion befand. Die Funktion sollte nur verwendet werden, wenn schwerwiegende Probleme mit Code oder Inhalt aufgetreten sind. Die neuesten Daten zwischen dem Zeitpunkt des wiederhergestellten Backups und dem aktuellen Zeitpunkt gehen verloren. Die Staging-Umgebung wird ebenfalls in der alten Version wiederhergestellt."

Sollte es zu Inhalts- oder Datenbeschädigungen kommen, kann AEM as a Cloud Service die vollständige Anwendung eines Kunden (Code und Inhalt) auf bestimmte, vordefinierte Zeitpunkte in den letzten sieben Tagen zurücksetzen, wodurch Inhalte in der Produktion ersetzt werden.
Wenn die Implementierung eines Kunden beschädigt ist (d. h. der bereitgestellte Anwendungs-Code beschädigt oder fehlerhaft ist), sollten Sie sie beheben und zu einer neuen Version wechseln, anstatt die Implementierung aus dem Backup wiederherzustellen. Das Backup wird so durchgeführt, dass es keine Auswirkungen auf die Laufzeitleistung einer Anwendung hat.

>[!CAUTION]
>
>Die Funktion sollte nur verwendet werden, wenn schwerwiegende Probleme mit Code oder Inhalt aufgetreten sind. Die neuesten Daten zwischen dem Zeitpunkt des wiederhergestellten Backups und dem aktuellen Zeitpunkt gehen verloren. Die Staging-Umgebung wird ebenfalls in der alten Version wiederhergestellt.

## Verwendung

Kunden sollten ein Support-Ticket mit einer Beschreibung des aufgetretenen Problems erstellen. Dies führt zu einer Untersuchung durch das Adobe-Support-Team, das entscheiden wird, ob eine Wiederherstellung notwendig ist.

AEM as a Cloud Service unterstützt:

* 24-Stunden-Point-in-Time-Recovery, d. h. das System kann mit einem beliebigen Zeitpunkt aus den letzten 24 Stunden wiederhergestellt werden.
* Wiederherstellen anhand eines bestimmten, von der Adobe definierten Zeitstempels, der zweimal täglich für die letzten sieben Tage benötigt wird.  Alle Replikationsmeldungen (Löschen, Aktualisieren, Erstellen) bleiben erhalten.

In jedem Fall wird die Version des benutzerdefinierten Codes von der letzten erfolgreichen Implementierung, die vor dem Wiederherstellungspunkt stattgefunden hat, übernommen.

Das Recovery Time Objective (RTO) variiert je nach Größe des Repositorys, im Allgemeinen sollte die Wiederherstellungssequenz aber ca. 30 Minuten in Anspruch nehmen.

Nach einer Wiederherstellung wird die AEM-Version auf die neueste Version aktualisiert.

>[!CAUTION]
>
>Daten gelöschter Umgebungen gehen dauerhaft verloren und können nicht wiederhergestellt werden.
