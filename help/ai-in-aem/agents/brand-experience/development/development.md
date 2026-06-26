---
title: Übersicht über den Entwicklungsagenten
description: Erfahren Sie, wie der Entwicklungsagent in AEM fehlgeschlagene Pipelines in Cloud Manager analysiert und Protokolle erstellt, um Code-Fehlerbehebungen vorzuschlagen und das Debugging zu beschleunigen. Erfahren Sie außerdem, wie Sie Cloud Manager-Informationen abrufen, Hilfe bei Replikationsfehlern erhalten und wie Sie ruhige Stunden einrichten und kostenlose Zeiträume für AEM-Updates aktualisieren.
feature: Agentic AI, AI Assistant, AI Tools, User Roles
role: User, Admin, Developer
exl-id: 2194556f-aac2-4cdd-8f7f-00c92c8c4424
nudge: please
source-git-commit: 152b867e74ac87763f7249fa7e50986b257736b3
workflow-type: tm+mt
source-wordcount: '1547'
ht-degree: 8%

---


# Übersicht über den Entwicklungsagenten {#development-agent-overview}

[Im Rahmen der Brand Experience Agent &#x200B;](/help/ai-in-aem/agents/brand-experience/overview.md) der Entwicklungsagent herkömmliche AEM Java-Stack-Entwickler und -Administratoren dabei, Code effizienter zu erstellen, zu debuggen, bereitzustellen und zu optimieren.

Es unterstützt die folgenden Aufträge, auf die über die Konversationsoberfläche des KI-Assistenten zugegriffen werden kann.

* Cloud Manager-Vorgang: Nur-Lese-Vorgänge, einschließlich der Auflistung von Programmen und Umgebungen und des Pipeline-Status
* Pipeline-Fehlerbehebung: Pipelines debuggen fehlgeschlagen
* Ruhezeiten und Verwaltung freier Zeiträume aktualisieren Auftrag: Ruhestunden anzeigen, erstellen und bearbeiten und Freie Zeiträume aktualisieren
* Fehlerbehebung bei Replikationsproblemen (Beta): Beheben Sie replikationsbezogene Probleme, z. B. blockierte Warteschlangen.

>[!NOTE]
>
> Entwickler finden diese KI-gestützten Funktionen ebenfalls nützlich:
> * [IDE Agent Skills](/help/ai-in-aem/local-development-with-ai-tools.md#agent-skills) für lokale Entwicklungsszenarien wie das Generieren von AEM-Komponenten.
> * [Lokale MCP-Server](/help/ai-in-aem/local-development-with-ai-tools.md#aem-quickstart-mcp-server) für die lokale Entwicklung, insbesondere zum Debugging von AEM- und Dispatcher-Problemen.
> * [Remote-MCP-Server](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md) für den Zugriff auf APIs und AEM-Agenten.

>[!IMPORTANT]
>
>KI-generierte Antworten können ungenau oder irreführend sein. Überprüfen Sie unbedingt die vorgeschlagenen Fehlerbehebungen und Antworten.
>
>Siehe auch [Benutzerhandbücher für generative KI von Adobe Experience Cloud](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

Sie können das für den Entwicklungsagenten spezifische Feedback per E-Mail an [aem-devagent@adobe.com](mailto:aem-devagent@adobe.com) senden.

## Cloud Manager-Vorgang {#cloud-manager-job}

Hier finden Sie Informationen zu Ihren AEM-Programmen und -Umgebungen, einschließlich:
* Auflisten von Programmen und Umgebungen
* Auflisten von Umgebungsvariablen
* Suchen der Namen von Pipelines sowie des aktuellen Ausführungsstatus und der Schrittdetails
* Abrufen von Links zu Protokollen, die heruntergeladen werden können

### Eingabeaufforderungen {#sample-cm-job-prompts}


| Prompt | Ergebnis |
| --- | --- |
| *Listen Sie alle meine AEM Cloud Service-Programme auf* | Listet Programme auf, auf die Sie Zugriff haben. |
| *Abrufen von Details zur 12345* | Abrufen von Details zum Programm. |
| *Auflisten von Umgebungen in 12345* | Führt Umgebungen im Programm auf. |
| *Abrufen von Protokollen für die Produktionsumgebung* | Ruft Links zu verschiedenen AEM-, Dispatcher- und CDN-Protokolldateien ab, damit sie für Debugging- oder andere Zwecke heruntergeladen werden können. |
| *Auflisten von Pipelines für 12345* | Listen Sie Pipelines im Programm auf. |
| *Wie ist der Status der aktuellen Pipeline-Ausführung?* | Antwortet mit Status der Pipeline. |
| *Erhalten Sie die Build-Protokoll-Links für die Pipeline-Ausführung 12345* | Ruft Links zu Pipeline-Build-Protokollen für eine bestimmte Pipeline-Ausführung ab. |


## Ruhestunden und Aktualisieren von Freie Zeiträume Management Job {#control-updates-job}

Ruhestunden anzeigen, erstellen und bearbeiten und Freizeiten aktualisieren direkt über den AEM AI-Assistenten.

Der Hauptvorteil liegt in der Verringerung von Zeitplanfehlern. Wenn Sie eine Anfrage stellen, führt Sie der Assistent durch das Mögliche und kennzeichnet die geltenden Beschränkungen, z. B. die Obergrenze für drei Zeiträume, die obligatorische Lücke von einer Woche zwischen Zeiträumen und die geplanten Zeitfenster für Wartungsausschlüsse, für die Sie keinen Zeitplan festlegen können.

Anstatt also nach einer fehlgeschlagenen Konfiguration eine Einschränkung zu ermitteln, werden Geschäftsinhaber und Bereitstellungs-Manager im selben Gespräch auf einen gültigen Zeitplan geleitet. Dadurch werden wichtige Geschäftsfenster vor automatischen Wartungs-Updates geschützt und gleichzeitig das Hin- und Herschieben und Fehlkonfigurieren reduziert.

### Eingabeaufforderungen {#sample-updates-prompts}

| Prompt | Ergebnis |
| --- | --- |
| *Wie sieht der aktuelle Aktualisierungszeitplan für Programm 12345 aus?* | Dies führt zu einer Auflistung der aktuellen AEM-Aktualisierungsregeln. |
| *Blockieren Sie AEM-Updates von 9 bis 17 Uhr EST für 12345* | Richtet eine Regel ein, damit AEM-Aktualisierungen nicht während der Standardarbeitszeit angewendet werden. |
| *Entfernen des täglichen Update-Blocks für das Programm 12345* | Entfernt die Regeln, die AEM-Updates verhindern. |
| *AEM-Updates ab zwei Wochen pausieren, um 12345* zu erhalten | Erstellt eine Regel, um AEM-Aktualisierungen zu verhindern. |
| *Mein Programm wird zu unangenehmen Zeiten immer wieder aktualisiert. Welche Optionen habe ich?* | Antwortet mit Informationen darüber, wie Regeln zur Steuerung des AEM-Aktualisierungszeitplans festgelegt werden. |



## Fehlerbehebung bei Pipeline-Aufträgen {#cloud-manager-pipeline-troubleshooting}

Dieser Auftrag kann Pipeline-Status abrufen und Ihnen bei der Fehlerbehebung bei fehlgeschlagenen Build-Schritten helfen, indem Fehlerbehebungen vorgeschlagen werden. Dies spart Zeit beim Debugging von AEM as a Cloud Service-Bereitstellungen in Entwicklungs-, Staging- und Produktionsumgebungen. Es werden Build-Protokolle und verwandter Code untersucht, um eine Fehlerbehebung zu empfehlen, die Sie manuell anwenden können.

>[!VIDEO](https://video.tv.adobe.com/v/3478006?quality=12&learn=on)

>[!NOTE]
>
>Die Fehlerbehebung bei Pipelines ist auf Full-Stack-Pipelines (Bereitstellung und Code-Qualität) und die Web-Stufen-Konfigurations-Pipeline beschränkt.

<!--
To access this agent, please refer to the [release notes](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs) for instructions on how to enroll in the beta program, being sure to indicate your interest in the  Development Agent. You can also email development agent–specific feedback to [aem-devagent@adobe.com.](mailto:aem-devagent@adobe.com)

-->

[In einem Tutorial erfahren &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/ai/agents/development-agent-troubleshoot-ci-cd-pipeline), wie Sie mit dem Entwicklungsagenten Pipeline-Fehler beheben können.

### Zugriff auf den Entwicklungsagenten über Cloud Manager {#how-to-access-the-agent}

Der Zugriff auf den Entwicklungsagenten erfolgt über den KI-Assistenten, der sich in den Benutzeroberflächen, einschließlich Cloud Manager oder Experience Hub, befindet.

1. Klicken Sie zunächst auf [Adobe Experience Cloud](https://experience.adobe.com), um die Startseite zu öffnen.

   ![Startseite von Adobe Experience Cloud](/help/implementing/cloud-manager/assets/experience-cloud-experiencemanager.png)

1. Klicken Sie in der linken Leiste unter **Services** auf **Cloud Manager**.

   ![Die linke Leiste von Experience Hub mit Cloud Manager, das unter der Überschrift Services aufgeführt ist](/help/implementing/cloud-manager/assets/experience-hub-role-selection.png)

   >[!IMPORTANT]
   >
   >Die angezeigten Widgets, Tools und Artefakte hängen von der Benutzerrolle, den Berechtigungen und dem AEM-Bereitstellungstyp (AEM as a Cloud Service oder Managed Services 6.5/6.5 LTS) ab.

1. Klicken Sie in der linken Leiste unter **Programm** auf **![Übersichtssymbol](/help/implementing/cloud-manager/configuring-pipelines/assets/overview.svg) Übersicht**.

1. Klicken Sie auf der **Programmübersicht** auf der Karte **Pipelines** auf eine Pipeline.

   ![Ausgewählte Pipeline](/help/ai-in-aem/agents/brand-experience/development/assets/dev-agent-pipeline-select.png)

1. Beachten Sie auf **Seite Build- und** die fehlgeschlagene Pipeline.

   ![Pipeline-Fehler, wie auf der Seite Build- und Code-Überprüfung angezeigt](/help/ai-in-aem/agents/brand-experience/development/assets/dev-agent-pipeline-failure.png)

1. Klicken Sie in der rechten oberen Ecke der Benutzeroberfläche von AEM (entweder auf den Cloud Manager-Seiten oder in der Autoreninstanz der AEM-Umgebungen) auf das Symbol **KI-Assistent**.

   ![Symbol „KI-Assistent“ in der Symbolleiste](/help/implementing/cloud-manager/assets/ai-assistant-icon.png)

   Siehe auch [KI-Assistent in AEM](/help/implementing/cloud-manager/ai-assistant-in-aem.md).

1. Geben Sie im Textfeld **KI-Assistent** unten Ihre Frage oder Ihren Prompt ein und drücken Sie dann `Enter` oder klicken Sie auf das Symbol zum ![Senden](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Send_18_N.svg).

   Beispiel:
   *Analysieren Sie im Programm „eda-org-01-no-access“ den Fehler bei der Pipeline „no-access“ und beheben Sie die Fehler.*

   Die Eingabeaufforderung führt zur folgenden Antwort.

   ![KI-Assistenten-Eingabeaufforderung und resultierende Antwort](/help/ai-in-aem/agents/brand-experience/development/assets/dev-agent-prompt-response.png)

#### Fehlerbehebung direkt aus einer fehlgeschlagenen Pipeline-Ausführung {#troubleshoot-with-ai-button}

Wenn eine Pipeline-Ausführung fehlschlägt, wird von Cloud Manager auch direkt auf **Seite zur Pipeline-Ausführung die Schaltfläche** Fehlerbehebung mit KI“ angezeigt. Dies ist die schnellste Möglichkeit, eine Fehlerbehebungssitzung zu starten, da die fehlgeschlagene Ausführung automatisch als Kontext an den KI-Assistenten übergeben wird - es ist keine manuelle Eingabeaufforderung erforderlich.

1. Öffnen Sie in Cloud Manager die fehlgeschlagene Pipeline-Ausführung. Das Statusbanner wird **Fehlgeschlagen** und die Schaltfläche **Fehlerbehebung mit KI** wird oben rechts auf der Seite angezeigt.

   ![Seite „Fehlgeschlagene Pipeline-Ausführung“ mit der Schaltfläche „Fehlerbehebung mit KI“ und dem Bedienfeld „KI-Assistent“ mit einer vorab geladenen Analyse](/help/ai-in-aem/agents/brand-experience/development/assets/dev-agent-troubleshoot-button.png)

1. Klicken Sie auf **Fehlerbehebung mit KI**.

   Das Bedienfeld KI-Assistent wird auf der rechten Bildschirmseite geöffnet. Der Assistent verweist automatisch auf die fehlgeschlagene Pipeline-Ausführung und beginnt mit der Analyse, ermittelt den fehlgeschlagenen Schritt und schlägt eine Fehlerbehebung vor, die Sie manuell anwenden können.

1. Überprüfen Sie die Antwort und setzen Sie die Konversation bei Bedarf im Textfeld **KI-Assistent** fort, um Folgefragen zu stellen oder weitere Details anzufordern.

#### Fehlerbehebung im Widget Fehlgeschlagene Pipelines von Experience Home {#troubleshoot-from-experience-home-widget}

Experience Home enthält ein Widget **Fehlgeschlagene Pipelines** mit dem Sie einen Überblick über Pipeline-Fehler in Ihren Programmen erhalten, ohne dass Sie zuerst zu Cloud Manager navigieren müssen. Jede Zeile im Widget stellt eine fehlgeschlagene Pipeline dar und zeigt den Pipeline-Namen, das Datum und die Uhrzeit der letzten Ausführung, die Dauer sowie den fehlgeschlagenen Schritt an. Für **Eintrag ist eine Schaltfläche** Fehlerbehebung mit KI“ inline verfügbar.

>[!NOTE]
>
>Das **Fehlgeschlagene Pipelines** **-Widget ist nur sichtbar, wenn in der Experience** Startseite die Rolle „Admin &amp; IT“ ausgewählt ist. Wenn das Widget nicht angezeigt wird, überprüfen Sie mithilfe der Rollenauswahl in der rechten oberen Ecke **Rolle, ob Ihre Rolle auf** Admin &amp; IT“ eingestellt ist.

![Das Widget Fehlgeschlagene Pipelines auf der Experience-Startseite zeigt einen fehlgeschlagenen Pipeline-Eintrag mit der Schaltfläche Fehlerbehebung mit KI an](/help/ai-in-aem/agents/brand-experience/development/assets/dev-agent-failed-pipelines-widget.png)

1. Öffnen Sie [Experience-Startseite](https://experience.adobe.com) klicken Sie auf **Experience Manager** und scrollen Sie zum Widget **Fehlgeschlagene Pipelines**.

1. Suchen Sie die Pipeline, die Sie untersuchen möchten, und klicken Sie dann auf **Fehlerbehebung mit KI** in dieser Zeile.

   Das Bedienfeld KI-Assistent wird geöffnet, wobei die fehlgeschlagene Pipeline-Ausführung im Kontext vorgeladen wird. Der Assistent beginnt automatisch mit der Analyse, ermittelt die Grundursache und schlägt eine Lösung vor.

1. Überprüfen Sie die Antwort und setzen Sie die Konversation bei Bedarf im Textfeld **KI-Assistent** fort, um Folgefragen zu stellen oder weitere Details anzufordern.

### Berechtigungen {#permissions}

Für die Fehlerbehebung bei Pipelines ist entweder die Rolle Cloud Manager - Entwickler oder die Rolle Cloud Manager - Programm-Manager erforderlich.

### Eingabeaufforderungen {#sample-pipeline-prompts}

| Prompt | Ergebnis |
| --- | --- |
| *Fehlerbehebung bei fehlgeschlagener Pipeline* | Führt eine Analyse der Gründe für den Pipeline-Fehler durch. Wenn nicht klar ist, auf welche Pipeline verwiesen wird, werden dem Benutzer zusätzliche Fragen gestellt. |
| *Liste meiner fehlgeschlagenen Pipelines für das Hauptprogramm des Programms.* | Auch wenn die Ergebnisse variieren können, gibt diese Eingabeaufforderung eine Tabelle mit fehlgeschlagenen Pipelines mit einem Folgenachweis zurück, der auf eine bestimmte zu analysierende Pipeline verweist. |
| *Analysieren Sie meine fehlgeschlagene Pipeline mit dem Namen „Entwicklungs-Pipeline“* | Diese Eingabeaufforderung führt zu einer Analyse der fehlgeschlagenen Pipeline mit Vorschlägen zur Korrektur. Bei mehreren Fehlern werden dem Benutzer zusätzliche Fragen gestellt. |
| *Fehlerbehebung bei der Pipeline-Ausführung 1234567* | Durch Angabe einer exakten Pipeline-Ausführungs-ID wird eine Pipeline-Analyse durchgeführt. |

### Nicht im Umfang enthaltene Funktionen {#out-of-scope-features}

Die Fehlerbehebung bei Pipelines erfolgt im Build- und Unit-Test-Schritt und im Code-Scan-Schritt in Full-Stack-Bereitstellungs- und Code-Qualitäts-Pipelines. Es unterstützt auch [Pipelines mit Webstufen-Konfiguration](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines).

Debuggen Sie bei anderen Pipeline-Typen und -Schritten Fehler, indem Sie die Protokolle herunterladen und überprüfen. Weitere Informationen finden [&#x200B; unter „Zugreifen auf und Herunterladen &#x200B;](/help/implementing/cloud-manager/manage-logs.md) Protokollen“.

## Fehlerbehebungsauftrag für die Replikation (Beta) {#replication-troubleshooting-job}

Debuggen Sie replikationsbezogene Probleme, z. B. blockierte Warteschlangen.

aem-devagent@adobe.com Bitte eine E-Mail an [&#128279;](mailto:aem-devagent@adobe.com) senden, um Zugriff auf das Beta-Programm zu erhalten.

