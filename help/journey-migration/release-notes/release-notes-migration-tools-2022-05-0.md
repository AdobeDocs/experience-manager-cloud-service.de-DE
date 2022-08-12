---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.5.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.5.0
feature: Release Information
source-git-commit: 6196f3fc67dbcfe03a71bb6a0796dd5d1d0f8546
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 90%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.5.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.5.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.30 wurde am 1. Juni 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Die Möglichkeit, die Verwendung von Widgets für benutzerdefinierte Dialogfelder mithilfe von CoralUI- und Classic-Dialogfeldwidgets zu erkennen und darüber zu berichten. Es wird empfohlen, benutzerdefinierte Widgets für Classic-Dialogfelder von ExtJS in CoralUI zu konvertieren. Benutzerdefinierte Coral Dialog-Widgets sollten auf CoralUI3 aktualisiert werden.
* Die Möglichkeit, Nutzung und Version von Assets Share Commons zu erkennen und darüber zu berichten. Asset Share Commons 1.x wird in AEM as a Cloud Service nicht unterstützt und muss ein Upgrade auf 2.x erhalten.
* Die Möglichkeit, die Anzahl der Knoten aus Versionen zu erkennen und darüber zu berichten.
* Die Möglichkeit, benutzerdefinierte Replikationsagenten oder modifizierte vorkonfigurierte Replikationsagenten zu erkennen und darüber zu berichten.

### Fehlerbehebungen {#bug-fixes-bpa}

* BPA meldete NCC (Non-compatible changes, nicht kompatible Änderungen), UMI (Upgrade Misconfiguration Issue, Problem mit Upgrade-Fehlkonfiguration) und PCX (Page Complexity, Seitenkomplexität), bei denen es sich um falsch positive Ergebnisse handelte. Dies wurden behoben.
* BPA meldete Fehler, wenn die Länge eines Knotennamens 150 Byte überschritt. Dies wurde behoben, sodass solche Fehler nur noch erkannt werden, wenn der übergeordnete Pfad des Knotens gleich oder größer als 350 Byte ist.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 2.0.10 wurde am 2. Juni 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Das Content Transfer Tool (CTT) wurde entwickelt, um mit Cloud Acceleration Manager zusammenzuarbeiten und den gesamten Prozess des Inhaltstransfers zu optimieren. CTT konzentriert sich nun auf die Durchführung von Inhaltsextraktionen. Der CTT-Aufnahme-Service ist jetzt in Cloud Acceleration Manager integriert. Die Vorteile dieser Weiterentwicklung sind:
   * Self-Service-Methode, um einen Migrationssatz einmal zu extrahieren und ihn parallel in mehrere Umgebungen aufzunehmen.
   * Verbessertes Benutzererlebnis durch bessere Ladezustände, Leitlinien und Fehlerbehandlung.
   * Aufnahmeprotokolle bleiben erhalten und stehen immer zur Fehlerbehebung zur Verfügung.

## Cloud Acceleration Manager {#cam-release}

### Veröffentlichungsdatum {#release-date-cam}

Das Veröffentlichungsdatum für Cloud Acceleration Manager war der 2. Juni 2022.

### Neue Funktionen {#what-is-new-cam}

* Cloud Acceleration Manager bietet Benutzern jetzt die Möglichkeit, Inhaltstransfers zu starten und zu verwalten, um Inhalte von der AEM einer Kundeninstanz (On-Premise oder Adobe Managed Services) in AEM as a Cloud Service Teil eines Migrationsprojekts zu verschieben. Weitere Informationen finden Sie unter [Verwenden der Content Transfer Card](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-implementation-phase.html?lang=de#content-transfer).
