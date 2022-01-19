---
title: Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2022.1.0
description: Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2022.1.0
feature: Release Information
source-git-commit: 0bc2dedd9bfbf138fddf9fe112ba0d66444fcb41
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
