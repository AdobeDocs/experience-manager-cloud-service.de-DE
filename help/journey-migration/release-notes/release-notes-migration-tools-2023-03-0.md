---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.03.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.03.0
feature: Release Information
exl-id: cdc57cca-e10a-4b0d-b803-910ccc9350a6
role: Admin
source-git-commit: fecbebde808c545a84889da5610a79c088f2f459
workflow-type: ht
source-wordcount: '297'
ht-degree: 100%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.03.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.03.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer v2.1.40 wurde am 03. März 2023 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* BPA kann jetzt widersprüchliche Knoten – Knoten mit derselben `jcr:uuid` – erkennen und melden. Solche Ergebnisse werden als kritisch markiert, da sie zu Fehlern bei der Inhaltsaufnahme führen können, wenn Inhalte auf AEM as a Cloud Service verschoben werden.
* BPA kann jetzt die Verwendung von Event-Listenern erkennen und darüber berichten. Es wird empfohlen, diesen Ereignistyp bei der Umstellung auf AEM as a Cloud Service in Sling-Aufträge umzuwandeln.

### Fehlerbehebungen {#bug-fixes-bpa}

* BPA meldete falsch-positive Ergebnisse bei `grouprendercondition`. Dieses Problem wurde behoben.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool v2.0.16 wurde am 08. März 2023 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Die Benutzerzuordnung wurde optimiert und in den Schritt zur Inhaltsextraktion integriert. Es ist keine Einrichtung erforderlich. Standardmäßig erfolgt die Benutzerzuordnung automatisch, wenn Benutzende die Inhaltsextraktion starten. Die Benutzenden haben die Möglichkeit, bei Bedarf die Benutzerzuordnung zu deaktivieren. 
* Der Vorkopierschritt mit [AzCopy](https://learn.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10) wurde in das Content Transfer Tool integriert, was die Extraktion von Inhalten erheblich beschleunigt. Vorkopie wird automatisch konfiguriert und installiert, wenn diese CTT-Version installiert ist. Wenn die Extraktion initiiert wird, wird die Vorkopie automatisch für Migrationssätze ausgeführt, die größer als 200 GB sind. Benutzende haben die Möglichkeit, sie bei Bedarf zu deaktivieren. Weitere Informationen finden Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de).
* CTT kann jetzt auf Windows-Servern verwendet werden.

### Fehlerbehebungen {#bug-fixes-ctt}

* Mehrere Fehlerbehebungen zur Verbesserung der Belastbarkeit bei der Inhaltsextraktion.
