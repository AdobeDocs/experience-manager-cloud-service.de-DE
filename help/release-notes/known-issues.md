---
title: Bekannte Probleme
description: Spezifische Versionshinweise zu bekannte Problemen mit Adobe Experience Manager as a Cloud Service.
exl-id: 897b944a-d320-4d21-91f4-2cd3da6179b1
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 100%

---

# Bekannte Probleme {#known-issues}

In diesem Artikel werden die bekannten Probleme mit Adobe Experience Manager as a Cloud Service aufgeführt. Die Liste wird mit jeder neuen Version von Adobe Experience Manager überarbeitet und aktualisiert.

[Wenden Sie sich an den Support](https://helpx.adobe.com/de/marketing-cloud/experience-manager.html), um weitere Informationen zu den folgenden bekannten Problemen zu erhalten.

<!-- 
## Platform {#platform}

## Sites {#sites}
-->

## Assets {#assets}

<!-- Jira label: assets-cloud-known-issues -->

Zu den bekannten Probleme zählen:

* **Metadatenschema**: Das Widget zur Asset-Bewertung, das verwendet wird, um JSP-Kompilierungsfehler zu verursachen. Es wurde aus dem Metadatenschema entfernt. <!-- CQ-4282865, CQ-4284633 -->

### Künftig verfügbare AEM Assets-Funktionen {#upcoming-assets-capabilities}

Einige Funktionen von Adobe Experience Manager-Assets, die von den grundlegenden Funktionen abhängen, die noch nicht in der Adobe Experience Manager as a Cloud Service-Bereitstellungsarchitektur verfügbar sind, werden voraussichtlich zu einem späteren Zeitpunkt aktiviert:

* Aufgrund der Abhängigkeit von Commerce Integration Framework-APIs sind die folgenden Funktionen derzeit nicht aktiviert:
   * Fotoshooting-Workflow-Modelle.
   * In der Benutzeroberfläche der Asset-Eigenschaften ist die Registerkarte mit den Produktinformationen nicht ausgefüllt.
* Aufgrund der Abhängigkeit von der InDesign Server-Integration sind die folgenden Funktionen derzeit nicht aktiviert:
   * Asset-Vorlagen und Asset-Kataloge.
   * Mehrseitige Vorschau von Adobe InDesign-Dateien.

>[!MORELIKETHIS]
>
>* [Wichtige Änderungen an AEM](aem-cloud-changes.md)
* [Veraltete und entfernte Funktionen](deprecated-removed-features.md)
* [Versionshinweise](home.md)

