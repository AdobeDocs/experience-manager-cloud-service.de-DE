---
title: Versionshinweise für Adobe Experience Manager as a Cloud Service 2020.7.0
description: Versionshinweise für Experience Manager 2020.7.0
translation-type: tm+mt
source-git-commit: 74abf1c4cc6ae449a81e3e40d073bfcb23b056e8
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 51%

---


# Versionshinweise für AEM as a Cloud Service 2020.7.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.7.0 beschrieben.

## Neue Funktionen in Cloud Manager {#cloud-manager}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für Cloud Manager in Version 2020.7.0 von AEM as a Cloud Service.

### Veröffentlichungsdatum {#release-date}

Die Version 2020.7.0 von [!UICONTROL Cloud Manager] wurde am 09. Juli 2020 veröffentlicht.

### Neuerungen {#what-is-new-cloud-manager}

* Die Seite &quot;Umgebung&quot;wurde neu gestaltet.

* Bei ausgeblendeten Umgebung wird nun ein eigenständiger Status in Cloud Manager angezeigt, wenn sie ausgeblendet werden.

* Der Cloud Manager-Build-Container unterstützt jetzt sowohl Java 8 als auch Java 11.

### Fehlerbehebungen {#bug-fixes-cm}

* Die Verknüpfung von Cloud Manager mit der Developer Console war vor der vollständigen Erstellung der Umgebung nicht korrekt aktiviert.

* Der Link zur Developer Console direkt aus Cloud Manager zeigte keine Option zum Deaktivieren/Entfernen der Umgebung eines Sandbox-Programms an.

* The **Cancel** and **Save** options on the Non-Production Pipeline edit page were not always visible.

* Bestimmte Fehler im Code-Qualitätsprozess konnten dazu führen, dass die Protokolldatei nicht korrekt erzeugt wurde.

* Beim Erstellen eines neuen Programms gibt der vorgeschlagene Name manchmal ein Duplikat eines vorhandenen Programms zurück.

* Protokolle für bestimmte größere Pipeline-Schritte konnten nicht über die gesamte Benutzeroberfläche konsistent heruntergeladen werden.

* Bei der Validierung von Umgebung ist ein Fehler aufgetreten.

* Auf der Seite &quot;Umgebung&quot;werden manchmal Veröffentlichungs- und Dispatcher-Segmente angezeigt, wenn keine vorhanden war.