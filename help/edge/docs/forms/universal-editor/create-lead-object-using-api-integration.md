---
title: Erstellen eines Salesforce Lead-Objekts mithilfe der API-Integration
description: Erfahren Sie, wie Sie ein Salesforce Lead-Objekt mithilfe der API-Integration erstellen.
feature: Adaptive Forms, Core Components, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
keywords: Integrieren der API im Regeleditor, Aufrufen von Service-Verbesserungen
exl-id: 55835ffe-1b77-449b-b76d-16c0a343cf5c
hide: true
hidefromtoc: true
index: false
source-git-commit: 3a09a3fa9b8fb3dacef4c900979c4cc256551941
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 100%

---

# Erstellen eines Salesforce Lead-Objekts mithilfe der API-Integration

In diesem Anwendungsbeispiel wird erläutert, wie Sie in Salesforce ein Lead-Objekt mithilfe der API-Integration erstellen. Am Ende dieses Prozesses können Sie:

Eine [verbundene App in Salesforce](https://help.salesforce.com/s/articleView?id=platform.ev_relay_create_connected_app.htm&type=5) einrichten, um sicheren API-Zugriff zu ermöglichen.

CORS (Cross-Origin Resource Sharing) konfigurieren, damit in einem Webbrowser ausgeführter Code (z. B. JavaScript) mit Salesforce von einem bestimmten Ursprung kommunizieren kann. Fügen Sie den Ursprung der Zulassungsliste hinzu, wie unten dargestellt.

![cors](assets/salesforce-cors.png)

## Einstellungen für verbundene Apps

Die folgenden Einstellungen werden in der verbundenen App verwendet. Sie können die OAuth-Bereiche je nach Ihren Anforderungen zuweisen.
![connected-app-settings](assets/salesforce-connected-app-settings.png)

## Erstellen einer API-Integration

| Name | Wert |
|--------------------------------|------------------|
| API-URL | https://`<your-domain>`d.my.salesforce.com/services/data/v32.0/sobjects/Lead |
| Client-ID | Spezifisch für Ihre verbundene App |
| Client-Geheimnis | Spezifisch für Ihre verbundene App |
| OAuth-URL | https://login.salesforce.com/services/oauth2/authorize |
| URL des Zugriffs-Tokens | https://`<your-domain>`/services/oauth2/token |
| URL für aktualisiertes Token | https://`<your-domain>`/services/oauth2/token |
| Autorisierungsumfang | api chatter_api full id openid refresh_token visualforce web |
| Autorisierungs-Header | Autorisierungsträger |

![api-integration](assets/salesforce-api-integration-create-lead.png)

## Eingabe- und Ausgabeparameter

Definieren Sie die Eingabeparameter für den API-Aufruf und ordnen Sie die Ausgabeparameter mithilfe der folgenden JSON zu.

```json
{
    "id": "00QKY000001LyJR2A0",
    "success": true
}
```

![input-output](assets/create-lead-api-integration-input-output.png)

## Erstellen eines Formulars

Erstellen Sie ein einfaches adaptives Formular mit dem universellen Editor, um die Details zum Lead-Objekt wie unten gezeigt zu erfassen.
![lead-object-form](assets/create-lead.png)

Verwalten Sie das Klickereignis im Kontrollkästchen „Lead erstellen“ mithilfe des Regeleditors. Ordnen Sie die Eingabeparameter wie unten dargestellt den Werten der entsprechenden Formularobjekte zu. Die ID des neu erstellten Lead-Objekts wird im TextField-Objekt `leadid` angezeigt.
![rule-editor](assets/create-leade-rule-editor.png)

## Testen der Integration

- Zeigen Sie eine Vorschau des Formulars an.
- Geben Sie einige aussagekräftige Werte ein.
- Aktivieren Sie das Kontrollkästchen `Create Lead`, um den API-Aufruf auszulösen.
- Die Lead-ID des neu erstellten Lead-Objekts wird im Textfeld `Lead ID` angezeigt.
