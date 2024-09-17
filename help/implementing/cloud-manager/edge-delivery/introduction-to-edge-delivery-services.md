---
title: Einführung in Edge Delivery Services in Cloud Manager
description: Erfahren Sie, wie Sie Ihre Cloud Manager-Projekte mit Edge Delivery Services bereitstellen.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5dc3d571c553f2972295172c7a6d0249be3285b8
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 6%

---

# Einführung in Edge Delivery Services in Cloud Manager {#edge-delivery-services}

Edge Delivery Services ist ein zusammenstellbarer Satz von Services, der eine hohe Flexibilität bei der Erstellung von Inhalten auf Ihrer Website ermöglicht. Mit dieser Funktion können Sie Folgendes tun:

* Erstellen Sie schnelle Websites mit einem perfekten Lighthouse-Score.
* Kontinuierliche Überwachung der Leistung durch RUM (Real Use Monitoring).
* Erhöhen Sie die Autoreneffizienz durch Entkopplung von Inhaltsquellen.

Sie können sowohl AEM Content Management als auch WYSIWYG-Authoring mit dem universellen Editor und dem dokumentbasierten Authoring verwenden.

Mit Cloud Manager in AEM as a Cloud Service können Sie den Edge Delivery-Dienst für Ihr Projekt aktivieren.

>[!TIP]
>
>Weitere Informationen zu Edge Delivery Services und zur Verwendung mit AEM finden Sie unter [Übersicht über Edge Delivery Services](/help/edge/overview.md).

<!-- RELEASED TO GA SEPTEMBER 5, 2024
>[!NOTE]
>
>This feature is only available to [the early adopter program](/help/implementing/cloud-manager/release-notes/current.md#early-adoption). -->


## Über Edge Delivery Services in Cloud Manager {#edge-in-cloud-manager}

Wenn Sie Edge Delivery Services als Teil von Adobe Experience Manager Sites lizenziert haben, können Sie Ihre Site mit Edge Delivery Services direkt in Cloud Manager integrieren und [mit einem geführten Self-Service-Erlebnis](/help/implementing/cloud-manager/managing-code/private-repositories.md) live gehen.

Darüber hinaus können Sie auf ein einheitliches Erlebnis für die Verwaltung aller AEM zugreifen und gleichzeitig die Konsistenz wichtiger Workflows sicherstellen. Dazu gehören die Verwaltung von Domain-Namen, die SSL-Zertifikatverwaltung und CDN-Zuordnungen.

## Hinzufügen von Edge Delivery Services zu einem Produktionsprogramm oder Sandbox-Programm

Um Programme hinzuzufügen oder zu bearbeiten, müssen Sie Mitglied der Rolle **Business Owner** sein oder über die entsprechende Berechtigung verfügen.

Ihr Unternehmen muss über eine nicht verwendete Edge Delivery Services-Lizenz verfügen, bevor diese auf ein Produktionsprogramm angewendet werden kann.

>[!NOTE]
>
>Sobald die Edge Delivery Services-Lizenz auf ein Programm angewendet oder daraus entfernt wurde, wird die Änderung sofort wirksam, ohne dass eine Pipeline ausgeführt werden muss. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

Führen Sie je nach Anwendungsfall einen der folgenden Schritte aus:

| Anwendungsfall | Beschreibung |
| --- | --- |
| Ich möchte Edge Delivery Services zu einem neuen Produktionsprogramm hinzufügen. | Siehe [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).<br>Wählen Sie im Assistenten auf der Registerkarte **Lösungen und Add-ons** die Option **Edge Delivery Services** aus. |
| Ich möchte einem bestehenden Produktionsprogramm Edge Delivery Services hinzufügen. | Siehe [Bearbeiten von Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md).<br>Wählen Sie im Dialogfeld **Programm bearbeiten** auf der Registerkarte **Lösungen und Add-ons** die Option **Edge Delivery Services** aus. |
| Ich möchte eine Edge Delivery-Site zu Cloud Manager hinzufügen | Siehe [Hinzufügen einer Edge Delivery-Site](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md). |
| Ich möchte Edge Delivery Services zu einem neuen oder vorhandenen Sandbox-Programm hinzufügen. | Siehe [Sandbox-Programme erstellen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md).<br>Wenn Sie ein Sandbox-Programm erstellen, werden dem Programm standardmäßig Edge Delivery Services hinzugefügt. Sie müssen es nicht auswählen.<br>Vorhandene Sandbox-Programme vor der allgemeinen Verfügbarkeit von Edge Delivery übernehmen automatisch Edge Delivery Services. |

## Adobe empfohlener Pfad für lizenzierte Kunden {#recommended-path-eds}

Als lizenzierter Kunde sollten Sie sicherstellen, dass Sie die Vorteile von Adobe maximieren, indem Sie über Cloud Manager auf Ihre Edge Delivery Services-Lizenz zugreifen und diese nutzen. Mit diesem Ansatz können Sie [vom Adobe verwaltetes CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) verwenden und von den wichtigsten Vorteilen wie der Self-Service-CDN-Verwaltung, einschließlich der Konfiguration und des Hinzufügens von DV-Zertifikaten, profitieren. Nach der Erstellung eines DV-Zertifikats erneuert Adobe es automatisch alle drei Monate, es sei denn, es wird gelöscht. Wenn Sie keine Edge Delivery Services-Lizenz mit Adobe haben und sich dafür entscheiden, diese Vorteile zu umgehen, können Sie nur ein kundenverwaltetes CDN verwenden. Diese Einrichtung muss sich auf der `aem.live`-Plattform befinden.

Wenn Sie über eine Lizenz für AEM as a Cloud Service Sites Edge Delivery Services verfügen, melden Sie sich bei Cloud Manager an, um sicherzustellen, dass Sie Folgendes tun können:

* Verbrauchen Sie Ihre Lizenz für Ihr ausgewähltes Programm.
* Nutzen Sie die Vorteile von [API-first](https://developer.adobe.com/experience-cloud/experience-manager-apis/) für die Ausführung von CRUD-Vorgängen (Erstellen, Lesen, Aktualisieren, Löschen).
<!-- REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+Self-service+access+to+Edge+Delivery+Services+and+Adobe+Managed+CDN * Access to license dashboard and reporting -->
* Zugriff auf SLA-Berichte (*in Kürze verfügbar*) <!-- ADD LINK TO IT WHEN FINALLY ADDED -->
* Adobe-Unterstützung erhalten. Stellen Sie sicher, dass Ihre Edge Delivery Services-Sites über ein Produktionsprogramm in Cloud Manager registriert sind, um eine ordnungsgemäße Erkennung und Unterstützung durch Adobe zu erhalten.


## Über die Aufgabenliste von Edge Delivery {#ed-todo-list}

Die **Edge Delivery-Aufgabenliste** ist eine Checkliste für Onboarding-Aufgaben, die Sie durch das Onboarding führen und Ihre Edge Delivery-Site bis zum [Go-Live](/help/journey-onboarding/go-live-checklist.md) verwalten soll.

![Edge Delivery-Website-Aufgabenliste](/help/implementing/cloud-manager/assets/cm-eds-todo-list.png)

|  | Aufgabe | Beschreibung |
| --- | --- | --- |
| 1 | Dem Kanal für Produktzusammenarbeit beitreten | Durch Klicken auf **Anfrage jetzt senden** wird eine Anfrage an Adobe gesendet, einen Kanal für Ihr Unternehmen zu erstellen. Wenn der Kanal bereits vorhanden ist, werden Sie an den Kanal Ihres Unternehmens weitergeleitet. |
| 2 | Voraussetzungen erfüllen | Wenn Sie auf **Tutorial Erste Schritte anzeigen** klicken, gelangen Sie zum Tutorial [Erste Schritte - Entwickler](https://www.aem.live/developer/tutorial). |
| 3 | Edge Delivery-Site hinzufügen | Siehe [Hinzufügen einer Edge Delivery-Site](#eds-add-site). |
| 4 | Domain hinzufügen | Siehe [Hinzufügen eines benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). |
| 5 | SSL-Zertifikat hinzufügen | Siehe [SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md). |
| 6 | CDN Ihrer Edge Delivery-Site konfigurieren | Siehe [Hinzufügen einer CDN-Konfiguration](#add-cdn). |

>[!VIDEO](https://video.tv.adobe.com/v/3428020?learn=on)

<!--
Edge Delivery Services can be enabled when adding a new production program or editing an existing one.

![Add production program with Edge Delivery Services](assets/add-production-program-with-edge.png)

For more information about adding programs, see the following:

* [Create Production programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
* [Create Sandbox programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) -->
