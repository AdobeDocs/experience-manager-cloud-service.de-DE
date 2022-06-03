---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.5.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.5.0
feature: Release Information
source-git-commit: 48dd6b3184cdde06b902eae35fac42515f606e77
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 23%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.5.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.5.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.30 wurde am 1. Juni 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Möglichkeit, die Verwendung von Widgets für benutzerdefinierte Dialogfelder mithilfe von CoralUI- und Classic-Dialogfeldwidgets zu erkennen und darüber zu berichten. Es wird empfohlen, benutzerdefinierte Widgets für klassische Dialogfelder von ExtJS in CoralUI zu konvertieren. Benutzerdefinierte Coral Dialog Widgets sollten auf CoralUI3 aktualisiert werden.
* Möglichkeit, Nutzung und Version von Assets Share Commons zu erkennen und darüber zu berichten. Asset Share Commons 1.x wird auf AEM as a Cloud Service nicht unterstützt und muss auf 2.x aktualisiert werden.
* Möglichkeit, die Anzahl der Knoten aus Versionen zu erkennen und darüber zu berichten.
* Möglichkeit zur Erkennung und Berichterstellung von benutzerdefinierten Replikationsagenten oder vordefinierten Replikationsagenten, die geändert wurden.

### Fehlerbehebungen {#bug-fixes-bpa}

* BPA meldete NCC (nicht kompatible Änderungen), UMI (Upgrade Misconfiguration Issue) und PCX (Page Complexity) Ergebnisse, die falsch-positive Ergebnisse sind. Diese wurden behoben.
* BPA meldete Fehler, wenn die Länge eines Knotennamens 150 Byte überschreitete. Dieser Fehler wurde behoben, um solche Fehler nur zu erkennen, wenn der übergeordnete Pfad des Knotens mindestens 350 Byte beträgt.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 2.0.10 wurde am 2. Juni 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Das Content Transfer Tool (CTT) wurde entwickelt, um mit Cloud Acceleration Manager zusammenzuarbeiten und den gesamten Inhaltstransfer zu optimieren. CTT konzentriert sich nun auf die Durchführung von Inhaltsextraktionen. Der CTT-Erfassungsdienst ist jetzt in Cloud Acceleration Manager integriert. Die Vorteile dieser Entwicklung sind:
   * Self-Service-Methode, um einen Migrationssatz einmal zu extrahieren und ihn parallel in mehrere Umgebungen aufzunehmen.
   * Verbessertes Benutzererlebnis durch bessere Ladezustände, Limits und Fehlerbehandlung.
   * Aufnahmeprotokolle bleiben erhalten und stehen immer zur Fehlerbehebung zur Verfügung.

## Cloud Acceleration Manager {#cam-release}

### Veröffentlichungsdatum {#release-date-cam}

Die Cloud Acceleration Manager-Version wurde am 2. Juni 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-cam}

* Cloud Acceleration Manager bietet Benutzern jetzt die Möglichkeit, Inhaltstransfers zu starten und zu verwalten, um Inhalte von der AEM einer Kundeninstanz (On-Premise oder Adobe Managed Services) in AEM as a Cloud Service Teil eines Migrationsprojekts zu verschieben. Siehe [Verwenden der Content Transfer Card](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-implementation-phase.html#content-transfer) für weitere Details.
