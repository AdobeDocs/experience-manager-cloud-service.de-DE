---
title: Erstellen von Produktionsprogrammen
description: Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Produktionsprogramm für das Hosten von Live-Traffic erstellen.
exl-id: 4ccefb80-de77-4998-8a9d-e68d29772bb4
source-git-commit: 418aff3f8519bba4bf5e2459175983633eb664b8
workflow-type: ht
source-wordcount: '1031'
ht-degree: 100%

---


# Erstellen von Produktionsprogrammen {#create-production-program}

Ein Produktionsprogramm ist für einen Benutzer gedacht, der mit AEM und Cloud Manager vertraut ist und Code für die Bereitstellung zum Hosten von Live-Traffic schreiben, erstellen und testen möchte.

Weitere Informationen zu Programmtypen finden Sie im Dokument [Programm- und Programmtypen](program-types.md).

## Erstellen eines Produktionsprogramms {#create}

Gehen Sie wie folgt vor, um ein Produktionsprogramm zu erstellen. Beachten Sie, dass abhängig von den Berechtigungen Ihrer Organisation möglicherweise [zusätzliche Optionen](#options) angezeigt werden, wenn Sie Ihr Programm hinzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Tippen oder klicken Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** oben rechts auf dem Bildschirm auf **Programm hinzufügen**.

   ![Cloud Manager-Landingpage](assets/log-in.png)

1. Wählen Sie im Assistenten „Programm erstellen“ die Option **Für die Produktion einrichten** aus, um ein Produktionsprogramm zu erstellen und einen Programmnamen anzugeben.

   ![Assistent zum Erstellen von Programmen](assets/create-production-program.png)

1. Optional können Sie ein Bild zum Programm hinzufügen, indem Sie eine Bilddatei per Drag-and-Drop auf das Ziel **Programmbild hinzufügen** ziehen oder darauf klicken, um ein Bild aus einem Datei-Browser auszuwählen. Wählen Sie **Weiter**.

1. Wählen Sie auf der Registerkarte **Lösungen und Add-ons** die Lösungen aus, die im Programm enthalten sein sollen.

   * Wenn Sie sich nicht sicher sind, ob Sie ein oder mehrere Programme für die verschiedenen verfügbaren Lösungen benötigen, wählen Sie diejenige aus, die für Sie am interessantesten ist. Sie können zusätzliche Lösungen aktivieren, indem Sie [das Programm später bearbeiten](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md). Weitere Empfehlungen zur Programmeinrichtung finden Sie im Dokument [Einführung in Produktionsprogramme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md).
   * Für die Programmerstellung ist mindestens eine Lösung erforderlich.
   * Wenn Sie die Option **[Erweiterte Sicherheit aktivieren](#security)** ausgewählt haben, dürfen Sie nur diejenigen Lösungen auswählen, für die HIPAA-Berechtigungen verfügbar sind.

   ![Lösungen auswählen](assets/setup-prod-select.png)

1. Klicken Sie auf den Pfeil vor den Lösungsnamen, um optionale Add-ons anzuzeigen, z. B. die Add-on-Option **Commerce** unter **Sites**.

   ![Add-ons auswählen](assets/setup-prod-commerce.png)

1. Klicken Sie nach der Auswahl von Lösungen und Add-ons auf **Weiter**.

1. Geben Sie auf der Registerkarte **Tag der Live-Schaltung** das Datum ein, an dem Ihr Produktionsprogramm veröffentlicht werden soll.

   ![Geplanten Tag der Live-Schaltung definieren](assets/set-up-go-live.png)

   * Dieses Datum kann jederzeit bearbeitet werden.
   * Dieses Datum dient nur zu Informationszwecken und löst das Live-Schaltungs-Widget auf der [**Programmübersichtsseite** ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#program-overview) aus, um rechtzeitig produktinterne Links zur Best-Practice-Dokumentation von AEM as a Cloud Service bereitzustellen und Ihnen so eine erfolgreiche und reibungslose Live-Schaltung ermöglicht.

1. Klicken Sie auf **Erstellen**.

Ihr Programm wird von Cloud Manager erstellt, wird auf der Landingpage angezeigt und kann dort ausgewählt werden.

![Übersicht über Cloud Manager](assets/navigate-cm.png)

## Zusätzliche Produktions-Programmoptionen {#options}

Je nachdem, welche Berechtigungen Ihrer Organisation zur Verfügung stehen, stehen Ihnen beim Erstellen eines Produktionsprogramms möglicherweise zusätzliche Optionen zur Verfügung.

### Sicherheit {#security}

Wenn Sie über die erforderlichen Berechtigungen verfügen, wird die Registerkarte **Sicherheit** als erste Registerkarte im Dialog **Für Produktion einrichten** angezeigt.

Die Registerkarte **Sicherheit** bietet die Möglichkeit, **HIPAA** und/oder **WAF-DDOS-Schutz** für Ihr Produktionsprogramm zu aktivieren.

Die HIPAA-konforme Web Application Firewall (WAF) von Adobe erleichtert die Cloud-basierte Sicherheit als Teil eines mehrschichtigen Ansatzes zum Schutz vor Sicherheitslücken.

* **HIPAA**: Diese Option ermöglicht die Implementierung der Adobe HIPAA-fähigen Lösung.
   * Hier finden Sie [weitere Informationen](https://www.adobe.com/go/hipaa-ready) zur Implementierung einer HIPAA-fähigen Lösung von Adobe.
   * Die HIPAA-Option kann nach der Programmerstellung weder aktiviert noch deaktiviert werden.
* **WAF-DDOS-Schutz**: Diese Option aktiviert die Firewall der Web-Anwendung über Regeln, um Ihre Anwendung zu schützen.
   * Nach der Aktivierung kann der WAF-DDOS-Schutz durch Einrichten einer [produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) konfiguriert werden.
   * Im Dokument [Traffic-Filterregeln einschließlich WAF-Regeln](/help/security/traffic-filter-rules-including-waf.md) finden Sie Informationen dazu, wie Sie Traffic-Filterregeln in Ihrem Repository verwalten, damit sie ordnungsgemäß bereitgestellt werden.

![Sicherheitsoptionen](assets/create-production-program-security.png)

### SLA {#sla}

Wenn Sie über die erforderlichen Berechtigungen verfügen, wird die Registerkarte **SLA** als zweite oder dritte Registerkarte im Dialog **Für Produktion einrichten** angezeigt.

AEM Sites bietet standardmäßig ein Service Level Agreement (SLA) zu 99,9 % an. **99,99 % Service Level Agreement** ermöglicht einen minimalen Betriebszeitprozentsatz von 99,99 % für Ihre Produktionsumgebungen.

SLA mit 99,99 % bietet Vorteile wie höhere Verfügbarkeit und geringere Latenz und erfordert, dass eine [zusätzliche Veröffentlichungsregion](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) auf die Produktionsumgebung im Programm angewendet wird.

![SLA-Optionen](assets/create-production-program-sla.png)

Sobald die [Anforderungen](#sla-requirements) für die Aktivierung von 99,99 % SLA erfüllt sind, müssen Sie eine [Full-Stack-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) ausführen, um sie zu aktivieren.

#### Anforderungen für 99,99 % SLA {#sla-requirements}

Über die erforderlichen Berechtigungen hinaus gelten für 99,99 % SLA zusätzliche Nutzungsanforderungen.

* Sowohl 99,99 % SLA als auch zusätzliche Berechtigungen für die Veröffentlichungsregion müssen der Organisation zum Zeitpunkt der Anwendung von 99,99 % SLA auf das Programm zur Verfügung stehen.
* Um eine SLA von 99,99 % auf das Programm anzuwenden, prüft Cloud Manager, ob eine nicht verbrauchte [zusätzliche Veröffentlichungsregion](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) ebenfalls verfügbar ist und auf das Programm angewendet werden kann.
* Wenn ein Programm bereits eine Produktionsumgebung mit mindestens einer zusätzlichen Veröffentlichungsregion enthält, prüft Cloud Manager beim Bearbeiten nur die Verfügbarkeit einer SLA-Berechtigung von 99,99 %.
* Damit der SLA von 99,99 % und die Berichterstellung aktiviert werden können, muss die [Produktions-/Staging-Umgebung](/help/implementing/cloud-manager/manage-environments.md#adding-environments) erstellt worden sein und mindestens eine zusätzliche Veröffentlichungsregion auf die Produktions-/Staging-Umgebung angewendet worden sein.
   * Wenn Sie ein [erweitertes Netzwerk](/help/security/configuring-advanced-networking.md) verwenden, stellen Sie sicher, dass Sie im Dokument [Hinzufügen mehrerer Veröffentlichungsregionen zu einer neuen Umgebung](/help/implementing/cloud-manager/manage-environments.md#adding-regions) nach Empfehlungen suchen, damit die Konnektivität im Falle eines regionalen Ausfalls erhalten bleibt.
* Mindestens eine zusätzliche Veröffentlichungsregion muss in Ihrem 99,99 %-SLA-Programm verbleiben. Benutzende dürfen den letzten zusätzlichen Veröffentlichungsbereich nicht aus Ihrem 99,99 %-SLA-Programm löschen.
* 99,99 % SLA wird für Produktionsprogramme unterstützt, für die die Sites-Lösung aktiviert ist.
* Sie müssen eine [vollständige Stack-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) ausführen, um 99,99 % SLA zu aktivieren (oder, wenn Sie ein Programm bearbeiten, zu deaktivieren).

## Zugriff auf ein Programm {#accessing}

1. Wenn Sie die Programmkarte auf der Landingpage sehen, wählen Sie die Schaltfläche mit den Auslassungspunkten aus, um die für Sie verfügbaren Menüoptionen anzuzeigen.

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
