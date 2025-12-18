---
title: Versionshinweise für Cloud Manager 2025.12.0
description: Erfahren Sie mehr über Version 2025.12.0 von Cloud Manager in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 7c1f1f1022fd63c190a493d312ab1f355859d15a
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 61%

---

# Versionshinweise für Cloud Manager 2025.12.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

Erfahren Sie mehr über Version 2025.12.0 von Cloud Manager in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2025.12.0 von Cloud Manager in AEM as a Cloud Service wurde am Donnerstag, dem Freitag, 4. Dezember 2025 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für den Freitag, 22. Januar 2026 geplant.

## Neue Funktionen - Experience Hub {#experience-hub-whats-new}

* **Vereinfachter Zugriff auf Experience Hub**

  Die Auswahl der Benutzerrolle wurde entfernt und ein Handbuch für die Auswahl **Voreinstellung** (Inhaltsautor, Asset-Bibliothekarin, Admin und IT) hinzugefügt.

* **Ankündigungen** und **Produktaktualisierungen**

  Sie können zwischen den verfügbaren Ankündigungen wechseln und iterieren, sie aber auch verwerfen.

* **Zuletzt verwendet**

  Zusätzliche Seiten und Ressourcen, einschließlich Seiteneditor, Assets, Programmen und Details zur Pipeline-Ausführung sowie Sicherheitsseiten werden jetzt unterstützt.

* **Programmliste**

  Anzeige der AEM Cloud Manager-Programme in Ihrer Organisation mit Schnellzugriff auf die Cloud Manager-Detailseite.

* **AEM Guides**

  Schnellzugriff und Tastaturbefehl für die Authoring-Umgebungen, in denen AEM Guides-Add-ons aktiviert sind.

## Neue Funktionen - Cloud Manager {#cloud-manager-whats-new}

* **Verbesserte Stabilität, Leistung und Zuverlässigkeit**

  Diese Version umfasst Optimierungs- und Wartungsaktualisierungen, die die Stabilität, Leistung und Zuverlässigkeit von Cloud Manager verbessert haben.

* **Spezialisierte Testumgebung**

  >[!NOTE]
  >
  >Spezielle Testumgebungen können jetzt erworben werden. Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um eine Bestellung aufzugeben.

  Cloud Manager unterstützt jetzt das Hinzufügen eines neuen Umgebungstyps namens **Spezialisierte Testumgebung**. Diese Umgebung soll Teams dabei helfen, Funktionen vor der Live-Schaltung unter produktionsnahen Bedingungen zu validieren. Dieser Umgebungstyp unterscheidet sich von *Produktion + Staging*, *Entwicklung* oder *Schnelle Entwicklung* und bietet einen fokussierten Raum für die Ausführung erweiterter Validierungsszenarien.

  Siehe [Hinzufügen einer spezialisierten Testumgebung](/help/implementing/cloud-manager/specialized-test-environment.md).

  ![Dialogfeld „Umgebung hinzufügen“ mit aktiviertem Optionsfeld „Spezialisierte Testumgebung“](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png)

<!--
>[!NOTE]
>
>Adobe has closed beta access requests for Specialized Testing Environments, having reached a sufficient number of participants. The feature is now in preparation for general availability.

If you are interested in testing this new feature and sharing your feedback, send an email to [grp-earlyadopter_cs_advtestenvironment@adobe.com](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com) from your email address associated with your Adobe ID. -->


* **Ein-Klick-Rollback für Pipeline-Bereitstellungen**

  Kehren Sie schnell zu einer vorherigen Bereitstellung zurück, wenn der neueste Kunden-Quell-Code nicht wie erwartet funktioniert. Es ist nicht erforderlich, die vollständige Pipeline erneut auszuführen oder Commits manuell rückgängig zu machen. <!--https://jira.corp.adobe.com/browse/CMGR-69556 -->

  Siehe [Wiederherstellen des vorherigen in AEM as a Cloud Service bereitgestellten Codes](/help/operations/restore-previous-code-deployed.md).

  Siehe auch [Wiederherstellung von Content in AEM as a Cloud Service](/help/operations/restore.md).

* **Self-Service-WAF-Setup für Edge Delivery Services**

  Wenn Sie ein Edge Delivery Services-Programm in Cloud Manager erstellen, können Sie die Web Application Firewall (WAF) aktivieren. Diese Einstellung schützt Ihre Site sofort vor bösartigem Traffic und DDoS-Angriffen, wodurch der manuelle Einrichtungsaufwand reduziert wird.

  Siehe [Erstellen Ihrer ersten Edge Delivery-Site mit einem Klick](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md).


## Beta-Programme {#private-beta-program}

Nehmen Sie am Beta-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor ihrer regulären Veröffentlichung zu erhalten.

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (durch Adobe Support Services oder anderweitig). Adobe empfiehlt Kunden, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

Siehe auch [AEM Beta-Programme](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs)

Derzeit stehen die folgenden Möglichkeiten zur Verfügung:
<!--
### Support for Custom Author Domains in Cloud Service

AEM Cloud Service is going to soon support one custom domain per Author environment.-->

### Erweiterbarkeit und Anpassung von Experience Hub {#exp-hub-extensibility}

[Experience Hub](/help/experience-hub.md) dient als Einstiegspunkt für AEM und ist an die Anforderungen Ihres Unternehmens angepasst. Teilen Sie Adobe Ihre bestehenden Erweiterungen der AEM-Benutzeroberfläche mit, damit Sie sie mit minimalem Aufwand in Experience Hub aktivieren können.

![Diagramm des Erweiterbarkeits- und Anpassungs-Workflows von Experience Hub](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

Betten Sie benutzerdefinierte Erlebnisse in Experience Hub ein, um das Dashboard Ihres Unternehmens zu erweitern und zu personalisieren. Zusätzlich zu den integrierten Widgets von Adobe können Sie Ihre eigenen mit dem Framework für die [Erweiterbarkeit der Benutzeroberfläche](https://developer.adobe.com/uix/docs/) hinzufügen. Erstellen Sie auf JavaScript basierte Benutzeroberflächen-Apps und stellen Sie sie Ihren Benutzenden zur Verfügung, um geschäftsspezifische Anforderungen und Workflows zu erfüllen.

Sie interessieren sich für die Beta-Version? Senden Sie eine E-Mail an [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) mit Ihrer Adobe-OrgID und einer kurzen Beschreibung der Anpassung, die Sie vornehmen möchten.

### Schnellere Builds mit Modul-Caching {#quick-build-cm-pipelines}

Ein neues Build-Modell kompiliert nur geänderte Module (nicht das gesamte Repository) mithilfe des Caching auf Modulebene, um die Erstellungszeiten zu verkürzen. Es kann für Code-Qualitäts-, Full-Stack- und reine Staging-Pipelines angewendet werden.

![Dialogfeld „Produktionsfremde Pipeline bearbeiten“ mit den beiden Optionen für die Build-Strategie „Vollständiger Build“ und „Intelligenter Build“](/help/implementing/cloud-manager/release-notes/assets/non-production-pipeline-edit.png)
*Dialogfeld „Produktionsfremde Pipeline bearbeiten“ mit den beiden Optionen für die Build-Strategie „Vollständiger Build“ und „Intelligenter Build“.*

Im Dialogfeld **Pipeline hinzufügen/bearbeiten** auf der Registerkarte **Source-Code** können Sie mit dem Abschnitt **Erstellen-Strategie** eine der folgenden Build-Optionen auswählen:

* **Vollständiger Build** - Erstellt bei jeder Ausführung alle Module im Repository.
* **Smarter Build** - Erstellt nur Module, die seit dem letzten Commit geändert wurden, was die Erstellungszeit insgesamt verkürzt.

Sie steuern, welche Pipelines „Smart **Build“**. Während der Beta-Phase wird diese Option nur für Pipelines **Code-Qualität** und **Bereitstellung durch Entwicklung** angezeigt.

Sie sind interessiert? Senden Sie eine E-Mail an [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) mit Ihrer Adobe-OrgID und Programm-ID.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline Variables in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).-->

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

In der Cloud Manager-Version vom Dezember 2025 gibt es keine signifikanten Fehlerbehebungen.


<!-- ## Known issues {#known-issues} -->

