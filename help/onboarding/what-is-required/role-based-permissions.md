---
title: Rollenbasierte Berechtigungen
description: Rollenbasierte Berechtigungen
translation-type: tm+mt
source-git-commit: e59fe55c255d5239a561a9fb878faa81d17b4b48

---


# Rollenbasierte Berechtigungen {#role-based-permissions}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Beispielsweise schreibt ein Entwickler Code und ist berechtigt, den Code per Push an das **Git-Repository** zu übertragen. Ein Business Owner verfügt wiederum über verschiedene Berechtigungen, um KPIs (Key Performance Indicators) zu definieren und Bereitstellungen zu genehmigen.

## Anwenderberechtigungen {#user-permissions}

Jede Rolle verfügt über bestimmte Berechtigungen, vorkonfigurierte Aufgaben oder Berechtigungen, die jeder Rolle zugeordnet sind. In der folgenden Tabelle sind die verfügbaren Funktionen und Rollen aufgelistet, die die Funktion ausführen können.

| Berechtigung | Beschreibung | Business Owner | Bereitstellungsmanager | Programmmanager | Entwickler |
|--- |--- |--- |--- |--- |--- |
| Programm hinzufügen | Neues Programm hinzufügen. | x | x | x | x |
| Anwendung lesen | Lesen Sie die Programm-KPIs. | x | x | x | x |
| Anwendung schreiben | Programmeinrichtung oder -bearbeitung. | x |  |  |  |  |
| Umgebung lesen | Siehe Umgebungsdetails. | x | x | x | x |
| Ausführung erstellen | Starten der Pipeline. | x | x | x |  |
| Ausführung lesen | Siehe Ausführungsstatus. | x | x | x | x |
| Ausführung fortsetzen | Kann die Ausführung fortsetzen, wenn sie angehalten wurde. | x | x | x |  | x |
| Ausführung, Bereitstellung für die Produktion genehmigen | Bereitstellen der GoLive-Genehmigung. | x | x | x |  |  |
| Ausführung, Bereitstellung für die Produktion planen | Planen der Bereitstellung für die Produktion. | x | x | x |
| Ausführung abbrechen | Abbrechen der aktuellen Ausführung. | x | x | x |  |
| Ausführung, Quality-Gate-Fehler außer Kraft setzen | Genehmigen bedeutender Quality-Gate-Fehler. | x | x | x |  |
| Pipeline erstellen | Einrichten/Bearbeiten der Pipeline. |  | x |  |  |
| Pipeline lesen | Siehe Pipelinedetails. | x | x | x | x |
| Pipeline schreiben | Einrichten/Bearbeiten der Pipeline. |  | x |  |  |
| Pipeline ändern, Genehmigung | Berechtigung zum Bearbeiten der Option „Business Owner“. |  | x |  |  |
| Schritt lesen | Siehe Ergebnis des Schritts „Qualitätsmetriken“. | x | x | x | x |
