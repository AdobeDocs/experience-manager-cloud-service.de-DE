---
title: Einschränkungen beim Rückgängigmachen und Wiederherstellen
description: Erfahren Sie mehr über die Einschränkungen der Optionen "Rückgängig"und "Wiederholen"im AEM Seiteneditor.
source-git-commit: bbd845079cb688dc3e62e2cf6b1a63c49a92f6b4
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 92%

---


# Einschränkungen beim Rückgängigmachen und Wiederherstellen {#undo-redo}

AEM speichert einen Verlauf der Aktionen, die Sie ausführen, sowie die Reihenfolge der Ausführung. Sie können also mehrere Aktionen in der umgekehrten Reihenfolge ihrer Ausführung rückgängig machen und bei Bedarf die Aktionen wiederholen, wenn Sie eine oder mehrere davon erneut anwenden möchten.

Wenn ein Element auf der Inhaltsseite ausgewählt wird, gelten die Befehle „Rückgängig“ und „Wiederholen“ für das ausgewählte Element, also z. B. für eine Textkomponente.

Das Verhalten der Befehle „Rückgängig“ und „Wiederholen“ ähnelt dem in anderer Software. Verwenden Sie die Befehle zum Wiederherstellen des aktuellen Status Ihrer Web-Seite, wenn Sie Entscheidungen über Inhalte treffen. Wenn Sie beispielsweise einen Textabsatz an eine Stelle auf der Seite verschoben haben, können Sie ihn mithilfe des Befehls zum Rückgängigmachen wieder zurück an die ursprüngliche Stelle verschieben. Falls Sie dann entscheiden, dass die vorherige Position besser war, verwenden Sie den Befehl „Wiederherstellen“, um „das Rückgängigmachen rückgängig zu machen“.

Sie können beispielsweise:

* Sie können Aktionen wiederholen, solange Sie seit der Verwendung von „Rückgängig machen“ keine Seitenbearbeitungen durchgeführt haben.
* Sie können maximal 20 Bearbeitungsaktionen rückgängig machen (Standardeinstellung).
* Sie können zum Rückgängigmachen und Wiederholen auch [Tastaturbefehle](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md) verwenden.

Sie können die folgenden Arten von Seitenänderungen rückgängig machen und wiederherstellen:

* Hinzufügen, Bearbeiten, Entfernen und Verschieben von Absätzen
* Bearbeitung von Absatzinhalten im Kontext
* Kopieren, Ausschneiden und Einfügen von Elementen auf einer Seite

>[!NOTE]
>
>* Spezielle Berechtigungen sind erforderlich, um Änderungen rückgängig zu machen bzw. wiederherzustellen, die an Dateien und Bildern vorgenommen wurden.
>* Änderungen an Dateien und Bildern können für einen Verlauf von mindestens zehn Stunden rückgängig gemacht werden. Bei länger zurückliegenden Änderungen ist dies unter Umständen nicht mehr möglich. Ihre Admins können die Standardzeit von zehn Stunden ändern.
>* Ihr Systemadministrator kann verschiedene Aspekte der Funktionen „Rückgängig“ und „Wiederholen“ den Anforderungen Ihrer Instanz entsprechend konfigurieren.
