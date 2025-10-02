---
title: Versionshinweise für Cloud Manager 2025.10.0
description: Erfahren Sie mehr über Version 2025.10.0 von Cloud Manager in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 4acedba631b3732b989794c648079356f9b79fdd
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 64%

---

# Versionshinweise für Cloud Manager 2025.10.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

Erfahren Sie mehr über Version 2025.10.0 von Cloud Manager in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2025.10.0 von Cloud Manager in AEM as a Cloud Service wurde am Freitag, 2. Oktober 2025 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für den Freitag, 6. November 2025 geplant.

## Neue Funktionen {#what-is-new}

* **AEM Cloud Health Assessment Service**

  Adobe führt den AEM Cloud Health Assessment Service ein, ein automatisiertes, nicht-invasives Checkup-Tool, das Ihre AEM as a Cloud Service-Umgebung optimiert, sicher und mit Best Practices abgestimmt hält.

  Dieser Service bietet folgende Funktionen:

   * Durchsucht Umgebungen nach Performance-Engpässen, Ineffizienzen und potenziellen Risiken.
   * Analysiert Inhaltsstrukturen (Blueprints, Live Copies) und benutzerdefinierte Konfigurationen.
   * Identifiziert veraltete Abhängigkeiten (AEM SDK, Drittanbieterbibliotheken).
   * Kennzeichnet Probleme mit der Code-Qualität (falsche Anmerkungen, ineffiziente Muster).
   * Stellt verwertbare Anleitungen über Dashboards wie **Action Center** bereit.
   * Unterstützt die proaktive Optimierung durch frühzeitige Erkennung und Behebung von Problemen.

  Teams können ihre AEM-Umgebungen kontinuierlich überwachen und verbessern, um eine reibungslosere Leistung, mehr Sicherheit und langfristige Wartungsfreundlichkeit zu erzielen.

  Siehe [Health Assessment for Production and Staging Environments](/help/implementing/cloud-manager/reports/report-health-assessment.md).

* **Pipeline-Unterstützung konfigurieren**

  Konfigurations-Pipelines werden jetzt für Sites unterstützt, die mit Edge Delivery Services erstellt wurden, sodass diese Funktion über Cloud-Service-Umgebungen hinaus genutzt werden kann. Sie können **Konfigurations-Pipelines** verwenden, um ggf. Einstellungen wie Traffic-Filterregeln und Web Application Firewall (WAF)-Konfigurationen zu verwalten. Siehe [Unterstützte Konfigurationen](/help/operations/config-pipeline.md#configurations).

  Edge Delivery-Konfigurations-Pipelines unterstützen über Cloud Manager-Pipeline-Variablen auch Geheimnisse.

  Siehe [Edge Delivery-Pipeline hinzufügen](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).

* **Das Dialogfeld „Domain Mapping-CDN Setup“ wurde optimiert**

  Cloud Manager hat den Fluss **Domain zu CDN zuordnen** vereinfacht, um Verwirrung zu stiften und die Konfiguration zu beschleunigen. Das Dialogfeld betont jetzt das von **Adobe verwaltete CDN** (mit dem Badge „Recommended„).

  ![Dialogfeld „Domain dem CDN zuordnen“ mit aktiviertem Optionsfeld „Von Adobe verwaltetes CDN“](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-dialog-box-adobe-managed-cdn.png).

  Siehe [Hinzufügen einer Domain-Zuordnung](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md).

  Das Dialogfeld enthält auch eine einzelne, knappe Checkliste für die Karte **Andere CDN-Anbieter** mit Schwerpunkt auf Anleitungsinhalten mit den folgenden Inhalten:

   * Verweisen Sie Ihren CDN-Ursprung auf `publish-p<PROGRAM_ID>-e<ENV_ID>.adobeaemcloud.com`.
   * Setzen Sie **Host/SNI** auf den ursprünglichen Host.
   * Fügen Sie `X-AEM-Edge-Key` hinzu (nach Bereitstellung des Schlüssels in Cloud Manager).
   * `X-Forwarded-Host` Sie auf Ihre kundenorientierte Domain.
   * Löschen Sie andere `X-Forwarded-*`, bevor Sie AEM erreichen.

  ![Dialogfeld „Domain dem CDN zuordnen“ mit aktiviertem Optionsfeld „Andere CDN-Anbieter“](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-dialog-box-other-cdn-provider.png)

  <!-- (no redundant `Origin` field or "Learn more" clutter) -->Die zugehörige Fußzeile enthält zwei hilfreiche Links: Beispielkonfigurationen für gängige CDNs und einen Link zur vollständigen Dokumentation. Eine einzige Bestätigungsschaltfläche - Ich habe mein CDN konfiguriert - vervollständigt den Fluss.

  Siehe [CDN in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#point-to-point-CDN).

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

### Erweiterbarkeit und Anpassung von Experience Hub {#exp-hub-extensibility}

[Experience Hub](/help/experience-hub.md) dient als Einstiegspunkt für AEM, angepasst an die Anforderungen Ihres Unternehmens. Teilen Sie Adobe Ihre bestehenden Erweiterungen der AEM-Benutzeroberfläche mit, damit Sie sie mit minimalem Aufwand in Experience Hub aktivieren können.

![Abbildung des Erweiterbarkeits- und Anpassungs-Workflows von Experience Hub](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

Betten Sie benutzerdefinierte Erlebnisse in Experience Hub ein, um das Dashboard Ihres Unternehmens zu erweitern und zu personalisieren. Zusätzlich zu den integrierten Widgets von Adobe können Sie Ihre eigenen mit dem [UI Extensibility](https://developer.adobe.com/uix/docs/)-Framework hinzufügen. Erstellen Sie JavaScript-basierte Benutzeroberflächen-Apps und stellen Sie sie Ihren Benutzern zur Verfügung, um geschäftsspezifische Anforderungen und Workflows zu erfüllen.

Sie interessieren sich für die Beta-Version? Senden Sie eine E-[&#x200B; an &#x200B;](mailto:beta_exphubextensibility@adobe.com)beta_exphubextensibility@adobe.commit Ihrer Adobe-OrgID und einer kurzen Beschreibung der Anpassung, die Sie erstellen möchten.

### Schnellere Builds mit Modul-Caching {#quick-build-cm-pipelines}

Ein neues Build-Modell kompiliert nur geänderte Module (und nicht das gesamte Repository) mithilfe des Caching auf Modulebene, um die Erstellungszeiten zu verkürzen. Sie gilt für Pipelines in Code-Qualität, mit vollem Stapel und nur Staging.

Interessiert? Senden Sie eine E-Mail an [0&rbrace;beta_quickbuild_cmpipelines@adobe.com&quot; mit Ihrer Adobe-OrgID und Programm-ID.](mailto:beta_quickbuild_cmpipelines@adobe.com)

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline Variables in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).-->



### Rollback mit einem Klick bei Pipeline-Bereitstellungen {#one-click-rollback}

Kehren Sie schnell zu einer vorherigen Bereitstellung zurück, wenn der neueste kundenspezifische Quell-Code nicht wie erwartet funktioniert. Dabei ist es nicht erforderlich, die vollständige Pipeline erneut auszuführen oder Commits manuell zurückzusetzen.<!--https://jira.corp.adobe.com/browse/CMGR-69556 -->

![Stellen Sie kundenspezifischen Quell-Code über die Karte „Umgebungen“ &#x200B;](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed.png)*Karte „Umgebungen“ oben mit der Option **Wiederherstellen**>**Zuvor bereitgestellter Code**&#x200B;für eine ausgewählte Umgebung wieder her.*

![Dialogfeld „Zuvor bereitgestellten Code wiederherstellen“](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed-dialogbox.png)
*Überprüfen Sie im Dialogfeld **Zuvor bereitgestellten Code wiederherstellen**&#x200B;die aktuell bereitgestellte Version sowie die Version, die Sie wiederherstellen möchten, und klicken Sie dann auf **Bestätigen***.

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


## Fehlerbehebungen {#bug-fixes}

Es gibt keine signifikanten Fehlerbehebungen in der Cloud Manager-Version vom Oktober.


<!-- ## Known issues {#known-issues} -->

