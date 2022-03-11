---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2022.02.0
description: Dies sind die Versionshinweise für Cloud Manager in AEM as a Cloud Service Version 2022.02.0.
feature: Release Information
exl-id: da0643a0-78f8-4e9d-9cc9-a1a17067a08c
source-git-commit: 8162d1d6ddeff867507f749f223c0111b6856122
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 18%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2022.02.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für Cloud Manager in AEM as a Cloud Service Version 2022.02.0 beschrieben.

>[!NOTE]
>
>Siehe [diese Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) für die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager-Version AEM as a Cloud Service Version 2022.02.0 wurde am 10. Februar 2022 veröffentlicht. Die nächste Version soll am 10. März 2022 veröffentlicht werden.

## Neue Funktionen {#what-is-new}

* Neu beschleunigt [Web-Ebenen-Konfigurations-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) wurden eingeführt, um ausschließlich die HTTPD/Dispatcher-Konfiguration bereitzustellen.
   * Sie müssen AEM Version verwenden `2021.12.6151.20211217T120950Z` oder neuer und [Aktivieren des flexiblen Modus der Dispatcher-Tools](/help/implementing/dispatcher/disp-overview.md#validation-debug) , um diese Funktion zu verwenden.
   * Diese Funktion wird in den zwei Wochen nach der Version 2022.02.0 schrittweise eingeführt.
* Das Landingpage-Erlebnis von Cloud Manager wurde aktualisiert, um eine verbesserte Navigation, einen einfachen Wechsel zwischen Raster-/Kachelansichten und Pop-ups für eine schnelle Programmzusammenfassung zu ermöglichen.
* Ein neuer ausfallender Schwellenwert (`< D`) wurde zum [Zuverlässigkeitsbewertungsmetrik.](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules)
   * Kunden mit schwerwiegenden Qualitätsproblemen, die sich auf die Systemstabilität auswirken und in erster Linie auf ungültige Indizes und Workflow-Prozesse zurückzuführen sind, können die Bereitstellung erst nach Behebung dieser Probleme durchführen.
* Die Schwere der `BannedPath` [Qualitätsregel](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules) wurde von Blocker zu kritisch geändert.
* Der Pipeline-Assistent informiert den Benutzer, wenn vor dem Konfigurieren einer AEM möglicherweise eine Aktualisierung der Umgebung erforderlich ist. [Web-Ebenen-Konfigurations-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) zugeordnet.

## Fehlerbehebungen {#bug-fixes}

* Alte Git-Repository-Kennwörter werden jetzt immer invalidiert, wenn ein neues Kennwort generiert wird.
* Die Aktualisierung von Umgebungsvariablen über die API beeinträchtigt in seltenen Fällen nicht mehr die Pipelineausführung.
