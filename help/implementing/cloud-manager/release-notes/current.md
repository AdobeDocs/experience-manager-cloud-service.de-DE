---
title: Versionshinweise für Cloud Manager 2023.6.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2023.6.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 35%

---


# Versionshinweise für Cloud Manager 2023.6.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2023.6.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Siehe [diese Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) für die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager -Version 2023.6.0 in AEM as a Cloud Service Version wurde am 8. Juni 2023 veröffentlicht. Die nächste Version ist für den 6. Juli 2023 geplant.

## Neue Funktionen {#what-is-new}

* Kunden können zusätzlich zur primären Region weitere sekundäre Veröffentlichungsregionen erwerben, was Vorteile mit reduzierter Latenz und höherer Verfügbarkeit bringt. Hinweis: Es können bestimmte Einschränkungen gelten.
* Beim Erstellen eines neuen [Programm oder Umwelt,](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) Der Name ist nun auf die Verwendung von alphanumerischen Zeichen und einer begrenzten Anzahl von Sonderzeichen beschränkt.
* Beim Fortsetzen einer [Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) wird jetzt beim Genehmigungsschritt ein Bestätigungsdialogfeld angezeigt.
* Für **[Kundenfunktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)** und **[Testen der benutzerdefinierten Benutzeroberfläche](/help/implementing/cloud-manager/ui-testing.md)** Pipeline-Schritte, eine neue `INCOMPLETE` -Status nun möglich, was bedeutet, dass solche Tests nicht vorhanden und daher nicht durchgeführt wurden.
   * In solchen Fällen schlägt die Pipeline nicht fehl und fährt mit dem nächsten Schritt fort.

## Fehlerbehebungen {#bug-fixes}

* Die [Web-Tier-Konfigurationspipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) sind nicht mehr fälschlicherweise für Nur-Assets-Programme aktiviert.
* Es wurde eine stabilere Validierung hinzugefügt, um bestimmte Arten von Fehlern bei der Umgebungsbereitstellung zu verhindern.
