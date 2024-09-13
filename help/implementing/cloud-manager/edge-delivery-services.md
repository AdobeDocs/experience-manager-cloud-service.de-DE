---
title: Edge Delivery Services-Unterstützung in Cloud Manager
description: Erfahren Sie, wie Sie Ihre Cloud Manager-Projekte mit Edge Delivery Services bereitstellen.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: bc9aa376a402a55191e153f662262ff65df32f5e
workflow-type: tm+mt
source-wordcount: '1516'
ht-degree: 6%

---

# Unterstützung für Edge Delivery Services in Cloud Manager {#edge-delivery-services}

Erfahren Sie, wie Sie mit Ihrer Edge Delivery Services-Lizenz eine Edge Delivery Services-Site erstellen.

<!-- RELEASED TO GA SEPTEMBER 5, 2024
>[!NOTE]
>
>This feature is only available to [the early adopter program](/help/implementing/cloud-manager/release-notes/current.md#early-adoption). -->

## Edge Delivery Services in Kurzform {#edge-overview}

Edge Delivery Services ist ein zusammenstellbarer Satz von Services, der eine hohe Flexibilität bei der Erstellung von Inhalten auf Ihrer Website ermöglicht. Mit dieser Funktion können Sie Folgendes tun:

* Erstellen Sie schnelle Websites mit einem perfekten Lighthouse-Score.
* Kontinuierliche Überwachung der Leistung durch RUM (Real Use Monitoring).
* Erhöhen Sie die Autoreneffizienz durch Entkopplung von Inhaltsquellen.

Sie können sowohl AEM Content Management als auch WYSIWYG-Authoring mit dem universellen Editor und dem dokumentbasierten Authoring verwenden.

Mit Cloud Manager in AEM as a Cloud Service können Sie den Edge Delivery-Dienst für Ihr Projekt aktivieren.

>[!TIP]
>
>Weitere Informationen zu Edge Delivery Services und zur Verwendung mit AEM finden Sie im Dokument [Überblick über Edge Delivery Services](/help/edge/overview.md) .

## Edge Delivery Services in Cloud Manager {#edge-in-cloud-manager}

Wenn Sie Edge Delivery Services als Teil von Adobe Experience Manager Sites lizenziert haben, können Sie Ihre Site mit Edge Delivery Services direkt in Cloud Manager integrieren und [mit einem geführten Self-Service-Erlebnis](/help/implementing/cloud-manager/managing-code/private-repositories.md) live gehen.

Darüber hinaus können Sie auf ein einheitliches Erlebnis für die Verwaltung aller AEM zugreifen und gleichzeitig die Konsistenz wichtiger Workflows sicherstellen. Dazu gehören die Verwaltung von Domain-Namen, die SSL-Zertifikatverwaltung und CDN-Zuordnungen.

## Hinzufügen von Edge Delivery Services zu einem Produktions- oder Sandbox-Programm

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
| Ich möchte Edge Delivery Services zu einem neuen oder vorhandenen Sandbox-Programm hinzufügen. | Siehe [Sandbox-Programme erstellen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md).<br>Wenn Sie ein Sandbox-Programm erstellen, werden dem Programm standardmäßig Edge Delivery Services hinzugefügt. Sie müssen es nicht auswählen.<br>Vorhandene Sandbox-Programme übernehmen Edge Delivery Services automatisch. |

## Von Adobe empfohlener Pfad für Kunden mit Vertragsvertrag {#recommended-path-eds}

Stellen Sie als Vertragskunde sicher, dass Sie die Vorteile von Adobe maximieren, indem Sie über Cloud Manager auf Ihre Edge Delivery Services-Lizenz zugreifen und diese nutzen. Mit diesem Ansatz können Sie [vom Adobe verwaltetes CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) verwenden und von den wichtigsten Vorteilen wie der Self-Service-CDN-Verwaltung, einschließlich der Konfiguration und des Hinzufügens von DV-Zertifikaten, profitieren. Nach der Erstellung eines DV-Zertifikats erneuert Adobe es automatisch alle drei Monate, es sei denn, es wird gelöscht. Wenn Sie keine Edge Delivery Services-Lizenz mit Adobe haben und sich dafür entscheiden, diese Vorteile zu umgehen, können Sie nur ein kundenverwaltetes CDN verwenden. Diese Einrichtung muss sich auf der `aem.live`-Plattform befinden.

Wenn Sie mit AEM as a Cloud Service Sites Edge Delivery Services-Lizenzen beauftragt sind, melden Sie sich bei Cloud Manager an, um sicherzustellen, dass Sie Folgendes tun können:

* Verbrauchen Sie Ihre Lizenz für Ihr ausgewähltes Programm.
* Nutzen Sie die Vorteile von [API-first](https://developer.adobe.com/experience-cloud/experience-manager-apis/) für die Ausführung von CRUD-Vorgängen (Erstellen, Lesen, Aktualisieren, Löschen).
<!-- REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+Self-service+access+to+Edge+Delivery+Services+and+Adobe+Managed+CDN * Access to license dashboard and reporting -->
* Zugriff auf SLA-Berichte (*in Kürze verfügbar*) <!-- ADD LINK TO IT WHEN FINALLY ADDED -->
* Adobe-Unterstützung erhalten. Stellen Sie sicher, dass Ihre Edge Delivery Services-Sites über ein Produktionsprogramm in Cloud Manager registriert sind, um eine ordnungsgemäße Erkennung und Unterstützung durch Adobe zu erhalten.

## Hinzufügen einer Edge Delivery-Site {#eds-add-site}

Nachdem Sie einem Produktionsprogramm Edge Delivery Services hinzugefügt haben, wird Ihre Edge Delivery Services-Lizenz darauf angewendet.

Auf der Übersichtsseite wird eine klickbare Registerkarte mit dem Namen **Edge Delivery** angezeigt. Durch Klicken auf die Registerkarte wird eine Tabelle mit den einzelnen Edge Delivery-Sites angezeigt, die Sie hinzugefügt haben. Beachten Sie im linken Navigationsbereich unter der Gruppierung **Dienste** die Menüoption namens **Edge Delivery Sites**.

![Übersichtsseite mit Edge Delivery Sites im linken Navigationsbereich und der Registerkarte Edge Delivery rechts neben der Registerkarte Publish-Bereitstellung](/help/implementing/cloud-manager/assets/cm-overview-eds.png)

**So fügen Sie eine Edge Delivery-Site hinzu:**

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm mit konfigurierten Edge Delivery Services aus, in dem Sie eine Edge Delivery-Site hinzufügen möchten.
1. Führen Sie eine der folgenden Aktionen aus:
   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery** . Klicken Sie dann unten rechts auf der Seite auf **Edge Delivery-Site hinzufügen**.

     ![Hinzufügen der Edge Delivery-Site vom Tab &quot;Edge Delivery&quot;](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

     Die im obigen Bild dargestellte &quot;Edge Delivery-Aufgabenliste&quot;**ist eine optionale Anleitung zur Einstieg in die Checkliste, die Ihnen bei den ersten Schritten mit Edge Delivery helfen soll.** Siehe [Info zur Edge Delivery-Aufgabenliste](#ed-todo-list).

   * Klicken Sie oben links auf der Seite auf das Hamburger-Symbol, um das linke Navigationsmenü anzuzeigen. Klicken Sie unter der Überschrift **Dienste** auf **Edge Delivery Sites**. Klicken Sie in der rechten oberen Ecke der Seite auf **Site hinzufügen**.

     ![Edge Delivery-Site über die Schaltfläche &quot;Edge Delivery Sites&quot;hinzufügen](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. Gehen Sie im Dialogfeld **Edge Delivery-Site hinzufügen** wie folgt vor:

   | Textfeld | Vorgehensweise |
   | --- | --- |
   | Site-Name | Geben Sie den Namen der Edge Delivery-Site ein, die Sie hinzufügen. Der Name dient als eindeutige Kennung für die Site in Cloud Manager. |
   | Repository-URL | Dieses Feld bezieht sich auf das Git-Repository, in dem der Code Ihrer Website gespeichert ist.<br>Geben Sie die URL des Git-Repositorys ein, das die erforderlichen Dateien und Ressourcen (wie HTML, CSS, JavaScript und andere Web-Assets) für Ihre Edge Delivery-Site enthält. Auf diese Weise kann Cloud Manager den Code während des Bereitstellungsprozesses aus diesem Repository abrufen. |
   | Site-Beschreibung (optional) | Geben Sie eine kurze Beschreibung der Edge Delivery-Site ein, die Sie hinzufügen.<br>Diese Beschreibung hilft, die Site zu identifizieren und zu unterscheiden, wodurch es einfacher wird, unter anderen von Ihnen hinzugefügten Sites zu verwalten und zu erkennen. Sie können Details zum Zweck, zum Inhalt oder zu anderen relevanten Informationen der Site hinzufügen, die dazu beitragen können, deren Funktion oder Umfang zu verdeutlichen. |

1. Klicken Sie in der rechten unteren Ecke des Dialogfelds auf **Hinzufügen**.

1. Führen Sie im Dialogfeld **Repository-Eigentümer überprüfen** die folgenden Schritte aus:

   | Schritt | Beschreibung |
   | --- | --- |
   | 1 | Fügen Sie eine Datei mit dem Speicherortpfad zur Verzweigung `main` des Git-Repositorys hinzu, die im Feld **Repository-URL** aufgeführt ist. Klicken Sie bei Bedarf auf das Symbol Kopieren , um den Pfad in die Zwischenablage zu kopieren.<br> Der Speicherort ist:<br>`well-known/adobe/cloudmanager-challenge.txt`.<br><br>Fügen Sie *nicht* am Anfang des Speicherortpfads einen Punkt hinzu, der sich in:<br>`.well-known/adobe/cloudmanager-challenge.txt` befindet. |
   | 2 | Fügen Sie den generierten Code der Datei hinzu, die Sie in Schritt 1 erstellt haben. Klicken Sie bei Bedarf auf das Symbol Kopieren , um den Code in die Zwischenablage zu kopieren. |
   | 3 | Erstellen Sie im Git-Repository eine Pull-Anfrage und führen Sie sie dann zusammen, um den Code zu übertragen. |

1. Klicken Sie auf **Verify**. Nachdem das Repository verifiziert wurde, ändert sich sein Status in der Tabelle Edge Deliver Sites in einen grünen Kreis mit einem weißen Häkchen darin.

## Über die Aufgabenliste von Edge Delivery {#ed-todo-list}

Die **Edge Delivery-Aufgabenliste** ist eine Checkliste für Onboarding-Aufgaben, die Sie durch das Onboarding führen und Ihre Edge Delivery-Site bis zum [Go-Live](/help/journey-onboarding/go-live-checklist.md) verwalten soll.

|  | Aufgabe | Beschreibung |
| --- | --- | --- |
| 1 | Dem Kanal für Produktzusammenarbeit beitreten | Durch Klicken auf **Anfrage jetzt senden** wird eine Anfrage an Adobe gesendet, einen Kanal für Ihr Unternehmen zu erstellen. Wenn der Kanal bereits vorhanden ist, werden Sie an den Kanal Ihres Unternehmens weitergeleitet. |
| 2 | Voraussetzungen erfüllen | Wenn Sie auf **Tutorial Erste Schritte anzeigen** klicken, gelangen Sie zum Tutorial [Erste Schritte - Entwickler](https://www.aem.live/developer/tutorial). |
| 3 | Edge Delivery-Site hinzufügen | Siehe [Hinzufügen einer Edge Delivery-Site](#eds-add-site). |
| 4 | Domain hinzufügen | Siehe [Hinzufügen eines benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). |
| 5 | SSL-Zertifikat hinzufügen | Siehe [SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md). |
| 6 | CDN Ihrer Edge Delivery-Site konfigurieren | Siehe [Hinzufügen einer CDN-Konfiguration](#add-cdn). |

>[!VIDEO](https://video.tv.adobe.com/v/3428020?learn=on)

## Hinzufügen einer CDN-Konfiguration zu Ihrer Edge Delivery-Site {#add-cdn}

Siehe [Hinzufügen einer CDN-Konfiguration](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md).

## Löschen einer Edge Delivery-Site {#eds-site-delete}

>[!IMPORTANT]
>
>Wenn Sie eine Edge Delivery Services-Site löschen, werden auch alle zugehörigen CDN-Konfigurationen entfernt. Diese Aktion unterbricht die Verbindung zwischen benutzerdefinierten Domänen und der Site. Weitere Informationen finden Sie unter CDN-Konfigurationen. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**So löschen Sie eine Edge Delivery-Site:**

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm mit konfigurierten Edge Delivery Services aus, in dem Sie eine Edge Delivery-Site hinzufügen möchten.
1. Führen Sie eine der folgenden Aktionen aus:
   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery** . Klicken Sie in der Edge Delivery-Sitetabelle auf das Auslassungszeichen am Ende einer Zeile, deren Site Sie entfernen möchten. Klicken Sie auf **Löschen** und dann erneut auf **Löschen** , um das Entfernen der Site zu bestätigen.

     ![Hinzufügen der Edge Delivery-Site vom Tab &quot;Edge Delivery&quot;](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * Klicken Sie oben links auf der Seite auf das Hamburger-Symbol, um das linke Navigationsmenü anzuzeigen. Klicken Sie unter der Überschrift **Dienste** auf **Edge Delivery Sites**. Klicken Sie in der Edge Delivery-Sitetabelle auf das Auslassungszeichen am Ende einer Zeile, deren Site Sie entfernen möchten. Klicken Sie auf **Löschen** und dann erneut auf **Löschen** , um das Entfernen der Site zu bestätigen.


     ![Edge Delivery-Site über die Schaltfläche &quot;Edge Delivery Sites&quot;hinzufügen](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)


<!--
Edge Delivery Services can be enabled when adding a new production program or editing an existing one.

![Add production program with Edge Delivery Services](assets/add-production-program-with-edge.png)

For more information about adding programs, see the following:

* [Create Production programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
* [Create Sandbox programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) -->
