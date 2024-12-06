---
title: Versionshinweise für Cloud Manager 2024.12.0 in Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Version Cloud Manager 2024.12.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 8e89adcaadbc53c3d525d57ef452f671137a619f
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 41%

---

# Versionshinweise für Cloud Manager 2024.12.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Erfahren Sie mehr über die Version Cloud Manager 2024.12.0 in AEM (Adobe Experience Manager) as a Cloud Service.

>[!NOTE]
>
>Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2024.12.0 von Cloud Manager in AEM as a Cloud Service wurde am Donnerstag, 5. Dezember 2024 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für den Freitag, 23. Januar 2025 geplant.


## Neue Funktionen {#what-is-new}

<!-- * **Java 21 support:** Customers can now optionally build with Java 17 or Java 21, benefiting from performance improvements and new language features. See [Build environment](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) for configuration steps, including updating your Maven project description, and certain library versions. When the build version is set to Java 17 or Java 21, the runtime defaults to Java 21.

    Starting February 2025, sandboxes and dev environments upgrade to the Java 21 runtime, regardless of the build version (Java 8, 11, 17, or 21). Production environments follow with an upgrade in April 2025. -->

* **Ein Record Types:** Unterstützung für A-Record-Typen wurde hinzugefügt, um die GoLive-Bereitschaft für Domänen mithilfe von CDN-Konfigurationen in AEM Cloud Manager zu verbessern. Jetzt können Sie live gehen, indem Sie entweder einen CNAME-Record-Typ oder einen A-Record-Typ hinzufügen, der die IPs von Fastly darstellt, und so das Domain-Routing vereinfachen. Diese Verbesserung beseitigt die Beschränkung, sich bei der Domain-Einrichtung mit Fastly ausschließlich auf CNAME-Einträge zu verlassen.

  Siehe [Hinzufügen eines benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). <!-- CMGR-63076 -->

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. -->

* **Mehrere Domänen zu einer Edge Delivery-Site hinzufügen:** Sie können jetzt mehrere Domänen, einschließlich sowohl Apex- als auch Nicht-Apex-Domänen, zu einer Edge Delivery-Site (EDS) in AEM Cloud Manager hinzufügen. Durch diese Verbesserung werden frühere Einschränkungen behoben, durch die die Möglichkeit eingeschränkt wurde, mehrere Domänen mit einer EDS-Herkunft zu verknüpfen. Die Aktualisierung sorgt für mehr Flexibilität bei der Verwaltung von Domänenkonfigurationen und vereinfacht die GoLive-Prozesse für Sites mit komplexen Domänen-Setups. <!-- CMGR-63007 -->

* **Erweiterte Filteroptionen:** Erweiterte Filteroptionen wurden auf Pipeline-Ausführungsseiten und auf SSL-Zertifikatsseiten in AEM Cloud Manager eingeführt. Sie können jetzt nach mehreren Kriterien filtern, um schneller auf relevante Daten zugreifen zu können und die Implementierungseffizienz zu verbessern. <!-- CMGR-26263 -->

   * **Filterung der Pipeline-Aktivitäten:** Enthält die Filterung der Pipeline-Aktivität, mit der Sie Suchergebnisse für bestimmte Pipeline-Aktivitäten eingrenzen können. Zu den verfügbaren Filtern gehören Pipeline, Aktion und Status.
     ![Filterung von Pipeline-Aktivitäten](/help/implementing/cloud-manager/assets/filters-pipeline.png)


   * **Datei mit SSL-Zertifikaten:** Enthält die Filterung von SSL-Zertifikaten, sodass Sie die Suchergebnisse für bestimmte Zertifikate verfeinern können. Zu den verfügbaren Filtern gehören Name, Besitz und Status des SSL-Zertifikats.
     ![SSL-Zertifikatfilterung](/help/implementing/cloud-manager/assets/filters-ssl-certificates.png)

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie am Early-Adopter-Programm von Cloud Manager teil und nutzen Sie die Möglichkeit, zukünftige Funktionen zu testen.

### Bringen Sie Ihren eigenen Git mit – jetzt mit Unterstützung für GitLab und Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

Die Funktion **Eigenes Git holen** wurde erweitert und unterstützt jetzt auch externe Repositorys wie GitLab und Bitbucket. Diese neue Unterstützung ergänzt die bereits vorhandene Unterstützung für private und Unternehmens-GitHub-Repositorys. Wenn Sie diese neuen Repositorys hinzufügen, können Sie sie auch direkt mit Ihren Pipelines verknüpfen. Sie können diese Repositorys auf öffentlichen Cloud-Plattformen oder in Ihrer privaten Cloud oder Infrastruktur hosten. Durch diese Integration entfällt auch die Notwendigkeit der konstanten Code-Synchronisation mit dem Adobe-Repository. Sie bietet weiterhin die Möglichkeit, Pull-Anfragen zu überprüfen, bevor sie in einer Hauptverzweigung zusammengeführt werden.

Pipelines, die externe Repositorys verwenden (außer von GitHub gehostete) und der **Bereitstellungs-Trigger** auf **On Git Changes** eingestellt sind, starten jetzt automatisch.

Siehe [Hinzufügen von externen Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Derzeit sind vorkonfigurierte Code-Qualitätsprüfungen für Pull-Anfragen ausschließlich für von GitHub gehostete Repositorys verfügbar. Es ist jedoch ein Update in Arbeit, um diese Funktionen auf andere Git-Anbieter zu erweitern.

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com). Geben Sie unbedingt an, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder einer Unternehmens-Repository-Struktur befinden.

## Fehlerbehebungen

* Es wurde eine Schutzmaßnahme hinzugefügt, um das Löschen von Domänen mit aktiven Domänenzuordnungen in AEM Cloud Manager zu verhindern. Benutzer, die versuchen, solche Domänen zu löschen, erhalten jetzt eine Fehlermeldung, in der sie angewiesen werden, zunächst die Domänenzuordnung zu löschen, bevor sie mit dem Löschen der Domäne fortfahren. Dieser Workflow stellt die Integrität der Domain sicher und verhindert versehentliche Fehlkonfigurationen. <!-- CMGR-63033 -->
* In seltenen Fällen war es Benutzern nicht möglich, einen Domänennamen hinzuzufügen oder ein SSL-Zertifikat zu aktualisieren, da in den entsprechenden Fällen ein falscher Status zugeordnet war. <!-- CMGR-62816 -->


<!-- ## Known issues {#known-issues} -->
