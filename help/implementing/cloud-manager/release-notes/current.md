---
title: Versionshinweise für Cloud Manager 2025.6.0
description: Erfahren Sie mehr über Cloud Manager 2025.6.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 9e2be3cabe0a93e6e357ceb5ecf4950c25d034d0
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 33%

---

# Versionshinweise für Cloud Manager 2025.6.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

Erfahren Sie mehr über Cloud Manager 2025.6.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2025.6.0 von Cloud Manager in AEM as a Cloud Service wurde am Donnerstag, den Freitag, 5. Juni 2025 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für Donnerstag, den Freitag, 10. Juli 2025 geplant.

## Neue Funktionen {#what-is-new}

* **(UI) License Dashboard enthält jetzt Edge Delivery Services-Lizenz**

  Die Lizenznutzung von Edge Delivery Services wird jetzt im Lizenz-Dashboard angezeigt, sodass Sie Ihre Berechtigungen und den Status besser einsehen können. <!-- CMGR-67686 -->

  ![Lizenz-Dashboard](/help/implementing/cloud-manager/assets/license-dashboard.png)

  Siehe [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

* **(UI) Edge Delivery-Site-Konfiguration aktualisiert**

  Der Arbeitsablauf für das Hinzufügen einer Edge Delivery-Site wurde vereinfacht, indem die **Edge Delivery-Herkunft** anstelle der **Repository-URL** angefordert wurde, wodurch Onboarding und Einrichtung schneller und intuitiver <!-- CMGR-67686 --> werden

  ![Dialogfeld &quot;Edge Delivery-Site hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/add-edge-delivery-site.png)

  Siehe [Hinzufügen einer Edge Delivery-Site](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md).

* **(UI) Pipeline-Favoriten**

  In dieser Version bietet Cloud Manager die Möglichkeit, Favoriten-Pipelines anzuheften, sodass Sie bestimmte Pipelines als Favoriten markieren können, sodass sie oben in der Liste auf der Seite **Pipelines** angezeigt werden. Diese Verbesserung erleichtert das Auffinden und Ausführen häufig verwendeter Pipelines. <!-- CMGR-68293 -->

  ![Pipelines, die als Favoriten markiert sind](/help/implementing/cloud-manager/release-notes/assets/pipeline-favorites.png) *Zwei Pipelines, die als Favoriten markiert sind.*

  Siehe [Pipeline-Favoriten markieren](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipeline-favorites).


## Early-Adopter-Programm {#early-adoption}

Nehmen Sie am Early-Adopter-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor ihrer regulären Veröffentlichung zu erhalten.

Derzeit stehen die folgenden Möglichkeiten für eine frühzeitige Verwendung zur Verfügung:


### Zugriffstoken verwalten{#manage-access-tokens}

Verwenden Sie die Funktion **Zugriffs-Token verwalten** in Cloud Manager, um Zugriffs-Token anzuzeigen, umzubenennen und zu löschen, die mit externen Bring-Your-Own-Git-Repositorys verknüpft sind, z. B. GitHub Enterprise, GitLab, Bitbucket und Azure DevOps.

Siehe [Verwalten von Zugriffstoken](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md)

Wenn Sie diese neue Funktion testen und Ihr Feedback geben möchten, senden Sie über Ihre mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an .


### Spezialisierte Testumgebung {#specialized-test-environment}

Cloud Manager unterstützt jetzt das Hinzufügen eines neuen Umgebungstyps namens &quot;**Testumgebung**. Die Umgebung soll Teams dabei helfen, Funktionen vor der Live-Schaltung unter produktionsnahen Bedingungen zu validieren. Dieser Umgebungstyp unterscheidet sich von *Produktion + Staging*, *Entwicklung* oder *Schnelle Entwicklung* und bietet einen fokussierten Raum für die Ausführung erweiterter Validierungsszenarien.

Siehe [Hinzufügen einer speziellen Testumgebung](/help/implementing/cloud-manager/specialized-test-environment.md).

![Dialogfeld „Umgebung hinzufügen“ mit aktiviertem Optionsfeld „Spezielle Testumgebung“](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png)

Wenn Sie diese neue Funktion testen und Ihr Feedback geben möchten, senden Sie von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse eine E-[&#128279;](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com) an grp-earlyadopter_cs_advtestenvironment@adobe.com.


### Bringen Sie Ihren eigenen Git mit – jetzt mit Unterstützung für Azure DevOps {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Kundinnen und Kunden können nun ihre Azure DevOps-Git-Repositorys in Cloud Manager integrieren, wobei sowohl moderne Azure DevOps- als auch ältere VSTS(Visual Studio Team Services)-Repositorys unterstützt werden.

* Für Edge Delivery Services-Benutzende kann das integrierte Repository zum Synchronisieren und Bereitstellen von Sitecode verwendet werden.
* Für Benutzende von AEM as a Cloud Service und Adobe Managed Services (AMS) kann das Repository mit Fullstack- und Frontend-Pipelines verknüpft werden.

Zusätzliche Pipeline-Typen und die Validierung von Pull-Anfragen durch Code-Qualitäts-Pipelines werden demnächst unterstützt.

Siehe [Hinzufügen von externen Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png)

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com). Geben Sie unbedingt an, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder einer Unternehmens-Repository-Struktur befinden.


#### Häufig gestellte Fragen zu Bring Your Own Git

| Frage | Antwort |
|---|---|
| *Wie kann ein Projekt bei Bedarf zurück zum von Adobe verwalteten Git-Repository wechseln?* | Ein Zurückwechseln ist unkompliziert. [Aktualisieren Sie die Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md), um auf das Adobe-Repository zu verweisen, und entfernen Sie das externe Repository, wenn es nicht mehr benötigt wird. |
| *Ist es möglich, verschiedene Repositorys für verschiedene Umgebungen zu konfigurieren (z. B. Nicht-Produktion versus Produktion), um Tests zuerst in Nicht-Produktion zu ermöglichen?* | Ja, verschiedene Repositorys können für separate Umgebungen konfiguriert werden. Beispielsweise kann die Entwicklungs- oder Code-Qualitäts-Pipeline auf ein externes Repository verweisen, während die Produktions-Pipeline mit dem Adobe-Repository verbunden bleibt. Stellen Sie sicher, dass der Synchronisierungsauftrag zwischen den beiden Repositorys während dieser Konfiguration aktiv bleibt. |
| *Funktionieren bestehende Einstellungen wie IP-Zulassungslisten weiterhin?* | Ja, bestehende IP-Zulassungslisten funktionieren weiterhin wie gewohnt. Wenn das externe Git-Repository jedoch durch eine Firewall geschützt ist, müssen die erforderlichen [Adobe-IP-Adressen zur Zulassungsliste hinzugefügt werden](/help/implementing/cloud-manager/ip-allow-lists/introduction.md). |
| *Funktionieren alle GitLab-Repository-URLs? Die verwendete Repository-URL folgt dem Format `https://gitlab_dedicated_url.com/path/repo-name.git`, das sich vom Beispiel in der Dokumentation unterscheidet.* | Ja, jedes GitLab-Repository, das API V3 oder V4 unterstützt, wird unterstützt, einschließlich selbst gehosteter GitLab-URLs wie unter [Hinzufügen externer Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md) (`https://git-vendor-name.com/org-name/repo-name.git`) beschrieben. |


### Edge Delivery-Konfigurations-Pipeline hinzufügen {#add-eds-pipeline}

Konfigurations-Pipelines werden jetzt für Sites unterstützt, die mit Edge Delivery Services erstellt wurden, wodurch diese Funktion über Cloud Service-Umgebungen hinaus erweitert wird. Sie können **Konfigurations-Pipelines** verwenden, um Einstellungen wie Traffic-Filterregeln und gegebenenfalls Konfigurationen der Web Application Firewall (WAF) zu verwalten. Siehe [Unterstützte Konfigurationen](/help/operations/config-pipeline.md#configurations).

![Edge Delivery-Pipeline hinzufügen in der Dropdown-Liste „Pipeline hinzufügen](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add.png) *Hinzufügen einer Edge Delivery-Pipeline von der **Programmübersicht**&#x200B;Seite,**Pipelines**.*

![Dialogfeld &quot;Edge Delivery-Pipeline hinzufügen](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add-dialogbox.png) *Dialogfeld &quot;Edge Delivery-Pipeline hinzufügen“*

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com).


## Fehlerbehebungen

* Sandbox-Umgebungen, die zuvor als `HIBERNATED` gekennzeichnet waren, bleiben in diesem Status nicht mehr hängen, sodass die Pipeline-Ausführung oder -Bereitstellung erwartungsgemäß fortgesetzt werden kann. <!-- CMGR-67705 -->
* AEM Cloud Manager ordnet jetzt Maven-Build-Fehler, die durch 409-Fehler (Konflikte) verursacht wurden, beim Abrufen von Kundenartefakten korrekt einem kundenbedingten Fehler zu. Diese Änderung verbessert das Fehlermeldungssystem, indem zwischen internen Fehlern und Problemen im Zusammenhang mit der Einrichtung der Kundenumgebung unterschieden wird. <!-- CMGR-66673 -->


<!-- ## Known issues {#known-issues} -->

