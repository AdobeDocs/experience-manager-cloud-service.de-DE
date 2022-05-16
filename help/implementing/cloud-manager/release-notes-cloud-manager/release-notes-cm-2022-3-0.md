---
title: Versionshinweise für Cloud Manager 2022.3.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2022.3.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: d09d48c5-6e0a-4a6a-85e9-1a60fdd6e5bf
source-git-commit: 68586304724530f83649cffee76cefef3e1c8627
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionshinweise für Cloud Manager 2022.3.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite werden die Versionshinweise für Cloud Manager 2022.3.0 AEM as a Cloud Service dokumentiert.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager -Version 2022.3.0 in AEM as a Cloud Service wurde am 10. März 2022 veröffentlicht. Die nächste Version ist für den 7. April 2022 geplant.

## Neue Funktionen {#what-is-new}

* Der Zugriff auf AEM Umgebungsprotokoll kann über die Entwicklerrolle erfolgen.

## Fehlerbehebungen {#bug-fixes}

* Eine Untergruppe von manuell erstellten Git-Repositorys hatte einen falschen Namenswert, was verhindert hat, dass die Funktion zur Wiederverwendung von Build-Artefakten effektiv war. Die Namen dieser Repositorys wurden geändert, und die Benutzer sehen den berichtigten Namen in der Cloud Manager-API/-Benutzeroberfläche.
* Build-Artefakte aus produktionsfremden Pipelines wurden in Vollstapel-Pipelines der Produktion unangemessen wiederverwendet.
* Beim Hinzufügen oder Bearbeiten einer Code-Qualitäts-Pipeline werden die Optionen zum Verarbeiten von Metrikfehlern nicht mehr angezeigt.
* Im Build-Schritt konnten einige unerwartete Konfigurationen von Pipeline-Variablen auftreten.
