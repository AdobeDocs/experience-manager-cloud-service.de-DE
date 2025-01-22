---
title: Versionshinweise für Cloud Manager 2025.1.0 in Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Version Cloud Manager 2025.1.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: f6c1aa32647bcabeb0781973f81b75c11edc6a5d
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 19%

---

# Versionshinweise für Cloud Manager 2025.1.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3389843928 -->

Erfahren Sie mehr über die Version Cloud Manager 2025.1.0 in AEM (Adobe Experience Manager) as a Cloud Service.

>[!NOTE]
>
>Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Cloud Manager 2025.1.0 wurde in AEM as a Cloud Service am Mittwoch, 22. Januar 2025 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für den Freitag, 13. Februar 2025 geplant.


## Neue Funktionen {#what-is-new}

* **Regeln zur Code-Qualität - SonarQube-Server-Upgrade:** Der Schritt &quot;Cloud Manager-Code-Qualität“ wird ab Donnerstag, 13. Februar 2025, die Verwendung von SonarQube-Server 9.9 mit der Version Cloud Manager 2025.2.0 planen.

Zur Vorbereitung sind aktualisierte SonarQube-Regeln jetzt verfügbar unter [Code-Qualitätsregeln](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules).

Sie können die neuen Regeln frühzeitig überprüfen, indem Sie die folgende Pipeline-Textvariable festlegen:

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

Legen Sie außerdem die folgende Variable fest, um sicherzustellen, dass der Code-Qualitätsschritt für denselben Commit ausgeführt wird (normalerweise für denselben `commitId` übersprungen):

`CM_DISABLE_BUILD_REUSE` = `true`

![Seite Variablenkonfiguration](/help/implementing/cloud-manager/release-notes/assets/variables-config.png)

>[!NOTE]
>
>Adobe empfiehlt die Erstellung einer neuen CI/CD-Code-Qualitäts-Pipeline, die auf derselben Verzweigung wie die Haupt-Produktions-Pipeline konfiguriert ist. Legen Sie die entsprechenden Variablen *vor* der Version vom 13. Februar 2025 fest, um zu überprüfen, ob die neuen erzwungenen Regeln keine Blocker einführen.

* Build-Unterstützung für **Java 17 und Java 21:** Kunden können jetzt mit Java 17 oder Java 21 erstellen und erhalten Zugriff auf Leistungsverbesserungen und neue Sprachfunktionen. Konfigurationsschritte, einschließlich der Aktualisierung Ihrer Maven-Projekt- und Bibliotheksversionen, finden Sie unter [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). Wenn die Build-Version auf Java 17 oder Java 21 festgelegt ist, wird Java 21 als Laufzeit bereitgestellt.

   * **Funktionsaktivierung**
      * Diese Funktion wird am Donnerstag, dem 13. Februar 2025, zeitgleich mit dem standardmäßigen Rollout der neuen SonarQube-Version für alle Kunden aktiviert.
      * Kunden können sie *sofort aktivieren* indem sie die beiden oben beschriebenen Variablenkonfigurationen für die Aktualisierung der SonarQube 9.9-Version festlegen.

   * **Java 21-Laufzeitbereitstellung**
      * Die Java 21-Laufzeit wird beim Erstellen mit Java 17 oder Java 21 bereitgestellt.
      * Der schrittweise Rollout für alle Cloud Manager-Umgebungen beginnt im Februar für Sandboxes und Entwicklungsumgebungen und erstreckt sich im April auf Produktionsumgebungen.
      * Kunden, die mit Java 11 erstellen und die Java 21-Laufzeitumgebung (früher) *möchten,* sich unter [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com) an Adobe.

* **CDN-Konfigurationen“ in „Domain-Zuordnungen“ umbenannt:** Im Rahmen der Verbesserungen der Benutzeroberfläche in AEM Cloud Manager wird die Bezeichnung „CDN-Konfigurationen“ jetzt in „Domain-Zuordnungen“ umbenannt, um die Terminologieausrichtung an der Funktionalität zu verbessern. <!-- CMGR-64738 -->

  ![CDN-Konfigurationen“ wurden in der Benutzeroberfläche in „Domain-Zuordnungen“ umbenannt](/help/implementing/cloud-manager/release-notes/assets/domain-mappings.png)


<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->

<!-- ## Bug fixes -->




<!-- ## Known issues {#known-issues} -->
