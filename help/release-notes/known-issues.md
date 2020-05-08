---
title: Bekannte Probleme
description: Spezifische Versionshinweise zu bekannte Problemen mit Adobe Experience Manager as a Cloud Service.
translation-type: ht
source-git-commit: ce82d7c9ca1fd8fe3d6f61213cfee360fc6496fd

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

* Erweiterte Funktionen für Smart-Tagging, die KI-Dienste von Adobe I/O nutzen, sind derzeit nicht verfügbar.
* Aufgrund der Abhängigkeit von Commerce Integration Framework-APIs sind die folgenden Funktionen derzeit nicht aktiviert:
   * Fotoshooting-Workflow-Modelle.
   * In der Benutzeroberfläche der Asset-Eigenschaften ist die Registerkarte mit den Produktinformationen nicht ausgefüllt.
* Aufgrund der Abhängigkeit von der InDesign Server-Integration sind die folgenden Funktionen derzeit nicht aktiviert:
   * Asset-Vorlagen und Asset-Kataloge.
   * Mehrseitige Vorschau von InDesign-Dateien.

>[!MORELIKETHIS]
>
>* [Wichtige Änderungen an AEM](aem-cloud-changes.md)
>* [Veraltete und entfernte Funktionen](deprecated-removed-features.md)
>* [Versionshinweise](home.md)

