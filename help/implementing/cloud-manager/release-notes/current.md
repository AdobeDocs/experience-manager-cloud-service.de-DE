---
title: Versionshinweise für Cloud Manager 2025.9.0
description: Erfahren Sie mehr über Version 2025.9.0 von Cloud Manager in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 8092f18ec350a68bc192a11afbd0ca440f72e282
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 88%

---

# Versionshinweise für Cloud Manager 2025.9.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

Erfahren Sie mehr über Version 2025.9.0 von Cloud Manager in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2025.9.0 von Cloud Manager in AEM as a Cloud Service wurde am Freitag, 4. September 2025 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für den Freitag, 2. Oktober 2025 geplant.

## Neue Funktionen {#what-is-new}

* **Manuelles Verlängern von Adobe-verwalteten Domain-Validierungszertifikaten**

  Sie können jetzt in Adobe verwaltete Domain-Validierungszertifikate (DV) von Cloud Manager oder der öffentlichen API manuell erneuern, um Zertifikate proaktiv zu aktualisieren. <!-- CMGR-68738 -->

  ![Verlängerung des SSL-Zertifikats](/help/implementing/cloud-manager/release-notes/assets/ssl-certificate-adobedv-renew.png)

* **Unterstützung für Azure DevOps (private Repositorys) wurde hinzugefügt**

  Zu den Aktualisierungen der Dokumentation gehören Konfigurationsschritte für Bring Your Own Git with Azure DevOps und die Validierung von Pull-Anfragen. Siehe [Hinzufügen externer Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

* **Bringen Sie Ihre eigene Git-Unterstützung (BYOG) auf Konfigurations-Pipelines (private Repositorys) erweitert**

  Cloud Manager unterstützt jetzt Konfigurations-Pipelines mit privaten Repositorys in GitHub, Bitbucket, Azure DevOps und GitLab. Diese Unterstützung beschleunigt den Entwicklungszyklus weiter. Siehe [Pull-Anforderungsprüfungen für private Repositorys](/help/implementing/cloud-manager/managing-code/github-check-config.md).

<!--
### Staging-Only and Production-Only Pipelines {#staging-production-only-pipelines}

Support for [staging-only and production-only pipelines](/help/implementing/cloud-manager/configuring-pipelines/stage-prod-only.md) has been introduced, enabling you to split full-stack production deployment pipelines into smaller, specialized deployments.

If you are interested in testing this new feature and sharing your feedback, send an email to  `Grp-cloudmanager_splitpipelines@adobe.com` from your email address associated with your Adobe ID. -->


## Beta-Programme {#private-beta-program}

Nehmen Sie am Beta-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor ihrer regulären Veröffentlichung zu erhalten.

Derzeit stehen die folgenden Möglichkeiten zur Verfügung:
<!--
### Support for Custom Author Domains in Cloud Service

AEM Cloud Service is going to soon support one custom domain per Author environment.-->

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

**Neueste Verbesserungen**

* Sie können jetzt mit einem einfacheren, intuitiveren Workflow spezialisierte Testumgebungen für produktionsfremde Pipelines konfigurieren. Die optimierte Einrichtung beschleunigt die Fertigstellung und reduziert Konfigurationsfehler.
* **Inhalt kopieren** wird jetzt in speziellen Testumgebungen unterstützt. Sie können **Inhalt kopieren** jetzt sicher in isolierten Testumgebungen ausführen, die die Produktion spiegeln. <!-- (CMGR‑68900) -->

Siehe [Hinzufügen einer spezialisierten Testumgebung](/help/implementing/cloud-manager/specialized-test-environment.md).

![Dialogfeld „Umgebung hinzufügen“ mit aktiviertem Optionsfeld „Spezialisierte Testumgebung“](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png)

>[!NOTE]
>
>Adobe hat Anfragen zum Beta-Zugriff für spezialisierte Testumgebungen abgeschlossen und eine ausreichende Anzahl von Teilnehmenden erreicht. Die Funktion ist jetzt in Vorbereitung für die allgemeine Verfügbarkeit.

<!--
If you are interested in testing this new feature and sharing your feedback, send an email to [grp-earlyadopter_cs_advtestenvironment@adobe.com](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com) from your email address associated with your Adobe ID. -->


### Bring Your Own Git (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Kundinnen und Kunden können nun ihre Azure DevOps-Git-Repositorys in Cloud Manager integrieren, wobei sowohl moderne Azure DevOps- als auch ältere VSTS(Visual Studio Team Services)-Repositorys unterstützt werden.

* Für Edge Delivery Services-Benutzende kann das integrierte Repository zum Synchronisieren und Bereitstellen von Sitecode verwendet werden.
* Für Benutzende von AEM as a Cloud Service und Adobe Managed Services (AMS) kann das Repository mit Fullstack- und Frontend-Pipelines verknüpft werden.

Zusätzliche Pipeline-Typen und die Validierung von Pull-Anfragen durch Code-Qualitäts-Pipelines werden demnächst unterstützt.

Siehe [Hinzufügen von externen Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png)

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->

**Häufig gestellte Fragen zu BYOG**

| Frage | Antwort |
|---|---|
| *Wie kann ein Projekt bei Bedarf zurück zum von Adobe verwalteten Git-Repository wechseln?* | Das Zurückwechseln ist unkompliziert. [Aktualisieren Sie die Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md), um auf das Adobe-Repository zu verweisen und entfernen Sie das externe Repository, wenn es nicht mehr benötigt wird. |
| *Ist es möglich, verschiedene Repositorys für verschiedene Umgebungen zu konfigurieren (z. B. produktionsfremd gegenüber Produktion), um Tests zuerst in produktionsfremden Umgebungen zu ermöglichen?* | Ja, verschiedene Repositorys können für separate Umgebungen konfiguriert werden. Beispielsweise kann die Qualitäts-Pipeline für Entwicklung oder Code auf ein externes Repository verweisen, während die Produktions-Pipeline mit dem Adobe-Repository verbunden bleibt. Stellen Sie sicher, dass der Synchronisationsauftrag zwischen den beiden Repositorys während dieser Konfiguration aktiv bleibt. |
| *Funktionieren bestehende Einstellungen wie `IP Allow`-Listen weiterhin?* | Ja, bestehende `IP Allow`-Listen funktionieren weiterhin wie gewohnt. Wenn das externe Git-Repository jedoch durch eine Firewall geschützt ist, müssen die erforderlichen [Adobe-IP-Adressen zur Zulassungsliste hinzugefügt werden](/help/implementing/cloud-manager/ip-allow-lists/introduction.md). |
| *Funktionieren alle GitLab-Repository-URLs? Die verwendete Repository-URL folgt dem Format `https://gitlab_dedicated_url.com/path/repo-name.git`, das sich vom Beispiel in der Dokumentation unterscheidet.* | Ja, jedes GitLab-Repository, das API V3 oder V4 unterstützt, wird unterstützt, einschließlich selbst gehosteter GitLab-URLs wie unter [Hinzufügen externer Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md) (`https://git-vendor-name.com/org-name/repo-name.git`) beschrieben. |


#### Zugriffstoken verwalten{#manage-access-tokens}

Verwenden Sie **Zugriffstoken verwalten** in Cloud Manager, um Zugriffstoken in Verbindung mit externen BYOG-Repositorys wie GitHub Enterprise, GitLab, Bitbucket und Azure DevOps anzuzeigen, umzubenennen und zu löschen.

Siehe [Verwalten von Zugriffstoken](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md).

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

### Edge Delivery-Konfigurations-Pipeline hinzufügen {#add-eds-pipeline}

Konfigurations-Pipelines werden jetzt für Sites unterstützt, die mit Edge Delivery Services erstellt wurden, sodass diese Funktion über Cloud-Service-Umgebungen hinaus genutzt werden kann. Sie können **Konfigurations-Pipelines** verwenden, um ggf. Einstellungen wie Traffic-Filterregeln und Web Application Firewall (WAF)-Konfigurationen zu verwalten. Siehe [Unterstützte Konfigurationen](/help/operations/config-pipeline.md#configurations).

**Neueste Verbesserung**

* Edge Delivery-Konfigurations-Pipelines unterstützen jetzt über Cloud Manager-Pipeline-Variablen geheime Daten.
* Edge Delivery Services-Pipelines zeigen in der Spalte **Bereitgestellter Code** jetzt **Konfiguration** an, was die sofortige Identifizierung von Bereitstellungen nur für Konfigurationen ermöglicht. <!-- CMGR‑69681 -->
* Cloud Manager zeigt **Edge Delivery-Pipeline hinzufügen** an, sobald ein Programm mindestens eine Edge Delivery Services-Site und eine zugeordnete Domain enthält. Andernfalls wird die Option deaktiviert angezeigt und in einer QuickInfo wird erklärt, welche Voraussetzungen nicht erfüllt sind. <!-- CMGR‑69680 -->
* Die Registerkarte **Edge Delivery** zeigt ein neues Widget **Edge Delivery-Pipelines**, das den Namen, den Status, das Repository und die Verzweigung jeder Pipeline auflistet. <!-- (CMGR-69052) -->

  ![Edge Delivery-Pipeline-Widget, das Pipeline-Namen, -Status, -Repository und -Verzweigung anzeigt](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-widget.png)

* Im Panel **Filter** wird der Abschnitt **Bereitstellungstyp** hinzu, der die Kontrollkästchen **Edge-Bereitstellung** und **Veröffentlichungsbereitstellung** enthält. <!-- (CMGR-69682) -->

  ![Filterbedienfeld, das den neuen Bereitstellungstyp der Edge-Bereitstellung und der Veröffentlichungsbereitstellung anzeigt](/help/implementing/cloud-manager/release-notes/assets/filter-delivery-type.png)

![„Edge Delivery-Pipeline hinzufügen“ in der Dropdown-Liste „Pipeline hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add.png) *Hinzufügen einer Edge Delivery-Pipeline über die Seite **Programmübersicht**, Karte **Pipelines**.*

![Dialogfeld „Edge Delivery-Pipeline hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add-dialogbox.png) *Dialogfeld „Edge Delivery-Pipeline hinzufügen“.*

Siehe [Pipeline von Edge Delivery hinzufügen](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md)

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com).

## Fehlerbehebungen {#bug-fixes}

In der Cloud Manager-Version vom September gibt es keine signifikanten Fehlerbehebungen.


<!-- ## Known issues {#known-issues} -->

