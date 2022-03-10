---
title: Versionshinweise für Cloud Manager 2022.3.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2022.3.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 428bba062fcfb44ebfbbf3c1d05ce1a4634fb429
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 2%

---


# Versionshinweise für Cloud Manager 2022.3.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite werden die Versionshinweise für Cloud Manager 2022.3.0 AEM as a Cloud Service dokumentiert.

>[!NOTE]
>
>Siehe [diese Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) für die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager -Version 2022.3.0 wurde AEM as a Cloud Service 10. März 2022 veröffentlicht. Die nächste Version ist für den 7. April 2022 geplant.

## Neue Funktionen {#what-is-new}

* Ein Benutzer mit der **Entwickler** -Rolle kann jetzt auf das AEM-Umgebungsprotokoll zugreifen.
* [Die `reliability_rating` kritische Metrik](/help/implementing/cloud-manager/code-quality-testing.md) wurde deaktiviert.
* Ein Benutzer kann nun die Spalten im **Pipelines** in Cloud Manager.

## Fehlerbehebungen {#bug-fixes}

* Eine Untergruppe manuell erstellter Git-Repositorys hatte falsche Namenswerte, die sich auf [die Funktion zur Wiederverwendung von Build-Artefakten.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) Die Namen dieser Repositorys wurden geändert, und die Benutzer sehen den berichtigten Namen in der Cloud Manager-API/-Benutzeroberfläche.
* [Beim Hinzufügen oder Bearbeiten einer Code-Qualitäts-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) die **Verhalten bei wichtigen Metrikfehlern** werden nicht mehr angezeigt.
* Unerwartete Pipelinevariablenkonfigurationen verursachen keine Fehler mehr im Build-Schritt.
