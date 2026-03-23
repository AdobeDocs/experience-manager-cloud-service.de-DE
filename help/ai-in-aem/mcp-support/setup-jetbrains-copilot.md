---
title: Einrichten von JetBrains mit GitHub Copilot und AEM MCP
description: Erfahren Sie, wie Sie GitHub Copilot in JetBrains IDEs konfigurieren, um eine Verbindung zu AEM MCP-Servern herzustellen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: c5b46aff5b4ccffa60e8bebf7341935b435079e3
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 1%

---

# Einrichten von JetBrains mit GitHub Copilot und AEM MCP {#setup-jetbrains-copilot}

Führen Sie diese Schritte aus, um GitHub Copilot in einer JetBrains-IDE (wie IntelliJ IDEA, WebStorm oder PyCharm) mit den MCP-Servern von AEM zu verbinden.

1. Öffnen Sie den GitHub-Copilot-Chat in Ihrer JetBrains-IDE, indem Sie auf **GitHub-Copilot-Chat** rechts im Editor klicken.

   ![Die JetBrains-IDE mit offenem GitHub-Copilot-Chat.](assets/jetbrains-copilot-1.png)

1. Klicken Sie auf **Einstellungen** im Bedienfeld Kopilot-Chat, um die MCP-Konfiguration zu öffnen.

   ![Das GitHub Copilot Chat-Bedienfeld mit hervorgehobenem Einstellungssymbol.](assets/jetbrains-copilot-2.png)

1. Navigieren **Einstellungen** zu **Tools > GitHub-Copilot > Model Context Protocol (MCP)** und klicken Sie auf **Konfigurieren**, um die `mcp.json` Konfigurationsdatei zu öffnen.

   ![Das Dialogfeld JetBrains-Einstellungen , das die Konfiguration des Model Context Protocol (MCP) unter GitHub Copilot anzeigt.](assets/jetbrains-copilot-3.png)

1. Fügen Sie eine oder mehrere AEM MCP-Server-URLs zur `mcp.json` hinzu. Zum Beispiel:

   ```json
   {
     "servers": {
       "aem": {
         "url": "https://mcp.adobeaemcloud.com/adobe/mcp/content"
       }
     }
   }
   ```


   ![Die Konfigurationsdatei mcp.json mit der AEM-MCP-Server-URL.](assets/jetbrains-copilot-4.png)


1. Speichern Sie die Datei. GitHub Copilot erkennt die neue Server-Konfiguration automatisch und zeigt eine **Start**-Aktion an.

   ![Die Datei „mcp.json“, die den konfigurierten AEM-Server mit erkannten Tools anzeigt.](assets/jetbrains-copilot-5.png)

1. Klicken Sie auf **Start** und melden Sie sich bei Aufforderung bei Ihrer Adobe ID an, um den Authentifizierungsvorgang abzuschließen.

1. Sie können die gefundenen Tools überprüfen und verwalten, indem Sie auf die **tools** Anzeige klicken, die im Bedienfeld Copilot Chat angezeigt wird. Optional können Sie einzelne Tools aktivieren oder deaktivieren.


   ![Das Dialogfeld „Tools konfigurieren“ mit den verfügbaren AEM-MCP-Tools.](assets/jetbrains-copilot-6.png)

1. Verwenden Sie den GitHub-Copilot-Chat, um AEM-Tools als Teil Ihrer Entwicklungs- oder Inhalts-Workflows aufzurufen.