---
title: Anthropic Claude mit AEM MCP einrichten
description: Erfahren Sie, wie Sie Anthropic Claude für die Verbindung mit AEM MCP-Servern konfigurieren
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 2b90b2b2-cdd0-4f1e-890f-2f58f578face
source-git-commit: 07a7aa5f02d7bfa992df825f3b8a19e18d569d5b
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# Anthropic Claude mit AEM MCP einrichten {#setup-claude}

Dieser Artikel behandelt zwei verschiedene Arten, um Anthropic Claude mit AEM zu verwenden:

- Manuelles Konfigurieren eines oder mehrerer MCP-Server von AEM in Claude (die unter &quot;[&#x200B; von MCP mit AEM as a Cloud Service - MCP-Server](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md#mcp-servers) beschriebenen Server).
- Installieren Sie den Adobe Experience Manager-Connector vom Anthropic-Connector-Marketplace. Es weist derzeit eine Funktionsparität mit Content MCP Server auf und stellt eine wachsende Untergruppe von Tools zur Verfügung, die in AEM MCP-Servern verfügbar sind.



## Manuelles Konfigurieren der AEM-MCP-Server in Claude {#manual-configure-aems-mcp-servers-in-claude}

In diesem Abschnitt wird der **manuelle Konfiguration**-Ansatz beschrieben, bei dem Sie einen oder mehrere MCP-Server von AEM zu Claude als benutzerdefinierte Connectoren hinzufügen.

>[!NOTE]
>
>Die Claude-Benutzeroberfläche kann sich ändern und ist nicht endgültig. Diese Anweisungen dienen nur zur Veranschaulichung.

1. Öffnen Sie das Kontomenü in der linken unteren Ecke der Claude-Web-App und wählen Sie **Einstellungen**, um den Bereich Einstellungen zu öffnen.

   ![Konto-Menü in Claude mit ausgewählten Einstellungen.](assets/claude-1.png)

1. Wählen Sie in der Seitenleiste Einstellungen **Connectoren** aus. Wählen Sie auf der Seite „Connectoren **die Option „Benutzerdefinierten Connector hinzufügen** aus, um einen benutzerdefinierten MCP-Endpunkt zu registrieren.

   ![Seite „Connectoren“ in den Einstellungen mit „Benutzerdefinierten Connector hinzufügen“.](assets/claude-2.png)

1. Geben **im Dialogfeld Benutzerdefinierten Connector hinzufügen** einen Anzeigenamen (z. B. **AEM Content MCP Service**) und Ihre MCP-Server-URL ein und wählen Sie dann **Hinzufügen** aus. Verwenden Sie **Erweiterte Einstellungen** nur, wenn Ihre Bereitstellung zusätzliche Optionen erfordert.

   ![Dialogfeld „Benutzerdefinierten Connector hinzufügen“ mit Namen und MCP-URL.](assets/claude-3.png)

1. Suchen Sie in der Liste „Connectoren“ Ihren benutzerdefinierten Connector-Eintrag (er weist eine **CUSTOM**-Kennzeichnung auf) und wählen Sie **Verbinden** aus, um sich anzumelden und den Connector mit Ihrem Claude-Konto zu verknüpfen.

   ![Connectoren-Liste mit für AEM Content MCP Service ausgewähltem „Verbinden“](assets/claude-4.png)

1. Wenn der Connector in der Liste mit seiner URL angezeigt wird, wählen Sie **Konfigurieren** neben **AEM Content MCP Service** aus, um die Connector-Details zu öffnen und mit der Einrichtung fortzufahren.

   ![Connectoren-Liste mit Für AEM Content MCP Service ausgewähltem Konfigurieren.](assets/claude-5.png)

1. Überprüfen Sie auf der Seite **Toolberechtigungen** die Standardeinstellung (z. B. **Genehmigung erforderlich**) und legen Sie dann jedes AEM-Tool **Immer zulassen**, **Nach Berechtigung fragen** oder **Niemals zulassen** gemäß Ihrer Sicherheitsrichtlinie fest.

   ![Tool-Berechtigungen für AEM Content MCP Service.](assets/claude-6.png)

1. Öffnet ein Gespräch. Wählen Sie das Tools- und Modellmenü (Schiebereglersymbol) links neben dem Nachrichtenfeld aus, aktivieren Sie **AEM Content MCP Service** unter Connectoren und geben Sie dann Ihre Eingabeaufforderung ein, damit Claude die MCP-Tools für diesen Chat verwenden kann.

   ![Chat Composer mit aktiviertem AEM Content MCP Service im Menü „Tools“.](assets/claude-7.png)

## Installieren des Adobe Experience Manager-Connectors (Anthropic-Connector-Marketplace) {#install-adobe-experience-manager-connector}

In diesem Abschnitt wird der **installierbare Connector** vom Anthropic-Connector-Marketplace beschrieben (im Gegensatz zum Hinzufügen einer benutzerdefinierten Connector-URL). Es enthält eine Teilmenge der Tools, die in den MCP-Servern von AEM verfügbar sind.

Um den **Adobe Experience Manager-Connector** zu installieren, öffnen Sie **Einstellungen** > **Connectoren** in Claude. Sie können die Seite Connectoren auch direkt unter [https://claude.ai/settings/connectors](https://claude.ai/settings/connectors) öffnen. Der Connector registriert einen MCP-Server, der einen wachsenden Satz von Tools für AEM-Workflows bereitstellt.

![Installieren des Adobe Experience Manager Claude-Connectors über das Connector-Verzeichnis.](assets/claude-connector.png)