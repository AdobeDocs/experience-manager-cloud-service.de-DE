---
title: Versionshinweise für die Version 2020.10.0 [!DNL Adobe Experience Manager] von als Cloud Service.
description: '[!DNL Adobe Experience Manager] als Cloud Service-Versionshinweise für 2020.10.0.'
translation-type: tm+mt
source-git-commit: f0ac4b511fefa0bcde8d59c416da638941cd52ad
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 52%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

The following section outlines the general Release Notes for [!DNL Experience Manager] as a Cloud Service 2020.10.0.

## Cloud Manager {#cloud-manager}

* Die Seite &quot;Umgebung&quot;wurde neu gestaltet.

* Im Ruhezustand befindliche Umgebungen verfügen jetzt über einen separaten Status.

* Der Cloud Manager Build Container unterstützt jetzt das Kompilieren von Projekten mit Java 8 oder Java 11. Java 11 wird vom Maven Toolchain-System unterstützt.

* Die Anzahl der Umgebungsvariablen pro Umgebung wurde auf 200 erhöht.

* Die Umgebung auf der Übersichtsseite wird jetzt bis zu drei Umgebung Liste. Die Benutzer können auf die Schaltfläche &quot;Alle **** anzeigen&quot;klicken, um zur Zusammenfassungsseite der Umgebung zu navigieren und eine Tabelle mit einer vollständigen Liste der Umgebung Ansicht.
Weitere Informationen finden Sie unter Umgebung [](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) anzeigen.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Die Verknüpfung von Cloud Manager mit der Developer Console war vor der vollständigen Erstellung der Umgebung nicht korrekt aktiviert.

* Die Verknüpfung zur Developer Console direkt aus Cloud Manager zeigte die Option zum Versetzen der Umgebung eines Sandbox-Programms in den Ruhezustand und zum Aufheben des Ruhezustands nicht an.

* Die Schaltflächen &quot;Abbrechen&quot;und &quot;Speichern&quot;auf der Seite &quot;Bearbeiten in der Nicht-Produktionsumgebung&quot;waren nicht immer sichtbar.

* Bestimmte Fehler im Code-Qualitätsprozess konnten dazu führen, dass die Protokolldatei nicht korrekt erzeugt wurde.

* Beim Erstellen eines neuen Programms gab der vorgeschlagene Name manchmal ein Duplikat eines vorhandenen Programmnamens zurück.

* Protokolle für bestimmte größere Pipeline-Schritte konnten nicht über die gesamte Benutzeroberfläche konsistent heruntergeladen werden.

* Bei der Validierung von Umgebungsnamen trat ein Fehler mit einer Verschiebung um den Wert eins auf.

* Auf der Seite „Umgebungen“ wurden manchmal Veröffentlichungs- und Dispatcher-Segmente angezeigt, wenn keine vorhanden waren.

