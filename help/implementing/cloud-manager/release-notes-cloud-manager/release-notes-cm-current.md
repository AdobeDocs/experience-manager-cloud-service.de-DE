---
title: Versionshinweise für Cloud Manager 2023.1.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2024.1.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 5aabdf22a040a031a3fa2a1a9f70247cf2e38f2e
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 36%

---


# Versionshinweise für Cloud Manager 2023.1.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite werden die Versionshinweise für die Cloud Manager-Version 2023.1.0 AEM as a Cloud Service dokumentiert.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager -Version 2023.1.0 in AEM as a Cloud Service wurde am 19. Januar 2023 veröffentlicht. Die nächste Version soll am 16. Februar 2023 veröffentlicht werden.

## Neue Funktionen {#what-is-new}

* Verbesserungen der Benutzerfreundlichkeit wurden durch die Aktualisierung von Cursorstilen erreicht, die unterscheiden zwischen dem Ort, an dem Benutzer Aktionen ausführen können, und dem Standardzeiger.

* Die benutzerdefinierten UI-Testberichte werden jetzt in den Cloud Manager-Speicher kopiert und können über den Cloud Manager-API-Aufruf aufgerufen werden.

* Benutzer können nun mithilfe der Pfeile nach links und rechts zwischen den Status eines Go-Live-Widgets wechseln.

   ![Go-Live-Widget-Transitionen](assets/go-live-transitions.gif)

* Self-Service [Erstellung von HIPAA-fähigen Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) ist jetzt möglich, wenn entsprechende Berechtigungen verfügbar sind.

## Fehlerbehebungen {#bug-fixes}

* Cloud Manager verhindert, dass zwei Pipeline-Ausführungen gleichzeitig (oder nahezu gleichzeitig) beginnen, wodurch Pipelinefehler vermieden werden.
