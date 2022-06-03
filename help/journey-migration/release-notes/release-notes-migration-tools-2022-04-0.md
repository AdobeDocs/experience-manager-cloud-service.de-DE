---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.4.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.4.0
feature: Release Information
exl-id: 4941736b-82cd-4050-b3e9-aef250d5c4c7
source-git-commit: 717b2c851a18ef5171d64a462509ce08fb87a59c
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 31%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.4.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.4.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.28 wurde am 22. April 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Möglichkeit, die Verwendung nicht unterstützter Asset Manager-APIs zu erkennen und darüber zu berichten. Es gibt vier APIs, die AEM as a Cloud Service nicht mehr unterstützt werden. Kunden sollten sicherstellen, dass sie diese APIs nicht mehr verwenden und die neue Methode zum Hochladen von Assets verwenden.

* Möglichkeit, die Verwendung von Inhaltsfragmentvorlagen zu erkennen. Inhaltsfragmentvorlagen werden für die Erstellung neuer Inhaltsfragmente auf AEM as a Cloud Service nicht mehr unterstützt. Kunden müssen Inhaltsfragmentmodelle erstellen, um Inhaltsfragmentvorlagen zu ersetzen.

* Möglichkeit, Assets mit mehr als 100 untergeordneten Elementen unter dem Metadatenknoten des Assets im Repository zu erkennen. Es wird empfohlen, Metadaten-Knoten zu entfernen, die nicht erforderlich sind, um die Leistung beim Laden von Ordnern, die aus solchen Assets bestehen, zu verbessern.

* Möglichkeit, den Typ des verwendeten Datenspeichers zu erkennen und darüber zu berichten.

* Das Muster wurde für AEM Formularportal aktualisiert.

### Fehlerbehebungen {#bug-fixes-bpa}

* BPA meldete Ergebnisse für Kernkomponenten, statt nur über Kundenkomponenten zu berichten. Dieses Problem wurde behoben.
