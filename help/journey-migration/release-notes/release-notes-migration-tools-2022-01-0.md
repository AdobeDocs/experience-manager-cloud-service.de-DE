---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.1.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.1.0
feature: Release Information
exl-id: cbd0c316-bda3-48fb-89d6-a8f97bad1970
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: ht
source-wordcount: '133'
ht-degree: 100%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.1.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.1.0.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Die Version 1.7.18 von Content Transfer Tool wurde am 18. Januar 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Ein Umschalter wurde zur Extraktionsphase im Content Transfer Tool hinzugefügt, damit Benutzer die Option für eine [Vorabkopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de) während der Extraktion deaktivieren können. Für optimale Extraktionsgeschwindigkeiten sollte die Vorabkopie während der Extraktion für kleine Migrationssätze deaktiviert werden. Dies gilt auch, wenn seit der letzten Extraktion nur wenige Blobs hinzugefügt wurden.

### Fehlerbehebungen {#bug-fixes-ctt}

* Standardkonfigurationen wurden aktualisiert, um Ausführungszeitüberschreitungen während der Extraktion zu reduzieren.
