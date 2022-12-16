---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.9.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.9.0
feature: Release Information
source-git-commit: d6c47c3b8fe4ac994ee9f2db365888f496be12f0
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 41%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.9.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.9.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Die Version 2.1.34 von Best Practices Analyzer wurde am 12. September 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* BPA kann jetzt erkennen und berichten, ob der Kunde eine benutzerdefinierte Logger-Konfiguration hinzugefügt hat. AEM as a Cloud Service unterstützt keine benutzerdefinierten Protokolldateien. Alle Protokolldateien müssen an `error.log`
* BPA kann jetzt Berichte zu den verschiedenen binären MIME-Typen erstellen, die im Repository des Kunden vorhanden sind, und die mit ihm verbundenen Zählungen.

### Fehlerbehebungen {#bug-fixes-bpa}

* In der BPA-Benutzeroberfläche traten bei der Anzeige einer großen Anzahl von Ergebnissen unter einem einzigen Muster Rendering-Probleme auf. Dieses Problem wurde behoben.
* BPA meldete einige Feststellungen fälschlicherweise als nicht kompatible Änderungen mit kritischem Schweregrad an. Dieses Problem wurde behoben.
