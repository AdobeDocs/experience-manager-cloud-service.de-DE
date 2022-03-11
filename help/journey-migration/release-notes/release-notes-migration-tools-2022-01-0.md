---
title: Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2022.1.0
description: Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2022.1.0
feature: Release Information
exl-id: cbd0c316-bda3-48fb-89d6-a8f97bad1970
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 14%

---

# Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2022.1.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für die Migrationswerkzeuge in AEM as a Cloud Service Version 2022.1.0.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Die Version 1.7.18 des Content Transfer Tool wurde am 18. Januar 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Wechsel zur Extraktionsphase im Content Transfer Tool hinzugefügt, damit Benutzer die Option deaktivieren können [pre-copy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de) während der Extraktion. Für optimale Extraktionsgeschwindigkeiten sollte die Vorauskopie während der Extraktion für kleine Migrationssätze deaktiviert werden oder wenn seit der letzten Extraktion nur wenige Blobs hinzugefügt wurden.

### Fehlerbehebungen {#bug-fixes-ctt}

* Standardkonfigurationen wurden aktualisiert, um Ausführungszeitüberschreitungen während der Extraktion zu reduzieren.
