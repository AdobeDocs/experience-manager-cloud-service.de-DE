---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2021.10.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2021.11.0
feature: Release Information
exl-id: 6b1caa63-dcb0-4c48-ab2c-fd72617abf13
role: Admin
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 100%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2021.10.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2021.10.0.

>[!NOTE]
>
>Die neuesten Versionshinweise finden Sie unter [Aktuelle Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Cloud Acceleration Manager {#cam-release}

### Veröffentlichungsdatum {#release-date-cam}

Das Veröffentlichungsdatum für Cloud Acceleration Manager war der 25. Oktober 2021.

### Neue Funktionen {#what-is-new-cam}

Cloud Acceleration Manager bietet Benutzern jetzt die Möglichkeit, bisherige BPA-Berichte in einem Trend-Linienbericht anzuzeigen. Mit diesem Bericht können Benutzer ihre Fortschritte in einer einfach zu nutzenden grafischen Darstellung anzeigen. Weitere Informationen dazu finden Sie unter [Verwenden von „Trend-Linie anzeigen“](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=de#trendline-view-cam).

### Veröffentlichungsdatum {#release-date-october-cam}

Das Veröffentlichungsdatum für Cloud Acceleration Manager war der 4. Oktober 2021.

### Neue Funktionen {#what-is-new-cam-oct}

Cloud Acceleration Manager bietet den Nutzern jetzt die Möglichkeit, die BPA-Berichte in einer Druckvorschau zu betrachten, so dass sie einfach ausgedruckt oder als PDF gedruckt werden können, um sie leicht weitergeben zu können. Siehe Schritt 6 und 7 in [Verwenden der Best-Practices-Analyse-Karte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=de#best-practices-analysis).


## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Die Version 1.6.0 von Content Transfer Tool wurde am 4. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt-oct}

* Verbessertes Tool für die Benutzerzuordnung mit einem vereinfachten Benutzererlebnis, einschließlich der folgenden unten aufgeführten Funktionen. Weitere Informationen finden Sie unter [Verwenden des Tools für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html?lang=de).
   * Testen der Verbindung zur User Management-API, bevor die Benutzerzuordnung ausgeführt wird
   * Fehler elegant überspringen und mit der Aktivität Benutzerzuordnung fortfahren
   * Die Benutzerzuordnung schlägt nicht mehr fehl, wenn das **Zugriffstoken** nach 24 Stunden abläuft. Die Benutzerzuordnung kann an der Stelle erneut ausgeführt werden, an der sie zuletzt angehalten wurde.

* Um die Stabilität des Content Transfer Tool zu erhöhen, können Inhalte gleichzeitig in die Autoren- oder Veröffentlichungsinstanz aufgenommen werden. Weitere Informationen finden Sie unter [Erste Schritte mit dem Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de).

* Wenn Versionen enthalten sind, wird der Pfad `/var/audit` automatisch einbezogen, um Prüfereignisse zu migrieren.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa-latest}

Best Practices Analyzer 2.1.20 wurde am 5. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa-oct}

* Möglichkeit, die Länge von Knotennamen zu erkennen und darüber zu berichten.

* Möglichkeit, die Gesamtgröße des Index zu erkennen und darüber zu berichten.

* Möglichkeit, Assets zu erkennen, denen die ursprüngliche Ausgabedarstellung fehlt und darüber zu berichten.
