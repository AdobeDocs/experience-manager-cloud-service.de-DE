---
title: Versionshinweise für Version 2020.2.0
description: Versionshinweise für Version 2020.2.0
translation-type: tm+mt
source-git-commit: 157809fb4aacf45358db6412dea04398a7f12495

---


# Versionshinweise für AEM als Cloud-Dienst 2020.2.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager als Cloud Service 2020.2.0 beschrieben.

Das Veröffentlichungsdatum ist der 13. Februar 2020.

## Cloud Manager {#cloud-manager}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Cloud Manager Release 2020.2.0.

### Neuerungen {#what-is-new}

* Die Archetypversion von Adobe Experience Manager wurde auf Version 22 aktualisiert.
* Die Stage- und Produktionsumgebungen in den Sandbox-/Demo-Programmen können jetzt über die Benutzeroberfläche von Cloud Manager aktualisiert werden.
* Die in Experience Cloud-Benachrichtigungen verwendeten URLs wurden optimiert, um eine zusätzliche Umleitung zu vermeiden.
* Schritte zur Pipeline-Ausführung, bei denen eine Zeitüberschreitung aufgetreten ist, geben dies jetzt explizit an.
* Der Schritt zur Code-Prüfung enthält jetzt ein herunterladbares Protokoll.
* Die Tabelle mit den während der Codeprüfung entdeckten Problemen enthält jetzt eine Spalte mit einem Link zur Dokumentation der jeweiligen Regel.

### Fehlerbehebungen  {#bug-fixes}

* Sicherheitsrichtlinien des Browsers verhindern manchmal, dass bestimmte Schaltflächen im Bildschirm zur Ausführung der Pipeline ordnungsgemäß funktionieren.
* Die Links Überblick, Umgebungen und Aktivität waren manchmal auf der Einstiegsseite von Cloud Manager verfügbar.
* Bestimmte Fehler bei der Bereitstellung könnten die Erstellung neuer Pipelines fälschlicherweise verhindern.