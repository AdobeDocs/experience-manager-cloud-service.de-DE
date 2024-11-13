---
title: Einführung in Edge Delivery Services in Cloud Manager
description: Erfahren Sie, wie Sie Ihre Cloud Manager-Projekte mit Edge Delivery Services bereitstellen.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: abd0fa0ea3e6e18187bcb60731ec6fe823a98e45
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 10%

---


# Einführung in Edge Delivery Services in Cloud Manager {#edge-delivery-services}

Edge Delivery Services ist ein zusammenstellbarer Satz von Services, der eine hohe Flexibilität bei der Erstellung von Inhalten auf Ihrer Website ermöglicht. Mit dieser Funktion können Sie Folgendes tun:

* Erstellen Sie schnelle Websites mit einem perfekten Lighthouse-Score.
* Kontinuierliche Überwachung der Leistung durch RUM (Real Use Monitoring).
* Erhöhen Sie die Autoreneffizienz durch Entkopplung von Inhaltsquellen.

Sie können sowohl AEM Content Management als auch WYSIWYG Authoring mit dem universellen Editor und dem dokumentbasierten Authoring verwenden.

Mit Cloud Manager in AEM as a Cloud Service können Sie den Edge Delivery-Dienst für Ihr Projekt aktivieren.

>[!TIP]
>
>Weitere Informationen zu Edge Delivery Services und zur Verwendung mit AEM finden Sie in der [Übersicht über Edge Delivery Services](/help/edge/overview.md) .

## Über Edge Delivery Services in Cloud Manager {#edge-in-cloud-manager}

Wenn Sie Edge Delivery Services als Teil von Adobe Experience Manager Sites lizenziert haben, können Sie Ihre Site mit Edge Delivery Services direkt in Cloud Manager integrieren und [mit einem geführten Self-Service-Erlebnis](/help/implementing/cloud-manager/managing-code/private-repositories.md) live gehen.

Darüber hinaus können Sie auf ein einheitliches Erlebnis für die Verwaltung aller AEM zugreifen und gleichzeitig die Konsistenz wichtiger Workflows sicherstellen. Zu diesen Workflows gehören Domain-Namensverwaltung, SSL-Zertifikatverwaltung und CDN-Zuordnungen.

## Vorteile der Verwendung des von Adobe empfohlenen Pfads für Edge Delivery Services {#recommended-path-eds}

Maximieren Sie Ihre Vorteile durch Adobe, indem Sie über Cloud Manager auf Ihre Edge Delivery Services-Lizenz zugreifen und diese nutzen. Auf diese Weise können Sie von mehreren wichtigen Vorteilen profitieren.

* [Verwenden Sie Ihre Lizenz für Ihr ausgewähltes Programm](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md), oder [aktualisieren Sie andere Programme](/help/implementing/cloud-manager/edge-delivery/manage-edge-delivery-sites.md) oder beides.
* Nutzen Sie die Vorteile von [API-first](https://developer.adobe.com/experience-cloud/experience-manager-apis/) für die Ausführung von CRUD-Vorgängen (Erstellen, Lesen, Aktualisieren, Löschen).
* [Zugriff auf SLA Reporting](/help/implementing/cloud-manager/sla-reporting.md) (*in Kürze verfügbar*)
* [Erhalten Sie Zugriff auf Adobe-Support](/help/edge/overview.md#support-ticket) für Ihre registrierten Produktionsprogramme.

Darüber hinaus können Sie mit Cloud Manager [Adobe verwaltetes CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) für Ihre Edge Delivery-Site verwenden und wichtige Vorteile wie die Self-Service-CDN-Verwaltung nutzen, einschließlich der Konfiguration und des Hinzufügens von DV-Zertifikaten. Nach der Erstellung eines DV-Zertifikats erneuert Adobe es automatisch alle drei Monate, es sei denn, es wird gelöscht. Wenn Sie nicht über eine Edge Delivery Services-Lizenz mit Adobe verfügen und sich dafür entscheiden, diese Vorteile zu umgehen, können Sie nur Ihr eigenes selbst verwaltetes CDN verwenden. Diese Einrichtung muss sich auf der [`aem.live` Plattform](https://www.aem.live/docs/go-live-checklist#cdn-configuration) befinden.

## Über das Hinzufügen von Edge Delivery Services zu einem Produktionsprogramm oder Sandbox-Programm

Je nach Projektbeginn können Edge Delivery Services auf verschiedene Weise hinzugefügt werden.

| Anwendungsfall | Beschreibung |
| --- | --- |
| Ich möchte Edge Delivery Services zu einem neuen Produktionsprogramm hinzufügen. | Siehe [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).<br>Wählen Sie im Assistenten auf der Registerkarte **Lösungen und Add-ons** die Option **Edge Delivery Services** aus. |
| Ich möchte einem bestehenden Produktionsprogramm Edge Delivery Services hinzufügen. | Siehe [Bearbeiten von Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md).<br>Wählen Sie im Dialogfeld **Programm bearbeiten** auf der Registerkarte **Lösungen und Add-ons** die Option **Edge Delivery Services** aus. |
| Ich möchte eine Edge Delivery-Site zu Cloud Manager hinzufügen | Siehe [Hinzufügen einer Edge Delivery-Site](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md). |
| Ich möchte Edge Delivery Services zu einem neuen oder vorhandenen Sandbox-Programm hinzufügen. | Siehe [Sandbox-Programme erstellen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md).<br>Wenn Sie ein Sandbox-Programm erstellen, werden dem Programm standardmäßig Edge Delivery Services hinzugefügt. Sie müssen es nicht auswählen.<br>Vorhandene Sandbox-Programme vor der allgemeinen Verfügbarkeit von Edge Delivery übernehmen automatisch Edge Delivery Services. |

>[!NOTE]
>
>* Um Programme hinzuzufügen oder zu bearbeiten, müssen Sie Mitglied der Rolle **Business Owner** sein oder über die entsprechende Berechtigung verfügen.
>* Ihr Unternehmen muss über eine nicht verwendete Edge Delivery Services-Lizenz verfügen, bevor diese auf ein Produktionsprogramm angewendet werden kann.
>* Sobald die Edge Delivery Services-Lizenz auf ein Programm angewendet oder daraus entfernt wurde, wird die Änderung sofort wirksam, ohne dass eine Pipeline ausgeführt werden muss.


## Über die Aufgabenliste von Edge Delivery {#ed-todo-list}

<!-- &#x2460; for "1" inside circle -->

Die **Edge Delivery-Aufgabenliste** ist eine Checkliste für Onboarding-Aufgaben, die Sie durch das Onboarding führen und Ihre Edge Delivery-Site bis zum [Go-Live](/help/journey-onboarding/go-live-checklist.md) verwalten soll.

![Edge Delivery-Website-Aufgabenliste](/help/implementing/cloud-manager/assets/cm-eds-todo-list.png)

|   | Aufgabe | Beschreibung |
| --- | --- | --- |
| 1 | Dem Kanal für Produktzusammenarbeit beitreten | Durch Klicken auf **Anfrage jetzt senden** wird eine Anfrage an Adobe gesendet, einen Kanal für Ihr Unternehmen zu erstellen. Wenn der Kanal bereits vorhanden ist, werden Sie an den Kanal Ihres Unternehmens weitergeleitet. |
| 2 | Voraussetzungen erfüllen | Siehe [Erste Schritte-Tutorial anzeigen](https://www.aem.live/developer/tutorial). |
| 3 | Edge Delivery-Site hinzufügen | Siehe [Hinzufügen einer Edge Delivery-Site](#eds-add-site). |
| 4 | Domain hinzufügen | Siehe [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). |
| 5 | SSL-Zertifikat hinzufügen | Siehe [SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md). |
| 6 | CDN Ihrer Edge Delivery-Site konfigurieren | Siehe [Hinzufügen einer CDN-Konfiguration](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md). |
| 7 | Push-Validierung einrichten | Siehe [Push-Validierung für eine Edge Delivery-Site einrichten](/help/implementing/cloud-manager/edge-delivery/cdn-setup-push-invalidation.md). |
| 8 | Live-Schaltung | Siehe [Go-Live-Checkliste](/help/edge/docs/go-live-checklist.md). |

>[!VIDEO](https://video.tv.adobe.com/v/3428020?learn=on)

## Einreichen eines Support-Tickets {#eds-support-ticket}

{{support-ticket}}



