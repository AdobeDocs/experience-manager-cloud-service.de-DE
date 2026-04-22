---
title: Einrichten des Cursors mit AEM MCP
description: Erfahren Sie, wie Sie Cursor konfigurieren, um eine Verbindung zu AEM MCP-Servern herzustellen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: f0897898-cb1d-4af6-859c-f5a1c0ec6168
source-git-commit: f7a5c43a4a4dd6629225f3628a7c592056d6d144
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Einrichten des Cursors mit AEM MCP {#setup-cursor}

Führen Sie diese Schritte aus, um den Cursor mit den MCP-Servern von AEM zu verbinden.

* Erstellen Sie in den MCP-Einstellungen des Cursors einen neuen MCP-Server-Eintrag mit einer oder mehreren AEM MCP-URLs.
* Bei Aufforderung mit Ihrer Adobe ID authentifizieren.
* Optional können Sie einzelne Werkzeuge aktivieren oder deaktivieren, indem Sie auf die Werkzeugnamen klicken. Alle Tools sind standardmäßig aktiviert.
* Verwenden Sie den Editor oder Chat des Cursors, um AEM-Tools als Teil von Entwicklungs- oder Inhalts-Workflows aufzurufen.

>[!NOTE]
>
>Die Benutzeroberfläche des Cursors kann sich ändern und ist nicht endgültig. Diese Anweisungen dienen nur zur Veranschaulichung.

1. Öffnen Sie **Cursor-Einstellungen**, um zu konfigurieren, wie der Cursor eine Verbindung zu MCP-Servern herstellt.

   ![Der Dialog Cursor-Einstellungen.](assets/cursor-1.png)

1. Öffnen Sie **Tools und MCP** und wählen Sie dann **Benutzerdefiniertes MCP hinzufügen** aus, um einen benutzerdefinierten MCP-Server-Eintrag zu starten.

   ![Das Bedienfeld Tools und MCP mit der Option, einen benutzerdefinierten MCP-Server hinzuzufügen.](assets/cursor-2.png)

1. Geben Sie auf dem benutzerdefinierten MCP-Server-Formular **Name** Ihren AEM-MCP-**URL** (oder URLs) und alle anderen erforderlichen Felder ein und klicken Sie dann **Speichern**.

   ![Das Formular für benutzerdefinierte MCP-Server-Einstellungen in Cursor.](assets/cursor-3.png)

1. Wenn das Verbindungsdialogfeld angezeigt wird, schließen Sie die Anmeldung ab, indem Sie auf **Verbinden** klicken, sodass der neue MCP-Server autorisiert ist.

   ![Das Verbindungsdialogfeld für den neuen MCP-Server in Cursor.](assets/cursor-4.png)

1. Schreiben Sie **Chat** oder im Editor Eingabeaufforderungen, die **AEM-Tools aufrufen** damit der konfigurierte MCP-Server an Ihrem Workflow teilnimmt.

   ![Cursor wird aufgefordert, den neuen AEM MCP-Service zu verwenden.](assets/cursor-5.png)
