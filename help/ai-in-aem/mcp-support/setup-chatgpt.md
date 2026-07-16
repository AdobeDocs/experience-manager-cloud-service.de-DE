---
title: Einrichten von OpenAI ChatGPT mit AEM MCP
description: Erfahren Sie, wie Sie OpenAI ChatGPT konfigurieren, um eine Verbindung zu AEM MCP-Servern herzustellen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 1f116225-168b-483c-9df6-c752a573b57b
source-git-commit: e5eceb1e540a85aab03b7b856af36276291745f6
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---

# Einrichten von OpenAI ChatGPT mit AEM MCP {#setup-chatgpt}

Dieser Artikel behandelt zwei verschiedene Möglichkeiten, OpenAI ChatGPT mit AEM zu verwenden:

- Konfigurieren Sie manuell einen oder mehrere MCP-Server von AEM in ChatGPT (die unter &quot;[ von MCP mit AEM as a Cloud Service - MCP-Server](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md#mcp-servers) beschriebenen Server).
- Installieren Sie das Adobe Experience Manager-Plug-in über den ChatGPT-Plug-in-Marketplace. Es weist derzeit eine Funktionsparität mit Content MCP Server auf und stellt eine wachsende Untergruppe von Tools zur Verfügung, die in AEM MCP-Servern verfügbar sind.

## Manuelles Konfigurieren der AEM-MCP-Server in ChatGPT {#manual-configure-aems-mcp-servers-in-chatgpt}

In diesem Abschnitt wird der Ansatz **manuelle Konfiguration** beschrieben, bei dem Sie einen oder mehrere MCP-Server von AEM als benutzerdefinierte Programme oder Connectoren zu ChatGPT hinzufügen.

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

1. Aktivieren Sie **Entwicklermodus** in **Apps und Connectoren**, damit Sie ein benutzerdefiniertes Plug-in hinzufügen und konfigurieren können.

   ![Aktivieren des Entwicklermodus im Abschnitt „Apps und Connectoren“.](assets/chatgpt-3.png)

1. Starten Sie **Neue App erstellen** (oder das entsprechende Steuerelement), um einen App-Eintrag für Ihren AEM MCP-Server hinzuzufügen.

   ![Das Dialogfeld zum Erstellen einer neuen App in ChatGPT.](assets/chatgpt-4.png)

1. Füllen Sie das Formular **Neue App** aus, z. B. benennen Sie die App und geben Sie Ihre AEM MCP-Server-URL und alle anderen erforderlichen Felder ein. **Speichern**.

   ![Das neue App-Konfigurationsformular in ChatGPT.](assets/chatgpt-5.png)

1. Bestätigen Sie, dass **AEM Content MCP Service** (oder Ihre konfigurierte App) in &quot;**und Connectoren“ angezeigt wird** damit ChatGPT ihn verwenden kann.

   ![Der AEM Content MCP Service wird in „Apps und Connectoren“ aufgeführt.](assets/chatgpt-6.png)

1. Schreiben Sie in einem Chat eine Eingabeaufforderung, die ChatGPT anweist, die konfigurierten **AEM-Tools zu verwenden** (z. B. um Autoreninhalte oder Sites abzufragen).

   ![ChatGPT wird aufgefordert, den AEM Content MCP Service zu verwenden.](assets/chatgpt-7.png)

## Installieren des Adobe Experience Manager-Plug-ins (ChatGPT-Plug-in-Marketplace) {#install-adobe-experience-manager-plugin}

In diesem Abschnitt wird das **installierbare Plug-in** aus dem ChatGPT-Plug-in-Marktplatz beschrieben (im Gegensatz zum Hinzufügen einer benutzerdefinierten MCP-Server-URL). Es enthält eine Teilmenge der Tools, die in den MCP-Servern von AEM verfügbar sind.

>[!NOTE]
>
>Die OpenAI ChatGPT-Benutzeroberfläche kann sich ändern und ist nicht endgültig. Diese Anweisungen dienen nur zur Veranschaulichung.

Sie können das Adobe Experience Manager-Plug-in auf zwei Arten erreichen. Verwenden Sie den bequemeren Schlüssel und fahren Sie dann mit den folgenden Schritten zur Anmeldung fort.

**Option 1: Öffnen Sie die Plug-in-Seite direkt**

Wechseln Sie zu [https://chatgpt.com/plugins/plugin_asdk_app_6a35d3c1258081919c084a1fd22cd02d](https://chatgpt.com/plugins/plugin_asdk_app_6a35d3c1258081919c084a1fd22cd02d) und wählen Sie **Plug-in installieren**.

![Die Adobe Experience Manager-Plug-in-Seite mit der Schaltfläche „Plug-in installieren“.](assets/chatgpt-plugin-install.png)

**Option 2: Finden Sie das Plug-in im Marktplatz**

1. Wählen **Einstellungen** die Option **Plug-ins** und wählen Sie dann unten in der Liste **Plug-ins durchsuchen**.

   ![Die Seite „Plugins“ in den ChatGPT-Einstellungen mit den Browse-Plugins.](assets/chatgpt-plugin-1.png)

1. Suchen Sie nach **Adobe Experience Manager** und wählen Sie es aus.

   ![Suchen nach dem Adobe Experience Manager-Plug-in im Plug-in-Marketplace.](assets/chatgpt-plugin-2.png)

**Anmelden und bestätigen**

Nachdem Sie das Plug-in mit einer der oben genannten Optionen gefunden oder installiert haben, schließen Sie die Verbindung ab:

1. Wählen Sie **Mit Adobe Experience Manager anmelden** und melden Sie sich bei AEM an, wenn Sie umgeleitet werden.

   ![Der Dialog Adobe Experience Manager zu ChatGPT hinzufügen mit Anmelden bei Adobe Experience Manager.](assets/chatgpt-plugin-3.png)

1. Bestätigen Sie, dass das grüne Banner anzeigt, dass Adobe Experience Manager jetzt verbunden ist.

   ![Das grüne Banner, das bestätigt, dass das Adobe Experience Manager-Plug-in verbunden ist.](assets/chatgpt-plugin-4.png)
