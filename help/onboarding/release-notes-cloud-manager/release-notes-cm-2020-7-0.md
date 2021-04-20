---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.7.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.7.0
feature: Release Information
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.7.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.7.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.7.0 von Cloud Manager in AEM as a Cloud Service wurde am 9. Juli 2020 veröffentlicht.

## Neue Funktionen {#whats-new-cloud-manager}

* Die Seite „Umgebungen“ wurde neu gestaltet.

* Im Ruhezustand befindliche Umgebungen verfügen jetzt über einen separaten Status.

* Die Anzahl der Umgebungsvariablen pro Umgebung wurde auf 200 erhöht.

* Cloud Manager-Pipelines unterstützen jetzt anwenderspezifische Variablen und Geheimnisse.

   Weitere Informationen finden Sie unter [Pipeline-Variablen](/help/onboarding/getting-access-to-aem-in-cloud/build-environment-details.md#pipeline-variables).

* Authentifizierungsgebundene Private Maven-Repositorys werden jetzt unterstützt.

* Der Cloud Manager-Build-Container unterstützt jetzt sowohl Java 8 als auch Java 11.
Weitere Informationen finden Sie unter [Java 11-Unterstützung verwenden](/help/onboarding/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support).

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

* Aufgrund einer Änderung bei der Berechnung der Code-Abdeckung ist die erforderliche *Mindestversion* des Jacoco-Plugins jetzt 0.7.5.201505241946 (veröffentlicht im Mai 2015). Kunden, die eine ältere Version verwenden, erhalten eine Fehlermeldung im Code-Qualitätsprozess.