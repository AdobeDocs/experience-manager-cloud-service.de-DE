---
title: Dynatraktion
description: Erfahren Sie, wie Sie Dynatrace mit AEM as a Cloud Service verwenden.
exl-id: b58c8b82-a098-4d81-bc36-664e890c8f66
source-git-commit: a234f2a00c51bcb23b0c52feac9971259d26b8c3
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---

# Dynatraktion {#dynatrace}

Adobe bietet die Möglichkeit, Dynatraace zu verwenden, um AEM im Rahmen der Unternehmensbereitstellung zu überwachen, die Ursache möglicher Probleme zu ermitteln und Maßnahmen zu ergreifen, um diese bei Bedarf zu beheben.

Mit Dynatraktion können Sie für alle Ihre AEM-Anwendungen eine nahtlose Beobachtbarkeit erhalten. Dynatrace bietet einen umfassenden Einblick in das Benutzererlebnis, indem Sie Ihre AEM-Anwendungen automatisch erkennen und ihre Abhängigkeiten von der Website zum Container für den Cloud-Service visualisieren. In Verbindung mit End-to-End-Traces in allen Ebenen und der Echtzeit-Benutzerüberwachung können Sie Ihre AEM inhaltsbasierten Erlebnisse ohne Lücken oder blinde Flecken auf die nächste Ebene bringen. Wenn Anomalien auftreten, diagnostiziert Dynatrace sie in Echtzeit mit der Davis AI-Engine und zeigt die Ursache auf den fehlerhaften Code an, bevor Ihre Kunden betroffen sind. Dadurch wird die mittlere Reparaturzeit minimiert.

Weitere Informationen zu Dynatrace finden Sie unter [Adobe AEM Cloud Service-Integration](https://www.dynatrace.com/hub/detail/adobe-experience-manager-1/).

![Leistungsmetriken AEM Autoren- und Herausgeber](/help/implementing/cloud-manager/assets/dynatrace-performance-metrics.png)

## Integrieren von Dynatrakien in AEM as a Cloud Service {#integrating-dynatrace-with-aem-as-a-cloud-service}

Dynatraktikkunden können ihre AEM-Umgebungen überwachen, indem sie über ein Support-Ticket eine Konnektivität anfordern.

Die für Verbindungsanfragen erforderlichen Details werden nachfolgend beschrieben:

| **Feld** | **Beschreibung** |
|---|---|
| URL der dynamischen Umgebung | Ihre URL der dynamischen Umgebung.<br><br>Für Dynatrace SaaS-Kunden lautet das Format `https://<your-environment-id>.live.dynatrace.com`.<br><br>Für Dynatrace Managed -Kunden lautet das Format `https://<your-managed-url>/e/<environmentId>` |
| Dynamic Environment ID | Ihre ID der dynamischen Umgebung. Siehe [Abrufen von Informationen zur Dynatraktionsumgebung](#get-dynatrace-env-info) für Informationen dazu. |
| Dynatraktische Umgebungstoken | Ihr Token für die Dynatraktionsumgebung. Siehe [Abrufen von Informationen zur Dynatraktionsumgebung](#get-dynatrace-env-info) für Informationen dazu.<br><br>Dies sollte als geheim betrachtet werden. Verwenden Sie daher geeignete Sicherheitspraktiken. Zum Beispiel schützen Passwörter sie auf einer Website wie **zerobin.net**, auf die das Kundensupport-Ticket zusammen mit dem Kennwort verweisen kann. |
| Dynatraktions-API-Zugriffstoken | Das API-Zugriffstoken Ihrer Dynatraktionsumgebung.  Siehe [Erstellen eines Dynatraktions-API-Zugriffstokens](#create-dynatrace-access-token) für die Erstellung.<br><br>Dies sollte als geheim betrachtet werden, sodass geeignete Sicherheitspraktiken zum Einsatz kommen. Zum Beispiel schützen Passwörter sie auf einer Website wie **zerobin.net**, auf die das Kundensupport-Ticket zusammen mit dem Kennwort verweisen kann.<br><br>Hinweis: Dies ist nur für Dynatrace Managed erforderlich. |
| Dynatrace ActiveGate Port | Ihr ActiveGate-Port von Dynatracet, mit dem die AEM-Integration eine Verbindung herstellen soll.<br><br>Hinweis: Dies ist nur für Dynatrace Managed erforderlich. |
| DynamicGate-Netzwerkzone | Ihre [Dynatrace ActiveGate-Netzwerkzone](https://docs.dynatrace.com/docs/manage/network-zones) die effiziente Weiterleitung AEM Überwachungsdaten über Rechenzentren und Netzwerkregionen hinweg.<br><br>Hinweis: Eine DynamicGate-Netzwerkzone ist optional. |
| AEM Umgebungs-ID(s) | Die AEM-Umgebungs-ID(s) für die Überwachung durch Dynatraktion. |

>[!NOTE]
>
>Nach der Integration von Dynatrace fließen die Daten nicht mehr in andere APM-Tools wie New Relic, sofern sie zuvor aktiviert waren.


## Erstellen eines Dynatraktions-API-Zugriffstokens {#create-dynatrace-access-token}

1. Melden Sie sich bei Ihrer Dynatraktionsumgebung an.
1. Gehen Sie im Dynatraktionsmenü zu Verwalten > Zugriffstoken .
1. Wählen Sie Neues Token generieren aus.
1. Definieren Sie einen Tokennamen.

1. Optional: Legen Sie ein Ablaufdatum fest. Stellen Sie sicher, dass Sie ein neues Token generieren, bevor es abläuft.
1. Setzen Sie den Token-Umfang auf PaaS-Integration - Installationsprogramm herunterladen
1. Wählen Sie Token generieren aus.
1. Kopieren Sie das generierte Zugriffstoken und speichern Sie es an einem sicheren Ort.


## Abrufen von Informationen zur Dynatraktionsumgebung {#get-dynatrace-env-info}

1. Führen Sie die folgende API-Anfrage an Ihre Dynatraktionsumgebung aus:

`curl -X GET "<environmentUrl>/api/v1/deployment/installer/agent/connectioninfo" -H "accept: application/json" -H "Authorization: Api-Token <accessToken>"`

Ersetzen \&lt;environmenturl> mit der URL Ihrer dynamischen Umgebung und \&lt;accesstoken> mit Ihrem erstellten API-Zugriffstoken.

1. Kopieren Sie den \&lt;environmentid> und \&lt;environmenttoken> aus der Antwort-Payload und speichern Sie sie an einem gesicherten Ort.

```
{
   "tenantUUID": "<environmentId>",
   "tenantToken": "<environmentToken>",
   "communicationEndpoints": [
   ... 
   ],
   "formattedCommunicationEndpoints": "<endpoints>" 
}
```


