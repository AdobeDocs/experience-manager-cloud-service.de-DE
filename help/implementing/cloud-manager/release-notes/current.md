---
title: Versionshinweise für Cloud Manager 2025.2.0 in Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Version Cloud Manager 2025.2.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: c2a0961cae6d36d8ea3116c6e7982889257f90c8
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 35%

---

# Versionshinweise für Cloud Manager 2025.2.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3389843928 -->

Erfahren Sie mehr über die Version Cloud Manager 2025.2.0 in AEM (Adobe Experience Manager) as a Cloud Service.


Siehe auch die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2025.2.0 von Cloud Manager in AEM as a Cloud Service wurde am Donnerstag, dem Freitag, 13. Februar 2025 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für Donnerstag, den Freitag, 13. März 2025 geplant.

## Neue Funktionen {#what-is-new}

* **Aktualisieren der Code-Qualitätsregeln.**
Ab Donnerstag, dem 13. Februar 2025, verwendet der Cloud Manager-Code-Qualitätsschritt jetzt eine aktualisierte SonarQube-Version 9.9.5.90363.

  Die aktualisierten Regeln, die für Cloud Manager in AEM as a Cloud Service unter [diesem Link](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules) verfügbar sind, gelten für die Sicherheitsbewertungen und die Code-Qualität für Cloud Manager-Pipelines. Diese Aktualisierung kann sich auf Ihre Qualitäts-Gates auswirken und Bereitstellungen möglicherweise blockieren.

* **Java 17- und Java 21-Build-Unterstützung.**

  Kunden können jetzt mit Java 17 oder Java 21 erstellen und erhalten Zugriff auf Leistungsverbesserungen und neue Sprachfunktionen. Konfigurationsschritte, einschließlich der Aktualisierung Ihrer Maven-Projekt- und Bibliotheksversionen, finden Sie unter [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). Wenn die Build-Version auf Java 17 oder Java 21 festgelegt ist, wird Java 21 als Laufzeit bereitgestellt.

   * **Aktivierung von Funktionen**
      * Diese Funktion wird am Donnerstag, dem 13. Februar 2025, zeitgleich mit dem standardmäßigen Rollout der neuen SonarQube-Version für alle Kundinnen und Kunden aktiviert.
      * Kundinnen und Kunden können sie *sofort* aktivieren, indem sie die beiden oben beschriebenen Variablenkonfigurationen für die Aktualisierung der SonarQube-Version 9.9 festlegen.

   * **Java 21-Laufzeitbereitstellung**
      * Die Java 21-Laufzeit wird beim Erstellen mit Java 17 oder Java 21 bereitgestellt.
      * Der schrittweise Rollout für alle Cloud Manager-Umgebungen beginnt im Februar für Sandboxes und Entwicklungsumgebungen und wird im April auf Produktionsumgebungen ausgeweitet.
      * Kundinnen und Kunden, die mit Java 11 erstellen und die Java 21-Laufzeitumgebung *früher* übernehmen möchten, können sich unter [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com) an Adobe wenden.

* **99,99 % Uptime-Reporting für Edge Delivery Services.**
Für qualifizierte Edge Delivery Services-Programme ist jetzt ein Hochverfügbarkeits-Reporting zu 99,99 % verfügbar. Um diese Funktion zu aktivieren, müssen Kunden ihre Edge Delivery Services-Sites erfolgreich integrieren und ihre 99,99 %-Service level agreement (SLA) in Cloud Manager anwenden.

  Siehe auch [SLA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla).

* **Verbessertes Benutzereinladungserlebnis für Edge Delivery Services.**
Das Erlebnis, Benutzende in das mit Edge Delivery Services verknüpfte Inhalts-Repository einzuladen, wurde verbessert. <!-- CMGR-65331 -->

* **Automatische Erstellung von Administratorprofilen auf Veröffentlichungsinstanzen.**
Zuvor ermöglichte Cloud Manager die manuelle Erstellung von Administratorprofilen auf Veröffentlichungsinstanzen, unterstützte jedoch nicht standardmäßig die automatische Erstellung. Mit diesem Update werden jetzt automatisch Administratorprofile in Veröffentlichungsinstanzen erstellt, was die Benutzerfreundlichkeit verbessert und die Einrichtungszeit für Kunden reduziert.

  Weitere Informationen finden Sie unter [Benutzerdefinierte Berechtigungen](/help/implementing/cloud-manager/custom-permissions.md).

  ![Filtern von Pipeline-Aktivitäten](/help/implementing/cloud-manager/release-notes/assets/product-profiles.png)

* **Wechsel zu OAuth für Cloud Service-Umgebungen.**
In neuen Cloud Service-Umgebungen wird jetzt die OAuth-basierte Service-zu-Service-Authentifizierung für Adobe Developer Console-Integrationsprojekte anstelle der zuvor verwendeten JWT-Authentifizierungsmethode verwendet. Die JWT-Authentifizierung wird nicht mehr unterstützt und ist für das Ende der Lebensdauer im Juni 2025 geplant.

* **Unterstützung für EC (Elliptic Curve) Private Keys (secp384r1).**
Cloud Manager unterstützt jetzt `secp384r1` privaten EC-Schlüssel (Elliptic Curve) und bietet so verbesserte Sicherheit und Compliance für kundenverwaltete OV/EV-SSL-Zertifikate.
Weitere Informationen finden Sie unter [Anforderungen für kundenverwaltete OV/EV-SSL-Zertifikate](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md). <!-- CMGR-63636 -->

<!--
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


## Fehlerbehebungen

* **(UI) Es wurde ein Problem behoben, das die CDN-Konfiguration für Domains in Cloud Manager verhinderte.**
Kunden, die versuchen, eine CDN-Konfiguration in Cloud Manager hinzuzufügen, haben einen Bildschirmfehler festgestellt, als sie eine Domain aus dem Dropdown-Menü ausgewählt haben. Dieser Benutzeroberflächenfehler verhinderte die Domain-Zuordnung in Produktionsumgebungen und blockierte so den Konfigurationsprozess.

  Darüber hinaus blieb der Zugriff auf einige Domains im Backend trotz Entfernung aus der Benutzeroberfläche unmöglich. Dieses Problem führte zu Konflikten mit vorhandenen CDN-Konfigurationen.

  Mit dieser Fehlerbehebung können Sie jetzt eine Domain erfolgreich aus der Dropdown-Liste auswählen, ohne einen Fehler zu verursachen. Backend-Inkonsistenzen, die eine Domain-Neukonfiguration verhindert haben, wurden behoben. Und schließlich stellt die verbesserte Validierung jetzt sicher, dass widersprüchliche Domains ordnungsgemäß entfernt werden, bevor sie erneut hinzugefügt werden.<!-- CMGR-64888 -->
* **(Backend) Es wurde ein Problem behoben, bei dem SSL-Ablaufbenachrichtigungen mehrmals gesendet wurden.**
Es wurde ein Fehler entdeckt, durch den der SSL-Ablaufbenachrichtigungs-Planer, der einmal täglich um Mitternacht ausgeführt werden soll, fälschlicherweise zweimal täglich um Mitternacht und erneut um 0:30 Uhr ausgelöst wurde. Dieses Problem führte dazu, dass mehrere redundante Benachrichtigungen zu ablaufenden SSL-Zertifikaten gesendet wurden.

  Die Benachrichtigungsplanung wird jetzt korrekt ausgeführt, wie vorgesehen, nur einmal pro Tag. Außerdem erhalten Sie keine doppelten SSL-Ablaufbenachrichtigungen mehr. <!-- CMGR-64748 -->




<!-- ## Known issues {#known-issues} -->
