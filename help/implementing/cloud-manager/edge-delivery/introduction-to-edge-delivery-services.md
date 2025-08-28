---
title: Einführung in Edge Delivery Services in Cloud Manager
description: Erfahren Sie, wie Sie Ihre Cloud Manager-Projekte mit Edge Delivery Services bereitstellen.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 99%

---


# Einführung in Edge Delivery Services in Cloud Manager {#edge-delivery-services}

Edge Delivery Services ist ein zusammenstellbarer Satz von Services, der eine hohe Flexibilität bei der Erstellung von Inhalten auf Ihrer Website ermöglicht. Dadurch können Sie:

* schnelle Websites mit einer perfekten Lighthouse-Bewertung erstellen,
* die Leistung durch betriebliche Telemetrie kontinuierlich überwachen,
* die Autoreneffizienz durch Entkopplung von Inhaltsquellen erhöhen.

Sie können sowohl das AEM-Content-Management und WYSIWYG-Authoring mit dem universellen Editor als auch das dokumentenbasierte Authoring verwenden.

Mit Cloud Manager in AEM as a Cloud Service können Sie Edge Delivery Services für Ihr Projekt aktivieren.

>[!TIP]
>
>Weitere Informationen zu Edge Delivery Services und zur Verwendung mit AEM finden Sie unter [Überblick über Edge Delivery Services](/help/edge/overview.md).

## Über Edge Delivery Services in Cloud Manager {#edge-in-cloud-manager}

Wenn Sie Edge Delivery Services als Teil von Adobe Experience Manager Sites lizenziert haben, können Sie Ihre Site mit Edge Delivery Services direkt in Cloud Manager integrieren und [mit einem geführten Self-Service-Erlebnis](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) die Live-Schaltung vornehmen.

Darüber hinaus steht Ihnen ein einheitliches Erlebnis bei der Verwaltung aller AEM-Eigenschaften offen, bei gleichzeitiger Konsistenz wichtiger Workflows. Diese Workflows umfassen die Verwaltung von Domain-Namen, SSL-Zertifikaten und CDN-Zuordnungen.

## Vorteile des von Adobe empfohlenen Pfads für Edge Delivery Services {#recommended-path-eds}

Maximieren Sie die Vorteile, die Ihnen Adobe bietet, indem Sie über Cloud Manager auf Ihre Edge Delivery Services-Lizenz zugreifen und diese nutzen. Dadurch profitieren Sie von verschiedenen wichtigen Vorzügen.

* [Verwenden Sie Ihre Lizenz für das von Ihnen gewünschte Programm](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) oder [aktualisieren Sie andere Programme](/help/implementing/cloud-manager/edge-delivery/manage-edge-delivery-sites.md) oder beides.
* Nutzen Sie die Vorteile des [API-first](https://developer.adobe.com/experience-cloud/experience-manager-apis/)-Prinzips bei der Ausführung von CRUD-Vorgängen, also beim Erstellen, Lesen, Aktualisieren und Löschen.
* [Nutzen Sie das SLA-Reporting](/help/implementing/cloud-manager/sla-reporting.md) (*in Kürze verfügbar*)
* [Nutzen Sie den Adobe-Support](/help/edge/overview.md#support-ticket) für Ihre registrierten Produktionsprogramme.

Wenn Sie über eine Edge Delivery Services(EDS)-Lizenz verfügen, können Sie ein von [Adobe verwaltetes CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) für Ihre Edge Delivery-Site verwenden und Funktionen wie Self-Service-CDN-Verwaltung und automatische Verlängerung von DV-Zertifikaten alle drei Monate nutzen, sofern sie nicht gelöscht wird.

Wenn Sie alternativ Ihr CDN (d. h. ein nicht von Adobe verwaltetes CDN) unabhängig von Ihrer Edge Delivery Services-Lizenz verwenden möchten, müssen Sie es auf der Plattform `aem.live` konfigurieren. Siehe [BYO-CDN-Einrichtung](https://www.aem.live/docs/byo-cdn-setup).


## Über das Hinzufügen von Edge Delivery Services zu einem Produktions- oder Sandbox-Programm

Je nachdem, wie ein Projekt aufgesetzt wurde oder wann Sie die Site erstellen möchten, können Edge Delivery Services auf verschiedene Weise hinzugefügt werden.

| Anwendungsfall | Beschreibung |
| --- | --- |
| Edge Delivery Services zu einem neuen Produktionsprogramm hinzufügen. | Siehe [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).<br>Wählen Sie im Assistenten auf der Registerkarte **Lösungen und Add-ons** die Option **Edge Delivery Services** aus. |
| Edge Delivery Services zu einem vorhandenen Produktionsprogramm hinzufügen. | Siehe [Bearbeiten von Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md).<br>Wählen Sie im Dialogfeld **Programm bearbeiten** auf der Registerkarte **Lösungen und Add-ons** die Option **Edge Delivery Services** aus. |
| Edge Delivery-Site zu Cloud Manager hinzufügen | Siehe [Hinzufügen einer Edge Delivery-Site](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md). |
| Sofort eine Edge Delivery-Site erstellen | Siehe [Schnelles Erstellen einer Edge Delivery-Site in Cloud Manager mit einem Klick](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md). |
| Edge Delivery Services zu einem neuen oder vorhandenen Sandbox-Programm hinzufügen. | Siehe [Erstellen von Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md).<br>Wenn Sie ein Sandbox-Programm erstellen, werden dem Programm standardmäßig Edge Delivery Services hinzugefügt. Eine Auswahl ist nicht erforderlich.<br>Vorhandene Sandbox-Programme „erben“ automatisch Edge Delivery Services, sofern Edge Delivery noch nicht allgemein verfügbar ist. |

>[!NOTE]
>
>* Um Programme hinzuzufügen oder zu bearbeiten, müssen Sie Mitglied der Rolle **Geschäftsinhaber** sein oder über die entsprechende Berechtigung verfügen.
>* Ihre Organisation muss eine nicht verwendete Edge Delivery Services-Lizenz besitzen, bevor diese auf ein Produktionsprogramm angewendet werden kann.
>* Wenn die Edge Delivery Services-Lizenz auf ein Programm angewendet oder daraus entfernt wurde, wird die Änderung sofort wirksam, ohne dass eine Pipeline ausgeführt werden muss.


## Über die Aufgabenliste von Edge Delivery in Cloud Manager {#ed-todo-list}

<!-- &#x2460; for "1" inside circle -->

Die **Aufgabenliste von Edge Delivery** in Cloud Manager ist eine Checkliste für Onboarding-Aufgaben, die Sie durch das Onboarding und die Verwaltung Ihrer Edge Delivery-Site bis hin zur [Live-Schaltung](/help/journey-onboarding/go-live-checklist.md) führt.

![Site-Aufgabenliste von Edge Delivery in Cloud Manager](/help/implementing/cloud-manager/assets/cm-eds-todo-list.png)

|   | Aufgabe | Beschreibung |
| --- | --- | --- |
| 1 | Dem Kanal für Produktzusammenarbeit beitreten | Durch Klicken auf **Anfrage jetzt senden** wird eine Anfrage an Adobe gesendet, um einen Kanal für Ihr Unternehmen zu erstellen. Wenn der Kanal bereits vorhanden ist, werden Sie an den Kanal Ihres Unternehmens weitergeleitet. |
| 2 | Voraussetzungen erfüllen | Weitere Informationen finden Sie im Tutorial [Erste Schritte](https://www.aem.live/developer/tutorial). |
| 3 | Edge Delivery-Site hinzufügen ODER <br>Site jetzt erstellen | Siehe [Hinzufügen einer Edge Delivery-Site](#eds-add-site).<br>Siehe [Erstellen einer Edge Delivery-Site in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md). |
| 4 | Konfigurieren einer Edge Delivery-Site zur Verwendung eines externen Git-Repositorys | Siehe [Konfigurieren einer Edge Delivery-Site zur Verwendung eines externen Git-Repositorys](/help/implementing/cloud-manager/edge-delivery/config-edge-delivery-site-with-byog.md). |
| 5 | Domain hinzufügen | Siehe [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). |
| 6 | SSL-Zertifikat hinzufügen | Siehe [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md). |
| 7 | CDN der Edge Delivery-Site konfigurieren | Siehe [Hinzufügen einer Domain-Zuordnung](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md). |
| 8 | Einrichten der Push-Validierung | Weitere Informationen finden Sie unter [Einrichten der Push-Validierung für eine Edge Delivery-Site](/help/implementing/cloud-manager/edge-delivery/cdn-setup-push-invalidation.md). |
| 9 | Live-Schaltung | Weitere Informationen finden Sie unter [Checkliste für die Live-Schaltung](https://www.aem.live/docs/go-live-checklist). |

>[!VIDEO](https://video.tv.adobe.com/v/3441570?learn=on&captions=ger)

## Einreichen eines Support-Tickets {#eds-support-ticket}

{{support-ticket}}



