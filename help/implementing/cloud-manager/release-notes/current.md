---
title: Versionshinweise für Cloud Manager 2024.12.0 in Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Version Cloud Manager 2024.12.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 8e89adcaadbc53c3d525d57ef452f671137a619f
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 47%

---

# Versionshinweise für Cloud Manager 2024.12.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Erfahren Sie mehr über die Version Cloud Manager 2024.12.0 in AEM (Adobe Experience Manager) as a Cloud Service.

>[!NOTE]
>
>Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Cloud Manager 2024.12.0 wurde in AEM as a Cloud Service am Donnerstag, 5. Dezember 2024 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für den 23. Januar 2025 geplant.


## Neue Funktionen {#what-is-new}

<!-- * **Java 21 support:** Customers can now optionally build with Java 17 or Java 21, benefiting from performance improvements and new language features. See [Build environment](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) for configuration steps, including updating your Maven project description, and certain library versions. When the build version is set to Java 17 or Java 21, the runtime defaults to Java 21.

    Starting February 2025, sandboxes and dev environments upgrade to the Java 21 runtime, regardless of the build version (Java 8, 11, 17, or 21). Production environments follow with an upgrade in April 2025. -->

* **A-Datensatztypen:** Unterstützung für A-Datensatztypen wurde hinzugefügt, um die Live-Schaltung für Domains mithilfe von CDN-Konfigurationen in AEM Cloud Manager zu verbessern. Sie haben jetzt die Möglichkeit, live zu gehen, indem Sie entweder einen CNAME-Datensatztyp oder einen A-Datensatztyp hinzufügen, der die IPs von Fastly darstellt, was das Domain-Routing vereinfacht. Durch diese Verbesserung entfällt die Beschränkung, sich bei der Domain-Einrichtung mit Fastly ausschließlich auf CNAME-Einträge zu verlassen.

  Siehe [Hinzufügen eines benutzerdefinierten Domain-](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)<!-- CMGR-63076 -->.

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. -->

* **Hinzufügen mehrerer Domains zu einer Edge Delivery-Site:** Sie können einer Edge Delivery-Site (EDS) in AEM Cloud Manager jetzt mehrere Domains hinzufügen, einschließlich Apex- und Nicht-Apex-Domains. Diese Verbesserung beseitigt frühere Einschränkungen, die die Möglichkeit einschränkten, mehrere Domains mit einem EDS-Ursprung zu verknüpfen. Die Aktualisierung sorgt für eine höhere Flexibilität bei der Verwaltung von Domain-Konfigurationen und vereinfacht die Live-Schaltung für Sites mit komplexen Domain-Setups. <!-- CMGR-63007 -->

* **Erweiterte Filteroptionen:** Erweiterte Filteroptionen wurden auf den Seiten der Pipeline-Ausführung und des SSL-Zertifikats in AEM Cloud Manager eingeführt. Sie können jetzt nach mehreren Kriterien filtern, um so den Zugriff auf relevante Daten zu beschleunigen und die Bereitstellungseffizienz zu verbessern. <!-- CMGR-26263 -->

   * **Filterung von Pipeline-Aktivitäten** Umfasst die Filterung von Pipeline-Aktivitäten, mit denen Sie die Suchergebnisse für bestimmte Pipeline-Aktivitäten verfeinern können. Zu den verfügbaren Filtern gehören Pipeline, Aktion und Status.
     ![Filtern von Pipeline-Aktivitäten](/help/implementing/cloud-manager/assets/filters-pipeline.png)


   * **SSL-Zertifikatfilterung:** Umfasst die Filterung von SSL-Zertifikaten, mit der Sie die Suchergebnisse für bestimmte Zertifikate verfeinern können. Zu den verfügbaren Filtern gehören SSL-Zertifikatname, Eigentümerschaft und Status.
     ![SSL-Zertifikatfilterung](/help/implementing/cloud-manager/assets/filters-ssl-certificates.png)

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie am Early-Adopter-Programm von Cloud Manager teil und nutzen Sie die Möglichkeit, zukünftige Funktionen zu testen.

### Bringen Sie Ihren eigenen Git mit – jetzt mit Unterstützung für GitLab und Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

Die Funktion zum **Einbringen des eigenen Git** wurde erweitert und unterstützt jetzt auch externe Repositorys wie GitLab und Bitbucket. Diese neue Unterstützung ergänzt die bereits vorhandene Unterstützung für private und Unternehmens-GitHub-Repositorys. Wenn Sie diese neuen Repositorys hinzufügen, können Sie sie auch direkt mit Ihren Pipelines verknüpfen. Sie können diese Repositorys auf öffentlichen Cloud-Plattformen oder in Ihrer privaten Cloud oder Infrastruktur hosten. Durch diese Integration entfällt auch die Notwendigkeit der konstanten Code-Synchronisation mit dem Adobe-Repository. Sie bietet weiterhin die Möglichkeit, Pull-Anfragen zu überprüfen, bevor sie in einer Hauptverzweigung zusammengeführt werden.

Pipelines, die externe Repositorys (ausgenommen GitHub-gehostete Repositorys) und die Option **Bereitstellungsauslöser** **Bei Git-Änderungen** verwenden, starten jetzt automatisch.

Siehe [Hinzufügen von externen Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Derzeit sind vorkonfigurierte Code-Qualitätsprüfungen für Pull-Anfragen ausschließlich für von GitHub gehostete Repositorys verfügbar. Es ist jedoch ein Update in Arbeit, um diese Funktionen auf andere Git-Anbieter zu erweitern.

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com). Geben Sie unbedingt an, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder einer Unternehmens-Repository-Struktur befinden.

## Fehlerbehebungen

* Es wurde ein Schutzmechanismus hinzugefügt, um das Löschen von Domains mit aktiven Domain-Zuordnungen in AEM Cloud Manager zu verhindern. Benutzer, die versuchen, solche Domains zu löschen, erhalten jetzt eine Fehlermeldung, die sie anweist, zunächst die Domain-Zuordnung zu löschen, bevor mit dem Löschen der Domain fortgefahren wird. Dieser Workflow stellt die Integrität der Domain sicher und verhindert versehentliche Fehlkonfigurationen. <!-- CMGR-63033 -->
* In seltenen Fällen konnten Benutzer aufgrund eines falschen Status, der in den jeweiligen Fällen zugewiesen wurde, keinen Domain-Namen hinzufügen oder ein SSL-Zertifikat aktualisieren. <!-- CMGR-62816 -->


<!-- ## Known issues {#known-issues} -->
