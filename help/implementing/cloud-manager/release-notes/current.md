---
title: Versionshinweise für Cloud Manager 2024.12.0 in Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Version Cloud Manager 2024.12.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: ea1aa471a4fcb2ace6e4079715ac88af2d296e18
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionshinweise für Cloud Manager 2024.12.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Erfahren Sie mehr über die Version Cloud Manager 2024.12.0 in AEM (Adobe Experience Manager) as a Cloud Service.

>[!NOTE]
>
>Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2024.12.0 von Cloud Manager in AEM as a Cloud Service wurde am Donnerstag, 5. Dezember 2024 veröffentlicht.

Die nächste geplante Version ist Januar 2024.

## Neue Funktionen {#what-is-new}

* **Java 21-Unterstützung:** Kunden können jetzt optional mit Java 17 oder Java 21 erstellen, wobei sie von Leistungsverbesserungen und neuen Sprachfunktionen profitieren. Informationen zu den Konfigurationsschritten, einschließlich der Aktualisierung Ihrer Maven-Projektbeschreibung und bestimmter Bibliotheksversionen, finden Sie unter [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) . Wenn die Build-Version auf Java 17 oder Java 21 festgelegt ist, wird zur Laufzeit standardmäßig Java 21 verwendet.

  Ab Februar 2025 aktualisieren Sandboxes und Entwicklungsumgebungen auf die Java 21-Laufzeitumgebung, unabhängig von der Build-Version (Java 8, 11, 17 oder 21). Die Produktionsumgebungen werden im April 2025 aktualisiert.

* **Ein Record Types:** Unterstützung für A-Record-Typen wurde hinzugefügt, um die GoLive-Bereitschaft für Domänen mithilfe von CDN-Konfigurationen in AEM Cloud Manager zu verbessern. Jetzt können Sie live gehen, indem Sie entweder einen CNAME-Record-Typ oder einen A-Record-Typ hinzufügen, der die IPs von Fastly darstellt, und so das Domain-Routing vereinfachen. Diese Verbesserung beseitigt die Beschränkung, sich bei der Domain-Einrichtung mit Fastly ausschließlich auf CNAME-Einträge zu verlassen.

  Siehe [Hinzufügen eines benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). <!-- CMGR-63076 -->

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