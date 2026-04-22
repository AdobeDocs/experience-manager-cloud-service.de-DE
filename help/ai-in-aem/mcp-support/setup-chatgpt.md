---
title: Einrichten von OpenAI ChatGPT mit AEM MCP
description: Erfahren Sie, wie Sie OpenAI ChatGPT konfigurieren, um eine Verbindung zu AEM MCP-Servern herzustellen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 1f116225-168b-483c-9df6-c752a573b57b
source-git-commit: f7a5c43a4a4dd6629225f3628a7c592056d6d144
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Einrichten von OpenAI ChatGPT mit AEM MCP {#setup-chatgpt}

Führen Sie diese Schritte aus, um OpenAI ChatGPT mit den MCP-Servern von AEM zu verbinden.

* Fügen Sie eine oder mehrere AEM MCP-Server-URLs in dem Bereich hinzu, in dem MCP-Verbindungen oder -Tools konfiguriert sind.
* Erstellen Sie einen Trigger für die Verbindung und melden Sie sich bei der Weiterleitung mit Ihrer Adobe ID an.
* Verweisen Sie in einem Chat auf die konfigurierten AEM-Tools in Ihren Eingabeaufforderungen, z. B.:

  ```
  "Using the configured AEM MCP tools, list all sites in the author environment."
  ```

>[!NOTE]
>
>Die OpenAI ChatGPT-Benutzeroberfläche kann sich ändern und ist nicht endgültig. Diese Anweisungen dienen nur zur Veranschaulichung.

1. Öffnen Sie **Einstellungen**, um den Bereich zu erreichen, in dem MCP-Verbindungen oder -Tools konfiguriert sind.

   ![Der Dialog ChatGPT-Einstellungen.](assets/chatgpt-1.png)

1. Öffnen Sie **Programme und Connectoren** die Option **Erweiterte Einstellungen**, um Connector- und MCP-bezogene Optionen zu verwalten.

   ![Das Bedienfeld Erweiterte Einstellungen für Apps und Connectoren in ChatGPT.](assets/chatgpt-2.png)

1. Aktivieren Sie **Entwicklermodus** in **Apps und Connectoren**, damit Sie benutzerdefinierte Apps oder Connectoren hinzufügen und konfigurieren können.

   ![Aktivieren des Entwicklermodus im Abschnitt „Apps und Connectoren“.](assets/chatgpt-3.png)

1. Starten Sie **Neue App erstellen** (oder das entsprechende Steuerelement), um einen App-Eintrag für Ihren AEM MCP-Server hinzuzufügen.

   ![Das Dialogfeld zum Erstellen einer neuen App in ChatGPT.](assets/chatgpt-4.png)

1. Füllen Sie das Formular **Neue App** aus, z. B. benennen Sie die App und geben Sie Ihre AEM MCP-Server-URL und alle anderen erforderlichen Felder ein. **Speichern**.

   ![Das neue App-Konfigurationsformular in ChatGPT.](assets/chatgpt-5.png)

1. Bestätigen Sie, dass **AEM Content MCP Service** (oder Ihre konfigurierte App) in &quot;**und Connectoren“ angezeigt wird** damit ChatGPT ihn verwenden kann.

   ![Der AEM Content MCP Service wird in „Apps und Connectoren“ aufgeführt.](assets/chatgpt-6.png)

1. Schreiben Sie in einem Chat eine Eingabeaufforderung, die ChatGPT anweist, die konfigurierten **AEM-Tools zu verwenden** (z. B. um Autoreninhalte oder Sites abzufragen).

   ![ChatGPT wird aufgefordert, den AEM Content MCP Service zu verwenden.](assets/chatgpt-7.png)
