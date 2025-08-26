---
title: Versionshinweise für Cloud Manager 2025.8.0
description: Erfahren Sie mehr über Version 2025.8.0 von Cloud Manager in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 8bd6fd4a7abcfbf37ba8aa458a9d2a035cca050e
workflow-type: tm+mt
source-wordcount: '1403'
ht-degree: 93%

---

# Versionshinweise für Cloud Manager 2025.8.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

Erfahren Sie mehr über Version 2025.8.0 von Cloud Manager in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2025.8.0 von Cloud Manager in AEM as a Cloud Service wurde am 7. August 2025 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für den 4. September 2025 geplant.

## Neue Funktionen {#what-is-new}

* **Adobe Experience Hub in Kürze verfügbar**

  Ab dem 19. August 2025 beginnt Adobe mit dem schrittweisen Rollout des neuen Experience Hub für alle Adobe Experience Manager-Benutzer.

  Experience Hub ist ein einheitlicher Ausgangspunkt, der personalisierte, kontextuelle Erlebnisse bereitstellt, mit denen Benutzende Ziele schneller erreichen können. Der Rollout endet am 26. August 2025, sodass er für alle Benutzer verfügbar ist. Die neue Experience Hub ist direkt unter [experience.adobe.com](https://experience.adobe.com/) verfügbar. Weitere Informationen finden Sie unter [Adobe Experience Hub](/help/experience-hub.md).

* **Die Edge Delivery Services-Lizenz kann im Self-Service in ein HIPAA-Programm aufgenommen werden**

  Unternehmen, die Gesundheitsdaten oder vertrauliche Daten schützen müssen, können Edge Delivery Services jetzt im Self-Service verwenden, was die HIPAA-Konformität und die Einhaltung strikter regulatorischer Vorgaben ermöglicht. <!-- CMGR-70016 -->

* **BYOG ist jetzt für Edge Delivery Services verfügbar**

  Mit Cloud Manager können Sie jetzt externe Git-Repositorys konfigurieren, was flexible Code-Management-Workflows ermöglicht. <!--(CMGR‑69010, CMGR‑70988) --> Außerdem können Sie Code aus einer ausgewählten Verzweigung direkt in der Cloud Manager-Benutzeroberfläche abrufen, wodurch manuelle Repository-Aufgaben reduziert werden. Siehe [Konfigurieren einer Edge Delivery-Site zur Verwendung eines externen Git-Repositorys](/help/implementing/cloud-manager/edge-delivery/config-edge-delivery-site-with-byog.md) <!-- (CMGR‑68085)(CMGR-69015) --> <!-- KT: https://wiki.corp.adobe.com/display/DMSArchitecture/%5B2025%5D+Cloud+Manager+-+Bring+Your+Own+Git+with+EDS -->

* **Automatisierte Bereitstellung für das neue Forms-Add-on**

  Kundenunternehmen, die nur Sites verwenden, benötigen häufig eine einfache, kostengünstige Methode zum Erstellen von Marketing-Formularen. Das neue AEM Forms Sites-Add-on erfüllt diese Anforderungen, indem es einem Sites-Programm eingeschränkte Forms-Funktionen hinzufügt. Außerdem wird ein klarer Upgrade-Pfad zum vollständigen AEM Forms-Angebot geschaffen. <!-- (CMGR-64301) --> <!-- KT: CMGR Provisioning Support for AEM Forms Sites Add-On SKU https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3578379797 -->

  Das Add-on:
   * wird an ein Sites-Programm angehängt und neben diesem bereitgestellt – kein separates Forms-Programm und keine Berechtigung erforderlich.
   * erfüllt einfache Anwendungsszenarien für Marketing-Formualre.
   * wird bei der Erstellung oder Bearbeitung eines Produktionsprogramms nur in der Liste **Lösungen und Add-ons** aufgeführt, wenn die IMS-Organisation verfügbare Forms-Add-on-Lizenzen besitzt.

     ![Forms-Add-ons](/help/implementing/cloud-manager/release-notes/assets/forms-add-on.png) *Das Forms-Add-on kann nur im Programm hinzugefügt werden, wenn in Ihrer IMS-Organisation Lizenzen für das Forms-Add-on verfügbar sind.*

     ![Forms-Add-on in „Lösungen und Add-ons“ beim Erstellen eines Produktionsprogramms](/help/implementing/cloud-manager/release-notes/assets/forms-add-on-creating-production-program.png) *Bei der Programmerstellung können Sie das Forms-Add-on innerhalb der Sites-Lösung auswählen.*

     ![Forms-Add-on beim Bearbeiten eines Produktionsprogramms](/help/implementing/cloud-manager/release-notes/assets/forms-add-on-editing-production-program.png) *Wählen Sie unter **Programm bearbeiten**&#x200B;das Forms-Add-on für das Sites-Programm aus und führen Sie dann die Pipeline aus, um sie in den Umgebungen zu aktivieren.*

     Weitere Informationen finden Sie unter [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).

## Beta-Programme {#private-beta-program}

Nehmen Sie am Beta-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor ihrer regulären Veröffentlichung zu erhalten.

Derzeit stehen die folgenden Möglichkeiten zur Verfügung:

### Rollback mit einem Klick bei Pipeline-Bereitstellungen {#one-click-rollback}

Kehren Sie schnell zu einer vorherigen Bereitstellung zurück, wenn der neueste kundenspezifische Quell-Code nicht wie erwartet funktioniert. Dabei ist es nicht erforderlich, die vollständige Pipeline erneut auszuführen oder Commits manuell zurückzusetzen.<!--https://jira.corp.adobe.com/browse/CMGR-69556 -->

![Stellen Sie kundenspezifischen Quell-Code über die Karte „Umgebungen“ ](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed.png)*Karte „Umgebungen“ oben mit der Option **Wiederherstellen**>**Zuvor bereitgestellter Code**&#x200B;für eine ausgewählte Umgebung wieder her.*

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
>Adobe hat Anfragen zum Beta-Zugriff für spezialisierte Testumgebungen abgeschlossen und eine ausreichende Anzahl von Teilnehmern erreicht. Die Funktion ist jetzt in Vorbereitung auf die allgemeine Verfügbarkeit.

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

### Hinzufügen einer Konfigurations-Pipeline für Edge Delivery {#add-eds-pipeline}

Konfigurations-Pipelines werden jetzt für Sites unterstützt, die mit Edge Delivery Services erstellt wurden, sodass diese Funktion über Cloud-Service-Umgebungen hinaus genutzt werden kann. Sie können **Konfigurations-Pipelines** verwenden, um ggf. Einstellungen wie Traffic-Filterregeln und Web Application Firewall (WAF)-Konfigurationen zu verwalten. Siehe [Unterstützte Konfigurationen](/help/operations/config-pipeline.md#configurations).

**Neueste Verbesserung**

* Edge Delivery Services-Pipelines zeigen in der Spalte **Bereitgestellter Code** jetzt **Konfiguration** an, was die sofortige Identifizierung von Bereitstellungen nur für Konfigurationen ermöglicht. <!-- CMGR‑69681 -->
* Cloud Manager zeigt **Edge Delivery-Pipeline hinzufügen** an, sobald ein Programm mindestens eine Edge Delivery Services-Site und eine zugeordnete Domain enthält. Andernfalls wird die Option deaktiviert angezeigt und in einer QuickInfo wird erklärt, welche Voraussetzungen nicht erfüllt sind. <!-- CMGR‑69680 -->
* Die Registerkarte **Edge Delivery** zeigt ein neues Widget **Edge Delivery-Pipelines**, das den Namen, den Status, das Repository und die Verzweigung jeder Pipeline auflistet. <!-- (CMGR-69052) -->

  ![Edge Delivery-Pipeline-Widget, das Pipeline-Namen, -Status, -Repository und -Verzweigung anzeigt](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-widget.png)

* Im Panel **Filter** wird der Abschnitt **Bereitstellungstyp** hinzu, der die Kontrollkästchen **Edge-Bereitstellung** und **Veröffentlichungsbereitstellung** enthält. <!-- (CMGR-69682) -->

  ![Filterbedienfeld, das den neuen Bereitstellungstyp der Edge-Bereitstellung und der Veröffentlichungsbereitstellung anzeigt](/help/implementing/cloud-manager/release-notes/assets/filter-delivery-type.png)

![„Edge Delivery-Pipeline hinzufügen“ in der Dropdown-Liste „Pipeline hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add.png) *Hinzufügen einer Edge Delivery-Pipeline über die Seite **Programmübersicht**, Karte **Pipelines**.*

![Dialogfeld „Edge Delivery-Pipeline hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add-dialogbox.png) *Dialogfeld „Edge Delivery-Pipeline hinzufügen“*

Siehe [Pipeline von Edge Delivery hinzufügen](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md)

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com).


## Fehlerbehebungen

* Pipelines stellen Variablen jetzt nur noch für die aktive Edge Delivery Services-Domain-Konfiguration bereit und überspringen dabei Konfigurationen, die während der Pipeline-Neuerstellung entfernt wurden. <!-- (CMGR‑70039) -->
* Die Pipeline-Ausführung startet jetzt zuverlässig. Es wurde ein Problem behoben, bei dem einige Pipelines aufgrund interner Fehler bei der Ressourcenverarbeitung nicht gestartet werden konnten. <!-- (CMGR‑58167) -->
* Die Inhaltskopie überprüft Cloud Manager-Berechtigungen und blockiert Starts, wenn Benutzende keine Deployment Manager- oder Administratorrechte haben. <!-- (CMGR‑62097) -->


<!-- ## Known issues {#known-issues} -->

