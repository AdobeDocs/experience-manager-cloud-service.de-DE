---
title: Rollenbasierte Berechtigungen
description: Rollenbasierte Berechtigungen
translation-type: tm+mt
source-git-commit: 3c56d94f9922cb65b91912dd96eb8aa60efc2b53

---


# Rollenbasierte Berechtigungen {#role-based-permissions}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Beispielsweise schreibt ein Entwickler Code und ist berechtigt, den Code per Push an das **Git-Repository** zu übertragen. Ein Business Owner verfügt wiederum über verschiedene Berechtigungen, um KPIs (Key Performance Indicators) zu definieren und Bereitstellungen zu genehmigen.

## Anwenderberechtigungen {#user-permissions}

Jede der Rollen verfügt über spezifische Berechtigungen, vorkonfigurierte Aufgaben oder Berechtigungen, die jeder Rolle zugeordnet sind. In der folgenden Tabelle sind die verfügbaren Funktionen und Rollen aufgelistet, die die Funktion ausführen können.

| Berechtigung | Beschreibung | Business Owner | Bereitstellungsmanager | Programmmanager | Entwickler |
|--- |--- |--- |--- |--- |--- |
| Programm hinzufügen | Hinzufügen ein neues Programm. | x |  |  |  |
| Umgebung erstellen | Erstellen Sie Prod+Stage-, Dev- und Playground-Umgebung. | x | x |  |  |
| Umgebung aktualisieren | Aktualisieren Sie die Umgebung Prod+Stage, Dev und Playground. | x | x |  |  |
| Umgebung löschen | Löschen Sie Umgebung ohne Prod, Dev und Playground. | x | x |  |  |
| Umgebung löschen | Löschen Sie die Umgebung Prod+Stage. |  |  |  |  |
| Programm einrichten | Konfigurieren Sie Programm (einschließlich KPIs). | x |  |  |  |
| Programm einrichten | Zugriff erlauben |  | x |  | x |
| Pipeline-Einrichtung | Einrichten oder Bearbeiten der Pipeline. |  | x |  |  |
| Pipeline-Ausführung | Beginn der Pipeline. | x | x |  |  |
| Pipeline-Ausführung | Ablehnen/Genehmigen Sie wichtige 3-Stufen-Fehler. | x | x | x |  |
| Pipeline-Ausführung | Bereitstellen der GoLive-Genehmigung. | x | x | x |  |
| Pipeline-Ausführung | Planen der Bereitstellung für die Produktion. | x | x | x |  |
| Pipeline-Ausführung | Produktionskanal fortsetzen. |  |  |  |  |
| Pipeline löschen | Ermöglicht das Löschen einer Pipeline. |  | x |  |  |
| Ausführung abbrechen | Aktuelle Ausführung abbrechen. |  | x |  |  |
| Umgebung verwalten  | Hinzufügen Sie das Segment Publish-Dispatcher im Bildschirm &quot;Umgebung verwalten&quot;. | x | x |  |  |  |
| Push-Aktualisierung | Push-Update-Pipeline des Beginns |  |  |  |  |
| Persönliches Zugriffs-Token erstellen | Zugriff auf Git. |  | x |  | x |

