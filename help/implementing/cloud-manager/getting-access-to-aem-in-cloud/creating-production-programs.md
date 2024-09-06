---
title: Erstellen von Produktionsprogrammen
description: Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Produktionsprogramm für das Hosten von Live-Traffic erstellen.
exl-id: 4ccefb80-de77-4998-8a9d-e68d29772bb4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 6a3d2d484bde20586b329010cdfe156570e736f5
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 34%

---


# Erstellen von Produktionsprogrammen {#create-production-program}

Ein Produktionsprogramm richtet sich an Anwender, die mit AEM und Cloud Manager vertraut sind und Code schreiben, erstellen und testen können, um ihn für Live-Traffic bereitzustellen.

Weitere Informationen zu Programmtypen finden Sie im Dokument [Grundlegendes zu Programm- und Programmtypen](program-types.md) .

## Erstellen eines Produktionsprogramms {#create}

Abhängig von den Berechtigungen Ihres Unternehmens sehen Sie beim Hinzufügen Ihres Programms möglicherweise [zusätzliche Optionen](#options) .

**So erstellen Sie ein Produktionsprogramm:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** in der rechten oberen Ecke auf **Programm hinzufügen**.

   ![Cloud Manager-Landingpage](assets/log-in.png)

1. Geben Sie im Assistenten *Erstellen Ihres Programms* im Textfeld **Programmname** den gewünschten Namen für das Programm ein.

1. Wählen Sie unter **Programmziel** die Option **`Set up for production`** aus.

   ![Assistent zum Erstellen von Programmen](assets/create-production-program.png)

1. (Optional) Führen Sie in der rechten unteren Ecke des Assistenten-Dialogfelds einen der folgenden Schritte aus:

   * Ziehen Sie eine Bilddatei per Drag-and-Drop auf das Ziel **Programmbild hinzufügen** .
   * Klicken Sie auf **Programmbild hinzufügen** und wählen Sie dann ein Bild aus einem Dateibrowser aus.
   * Klicken Sie auf das Papierkorbsymbol, um ein hinzugefügtes Bild zu löschen.

1. Klicken Sie auf **Weiter**.

1. Wählen Sie im Listenfeld **Lösungen und Add-ons** eine oder mehrere Lösungen aus, die in das Programm aufgenommen werden sollen.

   * Wenn Sie sich nicht sicher sind, ob Sie ein oder mehrere Programme für die verschiedenen verfügbaren Lösungen benötigen, wählen Sie diejenige aus, die für Sie am interessantesten ist. Sie können zusätzliche Lösungen aktivieren, indem Sie [das Programm später bearbeiten](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md). Weitere Empfehlungen zur Programmeinrichtung finden Sie im Dokument [Einführung in Produktionsprogramme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md).
   * Für die Programmerstellung ist mindestens eine Lösung erforderlich.
   * Wählen Sie **Edge Deliver Services** für eine vollständig verwaltete CDN-Lösung, die digitale Erlebnisse optimiert. Siehe [Über die Verwendung von Edge Delivery Services zur Bereitstellung Ihres Cloud Manager-Projekts](#edge-overview)
   * Wenn Sie die Option **[Erweiterte Sicherheit aktivieren](#security)** ausgewählt haben, können Sie nur so viele Lösungen auswählen, für die HIPAA-Berechtigungen verfügbar sind.

   ![Lösungen auswählen](/help/implementing/cloud-manager/assets/add-production-program-with-edge.png)

1. Klicken Sie auf den Pfeil links neben dem Lösungsnamen, um optionale Add-ons wie die Add-On-Option **Commerce** unter **Sites** anzuzeigen.

   ![Add-ons auswählen](assets/setup-prod-commerce.png)

1. Klicken Sie nach der Auswahl von Lösungen und Add-ons auf **Weiter**.

1. Geben Sie auf der Registerkarte **Aufschaltdatum** das Datum ein, an dem Sie das Produktionsprogramm &quot;Aufschaltdatum&quot;festlegen möchten.

   ![Geplanten Tag der Live-Schaltung definieren](assets/set-up-go-live.png)

   * Sie können dieses Datum jederzeit bearbeiten.
   * Das Datum dient zu Informationszwecken und Trigger des Widgets &quot;Go Live&quot;auf der Seite [**Programmübersicht**](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#program-overview). Diese Funktion bietet zeitnahe produktinterne Links zu Best Practices für AEM as a Cloud Service, um ein reibungsloses Live-Erlebnis zu gewährleisten.

1. Klicken Sie auf **Erstellen**. Cloud Manager erstellt Ihr Programm und zeigt es zur Auswahl auf der Landingpage an.

![Übersicht über Cloud Manager](assets/navigate-cm.png)

## Zusätzliche Optionen für Produktionsprogramme {#options}

Je nachdem, welche Berechtigungen Ihrer Organisation zur Verfügung stehen, stehen Ihnen beim Erstellen eines Produktionsprogramms möglicherweise zusätzliche Optionen zur Verfügung.

### Sicherheit {#security}

Wenn Sie über die erforderlichen Berechtigungen verfügen, wird die Registerkarte **Sicherheit** als erste Registerkarte im Dialogfeld **`Set up for production`** angezeigt.

![Sicherheitsoptionen](assets/create-production-program-security.png)

Auf der Registerkarte **Sicherheit** finden Sie die Optionen zum Aktivieren von **HIPAA** oder **WAF-DDOS-Schutz** oder beidem für Ihr Produktionsprogramm.

Adobe HIPAA Compliant und WAF-DDOS (Web Application Firewall - Distributed Denial of Service) erleichtern die Cloud-basierte Sicherheit als Teil eines mehrstufigen Ansatzes zum Schutz vor Sicherheitslücken.

* **HIPAA**: Diese Option ermöglicht die Implementierung der Adobe HIPAA-fähigen Lösung.
   * Hier finden Sie [weitere Informationen](https://www.adobe.com/trust/compliance/hipaa-ready.html) zur Implementierung einer HIPAA-fähigen Lösung von Adobe.
   * Die HIPAA-Option kann nach der Programmerstellung weder aktiviert noch deaktiviert werden.
* **WAF-DDOS-Schutz** - Mit dieser Option wird die Webanwendungs-Firewall durch Regeln zum Schutz Ihrer Anwendung aktiviert.
   * Nach der Aktivierung kann der WAF-DDOS-Schutz konfiguriert werden, indem eine [produktionsfremde Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) eingerichtet wird.
   * Unter [Traffic-Filterregeln einschließlich WAF-Regeln](/help/security/traffic-filter-rules-including-waf.md) erfahren Sie, wie Sie Traffic-Filterregeln in Ihrem Repository verwalten, damit sie ordnungsgemäß bereitgestellt werden.

### SLA {#sla}

Wenn Sie über die erforderlichen Berechtigungen verfügen, wird die Registerkarte **SLA** als zweite oder dritte Registerkarte im Dialogfeld **`Set up for production`** angezeigt.

![SLA-Optionen](assets/create-production-program-sla.png)

AEM Sites und Forms bieten standardmäßig ein Service Level Agreement (SLA) mit 99,99 % an. Die Option **Service Level Agreement von 99,99 %** ermöglicht einen minimalen Betriebszeitprozentsatz von 99,99 % für Ihre Sites- und/oder Forms-Produktionsumgebungen.

SLA mit 99,99 % bietet Vorteile wie höhere Verfügbarkeit und geringere Latenz und erfordert, dass eine [zusätzliche Veröffentlichungsregion](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) auf die Produktionsumgebung im Programm angewendet wird.

Wenn die [Anforderungen](#sla-requirements) für die Aktivierung von 99,99 % SLA erfüllt sind, müssen Sie eine [vollständige Stack-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) ausführen, um sie zu aktivieren.

#### Anforderungen für 99,99 % SLA {#sla-requirements}

Über die erforderlichen Berechtigungen hinaus gelten für 99,99 % SLA zusätzliche Nutzungsanforderungen.

* Die Organisation muss über 99,99 % SLA und zusätzliche Berechtigungen für Veröffentlichungsgebiete verfügen, wenn SLA 99,99 % auf das Programm angewendet wird.
* Cloud Manager überprüft, ob eine nicht verwendete Berechtigung für [zusätzliche Veröffentlichungsregion](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) verfügbar ist, bevor SLA 99,99 % auf das Programm angewendet wird.
* Wenn ein Programm bereits eine Produktionsumgebung mit mindestens einer zusätzlichen Veröffentlichungsregion enthält, prüft Cloud Manager beim Bearbeiten nur die Verfügbarkeit einer SLA-Berechtigung von 99,99 %.
* Für die Aktivierung von 99,99 % SLA und Berichterstellung muss die [Produktions-/Staging-Umgebung](/help/implementing/cloud-manager/manage-environments.md#adding-environments) erstellt und mindestens ein zusätzlicher Veröffentlichungsbereich in der Produktions-/Staging-Umgebung angewendet worden sein.
   * Achten Sie bei Verwendung von [erweiterten Netzwerken](/help/security/configuring-advanced-networking.md) darauf, im Dokument &quot;[Hinzufügen mehrerer Publish-Regionen zu einer neuen Umgebung&quot;](/help/implementing/cloud-manager/manage-environments.md#adding-regions)&quot;Empfehlungen zu finden, damit bei regionalem Fehler die Konnektivität aufrechterhalten wird.
* Mindestens eine zusätzliche Veröffentlichungsregion muss in Ihrem 99,99 %-SLA-Programm verbleiben. Benutzende dürfen den letzten zusätzlichen Veröffentlichungsbereich nicht aus Ihrem 99,99 %-SLA-Programm löschen.
* Ein SLA von 99,99 % wird für Produktionsprogramme unterstützt, für die die Sites- oder Forms-Lösung aktiviert ist.
* Führen Sie eine [vollständige Stack-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) aus, um beim Bearbeiten eines Programms die SLA 99,99 % zu aktivieren oder zu deaktivieren.

## Auf das Programm zugreifen {#accessing}

1. Wenn Sie die Programmkarte auf der Landingpage sehen, wählen Sie die Schaltfläche mit den Auslassungspunkten aus, um die für Sie verfügbaren Menüoptionen anzuzeigen.

   ![Programmübersicht](assets/program-overview.png)

1. Wählen Sie **Cloud Manager** aus, um zur Seite **Übersicht** von Cloud Manager zu gelangen.

1. Die Hauptaktionskarte auf der Übersichtsseite führt Sie durch die Erstellung einer Umgebung, einer Nicht-Produktions-Pipeline und schließlich einer Produktions-Pipeline.

   ![Programmübersicht](assets/set-up-prod5.png)

>[!TIP]
>
>Weitere Informationen zum Navigieren in Cloud Manager und zum Verständnis der Konsole **Meine Programme** finden Sie unter [Navigieren in der Cloud Manager-Benutzeroberfläche](/help/implementing/cloud-manager/navigation.md) .

>[!NOTE]
>
>Im Gegensatz zu einem [Sandbox-Programm](introduction-sandbox-programs.md#auto-creation) erfordert ein Produktionsprogramm, dass der Benutzer mit der entsprechenden Cloud Manager-Rolle das Projekt erstellt und über die Self-Service-Benutzeroberfläche eine Umgebung hinzufügt.


