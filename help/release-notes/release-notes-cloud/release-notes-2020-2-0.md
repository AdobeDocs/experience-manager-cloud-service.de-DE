---
title: Versionshinweise für Version 2020.2.0
description: Versionshinweise für Version 2020.2.0
translation-type: tm+mt
source-git-commit: e9514d2ba625a7df8a8126f5b0ab74b975eeda51

---


# Versionshinweise für AEM als Cloud-Dienst 2020.2.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager als Cloud Service 2020.2.0 beschrieben.

## Cloud Manager {#cloud-manager}

Das Veröffentlichungsdatum für Cloud Manager Version 2020.2.0 ist der 13. Februar 2020.

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