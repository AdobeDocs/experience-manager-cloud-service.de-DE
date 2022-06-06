---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.2.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.2.0
feature: Release Information
exl-id: b1cd871d-c71e-4902-a97e-2c859f6a4da4
source-git-commit: c497424271ea960d22a30b4a6c66432935ec820d
workflow-type: ht
source-wordcount: '250'
ht-degree: 100%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.2.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.2.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.24 wurde am 01. Februar 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Die Möglichkeit, die Anzahl der Assets mit und ohne Smart-Tags zu erkennen und darüber zu berichten.
* Die Möglichkeit, die verwendete Version von Kernkomponenten zu erkennen und darüber zu berichten.
* Die Möglichkeit, den Typ der Quellebene (Autor oder Veröffentlichung), in der der BPA ausgeführt wurde, zu erkennen und darüber zu berichten.

### Fehlerbehebungen {#bug-fixes-bpa}

* Die BPA-Skalierungslogik wurde schneller und effizienter gestaltet.
* In einigen Szenarien inkrementierte der BPA die analysierte Anzahl nicht, als er ausgeführt wurde. Dieses Problem wurde behoben.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 1.8.6 wurde am 03. Februar 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Inhaltsvalidierung: Benutzer können zuverlässig feststellen, ob der gesamte vom Content Transfer Tool extrahierte Inhalt erfolgreich in die Zielinstanz aufgenommen wurde. Um diese Funktion verwenden zu können, müssen Sie sie in der `System Console` der AEM-Quellumgebung aktivieren. Weitere Informationen finden Sie unter [Validieren von Inhaltsübertragungen – Erste Schritte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html?lang=de#getting-started).

### Fehlerbehebungen {#bug-fixes-ctt}

* Einige Benutzer wurden nicht zugeordnet, da bei der Benutzerzuordnung zwischen Groß- und Kleinschreibung unterschieden wurde. Dieses Problem wurde behoben. Bei der Benutzerzuordnung wird nicht mehr zwischen Groß- und Kleinschreibung unterschieden.
