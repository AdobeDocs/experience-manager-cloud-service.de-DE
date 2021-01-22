---
title: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.10.0
description: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.10.0
translation-type: tm+mt
source-git-commit: 65752c7c51538de27aa2b21695e8eb6c6695a5f5
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 48%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager als Cloud Service 2020.10.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für Cloud Manager in AEM als Cloud Service 2020.10.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2020.10.0 ist der 01. Oktober 2020.

## Cloud Manager {#cloud-manager}

### Neue Funktionen {#what-is-new}

* Die Seite &quot;Umgebung&quot;wurde neu gestaltet.

* Im Ruhezustand befindliche Umgebungen verfügen jetzt über einen separaten Status.

* Der Cloud Manager Build Container unterstützt jetzt das Kompilieren von Projekten mit Java 8 oder Java 11. Java 11 wird vom Maven Toolchain-System unterstützt.

* Die Anzahl der Umgebungsvariablen pro Umgebung wurde auf 200 erhöht.

* Die Umgebung auf der Übersichtsseite wird jetzt bis zu drei Umgebung Liste. Die Benutzer können die Schaltfläche **Alle anzeigen** auswählen, um zur Zusammenfassungsseite der Umgebung zu navigieren und eine Tabelle mit einer vollständigen Liste von Umgebung Ansicht.
Weitere Informationen finden Sie unter [Umgebung anzeigen](/help/implementing/cloud-manager/manage-environments.md#viewing-environment).


### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Die Verknüpfung von Cloud Manager mit der Developer Console war vor der vollständigen Erstellung der Umgebung nicht korrekt aktiviert.

* Die Verknüpfung zur Developer Console direkt aus Cloud Manager zeigte die Option zum Versetzen der Umgebung eines Sandbox-Programms in den Ruhezustand und zum Aufheben des Ruhezustands nicht an.

* Die Schaltflächen &quot;Abbrechen&quot;und &quot;Speichern&quot;auf der Seite &quot;Bearbeiten in der Nicht-Produktionsumgebung&quot;waren nicht immer sichtbar.

* Bestimmte Fehler im Code-Qualitätsprozess konnten dazu führen, dass die Protokolldatei nicht korrekt erzeugt wurde.

* Beim Erstellen eines neuen Programms gab der vorgeschlagene Name manchmal ein Duplikat eines vorhandenen Programmnamens zurück.

* Protokolle für bestimmte größere Pipeline-Schritte konnten nicht über die gesamte Benutzeroberfläche konsistent heruntergeladen werden.

* Bei der Validierung von Umgebungsnamen trat ein Fehler mit einer Verschiebung um den Wert eins auf.

* Auf der Seite „Umgebungen“ wurden manchmal Veröffentlichungs- und Dispatcher-Segmente angezeigt, wenn keine vorhanden waren.