---
title: Übersicht über den Entwicklungsagenten
description: Erfahren Sie, wie der Entwicklungsagent in AEM fehlgeschlagene Pipelines in Cloud Manager analysiert und Protokolle erstellt, um Code-Fehlerbehebungen vorzuschlagen und das Debugging zu beschleunigen.
feature: Agentic AI, AI Assistant, AI Tools, User Roles
role: User, Admin, Architect, Developer
source-git-commit: b206c73853e2f81a1bd5a15bb1e0d5d7658f70a5
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 1%

---


# Übersicht über den Entwicklungsagenten {#development-agent-overview}

Der Entwicklungs-Agent unterstützt AEM-Entwickler und -Administratoren dabei, Code effizienter zu erstellen, zu debuggen, bereitzustellen und zu optimieren.

Derzeit kann der Agent Pipeline-Status abrufen und Ihnen bei der Fehlerbehebung bei fehlgeschlagenen Build-Schritten helfen, indem er Fehlerbehebungen vorschlägt und so Zeit beim Debugging von AEM as a Cloud Service-Bereitstellungen in Entwicklungs-, Staging- und Produktionsumgebungen spart. Es werden Build-Protokolle und verwandter Code untersucht, um eine Fehlerbehebung zu empfehlen, die Sie manuell anwenden können.

>[!VIDEO](https://video.tv.adobe.com/v/3478016?captions=ger&quality=12&learn=on)

>[!IMPORTANT]
>
>KI-generierte Antworten können ungenau oder irreführend sein. Überprüfen Sie unbedingt die vorgeschlagenen Fehlerbehebungen und Antworten.
>
>Siehe auch [Benutzerhandbücher für die generative KI von Adobe Experience Cloud](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

<!-- 
## Cloud Manager Pipeline Troubleshooting  {#cloud-manager-pipeline-troubleshooting}
-->

## Zugriff auf den Entwicklungsagenten über Cloud Manager {#how-to-access-the-agent}

Der Zugriff auf den Entwicklungsagenten erfolgt über den KI-Assistenten, der sich in den Benutzeroberflächen, einschließlich Cloud Manager oder Experience Hub, befindet.

**So greifen Sie über Cloud Manager auf den Entwicklungsagenten zu:**

1. Klicken Sie zunächst auf [Adobe Experience Cloud](https://experience.adobe.com/#/@foundationinternal/home), um die Startseite zu öffnen.

   ![Adobe Experience Cloud-Startseite](/help/implementing/cloud-manager/assets/experience-cloud-experiencemanager.png)

1. Klicken Sie in der linken Leiste unter **Services** auf **Cloud Manager**.

   ![Die Dropdown-Liste mit der Inhaltsautorenvorgabe ist ausgewählt](/help/implementing/cloud-manager/assets/experience-hub-role-selection.png)

   >[!IMPORTANT]
   >
   >Die angezeigten Widgets, Tools und Artefakte hängen von der Benutzerrolle, den Berechtigungen und dem AEM-Bereitstellungstyp (AEM as a Cloud Service oder Managed Services 6.5/6.5 LTS) ab.

1. Klicken Sie in der linken Leiste unter **Programm** auf **![Übersichtssymbol](/help/implementing/cloud-manager/configuring-pipelines/assets/overview.svg) Übersicht**.

1. Klicken Sie auf der **Programmübersicht** auf der Karte **Pipelines** auf eine Pipeline.

   ![Ausgewählte Pipeline](/help/ai-in-aem/agents/development/assets/dev-agent-pipeline-select.png)

1. Beachten Sie auf **Seite Build- und** die fehlgeschlagene Pipeline.

   ![Pipeline-Fehler, wie auf der Seite Build- und Code-Überprüfung angezeigt](/help/ai-in-aem/agents/development/assets/dev-agent-pipeline-failure.png)

1. Klicken Sie in der rechten oberen Ecke der Benutzeroberfläche von AEM (entweder auf den Cloud Manager-Seiten oder in der Autoreninstanz der AEM-Umgebungen) auf das Symbol **KI-**).

   ![Symbol „KI-Assistent“ in der Symbolleiste](/help/implementing/cloud-manager/assets/ai-assistant-icon.png)

   Siehe auch [KI-Assistent in AEM](/help/implementing/cloud-manager/ai-assistant-in-aem.md).

1. Geben Sie im Textfeld **KI** Assistent“ unten Ihre Frage oder Eingabeaufforderung ein und drücken Sie dann die `Enter` oder klicken Sie auf ![Senden-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Send_18_N.svg).

   Beispiel:
   *Analysieren Sie im Programm „eda-org-01-no-access“ den Fehler bei der Pipeline „no-access“ und beheben Sie die Fehler.*

   Die Eingabeaufforderung führt zur folgenden Antwort.

   ![KI-Assistenten-Eingabeaufforderung und resultierende Antwort](/help/ai-in-aem/agents/development/assets/dev-agent-prompt-response.png)


## Berechtigungen {#permissions}

Für die Fehlerbehebung bei der Pipeline des Entwicklungsagenten ist entweder die Rolle Cloud Manager - Entwickler oder die Rolle Cloud Manager - Programm-Manager erforderlich.

## Eingabeaufforderungen im Beispiel {#sample-prompts}

| Prompt | Ergebnis |
| --- | --- |
| *Liste meiner fehlgeschlagenen Pipelines für das Hauptprogramm des Programms.* | Auch wenn die Ergebnisse variieren können, gibt diese Eingabeaufforderung eine Tabelle mit fehlgeschlagenen Pipelines mit einem Folgenachweis zurück, der auf eine bestimmte zu analysierende Pipeline verweist. |
| *Analysieren Sie meine fehlgeschlagene Pipeline mit dem Namen „Entwicklungs-Pipeline“* | Diese Eingabeaufforderung führt zu einer Analyse der fehlgeschlagenen Pipeline mit Vorschlägen zur Korrektur. |

## Nicht im Umfang enthaltene Funktionen {#out-of-scope-features}

Die Fehlerbehebung bei Pipelines erfolgt im Build-Schritt der Full-Stack-Pipeline. Debuggen Sie bei anderen Pipeline-Typen und -Schritten Fehler, indem Sie die Protokolle herunterladen und überprüfen.

Siehe [Zugreifen auf und Herunterladen von Protokollen](/help/implementing/cloud-manager/manage-logs.md).

Die Fehlerbehebung bei Pipelines wird für Programme, die BYOGIT verwenden (bring Your Own Git), nicht unterstützt.
