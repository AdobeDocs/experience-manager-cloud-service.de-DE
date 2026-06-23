---
title: Einführung in Edge Delivery Services in Cloud Manager
description: Erfahren Sie, wie Sie Ihre Cloud Manager-Projekte mit Edge Delivery Services bereitstellen.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 069e94e230b856fba15c3f465c966a5bf6b0ac46
workflow-type: tm+mt
source-wordcount: '1474'
ht-degree: 47%

---


# Einführung in Edge Delivery Services in Cloud Manager {#edge-delivery-services}

Edge Delivery Services ist ein zusammenstellbarer Satz von Services, der eine hohe Flexibilität bei der Erstellung von Inhalten auf Ihrer Website ermöglicht. Dadurch können Sie:

* schnelle Websites mit einer perfekten Lighthouse-Bewertung erstellen,
* die Leistung durch betriebliche Telemetrie kontinuierlich überwachen,
* die Autoreneffizienz durch Entkopplung von Inhaltsquellen erhöhen.

Sie können sowohl das AEM-Content-Management und WYSIWYG-Authoring mit dem universellen Editor als auch das dokumentenbasierte Authoring verwenden.

Mit Cloud Manager in AEM as a Cloud Service können Sie die Edge Delivery Services für Ihr Projekt aktivieren.

>[!TIP]
>
>Weitere Informationen zu Edge Delivery Services und zur Verwendung mit AEM finden Sie unter [Überblick über Edge Delivery Services](/help/edge/overview.md#how-does-it-work).

## Über Edge Delivery Services in Cloud Manager {#edge-in-cloud-manager}

Wenn Sie Edge Delivery Services lizenziert haben, können Sie Ihre Site direkt in Cloud Manager integrieren und live schalten [mithilfe eines geführten Self-Service-Erlebnisses](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).

Darüber hinaus steht Ihnen ein einheitliches Erlebnis bei der Verwaltung aller AEM-Eigenschaften offen, bei gleichzeitiger Konsistenz wichtiger Workflows. Diese Workflows umfassen die Verwaltung von Domain-Namen, SSL-Zertifikaten und CDN-Zuordnungen.

Cloud Manager bietet zwei Bereitstellungstypen für Edge Delivery Services im von Adobe verwalteten CDN mit unterschiedlichen Funktionen. [Weitere Informationen](#edge-delivery-deployment-options)

>[!NOTE]
>
>Edge Delivery Services kann auch mithilfe der Konfigurations-Pipeline und der Ursprungsauswahl in bestehende AEM Sites as a Cloud Service-Umgebungen integriert werden. Weitere Informationen finden Sie unter [Proxys für Edge Delivery Services](/help/implementing/dispatcher/cdn-configuring-traffic.md#proxying-to-edge-delivery) und [Einrichten eines Proxys aus einer bestehenden Umgebung](https://www.aem.live/docs/byo-cdn-adobe-managed#option-1-setup-a-proxy-from-an-existing-environment).

## Edge Delivery Services-Bereitstellungsoptionen im von Adobe verwalteten CDN {#edge-delivery-deployment-options}

Es gibt zwei Bereitstellungstypen für Edge Delivery Services im von Adobe verwalteten CDN:

1. **Mit einer bestehenden AEMaaCS-Umgebung** - Richten Sie einen HTTP-Proxy aus einer bestehenden AEM Sites as a Cloud Service-Umgebung ein. Dieser Ansatz wird in der Regel verwendet, wenn Sie bereits über eine bestehende Umgebung verfügen und einen Teil einer Site nach Edge Delivery Services migrieren möchten. Siehe [Einrichten eines Proxys aus einer vorhandenen Umgebung](https://www.aem.live/docs/byo-cdn-adobe-managed#option-1-setup-a-proxy-from-an-existing-environment).

1. **Ohne bestehende AEMaaCS-Umgebung (Edge-Umgebung)** - Richten Sie eine neue Edge Delivery-Site unabhängig von einer AEM Sites as a Cloud Service-Umgebung ein. Dieser Ansatz wird verwendet, wenn Sie keine AEM-Autoren- oder Veröffentlichungsumgebung haben und Edge Delivery Services allein verwenden möchten. Siehe [Einrichten einer Edge Delivery-Site ohne vorhandene Umgebung](https://www.aem.live/docs/byo-cdn-adobe-managed#option-2-setup-an-edge-delivery-site-without-an-existing-environment).

Diese beiden Optionen bieten auch verschiedene Funktionen:

* **Konfigurations-**) ist für AEM as a Cloud Service-Umgebungen verfügbar.
* **Konfigurations-Pipeline** ist derzeit nur über das eingeschränkte Beta-Programm für Edge-Umgebungen verfügbar.

Vollständige Einrichtungsanweisungen finden Sie unter [Adobe Managed CDN](https://www.aem.live/docs/byo-cdn-adobe-managed)


## Über Edge Delivery Services mit AEM Authoring {#eds-aem-authoring}

Moderne Web-Erlebnisse erfordern eine leistungsstarke Bereitstellung, aber viele Unternehmen verlassen sich auch auf etablierte AEM-Authoring-Workflows, Governance und Muster für die Wiederverwendung von Inhalten. Um Ihre Teams bei der Modernisierung des Versands zu unterstützen, ohne das Authoring zu unterbrechen, führt Cloud Manager Funktionen ein, die Ihnen Folgendes ermöglichen:

* Bereitstellen von Erlebnissen mit Edge Delivery Services.
* Verwenden Sie AEM Author weiterhin für die Inhaltserstellung.
* Stellen Sie nur die für Ihre Architektur erforderliche Infrastruktur bereit.

Mit diesen Funktionen können Unternehmen die moderne Bereitstellung schrittweise umsetzen, ohne vorhandene Workflows zu opfern.

### Authoring-Optionen für Edge Delivery Sites {#authoring-options-eds}

Wenn Sie eine Edge Delivery-Site in Cloud Manager erstellen, können Sie Ihren bevorzugten Authoring-Ansatz wählen:

* Dokumentenbasiertes Authoring - Erstellen Sie Inhalte in Google Drive oder SharePoint. Es ist keine AEM-Umgebung erforderlich.
* AEM-Authoring - Erstellen Sie Inhalte in AEM mit dem universellen Editor. Für diese Methode ist eine AEM Author-Umgebung erforderlich. Bei dieser Option ist keine Veröffentlichungsebene erforderlich, wenn Edge Delivery die Inhaltsbereitstellung handhabt.

Unternehmen können je nach ihren Workflow-Voreinstellungen zwischen diesen Ansätzen wählen oder beide inkrementell verwenden. Siehe [Erstellen Ihrer ersten Edge Delivery-Site mit einem Klick](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md).

### Flexible Veröffentlichungsebene {#flexible-publish-tier}

Mit Cloud Manager können Sie konfigurieren, ob für die Umgebungen Ihres Programms eine Veröffentlichungsebene bereitgestellt wird. Nicht alle Architekturen erfordern eine Veröffentlichungsebene, wie in der folgenden Tabelle dargestellt:

| Architektur | Veröffentlichungsebene |
| --- | --- |
| Traditionelles AEM Sites | Erforderlich |
| Headless/API-First | Erforderlich |
| Edge Delivery Services | Nicht erforderlich |

Durch die Aktivierung der Veröffentlichungsebene nur bei Bedarf können Teams Umgebungen schneller bereitstellen, die Infrastruktur vereinfachen und unnötige Komponenten reduzieren. Siehe [Flexible Veröffentlichungsebene (Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier).

## Vorteile des von Adobe empfohlenen Pfads für Edge Delivery Services {#recommended-path-eds}

Maximieren Sie die Vorteile, die Ihnen Adobe bietet, indem Sie über Cloud Manager auf Ihre Edge Delivery Services-Lizenz zugreifen und diese nutzen. Dies bietet mehrere wichtige Vorteile.

* [Verwenden Sie Ihre Lizenz für das von Ihnen gewünschte Programm](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) oder [aktualisieren Sie andere Programme](/help/implementing/cloud-manager/edge-delivery/manage-edge-delivery-sites.md) oder beides.
* [Verwenden Sie ein externes Git-Repository](/help/implementing/cloud-manager/managing-code/external-repositories.md) (bringen Sie Ihr eigenes Git mit), um Ihren Edge Delivery Services-Site-Code zu synchronisieren und bereitzustellen. Um diese Funktion nutzen zu können, müssen Sie zunächst [Ihre Site in Cloud Manager integrieren](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) <!-- NEW from CQDOC-22867 -->
* [Verwenden Sie die Edge Delivery Config](/help/implementing/dispatcher/cdn-configuring-traffic.md)Pipeline, um in Adobe verwaltete CDN-Einstellungen für Ihre Edge Delivery-Site zu konfigurieren, indem Sie Regeln wie Traffic-Filter, Herkunftsselektoren und Umleitungen definieren. <!-- NEW from CQDOC-22867 -->
* Verwenden Sie [API-first](https://developer.adobe.com/experience-cloud/experience-manager-apis/)-Funktionen zum Ausführen von CRUD-Vorgängen (Erstellen, Lesen, Aktualisieren, Löschen).
* [Zugriff auf SLA-](/help/implementing/cloud-manager/reports/report-sla.md).
* [Nutzen Sie den Adobe-Support](/help/edge/overview.md#support-ticket) für Ihre registrierten Produktionsprogramme.

Wenn Sie über eine Edge Delivery Services (EDS)-Lizenz verfügen, können Sie ein von [Adobe verwaltetes CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) für Ihre Edge Delivery-Site verwenden. Dies ermöglicht die Self-Service-CDN-Verwaltung und DV-Zertifikate, die automatisch alle drei Monate erneuert werden, es sei denn, Sie löschen das Zertifikat.

Alternativ müssen Sie Ihr eigenes CDN (d. h. ein nicht von Adobe verwaltetes CDN) unabhängig von Ihrer Edge Delivery Services-Lizenz auf der `aem.live` konfigurieren. Siehe [BYO-CDN-Einrichtung](https://www.aem.live/docs/byo-cdn-setup).


## Über das Hinzufügen von Edge Delivery Services zu einem Produktions- oder Sandbox-Programm {#about-adding-eds-to-prod-sandbox}

Edge Delivery Services kann auf verschiedene Arten hinzugefügt werden, je nachdem, wie Sie Ihr Projekt begonnen haben oder wann Sie die Site erstellen möchten.

| Anwendungsfall | Beschreibung |
| --- | --- |
| Edge Delivery Services zu einem neuen Produktionsprogramm hinzufügen. | Siehe [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).<br>Wählen Sie im Assistenten auf der Registerkarte **Lösungen und Add-ons** die Option **Edge Delivery Services** aus. |
| Edge Delivery Services zu einem vorhandenen Produktionsprogramm hinzufügen. | Siehe [Bearbeiten von Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md).<br>Wählen Sie im Dialogfeld **Programm bearbeiten** auf der Registerkarte **Lösungen und Add-ons** die Option **Edge Delivery Services** aus. |
| Edge Delivery-Site zu Cloud Manager hinzufügen | Siehe [Hinzufügen einer Edge Delivery-Site](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md). |
| Sofort eine Edge Delivery-Site erstellen | Siehe [Schnelles Erstellen einer Edge Delivery-Site in Cloud Manager mit einem Klick](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md). |
| Edge Delivery Services zu einem neuen oder vorhandenen Sandbox-Programm hinzufügen. | Siehe [Erstellen von Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md).<br>Wenn Sie ein Sandbox-Programm erstellen, werden dem Programm standardmäßig Edge Delivery Services hinzugefügt. Eine Auswahl ist nicht erforderlich.<br>Vorhandene Sandbox-Programme „erben“ automatisch Edge Delivery Services, sofern Edge Delivery noch nicht allgemein verfügbar ist. |
| Ich möchte eine Edge Delivery-Site erstellen, die das Authoring mit AEM verwendet | Siehe [Erstellen einer Edge Delivery-Site](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md#one-click-edge-delivery-site). Bei Verwendung von AEM-Authoring mit Edge Delivery ist eine Veröffentlichungsebene optional. Siehe [Flexible Veröffentlichungsebene (Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier). |

>[!NOTE]
>
>* Um Programme hinzuzufügen oder zu bearbeiten, müssen Sie Mitglied der Rolle **Geschäftsinhaber** sein oder über die entsprechende Berechtigung verfügen.
>* Ihre Organisation muss eine nicht verwendete Edge Delivery Services-Lizenz besitzen, bevor diese auf ein Produktionsprogramm angewendet werden kann.
>* Wenn die Edge Delivery Services-Lizenz auf ein Programm angewendet oder daraus entfernt wurde, wird die Änderung sofort wirksam, ohne dass eine Pipeline ausgeführt werden muss.


## Über die Aufgabenliste von Edge Delivery in Cloud Manager {#ed-todo-list}

Die **Edge Delivery-Aufgabenliste** in Cloud Manager ist eine Onboarding-Aufgabencheckliste. Er soll Sie durch das Onboarding und Verwalten Ihrer Edge Delivery-Site führen, bis Sie [den Go-Live-Prozess abschließen](/help/journey-onboarding/go-live-checklist.md).

![Site-Aufgabenliste von Edge Delivery in Cloud Manager](/help/implementing/cloud-manager/assets/cm-eds-todo-list.png)

|   | Aufgabe | Beschreibung |
| --- | --- | --- |
| 1 | Dem Kanal für Produktzusammenarbeit beitreten | Durch Klicken auf **Anfrage jetzt senden** wird eine Anfrage an Adobe gesendet, um einen Kanal für Ihr Unternehmen zu erstellen. Wenn der Kanal bereits vorhanden ist, werden Sie an den Kanal Ihres Unternehmens weitergeleitet. |
| 2 | Voraussetzungen erfüllen | Weitere Informationen finden Sie im Tutorial [Erste Schritte](https://www.aem.live/developer/tutorial). |
| 3 | Edge Delivery-Site hinzufügen ODER <br>Jetzt eine Site erstellen | Siehe [Hinzufügen einer Edge Delivery-Site](#eds-add-site).<br>Siehe [Erstellen einer Edge Delivery-Site in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md). |
| 4 | Konfigurieren einer Edge Delivery-Site zur Verwendung eines externen Git-Repositorys | Siehe [Konfigurieren einer Edge Delivery-Site zur Verwendung eines externen Git-Repositorys](/help/implementing/cloud-manager/edge-delivery/config-edge-delivery-site-with-byog.md). |
| 5 | Domain hinzufügen | Siehe [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). |
| 6 | SSL-Zertifikat hinzufügen | Siehe [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md). |
| 7 | CDN der Edge Delivery-Site konfigurieren | Siehe [Hinzufügen einer Domain-Zuordnung](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md). |
| 8 | Einrichten der Push-Validierung | Weitere Informationen finden Sie unter [Einrichten der Push-Validierung für eine Edge Delivery-Site](/help/implementing/cloud-manager/edge-delivery/cdn-setup-push-invalidation.md). |
| 9 | Live-Schaltung | Weitere Informationen finden Sie unter [Checkliste für die Live-Schaltung](https://www.aem.live/docs/go-live-checklist). |

>[!VIDEO](https://video.tv.adobe.com/v/3428020?learn=on)

## Einreichen eines Support-Tickets {#eds-support-ticket}

{{support-ticket}}



