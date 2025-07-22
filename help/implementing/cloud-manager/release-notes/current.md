---
title: Versionshinweise für Cloud Manager 2025.7.0
description: Erfahren Sie mehr über Cloud Manager 2025.7.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: f3e31d1f17283086cd6fe9e73d67feac938d6567
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 97%

---

# Versionshinweise für Cloud Manager 2025.7.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

Erfahren Sie mehr über Cloud Manager 2025.7.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2025.7.0 von Cloud Manager in AEM as a Cloud Service wurde am 10. Juli 2025 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für den 7. August 2025 geplant.

## Neue Funktionen {#what-is-new}

* **Cloud Manager unterstützt jetzt SSL-Zertifikate für ECDSA (Elliptic Curve Digital Signature Algorithm)**

  Cloud Manager unterstützt jetzt ECDSA-Zertifikate. Die Funktion sorgt für hohe Sicherheit bei kleineren Schlüsselgrößen, sodass Kundinnen und Kunden in ihren CDN-Konfigurationen einfache, moderne Verschlüsselung nutzen können. <!-- https://jira.corp.adobe.com/browse/CMGR-62399 -->

* **Bericht zur Nutzung von Site-Lizenzen herunterladen**

  Auf der Seite **Details zur Site-Nutzung** (Klicken Sie in Cloud Manager auf **Lizenz**. In der Tabelle „Lösungen“ klicken Sie in der Zeile **Sites** auf **Nutzungsdetails anzeigen**.) können Kundinnen und Kunden jetzt auf **Bericht herunterladen** klicken, um die Daten als CSV-Datei zu exportieren. Dieser Download vereinfacht die Analyse und Freigabe von Nutzungs-Trends. <!-- https://jira.corp.adobe.com/browse/CMGR-42274 -->

  ![Seite „Details zur Site-Nutzung“](/help/implementing/cloud-manager/release-notes/assets/sites-license-usage-page.png)

  Siehe [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

## Alpha/Beta-Programme {#private-beta-program}

Nehmen Sie an den Alpha- und Beta-Programmen von Cloud Manager teil, um vor der allgemeinen Veröffentlichung exklusiven Zugriff auf kommende Funktionen zu erhalten.

Derzeit stehen die folgenden Möglichkeiten zur Verfügung:

### Rollback mit einem Klick bei Pipeline-Bereitstellungen {#one-click-rollback}

Kehren Sie schnell zu einer vorherigen Bereitstellung zurück, wenn der neueste kundenspezifische Quell-Code nicht wie erwartet funktioniert. Dabei ist es nicht erforderlich, die vollständige Pipeline erneut auszuführen oder Commits manuell zurückzusetzen.<!--https://jira.corp.adobe.com/browse/CMGR-69556 -->

![Stellen Sie kundenspezifischen Quell-Code über die Karte „Umgebungen“ ](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed.png)*Karte „Umgebungen“ oben mit der Option **Wiederherstellen**>**Zuvor bereitgestellter Code**für eine ausgewählte Umgebung wieder her.*


![Dialogfeld „Zuvor bereitgestellten Code wiederherstellen“](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed-dialogbox.png)
*Überprüfen Sie im Dialogfeld **Zuvor bereitgestellten Code wiederherstellen**die aktuell bereitgestellte Version sowie die Version, die Sie wiederherstellen möchten, und klicken Sie dann auf **Bestätigen***.


![Aktivierung wird wiederhergestellt](/help/implementing/cloud-manager/release-notes/assets/restoring-previous-code-deployed-restoring.png)
*Cloud Manager setzt die Umgebung auf den früheren Build zurück, behält Inhalte und Konfiguration bei und markiert die Umgebung als **Wiederherstellung läuft**, bis die Bereitstellung abgeschlossen ist.*


![Verwendete Quell-Code-Version](/help/implementing/cloud-manager/release-notes/assets/environments-view-details-sourcecodeversion.png) *Die Ansicht „Umgebungsdetails“, wie oben dargestellt, zeigt jetzt auch die verwendete aktive Quell-Code-Version an.*

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [restorecode@adobe.com](mailto:restorecode@adobe.com).

Siehe [Wiederherstellen des vorherigen in AEM as a Cloud Service bereitgestellten Codes](/help/operations/restore-previous-code-deployed.md).

Siehe auch [Wiederherstellung von Content in AEM as a Cloud Service](/help/operations/restore.md).


### Spezialisierte Testumgebung {#specialized-test-environment}

Cloud Manager unterstützt jetzt das Hinzufügen eines neuen Umgebungstyps namens **Spezialisierte Testumgebung**. Diese Umgebung soll Teams dabei helfen, Funktionen vor der Live-Schaltung unter produktionsnahen Bedingungen zu validieren. Dieser Umgebungstyp unterscheidet sich von *Produktion + Staging*, *Entwicklung* oder *Schnelle Entwicklung* und bietet einen fokussierten Raum für die Ausführung erweiterter Validierungsszenarien.

Neueste Verbesserung: Sie können jetzt mit einem einfacheren, intuitiveren Workflow spezialisierte Testumgebungen für produktionsfremde Pipelines konfigurieren. Das optimierte Setup beschleunigt den Abschluss und verringert Konfigurationsfehler.

Siehe [Hinzufügen einer spezialisierten Testumgebung](/help/implementing/cloud-manager/specialized-test-environment.md).

![Dialogfeld „Umgebung hinzufügen“ mit aktiviertem Optionsfeld „Spezialisierte Testumgebung“](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png)

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [grp-earlyadopter_cs_advtestenvironment@adobe.com](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com).


### Bringen Sie Ihren eigenen Git mit (BYOG) – jetzt mit Unterstützung für Azure DevOps {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Kundinnen und Kunden können nun ihre Azure DevOps-Git-Repositorys in Cloud Manager integrieren, wobei sowohl moderne Azure DevOps- als auch ältere VSTS(Visual Studio Team Services)-Repositorys unterstützt werden.

* Für Edge Delivery Services-Benutzende kann das integrierte Repository zum Synchronisieren und Bereitstellen von Sitecode verwendet werden.
* Für Benutzende von AEM as a Cloud Service und Adobe Managed Services (AMS) kann das Repository mit Fullstack- und Frontend-Pipelines verknüpft werden.

Zusätzliche Pipeline-Typen und die Validierung von Pull-Anfragen durch Code-Qualitäts-Pipelines werden demnächst unterstützt.

Siehe [Hinzufügen von externen Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png)

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com). Geben Sie unbedingt an, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder einer Unternehmens-Repository-Struktur befinden.


**Häufig gestellte Fragen zu BYOG**

| Frage | Antwort |
|---|---|
| *Wie kann ein Projekt bei Bedarf zurück zum von Adobe verwalteten Git-Repository wechseln?* | Das Zurückwechseln ist unkompliziert. [Aktualisieren Sie die Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md), um auf das Adobe-Repository zu verweisen und entfernen Sie das externe Repository, wenn es nicht mehr benötigt wird. |
| *Ist es möglich, verschiedene Repositorys für verschiedene Umgebungen zu konfigurieren (z. B. produktionsfremd gegenüber Produktion), um Tests zuerst in produktionsfremden Umgebungen zu ermöglichen?* | Ja, verschiedene Repositorys können für separate Umgebungen konfiguriert werden. Beispielsweise kann die Qualitäts-Pipeline für Entwicklung oder Code auf ein externes Repository verweisen, während die Produktions-Pipeline mit dem Adobe-Repository verbunden bleibt. Stellen Sie sicher, dass der Synchronisationsauftrag zwischen den beiden Repositorys während dieser Konfiguration aktiv bleibt. |
| *Funktionieren bestehende Einstellungen wie IP-Zulassungslisten weiterhin?* | Ja, bestehende IP-Zulassungslisten funktionieren weiterhin wie gewohnt. Wenn das externe Git-Repository jedoch durch eine Firewall geschützt ist, müssen die erforderlichen [Adobe-IP-Adressen zur Zulassungsliste hinzugefügt werden](/help/implementing/cloud-manager/ip-allow-lists/introduction.md). |
| *Funktionieren alle GitLab-Repository-URLs? Die verwendete Repository-URL folgt dem Format `https://gitlab_dedicated_url.com/path/repo-name.git`, das sich vom Beispiel in der Dokumentation unterscheidet.* | Ja, jedes GitLab-Repository, das API V3 oder V4 unterstützt, wird unterstützt, einschließlich selbst gehosteter GitLab-URLs wie unter [Hinzufügen externer Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md) (`https://git-vendor-name.com/org-name/repo-name.git`) beschrieben. |


#### Zugriffstoken verwalten{#manage-access-tokens}

Verwenden Sie **Zugriffstoken verwalten** in Cloud Manager, um Zugriffstoken in Verbindung mit externen BYOG-Repositorys wie GitHub Enterprise, GitLab, Bitbucket und Azure DevOps anzuzeigen, umzubenennen und zu löschen.

Siehe [Verwalten von Zugriffstoken](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md).

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com).


### Hinzufügen einer Konfigurations-Pipeline für Edge Delivery {#add-eds-pipeline}

Konfigurations-Pipelines werden jetzt für Sites unterstützt, die mit Edge Delivery Services erstellt wurden, sodass diese Funktion über Cloud-Service-Umgebungen hinaus genutzt werden kann. Sie können **Konfigurations-Pipelines** verwenden, um ggf. Einstellungen wie Traffic-Filterregeln und Web Application Firewall (WAF)-Konfigurationen zu verwalten. Siehe [Unterstützte Konfigurationen](/help/operations/config-pipeline.md#configurations).

![„Edge Delivery-Pipeline hinzufügen“ in der Dropdown-Liste „Pipeline hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add.png) *Hinzufügen einer Edge Delivery-Pipeline über die Seite **Programmübersicht**, Karte **Pipelines**.*

![Dialogfeld „Edge Delivery-Pipeline hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add-dialogbox.png) *Dialogfeld „Edge Delivery-Pipeline hinzufügen“*

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com).


## Fehlerbehebungen

* Cloud Manager aktualisiert jetzt bei Umgebungs-Upgrades die freigegebene Version für alle Pipelines, um über alle Pipeline-Typen hinweg für ein konsistentes Versions-Tracking zu sorgen. <!-- CMGR-69043 -->
* Die Benutzeroberfläche zeigt jetzt Status- und detaillierte Fehlermeldungen an, wenn ein SSL-Zertifikat für die Domain-Validierung (DV) fehlschlägt. Das hilft beim Verständnis und der Lösung von Problemen mit Zertifikaten. <!-- CMGR-68872 -->
* Beim Bearbeiten einer Domain-Zuordnung verhindert die Benutzeroberfläche jetzt, dass SSL-Zertifikate ausgewählt werden, die nicht mit der ausgewählten Domain übereinstimmen. Dadurch werden Fehlkonfigurationen reduziert und die Zuverlässigkeit beim Setup wird verbessert. <!-- CMGR-64307 -->
* In einigen Fällen wurden die Zertifikate nicht ordnungsgemäß gelöscht, sodass die Domain weiter aktiv bleibt. <!-- CMGR-69867 -->
* Upgrades von *Adobe Assets* auf *Adobe Assets Ultimate* werden jetzt zuverlässig ausgeführt. Übergänge verlaufen jetzt reibungsloser und zuverlässiger. <!-- CMGR-69506 -->
* Es wurde ein Problem behoben, bei dem Schlüsselregionsfelder beim Erstellen von Umgebungen automatisch mit verschiedenen Regionen festgelegt werden, um nachgelagerte Services und Bereitstellungen reibungslos zu unterstützen. <!-- CMGR-69471 -->
* Es wurde ein Problem behoben, bei dem einige Konfigurations-Pipelines nach der Ausführung nicht ordnungsgemäß angehalten wurden. Pipelines werden nun erfolgreich abgeschlossen und wie erwartet geschlossen, was die Zuverlässigkeit erhöht. <!-- CMGR-69344 -->


<!-- ## Known issues {#known-issues} -->

