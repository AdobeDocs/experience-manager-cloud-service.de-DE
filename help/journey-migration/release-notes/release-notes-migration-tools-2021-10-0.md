---
title: Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2021.10.0
description: Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2021.11.0
feature: Release Information
exl-id: 6b1caa63-dcb0-4c48-ab2c-fd72617abf13
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 71%

---

# Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2021.10.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für die Migrationswerkzeuge in AEM as a Cloud Service Version 2021.10.0.

>[!NOTE]
>Klicken Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de), um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen.

## Cloud Acceleration Manager {#cam-release}

### Veröffentlichungsdatum {#release-date-cam}

Die Cloud Acceleration Manager-Version wurde am 25. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cam}

Cloud Acceleration Manager bietet Benutzern jetzt die Möglichkeit, historische BPA-Berichte in einem Trendzeilenbericht anzuzeigen. Mit diesem Bericht können Benutzer die erzielten Fortschritte in einer einfach zu nutzenden grafischen Darstellung anzeigen. Siehe [Verwenden der Trendlinie anzeigen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#trendline-view-cam) für weitere Details.

### Veröffentlichungsdatum {#release-date-october-cam}

Das Veröffentlichungsdatum für Cloud Acceleration Manager war der 4. Oktober 2021.

### Neue Funktionen {#what-is-new-cam-oct}

Cloud Acceleration Manager bietet den Nutzern jetzt die Möglichkeit, die BPA-Berichte in einer Druckvorschau zu betrachten, so dass sie einfach ausgedruckt oder als PDF gedruckt werden können, um sie leicht weitergeben zu können. Siehe Schritt 6 und 7 in [Verwenden der Best-Practices-Analyse-Karte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#best-practices-analysis).


## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Die Version 1.6.0 von Content Transfer Tool wurde am 4. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt-oct}

* Verbessertes Tool für die Benutzerzuordnung mit einem vereinfachten Benutzererlebnis, einschließlich der folgenden unten aufgeführten Funktionen. Weitere Informationen finden Sie unter [Verwenden des Tools für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html?lang=de).
   * Testen der Verbindung zur User Management-API, bevor die Benutzerzuordnung ausgeführt wird
   * Fehler elegant überspringen und mit der Aktivität Benutzerzuordnung fortfahren
   * Die Benutzerzuordnung schlägt nicht mehr fehl, wenn das **Zugriffstoken** nach 24 Stunden abläuft. Die Benutzerzuordnung kann an der Stelle erneut ausgeführt werden, an der sie zuletzt angehalten wurde.

* Um die Stabilität des Content Transfer Tool zu erhöhen, können Inhalte gleichzeitig in die Autoren- oder Veröffentlichungsinstanz aufgenommen werden. Weitere Informationen finden Sie unter [Erste Schritte mit dem Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de).

* Wenn Versionen enthalten sind, wird der Pfad `/var/audit` automatisch einbezogen, um Prüfereignisse zu migrieren.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa-latest}

Best Practices Analyzer 2.1.20 wurde am 5. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa-oct}

* Möglichkeit, die Länge von Knotennamen zu erkennen und darüber zu berichten.

* Möglichkeit, die Gesamtgröße des Index zu erkennen und darüber zu berichten.

* Möglichkeit, Assets zu erkennen, denen die ursprüngliche Ausgabedarstellung fehlt und darüber zu berichten.
