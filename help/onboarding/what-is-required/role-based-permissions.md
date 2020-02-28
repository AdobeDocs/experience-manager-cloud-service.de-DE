---
title: Rollenbasierte Berechtigungen
description: Rollenbasierte Berechtigungen
translation-type: tm+mt
source-git-commit: 6cae9b2b719dab687f601a0596d37f99afded9ab

---


# Rollenbasierte Berechtigungen {#role-based-permissions}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Beispielsweise schreibt ein Entwickler Code und ist berechtigt, den Code per Push an das **Git-Repository** zu übertragen. Ein Business Owner verfügt wiederum über verschiedene Berechtigungen, um KPIs (Key Performance Indicators) zu definieren und Bereitstellungen zu genehmigen.

## Anwenderberechtigungen {#user-permissions}

Jede Rolle verfügt über bestimmte Berechtigungen, vorkonfigurierte Aufgaben oder Berechtigungen, die jeder Rolle zugeordnet sind. In der folgenden Tabelle sind die verfügbaren Funktionen und Rollen aufgelistet, die die Funktion ausführen können.

| Berechtigung | Beschreibung | Business Owner | Bereitstellungsmanager | Programmmanager | Entwickler |
|--- |--- |--- |--- |--- |--- |
| Mandanten erstellen | Neuen Mandanten erstellen |  |  |  |  |
| Mandanten aktualisieren | Mandanten aktualisieren. |  |  |  |  |
| Programm hinzufügen | Neues Programm hinzufügen. | x |  |  |  |
| Umgebung erstellen | Erstellen Sie Prod+Stage, Dev, Playground-Umgebungen. | x | x |  |  |
| Umgebungsvariablen konfigurieren | Konfigurieren Sie Umgebungsvariablen und -geheimnisse. |  | x |  | x |
| Benutzerdefinierten Domänennamen hinzufügen oder entfernen, SSL-Zertifikat hochladen oder aktualisieren | Benutzerdefinierten Domänennamen hinzufügen/entfernen, SSL-Zertifikat hochladen/aktualisieren | x | x |  |  |
| Umgebung aktualisieren | Aktualisieren Sie Prod+Stage, Dev, Playground-Umgebungen. | x | x |  |  |
| Umgebung löschen | Löschen Sie Umgebungen ohne Prod, Dev und Playground. | x | x |  |  |
| Umgebung löschen | Löschen Sie Prod+Stage-Umgebung. |  |  |  |  |
| Hibernate-Umgebung | Hibernate Non-prod, Dev, Playground-Umgebungen. | x | x |  |  |
| Programm-Setup | Konfigurieren Sie das Programm (einschließlich KPIs). | x |  |  |  |
| Programm-Setup | Richtlinien zur Skalierung konfigurieren (Allgemein: Konfigurieren der maximalen Anzahl von Stufen und des horizontalen Ausmaßes nach Bedarf: Teilnahme). | x |  |  |  |
| Programm-Setup | Zugriff erlauben |  | x |  | x |
| Pipeline-Einrichtung | Einrichten oder Bearbeiten der Pipeline. |  | x |  |  |
| Pipeline-Ausführung | Starten Sie die Pipeline. | x | x |  |  |
| Pipeline-Ausführung | Ablehnen/Genehmigen Sie wichtige Fehler in 3 Stufen. | x | x | x |  |
| Pipeline-Ausführung | Bereitstellen der GoLive-Genehmigung. | x | x | x |  |
| Pipeline-Ausführung | Planen der Bereitstellung für die Produktion. | x | x | x |  |
| Pipeline-Ausführung | Produktionskanal fortsetzen. |  |  |  |  |
| Teilnahme (oder Abmeldung) an der Bereitstellung | Wählen Sie im Bildschirm &quot;Programm-Setup&quot;die Option &quot;Horizontale On-Demand-Bereitstellung&quot;. Konfigurieren Sie die max. &#39;zulässigen&#39; P-D-Segmente, die horizontal verkleinert werden können, in unseren (nicht-) Listen-Umgebungen. | x |  |  |  |
| Umgebung verwalten  | Fügen Sie im Bildschirm &quot;Umgebung verwalten&quot;das Segment &quot;Publish-Dispatcher&quot;hinzu. | x | x |  |  |  |
| Produktaktualisierung | Die AEM Update Card ist sichtbar und bringt den Benutzer zum Updateassistenten. | x | x | x | x |
| Produktaktualisierung | Der Assistent zum Aktualisieren von Produkten kann aktiviert werden. | x | x |  |  |
| Push-Aktualisierung | Starten Sie Push Update Pipeline. |  |  |  |  |
| Persönliches Zugriffstoken erstellen | Persönliches Zugriffstoken erstellen. |  | x |  | x |

