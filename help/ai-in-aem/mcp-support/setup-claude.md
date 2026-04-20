---
title: Anthropic Claude mit AEM MCP einrichten
description: Erfahren Sie, wie Sie Anthropic Claude für die Verbindung mit AEM MCP-Servern konfigurieren
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 2b90b2b2-cdd0-4f1e-890f-2f58f578face
source-git-commit: fede808fcd8b082a71273bf9ffceb48b5332f45d
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Anthropic Claude mit AEM MCP einrichten {#setup-claude}

Führen Sie diese Schritte aus, um Anthropic Claude mit den MCP-Servern von AEM zu verbinden.

* Registrieren Sie in Claudes MCP-Konfiguration eine oder mehrere AEM MCP-Server-URLs.
* Schließen Sie den Adobe-Anmeldeablauf ab.
* Aktivieren Sie optional die automatische Bestätigung für bestimmte Tools im Konfigurationsbereich. Diese Option wird für Suchvorgänge oder schreibgeschützte Vorgänge empfohlen.
* Stellen Sie sicher, dass der MCP-Server ausgewählt ist, bevor Sie mit der Konversation beginnen.
* Bitten Sie Claude, AEM-bezogene Aufgaben auszuführen. Claude wählt die vom MCP-Server bereitgestellten AEM-Tools anhand Ihrer Eingabeaufforderung aus.

Gehen Sie wie folgt vor, um Claude für AEM MCP zu konfigurieren:

>[!NOTE]
>
>Die Claude-Benutzeroberfläche kann sich ändern und ist nicht endgültig. Diese Anweisungen dienen nur zur Veranschaulichung.

1. Öffnen Sie das Kontomenü in der linken unteren Ecke der Claude-Web-App und wählen Sie **Einstellungen**, um den Bereich Einstellungen zu öffnen.

   ![Konto-Menü in Claude mit ausgewählten Einstellungen.](assets/claude-1.png)

1. Wählen Sie in der Seitenleiste Einstellungen **Connectoren** aus. Wählen Sie auf der Seite „Connectoren **die Option „Benutzerdefinierten Connector hinzufügen** aus, um einen benutzerdefinierten MCP-Endpunkt zu registrieren.

   ![Seite „Connectoren“ in den Einstellungen mit „Benutzerdefinierten Connector hinzufügen“.](assets/claude-2.png)

1. Geben **im Dialogfeld Benutzerdefinierten Connector hinzufügen** einen Anzeigenamen (z. B. **AEM Content MCP Service**) und Ihre AEM MCP-Server-URL ein und wählen Sie dann **Hinzufügen**. Verwenden Sie **Erweiterte Einstellungen** nur, wenn Ihre Bereitstellung zusätzliche Optionen erfordert.

   ![Dialogfeld „Benutzerdefinierten Connector hinzufügen“ mit Namen und MCP-URL.](assets/claude-3.png)

1. Suchen Sie in der Liste „Connectoren“ Ihren benutzerdefinierten Connector-Eintrag (er weist eine **CUSTOM**-Kennzeichnung auf) und wählen Sie **Verbinden** aus, um sich anzumelden und den Connector mit Ihrem Claude-Konto zu verknüpfen.

   ![Connectoren-Liste mit für AEM Content MCP Service ausgewähltem „Verbinden“](assets/claude-4.png)

1. Wenn der Connector in der Liste mit seiner URL angezeigt wird, wählen Sie **Konfigurieren** neben **AEM Content MCP Service** aus, um die Connector-Details zu öffnen und mit der Einrichtung fortzufahren.

   ![Connectoren-Liste mit Für AEM Content MCP Service ausgewähltem Konfigurieren.](assets/claude-5.png)

1. Überprüfen Sie auf der Seite **Toolberechtigungen** die Standardeinstellung (z. B. **Genehmigung erforderlich**) und legen Sie dann jedes AEM-Tool **Immer zulassen**, **Nach Berechtigung fragen** oder **Niemals zulassen** gemäß Ihrer Sicherheitsrichtlinie fest.

   ![Tool-Berechtigungen für AEM Content MCP Service.](assets/claude-6.png)

1. Öffnet ein Gespräch. Wählen Sie das Tools- und Modellmenü (Schiebereglersymbol) links neben dem Nachrichtenfeld aus, aktivieren Sie **AEM Content MCP Service** unter Connectoren und geben Sie dann Ihre Eingabeaufforderung ein, damit Claude die MCP-Tools für diesen Chat verwenden kann.

   ![Chat Composer mit aktiviertem AEM Content MCP Service im Menü „Tools“.](assets/claude-7.png)

## Adobe Experience Manager Claude-Connector {#aem-claude-connector}

Um den **Adobe Experience Manager Claude-Connector zu installieren** öffnen Sie **Einstellungen** > **Connectoren** in Claude. Sie können die Seite Connectoren auch direkt unter [https://claude.ai/settings/connectors](https://claude.ai/settings/connectors) öffnen. Der Connector registriert einen MCP-Server, der einen wachsenden Satz von Tools für AEM-Workflows bereitstellt.

![Installieren des Adobe Experience Manager Claude-Connectors über das Connector-Verzeichnis.](assets/claude-connector.png)