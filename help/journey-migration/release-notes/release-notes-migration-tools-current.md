---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.7.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.7.0
feature: Release Information
source-git-commit: f84327096951772e1bed8656334841e1292d6bcf
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 28%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.7.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.7.0.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Die Version 2.0.12 des Content Transfer Tool wurde am 19. Juli 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Benutzer, die über LDAP angemeldet sind, können jetzt die Funktionen &quot;Check Size&quot;und &quot;User Mapping&quot;in CTT ausführen.
* Um beim Debugging von SSL-/TLS-Verbindungsproblemen während der Extraktion zu helfen, können Benutzer jetzt die SSL-Protokollierung aktivieren.
* Um Probleme mit der Quellverbindung zu beheben, werden nun Subdomänennamen in den Protokollen gedruckt, wenn die Verbindung zu Azure fehlschlägt.
* Um Probleme während der Vorkopie zu beheben, werden AzCopy-Protokolle jetzt an die Extraktionslogs angehängt, wenn die Vorkopie fehlschlägt.
* Um veraltete Ergebnisse der Prüfung der Größe zu vermeiden, können Benutzer erst nach Abschluss einer vorherigen Prüfung der Größe die Funktion &quot;Prüfgröße&quot;erneut ausführen.

### Fehlerbehebungen {#bug-fixes-ctt}

* Frühere Extraktionsprotokolle wurden nach dem Löschen und erneuten Erstellen eines Migrationssatzes angezeigt. Dieses Problem wurde behoben.
* Die Schaltfläche Fortschritt anzeigen war nicht für Migrationssätze mit STOPPED-Status verfügbar. Dieses Problem wurde behoben.
* Die Schaltfläche Aktion löschen war nicht für Migrationssätze mit abgelaufenem Extraktionsschlüssel verfügbar. Dieses Problem wurde behoben.
* Mehrere Fehler in der Benutzeroberfläche wurden behoben.

## Cloud Acceleration Manager {#cam-release}

### Veröffentlichungsdatum {#release-date-cam}

Das Veröffentlichungsdatum für Cloud Acceleration Manager war der 15. Juli 2022.

### Neue Funktionen {#what-is-new-cam}

* Cloud Acceleration Manager bietet Benutzern jetzt die Möglichkeit, das Migrationstoken manuell abzurufen, um eine Erfassung starten zu können, wenn der automatische Abruf fehlschlägt. Der automatische Abruf kann fehlschlagen, wenn Kunden eine IP-Zulassungsliste eingerichtet haben, die CAM blockiert, oder wenn ein Benutzer ohne Administratorrechte versucht, eine Aufnahme zu starten. Siehe [Fehlerbehebung](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#troubleshooting) für weitere Informationen.
* Lange Tabellen auf der Seite &quot;Migrationskomplexität&quot;sind jetzt zur einfachen Verwendung ausgeblendet.

