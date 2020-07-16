---
title: Versionshinweise für Adobe Experience Manager as a Cloud Service 2020.7.0
description: Versionshinweise für Experience Manager 2020.7.0
translation-type: tm+mt
source-git-commit: 610e00a8669a7d81482d99685d200bd705b1848f
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 31%

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

* Die Anzahl der Umgebung pro Umgebung wurde auf 200 erhöht.

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

### Bekannte Probleme {#known-issues}

* Aufgrund einer Änderung bei der Berechnung der Codeabdeckung ist die _Mindestversion_ des Jacoco-Plugins jetzt 0.7.5.201505241946 (veröffentlicht im Mai 2015). Kunden, die explizit auf eine ältere Version verweisen, erhalten eine Fehlermeldung im Code-Qualitätsprozess.

## Neue Funktionen in Cloud-Bereitstellungsanalysator {#cloud-readiness-analyzer}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Cloud Readiness Analyzer Version 1.0.2.

### Fehlerbehebungen {#cra-bug-fixes}

* Frühere Versionen der CRA konnten nicht auf Adobe Experience Manager (AEM) 6.1 ausgeführt werden. Es wurde eine explizite Unterstützung hinzugefügt, um Benutzern in der Administratorgruppe zuzulassen.

   Weitere Informationen finden Sie unter [Installieren von CRA auf AEM 6.1](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html#installing-on-aem61) .

* Der im Zusammenfassungsbericht angezeigte Ablaufzeitstempel war nicht korrekt.

* CRA erkannte benutzerdefinierte Duplikat-Komponenten.

* Bei AEM 6.1 wurde die Inhaltsüberprüfung beendet, bevor die vollständige Überprüfung abgeschlossen wurde. Die Ausnahmebehandlung wurde hinzugefügt, damit der Inspektor die Prüfung überspringen und fortsetzen kann, bis die vollständige Überprüfung abgeschlossen ist.

