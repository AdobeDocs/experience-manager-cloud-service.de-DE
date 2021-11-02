---
title: Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2021.10.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.10.0
feature: Release Information
exl-id: null
source-git-commit: c7cee58a465887b15994a963448fcba8d546673a
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 15%

---


# Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2021.10.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für die Migrationswerkzeuge in AEM as a Cloud Service Version 2021.10.0.

>[!NOTE]
>Klicken Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de), um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Die Version 1.6.0 des Content Transfer Tool wurde am 4. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt-oct}

* Verbessertes Tool für die Benutzerzuordnung mit einem vereinfachten Benutzererlebnis, einschließlich der folgenden unten aufgeführten Funktionen. Weitere Informationen finden Sie unter [Verwenden des Benutzerzuordnungs-Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html).
   * Testen Sie die Verbindung zur User Management-API, bevor Sie die Benutzerzuordnung ausführen.
   * Fehler lassen und mit der Aktivität Benutzerzuordnung fortfahren
   * Die Benutzerzuordnung schlägt nicht mehr fehl, wenn **Zugriffstoken** läuft nach 24 Stunden ab. Die Benutzerzuordnung kann an der Stelle erneut ausgeführt werden, an der sie zuletzt angehalten wurde.

* Um die Stabilität des Content Transfer Tool zu erhöhen, können Inhalte gleichzeitig in die Autoren- oder Veröffentlichungsinstanz aufgenommen werden. Siehe [Erste Schritte mit dem Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) für weitere Details.

* Wenn Versionen enthalten sind, wird der Pfad `/var/audit` wird automatisch einbezogen, um Prüfereignisse zu migrieren.


## Cloud Acceleration Manager {#cam-release}

### Veröffentlichungsdatum {#release-date-cam}

Die Cloud Acceleration Manager-Version wurde am 25. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cam}

Cloud Acceleration Manager bietet Benutzern jetzt die Möglichkeit, historische BPA-Berichte in einem Trendzeilenbericht anzuzeigen. Mit diesem Bericht können Benutzer die erzielten Fortschritte in einer einfach zu nutzenden grafischen Darstellung anzeigen. Siehe [Verwenden der Trendlinie anzeigen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#trendline-view-cam) für weitere Details.

### Veröffentlichungsdatum {#release-date-october-cam}

Die Cloud Acceleration Manager-Version wurde am 4. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cam-oct}

Cloud Acceleration Manager bietet Benutzern jetzt die Möglichkeit, die BPA-Berichte in einer druckbaren Vorschau anzuzeigen, sodass sie zur einfachen Freigabe einfach drucken oder auf PDF drucken können. Siehe Schritt 6 und 7 unter [Verwenden der Analyse-Karte mit Best Practices](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#best-practices-analysis).

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa-latest}

Die Version 2.1.20 von Best Practices Analyzer wurde am 5. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa-oct}

* Möglichkeit, die Länge von Knotennamen zu erkennen und darüber zu berichten.

* Möglichkeit, die Gesamtgröße des Index zu erkennen und darüber zu berichten.

* Möglichkeit zur Erkennung und Berichterstellung von Assets, denen die ursprüngliche Ausgabedarstellung fehlt.