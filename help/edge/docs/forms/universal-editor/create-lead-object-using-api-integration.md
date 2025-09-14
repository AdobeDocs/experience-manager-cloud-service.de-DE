---
title: Erstellen eines Salesforce-Lead-Objekts mithilfe der API-Integration
description: Erfahren Sie, wie Sie ein Salesforce Lead-Objekt mithilfe der API-Integration erstellen.
feature: Adaptive Forms, Core Components, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
keywords: Integrieren der API im Regeleditor, Aufrufen von Service-Verbesserungen
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 11%

---

# Erstellen eines Salesforce-Lead-Objekts mithilfe der API-Integration

In diesem Anwendungsbeispiel wird erläutert, wie Sie einen Lead in Salesforce mithilfe der API-Integration erstellen. Am Ende des Prozesses können Sie:

Richten Sie eine [Connected App in Salesforce&quot; ein](https://help.salesforce.com/s/articleView?id=platform.ev_relay_create_connected_app.htm&type=5) um einen sicheren API-Zugriff zu ermöglichen.

Konfigurieren Sie CORS (Cross-Origin Resource Sharing), damit in einem Webbrowser ausgeführter Code (z. B. JavaScript) mit Salesforce von einem bestimmten Ursprung kommunizieren kann, und fügen Sie der Zulassungsliste den Ursprung hinzu, wie unten dargestellt.

![CORS](assets/salesforce-cors.png)

## Einstellungen für verbundene Anwendungen

Die folgenden Einstellungen werden in der verbundenen App verwendet. Sie können die OAuth-Bereiche je nach Ihren Anforderungen zuweisen.
![connected-app-settings](assets/salesforce-connected-app-settings.png)

## API-Integration erstellen

| Name | Wert |
|--------------------------------|------------------|
| API-URL | https://`<your-domain>`d.my.salesforce.com/services/data/v32.0/sobjects/Lead |
| Client-ID | Spezifisch für Ihre verbundene App |
| Client-Geheimnis | Spezifisch für Ihre verbundene App |
| OAuth-URL | https://login.salesforce.com/services/oauth2/authorize |
| URL des Zugriffs-Tokens | https://`<your-domain>`/services/oauth2/token |
| URL für aktualisiertes Token | https://`<your-domain>`/services/oauth2/token |
| Autorisierungsumfang | api chatter_api full id openid refresh_token visualforce web |
| Autorisierungs-Header | Autorisierungs-Träger |

![API-Integration](assets/salesforce-api-integration-create-lead.png)

## Eingabe- und Ausgabeparameter

Definieren Sie die Eingabeparameter für den API-Aufruf und ordnen Sie die Ausgabeparameter mithilfe der folgenden JSON zu

```json
{
    "id": "00QKY000001LyJR2A0",
    "success": true
}
```

![Input-Output](assets/create-lead-api-integration-input-output.png)

## Formular erstellen

Erstellen Sie ein einfaches adaptives Formular mit dem universellen Editor, um die Details zum Lead-Objekt zu erfassen, wie unten gezeigt
![lead-object-form](assets/create-lead.png)

Verarbeiten Sie das Klickereignis im Kontrollkästchen Lead erstellen mit dem Regeleditor. Ordnen Sie die Eingabeparameter den Werten der entsprechenden Formularobjekte zu, wie unten dargestellt. Zeigt die ID des neu erstellten Lead-Objekts im `leadid` TextField-Objekt an
![Regel-Editor](assets/create-leade-rule-editor.png)

## Testen der Integration

- Vorschau des Formulars
- Eingeben aussagekräftiger Werte
- Aktivieren Sie das Kontrollkästchen `Create Lead` , um den API-Aufruf Trigger
- Die Lead-ID des neu erstellten Lead-Objekts wird im `Lead ID` Textfeld angezeigt.