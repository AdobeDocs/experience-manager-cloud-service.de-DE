---
title: Versionshinweise für Migration-Tools in AEM as a Cloud Service 2021.12.0
description: Versionshinweise für Migration-Tools in AEM as a Cloud Service 2021.12.0
feature: Release Information
exl-id: 4155e1c0-cd40-4cbc-9d6c-b106d68a2db5
role: Admin
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 100%

---

# Versionshinweise für Migration-Tools in AEM as a Cloud Service 2021.12.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2021.12.0.

>[!NOTE]
>
>Die neuesten Versionshinweise finden Sie unter [Aktuelle Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.22 wurde am 01. Dezember 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Die Möglichkeit, die verwendete Version von ACS Commons zu erkennen und darüber zu berichten.
* Die Möglichkeit, die Anzahl der Benutzer und Untergruppen in einer Gruppe zu erkennen und darüber zu berichten.
* Die Möglichkeit, Knoteneigenschaftswerte in MongoDB, die 16 MB überschreiten, zu erkennen und darüber zu berichten.

### Fehlerbehebungen {#bug-fixes-bpa}

* Die Erkennung von Foundation-Komponenten wurde optimiert, um falsche negative Werte zu reduzieren.
* Für AEM Forms-Kunden: BPA-Messaging zur fehlenden Verfügbarkeit von `EMAIL_PDF_SUBMIT_ACTION` in AEM as a Cloud Service wurde behoben.


## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 1.7.10 wurde am 08. Dezember 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Ein Umschalter wurde zur Aufnahmephase im Content Transfer Tool hinzugefügt, damit Benutzer [Vorkopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de) während der Aufnahme deaktivieren können. Für optimale Aufnahmegeschwindigkeiten sollte die Vorkopie während der Aufnahme bei kleinen Migrationssätzen deaktiviert werden oder wenn seit der letzten Aufnahme nur wenige Blobs hinzugefügt wurden.
* Die Benutzerzuordnung wurde aktualisiert, um eine verbesserte User Management-API zu verwenden, mit der 2000 Benutzer gleichzeitig abgerufen werden können, was die Leistung erheblich verbessert.
