---
title: Einrichten von Microsoft Copilot Studio mit AEM MCP
description: Erfahren Sie, wie Sie Microsoft Copilot Studio für die Verbindung mit AEM MCP-Servern konfigurieren
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: c8e96fe6-1a05-47c0-8215-0c28705e5e48
source-git-commit: f7a5c43a4a4dd6629225f3628a7c592056d6d144
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Einrichten von Microsoft Copilot Studio mit AEM MCP {#setup-microsoft-copilot-studio}

Führen Sie diese Schritte aus, um Microsoft Copilot Studio mit den MCP-Servern von AEM zu verbinden.

>[!NOTE]
>
>Die Benutzeroberfläche von Microsoft Copilot Studio kann sich ändern und ist nicht endgültig. Diese Anweisungen dienen nur zur Veranschaulichung.

1. Starten Sie **Agenten** den Fluss, um einen Agenten hinzuzufügen, der AEM MCP-Tools verwendet.

   * Erstellen Sie einen neuen Agenten.

   ![Das Bedienfeld „Agenten“ in Microsoft Copilot Studio.](assets/copilot-1.png)

1. Öffnen Sie den Bereich Tools für diesen Agenten, damit Sie registrieren können, wie er externe Funktionen aufruft.

   * Navigieren Sie zum Abschnitt „Tool“ und klicken Sie auf **Tool hinzufügen**.

   ![Das Dialogfeld „Tool hinzufügen“ in Microsoft Copilot Studio.](assets/copilot-2.png)

1. Entscheiden Sie, ob eine vorhandene Integration wiederverwendet oder ein neues MCP-unterstütztes Tool definiert werden soll.

   * Wählen Sie ein vorhandenes Tool aus oder erstellen Sie ein neues.

   ![Auswählen des Modellkontextprotokolls als Werkzeugtyp.](assets/copilot-3.png)

1. Wenn Sie ein neues MCP-Tool erstellen, fahren Sie mit dem Server-Schritt **Model Context Protocol** fort, einschließlich des Vorschaumodus, wenn er angezeigt wird.

   * Konfigurieren Sie ein neues MCP-Tool, das auf einen oder mehrere AEM MCP-Server (**)**.

   ![Hinzufügen eines Modellkontext-Protokoll-Servers im Vorschaumodus.](assets/copilot-4.png)

1. Legen Sie fest, wie dieser MCP-Endpunkt vom Agenten erreicht wird, einschließlich der Angabe, ob der Zugriff freigegeben oder dediziert ist.

   * Stellen Sie eine Verbindung her, die zwischen Agenten **freigegeben** oder **dediziert** werden kann.

   ![Das Dialogfeld zum Erstellen einer neuen Verbindung.](assets/copilot-5.png)

1. Geben **unter „Hinzufügen und**&quot; Details zum MCP-Tool an bzw. bestätigen Sie diese, damit der Agent Ihre AEM-Umgebung erreichen kann.

   ![Das Bedienfeld „Hinzufügen“ und „Konfigurieren“ für das MCP-Tool.](assets/copilot-6.png)

1. Füllen Sie die Felder im MCP-Tool-Formular aus (z. B. **URLs** und authentifizierungsbezogene Optionen).

   * Optional können Sie **automatischen Bestätigungsmodus** aktivieren oder eine **Endbenutzerbestätigung)** alle Tool-Interaktionen verlangen.

   ![Das Formular für die Konfiguration des MCP-Tools.](assets/copilot-7.png)

1. Überprüfen Sie die Verbindung zum MCP-Server, und melden Sie sich vollständig über einen Browser an, wenn Copilot Studio Sie weiterleitet.

   * Melden Sie sich bei der Weiterleitung mit Ihrer **Adobe ID** an.

   ![Testen der Verbindung mit dem AEM MCP-Server.](assets/copilot-8.png)

1. Öffnen Sie vor dem Ausführen eines Tests **Verbindungen verwalten** (oder den **Verbindungs-Manager**) und weisen Sie Ihrer Sitzung die richtige Verbindung zu.

   * Öffnen Sie beim Testen Ihres Agenten **Verbindungs-Manager** um Ihrer Sitzung eine Verbindung zuzuweisen.

   ![Das Bedienfeld „Verbindungen verwalten“ mit verfügbaren Verbindungen.](assets/copilot-9.png)

1. Führen Sie in der Testerfahrung den Agenten für Ihre AEM MCP-Verbindung aus.

   * Drücken Sie beim Testen des Agenten **Wiederholen** nachdem Sie im **Verbindungs-Manager“ eine Verbindung**.

   ![Testen des Agenten mit der AEM MCP-Verbindung.](assets/copilot-10.png)
