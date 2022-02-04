---
title: Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2022.2.0
description: Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2022.2.0
feature: Release Information
source-git-commit: 8876702f1a172282fd1ff46387ade2a45e187fed
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 18%

---


# Versionshinweise für Migrationswerkzeuge in AEM as a Cloud Service Version 2022.2.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für die Migrationswerkzeuge in AEM as a Cloud Service Version 2022.2.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.24 wurde am 01. Februar 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Möglichkeit, die Anzahl der Assets mit und ohne Smart-Tags zu erkennen und darüber zu berichten.
* Möglichkeit, die Version der verwendeten Kernkomponente zu erkennen und darüber zu berichten.
* Möglichkeit, den Typ der Quellebene (Autor oder Veröffentlichung) zu erkennen und darüber zu berichten, in der BPA ausgeführt wurde.

### Fehlerbehebungen {#bug-fixes-bpa}

* Die BPA-Skalierungslogik wurde schneller und effizienter gestaltet.
* In einigen Szenarien inkrementierte BPA die analysierte Anzahl nicht, als sie ausgeführt wurde. Dieses Problem wurde behoben.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 1.8.6 wurde am 03. Februar 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Inhaltsvalidierung - Benutzer können zuverlässig feststellen, ob der gesamte vom Content Transfer Tool extrahierte Inhalt erfolgreich in die Zielinstanz aufgenommen wurde. Um diese Funktion verwenden zu können, müssen Sie sie im `System Console` der AEM. Siehe [Validieren von Inhaltsübertragungen - Erste Schritte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html?lang=en#getting-started) für weitere Details.

### Fehlerbehebungen {#bug-fixes-ctt}

* Einige Benutzer wurden nicht zugeordnet, da bei der Benutzerzuordnung zwischen Groß- und Kleinschreibung unterschieden wurde. Dieses Problem wurde behoben. Bei der Benutzerzuordnung wird nicht mehr zwischen Groß- und Kleinschreibung unterschieden.

