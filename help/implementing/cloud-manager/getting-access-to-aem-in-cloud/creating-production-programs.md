---
title: Erstellen von Produktionsprogrammen
description: Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Produktionsprogramm für das Hosten von Live-Traffic erstellen.
exl-id: 4ccefb80-de77-4998-8a9d-e68d29772bb4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8ca3546725f2a95d233497a899afe3b4f6036775
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 95%

---


# Erstellen von Produktionsprogrammen {#create-production-program}

Ein Produktionsprogramm richtet sich an Benutzende, die mit Adobe Experience Manager (AEM) und Cloud Manager vertraut sind und Code schreiben, erstellen und testen können, um ihn für Live-Traffic bereitzustellen.

Weitere Informationen zu Programmtypen finden Sie unter [Programme und Programmtypen](program-types.md).

## Erstellen eines Produktionsprogramms {#create}

Abhängig von den Berechtigungen Ihrer Organisation werden möglicherweise zusätzliche Optionen für Produktionsprogramme angezeigt, wenn Sie Ihr Programm hinzufügen.
Siehe [Zusätzliche Optionen für Produktionsprogramme](#options).

**So erstellen Sie ein Produktionsprogramm:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie oben rechts in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** auf **Programm hinzufügen**.

   ![Cloud Manager-Landingpage](assets/log-in.png)

1. Geben Sie im Assistenten *Erstellen Sie Ihr Programm* im Textfeld **Programmname** den gewünschten Namen für das Programm ein.

1. Wählen Sie unter **Programmziel** die Option ![Weltkugelsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Globe_18_N.svg) **Für die Produktion einrichten**.

   ![Assistent zum Erstellen von Programmen](assets/create-production-program.png)

1. (Optional) Führen Sie unten rechts im Dialogfeld des Assistenten einen der folgenden Schritte aus:

   * Ziehen Sie eine Bilddatei per Drag-and-Drop auf das Ziel ![Bildsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Image_18_N.svg) **Programmbild hinzufügen**.
   * Klicken Sie auf ![Bildsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Image_18_N.svg) **Programmbild hinzufügen** und wählen Sie dann ein Bild aus einem Datei-Browser aus.
   * Klicken Sie auf ![Löschen-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg), um ein hinzugefügtes Bild zu löschen.

1. Klicken Sie auf **Weiter**.

1. Wählen Sie im Listenfeld **Lösungen und Add-ons** eine oder mehrere Lösungen aus, die im Programm enthalten sein sollen.

   * Wenn Sie sich nicht sicher sind, ob Sie ein oder mehrere Programme für die verschiedenen verfügbaren Lösungen benötigen, wählen Sie diejenige aus, die für Sie am interessantesten ist. Sie können zusätzliche Lösungen aktivieren, indem Sie [das Programm später bearbeiten](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md). Weitere Empfehlungen zur Programmeinrichtung finden Sie im Dokument [Einführung in Produktionsprogramme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md).
   * Sie müssen mindestens eine Lösung für die Programmerstellung auswählen. Sie können beispielsweise **Edge Delivery Services** für eine vollständig verwaltete CDN-Lösung auswählen, die digitale Erlebnisse optimiert. Siehe [Informationen zur Verwendung von Edge Delivery Services zum Bereitstellen Ihres Cloud Manager-Projekts](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md)

   ![Lösungen auswählen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/add-production-program-with-edge-v2.png)




   <!-- * If you selected the **[Enable Enhanced Security](#security)** option, you can select only as many solutions for which HIPAA entitlements are available. -->



   * Klicken Sie ![Chevron Size 300 icon](https://spectrum.adobe.com/static/icons/ui_18/ChevronSize300.svg) links neben einem Lösungsnamen, um optionale Add-ons anzuzeigen. <!-- such as the **Commerce** add-on option under **Sites**. -->

   ![Add-ons auswählen](assets/setup-prod-commerce.png)

1. Wenn Sie mit der Auswahl Ihrer Lösungen und Add-ons fertig sind, klicken Sie auf **Fortsetzen**.

1. Geben Sie auf der Registerkarte **Tag der Veröffentlichung** das Datum ein, an dem Ihr Produktionsprogramm veröffentlicht werden soll.

   ![Geplanten Tag der Live-Schaltung definieren](assets/set-up-go-live.png)

   * Sie können dieses Datum jederzeit bearbeiten.
   * Das Datum dient zu Informationszwecken und löst das Go Live-Widget auf der Seite [**Programmübersicht** aus](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#program-overview). Diese Funktion bietet zeitnah produktinterne Links zu Best Practices für AEM as a Cloud Service, um ein reibungsloses Live-Erlebnis zu gewährleisten.

1. Klicken Sie auf **Erstellen**. Cloud Manager erstellt Ihr Programm und zeigt es zur Auswahl auf der Landingpage an.

   ![Übersicht über Cloud Manager](assets/navigate-cm.png)

## Zusätzliche Optionen für Produktionsprogramme {#options}

Je nachdem, welche Berechtigungen Ihrer Organisation verfügbar sind, stehen Ihnen beim Erstellen eines Produktionsprogramms möglicherweise die folgenden zusätzlichen Optionen zur Verfügung.

### Sicherheit {#security}

Wenn Sie über die erforderlichen Berechtigungen verfügen, wird die Registerkarte **Sicherheit** als erste Registerkarte im Dialogfeld **`Set up for production`** angezeigt.

![Sicherheitsoptionen](assets/create-production-program-security.png)

Die Registerkarte **Sicherheit** bietet die Möglichkeit, **HIPAA** und/oder **WAF-DDOS-Schutz** oder beide Optionen für Ihr Produktionsprogramm zu aktivieren.

Die HIPAA-Compliance und WAF-DDOS (Web Application Firewall- Distributed Denial of Service) von Adobe erleichtert die Cloud-basierte Sicherheit als Teil eines mehrschichtigen Ansatzes zum Schutz vor Sicherheitslücken.

* **HIPAA**: Diese Option ermöglicht die Implementierung der Adobe HIPAA-fähigen Lösung.
   * Hier finden Sie [weitere Informationen](https://www.adobe.com/trust/compliance/hipaa-ready.html) zur Implementierung einer HIPAA-fähigen Lösung von Adobe.
   * Die HIPAA-Option kann nach der Programmerstellung weder aktiviert noch deaktiviert werden.
* **WAF-DDOS-Schutz**: Diese Option aktiviert die Firewall der Web-Anwendung über Regeln, um Ihre Anwendung zu schützen.
   * Nach der Aktivierung kann der WAF-DDOS-Schutz durch Einrichten einer [produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) konfiguriert werden.
   * Unter [Traffic-Filterregeln einschließlich WAF-Regeln](/help/security/traffic-filter-rules-including-waf.md) finden Sie Informationen dazu, wie Sie Traffic-Filterregeln in Ihrem Repository verwalten, damit sie ordnungsgemäß bereitgestellt werden.

### SLA {#sla}

Wenn Sie über die erforderlichen Berechtigungen verfügen, wird die Registerkarte **SLA** als zweite oder dritte Registerkarte im Dialogfeld **`Set up for production`** angezeigt.

![SLA-Optionen](assets/create-production-program-sla.png)

Sites und Forms bieten standardmäßig ein Service Level Agreement (SLA) mit 99,99 % an. Die Option **Service Level Agreement von 99,99 %** ermöglicht eine Mindestverfügbarkeit von 99,99 % für Ihre Produktionsumgebungen für Sites, Forms, Edge Delivery Services oder alle drei.

Das SLA von 99,99 % bietet unter anderem die Vorteile einer höheren Verfügbarkeit und geringeren Latenz.

Für Sites- und Forms-Programme erfordert die SLA von 99,99 % eine [zusätzliche Veröffentlichungsregion](/help/implementing/cloud-manager/manage-environments.md#multiple-regions), die im Programm auf die Produktionsumgebung angewendet werden muss. Wenn die [Anforderungen](#sla-requirements) für die Aktivierung des SLA von 99,99 % erfüllt sind, müssen Sie eine [Full-Stack-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) ausführen, um es zu aktivieren.

Für Edge Delivery Services besteht *keine* andere Anforderung als die Konfiguration der SLA-Lizenz von 99,99 % im Programm.

#### Anforderungen für ein SLA von 99,99 %  {#sla-requirements}

Zusätzlich zu den erforderlichen Berechtigungen umfasst die Verwendung des SLA von 99,99 % für Sites- oder Forms-Programme die folgenden zusätzlichen Anforderungen:

* Sowohl 99,99 % SLA als auch zusätzliche Berechtigungen für die Veröffentlichungsregion müssen der Organisation zur Verfügung stehen, wenn 99,99 % SLA auf das Programm angewendet wird.
* Cloud Manager überprüft, ob eine nicht verwendete Berechtigung für [zusätzliche Veröffentlichungsregion](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) verfügbar ist, bevor 99,99 % SLA auf das Programm angewendet wird.
* Wenn ein Programm bereits eine Produktionsumgebung mit mindestens einer zusätzlichen Veröffentlichungsregion enthält, prüft Cloud Manager beim Bearbeiten nur die Verfügbarkeit einer SLA-Berechtigung von 99,99 %.
* Damit 99,99 % SLA und die Berichterstellung aktiviert werden können, muss die [Produktions-/Staging-Umgebung](/help/implementing/cloud-manager/manage-environments.md#adding-environments) erstellt worden sein und es muss mindestens eine zusätzliche Veröffentlichungsregion auf die Produktions-/Staging-Umgebung angewendet worden sein.
   * Wenn Sie ein [erweitertes Netzwerk](/help/security/configuring-advanced-networking.md) verwenden, stellen Sie sicher, dass Sie die Empfehlungen im Dokument [Hinzufügen mehrerer Veröffentlichungsregionen zu einer neuen Umgebung](/help/implementing/cloud-manager/manage-environments.md#adding-regions) befolgen, damit die Konnektivität im Falle eines regionalen Ausfalls erhalten bleibt.
* Ihr SLA-Programm von 99,99 % muss immer mindestens eine zusätzliche Veröffentlichungsregion umfassen. Benutzende dürfen den letzten verbleibenden zusätzlichen Veröffentlichungsbereich nicht aus dem Programm löschen.
* Ihr SLA von 99,99 % wird für Produktionsprogramme unterstützt, für die die Sites- oder Forms-Lösung aktiviert ist.
* Führen Sie eine [vollständige Stack-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) aus, um das SLA von 99,99 % zu aktivieren (bzw. zu deaktivieren, wenn Sie ein Programm bearbeiten).

## Zugriff auf ein Programm {#accessing}

1. Wenn Sie Ihre Programmkarte auf der Landingpage sehen, klicken Sie auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), um die für Sie verfügbaren Menüoptionen anzuzeigen.

   ![Programmübersicht](assets/program-overview.png)

1. Wählen Sie **Cloud Manager** aus, um zur Seite **Übersicht** von Cloud Manager zu gelangen.

1. Die wichtigste Karte mit Handlungsaufforderung auf der Übersichtsseite führt Sie durch die Erstellung einer Umgebung, einer produktionsfremden Pipeline und schließlich einer Produktions-Pipeline.

   ![Programmübersicht](assets/set-up-prod5.png)

>[!TIP]
>
>Weitere Informationen zum Navigieren in Cloud Manager und zum Verständnis der Konsole **Meine Programme** finden Sie unter [Navigation in der Cloud Manager-Benutzeroberfläche](/help/implementing/cloud-manager/navigation.md).

>[!NOTE]
>
>Im Gegensatz zu einem [Sandbox-Programm](introduction-sandbox-programs.md#auto-creation) erfordert ein Produktionsprogramm, dass die Person das Projekt in der entsprechenden Cloud Manager-Rolle erstellt und über die Self-Service-Benutzeroberfläche eine Umgebung hinzufügt.


