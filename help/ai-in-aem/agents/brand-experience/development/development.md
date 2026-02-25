---
title: Übersicht über Entwicklungsaufträge
description: Erfahren Sie, wie der Entwicklungsauftrag in AEM fehlgeschlagene Pipelines in Cloud Manager analysiert und Protokolle erstellt, um Code-Fehlerbehebungen vorzuschlagen und das Debugging zu beschleunigen.
feature: Agentic AI, AI Assistant, AI Tools, User Roles
role: User, Admin, Architect, Developer
exl-id: 2194556f-aac2-4cdd-8f7f-00c92c8c4424
source-git-commit: 71e3770a7a26b8d3144717513f3ec1c997b3b435
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 1%

---


# Übersicht über Entwicklungsaufträge {#development-job-overview}

[Als Teil des Brand Experience Agents &#x200B;](/help/ai-in-aem/agents/brand-experience/overview.md) der Entwicklungsauftrag AEM-Entwicklern und -Administratoren dabei, Code effizienter zu erstellen, zu debuggen, bereitzustellen und zu optimieren.

Der Auftrag kann Pipeline-Status abrufen und Ihnen bei der Fehlerbehebung bei fehlgeschlagenen Build-Schritten helfen, indem Fehlerbehebungen vorgeschlagen werden. Dies spart Zeit beim Debugging von AEM as a Cloud Service-Bereitstellungen in Entwicklungs-, Staging- und Produktionsumgebungen. Es werden Build-Protokolle und verwandter Code untersucht, um eine Fehlerbehebung zu empfehlen, die Sie manuell anwenden können.

>[!VIDEO](https://video.tv.adobe.com/v/3478006?quality=12&learn=on)

>[!IMPORTANT]
>
>KI-generierte Antworten können ungenau oder irreführend sein. Überprüfen Sie unbedingt die vorgeschlagenen Fehlerbehebungen und Antworten.
>
>Siehe auch [Benutzerhandbücher für die generative KI von Adobe Experience Cloud.](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html)

<!-- 
## Cloud Manager Pipeline Troubleshooting  {#cloud-manager-pipeline-troubleshooting}
-->

Um auf diesen Auftrag zuzugreifen, lesen Sie bitte die [Versionshinweise](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs), um Anweisungen zur Registrierung für das Beta-Programm zu erhalten und sicherzustellen, dass Sie Ihr Interesse an dem Entwicklungsauftrag bekunden. Sie können auch auftragsspezifisches Feedback für Entwicklungsaufgaben per E-Mail an [aem-devagent@adobe.com.](mailto:aem-devagent@adobe.com) senden.

[In einem Tutorial erfahren &#x200B;](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/ai/development-agent-troubleshoot-ci-cd-pipeline), wie Sie mit dem Entwicklungsagenten Pipeline-Fehler beheben können.

## Zugriff auf den Entwicklungsauftrag über Cloud Manager {#how-to-access-the-job}

Der Zugriff auf den Entwicklungsauftrag erfolgt über den KI-Assistenten in Benutzeroberflächen wie Cloud Manager oder Experience Hub.

1. Klicken Sie zunächst auf [Adobe Experience Cloud](https://experience.adobe.com/#/@foundationinternal/home), um die Startseite zu öffnen.

   ![Adobe Experience Cloud-Startseite](/help/implementing/cloud-manager/assets/experience-cloud-experiencemanager.png)

1. Klicken Sie in der linken Leiste unter **Services** auf **Cloud Manager**.

   ![Die Dropdown-Liste mit der Inhaltsautorenvorgabe ist ausgewählt](/help/implementing/cloud-manager/assets/experience-hub-role-selection.png)

   >[!IMPORTANT]
   >
   >Die angezeigten Widgets, Tools und Artefakte hängen von der Benutzerrolle, den Berechtigungen und dem AEM-Bereitstellungstyp (AEM as a Cloud Service oder Managed Services 6.5/6.5 LTS) ab.

1. Klicken Sie in der linken Leiste unter **Programm** auf **![Übersichtssymbol](/help/implementing/cloud-manager/configuring-pipelines/assets/overview.svg) Übersicht**.

1. Klicken Sie auf der **Programmübersicht** auf der Karte **Pipelines** auf eine Pipeline.

   ![Ausgewählte Pipeline](/help/ai-in-aem/agents/brand-experience/development/assets/dev-agent-pipeline-select.png)

1. Beachten Sie auf **Seite Build- und** die fehlgeschlagene Pipeline.

   ![Pipeline-Fehler, wie auf der Seite Build- und Code-Überprüfung angezeigt](/help/ai-in-aem/agents/brand-experience/development/assets/dev-agent-pipeline-failure.png)

1. Klicken Sie in der rechten oberen Ecke der Benutzeroberfläche von AEM (entweder auf den Cloud Manager-Seiten oder in der Autoreninstanz der AEM-Umgebungen) auf das Symbol **KI-**).

   ![Symbol „KI-Assistent“ in der Symbolleiste](/help/implementing/cloud-manager/assets/ai-assistant-icon.png)

   Siehe auch [KI-Assistent in AEM](/help/implementing/cloud-manager/ai-assistant-in-aem.md).

1. Geben Sie im Textfeld **KI** Assistent“ unten Ihre Frage oder Eingabeaufforderung ein und drücken Sie dann die `Enter` oder klicken Sie auf ![Senden-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Send_18_N.svg).

   Beispiel:
   *Analysieren Sie im Programm „eda-org-01-no-access“ den Fehler bei der Pipeline „no-access“ und beheben Sie die Fehler.*

   Die Eingabeaufforderung führt zur folgenden Antwort.

   ![KI-Assistenten-Eingabeaufforderung und resultierende Antwort](/help/ai-in-aem/agents/brand-experience/development/assets/dev-agent-prompt-response.png)


## Berechtigungen {#permissions}

Für den Entwicklungsauftrag ist entweder die Rolle Cloud Manager - Entwickler oder die Rolle Cloud Manager - Programm-Manager erforderlich.

## Eingabeaufforderungen im Beispiel {#sample-prompts}

| Prompt | Ergebnis |
| --- | --- |
| *Fehlerbehebung bei fehlgeschlagener Pipeline* | Führt eine Analyse der Gründe für den Pipeline-Fehler durch. Wenn nicht klar ist, auf welche Pipeline verwiesen wird, werden dem Benutzer zusätzliche Fragen gestellt. |
| *Liste meiner fehlgeschlagenen Pipelines für das Hauptprogramm des Programms.* | Auch wenn die Ergebnisse variieren können, gibt diese Eingabeaufforderung eine Tabelle mit fehlgeschlagenen Pipelines mit einem Folgenachweis zurück, der auf eine bestimmte zu analysierende Pipeline verweist. |
| *Analysieren Sie meine fehlgeschlagene Pipeline mit dem Namen „Entwicklungs-Pipeline“* | Diese Eingabeaufforderung führt zu einer Analyse der fehlgeschlagenen Pipeline mit Vorschlägen zur Korrektur. Bei mehreren Fehlern werden dem Benutzer zusätzliche Fragen gestellt. |
| *Fehlerbehebung bei der Pipeline-Ausführung 1234567* | Durch Angabe einer exakten Pipeline-Ausführungs-ID wird eine Pipeline-Analyse durchgeführt. |

## Nicht im Umfang enthaltene Funktionen {#out-of-scope-features}

Die Fehlerbehebung bei Pipelines erfolgt im Build-Schritt der Full-Stack-Pipeline. Debuggen Sie bei anderen Pipeline-Typen und -Schritten Fehler, indem Sie die Protokolle herunterladen und überprüfen.

Weitere Informationen finden [&#x200B; unter „Zugreifen auf und Herunterladen &#x200B;](/help/implementing/cloud-manager/manage-logs.md) Protokollen“.
