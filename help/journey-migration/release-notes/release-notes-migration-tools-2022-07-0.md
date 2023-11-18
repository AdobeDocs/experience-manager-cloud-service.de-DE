---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.7.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.7.0
feature: Release Information
exl-id: bc8f1a80-867e-423a-9c03-4a53b1ebc57c
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 93%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.7.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.7.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer v2.1.30 wurde am 27. Juli 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* BPA kann jetzt die migrierbare Gesamtgröße des Lucene-Index ermitteln und in Berichten angeben. Diese entspricht der Gesamtgröße des Lucene-Index ohne `/oak:index/lucene` und `/oak:index/damAssetLucene`.
* In BPA wurde ein neues Muster hinzugefügt, um die Verwendung benutzerdefinierter i18n-Wörterbücher zu erkennen und in Berichten zu erfassen. Translator.html ist nicht in AEM as a Cloud Service und benutzerdefinierten i18n-Wörterbuch verfügbar, das über die CI/CD-Pipeline von Cloud Manager aus bereitgestellt werden muss.

### Fehlerbehebungen {#bug-fixes-bpa}

* BPA meldete fehlende ursprüngliche Ausgabedarstellungen für Inhaltsfragmente. Da Inhaltsfragmente keine Ausgabedarstellungen aufweisen, wird diese Prüfung für Inhaltsfragmente jetzt übersprungen.
* In der BPA-Benutzeroberfläche fehlte die Option zum Filtern von ACS Commons-Ergebnissen. Dieses Problem wurde behoben.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 2.0.12 wurde am 19. Juli 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Benutzer, die über LDAP angemeldet sind, können in CTT jetzt die Funktionen „Größenprüfung“ und „Benutzerzuordnung“ ausführen.
* Benutzende können jetzt durch die Aktivierung der SSL-Protokollierung das Debugging bei SSL-/TLS-Verbindungsproblemen während der Extraktionen vereinfachen.
* Um Probleme mit der Quellverbindung zu beheben, werden nun Subdomain-Namen in den Protokollen angegeben, wenn die Verbindung zu Azure fehlschlägt.
* Um Probleme während der Vorkopie zu beheben, werden AzCopy-Protokolle jetzt an die Extraktionslogs angehängt, wenn die Vorkopie fehlschlägt.
* Um veraltete Größenprüfungsergebnisse zu vermeiden, können Benutzende erst dann eine neue Größenprüfung durchführen, wenn die vorherige abgeschlossen ist.

### Fehlerbehebungen {#bug-fixes-ctt}

* Frühere Extraktionsprotokolle wurden nach dem Löschen und erneuten Erstellen eines Migrationssatzes angezeigt. Dieses Problem wurde behoben.
* Die Schaltfläche „Fortschritt anzeigen“ war nicht für Migrationssätze mit dem Status STOPPED verfügbar. Dieses Problem wurde behoben.
* Die Schaltfläche „Aktion löschen“ war nicht für Migrationssätze mit abgelaufenem Extraktionsschlüssel verfügbar. Dieses Problem wurde behoben.
* Mehrere Fehler in der Benutzeroberfläche wurden behoben.

## Cloud Acceleration Manager {#cam-release}

### Veröffentlichungsdatum {#release-date-cam}

Das Veröffentlichungsdatum für Cloud Acceleration Manager war der 15. Juli 2022.

### Neue Funktionen {#what-is-new-cam}

* Cloud Acceleration Manager bietet Benutzenden jetzt die Möglichkeit, das Migrations-Token manuell abzurufen, um eine Aufnahme starten zu können, wenn der automatische Abruf fehlschlägt. Der automatische Abruf kann fehlschlagen, wenn Kunden eine IP-Zulassungsliste eingerichtet haben, die CAM blockiert, oder wenn Benutzende ohne Administratorrechte versuchen, eine Aufnahme zu starten. Weitere Informationen finden Sie unter [Fehlerbehebung](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#troubleshooting).
* Lange Tabellen auf der Seite „Migrationskomplexität“ können jetzt reduziert werden, um die Verwendung zu vereinfachen.
