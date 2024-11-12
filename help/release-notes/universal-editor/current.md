---
title: Universeller Editor 2024.11.12 – Versionshinweise
description: Dies sind die Versionshinweise für die Version 2024.11.12 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 03ccad00e689052ada8cca976d6c385be01d3cc9
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 12%

---


# Universeller Editor 2024.11.12 – Versionshinweise {#release-notes}

Dies sind die Versionshinweise für die Version des universellen Editors vom 12. November 2024.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* **Option zum Wiederholen der CORS-Zeitüberschreitung:** Mit der Version 2024.09.26, ](/help/release-notes/universal-editor/2024/2024-09-26.md) wurde ein Fehlerbedienfeld eingeführt, wenn der Editor keine Verbindung zur geladenen Seite herstellen konnte, wodurch endlose Ladezustände verhindert wurden.[
   * Mit dieser Version versucht der Editor automatisch das Wiederholen. Sobald die Verbindung hergestellt ist, kann die Bearbeitung fortgesetzt werden.
   * Dies ist besonders für Seiten nützlich, die länger als die einminütige Zeitüberschreitung dauern können, bis sie initialisiert werden.
* **Erweiterbarkeitsverbesserungen für Entwickler:** Der Universal Editor unterstützt jetzt das Senden von Ereignissen an Erweiterungen, sodass Erweiterungsentwickler [Ereignisse abonnieren können.](/help/implementing/universal-editor/events.md)
   * Dadurch können Entwickler [auf Editor-Ereignisse innerhalb ihrer benutzerdefinierten Erweiterungen reagieren.](/help/implementing/universal-editor/customizing.md#extending)
* **Persistente Komponentenauswahl:** Ausgewählte Komponenten im Editor bleiben jetzt auch nach der Aktualisierung des Browsers erhalten.
   * Dadurch wird sichergestellt, dass Benutzer ihre Arbeit fortsetzen können, ohne ihren Kontext beim Neuladen der Seite zu verlieren.
* **Lokalisierte Schnelllinks:** Der Abschnitt **Quick Links** auf dem Startbildschirm enthält jetzt lokalisierte Links zur Dokumentation, die Benutzern den einfachen Zugriff auf relevante Handbücher basierend auf ihren Spracheinstellungen ermöglichen.
* **Anforderungs-ID für erweitertes Debugging:** Fehlerbenachrichtigungen enthalten jetzt eine **Anforderungs-ID** im Detailabschnitt, die mit der `x-request-id header` korreliert.
   * Dies erleichtert es Adobe-Engineering-Teams, Probleme zu erkennen und zu diagnostizieren, indem sie diese Fehler mit internen Protokollen abgleichen.

## Weitere Verbesserungen {#other-improvements}

* **Korrektur der Beschriftungen der langen Inhaltsstruktur:** Behebung eines Problems, bei dem lange Beschriftungen im Bedienfeld **Inhaltsstruktur** abgeschnitten wurden
   * Dadurch wird sichergestellt, dass Drag &amp; Drop-Handles immer für die Neuanordnung von Inhalten sichtbar sind.
* **Beschriftungen für lange Eigenschaften behoben:** Es wurde ein Fehler behoben, durch den lange Feldbezeichnungen im Bedienfeld **Eigenschaften** mit Feldvalidierungsinformationen überlagert wurden.
* **Horizontaler Bildlauf im Eigenschaftenbedienfeld:** Es wurde ein Problem behoben, bei dem breite Elemente im Bedienfeld **Eigenschaften** einen horizontalen Bildlauf verursachten.
* **Inaktive Symbolleiste während Benachrichtigungen korrigiert:** Die obere Symbolleiste **Adobe Experience Cloud** funktioniert jetzt vollständig, wenn [toast](https://spectrum.adobe.com/page/toast/) -Benachrichtigungen angezeigt werden.
* **Verbesserte Stabilität:** Es wurden Fehlergrenzen hinzugefügt, mit denen unerwartete Werte verarbeitet werden können. Dadurch wird verhindert, dass die gesamte Benutzeroberfläche abstürzt, wenn ein einzelner Renderer oder Validator fehlschlägt, was die Stabilität verbessert.
