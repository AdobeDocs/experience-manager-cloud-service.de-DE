---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.11.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.11.0
feature: Release Information
exl-id: null
source-git-commit: ec2719fca19f366e0021fea7429e93c15e9579df
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 20%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.11.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.11.0.

>[!NOTE]
>Klicken Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de), um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.11.0 von Cloud Manager in AEM as a Cloud Service wurde am 04. November 2021 veröffentlicht.
Die nächste Version ist für den 16. Dezember 2021 geplant.

### Neue Funktionen {#what-is-new}

* Benutzer können jetzt neue Front-End-Pipelines nutzen, um Frontend-Code exklusiv schneller bereitzustellen. Siehe [Cloud Manager-Frontend-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) , um mehr zu erfahren.

   >[!IMPORTANT]
   >Sie müssen AEM Version verwenden `2021.10.5933.20211012T154732Z` , um neue Front-End-Pipelines zu nutzen.

* Die Dauer der Code-Qualitäts-Pipeline wird erheblich reduziert, indem die Codeanalyse effizienter durchgeführt wird, ohne dass ein ganzes AEM Bild erstellt werden muss. Diese Änderung wird in den Wochen nach der Veröffentlichung schrittweise eingeführt.

* Die Git-Zusage-ID wird jetzt in den Details zur Pipeline-Ausführung angezeigt, was die Verfolgung des erstellten Codes erleichtert.

* Die Erstellung von Programmen ist jetzt über öffentlich zugängliche APIs verfügbar.

* Die Erstellung von Umgebungen ist jetzt über öffentlich zugängliche APIs verfügbar.

* Die `x-request-id` Die Antwort-Kopfzeile ist jetzt in der API-Wiedergabe auf [www.adobe.io](https://www.adobe.io/). Diese Kopfzeile ist beim Senden von Problemen bei der Kundenunterstützung zur Fehlerbehebung nützlich.

* Als Benutzer sehe ich die Pipeline-Karte mit Null-Pipelines, die mir eine entsprechende Anleitung bietet.

* Eine neue Aktivitätsseite ist jetzt verfügbar, auf der Aktivitäten wie Pipeline- und Codeausführungen zusammen mit den zugehörigen Details angezeigt werden können. Im Laufe der Zeit werden die auf dieser Seite aufgelisteten Aktivitäten zusammen mit den angegebenen Details erweitert.

* Eine neue Pipelines-Seite mit einem On-Hover-Status-Popup für einen einfachen Überblick über die Zusammenfassung der Details ist jetzt verfügbar. Pipeline-Ausführungen können zusammen mit den zugehörigen Details angezeigt werden.

* Die API &quot;Pipeline bearbeiten&quot;unterstützt jetzt das Ändern der in den Bereitstellungsphasen verwendeten Umgebung.

* Für große Packages wurde eine Optimierung des OakPal-Scanprozesses eingeführt.

* Die CSV-Datei mit dem Qualitätsproblem enthält jetzt den Zeitstempel für jedes Qualitätsproblem.

### Fehlerbehebungen {#bug-fixes}

* Bestimmte unorthodoxe Build-Konfigurationen führten dazu, dass unnötige Dateien im Maven-Artefakt-Cache der Pipeline gespeichert wurden, was beim Starten und Beenden des Build-Containers zu irrelevanten Netzwerk-I/O führte.

* Die Pipeline-PATCH-API schlägt fehl, wenn die Bereitstellungsphase nicht vorhanden ist.

* Die `ClientlibProxyResourceCheck` Qualitätsregel verursachte falsch positive Probleme, wenn es Client-Bibliotheken mit gemeinsamen Basispfaden gab.

* Die Fehlermeldung, wenn die maximale Anzahl von Repositorys erreicht wurde, hat den Grund für den Fehler nicht angegeben.

* In seltenen Fällen schlugen Pipelines aufgrund einer unangemessenen Wiederholungsverarbeitung bestimmter Antwort-Codes fehl.

