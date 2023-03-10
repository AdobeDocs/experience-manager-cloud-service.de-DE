---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2023.03.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.03.0
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
source-git-commit: b2681113f5565e4f63c76abeaf46d5f4b1a8a8ea
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 30%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2023.03.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.03.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.40 wurde am 03. März 2023 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* BPA kann jetzt Knoten, die in Konflikt zueinander stehen, erkennen und darüber berichten - Knoten mit denselben `jcr:uuid`. Solche Ergebnisse werden als kritisch markiert, da sie zu Fehlern bei der Inhaltsaufnahme führen können, wenn Inhalte auf AEM as a Cloud Service verschoben werden.
* BPA kann jetzt die Verwendung von Event-Listenern erkennen und darüber berichten. Es wird empfohlen, diesen Ereignistyp bei der Umstellung auf AEM as a Cloud Service in Sling-Aufträge umzuwandeln.

### Fehlerbehebungen {#bug-fixes-bpa}

* BPA meldete falsch-positive Ergebnisse über `grouprendercondition`. Dieses Problem wurde behoben.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 2.0.16 wurde am 08. März 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Die Benutzerzuordnung wurde optimiert und in den Schritt zur Inhaltsextraktion integriert. Es ist kein Setup erforderlich. Standardmäßig erfolgt die Benutzerzuordnung automatisch, wenn der Benutzer die Inhaltsextraktion startet. Der Benutzer hat die Möglichkeit, bei Bedarf die Benutzerzuordnung zu deaktivieren. Weitere Informationen finden Sie [hier.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/user-mapping-and-migration.html?lang=en#user-mapping-detail)
* Der Schritt &quot;Prepopy&quot;mit [AzCopy](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) wurde in das Content Transfer Tool integriert, um die Inhaltsextraktion erheblich zu beschleunigen. Precopy wird automatisch konfiguriert und installiert, wenn diese CTT-Version installiert ist. Wenn die Extraktion initiiert wird, wird die Prepy automatisch für Migrationssätze ausgeführt, die größer als 200 GB sind. Benutzer haben die Möglichkeit, sie bei Bedarf zu deaktivieren. Weitere Informationen finden Sie [hier.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en)
* CTT kann jetzt auf Windows-Servern verwendet werden.

### Fehlerbehebungen {#bug-fixes-ctt}

* Mehrere Fehlerbehebungen zur Verbesserung der Resilienz bei der Inhaltsextraktion.
