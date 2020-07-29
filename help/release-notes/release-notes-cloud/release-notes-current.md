---
title: Versionshinweise für Adobe Experience Manager as a Cloud Service 2020.7.0
description: Versionshinweise für Experience Manager 2020.7.0
translation-type: tm+mt
source-git-commit: 9e27ff9510fda5ed238a25b2d63d1d9a3099a8b5
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 100%

---


# Versionshinweise für AEM as a Cloud Service 2020.7.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.7.0 beschrieben.

## Neue Funktionen in Cloud Manager {#cloud-manager}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für Cloud Manager in AEM as a Cloud Service Version 2020.7.0.

### Veröffentlichungsdatum {#release-date}

Die Version 2020.7.0 von [!UICONTROL Cloud Manager] wurde am 09. Juli 2020 veröffentlicht.

### Neuerungen {#what-is-new-cloud-manager}

* Die Seite „Umgebungen“ wurde neu gestaltet.

* Im Ruhezustand befindliche Umgebungen verfügen jetzt über einen separaten Status.

* Die Anzahl der Umgebungsvariablen pro Umgebung wurde auf 200 erhöht.

* Cloud Manager-Pipelines unterstützen jetzt benutzerspezifische Variablen und Geheimnisse.
Weitere Informationen finden Sie unter [Pipeline-Variablen](/help/onboarding/getting-access-to-aem-in-cloud/creating-aem-application-project.md#pipeline-variables).

### Fehlerbehebungen {#bug-fixes-cm}

* Die Verknüpfung von Cloud Manager mit der Developer Console war vor der vollständigen Erstellung der Umgebung nicht korrekt aktiviert.

* Die Verknüpfung zur Developer Console direkt aus Cloud Manager zeigte die Option zum Versetzen der Umgebung eines Sandbox-Programms in den Ruhezustand und zum Aufheben des Ruhezustands nicht an.

* Die Optionen **Abbrechen** und **Speichern** auf der Seite „Bearbeiten“ für produktionsfremde Pipelines waren nicht immer sichtbar.

* Bestimmte Fehler im Code-Qualitätsprozess konnten dazu führen, dass die Protokolldatei nicht korrekt erzeugt wurde.

* Beim Erstellen eines neuen Programms gab der vorgeschlagene Name manchmal ein Duplikat eines vorhandenen Programmnamens zurück.

* Protokolle für bestimmte größere Pipeline-Schritte konnten nicht über die gesamte Benutzeroberfläche konsistent heruntergeladen werden.

* Bei der Validierung von Umgebungsnamen trat ein Fehler mit einer Verschiebung um den Wert eins auf.

* Auf der Seite „Umgebungen“ wurden manchmal Veröffentlichungs- und Dispatcher-Segmente angezeigt, wenn keine vorhanden waren.

### Bekannte Probleme {#known-issues}

* Aufgrund einer Änderung bei der Berechnung der Code-Abdeckung ist die erforderliche _Mindestversion_ des Jacoco-Plugins jetzt 0.7.5.201505241946 (veröffentlicht im Mai 2015). Kunden, die eine ältere Version verwenden, erhalten eine Fehlermeldung im Code-Qualitätsprozess.

## Neue Funktionen in Cloud Readiness Analyzer {#cloud-readiness-analyzer}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Cloud Readiness Analyzer Version 1.0.2.

### Fehlerbehebungen {#cra-bug-fixes}

* Frühere Versionen des CRA konnten nicht unter Adobe Experience Manager (AEM) 6.1 ausgeführt werden. Es wurde expliziter Support hinzugefügt, um Benutzer für die Administratorgruppe zuzulassen.

   Weitere Informationen finden Sie unter [Installieren von CRA unter AEM 6.1](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html#installing-on-aem61) .

* Der im Zusammenfassungsbericht angezeigte Ablaufzeitstempel war nicht korrekt.

* CRA erkannte doppelt vorhandene benutzerdefinierte Komponenten.

* Bei AEM 6.1 wurde die Inhaltsüberprüfung beendet, bevor die vollständige Überprüfung abgeschlossen wurde. Die Ausnahmebehandlung wurde hinzugefügt, damit der Inspektor die Prüfung überspringen und fortsetzen kann, bis die vollständige Überprüfung abgeschlossen ist.

