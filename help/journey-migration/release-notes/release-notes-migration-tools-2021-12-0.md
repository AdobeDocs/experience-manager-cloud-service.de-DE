---
title: Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2021.12.0
description: Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2021.12.0
feature: Release Information
exl-id: 4155e1c0-cd40-4cbc-9d6c-b106d68a2db5
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 19%

---

# Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2021.12.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für die Migrationswerkzeuge in AEM as a Cloud Service Version 2021.12.0.

>[!NOTE]
>Klicken Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de), um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Die Version 2.1.22 von Best Practices Analyzer wurde am Donnerstag, 1. Dezember 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Möglichkeit, die Version der verwendeten ACS-Commons zu erkennen und darüber zu berichten.
* Möglichkeit, die Anzahl der Benutzer und Untergruppen in einer Gruppe zu erkennen und darüber zu berichten.
* Möglichkeit zur Erkennung und Berichterstellung von Knoteneigenschaftswerten in MongoDB, die 16 MB überschreiten.

### Fehlerbehebungen {#bug-fixes-bpa}

* Die Erkennung von Foundation-Komponenten wurde optimiert, um falsche negative Werte zu reduzieren.
* Für AEM Forms-Kunden: BPA-Nachrichten zu `EMAIL_PDF_SUBMIT_ACTION` nicht verfügbar auf AEM as a Cloud Service wurde behoben.


## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Die Version 1.7.10 des Content Transfer Tool wurde am 8. Dezember 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Wechsel zur Aufnahmephase im Content Transfer Tool hinzugefügt, damit Benutzer die Option deaktivieren können [pre-copy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de) während der Aufnahme. Für optimale Aufnahmegeschwindigkeiten sollte die Vorkopie während der Aufnahme für kleine Migrationssätze deaktiviert werden oder wenn seit der letzten Aufnahme nur wenige Blobs hinzugefügt wurden.
* Die Benutzerzuordnung wurde aktualisiert, um eine verbesserte User Management-API zu verwenden, mit der 2000 Benutzer gleichzeitig abgerufen werden können, was die Leistung erheblich verbessert.
