---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.9.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.9.0
feature: Release Information
exl-id: 581370ba-e3e8-487e-af83-a1eacbda2763
source-git-commit: dd4515bdbba81dcec0868c3058c7745775cc80ff
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 100%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.9.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.9.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer Version 2.1.34 wurde am 12. September 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* BPA kann jetzt erkennen und berichten, ob der Kunde eine benutzerdefinierte Logger-Konfiguration hinzugefügt hat. AEM as a Cloud Service unterstützt keine benutzerdefinierten Protokolldateien. Alle Protokolldateien müssen an `error.log` weitergeleitet werden
* BPA kann jetzt Berichte zu den verschiedenen binären MIME-Typen, die im Repository des Kunden vorhanden sind, und den damit verbundenen Zählungen erstellen.

### Fehlerbehebungen {#bug-fixes-bpa}

* In der BPA-Benutzeroberfläche traten bei der Anzeige einer großen Anzahl von Ergebnissen unter einem einzigen Muster Rendering-Probleme auf. Dieses Problem wurde behoben.
* BPA meldete einige Ergebnisse fälschlicherweise als nicht kompatible Änderungen mit kritischem Schweregrad. Dieses Problem wurde behoben.
